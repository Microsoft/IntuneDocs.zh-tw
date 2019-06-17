---
title: Microsoft Intune - Azure 中不符合規範的訊息與動作 | Microsoft Docs
description: 建立電子郵件通知，並傳送到不符合規範的裝置。 在裝置受標記為不符合規範之後新增動作，例如新增寬限期以讓其符合規範，或建立排程來禁止存取，直到裝置符合規範為止。 在 Azure 中使用 Microsoft Intune 來執行。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/01/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b799fd65a08646b46bf7fcce67bf4a09dc0413a6
ms.sourcegitcommit: cc5d757018d05fc03ac9ea3d30f563df9bfd61ed
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/10/2019
ms.locfileid: "66819903"
---
# <a name="automate-email-and-add-actions-for-noncompliant-devices-in-intune"></a>在 Intune 中將電子郵件自動化，並為不符合規範的裝置新增動作

針對不符合合規性政策或規則的裝置，您可以新增 [不符合規範時所採取的動作]  。 這項功能會設定按時間排序的一連串動作，例如傳送電子郵件給終端使用者等。

## <a name="overview"></a>概觀

根據預設，當 Intune 偵測到不符合規範的裝置時，Intune 會立即將其標記為不符合規範。 Azure Active Directory (AD) [條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) 隨後會封鎖該裝置。 當裝置不符合規範時，[不符合規範時所採取的動作]  可讓您更靈活地決定該怎麼處置不符合規範的裝置。 例如，不立即封鎖裝置，並給使用者一個寬限期，讓其符合規範。

有數種動作：

- **傳送電子郵件給終端使用者**：自訂電子郵件通知，再將其傳送給終端使用者。 您可以自訂收件者、主旨與郵件內文，包括公司標誌和連絡人資訊。

    此外，Intune 會在電子郵件通知中包含不符合規範裝置的詳細資料。

- **遠端鎖定不符合規範的裝置**：針對不符合規範的裝置，您可以發出遠端鎖定。 然後便會提示使用者輸入 PIN 或密碼來解除鎖定裝置。 [遠端鎖定](device-remote-lock.md)功能的詳細資訊。 

- **將裝置標記為不符合規範**：在裝置被標記為不符合規範後建立排程 (數天)。 您可以將動作設定為立即生效，或給使用者一個寬限期，讓其符合規範。

本文將示範下列項目的作法：

- 建立訊息通知範本
- 針對不符合規範建立動作，例如傳送電子郵件或從遠端鎖定裝置


## <a name="before-you-begin"></a>開始之前

- 若要為不符合規範的狀況設定動作，您至少需要一項裝置合規性政策。 若要建立裝置合規性政策，請參考以下平台的說明：

  - [Android](compliance-policy-create-android.md)
  - [Android 工作設定檔](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- 當您使用裝置合規性政策禁止裝置存取公司資源時，必須設定 Azure AD 條件式存取。 請參閱 [Azure Active Directory 中的條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)或[透過 Intune 使用條件式存取的常見方式](conditional-access-intune-common-ways-use.md)以獲得指導方針。

## <a name="create-a-notification-message-template"></a>建立通知訊息範本

若要傳送電子郵件給您的使用者，請建立通知訊息範本。 裝置不符合規範時，您在範本中輸入的詳細資料會顯示在傳送給您使用者的電子郵件裡。

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [裝置合規性]   > [通知]  。
3. 選取 [建立通知]  。 輸入下列資訊：

   - **名稱**
   - **主旨**
   - **Message**
   - **電子郵件標題 – 包含公司標誌**
   - **電子郵件頁尾 – 包含公司名稱**
   - **電子郵件頁尾 – 包含連絡人資訊**

   ![在 Intune 中符合規範的通知訊息範例](./media/actionsfornoncompliance-1.PNG)

4. 一旦您完成新增資訊，請選擇 [建立]  。 通知訊息範本便可供使用。 您當作公司入口網站商標一部分上傳的標誌將會用於電子郵件範本。 如需公司入口網站商標的詳細資訊，請參閱[公司識別商標自訂](company-portal-app.md#company-identity-branding-customization)。

> [!NOTE]
> 您也可以變更或更新先前建立的現有通知範本。

## <a name="add-actions-for-noncompliance"></a>新增不符合規範時所採取的動作

當您建立裝置合規性政策時，Intune 會針對不符合規範自動建立動作。 如果裝置不符合合規性政策，此動作會將其標記為不符合規範。 您可以自訂將裝置標記為不符合規範的時間長度。 該動作無法移除。

您也可以在建立合規性政策或更新現有政策時新增另一個動作。 

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)，然後選取 [裝置相容性]  。
2. 選取 [原則]  ，選擇您的原則，然後選取 [屬性]  。 

    尚未建立原則嗎？ 您可建立 [Android](compliance-policy-create-android.md)、[iOS](compliance-policy-create-ios.md)、[Windows](compliance-policy-create-windows.md) 或其他平台的原則。
  
    > [!NOTE]
    > JAMF 裝置和裝置群組目標的裝置目前無法接收合規性動作。

3. 選取 [不符合規範時所採取的動作]   > [新增]  。
4. 選取您的 [動作]  ： 

    - **傳送電子郵件給終端使用者**：裝置不符合規範時，選擇傳送電子郵件給使用者。 此外： 
    
         - 選擇您先前建立的 [訊息範本] 
         - 選取群組來輸入任何 [其他收件者] 
    
    - **遠端鎖定不符合規範的裝置**：裝置不符合規範時，鎖定裝置。 此動作會強制使用者輸入 PIN 或密碼來解除鎖定裝置。 
    
5. 設定 [排程]  ：輸入不符合規範之後在使用者裝置觸發動作的天數 (0 到 365)。 在此寬限期間之後，您可以強制執行條件式存取原則。 如果您輸入 **0** (零) 天，則條件式存取會**立即**生效。 比方說，如果裝置不符合規範，您可以立即封鎖對公司資源的存取權。

6. 完成後，請選取 [新增]   > [確定]  以儲存變更。

## <a name="next-steps"></a>後續步驟

[監視您的原則](compliance-policy-monitor.md)。
