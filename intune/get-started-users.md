---
title: "開始使用使用者"
titleSuffix: Intune on Azure
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 22a232de-ab93-44ab-b0b5-d2b3ccb007fe
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fc1c4f6d18fd78f455be8e333bb765080184c908
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2017
---
# <a name="get-started-with-users"></a>開始使用使用者

![Azure 中的一般使用者](/intune/media/generic-intune-user.png)

Azure AD 管理貴組織的物件群組，例如裝置和應用程式，也會管理使用者群組。 您可以將使用者或裝置分組在一起，而不必個別管理每部裝置。 這可讓您輕鬆地將應用程式和設定指派給大量的使用者和裝置。

## <a name="how-do-i-create-a-user"></a>如何建立使用者？

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 使用 [搜尋資源]，搜尋 [使用者和群組]。
3. 一旦您開啟 [使用者和群組] 刀鋒視窗，請選取 [所有使用者]，然後選取 [+ 新增使用者]。
4. 輸入使用者的詳細資料，例如 [名稱] 和 [使用者名稱]。 使用者名稱的網域名稱部分，必須是初始預設網域名稱 "contoso.onmicrosoft.com" 網域名稱，或已驗證、非同盟的網域名稱，例如 "contoso.com"。
5. 在 [群組] 下，選擇要將使用者新增到其中的測試群組。
6. 儲存自動產生的使用者密碼，以便您可以使用它來登入測試裝置。 您必須提供這個密碼給使用者，讓使用者將其能變更為易記的一般密碼。
7. 在 [使用者] 刀鋒視窗上，選取 [建立]。

## <a name="assigning-licenses-to-users"></a>將授權指派給使用者

您已建立使用者之後，需要使用 [Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)將 Intune 授權指派給該使用者。 若不指派授權給他們，他們將無法註冊其裝置以納入管理。

1. 使用與您用來登入 Intune 相同的認證登入 [Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)。
2. 選取 [使用者]  > [ 作用中使用者]，然後選取您先前建立的使用者。
3. 您可能需要稍待片刻，以便載入所有使用者資訊。 載入之後，針對使用者的 [產品授權] 選取 [編輯]。
4. 指派 [位置] 給使用者，然後將 Intune 切換為 [開啟]。

 > [!NOTE]
 > 這樣會將您的其中一個授權用於這名使用者。 如果您使用實際環境，可以稍後關閉使用此授權，將它重新指派給真正的使用者。

5. 選取 [儲存]。
