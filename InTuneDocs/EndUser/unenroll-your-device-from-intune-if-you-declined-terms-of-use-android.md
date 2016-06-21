---
# required metadata

title: Annuler l’inscription de votre appareil dans Intune si vous avez refusé les conditions d’utilisation | Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 4278f000-0258-4de5-93a1-195b48e5061e

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: chrisbal
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Annuler l’inscription de votre appareil dans Intune si vous avez refusé les conditions d’utilisation

La meilleure façon de désinscrire votre appareil Android est d’accepter les conditions d’utilisation, de se connecter à l’application Portail d’entreprise, puis d’utiliser [ces instructions](unenroll-your-device-from-intune-android.md) pour le désinscrire. Toutefois, si vous avez refusé les conditions d’utilisation lors de la tentative de connexion à l’application Portail d’entreprise, vous ne pourrez pas vous connecter à l’application Portail d’entreprise à l’avenir. Vous devez donc utiliser ces instructions de résolution pour annuler l’inscription de votre appareil.

Quand vous désinstallez l’application Portail d’entreprise, vous désinscrivez également votre appareil d’Intune, ce qui signifie que votre appareil ne peut plus accéder aux ressources d’entreprise.  Pour plus d’informations sur ce qui se passe lors d’une désinscription, consultez [Que se passe-t-il quand vous désinscrivez votre appareil d’Intune ?](what-happens-if-you-unenroll-your-device-from-intune-android.md).

Avant de pouvoir désinstaller l’application Portail d’entreprise, vous devez accéder au paramètre **Administrateurs de l’appareil** et désactiver **Portail d’entreprise**. Les étapes peuvent être légèrement différentes selon l’appareil Android que vous utilisez.

Pour désinscrire votre appareil d’Intune à partir de l’application Portail d’entreprise :

1.  Accédez à **Paramètres** &gt; **Sécurité &amp;Verrouillage d’écran** &gt; **Administrateurs de l’appareil**.

    Cette étape désinscrit immédiatement votre appareil.

2.  Décochez la case **Portail d’entreprise** ou désactivez-le.

    Vous pouvez désormais désinstaller l’application Portail d’entreprise.

Si vous avez besoin d’aide et si vous ne trouvez pas les coordonnées de votre administrateur informatique, regardez si elles ne sont pas répertoriées sur le [site web du Portail d’entreprise](http://portal.manage.microsoft.com).

### Voir aussi
[Utilisation de votre appareil Android avec Intune](using-your-android-device-with-intune.md)

<!--HONumber=Jun16_HO1-->


