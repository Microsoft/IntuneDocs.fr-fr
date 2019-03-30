---
title: fichier descriptif
description: fichier descriptif
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: babebc2cbdd13b84d763363c85ab38b9053a9aaa
ms.sourcegitcommit: e23e78a563928ed2b2cbc588f2aa65678f7bb409
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58632835"
---
Ces mentions fournissent important des informations qui peuvent vous aider à préparer pour les fonctionnalités et les futures modifications Intune. 

### <a name="change-in-enrollment-workflow-with-intune-company-portal-on-corporate-ios-devices-authenticating-with-setup-assistant----1927359---"></a>Modifier dans le flux de travail d’inscription avec le portail d’entreprise Intune sur les appareils iOS d’entreprise qui s’authentifient avec l’Assistant Configuration <!-- 1927359 -->
Il existe une modification à venir dans le flux de travail pour l’inscription des appareils iOS via une des méthodes de l’inscription d’Apple appareil d’entreprise - Apple Configurator, Apple Business Manager, Apple School Manager ou le dispositif de programme d’inscription (APPLE), lorsque vous utilisez le programme d’installation Assistant pour l’authentification. Cette modification s’applique uniquement aux appareils inscrits sans affinité utilisateur.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Lorsque cette modification est appliquée sur ~~mars~~ avril, les profils d’inscription dans Intune sur le Portail Azure sont mis à jour : il sera ainsi possible de spécifier la façon dont les appareils sont authentifiés et d’indiquer s’ils peuvent recevoir l’application Portail d’entreprise. Il y aura un flux de travail amélioré pour inscrire des appareils iOS via les méthodes répertoriées ci-dessus.

- Lorsque l’inscription de nouveaux appareils et d’authentification avec l’Assistant Configuration, vous serez en mesure de choisir s’il faut déployer automatiquement de l’application portail d’entreprise. Les utilisateurs finaux ne voyez plus l’écran « Identify votre appareil » et l’écran « Confirmez votre appareil » dans la procédure d’inscription.  
- Sur les appareils déjà inscrits via l’Assistant Configuration via une des méthodes d’inscription des appareils d’entreprise d’Apple, vous devez agir si vous souhaitez activer l’accès conditionnel. Vous devrez configurer une stratégie de configuration d’application avec un fichier xml spécifique pour transmettre le portail d’entreprise à ces appareils. Directions à suivre se trouvent dans le billet de blog sur le lien informations supplémentaires. Si vous choisissez d’envoyer le portail d’entreprise de cette manière, les utilisateurs finaux ne voyez plus l’écran « Identify votre appareil » et l’écran « Confirmez votre appareil » dans la procédure d’inscription. 
- Une fois cette modification est transférée, si vous n’avez pas déployé le portail d’entreprise avec le profil de configuration d’application mentionné ci-dessus et si le téléchargement des utilisateurs finaux stocker à l’application de portail d’entreprise à partir de l’application, ils peuvent se connecter, mais ils allez Obtient un message d’erreur. Ils ne pourront utiliser l’application pour l’accès conditionnel. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que dois-je faire pour me préparer à cette modification ?
Si vous prévoyez d’utiliser le flux de travail modifié, allez voulez-vous mettre à jour votre Guide de l’utilisateur final pour indiquer que :

- Les utilisateurs finaux ne voyez plus les deux écrans indiqué plus haut dans la procédure d’inscription. 
- Ils aurez besoin pour se connecter au portail d’entreprise lorsqu’elle est automatiquement déployée et le télécharger à partir de l’app store. 

Vous pouvez choisir de créer une stratégie de configuration d’application maintenant, si nécessaire, en préparation de cette modification. Lorsque ce nouveau flux de travail déploie, vous verrez les profils d’inscription mis à jour dans la console. Nous allons également vous informer de ce déploiement via le centre de messages. Après cela, vous devez effectuer l’action afin que vos utilisateurs finaux peuvent inscrire via le programme DEP en s’authentifiant avec l’Assistant Configuration et vous pouvez utiliser le portail d’entreprise pour l’accès conditionnel.

Consultez notre blog de prise en charge sur le lien informations supplémentaires pour plus d’informations sur cette modification.

#### <a name="additional-information"></a>Informations supplémentaires 
[https://aka.ms/enrollment_setup_assistant](https://aka.ms/enrollment_setup_assistant)


### <a name="plan-for-change-user-experience-update-to-intune-company-portal-app-for-ios"></a>Planifier des modifications : mise à jour de l’expérience utilisateur dans l’application Portail d’entreprise Intune pour iOS
Nous sommes ravis d’annoncer qu’Intune va bientôt publier une mise à jour majeure de l’expérience utilisateur dans l’application iOS Portail d’entreprise. La mise à jour proposera une refonte visuelle de la page d’accueil avec des filtres avancés et un accès plus rapide aux applications et aux livres.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Cette mise à jour de l’expérience utilisateur, tout en conservant les fonctionnalités actuelles du Portail d’entreprise iOS, proposera ce qui suit :
- Page d’accueil avec l’apparence native d’iOS. 
- Fonctionnalités de filtrage sur les listes de contenu et les recherches, avec possibilité de filtrer par type de contenu (applications ou livres électroniques) et par disponibilité (gestion des appareils obligatoire ou disponible sans inscription).
- Recherche de contenu dans les livres électroniques.
- Historique de recherche pour les applications et les livres électroniques

Si vous faites partie du programme Apple TestFlight, vous serez informé de la disponibilité dans Intune de l’application mise à jour Portail d’entreprise pour iOS en préversion. Si vous ne faites pas partie du programme Apple TestFlight, il n’est pas trop tard pour vous inscrire. L’inscription vous permet d’utiliser l’application Portail d’entreprise mise à jour avant qu’elle ne soit accessible à vos utilisateurs finaux. Vous pouvez également fournir vos commentaires directement à l’équipe Intune.  

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Que puis-je faire pour me préparer à cette modification ?
Aucune action de votre part n’est requise. Ces changements seront publiés dans une version à venir de l’application iOS Portail d’entreprise. 

#### <a name="additional-information"></a>Informations supplémentaires
[https://aka.ms/cp_update_iOS](https://aka.ms/cp_update_iOS)

### <a name="check-your-delay-visibility-of-software-updates-setting-in-intune"></a>Vérifiez votre paramètre de « Délai de visibilité de mises à jour logicielles » dans Intune 

Nous avons indiqué dans MC171466 nous étions déplacer certains paramètres dans la console. La mise à jour de mars à Intune, nous allons complètement supprimer le paramètre « Mises à jour de visibilité de délai de logiciels » à partir du Panneau de stratégie de mise à jour iOS. Cela ne modifie pas la façon d’appliquent vos mises à jour logicielles planifiées, mais elle peut affecter la durée pendant laquelle la visibilité d’une mise à jour est retardée pour les utilisateurs finaux. Vous devrez peut-être effectuer une action avant la fin du mois de mars si vous utilisez ce paramètre. 

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Après la mise à jour du service Intune de février, vous remarquerez que le paramètre apparaît à la fois dans les profils de restriction d’appareil dans la console et dans iOS mettre à jour des stratégies dans le panneau de mise à jour logicielle. Lorsque vous voyez cette modification est reflétée dans la console, voici ce que vous devrez peut-être faire.

- Pour les stratégies de mise à jour existantes pour iOS : Si vous avez personnalisé configuré ce paramètre sur n’importe quelle autre que la valeur par défaut de 30 jours et souhaitez que vos configurations existantes pour le paramètre de délai de visibilité continuer à appliquer après la fin du mois de mars, vous devrez créer un nouveau profil de restriction d’appareil iOS. Ici, le paramètre de délai de visibilité devez ont les mêmes valeurs, comme dans la stratégie de mise à jour iOS existante et les mêmes groupes ciblés. Après la mise à jour de service de mars, vous ne serez n’est plus en mesure de modifier les valeurs de ce paramètre dans les stratégies de mise à jour iOS existantes dans la mesure où il ne sera plus visible dans ce panneau. Vous allez configurer ce paramètre dans les nouveaux profils à la place.
  Si la valeur de nombre de jours pendant lesquels vous pouvez différer la visibilité ne correspond pas aux deux emplacements pour les valeurs de paramètre configuré personnalisé, la visibilité de délai de paramètre ne fonctionne pas, et les utilisateurs finaux voient la mise à jour sur leurs appareils dès qu’elles sont disponibles. Cela peut avoir un impact minimal pour la plupart des clients dans la mesure où les autres paramètres dans le panneau de la stratégie de mise à jour logicielle toujours prioritaire sur ce paramètre dans la console.
- De nouvelles stratégies de mise à jour pour iOS : Si vous essayez de créer des stratégies dans le panneau de mises à jour logicielles après la mise à jour du service Intune février, vous verrez que ce paramètre grisé. Vous verrez une note dans la console de redirection vers le panneau de configuration d’appareil si vous souhaitez différer la visibilité des mises à jour.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Que puis-je faire pour me préparer à cette modification ?
Il est inutile d’agir si vous n’utilisez pas ce paramètre ou que vous ne souhaitez pas différer la visibilité des mises à jour logicielles pour vos utilisateurs finaux.

Si vous souhaitez différer la visibilité des mises à jour, démarrer la configuration du paramètre dans les nouveaux profils dans le panneau de Configuration de l’appareil sous les Restrictions d’appareil > Général. Si vous avez personnalisé de ce paramètre configuré dans iOS existants des stratégies de mise à jour, créer un nouveau profil de restriction d’appareil équivalent avec la même valeur pour « days » différer la visibilité des mises à jour à vos utilisateurs, une fois le février mettre à jour et avant le mars déploie. 

Voulez-vous mettre à jour de votre Guide de professionnels de l’informatique et informer votre support technique.

Consultez notre blog de prise en charge à des informations supplémentaires pour plus d’informations sur la façon de configurer ce paramètre.

#### <a name="additional-information"></a>Informations supplémentaires 
[https://aka.ms/Delay_visibility_setting_iOS](https://aka.ms/Delay_visibility_setting_iOS)

### <a name="plan-for-change-upcoming-fix-for-windows-10-email-profiles-in-intune---3904031--"></a>Modification planifiée : correctif à venir pour les profils de messagerie Windows 10 dans Intune <!--3904031-->
Nous mettons à jour le moyen Qu'intune écrit e-mail mettre à jour des profils pour Windows 10 en avril au service Intune pour corriger un bogue, ainsi que pour que vos profils de messagerie continuent à fonctionner dans les futures versions de Windows 10. Il est action à entreprendre après que ce correctif est déployé.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Cette modification a un impact sur vous si vous utilisez des profils de messagerie Windows 10 avec
- Le client de messagerie natif sur les ordinateurs de bureau Windows 10 ou
- Le client de messagerie Outlook sur Windows 10 Mobile

Cela affecte les deux clients de gestion des appareils mobiles (MDM) Intune autonome et hybride.

Une fois la mise à jour d’avril se déploie, vous devrez recréer ces profils dans la console Intune (dans la console d’administration de Configuration Manager si vous utilisez MDM hybride).

Si vous ne prenez pas d’action, voici ce que vous verrez pour les profils créés avant la mise à jour d’avril :

- Les profils de messagerie existants seront affiche dans l’état d’erreur dans la console Intune ou de la console d’administration de Configuration Manager, mais les utilisateurs finaux auront toujours accès à la messagerie électronique. Toutefois, après qu’une mise à jour ultérieur de Windows se déploie, ces profils ne fonctionnera pas. Les utilisateurs finaux sur les appareils ciblés par ces profils perdre l’accès à la messagerie électronique.
- Modifications apportées à ces profils après que avril n’apparaîtront pas dans les appareils ciblés.
- Réinitialisation sélective ne fonctionne pas pour la suppression de ces profils même après que le correctif est transférée en avril.

Si vous prenez des mesures et recréez les profils de messagerie, les utilisateurs finaux doivent passer par des étapes similaires à celles lorsqu’un profil de messagerie est déployé pour la première fois. Leur courrier électronique est bloqué à partir de la synchronisation jusqu'à ce qu’ils acceptent la mise à jour qui s’applique le nouveau profil.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que dois-je faire pour me préparer à cette modification ?
Vous devez prendre des mesures qu’une fois que le correctif est transférée avec la mise à jour d’avril. Nous allons vous contacter via le centre de messages lors de cette modification publiée pour que vous puissiez recréer vos profils dans Intune.

Si vous utilisez des profils de messagerie Windows 10 dans Intune, vous devez procédez comme suit :

1. Capturer les paramètres de profil Windows 10 existants
2. Supprimer l’affectation et/ou de supprimer des profils existants
3. Créer des profils en utilisant les paramètres capturés et affecter les nouveaux profils aux mêmes groupes

Vous devrez informer vos utilisateurs finaux et informer votre support technique de cette modification. Consultez le billet de blog de prise en charge dans les informations supplémentaires pour les détails de l’erreur et des instructions pour recréer ces profils.

#### <a name="additional-information"></a>Informations supplémentaires
https://aka.ms/Win10EmailProfiles