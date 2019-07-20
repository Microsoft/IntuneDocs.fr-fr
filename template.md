---
title:
- TITRE DE L’ARTICLE | NOM DU SERVICE
description: ''
keywords: ''
author:
- GITHUB USERNAME
manager:
- ALIAS
ms.date: 04/28/2016
ms.topic: article
ms.prod: ''
ms.service: ''
ms.technology: ''
ms.assetid:
- GET ONE FROM guidgenerator.com
ms.openlocfilehash: 0a5e90c6bc6b352f4d7a0fc0ae22c65110563461
ms.sourcegitcommit: bd09decb754a832574d7f7375bad0186a22a15ab
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68354405"
---
# <a name="metadata-and-markdown-template"></a>Métadonnées et modèle Markdown

Ce modèle docs.ms contient des exemples de syntaxe Markdown, ainsi que des conseils sur la définition des métadonnées. Il est disponible dans le répertoire racine de chaque référentiel EM Pilot (par exemple, ~/Azure-RMSDocs-pr /template.md) et doit être lu comme un fichier Markdown. Vous pouvez également consulter [la version publiée](https://stage.docs.microsoft.com/en-us/rights-management/template) pour découvrir le rendu des exemples de fichiers Markdown.

Quand vous créez un fichier Markdown, vous devez copier le modèle dans un nouveau fichier, remplir les métadonnées comme indiqué ci-dessous, définir le titre H1 ci-dessus comme titre de l’article et supprimer le contenu. 


## <a name="metadata"></a>Métadonnées 

Le bloc de métadonnées complet se situe au-dessus, divisé en champs obligatoires et facultatifs. Consultez la [Fiche récapitulative des métadonnées OPS](https://ppe.msdn.microsoft.com/en-us/ce-csi-docs/ops/ops-onboarding/managing-content/content-meta-data) pour plus de détails. Remarques importantes :

- Vous **devez** ajouter un espace entre le signe deux-points (:) et la valeur d’un élément de métadonnées.
- Si un élément de métadonnées facultatif n’a pas de valeur, commentez l’élément avec le signe # (ne le laissez pas vide et n’utilisez pas « n/a »). Si vous ajoutez une valeur à un élément commenté, assurez-vous de supprimer le signe #.
- Le signe deux-points dans une valeur (par exemple, un titre) arrête l’analyseur de métadonnées. À la place, utilisez l’encodage HTML &#58; (par exemple, « title: Azure Rights Management &#58; les principes de base | Azure RMS »).
- **title** : Ce titre s’affiche dans les résultats des moteurs de recherche. Il doit se terminer par une barre verticale (|) suivie du nom du service (voir ci-dessus). Il ne doit pas être identique à votre titre H1. Il doit contenir environ 65 caractères (y compris | NOM DU SERVICE)
- **author**, **manager**, **reviewer** : Le champ author doit contenir le **nom d’utilisateur Github** de l’auteur, pas son alias.  En revanche, les champs « manager » et « reviewer » doivent contenir des alias. ms.reviewer spécifie le nom du PM associé à l’article ou au service.
- **ms.assetid** : Il s’agit du GUID de l’article en majuscules. Lorsque vous créez un fichier Markdown, récupérez un GUID sur [https://www.guidgenerator.com](https://www.guidgenerator.com). 
- **ms.prod**, **ms.service**, **ms.technology**, **ms.devlang**, **ms.topic**, **ms.tgt_pltfrm** : Des valeurs possibles pour ces éléments se trouvent [ici](https://microsoft.sharepoint.com/teams/STBCSI/Insights/_layouts/15/WopiFrame.aspx?sourcedoc=%7b7A321BF1-0611-4184-84DA-A0E964C435FA%7d&file=WEDCS_MasterList_CSIValues.xlsx&action=default).

## <a name="basic-markdown-and-gfm"></a>Formats GFM et Markdown de base

Tous les formats Markdown et Github-flavored Markdown de base sont pris en charge. Pour plus d’informations sur ce sujet, consultez :

- [Syntaxe Markdown de référence](https://daringfireball.net/projects/markdown/syntax)
- [Documentation GFM (Github-Flavored Markdown)](https://guides.github.com/features/mastering-markdown)

## <a name="headings"></a>Titres

Des exemples de titres de premier et de deuxième niveau sont présentés ci-dessus. 

Vous ne **pouvez avoir** qu’un seul titre de premier niveau dans votre rubrique, qui sera affiché comme titre sur la page.  

Les titres de deuxième niveau génèrent la table des matières sur la page qui s’affiche dans la section « Dans cet article », en dessous du titre sur la page.

### <a name="third-level-heading"></a>Titre de troisième niveau
#### <a name="fourth-level-heading"></a>Titre de quatrième niveau
##### <a name="fifth-level-heading"></a>Titre de cinquième niveau
###### <a name="sixth-level-heading"></a>Titre de sixième niveau

## <a name="text-styling"></a>Style du texte

*Italique* 

**Gras** 

~~Barré~~



## <a name="links"></a>Liens

Pour créer un lien vers un fichier Markdown dans le même référentiel, utilisez des [liens relatifs](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2). 

- Exemple : [En quoi consiste Azure Rights Management](./understand-explore/what-is-azure-rights-management.md)

Pour créer un lien vers un en-tête dans le même fichier Markdown, affichez la source de l’article publié, recherchez l’ID de la tête (par exemple, `id="blockquote"`, et liez-le avec # + ID (par exemple, `#blockquote`).

- Exemple : [Blockquotes](#blockquote)

Pour créer un lien vers un en-tête dans un fichier Markdown dans le même référentiel, utilisez des liaisons relatives + les liaisons par balise de hachage.

- Exemple : [Présentation technique de la procédure d’inscription](./understand-explore/rms-for-individuals-user-signup.md#technical-overview-of-the-sign-up-process)

Pour créer un lien vers un fichier externe, utilisez l’URL complète comme lien.

- Exemple : [Github](http://www.github.com)

Si une URL apparaît dans un fichier Markdown, elle est transformée en lien actif.

- Exemple : http://www.github.com

## <a name="lists"></a>Listes

### <a name="ordered-lists"></a>Listes triées

1. Cela 
1. Est
1. Une
1. Liste
1. Triée  


#### <a name="ordered-list-with-an-embedded-list"></a>Liste triée avec une liste intégrée

1. Voici
1. ici
1. une
1. liste
    1. Mademoiselle Rose
    1. Monsieur Violet
1. intégrée
1. triée


### <a name="unordered-lists"></a>Listes non triées

- Cela
- est
- une
- liste
- à puces


#### <a name="unordered-list-with-an-embedded-lists"></a>Liste non triée avec une liste intégrée

- Cette 
- liste 
- triée
  - Madame Pervenche
  - Monsieur Olive
- contient  
- d’autres
    1. listes
    1. Madame Leblanc
- Colonel Moutarde


## <a name="horizontal-rule"></a>Règle horizontale

---

## <a name="tables"></a>Tableaux

| Tables        | sont           | pratiques  |
| ------------- |:-------------:| -----:|
| col 3 est      | alignée à droite | 1 600 USD |
| col 2 est      | centrée      |   $12 |
| col 1 est par défaut | alignée à gauche     |    $1 |


## <a name="code"></a>Code

### <a name="codeblock"></a>Bloc de code

    function fancyAlert(arg) {
      if(arg) {
        $.docs({div:'#foo'})
      }
    }

### <a name="in-line-code"></a>Code inséré

Il s’agit d’un exemple de `in-line code`.

## <a name="blockquotes"></a>Blockquotes

> La sécheresse durait maintenant depuis dix millions d’années et le règne des terribles lézards avait depuis longtemps pris fin. Ici au niveau de l’Équateur, sur le continent qui serait un jour connu sous le nom d’Afrique, la lutte pour la vie avait atteint un nouveau paroxysme de férocité et la victoire n’était pas encore en vue. Sur cette terre désertique et desséchée, seul le petit, le rapide ou le féroce pouvait prospérer, ou même espérer survivre.

## <a name="images"></a>Images

### <a name="static-image"></a>Image statique

![il s’agit du texte de remplacement](./media/AzRMS_elements.png)

### <a name="linked-image"></a>Image liée

[![texte de remplacement de l’image liée](./media/AzRMS_elements.png)](https://azure.microsoft.com) 

### <a name="animated-gif"></a>Gif animé

![gif animé](./media/hololens.gif)

## <a name="alerts"></a>Alertes

### <a name="note"></a>Remarque

> [!NOTE]
> Il s’agit d’une REMARQUE

### <a name="warning"></a>Avertissement

> [!WARNING]
> Il s’agit d’un AVERTISSEMENT

### <a name="tip"></a>Conseil

> [!TIP]
> Il s’agit d’un CONSEIL

### <a name="important"></a>Important

> [!IMPORTANT]
> Cela est IMPORTANT

## <a name="videos"></a>Vidéos

### <a name="channel-9"></a>Channel 9

<iframe src="http://channel9.msdn.com/Series/Azure-Active-Directory-Videos-Demos/Azure-Active-Directory-Connect-Express-Settings/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>


### <a name="youtube"></a>YouTube

<iframe width="420" height="315" src="https://www.youtube.com/embed/R6_eWWfNB54" frameborder="0" allowfullscreen></iframe>

## <a name="docsms-extentions"></a>extensions docs.ms

### <a name="button"></a>Bouton

> [!div class="button"]
[liens de boutons](/rights-management)

### <a name="selector"></a>Sélectionneur

> [!div class="op_single_selector"]
- [foo](/rights-management/template.md)
- [barre](/rights-management/scratch.md)

### <a name="step-by-step"></a>Procédure pas à pas

>[!div class="step-by-step"]
[Pré](https://www.example.com)
[Suivant](https://www.example.com)
