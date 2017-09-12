---
title: "如何使用 TeamViewer 從遠端管理 Android 裝置"
titlesuffix: Azure portal
description: "了解如何使用 TeamViewer 從遠端管理 Android 裝置。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 72cdd888-efca-46e6-b2e7-fb9696bb2fba
ms.reviewer: davidra
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: da908316989598134edc7ab46491890f81676db6
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2017
---
# <a name="provide-remote-assistance-for-intune-managed-android-devices"></a>對 Intune 管理的 Android 裝置提供遠端協助

Intune 可以使用另行購買的 [TeamViewer](https://www.teamviewer.com) 軟體，讓您為 Android 裝置的使用者提供遠端協助。 使用本主題中的資訊以開始使用。

## <a name="before-you-start"></a>開始之前

### <a name="required-permissions"></a>必要權限

確認 Azure 入口網站的使用者具有下列指派給他們作為 [Intune 角色](https://docs.microsoft.com/intune-azure/access-control/role-based-access-control)的權限：
- 若要讓管理員能夠修改 TeamViewer 連接器設定，請授與**更新遠端協助**權限。
- 若要讓系統管理員能夠起始新的遠端協助要求，請授與**要求遠端協助**權限。 具有**要求遠端協助**權限的使用者可以要求起始任何使用者的工作階段， 而不會受到任何 Intune 角色指派範圍所限制。 Intune 角色指派範圍不會限制可以對其起始遠端協助要求的裝置或使用者。

>[!NOTE]
>藉由啟用 TeamViewer，您允許適用於 Intune 連接器的 TeamViewer 建立 TeamViewer 工作階段、讀取 Active Directory 資料，以及儲存 TeamViewer 帳戶存取權杖。

### <a name="configure-the-intune-teamviewer-connector"></a>設定 Intune TeamViewer 連接器

您必須先使用下列步驟來設定 Intune TeamViewer 連接器，然後才能為 Android 裝置提供遠端協助：


1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置]。
4. 在 [裝置和群組] 刀鋒視窗中，選擇 [設定] > [TeamViewer 連接器]。
5. 在 [TeamViewer 連接器] 刀鋒視窗中，按一下 [啟用]，然後檢視並接受 TeamViewer 服務授權合約。
6. 選擇 [登入 TeamViewer 進行授權]。
7. 隨即開啟一個網頁來顯示 TeamViewer 網站。 輸入您的 TeamViewer 授權認證，然後按一下 [登入]。


## <a name="how-to-remotely-administer-an-android-device"></a>如何從遠端管理 Android 裝置

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置]。
4. 在 [裝置] 刀鋒視窗中，選擇 [管理] > [所有裝置]。
5. 選取您想要從遠端管理的裝置，然後在 [裝置內容] 刀鋒視窗中，選擇 [更多] > [新的遠端協助工作階段]。
6. 當 Intune 連線至 TeamViewer 服務之後，您將會看到一些關於 Android 裝置的資訊。 選擇 [連線] 以啟動遠端工作階段。

![Android 的 TeamViewer 視窗](./media/android-teamviewer.png)

在 TeamViewer 視窗中，您可以在 Android 裝置上執行一連串的遠端動作，包括裝置的遠端控制。 如需您可執行之動作的完整詳細資料，請參閱 [TeamViewer 文件](https://www.teamviewer.com/support/documents/) \(英文\)。

完成後，請關閉 TeamViewer 視窗。

## <a name="end-user-notifications"></a>終端使用者通知

終端使用者會在其裝置的公司入口網站應用程式圖示上看到通知旗標，也會在其開啟應用程式時看到通知。 接著，他們就能接受遠端協助要求。

