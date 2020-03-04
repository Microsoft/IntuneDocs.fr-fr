---
title: Scénario guidé – Bureau moderne géré par le cloud
titleSuffix: Microsoft Intune
description: Aidez-vous du scénario guidé pour configurer un bureau moderne de base à partir du portail Gestion des appareils Microsoft 365.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/26/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9ddd59715a0730a52738088700a1f2b9166bfa80
ms.sourcegitcommit: fab685b22a010fe231b27a0c5eda34a6f22f4c8d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2020
ms.locfileid: "78216212"
---
# <a name="guided-scenario---cloud-managed-modern-desktop"></a>Scénario guidé – Bureau moderne géré par le cloud

Le bureau moderne est la plateforme de productivité à la pointe de la technologie destinée aux travailleurs de l’information. Office 365 ProPlus et Windows 10 sont les principaux composants du bureau moderne, parallèlement aux dernières bases de référence de sécurité pour Windows 10 et à Microsoft Defender ATP (Advanced Threat Protection). 

Les actions à distance à l’échelle d’Internet constituent l’atout supplémentaire de la gestion du bureau moderne à partir du cloud. La gestion cloud s’appuie sur les stratégies intégrées de gestion des appareils mobiles Windows et élimine les dépendances vis-à-vis de la stratégie de groupe locale Active Directory. 

Si vous voulez évaluer un bureau moderne géré par le cloud dans votre propre organisation, ce scénario guidé prédéfinit toutes les configurations nécessaires à un déploiement de base. Dans ce scénario guidé, vous allez créer un environnement sécurisé dans lequel vous pourrez tester les fonctionnalités de gestion d’appareils Intune. 

## <a name="prerequisites"></a>Prérequis
- [Définir l’autorité MDM sur Intune](~/fundamentals/mdm-authority-set.md#set-mdm-authority-to-intune) – Le paramètre d’autorité de gestion des appareils mobiles (MDM) détermine la façon dont vous gérez vos appareils. En tant qu’administrateur informatique, vous devez définir une autorité de gestion des appareils mobiles (MDM) avant que les utilisateurs puissent inscrire des appareils pour la gestion.
- M365 E3 minimum (ou M365 E5 pour une sécurité optimale)
- Appareil Windows 10 1903 (inscrit auprès de Windows Autopilot pour une expérience utilisateur optimale)
- Autorisations d’administrateur de service Intune nécessaires pour suivre ce scénario guidé :
  - Lecture, création, suppression, affectation et mise à jour pour la configuration de l’appareil
  - Lecture d’appareil, lecture de profil, création de profil, affectation de profil et suppression de profil pour les programmes d’inscription
  - Lecture, création, suppression, affectation et mise à jour des applications mobiles
  - Lecture et mise à jour pour l’organisation
  - Lecture, création, affectation et mise à jour des bases de référence de sécurité
  - Lecture, création, suppression, affectation et mise à jour des ensembles de stratégies

## <a name="step-1---introduction"></a>Étape 1 – Introduction

Dans ce scénario guidé, vous allez configurer un utilisateur de test, inscrire un appareil dans Intune, déployer l’appareil avec les paramètres recommandés par Intune ainsi que Windows 10 et Office ProPlus. Votre appareil sera aussi configuré pour Microsoft Defender ATP (Advanced Threat Protection) si vous choisissez d’[activer cette protection dans Intune](~/protect/advanced-threat-protection.md#enable-microsoft-defender-atp-in-intune). L’utilisateur que vous configurez et l’appareil que vous inscrivez seront ajoutés à un nouveau groupe de sécurité qui sera configuré avec les paramètres recommandés pour la sécurité et la productivité. 

### <a name="what-you-will-need-to-continue"></a>Ce dont vous avez besoin pour continuer

Vous devez indiquer l’appareil de test et l’utilisateur de test dans ce scénario guidé. Veillez à effectuer les tâches suivantes :
- Configurez un compte d’utilisateur de test dans Azure Active Directory.
- Créez un appareil de test exécutant Windows 10, version 1903 ou ultérieure.
- (Facultatif) [Inscrivez l’appareil de test auprès de Windows Autopilot](~/enrollment/enrollment-autopilot.md#add-devices).
- (Facultatif) Activez la [personnalisation dans la page de connexion Azure Active Directory de votre organisation](https://go.microsoft.com/fwlink/?linkid=2102455).

## <a name="step-2---user"></a>Étape 2 – Utilisateur

Choisissez l’utilisateur à configurer sur l’appareil. Cette personne sera l’utilisateur principal de l’appareil.

Si vous souhaitez ajouter des utilisateurs ou des appareils supplémentaires à cette configuration, ajoutez-les simplement aux groupes de sécurité AAD générés par l’Assistant. Contrairement aux autres scénarios guidés, vous n’avez pas besoin d’exécuter l’Assistant plusieurs fois, car la configuration n’est pas personnalisable. Il vous suffit d’ajouter les utilisateurs et les appareils aux groupes AAD créés. Une fois l’Assistant terminé, le groupe généré est déployé avec les stratégies recommandées. 

## <a name="step-3---device"></a>Étape 3 : Appareil

Vérifiez que votre appareil exécute bien Windows 10 version 1903 ou ultérieure.  L’utilisateur principal doit configurer l’appareil dès qu’il en prend possession. L’utilisateur a le choix entre deux configurations possibles. 

### <a name="option-a--windows-autopilot"></a>Option A – Windows Autopilot
Windows Autopilot automatise la configuration des nouveaux appareils. Les utilisateurs n’ont donc pas besoin de faire appel à une quelconque assistance informatique pour configurer leur appareil après l’avoir déballé. Si votre appareil est déjà inscrit auprès de Windows Autopilot, sélectionnez-le par son numéro de série. Pour plus d’informations sur l’utilisation de Windows Autopilot, consultez [Inscrire un appareil auprès de Windows Autopilot (facultatif)](~/fundamentals/guided-scenarios-cloud-managed-pc.md#register-device-with-windows-autopilot-optional).

### <a name="option-b--manual-device-enrollment"></a>Option B – Inscription manuelle de l’appareil
Les utilisateurs configurent et inscrivent manuellement leurs nouveaux appareils dans la gestion des appareils mobiles. Après avoir suivi ce scénario, réinitialisez l’appareil et donnez à l’utilisateur principal les instructions d’inscription pour appareils Windows. Pour plus d’informations, consultez [Joindre un appareil Windows 10 à Azure AD lors de la première exécution](https://docs.microsoft.com/azure/active-directory/devices/azuread-joined-devices-frx#joining-a-device).

## <a name="step-4---review--create"></a>Étape 4 – Vérifier + créer

La dernière étape vous permet d’examiner un récapitulatif des paramètres que vous avez configurés. Une fois que vous avez examiné vos choix, cliquez sur **Déployer** pour terminer le scénario guidé. Une fois le scénario guidé terminé, un tableau des ressources s’affiche. Vous pouvez modifier ces ressources par la suite, mais une fois que vous quittez le récapitulatif, le tableau n’est pas enregistré.

> [!IMPORTANT]
> Une fois le scénario guidé terminé, vous obtenez un récapitulatif. Vous pouvez par la suite modifier les ressources listées dans le récapitulatif, mais le tableau qui affiche ces ressources n’est pas enregistré.

### <a name="verification"></a>Vérification
1. Vérifiez qu’une portée utilisateur GDR est affectée à l’utilisateur sélectionné.
    - Vérifiez que le paramètre [Portée de l’utilisateur GDR](~/enrollment/windows-enroll.md#enable-windows-10-automatic-enrollment) est défini sur :
        - **Tous** pour l’application **Microsoft Intune**, ou sur
        - **Certain(e)s**. De même, ajoutez le groupe d’utilisateurs créé par ce scénario guidé.
2. Vérifiez que l’utilisateur sélectionné peut joindre des appareils à Azure Active Directory.
    - Vérifiez que la jonction AAD est définie sur :
        - **Tous**, ou sur
        - **Certain(e)s**. Ajoutez aussi le groupe d’utilisateurs créé par ce scénario guidé.
3. Joignez l’appareil à Azure AD en suivant les étapes correspondant à votre cas :
    - Avec Autopilot. Pour plus d’informations, consultez [Mode piloté par l’utilisateur Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven).
    - Sans Autopilot : Pour plus d’informations, consultez [Joindre un appareil Windows 10 à Azure AD lors de la première exécution](https://docs.microsoft.com/azure/active-directory/devices/azuread-joined-devices-frx#joining-a-device).

### <a name="what-happens-when-i-click-deploy"></a>Que se passe-t-il quand je clique sur Déployer ?
L’utilisateur et l’appareil sont ajoutés aux nouveaux groupes de sécurité. De même, ils sont configurés avec les paramètres recommandés par Intune pour la sécurité et la productivité au travail ou à l’école. Une fois que l’utilisateur a joint l’appareil à Azure AD, des paramètres et des applications supplémentaires sont ajoutés à l’appareil. Pour en savoir plus sur ces configurations supplémentaires, consultez [Démarrage rapide : Inscrire votre appareil Windows 10](~/enrollment/quickstart-enroll-windows-device.md).

## <a name="additional-information"></a>Informations supplémentaires

### <a name="register-device-with-windows-autopilot-optional"></a>Inscrire un appareil auprès de Windows Autopilot (Facultatif)

Vous pouvez éventuellement choisir d’utiliser un appareil Autopilot inscrit. Pour Autopilot, ce scénario guidé affecte un profil de déploiement Autopilot et un profil de page d’état d’inscription. Le profil de déploiement Autopilot est configuré comme suit :
- Mode piloté par l’utilisateur : l’utilisateur final doit entrer un nom d’utilisateur et un mot de passe pendant l’installation de Windows.
- Jonction à Azure AD.
- Personnalisation de l’installation de Windows :
  - Masquage de l’écran des termes du contrat de licence logiciel Microsoft
  - Masquage des paramètres de confidentialité 
  - Création du profil local de l’utilisateur sans privilèges d’administrateur local
  - Masquage des options Changer de compte dans la page de connexion d’entreprise

La page d’état d’inscription est configurée pour être activée uniquement pour les appareils Autopilot, et elle attend que toutes les applications soient installées.

Par ailleurs, le scénario guidé affecte l’utilisateur à l’appareil Autopilot sélectionné pour une expérience d’installation personnalisée.

#### <a name="post-requisites"></a>Postrequis
Une fois que l’utilisateur a joint l’appareil à Azure Active Directory, les configurations suivantes sont appliquées à l’appareil :
1. Office 365 ProPlus est automatiquement installé sur le PC géré par le cloud. Cette installation inclut les applications que vous connaissez bien, à savoir Access, Excel, OneNote, Outlook, PowerPoint, Publisher, Skype Entreprise et Word. Vous pouvez utiliser ces applications pour vous connecter aux services Office 365 que sont SharePoint Online, Exchange Online et Skype sur le web. Office 365 ProPlus fait l’objet de mises à jour régulières avec de nouvelles fonctionnalités, ce qui n’est pas le cas des versions d’Office sans abonnement. Pour obtenir la liste des nouvelles fonctionnalités, consultez Nouveautés d’Office 365.
2. Les bases de référence de sécurité Windows sont installées sur le PC géré par le cloud. Si vous avez installé Microsoft Defender ATP (Advanced Threat Protection), le scénario guidé configure aussi les paramètres de base pour Defender. Defender ATP dote la pile de sécurité Windows 10 d’une nouvelle couche de protection après une violation de la sécurité. La technologie cliente intégrée à Windows 10 associée à la robustesse du service cloud vous permettront de détecter les menaces qui ont déjoué les autres moyens de défense. 

## <a name="next-steps"></a>Étapes suivantes

- Si vous utilisez Microsoft Defender ATP, créez une [stratégie de conformité Intune](~/protect/advanced-threat-protection.md#create-and-assign-the-compliance-policy) pour mettre en conformité l’analyse des menaces de Defender.
- Créez une [stratégie d’accès conditionnel en fonction de l’appareil](~/protect/advanced-threat-protection.md#create-a-conditional-access-policy) pour bloquer l’accès si l’appareil ne respecte pas les règles de conformité Intune.
