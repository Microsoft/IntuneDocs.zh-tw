---
title: 部署和監視合規性政策
description: 使用本主題中的逐步指示以部署及監視裝置合規性政策。
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 11/14/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d8f246d4-0d86-4c8b-a1bf-9977985506d8
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7e3f67411a4eff357102756e785f4cbbff120d23
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune"></a>在 Microsoft Intune 中部署和監視裝置相容性原則

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

## <a name="deploy-a-compliance-policy"></a>部署合規性政策
將您[建立的](create-a-device-compliance-policy-in-microsoft-intune.md)合規性原則部署到組織中的一或多個使用者群組。 將相容性原則部署到使用者時，即會檢查使用者裝置的相容性。

1.  在 [原則] 工作區中，選取您要部署的原則，然後選擇 [管理部署]。
![在頂端顯示 [管理部署] 功能表選項的合規性原則頁面螢幕擷取畫面](./media/intune-sa-3c-deploy-compliance-policy2.png)

2.  在 [管理部署] 對話方塊中，選擇您要部署原則的一或多個群組，然後選擇 [新增] > [確定]。
![[管理部署] 對話方塊的螢幕擷取畫面](./media/intune-sa-3d-deploy-compliance-policy3-Manage.png) 使用已建立並同步處理至 Intune 的 Active Directory 群組，或在 Intune 主控台中手動建立這些群組。 如需深入了解如何部署原則，請參閱[部署設定原則](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)。

使用 [原則] 工作區 [概觀] 頁面上的狀態摘要和警示，來識別需要注意的原則問題。 此外，狀態摘要還會顯示在 [儀表板]  工作區中。

> [!IMPORTANT]
> 若未部署合規性原則，但您啟用了 Exchange 條件式存取原則，則所有目標裝置都會擁有存取。

## <a name="monitor-the-compliance-policy"></a>監視合規性政策

#### <a name="to-view-devices-that-do-not-conform-to-a-compliance-policy"></a>檢視裝置不符合相容性原則的裝置

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 [群組] > [所有裝置]。

2.  按兩下裝置清單中的裝置名稱。

3.  選擇 [原則] 索引標籤，以查看該裝置的原則清單。

4.  從 [篩選條件] 下拉式清單中，選擇 [不符合合規性原則]。
![顯示篩選條件清單中選項清單的螢幕擷取畫面](./media/intune-sa-3e-view-device-noncompliance.png)

#### <a name="to-view-the-health-attestation-reports"></a>檢視健康情況證明報告

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 [報表]。

2.  在 [健康情況證明報告 - 建立新報告] 頁面中，您可以檢視內含 Intune 所收集之所有 Windows 10 健康情況證明資料的報告。 您也可以使用篩選條件，利用一部分的資料子集來建立報告。 篩選條件可以裝置類型、作業系統或僅一部分資料點為依據。

## <a name="how-intune-resolves-policy-conflicts"></a>Intune 如何解決原則衝突
將多項 Intune 原則套用至一部裝置時，可能會發生原則衝突。 如果原則設定重疊，Intune 會使用下列規則解決任何衝突︰

-   若衝突的設定來自 Intune 設定原則與合規性原則，合規性原則中的設定仍優先於設定原則中的設定。 即使設定原則中的設定更為安全亦然。

-   若您已部署多項合規性原則，Intune 將會取其中最安全的原則。

## <a name="next-steps"></a>接下來的步驟
若要了解如何使用合規性原則搭配條件式存取原則，以控制組織中服務的存取，請參閱[限制存取電子郵件及 O365 服務](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)。


### <a name="see-also"></a>另請參閱
[Intune 中的裝置合規性原則簡介](introduction-to-device-compliance-policies-in-microsoft-intune.md)
