---
title: Configurer les paramètres de proxy pour le connecteur Intune pour Active Directory
description: Explique comment configurer le connecteur Intune pour Active Directory afin qu’il soit utilisable avec des serveurs proxy locaux existants.
keywords: ''
author: master11218
ms.author: tanvira
manager: smantri
ms.date: 4/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tanvira
ms.suite: ems
search.appverid: ''
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 11537902e8306d753d6c3e144e0ac15f90ab3b51
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503279"
---
# <a name="work-with-existing-on-premises-proxy-servers"></a>Utiliser des serveurs proxy locaux existants

Cet article explique comment configurer le connecteur Intune pour Active Directory afin qu’il soit utilisable avec des serveurs proxy sortants. Il s’adresse aux clients dont les environnements réseau comportent des proxys.

Pour plus d’informations sur le fonctionnement des connecteurs, consultez [Présentation des connecteurs de proxy d’application Azure AD](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-connectors).

## <a name="bypass-outbound-proxies"></a>Contourner les proxys sortants

Les connecteurs ont des composants de système d’exploitation sous-jacents qui effectuent des demandes sortantes. Ces composants tentent automatiquement de localiser un serveur proxy sur le réseau à l’aide de WPAD (Web Proxy Auto-Discovery).

Les composants de système d’exploitation tentent de localiser un serveur proxy en effectuant une recherche DNS de wpad.domainsuffix. Si la recherche est résolue dans le système DNS, une requête HTTP est effectuée à l’adresse IP pour wpad.dat. Cette requête devient le script de configuration de proxy dans votre environnement. Le connecteur utilise ce script pour sélectionner un serveur proxy sortant. Toutefois, il est possible que le trafic du connecteur soit bloqué ; dans ce cas, des paramètres de configuration supplémentaires sont nécessaires sur le serveur proxy.

Vous pouvez configurer le connecteur pour qu’il contourne votre proxy local et qu’il utilise ainsi une connexion directe aux services Azure. Nous vous recommandons cette approche, sous réserve que votre stratégie réseau le permette, car vous avez alors une configuration de moins à gérer.

Pour désactiver l’utilisation de proxy sortant pour le connecteur, modifiez le fichier :\Program Files\Microsoft Intune\ODJConnector\ODJConnectorUI\ODJConnectorUI.exe.config, puis ajoutez l’adresse de proxy et le port de proxy dans la section indiquée dans l’exemple de code suivant :

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>  
        <defaultProxy>   
            <proxy proxyaddress="<PROXY ADDRESS HERE>:<PORT HERE>" bypassonlocal="True" usesystemdefault="True"/>   
        </defaultProxy>  
    </system.net>
    <runtime>
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
            <dependentAssembly>
                <assemblyIdentity name="mscorlib" publicKeyToken="b77a5c561934e089" culture="neutral"/>
                <bindingRedirect oldVersion="0.0.0.0-2.0.0.0" newVersion="4.6.0.0" />
            </dependentAssembly>
        </assemblyBinding>
    </runtime>
    <startup> 
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="SignInURL" value="https://portal.manage.microsoft.com/Home/ClientLogon"/>
        <add key="LocationServiceEndpoint" value="RestUserAuthLocationService/RestUserAuthLocationService/ServiceAddresses"/>
    </appSettings>
</configuration>
```

Pour que le connecteur Connector Updater contourne également le proxy, apportez une modification similaire au fichier C:\Program Files\Microsoft Intune\ODJConnector\ODJConnectorSvc\ODJConnectorSvc.exe.config.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>  
        <defaultProxy>   
            <proxy proxyaddress="<PROXY ADDRESS HERE>:<PORT HERE>" bypassonlocal="True" usesystemdefault="True"/>   
        </defaultProxy>  
    </system.net>
    <startup>
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="BaseServiceAddress" value="https://manage.microsoft.com/" />
    </appSettings>
</configuration>
```

Veillez à faire des copies des fichiers d’origine, au cas où vous deviez restaurer les fichiers .config par défaut.

Une fois les fichiers de configuration modifiés, vous devez redémarrer le service Intune Connector. 

1. Ouvrez **services.msc**.
2. Recherchez et sélectionnez le **Service ODJConnector Intune**.
3. Sélectionnez **Redémarrer**.

![Capture d’écran du redémarrage du service](./media/autopilot-hybrid-connector-proxy/service-restart.png)


## <a name="next-steps"></a>Étapes suivantes

[Gérer vos appareils](../remote-actions/device-management.md)