---
title: 我的 Intune 功能移到 Azure 中的哪個位置？
titleSuffix: Microsoft Intune
description: 協助您在 Azure 入口網站中尋找 Microsoft Intune 功能。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 1/4/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 4a1c5f2b400e73566db88fea8e06383e45b363a3
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187747"
---
# <a name="where-did-my-intune-feature-go-in-azure"></a>我的 Intune 功能移到 Azure 中的哪個位置？
當我們將 Intune 移到 Azure 入口網站時，我們藉此機會以更邏輯的方式來組織一些工作。 但每項改進都需要您學習新的組織。 此參考指南適用於已經十分熟悉傳統入口網站中 Intune，但是想知道 Azure 入口網站中 Intune 操作步驟的使用者。 如果本文未涵蓋您嘗試尋找的功能，請在本文結尾留下意見，以便我們可以進行更新。
## <a name="quick-reference-guide"></a>快速參考指南

|功能 |傳統入口網站中的路徑|Azure 入口網站中 Intune 的路徑|
|------------|---------------|---------------|
|裝置註冊計劃 (DEP) [僅限 iOS]|[管理] > [行動裝置管理] > [iOS] > [裝置註冊計劃]|[[裝置註冊] > [Apple 註冊] > [註冊計劃權杖]](#where-did-apple-dep-go) |
|裝置註冊計劃 (DEP) [僅限 iOS]| [管理] > [行動裝置管理] > [iOS 與 Mac OS X] > [裝置註冊計劃] |[[裝置註冊] > [Apple 註冊] > [註冊計劃序號]](#where-did-apple-dep-go) |
|註冊規則 |[管理] > [行動裝置管理] > [註冊規則]|[[裝置註冊] > [註冊限制]](#where-did-enrollment-rules-go) |
|依 iOS 序號分組 |[群組] > [所有裝置] > [公司預先註冊的裝置] > [依 iOS 序號]|[[裝置註冊] > [Apple 註冊] > [註冊計劃序號]](#where-did-corporate-pre-enrolled-devices-go) |
|依 iOS 序號分組 |[群組] > [所有裝置] > [公司預先註冊的裝置] > [依 iOS 序號]| [[裝置註冊] > [Apple 註冊] > [AC 序號]](#where-did-corporate-pre-enrolled-devices-go)|
|依 IMEI 分組 (所有平台)| [群組] > [所有裝置] > [公司預先註冊的裝置] > [依 IMEI (所有平台)] | [[裝置註冊] > [公司裝置識別碼]](#by-imei-all-platforms)|
| 公司裝置註冊設定檔| [原則] > [公司裝置註冊] | [[裝置註冊] > [Apple 註冊] > [註冊計劃設定檔]](#where-did-corporate-pre-enrolled-devices-go) |
| 公司裝置註冊設定檔 | [原則] > [公司裝置註冊] | [[裝置註冊] > [Apple 註冊] > [AC 設定檔]](#where-did-corporate-pre-enrolled-devices-go) |
| Android for Work | [管理] > [行動裝置管理] > [Android for Work] | [裝置註冊] > [Android 註冊] |
| 條款及條件 | [原則] > [條款及條件] | [裝置註冊] > [條款及條件] |
公司入口網站設定|管理 > 公司入口網站|**管理** > Mobile 應用程式<br> **設定** > 公司入口網站商標


## <a name="where-do-i-manage-groups"></a>我在何處管理群組？
Azure 入口網站中的 Intune 使用 [Azure Active Directory (AD)](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal) 來管理群組。

## <a name="where-did-enrollment-rules-go"></a>註冊規則在哪裡？
在傳統入口網站中，您可以設定規則來控管行動裝置以及新式 Windows 和 macOS 裝置的 MDM 註冊。

![傳統行動裝置註冊規則的影像](./media/01-classic-rules.png)

這些規則會套用到您的 Intune 帳戶中的所有使用者，無一例外。 在 Azure 入口網站中，這些規則現在會顯示在兩種不同的原則類型中：[裝置類型限制] 和 [裝置限制]。

![Azure 行動裝置註冊限制的影像](./media/02-azure-enroll-restrictions.png)

預設的 [裝置限制] 對應至傳統入口網站中的 [裝置註冊限制]。

![Azure 裝置限制的影像](./media/03-azure-device-limit.png)

預設的 [裝置類型限制] 對應至傳統入口網站中的 [平台限制]。

![Azure 裝置類型限制的影像](./media/04-azure-platform-restrictions.png)

允許或封鎖個人擁有之裝置的功能現在是在 [裝置類型限制] 的 [平台設定] 下進行管理。

![Azure 個人裝置封鎖設定的影像](./media/05-azure-personal-block.png)

新的限制功能只會新增至 Azure 入口網站。

## <a name="where-did-my-conditional-access-policies-go"></a>我的條件式存取原則移到哪個位置？
當您的租用戶移轉至 Azure 入口網站之後，租用戶的條件式存取原則會繼續強制執行。 不過，您無法從 Azure 入口網站的 Intune 進行檢視或修改。

如果您想要從 Azure 入口網站檢視條件式存取原則並進行變更，您需要從傳統入口網站移除舊的原則。 然後在 Azure 入口網站中重新建立這些原則。 如需移轉條件式存取原則的詳細資訊，請參閱[移轉 Azure 入口網站中的傳統原則](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-migration)。 

## <a name="where-did-my-compliance-policies-go"></a>我的合規性原則移到哪個位置？
當您的租用戶移轉至 Azure 入口網站之後，租用戶的合規性原則會繼續強制執行。 不過，您無法從 Azure 入口網站的 Intune 進行檢視或修改。

如果您想要從 Azure 入口網站檢視合規性原則並進行變更，您需要從傳統入口網站移除舊原則。 然後在 Azure 入口網站中重新建立這些原則。 如需裝置合規性原則的詳細資訊，請參閱[開始使用 Intune 中的裝置合規性原則](https://docs.microsoft.com/intune/known-issues#compliance)。 

## <a name="where-did-apple-dep-go"></a>Apple DEP 在哪裡？
在傳統入口網站中，您可以設定 Intune 與 Apple 裝置註冊計劃的整合，並手動要求與 Apple 服務同步處理：

![傳統 DEP 權杖的影像](./media/06-classic-dep-token.png)

在 Azure 入口網站中，您會透過 Intune 傳統中的相同步驟，來設定 Apple 裝置註冊計劃：

![Azure DEP 權杖的影像](./media/07-azure-dep-token.png)

不過，傳統入口網站中的 [同步] 選項已移至序號管理工作流程，因為手動同步的結果會出現在該處：

![Azure DEP 同步的影像](./media/08-azure-dep-sync.png)

## <a name="where-did-corporate-pre-enrolled-devices-go"></a>公司預先註冊的裝置在哪裡？
### <a name="by-ios-serial-number"></a>依 iOS 序號
在傳統入口網站中，您可以透過 Apple 裝置註冊計劃 (DEP) 和 Apple Configurator 工具來註冊 iOS 裝置。 這兩種方法會依序號提供裝置預先註冊，而且需要指派特殊的公司裝置註冊設定檔。 在註冊之前，可透過 [公司預先註冊的裝置] 的 [依 iOS 序號] 裝置群組管理註冊設定檔指派：

![傳統 Apple 序號的影像](./media/09-classic-apple-serials.png)

這會以單一清單列出 Apple DEP 和 Configurator 註冊的序號。 為了減少設定檔指派不相符的情況 (將 DEP 設定檔指派給 AC 序號及將 AC 序號指派給 DEP 設定檔)，我們在 Azure 入口網站中將序號分成兩份清單：

**DEP 序號**
![Azure DEP 序號的影像](./media/10-azure-dep-serials.png)

**Apple Configurator 序號**
![Azure Apple Configurator 序號的影像](./media/11-azure-ac-serials.png)

### <a name="by-imei-all-platforms"></a>依 IMEI (所有平台)

在傳統入口網站中，您可以預先列出裝置的 IMEI 編號，以在向 Intune 註冊裝置時，將裝置標示為公司：

![IMEI 編號之傳統清單的影像](./media/12-classic-corp-imei.png)

在 Azure 入口網站中，您必須使用逗號分隔值 (CSV) 檔案，將相同的 IMEI 上傳至「公司裝置識別碼」清單。 新的入口網站不支援手動輸入 IMEI 編號：

![IMEI 編號之 Azure 清單的影像](./media/13-azure-corp-imei.png)

Azure 入口網站中的 Intune 未來將支援除 IMEI 以外的其他識別碼類型，但目前只允許預先列出 IMEI 編號。

## <a name="where-did-corporate-device-enrollment-profiles-go"></a>公司裝置註冊設定檔在哪裡？
若要透過 Apple 裝置註冊計劃或 Apple Configurator 工具註冊 iOS 裝置，您必須提供要指派裝置的公司裝置註冊設定檔。 在傳統入口網站中，這些設定檔的建立和管理作業都是在單一清單中進行：

![傳統裝置註冊設定檔的影像](./media/14-classic-corp-profiles.png)

此清單會顯示啟用給 Apple 裝置註冊計劃使用的設定檔 (**啟動 DEP**)，以及僅啟用給 Apple Configurator 工具使用的設定檔 (**關閉 DEP**)。

為了減少兩種設定檔類型之間發生混淆，以及指派可能不相符的情況 (將 DEP 設定檔指派給 Configurator 裝置及將 Configurator 裝置指派給 DEP 設定檔)，我們已分開進行註冊計劃設定檔 (支援 Apple 裝置註冊計劃和 Apple School Manager) 和 Apple Configurator 設定檔的建立和管理作業：

**DEP 設定檔**
![Azure DEP 設定檔的影像](./media/15-azure-dep-profiles.png)

**Apple Configurator 設定檔**
![Azure Apple Configurator 設定檔的影像](./media/16-azure-ac-profiles.png)
