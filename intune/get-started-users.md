---
title: 開始管理使用者
titlesuffix: Microsoft Intune
description: 將使用者新增至 Intune，並將授權指派給他們，讓他們可以在行動裝置上存取公司資源。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 22a232de-ab93-44ab-b0b5-d2b3ccb007fe
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: fc5d2a6f17bdac8711348c136ee390a400fc21bd
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52182494"
---
# <a name="get-started-managing-users"></a>開始管理使用者

請思考組織中所有不同的人。 使用公司資料的所有這些使用者都需要使用者在 Intune 中管理其存取權。

## <a name="how-do-i-create-a-user"></a>如何建立使用者？

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在您開啟 [Microsoft Intune] 窗格之後，請選取 [使用者]。 在 [所有使用者] 頁面上，選取[+ 新增使用者]。
4. 輸入使用者的詳細資料，例如 [名稱] 和 [使用者名稱]。 使用者名稱的網域名稱部分必須是下列其中一個網域：
    - 初始預設網域名稱 "contoso.onmicrosoft.com" 網域名稱，或者
    - 已驗證的非同盟網域名稱，例如 "contoso.com"。
5. 在 [群組] 下，選擇要將使用者新增到其中的[群組](get-started-groups.md)。
6. 儲存自動產生的使用者密碼，以便您可以使用它來登入測試裝置。 您必須提供這個密碼給使用者，讓使用者將其能變更為易記的一般密碼。
7. 在 [使用者] 窗格中，選取 [建立]。

## <a name="assigning-licenses-to-users"></a>將授權指派給使用者

您已建立使用者之後，需要使用 [Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)將 Intune 授權指派給該使用者。 若不指派授權給他們，他們將無法註冊其裝置以納入管理。

1. 使用與您用來登入 Intune 相同的認證登入 [Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)。
2. 選取 [使用者]  > [ 作用中使用者]，然後選取您先前建立的使用者。
3. 您可能需要稍待片刻，以便載入所有使用者資訊。 載入之後，針對使用者的 [產品授權] 選取 [編輯]。
4. 指派 [位置] 給使用者，然後將 Intune 切換為 [開啟]。

   > [!NOTE]
   > 這樣會將您的其中一個授權用於這名使用者。 如果您使用實際環境，可以稍後關閉使用此授權，將它重新指派給真正的使用者。

5. 選取 [儲存]。

## <a name="next-steps"></a>接下來的步驟

[開始使用群組](get-started-groups.md) - 將使用者組織成群組，以更輕鬆地管理他們可存取的原則和應用程式。
