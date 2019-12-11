---
title: Systèmes d’exploitation et navigateurs pris en charge par Microsoft Intune
titleSuffix: ''
description: Répertorie les plateformes d’appareils et navigateurs pris en charge par pour la gestion des appareils Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5d1ac59c-a885-4276-8576-f3cf81c2d268
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2b58cbd0aa07babd36c7a7e5aa3dcc5b8d32d58a
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "73415065"
---
# <a name="supported-operating-systems-and-browsers-in-intune"></a>Systèmes d’exploitation et navigateurs pris en charge dans Intune

Avant de configurer Microsoft Intune, passez en revue les systèmes d’exploitation et les navigateurs pris en charge.

Pour obtenir de l’aide sur l’installation d’Intune sur votre appareil, consultez [Utilisation d’appareils gérés pour réaliser vos tâches](https://docs.microsoft.com/intune-user-help/company-portal-frequently-asked-questions) et [Utilisation de la bande passante réseau Intune](network-bandwidth-use.md).

Pour plus d’informations sur la prise en charge d’un fournisseur de services de configuration, consultez la [référence de fournisseur de services de configuration](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference).

## <a name="intune-supported-operating-systems"></a>Systèmes d’exploitation pris en charge Intune

Vous pouvez gérer des appareils qui exécutent les systèmes d’exploitation suivants :

[!INCLUDE [mdm-supported-devices](../includes/mdm-supported-devices.md)]

### <a name="supported-samsung-knox-standard-devices"></a>Appareils Samsung Knox Standard pris en charge

Pour éviter les erreurs d’activation Knox qui empêchent l’inscription MDM, l’application Portail d’entreprise tente l’activation de Samsung Knox lors de l’inscription à MDM uniquement si l’appareil figure dans la [liste des appareils Knox pris en charge](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Les appareils qui ne prennent pas en charge l’activation de Samsung Knox s’inscrivent en tant qu’appareils Android standard. Un appareil Samsung peut avoir des numéros de modèles qui prennent en charge Knox, alors que d’autres ne le prennent pas en charge. Vérifiez la compatibilité de Knox auprès du revendeur de votre appareil avant d’acheter et de déployer des appareils Samsung.

> [!NOTE]
> L’inscription des appareils Samsung Knox peut vous obliger à [activer l’accès aux serveurs de Samsung](https://support.samsungknox.com/hc/articles/115013833108-Our-corporate-devices-are-behind-a-firewall-How-do-I-enable-Knox-Workspace-devices-to-contact-Samsung-servers).

Les modèles d’appareils Samsung figurant dans la liste suivante ne prennent pas en charge Knox. Ils sont inscrits comme appareils Android natifs par l’application Portail d’entreprise pour Android :

| **Nom de l’appareil** | **Numéro de modèle de l’appareil** |
| --- | --- |
| Galaxy Avant | SM-G386T |
| Galaxy Core 2/Core 2 Duos | SM-G355H<br>SM-G355M |
| Galaxy Core Lite | SM-G3588V |
| Galaxy Core Prime | SM-G360H |
| Galaxy Core LTE | SM-G386F<br>SM-G386W |
| Galaxy Grand | GT-I9082L<br>GT-I9082<br>GT-I9080L |
| Galaxy Grand 3 | SM-G7200 |
| Galaxy Grand Neo | GT-I9060I |
| Galaxy Grand Prime Value Edition | SM-G531H |
| Galaxy J Max | SM-T285YD |
| Galaxy J1 | SM-J100H<br>SM-J100M<br>SM-J100ML |
| Galaxy J1 Ace | SM-J110F<br>SM-J110H |
| Galaxy J1 Mini | SM-J105M |
| Galaxy J2/J2 Pro | SM-J200H<br>SM-J210F |
| Galaxy J3 | SM-J320F<br>SM-J320FN<br>SM-J320H<br>SM-J320M |
| Galaxy K Zoom | SM-C115 |
| Galaxy Light | SGH-T399N |
| Galaxy Note 3 | SM-N9002<br>SM-N9009 |
| Galaxy Note 7/Note 7 Duos | SM-N930S<br>SM-N9300<br>SM-N930F<br>SM-N930T<br>SM-N9300<br>SM-N930F<br>SM-N930S<br>SM-N930T |
| Galaxy Note 10.1 3G | SM-P602 |
| Galaxy S2 Plus | GT-I9105P |
| Galaxy S3 Mini | SM-G730A<br>SM-G730V |
| Galaxy S3 Neo | GT-I9300<br>GT-I9300I |
| Galaxy S4 | SM-S975L |
| Galaxy S4 Neo | SM-G318ML |
| Galaxy S5 | SM-G9006W |
| Galaxy S6 Edge | 404SC |
| Galaxy Tab A 7.0&quot; | SM-T280<br>SM-T285 |
| Galaxy Tab 3 7&quot;/Tab 3 Lite 7&quot; | SM-T116<br>SM-T210<br>SM-T211 |
| Galaxy Tab 3 8.0&quot; | SM-T311 |
| Galaxy Tab 3 10.1&quot; | GT-P5200<br>GT-P5210<br>GT-P5220 |
| Galaxy Trend 2 Lite | SM-G318H |
| Galaxy V Plus | SM-G318HZ |
| Galaxy Young 2 Duos | SM-G130BU |

### <a name="windows-pc-software-client"></a>Logiciel client pour PC Windows

Vous pouvez déployer et installer un [logiciel client Intune](manage-windows-pcs-with-microsoft-intune.md) sur les PC Windows en guise d’alternative à l’inscription. Cette fonctionnalité est uniquement disponible dans le portail classique Intune. Vous pouvez utiliser le logiciel client Intune pour gérer des PC Windows 7 et versions ultérieures, à l’exception de Windows 10 Édition familiale.

> [!Note]
> Microsoft a annoncé que le support de Windows 7 prendra fin le 14 janvier 2020. À cette date, Intune cessera également de prendre en charge les appareils exécutant Windows 7.
>
> Pour plus d’informations, consultez [Calendrier des modifications Intune : la prise en charge de Windows 7 touche à sa fin](https://docs.microsoft.com/intune/fundamentals/whats-new#intune-plan-for-change-nearing-end-of-support-for-windows-7)
>
> Microsoft Intune cessera le support de la console Intune basée sur Silverlight le 15 octobre 2020. Cette mise hors service s’accompagne de la fin du support pour le client logiciel PC configuré avec la console Silverlight (également appelé agent PC)
>
> Pour plus d’informations, consultez [Fin du support pour la console d’administration basée sur Silverlight par Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Take-Action-Microsoft-Intune-ending-support-for-the-Silverlight/ba-p/916249)

<!--  ### Exchange ActiveSync management

You can manage [Exchange ActiveSync devices](../enrollment/device-enrollment.md#mobile-device-management-with-exchange-activesync-and-intune) from the Intune console. This option provides a limited set of management capabilities when compared to the other methods. See [Capabilities of built-in Mobile Device Management in Office 365](https://support.office.com/article/Capabilities-of-built-in-Mobile-Device-Management-for-Office-365-a1da44e5-7475-4992-be91-9ccec25905b0) for a list of supported devices.  -->

## <a name="intune-supported-web-browsers"></a>Navigateurs web pris en charge par Intune

Différentes tâches administratives vous obligent à utiliser l’un des sites web d’administration suivants.

- [Centre d’administration Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Portail Azure](https://portal.azure.com/)

Les navigateurs suivants sont pris en charge pour ces portails :

- Microsoft Edge (dernière version)
- Microsoft Internet Explorer 11
- Safari (dernière version, Mac uniquement)
- Chrome (dernière version)
- Firefox (dernière version)

### <a name="intune-classic-portal"></a>Portail classique Intune

Le portail classique Intune est utilisé uniquement pour gérer les appareils inscrits auprès du client logiciel Intune PC (https://manage.microsoft.com). Le portail classique Intune nécessite la prise en charge du navigateur Silverlight.

Les navigateurs Silverlight suivants prennent en charge la console Intune :

- Internet Explorer 10 ou version ultérieure
- Google Chrome (versions antérieures à la version 42)
- Mozilla Firefox avec Silverlight activé (versions antérieures à 56)

> [!Note]
> Microsoft Edge et les navigateurs mobiles ne sont pas pris en charge pour le portail classique Intune, car ils ne prennent pas en charge [Microsoft Silverlight](https://msdn.microsoft.com/library/cc838158(v=vs.95).aspx).

Seuls les utilisateurs disposant d’autorisations d’administrateur de service ou les administrateurs clients ayant le rôle Administrateur général peuvent se connecter à ce portail. Pour accéder à la console d’administration, votre compte doit posséder une licence d’utilisation de Microsoft Intune et son état de connexion doit être **Autorisé**.
