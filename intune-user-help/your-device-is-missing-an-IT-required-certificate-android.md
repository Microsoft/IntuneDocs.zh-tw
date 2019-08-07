---
title: 您的裝置遺失憑證 | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/29/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f0ba4cbb-ef0a-4335-86bf-f1d006867fa2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: d44af8f40243596bda58d610b369db6f54be6d1e
ms.sourcegitcommit: 3baa9965095bb874d9b8c7a3cbb4aa925ed52cae
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68625129"
---
# <a name="install-missing-certificate-required-by-your-organization"></a>安裝貴組織所需的遺失憑證  

如果您的裝置未在 Intune 註冊，且遺失公司支援人員所要求的特定憑證，您就無法登入公司入口網站應用程式。 當您嘗試登入時，您會看到下列訊息：

![screenshot-error-message-about-missing-certificate](./media/andr-cert_install-1-cert_missing.png)

有兩個選項可讓您嘗試下載所需的憑證, 並註冊您的裝置。 

- 在公司入口網站應用程式中啟用瀏覽器存取。
- 識別公司或學校電腦上遺漏的憑證。 然後搜尋網際網路以下載遺失的憑證。 

請先完成啟用瀏覽器存取的步驟。 之後, 如果您仍然無法註冊您的裝置, 請遵循下列步驟來找出網際網路上的憑證。 

## <a name="enable-browser-access"></a>啟用瀏覽器存取
請完成下列步驟以啟用瀏覽器存取。 啟用存取之後, 公司入口網站將會安裝適當的憑證, 並繼續註冊。    

1. 在公司入口網站應用程式中, 移至右上角並選取功能表。  
2. 選取 [設定]  。  
3. 在 [**啟用瀏覽器存取**] 旁, 選取 [**啟用**]。  
4. 在 [裝置系統管理員] 畫面上, 選取 [**啟用**]。 

## <a name="identify-and-download-the-missing-certificate-through-web-search"></a>透過 web 搜尋識別並下載遺失的憑證
完成這些步驟, 以在您的裝置上手動識別並安裝憑證。  

1. 在電腦上開啟 Internet Explorer。 如果您沒有可用於此用途的電腦，請連絡公司支援人員。 如需公司支援人員的連絡資訊，請查看[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)。

2. 請移至[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)，並使用您的公司或學校認證登入。

3. 在瀏覽器的網址列最右側，選擇看似掛鎖的符號，如下方螢幕擷取畫面所示。

    ![screenshot-internet-explorer-address-bar-padlock-symbol](./media/andr-missing-cert-ie-padlock-symbol.png)

    如果未顯示掛鎖符號，請停止作業，並連絡您公司的支援人員。 鎖頭符號表示您已經安全地登入，因此除非您看到該符號，否則不應該繼續。

4. 按一下 [檢視憑證]  。

    ![screenshot-internet-explorer-view-certificates-button-on-website-identification-dialog](./media/andr-missg-cert-ie-view-cert-button.png)

5. 選擇 [憑證路徑]  索引標籤，然後找出您需要從網際網路取得的憑證。 您可在上述範例螢幕擷取畫面中反白顯示之憑證的相同位置，找到所需憑證的名稱。

6. 使用搜尋引擎 (例如 Bing 或 Google) 搜尋您在上一節中識別的遺失憑證名稱。 憑證可能會以不同的副檔名結束，例如 ".crt" 或 ".pem" 等。

7. 從網站下載根憑證。

8. 下載憑證之後，從您的裝置頂端下拉以開啟通知，然後點選通知清單中的憑證名稱。

4. 在下方螢幕擷取畫面顯示的 [命名憑證]  對話方塊中，接受預設憑證名稱。

5. 請確認 [認證使用]  設為 [用於 VPN 和應用程式]  ，然後點選 [確定]  。

    ![screenshot-certificate-name-dialog-showing-certificate-name](./media/andr-missing-cert-cert-name.png)

6. 關閉公司入口網站應用程式。

7. 重新開啟公司入口網站應用程式。 您現在應該能夠登入公司入口網站應用程式。 如果您需要協助，請連絡您公司的支援人員。

如果您已經遵循相關步驟，卻仍顯示上述相同的「遺失憑證」訊息，可能表示您需要公司支援人員協助安裝其他憑證。 請使用可在[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)取得的連絡資訊來連絡您公司的支援人員以取得協助。
