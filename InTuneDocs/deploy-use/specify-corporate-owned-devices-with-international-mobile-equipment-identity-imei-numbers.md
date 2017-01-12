---
title: "Spécification de numéros IMEI | Microsoft Intune"
description: "Microsoft Intune permet aux administrateurs d’importer des numéros IMEI pour les plateformes d’appareils mobiles afin d’identifier les appareils mobiles d’entreprise"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1712bd39-562b-4409-9cec-155d5f4d8a39
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 656c93771776fd317f2b8d91bc59125fba1eb0b9
ms.openlocfilehash: 8b19cb740ed34b479fa8c4f5e2c1d13f13cda1f4


---

# <a name="specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers"></a>Spécifier des appareils d’entreprise avec des numéros IMEI (International Mobile Equipment Identity)
Microsoft Intune permet aux administrateurs d’importer des numéros d’identité internationale d’équipement mobile (IMEI, International Mobile Equipment Identity) pour les plateformes d’appareils mobiles afin d’identifier les appareils mobiles d’entreprise. Une fois que les appareils sont inscrits dans Intune, vous pouvez afficher ceux qui ont importé des numéros IMEI sous **Groupes** > **Vue d’ensemble** > **Tous les appareils**. **Groupe d’appareils** répertorie les appareils qui ont importé des numéros IMEI avec **Entreprise** dans la colonne **Propriété**.

1. Dans la [console d’administration Microsoft Intune](http://manage.microsoft.com), choisissez **Groupes** &gt; **Tous les appareils** &gt; **Tous les appareils d’entreprise préinscrits** &gt; **Par IMEI (toutes les plateformes)**, puis choisissez **Ajouter des appareils**. Vous pouvez ajouter des appareils de deux manières :

    -   **Chargez un fichier .csv qui contient les numéros de série** : créez une liste de valeurs séparées par des virgules (.csv) de deux colonnes sans en-tête, limitée à 5 000 appareils ou à 5 Mo par fichier .csv.

        |||
        |-|-|
        |&lt;IMEI 1&gt;|&lt;Détails de l’appareil 1&gt;|
        |&lt;IMEI 2&gt;|&lt;Détails de l’appareil 2&gt;|
        Dans un éditeur de texte, ce fichier .csv s'affiche comme suit :

        ```
        AABBBBBBCCCCCCD,PO 1234
        AABBBBBBCCCCCCE,PO 1234
        ```

    -   **Ajoutez manuellement les détails des appareils** : entrez le numéro IMEI et les détails de 15 appareils au maximum.

   Le champ *Détails* est destiné à l’administration. Vous pouvez spécifier des détails pour identifier l’appareil dans la liste des appareils d’entreprise répertoriés par ID du matériel. Ces informations ne sont pas envoyées à l’appareil, mais elles apparaissent dans la console Intune.

2.   Choisissez **Suivant**.
3.  Dans le volet **Passer en revue les appareils**, vous pouvez vérifier les numéros IMEI des appareils importés. Vous pouvez également décider s’il convient de remplacer les **détails** pour les numéros IMEI réimportés. Vous pouvez décocher la case **Remplacer** pour conserver les détails actuels. Choisissez **Terminer** pour importer les numéros IMEI.
4.  Les numéros IMEI importés et les descriptions sont ajoutés à la liste **Par IMEI (toutes les plateformes)**.

Quand un appareil avec un numéro IMEI s’inscrit dans Intune, généralement quand un utilisateur installe l’application Portail d’entreprise et termine le processus d’inscription, l’appareil est étiqueté comme appareil d’entreprise et apparaît inscrit dans le groupe **Appareils IMEI**.



<!--HONumber=Nov16_HO3-->

