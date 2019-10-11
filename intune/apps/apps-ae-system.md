---
title: 將 Android Enterprise 系統應用程式新增至 Microsoft Intune
titleSuffix: ''
description: 了解如何將 Enterprise 系統應用程式新增至 Microsoft Intune。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c07ce82bbc056e1d76abeb5d31bf57e0973fad6e
ms.sourcegitcommit: bdf948be824cf5390d5166a277f389f3785c81f9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71960885"
---
# <a name="add-android-enterprise-system-apps-to-microsoft-intune"></a>將 Android Enterprise 系統應用程式新增至 Microsoft Intune

在您將應用程式指派給一部裝置或一群使用者之前，必須先將該應用程式新增到 Microsoft Intune。 Android Enterprise 裝置上支援系統應用程式。 您可以針對 [Android Enterprise 專用裝置](../enrollment/android-kiosk-enroll.md)或[完全受控裝置](../enrollment/android-fully-managed-enroll.md)啟用系統應用程式。

## <a name="add-the-app"></a>新增應用程式

您可以採取下列步驟，從 Azure 入口網站將 Android Enterprise 系統應用程式新增至 Intune：

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 在 [Intune]  窗格中，選取 [用戶端應用程式]   > [應用程式]   > [新增]  。
3. 在 [新增應用程式]  窗格中的可用 [其他]  類型底下，選取 [Android Enterprise 系統應用程式]  。
4. 若要設定應用程式資訊，選取 [設定]  ，然後提供下列資訊：
    - **應用程式名稱**：輸入應用程式的名稱。
    - **發行者**：輸入應用程式發行者的名稱。  
    - **套件名稱**：輸入套件名稱。 Intune 將會驗證套件名稱是否有效。
5. 選取 [確定]  。
6. 選取 [新增]  。

> [!NOTE]
> 您必須使用裝置的 OEM 來尋找您想要啟用/停用之應用程式的套件名稱。

您建立的應用程式即會顯示在應用程式清單中，而您可從中將該應用程式指派給所選的群組。 

Android Enterprise 系統應用程式將啟用或停用已屬於平台一部分的應用程式。 若要啟用應用程式，將系統應用程式指派為 [必要]  。 若要停用應用程式，將系統應用程式指派為 [解除安裝]  。 無法將系統應用程式指派為可供使用者使用。


## <a name="next-steps"></a>後續步驟

- [將應用程式指派給群組](apps-deploy.md)
