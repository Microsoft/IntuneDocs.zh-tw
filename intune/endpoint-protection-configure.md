---
title: 在 Microsoft Intune 中設定 Endpoint Protection 設定 - Azure | Microsoft Docs
description: 您可以在於 Microsoft Intune 中建立 macOS 或 Windows 10 裝置設定檔時，建立 Endpoint Protection 設定。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 5/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
mr.reviewer: karthib
ms.openlocfilehash: 1a5cd898545bae51395352d5cf1e7b1ee9bd22dd
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67883239"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>在 Intune 中新增 Endpoint Protection 設定

透過 Intune，您可以使用裝置組態設定檔，來管理裝置上的一般端點保護安全性功能，包括：
- 防火牆 
- BitLocker
- 允許和封鎖應用程式  
- Windows Defender 和加密

例如，您可以建立一個只允許 macOS 使用者從 Mac App Store 安裝應用程式的 Endpoint Protection 設定檔。 或者，在於 Windows 10 裝置上執行應用程式時，啟用 Windows SmartScreen。

建立設定檔之前，請檢閱下列文章，這些文章將詳細說明 Intune 可基於每個支援平台來管理的端點保護設定： 
- [macOS 設定](endpoint-protection-macos.md)
- [Windows 10 設定](endpoint-protection-windows-10.md)

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>建立包含 Endpoint Protection 設定的裝置設定檔

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 選取 [裝置設定]   > [設定檔]   > [建立設定檔]  。
4. 輸入 Endpoint Protection 設定檔的 [名稱]  和 [描述]  。
5. 從 [平台]  下拉式清單中，選取要套用自訂設定的裝置平台。 您目前可選擇下列平台之一，進行裝置限制設定︰
   - **macOS**
   - **Windows 10 及更新版本**
6. 從 [設定檔類型]  下拉式清單中，選擇 [Endpoint Protection]  。 
7. 您可設定的設定會視您選擇的平台而不同。 請參閱：
   - [macOS 設定](endpoint-protection-macos.md)
   - [Windows 10 設定](endpoint-protection-windows-10.md)  

8. 設定適用的設定之後，選取 [建立設定檔]  頁面上的 [建立]  。

   設定檔隨即建立，並出現在 [設定檔清單] 頁面上。 若要將此設定檔指派給群組，請參閱[指派裝置設定檔](device-profile-assign.md)。


## <a name="next-steps"></a>後續步驟  

若要將設定檔指派給群組，請參閱[指派裝置設定檔](device-profile-assign.md)。
