---
title: Afficher et corriger des données personnelles
description: Découvrez comment visualiser et corriger les données personnelles.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1ba77bc7-505e-4eca-a49e-dcdaa75d0043
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3a764cc3c46798d1fe34147f627e91d90c820263
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57229528"
---
# <a name="view-and-correct-personal-data"></a>Afficher et corriger des données personnelles

Les administrateurs Intune peuvent visualiser certaines données personnelles en fonction de leurs autorisations d’accès, mais seuls les utilisateurs finaux peuvent modifier les données personnelles de leur appareil.

[!INCLUDE [GDPR-related guidance](./includes/gdpr-dsr-and-stp-note.md)]


## <a name="view-personal-data"></a>Visualiser les données personnelles

Les administrateurs peuvent voir des informations personnelles de l’utilisateur final dans différents panneaux de l’interface utilisateur d’Intune. Les articles suivants expliquent à quelles informations les administrateurs ont accès ou non :
- Consultez [Détails de l’appareil](device-inventory.md) dans Intune, qui explique comment vous pouvez consulter des informations détaillées sur l’appareil d’un utilisateur final.
- [Surveiller les informations sur les applications et les affectations](apps-monitor.md) explique comment visualiser des informations détaillées sur les applications installées sur l’appareil d’un utilisateur final.
- L’article [Quelles informations mon entreprise peut-elle voir quand j’inscris mon appareil ?](https://docs.microsoft.com/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune) donne aux utilisateurs finaux une liste des données que leur entreprise peut voir ou pas. Il est préférable d’indiquer clairement à vos utilisateurs quel type de données vous collectez et pourquoi. Cet article peut être la première étape de cette démarche de transparence.

### <a name="who-can-view-the-data"></a>Qui peut voir les données ?

Microsoft utilise un contrôle strict pour régir l’accès aux données des clients, en accordant le niveau d’accès requis le plus bas pour effectuer des tâches clés et en révoquant l’accès lorsqu’il n’est plus nécessaire. 

Vous pouvez sécuriser et contrôler l’accès aux données personnelles des utilisateurs finaux à l’aide du contrôle d’accès en fonction du rôle (RBAC). Pour plus d’informations, consultez [RBAC avec Microsoft Intune](role-based-access-control.md).

Vous pouvez découvrir plus d’informations sur les pratiques de Microsoft en matière de données en lisant les conditions des services en ligne et la [Déclaration de confidentialité de Microsoft Online Services](http://go.microsoft.com/fwlink/p/?linkid=131004&clcid=0x409). 

## <a name="correct-end-user-personal-data"></a>Corriger les données personnelles des utilisateurs finaux

Les administrateurs ne peuvent pas mettre à jour les informations spécifiques de l’appareil ou de l’application. Si un utilisateur final souhaite corriger des données personnelles (par exemple le nom de l’appareil), il doit le faire directement sur son appareil. Ces modifications sont synchronisées la prochaine fois qu’il se connecte à Intune.


## <a name="next-steps"></a>Étapes suivantes

Découvrez comment [auditer, exporter ou supprimer](privacy-data-audit-export-delete.md) des données personnelles dans Intune.
