---
title: 如何只抹除應用程式中的公司資料
titleSuffix: Microsoft Intune
description: 了解如何使用 Microsoft Intune 從 Intune 管理的應用程式中選擇性地抹除公司資料。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
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
ms.openlocfilehash: a5bcdf9c3218df91bea85858ea21e88718e81633
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72498324"
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

1. 登入 [Azure 入口網站](https://portal.azure.com)。

2. 選擇 [所有服務]  ，接著在 [篩選] 文字方塊中鍵入 **Intune**，然後選取 [Intune]  。 當 [Intune] 窗格開啟時，選擇 [用戶端應用程式]  窗格。

    ![Microsoft Intune 窗格的螢幕擷取畫面](./media/apps-selective-wipe/apps-selective-wipe01.png)

3. 在 [用戶端應用程式]  窗格上選擇 [應用程式選擇性抹除]  。

4. 選擇 [新增抹除要求]  。 [新增抹除要求]  窗格會隨即開啟。

    ![[新增抹除要求] 窗格的螢幕擷取畫面](./media/apps-selective-wipe/AzurePortal_MAM_NewWipeRequest.png)

5. 選擇使用者，然後選擇 [選取]  來選取您要抹除其應用程式資料的使用者。

6. 接下來，從 [新增抹除要求]  窗格中選擇 [裝置]  。 這會開啟 [選取裝置]  窗格，列出與所選使用者建立關聯的所有裝置，並會提供兩個資料行，其中 [裝置名稱] 是使用者定義的易記名稱，而 [裝置類型] 則是其裝置平台。 選取您要抹除的裝置。

7. 現在您已回到 [新增抹除要求]  窗格。 選擇 [確定]  以提出抹除要求。

此服務會為裝置上每個受保護的應用程式建立個別的抹除要求，並加以追蹤，以及抹除要求相關聯的使用者。

## <a name="monitor-your-wipe-requests"></a>監視抹除要求

您可有摘要報表顯示抹除要求的整體狀態，以及暫止的要求數與失敗數。 若要取得更多詳細資訊，請遵循下列步驟︰

1. [用戶端應用程式 - 應用程式選擇性抹除]  窗格上會依使用者分組列出您的要求清單。 由於系統會針對裝置上執行的每個受保護應用程式建立抹除要求，因此您可能會看到一名使用者具有多個要求的情況。 狀態指出抹除要求為**擱置**、**失敗**或**成功**。

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
