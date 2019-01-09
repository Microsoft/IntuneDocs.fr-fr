---
title: Configurer un accès conditionnel basé sur un périphérique avec Intune
titlesuffix: Microsoft Intune
description: Découvrez comment créer une stratégie d’accès conditionnel basée sur l’appareil en fonction de la conformité des appareils Microsoft Intune et de la gestion des applications mobiles.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 12/11/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 320ded06b59b583baf27544249393029f7488b2d
ms.sourcegitcommit: 0f19bc5c76b7c0835bfd180459f2bbd128eec1c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53267714"
---
# <a name="create-a-device-based-conditional-access-policy"></a>Créer une stratégie d’accès conditionnel basée sur l’appareil

Avec Intune, vous pouvez améliorer l’accès conditionnel dans Azure Active Directory en ajoutant une conformité des appareils mobiles avec les contrôles d’accès. Après avoir créé une stratégie de conformité Intune définissant les exigences pour que les appareils soient déclarés comme étant conformes, vous pouvez utiliser l’état de conformité d’un appareil pour autoriser ou bloquer l’accès à vos applications et services. Vous pouvez le faire en créant une stratégie d’accès conditionnel utilisant le paramètre **Exiger que l’appareil soit marqué comme conforme**. 

Une stratégie d’accès conditionnel spécifie l’application ou les services que vous souhaitez protéger, les conditions sous lesquelles les applications ou les services sont accessibles et les utilisateurs auxquels la stratégie s’applique. L’accès conditionnel est une fonctionnalité premium d’Azure AD configurable dans Azure Active Directory, mais vous pouvez également configurer ces stratégies à partir du portail Intune. 

> [!IMPORTANT]
> Avant de configurer l’accès conditionnel, vous devez configurer les stratégies de conformité des appareils Intune pour évaluer si les appareils répondent à des exigences spécifiques. Consultez l’article [Bien démarrer avec les stratégies de conformité des appareils dans Intune](device-compliance-get-started.md).

## <a name="create-conditional-access-policy"></a>Créer la stratégie d’accès conditionnel

1.  Depuis le portail Intune, sélectionnez **Accès conditionnel** > **Stratégies** > **Nouvelle stratégie**.
   
    ![Créer une stratégie d’accès conditionnel](media/create-conditional-access-intune/create-ca.png)
 
2.  Sous **Affectations**, sélectionnez **Utilisateurs et groupes**. 
3.  Sous l’onglet **Inclure**, identifiez les utilisateurs ou les groupes auxquels vous souhaitez appliquer cette stratégie d’accès conditionnel. Une fois que vous avez choisi lesquelles inclure, vous pouvez utiliser l’onglet **Exclure** s’il existe des utilisateurs, des rôles ou des groupes que vous souhaitez exclure de cette stratégie.  
    - **Tous les utilisateurs** : sélectionnez cette option pour appliquer la stratégie à tous les utilisateurs et tous groupes, y compris les utilisateurs internes et les invités.
  
    - **Sélectionner les utilisateurs et les groupes** : sélectionnez cette option et spécifiez une ou plusieurs des options suivantes :
  
      a. **Tous les utilisateurs invités** : sélectionnez cette option pour inclure ou exclure les utilisateurs invités externes (par exemple, les partenaires, les collaborateurs externes)
       
      b. **Rôles d’annuaire** : sélectionnez un ou plusieurs rôles Azure AD afin d’inclure ou d’exclure les utilisateurs affectés à ces rôles.
      
      c. **Utilisateurs et groupes** : sélectionnez cette option pour rechercher et sélectionner des utilisateurs individuels ou des groupes que vous souhaitez inclure ou exclure.
     
       > [!TIP]  
       > Testez la stratégie sur un plus petit groupe d’utilisateurs pour vérifier qu’elle fonctionne comme prévu.
4.  Sélectionnez **Terminé**.
5.  Sous **Affectations**, sélectionnez **Applications cloud**. 
6.  Sur l’onglet **Inclure**, identifiez les applications et les services que vous souhaitez protéger avec cette stratégie d’accès conditionnel. Vous pouvez ensuite utiliser l’onglet **Exclure** si vous souhaitez exclure des applications ou des services de cette stratégie.
    - **Toutes les applications cloud** : sélectionnez cette option pour appliquer la stratégie à toutes les applications.
      > [!IMPORTANT]  
      > L’application de gestion Microsoft Azure pour l’accès au portail Azure est incluse dans cette liste. Veillez à utiliser l’onglet **Exclure** soit à cet emplacement ou dans les options **Utilisateurs et groupes** pour vous assurer que vous (ou les utilisateurs ou groupes que vous désignez) serez en mesure de vous connecter au portail Azure. 

    - **Sélectionner des applications** : sélectionnez cette option, choisissez **Sélectionner**, puis utilisez la liste des applications pour rechercher et sélectionner les applications ou les services que vous souhaitez protéger.
    
      ![Créer une stratégie d’accès conditionnel](media/create-conditional-access-intune/create-ca-select-apps.png)

7.  Sélectionnez **Terminé**.
8.  Sous **Affectations**, sélectionnez **Conditions**.
    - **Risque de connexion** : choisissez Oui pour utiliser la détection de risque de connexion Azure AD Identity Protection avec cette stratégie, puis choisissez les niveaux de risque de connexion auxquels la stratégie doit s’appliquer.
    - **Plateformes d'appareils** : Sous l’onglet **Inclure**, identifiez les plateformes d’appareil auxquels vous souhaitez appliquer cette stratégie d’accès conditionnel. Utilisez l’onglet **Exclure** pour exclure des plateformes de cette stratégie.
    - **Emplacements** : sous l’onglet **Inclure**, spécifiez si la stratégie s’applique à n’importe quel emplacement, des emplacements réseau approuvés sous le contrôle de votre service informatique ou des emplacements réseau spécifiques. Utilisez l’onglet **Exclure** pour exclure des emplacements réseau de cette stratégie. 
    - **Applications clientes** : Choisissez **Oui** pour spécifier si la stratégie doit s’appliquer à des applications de navigateur, des applications mobiles et des clients de bureau. Vous pouvez également sélectionner des **clients d’authentification moderne** (comme Outlook pour iOS ou Outlook pour Android) et des **clients Exchange ActiveSync**.
    - **État de l’appareil** : la stratégie d’accès conditionnel s’applique à tous les états de l’appareil, à moins de choisir Oui et d’exclure spécifiquement les états Appareil Azure AD Hybride joint ou Appareil marqué comme conforme (ou les deux).
    
      ![Créer une stratégie d’accès conditionnel](media/create-conditional-access-intune/create-ca-device-platforms.png)

      > [!TIP]  
      > Si vous souhaitez protéger à la fois les clients **d’authentification moderne** et les **clients Exchange ActiveSync**, créez deux stratégies d’accès conditionnel distinctes, une pour chaque type de client. Bien qu’Exchange ActiveSync prenne en charge l’authentification moderne, la seule condition prise en charge par Exchange ActiveSync est la plateforme. Les autres conditions, y compris l’authentification multifacteur, ne sont pas prises en charge. Pour protéger efficacement l’accès à Exchange Online à partir d’Exchange ActiveSync, créez une stratégie d’accès conditionnel qui spécifie l’application cloud Office 365 Exchange Online et l’application client Exchange ActiveSync, en sélectionnant le paramètre Appliquer la stratégie uniquement aux plateformes prises en charge.

9.  Sélectionnez **Terminé**.
10. Sous **Contrôles d’accès**, sélectionnez **Accorder**. Configurez ce qui se passe en fonction des conditions configurées.  Vous pouvez sélectionner l’une des options suivantes :
    - **Bloquer l’accès** : les utilisateurs spécifiés dans cette stratégie n’auront pas accès aux applications dans les conditions que vous avez spécifiées.
    - **Accorder l’accès** : les utilisateurs spécifiés dans cette stratégie auront un accès, mais vous pouvez exiger les actions supplémentaires suivantes :
      - **Exiger l'authentification multifacteur** : l’utilisateur doit suivre les exigences de sécurité supplémentaires, comme un appel téléphonique ou un message texte.
      - **Exiger que l'appareil soit marqué comme conforme** : l’appareil doit être compatible avec Intune. Si l’appareil n’est pas conforme, l’utilisateur a la possibilité d’inscrire l’appareil dans Intune. 
      - **Exiger un appareil joint à une version hybride d'Azure AD** : les appareils doivent être joints à une version hybride d'Azure AD.
      - **Demander une application cliente approuvée** : l'appareil doit utiliser des applications clientes approuvées. 
      - **Pour plusieurs contrôles** : sélectionnez **Demander tous les contrôles sélectionnés** afin que toutes les exigences ci-dessus soient appliquées quand un appareil tente d’accéder à l’application.
    
      ![Contrôles d’accès - Paramètres Accorder](media/create-conditional-access-intune/create-ca-grant-access-settings.png)
 
11. Sous **Activer la stratégie**, sélectionnez **Activé**.
     
     ![Activer la stratégie](media/create-conditional-access-intune/enable-policy.png)

12. Sélectionnez **Créer**.

## <a name="see-also"></a>Voir aussi
[Accès conditionnel basé sur l’application avec Intune](app-based-conditional-access-intune.md)
