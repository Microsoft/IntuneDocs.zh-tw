---
title: "iOS Classroom 應用程式的 Intune 共用裝置設定"
titlesuffix: Azure portal
description: "了解可用來控制 iOS 裝置上 Classroom 應用程式設定的 Intune 設定。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1381a5ce-c743-40e9-8a10-4c218085bb5f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c183af24e953f87e12e87654f767dd9a30f8509f
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-configure-intune-education-settings-for-shared-ipad-devices"></a>如何設定共用 iPad 裝置的 Intune 教育設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune 支援 iOS Classroom 應用程式，可協助老師在課堂中引導學習，並控制學生的裝置。 此外，對於 Classroom 應用程式，Apple 支援設定學生 iPad 裝置的功能，可讓多位學生共用單一裝置。 本文件將引導您使用 Intune 達成這個目標。

如需設定專用 (1:1) iPad 裝置以使用 Classroom 應用程式的詳細資訊，請參閱[如何設定 iOS Classroom 應用程式的 Intune 設定](education-settings-configure-ios.md)。

## <a name="before-you-start"></a>開始之前

使用共用 iPad 功能的必要條件如下：

- 安裝 [Apple School Manager](apple-school-manager-set-up-ios.md) 和 [School Data Sync (SDS)](https://support.office.com/article/Apple-School-Manager-integration-with-Intune-for-Education-and-School-Data-Sync-974bd1f9-2c7a-45cb-9447-b58166108617)。
- 在 Apple School Manager 的安裝過程中，為學生設定[管理式 Apple ID](http://help.apple.com/schoolmanager/#/tes78b477c81)。 [深入了解管理式 Apple ID](https://support.apple.com/en-us/HT205918)。
- 針對已從 Apple School Manager 同步處理的裝置序號，建立註冊設定檔。

## <a name="step-1---import-your-school-data-into-azure-active-directory"></a>步驟 1 - 將學校資料匯入至 Azure Active Directory

使用 Microsoft 的學校資料同步處理 (SDS) 從現有的學生資訊系統 (SIS) 將學校記錄匯入至 Azure Active Directory (Azure AD)。
SDS 會同步處理 SIS 的資訊，並將它儲存在 Azure AD 中。 Azure AD 是一套可協助您組織使用者與裝置的 Microsoft 管理系統。 之後，您就可以使用這些資料來協助管理您的學生和課程。 [深入了解如何部署 SDS](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91)。

### <a name="how-to-import-data-using-sds"></a>如何使用 SDS 匯入資料

您可以使用下列其中一種方法，將資訊匯入至 SDS：

- [CSV 檔案](https://support.office.com/article/Follow-these-steps-71d5fe4a-aa51-4f35-9b53-348898a390a1) - 手動匯出並編譯逗號分隔值 (.csv) 檔案
- [PowerSchool API](https://support.office.com/article/Follow-these-steps-851b5edc-558f-43a9-9122-b2d63458cb8f) - 簡化 Azure AD 同步流程的 SIS 提供者
- [Clever API](https://support.office.com/article/Follow-these-steps-f3d92fde-3ad0-48f3-80a1-1ad0ac4a3fae) - 直接與 Azure AD 進行同步處理的身分識別管理解決方案
- [OneRoster](https://support.office.com/article/Follow-these-steps-f43cbb2a-b502-497d-a8b1-783dc05a57ab) - 您可以匯出並轉換成此種 CSV 格式以便與 Azure AD 同步

### <a name="find-out-more"></a>深入了解

- [深入了解將內部部署學校資料同步至 Azure AD 的完整經驗](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)
- [深入了解 Microsoft 學校資料同步處理](https://sds.microsoft.com/)
- [深入了解 Azure Active Directory 中的授權](https://docs.microsoft.com/azure/active-directory/active-directory-licensing-whatis-azure-portal)


## <a name="step-2---create-and-assign-an-ios-education-profile-in-intune"></a>步驟 2 - 在 Intune 中建立並指派 iOS 教育設定檔

### <a name="configure-general-settings"></a>設定一般設定

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [其他]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中選擇 [設定裝置]。
4. 在 [裝置設定] 刀鋒視窗中，選擇 [管理]  >  [設定檔]。
5. 在設定檔刀鋒視窗中，選擇 [建立設定檔]。
6. 在 [建立設定檔] 刀鋒視窗中，為 iOS 教育設定檔輸入 [名稱] 及 [描述]。
7. 從 [平台] 下拉式清單中，選擇 [iOS]。
8. 從 [設定檔類型] 下拉式清單中，選擇 [教育]。
9. 選擇 [設定]  >  [設定]。

接下來，您需要憑證才能建立老師和學生 iPad 之間的信任關係。 憑證是用來順暢且無訊息地驗證裝置之間的連線，而不需要輸入使用者名稱和密碼。

>[!Important]
>您使用的老師和學生憑證必須由不同的憑證授權單位 (CA) 發行。 您必須建立兩個新的次級 CA，連線到現有的憑證基礎結構。一個供老師使用，一個供學生使用。

iOS 教育設定檔只支援 PFX 憑證。 不支援 SCEP 憑證。

您建立的憑證除了支援使用者驗證，還必須支援伺服器驗證。

### <a name="configure-teacher-certificates"></a>設定老師憑證

在 [教育] 刀鋒視窗中，選擇 [老師憑證]。

#### <a name="configure-teacher-root-certificate"></a>設定老師根憑證

在 [老師根憑證] 下，選擇瀏覽按鈕以選取副檔名為 .cer (DER 或 Base64 編碼) 或 .P7B (不論有無完整鏈結) 的老師根憑證。

#### <a name="configure-teacher-pkcs12-certificate"></a>設定老師 PKCS#12 憑證

在 [老師 PKCS #12 憑證] 下，設定下列值︰

- **主體名稱格式** - Intune 會自動為老師憑證的憑證一般名稱前面加上 **leader**，然後為學生憑證的憑證一般名稱前面加上 **member**。
- **憑證授權單位**：在企業版 Windows Server 2008 R2 或更新版本上執行的企業憑證授權單位 (CA)。 不支援獨立 CA。
- **憑證授權單位名稱**：輸入您的憑證授權單位名稱。
- **憑證範本名稱**- 輸入已新增至發行 CA 的憑證範本名稱。
- **更新閾值 (%)** - 指定裝置要求憑證更新之前，剩餘的憑證存留時間百分比。
- **憑證有效期間** - 指定憑證到期之前的剩餘時間。 您可以指定一個比憑證範本中指定之有效期間更低，而不是更高的值。 舉例來說，如果憑證範本中的憑證有效期間為兩年，您可以指定一年而不是五年的值。 此值也必須低於發行 CA 憑證的剩餘有效期間。

當您完成設定老師憑證時，請選擇 [確定]。

### <a name="configure-student-certificates"></a>設定學生憑證

1. 在 [教育] 刀鋒視窗中，選擇 [學生憑證]。
2. 在 [學生憑證] 刀鋒視窗中，從 [學生裝置憑證類型] 清單中，選擇 [共用的 iPad]。

#### <a name="configure-student-root-certificate"></a>設定學生根憑證

在 [裝置根憑證] 下，選擇瀏覽按鈕以選取副檔名為 .cer (DER 或 Base64 編碼) 或 .P7B (不論有無完整鏈結) 的學生根憑證。

#### <a name="configure-device-pkcs12-certificate"></a>設定裝置 PKCS#12 憑證

在 [學生 PKCS #12 憑證] 下，設定下列值︰

- **主體名稱格式** - Intune 會自動為老師憑證的憑證一般名稱前面加上 leader，並為裝置憑證的憑證一般名稱前面加上 member。
- **憑證授權單位**：在企業版 Windows Server 2008 R2 或更新版本上執行的企業憑證授權單位 (CA)。 不支援獨立 CA。
- **憑證授權單位名稱**：輸入您的憑證授權單位名稱。
- **憑證範本名稱** - 輸入已新增至發行 CA 的憑證範本名稱。
- **更新閾值 (%)** - 指定裝置要求憑證更新之前，剩餘的憑證存留時間百分比。
- **憑證有效期間** - 指定憑證到期之前的剩餘時間。 您可以指定一個比憑證範本中指定之有效期間更低，而不是更高的值。 舉例來說，如果憑證範本中的憑證有效期間為兩年，您可以指定一年而不是五年的值。 此值也必須低於發行 CA 憑證的剩餘有效期間。

當您完成設定憑證時，請選擇 [確定]。

### <a name="complete-certificate-setup"></a>完成憑證設定

1. 在 [教育] 刀鋒視窗中，選擇 [確定]。
2. 在 [建立設定檔] 刀鋒視窗中，選擇 [建立]。

設定檔隨即建立，並出現在 [設定檔清單] 刀鋒視窗上。

## <a name="step-3---create-a-device-category"></a>步驟 3 - 建立裝置類別

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [其他]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置註冊]。
4. 在 [註冊 - 概觀] 刀鋒視窗中，選擇 [裝置類別]。
5. 在 [註冊 - 裝置類別] 刀鋒視窗中，選擇 [建立]。
6. 在 [建立裝置類別] 刀鋒視窗中，為類別輸入 [名稱] 及 [描述]。
7. 在 [建立裝置類別] 刀鋒視窗中，選擇 [建立]。

即會在 [註冊 – 裝置類別] 刀鋒視窗中建立裝置類別。

## <a name="step-4--create-a-dynamic-group"></a>步驟 4 – 建立動態群組

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [其他]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [群組]。
4. 在 [使用者和群組 - 所有群組] 刀鋒視窗中，選擇 [新增群組]。
5. 在 [群組] 刀鋒視窗中，為群組輸入 [名稱] 及 [描述]。
6. 從 [成員資格類型] 下拉式清單中，選擇 [動態裝置]。
7. 選擇 [動態裝置成員] 來建立成員資格規則。
8. 在 [動態成員資格規則] 刀鋒視窗中：
1. 從 [新增裝置，其中] 下拉式清單中，選取 [deviceCategory]。
2. 選擇 [等於]
3. 在空白的文字方塊中輸入您建立的裝置類別
9. 在 [動態成員資格規則] 刀鋒視窗中，選擇 [新增查詢]。
10. 在 [群組] 刀鋒視窗中，選擇 [建立]。

即會在 [使用者和群組 – 所有群組] 刀鋒視窗中建立動態群組。

## <a name="step-5--assign-a-device-to-a-category-carts"></a>步驟 5 – 將裝置指派給類別 (購物車)

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [其他]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置]。
4. 在 [裝置] 刀鋒視窗中，選擇 [所有裝置]。
5. 在 [裝置 – 所有裝置] 刀鋒視窗中，選擇 一個裝置。
6. 在 [裝置] 刀鋒視窗中，選擇 [內容]。
7. 在裝置的 [內容] 刀鋒視窗中，於 [裝置類別] 文字方塊中輸入裝置類別。
8. 在 [裝置] 刀鋒視窗中，選擇 [儲存]。

裝置現在已與裝置類別相關聯。 針對您想要關聯到所建立裝置類別的所有裝置，重複此處理序。

## <a name="step-6--create-classroom-profiles"></a>步驟 6 – 建立教室設定檔

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [其他]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中選擇 [設定裝置]。
4. 在 [裝置設定] 刀鋒視窗中，選擇 [管理]  > [購物車設定檔]。
5. 在設定檔刀鋒視窗中，選擇 [建立設定檔]。
6. 在 [建立關聯] 刀鋒視窗中，輸入 [名稱] 及 [描述]。
7. 選擇 [選取類別] > [設定]，將群組關聯至購物車設定檔。
8. 選擇要納入購物車設定檔的類別，然後選擇 [選取]。 
9. 選擇 [選取購物車] > [設定]，將群組關聯至購物車設定檔。
10. 選擇要納入購物車設定檔的群組，然後選擇 [選取]。
11. 在 [建立關聯] 刀鋒視窗中，選擇 [儲存] 來儲存購物車設定檔。

設定檔隨即建立，並出現在 [設定檔清單] 刀鋒視窗上。

## <a name="step-7---assign-the-cart-profile-to-classes"></a>步驟 7 - 將購物車設定檔指派給類別

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [其他]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中選擇 [設定裝置]。
4. 在 [裝置設定] 刀鋒視窗中，選擇 [監視]  > [指派狀態]。
5. 在 [指派狀態] 刀鋒視窗中，選取您所建立的 [購物車設定檔]。
6. 在 [購物車設定檔] 刀鋒視窗中，選擇 [指派]，然後在 [Include] 中，選擇 [選取要納入的群組]。
7. 選擇您希望購物車設定檔設為目標的類別 (不要選取群組)，然後選擇 [選取]。 
8. 完成之後，請選擇 **[儲存]**。

指派完成時，Intune 會根據教室指派，將教室設定檔部署到目標裝置上。

## <a name="next-steps"></a>後續步驟

現在學生可以共用學生間的裝置，學生可以挑選教室中的任何 iPad，使用 PIN 碼進行登入，然後利用其內容進行個人化。 如需共用 iPad 的詳細資訊，請參閱 [Apple 網站](https://www.apple.com/education/it/)。
