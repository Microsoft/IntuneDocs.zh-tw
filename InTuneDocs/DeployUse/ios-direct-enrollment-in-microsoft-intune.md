---
# required metadata

title: 使用 Microsoft Intune 進行 iOS 裝置的直接註冊 | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: a692b90c-72ae-47d1-ba9c-67a2e2576cc2

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用 Apple Configurator 直接註冊 iOS 裝置
Intune 支援使用 Mac 電腦上所執行的 [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) 工具，來註冊公司所擁有的 iOS 裝置。 此處理程序並不會將裝置重設成出廠預設值，並使用預先定義的原則來註冊裝置。 這個方法針對具有無使用者親和性的裝置，且需要您透過 USB 將 iOS 裝置連線到 Mac 電腦，以設定公司註冊。 直接註冊的裝置不支援公司入口網站應用程式。 本指南假設您在 Mac 電腦上使用 Apple Configurator 2.0。

1.  建立裝置的設定檔 裝置註冊設定檔會定義套用至裝置的設定。

    #### 如果您尚未這麼做，請建立使用 Apple Configurator 所註冊之 iOS 裝置的裝置註冊設定檔。

    1.  建立設定檔

        ![在 [Microsoft Intune 管理主控台](http://manage.microsoft.com)中，移至 [原則] &gt; [公司裝置註冊]，然後按一下 [新增]](../media/pol-sa-corp-enroll.png)

    2.  建立裝置註冊設定檔頁面

        -   輸入裝置設定檔的詳細資料： 名稱 - 裝置註冊設定檔的名稱。

        -   使用者看不到這些內容。 描述 - 裝置註冊設定檔的描述。

        -   使用者看不到這些內容。 使用者關係 - 指定裝置的註冊方式。

        -   針對 [直接註冊]，選取 [無使用者親和性] 裝置群組預先指派 - 所有部署此設定檔的裝置，一開始均屬於此群組。

    3.  您可以在註冊之後重新指派裝置。

2.  按一下 [儲存設定檔]  新增設定檔。

    ![新增要使用 Apple Configurator 註冊的 iOS 裝置](../media/pol-SA-enroll-iOS-SetupAssistant.png)

      在 [Microsoft Intune 管理主控台](http://manage.microsoft.com)中，移至 [群組] &gt; [所有裝置] &gt; [公司預先註冊的裝置] &gt; [依 iOS 序號]，然後按一下 [新增裝置]

    -   iOS 設定助理

        |||
        |-|-|
        |&lt;您可以使用下列兩種方式新增裝置：&gt;|&lt;上傳包含序號的 CSV 檔案 - 建立以逗號分隔值的清單，並在其中包含兩個不含標頭的資料行，且限制每個 CSV 檔案最多可有 5000 部裝置或 5 MB。&gt;|
        |&lt;序列 # 1&gt;|&lt;裝置 #1 詳細資料&gt;|
        序列 #2

        ```
        0000000,PO 1234
        111111111,PO 1234
        ```

    -   裝置 #2 詳細資料

    > [!NOTE]
    > 在文字編輯器中檢視此 .csv 檔案時，其外觀大致如下：  手動新增裝置詳細資料 - 輸入最多五個裝置的序號和裝置詳細資料，然後按 [下一步]

3.  如果您稍後必須從 Intune 管理中移除屬公司擁有的裝置，就必須從 Intune 的 [屬公司擁有的裝置] 群組中移除裝置序號，以停用裝置註冊。 如果 Intune 在移除序號期間或前後執行嚴重損壞修復程序，則您必須確認該群組中只會出現使用中裝置的序號。 選取要註冊的裝置

4.  確認要註冊的裝置。 無法匯入已註冊或透過其他方法註冊的序號。

5.  按 [下一步]  以繼續。 指派設定檔 從可用的設定檔清單中，指定要指派給新增之裝置的設定檔，檢閱 [註冊設定檔詳細資料]，然後按一下 [完成]。 手動新增的裝置可以指派給任何註冊設定檔。 選取要部署到 iOS 裝置的設定檔

6.  在 [Microsoft Intune 管理主控台](http://manage.microsoft.com)中，移至 [原則] &gt; [公司裝置註冊]，然後選取要部署到行動裝置的裝置設定檔。
    > [!NOTE]
    > 此設定檔應該是您在先前步驟中指派要部署的相同設定檔。 按一下工作列中的 [匯出]
7.  。

    1.  按一下 [下載設定檔] 並儲存下載的 .mobileconfig 檔案。

    2.  傳送檔案 將下載的 .mobileconfig 檔案複製到 Mac 電腦。

    3.  註冊設定檔 URL 從匯出時起算兩週內有效。 在兩週之後，您必須匯出新的註冊設定檔 URL，以使用 [設定助理] 註冊 iOS 裝置。 使用 Apple Configurator 準備裝置

    4.  iOS 裝置會連線到 Mac 電腦並註冊，以進行行動裝置管理。 在 Mac 電腦上，啟動 Apple Configurator 2.0  將 iOS 裝置以 USB 線連接到 Mac 電腦。

8.  關閉相片、iTunes，以及在偵測到裝置時，針對裝置開啟的其他應用程式。 在 Apple Configurator 中，按一下已連線的 iOS 裝置，然後按一下 [新增] 按鈕。  可以新增至裝置的選項會出現在下拉式清單中。

    ###### 按一下 [設定檔]

    1.  使用檔案選擇器選取您從 Intune 匯出的 .mobileconfig 檔案，然後按一下 [新增]。

    2.  設定檔會新增至裝置。

    3.  如果裝置不受監督，安裝將會需要在裝置上進行接受。

    4.  安裝設定檔

    5.  您已準備好在 iOS 裝置上安裝設定檔。

    6.  裝置必須已完成 [設定助理]，而且可供使用。

9. 如果註冊需要應用程式部署，裝置應該要設定 Apple ID，因為應用程式部署將需要您具備登入 App Store 的 Apple ID。 完成不受監督之 iOS 裝置的設定檔接受

10. 解除鎖定 iOS 裝置。


### 在 [管理設定檔] 的 [安裝設定檔] 對話方塊中，點選 [安裝]
[提供裝置密碼或 Apple ID，如有必要的話。](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=May16_HO2-->


