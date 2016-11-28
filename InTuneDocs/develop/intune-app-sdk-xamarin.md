---
title: "Composant Xamarin du SDK d’application Microsoft Intune | Microsoft Intune"
description: 
keywords: sdk, Xamarin, intune
author: oydang
manager: karthikaraman
ms.author: oydang
ms.date: 11/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: karthikaraman
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ca4623db80d711f3543b6d688fb1bb1ef228c62c
ms.openlocfilehash: e2d43fff8772046fe7426b267e39d53b278d4e5c


---

# <a name="microsoft-intune-app-sdk-xamarin-component"></a>Composant Xamarin du SDK d’application Microsoft Intune

## <a name="overview"></a>Vue d'ensemble
Le [composant Xamarin du SDK d’application Intune](https://components.xamarin.com/view/microsoft.intune.mam) permet d’activer les [fonctionnalités de gestion des applications mobiles Intune](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) dans les applications Android et iOS développées avec Xamarin. Le composant permet aux développeurs de générer facilement des fonctionnalités de restriction d’application et de protection des données dans leur application Xamarin.

Comme vous pourrez le constater, il est possible d’activer des fonctionnalités du SDK sans modifier le comportement de votre application. Une fois que vous avez créé le composant dans votre application mobile iOS ou Android, l’administrateur informatique est en mesure de déployer la stratégie via Microsoft Intune en prenant en charge un ensemble de fonctionnalités qui activent la protection des données.

## <a name="supported-scenarios"></a>Scénarios pris en charge

### <a name="platforms"></a>Plateformes
* Android
* iOS


### <a name="emm-scenarios"></a>Scénarios de gestion de la mobilité d’entreprise

* GAM Intune sur des appareils inscrits à la MDM Intune
* GAM Intune sur des appareils inscrits à une gestion de la mobilité d’entreprise tierce
* GAM Intune sur des appareils non inscrits et non gérés

Les applications Xamarin développées avec le composant Xamarin du SDK d’application Intune peuvent maintenant recevoir des stratégies de gestion des applications mobiles (GAM) sur des appareils inscrits et non inscrits à la gestion des appareils mobiles (MDM) Intune.

## <a name="prerequisites"></a>Conditions préalables

* **[Android uniquement]** La dernière application Portail d’entreprise Microsoft Intune doit toujours être installée sur l’appareil.

## <a name="get-started"></a>Prise en main

1.  Téléchargez **Xamarin-component.exe** [ici](https://components.xamarin.com/submit/xpkg) et extrayez-le.

2. Lisez les [termes du contrat de licence](https://components.xamarin.com/license/microsoft.intune.mam) du composant Xamarin de la GAM Microsoft Intune.

3.  Téléchargez le dossier Composant Xamarin du SDK d’application Intune depuis [GitHub](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) ou [Xamarin](https://components.xamarin.com/license/microsoft.intune.mam) et extrayez-le. Les deux fichiers téléchargés aux étapes 1 et 2 doivent être dans le même niveau de répertoire.

4.  Dans la ligne de commande, exécutez `Xamain.Component.exe install <.xam> file` comme administrateur.

5.  Dans Visual Studio, cliquez avec le bouton droit sur **composants** dans votre projet Xamarin créé précédemment.

6.  Sélectionnez **Modifier les composants** et ajoutez le composant SDK d’application Intune que vous avez téléchargé localement sur votre ordinateur.



## <a name="enabling-intune-mam-in-your-ios-mobile-app"></a>Activation de la GAM Intune dans votre application mobile iOS
1.  Pour initialiser le SDK d’application Intune, vous devez appeler une API dans la classe `AppDelegate.cs`. Exemple :

      ```csharp
      public override bool FinishedLaunching (UIApplication application, NSDictionary launchOptions)
      {
            Console.WriteLine ("Is Managed: {0}", IntuneMAMPolicyManager.Instance.PrimaryUser != null);
            return true;
      }

      ```

2.  Maintenant que le composant est ajouté et initialisé, vous pouvez suivre les étapes générales requises pour intégrer le SDK d’application à une application mobile iOS. Vous trouverez la documentation complète pour l’activation des applications natives iOS dans le [Guide du SDK d’application Intune pour les développeurs iOS](intune-app-sdk-ios).
3. **Important** : Il existe plusieurs modifications propres aux applications iOS basées sur Xamarin. Par exemple, quand vous activez des groupes de trousseaux, vous devez ajouter le code suivant pour inclure l’exemple d’application Xamarin que nous avons inclus dans le composant. Voici un exemple des groupes requis dans vos groupes de trousseaux d’accès :

      ```xml
      <?xml version="1.0" encoding="UTF-8"?>
      <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
      <plist version="1.0">
            <dict>
                  <key>keychain-access-groups</key>
                  <array>
                        <string>$(AppIdentifierPrefix)com.xamarin.microsoftintunesample</string>
                        <string>$(AppIdentifierPrefix)com.xamarin.microsoftintunesample.intunemam</string>
                        <string>$(AppIdentifierPrefix)com.microsoft.intune.mam</string>
                        <string>$(AppIdentifierPrefix)com.microsoft.adalcache</string>
                  </array>
            </dict>
      </plist>
      ```

Vous avez terminé les étapes nécessaires pour générer le composant dans votre application iOS basée sur Xamarin. Si vous utilisez Xcode pour générer votre projet, vous pouvez utiliser `Intune App SDK Settings.bundle`. Ainsi, vous pouvez activer et désactiver les paramètres de stratégie Intune quand vous générez votre projet à des fins de test et de débogage. Pour tirer parti de cet ensemble d’applications, suivez les étapes décrites dans le [Guide du SDK d’application Intune pour les développeurs iOS](intune-app-sdk-ios) et lisez la section sur le [débogage dans Xcode](intune-app-sdk-ios#debug-information).

## <a name="enabling-mam-in-your-android-mobile-app"></a>Activation de la GAM dans votre application mobile Android
Pour les applications Android basées sur Xamarin qui n’utilisent pas un framework d’interface utilisateur, vous devez lire et suivre le [guide du SDK d’application Intune pour les développeurs Android]. Pour votre application Android basée sur Xamarin, vous devez remplacer la classe, les méthodes et les activités par leurs équivalents GAM selon le [tableau](intune-app-sdk-android#replace-classes-methods-and-activities-with-their-mam-equivalent-required) inclus dans le guide. Si votre application ne définit pas de classe `android.app.Application`, vous devrez en créer une et vérifier que vous héritez de `MAMApplication`.

Pour les formulaires Xamarin et d’autres framework d’interface utilisateur, nous avons fourni un outil appelé `MAM.Remapper`. L’outil exécutera le remplacement de la classe pour vous. Toutefois, vous devrez effectuer les étapes suivantes :

1.  Ajoutez une référence au package nuget ` Microsoft.Intune.MAM.Remapper.Tasks` version 0.1.0.0 ou supérieure.

2.  Ajoutez la ligne suivante à votre csproj Android :
  ```xml
  <Import
  Project="$(NugetPack)\\Microsoft.Intune.MAM.Remapper.Tasks.0.1.X.X\\build\\MonoAndroid10\\Microsoft.Intune.MAM.Remapper.targets" />
  ```

3.  Affectez à l’action de génération du fichier `remapping-config.json` la valeur **RemappingConfigFile**. Le fichier `remapping-config.json` inclus fonctionne uniquement avec Xamarin.Forms. Pour les autres framework d’interface utilisateur, consultez le fichier Lisez-moi inclus dans le package nuget Remapper.

## <a name="test-your-app"></a>Tester votre application

Vous avez terminé les étapes élémentaires de la génération du composant dans votre application. Maintenant, vous pouvez suivre les étapes incluses dans l’exemple d’application Android. Nous avons fourni deux exemples, un pour Xamarin.Forms et un autre pour Android.



<!--HONumber=Nov16_HO3-->


