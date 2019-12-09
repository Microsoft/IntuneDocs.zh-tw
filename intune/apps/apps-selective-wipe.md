---
title: 如何只抹除應用程式中的公司資料
titleSuffix: Microsoft Intune
description: 了解如何使用 Microsoft Intune 從 Intune 管理的應用程式中選擇性地抹除公司資料。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 42605e6e-5b84-44ff-b86e-346ea123b53e
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c0ca82b434b83937c7962b2676ce3c2a12c1424
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/27/2019
ms.locfileid: "74564009"
---
# <a name="how-to-wipe-only-corporate-data-from-intune-managed-apps"></a>如何只抹除 Intune 管理之應用程式中的公司資料

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

當裝置遺失或遭竊，或者如果員工離職，您會想要確定公司應用程式資料已從裝置移除。 不過，您可能不想要移除裝置上的個人資料，特別是當該裝置為員工擁有的裝置時。

>[!NOTE]
> 目前僅支援 iOS、Android 和 Windows 10 平台可從 Intune 管理的應用程式抹除公司資料。 Intune 受控應用程式是包含 Intune APP SDK 並具有您組織所授權使用者帳戶的應用程式。 您不需要部署應用程式保護原則，即可啟用應用程式選擇性抹除。

若要選擇性地移除公司應用程式資料，請使用本主題中的步驟建立抹除要求。 完成抹除要求之後，當裝置下一次執行應用程式時，即會從應用程式中移除公司資料。 不符合應用程式保護原則 (APP) 存取設定的條件時，除了建立抹除要求之外，您還可以設定選擇性抹除組識資料作為新的動作。 這項功能可協助您依據預先設定的準則，自動保護並移除應用程式中的機密組織資料。

>[!IMPORTANT]
> 移除直接從應用程式同步到原生通訊錄的連絡人。 無法清除從原生通訊錄同步處理到其他外部來源的任何連絡人。 目前只有 Microsoft Outlook 應用程式可使用此功能。

## <a name="deployed-wip-policies-without-user-enrollment"></a>在無須使用者註冊的情況下部署 WIP 原則
「Windows 資訊保護」(WIP) 原則能在無須 MDM 使用者註冊其 Windows 10 裝置的情況下部署。 此設定允許公司根據 WIP 設定保護其公司文件，同時允許使用者維持其自身 Windows 裝置的管理。 一旦使用 WIP 原則保護文件，Intune 系統管理員便可以選擇性抹除受保護的資料。 透過選取使用者和裝置，並傳送抹除要求，所有透過 WIP 原則保護的資料都會無法使用。 從 Azure 入口網站中的 Intune，選取 [用戶端應用程式]   > [應用程式選擇性抹除]  。 如需詳細資訊，請參閱[使用 Intune 建立及部署 Windows 資訊保護 (WIP) 應用程式保護原則](windows-information-protection-policy-create.md)。

## <a name="create-a-wipe-request"></a>建立抹除要求

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [應用程式]   > [應用程式選擇性抹除]   > [建立抹除要求]  。<br>
   即會顯示 [Create wipe request] \(建立抹除要求\)  窗格。
3. 按一下 [選取使用者]  ，選擇想要抹除其應用程式資料的使用者，然後按一下 [選取使用者]  窗格底部的 [選取]  。

    ![[選取使用者] 窗格的螢幕擷取畫面](./media/apps-selective-wipe/apps-selective-wipe-01.png)

4. 按一下 [選取裝置]  選擇裝置，然後按一下 [選取裝置]  窗格底部的 [選取]  。

    ![[建立抹除要求] 窗格的螢幕擷取畫面，其中已選取裝置](./media/apps-selective-wipe/apps-selective-wipe-02.png)

5. 按一下 [確定]  以提出抹除要求。

此服務會為裝置上每個受保護的應用程式建立個別的抹除要求，並加以追蹤，以及抹除要求相關聯的使用者。

   ![[用戶端應用程式 - 應用程式選擇性抹除] 窗格的螢幕擷取畫面](./media/apps-selective-wipe/apps-selective-wipe-03.png)

## <a name="monitor-your-wipe-requests"></a>監視抹除要求

您可有摘要報表顯示抹除要求的整體狀態，以及暫止的要求數與失敗數。 若要取得更多詳細資訊，請遵循下列步驟︰

1. 在 [應用程式]   > [應用程式選擇性抹除]  窗格上會依使用者分組列出您的要求清單。 由於系統會針對裝置上執行的每個受保護應用程式建立抹除要求，因此您可能會看到一名使用者具有多個要求的情況。 狀態指出抹除要求為**擱置**、**失敗**或**成功**。

    ![[應用程式選擇性抹除] 窗格中抹除要求狀態的螢幕擷取畫面](./media/apps-selective-wipe/wipe-request-status-1.png)

此外，您可以查看裝置名稱及其裝置類型，這對閱讀報表十分有幫助。

>[!IMPORTANT]
> 使用者必須開啟應用程式，抹除才會發生，並可能在發出要求後花費 30 分鐘的時間。

## <a name="delete-a-wipe-request"></a>刪除抹除要求

處於擱置狀態的抹除將會顯示，直到您手動將其刪除為止。 若要手動刪除抹除要求：

1. 在 [用戶端應用程式 - 應用程式選擇性抹除]  窗格上。

2. 在清單中，以滑鼠右鍵按一下要刪除的抹除要求，然後選擇 [刪除抹除要求]  。

    ![[應用程式選擇性抹除] 窗格中抹除要求清單的螢幕擷取畫面](./media/apps-selective-wipe/delete-wipe-request.png)

3. 當收到確認刪除的提示時，請選擇 [是]  或 [否]  ，然後按一下 [確定]  。

## <a name="see-also"></a>請參閱
[什麼是應用程式保護原則](app-protection-policy.md)

[什麼是應用程式管理](app-management.md)
