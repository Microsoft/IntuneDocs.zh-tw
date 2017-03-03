---
title: "設定 Android for Work  | Microsoft Docs"
description: "使用 Microsoft Intune 來啟用 Android for Work 裝置的行動裝置管理 (MDM)。"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b2fdcea9-9ad7-4d73-88e2-854b7a774bb2
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 31e28514ab4bdb0f5af261a1f7c87633ca0bd4a6
ms.openlocfilehash: 24ab39a92d69e92e1c202005fcd783018c4d4621


---

# <a name="enable-enrollment-of-android-for-work-devices"></a>啟用 Android for Work 裝置的註冊

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

若要啟用 Android for Work 裝置的管理，您必須將 Android for Work 繫結新增至 Intune。 若要註冊支援 Android for Work 但先前註冊為一般 Android 裝置的裝置，必須將裝置取消註冊，再重新註冊。

## <a name="add-android-for-work-binding-for-intune"></a>新增 Intune 的 Android for Work 繫結

1. **設定 Intune**<br>
如果尚未這麼做，請將[行動裝置管理授權單位](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-8#enable-device-enrollment)設定為 **Microsoft Intune** 並設定 MDM，為行動裝置管理做好準備。

2. **設定 Android for Work 繫結**<br>
    以 Intune 系統管理使用者身分開啟 [Microsoft Intune 管理主控台](http://manage.microsoft.com)，移至 [管理]**** &gt; [行動裝置管理]**** &gt; [Android for Work]****，然後按一下 [設定]**** 開啟 Google Play 的 Android for Work 網站。 這會在瀏覽器中以新的索引標籤開啟。

3. **登入 Google**<br>
   在 Google 的登入頁面上，輸入要與此租用戶之所有 Android for Work 管理工作相關聯的 Google 帳戶。 這可能是管理 Intune 之所有系統管理員所共用的 Google 帳戶。 這是您的組織在 Play for Work 主控台中管理及發行應用程式所使用的 Google 帳戶。

4. **提供組織詳細資料**<br>
   提供您的公司名稱作為**組織名稱**。 針對**企業行動管理 (EMM) 提供者**，應該顯示 *Microsoft Intune*。 同意 Android for Work 合約，然後按一下 [確認]。 您的要求將會被處理。

## <a name="specify-android-for-work-enrollment-settings"></a>指定 Android for Work 註冊設定
   只有特定 Android 裝置才支援 Android for Work。 請參閱 Google 的[使用 Android for Work 的必備條件](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012 style="target=new_window")。  支援 Android for Work 的所有裝置也會支援傳統 Android 管理。  Intune 可讓您指定應該如何管理支援 Android for Work 的裝置：

   - **將所有裝置當做 Android 來管理** - (已停用) 所有 Android 裝置 (包括支援 Android for Work 的裝置) 將會註冊為傳統 Android 裝置。
   - **將支援的裝置當做 Android for Work 來管理** - (已啟用) 所有支援 Android for Work 的裝置都會註冊為 Android for Work 裝置。 不支援 Android for Work 的任何 Android 裝置會註冊為傳統 Android 裝置。
   - **只為這些使用者群組中的使用者將支援的裝置當做 Android for Work 來管理** - (測試中) 可讓您將 Android for Work 管理的目標設為有限的一組使用者。 只有註冊支援 Android for Work 之裝置的所選群組成員，才能註冊為 Android for Work 裝置。 所有其他成員則會註冊為 Android 裝置。

## <a name="next-steps-for-android-for-work"></a>Android for Work 的後續步驟
設定 Android for Work 繫結和設定之後，您可以執行下列動作進行管理：
- [部署 Android for Work 應用程式](android-for-work-apps.md)
- [新增 Android for Work 設定原則](android-for-work-policy-settings-in-microsoft-intune.md)

## <a name="unbinding-your-android-for-work-administrative-account"></a>解除 Android for Work 系統管理帳戶繫結

您可以關閉 Android for Work 註冊和管理。 按一下 Intune 管理主控台中的 [解除繫結] 將所有註冊的 Android for Work 裝置取消註冊，並移除 Android for Work 帳戶與 Intune 之間的關聯性。

### <a name="how-to-unbind-an-android-for-work-account"></a>如何解除 Android for Work 帳戶繫結

1. **解除 Android for Work 繫結**<br>
    以系統管理使用者身分開啟 [Microsoft Intune 管理主控台](http://manage.microsoft.com)，移至 [管理]**** &gt; [行動裝置管理]**** &gt; [Android for Work]****，然後按一下 [解除繫結]****。

2. **同意刪除 Android for Work 繫結**<br>
  按一下 [是] 刪除繫結，並從 Intune 取消註冊所有 Android for Work 裝置。



<!--HONumber=Feb17_HO1-->


