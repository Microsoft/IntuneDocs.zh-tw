---
title: 將 Jamf Pro 與 Microsoft Intune 整合以符合規範
titlesuffix: ''
description: 使用 Azure Active Directory 條件式存取搭配 Microsoft Intune 合規性政策來協助保護受 Jamf 管理的裝置。
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 01/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: cdeb3a21af2b4cf020d3e5029eeb5b0bc31db062
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>將 Jamf Pro 與 Intune 整合以取得合規性

|適用對象：Azure 入口網站的 Intune |
|--|
|您需要傳統入口網站的 Intune 相關文件嗎？ [請移至這裡](/intune/introduction-intune?toc=/intune-classic/toc.json)。|
| |

如果您的組織使用 [Jamf Pro](https://www.jamf.com) 來管理使用者的 Mac，您可以使用 Microsoft Intune 合規性原則搭配 Azure Active Directory 條件式存取，來確保您組織中的裝置能符合規範。

## <a name="prerequisites"></a>必要條件

您需要下列項目以搭配 Jamf Pro 設定條件式存取：

- Jamf Pro 10.1.0 或更新版本
- [macOS 版公司入口網站應用程式](https://aka.ms/macoscompanyportal)
- 具有 OS X 10.11 Yosemite 或更新版本的 macOS 裝置

## <a name="connecting-intune-to-jamf-pro"></a>將 Intune 連線到 Jamf Pro

您可以透過下列方法將 Intune 連線到 Jamf Pro：

1. 在 Azure 中建立新的應用程式
2. 使 Intune 與 Jamf Pro 整合
3. 在 Jamf Pro 中設定條件式存取

## <a name="create-a-new-application-in-azure-active-directory"></a>在 Azure Active Directory 中建立新的應用程式

1. 開啟 [Azure Active Directory] > [應用程式註冊]。
2. 按一下 [+新增應用程式註冊]。
3. 輸入**顯示名稱**，例如 **Jamf 條件式存取**。
4. 選取 [Web 應用程式 / API]。
5. 使用 Jamf Pro 執行個體 URL 指定 [登入 URL]。
6. 按一下 [建立應用程式]。
7. 儲存新建立的 [應用程式識別碼]，然後開啟 [設定] 並巡覽至 [API 存取] > [金鑰] 以建立新的應用程式金鑰。 輸入 [描述]、[到期日] 前等待的時間，然後將儲存應用程式金鑰。

   > [!IMPORTANT]
   > 應用程式金鑰在此程序期間只會顯示一次。 請務必將它儲存在您可以輕鬆擷取的地方。

8. 開啟 [設定] ，然後巡覽至 [API 存取] > [必要權限]，並刪除所有權限。

   > [!NOTE]
   > 新增必要權限。 應用程式只有在具有單一必要權限時才能正常運作。

9. 選取 [Microsoft Intune API]，然後按一下 [選取]。
10. 選擇 [傳送裝置屬性到 Microsoft Intune]，然後按一下 [選取]。
11. 儲存應用程式的必要權限之後，請按一下 [授與權限] 按鈕。

    > [!NOTE]
    > 如果應用程式金鑰到期，您必須在 Microsoft Azure 中建立新的應用程式金鑰，然後更新 Jamf Pro 中的條件式存取資料。 Azure 允許您同時啟用舊金鑰與新金鑰，以避免服務中斷。

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>使 Intune 與 Jamf Pro 整合

1. 在 Microsoft Azure 入口網站中，開啟 [Microsoft Intune] > [裝置合規性] > [Partner device management] \(夥伴裝置管理)。
2. 將應用程式識別碼貼上至 [Jamf Azure Active Directory 應用程式識別碼] 欄位，以啟用適用於 Jamf 的合規性連接器。
3. 按一下 **[儲存]**。

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>在 Jamf Pro 中設定 Microsoft Intune 整合

1. 在 Jamf Pro 中，瀏覽至 [全域管理] > [條件式存取]。 按一下 [Microsoft Intune 整合] 索引標籤上的 [編輯] 按鈕。
2. 選取 [啟用 Microsoft Intune 整合] 核取方塊。
3. 提供您 Azure 租用戶的相關必要資訊，包括 [位置]、[網域名稱]，以及您在先前步驟中儲存的 [應用程式識別碼] 和 [應用程式金鑰]。
4. 按一下 **[儲存]**。 Jamf Pro 會測試您的設定，並確認是否成功。

## <a name="set-up-compliance-policies-and-register-devices"></a>設定合規性原則並註冊裝置

完成設定 Intune 和 Jamf 之間的整合後，您需要[將合規性原則套用至受 Jamf 管理的裝置](conditional-access-assign-jamf.md)。

## <a name="information-shared-from-jamf-pro-to-intune"></a>從 Jamf Pro 共用至 Intune 的資訊

Jamf Pro 會擷取有關受管理 macOS 裝置的清查資訊。 Jamf Pro 會將下列資訊回報給 Intune：

* 裝置 Azure AD 識別碼
* JAMF 清查狀態 (過去 24 小時內使用 Jamf Pro 簽入之電腦的清查狀態)
* 作業系統版本
* 使用者 Azure AD 識別碼
* 已加密 (FileVault 2)
* 閘道管理員狀態
* 密碼：字元集數目下限
* 密碼到期 (天數)
* 密碼類型：簡單、英數字元，或不明
* 避免自動登入
* 必要的密碼長度
* 密碼：避免重複使用的舊密碼數目
* 系統完整性保護
* 上次簽入時間
* 架構類型
* 可用的 RAM 插槽
* 電池容量
* 開機 ROM
* 匯流排速度
* 快取大小
* 裝置名稱
* 加入網域
* Jamf 識別碼
* MAC 位址
* 品牌
* 型號
* 型號識別碼
* NIC 速度
* 核心數目
* 處理器數目
* OS
* 平台
* 處理器速度
* 處理器類型
* 次要 MAC 位址
* 序號
* SMC 版本
* RAM 總計
* UDID
* 使用者電子郵件

## <a name="next-steps"></a>接下來的步驟

- [將合規性原則套用至受 Jamf 管理的裝置](conditional-access-assign-jamf.md)
