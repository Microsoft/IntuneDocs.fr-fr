---
title: Paramètres d’appareils partagés Intune pour l’application iOS Classroom
titleSuffix: Microsoft Intune
description: Découvrez les paramètres Intune qui vous permettent de contrôler les paramètres pour l’application Classroom sur les appareils iOS.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1381a5ce-c743-40e9-8a10-4c218085bb5f
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 558f55d1d809fe634f7b48a91962644fe0d97232
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55842879"
---
# <a name="configure-intune-education-settings-for-shared-ipad-devices"></a>Configurer les paramètres d’Intune Education pour les appareils iPad partagés

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

> [!NOTE]
> Les paramètres Intune de l’application Classroom sont obsolètes dans Intune. Cet article s’applique uniquement aux utilisateurs ayant des profils Éducation existants dans Intune.

Intune prend en charge l’application iOS Classroom, qui permet aux enseignants d’orienter l’apprentissage et de contrôler les appareils des étudiants dans la salle de classe. En outre, pour l’application Classroom, Apple prend en charge la possibilité de configurer les appareils iPad des étudiants de sorte que plusieurs étudiants puissent partager un même appareil. Ce document vous explique comment atteindre cet objectif avec Intune.

Pour plus d’informations sur la configuration des appareils iPad dédiés (1:1) pour utiliser l’application Classroom, consultez [Guide pratique pour configurer les paramètres Intune pour l’application iOS Classroom](education-settings-configure-ios.md).

## <a name="before-you-start"></a>Avant de commencer

Les prérequis pour utiliser les fonctionnalités partagées iPad sont les suivants :

- Installez [Apple School Manager](apple-school-manager-set-up-ios.md) et [School Data Sync (SDS)](https://support.office.com/article/Apple-School-Manager-integration-with-Intune-for-Education-and-School-Data-Sync-974bd1f9-2c7a-45cb-9447-b58166108617).
- Dans le cadre de l’installation d’Apple School Manager, configurer des [ID Apple gérés](http://help.apple.com/schoolmanager/#/tes78b477c81) pour les étudiants. [En savoir plus sur les ID Apple gérés](https://support.apple.com/HT205918).
- Créer un profil d’inscription pour les numéros de série d’appareils synchronisés à partir d’Apple School Manager.

## <a name="step-1---import-your-school-data-into-azure-active-directory"></a>Étape 1 : Importer vos données scolaires dans Azure Active Directory

Utilisez SDS (School Data Sync) de Microsoft pour importer des dossiers scolaires d’un système SIS (Student Information System) existant vers Azure AD (Azure Active Directory).
SDS synchronise les informations de votre SIS et les stocke dans Azure AD. Azure AD est un système de gestion Microsoft qui vous permet d’organiser les utilisateurs et les appareils. Vous pouvez ensuite utiliser ces données pour vous aider à gérer les étudiants et cours. [En savoir plus sur le déploiement de SDS](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91).

### <a name="how-to-import-data-using-sds"></a>Comment importer des données à l’aide de SDS ?

Vous pouvez importer des informations dans SDS en appliquant l’une des méthodes suivantes :

- [Fichiers CSV](https://support.office.com/article/Follow-these-steps-71d5fe4a-aa51-4f35-9b53-348898a390a1) : exportez et compilez manuellement des fichiers de valeurs séparées par des virgules (.csv)
- [API PowerSchool](https://support.office.com/article/Follow-these-steps-851b5edc-558f-43a9-9122-b2d63458cb8f) : fournisseur SIS qui simplifie la synchronisation avec Azure AD
- [OneRoster](https://support.office.com/article/Follow-these-steps-f43cbb2a-b502-497d-a8b1-783dc05a57ab) : format CSV que vous pouvez exporter et convertir pour la synchronisation avec Azure AD

### <a name="find-out-more"></a>En savoir plus

- [En savoir plus sur l’expérience complète de la synchronisation des données scolaires locales avec Azure AD](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)
- [En savoir plus sur School Data Sync de Microsoft](https://sds.microsoft.com/)
- [En savoir plus sur les licences dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-licensing-whatis-azure-portal)


## <a name="step-2---create-and-assign-an-ios-education-profile-in-intune"></a>Étape 2 : Créer et affecter un profil Éducation iOS dans Intune

### <a name="configure-general-settings"></a>Configurer les paramètres généraux

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Dans le volet **Intune**, choisissez **Configuration de l’appareil**.
2. Dans le volet **Configuration de l’appareil**, sous la section **Gérer**, choisissez **Profils**.
5. Dans le volet de profils, choisissez **Créer un profil**.
6. Dans le volet **Créer un profil**, entrez un **Nom** et une **Description** pour le profil Éducation iOS.
7. Dans la liste déroulante **Plateforme**, choisissez **iOS**.
8. Dans la liste déroulante **Type de profil**, choisissez **Education**.
9. Choisissez **Paramètres** > **Configurer**.

Vous avez ensuite besoin de certificats pour établir une relation d’approbation entre les iPad des enseignants et étudiants. Les certificats sont utilisés pour authentifier de manière fluide et silencieuse les connexions entre les appareils sans avoir à entrer les noms d’utilisateur et mots de passe.

>[!Important]
>Les certificats des enseignants et étudiants que vous utilisez doivent être émis par des autorités de certification différentes. Vous devez créer deux autorités de certification subordonnées connectées à votre infrastructure de certificats existante : une pour les enseignants et une pour les étudiants.

Les profils Éducation iOS prennent en charge uniquement les certificats PFX. Les certificats SCEP ne sont pas pris en charge.

Les certificats que vous créez doivent prendre en charge l’authentification du serveur en plus de l’authentification de l’utilisateur.

### <a name="configure-teacher-certificates"></a>Configurer des certificats d’enseignant

Dans le volet **Éducation**, choisissez **Certificats d’enseignant**.

#### <a name="configure-teacher-root-certificate"></a>Configurer le certificat racine de l’enseignant

Sous **Certificat racine d’enseignant**, cliquez sur le bouton Parcourir pour sélectionner le certificat racine de l’enseignant avec l’extension .cer (DER ou codé en Base64), ou .P7B (avec ou sans la chaîne complète).

#### <a name="configure-teacher-pkcs12-certificate"></a>Configurer le certificat PKCS#12 de l’enseignant

Sous **Certificat PKCS#12 d’enseignant**, configurez les valeurs suivantes :

- **Format du nom de l’objet** : Intune ajoute automatiquement **organisateur** comme préfixe au nom commun du certificat pour le certificat de l’enseignant, et **membre** pour le certificat de l’étudiant.
- **Autorité de certification** : autorité de certification d’entreprise qui s’exécute sur une édition Entreprise de Windows Server 2008 R2 ou version ultérieure. Une autorité de certification autonome n'est pas prise en charge.
- **Nom de l’autorité de certification** : entrez le nom de votre autorité de certification.
- **Nom du modèle de certificat** : entrez le nom d’un modèle de certificat qui a été ajouté à une autorité de certification émettrice.
- **Seuil de renouvellement (%)** : spécifiez le pourcentage de durée de vie restante du certificat avant que l’appareil ne demande le renouvellement du certificat.
- **Période de validité du certificat** : spécifiez la quantité de temps restant avant l’expiration du certificat. Vous pouvez spécifier une valeur inférieure à la période de validité du modèle de certificat spécifié, mais pas une valeur supérieure. Par exemple, si la période de validité du certificat dans le modèle de certificat est de 2 ans, vous pouvez spécifier une valeur de 1 an mais pas une valeur de 5 ans. La valeur doit également être inférieure à la période de validité restante du certificat de l’autorité de certification émettrice.

Quand vous avez terminé la configuration des certificats d’enseignants, choisissez **OK**.

### <a name="configure-student-certificates"></a>Configurer des certificats d’étudiant

1. Dans le volet **Éducation**, choisissez **Certificats d’étudiant**.
2. Dans le volet **Certificats d’étudiant**, dans la liste **Type de certificat d’appareil étudiant**, choisissez **iPad partagé**.

#### <a name="configure-student-root-certificate"></a>Configurer le certificat racine de l’étudiant

Sous **Certificat racine de l’appareil**, cliquez sur le bouton Parcourir pour sélectionner le certificat racine de l’étudiant avec l’extension .cer (DER ou codé en Base64) ou .P7B (avec ou sans la chaîne complète).

#### <a name="configure-device-pkcs12-certificate"></a>Configurer le certificat PKCS#12 d’appareil

Sous **Certificat PKCS#12 d’étudiant**, configurez les valeurs suivantes :

- **Format du nom de l’objet** : Intune ajoute automatiquement « organisateur » comme préfixe au nom commun du certificat pour le certificat de l’enseignant, et « membre » pour le certificat de l’appareil.
- **Autorité de certification** : autorité de certification d’entreprise qui s’exécute sur une édition Entreprise de Windows Server 2008 R2 ou version ultérieure. Une autorité de certification autonome n'est pas prise en charge.
- **Nom de l’autorité de certification** : entrez le nom de votre autorité de certification.
- **Nom du modèle de certificat** : entrez le nom d’un modèle de certificat qui a été ajouté à une autorité de certification émettrice.
- **Seuil de renouvellement (%)** : spécifiez le pourcentage de durée de vie restante du certificat avant que l’appareil ne demande le renouvellement du certificat.
- **Période de validité du certificat** : spécifiez la quantité de temps restant avant l’expiration du certificat. Vous pouvez spécifier une valeur inférieure à la période de validité du modèle de certificat spécifié, mais pas une valeur supérieure. Par exemple, si la période de validité du certificat dans le modèle de certificat est de 2 ans, vous pouvez spécifier une valeur de 1 an mais pas une valeur de 5 ans. La valeur doit également être inférieure à la période de validité restante du certificat de l’autorité de certification émettrice.

Quand vous avez terminé la configuration des certificats, choisissez **OK**.

### <a name="complete-certificate-setup"></a>Terminer l’installation du certificat

1. Dans le volet **Éducation**, choisissez **OK**.
2. Dans le volet **Créer un profil**, choisissez **Créer**.

Le profil est créé et apparaît dans le volet de la liste des profils.

## <a name="step-3---create-a-device-category"></a>Étape 3 : Créer une catégorie d’appareils

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Dans le volet **Intune**, choisissez **Inscription de l’appareil**.
4. Dans le volet **Inscription de l’appareil - Vue d’ensemble**, choisissez **Catégories d’appareils**.
5. Dans le volet **Inscription de l’appareil - Catégories d’appareils**, choisissez **Créer**.
6. Dans le volet **Créer une catégorie d’appareils**, entrez un **Nom** et une **Description** pour la catégorie.
7. Dans le volet **Créer une catégorie d’appareils**, choisissez **Créer**.

La catégorie d’appareils est créée dans le volet **Inscription - Catégories d’appareils**.

## <a name="step-4--create-a-dynamic-group"></a>Étape 4 : Créer un groupe dynamique

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Dans le volet **Intune**, choisissez **Groupes**.
4. Dans le volet **Utilisateurs et groupes – Tous les groupes**, choisissez **Nouveau groupe**.
5. Dans le volet **Groupe**, choisissez un **Type de groupe**, puis entrez un **Nom** et une **Description** pour le groupe.
6. Dans la liste déroulante **Type d’adhésion**, choisissez **Appareil dynamique**.
7. Choisissez **Membres de dispositif dynamique** pour créer des règles d’adhésion.
8. Dans le volet **Règles d’appartenance dynamique** :
1. Sélectionnez **deviceCategory** dans la liste déroulante **Ajouter des appareils où**.
2. Choisissez **Est égal à**.
3. Entrez la catégorie d’appareils que vous avez créée dans la zone de texte vide.
9. Dans le volet **Règles d’appartenance dynamique**, choisissez **Ajouter une requête**.
10. Dans le volet **Groupe**, choisissez **Créer**.

Le groupe dynamique est créé dans le volet **Utilisateurs et groupes – Tous les groupes**.

## <a name="step-5--assign-a-device-to-a-category-carts"></a>Étape 5 : Affecter un appareil à une catégorie (paniers)

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Dans le volet **Intune**, choisissez **Appareils**.
4. Dans le volet **Appareils**, choisissez **Tous les appareils**.
5. Dans le volet **Appareils – Tous les appareils**, choisissez un appareil.
6. Dans le volet de l’appareil, choisissez **Propriétés**.
7. Dans le volet des propriétés de l’appareil, entrez la catégorie d’appareils dans la zone de texte **Catégorie d’appareils**.
8. Dans le volet des appareils, choisissez **Enregistrer**.

L’appareil est maintenant associé à la catégorie d’appareils. Répétez ce processus pour tous les appareils que vous souhaitez associer à la catégorie d’appareils que vous avez créée.

## <a name="step-6--create-classroom-profiles"></a>Étape 6 : Créer des profils de classe

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Dans le volet **Intune**, choisissez **Configuration de l’appareil**.
4. Dans le volet **Configuration de l’appareil**, choisissez **Gérer** > **Profils de panier**.
5. Dans le volet de profils, choisissez **Créer un profil**.
6. Dans le volet **Créer une association**, entrez un **Nom** et une **Description**.
7. Choisissez **Sélectionner des classes** > **Configurer** pour associer des groupes au profil de panier.
8. Choisissez les classes à inclure au profil de panier, puis choisissez **Sélectionnez**. 
9. Choisissez **Sélectionner des paniers** > **Configurer** pour associer des groupes au profil de panier.
10. Choisissez les groupes à inclure au profil de panier, puis choisissez **Sélectionnez**.
11. Dans le volet **Créer une association**, choisissez **Enregistrer** pour enregistrer le profil de panier.

Le profil est créé et apparaît dans le volet de la liste des profils.

## <a name="step-7---assign-the-cart-profile-to-classes"></a>Étape 7 : Affecter le profil de panier à des classes

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. Choisissez **Tous les services** > **Intune**. Intune se trouve dans la section **Surveillance + Gestion**.
3. Dans le volet **Intune**, choisissez **Configuration de l’appareil**.
4. Dans le volet **Configuration de l’appareil**, choisissez **Surveiller** > **État de l’attribution**.
5. Dans le volet **État de l’attribution**, sélectionnez le **Profil de panier** que vous avez créé.
6. Dans le volet **Profil de panier**, choisissez **Affectations** puis, sous **Inclure**, choisissez **Sélectionner les groupes à inclure**.
7. Sélectionnez les classes que vous voulez que le profil de panier cible (ne sélectionnez pas un groupe), puis choisissez **Sélectionner**. 
8. Lorsque vous avez terminé, choisissez **Enregistrer**.

L’affectation se termine et Intune déploie le profil de classe sur les appareils ciblés en fonction de l’attribution de classe.

## <a name="next-steps"></a>Étapes suivantes

Les étudiants peuvent maintenant partager des appareils. Ils peuvent prendre n’importe quel iPad dans une salle de classe, se connecter avec un code PIN et le personnaliser avec leur contenu. Pour plus d’informations sur les iPad partagés, consultez le [site web d’Apple](https://www.apple.com/education/it/).
