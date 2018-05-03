---
title: Microsoft Intune - Azure 中不符合規範的訊息與動作 | Microsoft Docs
description: 建立電子郵件通知，並傳送到不符合規範的裝置。 在裝置受標記為不符合規範之後新增動作，例如新增寬限期以讓其符合規範，或建立排程來禁止存取，直到裝置符合規範為止。 在 Azure 中使用 Microsoft Intune 來執行。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8e8603ca59b46937b1529e710a8bc83aec5dd4d6
ms.sourcegitcommit: 4c18352d5b3b30080f7c7257fa63d852b1894850
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="automate-email-and-add-actions-for-noncompliant-devices---intune"></a>將電子郵件自動化，並為不符合規範的裝置新增動作 - Intune

**不符合規範時所採取的動作**功能可設定動作的時間排序順序。 這些動作會套用到不符合合規性政策的裝置。 

## <a name="overview"></a>概觀
根據預設，當 Intune 偵測到不符合規範的裝置時，Intune 會立即將其標記為不符合規範。 Azure Active Directory (AD) [條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) 隨後會封鎖該裝置。 當裝置不符合規範時，**不符合規範時所採取的動作**可讓您更靈活地決定該怎麼處置不符合規範的裝置。 例如，不立即封鎖裝置，並給使用者一個寬限期，讓其符合規範。

動作有兩種：

- **透過電子郵件通知終端使用者**：自訂電子郵件通知，再將其傳送給終端使用者。 您可以自訂收件者、主旨與郵件內文，包括公司標誌和連絡人資訊。

    此外，Intune 會在電子郵件通知中包含不符合規範裝置的詳細資料。

- **將裝置標記為不符合規範**：在裝置被標記為不符合規範後建立排程 (數天)。 您可以將動作設定為立即生效，或給使用者一個寬限期，讓其符合規範。

## <a name="before-you-begin"></a>開始之前

- 若要為不符合規範的狀況設定動作，您至少需要一項裝置合規性政策。 若要建立裝置合規性政策，請參考以下平台的說明：

  - [Android](compliance-policy-create-android.md)
  - [Android for Work](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- 當您使用裝置合規性政策禁止裝置存取公司資源時，必須設定 Azure AD 條件式存取。 請參閱 [Azure Active Directory 中的條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)以取得指導方針。

- 必須建立通知訊息範本。 為傳送電子郵件給您的使用者，會使用此範本來為不符合規範的狀況建立動作。

## <a name="create-a-notification-message-template"></a>建立通知訊息範本

1. 使用您的 Intune 認證登入 [Azure 入口網站](https://portal.azure.com)。 
2. 選取 [所有服務]，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選取 [裝置合規性]，然後選取 [通知]。 
4. 選取 [建立通知]，然後輸入下列資訊：

   - 名稱
   - 主體
   - 訊息
   - 電子郵件標題 – 包含公司標誌
   - 電子郵件頁尾 – 包含公司名稱
   - 電子郵件頁尾 – 包含連絡人資訊

   ![在 Intune 中符合規範的通知訊息範例](./media/actionsfornoncompliance-1.PNG)

一旦您完成新增資訊，請選擇 [建立]。 通知訊息範本便可供使用。

> [!NOTE]
> 您也可以編輯先前建立的 [通知] 範本。

## <a name="add-actions-for-noncompliance"></a>新增不符合規範時所採取的動作

根據預設，Intune 會自動為不符合規範的狀況建立動作。 當裝置不符合合規性政策時，此動作會將其標記為不符合規範。 您可以自訂將裝置標記為不符合規範的時間長度。 該動作無法移除。

您可以在建立新合規性政策或更新現有合規性政策時新增動作。 

1. 在 [Azure 入口網站](https://portal.azure.com)中，開啟 [Microsoft Intune]，然後選取 [裝置合規性]。
2. 選取 [原則]，選擇您的原則，然後選取 [屬性]。 

  尚未建立原則嗎？ 您可建立 [Android](compliance-policy-create-android.md)、[iOS](compliance-policy-create-ios.md)、[Windows](compliance-policy-create-windows.md) 或其他平台的原則。
  
  > [!NOTE]
  > JAMF 裝置和裝置群組目標的裝置目前無法接收合規性動作。

3. 選取 [不符合規範時所採取的動作]，然後選取 [新增] 輸入動作參數。 您可以選擇先前建立的訊息範本，新增其他收件者，並更新寬限期排程。 您可以輸入排程上的天數 (0 到 365)，然後強制執行條件式存取原則。 如果您輸入 **0** 天，則條件式存取會**立即**禁止對公司資源的存取。

4. 完成後，請選取 [新增] > [確定]以儲存變更。

## <a name="next-steps"></a>接下來的步驟
執行報表來監視裝置合規性活動。 [如何使用 Intune 監視裝置合規性](device-compliance-monitor.md)提供了一些指導方針。
