---
title: "針對 Intune 取得 Apple DEP 憑證"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰設定及上傳 MDM 推播憑證的指示，其為在 Intune 中管理 Apple 裝置的必要條件。 "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/03/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e5c79c5-2883-4841-9be6-74cba16ee447
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 8edc42bb86e3856ac6568cc3c1acc5d757978e79
ms.lasthandoff: 02/18/2017

---

# <a name="get-an-apple-dep-certificate"></a>取得 Apple DEP 憑證

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

您必須先從 Apple 取得 DEP 權杖，才能為公司擁有的 iOS 裝置註冊 Apple 的「裝置註冊方案」(DEP)。 此權杖可讓 Intune 同步處理貴公司所擁有的 DEP 參與裝置資訊。 它也允許 Intune 將註冊設定檔上傳至 Apple，並將這些設定檔指派給裝置。

若要使用 DEP 來管理屬公司擁有的 iOS 裝置，您的組織必須加入 Apple DEP，並透過該方案購得裝置。 此網址提供該程序的詳細資料：https://deploy.apple.com。 這個方案的優點包括不需要使用 USB 纜線將每部裝置連接到電腦，即可進行裝置的無操作安裝作業。

> [!NOTE]
> 此注意事項只適用於從 Intune 管理主控台移轉至 Azure 入口網站的 Intune 客戶。 若已於遷移期間從 Intune 管理主控台刪除了 Apple DEP 權杖，可能會發現到 DEP 權杖已還原至您的 Intune 帳戶。 如果發生此情況，只要從 Azure 入口網站刪除該 DEP 權杖即可。

## <a name="steps-to-get-the-apple-dep-certificate"></a>取得 Apple DEP 憑證的步驟
在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。 在 Intune 刀鋒視窗上，選擇 [註冊裝置]  >  [Apple DEP 權杖]，並依照 Azure 入口網站中的步驟編號進行，如下所示。

**步驟 1.下載建立 Apple DEP 權杖所需的 Intune 公開金鑰憑證。**<br>
選取 [下載您的公開金鑰憑證]，在本機下載並儲存加密金鑰 (.pem) 檔案。 這個 .pem 檔案會用於向 Apple 裝置註冊程式入口網站要求信任關係憑證。

**步驟 2.從正確的 Apple 網站下載 Apple DEP 權杖。**<br>
選取 [透過 Apple 部署計劃建立 DEP 權杖][](https://deploy.apple.com)(https://deploy.apple.com)，並以您的公司 Apple ID 登入。 您必須使用此 Apple ID 來更新 DEP 權杖。

   a.  在[裝置註冊方案入口網站](https://deploy.apple.com)中，移至 [裝置註冊方案] &gt; [管理伺服器]，然後選擇 [新增 MDM 伺服器]。

   b。  輸入 [MDM 伺服器名稱]，然後選擇 [下一步] 。 您可參考這個伺服器名稱，以識別行動裝置管理 (MDM) 伺服器， 但它不是 Microsoft Intune 伺服器的名稱或 URL。

   c.  [新增 &lt;伺服器名稱&gt;] 對話方塊隨即開啟。 選擇 [選擇檔案...] 以上傳 .pem 檔案，然後選擇 [下一步]。

   d.  [新增 &lt;伺服器名稱&gt;] 對話方塊會顯示 [您的伺服器權杖] 連結。 將伺服器權杖 (.p7m) 檔案下載到您的電腦，然後選擇 [完成]。

    This certificate (.p7m) file is used to establish a trust relationship between Intune and Apple’s Device Enrollment Program servers.

**步驟 3.輸入用以建立 Apple DEP 權杖的 Apple ID。此識別碼可用以更新您的 Apple DEP 權杖。**

**步驟 4.瀏覽至 Apple DEP 權杖，以進行上傳。Intune 會自動與您的 DEP 帳戶同步。**<br>
前往憑證 (.pem) 檔案，選擇 [開啟]，然後選擇 [上傳]。 使用推播憑證，透過將原則推送到已註冊的行動裝置，Intune 即可註冊和管理 iOS 裝置。

