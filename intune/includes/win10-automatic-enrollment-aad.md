---
ms.openlocfilehash: 748141dc494e28f25a09039a7a500411af76ace7
ms.sourcegitcommit: 52475fcd8d05d2f6b858d780ebb3d88eaadb0849
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76037609"
---
## <a name="enable-windows-10-automatic-enrollment"></a>Activer l’inscription automatique Windows 10

L’inscription automatique permet aux utilisateurs d’inscrire leurs appareils Windows 10 dans Intune. Pour s’inscrire, les utilisateurs ajoutent leur compte professionnel à leurs appareils personnels ou joignent des appareils d’entreprise à Azure Active Directory. En arrière-plan, l’appareil est inscrit et joint à Azure Active Directory. Une fois inscrit, l’appareil est géré avec Intune.

**Conditions préalables**

- Abonnement Premium à Azure Active Directory ([abonnement d’évaluation](https://go.microsoft.com/fwlink/?LinkID=816845))
- Abonnement Microsoft Intune

### <a name="configure-automatic-mdm-enrollment"></a>Configurer l’inscription automatique de MDM

1. Connectez-vous au [Portail Azure](https://portal.azure.com), puis sélectionnez **Azure Active Directory**.

   ![Capture d’écran montrant le portail Azure](../enrollment/media/windows-enroll/auto-enroll-azure-main.png)

2. Sélectionnez **Mobilité (gestion des données de référence et gestion des applications mobiles)** .

   ![Capture d’écran montrant le portail Azure](../enrollment/media/windows-enroll/auto-enroll-mdm.png)

3. Sélectionnez **Microsoft Intune**.

   ![Capture d’écran montrant le portail Azure](../enrollment/media/windows-enroll/auto-enroll-intune.png)

4. Configurez **Portée de l’utilisateur Gestion des données de référence**. Spécifiez les appareils des utilisateurs qui doivent être gérés par Microsoft Intune. Ces appareils Windows 10 peuvent s’inscrire automatiquement pour la gestion avec Microsoft Intune.

   - **Aucun** - Inscription automatique MDM désactivée
   - **Quelques-uns** : sélectionnez les **groupes** qui peuvent inscrire automatiquement leurs appareils Windows 10
   - **Tous** : tous les utilisateurs peuvent inscrire automatiquement leurs appareils Windows 10

      > [!IMPORTANT]
      > Pour les appareils BYOD, l’étendue des utilisateurs MAM est prioritaire si l’étendue des utilisateurs MAM et l’étendue des utilisateurs MDM (inscription MDM automatique) sont toutes deux activées pour tous les utilisateurs (ou pour les mêmes groupes d’utilisateurs). L’appareil utilise les stratégies Protection des informations Windows (si vous les avez configurées) au lieu d’être inscrit via MDM.
      >
      > Pour les appareils d’entreprise, la portée des utilisateurs MDM est prioritaire si les deux étendues sont activées. Les appareils sont inscrits via MDM.

   > [!NOTE]
   > La portée des utilisateurs MDM doit être définie sur un groupe Azure AD contenant des objets utilisateur.

   ![Capture d’écran montrant le portail Azure](../enrollment/media/windows-enroll/auto-enroll-scope.png)

5. Utilisez les valeurs par défaut pour les URL suivantes :
    - **URL des conditions d’utilisation de la gestion des données de référence**
    - **URL de détection MDM**
    - **URL de conformité GAM**

6. Sélectionnez **Enregistrer**.

Par défaut, l’authentification à deux facteurs n’est pas activée pour le service. Toutefois, l’authentification à deux facteurs est recommandée au moment de l’inscription d’un appareil. Pour activer l’authentification à deux facteurs, configurez un fournisseur d’authentification à deux facteurs dans Azure AD et configurez vos comptes d’utilisateur pour l’authentification multifacteur. Consultez [Bien démarrer avec le serveur Multi-Factor Authentication](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).
