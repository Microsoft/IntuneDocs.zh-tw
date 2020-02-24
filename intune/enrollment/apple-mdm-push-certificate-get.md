---
title: 取得適用於 Intune 的 Apple MDM Push Certificate
titleSuffix: ''
description: 取得 Apple MDM Push Certificate 以使用 Intune 管理 iOS/iPadOS 裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6f67fcd2-5682-4f9c-8d74-d4ab69dc978c
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 673f63194b46ca7e4dbf1206d363cbe70c6e6098
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414434"
---
# <a name="get-an-apple-mdm-push-certificate"></a>取得 Apple MDM Push Certificate

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

必須要有 Apple MDM Push Certificate，Intune 才能管理 iOS/iPadOS 與 macOS 裝置。 將憑證新增至 Intune 之後，使用者即可使用下列方式來註冊其裝置：

- 公司入口網站應用程式。

- Apple 的大量註冊方法，例如「裝置登記方案」、Apple School Manager 或 Apple Configurator。

如需有關註冊選項的詳細資訊，請參閱[選擇註冊 iOS/iPadOS 裝置的方式](ios-enroll.md)。

當 Push Certificate 到期時，您必須更新它。 進行更新時，請務必使用您最初建立 Push Certificate 時所使用的相同 Apple ID。


## <a name="steps-to-get-your-certificate"></a>取得憑證的步驟
登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)，選擇 [裝置]   > [註冊裝置]   > [Apple 註冊]   > [Apple MDM Push Certificate]  ，然後遵循下列步驟。

### <a name="step-1-grant-microsoft-permission-to-send-user-and-device-information-to-apple"></a>步驟 1： 將權限授與 Microsoft 以將使用者和裝置資訊傳送給 Apple
選取 [我同意]  來將權限授與 Microsoft，以將資料傳送給 Apple。

![未設定 MDM Push 的 [設定 MDM Push Certificate] 畫面。](./media/apple-mdm-push-certificate-get/create-mdm-push-certificate.png)

### <a name="step-2-download-the-intune-certificate-signing-request-required-to-create-an-apple-mdm-push-certificate"></a>步驟 2： 下載建立 Apple MDM Push Certificate 所需的 Intune 憑證簽署要求
選取 [下載您的 CSR]  ，在本機下載並儲存要求檔案。 該檔案可用來向 Apple Push Certificates 入口網站要求信任關係憑證。

### <a name="step-3-create-an-apple-mdm-push-certificate"></a>步驟 3： 建立 Apple MDM Push Certificate
選取 [建立您的 MDM Push Certificate]  ，以前往 Apple Push Certificates 入口網站。 使用您的公司 Apple ID 登入，然後按一下 [建立憑證]  。 選取 [選擇檔案]  ，然後瀏覽至憑證簽署要求檔案，然後選擇 [上傳]  。 在 [確認] 頁面上，選取 [下載]  以下載憑證檔案 (.pem)，然後將檔案儲存在本機。

> [!NOTE]
> 憑證會建立與用來建立憑證之 Apple ID 的關聯。 最佳做法是使用管理工作的公司 Apple ID，並確定信箱由多人監視，例如通訊群組清單。 請不要使用個人 Apple ID。

### <a name="step-4-enter-the-apple-id-used-to-create-your-apple-mdm-push-certificate"></a>步驟 4： 輸入用以建立 Apple MDM Push Certificate 的 Apple ID
請記錄此識別碼，以在需要更新此憑證時提醒您。

### <a name="step-5-browse-to-your-apple-mdm-push-certificate-to-upload"></a>步驟 5： 瀏覽至要上傳的 Apple MDM Push Certificate
前往憑證 (.pem) 檔案，選擇 [開啟]  ，然後選擇 [上傳]  。 Intune 可利用推播憑證，註冊及管理 Apple 裝置。

## <a name="renew-apple-mdm-push-certificate"></a>更新 Apple MDM Push Certificate
Apple MDM Push Certificate 有效期限為一年，且必須每年更新以維護 iOS/iPadOS 與 macOS 裝置管理。 如果您的憑證過期，即無法連絡註冊的 Apple 裝置。

憑證會與用來建立憑證的 Apple ID 相關。 請以用於建立 MDM Push Certificate 的同一個 Apple ID 予以更新。

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)，選擇 [裝置]   > [註冊裝置]   > [Apple 註冊]   > [Apple MDM Push Certificate]  。
2. 選擇 [下載您的 CSR]  ，在本機下載並儲存要求檔案。 該檔案可用來向 Apple Push Certificates 入口網站要求信任關係憑證。
3. 選取 [建立您的 MDM Push Certificate]  ，以前往 Apple Push Certificates 入口網站。 尋找您想要更新的憑證，並選取 [更新]  。
4. 在 [更新 Push Certificate]  畫面上，提供附註以協助您在未來識別憑證，選取 [選擇檔案]  以瀏覽至您下載的新要求檔案，然後選擇 [上傳]  。
   > [!TIP]
   > 可由其 UID 識別憑證。 檢查憑證詳細資料的**主體識別碼**，尋找 UID 的 GUID 部分。 或者，在已註冊的 iOS/iPadOS 裝置上移至 [設定]   > [一般]   > [裝置]  [管理]   > [管理設定檔]   > [詳細資料]   > [管理設定檔]  。 第二個明細項目 [主題]  ，包含可與 Apple Push Certificates 入口網站憑證比對的唯一 GUID。
 
6. 在 [確認]  畫面上，選取 [下載]  並將 .pem 檔案儲存於本機。
7. 在 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 中，選取 [Apple MDM Push Certificate]  瀏覽圖示、選取從 Apple 下載的 .pem 檔案，然後選擇 [上傳]  。

您的 Apple MDM Push Certificate 會顯示為 [使用中]  ，距離到期還有 365 天。
