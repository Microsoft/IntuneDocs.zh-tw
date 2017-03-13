---
title: "您的裝置遺失憑證 | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: df973b18-9166-417d-8aa3-49edd2bda256
searchScope:
- User help
ROBOTS: 
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: d6fcfac7c8bd469f5163ec9b4017ae8c3d486428
ms.openlocfilehash: e0aaa48e46e547d4853478fdbb80711700a9c22a
ms.lasthandoff: 01/05/2017

---

# <a name="your-android-device-is-missing-a-certificate-that-usually-comes-installed-on-your-phone"></a>您的 Android 裝置遺失通常已預先安裝於手機上的憑證

如果您的裝置未在 Intune 中註冊，且遺失通常已安裝在手機上的憑證，您將無法登入公司入口網站應用程式。 當您嘗試登入時，您會看到下列訊息︰

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

您可以從 [Digicert 的憑證頁面](https://www.digicert.com/digicert-root-certificates.htm)取得所需的憑證來修正此問題。

1. 尋找並下載 __Baltimore CyberTrust Root__ 憑證。 您也可以直接從[這裡](https://www.digicert.com/CACerts/BaltimoreCyberTrustRoot.crt)下載憑證。

2. 從畫面頂端向下拖曳以顯示最近的通知清單，然後點選 [BaltimoreCyberTrustRoot.crt]。

3. 裝置會要求您 [為憑證命名]。 請勿變更所顯示的預設憑證名稱。

4. 請確認 [認證使用] 設為 [用於 VPN 和應用程式]，然後點選 [確定]。

    ![screenshot-certificate-name-dialog-showing-baltimore-certificate-name](./media/andr-cert_install-2-add_cert_name.png)

5. 關閉瀏覽器和公司入口網站應用程式。

6. 重新開啟公司入口網站應用程式。 您現在應該能夠登入公司入口網站應用程式。 如果您還是無法使用公司入口網站應用程式，請使用[公司入口網站](http://portal.manage.microsoft.com)提供的資訊來連絡您的 IT 系統管理員以取得進一步指示。

>[!NOTE]
> 如果安裝憑證無法解決問題，且您看到不同的「遺失憑證」訊息，您將需要採取額外的步驟以[安裝遺失的憑證](your-device-is-missing-an-IT-required-certificate-android.md)。

是否仍需要協助？ 請連絡 IT 系統管理員。 如需連絡資訊，請查看[公司入口網站](http://portal.manage.microsoft.com)。

