---
title: Créer un profil Wi-Fi avec une clé prépartagée dans Microsoft Intune – Azure | Microsoft Docs
description: Utiliser un profil personnalisé pour créer un profil Wi-Fi avec une clé prépartagée et obtenir un exemple de code XML pour les profils Wi-Fi basé sur Android, Windows et EAP dans Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/28/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c6fd72a6-7dc8-48fc-9df1-db5627a51597
ms.reviewer: karanda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c9b56ba1515608afb6c2a0d151f5412711d49e57
ms.sourcegitcommit: 5ad0ce27a30ee3ef3beefc46d2ee49db6ec0cbe3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2020
ms.locfileid: "76886720"
---
# <a name="use-a-custom-device-profile-to-create-a-wifi-profile-with-a-pre-shared-key-in-intune"></a>Utiliser un profil d’appareil personnalisé pour créer un profil Wi-Fi avec une clé prépartagée dans Intune



Les clés prépartagées (PSK) servent généralement à authentifier les utilisateurs sur les réseaux Wi-Fi ou réseaux locaux sans fil. Avec Intune, vous pouvez créer un profil Wi-Fi à l’aide d’une clé prépartagée. Pour créer le profil, utilisez la fonctionnalité **Profils d’appareil personnalisés** dans Intune. Cet article contient également quelques exemples indiquant comment créer un profil Wi-Fi basé sur EAP.

Cette fonctionnalité prend en charge :

- Administrateur d’appareil Android
- Windows
- Wi-Fi basé sur EAP

> [!IMPORTANT]
> - Le fait d’utiliser une clé prépartagée avec Windows 10 provoque l’affichage d’une erreur de correction dans Intune. Quand cela se produit, le profil Wi-Fi est correctement affecté à l’appareil et fonctionne comme prévu.
> - Si vous exportez un profil Wi-Fi incluant une clé prépartagée, vérifiez que le fichier est protégé. La clé est au format texte brut, vous êtes donc responsable de sa protection.

## <a name="before-you-begin"></a>Avant de commencer

- Il peut s’avérer plus facile de copier le code à partir d’un ordinateur qui se connecte à ce réseau, comme décrit plus loin dans cet article.
- Vous pouvez ajouter plusieurs réseaux et plusieurs clés en ajoutant davantage de paramètres OMA-URI.
- Pour iOS, utilisez l’outil Apple Configurator sur une station Mac pour installer le profil.
- PSK nécessite une chaîne de 64 chiffres hexadécimaux ou une phrase secrète de 8 à 63 caractères ASCII imprimables. Certains caractères, comme l’astérisque (*) ne sont pas pris en charge.

## <a name="create-a-custom-profile"></a>Créer un profil personnalisé

1. Connectez-vous au [Centre d’administration du Gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Sélectionnez **Appareils** > **Profils de configuration** > **Créer un profil**.
3. Entrez les propriétés suivantes :

    - **Nom** : Attribuez un nom descriptif à la stratégie. Nommez vos stratégies afin de pouvoir les identifier facilement ultérieurement. Par exemple, **Paramètres du profil Wi-Fi OMA-URI personnalisés pour les appareils Android** est un bon nom de stratégie.
    - **Description** : Entrez la description du profil. Ce paramètre est facultatif, mais recommandé.
    - **Plateforme** : Choisissez votre plateforme.
    - **Type de profil** : Sélectionnez **Personnalisé**.

4. Dans **Paramètres**, sélectionnez **Ajouter**. Ajoutez un nouveau paramètre OMA-URI avec les propriétés suivantes :

    1. **Nom** : Donnez un nom au paramètre OMA-URI.
    2. **Description** : Entrez une description du paramètre OMA-URI. Ce paramètre est facultatif, mais recommandé.
    3. **OMA-URI** : Entrez l’une des options suivantes :

        - **Pour Android** : `./Vendor/MSFT/WiFi/Profile/SSID/Settings`.
        - **Pour Windows** : `./Vendor/MSFT/WiFi/Profile/SSID/WlanXml`.

        > [!NOTE]
        > Veillez à inclure le point au début.

        Le SSID est l’identificateur SSID pour lequel vous créez la stratégie. Par exemple, si le réseau Wi-Fi s’appelle `Hotspot-1`, entrez `./Vendor/MSFT/WiFi/Profile/Hotspot-1/Settings`.

    4. **Type de données** : Sélectionnez **chaîne**.

    5. **Valeur** : Collez votre code XML. Voir les [exemples](#android-or-windows-wi-fi-profile-example) de cet article. Mettez à jour chaque valeur pour correspondre à vos paramètres réseau. La section Commentaires du code inclut certains pointeurs.

5. Lorsque vous avez terminé, sélectionnez **OK** > **Créer** pour enregistrer vos modifications.

Votre profil s’affiche dans la liste. Maintenant, [affectez-le](../device-profile-assign.md) à vos groupes d’utilisateurs. Cette stratégie peut être attribuée uniquement à des groupes d’utilisateurs.

Lors du prochain enregistrement de chaque appareil, la stratégie est appliquée et un profil Wi-Fi est créé sur l’appareil. L’appareil peut alors se connecter automatiquement au réseau.

## <a name="android-or-windows-wi-fi-profile-example"></a>Exemple de profil Wi-Fi Android ou Windows

L’exemple suivant inclut le code XML pour un profil Wi-Fi Android ou Windows. L’exemple est fourni pour afficher le format approprié et fournir des détails supplémentaires. Ce n’est qu’un exemple et non une configuration recommandée pour votre environnement.

### <a name="what-you-need-to-know"></a>Ce que vous devez savoir

- `<protected>false</protected>` doit être défini sur **false**. La valeur**true** peut amener l’appareil à attendre un mot de passe chiffré et à tenter de le déchiffrer, ce qui risque d’entraîner un échec de connexion.

- `<hex>53534944</hex>` doit être défini sur la valeur hexadécimale de `<name><SSID of wifi profile></name>`. Les appareils Windows 10 peuvent retourner une erreur false `x87D1FDE8 Remediation failed`, mais l’appareil contient encore le profil.

- Le code XML comporte des caractères spéciaux, comme le `&` (esperluette). L’usage de caractères spéciaux peut empêcher le code XML de fonctionner comme prévu. 

### <a name="example"></a>Exemple

``` xml
<!--
<hex>53534944</hex> = The hexadecimal value of <name><SSID of wifi profile></name>
<Name of wifi profile> = Name of profile shown to users. It could be <name>Your Company's Network</name>.
<SSID of wifi profile> = Plain text of SSID. Does not need to be escaped. It could be <name>Your Company's Network</name>.
<nonBroadcast><true/false></nonBroadcast>
<Type of authentication> = Type of authentication used by the network, such as WPA2PSK.
<Type of encryption> = Type of encryption used by the network, such as AES.
<protected>false</protected> do not change this value, as true could cause device to expect an encrypted password and then try to decrypt it, which may result in a failed connection.
<password> = Plain text of the password to connect to the network
-->

<WLANProfile
xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
  <name><Name of wifi profile></name>
  <SSIDConfig>
    <SSID>
      <hex>53534944</hex>
 <name><SSID of wifi profile></name>
    </SSID>
    <nonBroadcast>false</nonBroadcast>
  </SSIDConfig>
  <connectionType>ESS</connectionType>
  <connectionMode>auto</connectionMode>
  <autoSwitch>false</autoSwitch>
  <MSM>
    <security>
      <authEncryption>
        <authentication><Type of authentication></authentication>
        <encryption><Type of encryption></encryption>
        <useOneX>false</useOneX>
      </authEncryption>
      <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>false</protected>
        <keyMaterial>password</keyMaterial>
      </sharedKey>
      <keyIndex>0</keyIndex>
    </security>
  </MSM>
</WLANProfile>
```

### <a name="eap-based-wi-fi-profile-example"></a>Exemple de profil Wi-Fi basé sur EAP
L’exemple suivant inclut le code XML pour un profil Wi-Fi basé sur EAP : L’exemple est fourni pour afficher le format approprié et fournir des détails supplémentaires. Ce n’est qu’un exemple et non une configuration recommandée pour votre environnement.


```xml
    <WLANProfile xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
      <name>testcert</name>
      <SSIDConfig>
        <SSID>
          <hex>7465737463657274</hex>
          <name>testcert</name>
        </SSID>
        <nonBroadcast>true</nonBroadcast>
      </SSIDConfig>
      <connectionType>ESS</connectionType>
      <connectionMode>auto</connectionMode>
      <autoSwitch>false</autoSwitch>
      <MSM>
        <security>
          <authEncryption>
            <authentication>WPA2</authentication>
            <encryption>AES</encryption>
            <useOneX>true</useOneX>
            <FIPSMode     xmlns="http://www.microsoft.com/networking/WLAN/profile/v2">false</FIPSMode>
          </authEncryption>
          <PMKCacheMode>disabled</PMKCacheMode>
          <OneX xmlns="http://www.microsoft.com/networking/OneX/v1">
            <cacheUserData>false</cacheUserData>
            <authMode>user</authMode>
            <EAPConfig>
              <EapHostConfig     xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
                <EapMethod>
                  <Type xmlns="http://www.microsoft.com/provisioning/EapCommon">13</Type>
                  <VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorId>
                  <VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorType>
                  <AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</AuthorId>
                </EapMethod>
                <Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
                  <Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1">
                    <Type>13</Type>
                    <EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1">
                      <CredentialsSource>
                        <CertificateStore>
                          <SimpleCertSelection>true</SimpleCertSelection>
                        </CertificateStore>
                      </CredentialsSource>
                      <ServerValidation>
                        <DisableUserPromptForServerValidation>false</DisableUserPromptForServerValidation>
                        <ServerNames></ServerNames>
                      </ServerValidation>
                      <DifferentUsername>false</DifferentUsername>
                      <PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</PerformServerValidation>
                      <AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</AcceptServerName>
                      <TLSExtensions xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
                        <FilteringInfo xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3">
                          <AllPurposeEnabled>true</AllPurposeEnabled>
                          <CAHashList Enabled="true">
                            <IssuerHash>75 f5 06 9c a4 12 0e 9b db bc a1 d9 9d d0 f0 75 fa 3b b8 78 </IssuerHash>
                          </CAHashList>
                          <EKUMapping>
                            <EKUMap>
                              <EKUName>Client Authentication</EKUName>
                              <EKUOID>1.3.6.1.5.5.7.3.2</EKUOID>
                            </EKUMap>
                          </EKUMapping>
                          <ClientAuthEKUList Enabled="true"/>
                          <AnyPurposeEKUList Enabled="false">
                            <EKUMapInList>
                              <EKUName>Client Authentication</EKUName>
                            </EKUMapInList>
                          </AnyPurposeEKUList>
                        </FilteringInfo>
                      </TLSExtensions>
                    </EapType>
                  </Eap>
                </Config>
              </EapHostConfig>
            </EAPConfig>
          </OneX>
        </security>
      </MSM>
    </WLANProfile>
```

## <a name="create-the-xml-file-from-an-existing-wi-fi-connection"></a>Création du fichier XML à partir d’une connexion Wi-Fi existante

Vous pouvez également créer un du fichier XML à partir d’une connexion Wi-Fi existante. Sur un ordinateur Windows, utilisez les étapes suivantes :

1. Créez un dossier local pour les profils Wi-Fi exportés, comme c:\WiFi.
2. Ouvrez une invite de commande en tant qu’administrateur (cliquez avec le bouton droit et sélectionnez `cmd` > **Exécuter en tant qu’administrateur**).
3. Exécutez `netsh wlan show profiles`. Les noms de tous les profils s’affichent.
4. Exécutez `netsh wlan export profile name="YourProfileName" folder=c:\Wifi`. Cette commande crée un fichier nommé `Wi-Fi-YourProfileName.xml` dans c:\Wifi.

    - Si vous exportez un profil Wi-Fi contenant une clé prépartagée, ajoutez `key=clear` à la commande :
  
        `netsh wlan export profile name="YourProfileName" key=clear folder=c:\Wifi`

        `key=clear` exporte la clé en texte brut, ce qui est nécessaire pour pouvoir utiliser correctement le profil.

Une fois le fichier XML obtenu, copiez et collez la syntaxe XML dans les paramètres OMA-URI > **Type de données**. La section [Créer un profil personnalisé](#create-a-custom-profile) (dans cet article) répertorie les étapes.

> [!TIP]
> `\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{guid}` inclut également tous les profils au format XML.

## <a name="best-practices"></a>meilleures pratiques recommandées.

- Avant de déployer un profil Wi-Fi avec une clé prépartagée, vérifiez que l’appareil peut se connecter directement au point de terminaison.

- Lors de la rotation des clés (mots de passe ou phrases secrètes), prévoyez un temps d’arrêt et planifiez vos déploiements. Il est préférable d’envoyer les nouveaux profils Wi-Fi en dehors des horaires de travail. Avertissez également les utilisateurs que la connectivité peut être affectée.

- Pour une transition en douceur, vérifiez que l’appareil de l’utilisateur final a une autre connexion à Internet. Par exemple, l’utilisateur final peut revenir au Wi-Fi invité (ou un autre réseau Wi-Fi), ou disposer d’une connectivité cellulaire pour communiquer avec Intune. Cette connexion supplémentaire permet à l’utilisateur de recevoir des mises à jour de stratégies quand le profil Wi-Fi d’entreprise est mis à jour sur l’appareil.

## <a name="next-steps"></a>Étapes suivantes

[Affectez le profil](device-profile-assign.md) et [effectuez un monitorage](device-profile-monitor.md) de son état.
