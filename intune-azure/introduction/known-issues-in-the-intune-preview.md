---
title: "Microsoft Intune Preview 的已知問題"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解預覽版的已知問題"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/06/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: b6c245d60c661c04b4c4d29c9bdcdd752254d978
ms.openlocfilehash: ec3f87994b19591bda4ec201eac3c839798d634c
ms.lasthandoff: 03/15/2017


---

# <a name="known-issues-in-the-microsoft-intune-preview"></a>Microsoft Intune Preview 的已知問題


[!INCLUDE[azure_preview](../includes/azure_preview.md)]


您可以使用本主題了解 Intune 預覽版的已知問題。

若要回報此處未列的 Bug，可[提出支援要求](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)。

若要要求在 Intune 中新增功能，請考慮前往我們的 [Uservoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console) 站台填寫報告。

## <a name="administration-and-accounts"></a>管理與帳戶

- 全域管理員 (也稱為租用戶管理員) 無須個別的 Intune 或 Enterprise Mobility Suite (EMS) 授權，也可以繼續執行日常的管理工作。 但是，如果全域系統管理員想要使用服務，例如註冊自己的裝置、公司裝置或使用 Intune 公司入口網站，他們就需要有 Intune 或 EMS 授權，像任何其他使用者一樣。

## <a name="apple-enrollment-profile-migration"></a>Apple 註冊設定檔移轉
- 在接下來的幾個月，Intune 會透過新的 Azure 入口網站啟用管理 Apple 裝置註冊方案和 Apple Configurator 註冊項目。 如果您刪除 Apple 裝置註冊方案的權杖，且沒有上傳更新的權杖，原始權杖就會還原在新的 Azure 入口網站中，成為您移轉 Intune 帳戶的一部分。 若要移除這個權杖，並避免 DEP 註冊，只要刪除 Azure 入口網站中的權杖即可。 

