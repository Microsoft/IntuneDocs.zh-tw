---
# required metadata

title: 保護未註冊裝置上的企業營運應用程式和資料 | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service:
ms.technology:
ms.assetid: 00219467-a62e-43b6-954b-3084f54c45ba

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: joglocke
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 保護未在 Microsoft Intune 註冊之裝置上的企業營運應用程式和資料

行動應用程式管理 (MAM) 原則協助保護公司資料的方式是限制複製和貼上這類資料移動，或防止使用者將公司文件儲存至個人位置。   若要將 MAM 原則套用至 iOS 和 (或) Android 企業營運應用程式，您必須先使用 Microsoft Intune App Wrapping Tool 來包裝應用程式。  應用程式包裝處理程序會將管理層套用到行動應用程式，而不需要對基礎應用程式進行任何變更。  應用程式在包裝之後，即可套用 MAM 原則，並將它發佈給使用者。  

本主題說明套用應用程式之 MAM 原則所需的步驟，而應用程式是在**員工擁有的未受管理裝置**以及**協力廠商行動裝置管理 (MDM) 解決方案**所管理的裝置上進行存取。  若要準備企業營運應用程式以**在 Intune 中註冊的裝置**上執行，請參閱[決定如何準備應用程式以使用 Microsoft Intune 進行行動應用程式管理](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)。
##  步驟 1：準備應用程式
您必須先使用 Microsoft Intune App Wrapping Tool 來包裝應用程式，才能將 MAM 原則套用至應用程式。  下載中包含應用程式包裝工具的安裝和使用指示。  
>[!IMPORTANT]  
>這版的應用程式包裝函式工具支援未在 Intune 中註冊的裝置，可在未來幾週的私人預覽中提供。 如果您想要參與，請將郵件傳送至 msintuneappsdk@microsoft.com 以取得詳細資訊。

## 步驟 2：新增應用程式

若要建立企業營運應用程式與 MAM 原則的關聯，您必須使用下列步驟將應用程式詳細資料新增至 Intune 訂閱/租用戶︰

1. 在 [Azure 入口網站](https://portal.azure.com/)中，移至 **[Intune 行動應用程式管理] > [設定]**，然後選擇 **[企業營運應用程式]**。

  ![含企業營運選項之 [設定] 刀鋒視窗的螢幕擷取畫面](../media/mam-azure-portal-lob-on-settings.png)

2. 在 **[企業營運應用程式]** 刀鋒視窗中，選擇 **[加入自訂應用程式]**。

  ![頂端有 [加入自訂應用程式] 按鈕之 [企業營運應用程式] 刀鋒視窗的螢幕擷取畫面](../media/mam-azure-portal-add-lob-app-action.png)
3.  提供應用程式的名稱、[應用程式識別碼] 欄位中的配套識別碼，以及平台 (iOS 或 Android)。

  ![[加入自訂應用程式] 刀鋒視窗的螢幕擷取畫面 ](../media/mam-azure-portal-add-app-details.png) 這個步驟有助於建立應用程式的唯一清單。  應用程式也會顯示在租用戶之 MAM 原則的目標應用程式清單中 (如下一步中所述)。

## 步驟 3︰套用 MAM 原則
將應用程式中繼資料上傳至服務之後，應用程式就會顯示在應用程式清單中。  您現在可以[建立新原則或現有原則](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)，並將它套用至您在步驟 2 新增的企業營運應用程式。

>[!IMPORTANT]
>您必須以會使用包裝的應用程式的使用者為 MAM 原則的目標。  使用者若未部署此原則，將無法使用該應用程式。


  ![顯示新企業營運應用程式之目標應用程式清單刀鋒視窗的螢幕擷取畫面](../media/mam-azure-portal-lob-on-targeted-app-list.png)
## 步驟 4︰發佈應用程式
您可以使用下列方式將應用程式部署至使用者︰
* 對於在協力廠商 MDM 解決方案中註冊的裝置，您可以透過 MDM 解決方案發佈應用程式。
* 對於未受到任何 MDM 解決方案管理的裝置，您需要自訂解決方案。 使用者必須在其裝置上下載並安裝應用程式。

## 變更中繼資料
如果您需要變更應用程式詳細資料 (如應用程式名稱或配套識別碼)，您必須[移除應用程式](#remove-apps)，並使用新的中繼資料來[新增應用程式](#add-the-app)。

##  移除應用程式
您可以從應用程式清單中移除企業營運應用程式。  這會從清單中移除應用程式，並移除與 MAM 原則的關聯，但不會從使用者裝置中移除或解除安裝應用程式。  

1.  在 [Azure 入口網站](https://portal.azure.com/)上，移至 **[Intune 行動應用程式管理] > [設定]**。  在 **[設定]** 刀鋒視窗上，選擇 **[企業營運]** 開啟現有應用程式清單。  
2.  選取您想要移除的應用程式，然後選擇 **[(…) 內容]** 功能表。

  ![含省略符號之 [企業營運應用程式] 刀鋒視窗的螢幕擷取畫面](../media/mam-azure-portal-lob-context-menu.png)
3.  選擇 **[刪除應用程式]** 刪除應用程式。

  ![含 [刪除應用程式] 選項之 [企業營運] 刀鋒視窗的螢幕擷取畫面](../media/mam-azure-portal-delete-app.png)

  這會從企業營運應用程式清單以及 MAM 原則的目標應用程式清單中移除應用程式。


<!--HONumber=Jun16_HO2-->


