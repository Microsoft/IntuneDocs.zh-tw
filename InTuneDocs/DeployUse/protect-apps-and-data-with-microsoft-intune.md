---
# required metadata

title: 保護應用程式和資料 | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 5c46e188-87eb-4ce2-b184-24809e8bf783

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: chrisgre
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用 Microsoft Intune 保護應用程式和資料


Intune 透過多重技術層級保護公司資料。  在身分識別層，條件式存取保護服務的存取，只允許從受管理和相容的裝置才能存取。  在用戶端應用程式層中，行動應用程式管理 (MAM) 可防止資料移到未受保護的應用程式或儲存體位置，並於裝置遺失或遭竊時清除資料，以此來防止資料遺失。  這兩種保護層級應該一起使用，以保護資料，同時保持行動工作者的生產力。

保護公司資料最重要的第一步是實作條件式存取，確保用來存取該資料的裝置已使用安全性保護，例如強式密碼、加密和未進行 JB 破解。 Microsoft Intune 可讓您設定裝置必須符合的條件，之後裝置才能存取公司電子郵件和資料。

[條件式存取](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)取決於可在 Intune 中設定的兩種原則：
- [相容性原則](introduction-to-device-compliance-policies-in-microsoft-intune.md)判斷裝置是否相容。 這些原則會評估下列設定和條件：
  - PIN 和密碼：您可以建立規則來要求解除鎖定裝置前需要密碼、密碼的複雜性需求，以及其他密碼設定。
  - 加密：您可以限制對加密裝置的存取。
  - 裝置未進行 JB 或 Root 破解：Intune 可以偵測已註冊的裝置是否進行 JB 破解，而您可以設定原則來封鎖對這類裝置的存取。
- [條件式存取原則](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)是針對 Exchange Online 或 SharePoint Online 等特定服務所設定。 針對每項服務，您可以定義應該套用這些原則的使用者群組。 例如，您可以確保財務部門的所有人只能從已註冊且相容的裝置存取公司電子郵件。

保護公司資源的存取只是保護公司資料的第一步。 您還必須能夠保護裝置上已被存取的資料。 資料現在可以複製、移動、儲存到不同的位置，或共用。 Intune 可讓您建立如下的一組規則來限制資料移動，以解決這個問題︰
- 阻止複製和貼上，或防止資料傳輸到工作環境之外。
- 防止備份到個人雲端儲存體、防止「另存新檔」。
- 要求 PIN/密碼或公司認證，以保護應用程式存取。
- 在 Intune 受管理瀏覽器中開啟所有網頁連結。

這幾組規則稱為[行動應用程式管理 (MAM) 原則](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)。  不論您是否管理裝置，MAM 原則可以套用至這些裝置上執行的應用程式。  在 Intune 中註冊的裝置上、由其他協力廠商 MDM 註冊和管理的裝置上，或您未管理的裝置上 (例如員工個人裝置)，您可以使用 MAM 原則來保護公司資料。

若要讓應用程式與 MAM 原則產生關聯，應用程式必須納入 Microsoft Intune 應用程式軟體開發套件 (SDK)，或使用應用程式包裝工具。

Microsoft Office 之類的應用程式已內建應用程式 SDK。 在 Microsoft Intune 應用程式夥伴頁面中，您可以在 [Microsoft Intune 行動應用程式庫](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)找到受支援應用程式的完整清單。 選擇應用程式來查看支援的案例、平台和應用程式是否支援多重身分識別。

您也可以[啟用自訂建置的企業營運應用程式](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)來搭配 MAM 原則一起使用。

如果裝置遺失或遭竊，或使用者已不再與您的公司合作，則除了限制資料移動，您還可以[選擇性地清除公司資料](wipe-managed-company-app-data-with-microsoft-intune.md)，只留下個人資料。


<!--HONumber=Jun16_HO2-->


