---
title: 適用於 iOS Classroom 應用程式的 Intune 設定
titleSuffix: Microsoft Intune
description: 了解可用來控制 iOS 裝置上 Classroom 應用程式設定的 Intune 設定。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 02/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1381a5ce-c743-40e9-8a10-4c218085bb5f
ms.reviewer: derriw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 63284a1dd5c1d5a6c588775f1c282bfcfef5de67
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-configure-intune-settings-for-the-ios-classroom-app"></a>如何設定 iOS Classroom 應用程式的 Intune 設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="introduction"></a>簡介
[Classroom](https://itunes.apple.com/app/id1085319084) 應用程式可協助老師在課堂中引導學習，並控制學生的裝置。 例如，老師使用應用程式可以︰

- 開啟學生裝置上的應用程式
- 鎖定和解除鎖定 iPad 螢幕
- 檢視學生的 iPad 螢幕
- 將學生的 iPad 導覽至一本書的書籤或章節
- 將學生的 iPad 螢幕顯示到 Apple 電視上

使用 Intune iOS **教育**裝置設定檔，以及本主題中的資訊，可協助您設定 Classroom 應用程式，以及在其中使用此應用程式的裝置。

## <a name="before-you-start"></a>開始之前

開始進行這些設定之前，請先考慮下列事項：

- 老師和學生都必須在 Intune 中註冊 iPad
- 確認您已在老師的裝置上安裝 [Apple Classroom](https://itunes.apple.com/us/app/classroom/id1085319084?mt=8) 應用程式。 您可以手動或使用 [Intune 應用程式管理](app-management.md)安裝此應用程式。
- 您必須設定憑證來驗證老師裝置和學生裝置之間的連線 (請參閱步驟 2)
- 老師和學生的 iPad 必須位於相同的 Wi-Fi 網路，而且也都啟用藍牙
- Classroom 應用程式是在執行 iOS 9.3 或更新版本之受監督的 iPad 上執行
- 在此版本中，Intune 支援管理每個學生都有自己專用 iPad 的 1 對 1 案例


## <a name="step-1---import-your-school-data-into-azure-active-directory"></a>步驟 1 - 將學校資料匯入至 Azure Active Directory

使用 Microsoft 的學校資料同步處理 (SDS) 從現有的學生資訊系統 (SIS) 將學校記錄匯入至 Azure Active Directory (Azure AD)。
SDS 會同步處理 SIS 的資訊，並將它儲存在 Azure AD 中。 Azure AD 是一套可協助您組織使用者與裝置的 Microsoft 管理系統。 之後，您就可以使用這些資料來協助管理您的學生和課程。 [深入了解如何部署 SDS](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91)。

### <a name="how-to-import-data-using-sds"></a>如何使用 SDS 匯入資料

您可以使用下列其中一種方法，將資訊匯入至 SDS：

- [CSV 檔案](https://support.office.com/article/Follow-these-steps-71d5fe4a-aa51-4f35-9b53-348898a390a1) - 手動匯出並編譯逗號分隔值 (.csv) 檔案
- [PowerSchool API](https://support.office.com/article/Follow-these-steps-851b5edc-558f-43a9-9122-b2d63458cb8f) - 簡化 Azure AD 同步流程的 SIS 提供者
- [OneRoster](https://support.office.com/article/Follow-these-steps-f43cbb2a-b502-497d-a8b1-783dc05a57ab) - 您可以匯出並轉換成此種 CSV 格式以便與 Azure AD 同步

### <a name="find-out-more"></a>深入了解

- [深入了解將內部部署學校資料同步至 Azure AD 的完整經驗](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)
- [深入了解 Microsoft 學校資料同步處理](https://sds.microsoft.com/)
- [深入了解 Azure Active Directory 中的授權](https://docs.microsoft.com/azure/active-directory/active-directory-licensing-whatis-azure-portal)

## <a name="step-2---create-and-assign-an-ios-education-profile-in-intune"></a>步驟 2 - 在 Intune 中建立並指派 iOS 教育設定檔

### <a name="configure-general-settings"></a>設定一般設定

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 窗格中，選擇 [裝置設定]。
2. 在 [裝置設定] 窗格的 [管理] 區段下，選擇 [設定檔]。
5.  在 [設定檔] 窗格中，選擇 [建立設定檔]。
6.  在 [建立設定檔] 窗格中，輸入 iOS 教育設定檔的 [名稱] 和 [描述]。
7.  從 [平台] 下拉式清單中，選擇 [iOS]。
8.  從 [設定檔類型] 下拉式清單中，選擇 [教育]。
9.  選擇 [設定]  >  [設定]。


接下來，您需要憑證才能建立老師和學生 iPad 之間的信任關係。 憑證是用來順暢且無訊息地驗證裝置之間的連線，而不需要輸入使用者名稱和密碼。

>[!IMPORTANT]
>您使用的老師和學生憑證必須由不同的憑證授權單位 (CA) 發行。 您必須建立兩個新的次級 CA，連線到現有的憑證基礎結構。一個供老師使用，一個供學生使用。

iOS 教育設定檔只支援 PFX 憑證。 不支援 SCEP 憑證。

您建立的憑證除了支援使用者驗證，還必須支援伺服器驗證。

### <a name="configure-teacher-certificates"></a>設定老師憑證

在 [教育] 窗格中，選擇 [教師憑證]。

#### <a name="configure-teacher-root-certificate"></a>設定老師根憑證

在 [老師根憑證] 下，選擇瀏覽按鈕以選取副檔名為 .cer (DER 或 Base64 編碼) 或 .P7B (不論有無完整鏈結) 的老師根憑證。

#### <a name="configure-teacher-pkcs12-certificate"></a>設定老師 PKCS#12 憑證

在 [老師 PKCS #12 憑證] 下，設定下列值︰

- **主體名稱格式** - Intune 會自動為老師憑證的憑證一般名稱前面加上 **leader**，然後為學生憑證的憑證一般名稱前面加上 **member**。
- **憑證授權單位**：在企業版 Windows Server 2008 R2 或更新版本上執行的企業憑證授權單位 (CA)。 不支援獨立 CA。 
- **憑證授權單位名稱**：輸入您的憑證授權單位名稱。
- **憑證範本名稱** - 輸入已新增至發行 CA 的憑證範本名稱。 
- **更新閾值 (%)** - 指定裝置要求憑證更新之前，剩餘的憑證存留時間百分比。
- **憑證有效期間** - 指定憑證到期之前的剩餘時間。
您可以指定一個比憑證範本中指定之有效期間更低，而不是更高的值。 舉例來說，如果憑證範本中的憑證有效期間為兩年，您可以指定一年而不是五年的值。 此值也必須低於發行 CA 憑證的剩餘有效期間。

當您完成設定憑證時，請選擇 [確定]。

### <a name="configure-student-certificates"></a>設定學生憑證

1.  在 [教育] 窗格中，選擇 [學生憑證]。
2.  在 [學生憑證] 窗格中，從 [學生裝置憑證] 類型清單中，選擇 [1:1]。

#### <a name="configure-student-root-certificate"></a>設定學生根憑證

在 [學生根憑證] 下，選擇瀏覽按鈕以選取副檔名為 .cer (DER 或 Base64 編碼) 或 .P7B (不論有無完整鏈結) 的學生根憑證。

#### <a name="configure-student-pkcs12-certificate"></a>設定學生 PKCS#12 憑證

在 [學生 PKCS #12 憑證] 下，設定下列值︰

- **主體名稱格式** - Intune 會自動為老師憑證的憑證一般名稱前面加上 **leader**，然後為學生憑證的憑證一般名稱前面加上 **member**。
- **憑證授權單位**：在企業版 Windows Server 2008 R2 或更新版本上執行的企業憑證授權單位 (CA)。 不支援獨立 CA。 
- **憑證授權單位名稱**：輸入您的憑證授權單位名稱。
- **憑證範本名稱** - 輸入已新增至發行 CA 的憑證範本名稱。 
- **更新閾值 (%)** - 指定裝置要求憑證更新之前，剩餘的憑證存留時間百分比。
- **憑證有效期間** - 指定憑證到期之前的剩餘時間。
您可以指定一個比憑證範本中指定之有效期間更低，而不是更高的值。 舉例來說，如果憑證範本中的憑證有效期間為兩年，您可以指定一年而不是五年的值。 此值也必須低於發行 CA 憑證的剩餘有效期間。

當您完成設定憑證時，請選擇 [確定]。

## <a name="finish-up"></a>完成

1.  在 [教育] 窗格中，選擇 [確定]。
2.  在 [建立設定檔] 窗格中，選擇 [建立]。
    
設定檔隨即建立，並出現在 [設定檔清單] 窗格上。

針對當您將學校資料與 Azure AD 同步時所建立的課堂群組，將設定檔指派給群組中的學生裝置。請參閱[如何指派裝置設定檔](device-profile-assign.md)。

## <a name="next-steps"></a>接下來的步驟

現在，當老師使用 Classroom 應用程式時，就可以完整控制學生裝置。

如需 Classroom 應用程式的詳細資訊，請參閱 Apple 網站上的[課堂輔助說明](https://help.apple.com/classroom/ipad/2.0/)。

如果您想要設定共用的 iPad 裝置學生版，請參閱[如何設定共用 iPad 裝置的 Intune 教育設定](education-settings-configure-ios-shared.md)。
