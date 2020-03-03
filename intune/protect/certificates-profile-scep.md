---
title: Utiliser des profils de certificat SCEP avec Microsoft Intune - Azure | Microsoft Docs
description: Créez et attribuez des profils de certificat Protocole d’inscription de certificats simple (SCEP) avec Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3cd153a4c602ba49a5b5135d1d6cb32a61f2668d
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576515"
---
# <a name="create-and-assign-scep-certificate-profiles-in-intune"></a>Créer et attribuer des profils de certificat SCEP dans Intune

Dès que vous avez [configuré votre infrastructure](certificates-scep-configure.md) pour prendre en charge les certificats Protocole d’inscription de certificats simple (SCEP), vous pouvez créer des profils de certificat SCEP et les attribuer aux utilisateurs et aux appareils dans Intune.

> [!IMPORTANT]  
> Avant de créer des profils de certificat SCEP, les appareils qui vont les utiliser doivent approuver votre autorité de certification racine de confiance. Utilisez un *profil de certificat approuvé* dans Intune afin de provisionner le certificat d’autorité de certification racine de confiance pour les utilisateurs et les appareils. Pour plus d’informations sur le profil de certificat approuvé, consultez [Exporter le certificat d’autorité de certification racine de confiance](certificates-configure.md#export-the-trusted-root-ca-certificate) et [Créer des profils de certificat approuvés](certificates-configure.md#create-trusted-certificate-profiles) dans *Utiliser des certificats pour l’authentification dans Intune*.


## <a name="create-a-scep-certificate-profile"></a>Créer un profil de certificat SCEP

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Sélectionnez **Appareils** > **Profil de configuration** > **Créer un profil**.

3. Entrez les propriétés suivantes :

4. Entrez un **Nom** et une **Description** pour le profil de certificat SCEP.

5. Dans la liste déroulante **Plateforme**, sélectionnez la [plateforme d’appareil prise en charge](certificates-configure.md#supported-platforms-and-certificate-profiles) pour ce certificat SCEP.

6. Dans la liste déroulante **Type de profil**, sélectionnez **Certificat SCEP**.  

   Pour la plateforme **Android Entreprise**, le *Type de profil* est divisé en deux catégories, à savoir *Propriétaire d’appareil uniquement* et *Profil professionnel uniquement*. Veillez à sélectionner le profil de certificat SCEP correct pour les appareils que vous gérez.  

   Les profils de certificat SCEP pour le profil *Propriétaire d’appareil uniquement* ont les limitations suivantes :

   1. Sous Surveillance, le rapport de certificat n’est pas disponible pour les profils de certificat SCEP de propriétaires d’appareils.

   2. Vous ne pouvez pas utiliser Intune pour révoquer des certificats provisionnés par les profils de certificat SCEP pour les propriétaires d’appareils. Vous pouvez gérer la révocation via un processus externe ou directement avec l’autorité de certification. 

   4. Pour les appareils Android Enterprise dédiés, les profils de certificat SCEP sont pris en charge pour l’authentification et la configuration du réseau Wi-Fi uniquement.  Les profils de certificat SCEP sur les appareils Android Enterprise dédiés ne sont pas pris en charge pour l’authentification d’application ou VPN.   

   
7. Sélectionnez **Paramètres**, puis effectuez les configurations suivantes :

   - **Type de certificat** :

     *(S’applique à :  Android, Android Entreprise, iOS/iPadOS, macOS, Windows 8.1 et ultérieur, et Windows 10 et ultérieur.)*

     Sélectionnez un type en fonction de votre utilisation du profil de certificat :

     - **Utilisateur** : L’objet et le SAN d’un certificat *Utilisateur* peuvent contenir des attributs d’utilisateur et d’appareil.  
     - **Appareil** :  L’objet et le SAN d’un certificat de type *Appareil* peuvent contenir uniquement des attributs d’appareil.

       Utilisez **Appareil** dans les scénarios de type appareils sans utilisateur (kiosques) ou pour les appareils Windows. Sur les appareils Windows, le certificat est placé dans le magasin de certificats de l’ordinateur local.

   - **Format du nom de l’objet** :

     sélectionnez la manière dont Intune crée automatiquement le nom de l'objet dans la demande de certificat. Les options de format du nom de l’objet dépendent du type de certificat que vous sélectionnez, **Utilisateur** ou **Appareil**.

     > [!NOTE]
     > Il existe un [problème connu](#avoid-certificate-signing-requests-with-escaped-special-characters) lié à l’utilisation de SCEP pour obtenir des certificats lorsque le nom d’objet dans la demande de signature de certificat (CSR) résultante inclut l’un des caractères suivants comme caractère d’échappement (suivi d’une barre oblique inverse \\) :
     > - \+
     > - ;
     > - ,
     > - =

     - **Type de certificat Utilisateur**

       Les options de *Format du nom de l’objet* sont notamment :

       - **Non configuré**
       - **Nom commun**
       - **Nom commun (adresse e-mail incluse)**
       - **Nom commun comme adresse e-mail**
       - **IMEI (International Mobile Equipment Identity)**
       - **Numéro de série**
       - **Personnalisé** : quand vous sélectionnez cette option, une zone de texte **Personnalisé** s’affiche également. Utilisez ce champ pour entrer un format de nom d’objet personnalisé, avec notamment des variables. Un format personnalisé prend en charge deux variables : **Nom commun (CN)** et **E-mail (E)**. **Nom courant (cn)** peut être défini sur une des variables suivantes :

         - **CN={{UserName}}**: Le nom d’utilisateur principal, par exemple, janedoe@contoso.com.
         - **CN={{AAD_Device_ID}}**: ID attribué quand vous inscrivez un appareil dans Azure Active Directory (AD). Cet ID est généralement utilisé pour l’authentification auprès d’Azure AD.
         - **CN={{SERIALNUMBER}}** : Numéro de série unique (SN) généralement utilisé par le fabricant pour identifier un appareil.
         - **CN={{IMEINumber}}** : Numéro IMEI (International Mobile Equipment Identity) unique utilisé pour identifier un téléphone mobile.
         - **CN={{OnPrem_Distinguished_Name}}** : Séquence de noms uniques relatifs séparés par une virgule, par exemple, *CN=Jane Doe,OU=UserAccounts,DC=Corp,DC=contoso,DC=com*.

           Pour utiliser la variable *{{OnPrem_Distinguished_Name}}*, synchronisez l’attribut utilisateur *onpremisesdistinguishedname* à l’aide d’[Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) sur votre Azure AD.

         - **CN={{onPremisesSamAccountName}}** : Les administrateurs peuvent synchroniser l’attribut samAccountName d’Active Directory sur Azure AD à l’aide d’Azure AD Connect dans un attribut appelé *onPremisesSamAccountName*. Intune peut remplacer cette variable dans le cadre d’une demande d’émission de certificat dans l’objet d’un certificat. L’attribut samAccountName est le nom de connexion de l’utilisateur utilisé pour prendre en charge les clients et serveurs avec une version antérieure de Windows (antérieure à Windows 2000). Le format du nom de connexion de l’utilisateur est : *DomainName\testUser* ou simplement *testUser*.

            Pour utiliser la variable *{{onPremisesSamAccountName}}*, synchronisez l’attribut utilisateur *onPremisesSamAccountName* à l’aide d’[Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) sur votre Azure AD.

         En combinant une ou plusieurs de ces variables et chaînes statiques, vous pouvez créer un format de nom d’objet personnalisé tel que :  
         - **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**

         Cet exemple comprend un format de nom d’objet qui utilise les variables CN et E ainsi que des chaînes pour les valeurs Unité d’organisation, Organisation, Emplacement, Région et Pays. La page [CertStrToName function](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) (Fonction CertStrToName) illustre cette fonction et ses chaînes prises en charge.

      - **Type de certificat Appareil**

        Les options de format du nom de l’objet sont notamment les variables suivantes :

        - **{{AAD_Device_ID}}** or **{{AzureADDeviceId}}** – chaque variable peut être utilisée pour identifier un appareil par son ID Azure AD.
        - **{{Device_Serial}}**
        - **{{Device_IMEI}}**
        - **{{SerialNumber}}**
        - **{{IMEINumber}}**
        - **{{WiFiMacAddress}}**
        - **{{IMEI}}**
        - **{{DeviceName}}**
        - **{{FullyQualifiedDomainName}}***(Applicable uniquement aux appareils Windows et joints à un domaine)*
        - **{{MEID}}**

        Vous pouvez spécifier ces variables, suivies du texte de la variable, dans la zone de texte. Par exemple, le nom commun d’un appareil nommé *Device1* peut être ajouté sous la forme **CN={{DeviceName}}Device1**.

        > [!IMPORTANT]
        > - Quand vous spécifiez une variable, mettez le nom de la variable entre accolades { }, comme indiqué dans l’exemple, pour éviter une erreur.  
        > - Les propriétés de l’appareil utilisées dans l’*objet* ou le *SAN* d’un certificat d’appareil, par exemple, **IMEI**, **SerialNumber** et **FullyQualifiedDomainName**, sont des propriétés qui peuvent être usurpées par quiconque a accès à l’appareil.
        > - Un appareil doit prendre en charge toutes les variables spécifiées dans un profil de certificat pour que ce profil s’installe sur cet appareil.  Par exemple, si **{{IMEI}}** est utilisé dans le nom d’objet d’un profil SCEP et correspond à un appareil qui n’a pas de numéro IMEI, l’installation du profil échoue.

   - **Autre nom de l’objet** : Sélectionnez la manière dont Intune crée automatiquement l’autre nom de l’objet (SAN) dans la demande de certificat. Les options de SAN dépendent du type de certificat que vous sélectionnez, **Utilisateur** ou **Appareil**.

      - **Type de certificat Utilisateur**

        Sélectionnez l’un des attributs disponibles :

        - **Adresse de messagerie**
        - **Nom d’utilisateur principal (UPN)**

        Par exemple, le type de certificat utilisateur peut avoir le nom d’utilisateur principal (UPN) dans l’autre nom de l’objet. Si un certificat client est utilisé pour l’authentification auprès d’un serveur de stratégie réseau, l’autre nom de l’objet doit être défini sur le nom d’utilisateur principal.

      - **Type de certificat Appareil**

        Utilisez la liste déroulante **Attribut** et sélectionnez un attribut,attribuez une **Valeur**, puis **Ajoutez**-la au profil de certificat. Vous pouvez ajouter plusieurs valeurs en sélectionnant des attributs supplémentaires.

        Les attributs disponibles sont notamment :

        - **Adresse de messagerie**
        - **Nom d’utilisateur principal (UPN)**
        - **DNS**

        Avec le type de certificat *Appareil*, vous pouvez utiliser les variables de certificat d’appareil suivantes pour la valeur :

        - **{{AAD_Device_ID}}** or **{{AzureADDeviceId}}** – chaque variable peut être utilisée pour identifier un appareil par son ID Azure AD.
        - **{{Device_Serial}}**
        - **{{Device_IMEI}}**
        - **{{SerialNumber}}**
        - **{{IMEINumber}}**
        - **{{WiFiMacAddress}}**
        - **{{IMEI}}**
        - **{{DeviceName}}**
        - **{{FullyQualifiedDomainName}}**
        - **{{MEID}}**

        Pour spécifier la valeur d’un attribut, ajoutez le nom de la variable entre accolades, suivi du texte de cette variable. Par exemple, la valeur de l’attribut DNS peut inclure **{{AzureADDeviceId}}.domain.com** où *.domain.com* est le texte. Pour un utilisateur nommé *User1*, une adresse e-mail peut apparaître sous la forme {{FullyQualifiedDomainName}}User1@Contoso.com.

        > [!IMPORTANT]
        > - Quand vous utilisez une variable de certificat d’appareil, placez le nom de la variable entre accolades { }.
        > - N’utilisez pas d’accolades **{ }**, de symboles de barre verticale **|** ni de points-virgules **;** dans le texte qui suit la variable.
        > - Les propriétés de l’appareil utilisées dans l’*objet* ou le *SAN* d’un certificat d’appareil, par exemple, **IMEI**, **SerialNumber** et **FullyQualifiedDomainName**, sont des propriétés qui peuvent être usurpées par quiconque a accès à l’appareil.
        > - Un appareil doit prendre en charge toutes les variables spécifiées dans un profil de certificat pour que ce profil s’installe sur cet appareil.  Par exemple, si **{{IMEI}}** est utilisé dans le SAN d’un profil SCEP et correspond à un appareil qui n’a pas de numéro IMEI, l’installation du profil échoue.

   - **Période de validité du certificat** :

     Vous pouvez entrer une valeur inférieure à la période de validité du modèle de certificat, mais pas une valeur supérieure. Si vous avez configuré le modèle de certificat pour [prendre en charge une valeur personnalisée pouvant être définie dans la console Intune](certificates-scep-configure.md#modify-the-validity-period-of-the-certificate-template), utilisez ce paramètre pour spécifier la durée restante avant expiration du certificat.

     Par exemple, si la période de validité du certificat dans le modèle de certificat est de 2 ans, vous pouvez entrer une valeur de 1 an, mais pas une valeur de 5 ans. La valeur doit également être inférieure à la période de validité restante du certificat de l’autorité de certification émettrice.

   - **Fournisseur de stockage de clés (KSP)**  :

     *(S’applique à :  Windows 8.1 et versions ultérieures, et Windows 10 et versions ultérieures)*

     Spécifiez l’emplacement de stockage de la clé du certificat. Choisissez l’une des valeurs suivantes :

     - **Inscrire auprès du fournisseur de stockage de clés (KSP) du module de plateforme sécurisée (TPM) s’il est présent ; sinon, inscrire auprès du fournisseur de stockage de clés du logiciel**
     - **Inscrire auprès du fournisseur de stockage de clés (KSP) du module de plateforme sécurisée (TPM), sinon mettre en échec**
     - **Inscrire auprès de Passport, sinon mettre en échec (Windows 10 et versions ultérieures)**
     - **Inscrire auprès du fournisseur de stockage de clés du logiciel**

   - **Utilisation de la clé** :

     Spécifiez les options d’utilisation de la clé pour le certificat :

     - **Signature numérique** : Autorisez l’échange de clé uniquement quand une signature numérique protège la clé.
     - **Chiffrage de clés** : Autorisez l’échange de clé uniquement quand la clé est chiffrée.

   - **Taille de clé (bits)**  :

     Sélectionnez le nombre de bits contenus dans la clé.

   - **Algorithme de hachage** :

     *(S’applique à Android, Android Entreprise, Windows Phone 8.1, Windows 8.1 et versions ultérieures, et Windows 10 et versions ultérieures)*

     Vous avez le choix entre les types d'algorithmes de hachage disponibles avec ce certificat. Permet de sélectionner le niveau le plus élevé de sécurité pris en charge par les appareils se connectant.

   - **Certificat racine** :

     Sélectionnez le *profil de certificat approuvé* que vous avez précédemment configuré et attribué aux utilisateurs et appareils applicables pour ce profil de certificat SCEP. Le profil de certificat approuvé est utilisé pour provisionner le certificat d’autorité de certification racine de confiance pour des utilisateurs et des appareils. Pour plus d’informations sur le profil de certificat approuvé, consultez [Exporter votre certificat d’autorité de certification racine de confiance](certificates-configure.md#export-the-trusted-root-ca-certificate) et [Créer des profils de certificat approuvés](certificates-configure.md#create-trusted-certificate-profiles) dans *Utiliser des certificats pour l’authentification dans Intune*. Si vous avez une autorité de certification racine et une autorité de certification émettrice, sélectionnez le profil Certificat racine approuvé associé à l’autorité de certification émettrice.

   - **Utilisation améliorée de la clé** :

     Ajoutez des valeurs pour le rôle prévu du certificat. Dans la plupart des cas, le certificat demande une *authentification client* pour que l’utilisateur ou l’appareil puisse être authentifié sur un serveur. Vous pouvez ajouter des utilisations de clé supplémentaires selon les besoins.

   - **Seuil de renouvellement (%)**  :

     entrez le pourcentage de durée de vie restante du certificat avant que l'appareil ne demande le renouvellement du certificat. Par exemple, si vous entrez la valeur 20, le renouvellement du certificat est tenté quand le certificat arrive à 80 % d’expiration. Les tentatives de renouvellement se poursuivent jusqu’à ce que le renouvellement réussisse. Le renouvellement génère un nouveau certificat, lui-même entraînant la création d’une nouvelle paire de clés publique/privée.

   - **URL du serveur SCEP** :

     entrez une ou plusieurs URL pour les serveurs NDES qui délivrent les certificats par le biais de SCEP. Par exemple, entrez une URL de type *https://ndes.contoso.com/certsrv/mscep/mscep.dll*. Vous pouvez ajouter des URL SCEP supplémentaires pour l’équilibrage de charge selon vos besoins, car les URL sont envoyées de manière aléatoire à l’appareil avec le profil. Si l’un des serveurs SCEP n’est pas disponible, la demande SCEP échoue et la demande de certificat peut être effectuée sur le même serveur non disponible lors d’enregistrements ultérieurs de l’appareil.

8. Sélectionnez **OK**, puis **Créer**. Le profil est créé et apparaît dans la liste *Configuration de l’appareil - Profils*.

### <a name="avoid-certificate-signing-requests-with-escaped-special-characters"></a>Éviter les demandes de signature de certificat avec des caractères spéciaux placés dans une séquence d’échappement

Il existe un problème connu pour les demandes de certificat SCEP et PKCS qui incluent un nom d’objet (CN) avec un ou plusieurs des caractères spéciaux suivants comme caractère d’échappement. Les noms d’objet qui incluent l’un des caractères spéciaux en tant que caractère d’échappement se produisent dans un CSR avec un nom d’objet incorrect. Un nom d’objet incorrect entraîne l’échec de validation de la stimulation SCEP Intune et aucun certificat n’est émis.

Les caractères spéciaux ont les suivants :
- \+
- ,
- ;
- =

Lorsque le nom de votre objet contient un des caractères spéciaux, utilisez l’une des options suivantes pour contourner cette limitation :

- Encapsulez la valeur CN qui contient le caractère spécial avec des guillemets.  
- Supprimez le caractère spécial de la valeur CN.

**Par exemple**, vous avez un nom d’objet qui apparaît en tant qu’*utilisateur de test (TestCompany, LLC)*.  Un CSR qui inclut un CN avec une virgule entre *TestCompany* et *LLC* présente un problème.  Le problème peut être évité en plaçant des guillemets autour de la totalité du CN ou en supprimant la virgule entre *TestCompany* et *LLC* :

- **Ajouter des guillemets** : *CN =*« Utilisateur de test (TestCompany, LLC) » OU=UserAccounts,DC=corp,DC=contoso,DC=com*
- **Supprimez la virgule** : *CN =Utilisateur de test (TestCompany, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com*

 Toutefois, toute tentative d’échappement de la virgule à l’aide d’un caractère de barre oblique inverse échoue et génère une erreur dans les journaux CRP :
 
- **Virgule d’échappement** : *CN =Utilisateur de test (TestCompany\\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com*

L’erreur est semblable à la suivante :

```
Subject Name in CSR CN="Test User (TESTCOMPANY\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com" and challenge CN=Test User (TESTCOMPANY\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com do not match  

  Exception: System.ArgumentException: Subject Name in CSR and challenge do not match

   at Microsoft.ConfigurationManager.CertRegPoint.ChallengeValidation.ValidationPhase3(PKCSDecodedObject pkcsObj, CertEnrollChallenge challenge, String templateName, Int32 skipSANCheck)

Exception:    at Microsoft.ConfigurationManager.CertRegPoint.ChallengeValidation.ValidationPhase3(PKCSDecodedObject pkcsObj, CertEnrollChallenge challenge, String templateName, Int32 skipSANCheck)

   at Microsoft.ConfigurationManager.CertRegPoint.Controllers.CertificateController.VerifyRequest(VerifyChallengeParams value
```

## <a name="assign-the-certificate-profile"></a>Affecter le profil de certificat

Attribuez des profils de certificat SCEP de la même façon que vous [déployez des profils d’appareil](../configuration/device-profile-assign.md) dans d’autres circonstances. Toutefois, tenez compte des points suivants avant de continuer :

- Quand vous attribuez des profils de certificat SCEP aux groupes, le fichier du certificat d’autorité de certification racine de confiance (comme spécifié dans le *profil de certificat approuvé*) est installé sur l’appareil. L’appareil utilise le profil de certificat SCEP pour créer une demande de certificat pour ce certificat d’autorité de certification racine de confiance.

- Le profil de certificat SCEP s’installe uniquement sur les appareils qui exécutent la plateforme que vous avez spécifiée à la création du profil de certificat.

- Vous pouvez affecter des profils de certificat sur des regroupements d’utilisateurs ou d’appareils.

- Pour publier un certificat sur un appareil rapidement après l’inscription de l’appareil, affectez le profil de certificat à un groupe d’utilisateurs plutôt qu’à un groupe d’appareils. Si vous l’affectez à un groupe d’appareils, une inscription complète des appareils est préalablement nécessaire pour qu’ils puissent recevoir des stratégies.

- Si vous utilisez la cogestion pour Intune et Configuration Manager, dans Configuration Manager [définissez le curseur de la charge de travail](https://docs.microsoft.com/configmgr/comanage/how-to-switch-workloads) pour la stratégie d’accès aux ressources sur **Intune** ou sur **Pilote Intune**. Ces paramètres permettent aux clients Windows 10 de démarrer le processus de demande de certificat.

- Même si vous créez et attribuez le profil de certificat approuvé et le profil de certificat SCEP séparément, les deux doivent être attribués. Si les deux ne sont pas installés sur un appareil, la stratégie de certificat SCEP échoue. Veillez à ce que tous les profils de certificat racine approuvé soient également déployés sur les mêmes groupes que le profil SCEP.

> [!NOTE]
> Sur les appareils iOS/iPadOS, quand un profil de certificat SCEP est associé à un profil supplémentaire, comme un profil Wi-Fi ou VPN, l’appareil reçoit un certificat pour chacun de ces profils supplémentaires. De cette façon, l’appareil iOS/iPadOS reçoit plusieurs certificats délivrés par la requête de certificat SCEP.  Si vous voulez un seul certificat, vous devez utiliser des certificats PKCS au lieu de certificats SCEP.  La différence entre les certificats PKCS et SCEP réside dans la façon dont ils sont distribués aux appareils.

## <a name="next-steps"></a>Étapes suivantes

[Affecter des profils](../configuration/device-profile-assign.md)

[Résolution des problèmes de déploiement des profils de certificats SCEP](../protect/troubleshoot-scep-certificate-profiles.md)