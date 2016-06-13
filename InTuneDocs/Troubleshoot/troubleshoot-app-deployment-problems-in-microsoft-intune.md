---
# required metadata

title: Résoudre les problèmes de déploiement d’applications | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 05/26/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 28ac298e-fb73-4c1c-b3fd-8336639e05e6

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Résoudre les problèmes de déploiement d’applications dans Microsoft Intune
Cette rubrique vous aide à résoudre les problèmes de déploiement d’applications dans Microsoft Intune.

Si ces informations ne vous permettent pas de remédier à votre problème, consultez [Comment obtenir un support technique pour Microsoft Intune](how-to-get-support-for-microsoft-intune.md) pour accéder à d’autres types d’assistance.


## Problèmes courants de déploiement d’applications

### Si vous ne pouvez pas vous connecter au Portail d’entreprise de Microsoft Intune

1.  Vérifiez si votre compte existe dans le [portail Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) ou s’il est désactivé.

2.  Assurez-vous que vous êtes configuré sur ce compte dans le [portail Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854).

3.  Dans le [portail Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854), veillez à utiliser le nom d’utilisateur et le mot de passe appropriés pour vous connecter à Intune et vérifiez qu’il est au format : **jean@domaine.com**

### Si les informations de la page Contacter l'administrateur ne figurent pas sur le portail d'entreprise

1.  Dans la console d’administration Intune, choisissez **Administration** &gt; **Portail d’entreprise**

2.  Définissez les détails de la page **Contacter l'administrateur** .

### Si aucune application spécifique n'est affichée dans la liste

1.  Assurez-vous que vous consultez la liste d'applications d'un utilisateur ou appareil pour lequel l'application a été déployée.

2.  Vérifiez que l’appareil répond aux exigences de l’application.

### Si une erreur se produit lors du téléchargement d’une application

1.  Assurez-vous qu’il n’y a pas plus d’un téléchargement en cours par utilisateur. Chaque utilisateur peut télécharger une application à la fois.

2.  Veillez à ce qu'il n'y ait pas trop de téléchargements simultanés par compte. Attendez quelques minutes et réessayez.

3.  Si un message iOS indique que l’installation est impossible, annulée ou que vous devez réessayer, cela peut être dû à un trafic élevé. Attendez quelques minutes et réessayez.

4.  Si la barre de progression de téléchargement de l'application iOS est terminée, mais que l'installation de l'application échoue, les fichiers d'application que vous avez fournis sont peut-être erronés.

### Si un lien iOS vous dirige vers un emplacement précédent de l’iTunes App Store

1.  La session iTunes App Store actuelle s'ouvre sur la page précédente de l'application.

2.  Fermez l'iTunes App Store sur l'appareil et réessayez le lien.

### Si une erreur se produit lors du lancement d'une application iOS

1.  La date d'expiration de l'application n'est peut-être pas valide.

### Si votre application est bloquée avec le statut « en cours » lors du téléchargement

1.  Quand vous téléchargez une application, les métadonnées sont ajoutées en premier, suivies du package d'application. Une fois les métadonnées téléchargées, l'application s'affiche avec le statut « en cours ». Si votre application reste dans l’état « en cours » pendant une durée inhabituellement longue, supprimez l’application puis retéléchargez-la.

2.  Évitez de gérer le déploiement de l'application quand son état est « en cours ».

### Si une défaillance se produit lors de l'installation d'une application iOS

1.  Assurez-vous que le pare-feu de votre organisation autorise l'accès à la mise en service Apple et aux sites Web de certification.

2.  Pour plus d'informations, voir la documentation pour développeurs d'Apple.

### Erreur : L’éditeur n’existe pas
Vous utilisez **Ajouter un autre contrat logiciel** pour ajouter un contrat de licence de tiers. Vous essayez d’ajouter l’éditeur à partir de la page **Autres contrats de licence logicielle**. La page fournit une liste des éditeurs existants dans l’ordre alphabétique.
Vous entrez l’éditeur manquant, mais recevez l’erreur **L’éditeur n’existe pas**. 

Ceci est volontaire. Intune fournit le suivi de licence uniquement pour les logiciels les plus courants. Intune nécessite qu’au moins 4 comptes distincts signalent le logiciel avant que celui-ci ne soit disponible dans la charge de travail de licence.

### Si les applications gérées ne signalent pas l'état de l'installation

L’état d’installation n’a pas été collecté pour les installations d’applications gérées antérieures à la mise à jour du service Microsoft Intune en novembre 2014. Pour les appareils sur lesquels des applications gérées ont été installées avant cette mise à jour du service, mettez à jour chaque déploiement d’applications associé à l’action de déploiement appropriée (par exemple, **Installation disponible**). Chaque appareil met à jour l'application pendant la vérification automatique des applications disponibles. Pour plus d’informations, consultez [Mettre à jour des applications à l’aide de Microsoft Intune](/intune/deploy-use/update-apps-using-microsoft-intune).

## <a name="BKMK_SoftDistErrorCodes"></a>Codes d'erreur du déploiement d'applications
Le tableau suivant répertorie les erreurs courantes qui peuvent se produire lors du déploiement d’applications Intune, les causes probables et les solutions possibles pour aider à les résoudre.

|Code d’erreur|Problème possible|Solution suggérée|
|--------------|--------------------|------------------------|
|0x80073CFF<br /><br />0x80CF201C (erreur du client)|Pour installer cette application, vous devez disposer d'un système compatible avec le chargement de versions tests.|Assurez-vous que le package d'application dispose d'une signature approuvée et qu'il est installé sur un ordinateur appartenant à un domaine sur lequel la stratégie AllowAllTrustedApps est activée ou sur un ordinateur qui possède une licence de chargement de version test de Windows sur lequel la stratégie AllowAllTrustedApps est activée (appliqué quand un appareil Windows RT est inscrit).|
|0x80073CF0|Le package n'a pas pu être ouvert.|Causes possibles :<br /><br />-   Le package n’est pas signé.<br />-   Le nom de l’éditeur ne correspond pas au sujet du certificat de signature.<br /><br />Consultez le journal des événements AppxPackagingOM pour plus d'informations.|
|0x80073CF3|Échec de la mise à jour du package, d'une dépendance ou validation de conflit|Causes possibles :<br /><br />-   Le package entrant est en conflit avec un package installé.<br />-   Une dépendance de package spécifiée est introuvable.<br />-   Ce package ne prend pas en charge l’architecture de processeur correcte.<br /><br />Consultez le journal des événements AppXDeployment-Server pour plus d'informations.|
|0x80073CFB|Le package fourni est déjà installé, et la réinstallation du package est bloquée|Cette erreur peut s'afficher si vous installez un package qui n'est pas identique au package déjà installé. Confirmez que la signature numérique fait également partie du package. Lorsqu'un package est reconstruit ou resigné, ce package n'est plus identique au niveau des bits au package déjà installé. Deux options possibles s'offrent à vous pour corriger cette erreur :<br /><br />-   incrémenter le numéro de version de l’application, puis reconstruire et signer à nouveau le package ;<br />-   supprimer l’ancien package pour chaque utilisateur sur le système avant d’installer le nouveau package.|

### Étapes suivantes
Si ces informations de dépannage n’ont pas permis de vous aider, contactez le Support Microsoft comme décrit dans [Comment obtenir un support technique pour Microsoft Intune](how-to-get-support-for-microsoft-intune.md).


<!--HONumber=Jun16_HO1-->


