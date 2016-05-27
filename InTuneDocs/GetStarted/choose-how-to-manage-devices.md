---
# required metadata

title: Choisir comment gérer des appareils avec Microsoft Intune | Microsoft Intune
description:
keywords:
author: jeffgilb
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 770aad50-fd7a-4cf1-a793-f95fe47fc3f8

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Choisir comment gérer des appareils
[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] vous permet de gérer une gamme d’appareils en les *inscrivant* auprès du service. Les utilisateurs peuvent ensuite utiliser un *portail d’entreprise* pour effectuer différentes opérations telles que l’inscription de leur appareil, la recherche et l’installation d’applications, la vérification de la conformité de leur appareil aux stratégies d’entreprise et la prise de contact avec le service d’assistance informatique.

## Mode de gestion des appareils mobiles
[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] peut gérer les plateformes d’appareils suivantes :

- Apple iOS 7.1 et versions ultérieures
- Google Android 4.0 et versions ultérieures (y compris Samsung KNOX)
- Windows Phone 8.0 et versions ultérieures
- Windows RT et Windows 8.1 RT
- PC exécutant Windows 8.1 et versions ultérieures
- Mac OS X 10.9 et versions ultérieures

<div class="alert alert-tip">
  <h5><span class="icon-tip"></span> Conseil</h5>
  <p>Si vous avez précédemment inscrit des appareils qui exécutent une version d’iOS antérieure à la version prise en charge mentionnée ci-dessus, ils resteront inscrits. Consultez néanmoins la documentation de chaque [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] pour vérifier que cette version d’iOS est prise en charge par la fonctionnalité.</p>
</div>

[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] peut gérer les appareils des utilisateurs. Ce concept est communément appelé BYOD (« apportez votre propre appareil »). Il peut également gérer les appareils appartenant à l'entreprise, notamment dans les scénarios où celle-ci fournit aux utilisateurs une liste d'appareils qu'ils peuvent utiliser. Il s'agit du concept CYOD (« choisissez votre propre appareil »).

### Inscription des appareils pour la gestion
Pour les systèmes d’exploitation d’appareils mobiles, notamment iOS, Android et Windows Phone, vous devez toujours inscrire les appareils. Toutefois, le mode d’inscription des appareils varie en fonction des besoins de votre organisation :

|Type d'inscription|BYOD|CYOD|Appareil partagé avec compte de gestionnaire|Appareil partagé sans compte d'utilisateur|
|-------------------|--------|--------|--------------------------------------|----------------------------------------|
|**Description**|Appareil personnel inscrit à l'aide de Microsoft Intune|Appareil d'entreprise pour un seul utilisateur|Appareil d'entreprise géré à l'aide d'un compte de gestionnaire partagé par de nombreux utilisateurs|Appareil d'entreprise sans utilisateur utilisé par de nombreux utilisateurs|
|**Utilisateur de l'appareil**|Propriétaire|Utilisateur affecté|Aucun compte spécifique à l'utilisateur|Aucun utilisateur spécifique|
|**Qui inscrit l’appareil ?**|Propriétaire|Administrateur|Gestionnaire d'appareils|Toute personne|
|**Qui annule l’inscription ?**|Propriétaire ou administrateur|Administrateur|Administrateur|Administrateur|
|**Qui peut réinitialiser ?**|Propriétaire ou administrateur|Administrateur|Administrateur|Administrateur|

<div class="alert alert-tip">
  <h5><span class="icon-tip"></span> Conseil</h5>
  <p>Pour obtenir une liste complète des fonctionnalités offertes par l’inscription d’appareils, consultez [Fonctionnalités de gestion des appareils mobiles](mobile-device-management-capabilities-in-microsoft-intune.md).</p>
</div>



## Mode de gestion des PC Windows
[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] peut gérer les PC Windows Vista et versions ultérieures à l’aide du client Intune. Toutefois, pour les PC Windows, vous pouvez soit les inscrire, soit installer le logiciel client PC [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] qui offre quelques fonctionnalités non disponibles quand vous inscrivez les appareils. Dans la plupart des scénarios, vous inscrirez votre appareil Windows avec Intune car cette approche offre davantage de fonctionnalités que le recours au client.

Utilisez le client Intune quand vous souhaitez :
<ul>
<li>Utiliser l’une des fonctionnalités du client Microsoft Intune pour gérer vos PC Windows.</li>
<li>Gérer un PC Windows qui exécute un système d’exploitation dont l’inscription n’est pas prise en charge.</li>
</ul>

<div class="alert alert-tip">
  <h5><span class="icon-tip"></span> Conseil</h5>
  <p>Pour obtenir une liste complète des fonctionnalités offertes par l’installation du client Intune sur les PC Windows pris en charge, consultez [Fonctionnalités de gestion des PC Windows](windows-pc-management-capabilities-in-microsoft-intune.md).</p>
</div>

## Gestion d’Exchange ActiveSync
Vous pouvez aussi gérer des appareils par le biais d’Exchange ActiveSync. Vous devez pour cela installer le connecteur local ou utiliser le connecteur de service à service intégré pour vous connecter à votre instance d’Exchange Server.

Pour en savoir plus sur la configuration matérielle et logicielle requise pour installer le connecteur local, consultez [Configuration requise pour le connecteur local](/Intune/network-infrastructure-requirements-for-microsoft-intune.md).

Pour en savoir plus sur l’utilisation du connecteur local ou du connecteur de service à service avec Exchange, consultez [Gestion des appareils mobiles à l’aide d’Exchange ActiveSync et de Microsoft Intune](/Intune/get-started/mobile-device-management-with-exchange-activesync-and-microsoft-intune.md).



## Étapes suivantes
Maintenant que vous avez découvert certaines des fonctionnalités disponibles quand vous inscrivez vos appareils avec [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], vous devez vous [préparer à inscrire vos appareils](/Intune/get-started/get-ready-to-enroll-devices-in-microsoft-intune.md). Une fois les appareils inscrits, vous pourrez tirer parti de toutes les fonctionnalités décrites dans cette rubrique. <!--lindavr: There's a logical flaw in our "get to know/get started" content. You can take the path in this topic or you can take the path in the What to know before your get started topic. And they don't cover the same ground. -->


<!--HONumber=May16_HO1-->

