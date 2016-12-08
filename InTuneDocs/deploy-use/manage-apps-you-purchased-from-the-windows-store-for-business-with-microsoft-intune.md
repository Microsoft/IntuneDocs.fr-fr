---
title: "Gérer le Windows Store pour les applications d’entreprise | Microsoft Intune"
description: "Connectez Microsoft Intune au Windows Store pour les entreprises si vous souhaitez gérer et déployer des applications achetées en volume à partir de la console Intune"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e38d47d-0c5e-40ce-b379-29d3657f5c28
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 37044da4c7a58749c7b3423b1872b07d1673603d


---

# <a name="manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune"></a>Gérer les applications que vous avez achetées dans le Windows Store pour Entreprises avec Microsoft Intune
[Windows Store pour Entreprises](https://www.microsoft.com/business-store) propose un lieu dans lequel vous pouvez trouver et acheter des applications pour votre organisation, individuellement ou par lots. En connectant le magasin à Microsoft Intune, vous pouvez gérer les applications achetées en volume depuis la console Intune. Exemple :
* Vous pouvez synchroniser la liste des applications que vous avez achetées dans le magasin avec Intune.
* Les applications qui sont synchronisées apparaissent dans la console d’administration Intune et vous pouvez les déployer comme toute autre application.
* Vous pouvez effectuer un suivi du nombre de licences disponibles et de la quantité de licences utilisée dans la console d’administration Intune.
* Intune bloque le déploiement et l’installation des applications s’il n’y a pas suffisamment de licences disponibles.

## <a name="before-you-start"></a>Avant de commencer
Passez en revue les informations suivantes avant de commencer la synchronisation et le déploiement des applications depuis Windows Store pour Entreprises :
* Vous devez configurer Intune comme autorité de gestion des appareils mobiles pour votre organisation. Pour plus d’informations, consultez [Conditions préalables pour l’inscription d’appareils dans Microsoft Intune](prerequisites-for-enrollment.md).
* Vous devez avoir créé un compte sur Windows Store pour Entreprises.
* Une fois que vous avez associé un compte Windows Business Store avec Intune, vous ne pouvez pas basculer sur un autre compte ultérieurement.
* Les applications achetées depuis le magasin ne peuvent pas être manuellement ajoutées ou supprimées d’Intune. Elles peuvent uniquement être synchronisées avec Windows Store pour Entreprises.
* Intune synchronise uniquement les applications sous licence en ligne que vous avez achetées auprès de Windows Store pour Entreprises.
* Les appareils doivent être joints à des services de domaine Active Directory ou à un espace de travail pour pouvoir utiliser cette fonctionnalité.
* Les appareils inscrits doivent utiliser la version 1511 de Windows 10.

## <a name="associate-your-windows-store-for-business-account-with-intune"></a>Associer votre compte Windows Store pour Entreprises à Intune
Avant d’activer la synchronisation dans la console Intune, vous devez configurer votre compte de magasin pour utiliser Intune comme outil de gestion :
1. Veillez à vous connecter à Business Store avec le compte de locataire que vous utilisez pour accéder à Intune.
2. Dans Business Store, choisissez **Paramètres** > **Outils de gestion**.
3. Sur la page Outils de gestion, choisissez **Ajouter un outil de gestion**, puis sélectionnez **Microsoft Intune**.

Vous pouvez maintenant continuer et configurer la synchronisation dans la console Intune.

## <a name="configure-synchronization"></a>Configuration de la synchronisation

1. Dans la [console d’administration Microsoft Intune](https://manage.microsoft.com), choisissez **Administration**
2. Dans l’espace de travail **Administration**, développez l’option **Gestion des appareils mobiles** > **Windows**, puis cliquez sur **Store Pro**.
3. Sur la page **Windows Store pour Entreprises**, procédez comme suit :
 * Si vous ne l’avez pas déjà fait, cliquez sur le lien pour vous inscrire à Windows Store pour Entreprises.
 * Une fois l’inscription effectuée, cliquez sur **Configurer la synchronisation**.
4. Dans la boîte de dialogue **Configurer la synchronisation des applications du Windows Store Pro**, sélectionnez **Activer la synchronisation du Windows Store Pro**.
5. Dans la liste déroulante **Langue**, choisissez la langue dans laquelle les applications de Windows Store pour Entreprises s’afficheront dans la console Intune. Quelle que soit la langue dans laquelle elles sont affichées, elles seront installées dans la langue de l’utilisateur final lorsqu’elles sont disponibles.
6. Cliquez sur **OK**.

## <a name="synchronize-apps"></a>Synchroniser les applications

1. Sur la page **Windows Store pour Entreprises**, cliquez sur **Synchroniser maintenant** pour synchroniser les applications que vous avez achetées dans le Windows Store avec Intune.
2. Dans l’espace de travail **Applications**, sélectionnez **Applications** > **Applications achetées en volume** pour afficher les applications que vous pouvez déployer et vérifier que vos applications achetées ont bien été importées. Les applications de ce nœud s’affichent avec le nombre total de licences que vous possédez, ainsi que le nombre de licences disponibles.
Par exemple, vous pouvez acheter l’application Portail d’entreprise (sous licence en ligne) dans le Windows Store pour Entreprises, la synchroniser dans la console Intune, puis la déployer en tant qu’application obligatoire sur les appareils Windows 10 nécessaires. 


## <a name="deploy-apps"></a>Déployer des applications

Vous déployez des applications à partir du magasin de la même façon que vous déploieriez toute autre application Intune. Pour plus d’informations, consultez [Déployer des applications dans Microsoft Intune](deploy-apps-in-microsoft-intune.md).
Lorsque vous déployez une application Windows Store pour Entreprises, une licence est utilisée par chaque utilisateur qui installe l’application. Si vous utilisez toutes les licences disponibles pour une application déployée, vous ne pourrez plus déployer d’autres copies. Vous devrez prendre l’une des actions suivantes :
* Désinstallez l’application de certains appareils.
* Réduisez la portée du déploiement actuel pour cibler uniquement les utilisateurs pour lesquels vous avez suffisamment de licences.
* Achetez plus de copies de l’application dans Windows Store pour Entreprises.

> [!Important]
> Les applications déployées sont uniquement disponibles pour l’utilisateur qui a inscrit l’appareil à l’origine. Aucun autre utilisateur ne peut accéder à l’application.


### <a name="see-also"></a>Voir aussi
[Ajouter des applications pour des appareils mobiles dans Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md)



<!--HONumber=Nov16_HO5-->


