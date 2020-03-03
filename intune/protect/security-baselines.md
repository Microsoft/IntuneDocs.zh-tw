---
title: 在 Microsoft Intune 中使用安全性基準 - Azure | Microsoft Docs
description: 使用建議的 Windows 安全性設定，使用 Microsoft Intune 來保護裝置上的使用者與資料，以用於行動裝置管理。 啟用加密、設定 Microsoft Defender 進階威脅防護、控制 Internet Explorer、設定本機安全性原則、要求使用密碼、封鎖網際網路下載項目等。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/24/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 43e104d9f32f6b6204ffc3bd461bb06764543e3c
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569263"
---
# <a name="use-security-baselines-to-configure-windows-10-devices-in-intune"></a>在 Intune 中使用安全性基準來設定 Windows 10 裝置

使 Intune 的安全性基準來協助您保護您使用者與裝置的安全。 安全性基準是預先設定的 Windows 設定群組，可協助您套用已知的設定群組與相關安全性小組所建議的預設值。 當您在 Intune 中建立安全性基準設定檔時，您是在建立由多個「裝置組態」  設定檔組成的範本。

本功能適用於：

- Windows 10 1809 版和更新版本

您在 Intune 中將安全性基準部署到使用者或裝置群組，而那些設定會套用到執行 Windows 10 或更新版本的裝置。 例如， *MDM 安全性基準*會自動針對抽取式磁碟機啟用 BitLocker、自動要求輸入密碼以將裝置解鎖，以及自動停用基本驗證等。 當預設值不適用於您的環境時，自訂基準以套用您所需的設定。

個別的基準類型可包括相同的設定，但會為那些設定使用不同的預設值。 了解您選擇使用之基準中的預設值非常重要，因為稍後您必須根據您的組織需求修改每個基準。

> [!NOTE]
> Microsoft 建議您不要在生產環境使用安全性基準的預覽版。 預覽基準中的設定在預覽期間可能會變更。

安全性基準可協助您在使用 Microsoft 365 時有端對端的安全工作流程。 以下為部分優點：

- 安全性基準包含關於會影響安全性之設定的最佳做法和建議。 Intune 會與建立群組原則安全性基準的同一個 Windows 安全性小組合作。 這些建議均以指引和豐富經驗為依據。
- 如果您從未用過 Intune，且不確定該從何處開始，則安全性基準可讓您具有優勢。 您可以快速建立並部署安全的設定檔，了解您正在協助保護貴組織的資源和資料。
- 如果您目前使用群組原則，使用這些基準移轉至 Intune 以進行管理會更簡單。 這些基準均原生內建於 Intune，並包含新式管理體驗。

[Windows 安全性基準](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines) \(部分機器翻譯\) 是深入了解此功能的絕佳資源。 [行動裝置管理](https://docs.microsoft.com/windows/client-management/mdm/) (MDM) \(英文\) 是關於 MDM 以及您如何在 Windows 裝置上加以運用的絕佳資源。

## <a name="about-baseline-versions-and-instances"></a>關於基準版本與執行個體

基準的每個新版本執行個體都可以新增或移除設定或引進其他變更。 例如，當新的 Windows 10 設定因為新版本的 Windows 10 推出而變成可用時，MDM 安全性基準可能會收到包括最新設定的新版本執行個體。

在 Intune 主控台中，每個基準的圖格都會顯示基準範本名稱和該基準的基本資訊。 該資訊包括您有多少個使用該基準類型的設定檔、有多少該基準類型的個別執行個體 (版本) 可用，以及可識別基準範本何時新增至您租用戶的「上次發行日期」  日期。 下列範例顯示常用 MDM 安全性基準的圖格：

![基準圖格](./media/security-baselines/baseline-tile.png)

若要檢視您使用之基準版本的詳細資訊，請選取基準圖格以開啟其 [概觀]  窗格，然後選取 [版本]  。 Intune 會顯示您的設定檔所使用基準版本的詳細資料。 在 [版本] 窗格上，您可以選取單一版本以檢視使用該版本之設定檔的深入詳細資料。 您也可以選取兩個不同的版本並選擇 [比較基準]  以下載詳述差異的 CSV 檔案。

![比較基準](./media/security-baselines/compare-baselines.png)

當您建立安全性基準設定檔  時，設定會自動使用最新的已發行安全性基準執行個體。  您可以繼續使用及編輯先前建立且使用較早基準版本執行個體的設定檔，包括使用預覽版本建立的基準。

您可以選擇[變更搭配給定設定檔使用的基準版本](#change-the-baseline-version-for-a-profile)。 這表示當新版本推出時，您不需要建立新的基準設定檔就能發揮其功能。 當您就緒時，您可以改為選取基準設定檔並使用內建選項將該設定檔的執行個體版本變更為新版本。

## <a name="available-security-baselines"></a>可用的安全性基準

 您可以同時在 Intune 環境中使用一或多個可用的基準。 您也可以使用具有不同自訂項目之相同安全性基準的多個執行個體。

當您使用多個安全性基準時，請檢閱各項設定，以識別不同的基準何時會引進相同設定的衝突值。 因為您可以部署專為不同意圖而設計的安全性基準，並部署包含自訂設定的相同基準的多個執行個體，所以您可能會[針對必須調查和解決的裝置建立設定衝突](security-baselines-monitor.md#troubleshoot-using-per-setting-status)。  也請留意您的[裝置組態設定檔](../configuration/device-profiles.md)，它可設定許多與安全性基準相同的設定。

下列安全性基準執行個體可以搭欸 Intune 使用。 使用連結來檢視每個基準最近執行個體的設定。

- **MDM 安全性基準**
  - [2019 年 5 月的 MDM 安全性基準](security-baseline-settings-mdm-all.md?pivots=mdm-may-2019)
  - [預覽：2018 年 10 月的 MDM 安全性基準](security-baseline-settings-mdm-all.md?pivots=mdm-preview)

- **Microsoft Defender ATP 基準**
  (若要使用此基準，您的環境必須滿足使用 [Microsoft Defender 進階威脅防護的先決條件](advanced-threat-protection.md#prerequisites))  。
  - [Microsoft Defender ATP 基準](security-baseline-settings-defender-atp.md)

  > [!NOTE]
  > Microsoft Defender ATP 安全性基準已針對實體裝置最佳化，目前不建議用於虛擬機器 (VM) 或 VDI 端點。 特定基準設定可能會影響虛擬化環境上的遠端互動式工作階段。  如需詳細資訊，請參閱 Windows 文件中的[提高 Microsoft Defender ATP 安全性基準的合規性](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline) \(英文\)。

- **Microsoft Edge 基準**
  - [預覽：Microsoft Edge 基準](security-baseline-settings-edge.md)

您可以繼續使用及編輯您以預覽範本為基礎建立的設定檔，即使已不提供該預覽設定檔來建立新設定檔也可以。

## <a name="manage-baselines"></a>管理基準

您在使用安全性基準時執行的一般工作包括：

- [建立設定檔](#create-the-profile) - 設定您要使用的設定，並將基準指派給群組。
- [變更版本](#change-the-baseline-version-for-a-profile) - 變更由設定檔使用的基準版本。
- [移除基準指派](#remove-a-security-baseline-assignment) - 了解當您停止使用安全性基準管理設定時會發生什麼事。


### <a name="prerequisites"></a>先決條件

- 若要在 Intune 中管理基準，您的帳戶必須擁有[原則和設定檔管理員](../fundamentals/role-based-access-control.md#built-in-roles)內建角色。

- 使用某些基準可能要求您必須有額外服務 (例如 Microsoft Defender ATP) 的有效訂用帳戶。

### <a name="create-the-profile"></a>建立設定檔

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 選取 [端點安全性]   > [安全性基準]  以檢視可用基準清單。

   ![選取要設定的安全性基準](./media/security-baselines/available-baselines.png)

3. 選取您想要使用的基準，然後選取 [建立設定檔]  。

4. 在 [基本]  索引標籤上，指定下列屬性：

   - **名稱**：輸入安全性基準設定檔的名稱。 例如，輸入 *Defender ATP 的標準設定檔*。

   - **描述**：輸入一些文字來描述此基準的用途。 您可以針對描述輸入任何想要的文字。 它是選擇性的，但建議使用。

   選取 [下一個]  以移至下一個索引標籤。移至新索引標籤之後，您可以選取索引標籤名稱以返回先前已檢視的索引標籤。

5. 在 [組態設定] 索引標籤上，檢視您選取之基準中可用的 [設定]  群組。 您可以展開群組以檢視該群組中的設定，以及基準中那些設定的預設值。 尋找特定設定：
   - 選取某個群組以展開及檢閱可用設定。
   - 使用 [搜尋]  列並指定可篩選檢視以僅顯示包含您的搜尋條件之群組的關鍵字。

   基準中的每個設定都有該基準版本的預設設定。 重新設定預設設定以滿足您的業務需求。 不同的基準可能包含相同的設定，您可以根據基準的意圖為設定使用不同的預設值。

   ![展開群組以檢視該群組的設定](./media/security-baselines/sample-list-of-settings.png)

6. 在 [範圍標籤]  索引標籤上，選取 [選取範圍標籤]  以開啟 [選取標籤]  窗格並指派範圍標籤到設定檔。

7. 在 [指派]  索引標籤上，選取 [選取要納入的群組]  並指派基準給一或多個群組。 使用 [選取要排除的群組]  以微調指派。

   ![指派設定檔](./media/security-baselines/assignments.png)

8. 當您準備好部署基準時，請移至 [檢閱 + 建立]  索引標籤並檢閱基準的詳細資料。 選取 [建立]  以儲存並部署設定檔。

   建立設定檔之後，它會被推送到指派的群組而且可能會立即套用。

   > [!TIP]
   > 若您儲存設定檔而未先將它指派給群組，您稍後可以編輯設定檔以執行此動作。

   ![檢閱基準](./media/security-baselines/review.png)

9. 建立設定檔之後，您可以透過前往 [端點安全性]   > [安全性基準]  、選取您設定的基準類型，然後選取 [設定檔]  來編輯該設定檔。 從可用設定檔清單選取設定檔，然後選取 [內容]  。 您可以從所有可用設定索引標籤編輯設定，然後選取 [檢閱並儲存]  以認可您的變更。

### <a name="change-the-baseline-version-for-a-profile"></a>變更設定檔的基準版本

您可以變更搭配設定檔使用之基準執行個體的版本。  當您變更版本時，您是選取相同基準的可用執行個體。 您無法在兩個不同的基準類型之間變更，例如將設定檔從使用 Defender ATP 的基準變更為使用 MDM 安全性基準。

在設定基準版本的變更時，您可以下載列出所涉及兩個基準版本間之變更的 CSV 檔案。 您也可以選擇保留原始基準版本的所有自訂項目，或使用其所有預設值來實作新版本。 當您在變更設定檔的基準版本時，您無法選擇變更個別設定。

儲存時，當轉換完成之後，基準會立即重新部署到指派的群組。

**在轉換期間**：

- 系統會新增不存在於您先前使用之原始版本中的新設定，並將它們設定為使用預設值。

- 系統會移除不存於您選取之新基準版本中的設定，而且那些設定再也不會由此安全性基準設定檔強制套用。

  當設定不再由基準設定檔管理時，該設定不會在裝置上重設。 裝置上的該設定會維持設定為其上次設定，直到一些其他程序管理那些設定並變更設定值。 可在您停止管理設定之後變更設定的程序範例包括不同的基準設定檔、群組原則設定，或在裝置上進行的手動設定。

#### <a name="to-change-the-baseline-version-for-a-profile"></a>變更設定檔的基準版本

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。 

2. 選取 [端點安全性]   > [安全性基準]  ，然後選取具有您要變更之設定檔的基準類型圖格。

3. 接著，選取 [設定檔]  ，然後選取您要編輯之設定檔的核取方塊，接著選取 [變更版本]  。

   ![選取基準](./media/security-baselines/select-baseline.png)

4. 在 [變更版本]  窗格上，使用 [選取要更新到的安全性基準]  下拉式清單，然後選取您要使用的版本執行個體。

   ![選取版本](./media/security-baselines/select-instance.png)

5. 選取 [檢閱更新]  以下載 CSV 檔案，此檔案顯示設定檔目前執行個體版本與您選取之新版本之間的差異。 檢閱此檔案，以便您了解那些設定是新的，或移除了哪些設定，以及這些設定在已更新之設定檔中的預設值為何。

   當您就緒時，繼續到下一個步驟。

6. 選擇 [選擇更新設定檔的方法]  兩個選項的其中一個：
   - **接受基準變更但保留我的現有設定自訂** - 此選項會保留您對基準設定檔所做的自訂，並將其套用到您選取要使用的新版本。
   - **接受基準變更並捨棄現有的設定自訂** - 此選項會完全覆寫您的原始設定檔。 更新的設定檔將會為所有設定使用預設值。

7. 選取 [提交]  。 設定檔會更新為選取的基準版本，而且在轉換完成後，基準會立即重新部署到指派的群組。

### <a name="remove-a-security-baseline-assignment"></a>移除安全性基準指派

當安全性基準設定不再套用到裝置時，或基準中的設定設定為 [尚未設定]  時，裝置上的那些設定不會還原為預先管理的設定。 裝置上先前的受控設定會保留其上次從基準所接收的設定，直到一些其他程序更新裝置上的那些設定。

稍後可能變更裝置上那些設定的其他程序包括不同或新的安全性基準、裝置設定檔、群組原則設定，或在裝置上手動編輯設定。

## <a name="co-managed-devices"></a>共同管理的裝置

Intune 管理之裝置上的安全性基準類似使用 Configuration Manager 的共同受控裝置。 共同受控裝置會使用 Configuration Manager 和 Microsoft Intune，同時管理 Windows 10 裝置。 它可讓您將現有的 Configuration Manager 投資雲端連結至 Intune 的優點。 如果您使用 Configuration Manager，同時也想擁有雲端的優點，則[共同管理概觀](https://docs.microsoft.com/configmgr/comanage/overview) \(英文\) 會是一項絕佳資源。

使用共同受控裝置時，您必須將**裝置設定**工作負載 (其設定) 切換至 Intune。 [裝置設定工作負載](https://docs.microsoft.com/configmgr/comanage/workloads#device-configuration) \(英文\) 會提供詳細資訊。

## <a name="q--a"></a>問答集

### <a name="why-these-settings"></a>為什麼是這些設定？

Microsoft 安全性小組擁有多年直接與 Windows 開發人員和安全性社群合作的體驗，從而提供了這些建議。 此基準中的設定均被視為最相關的安全性相關設定選項。 在每個新的 Windows 組建中，該小組都會根據新發行的功能來調整建議。

### <a name="is-there-a-difference-in-the-recommendations-for-windows-security-baselines-for-group-policy-vs-intune"></a>對於群組原則與 Intune 之 Windows 安全性基準的建議有任何差異嗎Intune？

同一個 Microsoft 安全性小組已選擇並組織了每個基準的設定。 Intune 包含 Intune 安全性基準中的所有相關設定。 群組原則基準中有一些設定是內部部署網域控制站特有的。 這些設定都會從 Intune 的建議中排除。 所有的其他設定都一樣。

### <a name="are-the-intune-security-baselines-cis-or-nsit-compliant"></a>Intune 安全性基準符合 CIS 或 NSIT 的規範嗎？

嚴格來說，不符合。 Microsoft 安全性小組會諮詢 CIS 之類的組織來編譯其建議。 但是，在「符合 CIS 規範」與 Microsoft 基準之間沒有一對一的對應關係。

### <a name="what-certifications-does-microsofts-security-baselines-have"></a>Microsoft 的安全性基準具備哪些認證？ 

- Microsoft 會持續發佈適用於群組原則 (GPO) 的安全性基準和[安全性合規性工具組](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10) \(部分機器翻譯\)，而這已行之有年。 許多組織都會使用這些基準。 這些基準中的建議均來自 Microsoft 安全性小組與企業客戶和外部機構的合作，包括美國國防部 (DoD)、美國國家標準技術研究所 (NIST) 及其他更多組織。 我們會與這些組織分享我們的建議和基準。 這些組織也擁有自己的建議，而這些建議均會密切地反映出 Microsoft 的建議。 隨著行動裝置管理 (MDM) 持續成長到雲端，Microsoft 建立了這些群組原則基準的對等 MDM 建議。 這些額外的基準均內建於 Microsoft Intune，並包含關於遵循 (或未遵循) 基準之使用者、群組和裝置的合規性報告。

- 許多客戶都會使用 Intune 基準建議作為起點，然後進行自訂以符合他們的 IT 和安全性需求。 Microsoft 的 Windows 10 RS5 **MDM 安全性基準**是第一個要發行的基準。 此基準會以一般基礎結構來建置，讓客戶最終可根據 CIS、NIST 和其他標準匯入其他安全性基準。 其目前適用於 Windows，而最終將包含 iOS/iPadOS 和 Android。

- 使用 Azure Active Directory (AD) 搭配 Microsoft Intune，從內部部署 Active Directory 群組原則移轉到純雲端解決方案是一趟旅程。 [Security Compliance Toolkit](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10) 中包括群組原則範本，可協助您管理混合式 AD 與 Azure AD 裝置。 這些裝置可以視需要從雲端 (Intune) 取得 MDM 設定，以及從內部部署網域控制站取得群組原則設定。

## <a name="next-steps"></a>後續步驟

- 檢視可用最新版基準中的設定：
  - [MDM 安全性基準](security-baseline-settings-mdm-all.md)
  - [Microsoft Defender ATP 基準](security-baseline-settings-defender-atp.md)

- 檢查狀態並監視[基準和設定檔](security-baselines-monitor.md)
