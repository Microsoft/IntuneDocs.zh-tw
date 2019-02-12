---
title: 對 Windows 電腦要求及提供遠端協助
titlesuffix: Microsoft Intune
description: 描述針對作為電腦管理的 Windows 桌上型電腦提供遠端協助所需的終端使用者和 IT 系統管理員步驟，以及遠端啟動電腦的步驟。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c2654491-5144-408a-a45a-644eb91ac1bb
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: af9098a814d102765df1b1a5316cfeeedd4fbc4f
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55838337"
---
# <a name="request-and-provide-remote-assistance-for-windows-pcs"></a>對 Windows 電腦要求及提供遠端協助

[!INCLUDE [classic-portal](includes/classic-portal.md)]

本主題中的資訊僅適用於使用 Intune 軟體用戶端作為電腦所管理的 Windows 桌上型電腦。

Intune 可以使用另行購買的 [TeamViewer](https://www.teamviewer.com) 軟體，讓您為執行 Intune 軟體用戶端的使用者提供遠端協助。 使用者向 Microsoft Intune Center 要求協助時，您會收到警示通知、可以接受要求，然後提供協助。 這項功能會取代 Intune 中的現有 Windows 遠端協助功能。


## <a name="before-you-start"></a>開始之前

請確認您具有下列必要條件，再開始建立並回應遠端協助要求︰

- 您必須[已註冊 TeamViewer 帳戶](https://login.teamviewer.com/LogOn#register)，才能登入 TeamViewer 網站。
- 您想要管理的 Windows 電腦必須[由 Windows 軟體用戶端所管理](manage-windows-pcs-with-microsoft-intune.md)。
- 可以管理 Intune 所支援的所有 Windows 電腦作業系統。

## <a name="configure-the-teamviewer-connector"></a>設定 TeamViewer 連接器

1. 在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 **[系統管理]**。
2. 在 **[系統管理]** 工作區中，選擇 **[TeamViewer]**。
3. 在 **[TeamViewer]** 頁面的 **[TeamViewer 連接器]** 下，選擇 **[啟用]**。
4. 在 **[啟用 TeamViewer]** 對話方塊中，檢視後 **[接受]** 授權條款。 如果您尚未擁有 TeamViewer 授權，請選擇 **[購買 TeamViewer 授權]**。
5. TeamViewer 瀏覽器視窗開啟之後，請使用 TeamViewer 認證登入網站。
6. 在 TeamViewer 網站上，閱讀後接受允許 Intune 使用 TeamViewer 連接的選項。
7. 在 Intune 主控台中，確認 **[TeamViewer 連接器]** 項目顯示為 **[啟用]**。


## <a name="open-a-remote-assistance-request-end-user"></a>開啟遠端協助要求 (使用者)

1. 在用戶端 Windows 電腦上，開啟 **[Microsoft Intune 中心]**。
2. 在 **[遠端協助]** 下，選擇 **[要求遠端協助]**。
3. 在您核准要求 (如下所示) 之後，會在用戶端上開啟 TeamViewer。 使用者必須接受指出網頁瀏覽器嘗試開啟 TeamViewer 應用程式的任何訊息。
4. 使用者會看到訊息，詢問您是否可以控制他們的電腦。 他們必須接受此訊息才能繼續。
5. 在遠端協助工作階段期間，使用者會看到顯示您已連接的視窗。 如果他們關閉這個視窗，遠端工作階段就會結束。

## <a name="respond-to-a-remote-assistance-request"></a>回應遠端協助要求

1. 使用者提交遠端協助要求時，您可以在 **[警示]** 工作區的 **[監視]** > **[遠端協助]** 下進行檢視。 例如：
   > ![遠端協助要求的螢幕擷取畫面](/intune/media/team-viewer.png)

<br>如果超過 4 小時未回應要求，便會將它移除。
2. 若要接受要求，請選擇 **[核准要求並啟動遠端協助]**。
3. 在 **[新的遠端協助要求擱置中]** 對話方塊中，選擇 **[接受遠端協助要求]**。 如果尚未安裝，TeamViewer 會在電腦上安裝任何必要的應用程式。
4. TeamViewer 接著會通知使用者：您想要控制其電腦。 使用者接受要求之後，TeamViewer 視窗隨即開啟，而您可以控制電腦。

處於遠端協助工作階段時，您可以使用所有可用的 TeamViewer 命令來控制遠端電腦。 如需這些命令的說明，請從 TeamViewer 網站下載[遠端控制手冊](http://www.teamviewer.com/en/support/documents/)。

## <a name="close-the-remote-assistance-session"></a>關閉遠端協助工作階段

從 **[TeamViewer]** 視窗的 **[動作]** 功能表中，選擇 **[結束工作階段]**。

## <a name="remotely-restart-a-windows-pc"></a>從遠端重新啟動 Windows 電腦
當您協助發生問題的使用者時，您偶而便必須從遠端重新啟動他們的電腦。 使用下列步驟從遠端重新啟動 Windows 電腦。

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com/)中，選擇 [群組] &gt; [所有裝置]\(或包含您想要重新啟動之電腦的其他群組)。

2.  選取一或多部電腦，然後選擇 [遠端工作] &gt; [重新啟動電腦]。

3.  若要檢視工作狀態，請選擇頁面右下角的 [遠端工作]。

4.  在 [工作狀態]  對話方塊中，檢閱目前的遠端工作、工作狀態、裝置名稱和任何回報的錯誤。

### <a name="see-also"></a>請參閱

[使用 Intune 軟體用戶端執行的一般 Windows 電腦管理工作](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
