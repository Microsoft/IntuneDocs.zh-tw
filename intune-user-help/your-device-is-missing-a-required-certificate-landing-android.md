---
title: "您的裝置遺失必要的憑證 | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213
searchScope:
- User help
ROBOTS: 
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 910fe2bc4e616c3b60d351efaffe173f58c04bc6
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---


# <a name="your-device-is-missing-a-required-certificate"></a>您的裝置遺漏必要的憑證

## <a name="whats-a-certificate"></a>何謂憑證？

[密碼編譯](https://technet.microsoft.com/library/cc962030.aspx)是提供資訊安全的科學。 密碼編譯在傳統上是用於傳遞加密訊息，以[確保通訊保持機密](https://technet.microsoft.com/library/cc962019.aspx)。 最簡單的密碼編譯形式是，它會取代或調換字母以建立加密訊息，使其變成無意義、無規則，或隱藏的訊息。 只有擁有解密金鑰 (或「憑證」) 的人才能將加密訊息轉換回可閱讀的原始格式。 Android 裝置會搭配使用憑證與 Intune，以確保裝置和組織資源之間在空中傳送的通訊 (如電子郵件與文件) 能夠保持安全。

## <a name="fixing-certificate-issues"></a>修正憑證問題

如果您的 Android 裝置未在 Intune 註冊，且遺失 IT 系統管理員要求的特定憑證，您就無法登入公司入口網站應用程式。 當您嘗試登入時，您會看到下列訊息：

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

您應該先查看裝置是否[遺失通常已預先安裝的憑證](your-device-is-missing-a-preinstalled-certificate-android.md)。

如果仍然有問題，您的 IT 系統管理員可能會[要求您安裝第二個憑證以獲得額外的安全性](your-device-is-missing-an-IT-required-certificate-android.md)。

是否仍需要協助？ 請連絡 IT 系統管理員。 如需連絡資訊，請查看[公司入口網站](http://portal.manage.microsoft.com)。

