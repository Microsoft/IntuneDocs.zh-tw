---
title: "使用設定助理註冊 iOS 裝置 | Microsoft Intune"
description: "透過 Apple Configurator 工具將裝置恢復出廠預設值，並使裝置準備好執行設定助理，來註冊公司擁有的 iOS 裝置。"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46e5b027-4280-4809-b45f-651a6ab6d0cd
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e2daff5dae435df55c866adbf602f554500d50e0
ms.openlocfilehash: 45aa4511945ab4763dc0dc35baefe47887e561bb


---

# 搭配使用 Apple Configurator 與設定助理來註冊 iOS 裝置
Intune 支援使用 Mac 電腦上所執行的 [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) 工具，來註冊公司所擁有的 iOS 裝置。 此處理程序會將裝置重設成出廠預設值，並準備好裝置以讓裝置的新使用者執行已預先安裝公司原則的設定助理。


## 使用 Microsoft Intune 進行 iOS 裝置的設定助理註冊
透過 Apple Configurator，您可以將 iOS 裝置重設成出廠預設值，以準備讓裝置的新使用者進行設定。  這個方法需要您透過 USB 將 iOS 裝置連線到 Mac 電腦，以設定公司註冊，且該方法之前提為假設您使用 Apple Configurator 2.0。 大部分案例需要套用至 iOS 裝置的原則包括**使用者親和性**來啟用 Intune 公司入口網站應用程式。

**必要條件**
* 透過安裝 APN 憑證以[啟用 iOS 註冊](set-up-ios-and-mac-management-with-microsoft-intune.md)
* IOS 裝置的實體存取 - 裝置必須是未經設定 (恢復出廠預設值)，無密碼保護
* 裝置序號 - [如何取得 iOS 序號](https://support.apple.com/en-us/HT204308)
* USB 連接線
* 搭配 [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) 的 Mac 電腦


1.  **建立行動裝置群組** (選用) 如果您的業務需要行動裝置群組來協助管理裝置，請建立這些群組。 [利用 Microsoft Intune 使用群組來管理使用者和裝置](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)。

2.  **建立裝置的設定檔**裝置註冊設定檔會定義套用到裝置群組的設定。 如果您尚未這麼做，請建立使用 Apple Configurator 所註冊之 iOS 裝置的裝置註冊設定檔。

    1.  在 [Microsoft Intune 管理主控台](http://manage.microsoft.com)中，移至 [原則] &gt; [公司裝置註冊]，然後選擇 [新增...]。
    ![建立裝置註冊設定檔](../media/pol-sa-corp-enroll.png)

    2.  輸入裝置設定檔的詳細資料：

        -   **名稱** - 裝置註冊設定檔的名稱。 (使用者看不到)

        -   **描述** - 裝置註冊設定檔的描述。 (使用者看不到)

        -   **詳冊詳細資料** - 指定裝置的註冊方式。

            -   **使用者親和性的提示** - 裝置必須在初始設定期間與使用者建立關聯，之後便可以該使用者身分存取公司資料與電子郵件。 應針對使用者所擁有且需要使用公司入口網站 (如安裝 App) 之受 DEP 管理的裝置設定**使用者親和性**。

            -   **無使用者親和性** - 該裝置不會與使用者建立關聯。 針對執行工作而不需存取本機使用者資料的裝置，請使用此關係。 需要使用者關聯的應用程式 (包含用於安裝企業營運應用程式的公司入口網站應用程式) 將無法運作。

        -   **裝置群組預先指派** - 所有部署此設定檔的裝置，一開始均屬於此群組。 您可以在註冊之後重新指派裝置。

            [!INCLUDE[groups deprecated](../includes/group-deprecation.md)]

          -  **裝置註冊方案** - Apple 裝置註冊方案 (DEP) 不能與設定助理註冊搭配使用。 請確定切換設定為 [關閉]。

    3.  選擇 [儲存設定檔] 以新增設定檔。

3.  **新增要使用設定助理註冊的 iOS 裝置**在 [Microsoft Intune 管理主控台](http://manage.microsoft.com) 中，前往 [群組] &gt; [所有裝置] &gt; [所有公司擁有的裝置] &gt; [所有裝置]，然後選擇 [新增裝置...]。 您可以使用下列兩種方式新增裝置：

    ![新增裝置對話方塊](../media/pol-SA-enroll-iOS-SetupAssistant.png)

    -   **上傳包含序號的 CSV 檔案** - 建立以逗號分隔值的清單，並在其中包含兩個不含標頭的資料行，且限制每個 CSV 檔案最多可有 5000 部裝置或 5 MB。

        |||
        |-|-|
        |&lt;序列 # 1&gt;|&lt;裝置 #1 詳細資料&gt;|
        |&lt;序列 #2&gt;|&lt;裝置 #2 詳細資料&gt;|
        在文字編輯器中檢視此 .csv 檔案時，其外觀大致如下：

        ```
        0000000,PO 1234
        111111111,PO 1234
        ```

    -   **手動新增裝置詳細資料** - 輸入最多五個裝置的序號和裝置詳細資料。

    > [!NOTE]
    > 如果您稍後必須從 Intune 管理中移除公司所擁有的裝置，您可能需要從 [公司預先註冊的裝置] 下的 [依 iOS 序號] 裝置群組中移除裝置序號，以停用裝置註冊。  如果 Intune 在移除序號期間或前後執行嚴重損壞修復程序，則您必須確認該群組中只會出現使用中裝置的序號。

    選擇 **[下一步]**。

4.  **選取要註冊的裝置**確認要註冊的裝置。 無法匯入已註冊或透過其他方法註冊的序號。 選擇 [下一步] 以繼續。

5.  **指派設定檔**從可用的設定檔清單中指定指派給新增裝置的設定檔，檢閱**註冊設定檔詳細資料**，然後選擇 [完成]。 手動新增的裝置可以指派給任何註冊設定檔。

6.  **匯出要部署到 iOS 裝置的設定檔**在 [Microsoft Intune 管理主控台](http://manage.microsoft.com) 中，移至 [原則] &gt; [註冊公司的裝置]，然後選擇要部署到行動裝置的裝置設定檔。 選擇 [匯出...] 。 複製並儲存 [設定檔 URL] 。 您稍後將在 Apple Configurator 中上傳它，以定義 iOS 裝置所使用的 Intune 設定檔。
    若要支援 Apple Configurator 2，則必須編輯 2.0 設定檔 URL。 取代
    ```
    https://manage.microsoft.com/EnrollmentServer/Discovery.svc/iOS/ESProxy?id=
    ```
    與

    ```
    https://appleconfigurator2.manage.microsoft.com/MDMServiceConfig?id=
    ```

   您將使用下列程序中的 Apple Configurator 將這個設定檔 URL 上傳至 Apple DEP 服務，以定義 iOS 裝置所使用的 Intune 設定檔。



7.  **使用 Apple Configurator 準備裝置**iOS 裝置會連線至 Mac 電腦並註冊行動裝置管理。

    1.  在 Mac 電腦上，開啟 [Apple Configurator 2] 在功能表列中，選擇 [Apple Configurator 2]，然後選擇 [喜好設定]。

         > [!WARNING]
         > 在註冊過程，會將裝置重設為原廠設定。 最佳做法是將裝置重設，並開啟其電源。 最佳做法是，當您將裝置連線時，裝置應該會在 **Hello** 畫面。

    2. 在喜好設定窗格中，選取 [伺服器]，然後選擇左窗格下方的 “+” 符號來啟動 MDM 伺服器精靈。 選擇 **[下一步]**。

    3. 輸入上面步驟 #6 中 MDM 伺服器的 [名稱] 和 [註冊 URL]。 對於註冊 URL，輸入從 Intune 匯出的註冊設定檔 URL。 選擇 **[下一步]**。  

       如果您收到指出「伺服器 URL 未經驗證」的警告，您可以放心地忽略該警告。 請選擇 [下一步]以繼續，直到精靈完成為止。

    4.  將 iOS 行動裝置連線到具有 USB 介面卡的 Apple 電腦。

        > [!WARNING]
        > 在註冊過程，會將裝置重設為原廠設定。 最佳做法是將裝置重設，並開啟其電源。 最佳做法是，當您啟動設定助理時，裝置應該會在 [Hello] 畫面上。

    5.  選擇 [準備]。 在 [準備 iOS 裝置] 窗格上，選取 [手動]，然後選擇 [下一步]。

    6. 在 [在 MDM 伺服器中註冊] 窗格上，選取您建立的伺服器名稱，然後選擇 [下一步]。

    7. 在 [監督裝置]窗格上，選取監督層級，然後選擇 [下一步]。

    8. 在 [建立組織] 窗格上，選擇 [組織] 或建立新的組織，然後選擇 [下一步]。

    9. 在 [設定 iOS 設定助理] 窗格中，選擇呈現給使用者的步驟，然後選擇 [準備]。 若出現提示，請驗證以更新信任設定。  

    10. 當 iOS 裝置完成準備時，可以拔除 USB 纜線。  

8.  **發佈裝置**裝置現在已準備好進行公司註冊。 關閉裝置電源，並將它們散發給使用者。 裝置開啟時，會啟動 [設定助理]。



### 請參閱
[準備註冊裝置](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Sep16_HO2-->


