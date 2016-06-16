---
# required metadata

title: MAM 原則的 Azure 入口網站 | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 7d6dae94-a833-40b7-9016-14ea234bb33c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: joglocke
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune MAM 原則的 Azure 入口網站
## 存取 Azure 入口網站
**Azure 入口網站**可讓您建立和管理行動應用程式管理原則。

建立 MAM 原則的 Azure 入口網站支援︰
- **由 Intune 註冊和管理**之裝置上執行的應用程式。
- **非**由任何 MDM 解決方案註冊之裝置上執行的應用程式。
- **在協力廠商 MDM 解決方案中註冊**之裝置上執行的應用程式。

如果您目前使用 **Intune 管理主控台**來管理裝置，則可以使用 [Intune 管理主控台](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)，為 Intune 註冊的裝置建立支援應用程式的 MAM 原則。
>[!IMPORTANT]
> 您可能看不到 Intune 管理主控台中的所有 MAM 原則設定。 Azure 入口網站是建立 MAM 原則的新管理主控台。如果您在 Intune 管理主控台和 Azure 入口網站上建立 MAM 原則，則會將 Azure 入口網站中的原則套用至應用程式並部署至使用者。

## 登入 Azure 入口網站和自訂起始頁

1.  移至 [Azure 入口網站](https://portal.azure.com)並以 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 認證登入。

    ![Azure 入口網站登入頁面的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAMSigninPage.png)

2.  一旦成功登入，您會看到 [儀表板]。 [儀表板] 頁面都附有一組可以移除及新增的預設磚，讓您自訂頁面。

    ![Azure 入口網站儀表板的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAMStartboard_NoMAM.png)

3.  從 **[瀏覽]** 功能表中，尋找 **Intune**。![反白顯示 Intune [瀏覽] 功能表的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAM_Browse_Intune.png)

4.  按一下 **[Intune] > [Intune 行動應用程式管理] > [設定]**。

    ![Intune 行動應用程式管理刀鋒視窗的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAM_Mainblade.png)

    > [!TIP]
    > 若要將刀鋒視窗釘選到 [開始]  頁面，您可以使用刀鋒視窗的 [釘選]  選項。  按一下 [Intune 行動應用程式管理] 刀鋒視窗的釘選圖示，將它釘選到 [開始]  頁面。

    ![反白顯示釘選圖示的 Intune 行動應用程式管理刀鋒視窗的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAM_PinBladeAction.png)

    ![包含釘選的 Intune 磚之儀表板的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAM_Startboard_withMAM.png)
## 後續步驟
[準備設定行動應用程式管理原則](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)


<!--HONumber=Jun16_HO2-->


