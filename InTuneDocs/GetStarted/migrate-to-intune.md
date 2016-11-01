---
title: "移轉至 Intune | Microsoft Intune"
description: 
keywords: 
author: jeffgilb
ms.author: jeffgilb
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 88936b8a-7453-4410-b6db-29f636ba3e72
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 59041e1c35d2f4b5c4d9b663494f3f02504c12f6
ms.openlocfilehash: b115912357e298016dee4e0fa87f2ed87f5f2f60


---

# 移轉至 Intune


從您現有的企業行動管理解決方案移轉至 Intune 可以依照以下的一般步驟順序︰

![Intune 的移轉步驟](./media/migrate-intune-steps.png)

## 通知使用者

一旦您認為 Intune 試驗部署已符合您的需求，請通知使用者即將將其裝置移轉至 Intune。 電子郵件訊息、指示和[海報](https://gallery.technet.microsoft.com/Intune-End-User-Enrollment-3a0c9b0c?WT.mc_id=Blog_Intune_General_PCIT)有助於設定預期，並提供使用者需要採取之步驟的註冊詳細資料，以保有公司資源與應用程式不中斷連線。 請確定您的支援團隊已準備好在移轉程序中協助使用者。

## 修改現有的企業行動管理解決方案

根據您計劃如何處理現有的企業行動管理解決方案與 Intune 之間的條件式存取原則，您可能需要停用現有的條件式存取原則。 您將停用現有的條件式存取原則「或」讓現有的條件式存取原則的範圍不包含您即將移轉至 Intune 的使用者/裝置。  請勿讓 Intune 與您的現有企業行動力管理解決方案對相同的使用者/裝置同時套用條件式存取原則。

## 啟用 Intune 條件式存取原則 (選擇性)

如果您已經決定要立即對進行移轉的裝置強制執行條件式存取原則，而無寬限期，請在此步驟的 Intune 中啟用條件式存取原則。  請確定已與您的使用者與您的技術服務人員團隊妥善溝通此決策。  如果裝置未在 Intune 中註冊，而且不符合 Intune 原則，使用者將無法存取公司資源，直到他們在 Intune 中註冊，並且裝置符合 Intune 原則。

## 從現有的企業行動管理解決方案取消註冊裝置

在裝置註冊使用 Intune 之前，必須從現有的企業行動管理解決方案中將裝置取消註冊。 我們的建議是讓使用者可自行取消註冊其裝置，以獲得最佳使用者經驗。  務必遵循解決方案提供者提供的取消註冊指引，以確定您從平台正確移除使用者和裝置，確保對使用者造成的中斷最小。

## 讓裝置註冊使用 Intune

排程進行移轉的使用者應該立即註冊使用 Intune，以重新取得或防止失去對公司資源、電子郵件和應用程式的存取。 如果您已設定條件式存取，而使用者嘗試在註冊使用 Intune 之前連線至電子郵件，其存取將遭封鎖，並向他們提供註冊電子郵件。 這封電子郵件將引導他們在 Intune 中註冊裝置。  或者，使用者可以透過 Intune 公司入口網站應用程式，或透過 Windows 8.1 和 Windows 10 行動裝置上的作業系統原生註冊使用 Intune。 請參閱[使用 Microsoft Intune 之使用者體驗的相關資源](/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)，以取得每個平台註冊步驟的進一步指引。

## 設定 Intune 條件式存取 (選擇性)

如果您已對條件式存取強制執行允許一段寬限期，請在 Intune 中啟用條件式存取原則，以在您向使用者通知的寬限期結束時開始強制執行。 這將立即要求所有裝置符合 Intune 條件式存取原則的需求。

## 註冊其他裝置和使用者

既然您已啟用條件式存取，所有使用者都需要註冊使用 Intune 並符合組織的相容性原則，才能存取公司資源。 如果您已在階段式註冊 (非一次移轉全部) 中移轉使用者，請重複上述步驟，直到所有裝置與使用者均已註冊且由 Intune 管理。

## 淘汰先前的企業行動管理解決方案

將所有使用者和裝置移轉至 Intune 並且驗證 Intune 的移轉作業都成功之後，您可以淘汰先前的企業行動管理解決方案及/或取消訂用帳戶服務。 請務必遵循解決方案提供者的指引，以確定您正確地移除任何不需要的基礎結構需求，並取消任何訂用帳戶/授權。

## 其他移轉資源

對於移轉至 Intune，您是否需要額外的協助？ 我們提供專家協助選項，可協助確認您的移轉沒有任何問題︰

<!--- - [Microsoft Intune Onboarding](/em/solutions/fasttrack-center-benefit-for-enterprise-mobility-suite-ems)--->
- [Microsoft 諮詢服務](https://www.microsoft.com/en-us/microsoftservices/default.aspx)
- [Intune 的技術和非技術支援](/intune/troubleshoot/how-to-get-support-for-microsoft-intune)
- [Microsoft Intune TechNet 論壇](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)

## 取得此指南的可下載副本

若要取得這整份指南的可下載版本，請瀏覽 [TechNet 資源庫](https://gallery.technet.microsoft.com/Migrating-to-Intune-ea439387)。



<!--HONumber=Oct16_HO3-->


