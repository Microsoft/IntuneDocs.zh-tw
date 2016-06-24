---
# required metadata

title: 使用電子郵件將診斷資料記錄檔傳送給 IT 系統管理員 | Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 05/31/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 85c868e7-8d63-480c-9770-4e99614a5c94

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: arnab
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# 使用電子郵件將診斷資料記錄檔傳送給 IT 系統管理員

當您使用學校或公司應用程式時，或在公司入口網站應用程式中，如果 Android 裝置上出現錯誤，您可以傳送診斷資料記錄檔，以協助您的 IT 系統管理員了解並修正錯誤。 若要在記錄檔中包含所有詳細資料，讓您的 IT 系統管理員更容易找出問題，請開啟 [詳細資訊記錄]。 您可以深入了解[詳細資訊記錄](use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android.md)。

若要啟用詳細資訊記錄：

1.  開啟公司入口網站應用程式。

2.  點選 [功能表] &gt; [設定]。

    > [功能表][!NOTE] 
    > **** 可能是軟體按鈕或硬體按鈕，視您擁有的 Android 裝置類型而定。

3.  在 [診斷資料] 下，點選 [傳送資料]。

    > [!NOTE]
    > **如果您只使用 Android 6.0 或更新版本的裝置**︰當您點選 **[傳送資料]** 時，您會看到此訊息：**是否允許公司入口網站存取裝置上的相片、媒體和檔案？** 

    此訊息會讓人誤解，因為 **Microsoft 永遠不會存取您裝置上的相片、媒體或檔案！** Google 控制訊息文字，Microsoft 無法變更它。  當您允許存取時，只需要允許您的裝置將資料記錄檔寫入裝置的 SD 記憶卡，這樣可讓您使用 USB 纜線移動這些記錄檔。

    如果您拒絕存取，則下次點選 [傳送資料] 時會再次出現此訊息，但點選 [不要再詢問] 核取方塊，即可關閉未來訊息。  如果您稍後決定允許存取，請移至 [設定] &gt; [應用程式] &gt; [公司入口網站] &gt; [權限] &gt; [儲存體]，然後開啟權限。

4.  遵循提示並選擇要用來傳送記錄檔給 IT 系統管理員的電子郵件應用程式。 應用程式會建立預先定址的電子郵件，並附加所有記錄檔。


### 請參閱
[透過 Intune 使用 Android 裝置](using-your-android-device-with-intune.md)

<!--HONumber=Jun16_HO2-->


