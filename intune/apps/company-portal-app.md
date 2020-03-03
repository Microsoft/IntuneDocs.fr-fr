---
title: Guide de configuration de l'application Portail d’entreprise
titleSuffix: Microsoft Intune
description: Découvrez comment appliquer un logo spécifique d'entreprise à l’application Portail d’entreprise Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/24/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4c938aba7fde84536af2452f13f6ed030fa1d823
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576420"
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>Guide pratique pour configurer l’application Portail d’entreprise Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Le portail d’entreprise Microsoft Intune permet aux utilisateurs d’accéder aux données de l’entreprise et d’effectuer des tâches courantes, notamment l’inscription d’appareils ou l’installation d’applications, et d’accéder à des informations d’assistance fournies par le département informatique. En outre, l’application du portail d’entreprise permet aux utilisateurs d’accéder en toute sécurité aux ressources de l’entreprise. L’application du portail d’entreprise fournit plusieurs pages différentes, comme l’accueil, les applications, les détails des applications, les appareils et les détails des appareils. Pour rechercher rapidement des applications dans le portail d’entreprise, vous pouvez filtrer les applications sur la page Applications.

> [!IMPORTANT]
> Pour prendre en charge Firebase Cloud Messaging (FCM) de Google, vous devez mettre à jour votre application de Portail d’entreprise Android vers la dernière version.  

> [!Tip]
> Quand vous personnalisez le Portail d’entreprise, les configurations s’appliquent au site web du Portail d’entreprise et aux applications du Portail d’entreprise. Notez que les utilisateurs doivent disposer d’une licence Intune pour accéder au site web Portail d’entreprise.

La personnalisation du Portail d’entreprise Intune permet de fournir une expérience familière et utile à vos utilisateurs finaux. Pour ce faire, accédez au [centre d’administration du gestionnaire de points de terminaison Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431), sélectionnez **Administration de locataire** > **Branding et personnalisation**, puis configurez les paramètres nécessaires.

Quand un utilisateur installe une application iOS/iPadOS à partir du portail d’entreprise, il reçoit une invite. Cela se produit quand l’application iOS/iPadOS est liée à l’App Store, à un programme d’achat en volume (VPP) ou à une application métier. L’invite permet aux utilisateurs d’accepter l’action ou d’autoriser la gestion de l’application. L’invite affiche le nom de votre société, ou, lorsque le nom de votre société n’est pas disponible, le **Portail d’entreprise**. 

> [!Note]
> Si vous utilisez Azure Government, l’utilisateur final dispose de journaux des applications pour décider du mode de partage des informations, quand il lance le processus d’obtention d’aide sur un problème. Toutefois, si vous n’utilisez pas Azure Government, le Portail d’entreprise pour Windows 10 envoie les journaux des applications directement à Microsoft, quand l’utilisateur lance le processus d’obtention d’aide sur un problème. L’envoi des journaux des applications à Microsoft facilite l’analyse et la résolution des problèmes. 

## <a name="company-information-and-privacy-statement"></a>Informations et déclaration de confidentialité de l’entreprise
Le nom de l’entreprise s’affiche comme titre du Portail d’entreprise. La déclaration de confidentialité s’affiche lorsqu’un utilisateur clique sur le lien correspondant.

| Nom du champ | Longueur maximale | Plus d’informations |
|---|---|---|
|**Nom de la société**| 40 | Ce nom s’affiche comme titre du Portail d’entreprise et sous forme de texte dans l’ensemble de l’expérience utilisateur Intune. |
| **URL de la déclaration de confidentialité** |     79     | Vous pouvez spécifier la déclaration de confidentialité de votre entreprise qui s’affiche lorsque les utilisateurs cliquent sur les liens de confidentialité à partir du Portail d’entreprise. Vous devez entrer une URL valide au format `<https://www.contoso.com>`. |

> [!NOTE]
> Conformément à la politique de Microsoft et d’Apple, nous ne vendons pas les données collectées par notre service à des tiers pour une raison quelconque.

## <a name="support-information"></a>Informations concernant le support
Entrez les informations de support de votre entreprise afin de fournir à vos employés un contact pour les questions relatives à Intune.

|Nom du champ|Longueur maximale|Plus d’informations|
|---|---|---|
|**Nom du contact** | 40 | Ce nom s’affiche sur la page **Aide et support**. |
|**Numéro de téléphone** | 20 | Ce numéro de contact se trouve dans la page **Aide et support** afin de permettre aux employés de vous contacter pour obtenir de l’aide. |
|**Adresse de messagerie**| 40 | Cette adresse de contact s’affiche sur la page **Aide et support**. Vous devez entrer une adresse e-mail valide au format `alias@domainname.com`. |
|**Nom du site web**| 40 | Il s'agit du nom convivial qui s'affiche pour l'URL permettant d'accéder au site Web de support technique. Si vous spécifiez l’URL d’un site web de support technique sans aucun nom convivial, Accéder au site web du service informatique apparaît dans la page **Aide et support** du Portail d’entreprise. |
|**URL du site web**| 150 | Si vous avez un site web de support technique auquel vous aimeriez que les utilisateurs accèdent, spécifiez cette URL ici. Elle doit être au format `https://www.contoso.com`. Si vous ne spécifiez aucune URL, rien ne s’affiche pour le site web de support technique dans la page **Aide et support** du Portail d’entreprise. |
| **Informations supplémentaires**| 120 | S’affiche sur la page **Aide et support**. |


## <a name="company-identity-branding-customization"></a>Personnalisation de l’identité de la société
Vous pouvez personnaliser votre Portail d’entreprise avec le logo et le nom de votre société, un thème chromatique et un arrière-plan.

### <a name="theme-color-and-logo-in-the-company-portal"></a>Couleur de thème et logo dans le Portail d’entreprise
Appliquez une couleur de thème au portail d’entreprise. Sélectionnez une couleur standard ou entrez le code hexadécimal à six chiffres d’une couleur personnalisée.

|Nom du champ|Plus d’informations|
|---|---|
|**Sélectionnez une couleur standard ou entrez un code hexadécimal à six chiffres**| Choisissez **Standard** pour sélectionner une couleur visuellement. Choisissez **Personnalisé** pour sélectionner une couleur spécifique basée sur une valeur de code hexadécimale.|
|**Couleur du thème**| Sélectionnez une couleur de thème à appliquer au Portail d’entreprise. Vous pouvez choisir une couleur standard ou entrer un code hexadécimal spécifique. |
|**Affichage**| Indiquez si vous souhaitez afficher les **Logo et nom d’entreprise**, le **Logo d’entreprise uniquement** ou le **Nom d’entreprise uniquement**. |
|**Charger le logo de votre entreprise**|Vous pouvez charger le logo de votre entreprise pour qu’il apparaisse sur le Portail de celle-ci. Notez que la couleur du texte est automatiquement choisie pour fournir le plus haut niveau de contraste. Pour améliorer l’apparence, chargez un logo avec un arrière-plan transparent.<p><ul><li>Taille maximale de l’image : 400 px x 400 px</li><li>Taille maximale du fichier : 750 Ko</li><li>Type de fichier : PNG, JPG ou JPEG</li></ul>|

Une fois le logo chargé, la zone d’aperçu l’affiche avec la couleur de thème. Si vous avez choisi d’afficher le nom de votre société, il apparaît en noir ou blanc dans le Portail d’entreprise, la couleur automatiquement sélectionnée étant celle qui fournit le plus haut niveau de contraste avec votre couleur de thème. La zone d’aperçu à l’écran n’affiche pas le nom de votre société. 

### <a name="logo-to-use-on-white-or-light-backgrounds"></a>Logo à utiliser sur des arrière-plans blancs ou clairs
Choisissez un logo qui ressort bien sur un arrière-plan blanc ou clair.

|Nom du champ|Plus d’informations|
|---|---|
|**Charger votre logo**| Cette option est disponible si vous avez choisi d’afficher le logo de la société. Pour améliorer l’apparence, chargez un logo avec un arrière-plan transparent.<p><ul><li>Taille maximale de l’image : 400 px x 400 px</li><li>Taille maximale du fichier : 750 Ko</li><li>Type de fichier : PNG, JPG ou JPEG</li></ul>|

### <a name="brand-image-for-company-portal"></a>Image de marque pour le Portail d’entreprise

Affichez une image de marque qui reflète la marque de votre société. Après avoir enregistré vos modifications, vous pouvez choisir **Afficher un aperçu de vos paramètres** dans le portail web Intune en haut du volet pour voir à quoi ressemblent vos configurations. Notez que vous ne pouvez afficher un aperçu de l’image de la marque que sur un appareil iOS/iPadOS ; la fonctionnalité d’aperçu n’est pas disponible sur le portail web d’Intune. 

|Nom du champ|Plus d’informations|
|---|---|
|**Charger l’image de votre marque**| Cette option vous permet d’afficher une image de marque. Dans le portail d’entreprise iOS/iPadOS, elle apparaît sous la forme d’une image d’arrière-plan sur la page de profil de l’utilisateur.<p><ul><li>Largeur recommandée pour l’image : Supérieure à 1125 px (doit être d’au moins 650 px)</li><li>Taille maximale de l’image : 1,3 Mo</li><li>Type de fichier : PNG, JPG ou JPEG</li></ul>|

Une bonne image de marque peut renforcer la confiance de l’utilisateur vis-à-vis du Portail d’entreprise en présentant votre société de manière affirmée. Voici quelques conseils que vous pouvez suivre pour acquérir, choisir et optimiser l’image dans le Portail d’entreprise. 

- Contactez votre service marketing ou artistique. Peut-être a-t-il déjà un ensemble approuvé d’images de marque. Il peut également être en mesure de vous aider à optimiser les images en fonction de vos besoins. 

- Envisagez des compositions avec orientation paysage et orientation portrait. L’image doit avoir suffisamment d’arrière-plan autour du point focal. L’image peut être rognée en fonction de l’orientation, de la taille et de la plateforme de l’appareil. 

- Évitez d’utiliser une image générique, tirée d’une banque d’images. L’image doit refléter la marque de votre société et sembler familière aux utilisateurs. Si vous n’en avez pas, il est préférable de ne pas en utiliser plutôt que de recourir à une image générique dénuée de sens pour l’utilisateur. 

- Supprimez les métadonnées inutiles. Le fichier image peut être accompagné de métadonnées telles que le profil de l’appareil photo, l’emplacement géographique, le titre ou la légende. Utilisez un outil d’optimisation d’image pour éliminer ces informations afin de conserver la qualité tout en respectant la limite de taille de fichier. 

Quand une image de marque est ajoutée ou modifiée dans Intune, l’utilisateur final peut ne pas voir la modification sur les appareils iOS/iPadOS jusqu’à ce que le portail d’entreprise ait reconnu la modification au démarrage, puis qu’il ait été redémarré pour afficher l’image de marque. 

### <a name="brand-image-examples"></a>Exemples d’image de marque

L’image suivante représente un exemple de personnalisation d’image iPad :

![Capture d’écran d’exemple de personnalisation d’image iPhone](./media/company-portal-app/company-portal-app-03.png)

L’image suivante représente un exemple de personnalisation d’image iPhone :

![Capture d’écran d’exemple de personnalisation d’image iPad](./media/company-portal-app/company-portal-app-02.png)

## <a name="privacy-statement-customization"></a>Personnalisation de la déclaration de confidentialité

Vous pouvez personnaliser la déclaration de confidentialité qui s’affiche pour votre organisation sur les appareils iOS/iPadOS gérés. Ce message liste les éléments que votre organisation ne peut pas voir ou effectuer sur les appareils iOS/iPadOS gérés.

Sous **Personnalisation du portail d'entreprise** > **Message de gestion et de confidentialité des appareils**, vous pouvez :

- Accepter la valeur **Par défaut** pour utiliser la liste comme indiqué, ou
- Choisir **Personnalisé** pour personnaliser la liste des éléments que votre organisation ne peut pas voir ou effectuer sur les appareils iOS/iPadOS gérés. Vous pouvez utiliser du [Markdown](https://daringfireball.net/projects/markdown/) pour ajouter des puces, des caractères gras ou en italique et des liens.

## <a name="company-portal-derived-credentials-for-ios-devices"></a>Informations d’identification dérivées du portail d’entreprise pour les appareils iOS
Intune prend en charge les informations d’identification dérivées de vérification de l’identité personnelle (PIV) et de carte d’accès commun (CAC) en partenariat avec les fournisseurs d’informations d’identification DISA Purebred, Entrust Datacard et Intercede. Les utilisateurs finaux passent par des étapes supplémentaires après l’inscription de leur appareil iOS/iPadOS pour vérifier leur identité dans l’application Portail d’entreprise. L’activation des informations d’identification dérivées pour les utilisateurs s’effectuera en configurant au préalable un fournisseur d’informations d’identification pour votre locataire, puis en ciblant des utilisateurs ou des appareils avec un profil qui utilise les informations d’identification dérivées.

> [!NOTE]
> L’utilisateur verra des instructions sur les informations d’identification dérivées basées sur le lien que vous avez spécifié via Intune.

Pour plus d’informations sur les informations d’identification dérivées pour les appareils iOS/iPadOS, consultez [Utiliser des informations d’identification dérivées dans Microsoft Intune](~/protect/derived-credentials.md).

## <a name="dark-mode-for-ios-company-portal"></a>Mode sombre pour le Portail d’entreprise iOS

Le Mode sombre est disponible sur le Portail d’entreprise iOS. Les utilisateurs peuvent télécharger des applications de l’entreprise, gérer leurs appareils et bénéficier d’un support informatique dans le modèle de couleurs de leur choix en fonction des paramètres de l’appareil. Le Portail d’entreprise iOS correspondra automatiquement aux paramètres de l’appareil de l’utilisateur final (Mode sombre ou clair). 

## <a name="windows-company-portal-keyboard-shortcuts"></a>Raccourcis clavier du Portail d’entreprise Windows

Les utilisateurs finaux peuvent déclencher des actions de navigation, d’application et d’appareil dans le Portail d’entreprise Windows à l’aide de raccourcis clavier (accélérateurs).

Les raccourcis clavier suivants sont disponibles dans l’application Portail d’entreprise Windows.

| Domaine | Description | Raccourci clavier |
|:------------------:|:--------------:|:-----------------:|
| Menu de navigation | Navigation | Alt+M |
|  | Accueil | Alt+H |
|  | Toutes les applications | Alt+A |
|  | Applications installées | Alt+I |
|  | Envoyer des commentaires | Alt+F |
|  | Mon profil | Alt+U |
|  | Paramètres | Alt+T |
| Accueil - Vignette de l’appareil | Renommer | F2 |
|  | Supprimer | Ctrl+D ou Supprimer |
|  | Vérifier l’accès | Ctrl+M ou F9 |
| Détails sur l'appareil | Renommer | F2 |
|  | Supprimer | Ctrl+D ou Supprimer |
|  | Vérifier l’accès | Ctrl+M ou F9 |
| Détails de l’application | Installer | Ctrl+I |
| Appareils | Disponible | Ctrl+D |

Les utilisateurs finaux pourront également voir les raccourcis disponibles dans l’application Portail d’entreprise Windows.

![Capture d’écran des raccourcis disponibles dans le Portail d’entreprise Windows](./media/company-portal-app/company-portal-app-01.png)

## <a name="user-self-service-device-actions-from-the-company-portal"></a>Actions d’appareil en libre-service pour l’utilisateur à partir du portail d’entreprise

Les utilisateurs peuvent effectuer des actions sur leurs appareils locaux ou distants via l’application ou le site web du portail d’entreprise. Les actions qu’un utilisateur peut effectuer varient en fonction de la configuration et de la plateforme de l’appareil. Dans tous les cas, les actions de l’appareil à distance ne peuvent être effectuées que par l’utilisateur principal de l’appareil.
- **Mettre hors service** : supprime l'appareil de la gestion Intune. Sur le site web et l’application du portail d’entreprise, il s’agit de **Supprimer**.
- **Réinitialiser** : cette action lance une réinitialisation de l’appareil. Sur le site web du portail d’entreprise, il s’agit de **Réinitialiser**, ou **Réinitialisation des paramètres d’usine** dans l’application iOS du portail d’entreprise.
- **Renommer ** : cette action modifie le nom de l’appareil que l’utilisateur peut voir dans le portail d’entreprise. Elle ne modifie pas le nom de l’appareil local, mais uniquement le nom répertorié dans le portail d’entreprise.
- **Synchroniser** : cette action lance un archivage de l’appareil avec le service Intune. Il s’agit de **Vérifier l'état** dans le portail d’entreprise.
- **Verrouillage à distance** : cette opération verrouille l’appareil, qui nécessite alors un code confidentiel pour être déverrouillé.
- **Réinitialiser le code secret ** : cette action permet de réinitialiser le code secret de l’appareil. Sur les appareils iOS/iPadOS, le code secret est supprimé et l’utilisateur final est invité à entrer un nouveau code dans les paramètres. Sur les appareils Android pris en charge, un nouveau code secret est généré par Intune et s’affiche temporairement dans le portail d’entreprise.
- **Récupération de clé ** : cette action permet de récupérer une clé de récupération personnelle pour les appareils macOS chiffrés à partir du site web du portail d’entreprise. 

### <a name="self-service-actions"></a>Actions en libre-service

Certaines plateformes et configurations n’autorisent pas les actions d’appareil en libre-service. Le tableau ci-dessous fournit des détails supplémentaires sur les actions en libre-service :

|  | Windows 10<sup> (3)</sup> | iOS/iPadOS<sup>(3)</sup> | MacOS<sup>(3)</sup> | Android <sup>(3)</sup> |
|----------------------|--------------------------|-------------------|-----------------------------------|-------------------------|
| Mettre hors service | Disponible <sup>(1)</sup> | Disponible | Disponible | Disponible <sup>(7)</sup> |
| Réinitialisation | Disponible | Disponible<sup>(5)</sup> | NA | Disponible <sup>(7)</sup> |
| Renommer <sup>(4)</sup> | Disponible | Disponible | Disponible | Disponible |
| Synchroniser | Disponible | Disponible | Disponible | Disponible |
| Verrouillage à distance | Uniquement Windows Phone | Disponible | Disponible | Disponible |
| Réinitialiser le code secret | Uniquement Windows Phone | Disponible<sup>(8)</sup> | NA | Disponible <sup>(6)</sup> |
| Récupération de clé | NA | NA | Disponible <sup>(2)</sup> | NA |

<sup>(1)</sup> **Retirer** est toujours bloqué sur les appareils Windows joints à Azure AD.<br>
<sup>(2)</sup> **Récupération de clé** pour MacOS est disponible seulement via le portail web.<br>
<sup>(3)</sup> Toutes les actions à distance sont désactivées si vous utilisez une inscription du gestionnaire d’inscription d’appareil.<br>
<sup>(4)</sup> **Renommer** change le nom de l’appareil seulement sur l’application Portail d’entreprise ou Portail web, et non pas sur l’appareil lui-même.<br>
<sup>(5)</sup> **Réinitialiser** n’est pas disponible sur les appareils iOS inscrits par l’utilisateur.<br>
<sup>(6)</sup> **Réinitialiser le code secret** n’est pas pris en charge sur certaines configurations Android et Android Entreprise. Pour plus d’informations, consultez [Réinitialiser ou supprimer un code secret de l’appareil dans Intune](../remote-actions/device-passcode-reset.md).<br>
<sup>(7)</sup> **Retirer** et la **Réinitialiser** ne sont pas disponibles dans les scénarios de propriétaire d’appareils Android Entreprise (COPE, COBO, COSU).<br> 
<sup>(8)</sup> **Réinitialiser le code secret** n’est pas pris en charge sur les appareils iOS inscrits par l’utilisateur.

## <a name="next-steps"></a>Étapes suivantes

- [Ajouter manuellement l’application Portail d’entreprise Windows 10 à l’aide de Microsoft Intune](company-portal-app.md)
