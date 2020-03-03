---
title: Utiliser des autorités de certification tierces avec SCEP dans Microsoft Intune – Azure | Microsoft Docs
description: Dans Microsoft Intune, vous pouvez ajouter un fournisseur ou une autorité de certification (AC) tierce pour émettre des certificats à destination d’appareils mobiles à l’aide du protocole SCEP. Dans cette vue d’ensemble, une application Azure Active Directory (Azure AD) accorde à Microsoft Intune les autorisations de valider des certificats. Utilisez ensuite l’ID d’application, la clé d’authentification et l’ID de locataire de l’application AAD dans le programme d’installation de votre serveur SCEP pour émettre des certificats.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 85aac54a81d81dc138dd12612db183aae839b72b
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77575983"
---
# <a name="add-partner-certification-authority-in-intune-using-scep"></a>Ajouter l’autorité de certification partenaire dans Intune à l’aide de SCEP

Utilisez des autorités de certification (AC) tierces avec Intune. Les autorités de certification tierces peuvent configurer des appareils mobiles avec des certificats nouveaux ou renouvelés à l’aide du protocole SCEP (Simple Certificate Enrollment Protocol), et peuvent prendre en charge les appareils Windows, iOS/iPadOS, Android et macOS.

Il existe deux façons d’utiliser cette fonctionnalité : l’API open source et les tâches d’administrateur Intune.

**Partie 1 : utiliser une API open source**  
Microsoft a créé une API pour intégrer à Intune. Par le biais d’une API, vous pouvez valider des certificats, envoyer des notifications de réussite ou d’échec et utiliser SSL, en particulier la fabrique de socket SSL, pour communiquer avec Intune.

L’API est disponible dans le [dépôt GitHub public d’API Intune SCEP](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation) pour que vous puissiez la télécharger et l’utiliser dans vos solutions. Utilisez cette API avec des serveurs SCEP tiers pour exécuter une validation de test personnalisée par rapport à Intune avant que SCEP ne configure un certificat sur un appareil.

[Intégrer à la solution de gestion Intune SCEP](scep-libraries-apis.md) fournit plus de détails sur l’utilisation de l’API, ses méthodes et le test de la solution que vous générez.

**Partie 2 : créer l’application et le profil**  
À l’aide d’une application Azure Active Directory (Azure AD), vous pouvez déléguer des droits à Intune pour gérer les demandes SCEP provenant des appareils. L’application Azure AD inclut les valeurs d’ID d’application et de clé d’authentification qui sont utilisées au sein de la solution d’API que le développeur crée. Les administrateurs créent et déploient des profils de certificats SCEP avec Intune et peuvent afficher des rapports sur l’état du déploiement sur les appareils.

Cet article fournit une vue d’ensemble de cette fonctionnalité du point de vue d’un administrateur, notamment la création de l’application Azure AD.

## <a name="overview"></a>Vue d’ensemble

Les étapes suivantes fournissent une vue d’ensemble de l’utilisation de SCEP pour les certificats dans Intune :

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

> [!div class="mx-imgBorder"]
> ![Intégration d’une autorité de certification tierce SCEP à Microsoft Intune](./media/certificate-authority-add-scep-overview/scep-certificate-vendor-integration.png)

## <a name="set-up-third-party-ca-integration"></a>Configurer l’intégration d’une autorité de certification tierce

### <a name="validate-third-party-certification-authority"></a>Valider l’autorité de certification tierce

Avant d’intégrer des autorités de certification tierces à Intune, vérifiez que l’autorité de certification que vous utilisez prend en charge Intune. [Partenaires des autorités de certification tierces](#third-party-certification-authority-partners) (dans cet article) inclut une liste. Vous pouvez également consulter les instructions de votre autorité de certification pour plus d’informations. L’autorité de certification peut inclure des instructions d’installation spécifiques à son implémentation.

### <a name="authorize-communication-between-ca-and-intune"></a>Autoriser la communication entre l’autorité de certification et Intune

Pour autoriser un serveur SCEP tiers à exécuter une validation de stimulation personnalisée par rapport à Intune, créez une application dans Azure AD. Cette application accorde des droits délégués à Intune pour valider les demandes SCEP.

Vérifiez que vous disposez des autorisations requises pour inscrire une application Azure AD. Consultez [Autorisations requises](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions) dans la documentation Azure AD.

#### <a name="create-an-application-in-azure-active-directory"></a>Créer une application dans Azure Active Directory  

1. Dans le [portail Azure](https://portal.azure.com), accédez à **Azure Active Directory** > **Inscriptions d’applications**, puis sélectionnez **Nouvelle inscription**.  

2. Sur la page **Inscrire une application**, spécifiez les détails suivants :  
   - Dans la section **Nom**, entrez un nom d’application explicite.  
   - Pour la section **Types de comptes pris en charge**, sélectionnez **Comptes dans n’importe quel répertoire d’organisation**.  
   - Pour **URI de redirection**, laissez la valeur par défaut du site web, puis spécifiez l’URL de connexion pour le serveur SCEP tiers.  

3. Sélectionnez **Inscrire** pour créer l’application et ouvrir la page Vue d’ensemble de cette nouvelle application.  

4. Sur la page **Vue d’ensemble** de l’application, copiez la valeur **ID d’application (client)** et enregistrez-la pour une utilisation ultérieure. Vous aurez besoin de cette valeur ultérieurement.  

5. Dans le volet de navigation de l’application, accédez à **Certificats et clés secrètes** sous **Gérer**. Sélectionnez le bouton **Nouvelle clé secrète client**. Entrez une valeur dans la Description, sélectionnez une option pour **Expire**, puis choisissez **Ajouter** afin de générer une *valeur* pour la clé secrète client. 
   > [!IMPORTANT]  
   > Avant de quitter cette page, copiez la valeur de la clé secrète client et enregistrez-la pour une utilisation ultérieure avec votre implémentation d’autorité de certification tierce. Cette valeur ne s’affiche plus. Veillez à consulter les instructions de configuration souhaitées par votre autorité de certification tierce pour l’ID d’application, la clé d’authentification et l’ID de locataire.  

6. Enregistrer votre **ID de locataire**. L’ID de locataire est le texte de domaine après le signe @ dans votre compte. Par exemple, si votre compte est *admin@name.onmicrosoft.com*, votre ID de locataire est **name.onmicrosoft.com**.  

7. Dans le volet de navigation de l’application, accédez à **Autorisations d’API** sous **Gérer**, puis sélectionnez **Ajouter une autorisation**.  

8. Sur la page **Demander des autorisations d’API**, sélectionnez **Intune**, puis sélectionnez **Autorisations d’application**. Activez la case à cocher pour **scep_challenge_provider** (validation de demande d’accès SCEP).  

   Sélectionnez **Ajouter des autorisations** pour enregistrer cette configuration.  

9. Restez à la page **Autorisations d’API**, sélectionnez **Accorder le consentement administrateur pour Microsoft**, puis sélectionnez **Oui**.  
   
   Le processus d’inscription d’application dans Azure AD est terminé.





### <a name="configure-and-deploy-a-scep-certificate-profile"></a>Configurer et déployer un profil de certificat SCEP
En tant qu’administrateur, créez un profil de certificat SCEP pour cibler des utilisateurs ou appareils. Ensuite, affectez le profil.

- [Créer un profil de certificat SCEP](certificates-profile-scep.md#create-a-scep-certificate-profile)

- [Affecter le profil de certificat](certificates-profile-scep.md#assign-the-certificate-profile)

## <a name="removing-certificates"></a>Suppression de certificats

Quand vous désinscrivez ou réinitialisez l’appareil, les certificats sont supprimés. Les certificats ne sont pas révoqués.

## <a name="third-party-certification-authority-partners"></a>Partenaires des autorités de certification tierces
Les autorités de certification tierces suivantes prennent en charge Intune :

- [Entrust Datacard](https://go.entrustdatacard.com/pki/intune/)
- [Version open source GitHub d’EJBCA](https://github.com/agerbergt/intune-ejbca-connector)
- [EverTrust](https://evertrust.fr/en/products/)
- [GlobalSign](https://downloads.globalsign.com/acton/attachment/2674/f-6903f60b-9111-432d-b283-77823cc65500/1/-/-/-/-/globalsign-aeg-microsoft-intune-integration-guide.pdf)
- [IDnomic](https://www.idnomic.com/)
- [Sectigo](https://sectigo.com/products)
- [DigiCert](https://knowledge.digicert.com/tutorials/microsoft-intune.html)
- [Venafi](https://www.venafi.com/platform/enterprise-mobility)
- [SCEPman](https://azuremarketplace.microsoft.com/marketplace/apps/gluckkanja.scepman)

Si vous êtes une autorité de certification tierce intéressée par l’intégration de votre produit à Intune, passez en revue les instructions de l’API :

- [Dépôt GitHub d’API Intune SCEP](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Instructions de l’API Intune SCEP pour les autorités de certification tierces](scep-libraries-apis.md)

## <a name="see-also"></a>Voir aussi

- [Configurer les profils de certificat](certificates-scep-configure.md)
- [Dépôt GitHub d’API Intune SCEP](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Instructions de l’API Intune SCEP pour les autorités de certification tierces](scep-libraries-apis.md)
