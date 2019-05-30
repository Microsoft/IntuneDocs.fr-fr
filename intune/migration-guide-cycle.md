---
title: Fonctionnement d’un cycle de migration Intune classique
titleSuffix: Microsoft Intune
description: Cet article explique le fonctionnement d’un cycle de migration Microsoft Intune et propose des exemples pour illustrer la façon dont vous pouvez gérer les cycles de migration.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3688b724-9521-4210-bf4d-bcf47d8d4ca0
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2b6a38544016172da0267eb0a47948029786b786
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66046390"
---
# <a name="typical-migration-cycle"></a>Cycle de migration classique

Il arrive souvent qu’une organisation débute une migration Intune avec un pilote de petite taille, en ciblant un sous-ensemble des utilisateurs au sein du service informatique. En outre, il se peut que votre organisation doive aborder certains facteurs, à savoir la volonté d’évolution du groupe, le nombre d’utilisateurs, la complexité, les exigences, l’emplacement et les risques métiers, pour identifier la plage de migration la plus adaptée.

Voici un exemple de planification de vos groupes cibles :

  | **Groupes ciblés par la migration** | **Période 1** | **Période 2** | **Période 3** | **Période 4** | **...**
|:---:|:---:|:---:|:---:|:---:|:---:|
| Service informatique pilote de taille restreinte (50 utilisateurs) | Annoncer le plan | Demander aux utilisateurs de s’inscrire | Définir une échéance | Appliquer un accès conditionnel |  |                                                        
| Service informatique pilote de taille étendue (200 utilisateurs) |  | Annoncer le plan | Demander aux utilisateurs de s’inscrire | Définir une échéance | Appliquer un accès conditionnel |
| Phase de migration 1 : Utilisateurs technophiles (2 000) |  |  | Annoncer le plan | Demander aux utilisateurs de s’inscrire | Définir une échéance |
| Phase de migration 2 : Est des États-Unis |  |  |  | Annoncer le plan | Demander aux utilisateurs de s’inscrire |
| Toutes les régions |  |  |  |  | Annoncer le plan |

## <a name="customer-migration-case-study"></a>Étude de cas client

### <a name="adatum-corporation"></a>Adatum Corporation

Découvrez comment [Adatum Corporation a effectué la migration de ces systèmes depuis un fournisseur MDM tiers vers Intune](https://gallery.technet.microsoft.com/Intune-migration-guide-893a95e3?redir=0).

## <a name="monitoring-migration"></a>Surveillance de la migration

Intune met à votre disposition plusieurs méthodes pour surveiller la migration :

* Vues de groupes d’utilisateurs Intune

* Ensembles de rapports intégrés

* Alertes générées dans la console

Suivez le nombre d’utilisateurs ayant inscrit des appareils après chaque phase de façon à pouvoir :

-   évaluer l’efficacité de votre plan de communication ;

-   estimer l’impact d’une stratégie d’accès conditionnel.


## <a name="post-migration"></a>Post-migration

Mettez le fournisseur MDM précédent hors service et annulez l’abonnement au service après avoir migré vers Intune. Par ailleurs, soustrayez toute exigence inutile concernant l’infrastructure en suivant les instructions du fournisseur MDM.
