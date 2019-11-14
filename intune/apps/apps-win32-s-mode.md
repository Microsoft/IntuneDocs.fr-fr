---
title: Activer les applications Win32 sur les appareils en mode S
titleSuffix: Microsoft Intune
description: Découvrez comment activer des applications Win32 sur les appareils en mode S à l’aide de Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a3a9eb45898102e9d5fcde88f69026467255c513
ms.sourcegitcommit: d2d18eef64bcf16eec1a48fcb67f1362537c0245
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2019
ms.locfileid: "73445275"
---
# <a name="enable-win32-apps-on-s-mode-devices"></a>Activer les applications Win32 sur les appareils en mode S

[Le mode S Windows 10](https://docs.microsoft.com/windows/deployment/s-mode) est un système d’exploitation verrouillé qui exécute uniquement les applications du Store. Par défaut, les appareils en mode S Windows n’autorisent pas l’installation et l’exécution d’applications Win32. Ces appareils incluent une *stratégie de base Win 10S* unique, qui empêche l’appareil en mode S d’y exécuter des applications Win32. Toutefois, en créant et en utilisant une **stratégie supplémentaire en mode S** dans Intune, vous pouvez installer et exécuter des applications Win32 sur des appareils managés en mode S Windows 10. À l’aide des outils PowerShell [Windows Defender Application Control (WDAC)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control), vous pouvez créer une ou plusieurs stratégies supplémentaires pour le mode S Windows. Vous devez signer les stratégies supplémentaires avec le service de signature [Device Guard Signing Service (DGSS)](https://go.microsoft.com/fwlink/?linkid=2095629) ou avec [SignTool.exe](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/signing-policies-with-signtool), puis charger et distribuer les stratégies via Intune. Vous pouvez également signer les stratégies supplémentaires avec un certificat de coconception de votre organisation, mais la méthode recommandée consiste à utiliser DGSS. Si vous utilisez le certificat de coconception de votre organisation, le certificat racine auquel le certificat de coconception est lié doit être présent sur l’appareil.

En attribuant la stratégie supplémentaire en mode S dans Intune, vous autorisez l’appareil à faire une exception à la stratégie en mode S existante de l’appareil, qui autorise le catalogue d’applications signé correspondant chargé. La stratégie définit une liste verte d’applications (catalogue d’applications) qui peuvent être utilisées sur l’appareil en mode S.

> [!NOTE]
> Les applications Win32 sur les appareils en mode S sont uniquement prises en charge sur la mise à jour de Windows 10 de novembre 2019 (Build 18363) ou versions ultérieures.

<!-- Add WDAC tooling diagram  -->

Les étapes permettant d’autoriser les applications Win32 à s’exécuter sur un appareil Windows 10 en mode S sont les suivantes :

1. Activez les appareils en mode S via Intune dans le cadre du processus d’inscription de Windows 10 S.
2. Créez une stratégie supplémentaire pour autoriser les applications Win32 :
   - Vous pouvez utiliser les [outils Windows Defender Application Control (WDAC)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) pour créer une stratégie supplémentaire. L’ID de stratégie de base de la stratégie doit correspondre à l’ID de stratégie de base en mode S (qui est codé en dur sur le client). En outre, assurez-vous que la version de la stratégie est supérieure à la version précédente.
   - Vous utilisez DGSS pour signer votre stratégie supplémentaire. Pour plus d’informations, consultez [Stratégie d’intégrité de code de signature avec la signature Device Guard](https://docs.microsoft.com/microsoft-store/sign-code-integrity-policy-with-device-guard-signing).
   - Vous chargez la stratégie supplémentaire signée sur Intune en créant une stratégie supplémentaire en mode S Windows 10 (voir ci-dessous).
3. Vous autorisez les catalogues d’applications Win32 via Intune :
   - Vous créez des fichiers catalogues (1 pour chaque application) et vous les signez à l’aide de DGSS ou d’une autre infrastructure de certificat.
   - Vous empaquetez le catalogue signé dans le fichier *.intunewin* à l’aide de l’[outil de préparation de contenu Microsoft Win32](https://go.microsoft.com/fwlink/?linkid=2065730). Pour plus d’informations, consultez [Gestion des applications Win32 - Préparer le contenu de l’application Win32 pour chargement](~/apps/apps-win32-app-management.md#prepare-the-win32-app-content-for-upload).
   - Intune applique le catalogue d’applications signé pour installer l’application Win32 sur l’appareil en mode S à l’aide de l’[extension de gestion Intune](~/apps/intune-management-extension.md).

> [!NOTE]
> Les offres groupées `.appx` et `.appx` métiers sur le mode S Windows 10 sont prises en charge via la signature Microsoft Store for Business (MSFB).
>
> **La stratégie supplémentaire en mode S** pour les applications doit être fournie par le biais de l’extension de gestion Intune.
>
> Les stratégies en mode S sont appliquées au niveau de l’appareil. Plusieurs stratégies ciblées sont fusionnées sur l’appareil. La stratégie fusionnée est appliquée sur l’appareil.

Pour créer une stratégie supplémentaire en mode S Windows 10, procédez comme suit :

1. Connectez-vous à [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Dans le volet **Intune**, sélectionnez **Applications clientes** > **Stratégies supplémentaires en mode S** > **Créer une stratégie**.
3. Avant d’ajouter le **fichier de stratégie**, vous devez le créer et le signer. Pour plus d'informations, voir :
    - [Créer une stratégie WDAC à l’aide des outils PowerShell et la convertir au format binaire](https://go.microsoft.com/fwlink/?linkid=2095387)
    - [Signer à l’aide du service de Device Guard Signing Service](https://go.microsoft.com/fwlink/?linkid=2095629) **(recommandé)**

4. Dans la page **De base**, ajoutez les valeurs suivantes :

    | Valeur | Description |
    |--------------|------------------------------------------------|
    | Fichier de stratégie | Fichier qui contient la stratégie WDAC. |
    | Nom | Nom de cette stratégie. |
    | Description | [Facultatif] Description de cette stratégie. |

5. Cliquez sur **Suivant : Balises d’étendue**.<br>
   Dans la page **Balises d’étendue**, vous pouvez éventuellement configurer des balises d’étendue pour déterminer qui peut voir la stratégie d’application dans Intune. Pour plus d’informations sur les balises d’étendue, voir [Utiliser le contrôle d’accès en fonction du rôle et les balises d’étendue pour l’informatique distribuée](~/fundamentals/scope-tags.md).

6. Cliquez sur **Suivant : Affectations**.<br>
   La page **Affectations** vous permet d’affecter la stratégie à des utilisateurs et des appareils. Il est important de noter que vous pouvez affecter une stratégie à un appareil, que celui-ci soit ou non géré par Intune.
7. Cliquez sur **Suivant : Vérifier + créer** pour examiner les valeurs que vous avez entrées pour le profil.
8. Lorsque vous avez terminé, cliquez sur **Créer** pour créer la stratégie supplémentaire en mode S dans Intune. 

Une fois que la stratégie est créée, elle est ajoutée à la liste des stratégies supplémentaires en mode S dans Intune. Une fois la stratégie affectée, elle est déployée sur les appareils. Notez que vous devez déployer l’application dans le même groupe de sécurité que la stratégie supplémentaire. Vous pouvez commencer à cibler et à affecter des applications à ces appareils. Cela permet ensuite à vos utilisateurs finaux d’installer et d’exécuter les applications sur les appareils en mode S.

## <a name="removal-of-s-mode-policy"></a>Suppression de la stratégie de mode S

Actuellement, pour supprimer la stratégie supplémentaire en mode S de l’appareil, vous devez affecter et déployer une stratégie vide pour remplacer la stratégie supplémentaire en mode S existante.

## <a name="policy-reporting"></a>Reporting de stratégie

La stratégie supplémentaire en mode S, qui est appliquée au niveau de l’appareil, a seulement un reporting au niveau de l’appareil. Le reporting au niveau de l’appareil est disponible pour les conditions d’erreur et de réussite. 

Valeurs de reporting affichées dans la console Intune pour les stratégies de reporting en mode S :
- **Opération réussie** : La stratégie supplémentaire en mode S est en vigueur.
- **Inconnu** : L’état de la stratégie supplémentaire en mode S n’est pas connu.
- **TokenError** : la stratégie supplémentaire en mode S est structurellement correcte, mais il existe une erreur avec l’autorisation du jeton.
- **NotAuthorizedByToken** : le jeton n’autorise pas cette stratégie supplémentaire en mode S.
- **PolicyNotFound** : la stratégie supplémentaire en mode S est introuvable.

## <a name="next-steps"></a>Étapes suivantes

- Pour plus d’informations, consultez [Applications Win32 sur le mode S](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/lob-win32-apps-on-s).
- Pour plus d’informations sur l’ajout d’applications à Intune, consultez [Ajouter des applications à Microsoft Intune](apps-add.md).
- Pour plus d’informations sur les applications Win32, consultez [Gestion des applications Win32 Intune](~/apps/apps-win32-app-management.md).
