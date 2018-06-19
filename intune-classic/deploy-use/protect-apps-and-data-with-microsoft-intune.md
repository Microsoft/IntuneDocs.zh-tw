---
title: 保護應用程式和資料
description: 本主題說明各種 Intune 功能和能力，可供您用來協助保護您的公司應用程式與資料。
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5c46e188-87eb-4ce2-b184-24809e8bf783
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2a05444c757b8e99ca0b897acfcd6238d960aeb2
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31017541"
---
# <a name="protect-apps-and-data-with-microsoft-intune"></a>使用 Microsoft Intune 保護應用程式和資料

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune 透過多重技術層級保護公司資料。 在身分識別層，條件式存取保護服務的存取，只允許從受管理和相容的裝置才能存取。 在用戶端應用程式層中，行動應用程式管理 (MAM) 可防止資料移到未受保護的應用程式或儲存體位置，並於裝置遺失或遭竊時清除資料，以此來防止資料遺失。 建議您一起使用這兩個保護層來協助保護資料安全，同時保留您的行動工作者的生產力。

保護公司資料的第一個重要步驟，便是實作條件式存取。 透過確定用來存取資料的裝置使用安全性保護 (例如強式密碼和加密) 且未進行越獄，您可以做到這點。 Intune 可讓您設定在允許裝置存取公司電子郵件和資料之前，裝置必須遵守的條件。

[條件式存取](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)取決於可在 Intune 中設定的兩種原則類型：
- 您可以使用[合規性原則](introduction-to-device-compliance-policies-in-microsoft-intune.md)來判斷裝置的合規性。 這些原則會評估下列設定和條件：
  - PIN 和密碼︰您可以建立要求密碼以解除鎖定裝置、密碼複雜性需求和其他密碼設定的規則。
  - 加密：您可以限制對加密裝置的存取。
  - 當裝置未經過破解或刷機︰Intune 可以偵測已註冊的裝置是否經過破解。 您可以設定原則來封鎖類似裝置的存取。
- 您可以針對 Exchange Online 或 SharePoint Online 等特定服務來設定[條件式存取原則](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)。 針對每項服務，您可以定義應該套用這些原則的使用者群組。 例如，您可以確保財務部門的所有人只能從已註冊且相容的裝置存取公司電子郵件。

保護公司資源的存取只是保護公司資料的第一步。 在裝置存取資料之後，您仍需要有保護資料的能力。 資料現在可以複製、移動、儲存到不同的位置，或共用。 Intune 可讓您建立如下的一組規則來限制資料移動，以解決這個問題︰
- 阻止複製和貼上，或防止資料傳輸到工作環境之外。
- 禁止備份到個人雲端儲存體，以及禁止「另存新檔」。
- 要求 PIN/密碼或公司認證，以保護應用程式存取。
- 在 Intune 受管理瀏覽器中開啟所有網頁連結。

這幾組規則稱為[行動應用程式管理 (MAM) 原則](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)。 您可以將 MAM 原則套用到可能是或可能不是由您管理之裝置上執行的應用程式。  

您可以使用 MAM 原則於下列裝置，以保護公司資料：**已在 Intune 中註冊**的裝置、**已在其他協力廠商行動裝置管理 (MDM) 解決方案中註冊並由其管理**的裝置，或者**未在任何 MDM 解決方案中註冊**的裝置 (例如員工所擁有的裝置)。

若要讓應用程式與 MAM 原則產生關聯，應用程式必須納入 Microsoft Intune 應用程式軟體開發套件 (SDK)，或使用應用程式包裝工具。

Microsoft Office 之類的應用程式已內建 Intune App SDK。 您可以移至 Microsoft Intune 應用程式夥伴頁面上的 [Microsoft Intune 行動應用程式庫](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)，查看受支援應用程式的完整清單。 選擇應用程式來查看支援的案例、平台和應用程式是否支援多重身分識別。

您也可以[啟用自訂建置的企業營運應用程式](/intune/apps-prepare-mobile-application-management)來搭配 MAM 原則一起使用。

如果裝置遺失或遭竊，或使用者已不再與您的公司合作，則除了限制資料移動以外，您還可以[選擇性地清除公司資料](wipe-managed-company-app-data-with-microsoft-intune.md)，只留下個人資料。
