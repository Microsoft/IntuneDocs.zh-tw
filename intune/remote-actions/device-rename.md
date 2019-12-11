---
title: 使用 Microsoft Intune 重新命名裝置 - Azure | Microsoft Docs
description: 使用 Microsoft Intune 重新命名裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0f5ee9a0fe27c3cf9de758fd7155dbd127fb1e5e
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "73712225"
---
# <a name="rename-a-device-in-intune"></a>在 Intune 中重新命名裝置

**重新命名裝置**動作可讓您重新命名已在 Intune 中註冊的裝置。 裝置在 Intune 中和裝置上的名稱都會變更。

您可以重新命名下列類型的裝置：
- 公司擁有的 Windows 
- 受 iOS 監督
- 公司擁有的 MacOS 10

這項功能目前不支援重新命名混合式 Azure AD Windows 裝置。

## <a name="rename-a-device"></a>重新命名裝置

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
3. 選擇 [裝置]   > [所有裝置]  > 選擇裝置 > [更多]   > [重新命名裝置]  。
4. 在 [重新命名裝置]  刀鋒視窗中，於文字方塊中輸入新名稱。 您可以使用字母、數字和連字號。 名稱必須包含至少一個字母或連字號。
5. 如果要讓裝置在重新命名之後重新啟動，請選擇 [重新命名後重新啟動]  旁邊的 [是]  。
6. 選擇 [重新命名]  。

## <a name="windows-device-rename-rules"></a>Windows 裝置重新命名規則
重新命名 Windows 裝置時，新名稱必須遵循這些規則：
- 15 個字元或更少 (必須小於或等於 63 個位元組，不包括尾端的 NULL 字元)
- 非 Null 或空字串
- 允許的 ASCII：字母 (a-z, A-Z)、數字 (0-9) 和連字號
- 允許的 Unicode：字元 >= 0x80，必須是有效的 UTF8，必須是 IDN 可映射 (也就是繼 RtlIdnToNameprepUnicode 之後；請參閱 RFC 3492)
- 名稱不能僅包含數字
- 名稱中不能有空格
- 不允許的字元：{ | } ~ [ \ ] ^ ' : ; < = > ? & @ ! " # $ % ` ( ) + / , . _ *)


## <a name="next-steps"></a>後續步驟

若要查看 [重新命名]  裝置動作的狀態，請檢查裝置的 [概觀]  頁面。
