---
title: Comprendre l’expérience d’inscription d’un appareil iOS
titlesuffix: Microsoft Intune
description: Découvrez l’expérience d’inscription en effectuant le processus d’inscription complet d’un appareil iOS.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2017
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b595848d-c451-43ab-812d-b22e0170fb7a
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 376d00a03feb78b4e66b3f8a4ed15567d3bc7976
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57230276"
---
# <a name="understand-the-users-experience-enrolling-an-ios-device"></a>Comprendre l’expérience d’inscription d’un appareil iOS pour l’utilisateur

Microsoft Intune vous permet de donner à votre personnel des appareils mobiles tout en protégeant vos données d’entreprise. Étant donné que vos utilisateurs finaux interagiront avec Intune sur leurs appareils plutôt que dans la console d’administration, vous devez vous familiariser avec l’expérience d’inscription. Ainsi, vous pouvez combiner des stratégies de conformité bien conçues avec votre expérience afin de montrer une empathie envers vos utilisateurs. Cela est particulièrement important car les utilisateurs sauront exactement les informations que vous, en tant qu’administrateur, pouvez voir :

| Ce qu’il ne peut pas voir | Ce qu’il peut voir |
|---|---|
| Historique des appels et de navigation | Modèle |
| Localisation | Numéro de série |
| E-mail personnel | Version du système d'exploitation |
| SMS | Noms des applications |
| Contacts | Propriétaire |
| Mots de passe de vos comptes personnels | Nom de l'appareil |
| Événements de calendrier | Fabricant (pour les appareils non-Apple) |
| Photos, notamment celles qui se trouvent dans l’application de photos ou sur la pellicule | Numéro de téléphone (pour les appareils de travail, le nombre entier. Pour les appareils personnels, uniquement les quatre derniers chiffres.) |

## <a name="how-do-i-enroll-a-device"></a>Comment inscrire un appareil ?

L’inscription d’un appareil est la première expérience que de nombreux utilisateurs finaux auront avec l’accès aux ressources d’entreprise. [Bien comprendre cette expérience](end-user-educate.md) peut contribuer à la rendre plus agréable.

1. Ouvrez l’**App Store** et recherchez le **Portail d’entreprise Intune**.
2. Téléchargez l’application **Portail d’entreprise Microsoft Intune**.
3. Ouvrez l’application **Portail d’entreprise**, entrez l’e-mail et le mot de passe de votre utilisateur test, puis appuyez sur **Se connecter**.
4. Mettez à jour le mot de passe temporaire.
5. Dans la page **Configuration de l’accès à l’entreprise**, appuyez sur **Inscription de l’appareil**.
6. Dans la page **Pourquoi inscrire votre appareil ?**, lisez ce qu’un utilisateur peut faire quand il inscrit son appareil, puis appuyez sur **Continuer**.
7. Consultez le descriptif de l’accès accordé à un utilisateur quand il s’inscrit, puis appuyez sur **Continuer**.
8. Passez en revue ce que les administrateurs informatiques peuvent et ne peuvent pas voir sur un appareil, puis appuyez sur **Continuer**.
9. Dans la page **Et ensuite ?**, découvrez ce qui se passe lors de l’inscription, puis appuyez sur **Inscrire**.
10. Dans la page **Installer un profil**, appuyez sur **Installer**, puis entrez le code secret de l’appareil si vous y êtes invité.
11. Appuyez sur **Installer**.
12. Appuyez à nouveau sur **Installer** pour indiquer que vous avez lu l’avertissement.
13. Dans la fenêtre contextuelle **Avertissement**, appuyez sur **Confiance**.
14. Quand l’écran change et indique que l’installation du profil est terminée, appuyez sur **Terminé**.
15. Un message « Inscription de l’appareil » s’affiche à l’écran, puis montre que l’appareil a été correctement inscrit. Une fenêtre contextuelle s’affiche et vous invite à ouvrir la page dans le portail d’entreprise. Appuyez sur **Ouvrir**.
16. Vous revenez à l’écran **Configuration de l’accès à l’entreprise**. Si aucune stratégie de test n’est configurée, l’appareil doit apparaître conforme. Si vous avez des stratégies de test, un appui sur **Conformité de l’appareil** indique que certaines actions doivent être effectuées pour renforcer la sécurité de l’appareil.

## <a name="next-steps"></a>Étapes suivantes

[Bien démarrer avec l’ajout d’applications](get-started-apps.md) : Recherchez et ajoutez des applications sur les appareils pour permettre à vos employés d’effectuer leur travail.

## <a name="learn-more"></a>En savoir plus

* [Options d’inscription pour Intune](enrollment-options.md)
* [Activer l’inscription BYOD (« Apportez votre propre appareil ») avec Intune](byod-enable.md)
* [Apprenez à vos utilisateurs finaux à utiliser l’inscription et la gestion des appareils](end-user-educate.md)
