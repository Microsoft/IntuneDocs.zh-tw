---
title: MAM 原則的 Azure 入口網站
description: 使用 Azure 入口網站建立行動裝置應用程式管理原則。 無論裝置是否有在 Intune 中註冊，您都可以套用在這裡建立的原則。
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 10/22/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7d6dae94-a833-40b7-9016-14ea234bb33c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ae0acf53a4987dac21e576826477d32da1f56155
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="azure-portal-for-intune-app-protection-policies"></a>用於 Intune 應用程式保護原則的 Azure 入口網站

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

針對下列，您可以使用 Azure 入口網站來建立和管理應用程式保護原則：

- **在 Intune 中註冊和管理**之裝置上執行的應用程式。

- **非**由任何 MDM 解決方案註冊之裝置上執行的應用程式。
- **在協力廠商 MDM 解決方案中註冊**之裝置上執行的應用程式。

>[!IMPORTANT]
> Azure 入口網站是建立應用程式保護原則的新管理員主控台，但您也可以使用 MDM 案例的 [Intune 管理主控台](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)來建立應用程式保護原則，其支援向 Intune 註冊的裝置應用程式。

> Intune 管理主控台可能不會顯示所有可用的應用程式保護原則設定。 此外，如果您在 Intune 管理主控台和 Azure 入口網站上都建立應用程式保護原則，則在 Azure 入口網站中建立的原則會覆寫在 Intune 管理主控台上建立的原則。 在此情況中，Azure 入口網站的應用程式保護原則會套用至應用程式並部署至使用者。


## <a name="sign-in-to-the-azure-portal-and-customize-your-start-page"></a>登入 Azure 入口網站並自訂起始畫面

1.  移至 [Azure 入口網站](https://portal.azure.com)，並使用您的 Intune 認證登入。

    ![Azure 入口網站登入頁面的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAMSigninPage.png)

2.  成功登入之後，您會看到 [儀表板]。 您可以自訂 [儀表板] 頁面。

    ![Azure 入口網站儀表板的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAMStartboard_NoMAM.png)

3.  選擇左功能表中的 [更多服務]，然後在文字方塊篩選中輸入 **Intune**。

    ![反白顯示 Intune 的 [瀏覽] 功能表螢幕擷取畫面](../media/AppManagement/MAM-Azure-Portal-1.png)

4.  選擇 [Intune 應用程式保護] > [Intune 行動應用程式管理] > [所有設定]。

    ![Intune 行動應用程式管理刀鋒視窗的螢幕擷取畫面](../media/AppManagement/MAM-Azure-Portal-2.png)

5. (選擇性) 若要將刀鋒視窗釘選到 [開始] 頁面，您可以使用刀鋒視窗的 [釘選] 選項。 按一下 [Intune 行動應用程式管理] 刀鋒視窗的釘選圖示，將刀鋒視窗釘選到 [開始] 頁面。

    ![反白顯示釘選圖示的 Intune 行動應用程式管理刀鋒視窗的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAM_PinBladeAction.png)

    ![包含釘選的 Intune 磚之儀表板的螢幕擷取畫面](../media/AppManagement/AzurePortal_MAM_Startboard_withMAM.png)

## <a name="next-steps"></a>接下來的步驟
[準備好設定應用程式保護原則](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)
