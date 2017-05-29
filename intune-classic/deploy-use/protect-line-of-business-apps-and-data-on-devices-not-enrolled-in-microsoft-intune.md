---
title: "保護未註冊裝置上的 LOB 應用程式 | Microsoft Docs"
description: "本主題說明如何準備您自訂的企業營運應用程式，以便您可以套用有助於防止資料遺失的行動裝置應用程式管理原則。"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00219467-a62e-43b6-954b-3084f54c45ba
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: f30837d90954b9b30b27e77240bb241db6e2b037
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="protect-line-of-business-apps-and-data-on-devices-that-are-not-enrolled-in-microsoft-intune"></a>保護未在 Microsoft Intune 註冊之裝置上的企業營運應用程式和資料

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

行動應用程式管理 (MAM) 原則可協助保護公司資料，方法是限制可能會遺漏公司資料的動作，以及強制執行資料存取需求 (例如應用程式 PIN)。 若要將 MAM 原則套用至 iOS 和 Android 企業營運應用程式，您必須先使用 Microsoft Intune App Wrapping Tool 來包裝應用程式。 應用程式包裝處理程序會將管理層套用到行動應用程式，而不需要對基礎應用程式進行任何變更。 應用程式在包裝之後，即可套用 MAM 原則，並將它發佈給使用者。  

本主題說明套用應用程式之 MAM 原則所需的步驟，而應用程式是在**員工擁有的未受管理裝置**以及**協力廠商行動裝置管理 (MDM) 解決方案**所管理的裝置上進行存取。  若要準備企業營運應用程式以在 **Intune MDM 中註冊的裝置**上執行，請參閱[決定如何準備應用程式以使用 Microsoft Intune 進行行動應用程式管理](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)。


##  <a name="step-1-prepare-the-app"></a>步驟 1：準備應用程式

在您可以將 MAM 原則套用到應用程式之前，您必須先包裝應用程式，方法是使用適用於 [iOS](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) 和 [Android](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) 的 Microsoft Intune App Wrapping Tool，或使用 [Intune App SDK](../develop/intune-app-sdk.md) 來手動整合 Intune 應用程式保護功能。

如需有關使用 App Wrapping Tool 與 SDK 的詳細資訊，請參閱[決定如何準備應用程式以使用 Microsoft Intune 進行行動應用程式管理](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)。

## <a name="step-2-add-the-app"></a>步驟 2：新增應用程式

若要建立企業營運應用程式與 MAM 原則的關聯，您必須使用下列步驟將應用程式詳細資料新增至 Intune 訂閱/租用戶︰

1. 在 [Azure 入口網站](https://portal.azure.com/)中，移至 [Intune 行動應用程式管理] > [設定]，然後選擇 [企業營運應用程式]。

  ![含企業營運選項之 [設定] 刀鋒視窗的螢幕擷取畫面](../media/mam-azure-portal-lob-on-settings.png)

2. 在 [企業營運應用程式] 刀鋒視窗中，選擇 [加入自訂應用程式]。

  ![頂端有 [加入自訂應用程式] 按鈕之 [企業營運應用程式] 刀鋒視窗的螢幕擷取畫面](../media/mam-azure-portal-add-lob-app-action.png)
3.    提供應用程式的名稱、[應用程式識別碼] 欄位中的配套識別碼，以及平台 (iOS 或 Android)。

  ![[加入自訂應用程式] 刀鋒視窗的螢幕擷取畫面](../media/mam-azure-portal-add-app-details.png)

  此步驟可協助您建立應用程式的唯一列示清單。 應用程式也會顯示在租用戶之 MAM 原則的目標應用程式清單中 (如下一步中所述)。

## <a name="step-3-apply-mam-policies"></a>步驟 3︰套用 MAM 原則
應用程式中繼資料上傳至服務之後，應用程式會顯示在應用程式清單中。 您現在可以[建立新原則或使用現有原則](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)，並將它套用至您在步驟 2 新增的企業營運應用程式。

>[!IMPORTANT]
>您必須以會使用包裝的應用程式的使用者為 MAM 原則的目標。  使用者若未部署此原則，將無法使用該應用程式。


  ![顯示新企業營運應用程式之目標應用程式清單刀鋒視窗的螢幕擷取畫面](../media/mam-azure-portal-lob-on-targeted-app-list.png)
## <a name="step-4-distribute-the-app"></a>步驟 4︰發佈應用程式
您可以使用下列方式將應用程式部署至使用者︰
* 對於在協力廠商 MDM 解決方案中註冊的裝置，您可以透過 MDM 解決方案發佈應用程式。
* 針對未受任何 MDM 解決方案管理的裝置，您需要自訂解決方案。 使用者必須在他們的裝置上下載並安裝應用程式。

## <a name="change-the-metadata"></a>變更中繼資料
如果您需要變更應用程式詳細資料 (如應用程式名稱或配套識別碼)，您必須[移除應用程式](#remove-apps)，並使用新的中繼資料來[新增應用程式](#step-2-add-the-app)。

##  <a name="remove-apps"></a>移除應用程式
您可以從應用程式清單中移除企業營運應用程式。 這會從清單中移除應用程式，並移除與 MAM 原則的關聯，但不會從使用者裝置中移除或解除安裝應用程式。  

1.    在 [Azure 入口網站](https://portal.azure.com/)上，移至 [Intune 行動應用程式管理] > [設定]。 在 **[設定]** 刀鋒視窗上，選擇 **[企業營運]** 開啟現有應用程式清單。  
2.    選取您想要移除的應用程式，然後選擇 [(…) 內容] 功能表。

  ![含省略符號之 [企業營運應用程式] 刀鋒視窗的螢幕擷取畫面](../media/mam-azure-portal-lob-context-menu.png)
3.    選擇 **[刪除應用程式]** 刪除應用程式。

  ![含 [刪除應用程式] 選項之 [企業營運] 刀鋒視窗的螢幕擷取畫面](../media/mam-azure-portal-delete-app.png)

  這會從企業營運應用程式清單以及 MAM 原則的目標應用程式清單中移除應用程式。

