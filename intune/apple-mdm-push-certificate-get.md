---
title: "取得 Apple MDM Push Certificate"
titleSuffix: Intune on Azure
description: "了解取得 Apple MDM Push Certificate 以利用 Intune 管理 iOS 裝置的步驟。\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a100b436ecf257c1e3886c23f15fa967fb877b7c
ms.sourcegitcommit: 10e3ab2aeb79a1fb2243bef2748ccc003fdd4cc7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2017
---
# <a name="get-an-apple-mdm-push-certificate"></a>取得 Apple MDM Push Certificate

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune 可啟用 iPad、iPhone 和 Mac 電腦的行動裝置管理 (MDM)，且可提供使用者對公司電子郵件和應用程式的存取。 需有 MDM Push 憑證才能管理 iOS 和 Mac 裝置。 將憑證新增至 Intune 之後，使用者即可安裝公司入口網站應用程式來註冊其裝置。 您也可以使用 Apple 的裝置註冊方案來設定公司擁有的 iOS 裝置管理，或使用 Apple Configurator (舉例) 來註冊裝置。 如需有關註冊選項的詳細資訊，請參閱[選擇如何註冊 iOS 裝置](enrollment-method-choose-ios.md)。

## <a name="steps-to-get-your-certificate"></a>取得憑證的步驟
在 Intune 入口網站中，選擇 [裝置註冊] > [Apple 註冊] > [Apple MDM Push Certificate]，然後遵循 Azure 入口網站中的下列步驟進行。

**步驟 1.需要下載 Intune 憑證簽署要求，才可建立 Apple MDM Push Certificate。**<br>
選取 [下載您的 CSR]，在本機下載並儲存要求檔案。 該檔案可用來向 Apple Push Certificates 入口網站要求信任關係憑證。

  ![顯示未設定 MDM Push 之 [設定 MDM Push Certificate] 的螢幕擷取畫面。](./media/create-mdm-push-certificate.png)

**步驟 2.建立 Apple MDM Push Certificate。**<br>
選取 [建立您的 MDM Push Certificate]，以前往 Apple Push Certificates 入口網站。 使用您的公司 Apple ID 登入，然後按一下 [建立憑證]。 選取 [選擇檔案]，然後瀏覽至憑證簽署要求檔案，然後選擇 [上傳]。 在 [確認] 頁面上，選取 [下載] 以下載憑證檔案 (.pem)，然後將檔案儲存在本機。

> [!NOTE]
> 憑證會與用來建立憑證的 Apple ID 相關。 最佳做法是對管理工作使用公司 Apple ID。 請不要使用個人 Apple ID。

**步驟 3.輸入用以建立 Apple MDM Push Certificate 的 Apple ID。**<br>
請記錄此識別碼，以在需要更新此憑證時提醒您。

**步驟 4.瀏覽至 Apple MDM Push Certificate 以進行上傳。**<br>
前往憑證 (.pem) 檔案，選擇 [開啟]，然後選擇 [上傳]。 Intune 可利用推播憑證，註冊及管理 Apple 裝置。

## <a name="renew-apple-mdm-push-certificate"></a>更新 Apple MDM Push Certificate
Apple MDM Push Certificate 有效期限為一年，必須每年更新以維護 iOS 及 macOS 裝置管理。 如果您的憑證過期，即無法連絡註冊的 Apple 裝置。

憑證會與用來建立憑證的 Apple ID 相關。 請以用於建立 MDM Push Certificate 的同一個 Apple ID 予以更新。

> [!NOTE]
> 憑證會與用來建立憑證的 Apple ID 相關。 最佳做法是對管理工作使用公司 Apple ID。 請不要使用個人 Apple ID。

1. 在 Intune 入口網站中，選擇 [裝置註冊] > [Apple 註冊]，然後選擇 [Apple MDM Push Certificate]。
2. 選擇 [下載您的 CSR]，在本機下載並儲存要求檔案。 該檔案可用來向 Apple Push Certificates 入口網站要求信任關係憑證。
3. 尋找您想要更新的憑證，並選取 [更新]。
4. 在 [更新 Push Certificate] 畫面上，提供附註以協助您在未來識別憑證，選取 [選擇檔案] 以瀏覽至您下載的新要求檔案，然後選擇 [上傳]。
5. 在 [確認] 畫面上，選取 [下載] 並將 .pem 檔案儲存於本機。
6. 在 Azure Intune 入口網站中，選取 **Apple MDM Push Certificate** 瀏覽圖示，選取從 Apple 下載的 .pem 檔案，然後選擇 [上傳]。

您的 Apple MDM Push Certificate 會顯示為 [使用中]，距離到期還有 365 天。
