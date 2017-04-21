---
title: "Microsoft Intune Preview 的已知問題"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解預覽版的已知問題"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/13/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33a6645-a57e-4424-a1e9-0ce932ea83c5
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 24498abc504f05bd22dc7309bc22948292f9b1e6
ms.openlocfilehash: 4c81c17ba1419f0b5bdc4910be7d26a5893b32e0
ms.lasthandoff: 04/13/2017


---

# <a name="known-issues-in-the-microsoft-intune-preview"></a>Microsoft Intune Preview 的已知問題


[!INCLUDE[azure_preview](../includes/azure_preview.md)]


您可以使用本主題了解 Intune 預覽版的已知問題。

若要回報此處未列的 Bug，可[提出支援要求](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)。

若要要求在 Intune 中新增功能，請考慮前往我們的 [Uservoice](https://microsoftintune.uservoice.com/forums/291681-ideas/category/189016-azure-admin-console) 站台填寫報告。

## <a name="groups-created-by-intune-during-migration-might-affect-functionality-of-other-microsoft-products"></a>由 Intune 在移轉期間所建立的群組，可能會影響其他 Microsoft 產品的功能

當您從傳統 Intune 移轉到 Azure 入口網站時，您可能會看到名為 **All Users - b0b08746-4dbe-4a37-9adf-9e7652c0b421** 的新群組。 請注意，此群組包含 Azure Active Directory 中的所有使用者，而非只有 Intune 授權的使用者。 如果您預期有某些不屬於任何群組的現有或新使用者，這可能會對其他 Microsoft 產品造成問題。

## <a name="altering-groups-created-by-intune-during-migration-will-delay-migration"></a>在移轉期間改變由 Intune 所建立的群組，將會延遲移轉

為了準備移轉，您的群組會從 Intune 複製到 Azure AD。 您在傳統 Intune 入口網站中所做的所有進一步變更，都會在 Azure AD 群組中更新。 不過，在 Azure AD 中所做的任何變更，並不會反向同步至傳統 Intune 主控台。 這可能會造成移轉至 Azure 入口網站失敗，並延遲您的移轉。

## <a name="compliance-policies-from-intune-will-not-show-up-in-new-console"></a>來自 Intune 的合規性原則將不會顯示於新的主控台中。 

您在傳統 Intune 入口網站所建立的所有合規性原則都會移轉至 Azure 入口網站，但並不會顯示於 Azure 入口網站中。 這是因為 Azure 入口網站的設計變更所導致。 您在傳統 Intune 入口網站所建立的合規性原則仍然會強制執行，但您必須在傳統入口網站中檢視及編輯它們。
除此之外，您在 Azure 入口網站所建立的新合規性原則將不會顯示於傳統入口網站中。
如需詳細資訊，請參閱[什麼是裝置合規性](https://docs.microsoft.com/intune-azure/set-device-compliance/what-is-device-compliance)。




## <a name="administration-and-accounts"></a>管理與帳戶

全域管理員 (也稱為租用戶管理員) 無須個別的 Intune 或 Enterprise Mobility Suite (EMS) 授權，也可以繼續執行日常的管理工作。 但是，如果全域系統管理員想要使用服務，例如註冊自己的裝置、公司裝置或使用 Intune 公司入口網站，他們就需要有 Intune 或 EMS 授權，像任何其他使用者一樣。

## <a name="apple-enrollment-profile-migration"></a>Apple 註冊設定檔移轉
在接下來的幾個月，Intune 會透過新的 Azure 入口網站啟用管理 Apple 裝置註冊方案和 Apple Configurator 註冊項目。 如果您刪除 Apple 裝置註冊方案的權杖，且沒有上傳更新的權杖，原始權杖就會還原在新的 Azure 入口網站中，成為您移轉 Intune 帳戶的一部分。 若要移除這個權杖，並避免 DEP 註冊，只要刪除 Azure 入口網站中的權杖即可。 

