---
title: Graphique des API pour configurer des appareils dans Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Afficher la liste de toutes les entités de l’API Graph avec le CSP Windows correspondant et décalage URI sur les appareils Windows 10 et versions ultérieures utilisé lors de la configuration des appareils dans Microsoft Intune. Consultez l’API correspondant et le fournisseur de services cryptographiques pour les PC partagés, protection de point de terminaison, Windows Defender advanced threat protection, protection d’identité, Windows 10 équipes, plein écran et Windows Update for Business.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/04/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 177448eaebfb7e78ead7bc2e0eb7443a7d8c7d49
ms.sourcegitcommit: 9a4c5b6c2ce511edaeace25426a23f180cb71e15
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/07/2019
ms.locfileid: "57566792"
---
# <a name="graph-apis-and-matching-windows-10-csps-used-in-intune"></a>API Graph et correspondant à Windows 10 CSP utilisé dans Intune

Microsoft Intune utilise le [entités de l’API Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview) (ouvre un autre site Docs) pour configurer des appareils (**Intune** > **configuration de l’appareil**) exécutant Windows 10 et versions ultérieures. L’API Graph utilise des fournisseurs de services de configuration (CSP) pour lire, définir, modifier, et/ou supprimer des paramètres de configuration sur les appareils.

Cette liste s’applique à :

- Windows 10 et versions ultérieures

Cet article répertorie les entités de graphes et leurs fournisseurs de services cryptographiques correspondant Windows 10 et le décalage d’URI.

Ces informations sont utiles pour un large éventail de scénarios. Par exemple, ce qui est utilisé par Intune, consultez les paramètres à inclure dans des configurations personnalisées OMA-URI et ainsi de suite. 

## <a name="windows-10-csps"></a>Fournisseurs de services cloud Windows 10

Pour plus d’informations sur les fournisseurs de services de configuration de Windows 10, consultez le [référence de fournisseur de service de configuration](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference) (ouvre un autre site Docs).

## <a name="graph-api-properties-to-csp-mapping"></a>Propriétés de l’API Graph au mappage de CSP

La liste suivante présente la plupart des entités de l’API de graphique utilisé par Microsoft Intune pour la configuration de périphérique Windows 10. Il montre également le fournisseur de services cryptographiques correspondant Windows 10 et le décalage d’URI.

Pour afficher les versions de Windows 10 que les API suivantes s’appliquent, utilisez Windows 10 [référence de fournisseur de service de configuration](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference) (ouvre un autre site Docs).

#### <a name="editionupgradeconfigurationlicense"></a>EditionUpgradeConfiguration.License 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/WindowsLicensing  
**Décalage d’URI**: /UpgradeEditionWithLicense

#### <a name="editionupgradeconfigurationlicensetype"></a>EditionUpgradeConfiguration.LicenseType 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/WindowsLicensing  
**Décalage d’URI**: /LicenseKeyType

#### <a name="editionupgradeconfigurationproductkey"></a>EditionUpgradeConfiguration.ProductKey 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/WindowsLicensing  
**Décalage d’URI**: /UpgradeEditionWithProductKey

#### <a name="editionupgradeconfigurationwindowssmode"></a>EditionUpgradeConfiguration.WindowsSMode 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/WindowsLicensing  
**Décalage d’URI**: / SMode/SwitchingPolicy

#### <a name="sharedpcconfigurationaccountmanagerpolicy"></a>SharedPCConfiguration.AccountManagerPolicy 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SharedPC  
**Décalage d’URI**: /DeletionPolicy, /DiskLevelCaching, /InactiveThreshold, /DiskLevelDeletion

#### <a name="sharedpcconfigurationaccountmanagerpolicy-windows-holographic-for-business-edition-targeted-devices"></a>SharedPCConfiguration.AccountManagerPolicy (Windows Holographic for Business appareils d’édition ciblée) 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/AccountManagement  
**Décalage d’URI**: /DeletionPolicy, /StorageCapacityStartDeletion, /StorageCapacityStopDeletion, /ProfileInactivityThreshold

#### <a name="sharedpcconfigurationallowedaccounts"></a>SharedPCConfiguration.AllowedAccounts 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SharedPC  
**Décalage d’URI**: /AccountModel

#### <a name="sharedpcconfigurationallowlocalstorage"></a>SharedPCConfiguration.AllowLocalStorage 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SharedPC  
**Décalage d’URI**: /RestrictLocalStorage

#### <a name="sharedpcconfigurationdisableaccountmanager"></a>SharedPCConfiguration.DisableAccountManager 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SharedPC  
**Décalage d’URI**: /EnableAccountManager

#### <a name="sharedpcconfigurationdisableedupolicies"></a>SharedPCConfiguration.DisableEduPolicies 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SharedPC  
**Décalage d’URI**: /SetEduPolicies

#### <a name="sharedpcconfigurationdisablepowerpolicies"></a>SharedPCConfiguration.DisablePowerPolicies 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SharedPC  
**Décalage d’URI**: /SetPowerPolicies

#### <a name="sharedpcconfigurationdisablesigninonresume"></a>SharedPCConfiguration.DisableSignInOnResume 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SharedPC  
**Décalage d’URI**: /SignInOnResume

#### <a name="sharedpcconfigurationenabled"></a>SharedPCConfiguration.Enabled 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SharedPC  
**Décalage d’URI**: /EnableSharedPCMode

#### <a name="sharedpcconfigurationidletimebeforesleepinseconds"></a>SharedPCConfiguration.IdleTimeBeforeSleepInSeconds 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SharedPC  
**Décalage d’URI**: /InactiveThreshold

#### <a name="sharedpcconfigurationkioskappdisplayname"></a>SharedPCConfiguration.KioskAppDisplayName 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SharedPC  
**Décalage d’URI**: /KioskModeUserTileDisplayText

#### <a name="sharedpcconfigurationkioskappusermodelid"></a>SharedPCConfiguration.KioskAppUserModelId 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SharedPC  
**Décalage d’URI**: /KioskModeAUMID

#### <a name="sharedpcconfigurationlocalstorage"></a>SharedPCConfiguration.LocalStorage 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SharedPC  
**Décalage d’URI**: /RestrictLocalStorage

#### <a name="sharedpcconfigurationmaintenancestarttime"></a>SharedPCConfiguration.MaintenanceStartTime 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SharedPC  
**Décalage d’URI**: /MaintenanceStartTime

#### <a name="sharedpcconfigurationsetaccountmanager"></a>SharedPCConfiguration.SetAccountManager
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SharedPC  
**Décalage d’URI**: /EnableAccountManager

#### <a name="sharedpcconfigurationsetedupolicies"></a>SharedPCConfiguration.SetEduPolicies 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SharedPC  
**Décalage d’URI**: /SetEduPolicies

#### <a name="sharedpcconfigurationsetpowerpolicies"></a>SharedPCConfiguration.SetPowerPolicies 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SharedPC  
**Décalage d’URI**: /SetPowerPolicies

#### <a name="sharedpcconfigurationsigninonresume"></a>SharedPCConfiguration.SignInOnResume 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SharedPC  
**Décalage d’URI**: /SignInOnResume

#### <a name="windows10endpointconfigurationsmartscreenblockoverrideforfiles"></a>Windows10endpointconfiguration.smartScreenBlockOverrideForFiles 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/SmartScreen/PreventOverrideForFilesInShell

#### <a name="windows10endpointprotectionconfigurationapplicationguardallowfilesaveonhost"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowFileSaveOnHost 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**Décalage d’URI**: / paramètres/SaveFilesToHost

#### <a name="windows10endpointprotectionconfigurationapplicationguardallowpersistence"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowPersistence 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**Décalage d’URI**: / paramètres/AllowPersistence

#### <a name="windows10endpointprotectionconfigurationapplicationguardallowprinttolocalprinters"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowPrintToLocalPrinters 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**Décalage d’URI**: / paramètres/PrintingSettings

#### <a name="windows10endpointprotectionconfigurationapplicationguardallowprinttonetworkprinters"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowPrintToNetworkPrinters 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**Décalage d’URI**: / paramètres/PrintingSettings

#### <a name="windows10endpointprotectionconfigurationapplicationguardallowprinttopdf"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowPrintToPDF 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**Décalage d’URI**: / paramètres/PrintingSettings

#### <a name="windows10endpointprotectionconfigurationapplicationguardallowprinttoxps"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowPrintToXPS 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**Décalage d’URI**: / paramètres/PrintingSettings

#### <a name="windows10endpointprotectionconfigurationapplicationguardallowvirtualgpu"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardAllowVirtualGPU 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**Décalage d’URI**: / paramètres/AllowVirtualGPU

#### <a name="windows10endpointprotectionconfigurationapplicationguardblockclipboardsharing"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardBlockClipboardSharing 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**Décalage d’URI**: / paramètres/ClipboardSettings

#### <a name="windows10endpointprotectionconfigurationapplicationguardblockfiletransfer"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardBlockFileTransfer 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**Décalage d’URI**: / paramètres/ClipboardFileType

#### <a name="windows10endpointprotectionconfigurationapplicationguardblocknonenterprisecontent"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardBlockNonEnterpriseContent 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**Décalage d’URI**: / paramètres/BlockNonEnterpriseContent

#### <a name="windows10endpointprotectionconfigurationapplicationguardenabled"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardEnabled 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**Décalage d’URI**: / paramètres/AllowWindowsDefenderApplicationGuard

#### <a name="windows10endpointprotectionconfigurationapplicationguardforceauditing"></a>Windows10EndpointProtectionConfiguration.ApplicationGuardForceAuditing 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/WindowsDefenderApplicationGuard  
**Décalage d’URI**: AuditApplicationGuard / d’Audit

#### <a name="windows10endpointprotectionconfigurationbitlockerallowstandarduserencryption"></a>Windows10EndpointProtectionConfiguration.BitLockerAllowStandardUserEncryption 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/BitLocker  
**Décalage d’URI**: /AllowStandardUserEncryption

#### <a name="windows10endpointprotectionconfigurationbitlockerdisablewarningforotherdiskencryption"></a>Windows10EndpointProtectionConfiguration.BitLockerDisableWarningForOtherDiskEncryption 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/BitLocker  
**Décalage d’URI**: /AllowWarningForOtherDiskEncryption

#### <a name="windows10endpointprotectionconfigurationbitlockerenablestoragecardencryptiononmobile"></a>Windows10EndpointProtectionConfiguration.BitLockerEnableStorageCardEncryptionOnMobile 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/BitLocker  
**Décalage d’URI**: /RequireStorageCardEncryption

#### <a name="windows10endpointprotectionconfigurationbitlockerencryptdevice"></a>Windows10EndpointProtectionConfiguration.BitLockerEncryptDevice 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/BitLocker  
**Décalage d’URI**: /RequireDeviceEncryption

#### <a name="windows10endpointprotectionconfigurationbitlockerfixeddrivepolicy"></a>Windows10EndpointProtectionConfiguration.BitLockerFixedDrivePolicy 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/BitLocker  
**Décalage d’URI**: /EncryptionMethodByDriveType, /FixedDrivesRequireEncryption, /FixedDrivesRecoveryOptions

#### <a name="windows10endpointprotectionconfigurationbitlockerremovabledrivepolicy"></a>Windows10EndpointProtectionConfiguration.BitLockerRemovableDrivePolicy 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/BitLocker  
**Décalage d’URI**: /EncryptionMethodByDriveType, /RemovableDrivesRequireEncryption

#### <a name="windows10endpointprotectionconfigurationbitlockersystemdrivepolicy"></a>Windows10EndpointProtectionConfiguration.BitLockerSystemDrivePolicy 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/BitLocker  
**Décalage d’URI**: /EncryptionMethodByDriveType, /SystemDrivesRequireStartupAuthentication, /SystemDrivesMinimumPINLength, /SystemDrivesRecoveryMessage, /SystemDrivesRecoveryOptions

#### <a name="windows10endpointprotectionconfigurationclientconnectionencryptionlevel"></a>windows10endpointprotectionconfiguration.clientConnectionEncryptionLevel 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/RemoteDesktopServices/ClientConnectionEncryptionLevel

#### <a name="windows10endpointprotectionconfigurationconfiguresmbv1clientdriver"></a>windows10endpointprotectionconfiguration.configureSMBV1ClientDriver 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/MSSecurityGuide/ConfigureSMBV1ClientDriver

#### <a name="windows10endpointprotectionconfigurationconnectivitydownloadingofprintdriversoverhttp"></a>Windows10EndpointProtectionConfiguration.ConnectivityDownloadingOfPrintDriversOverHttp 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Connectivity/DisableDownloadingOfPrintDriversOverHTTP

#### <a name="windows10endpointprotectionconfigurationconnectivityhardeneduncpaths"></a>Windows10EndpointProtectionConfiguration.ConnectivityHardenedUncPaths 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Connectivity/HardenedUNCPaths

#### <a name="windows10endpointprotectionconfigurationconnectivityinternetdownloadforwebpublishingandonlineorderingwizards"></a>Windows10EndpointProtectionConfiguration.ConnectivityInternetDownloadForWebPublishingAndOnlineOrderingWizards 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Connectivity/DisableInternetDownloadForWebPublishingAndOnlineOrderingWizards

#### <a name="windows10endpointprotectionconfigurationconnectivityprintingoverhttp"></a>Windows10EndpointProtectionConfiguration.ConnectivityPrintingOverHttp 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Connectivity/DiablePrintingOverHTTP

#### <a name="windows10endpointprotectionconfigurationcredentialsuienumerateadministrators"></a>Windows10EndpointProtectionConfiguration.CredentialsUIEnumerateAdministrators 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/CredentialsUI/EnumerateAdministrators

#### <a name="windows10endpointprotectionconfigurationdefenderadditionalguardedfolders"></a>Windows10EndpointProtectionConfiguration.DefenderAdditionalGuardedFolders 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy **décalage URI**: /Config/Defender/ControlledFolderAccessProtectedFolders

#### <a name="windows10endpointprotectionconfigurationdefenderadvancedransomewareprotectiontype"></a>Windows10EndpointProtectionConfiguration.DefenderAdvancedRansomewareProtectionType 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AttackSurfaceReductionRules

#### <a name="windows10endpointprotectionconfigurationdefenderattacksurfacereductionexcludedpaths"></a>Windows10EndpointProtectionConfiguration.DefenderAttackSurfaceReductionExcludedPaths 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AttackSurfaceReductionOnlyExclusions

#### <a name="windows10endpointprotectionconfigurationdefenderemailcontentexecution"></a>Windows10EndpointProtectionConfiguration.DefenderEmailContentExecution 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AllowEmailScanning

#### <a name="windows10endpointprotectionconfigurationdefenderemailcontentexecutiontype"></a>Windows10EndpointProtectionConfiguration.DefenderEmailContentExecutionType 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AttackSurfaceReductionRules (/ Configuration du fournisseur CSP nécessite des propriétés de graphique : windows10endpointprotection/Configuration.defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection / Configuration.defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration.defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection / Configuration.defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration.defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration.defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration.defenderEmailContentExecutionType, windows10endpointprotection/Configuration.defenderPreventCredentialStealingType, windows10endpointprotection / Configuration.defenderUntrustedUSBProcessType

#### <a name="windows10endpointprotectionconfigurationdefenderexploitprotectionxml"></a>Windows10EndpointProtectionConfiguration.DefenderExploitProtectionXml 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy **décalage URI**: /Config/ExploitGuard/ExploitProtectionSettings

#### <a name="windows10endpointprotectionconfigurationdefenderexploitprotectionxmlfilename"></a>Windows10EndpointProtectionConfiguration.DefenderExploitProtectionXmlFileName 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/ExploitGuard/ExploitProtectionSettings

#### <a name="windows10endpointprotectionconfigurationdefenderguardedfoldersallowedapppaths"></a>Windows10EndpointProtectionConfiguration.DefenderGuardedFoldersAllowedAppPaths 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy **décalage URI**: /Config/Defender/ControlledFolderAccessAllowedApplications

#### <a name="windows10endpointprotectionconfigurationdefenderguardmyfolderstype"></a>Windows10EndpointProtectionConfiguration.DefenderGuardMyFoldersType 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/EnableControlledFolderAccess

#### <a name="windows10endpointprotectionconfigurationdefendernetworkprotectiontype"></a>Windows10EndpointProtectionConfiguration.DefenderNetworkProtectionType 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy **décalage URI**: /Config/Defender/EnableNetworkProtection

#### <a name="windows10endpointprotectionconfigurationdefenderofficeappsexecutablecontentcreationorlaunch"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeAppsExecutableContentCreationOrLaunch 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AttackSurfaceReductionRules

#### <a name="windows10endpointprotectionconfigurationdefenderofficeappsexecutablecontentcreationorlaunchtype"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeAppsExecutableContentCreationOrLaunchType
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AttackSurfaceReductionRules (/ Configuration du fournisseur CSP nécessite des propriétés de graphique : windows10endpointprotection/Configuration.defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection / Configuration.defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration.defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection / Configuration.defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration.defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration.defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration.defenderEmailContentExecutionType, windows10endpointprotection/Configuration.defenderPreventCredentialStealingType, windows10endpointprotection / Configuration.defenderUntrustedUSBProcessType

#### <a name="windows10endpointprotectionconfigurationdefenderofficeappslaunchchildprocess"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeAppsLaunchChildProcess 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AttackSurfaceReductionRules

#### <a name="windows10endpointprotectionconfigurationdefenderofficeappslaunchchildprocesstype"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeAppsLaunchChildProcessType 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AttackSurfaceReductionRules (/ Configuration du fournisseur CSP nécessite des propriétés de graphique : windows10endpointprotection/Configuration.defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection / Configuration.defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration.defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection / Configuration.defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration.defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration.defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration.defenderEmailContentExecutionType, windows10endpointprotection/Configuration.defenderPreventCredentialStealingType, windows10endpointprotection / Configuration.defenderUntrustedUSBProcessType

#### <a name="windows10endpointprotectionconfigurationdefenderofficeappsotherprocessinjection"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeAppsOtherProcessInjection 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AttackSurfaceReductionRules

#### <a name="windows10endpointprotectionconfigurationdefenderofficeappsotherprocessinjectiontype"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeAppsOtherProcessInjectionType 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AttackSurfaceReductionRules (/ Configuration du fournisseur CSP nécessite des propriétés de graphique : windows10endpointprotection/Configuration.defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection / Configuration.defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration.defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection / Configuration.defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration.defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration.defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration.defenderEmailContentExecutionType, windows10endpointprotection/Configuration.defenderPreventCredentialStealingType, windows10endpointprotection / Configuration.defenderUntrustedUSBProcessType 

#### <a name="windows10endpointprotectionconfigurationdefenderofficemacrocodeallowwin32imports"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeMacroCodeAllowWin32Imports 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AttackSurfaceReductionRules

#### <a name="windows10endpointprotectionconfigurationdefenderofficemacrocodeallowwin32importstype"></a>Windows10EndpointProtectionConfiguration.DefenderOfficeMacroCodeAllowWin32ImportsType 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AttackSurfaceReductionRules (/ Configuration du fournisseur CSP nécessite des propriétés de graphique : windows10endpointprotection/Configuration.defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection / Configuration.defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration.defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection / Configuration.defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration.defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration.defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration.defenderEmailContentExecutionType, windows10endpointprotection/Configuration.defenderPreventCredentialStealingType, windows10endpointprotection / Configuration.defenderUntrustedUSBProcessType

#### <a name="windows10endpointprotectionconfigurationdefenderpreventcredentialstealingtype"></a>Windows10EndpointProtectionConfiguration.DefenderPreventCredentialStealingType 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AttackSurfaceReductionRules (/ Configuration du fournisseur CSP nécessite des propriétés de graphique : windows10endpointprotection/Configuration.defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection / Configuration.defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration.defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection / Configuration.defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration.defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration.defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration.defenderEmailContentExecutionType, windows10endpointprotection/Configuration.defenderPreventCredentialStealingType, windows10endpointprotection / Configuration.defenderUntrustedUSBProcessType

#### <a name="windows10endpointprotectionconfigurationdefenderprocesscreation"></a>Windows10EndpointProtectionConfiguration.DefenderProcessCreation 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AttackSurfaceReductionRules

#### <a name="windows10endpointprotectionconfigurationdefenderprocesscreationtype"></a>Windows10EndpointProtectionConfiguration.DefenderProcessCreationType 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AttackSurfaceReductionRules

#### <a name="windows10endpointprotectionconfigurationdefenderprotectagainstpotentiallyunwantedapplications"></a>Windows10EndpointProtectionConfiguration.DefenderProtectAgainstPotentiallyUnwantedApplications 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/MSSecurityGuide/TurnOnWindowsDefenderProtectionAgainstPotentiallyUnwantedApplications

#### <a name="windows10endpointprotectionconfigurationdefenderscriptdownloadedpayloadexecution"></a>Windows10EndpointProtectionConfiguration.DefenderScriptDownloadedPayloadExecution 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AttackSurfaceReductionRules

#### <a name="windows10endpointprotectionconfigurationdefenderscriptdownloadedpayloadexecutiontype"></a>Windows10EndpointProtectionConfiguration.DefenderScriptDownloadedPayloadExecutionType 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AttackSurfaceReductionRules (/ Configuration du fournisseur CSP nécessite des propriétés de graphique : windows10endpointprotection/Configuration.defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection / Configuration.defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration.defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection / Configuration.defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration.defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration.defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration.defenderEmailContentExecutionType, windows10endpointprotection/Configuration.defenderPreventCredentialStealingType, windows10endpointprotection / Configuration.defenderUntrustedUSBProcessType

#### <a name="windows10endpointprotectionconfigurationdefenderscriptobfuscatedmacrocode"></a>Windows10EndpointProtectionConfiguration.DefenderScriptObfuscatedMacroCode 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AttackSurfaceReductionRules

#### <a name="windows10endpointprotectionconfigurationdefenderscriptobfuscatedmacrocodetype"></a>Windows10EndpointProtectionConfiguration.DefenderScriptObfuscatedMacroCodeType 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AttackSurfaceReductionRules (/ Configuration du fournisseur CSP nécessite des propriétés de graphique : windows10endpointprotection/Configuration.defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection / Configuration.defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration.defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection / Configuration.defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration.defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration.defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration.defenderEmailContentExecutionType, windows10endpointprotection/Configuration.defenderPreventCredentialStealingType, windows10endpointprotection / Configuration.defenderUntrustedUSBProcessType

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterblockexploitprotectionoverride"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterBlockExploitProtectionOverride 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy **décalage URI**: /Config/WindowsDefenderSecurityCenter/DisallowExploitProtectionOverride

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisableaccountui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableAccountUI 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WindowsDefenderSecurityCenter/DisableAccountProtectionUI

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisableappbrowserui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableAppBrowserUI 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WindowsDefenderSecurityCenter/DisableAppBrowserUI

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisablefamilyui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableFamilyUI 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WindowsDefenderSecurityCenter/DisableFamilyUI

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisablehealthui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableHealthUI 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WindowsDefenderSecurityCenter/DisableHealthUI

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisablenetworkui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableNetworkUI 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WindowsDefenderSecurityCenter/DisableNetworkUI

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisablesecurebootui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableSecureBootUI 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WindowsDefenderSecurityCenter/HideSecureBoot

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisabletroubleshootingui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableTroubleshootingUI 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WindowsDefenderSecurityCenter/HideTPMTroubleshooting

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterdisablevirusui"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterDisableVirusUI 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WindowsDefenderSecurityCenter/DisableVirusUI

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterhelpemail"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterHelpEmail 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WindowsDefenderSecurityCenter/Email

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterhelpphone"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterHelpPhone 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WindowsDefenderSecurityCenter/Phone

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterhelpurl"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterHelpURL 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WindowsDefenderSecurityCenter/URL

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenteritcontactdisplay"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterITContactDisplay 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: / WindowsDefenderSecurityCenter/EnableCustomizedToasts, / WindowsDefenderSecurityCenter/EnableInAppCustomization

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenternotificationsfromapp"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterNotificationsFromApp 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WindowsDefenderSecurityCenter/HideWindowsSecurityNotificationAreaControl

#### <a name="windows10endpointprotectionconfigurationdefendersecuritycenterorganizationdisplayname"></a>Windows10EndpointProtectionConfiguration.DefenderSecurityCenterOrganizationDisplayName 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WindowsDefenderSecurityCenter/CompanyName

#### <a name="windows10endpointprotectionconfigurationdefenderuntrustedexecutable"></a>Windows10EndpointProtectionConfiguration.DefenderUntrustedExecutable 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AttackSurfaceReductionRules

#### <a name="windows10endpointprotectionconfigurationdefenderuntrustedexecutabletype"></a>Windows10EndpointProtectionConfiguration.DefenderUntrustedExecutableType 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AttackSurfaceReductionRules

#### <a name="windows10endpointprotectionconfigurationdefenderuntrustedusbprocess"></a>Windows10EndpointProtectionConfiguration.DefenderUntrustedUSBProcess 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AttackSurfaceReductionRules

#### <a name="windows10endpointprotectionconfigurationdefenderuntrustedusbprocesstype"></a>Windows10EndpointProtectionConfiguration.DefenderUntrustedUSBProcessType 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AttackSurfaceReductionRules (/ Configuration du fournisseur CSP nécessite des propriétés de graphique : windows10endpointprotection/Configuration.defenderOfficeAppsOtherProcessInjectionType, windows10endpointprotection / Configuration.defenderOfficeAppsExecutableContentCreationOrLaunchType, windows10endpointprotection/Configuration.defenderOfficeAppsLaunchChildProcessType, windows10endpointprotection / Configuration.defenderOfficeMacroCodeAllowWin32ImportsType, windows10endpointprotection/Configuration.defenderScriptObfuscatedMacroCodeType, windows10endpointprotection/Configuration.defenderScriptDownloadedPayloadExecutionType , windows10endpointprotection/Configuration.defenderEmailContentExecutionType, windows10endpointprotection/Configuration.defenderPreventCredentialStealingType, windows10endpointprotection / Configuration.defenderUntrustedUSBProcessType

#### <a name="windows10endpointprotectionconfigurationdeviceguardenablesecurebootwithdma"></a>Windows10EndpointProtectionConfiguration.DeviceGuardEnableSecureBootWithDMA 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/DeviceGuard/RequirePlatformSecurityFeatures

#### <a name="windows10endpointprotectionconfigurationdeviceguardenablevirtualizationbasedsecurity"></a>Windows10EndpointProtectionConfiguration.DeviceGuardEnableVirtualizationBasedSecurity 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy **décalage URI**: /Config/DeviceGuard/EnableVirtualizationBasedSecurity

#### <a name="windows10endpointprotectionconfigurationdeviceguardlaunchsystemguard"></a>Windows10EndpointProtectionConfiguration.DeviceGuardLaunchSystemGuard 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/DeviceGuard/ConfigureSystemGuardLaunch

#### <a name="windows10endpointprotectionconfigurationdeviceguardlocalsystemauthoritycredentialguardsettings"></a>Windows10EndpointProtectionConfiguration.DeviceGuardLocalSystemAuthorityCredentialGuardSettings 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/DeviceGuard/LsaCfgFlags

#### <a name="windows10endpointprotectionconfigurationdmaguarddeviceenumerationpolicy"></a>Windows10EndpointProtectionConfiguration.DmaGuardDeviceEnumerationPolicy 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/DmaGuard/DeviceEnumerationPolicy

#### <a name="windows10endpointprotectionconfigurationeventlogserviceapplicationlogmaximumfilesizeinkb"></a>Windows10EndpointProtectionConfiguration.EventLogServiceApplicationLogMaximumFileSizeInKb 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/EventLogService/SpecifyMaximumFileSizeApplicationLog

#### <a name="windows10endpointprotectionconfigurationeventlogservicesecuritylogmaximumfilesizeinkb"></a>Windows10EndpointProtectionConfiguration.EventLogServiceSecurityLogMaximumFileSizeInKb 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/EventLogService/SpecifyMaximumFileSizeSecurityLog

#### <a name="windows10endpointprotectionconfigurationeventlogservicesystemlogmaximumfilesizeinkb"></a>Windows10EndpointProtectionConfiguration.EventLogServiceSystemLogMaximumFileSizeInKb 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/EventLogService/SpecifyMaximumFileSizeSystemLog

#### <a name="windows10endpointprotectionconfigurationexplorerdataexecutionprevention"></a>Windows10EndpointProtectionConfiguration.ExplorerDataExecutionPrevention 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/FileExplorer/TurnOffDataExecutionPreventionForExplorer

#### <a name="windows10endpointprotectionconfigurationexplorerheapterminationoncorruption"></a>Windows10EndpointProtectionConfiguration.ExplorerHeapTerminationOnCorruption 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/FileExplorer/TurnOffHeapTerminationOnCorruption

#### <a name="windows10endpointprotectionconfigurationfirewallblockstatefulftp"></a>Windows10EndpointProtectionConfiguration.FirewallBlockStatefulFTP 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Firewall  
**Décalage d’URI**: /MdmStore/Global/DisableStatefulFtp

#### <a name="windows10endpointprotectionconfigurationfirewallcertificaterevocationlistcheckmethod"></a>Windows10EndpointProtectionConfiguration.FirewallCertificateRevocationListCheckMethod 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Firewall  
**Décalage d’URI**: /MdmStore/Global/CRLcheck

#### <a name="windows10endpointprotectionconfigurationfirewallidletimeoutforsecurityassociationinseconds"></a>Windows10EndpointProtectionConfiguration.FirewallIdleTimeoutForSecurityAssociationInSeconds 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Firewall  
**Décalage d’URI**: /MdmStore/Global/SaIdleTime

#### <a name="windows10endpointprotectionconfigurationfirewallipsecexemptionsallowdhcp"></a>Windows10EndpointProtectionConfiguration.FirewallIPSecExemptionsAllowDHCP 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Firewall  
**Décalage d’URI**: /MdmStore/Global/IPsecExempt

#### <a name="windows10endpointprotectionconfigurationfirewallipsecexemptionsallowicmp"></a>Windows10EndpointProtectionConfiguration.FirewallIPSecExemptionsAllowICMP 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Firewall  
**Décalage d’URI**: /MdmStore/Global/IPsecExempt

#### <a name="windows10endpointprotectionconfigurationfirewallipsecexemptionsallowneighbordiscovery"></a>Windows10EndpointProtectionConfiguration.FirewallIPSecExemptionsAllowNeighborDiscovery 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Firewall  
**Décalage d’URI**: /MdmStore/Global/IPsecExempt

#### <a name="windows10endpointprotectionconfigurationfirewallipsecexemptionsallowrouterdiscovery"></a>Windows10EndpointProtectionConfiguration.FirewallIPSecExemptionsAllowRouterDiscovery 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Firewall  
**Décalage d’URI**: /MdmStore/Global/IPsecExempt

#### <a name="windows10endpointprotectionconfigurationfirewallmergekeyingmodulesettings"></a>Windows10EndpointProtectionConfiguration.FirewallMergeKeyingModuleSettings 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Firewall  
**Décalage d’URI**: /MdmStore/Global/OpportunisticallyMatchAuthSetPerKM

#### <a name="windows10endpointprotectionconfigurationfirewallpacketqueueingmethod"></a>Windows10EndpointProtectionConfiguration.FirewallPacketQueueingMethod 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Firewall  
**Décalage d’URI**: /MdmStore/Global/EnablePacketQueue

#### <a name="windows10endpointprotectionconfigurationfirewallpresharedkeyencodingmethod"></a>Windows10EndpointProtectionConfiguration.FirewallPreSharedKeyEncodingMethod 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Firewall  
**Décalage d’URI**: /MdmStore/Global/PresharedKeyEncoding

#### <a name="windows10endpointprotectionconfigurationfirewallprofiledomain"></a>Windows10EndpointProtectionConfiguration.FirewallProfileDomain 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Firewall  
**Décalage d’URI**: /EnableFirewall, /DisableStealthMode, / protégées, /DisableUnicastResponsesToMulticastBroadcast, /DisableInboundNotifications, /AuthAppsAllowUserPrefMerge, /GlobalPortsAllowUserPrefMerge, /AllowLocalPolicyMerge , /DefaultOutboundAction, /DefaultInboundAction, /DisableStealthModeIpsecSecuredPacketExemption, /AllowLocalIpsecPolicyMerge

#### <a name="windows10endpointprotectionconfigurationfirewallprofiledomaininboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfileDomain.inboundConnectionsBlocked 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Firewall  
**Décalage d’URI**: /MdmStore/DomainProfile/DefaultInboundAction

#### <a name="windows10endpointprotectionconfigurationfirewallprofiledomaininboundnotificationsblocked"></a>windows10endpointprotectionconfiguration.firewallProfileDomain.inboundNotificationsBlocked 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Firewall  
**Décalage d’URI**: /MdmStore/DomainProfile/DisableInboundNotifications

#### <a name="windows10endpointprotectionconfigurationfirewallprofiledomaininboundnotificationsblocked"></a>windows10endpointprotectionconfiguration.firewallProfileDomain.inboundNotificationsBlocked 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Firewall  
**Décalage d’URI**: /MdmStore/DomainProfile/EnableFirewall

#### <a name="windows10endpointprotectionconfigurationfirewallprofiledomainoutboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfileDomain.outboundConnectionsBlocked 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Firewall  
**Décalage d’URI**: /MdmStore/DomainProfile/DefaultOutboundAction

#### <a name="windows10endpointprotectionconfigurationfirewallprofileprivate"></a>Windows10EndpointProtectionConfiguration.FirewallProfilePrivate 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Firewall  
**Décalage d’URI**: /EnableFirewall, /DisableStealthMode, / protégées, /DisableUnicastResponsesToMulticastBroadcast, /DisableInboundNotifications, /AuthAppsAllowUserPrefMerge, /GlobalPortsAllowUserPrefMerge, /AllowLocalPolicyMerge , /DefaultOutboundAction, /DefaultInboundAction, /DisableStealthModeIpsecSecuredPacketExemption, /AllowLocalIpsecPolicyMerge

#### <a name="windows10endpointprotectionconfigurationfirewallprofileprivatefirewallenabled"></a>windows10endpointprotectionconfiguration.firewallProfilePrivate.firewallEnabled 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Firewall  
**Décalage d’URI**: /MdmStore/PrivateProfile/EnableFirewall

#### <a name="windows10endpointprotectionconfigurationfirewallprofileprivateinboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePrivate.inboundConnectionsBlocked 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Firewall  
**Décalage d’URI**: /MdmStore/PrivateProfile/DefaultInboundAction

#### <a name="windows10endpointprotectionconfigurationfirewallprofileprivateinboundnotificationsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePrivate.inboundNotificationsBlocked 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Firewall  
**Décalage d’URI**: /MdmStore/PrivateProfile/DisableInboundNotifications

#### <a name="windows10endpointprotectionconfigurationfirewallprofileprivateoutboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePrivate.outboundConnectionsBlocked 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Firewall  
**Décalage d’URI**: /MdmStore/PrivateProfile/DefaultOutboundAction

#### <a name="windows10endpointprotectionconfigurationfirewallprofilepublic"></a>Windows10EndpointProtectionConfiguration.FirewallProfilePublic 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Firewall  
**Décalage d’URI**: /EnableFirewall, /DisableStealthMode, / protégées, /DisableUnicastResponsesToMulticastBroadcast, /DisableInboundNotifications, /AuthAppsAllowUserPrefMerge, /GlobalPortsAllowUserPrefMerge, /AllowLocalPolicyMerge , /DefaultOutboundAction, /DefaultInboundAction, /DisableStealthModeIpsecSecuredPacketExemption, /AllowLocalIpsecPolicyMerge

#### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicconnectionsecurityrulesfromgrouppolicymerged"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.connectionSecurityRulesFromGroupPolicyMerged 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Firewall  
**Décalage d’URI**: /MdmStore/PublicProfile/AllowLocalIpsecPolicyMerge

#### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicfirewallenabled"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.firewallEnabled 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Firewall  
**Décalage d’URI**: /MdmStore/PublicProfile/EnableFirewall

#### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicinboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.inboundConnectionsBlocked 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Firewall  
**Décalage d’URI**: /MdmStore/PublicProfile/DefaultInboundAction

#### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicinboundnotificationsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.inboundNotificationsBlocked 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Firewall  
**Décalage d’URI**: /MdmStore/PublicProfile/DisableInboundNotifications

#### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicoutboundconnectionsblocked"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.outboundConnectionsBlocked 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Firewall  
**Décalage d’URI**: /MdmStore/PublicProfile/DefaultOutboundAction

#### <a name="windows10endpointprotectionconfigurationfirewallprofilepublicpolicyrulesfromgrouppolicymerged"></a>windows10endpointprotectionconfiguration.firewallProfilePublic.policyRulesFromGroupPolicyMerged 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Firewall  
**Décalage d’URI**: /MdmStore/PublicProfile/AllowLocalPolicyMerge

#### <a name="windows10endpointprotectionconfigurationlanmanagerauthenticationlevel"></a>Windows10EndpointProtectionConfiguration.LanManagerAuthenticationLevel 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/NetworkSecurity\_LANManagerAuthenticationLevel

#### <a name="windows10endpointprotectionconfigurationlanmanagerworkstationdisableinsecureguestlogons"></a>Windows10EndpointProtectionConfiguration.LanManagerWorkstationDisableInsecureGuestLogons 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LanmanWorkstation/EnableInsecureGuestLogons

#### <a name="windows10endpointprotectionconfigurationlanmanagerworkstationenableinsecureguestlogons"></a>Windows10EndpointProtectionConfiguration.LanManagerWorkstationEnableInsecureGuestLogons 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LanmanWorkstation/EnableInsecureGuestLogons

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsadministratoraccountname"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAdministratorAccountName 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/Accounts\_RenameAdministratorAccount

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsadministratorelevationpromptbehavior"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAdministratorElevationPromptBehavior
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/UserAccountControl\_BehaviorOfTheElevationPromptForAdministrators

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowanonymousenumerationofsamaccountsandshares"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowAnonymousEnumerationOfSAMAccountsAndShares 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/NetworkAccess\_DoNotAllowAnonymousEnumerationOfSamAccountsAndShares

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowpku2uauthenticationrequests"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowPKU2UAuthenticationRequests 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/NetworkSecurity\_AllowPKU2UAuthenticationRequests

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowremotecallstosecurityaccountsmanager"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowRemoteCallsToSecurityAccountsManager 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/NetworkAccess\_RestrictClientsAllowedToMakeRemoteCallsToSAM

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowremotecallstosecurityaccountsmanagerhelperbool"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowRemoteCallsToSecurityAccountsManagerHelperBool 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/NetworkAccess\_RestrictClientsAllowedToMakeRemoteCallsToSAM

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowsystemtobeshutdownwithouthavingtologon"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowSystemToBeShutDownWithoutHavingToLogOn 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/Shutdown\_AllowSystemToBeShutDownWithoutHavingToLogOn

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowuiaccessapplicationelevation"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowUIAccessApplicationElevation 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/UserAccountControl\_AllowUIAccessApplicationsToPromptForElevation

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowuiaccessapplicationsforsecurelocations"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowUIAccessApplicationsForSecureLocations 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/UserAccountControl\_OnlyElevateUIAccessApplicationsThatAreInstalledInSecureLocations

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsallowundockwithouthavingtologon"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsAllowUndockWithoutHavingToLogon 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/Devices\_AllowUndockWithoutHavingToLogon

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsblockmicrosoftaccounts"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsBlockMicrosoftAccounts 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/Accounts\_BlockMicrosoftAccounts

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsblockremotelogonwithblankpassword"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsBlockRemoteLogonWithBlankPassword 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/Accounts\_LimitLocalAccountUseOfBlankPasswordsToConsoleLogonOnly

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsblockremoteopticaldriveaccess"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsBlockRemoteOpticalDriveAccess 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/Devices\_RestrictCDROMAccessToLocallyLoggedOnUserOnly

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsblockusersinstallingprinterdrivers"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsBlockUsersInstallingPrinterDrivers 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/Devices\_PreventUsersFromInstallingPrinterDriversWhenConnectingToSharedPrinters

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsclearvirtualmemorypagefile"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsClearVirtualMemoryPageFile 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/Shutdown\_ClearVirtualMemoryPageFile

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsclientdigitallysigncommunicationsalways"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsClientDigitallySignCommunicationsAlways 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/MicrosoftNetworkClient\_DigitallySignCommunicationsAlways

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsclientsendunencryptedpasswordtothirdpartysmbservers"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsClientSendUnencryptedPasswordToThirdPartySMBServers 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/MicrosoftNetworkClient\_SendUnencryptedPasswordToThirdPartySMBServers

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdetectapplicationinstallationsandpromptforelevation"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDetectApplicationInstallationsAndPromptForElevation 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/UserAccountControl\_DetectApplicationInstallationsAndPromptForElevation

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdisableadministratoraccount"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDisableAdministratorAccount 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/Accounts\_EnableAdministratorAccountStatus

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdisableclientdigitallysigncommunicationsifserveragrees"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDisableClientDigitallySignCommunicationsIfServerAgrees 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/MicrosoftNetworkClient\_DigitallySignCommunicationsIfServerAgrees

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdisableguestaccount"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDisableGuestAccount 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/Accounts\_EnableGuestAccountStatus

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdisableserverdigitallysigncommunicationsalways"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDisableServerDigitallySignCommunicationsAlways 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/MicrosoftNetworkServer\_DigitallySignCommunicationsAlways

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdisableserverdigitallysigncommunicationsifclientagrees"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDisableServerDigitallySignCommunicationsIfClientAgrees 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/MicrosoftNetworkServer\_DigitallySignCommunicationsIfClientAgrees

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdonotallowanonymousenumerationofsamaccounts"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDoNotAllowAnonymousEnumerationOfSAMAccounts 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/NetworkAccess\_DoNotAllowAnonymousEnumerationOfSAMAccounts

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdonotrequirectrlaltdel"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDoNotRequireCtrlAltDel 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/InteractiveLogon\_DoNotRequireCTRLALTDEL

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsdonotstorelanmanagerhashvalueonnextpasswordchange"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsDoNotStoreLANManagerHashValueOnNextPasswordChange 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/NetworkSecurity\_DoNotStoreLANManagerHashValueOnNextPasswordChange

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsenableadministratoraccount"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsEnableAdministratorAccount 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/Accounts\_EnableAdministratorAccountStatus

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsenableguestaccount"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsEnableGuestAccount 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/Accounts\_EnableGuestAccountStatus

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsformatandejectofremovablemediaalloweduser"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsFormatAndEjectOfRemovableMediaAllowedUser 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/Devices\_AllowedToFormatAndEjectRemovableMedia

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsguestaccountname"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsGuestAccountName 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/Accounts\_RenameGuestAccount

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionshidelastsignedinuser"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsHideLastSignedInUser 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/InteractiveLogon\_DoNotDisplayLastSignedIn

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionshideusernameatsignin"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsHideUsernameAtSignIn 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/InteractiveLogon\_DoNotDisplayUsernameAtSignIn

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsinformationdisplayedonlockscreen"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsInformationDisplayedOnLockScreen 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/InteractiveLogon\_DisplayUserInformationWhenTheSessionIsLocked

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsinformationshownonlockscreen"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsInformationShownOnLockScreen 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/InteractiveLogon\_DisplayUserInformationWhenTheSessionIsLocked

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionslogonmessagetext"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsLogOnMessageText 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/InteractiveLogon\_MessageTextForUsersAttemptingToLogOn

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionslogonmessagetitle"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsLogOnMessageTitle 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/InteractiveLogon\_MessageTitleForUsersAttemptingToLogOn

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsmachineinactivitylimit"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsMachineInactivityLimit 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/InteractiveLogon\_MachineInactivityLimit

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsmachineinactivitylimitinminutes"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsMachineInactivityLimitInMinutes 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/InteractiveLogon\_MachineInactivityLimit

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsminimumsessionsecurityforntlmsspbasedclients"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsMinimumSessionSecurityForNtlmSspBasedClients 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/NetworkSecurity\_MinimumSessionSecurityForNTLMSSPBasedClients

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsminimumsessionsecurityforntlmsspbasedservers"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsMinimumSessionSecurityForNtlmSspBasedServers 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/NetworkSecurity\_MinimumSessionSecurityForNTLMSSPBasedServers

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsonlyelevatesignedexecutables"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsOnlyElevateSignedExecutables 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/UserAccountControl\_OnlyElevateExecutableFilesThatAreSignedAndValidated

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsrestrictanonymousaccesstonamedpipesandshares"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsRestrictAnonymousAccessToNamedPipesAndShares 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/NetworkAccess\_RestrictAnonymousAccessToNamedPipesAndShares

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionssmartcardremovalbehavior"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsSmartCardRemovalBehavior 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/InteractiveLogon\_SmartCardRemovalBehavior

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsstandarduserelevationpromptbehavior"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsStandardUserElevationPromptBehavior 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/UserAccountControl\_BehaviorOfTheElevationPromptForStandardUsers

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsswitchtosecuredesktopwhenpromptingforelevation"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsSwitchToSecureDesktopWhenPromptingForElevation 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/UserAccountControl\_SwitchToTheSecureDesktopWhenPromptingForElevation

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsuseadminapprovalmode"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsUseAdminApprovalMode 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/UserAccountControl\_UseAdminApprovalMode

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsuseadminapprovalmodeforadministrators"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsUseAdminApprovalModeForAdministrators 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/UserAccountControl\_RunAllAdministratorsInAdminApprovalMode

#### <a name="windows10endpointprotectionconfigurationlocalsecurityoptionsvirtualizefileandregistrywritefailurestoperuserlocations"></a>Windows10EndpointProtectionConfiguration.LocalSecurityOptionsVirtualizeFileAndRegistryWriteFailuresToPerUserLocations 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/LocalPoliciesSecurityOptions/UserAccountControl\_VirtualizeFileAndRegistryWriteFailuresToPerUserLocations

#### <a name="windows10endpointprotectionconfigurationnetworkicmpredirectsoverrideospfgeneratedroutes"></a>Windows10EndpointProtectionConfiguration.NetworkIcmpRedirectsOverrideOspfGeneratedRoutes 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/MSSLegacy/AllowICMPRedirectsToOverrideOSPFGeneratedRoutes

#### <a name="windows10endpointprotectionconfigurationnetworkignorenetbiosnamereleaserequestsexceptfromwinsservers"></a>Windows10EndpointProtectionConfiguration.NetworkIgnoreNetBiosNameReleaseRequestsExceptFromWinsServers 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/MSSLegacy/AllowTheComputerToIgnoreNetBIOSNameReleaseRequestsExceptFromWINSServers

#### <a name="windows10endpointprotectionconfigurationnetworkipsourceroutingprotectionlevel"></a>Windows10EndpointProtectionConfiguration.NetworkIpSourceRoutingProtectionLevel 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/MSSLegacy/IPSourceRoutingProtectionLevel

#### <a name="windows10endpointprotectionconfigurationnetworkipv6sourceroutingprotectionlevel"></a>Windows10EndpointProtectionConfiguration.NetworkIpV6SourceRoutingProtectionLevel 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/MSSLegacy/IPv6SourceRoutingProtectionLevel

#### <a name="windows10endpointprotectionconfigurationpasswordpinlogon"></a>Windows10EndpointProtectionConfiguration.PasswordPinLogOn 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/CredentialProviders/AllowPINLogon

#### <a name="windows10endpointprotectionconfigurationpowershellshellscriptblocklogging"></a>Windows10EndpointProtectionConfiguration.PowerShellShellScriptBlockLogging 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WindowsPowerShell/TurnOnPowerShellScriptBlockLogging

#### <a name="windows10endpointprotectionconfigurationremoteassistancesolicitedsetting"></a>Windows10EndpointProtectionConfiguration.RemoteAssistanceSolicitedSetting 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Connectivity/HardenedUNCPaths

#### <a name="windows10endpointprotectionconfigurationremotedesktopservicesclientconnectionencryptionlevel"></a>Windows10EndpointProtectionConfiguration.RemoteDesktopServicesClientConnectionEncryptionLevel 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/RemoteDesktopServices/ClientConnectionEncryptionLevel

#### <a name="windows10endpointprotectionconfigurationremotedesktopservicesdriveredirection"></a>Windows10EndpointProtectionConfiguration.RemoteDesktopServicesDriveRedirection 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/RemoteDesktopServices/DoNotAllowDriveRedirection

#### <a name="windows10endpointprotectionconfigurationremotedesktopservicespasswordsaving"></a>Windows10EndpointProtectionConfiguration.RemoteDesktopServicesPasswordSaving 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/RemoteDesktopServices/DoNotAllowPasswordSaving

#### <a name="windows10endpointprotectionconfigurationremotedesktopservicespromptforpassworduponconnection"></a>Windows10EndpointProtectionConfiguration.RemoteDesktopServicesPromptForPasswordUponConnection 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/RemoteDesktopServices/PromptForPasswordUponConnection

#### <a name="windows10endpointprotectionconfigurationremotedesktopservicessecurerpccommunication"></a>Windows10EndpointProtectionConfiguration.RemoteDesktopServicesSecureRpcCommunication 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/RemoteDesktopServices/RequireSecureRPCCommunication

#### <a name="windows10endpointprotectionconfigurationremotehostdelegationofnonexportablecredentials"></a>Windows10EndpointProtectionConfiguration.RemoteHostDelegationOfNonExportableCredentials 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/CredentialsDelegation/RemoteHostAllowsDelegationOfNonExportableCredentials

#### <a name="windows10endpointprotectionconfigurationremotemanagementclientbasicauthentication"></a>Windows10EndpointProtectionConfiguration.RemoteManagementClientBasicAuthentication 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/RemoteManagement/AllowBasicAuthentication\_Client

#### <a name="windows10endpointprotectionconfigurationremotemanagementclientdigestauthentication"></a>Windows10EndpointProtectionConfiguration.RemoteManagementClientDigestAuthentication 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/RemoteManagement/DisallowDigestAuthentication

#### <a name="windows10endpointprotectionconfigurationremotemanagementclientunencryptedtraffic"></a>Windows10EndpointProtectionConfiguration.RemoteManagementClientUnencryptedTraffic 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/RemoteManagement/AllowUnencryptedTraffic\_Client

#### <a name="windows10endpointprotectionconfigurationremotemanagementservicebasicauthentication"></a>Windows10EndpointProtectionConfiguration.RemoteManagementServiceBasicAuthentication 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/RemoteManagement/AllowBasicAuthentication\_Service

#### <a name="windows10endpointprotectionconfigurationremotemanagementservicestoringrunascredentials"></a>Windows10EndpointProtectionConfiguration.RemoteManagementServiceStoringRunAsCredentials 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/RemoteManagement/DisallowStoringOfRunAsCredentials

#### <a name="windows10endpointprotectionconfigurationremotemanagementserviceunencryptedtraffic"></a>Windows10EndpointProtectionConfiguration.RemoteManagementServiceUnencryptedTraffic 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/RemoteManagement/AllowUnencryptedTraffic\_Service

#### <a name="windows10endpointprotectionconfigurationrpcunauthenticatedclientoptions"></a>Windows10EndpointProtectionConfiguration.RpcUnauthenticatedClientOptions 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/RemoteProcedureCall/RestrictUnauthenticatedRPCClients

#### <a name="windows10endpointprotectionconfigurationsecurityguideapplyuacrestrictionstolocalaccountsonnetworklogon"></a>Windows10EndpointProtectionConfiguration.SecurityGuideApplyUacRestrictionsToLocalAccountsOnNetworkLogon 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/MSSecurityGuide/ApplyUACRestrictionsToLocalAccountsOnNetworkLogon

#### <a name="windows10endpointprotectionconfigurationsecurityguidesmbv1clientdriverstartconfiguration"></a>Windows10EndpointProtectionConfiguration.SecurityGuideSmbV1ClientDriverStartConfiguration 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/MSSecurityGuide/ConfigureSMBV1ClientDriver

#### <a name="windows10endpointprotectionconfigurationsecurityguidesmbv1server"></a>Windows10EndpointProtectionConfiguration.SecurityGuideSmbV1Server 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/MSSecurityGuide/ConfigureSMBV1Server

#### <a name="windows10endpointprotectionconfigurationsecurityguidestructuredexceptionhandlingoverwriteprotection"></a>Windows10EndpointProtectionConfiguration.SecurityGuideStructuredExceptionHandlingOverwriteProtection 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/MSSecurityGuide/EnableStructuredExceptionHandlingOverwriteProtection

#### <a name="windows10endpointprotectionconfigurationsecurityguidewdigestauthentication"></a>Windows10EndpointProtectionConfiguration.SecurityGuideWDigestAuthentication 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/MSSecurityGuide/WDigestAuthentication

#### <a name="windows10endpointprotectionconfigurationsmartscreenblockoverrideforfiles"></a>Windows10EndpointProtectionConfiguration.SmartScreenBlockOverrideForFiles 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy **décalage URI**: /Config/DeviceGuard/RequirePlatformSecurityFeatures

#### <a name="windows10endpointprotectionconfigurationsmartscreenenableinshell"></a>Windows10EndpointProtectionConfiguration.SmartScreenEnableInShell 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy **décalage URI**: /Config/SmartScreen/EnableSmartScreenInShell

#### <a name="windows10endpointprotectionconfigurationsolicitedremoteassistance"></a>windows10endpointprotectionconfiguration.solicitedRemoteAssistance 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/RemoteAssistance/SolicitedRemoteAssistance

#### <a name="windows10endpointprotectionconfigurationuserrightsaccesscredentialmanagerastrustedcaller"></a>Windows10EndpointProtectionConfiguration.UserRightsAccessCredentialManagerAsTrustedCaller 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/AccessCredentialManagerAsTrustedCaller

#### <a name="windows10endpointprotectionconfigurationuserrightsaccessfromnetwork"></a>windows10EndpointProtectionConfiguration.UserRightsAccessFromNetwork 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/AccessFromNetwork

#### <a name="windows10endpointprotectionconfigurationuserrightsactaspartoftheoperatingsystem"></a>Windows10EndpointProtectionConfiguration.userRightsActAsPartOfTheOperatingSystem 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/ActAsPartOfTheOperatingSystem

#### <a name="windows10endpointprotectionconfigurationuserrightsallowaccessfromnetwork"></a>Windows10EndpointProtectionConfiguration.UserRightsAllowAccessFromNetwork 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/AccessFromNetwork

#### <a name="windows10endpointprotectionconfigurationuserrightsbackupdata"></a>Windows10EndpointProtectionConfiguration.UserRightsBackupData 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/BackupFilesAndDirectories

#### <a name="windows10endpointprotectionconfigurationuserrightsblockaccessfromnetwork"></a>Windows10EndpointProtectionConfiguration.UserRightsBlockAccessFromNetwork 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/DenyAccessFromNetwork

#### <a name="windows10endpointprotectionconfigurationuserrightschangesystemtime"></a>Windows10EndpointProtectionConfiguration.UserRightsChangeSystemTime 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/ChangeSystemTime

#### <a name="windows10endpointprotectionconfigurationuserrightscreateglobalobjects"></a>Windows10EndpointProtectionConfiguration.UserRightsCreateGlobalObjects 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/CreateGlobalObjects

#### <a name="windows10endpointprotectionconfigurationuserrightscreatepagefile"></a>Windows10EndpointProtectionConfiguration.UserRightsCreatePageFile 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/CreatePageFile

#### <a name="windows10endpointprotectionconfigurationuserrightscreatepermanentsharedobjects"></a>Windows10EndpointProtectionConfiguration.UserRightsCreatePermanentSharedObjects 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/CreatePermanentSharedObjects

#### <a name="windows10endpointprotectionconfigurationuserrightscreatesymboliclinks"></a>Windows10EndpointProtectionConfiguration.UserRightsCreateSymbolicLinks 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/CreateSymbolicLinks

#### <a name="windows10endpointprotectionconfigurationuserrightscreatetoken"></a>Windows10EndpointProtectionConfiguration.UserRightsCreateToken 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/CreateToken

#### <a name="windows10endpointprotectionconfigurationuserrightsdebugprograms"></a>Windows10EndpointProtectionConfiguration.UserRightsDebugPrograms 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/DebugPrograms

#### <a name="windows10endpointprotectionconfigurationuserrightsdelegation"></a>Windows10EndpointProtectionConfiguration.UserRightsDelegation 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/EnableDelegation

#### <a name="windows10endpointprotectionconfigurationuserrightsdenyaccessfromnetwork"></a>windows10EndpointProtectionConfiguration.UserRightsDenyAccessFromNetwork 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/DenyAccessFromNetwork

#### <a name="windows10endpointprotectionconfigurationuserrightsgeneratesecurityaudits"></a>Windows10EndpointProtectionConfiguration.UserRightsGenerateSecurityAudits 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/GenerateSecurityAudits

#### <a name="windows10endpointprotectionconfigurationuserrightsimpersonateclient"></a>Windows10EndpointProtectionConfiguration.UserRightsImpersonateClient 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/ImpersonateClient

#### <a name="windows10endpointprotectionconfigurationuserrightsincreaseschedulingpriority"></a>Windows10EndpointProtectionConfiguration.UserRightsIncreaseSchedulingPriority 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/IncreaseSchedulingPriority

#### <a name="windows10endpointprotectionconfigurationuserrightsloadunloaddrivers"></a>Windows10EndpointProtectionConfiguration.UserRightsLoadUnloadDrivers 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/LoadUnloadDeviceDrivers

#### <a name="windows10endpointprotectionconfigurationuserrightslocallogon"></a>Windows10EndpointProtectionConfiguration.UserRightsLocalLogOn 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/AllowLocalLogOn

#### <a name="windows10endpointprotectionconfigurationuserrightslockmemory"></a>Windows10EndpointProtectionConfiguration.UserRightsLockMemory 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/LockMemory

#### <a name="windows10endpointprotectionconfigurationuserrightsmanageauditingandsecuritylogs"></a>Windows10EndpointProtectionConfiguration.UserRightsManageAuditingAndSecurityLogs 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/ManageAuditingAndSecurityLog

#### <a name="windows10endpointprotectionconfigurationuserrightsmanagevolumes"></a>Windows10EndpointProtectionConfiguration.UserRightsManageVolumes 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/ManageVolume

#### <a name="windows10endpointprotectionconfigurationuserrightsmodifyfirmwareenvironment"></a>Windows10EndpointProtectionConfiguration.UserRightsModifyFirmwareEnvironment 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/ModifyFirmwareEnvironment

#### <a name="windows10endpointprotectionconfigurationuserrightsmodifyobjectlabels"></a>Windows10EndpointProtectionConfiguration.UserRightsModifyObjectLabels 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/ModifyObjectLabel

#### <a name="windows10endpointprotectionconfigurationuserrightsprofilesingleprocess"></a>Windows10EndpointProtectionConfiguration.UserRightsProfileSingleProcess 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/ProfileSingleProcess

#### <a name="windows10endpointprotectionconfigurationuserrightsregisterprocessasservice"></a>Windows10EndpointProtectionConfiguration.UserRightsRegisterProcessAsService 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/DenyLocalLogOn

#### <a name="windows10endpointprotectionconfigurationuserrightsremotedesktopserviceslogon"></a>Windows10EndpointProtectionConfiguration.UserRightsRemoteDesktopServicesLogOn 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/DenyRemoteDesktopServicesLogOn

#### <a name="windows10endpointprotectionconfigurationuserrightsremoteshutdown"></a>Windows10EndpointProtectionConfiguration.UserRightsRemoteShutdown 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/RemoteShutdown

#### <a name="windows10endpointprotectionconfigurationuserrightsrestoredata"></a>Windows10EndpointProtectionConfiguration.UserRightsRestoreData 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/RestoreFilesAndDirectories

#### <a name="windows10endpointprotectionconfigurationuserrightstakeownership"></a>Windows10EndpointProtectionConfiguration.UserRightsTakeOwnership 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/UserRights/TakeOwnership

#### <a name="windows10endpointprotectionconfigurationwindowsconnectionmanagerconnectiontonondomainnetworks"></a>Windows10EndpointProtectionConfiguration.WindowsConnectionManagerConnectionToNonDomainNetworks 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WindowsConnectionManager/ProhitConnectionToNonDomainNetworksWhenConnectedToDomainAuthenticatedNetwork

#### <a name="windows10endpointprotectionconfigurationwindowslogonsigninlastinteractiveuseraftersysteminitiatedrestart"></a>Windows10EndpointProtectionConfiguration.WindowsLogOnSignInLastInteractiveUserAfterSystemInitiatedRestart 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WindowsLogon/SignInLastInteractiveUserAutomaticallyAfterASystemInitiatedRestart

#### <a name="windows10endpointprotectionconfigurationxboxservicesaccessorymanagementservicestartupmode"></a>Windows10EndpointProtectionConfiguration.XboxServicesAccessoryManagementServiceStartupMode 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/SystemServices/ConfigureXboxAccessoryManagementServiceStartupMode

#### <a name="windows10endpointprotectionconfigurationxboxservicesenablexboxgamesavetask"></a>Windows10EndpointProtectionConfiguration.XboxServicesEnableXboxGameSaveTask 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/TaskScheduler/EnableXboxGameSaveTask

#### <a name="windows10endpointprotectionconfigurationxboxservicesliveauthmanagerservicestartupmode"></a>Windows10EndpointProtectionConfiguration.XboxServicesLiveAuthManagerServiceStartupMode 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/SystemServices/ConfigureXboxLiveAuthManagerServiceStartupMode

#### <a name="windows10endpointprotectionconfigurationxboxserviceslivegamesaveservicestartupmode"></a>Windows10EndpointProtectionConfiguration.XboxServicesLiveGameSaveServiceStartupMode 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/SystemServices/XboxServicesLiveGameSaveServiceStartupMode

#### <a name="windows10endpointprotectionconfigurationxboxserviceslivenetworkingservicestartupmode"></a>Windows10EndpointProtectionConfiguration.XboxServicesLiveNetworkingServiceStartupMode 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/SystemServices/ConfigureXboxLiveNetworkingServiceStartupMode

#### <a name="windows10enterprisemodernappmanagementconfigurationuninstallbuiltinapps"></a>Windows10EnterpriseModernAppManagementConfiguration.UninstallBuiltInApps
**FOURNISSEUR DE SERVICES CRYPTOGRAPHIQUES**: Appel d’API de graphique de n/a uniquement **URI décalage**: Appel d’API de graphique de n/a uniquement

#### <a name="windows10generalconfigurationaccountsblockaddingnonmicrosoftaccountemail"></a>Windows10GeneralConfiguration.AccountsBlockAddingNonMicrosoftAccountEmail 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Accounts/AllowAddingNonMicrosoftAccountsManually

#### <a name="windows10generalconfigurationantitheftmodeblocked"></a>Windows10GeneralConfiguration.AntiTheftModeBlocked 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Security/AntiTheftMode

#### <a name="windows10generalconfigurationappmanagementmsiallowusercontroloverinstall"></a>Windows10GeneralConfiguration.AppManagementMSIAllowUserControlOverInstall 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/ApplicationManagement/MSIAllowUserControlOverInstall

#### <a name="windows10generalconfigurationappmanagementmsialwaysinstallwithelevatedprivileges"></a>Windows10GeneralConfiguration.AppManagementMSIAlwaysInstallWithElevatedPrivileges 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/ApplicationManagement/MSIAlwaysInstallWithElevatedPrivileges

#### <a name="windows10generalconfigurationappsallowtrustedappssideloading"></a>Windows10GeneralConfiguration.AppsAllowTrustedAppsSideloading 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/ApplicationManagement/AllowAllTrustedApps

#### <a name="windows10generalconfigurationappsblockwindowsstoreoriginatedapps"></a>Windows10GeneralConfiguration.AppsBlockWindowsStoreOriginatedApps 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/ApplicationManagement/DisableStoreOriginatedApps

#### <a name="windows10generalconfigurationappsmicrosoftaccountsoptional"></a>Windows10GeneralConfiguration.AppsMicrosoftAccountsOptional 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/AppRuntime/AllowMicrosoftAccountsToBeOptional

#### <a name="windows10generalconfigurationassignedaccessmultimodeprofiles"></a>Windows10GeneralConfiguration.AssignedAccessMultiModeProfiles 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/AssignedAccess  
**Décalage d’URI**: configuration

#### <a name="windows10generalconfigurationassignedaccesssinglemodeappusermodelid"></a>Windows10GeneralConfiguration.AssignedAccessSingleModeAppUserModelId 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/AssignedAccess  
**Décalage d’URI**: configuration

#### <a name="windows10generalconfigurationassignedaccesssinglemodeusername"></a>Windows10GeneralConfiguration.AssignedAccessSingleModeUserName 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/AssignedAccess  
**Décalage d’URI**: configuration

#### <a name="windows10generalconfigurationauthenticationallowfidodevice"></a>Windows10GeneralConfiguration.AuthenticationAllowFIDODevice 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Authentication/AllowFidoDeviceSignon

#### <a name="windows10generalconfigurationauthenticationallowsecondarydevice"></a>Windows10GeneralConfiguration.AuthenticationAllowSecondaryDevice 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Authentication/AllowSecondaryAuthenticationDevice

#### <a name="windows10generalconfigurationauthenticationpreferredazureadtenantdomainname"></a>Windows10GeneralConfiguration.AuthenticationPreferredAzureADTenantDomainName 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Authentication/PreferredAadTenantDomainName

#### <a name="windows10generalconfigurationauthenticationwebsignin"></a>Windows10GeneralConfiguration.AuthenticationWebSignIn 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Authentication/EnableWebSignIn

#### <a name="windows10generalconfigurationautoplaydefaultautorunbehavior"></a>Windows10GeneralConfiguration.AutoPlayDefaultAutoRunBehavior 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Autoplay/SetDefaultAutoRunBehavior

#### <a name="windows10generalconfigurationautoplayfornonvolumedevices"></a>Windows10GeneralConfiguration.AutoPlayForNonVolumeDevices 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Autoplay/DisallowAutoplayForNonVolumeDevices

#### <a name="windows10generalconfigurationautoplaymode"></a>Windows10GeneralConfiguration.AutoPlayMode 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Autoplay/TurnOffAutoPlay

#### <a name="windows10generalconfigurationbluetoothallowedservices"></a>Windows10GeneralConfiguration.BluetoothAllowedServices 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Bluetooth/ServicesAllowedList

#### <a name="windows10generalconfigurationbluetoothblockadvertising"></a>Windows10GeneralConfiguration.BluetoothBlockAdvertising 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Bluetooth/AllowAdvertising

#### <a name="windows10generalconfigurationbluetoothblockdiscoverablemode"></a>Windows10GeneralConfiguration.BluetoothBlockDiscoverableMode 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Bluetooth/AllowDiscoverableMode

#### <a name="windows10generalconfigurationbluetoothblocked"></a>Windows10GeneralConfiguration.BluetoothBlocked 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Connectivity/AllowBluetooth

#### <a name="windows10generalconfigurationbluetoothblockprepairing"></a>Windows10GeneralConfiguration.BluetoothBlockPrePairing 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Bluetooth/AllowPrepairing

#### <a name="windows10generalconfigurationbluetoothblockpromptedproximalconnections"></a>Windows10GeneralConfiguration.BluetoothBlockPromptedProximalConnections 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Bluetooth/AllowPromptedProximalConnections

#### <a name="windows10generalconfigurationbluetoothdevicename"></a>Windows10GeneralConfiguration.BluetoothDeviceName 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Bluetooth/LocalDeviceName

#### <a name="windows10generalconfigurationbootstartdriverinitialization"></a>windows10generalconfiguration.bootStartDriverInitialization 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/System/BootStartDriverInitialization

#### <a name="windows10generalconfigurationcamerablocked"></a>Windows10GeneralConfiguration.CameraBlocked 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Camera/AllowCamera

#### <a name="windows10generalconfigurationcellularblockdatawhenroaming"></a>Windows10GeneralConfiguration.CellularBlockDataWhenRoaming 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Connectivity/AllowCellularDataRoaming

#### <a name="windows10generalconfigurationcellularblockvpn"></a>Windows10GeneralConfiguration.CellularBlockVpn 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Connectivity/AllowVPNOverCellular

#### <a name="windows10generalconfigurationcellularblockvpnwhenroaming"></a>Windows10GeneralConfiguration.CellularBlockVpnWhenRoaming 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Connectivity/AllowVPNRoamingOverCellular

#### <a name="windows10generalconfigurationcellulardata"></a>Windows10GeneralConfiguration.CellularData 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Connectivity/AllowCellularData

#### <a name="windows10generalconfigurationcertificatesblockmanualrootcertificateinstallation"></a>Windows10GeneralConfiguration.CertificatesBlockManualRootCertificateInstallation 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Security/AllowManualRootCertificateInstallation

#### <a name="windows10generalconfigurationconnecteddevicesserviceblocked"></a>Windows10GeneralConfiguration.ConnectedDevicesServiceBlocked 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Connectivity/AllowConnectedDevices

#### <a name="windows10generalconfigurationcopypasteblocked"></a>Windows10GeneralConfiguration.CopyPasteBlocked 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Experience/AllowCopyPaste

#### <a name="windows10generalconfigurationcortanablocked"></a>Windows10GeneralConfiguration.CortanaBlocked 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/AboveLock/AllowCortanaAboveLock

#### <a name="windows10generalconfigurationcryptographyallowfipsalgorithmpolicy"></a>Windows10GeneralConfiguration.CryptographyAllowFipsAlgorithmPolicy 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Cryptography/AllowFipsAlgorithmPolicy

#### <a name="windows10generalconfigurationdataprotectionblockdirectmemoryaccess"></a>Windows10GeneralConfiguration.DataProtectionBlockDirectMemoryAccess 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/DataProtection/AllowDirectMemoryAccess

#### <a name="windows10generalconfigurationdefenderblockenduseraccess"></a>Windows10GeneralConfiguration.DefenderBlockEndUserAccess 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AllowUserUIAccess

#### <a name="windows10generalconfigurationdefenderblockonaccessprotection"></a>Windows10GeneralConfiguration.DefenderBlockOnAccessProtection 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AllowOnAccessProtection

#### <a name="windows10generalconfigurationdefendercloudblocklevel"></a>Windows10GeneralConfiguration.DefenderCloudBlockLevel 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/CloudBlockLevel

#### <a name="windows10generalconfigurationdefendercloudextendedtimeout"></a>Windows10GeneralConfiguration.DefenderCloudExtendedTimeout 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/CloudExtendedTimeout

#### <a name="windows10generalconfigurationdefendercloudextendedtimeoutinseconds"></a>Windows10GeneralConfiguration.DefenderCloudExtendedTimeoutInSeconds 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/CloudExtendedTimeout

#### <a name="windows10generalconfigurationdefenderdaysbeforedeletingquarantinedmalware"></a>Windows10GeneralConfiguration.DefenderDaysBeforeDeletingQuarantinedMalware 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/DaysToRetainCleanedMalware

#### <a name="windows10generalconfigurationdefenderdetectedmalwareactions"></a>Windows10GeneralConfiguration.DefenderDetectedMalwareActions 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/ThreatSeverityDefaultAction

#### <a name="windows10generalconfigurationdefenderfileextensionstoexclude"></a>Windows10GeneralConfiguration.DefenderFileExtensionsToExclude 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/ExcludedExtensions

#### <a name="windows10generalconfigurationdefenderfilesandfolderstoexclude"></a>Windows10GeneralConfiguration.DefenderFilesAndFoldersToExclude 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/ExcludedPaths

#### <a name="windows10generalconfigurationdefendermonitorfileactivity"></a>Windows10GeneralConfiguration.DefenderMonitorFileActivity 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AllowRealtimeMonitoring

#### <a name="windows10generalconfigurationdefenderpotentiallyunwantedappaction"></a>Windows10GeneralConfiguration.DefenderPotentiallyUnwantedAppAction 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/PUAProtection

#### <a name="windows10generalconfigurationdefenderpotentiallyunwantedappactionsetting"></a>Windows10GeneralConfiguration.DefenderPotentiallyUnwantedAppActionSetting 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/PUAProtection

#### <a name="windows10generalconfigurationdefenderprocessestoexclude"></a>Windows10GeneralConfiguration.DefenderProcessesToExclude 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/ExcludedProcesses

#### <a name="windows10generalconfigurationdefenderpromptforsamplesubmission"></a>Windows10GeneralConfiguration.DefenderPromptForSampleSubmission 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/SubmitSamplesConsent

#### <a name="windows10generalconfigurationdefenderrequirebehaviormonitoring"></a>Windows10GeneralConfiguration.DefenderRequireBehaviorMonitoring 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AllowBehaviorMonitoring

#### <a name="windows10generalconfigurationdefenderrequirecloudprotection"></a>Windows10GeneralConfiguration.DefenderRequireCloudProtection 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AllowCloudProtection

#### <a name="windows10generalconfigurationdefenderrequirenetworkinspectionsystem"></a>Windows10GeneralConfiguration.DefenderRequireNetworkInspectionSystem 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AllowIntrusionPreventionSystem

#### <a name="windows10generalconfigurationdefenderrequirerealtimemonitoring"></a>Windows10GeneralConfiguration.DefenderRequireRealTimeMonitoring 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AllowRealtimeMonitoring

#### <a name="windows10generalconfigurationdefenderscanarchivefiles"></a>Windows10GeneralConfiguration.DefenderScanArchiveFiles 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AllowArchiveScanning

#### <a name="windows10generalconfigurationdefenderscandownloads"></a>Windows10GeneralConfiguration.DefenderScanDownloads 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AllowIOAVProtection

#### <a name="windows10generalconfigurationdefenderscanincomingmail"></a>Windows10GeneralConfiguration.DefenderScanIncomingMail 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AllowScanningNetworkFiles

#### <a name="windows10generalconfigurationdefenderscanmappednetworkdrivesduringfullscan"></a>Windows10GeneralConfiguration.DefenderScanMappedNetworkDrivesDuringFullScan 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AllowFullScanOnMappedNetworkDrives

#### <a name="windows10generalconfigurationdefenderscanmaxcpu"></a>Windows10GeneralConfiguration.DefenderScanMaxCpu 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AvgCPULoadFactor

#### <a name="windows10generalconfigurationdefenderscannetworkfiles"></a>Windows10GeneralConfiguration.DefenderScanNetworkFiles 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AllowScanningNetworkFiles

#### <a name="windows10generalconfigurationdefenderscanremovabledrivesduringfullscan"></a>Windows10GeneralConfiguration.DefenderScanRemovableDrivesDuringFullScan 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AllowFullScanRemovableDriveScanning

#### <a name="windows10generalconfigurationdefenderscanscriptsloadedininternetexplorer"></a>Windows10GeneralConfiguration.DefenderScanScriptsLoadedInInternetExplorer 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/AllowScriptScanning

#### <a name="windows10generalconfigurationdefenderscantype"></a>Windows10GeneralConfiguration.DefenderScanType 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/ScanParameter

#### <a name="windows10generalconfigurationdefenderscheduledquickscantime"></a>Windows10GeneralConfiguration.DefenderScheduledQuickScanTime 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/ScheduleQuickScanTime

#### <a name="windows10generalconfigurationdefenderscheduledscantime"></a>Windows10GeneralConfiguration.DefenderScheduledScanTime 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/ScheduleScanTime

#### <a name="windows10generalconfigurationdefenderschedulescanday"></a>Windows10GeneralConfiguration.DefenderScheduleScanDay 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/ScheduleScanDay

#### <a name="windows10generalconfigurationdefendersignatureupdateintervalinhours"></a>Windows10GeneralConfiguration.DefenderSignatureUpdateIntervalInHours 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/SignatureUpdateInterval

#### <a name="windows10generalconfigurationdefendersubmitsamplesconsenttype"></a>Windows10GeneralConfiguration.DefenderSubmitSamplesConsentType 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/SubmitSamplesConsent

#### <a name="windows10generalconfigurationdefendersystemscanschedule"></a>Windows10GeneralConfiguration.DefenderSystemScanSchedule 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Defender/ScheduleScanDay

#### <a name="windows10generalconfigurationdeveloperunlocksetting"></a>Windows10GeneralConfiguration.DeveloperUnlockSetting 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/ApplicationManagement/AllowDeveloperUnlock

#### <a name="windows10generalconfigurationdevicemanagementblockfactoryresetonmobile"></a>Windows10GeneralConfiguration.DeviceManagementBlockFactoryResetOnMobile 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/System/AllowUserToResetPhone

#### <a name="windows10generalconfigurationdevicemanagementblockmanualunenroll"></a>Windows10GeneralConfiguration.DeviceManagementBlockManualUnenroll 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Experience/AllowManualMDMUnenrollment

#### <a name="windows10generalconfigurationdiagnosticsdatasubmissionmode"></a>Windows10GeneralConfiguration.DiagnosticsDataSubmissionMode 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/System/AllowTelemetry

#### <a name="windows10generalconfigurationdisplayapplistwithgdidpiscalingturnedoff"></a>Windows10GeneralConfiguration.DisplayAppListWithGdiDPIScalingTurnedOff 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Display/TurnOffGdiDPIScalingForApps

#### <a name="windows10generalconfigurationdisplayapplistwithgdidpiscalingturnedon"></a>Windows10GeneralConfiguration.DisplayAppListWithGdiDPIScalingTurnedOn 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Display/TurnOnGdiDPIScalingForApps

#### <a name="windows10generalconfigurationedgeallowstartpagesmodification"></a>Windows10GeneralConfiguration.EdgeAllowStartPagesModification 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/HomePages

#### <a name="windows10generalconfigurationedgeblockaccesstoaboutflags"></a>Windows10GeneralConfiguration.EdgeBlockAccessToAboutFlags 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/PreventAccessToAboutFlagsInMicrosoftEdge

#### <a name="windows10generalconfigurationedgeblockaddressbardropdown"></a>Windows10GeneralConfiguration.EdgeBlockAddressBarDropdown 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/AllowAddressBarDropdown

#### <a name="windows10generalconfigurationedgeblockautofill"></a>Windows10GeneralConfiguration.EdgeBlockAutofill 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/AllowAutofill

#### <a name="windows10generalconfigurationedgeblockcompatibilitylist"></a>Windows10GeneralConfiguration.EdgeBlockCompatibilityList 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/AllowMicrosoftCompatibilityList

#### <a name="windows10generalconfigurationedgeblockdevelopertools"></a>Windows10GeneralConfiguration.EdgeBlockDeveloperTools 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/AllowDeveloperTools

#### <a name="windows10generalconfigurationedgeblocked"></a>Windows10GeneralConfiguration.EdgeBlocked 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/AllowBrowser

#### <a name="windows10generalconfigurationedgeblockeditfavorites"></a>Windows10GeneralConfiguration.EdgeBlockEditFavorites 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/LockdownFavorites

#### <a name="windows10generalconfigurationedgeblockextensions"></a>Windows10GeneralConfiguration.EdgeBlockExtensions 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/AllowExtensions

#### <a name="windows10generalconfigurationedgeblockfullscreenmode"></a>Windows10GeneralConfiguration.EdgeBlockFullScreenMode 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/AllowFullScreenMode

#### <a name="windows10generalconfigurationedgeblockinprivatebrowsing"></a>Windows10GeneralConfiguration.EdgeBlockInPrivateBrowsing 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/AllowInPrivate

#### <a name="windows10generalconfigurationedgeblocklivetiledatacollection"></a>Windows10GeneralConfiguration.EdgeBlockLiveTileDataCollection 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/PreventLiveTileDataCollection

#### <a name="windows10generalconfigurationedgeblockpasswordmanager"></a>Windows10GeneralConfiguration.EdgeBlockPasswordManager 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/AllowPasswordManager

#### <a name="windows10generalconfigurationedgeblockpopups"></a>Windows10GeneralConfiguration.EdgeBlockPopups 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/AllowPopups

#### <a name="windows10generalconfigurationedgeblockprelaunch"></a>Windows10GeneralConfiguration.EdgeBlockPrelaunch 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/AllowPrelaunch

#### <a name="windows10generalconfigurationedgeblockprinting"></a>Windows10GeneralConfiguration.EdgeBlockPrinting 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/AllowPrinting

#### <a name="windows10generalconfigurationedgeblocksavinghistory"></a>Windows10GeneralConfiguration.EdgeBlockSavingHistory 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/AllowSavingHistory

#### <a name="windows10generalconfigurationedgeblocksearchsuggestions"></a>Windows10GeneralConfiguration.EdgeBlockSearchSuggestions 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/AllowSearchSuggestionsinAddressBar

#### <a name="windows10generalconfigurationedgeblocksendingdonottrackheader"></a>Windows10GeneralConfiguration.EdgeBlockSendingDoNotTrackHeader 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/AllowDoNotTrack

#### <a name="windows10generalconfigurationedgeblocksendingintranettraffictointernetexplorer"></a>Windows10GeneralConfiguration.EdgeBlockSendingIntranetTrafficToInternetExplorer 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/SendIntranetTraffictoInternetExplorer

#### <a name="windows10generalconfigurationedgeblocksideloadingextensions"></a>Windows10GeneralConfiguration.EdgeBlockSideloadingExtensions 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/AllowSideloadingOfExtensions

#### <a name="windows10generalconfigurationedgeblocktabpreloading"></a>Windows10GeneralConfiguration.EdgeBlockTabPreloading 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/AllowTabPreloading

#### <a name="windows10generalconfigurationedgeblockwebcontentonnewtabpage"></a>Windows10GeneralConfiguration.EdgeBlockWebContentOnNewTabPage 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/AllowWebContentOnNewTabPage

#### <a name="windows10generalconfigurationedgeclearbrowsingdataonexit"></a>Windows10GeneralConfiguration.EdgeClearBrowsingDataOnExit 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/ClearBrowsingDataOnExit

#### <a name="windows10generalconfigurationedgecookiepolicy"></a>Windows10GeneralConfiguration.EdgeCookiePolicy 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/AllowCookies

#### <a name="windows10generalconfigurationedgedisablefirstrunpage"></a>Windows10GeneralConfiguration.EdgeDisableFirstRunPage 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/PreventFirstRunPage

#### <a name="windows10generalconfigurationedgeenterprisemodesitelistlocation"></a>Windows10GeneralConfiguration.EdgeEnterpriseModeSiteListLocation 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/EnterpriseSiteListServiceUrl

#### <a name="windows10generalconfigurationedgefavoritesbarvisibility"></a>Windows10GeneralConfiguration.EdgeFavoritesBarVisibility 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/ConfigureFavoritesBar

#### <a name="windows10generalconfigurationedgefavoriteslistlocation"></a>Windows10GeneralConfiguration.EdgeFavoritesListLocation 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/ProvisionFavorites

#### <a name="windows10generalconfigurationedgefirstrunurl"></a>Windows10GeneralConfiguration.EdgeFirstRunUrl 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/FirstRunURL

#### <a name="windows10generalconfigurationedgehomebuttonconfiguration"></a>Windows10GeneralConfiguration.EdgeHomeButtonConfiguration 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/SetHomeButtonURL

#### <a name="windows10generalconfigurationedgehomebuttonconfigurationenabled"></a>Windows10GeneralConfiguration.EdgeHomeButtonConfigurationEnabled 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/ConfigureHomeButton

#### <a name="windows10generalconfigurationedgehomepageurls"></a>Windows10GeneralConfiguration.EdgeHomepageUrls 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/SetHomeButtonURL

#### <a name="windows10generalconfigurationedgenewtabpageurl"></a>Windows10GeneralConfiguration.EdgeNewTabPageURL 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/SetNewTabPageURL

#### <a name="windows10generalconfigurationedgeopenswith"></a>Windows10GeneralConfiguration.EdgeOpensWith 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/ConfigureOpenMicrosoftEdgeWith

#### <a name="windows10generalconfigurationedgepreventcertificateerroroverride"></a>Windows10GeneralConfiguration.EdgePreventCertificateErrorOverride 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/PreventCertErrorOverrides

#### <a name="windows10generalconfigurationedgerequiresmartscreen"></a>Windows10GeneralConfiguration.EdgeRequireSmartScreen 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/AllowSmartScreen

#### <a name="windows10generalconfigurationedgesearchengine"></a>Windows10GeneralConfiguration.EdgeSearchEngine 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/SetDefaultSearchEngine

#### <a name="windows10generalconfigurationedgesendintranettraffictointernetexplorer"></a>Windows10GeneralConfiguration.EdgeSendIntranetTrafficToInternetExplorer 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/SendIntranetTraffictoInternetExplorer

#### <a name="windows10generalconfigurationedgeshowmessagewhenopeninginternetexplorersites"></a>Windows10GeneralConfiguration.EdgeShowMessageWhenOpeningInternetExplorerSites 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/ShowMessageWhenOpeningSitesInInternetExplorer

#### <a name="windows10generalconfigurationedgesyncfavoriteswithinternetexplorer"></a>Windows10GeneralConfiguration.EdgeSyncFavoritesWithInternetExplorer 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/SyncFavoritesBetweenIEAndMicrosoftEdge

#### <a name="windows10generalconfigurationedgetelemetryformicrosoft365analytics"></a>Windows10GeneralConfiguration.EdgeTelemetryForMicrosoft365Analytics 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/ConfigureTelemetryForMicrosoft365Analytics

#### <a name="windows10generalconfigurationenableautomaticredeployment"></a>Windows10GeneralConfiguration.EnableAutomaticRedeployment 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/CredentialProviders/DisableAutomaticReDeploymentCredentials

#### <a name="windows10generalconfigurationenterprisecloudprintdiscoveryendpoint"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintDiscoveryEndPoint 
**Fournisseur de services cryptographiques**: ./User/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/EnterpriseCloudPrint/CloudPrinterDiscoveryEndPoint

#### <a name="windows10generalconfigurationenterprisecloudprintdiscoverymaxlimit"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintDiscoveryMaxLimit 
**Fournisseur de services cryptographiques**: ./User/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/EnterpriseCloudPrint/DiscoveryMaxPrinterLimit

#### <a name="windows10generalconfigurationenterprisecloudprintmopriadiscoveryresourceidentifier"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintMopriaDiscoveryResourceIdentifier 
**Fournisseur de services cryptographiques**: ./User/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/EnterpriseCloudPrint/MopriaDiscoveryResourceId

#### <a name="windows10generalconfigurationenterprisecloudprintoauthauthority"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintOAuthAuthority 
**Fournisseur de services cryptographiques**: ./User/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/EnterpriseCloudPrint/CloudPrintOAuthAuthority

#### <a name="windows10generalconfigurationenterprisecloudprintoauthclientidentifier"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintOAuthClientIdentifier 
**Fournisseur de services cryptographiques**: ./User/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/EnterpriseCloudPrint/CloudPrintOAuthAuthority

#### <a name="windows10generalconfigurationenterprisecloudprintresourceidentifier"></a>Windows10GeneralConfiguration.EnterpriseCloudPrintResourceIdentifier 
**Fournisseur de services cryptographiques**: ./User/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/EnterpriseCloudPrint/CloudPrintResourceId

#### <a name="windows10generalconfigurationexperienceblockconsumerspecificfeatures"></a>Windows10GeneralConfiguration.ExperienceBlockConsumerSpecificFeatures 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Experience/AllowWindowsConsumerFeatures

#### <a name="windows10generalconfigurationexperienceblockdevicediscovery"></a>Windows10GeneralConfiguration.ExperienceBlockDeviceDiscovery 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Experience/AllowDeviceDiscovery

#### <a name="windows10generalconfigurationexperienceblockerrordialogwhennosim"></a>Windows10GeneralConfiguration.ExperienceBlockErrorDialogWhenNoSIM 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Experience/AllowSIMErrorDialogPromptWhenNoSIM

#### <a name="windows10generalconfigurationexperienceblocktaskswitcher"></a>Windows10GeneralConfiguration.ExperienceBlockTaskSwitcher 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Experience/AllowTaskSwitcher

#### <a name="windows10generalconfigurationexperienceblockwindowsspotlight"></a>Windows10GeneralConfiguration.ExperienceBlockWindowsSpotlight 
**Fournisseur de services cryptographiques**: ./User/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Experience/AllowWindowsSpotlight

#### <a name="windows10generalconfigurationexperiencedonotsyncbrowsersettings"></a>Windows10GeneralConfiguration.ExperienceDoNotSyncBrowserSettings 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Experience/DoNotSyncBrowserSettings

#### <a name="windows10generalconfigurationgamedvrblocked"></a>Windows10GeneralConfiguration.GameDvrBlocked 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/ApplicationManagement/AllowGameDVR

#### <a name="windows10generalconfigurationhardwaredeviceinstallationbydeviceidentifiers"></a>Windows10GeneralConfiguration.HardwareDeviceInstallationByDeviceIdentifiers 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/DeviceInstallation/PreventInstallationOfMatchingDeviceIDs

#### <a name="windows10generalconfigurationhardwaredeviceinstallationbysetupclasses"></a>Windows10GeneralConfiguration.HardwareDeviceInstallationBySetupClasses 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/DeviceInstallation/PreventInstallationOfMatchingDeviceSetupClasses

#### <a name="windows10generalconfigurationinkworkspaceaccess"></a>Windows10GeneralConfiguration.InkWorkspaceAccess 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WindowsInkWorkspace/AllowWindowsInkWorkspace

#### <a name="windows10generalconfigurationinkworkspaceaccessstate"></a>Windows10GeneralConfiguration.InkWorkspaceAccessState 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WindowsInkWorkspace/AllowWindowsInkWorkspace

#### <a name="windows10generalconfigurationinkworkspaceblocksuggestedapps"></a>Windows10GeneralConfiguration.InkWorkspaceBlockSuggestedApps 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WindowsInkWorkspace/AllowSuggestedAppsInWindowsInkWorkspace

#### <a name="windows10generalconfigurationinternetexploreractivexcontrolsinprotectedmode"></a>Windows10GeneralConfiguration.InternetExplorerActiveXControlsInProtectedMode 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/DoNotAllowActiveXControlsInProtectedMode

#### <a name="windows10generalconfigurationinternetexplorerautocomplete"></a>Windows10GeneralConfiguration.InternetExplorerAutoComplete 
**Fournisseur de services cryptographiques**: ./User/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/AllowAutoComplete

#### <a name="windows10generalconfigurationinternetexplorerblockoutdatedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerBlockOutdatedActiveXControls 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/DoNotBlockOutdatedActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerbypasssmartscreenwarnings"></a>Windows10GeneralConfiguration.InternetExplorerBypassSmartScreenWarnings 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/DisableBypassOfSmartScreenWarnings

#### <a name="windows10generalconfigurationinternetexplorerbypasssmartscreenwarningsaboutuncommonfiles"></a>Windows10GeneralConfiguration.InternetExplorerBypassSmartScreenWarningsAboutUncommonFiles 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/DisableBypassOfSmartScreenWarningsAboutUncommonFiles

#### <a name="windows10generalconfigurationinternetexplorercertificateaddressmismatchwarning"></a>Windows10GeneralConfiguration.InternetExplorerCertificateAddressMismatchWarning 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/AllowCertificateAddressMismatchWarning

#### <a name="windows10generalconfigurationinternetexplorercheckservercertificaterevocation"></a>Windows10GeneralConfiguration.InternetExplorerCheckServerCertificateRevocation 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/CheckServerCertificateRevocation

#### <a name="windows10generalconfigurationinternetexplorerchecksignaturesondownloadedprograms"></a>Windows10GeneralConfiguration.InternetExplorerCheckSignaturesOnDownloadedPrograms 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/CheckSignaturesOnDownloadedPrograms

#### <a name="windows10generalconfigurationinternetexplorercrashdetection"></a>Windows10GeneralConfiguration.InternetExplorerCrashDetection 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/DisableCrashDetection

#### <a name="windows10generalconfigurationinternetexplorerdisableprocessesinenhancedprotectedmode"></a>Windows10GeneralConfiguration.InternetExplorerDisableProcessesInEnhancedProtectedMode 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/DisableProcessesInEnhancedProtectedMode

#### <a name="windows10generalconfigurationinternetexplorerdownloadenclosures"></a>Windows10GeneralConfiguration.InternetExplorerDownloadEnclosures 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/DisableEnclosureDownloading

#### <a name="windows10generalconfigurationinternetexplorerencryptionsupport"></a>Windows10GeneralConfiguration.InternetExplorerEncryptionSupport 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/DisableEncryptionSupport

#### <a name="windows10generalconfigurationinternetexplorerenhancedprotectedmode"></a>Windows10GeneralConfiguration.InternetExplorerEnhancedProtectedMode 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/AllowEnhancedProtectedMode

#### <a name="windows10generalconfigurationinternetexplorerfallbacktossl3"></a>Windows10GeneralConfiguration.InternetExplorerFallbackToSsl3 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/AllowFallbackToSSL3

#### <a name="windows10generalconfigurationinternetexplorerignorecertificateerrors"></a>Windows10GeneralConfiguration.InternetExplorerIgnoreCertificateErrors 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/DisableIgnoringCertificateErrors

#### <a name="windows10generalconfigurationinternetexplorerincludeallnetworkpaths"></a>Windows10GeneralConfiguration.InternetExplorerIncludeAllNetworkPaths 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/IncludeAllNetworkPaths

#### <a name="windows10generalconfigurationinternetexplorerinternetzoneaccesstodatasources"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneAccessToDataSources 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneAllowAccessToDataSources

#### <a name="windows10generalconfigurationinternetexplorerinternetzoneallowonlyapproveddomainstouseactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneAllowOnlyApprovedDomainsToUseActiveXControls 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneAllowOnlyApprovedDomainsToUseActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerinternetzoneallowonlyapproveddomainstousetdcactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneAllowOnlyApprovedDomainsToUseTdcActiveXControls 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneAllowOnlyApprovedDomainsToUseTDCActiveXControl

#### <a name="windows10generalconfigurationinternetexplorerinternetzoneallowvbscripttorun"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneAllowVBScriptToRun 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneAllowVBScriptToRunInInternetExplorer

#### <a name="windows10generalconfigurationinternetexplorerinternetzoneautomaticpromptforfiledownloads"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneAutomaticPromptForFileDownloads 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneAllowAutomaticPromptingForFileDownloads

#### <a name="windows10generalconfigurationinternetexplorerinternetzonecopyandpasteviascript"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneCopyAndPasteViaScript 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneAllowCopyPasteViaScript

#### <a name="windows10generalconfigurationinternetexplorerinternetzonecrosssitescriptingfilter"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneCrossSiteScriptingFilter 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneEnableCrossSiteScriptingFilter

#### <a name="windows10generalconfigurationinternetexplorerinternetzonedonotrunantimalwareagainstactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDoNotRunAntimalwareAgainstActiveXControls 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneDoNotRunAntimalwareAgainstActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerinternetzonedotnetframeworkreliantcomponents"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDotNetFrameworkReliantComponents 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneAllowNETFrameworkReliantComponents

#### <a name="windows10generalconfigurationinternetexplorerinternetzonedownloadsignedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDownloadSignedActiveXControls 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneDownloadSignedActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerinternetzonedownloadunsignedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDownloadUnsignedActiveXControls 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneDownloadUnsignedActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerinternetzonedraganddroporcopyandpastefiles"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDragAndDropOrCopyAndPasteFiles 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneAllowDragAndDropCopyAndPasteFiles

#### <a name="windows10generalconfigurationinternetexplorerinternetzonedragcontentfromdifferentdomainsacrosswindows"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDragContentFromDifferentDomainsAcrossWindows 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneEnableDraggingOfContentFromDifferentDomainsAcrossWindows

#### <a name="windows10generalconfigurationinternetexplorerinternetzonedragcontentfromdifferentdomainswithinwindows"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneDragContentFromDifferentDomainsWithinWindows 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneEnableDraggingOfContentFromDifferentDomainsWithinWindows

#### <a name="windows10generalconfigurationinternetexplorerinternetzoneincludelocalpathwhenuploadingfilestoserver"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneIncludeLocalPathWhenUploadingFilesToServer 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneIncludeLocalPathWhenUploadingFilesToServer

#### <a name="windows10generalconfigurationinternetexplorerinternetzoneinitializeandscriptactivexcontrolsnotmarkedassafe"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneInitializeAndScriptActiveXControlsNotMarkedAsSafe 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneInitializeAndScriptActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerinternetzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneJavaPermissions 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneJavaPermissions


#### <a name="windows10generalconfigurationinternetexplorerinternetzonelaunchapplicationsandfilesinaniframe"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneLaunchApplicationsAndFilesInAnIFrame 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneLaunchingApplicationsAndFilesInIFRAME

#### <a name="windows10generalconfigurationinternetexplorerinternetzonelessprivilegedsites"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneLessPrivilegedSites 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneAllowLessPrivilegedSites

#### <a name="windows10generalconfigurationinternetexplorerinternetzoneloadingofxamlfiles"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneLoadingOfXamlFiles 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneAllowLoadingOfXAMLFiles

#### <a name="windows10generalconfigurationinternetexplorerinternetzonelogonoptions"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneLogonOptions 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneLogonOptions

#### <a name="windows10generalconfigurationinternetexplorerinternetzonenavigatewindowsandframesacrossdifferentdomains"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneNavigateWindowsAndFramesAcrossDifferentDomains 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneNavigateWindowsAndFrames

#### <a name="windows10generalconfigurationinternetexplorerinternetzonepopupblocker"></a>Windows10GeneralConfiguration.InternetExplorerInternetZonePopupBlocker 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneUsePopupBlocker

#### <a name="windows10generalconfigurationinternetexplorerinternetzoneprotectedmode"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneProtectedMode 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneEnableProtectedMode

#### <a name="windows10generalconfigurationinternetexplorerinternetzonerundotnetframeworkreliantcomponentssignedwithauthenticode"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneRunDotNetFrameworkReliantComponentsSignedWithAuthenticode 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneRunNETFrameworkReliantComponentsSignedWithAuthenticode

#### <a name="windows10generalconfigurationinternetexplorerinternetzonescriptingofwebbrowsercontrols"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneScriptingOfWebBrowserControls 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneAllowScriptingOfInternetExplorerWebBrowserControls

#### <a name="windows10generalconfigurationinternetexplorerinternetzonescriptinitiatedwindows"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneScriptInitiatedWindows 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneAllowScriptInitiatedWindows

#### <a name="windows10generalconfigurationinternetexplorerinternetzonescriptlets"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneScriptlets 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneAllowScriptlets

#### <a name="windows10generalconfigurationinternetexplorerinternetzonesecuritywarningforpotentiallyunsafefiles"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneSecurityWarningForPotentiallyUnsafeFiles 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneShowSecurityWarningForPotentiallyUnsafeFiles

#### <a name="windows10generalconfigurationinternetexplorerinternetzonesmartscreen"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneSmartScreen 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneAllowSmartScreenIE

#### <a name="windows10generalconfigurationinternetexplorerinternetzoneupdatestostatusbarviascript"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneUpdatesToStatusBarViaScript 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneAllowUpdatesToStatusBarViaScript

#### <a name="windows10generalconfigurationinternetexplorerinternetzoneuserdatapersistence"></a>Windows10GeneralConfiguration.InternetExplorerInternetZoneUserDataPersistence 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/InternetZoneAllowUserDataPersistence

#### <a name="windows10generalconfigurationinternetexplorerintranetzonedonotrunantimalwareagainstactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerIntranetZoneDoNotRunAntimalwareAgainstActiveXControls 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/IntranetZoneDoNotRunAntimalwareAgainstActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerintranetzoneinitializeandscriptactivexcontrolsnotmarkedassafe"></a>Windows10GeneralConfiguration.InternetExplorerIntranetZoneInitializeAndScriptActiveXControlsNotMarkedAsSafe 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/IntranetZoneInitializeAndScriptActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerintranetzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerIntranetZoneJavaPermissions 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/IntranetZoneJavaPermissions

#### <a name="windows10generalconfigurationinternetexplorerlocalmachinezonedonotrunantimalwareagainstactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerLocalMachineZoneDoNotRunAntimalwareAgainstActiveXControls 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/LocalMachineZoneDoNotRunAntimalwareAgainstActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerlocalmachinezonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerLocalMachineZoneJavaPermissions 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/LocalMachineZoneJavaPermissions

#### <a name="windows10generalconfigurationinternetexplorerlockeddowninternetzonesmartscreen"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownInternetZoneSmartScreen 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/LockedDownInternetZoneAllowSmartScreenIE

#### <a name="windows10generalconfigurationinternetexplorerlockeddownintranetzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownIntranetZoneJavaPermissions 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/LockedDownIntranetJavaPermissions

#### <a name="windows10generalconfigurationinternetexplorerlockeddownlocalmachinezonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownLocalMachineZoneJavaPermissions 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/LockedDownLocalMachineZoneJavaPermissions

#### <a name="windows10generalconfigurationinternetexplorerlockeddownrestrictedzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownRestrictedZoneJavaPermissions 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/LockedDownRestrictedSitesZoneJavaPermissions

#### <a name="windows10generalconfigurationinternetexplorerlockeddownrestrictedzonesmartscreen"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownRestrictedZoneSmartScreen 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/LockedDownRestrictedSitesZoneAllowSmartScreenIE

#### <a name="windows10generalconfigurationinternetexplorerlockeddowntrustedzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerLockedDownTrustedZoneJavaPermissions 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/LockedDownTrustedSitesZoneJavaPermissions

#### <a name="windows10generalconfigurationinternetexplorerpreventmanagingsmartscreenfilter"></a>Windows10GeneralConfiguration.InternetExplorerPreventManagingSmartScreenFilter 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/PreventManagingSmartScreenFilter

#### <a name="windows10generalconfigurationinternetexplorerpreventperuserinstallationofactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerPreventPerUserInstallationOfActiveXControls 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/PreventPerUserInstallationOfActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerprocessesconsistentmimehandling"></a>Windows10GeneralConfiguration.InternetExplorerProcessesConsistentMimeHandling 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/ConsistentMimeHandlingInternetExplorerProcesses

#### <a name="windows10generalconfigurationinternetexplorerprocessesmimesniffingsafetyfeature"></a>Windows10GeneralConfiguration.InternetExplorerProcessesMimeSniffingSafetyFeature 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/MimeSniffingSafetyFeatureInternetExplorerProcesses

#### <a name="windows10generalconfigurationinternetexplorerprocessesmkprotocolsecurityrestriction"></a>Windows10GeneralConfiguration.InternetExplorerProcessesMKProtocolSecurityRestriction 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/MKProtocolSecurityRestrictionInternetExplorerProcesses

#### <a name="windows10generalconfigurationinternetexplorerprocessesnotificationbar"></a>Windows10GeneralConfiguration.InternetExplorerProcessesNotificationBar 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/NotificationBarInternetExplorerProcesses

#### <a name="windows10generalconfigurationinternetexplorerprocessesprotectionfromzoneelevation"></a>Windows10GeneralConfiguration.InternetExplorerProcessesProtectionFromZoneElevation 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/ProtectionFromZoneElevationInternetExplorerProcesses

#### <a name="windows10generalconfigurationinternetexplorerprocessesrestrictactivexinstall"></a>Windows10GeneralConfiguration.InternetExplorerProcessesRestrictActiveXInstall 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictActiveXInstallInternetExplorerProcesses

#### <a name="windows10generalconfigurationinternetexplorerprocessesrestrictfiledownload"></a>Windows10GeneralConfiguration.InternetExplorerProcessesRestrictFileDownload 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictFileDownloadInternetExplorerProcesses

#### <a name="windows10generalconfigurationinternetexplorerprocessesscriptedwindowsecurityrestrictions"></a>Windows10GeneralConfiguration.InternetExplorerProcessesScriptedWindowSecurityRestrictions 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/ScriptedWindowSecurityRestrictionsInternetExplorerProcesses

#### <a name="windows10generalconfigurationinternetexplorerremoverunthistimebuttonforoutdatedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRemoveRunThisTimeButtonForOutdatedActiveXControls 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RemoveRunThisTimeButtonForOutdatedActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneaccesstodatasources"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneAccessToDataSources 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowAccessToDataSources

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneactivescripting"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneActiveScripting 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowActiveScripting

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneallowonlyapproveddomainstouseactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneAllowOnlyApprovedDomainsToUseActiveXControls 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowOnlyApprovedDomainsToUseActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneallowonlyapproveddomainstousetdcactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneAllowOnlyApprovedDomainsToUseTdcActiveXControls 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowOnlyApprovedDomainsToUseTDCActiveXControl

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneallowvbscripttorun"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneAllowVBScriptToRun 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowVBScriptToRunInInternetExplorer

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneautomaticpromptforfiledownloads"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneAutomaticPromptForFileDownloads 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowAutomaticPromptingForFileDownloads

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonebinaryandscriptbehaviors"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneBinaryAndScriptBehaviors 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowBinaryAndScriptBehaviors

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonecopyandpasteviascript"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneCopyAndPasteViaScript 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowCopyPasteViaScript

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonecrosssitescriptingfilter"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneCrossSiteScriptingFilter 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneEnableCrossSiteScriptingFilter

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedonotrunantimalwareagainstactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDoNotRunAntimalwareAgainstActiveXControls 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneDoNotRunAntimalwareAgainstActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedotnetframeworkreliantcomponents"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDotNetFrameworkReliantComponents 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowNETFrameworkReliantComponents

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedownloadsignedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDownloadSignedActiveXControls 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneDownloadSignedActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedownloadunsignedactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDownloadUnsignedActiveXControls 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneDownloadUnsignedActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedraganddroporcopyandpastefiles"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDragAndDropOrCopyAndPasteFiles 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowDragAndDropCopyAndPasteFiles

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedragcontentfromdifferentdomainsacrosswindows"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDragContentFromDifferentDomainsAcrossWindows 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneEnableDraggingOfContentFromDifferentDomainsAcrossWindows

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonedragcontentfromdifferentdomainswithinwindows"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneDragContentFromDifferentDomainsWithinWindows 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneEnableDraggingOfContentFromDifferentDomainsWithinWindows

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonefiledownloads"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneFileDownloads 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowFileDownloads

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneincludelocalpathwhenuploadingfilestoserver"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneIncludeLocalPathWhenUploadingFilesToServer 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneIncludeLocalPathWhenUploadingFilesToServer

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneinitializeandscriptactivexcontrolsnotmarkedassafe"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneInitializeAndScriptActiveXControlsNotMarkedAsSafe 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneInitializeAndScriptActiveXControls

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneJavaPermissions 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneJavaPermissions

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonelaunchapplicationsandfilesinaniframe"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneLaunchApplicationsAndFilesInAnIFrame 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneLaunchingApplicationsAndFilesInIFRAME

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonelessprivilegedsites"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneLessPrivilegedSites 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowLessPrivilegedSites

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneloadingofxamlfiles"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneLoadingOfXamlFiles 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowLoadingOfXAMLFiles

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonelogonoptions"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneLogonOptions 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneLogonOptions

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonemetarefresh"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneMetaRefresh 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowMETAREFRESH

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonenavigatewindowsandframesacrossdifferentdomains"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneNavigateWindowsAndFramesAcrossDifferentDomains 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneNavigateWindowsAndFrames

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonepopupblocker"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZonePopupBlocker 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneUsePopupBlocker

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneprotectedmode"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneProtectedMode 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneTurnOnProtectedMode

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonerunactivexcontrolsandplugins"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneRunActiveXControlsAndPlugins 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneRunActiveXControlsAndPlugins

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonerundotnetframeworkreliantcomponentssignedwithauthenticode"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneRunDotNetFrameworkReliantComponentsSignedWithAuthenticode 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneRunNETFrameworkReliantComponentsSignedWithAuthenticode

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonescriptactivexcontrolsmarkedsafeforscripting"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneScriptActiveXControlsMarkedSafeForScripting 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneScriptActiveXControlsMarkedSafeForScripting

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonescriptingofjavaapplets"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneScriptingOfJavaApplets 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneScriptingOfJavaApplets

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonescriptingofwebbrowsercontrols"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneScriptingOfWebBrowserControls 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowScriptingOfInternetExplorerWebBrowserControls

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonescriptinitiatedwindows"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneScriptInitiatedWindows 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowScriptInitiatedWindows

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonescriptlets"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneScriptlets 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowScriptlets

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonesecuritywarningforpotentiallyunsafefiles"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneSecurityWarningForPotentiallyUnsafeFiles 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneShowSecurityWarningForPotentiallyUnsafeFiles

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzonesmartscreen"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneSmartScreen 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowSmartScreenIE

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneupdatestostatusbarviascript"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneUpdatesToStatusBarViaScript 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowUpdatesToStatusBarViaScript

#### <a name="windows10generalconfigurationinternetexplorerrestrictedzoneuserdatapersistence"></a>Windows10GeneralConfiguration.InternetExplorerRestrictedZoneUserDataPersistence 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/RestrictedSitesZoneAllowUserDataPersistence

#### <a name="windows10generalconfigurationinternetexplorersecuritysettingscheck"></a>Windows10GeneralConfiguration.InternetExplorerSecuritySettingsCheck 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/DisableSecuritySettingsCheck

#### <a name="windows10generalconfigurationinternetexplorersecurityzonesuseonlymachinesettings"></a>Windows10GeneralConfiguration.InternetExplorerSecurityZonesUseOnlyMachineSettings 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/SecurityZonesUseOnlyMachineSettings

#### <a name="windows10generalconfigurationinternetexplorersoftwarewhensignatureisinvalid"></a>Windows10GeneralConfiguration.InternetExplorerSoftwareWhenSignatureIsInvalid 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/AllowSoftwareWhenSignatureIsInvalid

#### <a name="windows10generalconfigurationinternetexplorertrustedzonedonotrunantimalwareagainstactivexcontrols"></a>Windows10GeneralConfiguration.InternetExplorerTrustedZoneDoNotRunAntimalwareAgainstActiveXControls 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/TrustedSitesZoneDoNotRunAntimalwareAgainstActiveXControls

#### <a name="windows10generalconfigurationinternetexplorertrustedzoneinitializeandscriptactivexcontrolsnotmarkedassafe"></a>Windows10GeneralConfiguration.InternetExplorerTrustedZoneInitializeAndScriptActiveXControlsNotMarkedAsSafe 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/TrustedSitesZoneInitializeAndScriptActiveXControls

#### <a name="windows10generalconfigurationinternetexplorertrustedzonejavapermissions"></a>Windows10GeneralConfiguration.InternetExplorerTrustedZoneJavaPermissions 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/TrustedSitesZoneJavaPermissions

#### <a name="windows10generalconfigurationinternetexploreruseactivexinstallerservice"></a>Windows10GeneralConfiguration.InternetExplorerUseActiveXInstallerService 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/SpecifyUseOfActiveXInstallerService

#### <a name="windows10generalconfigurationinternetexplorerusersaddingsites"></a>Windows10GeneralConfiguration.InternetExplorerUsersAddingSites 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/DoNotAllowUsersToAddSites

#### <a name="windows10generalconfigurationinternetexploreruserschangingpolicies"></a>Windows10GeneralConfiguration.InternetExplorerUsersChangingPolicies 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/InternetExplorer/DoNotAllowUsersToChangePolicies

#### <a name="windows10generalconfigurationinternetsharingblocked"></a>Windows10GeneralConfiguration.InternetSharingBlocked 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WiFi/AllowInternetSharing

#### <a name="windows10generalconfigurationlocationservicesblocked"></a>Windows10GeneralConfiguration.LocationServicesBlocked 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/System/AllowLocation

#### <a name="windows10generalconfigurationlockscreenallowtimeoutconfiguration"></a>Windows10GeneralConfiguration.LockScreenAllowTimeoutConfiguration 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/DeviceLock/AllowScreenTimeoutWhileLockedUser/Config

#### <a name="windows10generalconfigurationlockscreenblockactioncenternotifications"></a>Windows10GeneralConfiguration.LockScreenBlockActionCenterNotifications 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/AboveLock/AllowActionCenterNotifications

#### <a name="windows10generalconfigurationlockscreenblockcortana"></a>Windows10GeneralConfiguration.LockScreenBlockCortana 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/AboveLock/AllowCortanaAboveLock

#### <a name="windows10generalconfigurationlockscreenblocktoastnotifications"></a>Windows10GeneralConfiguration.LockScreenBlockToastNotifications 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/AboveLock/AllowToasts

#### <a name="windows10generalconfigurationlockscreencamera"></a>Windows10GeneralConfiguration.LockScreenCamera 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/DeviceLock/PreventEnablingLockScreenCamera

#### <a name="windows10generalconfigurationlockscreenhidenetworkselectionui"></a>Windows10GeneralConfiguration.LockScreenHideNetworkSelectionUI 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WindowsLogon/DontDisplayNetworkSelectionUI

#### <a name="windows10generalconfigurationlockscreenslideshow"></a>Windows10GeneralConfiguration.LockScreenSlideShow 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/DeviceLock/PreventLockScreenSlideShow

#### <a name="windows10generalconfigurationlockscreentimeoutinseconds"></a>Windows10GeneralConfiguration.LockScreenTimeoutInSeconds 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/DeviceLock/ScreenTimeoutWhileLocked

#### <a name="windows10generalconfigurationlogonblockfastuserswitching"></a>Windows10GeneralConfiguration.LogonBlockFastUserSwitching 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WindowsLogon/HideFastUserSwitching

#### <a name="windows10generalconfigurationmessagingblockmms"></a>Windows10GeneralConfiguration.MessagingBlockMMS 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Messaging/AllowMMS

#### <a name="windows10generalconfigurationmessagingblockrichcommunicationservices"></a>Windows10GeneralConfiguration.MessagingBlockRichCommunicationServices 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Messaging/AllowRCS

#### <a name="windows10generalconfigurationmessagingblocksync"></a>Windows10GeneralConfiguration.MessagingBlockSync 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Messaging/AllowMessageSync

#### <a name="windows10generalconfigurationmicrosoftaccountblocked"></a>Windows10GeneralConfiguration.MicrosoftAccountBlocked 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Accounts/AllowMicrosoftAccountConnection

#### <a name="windows10generalconfigurationmicrosoftaccountblocksettingssync"></a>Windows10GeneralConfiguration.MicrosoftAccountBlockSettingsSync 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Experience/AllowSyncMySettings

#### <a name="windows10generalconfigurationmicrosoftaccountsigninassistantsettings"></a>Windows10GeneralConfiguration.MicrosoftAccountSignInAssistantSettings 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Accounts  
**Décalage d’URI**: /AllowMicrosoftAccountSignInAssistant

#### <a name="windows10generalconfigurationnetworkproxyapplysettingsdevicewide"></a>Windows10GeneralConfiguration.NetworkProxyApplySettingsDeviceWide 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/NetworkProxy  
**Décalage d’URI**: /ProxySettingsPerUser

#### <a name="windows10generalconfigurationnetworkproxyautomaticconfigurationurl"></a>Windows10GeneralConfiguration.NetworkProxyAutomaticConfigurationUrl 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/NetworkProxy  
**Décalage d’URI**: /SetupScriptUrl

#### <a name="windows10generalconfigurationnetworkproxydisableautodetect"></a>Windows10GeneralConfiguration.NetworkProxyDisableAutoDetect 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/NetworkProxy  
**Décalage d’URI**: /AutoDetect

#### <a name="windows10generalconfigurationnetworkproxyserver"></a>Windows10GeneralConfiguration.NetworkProxyServer 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/NetworkProxy  
**Décalage d’URI**: /ProxyAddress, /Exceptions et /UseProxyForLocalAddresses

#### <a name="windows10generalconfigurationnfcblocked"></a>Windows10GeneralConfiguration.NfcBlocked 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Connectivity/AllowNFC

#### <a name="windows10generalconfigurationonedrivedisablefilesync"></a>Windows10GeneralConfiguration.OneDriveDisableFileSync 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/System/DisableOneDriveFileSync

#### <a name="windows10generalconfigurationpasswordblocksimple"></a>Windows10GeneralConfiguration.PasswordBlockSimple 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/DeviceLock/AllowSimpleDevicePassword

#### <a name="windows10generalconfigurationpasswordexpirationdays"></a>Windows10GeneralConfiguration.PasswordExpirationDays 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/DeviceLock/DevicePasswordExpiration

#### <a name="windows10generalconfigurationpasswordminimumageindays"></a>Windows10GeneralConfiguration.PasswordMinimumAgeInDays 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/DeviceLock/MinimumPasswordAge

#### <a name="windows10generalconfigurationpasswordminimumcharactersetcount"></a>Windows10GeneralConfiguration.PasswordMinimumCharacterSetCount 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/DeviceLock/MinDevicePasswordComplexCharacters

#### <a name="windows10generalconfigurationpasswordminimumlength"></a>Windows10GeneralConfiguration.PasswordMinimumLength 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/DeviceLock/MinDevicePasswordLength

#### <a name="windows10generalconfigurationpasswordminutesofinactivitybeforescreentimeout"></a>Windows10GeneralConfiguration.PasswordMinutesOfInactivityBeforeScreenTimeout 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/DeviceLock/MaxInactivityTimeDeviceLock

#### <a name="windows10generalconfigurationpasswordpreviouspasswordblockcount"></a>Windows10GeneralConfiguration.PasswordPreviousPasswordBlockCount 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/DeviceLock/DevicePasswordHistory

#### <a name="windows10generalconfigurationpasswordrequired"></a>Windows10GeneralConfiguration.PasswordRequired 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/DeviceLock/DevicePasswordEnabled

#### <a name="windows10generalconfigurationpasswordrequiredtype"></a>Windows10GeneralConfiguration.PasswordRequiredType 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/DeviceLock/AlphanumericDevicePasswordRequired

#### <a name="windows10generalconfigurationpasswordrequirewhenresumefromidlestate"></a>Windows10GeneralConfiguration.PasswordRequireWhenResumeFromIdleState 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/DeviceLock/AllowIdleReturnWithoutPassword

#### <a name="windows10generalconfigurationpasswordsigninfailurecountbeforefactoryreset"></a>Windows10GeneralConfiguration.PasswordSignInFailureCountBeforeFactoryReset 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/DeviceLock/MaxDevicePasswordFailedAttempts

#### <a name="windows10generalconfigurationpersonalizationdesktopimageurl"></a>Windows10GeneralConfiguration.PersonalizationDesktopImageUrl 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Personalization  
**Décalage d’URI**: /DesktopImageUrl

#### <a name="windows10generalconfigurationpersonalizationlockscreenimageurl"></a>Windows10GeneralConfiguration.PersonalizationLockScreenImageUrl 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Personalization  
**Décalage d’URI**: /LockScreenImageUrl

#### <a name="windows10generalconfigurationpowerrequirepasswordonwakewhileonbattery"></a>Windows10GeneralConfiguration.PowerRequirePasswordOnWakeWhileOnBattery 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Power/RequirePasswordWhenComputerWakesOnBattery

#### <a name="windows10generalconfigurationpowerrequirepasswordonwakewhilepluggedin"></a>Windows10GeneralConfiguration.PowerRequirePasswordOnWakeWhilePluggedIn 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Power/RequirePasswordWhenComputerWakesPluggedIn

#### <a name="windows10generalconfigurationpowerstandbystateswhensleepingwhileonbattery"></a>Windows10GeneralConfiguration.PowerStandbyStatesWhenSleepingWhileOnBattery 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Power/AllowStandbyStatesWhenSleepingOnBattery

#### <a name="windows10generalconfigurationpowerstandbystateswhensleepingwhilepluggedin"></a>Windows10GeneralConfiguration.PowerStandbyStatesWhenSleepingWhilePluggedIn 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Power/AllowStandbyWhenSleepingPluggedIn

#### <a name="windows10generalconfigurationpreventinstallationofmatchingdeviceids"></a>windows10generalconfiguration.preventInstallationOfMatchingDeviceIDs 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/DeviceInstallation/PreventInstallationOfMatchingDeviceIDs

#### <a name="windows10generalconfigurationpreventinstallationofmatchingdevicesetupclasses"></a>windows10generalconfiguration.preventInstallationOfMatchingDeviceSetupClasses 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/DeviceInstallation/PreventInstallationOfMatchingDeviceSetupClasses

#### <a name="windows10generalconfigurationprinterblockaddition"></a>Windows10GeneralConfiguration.PrinterBlockAddition 
**Fournisseur de services cryptographiques**: ./User/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Education/PreventAddingNewPrinters

#### <a name="windows10generalconfigurationprinterdefaultname"></a>Windows10GeneralConfiguration.PrinterDefaultName 
**Fournisseur de services cryptographiques**: ./User/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Education/DefaultPrinterName

#### <a name="windows10generalconfigurationprinternames"></a>Windows10GeneralConfiguration.PrinterNames 
**Fournisseur de services cryptographiques**: ./User/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Education/PrinterNames

#### <a name="windows10generalconfigurationprivacyadvertisingid"></a>Windows10GeneralConfiguration.PrivacyAdvertisingId 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Privacy/DisableAdvertisingID

#### <a name="windows10generalconfigurationprivacyautoacceptpairingandconsentprompts"></a>Windows10GeneralConfiguration.PrivacyAutoAcceptPairingAndConsentPrompts 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Privacy/AllowAutoAcceptPairingAndPrivacyConsentPrompts

#### <a name="windows10generalconfigurationprivacyblockactivityfeed"></a>Windows10GeneralConfiguration.PrivacyBlockActivityFeed 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Privacy/EnableActivityFeed

#### <a name="windows10generalconfigurationprivacyblockinputpersonalization"></a>Windows10GeneralConfiguration.PrivacyBlockInputPersonalization 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Privacy/AllowInputPersonalization

#### <a name="windows10generalconfigurationprivacyblockpublishuseractivities"></a>Windows10GeneralConfiguration.PrivacyBlockPublishUserActivities 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Privacy/PublishUserActivities

#### <a name="windows10generalconfigurationsafesearchfilter"></a>Windows10GeneralConfiguration.SafeSearchFilter 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Search/SafeSearchPermissions

#### <a name="windows10generalconfigurationscreencaptureblocked"></a>Windows10GeneralConfiguration.ScreenCaptureBlocked 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Experience/AllowScreenCapture

#### <a name="windows10generalconfigurationsearchblockdiacritics"></a>Windows10GeneralConfiguration.SearchBlockDiacritics 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Search/AllowUsingDiacritics

#### <a name="windows10generalconfigurationsearchblockwebresults"></a>Windows10GeneralConfiguration.SearchBlockWebResults 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Search/DoNotUseWebResults

#### <a name="windows10generalconfigurationsearchdisableautolanguagedetection"></a>Windows10GeneralConfiguration.SearchDisableAutoLanguageDetection 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Search/AlwaysUseAutoLangDetection

#### <a name="windows10generalconfigurationsearchdisableindexerbackoff"></a>Windows10GeneralConfiguration.SearchDisableIndexerBackoff 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Search/DisableBackoff

#### <a name="windows10generalconfigurationsearchdisableindexingencrypteditems"></a>Windows10GeneralConfiguration.SearchDisableIndexingEncryptedItems 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Search/AllowIndexingEncryptedStoresOrItems

#### <a name="windows10generalconfigurationsearchdisableindexingremovabledrive"></a>Windows10GeneralConfiguration.SearchDisableIndexingRemovableDrive 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Search/DisableRemovableDriveIndexing

#### <a name="windows10generalconfigurationsearchdisablelocation"></a>Windows10GeneralConfiguration.SearchDisableLocation 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Search/AllowSearchToUseLocation

#### <a name="windows10generalconfigurationsearchdisableuselocation"></a>Windows10GeneralConfiguration.SearchDisableUseLocation 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Search/AllowSearchToUseLocation

#### <a name="windows10generalconfigurationsearchenableautomaticindexsizemanangement"></a>Windows10GeneralConfiguration.SearchEnableAutomaticIndexSizeManangement 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Search/PreventIndexingLowDiskSpaceMB

#### <a name="windows10generalconfigurationsearchenableremotequeries"></a>Windows10GeneralConfiguration.SearchEnableRemoteQueries 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Search/PreventRemoteQueries

#### <a name="windows10generalconfigurationsecurityblockazureadjoineddevicesautoencryption"></a>Windows10GeneralConfiguration.SecurityBlockAzureADJoinedDevicesAutoEncryption 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Security/PreventAutomaticDeviceEncryptionForAzureADJoinedDevices

#### <a name="windows10generalconfigurationsettingsblockaccountspage"></a>Windows10GeneralConfiguration.SettingsBlockAccountsPage 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Settings/PageVisibilityList

#### <a name="windows10generalconfigurationsettingsblockaddprovisioningpackage"></a>Windows10GeneralConfiguration.SettingsBlockAddProvisioningPackage 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Security/AllowAddProvisioningPackage

#### <a name="windows10generalconfigurationsettingsblockappspage"></a>Windows10GeneralConfiguration.SettingsBlockAppsPage 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Settings/PageVisibilityList

#### <a name="windows10generalconfigurationsettingsblockchangelanguage"></a>Windows10GeneralConfiguration.SettingsBlockChangeLanguage 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Settings/AllowLanguage

#### <a name="windows10generalconfigurationsettingsblockchangepowersleep"></a>Windows10GeneralConfiguration.SettingsBlockChangePowerSleep 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Settings/AllowPowerSleep

#### <a name="windows10generalconfigurationsettingsblockchangeregion"></a>Windows10GeneralConfiguration.SettingsBlockChangeRegion 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Settings/AllowRegion

#### <a name="windows10generalconfigurationsettingsblockchangesystemtime"></a>Windows10GeneralConfiguration.SettingsBlockChangeSystemTime 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Settings/AllowDateTime

#### <a name="windows10generalconfigurationsettingsblockdevicespage"></a>Windows10GeneralConfiguration.SettingsBlockDevicesPage 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Settings/PageVisibilityList

#### <a name="windows10generalconfigurationsettingsblockeaseofaccesspage"></a>Windows10GeneralConfiguration.SettingsBlockEaseOfAccessPage 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Settings/PageVisibilityList

#### <a name="windows10generalconfigurationsettingsblockeditdevicename"></a>Windows10GeneralConfiguration.SettingsBlockEditDeviceName 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Settings/AllowEditDeviceName

#### <a name="windows10generalconfigurationsettingsblockgamingpage"></a>Windows10GeneralConfiguration.SettingsBlockGamingPage 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Settings/PageVisibilityList

#### <a name="windows10generalconfigurationsettingsblocknetworkinternetpage"></a>Windows10GeneralConfiguration.SettingsBlockNetworkInternetPage 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Settings/PageVisibilityList

#### <a name="windows10generalconfigurationsettingsblockpersonalizationpage"></a>Windows10GeneralConfiguration.SettingsBlockPersonalizationPage 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Settings/PageVisibilityList

#### <a name="windows10generalconfigurationsettingsblockprivacypage"></a>Windows10GeneralConfiguration.SettingsBlockPrivacyPage 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Settings/PageVisibilityList

#### <a name="windows10generalconfigurationsettingsblockremoveprovisioningpackage"></a>Windows10GeneralConfiguration.SettingsBlockRemoveProvisioningPackage 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Security/AllowRemoveProvisioningPackage

#### <a name="windows10generalconfigurationsettingsblocksystempage"></a>Windows10GeneralConfiguration.SettingsBlockSystemPage 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Settings/PageVisibilityList

#### <a name="windows10generalconfigurationsettingsblocktimelanguagepage"></a>Windows10GeneralConfiguration.SettingsBlockTimeLanguagePage 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Settings/PageVisibilityList

#### <a name="windows10generalconfigurationsettingsblockupdatesecuritypage"></a>Windows10GeneralConfiguration.SettingsBlockUpdateSecurityPage 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Settings/PageVisibilityList

#### <a name="windows10generalconfigurationshareduserappdataallowed"></a>Windows10GeneralConfiguration.SharedUserAppDataAllowed 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/ApplicationManagement/AllowSharedUserAppData

#### <a name="windows10generalconfigurationsmartscreenblockpromptoverride"></a>Windows10GeneralConfiguration.SmartScreenBlockPromptOverride 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/PreventSmartScreenPromptOverride

#### <a name="windows10generalconfigurationsmartscreenblockpromptoverrideforfiles"></a>Windows10GeneralConfiguration.SmartScreenBlockPromptOverrideForFiles 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/PreventSmartScreenPromptOverrideForFiles

#### <a name="windows10generalconfigurationsmartscreenenableappinstallcontrol"></a>Windows10GeneralConfiguration.SmartScreenEnableAppInstallControl 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/SmartScreen/EnableAppInstallControl

#### <a name="windows10generalconfigurationstartblockunpinningappsfromtaskbar"></a>Windows10GeneralConfiguration.StartBlockUnpinningAppsFromTaskbar 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/NoPinningToTaskbar

#### <a name="windows10generalconfigurationstartmenuapplistvisibility"></a>Windows10GeneralConfiguration.StartMenuAppListVisibility 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/HideAppList

#### <a name="windows10generalconfigurationstartmenuhidechangeaccountsettings"></a>Windows10GeneralConfiguration.StartMenuHideChangeAccountSettings 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/HideChangeAccountSettings

#### <a name="windows10generalconfigurationstartmenuhidefrequentlyusedapps"></a>Windows10GeneralConfiguration.StartMenuHideFrequentlyUsedApps 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/HideFrequentlyUsedApps

#### <a name="windows10generalconfigurationstartmenuhidehibernate"></a>Windows10GeneralConfiguration.StartMenuHideHibernate 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/HideHibernate

#### <a name="windows10generalconfigurationstartmenuhidelock"></a>Windows10GeneralConfiguration.StartMenuHideLock 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/HideLock

#### <a name="windows10generalconfigurationstartmenuhidepowerbutton"></a>Windows10GeneralConfiguration.StartMenuHidePowerButton 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/HidePowerButton

#### <a name="windows10generalconfigurationstartmenuhiderecentjumplists"></a>Windows10GeneralConfiguration.StartMenuHideRecentJumpLists 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/HideRecentJumplists

#### <a name="windows10generalconfigurationstartmenuhiderecentlyaddedapps"></a>Windows10GeneralConfiguration.StartMenuHideRecentlyAddedApps 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/HideRecentlyAddedApps

#### <a name="windows10generalconfigurationstartmenuhiderestartoptions"></a>Windows10GeneralConfiguration.StartMenuHideRestartOptions 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/HideRestart

#### <a name="windows10generalconfigurationstartmenuhideshutdown"></a>Windows10GeneralConfiguration.StartMenuHideShutDown 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/HideShutDown

#### <a name="windows10generalconfigurationstartmenuhidesignout"></a>Windows10GeneralConfiguration.StartMenuHideSignOut 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/HideSignOut

#### <a name="windows10generalconfigurationstartmenuhidesleep"></a>Windows10GeneralConfiguration.StartMenuHideSleep 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/HideSleep

#### <a name="windows10generalconfigurationstartmenuhideswitchaccount"></a>Windows10GeneralConfiguration.StartMenuHideSwitchAccount 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/HideSwitchAccount

#### <a name="windows10generalconfigurationstartmenuhideusertile"></a>Windows10GeneralConfiguration.StartMenuHideUserTile 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/HideUserTile

#### <a name="windows10generalconfigurationstartmenulayoutedgeassetsxml"></a>Windows10GeneralConfiguration.StartMenuLayoutEdgeAssetsXml 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/ImportEdgeAssets

#### <a name="windows10generalconfigurationstartmenulayoutxml"></a>Windows10GeneralConfiguration.StartMenuLayoutXml 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/StartLayout

#### <a name="windows10generalconfigurationstartmenumode"></a>Windows10GeneralConfiguration.StartMenuMode 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/ForceStartSize

#### <a name="windows10generalconfigurationstartmenupinnedfolderdocuments"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderDocuments 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/AllowPinnedFolderDocuments

#### <a name="windows10generalconfigurationstartmenupinnedfolderdownloads"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderDownloads 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/AllowPinnedFolderDownloads

#### <a name="windows10generalconfigurationstartmenupinnedfolderfileexplorer"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderFileExplorer 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/AllowPinnedFolderFileExplorer

#### <a name="windows10generalconfigurationstartmenupinnedfolderhomegroup"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderHomeGroup 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/AllowPinnedFolderHomeGroup

#### <a name="windows10generalconfigurationstartmenupinnedfoldermusic"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderMusic 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/AllowPinnedFolderMusic

#### <a name="windows10generalconfigurationstartmenupinnedfoldernetwork"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderNetwork 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/AllowPinnedFolderNetwork

#### <a name="windows10generalconfigurationstartmenupinnedfolderpersonalfolder"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderPersonalFolder 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/AllowPinnedFolderPersonalFolder

#### <a name="windows10generalconfigurationstartmenupinnedfolderpictures"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderPictures 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/AllowPinnedFolderPictures

#### <a name="windows10generalconfigurationstartmenupinnedfoldersettings"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderSettings 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/AllowPinnedFolderSettings

#### <a name="windows10generalconfigurationstartmenupinnedfoldervideos"></a>Windows10GeneralConfiguration.StartMenuPinnedFolderVideos 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Start/AllowPinnedFolderVideos

#### <a name="windows10generalconfigurationstorageblockremovablestorage"></a>Windows10GeneralConfiguration.StorageBlockRemovableStorage 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/System/AllowStorageCard

#### <a name="windows10generalconfigurationstoragerequiremobiledeviceencryption"></a>Windows10GeneralConfiguration.StorageRequireMobileDeviceEncryption 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Security/RequireDeviceEncryption

#### <a name="windows10generalconfigurationstoragerestrictappdatatosystemvolume"></a>Windows10GeneralConfiguration.StorageRestrictAppDataToSystemVolume 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/ApplicationManagement/RestrictAppDataToSystemVolume

#### <a name="windows10generalconfigurationstoragerestrictappinstalltosystemvolume"></a>Windows10GeneralConfiguration.StorageRestrictAppInstallToSystemVolume 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/ApplicationManagement/RestrictAppToSystemVolume

#### <a name="windows10generalconfigurationsystembootstartdriverinitialization"></a>Windows10GeneralConfiguration.SystemBootStartDriverInitialization 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/System/BootStartDriverInitialization

#### <a name="windows10generalconfigurationsystemtelemetryproxyserver"></a>Windows10GeneralConfiguration.SystemTelemetryProxyServer 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/System/TelemetryProxy

#### <a name="windows10generalconfigurationtaskmanagerblockendtask"></a>Windows10GeneralConfiguration.TaskManagerBlockEndTask 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/TaskManager/AllowEndTask

#### <a name="windows10generalconfigurationtenantlockdownrequirenetworkduringoutofboxexperience"></a>Windows10GeneralConfiguration.TenantLockdownRequireNetworkDuringOutOfBoxExperience 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/TenantLockdown  
**Décalage d’URI**: /RequireNetworkInOOBE

#### <a name="windows10generalconfigurationusbblocked"></a>Windows10GeneralConfiguration.UsbBlocked 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Connectivity/AllowUSBConnection

#### <a name="windows10generalconfigurationvoicerecordingblocked"></a>Windows10GeneralConfiguration.VoiceRecordingBlocked 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Experience/AllowVoiceRecording

#### <a name="windows10generalconfigurationwebrtcblocklocalhostipaddress"></a>Windows10GeneralConfiguration.WebRtcBlockLocalhostIpAddress 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/PreventUsingLocalHostIPAddressForWebRTC

#### <a name="windows10generalconfigurationwifiblockautomaticconnecthotspots"></a>Windows10GeneralConfiguration.WiFiBlockAutomaticConnectHotspots 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WiFi/AllowAutoConnectToWiFiSenseHotspots

#### <a name="windows10generalconfigurationwifiblocked"></a>Windows10GeneralConfiguration.WiFiBlocked 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Wifi/AllowWiFi

#### <a name="windows10generalconfigurationwifiblockmanualconfiguration"></a>Windows10GeneralConfiguration.WiFiBlockManualConfiguration 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WiFi/AllowManualWiFi/Configuration

#### <a name="windows10generalconfigurationwifiscaninterval"></a>Windows10GeneralConfiguration.WiFiScanInterval 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WiFi/WLANScanMode

#### <a name="windows10generalconfigurationwindowslogonlocalusersondomainjoinedcomputers"></a>Windows10GeneralConfiguration.WindowsLogOnLocalUsersOnDomainJoinedComputers 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WindowsLogon/EnumerateLocalUsersOnDomainJoinedComputers

#### <a name="windows10generalconfigurationwindowsspotlightblockconsumerspecificfeatures"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockConsumerSpecificFeatures 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Experience/AllowWindowsConsumerFeatures

#### <a name="windows10generalconfigurationwindowsspotlightblocked"></a>Windows10GeneralConfiguration.WindowsSpotlightBlocked 
**Fournisseur de services cryptographiques**: ./User/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Experience/AllowWindowsSpotlight

#### <a name="windows10generalconfigurationwindowsspotlightblockonactioncenter"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockOnActionCenter 
**Fournisseur de services cryptographiques**: ./User/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Experience/AllowWindowsSpotlightOnActionCenter

#### <a name="windows10generalconfigurationwindowsspotlightblocktailoredexperiences"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockTailoredExperiences 
**Fournisseur de services cryptographiques**: ./User/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Experience/AllowTailoredExperiencesWithDiagnosticData

#### <a name="windows10generalconfigurationwindowsspotlightblockthirdpartynotifications"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockThirdPartyNotifications 
**Fournisseur de services cryptographiques**: ./User/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Experience/AllowThirdPartySuggestionsInWindowsSpotlight

#### <a name="windows10generalconfigurationwindowsspotlightblockwelcomeexperience"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockWelcomeExperience 
**Fournisseur de services cryptographiques**: ./User/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Experience/AllowWindowsSpotlightWindowsWelcomeExperience

#### <a name="windows10generalconfigurationwindowsspotlightblockwindowstips"></a>Windows10GeneralConfiguration.WindowsSpotlightBlockWindowsTips 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Experience/AllowWindowsTips

#### <a name="windows10generalconfigurationwindowsspotlightconfigureonlockscreen"></a>Windows10GeneralConfiguration.WindowsSpotlightConfigureOnLockScreen 
**Fournisseur de services cryptographiques**: ./User/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Experience/ConfigureWindowsSpotlightOnLockScreen

#### <a name="windows10generalconfigurationwindowsstoreblockautoupdate"></a>Windows10GeneralConfiguration.WindowsStoreBlockAutoUpdate 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/ApplicationManagement/AllowAppStoreAutoUpdate

#### <a name="windows10generalconfigurationwindowsstoreblocked"></a>Windows10GeneralConfiguration.WindowsStoreBlocked 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/ApplicationManagement/AllowStore

#### <a name="windows10generalconfigurationwindowsstoreenableprivatestoreonly"></a>Windows10GeneralConfiguration.WindowsStoreEnablePrivateStoreOnly 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/ApplicationManagement/RequirePrivateStoreOnly

#### <a name="windows10generalconfigurationwirelessdisplayblockprojectiontothisdevice"></a>Windows10GeneralConfiguration.WirelessDisplayBlockProjectionToThisDevice 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WirelessDisplay/AllowProjectionToPC

#### <a name="windows10generalconfigurationwirelessdisplayblockuserinputfromreceiver"></a>Windows10GeneralConfiguration.WirelessDisplayBlockUserInputFromReceiver 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WirelessDisplay/AllowUserInputFromWirelessDisplayReceiver

#### <a name="windows10generalconfigurationwirelessdisplayrequirepinforpairing"></a>Windows10GeneralConfiguration.WirelessDisplayRequirePinForPairing 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/WirelessDisplay/RequirePINForPairing

#### <a name="windows10networkboundaryconfigurationwindowsnetworkisolationpolicy"></a>Windows10NetworkBoundaryConfiguration.WindowsNetworkIsolationPolicy 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/NetworkIsolation/EnterpriseCloudResources, /Config/NetworkIsolation/EnterpriseIPRange, /Config/NetworkIsolation/EnterpriseIPRangesAreAuthoritative, / config/NetworkIsolation / EnterpriseInternalProxyServers, /Config/NetworkIsolation/EnterpriseNetworkDomainNames, /Config/NetworkIsolation/EnterpriseProxyServers, /Config/NetworkIsolation/EnterpriseProxyServersAreAuthoritative, / config/NetworkIsolation / NeutralResources

#### <a name="windows10policyoverrideconfigurationprefermdmovergrouppolicy"></a>Windows10PolicyOverrideConfiguration.PreferMdmOverGroupPolicy 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/ControlPolicyConflict/MDMWinsOverGP

#### <a name="windows10secureassessmentconfigurationallowprinting"></a>Windows10SecureAssessmentConfiguration.AllowPrinting 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SecureAssessment  
**Décalage d’URI**: /RequirePrinting

#### <a name="windows10secureassessmentconfigurationallowscreencapture"></a>Windows10SecureAssessmentConfiguration.AllowScreenCapture 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SecureAssessment  
**Décalage d’URI**: /AllowScreenMonitoring

#### <a name="windows10secureassessmentconfigurationallowtextsuggestion"></a>Windows10SecureAssessmentConfiguration.AllowTextSuggestion 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SecureAssessment  
**Décalage d’URI**: /AllowTextSuggestions

#### <a name="windows10secureassessmentconfigurationconfigurationaccount"></a>Windows10SecureAssessmentConfiguration.ConfigurationAccount 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SecureAssessment  
**Décalage d’URI**: /TesterAccount

#### <a name="windows10secureassessmentconfigurationconfigurationaccounttype"></a>Windows10SecureAssessmentConfiguration.ConfigurationAccountType 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SecureAssessment  
**Décalage d’URI**: /TesterAccount

#### <a name="windows10secureassessmentconfigurationlaunchuri"></a>Windows10SecureAssessmentConfiguration.LaunchUri 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SecureAssessment  
**Décalage d’URI**: /LaunchURI

#### <a name="windows10teamgeneralconfigurationazureoperationalinsightsblocktelemetry"></a>Windows10TeamGeneralConfiguration.AzureOperationalInsightsBlockTelemetry 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SurfaceHub  
**Décalage d’URI**: / MOMAgent/WorkspaceID et WorkspaceKey/MOMAgent /

#### <a name="windows10teamgeneralconfigurationazureoperationalinsightsworkspaceid"></a>Windows10TeamGeneralConfiguration.AzureOperationalInsightsWorkspaceId 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SurfaceHub  
**Décalage d’URI**: / MOMAgent/WorkspaceID

#### <a name="windows10teamgeneralconfigurationazureoperationalinsightsworkspacekey"></a>Windows10TeamGeneralConfiguration.AzureOperationalInsightsWorkspaceKey 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SurfaceHub  
**Décalage d’URI**: / MOMAgent/WorkspaceKey

#### <a name="windows10teamgeneralconfigurationconnectappblockautolaunch"></a>Windows10TeamGeneralConfiguration.ConnectAppBlockAutoLaunch 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SurfaceHub  
**Décalage d’URI**: /InBoxApps/Connect/AutoLaunch

#### <a name="windows10teamgeneralconfigurationdeviceaccountblockexchangeservices"></a>Windows10TeamGeneralConfiguration.DeviceAccountBlockExchangeServices 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SurfaceHub  
**Décalage d’URI**: / DeviceAccount/messagerie

#### <a name="windows10teamgeneralconfigurationdeviceaccountemailaddress"></a>Windows10TeamGeneralConfiguration.DeviceAccountEmailAddress 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SurfaceHub  
**Décalage d’URI**: / DeviceAccount/messagerie

#### <a name="windows10teamgeneralconfigurationdeviceaccountexchangeserveraddress"></a>Windows10TeamGeneralConfiguration.DeviceAccountExchangeServerAddress 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SurfaceHub  
**Décalage d’URI**: / DeviceAccount/ExchangeServer

#### <a name="windows10teamgeneralconfigurationdeviceaccountrequirepasswordrotation"></a>Windows10TeamGeneralConfiguration.DeviceAccountRequirePasswordRotation 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SurfaceHub  
**Décalage d’URI**: / DeviceAccount/PasswordRotationEnabled

#### <a name="windows10teamgeneralconfigurationdeviceaccountsessioninitiationprotocoladdress"></a>Windows10TeamGeneralConfiguration.DeviceAccountSessionInitiationProtocolAddress 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SurfaceHub  
**Décalage d’URI**: / DeviceAccount/SipAddress

#### <a name="windows10teamgeneralconfigurationmaintenancewindowblocked"></a>Windows10TeamGeneralConfiguration.MaintenanceWindowBlocked 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SurfaceHub  
**Décalage d’URI**: /MaintenanceHoursSimple/Hours/Duration et /MaintenanceHoursSimple/Hours/StartTime

#### <a name="windows10teamgeneralconfigurationmaintenancewindowdurationinhours"></a>Windows10TeamGeneralConfiguration.MaintenanceWindowDurationInHours 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SurfaceHub  
**Décalage d’URI**: /MaintenanceHoursSimple/Hours/Duration

#### <a name="windows10teamgeneralconfigurationmaintenancewindowstarttime"></a>Windows10TeamGeneralConfiguration.MaintenanceWindowStartTime 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SurfaceHub  
**Décalage d’URI**: /MaintenanceHoursSimple/Hours/StartTime

#### <a name="windows10teamgeneralconfigurationmiracastblocked"></a>Windows10TeamGeneralConfiguration.MiracastBlocked 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SurfaceHub  
**Décalage d’URI**: /InBoxApps/WirelessProjection/Enabled

#### <a name="windows10teamgeneralconfigurationmiracastchannel"></a>Windows10TeamGeneralConfiguration.MiracastChannel 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SurfaceHub  
**Décalage d’URI**: InBoxApps/WirelessProjection/canal

#### <a name="windows10teamgeneralconfigurationmiracastrequirepin"></a>Windows10TeamGeneralConfiguration.MiracastRequirePin 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SurfaceHub  
**Décalage d’URI**: /InBoxApps/WirelessProjection/PINRequired

#### <a name="windows10teamgeneralconfigurationsettingsblockmymeetingsandfiles"></a>Windows10TeamGeneralConfiguration.SettingsBlockMyMeetingsAndFiles 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SurfaceHub  
**Décalage d’URI**: / propriétés/DoNotShowMyMeetingsAndFiles

#### <a name="windows10teamgeneralconfigurationsettingsblocksessionresume"></a>Windows10TeamGeneralConfiguration.SettingsBlockSessionResume 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SurfaceHub  
**Décalage d’URI**: / propriétés/AllowSessionResume

#### <a name="windows10teamgeneralconfigurationsettingsblocksigninsuggestions"></a>Windows10TeamGeneralConfiguration.SettingsBlockSigninSuggestions 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SurfaceHub  
**Décalage d’URI**: / propriétés/DisableSigninSuggestions

#### <a name="windows10teamgeneralconfigurationsettingsdefaultvolume"></a>Windows10TeamGeneralConfiguration.SettingsDefaultVolume 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SurfaceHub  
**Décalage d’URI**: / propriétés/DefaultVolume

#### <a name="windows10teamgeneralconfigurationsettingsscreentimeoutinminutes"></a>Windows10TeamGeneralConfiguration.SettingsScreenTimeoutInMinutes 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SurfaceHub  
**Décalage d’URI**: / propriétés/ScreenTimeout

#### <a name="windows10teamgeneralconfigurationsettingssessiontimeoutinminutes"></a>Windows10TeamGeneralConfiguration.SettingsSessionTimeoutInMinutes 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SurfaceHub  
**Décalage d’URI**: / propriétés/SessionTimeout

#### <a name="windows10teamgeneralconfigurationsettingssleeptimeoutinminutes"></a>Windows10TeamGeneralConfiguration.SettingsSleepTimeoutInMinutes 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SurfaceHub  
**Décalage d’URI**: / propriétés/SleepTimeout

#### <a name="windows10teamgeneralconfigurationwelcomescreenbackgroundimageurl"></a>Windows10TeamGeneralConfiguration.WelcomeScreenBackgroundImageUrl 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SurfaceHub  
**Décalage d’URI**: /InBoxApps/Welcome/CurrentBackgroundPath

#### <a name="windows10teamgeneralconfigurationwelcomescreenblockautomaticwakeup"></a>Windows10TeamGeneralConfiguration.WelcomeScreenBlockAutomaticWakeUp 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SurfaceHub  
**Décalage d’URI**: /InBoxApps/Welcome/AutoWakeScreen

#### <a name="windows10teamgeneralconfigurationwelcomescreenmeetinginformation"></a>Windows10TeamGeneralConfiguration.WelcomeScreenMeetingInformation 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/SurfaceHub  
**Décalage d’URI**: /InBoxApps/Welcome/MeetingInfoOption

#### <a name="windowsdefenderadvancedthreatprotectionconfigurationadvancedthreatprotectionoffboardingblob"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.AdvancedThreatProtectionOffboardingBlob 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**Décalage d’URI**: /Offboarding 

#### <a name="windowsdefenderadvancedthreatprotectionconfigurationadvancedthreatprotectionoffboardingfilename"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.AdvancedThreatProtectionOffboardingFilename
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**Décalage d’URI**: /Offboarding 

#### <a name="windowsdefenderadvancedthreatprotectionconfigurationadvancedthreatprotectiononboardingblob"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.AdvancedThreatProtectionOnboardingBlob 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**Décalage d’URI**: /Onboarding 

#### <a name="windowsdefenderadvancedthreatprotectionconfigurationadvancedthreatprotectiononboardingfilename"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.AdvancedThreatProtectionOnboardingFilename 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**Décalage d’URI**: /Onboarding 

#### <a name="windowsdefenderadvancedthreatprotectionconfigurationallowsamplesharing"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.AllowSampleSharing 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**Décalage d’URI**: / Configuration/SampleSharing

#### <a name="windowsdefenderadvancedthreatprotectionconfigurationenableexpeditedtelemetryreporting"></a>WindowsDefenderAdvancedThreatProtectionConfiguration.EnableExpeditedTelemetryReporting 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection  
**Décalage d’URI**: / Configuration/TelemetryReportingFrequency

#### <a name="windowsdeliveryoptimizationconfigurationdeliveryoptimizationmode"></a>WindowsDeliveryOptimizationConfiguration.DeliveryOptimizationMode 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/DeliveryOptimization/DODownloadMode

#### <a name="windowsidentityprotectionconfigurationenhancedantispoofingforfacialfeaturesenabled"></a>WindowsIdentityProtectionConfiguration.EnhancedAntiSpoofingForFacialFeaturesEnabled 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/PassportForWork  
**Décalage d’URI**: / biométrie/FacialFeaturesUseEnhancedAntiSpoofing

#### <a name="windowsidentityprotectionconfigurationpinexpirationindays"></a>WindowsIdentityProtectionConfiguration.PinExpirationInDays 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/PassportForWork  
**Décalage d’URI**: / {AADTenantId} / stratégies/PINComplexity / d’Expiration

#### <a name="windowsidentityprotectionconfigurationpinlowercasecharactersusage"></a>WindowsIdentityProtectionConfiguration.PinLowercaseCharactersUsage 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/PassportForWork  
**Décalage d’URI**: / {AADTenantId} / stratégies/PINComplexity/LowercaseLetters

#### <a name="windowsidentityprotectionconfigurationpinmaximumlength"></a>WindowsIdentityProtectionConfiguration.PinMaximumLength 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/PassportForWork  
**Décalage d’URI**: / {AADTenantId} / stratégies/PINComplexity/MaximumPINLength

#### <a name="windowsidentityprotectionconfigurationpinminimumlength"></a>WindowsIdentityProtectionConfiguration.PinMinimumLength 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/PassportForWork  
**Décalage d’URI**: / {AADTenantId} / stratégies/PINComplexity/MinimumPINLength

#### <a name="windowsidentityprotectionconfigurationpinpreviousblockcount"></a>WindowsIdentityProtectionConfiguration.PinPreviousBlockCount 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/PassportForWork  
**Décalage d’URI**: / {AADTenantId} / stratégies/PINComplexity/historique

#### <a name="windowsidentityprotectionconfigurationpinrecoveryenabled"></a>WindowsIdentityProtectionConfiguration.PinRecoveryEnabled 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/PassportForWork  
**Décalage d’URI**: / {AADTenantId} / Policies/EnablePinRecovery

#### <a name="windowsidentityprotectionconfigurationpinspecialcharactersusage"></a>WindowsIdentityProtectionConfiguration.PinSpecialCharactersUsage 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/PassportForWork  
**Décalage d’URI**: / {AADTenantId} / stratégies/PINComplexity/SpecialCharacters

#### <a name="windowsidentityprotectionconfigurationpinuppercasecharactersusage"></a>WindowsIdentityProtectionConfiguration.PinUppercaseCharactersUsage
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/PassportForWork  
**Décalage d’URI**: / {AADTenantId} / stratégies/PINComplexity/UppercaseLetters

#### <a name="windowsidentityprotectionconfigurationsecuritydevicerequired"></a>WindowsIdentityProtectionConfiguration.SecurityDeviceRequired 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/PassportForWork  
**Décalage d’URI**: / / Policies/RequireSecurityDevice {AADTenantId}

#### <a name="windowsidentityprotectionconfigurationunlockwithbiometricsenabled"></a>WindowsIdentityProtectionConfiguration.UnlockWithBiometricsEnabled 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/PassportForWork  
**Décalage d’URI**: / biométrie/UseBiometrics

#### <a name="windowsidentityprotectionconfigurationusecertificatesforonpremisesauthenabled"></a>WindowsIdentityProtectionConfiguration.UseCertificatesForOnPremisesAuthEnabled 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/PassportForWork  
**Décalage d’URI**: / / Policies/UseCertificateForOnPremAuth {AADTenantId}

#### <a name="windowsidentityprotectionconfigurationwindowshelloforbusinessblocked"></a>WindowsIdentityProtectionConfiguration.WindowsHelloForBusinessBlocked 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/PassportForWork  
**Décalage d’URI**: / / Policies/UsePassportForWork {AADTenantId}

#### <a name="windowskioskconfigurationedgekioskenablepublicbrowsing"></a>WindowsKioskConfiguration.EdgeKioskEnablePublicBrowsing 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/ConfigureKioskMode

#### <a name="windowskioskconfigurationedgekioskresetafteridletimeinminutes"></a>WindowsKioskConfiguration.EdgeKioskResetAfterIdleTimeInMinutes 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Browser/ConfigureKioskResetAfterIdleTimeout

#### <a name="windowskioskconfigurationkioskbrowserblockedurlexceptions"></a>WindowsKioskConfiguration.KioskBrowserBlockedUrlExceptions 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/KioskBrowser/BlockedUrlExceptions

#### <a name="windowskioskconfigurationkioskbrowserblockedurls"></a>WindowsKioskConfiguration.KioskBrowserBlockedURLs 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/KioskBrowser/BlockedUrls

#### <a name="windowskioskconfigurationkioskbrowserdefaulturl"></a>WindowsKioskConfiguration.KioskBrowserDefaultUrl 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/KioskBrowser/DefaultUrl

#### <a name="windowskioskconfigurationkioskbrowserenableendsessionbutton"></a>WindowsKioskConfiguration.KioskBrowserEnableEndSessionButton 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/KioskBrowser/EnableEndSessionButton

#### <a name="windowskioskconfigurationkioskbrowserenablehomebutton"></a>WindowsKioskConfiguration.KioskBrowserEnableHomeButton 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/KioskBrowser/EnableHomeButton

#### <a name="windowskioskconfigurationkioskbrowserenablenavigationbuttons"></a>WindowsKioskConfiguration.KioskBrowserEnableNavigationButtons 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/KioskBrowser/EnableNavigationButtons

#### <a name="windowskioskconfigurationkioskbrowserrestartonidletimeinminutes"></a>WindowsKioskConfiguration.KioskBrowserRestartOnIdleTimeInMinutes 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/KioskBrowser/KioskBrowserRestartOnIdleTimeInMinutes

#### <a name="windowsupdateforbusinessconfigurationautomaticupdatemode"></a>WindowsUpdateForBusinessConfiguration.AutomaticUpdateMode 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Update/AllowAutoUpdate

#### <a name="windowsupdateforbusinessconfigurationautorestartnotificationdismissal"></a>WindowsUpdateForBusinessConfiguration.AutoRestartNotificationDismissal 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Update/AutoRestartRequiredNotificationDismissal

#### <a name="windowsupdateforbusinessconfigurationbusinessreadyupdatesonly"></a>WindowsUpdateForBusinessConfiguration.BusinessReadyUpdatesOnly 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Update/BranchReadinessLevel

#### <a name="windowsupdateforbusinessconfigurationdeliveryoptimizationmode"></a>WindowsUpdateForBusinessConfiguration.DeliveryOptimizationMode 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/DeliveryOptimization/DODownloadMode

#### <a name="windowsupdateforbusinessconfigurationdriversexcluded"></a>WindowsUpdateForBusinessConfiguration.DriversExcluded 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Update/ExcludeWUDriversInQualityUpdate

#### <a name="windowsupdateforbusinessconfigurationengagedrestartdeadlineforfeatureupdatesindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartDeadlineForFeatureUpdatesInDays 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Update/EngagedRestartDeadlineForFeatureUpdates

#### <a name="windowsupdateforbusinessconfigurationengagedrestartdeadlineindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartDeadlineInDays 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Update/EngagedRestartDeadline

#### <a name="windowsupdateforbusinessconfigurationengagedrestartsnoozescheduleforfeatureupdatesindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartSnoozeScheduleForFeatureUpdatesInDays 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Update/EngagedRestartSnoozeScheduleForFeatureUpdates

#### <a name="windowsupdateforbusinessconfigurationengagedrestartsnoozescheduleindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartSnoozeScheduleInDays 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Update/EngagedRestartSnoozeSchedule

#### <a name="windowsupdateforbusinessconfigurationengagedrestarttransitionscheduleforfeatureupdatesindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartTransitionScheduleForFeatureUpdatesInDays 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Update/EngagedRestartTransitionScheduleForFeatureUpdates

#### <a name="windowsupdateforbusinessconfigurationengagedrestarttransitionscheduleindays"></a>WindowsUpdateForBusinessConfiguration.EngagedRestartTransitionScheduleInDays 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Update/EngagedRestartTransitionSchedule

#### <a name="windowsupdateforbusinessconfigurationfeatureupdatesdeferralperiodindays"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesDeferralPeriodInDays 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Update/DeferFeatureUpdatesPeriodInDays

#### <a name="windowsupdateforbusinessconfigurationfeatureupdatespaused"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesPaused 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Update/PauseFeatureUpdates

#### <a name="windowsupdateforbusinessconfigurationfeatureupdatespausestartdatetime"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesPauseStartDateTime 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Update/PauseFeatureUpdatesStartTime

#### <a name="windowsupdateforbusinessconfigurationfeatureupdatesrollbackstartdatetime"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesRollbackStartDateTime
**FOURNISSEUR DE SERVICES CRYPTOGRAPHIQUES**: N/a - Graph API **décalage URI**: N/a - Graph API uniquement

#### <a name="windowsupdateforbusinessconfigurationfeatureupdateswillberolledback"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesWillBeRolledBack 
**FOURNISSEUR DE SERVICES CRYPTOGRAPHIQUES**: N/a - Graph API **décalage URI**: N/a - Graph API uniquement

#### <a name="windowsupdateforbusinessconfigurationfeatureupdatesrollbackwindowindays"></a>WindowsUpdateForBusinessConfiguration.FeatureUpdatesRollbackWindowInDays
**FOURNISSEUR DE SERVICES CRYPTOGRAPHIQUES**: N/a - Graph API **décalage URI**: N/a - Graph API uniquement

#### <a name="windowsupdateforbusinessconfigurationinstallationschedule"></a>WindowsUpdateForBusinessConfiguration.InstallationSchedule
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy **décalage URI**: /Config/Update/ActiveHoursStart, /Config/Update/ActiveHoursEnd, /Config/Update/ScheduledInstallDay, /Config/Update/ScheduledInstallTime

#### <a name="windowsupdateforbusinessconfigurationmicrosoftupdateserviceallowed"></a>WindowsUpdateForBusinessConfiguration.MicrosoftUpdateServiceAllowed 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Update/AllowMUUpdateService

#### <a name="windowsupdateforbusinessconfigurationpreviewbuildsetting"></a>WindowsUpdateForBusinessConfiguration.PreviewBuildSetting 
**Fournisseur de services cryptographiques**: ./Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Update/ManagePreviewBuilds

#### <a name="windowsupdateforbusinessconfigurationqualityupdatesdeferralperiodindays"></a>WindowsUpdateForBusinessConfiguration.QualityUpdatesDeferralPeriodInDays 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Update/DeferQualityUpdatesPeriodInDays

#### <a name="windowsupdateforbusinessconfigurationqualityupdatespaused"></a>WindowsUpdateForBusinessConfiguration.QualityUpdatesPaused 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Update/PauseQualityUpdates

#### <a name="windowsupdateforbusinessconfigurationqualityupdatespausestartdatetime"></a>WindowsUpdateForBusinessConfiguration.QualityUpdatesPauseStartDateTime 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Update/PauseQualityUpdatesStartTime

#### <a name="windowsupdateforbusinessconfigurationqualityupdatesrollbackstartdatetime"></a>WindowsUpdateForBusinessConfiguration.QualityUpdatesRollbackStartDateTime
**FOURNISSEUR DE SERVICES CRYPTOGRAPHIQUES**: N/a - Graph API **décalage URI**: N/a - Graph API uniquement

#### <a name="windowsupdateforbusinessconfigurationqualityupdateswillberolledback"></a>WindowsUpdateForBusinessConfiguration.QualityUpdatesWillBeRolledBack 
**FOURNISSEUR DE SERVICES CRYPTOGRAPHIQUES**: N/a - Graph API **décalage URI**: N/a - Graph API uniquement

#### <a name="windowsupdateforbusinessconfigurationscheduleimminentrestartwarninginminutes"></a>WindowsUpdateForBusinessConfiguration.ScheduleImminentRestartWarningInMinutes 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Update/ScheduleImminentRestartWarning

#### <a name="windowsupdateforbusinessconfigurationschedulerestartwarninginhours"></a>WindowsUpdateForBusinessConfiguration.ScheduleRestartWarningInHours 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Update/ScheduleRestartWarning

#### <a name="windowsupdateforbusinessconfigurationskipchecksbeforerestart"></a>WindowsUpdateForBusinessConfiguration.SkipChecksBeforeRestart 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Update/SetEDURestart

#### <a name="windowsupdateforbusinessconfigurationupdateweeks"></a>WindowsUpdateForBusinessConfiguration.UpdateWeeks 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Update/ScheduledInstallEveryWeek, /Config/Update/ScheduledInstallFirstWeek, /Config/Update/ScheduledInstallFourthWeek, /Config/Update/ScheduledInstallSecondWeek, / config/mise à jour / ScheduledInstallThirdWeek

#### <a name="windowsupdateforbusinessconfigurationuserpauseaccess"></a>WindowsUpdateForBusinessConfiguration.UserPauseAccess 
**Fournisseur de services cryptographiques**: ./Device/Vendor/MSFT/Policy  
**Décalage d’URI**: /Config/Update/SetDisablePauseUXAccess


## <a name="next-steps"></a>Étapes suivantes

- [Vue d’ensemble de configuration de périphérique](device-profiles.md)
- [Référence de fournisseur de service de configuration](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference) (ouvre un autre site Docs)
