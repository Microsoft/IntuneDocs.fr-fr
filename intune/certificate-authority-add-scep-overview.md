---
title: Utiliser une autorité de certification tierce avec SCEP dans Microsoft Intune - Azure | Microsoft Docs
description: Dans Microsoft Intune, vous pouvez ajouter un fournisseur ou une autorité de certification tierce pour émettre des certificats à destination d’appareils mobiles à l’aide du protocole SCEP. Dans cette vue d’ensemble, une application Azure Active Directory (Azure AD) accorde à Microsoft Intune les autorisations de valider des certificats. Utilisez ensuite l’ID d’application, la clé d’authentification et l’ID de locataire de l’application AAD dans le programme d’installation de votre serveur SCEP pour émettre des certificats.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: de0df4878d2461d2f7c0a022a7e3d305e58aef7f
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187784"
---
# <a name="add-partner-certification-authority-in-intune-using-scep"></a>Ajouter l’autorité de certification partenaire dans Intune à l’aide de SCEP

Dans Microsoft Intune, des autorités de certification tierces peuvent être ajoutées. Ces autorités de certification peuvent fournir des certificats aux appareils mobiles à l’aide du protocole SCEP (Simple Certificate Enrollment Protocol). Cette fonctionnalité peut émettre de nouveaux certificats et renouveler les certificats sur des appareils Windows, iOS, Android et macOS.

Il existe deux façons d’utiliser cette fonctionnalité : l’API open source et les tâches d’administrateur Intune.

**Partie 1 : utiliser une API open source**  
Microsoft a créé une API qui s’intègre à Intune pour valider des certificats, envoyer des notifications de réussite ou d’échec et utiliser SSL, en particulier la fabrique de socket SSL, pour communiquer avec Intune.

L’API est disponible dans le [dépôt GitHub public d’API Intune SCEP](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation) pour que vous puissiez la télécharger et l’utiliser dans vos solutions. Utilisez cette API avec des serveurs SCEP tiers pour exécuter une validation de stimulation personnalisée par rapport à Intune avant de remettre un certificat à un appareil.

[Intégrer à la solution de gestion Intune SCEP](scep-libraries-apis.md) fournit plus de détails sur l’utilisation de l’API, ses méthodes et le test de la solution que vous générez.

**Partie 2 : créer l’application et le profil**  
À l’aide d’une application Azure Active Directory (Azure AD), vous pouvez déléguer des droits à Intune pour gérer les demandes SCEP provenant des appareils. L’application Azure AD inclut les valeurs d’ID d’application et de clé d’authentification qui sont utilisées au sein de la solution d’API que le développeur crée. Les administrateurs peuvent ensuite créer et déployer des profils de certificat SCEP à l’aide d’Intune. Vous pouvez également afficher des rapports sur l’état du déploiement sur les appareils.

Cet article fournit une vue d’ensemble de cette fonctionnalité du point de vue d’un administrateur, notamment la création de l’application Azure AD.

## <a name="overview"></a>Vue d’ensemble

Les étapes suivantes fournissent une vue d’ensemble de l’émission de certificats SCEP dans Intune :

1. Dans Intune, un administrateur crée un profil de certificat SCEP, puis cible le profil sur des utilisateurs ou appareils.
2. L’appareil s’enregistre auprès d’Intune.
3. Intune crée une stimulation SCEP unique. Il ajoute également des informations de contrôle d’intégrité supplémentaires, telles que l’objet attendu et l’autre nom de l’objet.
4. Intune chiffre et signe les informations de stimulation et de contrôle d’intégrité, puis les envoie à l’appareil avec la demande SCEP.
5. L’appareil génère une demande de signature de certificat et une paire de clés publique/privée sur l’appareil selon le profil de certificat SCEP proposé par Intune.
6. La demande de signature de certificat et la stimulation chiffrée/signée sont envoyées au point de terminaison du serveur SCEP tiers.
7. Le serveur SCEP envoie la demande et la stimulation à Intune. Intune valide alors la signature, déchiffre la charge utile, puis compare la demande de signature de certificat aux informations de contrôle d’intégrité.
8. Intune renvoie une réponse au serveur SCEP et indique si la validation de stimulation est réussie ou non.  
9. Si la stimulation est correctement vérifiée, le serveur SCEP émet le certificat à destination de l’appareil.

Le diagramme suivant montre un flux détaillé de l’intégration d’un serveur SCEP tiers à Intune :

![Intégration d’une autorité de certification tierce SCEP à Microsoft Intune](./media/scep-certificate-vendor-integration.png)

## <a name="set-up-third-party-ca-integration"></a>Configurer l’intégration d’une autorité de certification tierce

### <a name="validate-third-party-certification-authority"></a>Valider l’autorité de certification tierce

Avant d’intégrer des autorités de certification tierces à Intune, vérifiez que l’autorité de certification que vous utilisez prend en charge Intune. [Partenaires des autorités de certification tierces](#third-party-certification-authority-partners) (dans cet article) inclut une liste. Vous pouvez également consulter les instructions de votre autorité de certification pour plus d’informations. L’autorité de certification peut inclure des instructions d’installation spécifiques à son implémentation.

### <a name="authorize-communication-between-ca-and-intune"></a>Autoriser la communication entre l’autorité de certification et Intune

Pour autoriser un serveur SCEP tiers à exécuter une validation de stimulation personnalisée par rapport à Intune, créez une application dans Azure AD. Cette application accorde des droits délégués à Intune pour valider les demandes SCEP.

Vérifiez que vous disposez des autorisations requises pour inscrire une application Azure AD. [Autorisations requises](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions) répertorie les étapes.

**Étape 1 : Créer une application Azure AD**

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Sélectionnez **Azure Active Directory** > **Inscriptions des applications** > **Inscription d’une nouvelle application**.
3. Entrez un nom et une URL de connexion. Sélectionnez **Application/API web** pour le type d’application.
4. Sélectionnez **Créer**.

[Intégrer des applications à Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) inclut des instructions sur la création d’une application, notamment des conseils sur l’URL et le nom.

**Étape 2 : Accorder des autorisations**

Après avoir créé votre application, accordez les autorisations requises à l’API Microsoft Intune :

1. Dans votre application Azure AD, ouvrez **Paramètres** > **Autorisations requises**.  
2. Sélectionnez **Ajouter** > **Sélectionner une API** > sélectionnez **API Microsoft Intune** > **Sélectionner**.
3. Dans **Sélectionner des autorisations**, choisissez **SCEP challenge validation** (Validation de stimulation SCEP) > **Sélectionner**.
4. Sélectionnez **Terminé** pour enregistrer vos changements.

**Étape 3 : Obtenir l’ID d’application et la clé d’authentification**

Obtenez ensuite les valeurs d’ID et de clé de votre application Azure AD. Les valeurs suivantes sont nécessaires :

- ID de l'application
- Clé d’authentification
- ID de locataire

**Pour obtenir l’ID d’application et la clé d’authentification** :

1. Dans Azure AD, sélectionnez votre nouvelle application (**Inscriptions des applications**).
2. Copiez **l’ID d’application** et stockez-le dans votre code d’application.
3. Ensuite, générez une clé d’authentification. Dans votre application Azure AD, ouvrez **Paramètres** > **Clés**.
4. Dans **Mots de passe**, entrez une description et choisissez la durée de la clé. **Enregistrez** les changements apportés. Copiez et enregistrez la valeur affichée.

    > [!IMPORTANT]
    > Copiez et enregistrez cette clé immédiatement, car elle ne va plus s’afficher. Cette valeur de clé est nécessaire avec votre implémentation de l’autorité de certification tierce. Veillez à consulter les instructions de configuration souhaitée pour l’ID d’application, la clé d’authentification et l’ID de locataire.

**L’ID de locataire** est le texte de domaine après le signe @ dans votre compte. Par exemple, si votre compte est `admin@name.onmicrosoft.com`, votre ID de locataire est **name.onmicrosoft.com**.

[Obtenir l’ID d’application et la clé d’authentification](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#get-application-id-and-authentication-key) répertorie les étapes pour obtenir ces valeurs et fournit des informations détaillées sur les applications Azure AD.

### <a name="configure-and-deploy-a-scep-certificate-profile"></a>Configurer et déployer un profil de certificat SCEP
En tant qu’administrateur, créez un profil de certificat SCEP pour cibler des utilisateurs ou appareils. Ensuite, affectez le profil.

- [Créer un profil de certificat SCEP](certificates-scep-configure.md#create-a-scep-certificate-profile)

- [Affecter le profil de certificat](certificates-scep-configure.md#assign-the-certificate-profile)

## <a name="removing-certificates"></a>Suppression de certificats

Quand vous désinscrivez ou réinitialisez l’appareil, les certificats sont supprimés. Les certificats ne sont pas révoqués.

## <a name="third-party-certification-authority-partners"></a>Partenaires des autorités de certification tierces
Les autorités de certification tierces suivantes prennent en charge Intune :

- [Entrust Datacard](http://www.entrustdatacard.com/resource-center/documents/documentation)
- [Version open source GitHub d’EJBCA](https://github.com/agerbergt/intune-ejbca-connector)
- [EverTrust](https://evertrust.fr/en/products/)

Si vous êtes une autorité de certification tierce intéressée par l’intégration de votre produit à Intune, passez en revue les instructions de l’API :

- [Dépôt GitHub d’API Intune SCEP](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Instructions de l’API Intune SCEP pour les autorités de certification tierces](scep-libraries-apis.md)

## <a name="see-also"></a>Voir aussi

- [Configurer les profils de certificat](certificates-scep-configure.md)
- [Dépôt GitHub d’API Intune SCEP](http://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Instructions de l’API Intune SCEP pour les autorités de certification tierces](scep-libraries-apis.md)
