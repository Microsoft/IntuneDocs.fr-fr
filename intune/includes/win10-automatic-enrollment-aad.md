---
ms.openlocfilehash: 3aadafbcf9c9208e7c87504c5459731de1e402b5
ms.sourcegitcommit: 614c4c36cfe544569db998e17e29feeaefbb7a2e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "71302597"
---
## <a name="enable-windows-10-automatic-enrollment"></a>Activer l’inscription automatique Windows 10

L’inscription automatique permet aux utilisateurs d’inscrire leurs appareils Windows 10 dans Intune. Pour s’inscrire, les utilisateurs ajoutent leur compte professionnel à leurs appareils personnels ou joignent des appareils d’entreprise à Azure Active Directory. En arrière-plan, l’appareil est inscrit et joint à Azure Active Directory. Une fois inscrit, l’appareil est géré par Intune.

**Prérequis**
- Abonnement Premium à Azure Active Directory ([abonnement d’évaluation](http://go.microsoft.com/fwlink/?LinkID=816845))
- Abonnement Microsoft Intune


### <a name="configure-automatic-mdm-enrollment"></a>Configurer l’inscription automatique de MDM

1. Connectez-vous au [Portail Azure](https://portal.azure.com), puis sélectionnez **Azure Active Directory**.

   ![Capture d’écran du portail Azure](../media/auto-enroll-azure-main.png)

2. Sélectionnez **Mobilité (MDM et GAM)** .

   ![Capture d’écran du portail Azure](../media/auto-enroll-mdm.png)

3. Sélectionnez **Microsoft Intune**.

   ![Capture d’écran du portail Azure](../media/auto-enroll-intune.png)

4. Configurez **Portée des utilisateurs MDM**. Spécifiez les appareils des utilisateurs qui doivent être gérés par Microsoft Intune. Ces appareils Windows 10 peuvent s’inscrire automatiquement pour la gestion avec Microsoft Intune.

   - **Aucun** - Inscription automatique MDM désactivée
   - **Quelques-uns** : sélectionnez les **groupes** qui peuvent inscrire automatiquement leurs appareils Windows 10
   - **Tous** : tous les utilisateurs peuvent inscrire automatiquement leurs appareils Windows 10

      > [!IMPORTANT]
      > Pour les appareils BYOD, l’étendue des utilisateurs MAM est prioritaire si l’étendue des utilisateurs MAM et l’étendue des utilisateurs MDM (inscription MDM automatique) sont toutes deux activées pour tous les utilisateurs (ou pour les mêmes groupes d’utilisateurs). L’appareil utilise les stratégies Protection des informations Windows (si vous les avez configurées) au lieu d’être inscrit via MDM.
      >
      > Pour les appareils d’entreprise, la portée des utilisateurs MDM est prioritaire si les deux étendues sont activées. Les appareils sont inscrits via MDM.

   > [!NOTE]
   > La portée des utilisateurs MDM doit être définie sur un groupe Azure AD contenant des objets utilisateur.

   ![Capture d’écran du portail Azure](../media/auto-enroll-scope.png)

5. Utilisez les valeurs par défaut pour les URL suivantes :
    - **URL des conditions d'utilisation de MDM**
    - **URL de détection de MDM**
    - **URL de conformité GAM**

6. Sélectionnez **Enregistrer**.

Par défaut, l'authentification à deux facteurs n'est pas activée pour le service. Toutefois, l’authentification à deux facteurs est recommandée au moment de l’inscription d’un appareil. Pour activer l’authentification à deux facteurs, configurez un fournisseur d’authentification à deux facteurs dans Azure AD et configurez vos comptes d’utilisateur pour l’authentification multifacteur. Consultez [Bien démarrer avec le serveur Multi-Factor Authentication](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).
