---
title: "Paramètres de stratégie de protection d’application Android | Version préliminaire d’Intune Azure | Microsoft Docs"
description: "Version préliminaire d&quot;Intune Azure : cette rubrique décrit les paramètres de stratégie de protection d’application pour les appareils Android."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9e9ef9f5-1215-4df1-b690-6b21a5a631f8
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: 6720c163e712e9d27319b16b0e1515e9e7f13ee8


---

# <a name="android-app-protection-policy-settings"></a>Paramètres de stratégie de protection d’application Android
Vous pouvez [configurer](app-protection-policies.md) les paramètres décrits dans cette rubrique pour une stratégie de protection d'application dans le panneau **Paramètres** du portail Azure.
Il existe deux catégories de paramètres de stratégie : réadressage des données et accès. Dans cette rubrique, le terme *Applications gérées par la stratégie* fait référence aux applications qui sont configurées avec des stratégies de protection d’application.

##  <a name="data-relocation-settings"></a>Paramètres de réadressage des données

| Paramètre | Procédure d'utilisation | Valeur(s) par défaut |
|------|------|------|
| **Interdire les sauvegardes Android** | Choisissez **Oui** pour empêcher cette application de sauvegarder les données professionnelles ou scolaires dans le [service de sauvegarde Android](https://developer.android.com/google/backup/index.html) Choisissez **Non** pour permettre à cette application de sauvegarder les données professionnelles ou scolaires.| Oui |
| **Autoriser l'application à transférer des données vers d'autres applications** | Spécifiez les applications qui peuvent recevoir des données à partir de cette application : <ul><li> **Applications gérées par la stratégie** : autoriser le transfert uniquement vers d’autres applications gérées par la stratégie.</li> <li>**Toutes les applications** : autoriser le transfert vers n’importe quelle application. </li> <li>**Aucune** : interdire le transfert de données vers n’importe quelle application, y compris d’autres applications gérées par la stratégie.</li></ul> | Toutes les applications |
| **Autoriser l'application à recevoir des données d'autres applications** | Spécifiez quelles applications peuvent transférer des données vers cette application : <ul><li>**Applications gérées par la stratégie** : autoriser le transfert uniquement à partir d’autres applications gérées par la stratégie.</li><li>**Toutes les applications** : autoriser le transfert de données à partir de n’importe quelle application.</li><li>**Aucune** : interdire le transfert de données depuis n’importe quelle application, y compris d’autres applications gérées par la stratégie. | Toutes les applications |
| **Empêcher « Enregistrer sous »** | Sélectionnez **Oui** pour interdire l’utilisation de l’option Enregistrer sous dans cette application. Choisissez **Non** pour autoriser l’utilisation de l’option Enregistrer sous. | Non |
| **Restreindre les opérations couper, copier et coller avec d'autres applications** | Spécifiez quand autoriser les actions couper, copier et coller avec cette application. Choisissez parmi : <ul><li>**Bloqué** : ne pas autoriser les actions couper, copier et coller entre cette application et une autre application.</li><li>**Applications gérées par la stratégie** : autoriser seulement les actions couper, copier et coller entre cette application et les autres applications gérées par la stratégie.</li><li>**Applications gérées par la stratégie avec Coller dans** : autoriser les actions couper et copier entre cette application et les autres applications gérées par la stratégie. Autoriser le collage dans cette application de données à partir de n'importe quelle application.</li><li>**N’importe quelle application** : aucune restriction pour les actions couper, copier et coller vers et depuis cette application. | N’importe quelle application |
|**Limiter le contenu web à afficher dans Managed Browser** | Choisissez **Oui** pour appliquer des liens web dans l’application à ouvrir dans l’application Managed Browser. <br><br> Pour les appareils non inscrits dans Intune, les liens web contenus dans les applications gérées par la stratégie peuvent s’ouvrir uniquement dans l’application Managed Browser. <br><br> Si vous utilisez Intune pour gérer vos appareils, consultez [Gérer l’accès à Internet à l’aide de stratégies Managed Browser avec Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/manage-internet-access-using-managed-browser-policies). | Non |
| **Chiffrer les données de l'application** | Choisissez **Oui** pour activer le chiffrement des données professionnels ou scolaires dans cette application. Intune utilise une méthode de chiffrement OpenSSL ainsi que le système Android Keystore pour chiffrer en toute sécurité les données de l'application. Les données sont chiffrées de façon synchrone durant les tâches d’E/S de fichier. Le contenu figurant sur le stockage de l’appareil est toujours chiffré. <br><br> La méthode de chiffrement n'est **pas** certifiée FIPS 140-2.  | Oui |
| **Désactiver la synchronisation des contacts** | Choisissez **Oui** pour empêcher l’application d'enregistrer les données vers l’application Contacts native sur l'appareil. Si vous choisissez **Non**, l’application peut enregistrer des données vers l’application Contacts native sur l'appareil. <br><br>Lorsque vous effectuez une réinitialisation sélective pour supprimer des données professionnelles ou scolaires à partir de l’application, les contacts directement synchronisés à partir de l’application vers l'application Contacts native sont supprimés. Les contacts synchronisés à partir du carnet d’adresses natif vers une autre source externe ne peuvent pas être effacés. Ceci s’applique uniquement à l’application Microsoft Outlook. | Non |
| **Désactiver l’impression** | Choisissez **Oui** pour empêcher l’application d'imprimer des données professionnelles ou scolaires. | Non |


  >[!NOTE]
  >La méthode de chiffrement du paramètre **Chiffrer les données de l’application** n'est **pas** certifiée FIPS 140-2.




##  <a name="access-settings"></a>Paramètres d’accès

| Paramètre | Procédure d'utilisation | Valeur(s) par défaut |
|------|------|------|
| **Exiger un code confidentiel d’accès** | Choisissez **Oui** afin d'exiger un code confidentiel pour utiliser cette application. L’utilisateur est invité à définir ce code lors de la première exécution de l’application dans un contexte professionnel ou scolaire. Valeur par défaut = **Oui**.<br><br> Configurez les paramètres suivants pour le niveau de sécurité du code confidentiel : <ul><li>**Nombre de tentatives avant réinitialisation du code confidentiel**: spécifiez le nombre de fois qu'un utilisateur doit saisir correctement son code confidentiel avant de devoir le réinitialiser. Valeur par défaut = **5**.</li><li> **Autoriser un code confidentiel simple :** choisissez **Oui** pour autoriser les utilisateurs à utiliser des séquences de code confidentiel simples telles que 1234 ou 1111. Choisissez **Non** pour empêcher l’utilisation de séquences simples. Valeur par défaut = **Oui**. </li><li> **Longueur du code confidentiel** : spécifiez le nombre minimal de chiffres d’une séquence de code confidentiel. Valeur par défaut = **4**. </li><li> **Autoriser une empreinte digitale à la place du code confidentiel (Android 6.0 et ultérieur)** : choisissez **Oui** pour autoriser l'utilisateur à se servir de [l'authentification par empreinte digitale](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication) à la place d’un code confidentiel pour accéder à l’application. Valeur par défaut = **Oui**.<br><br> Sur les appareils Android, vous pouvez laisser l’utilisateur prouver son identité à l’aide de [l’authentification par empreinte digitale Android](https://developer.android.com/about/versions/marshmallow/android-6.0.html#fingerprint-authentication) au lieu d’un code confidentiel. Quand l’utilisateur tente d'utiliser l’application à l'aide de son compte professionnel ou scolaire, il est invité à s’identifier par empreinte digitale au lieu d’entrer un code confidentiel. </li></ul>| Exiger un code confidentiel : Oui <br><br> Tentatives de réinitialisation du code confidentiel : 5 <br><br> Autoriser un code confidentiel : Oui <br><br> Longueur du code confidentiel : 4 <br><br> Autoriser l'empreinte digitale : Oui |
| **Exiger des informations d'identification d'entreprise pour l'accès** | Choisissez **Oui** pour obliger l’utilisateur à se connecter avec son compte professionnel ou scolaire au lieu d’entrer un code confidentiel pour accéder à l’application. Si vous affectez la valeur **Oui** à ce paramètre, il se substitue à l’obligation de recourir à un code confidentiel ou à un ID tactile.  | Non |
| **Bloquer l’exécution des applications gérées sur les appareils jailbreakés ou rootés** |  Choisissez **Oui** pour empêcher l'exécution de cette application sur les appareils jailbreakés ou rootés. L’utilisateur peut encore utiliser cette application pour des tâches personnelles, mais il doit utiliser un autre appareil pour accéder aux données professionnelles ou scolaires dans cette application. | Oui |
| **Revérifier les exigences d'accès après (minutes)** | Configurez les paramètres suivants : <ul><li>**Délai** : spécifiez le temps (en minutes) au bout duquel les conditions d’accès à l’application sont revérifiées. Valeur par défaut = **30** minutes.</li><li>**Période de grâce hors connexion** : si l’appareil est hors connexion, spécifiez la durée (en minutes) au bout de laquelle les conditions d’accès à l’application sont revérifiées. Valeur par défaut = **720** minutes (12 heures).</li></ul>| Délai d'expiration : 30 <br><br> Hors connexion : 720 |
| **Intervalle en mode hors connexion avant la réinitialisation des données d’application (en jours)** | Les données professionnelles ou scolaires de cette application peuvent être réinitialisées si un appareil est resté hors connexion au-delà d'un certain temps. Spécifiez le nombre de jours pendant lesquels un appareil peut rester hors connexion avant que les données professionnelles ou scolaires soient supprimées de l’appareil. <br><br> | 90 jours |
| **Bloquer la capture d'écran et l'Assistant Android (Android 6.0 et ultérieur)** | Sélectionnez **Oui** pour bloquer les fonctionnalités de capture d’écran et d’**Assistant Android** de l’appareil lors de l’utilisation de cette application. Si vous choisissez **Oui**, l’image d’aperçu du sélecteur d’application sera floue lors de l’utilisation de cette application avec un compte professionnel ou scolaire. | Non |



<!--HONumber=Feb17_HO1-->


