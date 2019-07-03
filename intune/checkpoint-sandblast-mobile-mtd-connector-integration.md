---
title: 整合 Check Point SandBlast MTD
titleSuffix: Microsoft Intune
description: 如何使用 Intune 設定 Check Point SandBlast Mobile Threat Defense (MTD) 解決方案，來控制行動裝置對公司資源的存取。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1e9b1576-b239-48cc-a672-da6b5fb7be0a
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 43e1bee27d785269d57fa7a35a8f6f9fd9bbbd8c
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67530578"
---
# <a name="integrate-check-point-sandblast-mobile-with-intune"></a>整合 Check Point SandBlast Mobile 與 Intune

## <a name="before-you-begin"></a>開始之前

> [!NOTE] 
> 您需要在 [Check Point SandBlast Mobile MTD 主控台](https://intune-4.eu1.locsec.net/) 中執行下列步驟。

開始整合 Check Point SandBlast Mobile 與 Intune 之前，請確定您有下列項目：

-   Microsoft Intune 訂閱

-   可授與下列權限的 Azure Active Directory 管理員認證：

    -   登入及讀取使用者設定檔

    -   以登入的使用者身分存取目錄

    -   讀取目錄資料

    -   將裝置資訊傳送至 Intune

-   可存取 Check Point SandBlast Mobile MTD 主控台的管理員認證。

### <a name="check-point-sandblast-app-authorization"></a>Check Point SandBlast 應用程式授權

Check Point SandBlast 應用程式授權程序是由下列項目所組成：

-   允許 Check Point SandBlast Mobile 將裝置健全狀況狀態的相關資訊傳送回 Intune。

-   同步處理 CheckPoint SandBlast Mobile 和 Azure AD 註冊群組成員資格，以填入其裝置上的資料庫。

-   允許 Check Point SandBlast 管理員主控台使用 Azure AD 單一登入 (SSO)。

-   允許 Check Point SandBlast 行動應用程式使用 Azure AD SSO 登入。

## <a name="to-set-up-check-point-sandblast-mobile-integration"></a>設定 Check Point SandBlast Mobile 整合

1.  移至 [Check Point SandBlast Mobile MTD 主控台](https://intune-4.eu1.locsec.net/)，以您的認證登入。

2.  按一下 [設定]  索引標籤。

3.  依序選擇 [裝置管理]  和 [設定]  。

4.  從 [MDM Service] (MDM 服務)  下拉式清單中選擇 [Microsoft Intune]  。

5.  一旦將 Microsoft Intune 設為 MDM 服務，[Microsoft Intune 設定]  視窗就會出現，選擇 [Add to my organization] \(新增至我的組織)  接受每個裝置平台：iOS、 Android 和 Windows 授權 Check Point SandBlast Mobile 與 Intune 和 Azure AD 進行通訊。

    ![顯示 Check Point MTD Intune 設定的影像](./media/checkpoint-MTD-1.PNG)

    > [!IMPORTANT]
    > 您必須新增所有裝置平台，才能繼續下一個步驟。

6.  選擇 [接受]  授權 Check Point SandBlast Mobile 應用程式與 Intune 和 Azure Active Directory 進行通訊。

7.  一旦啟用了所有裝置平台，就需要進入 Azure AD 安全性群組。

8.  選擇 [驗證]  ，一旦成功驗證 Azure AD 安全性群組，即選擇 [儲存]  。

## <a name="next-steps"></a>後續步驟

- [設定 Check Point SandBlast Mobile 應用程式](mtd-apps-ios-app-configuration-policy-add-assign.md)
