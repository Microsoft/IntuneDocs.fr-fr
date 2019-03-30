---
ms.openlocfilehash: dc86f2c22410236368753acd4dd3b66698037241
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57736858"
---

Ces mentions fournissent important des informations qui peuvent vous aider à préparer pour les fonctionnalités et les futures modifications Intune. 

### <a name="change-in-enrollment-workflow-with-intune-company-portal-on-corporate-ios-devices-authenticating-with-setup-assistant----1927359---"></a>Modifier dans le flux de travail d’inscription avec le portail d’entreprise Intune sur les appareils iOS d’entreprise qui s’authentifient avec l’Assistant Configuration <!-- 1927359 -->
Il existe une modification à venir dans le flux de travail pour l’inscription des appareils iOS via une des méthodes de l’inscription d’Apple appareil d’entreprise - Apple Configurator, Apple Business Manager, Apple School Manager ou le dispositif de programme d’inscription (APPLE), lorsque vous utilisez le programme d’installation Assistant pour l’authentification. Cette modification s’applique uniquement aux appareils inscrits sans affinité utilisateur.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Lorsque cette modification est appliquée sur ~~mars~~ avril, les profils d’inscription dans Intune sur le Portail Azure sont mis à jour : il sera ainsi possible de spécifier la façon dont les appareils sont authentifiés et d’indiquer s’ils peuvent recevoir l’application Portail d’entreprise. Il y aura un flux de travail amélioré pour inscrire des appareils iOS via les méthodes répertoriées ci-dessus. Remarque :

- Lorsque l’inscription de nouveaux appareils et d’authentification avec l’Assistant Configuration, vous serez en mesure de choisir s’il faut déployer automatiquement de l’application portail d’entreprise. Les utilisateurs finaux ne voyez plus l’écran « Identify votre appareil » et l’écran « Confirmez votre appareil » dans la procédure d’inscription.  
- Sur les appareils déjà inscrits via l’Assistant Configuration via une des méthodes d’inscription des appareils d’entreprise d’Apple, vous devez agir si vous souhaitez activer l’accès conditionnel. Vous devrez configurer une stratégie de configuration d’application avec un fichier xml spécifique pour transmettre le portail d’entreprise à ces appareils. Directions à suivre se trouvent dans le billet de blog sur le lien informations supplémentaires. Si vous choisissez d’envoyer le portail d’entreprise de cette manière, les utilisateurs finaux ne voyez plus l’écran « Identify votre appareil » et l’écran « Confirmez votre appareil » dans la procédure d’inscription. 
- Une fois cette modification est transférée, si vous n’avez pas déployé le portail d’entreprise avec le profil de configuration d’application mentionné ci-dessus et si le téléchargement des utilisateurs finaux stocker à l’application de portail d’entreprise à partir de l’application, allez pouvoir se connecter, mais ils allez Obtient un message d’erreur. Ils ne pourront utiliser l’application pour l’accès conditionnel. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Que dois-je faire pour me préparer à cette modification ?
Si vous prévoyez d’utiliser le flux de travail modifié, allez voulez-vous mettre à jour votre Guide de l’utilisateur final pour indiquer que :

- Les utilisateurs finaux ne voyez plus les deux écrans indiqué plus haut dans la procédure d’inscription. 
- Ils aurez besoin pour se connecter au portail d’entreprise lorsqu’elle est automatiquement déployée et le télécharger à partir de l’app store. 

Vous pouvez choisir de créer une stratégie de configuration d’application maintenant, si nécessaire, en préparation de cette modification. Lorsque ce nouveau flux de travail déploie, vous verrez les profils d’inscription mis à jour dans la console. Nous allons également vous informer de ce déploiement via le centre de messages. Après cela, vous devez effectuer l’action afin que vos utilisateurs finaux peuvent inscrire via le programme DEP en s’authentifiant avec l’Assistant Configuration et vous pouvez utiliser le portail d’entreprise pour l’accès conditionnel.

Consultez notre blog de prise en charge sur le lien informations supplémentaires pour plus d’informations sur cette modification.

#### <a name="additional-information"></a>Informations supplémentaires 
[https://aka.ms/enrollment_setup_assistant](https://aka.ms/enrollment_setup_assistant)


### <a name="company-portal-changes-for-ios-122-enrollment-in-intune"></a>Modifications de portail d’entreprise pour l’inscription iOS 12.2 dans Intune
Nous avons partagé sur MC172534 qu’Apple a annoncé des modifications relatives aux appareils iOS qui s’inscrivent dans les services de gestion des périphériques mobiles (GPM). La modification se produira probablement dans la version d’iOS prévue dans mars 2019, ainsi que toutes les versions futures d’iOS. Nous simplifions certaines mises à jour dans le portail d’entreprise afin de refléter les modifications d’Apple. 
 
#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Si vos utilisateurs finaux mettre à niveau leurs appareils vers iOS 12.2 et versions ultérieures, savoir qu’il existe un flux de travail modifié, et ils doivent prendre des mesures supplémentaires à effectuer d’inscription dans Intune. Après la mise à jour de mars à Intune, voici ce qu’ils amèneront faire-  

- Commencer le processus d’inscription dans l’application portail d’entreprise pour télécharger un profil de gestion
- Accédez à Paramètres > Général > profils et recherchez une notification de badge rouge
- Sélectionnez le profil approprié et cliquez sur pour l’installation
- Revenir au portail d’entreprise pour effectuer d’inscription

Pour plus d’informations sur la procédure d’inscription, cliquez sur informations supplémentaires.

Que si elles sont désinscrits et que vous avez besoin d’une nouvelle inscription, les appareils qui sont déjà inscrits et mise à niveau vers iOS 12.2 et versions ultérieures ne doivent pas être affectées. L’expérience d’inscription sur les appareils exécutant iOS 12.1 ou antérieur ne change pas avec cette nouvelle version publiée par Apple. Les appareils inscrits via un ou les méthodes de l’inscription d’entreprise d’Apple (DEP, Apple School Manager ou Apple Business Manager) ne seront pas affectés.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Que puis-je faire pour me préparer à cette modification ?
Pensez à mettre à niveau votre documentation et vos instructions pour l’utilisateur final. Vous pouvez aussi informer votre support technique de ces modifications. Nous vous tiendrons informé via notre page Nouveautés lorsque cette modification est publiée. 

Si vous souhaitez tirer parti des modifications de portail d’entreprise nous introduisons, demandez à vos utilisateurs finaux pour leur appareil de mettre à jour vers la nouvelle version d’iOS après la mise à jour de mars à Intune service lorsque 3.9.0 version de l’application portail d’entreprise. est publié.

Cliquez sur informations supplémentaires pour un billet de blog de prise en charge avec des captures d’écran de l’aperçu des modifications de portail d’entreprise.

Informations complémentaires [https://aka.ms/CP_changes_iOS12](https://aka.ms/CP_changes_iOS12)

### <a name="plan-for-change-workflow-changes-for-ios-12-enrollment-in-intune"></a>Modification planifiée : modifications de Workflow pour l’inscription iOS 12 dans Intune
Apple a annoncé des modifications relatives aux appareils iOS qui s’inscrivent dans les services MDM. La modification sera visible probablement dans la version d’iOS du printemps 2019 et dans toutes les versions futures d’iOS.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Si vos utilisateurs finaux mettent à niveau leurs appareils vers cette nouvelle version d’iOS 12 au printemps, notez qu’un workflow est modifié et que des étapes supplémentaires sont nécessaires pour l’inscription dans Intune. Lors de l’Apple apporte les modifications suivantes, les utilisateurs finaux auront pour :

- Commencer le processus d’inscription dans l’application portail d’entreprise pour télécharger un profil de gestion
- Accédez à Paramètres > Général > profils
- Sélectionnez le profil approprié et cliquez sur pour l’installation
- Revenir au portail d’entreprise pour effectuer d’inscription 

À moins qu’ils ne soient désinscrits et nécessitent une nouvelle inscription, les appareils qui sont déjà inscrits et qui effectuent la mise à niveau vers la nouvelle version d’iOS ne sont normalement pas affectés.

L’expérience d’inscription sur les appareils exécutant iOS 12.1 ou antérieur ne change pas avec cette nouvelle version publiée par Apple.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Que puis-je faire pour me préparer à cette modification ?
Pensez à mettre à niveau votre documentation et vos instructions pour l’utilisateur final. Vous pouvez aussi informer votre support technique de ces modifications. Nous vous tiendrons informé via le Centre de messages et notre page Nouveautés du moment où cette modification sera publiée.

#### <a name="additional-information"></a>Informations supplémentaires
[Prise en charge de billet de blog avec des captures d’écran et de la vidéo de la procédure d’inscription attendue](https://aka.ms/iOS_enrollment_changes).

### <a name="plan-for-change-user-experience-update-to-intune-company-portal-app-for-ios"></a>Planifier des modifications : mise à jour de l’expérience utilisateur dans l’application Portail d’entreprise Intune pour iOS
Nous sommes ravis d’annoncer qu’Intune va bientôt publier une mise à jour majeure de l’expérience utilisateur dans l’application iOS Portail d’entreprise. La mise à jour proposera une refonte visuelle de la page d’accueil avec des filtres avancés et un accès plus rapide aux applications et aux livres.

#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Cette mise à jour de l’expérience utilisateur, tout en conservant les fonctionnalités actuelles du Portail d’entreprise iOS, proposera ce qui suit :
- Page d’accueil avec l’apparence native d’iOS. 
- Fonctionnalités de filtrage sur les listes de contenu et les recherches, avec possibilité de filtrer par type de contenu (applications ou livres électroniques) et par disponibilité (gestion des appareils obligatoire ou disponible sans inscription).
- Recherche de contenu dans les livres électroniques.
- Historique de recherche pour les applications et les livres électroniques

Si vous faites partie du programme Apple TestFlight, vous serez informé de la disponibilité dans Intune de l’application mise à jour Portail d’entreprise pour iOS en préversion. Si vous ne faites pas partie du programme Apple TestFlight, il n’est pas trop tard pour vous inscrire. L’inscription vous permet d’utiliser l’application Portail d’entreprise mise à jour avant qu’elle ne soit accessible à vos utilisateurs finaux. Vous pouvez allez également fournir vos commentaires directement à l’équipe Intune.  

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Que puis-je faire pour me préparer à cette modification ?
Aucune action de votre part n’est requise. Ces changements seront publiés dans une version à venir de l’application iOS Portail d’entreprise. 

#### <a name="additional-information"></a>Informations supplémentaires
[https://aka.ms/cp_update_iOS](https://aka.ms/cp_update_iOS)


### <a name="reminder-removal-of-existing-exchange-online-to-intune-connectors----3105122---"></a>Rappel : Suppression du existant Exchange Online connecteurs Intune <!-- 3105122 -->
Dans MC165575, que nous avons partagés que nous serait supprimer Exchange Online pour la fonctionnalité du connecteur Intune Service à un Service dans une prochaine mise à jour. La mise à jour de février au service Intune, nous allons désactiver le bouton pour configurer de nouveaux connecteurs. Nous avons l’intention de supprimer tous les existant Exchange Online pour les connecteurs Intune en mars 2019.
 
#### <a name="how-does-this-affect-me"></a>Comment cela m’affecte-t-il ?
Vous recevez ce message, car, selon nos dossiers, vous utilisez peut-être la fonctionnalité de connecteur de service à service dans votre environnement. Ce connecteur prend en charge la gestion Intune des appareils Exchange Active Sync uniquement pour Exchange Online, mais ne gère pas l’infrastructure locale. En raison de la façon dont il s’affiche dans la console, le connecteur semble nécessaire pour l’accès conditionnel (CA), ce qui n’est pas le cas en réalité. Vous utilisiez ce connecteur pour comprendre l’utilisation d’Exchange Online avant d’appliquer l’accès conditionnel. Ces informations sont déjà fournies par le centre d’administration Microsoft 365. Vous trouverez ici, fournit des rapports d’utilisation pour Exchange Online, y compris l’application, tapez utilisée pour entre 7 et 180 jours. Pour plus d’informations, consultez [Office 365 rapports dans le centre d’administration - utilisation des applications de messagerie](https://docs.microsoft.com/office365/admin/activity-reports/email-apps-usage?view=o365-worldwide).  
 
Si vous utilisez ce connecteur dans votre environnement, vous ne pouvez pas surveiller ou réinitialiser les appareils Exchange Active Sync uniquement dans Intune une fois les connecteurs désactivés, en février. Cette modification devrait n’avoir aucune incidence sur vos utilisateurs finaux.
 
#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Que puis-je faire pour me préparer à cette modification ?
Si vous avez configuré le connecteur de service à service et que vous disposez d’appareils Exchange Active Sync uniquement, passez à d’autres méthodes de gestion de vos appareils. Les options suivantes sont disponibles :

- inscrire les appareils auprès de la gestion des appareils mobiles (MDM) ; 
- utiliser des stratégies Intune App Protection pour gérer vos appareils ; 
- Utiliser les contrôles Exchange, comme l’explique cette [documentation](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online) 

#### <a name="additional-information"></a>Informations supplémentaires  
https://docs.microsoft.com/intune/exchange-service-connector-configure




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
