---
title: "直接註冊 iOS 裝置"
description: "透過將公司擁有的 iOS 裝置利用 USB 連線到 Mac 電腦，來使用 Apple Configurator 工具以預先定義的原則直接註冊那些裝置。"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 01/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a692b90c-72ae-47d1-ba9c-67a2e2576cc2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9909e1dd4f9891a2efb47383242ed7765d3f0291
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="directly-enroll-ios-devices-by-using-apple-configurator"></a>使用 Apple Configurator 直接註冊 iOS 裝置

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune 支援使用 Mac 電腦上所執行的 [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) 工具，來註冊公司所擁有的 iOS 裝置。 此程序並不會將裝置重設成出廠預設值，並使用預先定義的原則來註冊裝置。 這個方法適用於**無使用者親和性**的裝置，且需要您透過 USB 將 iOS 裝置連線到 Mac 電腦，以設定公司註冊。

直接註冊 iOS 裝置時，您不需要該裝置的序號即可註冊裝置。 您也可以在 Intune 於註冊階段擷取裝置名稱之前，先命名該裝置以供識別。 直接註冊的裝置不支援公司入口網站應用程式。 本指南假設您在 Mac 電腦上使用 Apple Configurator 2.0。

>[!NOTE]
>此註冊方法不能與[裝置註冊管理員](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)方法一起使用。

1.  如果您尚不具備此條件，請為透過 Apple Configurator 所註冊的 iOS 裝置建立裝置註冊設定檔。 裝置註冊設定檔會定義套用至裝置的設定。

    1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，移至 [原則] &gt; [公司裝置註冊]，然後選擇 [新增]。

        ![建立裝置註冊設定檔頁面](../media/pol-sa-corp-enroll.png)

    2.  輸入裝置設定檔的詳細資料：

        -   **名稱**：裝置註冊設定檔的名稱。 使用者看不到這些內容。

        -   **描述**：裝置註冊設定檔的描述。 使用者看不到這些內容。

        -   **使用者關聯**：指定裝置的註冊方式。 針對 [直接註冊]，選擇 [無使用者親和性]。

        -   **裝置群組預先指派**：含有此設定檔的全部裝置，一開始均屬於此群組。 您可以在註冊之後重新指派裝置。

            [!INCLUDE[groups deprecated](../includes/group-deprecation.md)]

    3.  選擇 [儲存設定檔] 以新增設定檔。

5.  將設定檔匯出為 .mobileconfig 以部署到 iOS 裝置：

    1.   選取您所建立的裝置設定檔。

    2.   選擇工作列中的 [匯出]。

    3.   選擇 [下載設定檔] 並儲存下載的 .mobileconfig 檔案。

6.  將下載的 .mobileconfig 檔案複製到 Mac 電腦，以傳輸檔案。
    > [!NOTE]
    > 註冊設定檔 URL 從匯出時起算兩週內有效。 在兩週之後，您必須匯出新的註冊設定檔 URL，以使用 [設定助理] 註冊 iOS 裝置。

7.  使用 Apple Configurator 準備裝置。 iOS 裝置會連線到 Mac 電腦並註冊，以進行行動裝置管理。

    1.  在 Mac 電腦上，開啟 **Apple Configurator 2.0**。

    2.  將 iOS 裝置以 USB 線連接到 Mac 電腦。 關閉**相片**、**iTunes**，以及在偵測到裝置時，針對裝置開啟的其他應用程式。

    3.  在 Apple Configurator 中，依序選擇已連線的 iOS 裝置和 [新增] 按鈕。 可以新增至裝置的選項會出現在下拉式清單中。 選擇 [設定檔]。

    4.  使用檔案選擇器選取您從 Intune 匯出的 .mobileconfig 檔案，然後選擇 [新增]。 設定檔會新增至裝置。  如果裝置**不受監督**，安裝將會需要在裝置上進行接受。

8.  您已準備好在 iOS 裝置上安裝設定檔。 裝置必須已完成 [設定助理]，而且可供使用。 如果註冊需要應用程式部署，裝置應該要設定 Apple ID，因為應用程式部署將需要您具備登入 App Store 的 Apple ID。

    1.  解除鎖定 iOS 裝置。

    2.  在 [管理設定檔] 的 [安裝設定檔] 對話方塊中，選擇 [安裝]。

    3.  提供**裝置密碼**或 **Apple ID**，如有必要的話。

    4.  接受**警告**，然後選擇 [安裝]。

    5.  接受**遠端警告**，然後選擇 [信任]。

    6.  當 [已安裝設定檔] 方塊確認設定檔為 [已安裝] 時，選擇 [完成]。

9.  在 iOS 裝置上，開啟 [設定]，並移至 [一般] &gt; [裝置管理] &gt; [管理設定檔]。 確認其中有列出設定檔的安裝，並檢查 iOS 原則限制和已安裝的應用程式。 原則限制和應用程式可能需要 10 分鐘的時間才會出現在裝置上。

10.  散發裝置。 iOS 裝置現在已向 Intune 註冊並且受管理。
