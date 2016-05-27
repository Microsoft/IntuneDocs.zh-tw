---
# required metadata

title: 使用 Microsoft Intune 進行 iOS 裝置的設定助理註冊 | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 46e5b027-4280-4809-b45f-651a6ab6d0cd

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 搭配使用 Apple Configurator 與設定助理來註冊 iOS 裝置
Intune 支援使用 Mac 電腦上所執行的 [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) 工具，來註冊公司所擁有的 iOS 裝置。 此處理程序會將裝置重設成出廠預設值，並準備好裝置以讓裝置的新使用者執行已預先安裝公司原則的設定助理。


## 使用 Microsoft Intune 進行 iOS 裝置的設定助理註冊
透過 Apple Configurator，您可以將 iOS 裝置重設成出廠預設值，以準備讓裝置的新使用者進行設定。  這個方法需要您透過 USB 將 iOS 裝置連線到 Mac 電腦，以設定公司註冊，且該方法之前提為假設您使用 Apple Configurator 2.0。 大部分案例需要套用至 iOS 裝置的原則包括使用者親和性來啟用 Intune 公司入口網站應用程式。

**必要條件**
* IOS 裝置的實體存取 - 裝置必須是未經設定 (恢復出廠預設值)，無密碼保護
* 裝置序號 - [如何取得 iOS 序號](https://support.apple.com/en-us/HT204308)
* USB 連接線
* 搭配 [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) 的 Mac 電腦


1.  建立行動裝置群組 (選用) 如果您的業務需要行動裝置群組來協助管理裝置，請建立這些群組。

2.  利用 Microsoft Intune，使用群組管理使用者和裝置 建立裝置的設定檔

    ###### 裝置註冊設定檔會定義套用至裝置群組的設定。

    1.  如果您尚未這麼做，請建立使用 Apple Configurator 所註冊之 iOS 裝置的裝置註冊設定檔。

    ![建立設定檔](../media/pol-sa-corp-enroll.png)

    2.  在 [Microsoft Intune 管理主控台](http://manage.microsoft.com)中，移至 [原則] &gt; [屬公司擁有的裝置]，然後按一下 [新增]

        -   建立裝置註冊設定檔 輸入裝置設定檔的詳細資料：

        -   名稱 - 裝置註冊設定檔的名稱。 (使用者看不到)

        -   描述 - 裝置註冊設定檔的描述。

            -   (使用者看不到) 詳冊詳細資料 - 指定裝置的註冊方式。
            提示關聯使用者 - iOS 裝置可以在初始設定期間關聯到使用者，以便之後能夠以該使用者的身分存取公司資料及傳送電子郵件。

                -   在大部分設定助理的情況下，請使用 [提示提供使用者親和性] 此模式支援許多案例：

                -   屬公司擁有的個人裝置 -「選擇您自己的裝置 (CYOD)」。與私人擁有的裝置或個人裝置類似，但是系統管理員具有抹除、重設、管理和取消註冊裝置這類特定權限。 裝置的使用者可以安裝應用程式，並具有其他不受管理原則封鎖的大部分裝置使用權限。 裝置註冊管理員帳戶 - 使用特殊 Intune 系統管理員帳戶來註冊裝置。

            -   它可以做為私人帳戶進行管理，但只有知道註冊管理員認證的使用者才能安裝應用程式，以及抹除、重設、管理和取消註冊裝置。 如需透過共同帳戶註冊許多使用者共用之裝置的詳細資訊，請參閱[使用 Microsoft Intune 中的裝置註冊管理員註冊公司所擁有的裝置](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md) 無使用者親和性 - 裝置沒有使用者。

        -   針對執行工作而不需存取本機使用者資料的裝置，請使用此關係。 需要使用者關係的應用程式會予以停用，或無法運作。

          -  裝置群組預先指派 - 所有部署此設定檔的裝置，一開始均屬於此群組。 您可以在註冊之後重新指派裝置。

    3.  裝置註冊方案 - Apple 裝置註冊方案 (DEP) 不能與設定助理註冊搭配使用。

3.  請確定切換設定為 [關閉] 按一下 [儲存設定檔]  新增設定檔。

    ![新增要使用設定助理註冊的 iOS 裝置](../media/pol-SA-enroll-iOS-SetupAssistant.png)

    -   在 [Microsoft Intune 管理主控台](http://manage.microsoft.com)中，移至 [群組] &gt; [所有裝置] &gt; [所有行動裝置] &gt; [所有屬公司擁有的裝置]，然後按一下 [新增裝置]。

        |||
        |-|-|
        |&lt;您可以使用下列兩種方式新增裝置：&gt;|&lt;新增裝置對話方塊&gt;|
        |&lt;上傳包含序號的 CSV 檔案 - 建立以逗號分隔值的清單，並在其中包含兩個不含標頭的資料行，且限制每個 CSV 檔案最多可有 5000 部裝置或 5 MB。&gt;|&lt;序列 # 1&gt;|
        裝置 #1 詳細資料

        ```
        0000000,PO 1234
        111111111,PO 1234
        ```

    -   序列 #2

    > [!NOTE]
    > 裝置 #2 詳細資料  在文字編輯器中檢視此 .csv 檔案時，其外觀大致如下：

    手動新增裝置詳細資料 - 輸入最多五個裝置的序號和裝置詳細資料。

4.  如果您稍後必須從 Intune 管理中移除屬公司擁有的裝置，就可能需要從 Intune 的 [屬公司擁有的裝置] 群組中移除裝置序號，以停用裝置註冊。 如果 Intune 在移除序號期間或前後執行嚴重損壞修復程序，則您必須確認該群組中只會出現使用中裝置的序號。 然後按 [下一步]

5.  選取要註冊的裝置 確認要註冊的裝置。

6.  無法匯入已註冊或透過其他方法註冊的序號。 按 [下一步]  以繼續。 指派設定檔 從可用的設定檔清單中，指定要指派給新增之裝置的設定檔，檢閱 [註冊設定檔詳細資料]，然後按一下 [完成]。 手動新增的裝置可以指派給任何註冊設定檔。
    匯出要部署到 iOS 裝置的設定檔 在 [Microsoft Intune 管理主控台](http://manage.microsoft.com)中，移至 [原則] &gt; [公司裝置註冊]，然後選取要部署到行動裝置的裝置設定檔。
    ```
    https://manage.microsoft.com/EnrollmentServer/Discovery.svc/iOS/ESProxy?id=
    ```
    按一下工作列中的 [匯出]

    ```
    https://appleconfigurator2.manage.microsoft.com/MDMServiceConfig?id=
    ```

   。

    > [!NOTE]
    > 複製並儲存 [設定檔 URL] 。 您稍後將在 Apple Configurator 中上傳它，以定義 iOS 裝置所使用的 Intune 設定檔。

7.  若要支援 Apple Configurator 2，則必須編輯 2.0 設定檔 URL。

    1.  取代 與

         > [!WARNING]
         > 您將使用下列程序中的 Apple Configurator 將這個設定檔 URL 上傳至 Apple DEP 服務，以定義 iOS 裝置所使用的 Intune 設定檔。 註冊設定檔 URL 從匯出時起算兩週內有效。 在兩週之後，您必須匯出新的註冊設定檔 URL，以使用 [設定助理] 註冊 iOS 裝置。

    2. 使用 Apple Configurator 準備裝置 iOS 裝置會連線到 Mac 電腦並註冊，以進行行動裝置管理。

    3. 在 Mac 電腦上，開啟 [Apple Configurator 2] 在功能表列中，按一下 [Apple Configurator 2]，然後按一下 [喜好設定] 在註冊過程，會將裝置重設為原廠設定。  

       最佳做法是將裝置重設，並開啟其電源。 最佳做法是，當您將裝置連線時，裝置應該會在 Hello 畫面。 在 [喜好設定] 窗格中，選取 [伺服器]，然後按一下左窗格下方的 “+” 符號來啟動 [MDM 伺服器精靈]。

    4.  按 [下一步] 輸入上面步驟 #6 中 MDM 伺服器的 [名稱] 和 [註冊 URL]。 對於註冊 URL，輸入從 Intune 匯出的註冊設定檔 URL。

    5.  按 [下一步]

        > [!WARNING]
        > 如果您收到有關 Apple TV 之信任設定檔需求的警告，則按一下灰色 "X"，即可放心地取消 [信任設定檔] 選項。 您也可以放心地忽略任何錨點憑證警告。 若要繼續，請按 [下一步]，直到完成精靈。

    6.  在 [伺服器 ] 窗格上，按一下新伺服器設定檔旁邊的 [編輯]。 請確定註冊 URL 完全符合從 Intune 匯出的 URL。

    7. 如果不同，請重新輸入原始 URL，並「儲存」從 Intune 匯出的註冊設定檔。

    8. 將 iOS 行動裝置連線到具有 USB 介面卡的 Apple 電腦。

    9. 在註冊過程，會將裝置重設為原廠設定。

    10. 最佳做法是將裝置重設，並開啟其電源。 最佳做法是，當您啟動設定助理時，裝置應該會在 [Hello] 畫面上。  

    11. 按一下 [準備] 。  

8.  在 [準備 iOS 裝置] 窗格上，選取 [手動]，然後按 [下一步] 在 [在 MDM 伺服器中註冊] 窗格上，選取您建立的伺服器名稱，然後按 [下一步] 在 [監督裝置] 窗格上，選取監督層級，然後按 [下一步]



### 在 [建立組織] 窗格上，選擇 [組織] 或建立新的組織，然後按 [下一步]
[在 [設定 iOS 設定助理] 窗格中，選擇呈現給使用者的步驟，然後按一下 [準備]。](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=May16_HO2-->


