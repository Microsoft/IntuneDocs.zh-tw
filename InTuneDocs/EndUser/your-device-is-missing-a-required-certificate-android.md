---
title: "您的裝置遺漏必要的憑證 | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9081b1d8-50e8-4bc2-ba37-766421364213
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: arnab
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 016449720f6e77b8862fcaa232d252eefa8b20b3
ms.openlocfilehash: 27b3e3d4aefade368d900df95454c3d02e37bed4


---


# <a name="your-device-is-missing-a-required-certificate"></a>您的裝置遺漏必要的憑證


## <a name="your-device-is-missing-a-certificate-that-usually-comes-installed-on-your-phone"></a>您的裝置遺失通常已預先安裝於手機上的憑證
如果您的 Android 裝置未在 Intune 中註冊，且遺漏通常在電話中安裝的憑證，您將無法登入 Android 公司入口網站應用程式。 當您嘗試登入時，您會看到下列訊息︰

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

若要解決此問題並取得所需的憑證︰

1.  在瀏覽器中，前往這個 [Digicert 憑證頁面](https://www.digicert.com/digicert-root-certificates.htm)。

2.  尋找並下載 Baltimore CyberTrust 根憑證 (https://www.digicert.com/CACerts/BaltimoreCyberTrustRoot.crt)。

3.  若要開啟您的通知，請從頂端向下拖曳，然後點選通知清單中的 [BaltimoreCyberTrustRoot.crt]。

4.  在 [命名憑證] 對話方塊中，接受預設憑證名稱。

5. 請確認 [認證使用] 設為 [用於 VPN 和應用程式]，然後點選 [確定]。

    ![screenshot-certificate-name-dialog-showing-baltimore-certificate-name](./media/andr-cert_install-2-add_cert_name.png)

6. 關閉網頁瀏覽器和公司入口網站應用程式。

7. 重新開啟公司入口網站應用程式。 您現在應該能夠登入公司入口網站應用程式。 如果您需要協助，請連絡您的 IT 系統管理員。

## <a name="your-device-is-missing-a-certificate-required-by-your-it-admin"></a>您的裝置遺失 IT 系統管理員所需的憑證
如果您的 Android 裝置未在 Intune 註冊，並遺失 IT 系統管理員所需的特定憑證，您就無法登入 Android 公司入口網站應用程式。 當您嘗試登入時，您會看到下列訊息：

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

>[!NOTE]
> 如果您有看到「遺失憑證」的訊息，並已遵循[您的裝置遺失通常已預先安裝於手機上的憑證](#your-device-is-missing-a-certificate-that-usually-comes-installed-on-your-phone)中的步驟，請不用擔心。 那是與此不同的訊息與憑證，因此請繼續並遵循這一節中的步驟，以取得遺失的憑證。

若要修正此問題，並取得所需的憑證，您必須執行兩個主要步驟：

- 透過公司或學校電腦上尋找以識別遺失的憑證。
- 使用您的裝置從網際網路下載遺失的憑證。

### <a name="identify-the-missing-certificate-by-looking-on-a-company-or-school-pc"></a>透過公司或學校電腦上尋找以識別遺失的憑證

1. 在電腦上開啟 Internet Explorer。 如果您沒有可用於此用途的電腦，請連絡 IT 系統管理員。 如需 IT 系統管理員的連絡資訊，請查看[公司入口網站](http://portal.manage.microsoft.com)。

2. 請移至[公司入口網站](http://portal.manage.microsoft.com)，並使用您的公司或學校認證登入。

3. 在瀏覽器的網址列最右側，選擇看似掛鎖的符號，如下方螢幕擷取畫面所示。

    ![screenshot-internet-explorer-address-bar-padlock-symbol](./media/andr-missing-cert-ie-padlock-symbol.png)

    如果未顯示掛鎖符號，請停止作業並連絡您的 IT 系統管理員。 鎖頭符號表示您已經安全地登入，因此除非您看到該符號，否則不應該繼續。

4. 按一下 [檢視憑證]。

    ![screenshot-internet-explorer-view-certificates-button-on-website-identification-dialog](./media/andr-missg-cert-ie-view-cert-button.png)

5. 在 [憑證] 對話方塊中，選擇 [憑證路徑] 索引標籤，然後找出您需要從網際網路取得的憑證。 您可在上述範例螢幕擷取畫面中反白顯示之憑證的相同位置，找到所需憑證的名稱。

### <a name="download-and-install-the-missing-certificate-on-your-android-mobile-device"></a>在您的 Android 行動裝置上下載並安裝遺失的憑證

1. 使用搜尋引擎 (例如 Bing 或 Google) 搜尋您在上一節中識別的遺失憑證名稱。 憑證可能會以不同的副檔名結束，例如 ".crt" 或 ".pem" 等。

2. 從網站下載根憑證。

3. 下載憑證之後，從您的裝置頂端下拉以開啟通知，然後點選通知清單中的憑證名稱。

4. 在下方螢幕擷取畫面顯示的 [命名憑證] 對話方塊中，接受預設憑證名稱。

5. 請確認 [認證使用] 設為 [用於 VPN 和應用程式]，然後點選 [確定]。

    ![screenshot-certificate-name-dialog-showing-certificate-name](./media/andr-missing-cert-cert-name.png)

6. 關閉公司入口網站應用程式。

7. 重新開啟公司入口網站應用程式。 您現在應該能夠登入公司入口網站應用程式。 如果您需要協助，請連絡您的 IT 系統管理員。

如果您已經遵循相關步驟，卻仍顯示上述相同的「遺失憑證」訊息，可能表示您需要 IT 系統管理員協助安裝其他憑證。 請連絡 IT 系統管理員，並提供這個 [Android 憑證問題](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues)的連結，其中包含協助修正此問題的步驟。



<!--HONumber=Oct16_HO2-->


