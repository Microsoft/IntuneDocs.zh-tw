---
title: "在 Intune 中設定註冊限制 | Intune Azure 預覽版 | Microsoft Docs"
description: "Intune Azure 預覽版︰在 Intune 中限制不同平台的註冊及裝置註冊限制。 "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 11/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: 1bdefce35c20ce24b94ee701a2d13b5408f435ce

---

# <a name="set-enrollment-restrictions"></a>設定註冊限制 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

您可以藉由指定允許的平台，限制可以在 Intune 中註冊的裝置類型。 您也可以設定使用者能夠註冊的裝置數上限。

## <a name="set-device-type-restrictions"></a>設定裝置類型的限制

1. 在 Azure 入口網站中，選擇 [更多服務]，再於文字方塊中輸入 **Intune**，然後選擇 [其他]  >  [Intune]。

2. 在 [Intune] 刀鋒視窗上選擇 [註冊裝置]，然後選擇 [註冊限制]。

3. 從 [裝置類型限制] 下選取 [預設]。

4. 在 [所有使用者] 刀鋒視窗中選取 [平台]。

5. 對於可以在 Intune 中註冊的平台，請選取 [允許]。 對於您要禁止註冊的平台，請選取 [封鎖]。

6. 選取 [儲存]。

7. 選取 [平台設定]。

8. 選擇要允許或禁止註冊個人擁有的 iOS 裝置註冊。

9. 選取 [儲存]。

## <a name="set-device-limit-restrictions"></a>設定裝置限制

1. 在 Azure 入口網站的 [Intune] 刀鋒視窗上選擇 [註冊裝置]，然後選擇 [註冊限制]。

2. 從 [裝置限制] 下選取 [預設]。

3. 在 [所有使用者] 刀鋒視窗中選取 [裝置限制]。

4. 選取使用者能夠註冊的裝置數上限，然後按一下 [儲存]。



<!--HONumber=Feb17_HO1-->


