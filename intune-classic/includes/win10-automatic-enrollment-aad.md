---
ms.openlocfilehash: fbfff91d2993becc99e2132285bef78d245ff50e
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "35289501"
---
## <a name="enable-windows-10-automatic-enrollment"></a>Activer l’inscription automatique Windows 10

L’inscription automatique permet aux utilisateurs d’inscrire leurs appareils Windows 10 dans Intune lorsqu’ils ajoutent leur compte professionnel à des appareils personnels ou lorsqu’ils joignent leurs appareils d’entreprise à Azure Active Directory. En arrière-plan, l’appareil de l’utilisateur s’inscrit et rejoint Azure Active Directory. Une fois inscrit, l’appareil est géré avec Intune.

**Prérequis**
- Abonnement Premium à Azure Active Directory ([abonnement d’évaluation](http://go.microsoft.com/fwlink/?LinkID=816845))
- Abonnement Microsoft Intune


### <a name="configure-automatic-mdm-enrollment"></a>Configurer l’inscription automatique de MDM

1. Connectez-vous au [Portail de gestion Azure](https://portal.azure.com) (https://manage.windowsazure.com) et sélectionnez **Azure Active Directory**.

   ![Capture d’écran du portail Azure](../media/auto-enroll-azure-main.png)

2. Sélectionnez **Mobilité (MDM et GAM)**.

   ![Capture d’écran du portail Azure](../media/auto-enroll-mdm.png)

3. Sélectionnez **Microsoft Intune**.

   ![Capture d’écran du portail Azure](../media/auto-enroll-intune.png)

4. Configurez **Portée des utilisateurs MDM**. Spécifiez les appareils des utilisateurs qui doivent être gérés par Microsoft Intune. Les appareils Windows 10 de ces utilisateurs sont automatiquement inscrits à la gestion avec Microsoft Intune.

   - **Aucune.**
   - **Quelques-uns**
   - **Tous**

   ![Capture d’écran du portail Azure](../media/auto-enroll-scope.png)

5. Utilisez les valeurs par défaut pour les URL suivantes :
   - **URL des conditions d'utilisation de MDM**
   - **URL de détection de MDM**
   - **URL de conformité GAM**

6. Sélectionnez **Enregistrer**.

Par défaut, l'authentification à deux facteurs n'est pas activée pour le service. Toutefois, l’authentification à deux facteurs est recommandée au moment de l’inscription d’un appareil. Avant d’exiger l’authentification à deux facteurs pour ce service, vous devez configurer un fournisseur d’authentification à deux facteurs dans Azure Active Directory et configurer vos comptes d’utilisateur pour l’authentification multifacteur. Consultez [Bien démarrer avec le serveur Multi-Factor Authentication](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).
