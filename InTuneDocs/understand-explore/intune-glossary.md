---
title: "Intune 字彙 | Microsoft Docs"
description: "了解 Microsoft Intune 中的一些術語"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/17/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 86d00901-fac7-4471-aac2-f1d13a4879b6
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: 9e084cce8e34b0de2dce7c6b8503d5b5089c930e
ms.lasthandoff: 04/14/2017


---

# <a name="microsoft-intune-glossary"></a>Microsoft Intune 字彙

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="a"></a>A

|||
|-|-|
|App SDK|[Microsoft Intune App SDK](/intune/develop/intune-app-sdk) 可讓您將功能新增至您的內部撰寫應用程式，讓 Intune 行動應用程式管理原則可以管理他們。|
|App Wrapping Tool|建立企業營運應用程式包裝函式的[命令列應用程式](/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)，因而可讓 Intune 行動應用程式管理原則管理應用程式。|
|可用安裝|使用這個動作部署應用程式時，應用程式會顯示在公司入口網站中，而且使用者可以[隨需安裝](/intune/deploy-use/deploy-apps)。|
|Azure 入口網站|很快就會引進的新 Intune 主控台。 此時，您可以使用 Azure 入口網站建立裝置的 [Intune MAM 原則](/intune/deploy-use/azure-portal-for-microsoft-intune-mam-policies)。|

## <a name="b"></a>B
|||
|-|-|
|BYOD|[攜帶您自己的裝置](/intune/get-started/choose-how-to-enroll-devices1)。 使用者可以在裝置上安裝 Intune 公司入口網站應用程式，然後進行註冊，以存取公司資源 (例如電子郵件、公司應用程式、公司資料和支援)。|

## <a name="c"></a>C
|||
|-|-|
|憑證設定檔|當您使用 Wi-Fi、電子郵件或 VPN 設定檔時，可以使用這個原則類型，透過憑證[安全存取公司資源](/intune/deploy-use/secure-resource-access-with-certificate-profiles)。|
|雲端儲存空間|[儲存](/intune/deploy-use/add-apps#cloud-storage-space)您所建立之應用程式或應用程式資料的位置。|
|COD|根據組織需求和所管理裝置的類型，可以透過各種方式註冊[公司擁有的裝置](/intune/get-started/choose-how-to-enroll-devices1)。|
|公司入口網站|可供使用者[存取公司資料和應用程式](/intune/get-started/microsoft-intune-company-portal)的應用程式或網站。|
|相容性原則|請確定用來存取公司應用程式和資料的裝置[符合特定規則](/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune) (例如使用 PIN 存取裝置)，以及裝置上所儲存資料的加密。|
|符合規定及不符合規定的應用程式|這些設定是[一般組態原則](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)的一部分，可讓您定義使用者可以執行或無法執行的應用程式清單。 Intune 接著會透過下列方式通知您： 已安裝不相容應用程式的報表，或執行報表。 對於某些平台，Intune 也可以封鎖安裝不相容的應用程式。|
|條件式存取|[允許存取公司電子郵件、Office 365 和其他服務](/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)，而這些項目僅來自與您所設定之規則相容的裝置。|
|自訂原則|一般組態原則未包含符合您需求的內建設定時，請[使用這些原則](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)。 您可以使用自訂原則，透過其他方式 (例如 Apple Configurator 或 OMA-URI) 建立設定。|

## <a name="d"></a>D
|||
|-|-|
|部署|將應用程式或原則傳送至所管理裝置或使用者的動作。|
|部署動作|[部署應用程式](/intune/deploy-use/deploy-apps-in-microsoft-intune)時所進行的選擇。 您可以選擇將應用程式安裝設為必要、將應用程式安裝設為選擇性，也可以解除安裝應用程式。|
|裝置註冊管理員|組織可以搭配使用 Intune 與單一使用者帳戶來管理大量的行動裝置。 [裝置註冊管理員 (DEM)](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) 帳戶是特殊 Intune 帳戶，最多可以註冊 1,000 部裝置。|
|裝置群組對應|協助您根據您或使用者可指派給裝置的裝置類別目錄 (例如 "Personal" 或 "Sales")，[自動將裝置新增至群組](/intune/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune)。|

## <a name="e"></a>E
|||
|-|-|
|電子郵件設定檔|這個原則可以用來設定行動裝置上特定電子郵件用戶端的[電子郵件存取設定](/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)，以將使用者必須執行的設定量減到最少。|
|EMS|Microsoft Enterprise Mobility + Security (之前為 Enterprise Mobility Suite) 會保護公司資料，同時讓使用者[存取應用程式和其所需的內容](https://www.microsoft.com/cloud-platform/enterprise-mobility)。|
|使用者|使用 Intune 管理之[手機和電腦這類裝置的使用者](/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune)。|
|註冊|Microsoft Intune 使用[註冊](/intune/deploy-use/enroll-devices-in-microsoft-intune)來管理裝置，並允許其存取資源。|

## <a name="f"></a>F
|||
|-|-|
|FastTrack|適用於合格方案中具有 150 個授權之 Intune 使用者的 [Microsoft 服務](https://technet.microsoft.com/library/mt228265.aspx)。 Microsoft 專家會使用這項服務與您合作，來啟動並執行 Intune。|

## <a name="g"></a>G
|||
|-|-|
|中|群組可讓您[邏輯收集使用者或裝置](/intune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune)。 例如，您可以建立所有 Windows 電腦的群組。 您接著可以將應用程式和原則部署至這些群組。|

## <a name="h"></a>H
|||
|-|-|
|混合式|可以[透過 System Center Configuration Manager 主控台](/intune/get-started/integration-with-cloud-services)管理使用 Intune 所註冊之裝置的組態。|

## <a name="i"></a>I
|||
|-|-|
|Intune 系統管理主控台|用於大部分 Intune 管理作業的目前主控台。|
|Intune 軟體用戶端|另一種[管理一些 Windows 電腦](/intune/deploy-use/manage-windows-pcs-with-microsoft-intune)的方式。 如需決定要使用之方法的協助，請參閱[選擇如何管理裝置](/intune/get-started/choose-how-to-manage-devices)。|
|Intune 軟體發行者|一種工具，用來[定義您要部署的應用程式並將它們上傳至雲端儲存空間](/intune/deploy-use/add-apps)。|
|清查|用來檢視所管理裝置上[安裝的硬體和軟體](/intune/deploy-use/understand-your-devices-with-inventory-in-microsoft-intune)。|

## <a name="k"></a>K
|||
|-|-|
|資訊站模式|設定為[一般組態原則](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)的一 部分，這個模式可讓您鎖定裝置。 例如，您可以設定零售裝置只允許執行一個應用程式。|

## <a name="m"></a>M
|||
|-|-|
|受管理的瀏覽器|一個[網頁瀏覽應用程式](/intune/deploy-use/manage-internet-access-using-managed-browser-policies)，您可以在組織中使用 Microsoft Intune 來部署此應用程式。 受管理的瀏覽器原則會設定允許清單或封鎖清單，以限制受管理瀏覽器的使用者可瀏覽的網站。|
|行動應用程式管理|[行動應用程式管理 (MAM)](/intune/deploy-use/overview-of-app-lifecycle-in-microsoft-intune) 可讓您針對使用者發行、推送、設定、保護、監視和更新行動應用程式。
|行動裝置管理|[行動裝置管理 (MDM)](/intune/deploy-use/overview-of-device-lifecycle-in-microsoft-intune) 可讓您在 Intune 中註冊裝置，以在這些裝置上進行佈建、設定、監視和採取動作。
|MDM 授權單位|[MDM 授權單位](/intune/deploy-use/get-ready-to-enroll-devices-in-microsoft-intune)會定義有權管理一組裝置的管理服務。 MDM 授權單位選項包括單獨使用 Intune，以及具備 Intune 的 Configuration Manager。|
|行動應用程式佈建原則|一個 iOS 原則，可協助您確定所部署 iOS 應用程式的[佈建設定檔](/intune/deploy-use/ios-mobile-app-provisioning-profiles)未過期。|
|行動應用程式組態原則|一個 iOS 原則，用來在執行時[提供相容 iOS 應用程式的設定](/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune) (例如，公司名稱或伺服器位址)。|

## <a name="o"></a>O
|||
|-|-|
|OMA-DM|開放行動裝置聯盟裝置管理。 一種業界標準裝置管理通訊協定，許多硬體製造商可用來控制行動裝置和電腦的功能。|
|OMA-URI|開放行動裝置聯盟統一資源識別碼。 這些可識別符合 OMA-DM 標準的個別裝置設定。 沒有內建設定符合需求時，其中有一些可以用於 [Intune 自訂原則](/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)。|

## <a name="p"></a>P
|||
|-|-|
|原則|從 Intune 傳送至裝置的[資訊套件](/intune/deploy-use/microsoft-intune-policy-reference)。 例如，您可以將安全性設定或裝置相容性資訊部署至裝置。|
|密碼重設|一種 Intune 功能，可讓您強制使用者在支援的裝置上[重設密碼](/intune/deploy-use/use-remote-lock-and-passcode-reset-in-microsoft-intune)。|

## <a name="r"></a>R
|||
|-|-|
|遠端鎖定|一種 Intune 功能，可讓您[鎖定支援的裝置](/intune/deploy-use/use-remote-lock-and-passcode-reset-in-microsoft-intune)，即使您未擁有裝置也是一樣。|
|報告|Intune 提供各種[內建報表](/intune/deploy-use/understand-microsoft-intune-operations-by-using-reports)，以將所管理裝置的相關資訊提供給您。|
|必要安裝|使用這項動作部署應用程式時，它會在[沒有使用者介入](/intune/deploy-use/deploy-apps)的情況下安裝於裝置上 (雖然對於某些平台，使用者可能必須接受安裝)。|
|需求|一個[應用程式部署作業](/intune/deploy-use/add-apps)，可讓您選取必須符合才能在裝置上安裝應用程式的需求。 例如，您可以指定必須在安裝應用程式前安裝之 iOS 的作業系統版本。|

## <a name="s"></a>S
|||
|-|-|
|選擇性抹除|[選擇性抹除](/intune/deploy-use/use-remote-wipe-to-help-protect-data-using-microsoft-intune)只會移除公司資料，包括適用的行動應用程式管理 (MAM) 資料、設定和裝置的電子郵件設定檔。 選擇性抹除會將使用者的個人資料保留在裝置上。|
|訂用帳戶|您為了存取 Intune 租用戶所簽訂的合約。|

## <a name="t"></a>T
|||
|-|-|
|TeamViewer|一個協力廠商應用程式，可使用 Intune 來提供 Intune 軟體用戶端所管理之 Windows 電腦的[遠端協助功能](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#request-and-provide-remote-assistance-for-windows-pcs)。|
|租用戶|您可以使用訂用帳戶存取之 Intune 服務的單一執行個體。|
|條款及條件|一種部署至使用者的原則類型，包含使用者必須[閱讀並接受](/intune/deploy-use/terms-and-condition-policy-settings-in-microsoft-intune)的資訊，才能使用公司入口網站來註冊和存取其工作。|

## <a name="v"></a>V
|||
|-|-|
|大量購買的應用程式|某些應用程式市集可讓您購買多個您想要在公司內執行的應用程式授權。 Intune [透過此種程式](/intune/deploy-use/manage-volume-purchased-apps-in-microsoft-intune)從應用程式市集匯入授權資訊、追蹤您已經使用多少個授權，並避免您安裝超過擁有數目的應用程式複本，來協助您管理購買的應用程式。|
|VPN 設定檔|一種原則，可將 [VPN 設定](/intune/deploy-use/vpn-connections-in-microsoft-intune)部署至所管理的裝置，以將使用者所需的任何設定減到最少。|

## <a name="w"></a>W
|||
|-|-|
|Wi-Fi 設定檔|一種原則，可將[無線網路設定](/intune/deploy-use/wi-fi-connections-in-microsoft-intune)部署至裝置，讓使用者連接至公司網路，而不需要知道或進行任何設定。

