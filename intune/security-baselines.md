---
title: 在 Microsoft Intune 中使用安全性基準 - Azure | Microsoft Docs
description: 新增或設定建議的群組安全性設定，使用 Microsoft Intune 來保護裝置上的使用者和資料，以用於行動裝置管理。 啟用 BitLocker、設定 Windows Defender 進階威脅防護、控制 Internet Explorer、使用 SmartScreen、設定本機安全性原則、需要密碼、封鎖網際網路下載項目等等。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5b2a5e2bbd6d06cc4ec0cf71ee815229b01040a8
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61490643"
---
# <a name="create-a-windows-10-security-baseline-in-intune"></a>在 Intune 中建立 Windows 10 安全性基準

安全性基準為一項目前處於預覽狀態的功能，適用於執行 Windows 10 和更新版本的裝置。 此功能包含 Intune 支援的許多設定，可用來協助保護您的使用者和裝置。 它也會將這些設定自動設定為安全性小組所建議的值。 例如，基準會自動啟用 BitLocker、自動要求密碼以解除鎖定裝置、自動停用基本驗證等等。

本功能適用於：

- Windows 10 1809 版和更新版本

> [!NOTE]
> 儘管安全性基準目前處於預覽狀態，但 Microsoft 不建議在生產環境中使用設定檔，因為基準可能會在預覽期間變更。 當安全性基準正式推出時，現有設定檔不會轉換成最新支援的設定檔。

使用安全性基準的目標是在使用 Microsoft 365 時提供端對端的安全工作流程。 以下為部分優點：

- 安全性基準包含關於會影響安全性之設定的最佳做法和建議。 Intune 會與建立群組原則安全性基準的同一個 Windows 安全性小組合作。 這些建議均以指引和豐富經驗為依據。
- 如果您從未用過 Intune，且不確定該從何處開始，則安全性基準可讓您具有優勢。 您可以快速建立並部署安全的設定檔，了解您正在協助保護貴組織的資源和資料。
- 如果您目前使用群組原則，使用這些基準移轉至 Intune 以進行管理會更簡單。 這些基準均原生內建於 Intune，並包含新式管理體驗。

安全性基準會在 Intune 中建立「組態設定檔」。 此設定檔包含基準中的所有設定。 您接著會將此設定檔套用或指派給使用者、群組和裝置。

指派設定檔之後，您可以監視設定檔和基準。 例如，您可以查看哪些裝置符合基準，哪些不符合基準。

本文示範如何使用安全性基準來建立設定檔、指派設定檔，以及監視設定檔。

[Windows 安全性基準](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines) \(部分機器翻譯\) 是深入了解此功能的絕佳資源。 [行動裝置管理](https://docs.microsoft.com/windows/client-management/mdm/) (MDM) \(英文\) 是關於 MDM 以及您如何在 Windows 裝置上加以運用的絕佳資源。

## <a name="prerequisites"></a>必要條件
若要在 Intune 中管理基準，您的帳戶必須擁有[原則和設定檔管理員](role-based-access-control.md#built-in-roles)內建角色。


## <a name="co-managed-devices"></a>共同管理的裝置

Intune 管理之裝置上的安全性基準類似使用 Configuration Manager 的共同受控裝置。 共同受控裝置會使用 System Center Configuration Manager 和 Microsoft Intune，同時管理 Windows 10 裝置。 它可讓您將現有的 Configuration Manager 投資雲端連結至 Intune 的優點。 如果您使用 Configuration Manager，同時也想擁有雲端的優點，則[共同管理概觀](https://docs.microsoft.com/sccm/comanage/overview) \(英文\) 會是一項絕佳資源。

使用共同受控裝置時，您必須將**裝置設定**工作負載 (其設定) 切換至 Intune。 [裝置設定工作負載](https://docs.microsoft.com/sccm/comanage/workloads#device-configuration) \(英文\) 會提供詳細資訊。

## <a name="create-the-profile"></a>建立設定檔

1. 在 [Azure 入口網站](https://portal.azure.com/)中，選取 [所有服務] > 篩選 [Intune] > 選取 [Intune]。
2. 選取 [安全性基準 (預覽)]。 系統提供可用的基準清單。 新增更多基準時，您將會在此處看到它們：

    ![查看 Intune 中目前可用的安全性基準清單](./media/security-baselines/available-baselines.png)

3. 選取您想要使用的基準 > [建立設定檔]。
4. 在 [基本資訊] 中，輸入下列內容：

    - **名稱**：輸入安全性基準設定檔的名稱。 例如，輸入 `pilot Windows 10 MDM baseline - Oct 2018`。
    - **描述**：輸入一些文字來描述此基準的用途。 您可以針對描述輸入任何想要的文字。 它是選擇性的，但絕對建議使用。

5. 展開 [設定]。 在清單中，您會在此安全性基準中看到所有設定，以及自動設定該設定的結果。 建議使用這些設定及其值，但您可加以變更。

    ![在 Intune 中展開設定，以查看此安全性基準中的所有設定](./media/security-baselines/sample-list-of-settings.png)

    展開部分設定以檢查其值。 例如，展開 [Windows Defender]。 請注意部分設定及其設定結果：

    ![查看 Intune 中自動設定部分 Windows Defender 設定的結果](./media/security-baselines/expand-windows-defender.png)

6. **建立**設定檔。 
7. 選取 [設定檔]。 您的設定檔隨即建立，並顯示於清單中。 但它不會執行任何動作。 接下來，請指派設定檔。

## <a name="assign-the-profile"></a>指派設定檔

建立設定檔之後，就可以將它指派給您的使用者、裝置和群組。 指派之後，就會將設定檔及其設定套用至您選擇的使用者、裝置和群組。

1. 在 Intune 中，選取 [安全性基準] > 選擇基準 > [設定檔]。
2. 選取您的設定檔 > [指派]。

    ![在 Intune 中選擇您的安全性基準設定檔，然後按一下指派以部署設定檔](./media/security-baselines/assignments.png)

3. 在 [包含] 索引標籤中，新增您想要套用此原則的使用者、群組或裝置。

    > [!TIP]
    > 請注意，您也可以**排除**群組。 如果您將原則套用至**所有使用者**，請考慮排除系統管理員群組。 萬一發生某些事情，您和您的系統管理員都不希望遭到鎖定。

4. [儲存] 變更。

儲存之後，設定檔即會在裝置使用 Intune 簽入時推送給它們。 因此，它可以立即發生。

## <a name="available-security-baselines"></a>可用的安全性基準  

下列安全性基準可以與 Intune 搭配使用。
- **預覽：MDM 安全性基準**
  - 版本：[2018 年 10 月](security-baseline-settings-windows.md)

## <a name="q--a"></a>問答集

#### <a name="why-these-settings"></a>為什麼是這些設定？

Microsoft 安全性小組擁有多年直接與 Windows 開發人員和安全性社群合作的體驗，從而提供了這些建議。 此基準中的設定均被視為最相關的安全性相關設定選項。 在每個新的 Windows 組建中，該小組都會根據新發行的功能來調整建議。

#### <a name="is-there-a-difference-in-the-recommendations-for-windows-security-baselines-for-group-policy-vs-intune"></a>對於群組原則與 Intune 之 Windows 安全性基準的建議有任何差異嗎Intune？

同一個 Microsoft 安全性小組已選擇並組織了每個基準的設定。 Intune 包含 Intune 安全性基準中的所有相關設定。 群組原則基準中有一些設定是內部部署網域控制站特有的。 這些設定都會從 Intune 的建議中排除。 所有的其他設定都一樣。

#### <a name="are-the-intune-security-baselines-cis-or-nsit-compliant"></a>Intune 安全性基準符合 CIS 或 NSIT 的規範嗎？

嚴格來說，不符合。 Microsoft 安全性小組會諮詢 CIS 之類的組織來編譯其建議。 但是，在「符合 CIS 規範」與 Microsoft 基準之間沒有一對一的對應關係。

#### <a name="what-certifications-does-microsofts-security-baselines-have"></a>Microsoft 的安全性基準具備哪些認證？ 

- Microsoft 會持續發佈適用於群組原則 (GPO) 的安全性基準和[安全性合規性工具組](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10) \(部分機器翻譯\)，而這已行之有年。 許多組織都會使用這些基準。 這些基準中的建議均來自 Microsoft 安全性小組與企業客戶和外部機構的合作，包括美國國防部 (DoD)、美國國家標準技術研究所 (NIST) 及其他更多組織。 我們會與這些組織分享我們的建議和基準。 這些組織也擁有自己的建議，而這些建議均會密切地反映出 Microsoft 的建議。 隨著行動裝置管理 (MDM) 持續成長到雲端，Microsoft 建立了這些群組原則基準的對等 MDM 建議。 這些額外的基準均內建於 Microsoft Intune，並包含關於遵循 (或未遵循) 基準之使用者、群組和裝置的合規性報告。

- 許多客戶都會使用 Intune 基準建議作為起點，然後進行自訂以符合他們的 IT 和安全性需求。 Microsoft 的 Windows 10 RS5 **MDM 安全性基準**是第一個要發行的基準。 此基準會以一般基礎結構來建置，讓客戶最終可根據 CIS、NIST 和其他標準匯入其他安全性基準。 它目前適用於 Windows，而最終將包含 iOS 和 Android。

- 使用 Azure Active Directory (AD) 搭配 Microsoft Intune，從內部部署 Active Directory 群組原則移轉到純雲端解決方案是一趟旅程。 為了提供協助，已針對混合式 AD 和已加入 Azure AD 的裝置發佈附屬的 GPO。 這些裝置可以視需要從雲端 (Intune) 取得 MDM 設定，以及從內部部署網域控制站取得群組原則設定。

## <a name="next-steps"></a>後續步驟
- 檢視 Intune 支援的 [Windows 安全性基準設定](security-baseline-settings-windows.md)。  
- 檢查狀態並監視[基準和設定檔](security-baselines-monitor.md)。
