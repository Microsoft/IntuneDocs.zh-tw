---
title: "邁向現代化的 Windows 管理 | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: angrobe
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: aada7909-24c9-46e2-88f0-38dd9c99b2f8
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2bfba29b5b2585f276a85a8dee7e62009e41ec3f
ms.openlocfilehash: e86fd1f33cc2cea467e11b41a842471bdaf1c3ea


---

# 透過 Microsoft Intune 邁向現代化的 Windows 管理

組織管理裝置的方式因使用個人裝置來執行工作，以及員工在辦公室外工作，而有所改變。 有些組織的特定部門可能需要深入且精確地控制裝置，而其他組織則想要採用更輕鬆且以案例為基礎的管理，來提升現代化工作力。

Windows 10 秉持 Windows 傳統，為組織提供最容易管理的作業系統。 Windows 透過群組原則、Active Directory 和 System Center Configuration Manager 等技術，提供深度管理能力和安全性的支援。 它也提供採用「行動優先、雲端優先」之簡化的現代化管理，使用 Microsoft Enterprise Mobility Suite (EMS) 等雲端式裝置管理解決方案來進行管理。 未來透過 Windows 即服務提供的 Windows 創新功能，都會輔以快速移動的雲端服務支援，例如 Microsoft Intune、Azure Active Directory、Azure Rights Management Service、Office 365 和商務用 Windows 市集。

IT 組織若能有機會受益於創新功能和成本節省，將會更有彈性。 本文件提供部署及管理 Windows 10 的策略指引。 它也提供 Microsoft 針對裝置管理工具之策略性思考的深入資訊。 當您思考管理基礎及想要如何將這些基礎應用至不同的裝置時，請考慮下列四個裝置生命週期階段：

![[設定 MDM 授權單位] 對話方塊](../media/mdm-path-stages.png)

## 部署與佈建

不同於需要複雜 IT 作業的傳統 OS 部署，現代化裝置管理開啟了「現成管理」的機會。 IT 部門想要輕鬆地將新裝置轉換成完全設定且受完整管理的裝置，而不需要重新安裝映像。  動態佈建是由 Microsoft Intune 等雲端式裝置管理服務所啟用，比過去更容易。 您也可以建立 Windows 映像處理與設定設計工具 (ICD) 內建的獨立佈建套件。 當然，我們仍然也會支援傳統映像處理技術，因此組織可以使用 System Center Configuration Manager 部署自訂映像。

## 身分識別與驗證

Windows 10 和 Azure Active Directory 之類的服務，開啟了雲端式身分識別、驗證和管理的新可能性。 BYOD 和 CYOD 等案例讓企業重新思考使用者存取公司資源和應用程式的方式。 您可以預見使用者和裝置管理會落入下列兩種類別：

- 行動使用者針對 Office 365 等 SaaS 應用程式使用的公司 (CYOD) 或個人 (BYOD) 裝置。

  Windows 10 可讓員工自行佈建裝置。 公司裝置可透過 Azure AD Join 輕鬆地設定公司存取。 同樣地，經過簡化的新 BYOD 體驗可讓使用者將其工作帳戶新增至 Windows，並存取個人裝置上的工作資源。 Azure AD Join 和 Intune MDM 自動註冊的結合，讓裝置只要透過[一個簡單的步驟](https://blogs.technet.microsoft.com/ad/2015/08/14/windows-10-azure-ad-and-microsoft-intune-automatic-mdm-enrollment-powered-by-the-cloud/)就能進入公司管理的狀態，全部都在雲端中進行。 Azure AD Join 也是臨時員工、合作夥伴或其他兼職員工的絕佳解決方案。 這些帳戶可以與內部部署 AD 網域分開保存，但仍可存取所需的公司資源。
- 使用傳統應用程式和資源之加入網域的電腦和平板電腦，這些裝置需要驗證，或是存取高度敏感或機密的內部部署資源

  加入內部部署 Active Directory 網域的 Windows 10 裝置會自動向 Azure AD 註冊，因此使用者可以享有 Windows 10 體驗的額外好處，例如從任何位置對雲端和內部部署資源進行單一登入、企業設定漫遊、Microsoft Passport for Work 和 Windows Hello。 加入網域的電腦和平板電腦應該繼續使用 System Center Configuration Manager 用戶端或群組原則進行管理。

檢閱您組織中的角色。 識別需要 [網域加入] 的使用者或裝置，並考慮將其他人切換至 Azure AD。 您可以在[這篇文章](https://azure.microsoft.com/en-us/documentation/articles/active-directory-azureadjoin-windows10-devices/)中深入了解 Windows 10 和 Azure AD 如何最佳化對不同裝置和案例混合之工作資源的存取。

以下是一般決策樹的外觀。 當然在某些情況下也會有例外。

![[設定 MDM 授權單位] 對話方塊](../media/mdm-path-stages-flow1.png)

## 設定與組態

所需的管理層級、所管理的裝置和資料，以及產業需求全部都會定義組態需求。 同時，員工經常關心 IT 部門將嚴格的原則套用至其個人裝置，但仍想存取公司電子郵件和文件。 Windows 10 透過通用的 MDM 層，為不同的電腦、平板電腦和手機提供一組一致的組態。 MDM 方法需要達成系統管理員意圖的設定，而不會公開所有可能的設定。 相較之下，群組原則會公開系統管理員個別控制的細部設定。 MDM 的優點之一是它可讓系統管理員透過更輕鬆且更有效率的工具，來套用更廣泛的隱私權、安全性和應用程式管理設定。 這使得 MDM 成為持續移動之裝置的最佳選擇。

許多組織仍需對加入網域的電腦進行細微的管理，例如 Internet Explorer 的 1500 個可設定的 GP 設定，或非常特定的 Windows 防火牆規則。 在這些情況下，群組原則和 System Center Configuration Manager 持續是絕佳的管理選擇。 若要對使用 Windows 工具連線到公司網路之加入網域的 Windows 電腦和平板電腦進行細微的設定，群組原則會是最佳方法。 Microsoft 會持續在每個新版 Windows 中新增群組原則設定。 若要精細地設定強固的軟體部署、Windows 更新和 OS 部署，Configuration Manager 仍舊是建議的解決方案。

![[設定 MDM 授權單位] 對話方塊](../media/mdm-path-stages-flow2.png)

## 更新 Windows 裝置

透過 Windows 即服務，IT 組織不再需要於每次發行新版 Windows 時，執行複雜的映像處理 (抹除並載入) 程序。 無論是在最新分支 (CB) 或最新商務分支 (CBB) 上，裝置都會透過簡單且通常自動的修補程序，收到最新的功能和優質的更新。 MDM 與 Intune 提供可將 Windows Update 套用至企業中用戶端電腦的工具。 Configuration Manager 可對這些更新進行豐富的管理和追蹤功能，包括維護期間和自動部署規則。

## [摘要]

如果您想要在組織中採用現代化裝置管理，請考慮可採取的步驟來開始進行。

1. **您可以立即進行的投資。** 您需要保留哪些傳統裝置管理元件，又有哪些地方可進行現代化？ 無論您是採取步驟來減少自訂映像處理、重新評估設定管理，或是重新評估驗證和相容性，都能立即受益。

2. **評估您環境中的不同使用案例。** 這些裝置群組是否可能受益於更輕鬆、簡化的管理？ 例如，BYOD 裝置理所當然需要雲端式管理。 使用者或裝置若處理嚴格規定的資料，則可能需要內部部署 AD 網域進行驗證。 Configuration Manager 和 EMS 可讓您彈性地分段實作現代化管理案例，同時以最符合您業務需求的方式，設定不同的目標裝置。 當然，決定權完全在您手上。

## 下一步

- **評估您環境中的管理需求。** 根據人員、其行動性、裝置及其存取的資料，一種解決方案可能無法滿足您所有的需求。
- **考慮這些需求。** 透過 Windows 10、Configuration Manager 和 Enterprise Mobility Suite，您就能在任何情況下，彈性地處理映像、驗證、設定和管理工具。
- **微幅進行。** 移至現代化裝置管理不需要是一蹴可幾的轉換。
- **最佳化您現有的投資。** 從傳統內部部署管理邁向現代化雲端式管理的過程中，可利用 Configuration Manager 和 Intune 的彈性、混合式架構。 隨著雲端身分識別/MDM 模型有愈來愈多的功能可用，Microsoft 將致力於提供更明確的途徑，將傳統管理轉換成現代化管理。



<!--HONumber=Sep16_HO2-->


