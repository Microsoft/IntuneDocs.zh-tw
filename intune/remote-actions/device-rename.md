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
ms.openlocfilehash: 11b339a3e94e60db43e8237d9f3d2c729b48a57d
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/17/2020
ms.locfileid: "77413618"
---
# <a name="rename-a-device-in-intune"></a>在 Intune 中重新命名裝置

**重新命名裝置**動作可讓您重新命名已在 Intune 中註冊的裝置。 裝置在 Intune 中和裝置上的名稱都會變更。

您可以重新命名下列類型的裝置：
- 公司擁有的 Windows 
- iOS/iPadOS 受監管
- 公司擁有的 MacOS 10

這項功能目前不支援重新命名混合式 Azure AD Windows 裝置。

## <a name="rename-a-device"></a>重新命名裝置

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
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
