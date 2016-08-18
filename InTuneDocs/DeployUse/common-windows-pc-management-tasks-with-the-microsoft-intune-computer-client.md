---
title: "一般 Windows 電腦管理工作 | Microsoft Intune"
description: "請檢閱本主題中的工作，以了解如何管理執行 Intune 電腦用戶端軟體的電腦。"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: eb912c73-54d2-4d78-ac34-3cbe825804c7
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: dcfa3af374a7e64e931508e1a8022bf8a50c71a7
ms.openlocfilehash: 93d5718fcd9949945180434b0f89eea96e92bbc6


---

# 使用 Microsoft Intune 電腦用戶端的一般 Windows 電腦管理工作
請檢閱本主題中的工作，以了解如何管理執行 Intune 電腦用戶端軟體的電腦。 如果您尚未在電腦上安裝用戶端，請參閱[使用 Microsoft Intune 安裝 Windows 電腦用戶端](install-the-windows-pc-client-with-microsoft-intune.md)。


## 使用原則來簡化電腦管理
### 管理 Windows 防火牆
原則可簡化受管理電腦上的 Windows 防火牆設定管理。 如需詳細資訊，請參閱[在 Microsoft Intune 中使用 Windows 防火牆原則協助保護 Windows 電腦](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md)。

### 管理 Microsoft Intune Center
Microsoft Intune Center 可讓使用者︰

-   從公司入口網站取得應用程式。

-   檢查更新。

-   管理 Microsoft Intune Endpoint Protection。

-  要求遠端協助。

Microsoft Intune Center 會安裝在所有受管理電腦上。 您可以在 Intune 中進行下列設定，而使用者會在 Microsoft Intune Center 中看到這些設定：

|原則設定|詳細資料|
|------------------|--------------------|
|**Name**|管理電腦的系統管理員名稱。<br /><br />最大長度：40 個字元|
|**電話號碼**|管理電腦之系統管理員的電話號碼。<br /><br />最大長度：20 個字元|
|**電子郵件地址**|管理電腦之系統管理員的電子郵件地址。<br /><br />最大長度：40 個字元|
|**網站名稱**|使用者支援網站的名稱。<br /><br />最大長度：40 個字元|
|**網站 URL**|您的支援網站的 URL。<br /><br />最大長度：150 個字元|
|**附註**|使用者看到的附註。<br /><br />最大長度：120 個字元|

### 管理軟體更新設定
請使用原則來設定受管理電腦用來檢查和下載 Microsoft 和協力廠商提供之軟體更新的設定。 如需詳細資訊，請參閱[在 Microsoft Intune 中使用軟體更新讓 Windows 電腦維持最新狀態](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)。

### 管理 Endpoint Protection 設定
請使用原則來設定您隨後部署到受管理電腦的 Endpoint Protection 設定。 這包括掃描排程、偵測到惡意程式碼時採取的動作以及更多設定。 如需詳細資訊，請參閱[使用 Microsoft Intune 的 Endpoint Protection 協助保護 Windows 電腦](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)。

## 檢視硬體與軟體清查
Intune 會收集受管理電腦的硬體和軟體詳細資訊。 請使用下列程序中的資訊，瞭解如何建立：

-   列出電腦硬體功能相關資訊的報表。

-   列出每部電腦所安裝軟體的報表。

-   如何重新整理電腦清查以確保報表中的資料是最新的。

### 若要顯示電腦的相關資訊

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com/)中，選擇 [報表] &gt; [電腦清查報表]。

2.  在 [建立新報表]  頁面上，接受預設值或進行自訂，以篩選報表將傳回的結果。 例如，您可以選擇只讓執行 Windows 8.1 的電腦顯示在報表中。

3.  選擇 [檢視報表]，在新視窗中開啟 [電腦清查報表]。

    您可以選取每個欄標題，依任何一欄排序報表，例如 [名稱]、[底座類型] 或 [製造商]。

### 若要顯示電腦上安裝的軟體

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com/)中，選擇 [報表] &gt; [軟體清查報表]。

2.  在 [建立新報表]  頁面上，接受預設值或進行自訂，以篩選報表將傳回的結果。 例如，您可以選擇只讓 Microsoft 發佈的軟體顯示在報表中。

3.  選擇 [檢視報表]，在新視窗中開啟 [軟體清查報表]。

    您可以選擇每個欄標題，依任何一欄排序報表，例如 [名稱]、[發行者] 或 [類別]。 您可以選擇清單項目旁的方向箭頭，展開清單中的更新來顯示更多詳細資訊 (例如安裝軟體的電腦)。

### 若要重新整理電腦清查以確保它是最新的

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com/)中，選擇 [群組] &gt; [所有裝置] (或包含您想要重新整理清查之電腦的其他群組)。

2.  選取電腦，或按住 **Ctrl** 鍵選取多部電腦。

3.  在工作列上，選擇 [遠端工作] &gt; [重新整理清查]。

4.  若要檢視工作狀態，請選擇頁面右下角的 [遠端工作]。

    [工作狀態]  對話方塊會顯示目前的遠端工作、工作狀態、裝置名稱和任何回報的錯誤，並提供疑難排解資訊的連結。


## 從遠端重新啟動 Windows 電腦

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com/)中，選擇 [群組] &gt; [所有裝置] (或包含您想要重新啟動之電腦的其他群組)。

2.  選取一或多部電腦，然後選擇 [遠端工作] &gt; [重新啟動電腦]。

3.  若要檢視工作狀態，請選擇頁面右下角的 [遠端工作]。

4.  在 [工作狀態]  對話方塊中，檢閱目前的遠端工作、工作狀態、裝置名稱和任何回報的錯誤。

## 淘汰電腦

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com/)中，選擇 [群組] &gt; [所有裝置] (或包含您想要淘汰之電腦的其他群組)。

2.  選取您要淘汰的裝置，然後選擇 [淘汰/抹除]。

若要將電腦重新註冊到 Intune 中，請遵循[使用 Microsoft Intune 安裝 Windows 電腦用戶端](install-the-windows-pc-client-with-microsoft-intune.md)主題中的資訊，在電腦上重新安裝用戶端軟體。

如果電腦無法連線到 Intune，[儀表板] 工作區中會顯示訊息。

淘汰電腦時：

-   它會從 Intune 管理及清查移除，而與該電腦相關聯的授權將可重複使用。 [淘汰/抹除] 會移除 Intune 軟體用戶端，但不會從電腦移除應用程式或資料。

-   其狀態不再顯示在 Intune 主控台中。

-   Intune 會從電腦移除用戶端軟體。 如果電腦未連線到 Intune 服務，則會在下次連線時移除用戶端軟體。

-   Microsoft Intune Endpoint Protection 會從電腦移除。 如果電腦已安裝其他 Endpoint Protection 應用程式且已將它停用，則在移除 Microsoft Intune Endpoint Protection 之後，該應用程式可以重新啟用，以確保您的電腦受到保護。

-   所有原則都會從電腦移除，而且原則所設定的值將會變更。

-   電腦不會再從 Intune 服務接收軟體更新或惡意程式碼定義更新。

-   依據已淘汰電腦的設定方式，這些電腦仍可使用 Windows Server Update Services、Windows Update 或 Microsoft Update 繼續接收更新。

    > [!IMPORTANT]
    > 如果用戶端軟體是使用群組原則物件 (GPO) 安裝，您必須先移除群組原則物件 (GPO)，然後才能移除用戶端軟體，以避免重新安裝軟體。

    如果用戶端無法解除安裝，請參閱[疑難排解 Endpoint Protection](/intune/troubleshoot/troubleshoot-endpoint-protection-in-microsoft-intune) 以取得更多協助。

## 管理使用者裝置連結
將軟體部署給使用者之前，您必須先將使用者連結到電腦。 您可以將單一使用者連結到多部電腦，但是每一部電腦只能連結到一個使用者。 使用者會自動連結到他們在 Intune 中使用公司入口網站註冊的任何電腦。

### 若要將使用者連結到電腦

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com/)中，選擇 [群組] &gt; [所有裝置] (或包含您想要連結至使用者之電腦的其他群組)。

2.  選取您想要連結使用者的電腦，然後選擇 [連結使用者]。

    [連結使用者]  對話方塊會顯示可用使用者清單，列出使用者的顯示名稱、使用者識別碼，以及每個使用者目前連結的電腦數目。 如果使用者已經連結到選取的電腦，該使用者的名稱和使用者識別碼便會顯示在 [目前使用者] 下。 如果電腦未連結到任何使用者，[目前使用者]  下方將會出現 [沒有使用者] 。

3.  請執行下列其中一項動作：

    -   若要讓電腦與目前的使用者保持連結 (如有)，請選擇 [取消]。

    -   若要移除與目前使用者的連結 (如有)，請選擇 [移除連結] &gt; [確定]。

    -   若要將電腦連結到新的使用者，請在 [所有使用者]  清單中選取使用者。 請確認使用者資料是否正確，然後選擇 [確定]。

> [!TIP]
> 如果您想要限制使用者將自己連結到電腦的能力，請啟用 **Microsoft Intune 代理程式設定** 原則中的選項 [限制使用者將自己連結到電腦的能力]。

## 要求並提供使用 Intune 用戶端軟體之 Windows 電腦的遠端協助

Microsoft Intune 可以使用 [TeamViewer](https://www.teamviewer.com) 軟體，讓執行 Intune 用戶端軟體之電腦的使用者向您取得遠端協助。 使用者向 Microsoft Intune Center 要求協助時，您會收到警示通知、可以接受要求，然後提供協助。
這項功能會取代 Intune 中的現有 Windows 遠端協助功能。


### 開始之前

您必須先確認具有下列必要條件，再開始建立並回應遠端協助要求︰

- 您必須已[註冊 TeamViewer 帳戶](https://login.teamviewer.com/LogOn#register)，才能登入 TeamViewer 網站。
- 您想要管理的 Windows 電腦必須[由 Windows 電腦用戶端所管理](manage-windows-pcs-with-microsoft-intune.md)。
- 可以管理 Intune 所支援的所有 Windows 電腦作業系統。

### 設定 TeamViewer 連接器

1. 在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 **[系統管理]**。
2. 在 **[系統管理]** 工作區中，選擇 **[TeamViewer]**。
3. 在 **[TeamViewer]** 頁面的 **[TeamViewer 連接器]** 下，選擇 **[啟用]**。
4. 在 **[啟用 TeamViewer]** 對話方塊中，檢視後 **[接受]** 授權條款。 如果您尚未擁有 TeamViewer 授權，請選擇 **[購買 TeamViewer 授權]**。
5. TeamViewer 瀏覽器視窗開啟之後，請使用 TeamViewer 認證登入網站。
6. 在 TeamViewer 網站上，閱讀後接受允許 Intune 使用 TeamViewer 連接的選項。
7. 在 Intune 主控台中，確認 **[TeamViewer 連接器]** 項目顯示為 **[啟用]**。


### 開啟遠端協助要求 (使用者)

1. 在用戶端 Windows 電腦上，開啟 **[Microsoft Intune 中心]**。
2. 在 **[遠端協助]** 下，選擇 **[要求遠端協助]**。
3. 在您核准要求 (如下所示) 之後，會在用戶端上開啟 TeamViewer。 使用者必須接受指出網頁瀏覽器嘗試開啟 TeamViewer 應用程式的任何訊息。
4. 使用者會看到訊息，詢問您是否可以控制他們的電腦。 他們必須接受此訊息才能繼續。
5. 在遠端協助工作階段期間，使用者會看到顯示您已連接的視窗。 如果他們關閉這個視窗，遠端工作階段就會結束。

### 回應遠端協助要求

1. 使用者提交遠端協助要求時，您可以在 **[警示]** 工作區的 **[監視]** > **[遠端協助]** 下進行檢視。 例如：
> ![遠端協助要求的螢幕擷取畫面](./media/team-viewer.png)

<br>如果超過 4 小時未回應要求，便會將它移除。
2. 若要接受要求，請選擇 **[核准要求並啟動遠端協助]**。
3. 在 **[新的遠端協助要求擱置中]** 對話方塊中，選擇 **[接受遠端協助要求]**。 如果尚未安裝，TeamViewer 會在電腦上安裝任何必要的應用程式。
4. TeamViewer 接著會通知使用者：您想要控制其電腦。 使用者接受要求之後，TeamViewer 視窗隨即開啟，而您可以控制電腦。

處於遠端協助工作階段時，您可以使用所有可用的 TeamViewer 命令來控制遠端電腦。 如需這些命令的說明，請從 TeamViewer 網站下載[遠端控制手冊](http://www.teamviewer.com/en/support/documents/)。

### 關閉遠端協助工作階段

從 **[TeamViewer]** 視窗的 **[動作]** 功能表中，選擇 **[結束工作階段]**。



<!--HONumber=Aug16_HO1-->


