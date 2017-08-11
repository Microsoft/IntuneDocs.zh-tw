---
title: "在 Intune 中註冊 Android 裝置"
titleSuffix: Intune on Azure
description: "了解如何在 Intune 中註冊 Android 裝置。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 183e60af4d6174c18fc3883f2cdd9827505d2aba
ms.sourcegitcommit: 2ee1e8248814d74cef80b609a8e43f59fa0b2618
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2017
---
# <a name="enroll-android-devices"></a>註冊 Android 裝置

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

身為 Intune 系統管理員，Intune 可讓您管理 Android 裝置，包括 Samsung Knox Standard 裝置。 您也可以管理 [Android for Work 裝置](#enable-enrollment-of-android-for-work-devices)上的工作設定檔。

Intune 的多使用者管理支援執行 Samsung KNOX Standard 的裝置。 這代表使用者可以使用其 Azure AD 認證登入和登出裝置，而且該裝置不論是否正在使用，都會集中管理。 當終端使用者登入時，他們可以存取應用程式，此外也可以將任何原則套用到這些應用程式。 當使用者登出時，會清除所有應用程式資料。

## <a name="prerequisite"></a>必要條件

您必須將 MDM 授權單位設定為 **Microsoft Intune**準備管理行動裝置。 請參閱[設定 MDM 授權單](mdm-authority-set.md)以取得相關指示。 此項目只會設定一次，也就是第一次為行動裝置管理設定 Intune 之時。

## <a name="set-up-android-enrollment"></a>設定 Android 註冊

根據預設，Intune 允許註冊 Android 和 Samsung Knox Standard 裝置。

若要封鎖 Android 裝置，或者僅封鎖註冊個人擁有的 Android 裝置，請參閱[Set device type restrictions](enrollment-restrictions-set.md) (設定裝置類型限制)。

若要啟用裝置管理，您的使用者必須註冊其裝置，方法是下載從 Google Play 取得的 Intune 公司入口網站應用程式，然後開啟應用程式，並遵循提示進行註冊。 當 Android 裝置受到管理之後，您可以[指派合規性原則](compliance-policy-create-android.md)、[管理應用程式](app-management.md)等。

## <a name="enable-enrollment-of-android-for-work-devices"></a>啟用 Android for Work 裝置的註冊

若要在[支援 Android for Work (英文)](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012) 的裝置上啟用工作設定檔管理，您必須將 Android for Work 繫結新增至 Intune。 若要註冊支援 Android for Work 但先前註冊為一般 Android 裝置的裝置，必須將裝置取消註冊，再重新註冊。

## <a name="add-android-for-work-binding-for-intune"></a>新增 Intune 的 Android for Work 繫結

1. **設定 Intune MDM**<br>
如果尚未這麼做，請將[行動裝置管理授權單位](mdm-authority-set.md)設定為 **Microsoft Intune**，以針對行動裝置管理做準備。
2. **設定 Android for Work 繫結**<br>
    以 Intune 系統管理員的身分，在 Azure 入口網站中選擇 [更多服務] > [監視 + 管理] > [Intune]。

    1. 在 [Intune] 刀鋒視窗上，選擇 [裝置註冊] > [Android for Work 註冊]，然後按一下 [設定] 以開啟 Google Play 的 Android for Work 網站。 這會在瀏覽器中以新的索引標籤開啟。
  ![顯示設定 Android for Work 繫結之連結的螢幕擷取畫面](./media/android-work-bind.png)

    2. **登入 Google**<br>
   在 Google 的登入頁面上，輸入要與此租用戶之所有 Android for Work 管理工作相關聯的 Google 帳戶。 這是您組織的 IT 系統管理員用來在 Play for Work 主控台中管理及發行應用程式所共用的 Google 帳戶。

    3. **提供組織詳細資料**<br>
   提供您的公司名稱作為**組織名稱**。 針對**企業行動管理 (EMM) 提供者**，應該顯示 *Microsoft Intune*。 同意 Android for Work 合約，然後按一下 [確認]。 您的要求將會被處理。

## <a name="specify-android-for-work-enrollment-settings"></a>指定 Android for Work 註冊設定
   只有特定 Android 裝置才支援 Android for Work。 請參閱 Google 的[使用 Android for Work 的必備條件](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012 style="target=new_window")。 支援 Android for Work 的所有裝置也會支援傳統 Android 管理。  Intune 可讓您指定應該如何管理支援 Android for Work 的裝置：

   - **將所有裝置作為 Android 管理** - 所有 Android 裝置 (包括支援 Android for Work 的裝置) 將會註冊為傳統 Android 裝置。
   - **將受支援的裝置作為 Android for Work 管理** - 所有支援 Android for Work 的裝置都會註冊為 Android for Work 裝置。 不支援 Android for Work 的任何 Android 裝置會註冊為傳統 Android 裝置。
   - **只為這些使用者群組中的使用者將支援的裝置當做 Android for Work 來管理** - 可讓您將 Android for Work 管理的目標設為有限的一組使用者。 只有註冊支援 Android for Work 之裝置的所選群組成員，才能註冊為 Android for Work 裝置。 所有其他成員則會註冊為 Android 裝置。 這在 Android for Work 試驗期間會很有用。

<!--  ## Next steps for Android for Work
After configuring the Android for Work binding and settings, you can do the following:
- [Deploy Android for Work apps](android-for-work-apps.md)
- [Add Android for Work configuration policies](android-for-work-policy-settings-in-microsoft-intune.md)  -->

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>告知使用者如何註冊其裝置才可存取公司資源

您需要告訴使用者移至 Google Play 來下載 Intune 公司入口網站應用程式，然後開啟應用程式，並遵循提示以註冊其裝置。 應用程式會引導使用者進行註冊程序，即說明使用者能獲得什麼，以及 IT 系統管理員可以和無法在其裝置上看到什麼。

您也可以將線上註冊步驟的連結傳送給他們︰[在 Intune 註冊 Android 裝置](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android)。

如需其他使用者工作的資訊，請參閱下列文章：

- [使用 Microsoft Intune 之使用者體驗的相關資源](end-user-educate.md)
- [在 Intune 上使用您的 Android 裝置](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

## <a name="unbinding-your-android-for-work-administrative-account"></a>解除 Android for Work 系統管理帳戶繫結

您可以關閉 Android for Work 註冊和管理。 按一下 Intune 管理主控台中的 [解除繫結] 將所有註冊的 Android for Work 裝置取消註冊，並移除 Android for Work 帳戶與 Intune 之間的關聯性。

### <a name="how-to-unbind-an-android-for-work-account"></a>如何解除 Android for Work 帳戶繫結

1. **解除 Android for Work 繫結**<br>
    以 Intune 系統管理員的身分，在 Azure 入口網站中選擇 [更多服務] > [監視 + 管理] > [Intune]。  在 [Intune] 刀鋒視窗上，選擇 [裝置註冊] > [Android for Work 註冊]，然後按一下 [解除繫結]。

2. **同意刪除 Android for Work 繫結**<br>
  按一下 [是] 刪除繫結，並從 Intune 取消註冊所有 Android for Work 裝置。
