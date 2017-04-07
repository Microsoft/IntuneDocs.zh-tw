---
title: "手動同步您的 Windows 裝置 | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 443c6de7-5187-4dc4-b844-6085a0c659bd
searchScope:
- User help
ROBOTS: 
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: 10c7bc5461c746ab50e83c2ffc590b89efe75e5f
ms.openlocfilehash: e83299392fc516ed2b11248f28341403419d6758
ms.lasthandoff: 03/13/2017


---

# <a name="sync-your-windows-device-manually"></a>手動同步處理您的 Windows 裝置

有時嘗試在 Windows 裝置上安裝應用程式，所花的時間比您以為的長。 如果發生這種情況，您可以嘗試手動同步處理您的 Windows 裝置。 同步處理有助於加速安裝。

> [!Note]
> 如果您使用的網路速度較慢，或同時下載內容的裝置數量較多，安裝應用程式可能需時較長。

下列 Windows 版本可以手動同步處理。 如果您的裝置不幸使用不同版本的 Windows，就無法啟動手動同步處理。

* [同步處理 Windows 10 桌面](#windows-10-desktop)
* [同步處理 Windows 10 Mobile](#windows-10-mobile)
* [同步處理 Windows Phone 8.1](#windows-phone-81)

## <a name="windows-10-desktop"></a>Windows 10 Desktop
有多個版本的 Windows 10，因此有兩組步驟。 若要找出要使用的步驟，請查看螢幕擷取畫面，然後依照您在裝置上看到的步驟。

1. 選擇 [啟動] 按鈕，然後選擇 [設定]。

    ![[啟動] 按鈕](./media/win10pc-sync-1-start-button.png)

2. 在 [設定] 頁面上，選擇 [帳戶]。

    ![選擇 [設定] 頁面上的帳戶](./media/win10pc-sync-2-settings-accounts.png)

3. 查看接下來的兩個畫面，並找出其中看起來像在您裝置上所看到的畫面。 遵循您在裝置上看見的畫面中所顯示的步驟。

    如果您看到這個顯示 [存取公司或學校資源] 的畫面，請遵循[如果看見 [存取公司或學校資源] 時需遵循的步驟](#steps-to-follow-if-you-see-access-work-or-school)中的指示。

    ![如果看見 [存取公司或學校資源] 時需遵循的同步步驟](./media/w10-enroll-rs1-connect-to-work-or-school.png)

    如果您看到這個顯示 [公司存取] 的畫面，請遵循[如果看見 [公司存取] 時需遵循的步驟](#steps-to-follow-if-you-see-work-access)中的步驟。

    ![選擇 [公司存取] 作為帳戶類型](./media/win10pc-sync-3-work-access.png)

### <a name="steps-to-follow-if-you-see-access-work-or-school"></a>如果看見 [存取公司或學校資源] 時需遵循的步驟

1. 在 [帳戶] 頁面上，選擇 [存取公司或學校資源]。

    ![選擇 [存取公司或學校資源]](./media/w10-enroll-rs1-connect-to-work-or-school.png)

2. 選擇工作或學校帳戶。 根據 IT 系統管理員設定項目的方式，您可能會看到兩個帳戶，其與下列所示的範例類似。 其中一個帳戶旁邊會有公事包，另一個帳戶旁邊則會有 Microsoft 標誌。

    - 如果您看到具有公事包的帳戶，請選取它，並尋找其下的 [資訊] 按鈕。
    - 如果您看到具有 Microsoft 標誌的帳戶，請選取該帳戶，並尋找其下的 [資訊] 按鈕。

    ![選擇公事包或 Microsoft 標誌旁邊的帳戶名稱](./media/win10pc-rs1-sync-info-button.png)

3. 選擇 [資訊] 按鈕。 隨即開啟與下面範例類似的對話方塊。

    ![選擇公事包或 Microsoft 標誌旁邊的帳戶名稱](./media/win10pc-rs1-sync-button.png)

4. 選擇 [同步] 按鈕。 您的裝置將會使用 Intune 進行同步處理。

### <a name="steps-to-follow-if-you-see-work-access"></a>如果看見 [公司存取] 時需遵循的步驟

1. 在 [帳戶] 頁面上，選擇 [公司存取]。

    ![選擇 [公司存取] 作為帳戶類型](./media/win10pc-sync-3-work-access.png)

2. 在 [註冊裝置管理] 區段下方，選擇您的公司名稱。

    ![選擇用於裝置管理的公司名稱](./media/win10pc-sync-4-tap-com-name.png)

3. 選擇 [同步] 按鈕。

    ![選擇 [同步] 按鈕](./media/win10pc-sync-5-tap-sync.png)

   按鈕會變成灰色，直到同步完成為止。

   ## <a name="windows-10-mobile"></a>Windows 10 Mobile
   手動同步處理您的 Windows 10 Mobile 裝置來加速緩慢的應用程式安裝：

   1. 移至 [所有應用程式] > [設定] > [帳戶]。

       ![選擇 [設定] 畫面上的帳戶](./media/win10m-sync-1-settings-accounts.png)

   2. 選擇 [公司存取]。

       ![選擇 [公司存取] 作為帳戶類型](./media/win10m-sync-2-work-access.png)

   3. 在 [註冊裝置管理] 下方，選擇您的公司名稱。

       ![選擇用於裝置管理的公司名稱](./media/win10m-sync-3-tap-comp-name.png)

   4. 選擇**同步**圖示。

       ![選擇同步圖示](./media/win10m-sync-4-tap-sync.png)

       「我們正在同步您的帳戶」訊息會顯示在畫面頂端。 [同步] 按鈕會呈現灰色，直到您的裝置完成同步為止。

## <a name="windows-phone-81"></a>Windows Phone 8.1
手動同步處理您的 Windows Phone 8.1 裝置來加速緩慢的應用程式安裝：

1. 移至 [所有應用程式] > [設定] > [工作場所]。

    ![設定清單](./media/wp81-1-sync-settings-workplace.png)

2. 選擇您的公司名稱。

    ![選擇工作場所帳戶的公司名稱](./media/wp81-2-sync-tap-compname.png)

3. 選擇**同步**圖示。

    ![選擇同步圖示](./media/wp81-3-sync-tap-sync-button.png)

   「我們正在同步您的帳戶」訊息會顯示在畫面頂端，直到您的裝置完成同步為止。

是否仍需要協助？ 請連絡 IT 系統管理員。 如需連絡資訊，請查看[公司入口網站](http://portal.manage.microsoft.com)。

