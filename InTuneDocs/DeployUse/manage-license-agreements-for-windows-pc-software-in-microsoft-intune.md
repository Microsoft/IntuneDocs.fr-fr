---
# required metadata

title: Gérer les contrats de licence des logiciels de PC Windows | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: c59d8635-3f66-40f5-824a-a71c738e0341

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Gérer les contrats de licence des logiciels de PC Windows dans Microsoft Intune
Microsoft Intune permet d’ajouter et de gérer les informations de contrat de licence pour les logiciels achetés par l’intermédiaire de contrats de licence en volume Microsoft et pour des logiciels Microsoft ou non achetés par d’autres moyens. Vous pouvez aussi organiser ces informations en groupes logiques.

> [!IMPORTANT]
> Cette fonctionnalité est fournie uniquement à des fins pratiques et l'exactitude des informations n'est pas garantie. Ne vous fiez pas à elle pour valider la conformité avec les contrats de licence en volume Microsoft. Microsoft n’utilisera pas les données recueillies pour étudier les violations potentielles ou le respect des contrats de licence.
> 
> Les licences que vous ajoutez à Intune n’affectent ni vos contrats de licence ni vos droits d’utilisation de vos logiciels.  Par exemple, en supprimant une paire de numéros de contrats de licence dans Intune, vous ne supprimez ni n’annulez les contrats de licence établis entre vous et Microsoft.

Dans l’espace de travail **Licences** de la console d’administration d’Intune, vous pouvez :

-   ajouter et modifier des contrats de licence en volume Microsoft ;

-   ajouter et modifier d’autres contrats de licence logicielle ;

-   gérer des licences et des groupes ;

-   Comparer les informations de droit qu’Intune récupère de VLSC (Volume Licensing Service Center) à l’inventaire de logiciels Microsoft qu’Intune détecte sur vos PC Windows gérés.

De plus, vous pouvez générer des rapports qui indiquent le nombre d’installations et de licences pour des titres de logiciels. Les rapports de licence peuvent vous aider à évaluer votre position de licence dans son ensemble pour les logiciels Microsoft et non Microsoft.

> [!TIP] L’espace de travail **Licences** ne s’affiche pas dans la console d’administration tant que vous ne gérez pas au moins un PC Windows avec le logiciel client Intune pour PC Windows.

## Ajouter des contrats de licence en volume Microsoft
Les contrats de licence en volume Intune fournissent des informations de licence pour les logiciels achetés par le biais de contrats de licence en volume Microsoft. Vous pouvez ajouter des contrats de licence en volume Microsoft à Intune en fournissant des paires de numéros de contrats associées. Les numéros de contrat ou d'autorisation doivent correspondre aux numéros de licence ou d'inscription corrects. Les paires de numéros de contrats sont obtenues lorsque vous achetez vos contrats de licence depuis le [Centre de gestion des licences en volume Microsoft (VLSC)](http://go.microsoft.com/fwlink/?LinkID=223842).

1.  Dans la [console d'administration Microsoft Intune](https://account.manage.microsoft.com/admin/default.aspx), cliquez sur **Licences**.

2.  Dans la page **Ajouter des contrats** sous **Choisir le type de contrat**, sélectionnez **Contrat de licence en volume**.

3.  Dans la section **Ajouter des détails de contrat** , choisissez l’une des options suivantes :

    -   **Télécharger un fichier CSV contenant les détails du contrat** : cliquez sur Parcourir, puis sélectionnez le fichier CSV que vous voulez charger.

        -   Le fichier peut contenir deux ou trois colonnes ; deux uniquement pour les paires de contrats, ou trois si vous voulez ajouter un nom convivial pour chaque paire de contrats.

        -   Le nombre total de caractères dans une paire de numéros de contrats doit être de 16 caractères ASCII maximum.

        -   Les seuls caractères pris en charge sont les caractères ASCII.

        -   Les caractères suivants ne sont pas autorisés dans les noms des contrats : **~ ! @ # $ ^ &amp; &#42; ( ) = + [ ] { } \ | ; : ’ " &lt; &gt; /**. Les espaces sont autorisés dans le nom.

        -   Le nom du fichier ne doit pas contenir plus de 128 caractères.

        -   Le fichier doit contenir au moins une paire de contrats et ne peut pas en contenir plus de 5 000.

        **Format du fichier**

        Vous pouvez créer ce fichier en ajoutant vos paires de contrats à un nouveau document de texte brut dans l’un des formats suivants, en fonction du type d’organisation que vous avez inscrit auprès du VLSC. Spécifiez une paire de numéros de contrats par ligne.

        -   **Clients Open Value :** *Numéro de contrat*, *répéter le numéro de contrat*, *nom du contrat*

        -   **Clients Open :** *Numéro d'autorisation*, *numéro de licence correspondant*, *nom du contrat*

        -   **Client Select et Enterprise :** *Numéro de contrat*, *numéro d'inscription correspondant*, *nom du contrat*

        Le formulaire **Ajouter des contrats** vous invite à rechercher ce fichier quand vous ajoutez un nouveau contrat.

        L'exemple suivant montre le contenu d'un fichier .csv pour un client Open Value.

        `01-07001, 01-07001, Office agreements`

    -   **Ajouter manuellement les détails du contrat** : fournissez les informations suivantes, puis tapez les paires de numéros de contrats dans les zones **Numéro de contrat/d’autorisation** et **Numéro de client/d’inscription/de licence**. Après avoir tapé les deux numéros, cliquez sur l'icône **Ajouter une paire** pour enregistrer vos numéros, puis ajoutez une nouvelle paire en option.

        -   **Nom du contrat** : spécifiez un nom unique pour le contrat.

            Le nom du contrat peut comprendre 256 caractères au maximum et ne peut pas contenir les caractères suivants : **~ ! @ # $ ^ &amp; &#42; ( ) = + [ ] { } \ | ; : ’ " &lt; &gt; /**. Les espaces sont autorisés dans le nom.

        -   **Numéro de contrat/d’autorisation** : entrez le numéro de contrat/d’autorisation de la paire de licence.

        -   **Numéro de client/d’inscription/de licence** : entrez le numéro de client/d’inscription/de licence de la paire de licence.

        > [!NOTE] Si vous ajoutez plusieurs paires de numéros de contrats, Intune crée un contrat avec le nom que vous spécifiez, et toutes les paires que vous avez ajoutées feront partie de ce contrat.

    Vous pouvez cliquer sur **+** pour ajouter une autre paire de numéros de contrats ou sur **-** pour supprimer une paire de numéros de contrats que vous avez déjà entrée.

4.  Dans la zone **Sélectionner le groupe de licence** , effectuez l'une des opérations suivantes :

    -   **Ajouter les contrats au groupe Contrats non attribués**. Sélectionnez cela si vous ne voulez pas ajouter les nouveaux contrats à un groupe de licences.

    -   **Ajouter les contrats à un nouveau groupe de licences** - Indiquez un nom pour le nouveau groupe de licences.

    -   **Ajouter les contrats à un groupe de licences existant** - Dans la liste **Nom du groupe**, sélectionnez le groupe de licences auquel vous souhaitez ajouter les contrats.

5.  Cliquez sur **OK**.

L’affichage **Tous les contrats** apparaît, puis Intune se connecte au Centre de gestion des licences en volume Microsoft pour valider les paires de numéros de contrats que vous avez fournies.

Pour mettre à jour les informations de licence en volume après avoir ajouté des contrats de licence dans Intune, sur la page **Vue d’ensemble des licences**, cliquez sur **Actualiser maintenant**. Cette action récupère les informations de licence en cours depuis le [Centre de gestion des licences en volume Microsoft (VLSC)](http://go.microsoft.com/fwlink/?LinkId=223842).

> [!IMPORTANT] Jusqu’à l’actualisation des informations de licence en volume, vous pouvez voir différentes informations dans la liste des contrats ainsi que les informations des droits sur la page **Vue d’ensemble des contrats**.

Une fois les informations de licence en volume actualisées, vous pouvez comparer les informations de licence aux logiciels Microsoft détectés dans l’espace de travail **Applications** . Vous pouvez aussi exécuter les rapports de licence suivants :

-   **Rapports d’achat de licence** : permet d’afficher les logiciels sous licence figurant dans les groupes de licences que vous sélectionnez pour détecter d’éventuelles lacunes dans la couverture des contrats de licence.

-   **Rapports d’installation de licence** : aide à déterminer si vous disposez d’une couverture de contrats de licence suffisante.

> [!NOTE] Le **Nom du produit** affiché pour tous les contrats de licence en volume Microsoft est **Non disponible**.

## Ajouter et modifier d’autres contrats de licence logicielle
Vous pouvez aussi ajouter d’autres types de contrats de licence à Intune en plus des contrats de licence en volume Microsoft. Ces contrats peuvent inclure des logiciels non Microsoft ou des logiciels Microsoft achetés chez un revendeur.

> [!IMPORTANT]
> Vous devez avoir inscrit au moins un PC Windows dans Intune pour pouvoir ajouter un contrat.  De plus, vous devez avoir chargé un package logiciel sous licence que vous souhaitez utiliser sur au moins un ordinateur inscrit.

### Pour ajouter d'autres contrats de licence logicielle

1.  Dans la [console d'administration Microsoft Intune](https://account.manage.microsoft.com/admin/default.aspx), cliquez sur **Licences**.

2.  Cliquez sur **Ajouter des contrats** dans la section **Autres contrats de licence logicielle** .

3.  Sélectionnez **Autres contrats de licence logicielle** dans la section **Choisir le type de contrat** de la page **Ajouter des contrats** .

4.  Dans la zone **Ajouter des détails de contrat** , spécifiez les éléments suivants :

    -   **Agreement name** (obligatoire). Le nom du contrat peut comprendre 256 caractères au maximum et ne peut pas contenir les caractères suivants : **~ ! @ # $ ^ &amp; &#42; ( ) = + [ ] { } \ | ; : ’ " &lt; &gt; /**. Les espaces sont autorisés dans le nom.

    -   **Éditeur** (obligatoire). Lorsque vous commencez à saisir un nom d'éditeur, le service récupère tous les noms d'éditeurs contenant les lettres que vous tapez. Par exemple, si vous tapez « soft », le service récupère tous les noms des éditeurs contenant « soft », tels que « Microsoft » et « Microsoft Research ». Les noms d'éditeurs sont extraits du catalogue de logiciels. Avant de saisir le nom de produit, vous devez sélectionner l'éditeur.

        > [!IMPORTANT]
        > Il est possible que l’entreprise que vous voulez ajouter ne figure dans cette liste. Vous ne pouvez ajouter des contrats de licence logicielle que pour les entreprises déjà présentes dans le catalogue de logiciels. Cependant, Microsoft s’emploie constamment à ajouter les titres de logiciels les plus populaires. Vous pouvez envoyer une demande d’ajout d’une entreprise à cette liste via le [site Intune Uservoice](https://microsoftintune.uservoice.com/).

    -   **Nom du produit** (obligatoire). Lorsque vous commencez à saisir un nom de produit, le service récupère tous les noms de produits contenant les lettres que vous tapez. Vous devez spécifier un **Éditeur** avant de pouvoir spécifier un **Nom de produit**.

    -   **Nombre de licences** (obligatoire). Entrez le nombre de licences achetées.

    -   **Date de début de la licence**. Entrez la date de début de couverture de la licence.

    -   **Date de fin de la licence**. Entrez la date de fin de couverture de la licence.

    -   **Détails du contrat**. Vous pouvez éventuellement spécifier des informations de contact, des clés d'enregistrement et d'autres informations.

5.  Dans la zone **Sélectionner le groupe de licence** , effectuez l'une des opérations suivantes :

    -   Sélectionnez **Ajouter les contrats au groupe Contrats non attribués** si vous ne voulez pas ajouter les nouveaux contrats à un groupe de licences nouveau ou existant. Vous pouvez ajouter les contrats à des groupes de licences définis par l'utilisateur à tout moment.

    -   Sélectionnez **Ajouter les contrats à un nouveau groupe de licences** pour ajouter les nouveaux contrats à un nouveau groupe de licences. Vous êtes invité à fournir un nom pour le nouveau groupe de licences.

    -   Sélectionnez **Ajouter les contrats à un groupe de licences existant** pour ajouter les nouveaux contrats à un groupe de licences existant. Dans la liste **Nom du groupe** , sélectionnez le groupe de licences auquel vous souhaitez ajouter les contrats.

6.  Cliquez sur **OK**.

La liste **Tous les contrats** s'affiche.

## Gérer les contrats de licence
Des contrats de licence logicielle peuvent être ajoutés à des groupes de licences. Vous pouvez utiliser des groupes de licences pour organiser vos contrats de licence en unités logiques pour votre organisation. De plus, vous pouvez supprimer des contrats de licence que vous avez créés précédemment.

|||
|-|-|
|Tâche|Détails|
|Créer un groupe de licences|Dans la page **Vue d’ensemble** de l’espace de travail **Licences** , cliquez sur **Créer un groupe de licences** dans le menu **Tâches** . **Remarque :** Vous pouvez créer un nombre total maximum de 500 groupes de licences.|
|Renommer un groupe de licences|Dans l’espace de travail **Licences** , choisissez un groupe de licences, puis cliquez sur **Modifier le groupe de licences** dans le menu **Tâches** .|
|Supprimer un groupe de licences|Dans l’espace de travail **Licences** , choisissez un groupe de licences, puis cliquez sur **Supprimer le groupe de licences** dans le menu **Tâches** . **Conseil :** Les licences qui résidaient dans le groupe supprimé sont déplacées vers le groupe de licences **Contrats non attribués**.|
|Supprimer un contrat de licence|Dans l’espace de travail **Licences** , choisissez un contrat, puis cliquez sur **Supprimer**. **Conseil :** Après avoir supprimé les contrats de licence en volume, pour mettre à jour les informations de licence, cliquez sur **Actualiser maintenant** sur la page **Vue d’ensemble des licences** ou sous l’onglet **Général** pour un groupe de licences spécifique.|





<!--HONumber=Jun16_HO1-->


