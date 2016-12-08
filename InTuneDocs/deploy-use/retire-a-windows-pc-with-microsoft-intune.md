---
title: "淘汰 Windows 電腦 | Microsoft Intune"
description: "如何淘汰受 Intune 管理的 Windows 電腦。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5c916182-d99c-44c5-a779-3f596f261c40
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 19e8e2b6a7eaa3cf02e4296a6fd147baa1472b61


---

# <a name="retire-a-windows-pc"></a>淘汰 Windows 電腦
使用下列步驟來淘汰受 Intune 管理的電腦。

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com/)中，選擇 [群組] &gt; [所有裝置 (或包含您想要淘汰之電腦的其他群組)]。

2.  選取您要淘汰的裝置，然後選擇 [淘汰/抹除]。

若要將電腦重新註冊到 Intune 中，請使用[使用 Microsoft Intune 安裝 Windows 電腦用戶端](install-the-windows-pc-client-with-microsoft-intune.md)，在電腦上重新安裝軟體用戶端。

如果電腦無法連線到 Intune，[儀表板] 工作區中會顯示訊息。

淘汰電腦時：

-   它會從 Intune 管理及清查移除，而與該電腦相關聯的授權將可重複使用。 [淘汰/抹除] 會移除 Intune 軟體用戶端，但不會從電腦移除應用程式或資料。 這項淘汰作業不會在電腦上執行完整抹除。

-   其狀態不再顯示在 Intune 主控台中。

-   Intune 會從電腦移除軟體用戶端。 如果電腦未連線到 Intune 服務，則會在下次連線時移除軟體用戶端。

-   Microsoft Intune Endpoint Protection 會從電腦移除。 如果電腦已安裝其他 Endpoint Protection 應用程式且已將它停用，則在移除 Microsoft Intune Endpoint Protection 之後，該應用程式可以重新啟用，以確保您的電腦受到保護。

-   所有原則都會從電腦移除，而且原則所設定的值將會變更。

-   電腦不會再從 Intune 服務接收軟體更新或惡意程式碼定義更新。

-   依據已淘汰電腦的設定方式，這些電腦仍可使用 Windows Server Update Services、Windows Update 或 Microsoft Update 繼續接收更新。

    > [!IMPORTANT]
    > 如果用戶端軟體是使用群組原則物件 (GPO) 安裝，您必須先移除群組原則物件 (GPO)，然後才能移除用戶端軟體，以避免重新安裝軟體。

    如果用戶端無法解除安裝，請參閱[疑難排解 Endpoint Protection](/intune/troubleshoot/troubleshoot-endpoint-protection-in-microsoft-intune) 以取得更多協助。

### <a name="see-also"></a>請參閱

[使用 Intune 軟體用戶端執行的一般 Windows 電腦管理工作](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)


<!--HONumber=Nov16_HO4-->


