---
title: "使用 Intune 從遠端重新啟動裝置"
titlesuffix: Azure portal
description: "了解如何使用重新啟動裝置動作，從遠端重新啟動裝置。"
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 11/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c707e0c4-391a-4bad-9dfd-9a7799c48dd5
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9afe804d2f9e48e27ced4bd92959cd065f6ec89a
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="remotely-restart-devices-with-intune"></a>使用 Intune 從遠端重新啟動裝置


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**重新啟動**裝置動作會導致您選擇的裝置重新啟動。 重新啟動時不會自動通知裝置擁有者，因此將會遺失工作。

## <a name="supported-platforms"></a>支援的平台

- Windows - 支援 Windows 8.1 和更新版本
- Windows Phone - 支援 Windows Phone 8.1 和更新版本
- iOS - 支援

    > [!Note]  
    > 此命令需要受監督的裝置和**裝置鎖定**存取權限。 裝置隨即重新啟動。 密碼鎖定的 iOS 裝置重新啟動後，不會重新加入 Wi-Fi 網路；重新啟動後，它們可能無法與伺服器通訊。
- macOS - 不支援
- Android - 不支援

## <a name="how-to-restart-a-device"></a>如何重新啟動裝置

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置]。
4. 在 [裝置和群組] 刀鋒視窗中選擇 [所有裝置]。
5. 從您管理的裝置清單中，選擇裝置，然後選擇 [重新啟動] 裝置遠端動作。

## <a name="next-steps"></a>接下來的步驟

若要查看您剛採取的動作狀態，請在 [裝置和群組] 刀鋒視窗中，選擇 [裝置動作]。
