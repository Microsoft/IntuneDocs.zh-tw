---
# required metadata

title: 您的裝置遺漏必要的憑證 | Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 05/31/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: arnab
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# 您的裝置遺漏必要的憑證
如果您的 Android 裝置未在 Intune 中註冊，且遺漏通常在電話中安裝的憑證，您將無法登入 Android 公司入口網站應用程式。 當您嘗試登入時，您會看到下列訊息︰

![andr-cert-install-cert-missing](./media/andr-cert_install-1-cert_missing.png)

解決此問題並取得所需的憑證︰

1.  在瀏覽器中，瀏覽至這個 [Digicert 憑證頁面](https://www.digicert.com/digicert-root-certificates.htm)。

2.  尋找並下載 Baltimore CyberTrust 根憑證 (https://www.digicert.com/CACerts/BaltimoreCyberTrustRoot.crt)。

3.  若要開啟您的通知，請從頂端向下拖曳，然後點選通知清單中的 [BaltimoreCyberTrustRoot.crt]。

4.  在 [命名憑證] 對話方塊中，接受預設憑證名稱。

5. 請確認 [認證使用] 設為 [用於 VPN 和應用程式]，然後點選 [確定]。

    ![andr-cert-install-add-cert-name](./media/andr-cert_install-2-add_cert_name.png)

6. 關閉網頁瀏覽器和公司入口網站應用程式。

7. 重新開啟公司入口網站應用程式。 您現在應該能夠登入公司入口網站應用程式。 如果您需要協助，請連絡您的 IT 系統管理員。

是否仍需要協助？ 請連絡 IT 系統管理員。 如需其連絡資訊，請查看[公司入口網站](http://portal.manage.microsoft.com)。

<!--HONumber=Jun16_HO2-->


