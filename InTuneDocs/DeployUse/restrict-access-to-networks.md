---
title: "Restreindre l’accès aux réseaux avec Cisco ISE | Microsoft Intune"
description: "Utilisez Cisco ISE avec Intune pour que les appareils soient inscrits auprès d’Intune et conformes aux stratégies avant d’accéder aux infrastructures Wi-Fi et VPN contrôlées par Cisco ISE."
keywords: 
author: nbigman
manager: jeffgilb
ms.date: 06/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5631bac3-921d-438e-a320-d9061d88726c
translationtype: Human Translation
ms.sourcegitcommit: f33a86c51320c75ce74d20e0cac2b9581990ecec
ms.openlocfilehash: 78945498a951e7b897164ae6f33c4e87d521ca5b


---

# Utilisation de Cisco ISE avec Microsoft Intune
L’intégration d’Intune à Cisco ISE vous permet de créer des stratégies réseau dans votre environnement ISE faisant appel à l’état de conformité et à l’inscription d’appareils Intune. Grâce à ces stratégies, l’accès à votre réseau d’entreprise est limité aux appareils qui sont gérés par Intune et qui sont conformes aux stratégies Intune. 

## Configuration

Pour activer cette intégration, aucune configuration particulière n’est nécessaire dans votre client Intune. Vous devez fournir des autorisations à votre serveur Cisco ISE pour accéder à votre client Intune ; une fois cette opération effectuée, le reste de la configuration se déroule dans votre serveur Cisco ISE. Cet article indique comment fournir à votre serveur ISE des autorisations d’accès à votre client Intune. 

### Étape 1 : Gérer les certificats
1. Dans la console Azure Active Directory (AAD), exportez le certificat. 

    #### Internet Explorer 11
        
    a. Exécutez Internet Explorer en tant qu’administrateur, puis connectez-vous à la console AAD.
  
    b. Choisissez l’icône en forme de verrou dans la barre d’adresse, puis **Afficher les certificats**.
    
    c. Sous l’onglet **Détails** des propriétés des certificats, choisissez **Copier dans un fichier**.

    d. Dans la page **Assistant Exportation de certificat**, choisissez **Suivant**. 

    e. Dans la page **Format du fichier d’exportation**, laissez la valeur par défaut, **X.509 binaire encodé DER (*.cer)**, puis choisissez **Suivant**.  

    f. Dans la page **Fichier à exporter**, choisissez **Parcourir** pour choisir l’emplacement auquel enregistrer le fichier, puis fournissez un nom de fichier. Concrètement, cette opération consiste en fait à nommer le fichier dans lequel le certificat exporté sera enregistré. Choisissez **Suivant** &gt; **Terminer**.

    #### Safari
    
    a. Connectez-vous à la console AAD.

    b. Cliquez sur l’icône en forme de verrou &gt;  **Plus d’informations**.
    
    c. Choisissez **Afficher le certificat** &gt; **Détails**.

    d. Choisissez le certificat, puis **Exporter**.  


> [!IMPORTANT]
> Vérifiez la date d’expiration du certificat, car vous devrez en exporter et en importer un nouveau quand celui-ci arrivera à expiration.

    

2. À partir de la console ISE, importez le certificat Intune (le fichier exporté) dans le magasin **Trusted Certificates** (Certificats approuvés).
3. Dans la console ISE, accédez à **Administration** > **Certificates **(Certificats) > **System Certificates** (Certificats du système).
4. Sélectionnez le certificat ISE, puis choisissez **Export** (Exporter).
5. Dans un éditeur de texte, modifiez le certificat exporté :
 - Supprimez ** -----BEGIN CERTIFICATE-----**.
 - Supprimez ** -----END CERTIFICATE-----**.
 - Vérifiez que tout le texte contient sur une seule ligne.

### Étape 2 : Créer une application pour ISE dans votre client AAD
1. Dans la console Azure Active Directory (AAD), choisissez **Applications** > **Ajouter une application** > **Ajouter une application développée par mon organisation**.
2. Spécifiez un nom et une URL pour l’application. L’URL peut correspondre au site web de votre entreprise.
3. Téléchargez le manifeste d’application (fichier JSON).
4. Modifiez le fichier manifeste JSON. Pour le paramètre **keyCredentials**, fournissez le texte du certificat modifié à l’étape 1.
5. Enregistrez le fichier sans modifier son nom.
6. Fournissez à votre application des autorisations sur Microsoft Graph et l’API Microsoft Intune.
    1. Pour Microsoft Graph, choisissez les éléments suivants :
        - **Autorisations d’application** : Lire des données d’annuaire
        - **Autorisations déléguées** : 
            - Accéder aux données utilisateur à tout moment
          - Connecter les utilisateurs
   2. Pour l’API Microsoft Intune, dans **Autorisations d’application**, choisissez **Get device state and compliance from Intune** (Obtenir l’état et la conformité de l’appareil à partir d’Intune).

7. Choisissez **Points de terminaison** et copiez les valeurs suivantes, que vous utiliserez pour configurer les paramètres ISE :

|Valeur dans le portail d’AAD|Champ correspondant dans le portail ISE|
|-------------------|---------------------------------|
|Point de terminaison de l’API Microsoft Azure AD Graph|Auto Discovery URL (URL de découverte automatique)|
|Point de terminaison de jeton OAuth 2.0|Token Issuing URL (URL émettrice de jeton)|
|Mettre à jour votre code avec votre ID client|ID client|


### Étape 3 : Configurer les paramètres ISE 
2. Dans la console d’administration ISE, fournissez ces valeurs de paramètre : 
  - **Server Type** (Type de serveur) : Mobile Device Manager
  - **Authentication type** (Type d’authentification) : OAuth – Client Credentials (OAuth – Informations d’identification du client)
  - **Auto Discovery** (Découverte automatique) : Yes (Oui)
  - **Auto Discovery URL** (URL de découverte automatique) : entrez la valeur provenant de l’étape 1
  - **Client ID** (ID client) : entrez la valeur provenant de l’étape 1
  - **Token Issuing URL** (URL émettrice de jeton) : entrez la valeur provenant de l’étape 1



## Informations partagées entre votre client Intune et votre serveur Cisco ISE
Ce tableau répertorie les informations partagées entre votre client Intune et votre serveur Cisco ISE pour les appareils qui sont gérés par Intune.

|Propriété|  Description|
|---------------|------------------------------------------------------------|
|complianceState|   Vrai ou faux : chaîne indiquant si l’appareil est conforme.|
|isManaged| Vrai ou faux : indique si le client est géré par Intune.|
|macAddress|Adresse MAC de l’appareil.|
|serialNumber|Numéro de série de l’appareil. Concerne uniquement les appareils iOS.|
|imei|Le numéro IMEI (15 chiffres décimaux : 14 chiffres plus un chiffre de vérification) ou IMEISV (16 chiffres) inclut des informations sur l’origine, le modèle et le numéro de série de l’appareil. La structure du numéro IMEI/VP est définie dans la spécification 3GPP TS 23.003. (Concerne uniquement les appareils dotés de cartes SIM.)|
|udid|Identificateur unique de l’appareil (séquence de 40 lettres et chiffres propre aux appareils iOS)|
|meid|Identificateur d’équipement mobile (nombre global unique identifiant un élément physique de l’équipement de station mobile CDMA). Le format du nombre est défini par le rapport 3GPP2 S. R0048, mais dans la pratique, il peut être vu comme un numéro IMEI avec des chiffres hexadécimaux. Un identificateur MEID occupe 56 bits (14 caractères hexadécimaux). Il se compose de trois champs, dont un code régional de 8 bits, un code fabricant de 24 bits et un numéro de série de 24 bits attribué par le fabricant.| 
|osVersion| Version du système d’exploitation de l’appareil
|de modèle|Modèle de l’appareil
|manufacturer|Fabricant de l’appareil
|azureDeviceId| ID de l’appareil une fois joint à l’espace de travail avec Azure Active Directory. GUID vide pour les appareils qui ne sont pas joints.|
|lastContactTimeUtc|Date et heure du dernier enregistrement de l’appareil auprès du service de gestion Intune. 


## Expérience utilisateur

Quand un utilisateur tente d’accéder à des ressources à l’aide d’un appareil non inscrit, il reçoit une invite d’inscription, comme illustré ci-après :

![Exemple d’invite d’inscription](../media/cisco-ise-user-iphone.png)

Quand l’utilisateur choisit de s’inscrire, il est redirigé vers le processus d’inscription Intune. L’expérience utilisateur de l’inscription pour Intune est décrite dans les rubriques suivantes :

- [Inscrire un appareil Android dans Intune](/intune/end-user/enroll-your-device-in-Intune-android)</br>
- [Inscrire un appareil iOS dans Intune](/intune/end-user/enroll-your-device-in-intune-ios)</br>
- [Inscrire un appareil Mac OS X dans Intune](/intune/end-user/enroll-your-device-in-intune-mac-os-x)</br>
- [Inscrire un appareil Windows dans Intune](/intune/end-user/enroll-your-device-in-intune-windows)</br> 

Vous pouvez également [télécharger un ensemble d’instructions d’inscription](https://gallery.technet.microsoft.com/End-user-Intune-enrollment-55dfd64a) et l’adapter pour vos utilisateurs.


### Voir aussi

[Cisco Identity Services Engine Administrator Guide, Release 2.1 (Guide d’administration de Cisco Identity Services Engine, version 2.1)](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html#task_820C9C2A1A6647E995CA5AAB01E1CDEF)




<!--HONumber=Jun16_HO4-->


