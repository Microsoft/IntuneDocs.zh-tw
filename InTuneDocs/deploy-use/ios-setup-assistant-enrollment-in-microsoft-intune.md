---
title: "使用設定助理註冊 iOS 裝置 | Microsoft Intune"
description: "透過 Apple Configurator 工具將裝置重設為原廠設定，並使裝置準備好執行設定助理，來註冊屬公司擁有的 iOS 裝置。"
keywords: 
author: staciebarker
ms.author: stabar
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
ms.sourcegitcommit: 9d44a6494bed0758b9768045bd204ea0eb481636
ms.openlocfilehash: ea6a4732e747dccf9c42732c06bd1b8cdf20e91f


---

# <a name="enroll-ios-devices-with-apple-configurator-by-using-setup-assistant"></a>搭配使用 Apple Configurator 與設定助理來註冊 iOS 裝置
Intune 支援使用 Mac 電腦上所執行的 [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017)，來註冊屬公司擁有的 iOS 裝置。 此處理程序會將裝置重設為原廠設定，並使裝置準備好執行設定助理，以便為裝置的新使用者安裝公司的原則。

## <a name="setup-assistant-enrollment-for-ios-devices-with-microsoft-intune"></a>使用 Microsoft Intune 進行 iOS 裝置的設定助理註冊
您可以使用 Apple Configurator，將 iOS 裝置重設為原廠設定，並準備好裝置以讓裝置的新使用者進行設定。 這個方法需要您透過 USB 將 iOS 裝置連線到 Mac 電腦，以設定公司註冊，且該方法之前提為假設您使用 Apple Configurator 2.0。 大部分案例需要套用至 iOS 裝置的原則包括**使用者親和性**來啟用 Intune 公司入口網站應用程式。

**先決條件**
* 透過安裝 APN 憑證以[啟用 iOS 註冊](set-up-ios-and-mac-management-with-microsoft-intune.md)
* IOS 裝置的實體存取&mdash;裝置必須重設為無密碼保護的原廠設定
* 裝置序號&mdash;請參閱[如何取得 iOS 序號](https://support.apple.com/en-us/HT204308)
* USB 連接線
* 搭配 [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) 的 Mac 電腦


1.  **建立行動裝置群組** (選用)。
    如果您的業務需要行動裝置群組來協助管理裝置，請建立這些群組。 如需詳細資訊，請參閱[利用 Microsoft Intune，使用群組管理使用者和裝置](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)。

2.  **建立裝置的設定檔**。
    裝置註冊設定檔會定義套用至裝置群組的設定。 下列步驟示範如何針對使用 Apple Configurator 註冊的 iOS 裝置，建立裝置註冊設定檔。

    1.  在 [Microsoft Intune 管理主控台](http://manage.microsoft.com)中，移至 [原則] &gt; [公司裝置註冊]，然後選擇 [新增]。
    ![建立裝置註冊設定檔](../media/pol-sa-corp-enroll.png)

    2.  輸入裝置設定檔的詳細資料：

        -   **名稱**&mdash;裝置註冊設定檔的名稱 (使用者看不到)。

        -   **描述**&mdash;裝置註冊設定檔的描述 (使用者看不到)。

        -   **詳冊詳細資料**&mdash;指定裝置的註冊方式。

            -   **提示輸入使用者親和性**&mdash;裝置必須在初始設定期間與使用者建立關聯，之後便可以存取公司資料與電子郵件。 如果受 DEP 管理的裝置是屬於使用者，且裝置必須使用公司入口網站執行安裝應用程式等服務，則必須為此裝置設定 [使用者親和性]。

            -   **無使用者親和性**&mdash;該裝置不會與使用者建立關聯。 針對執行工作而不需存取本機使用者資料的裝置，請使用此關係。 需要使用者關聯的應用程式 (包含用於安裝企業營運應用程式的公司入口網站應用程式) 將無法運作。

        -   **裝置群組預先指派**&mdash;所有使用此設定檔部署的裝置，一開始均屬於此群組。 您可以在註冊之後重新指派裝置。

            [!INCLUDE[groups deprecated](../includes/group-deprecation.md)]

        -  **裝置註冊方案**&mdash;Apple 裝置註冊方案 (DEP) 不能與設定助理註冊搭配使用。 請確定切換設定為 [關閉]。

    3.  選擇 [儲存設定檔] 以新增設定檔。

3.  **新增要使用設定助理註冊的 iOS 裝置**。
    在 [Microsoft Intune 管理主控台](http://manage.microsoft.com)中，移至 [群組] &gt; [所有裝置] &gt; [所有屬公司擁有的裝置] &gt; [所有裝置]，然後選擇 [新增裝置]。 您可以使用下列兩種方式新增裝置：

    ![新增裝置對話方塊](../media/pol-SA-enroll-iOS-SetupAssistant.png)

    -   **上傳內含序號的 CSV 檔案**&mdash;建立逗號分隔值 (.csv) 清單，並在其中包含兩個不含標頭的資料行，且限制每個 .csv 檔案最多可有 5,000 部裝置或 5 MB。

        |||
        |-|-|
        |&lt;序號 #1&gt;|&lt;裝置 #1 詳細資料&gt;|
        |&lt;序號 #2&gt;|&lt;裝置 #2 詳細資料&gt;|
        在文字編輯器中檢視此 .csv 檔案時，其外觀大致如下：

        ```
        0000000,PO 1234
        111111111,PO 1234
        ```

    -   **手動新增裝置詳細資料**&mdash;輸入最多 15 部裝置的序號和裝置詳細資料。

    > [!NOTE]
    > 如果您稍後必須從 Intune 管理中移除公司所擁有的裝置，您可能需要從 [公司預先註冊的裝置] 下的 [依 iOS 序號] 裝置群組中移除裝置序號，以停用裝置註冊。 如果 Intune 在您移除序號期間或前後執行災害復原程序，則您必須確認該群組中只會出現使用中裝置的序號。

    選擇 **[下一步]**。

4.  **選取要註冊的裝置**。
    確認要註冊的裝置。 無法匯入已註冊或透過其他方法註冊的序號。 選擇 [下一步] 以繼續。

5.  **指派設定檔**。
    從可用的設定檔清單中，指定要指派給新增之裝置的設定檔，檢閱 [註冊設定檔詳細資料]，然後選擇 [完成]。 手動新增的裝置可以指派給任何註冊設定檔。

6.  **匯出要部署到 iOS 裝置的設定檔**。
    在 [Microsoft Intune 管理主控台](http://manage.microsoft.com)中，移至 [原則] &gt; [公司裝置註冊]，然後選取要部署到行動裝置的裝置設定檔。 選擇工作列中的 [匯出]。 複製並儲存 [設定檔 URL] 。 您稍後將在 Apple Configurator 中上傳它，以定義 iOS 裝置所使用的 Intune 設定檔。
    若要支援 Apple Configurator 2，則必須編輯 2.0 設定檔 URL。 若要執行這項操作，請將此程式碼：
    ```
    https://manage.microsoft.com/EnrollmentServer/Discovery.svc/iOS/ESProxy?id=
    ```
    取代為以下程式碼：

    ```
    https://appleconfigurator2.manage.microsoft.com/MDMServiceConfig?id=
    ```

   您將使用下列程序中的 Apple Configurator 將這個設定檔 URL 上傳至 Apple DEP 服務，以定義 iOS 裝置所使用的 Intune 設定檔。



7.  **使用 Apple Configurator 準備裝置**。
    iOS 裝置會連線到 Mac 電腦並註冊，以進行行動裝置管理。

    1.  在 Mac 電腦上，開啟 [Apple Configurator 2] 在功能表列中，選擇 [Apple Configurator 2]，然後選擇 [喜好設定]。

         > [!WARNING]
         > 在註冊過程，會將裝置重設為原廠設定。 最佳做法是將裝置重設，並加以啟動。 當您將裝置連線時，裝置應該會在 **Hello** 畫面。

    2. 在 [喜好設定] 窗格中，選取 [伺服器]，然後選擇加號 (+) 來啟動 MDM 伺服器精靈。 選擇 **[下一步]**。

    3. 輸入＜使用 Microsoft Intune 進行 iOS 裝置的設定助理註冊＞下步驟 #6 中 MDM 伺服器的 [名稱] 和 [註冊 URL]。 對於 [註冊 URL]，輸入從 Intune 匯出的註冊設定檔 URL。 選擇 **[下一步]**。  

       您可以放心地忽略指出「伺服器 URL 未經驗證」的警告。 請選擇 [下一步] 以繼續，直到精靈完成為止。

    4.  將 iOS 行動裝置連線到具有 USB 介面卡的 Mac 電腦。

        > [!WARNING]
        > 在註冊過程，會將裝置重設為原廠設定。 最佳做法是將裝置重設，並加以啟動。 當您啟動設定助理時，裝置應該會在 [Hello] 畫面上。

    5.  選擇 [準備]。 在 [Prepare iOS Device] (準備 iOS 裝置) 窗格上，選取 [手動]，然後選擇 [下一步]。

    6. 在 [Enroll in MDM Server] (在 MDM 伺服器中註冊) 窗格上，選取您建立的伺服器名稱，然後選擇 [下一步]。

    7. 在 [Supervise Devices] (監督裝置) 窗格上，選取監督層級，然後選擇 [下一步]。

    8. 在 [Create an Organization] (建立組織) 窗格上，選擇 [組織] 或建立新的組織，然後選擇 [下一步]。

    9. 在 [Configure iOS Setup Assistant] (設定 iOS 設定助理) 窗格上，選擇要呈現給使用者的步驟，然後選擇 [準備]。 若出現提示，請驗證以更新信任設定。  

    10. 當 iOS 裝置完成準備時，請拔除 USB 纜線。  

8.  **散發裝置**。
    裝置現在已準備好進行公司註冊。 關閉裝置，並將它們散發給使用者。 當使用者啟動其裝置時，設定助理將會啟動。



### <a name="see-also"></a>請參閱
[註冊裝置的必要條件](prerequisites-for-enrollment.md)



<!--HONumber=Nov16_HO2-->


