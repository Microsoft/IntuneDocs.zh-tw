---
title: "在 Intune 中註冊 Android 裝置"
titlesuffix: Microsoft Intune
description: "了解如何在 Intune 中註冊 Android 裝置。"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7e65a32843cec48268c7e205ab4a064038c28415
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="enroll-android-devices"></a>註冊 Android 裝置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

身為 Intune 系統管理員，您可以管理 Android 裝置，包括 Samsung Knox Standard 裝置。 您也可以管理 [Android for Work 裝置](#enable-enrollment-of-android-for-work-devices)工作設定檔。

Intune 的多使用者管理支援執行 Samsung Knox Standard 的裝置。 這表示使用者可以利用他們的 Azure AD 認證登入和登出裝置。 裝置不論是否處於使用狀態，都是集中管理。 當使用者登入時，他們可以存取應用程式，此外也可以將任何原則套用到這些應用程式。 當使用者登出時，會清除所有應用程式資料。

## <a name="prerequisite"></a>必要條件

若要準備管理行動裝置，您必須將行動裝置管理 (MDM) 授權單位設定為 **Microsoft Intune**。 請參閱[設定 MDM 授權單](mdm-authority-set.md)以取得相關指示。 此項目只會設定一次，也就是第一次為行動裝置管理設定 Intune 之時。

## <a name="set-up-android-enrollment"></a>設定 Android 註冊

根據預設，Intune 允許註冊 Android 和 Samsung Knox Standard 裝置。

若要封鎖 Android 裝置，或者僅封鎖註冊個人擁有的 Android 裝置，請參閱[Set device type restrictions](enrollment-restrictions-set.md) (設定裝置類型限制)。

若要啟用裝置管理，您的使用者必須註冊其裝置，方法是下載從 Google Play 取得的 Intune 公司入口網站應用程式，然後開啟應用程式並遵循提示。 當 Android 裝置受到管理之後，您可以[指派合規性原則](compliance-policy-create-android.md)、[管理應用程式](app-management.md)等。

## <a name="enable-enrollment-of-android-for-work-devices"></a>啟用 Android for Work 裝置的註冊

若要在[支援 Android for Work (英文)](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012) 的裝置上啟用工作設定檔管理，您必須將 Android for Work 繫結新增至 Intune。 若要在 Android for Work 註冊裝置，但先前已將那些裝置註冊為一般 Android 裝置，您必須取消註冊裝置，然後重新註冊。

如果要使用[裝置註冊管理員](device-enrollment-manager-enroll.md)帳戶註冊 Android for Work 裝置，每個帳戶只能註冊 10 部裝置。

## <a name="add-android-for-work-binding-for-intune"></a>新增 Intune 的 Android for Work 繫結

> [!NOTE]
> 因為 Google 和 Microsoft 網域之間的互動，這個步驟可能需要調整瀏覽器設定，才能順利完成。  請確定 "portal.azure.com" 和 "play.google.com" 位於您瀏覽器中相同的安全性區域。

1. **設定 Intune MDM**<br>
如果尚未這麼做，請將[行動裝置管理授權單位](mdm-authority-set.md)設定為 **Microsoft Intune**，以針對行動裝置管理做準備。
2. **設定 Android for Work 繫結**<br>
    以 Intune 系統管理員的身分，在 [Azure 入口網站](https://portal.azure.com)中選擇 [所有服務] > [監視 + 管理] > [Intune]。

   a. 在 [Intune] 窗格上，選擇 [裝置註冊] > [Android for Work 註冊]，然後選擇 [受控 Google Play – 設定] 以開啟 Google Play 的 Android for Work 網站。 在瀏覽器的新索引標籤中開啟網站。
   ![Android for Work 註冊畫面](./media/android-work-bind.png)

   b。 **登入 Google**<br>
   在 Google 的登入頁面上，輸入要與此租用戶之所有 Android for Work 管理工作相關聯的 Google 帳戶。 這是貴公司 IT 管理員共用的 Google 帳戶，以在 Play for Work 主控台中管理及發行應用程式。 您可以使用現有的 Google 帳戶或建立新帳戶。  您選擇的帳戶絕不能與 G 套件網域建立關聯性。

   c. **提供組織詳細資料**<br>
   提供您的公司名稱作為**組織名稱**。 針對**企業行動管理 (EMM) 提供者**，應該顯示 **Microsoft Intune**。 同意 Android for Work 合約，然後選擇 [確認]。 您的要求將會被處理。

## <a name="specify-android-for-work-enrollment-settings"></a>指定 Android for Work 註冊設定
只有特定 Android 裝置才支援 Android for Work。 請參閱 Google 的[使用 Android for Work 的必備條件](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22)。 支援 Android for Work 的所有裝置也會支援傳統 Android 管理。 Intune 可讓您指定應如何從[註冊限制](enrollment-restrictions-set.md)管理支援 Android for Work 的裝置。

- **封鎖 (預設設定)**：所有 Android 裝置 (包括支援 Android for Work 的裝置) 都會註冊為傳統 Android 裝置。
- **允許**：所有支援 Android for Work 的裝置都會註冊為 Android for Work 裝置。 不支援 Android for Work 的任何 Android 裝置會註冊為傳統 Android 裝置。

## <a name="approve-the-company-portal-app-in-the-managed-google-play-store"></a>在受控的 Google Play 商店中核准公司入口網站應用程式
您必須在受控的 Google Play 商店中核准 Android 公司入口網站應用程式，以確保它會接收自動的應用程式更新。 如果不核准，公司入口網站最後會過時，不能接收 Microsoft 發行的重要 Bug) 修正或新功能。

請遵循下列步驟核准 Intune 公司入口網站：

1.  在[受控 Google Play 商店](https://play.google.com/work/apps/details?id=com.microsoft.windowsintune.companyportal)中瀏覽到公司入口網站應用程式。
2.  以設定 Android for Work 繫結的相同 Google 帳戶，登入受控的 Google Play 商店。
3.  按一下 [核准]隨即開啟一個新的對話方塊。
4.  檢閱此對話方塊中的權限，然後按一下 [核准]。 您需要允許這些權限，才能讓公司入口網站應用程式管理裝置上的工作設定檔。
5.  選取 [Keep approved when app requests new permissions] (當應用程式要求新權限時，保留已核准的權限)，然後按一下 [儲存]。

<!--  ## Next steps for Android for Work
After configuring the Android for Work binding and settings, you can do the following:
- [Deploy Android for Work apps](android-for-work-apps.md)
- [Add Android for Work configuration policies](android-for-work-policy-settings-in-microsoft-intune.md)  -->

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>告知使用者如何註冊其裝置才可存取公司資源

通知您的使用者移至 Google Play 來下載 Intune 公司入口網站應用程式，然後開啟應用程式，並遵循提示以註冊其裝置。 應用程式會引導使用者進行註冊程序，即說明使用者能獲得什麼，以及 IT 系統管理員可以和無法在其裝置上看到什麼。

您也可以將線上註冊步驟的連結傳送給他們︰[在 Intune 註冊 Android 裝置](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android)。

如需其他使用者工作的資訊，請參閱下列文章：

- [使用 Microsoft Intune 之使用者體驗的相關資源](end-user-educate.md)
- [搭配 Intune 使用您的 Android 裝置](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

## <a name="unbind-your-android-for-work-administrative-account"></a>解除 Android for Work 系統管理帳戶繫結

您可以關閉 Android for Work 註冊和管理。 在 Intune 管理主控台選擇 [解除繫結]，移除所有已註冊 Android for Work 裝置的註冊。 它也會移除 Android for Work 帳戶與 Intune 之間的關聯性。

### <a name="to-unbind-an-android-for-work-account"></a>解除 Android for Work 帳戶的繫結

1. **解除 Android for Work 繫結**<br>
    以 Intune 系統管理員的身分，在 [Azure 入口網站](https://portal.azure.com)中選擇 [所有服務] > [監視 + 管理] > [Intune]。  在 [Intune] 窗格上，選擇 [裝置註冊] > [Android for Work 註冊]，然後選擇 [解除繫結]。

2. **同意刪除 Android for Work 繫結**<br>
  選擇 [是] 刪除繫結，並從 Intune 取消註冊所有 Android for Work 裝置。
