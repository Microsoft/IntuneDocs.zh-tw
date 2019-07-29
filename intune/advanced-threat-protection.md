---
title: 在 Microsoft Intune 中使用 Microsoft Defender ATP - Azure | Microsoft Docs
description: 了解如何在端對端案例中啟用 Microsoft Defender 進階威脅防護 (Microsoft Defender ATP)，包括在 Intune 和 Microsoft Defender 資訊安全中心中開啟 Microsoft Defender ATP、使用 Microsoft Defender ATP 組態設定檔來讓裝置上線、建立 Intune 裝置合規性政策、建立 Azure AD 條件式存取原則，以及監視裝置合規性。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: af27a9b07434346a5425d0539759cb90ebf1ee6f
ms.sourcegitcommit: 614c4c36cfe544569db998e17e29feeaefbb7a2e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68427079"
---
# <a name="enforce-compliance-for-microsoft-defender-atp-with-conditional-access-in-intune"></a>在 Intune 中使用條件式存取強制執行 Microsoft Defender ATP 的合規性  

Microsoft Defender 進階威脅防護 (Microsoft Defender ATP) 和 Microsoft Intune 能夠一起運作以協助防止安全性缺口，並協助限制因缺口而在組織內所造成的影響。

本功能適用於：Windows 10 裝置

例如，有人傳送內嵌惡意程式碼的 Word 附件給組織內的使用者。 使用者開啟該附件並啟用內容。 權限提升的攻擊將會展開，而來自遠端電腦的攻擊者將會擁有受害者裝置的系統管理員權限。 攻擊者接著會從遠端存取該使用者的其他裝置。

此安全性缺口可能會影響整個組織。

Microsoft Defender ATP 可以解決此類安全性事件。 Microsoft Defender 資訊安全中心會將該裝置報告為「高風險」，並包含可疑活動的詳細報表。 在我們的範例中，Microsoft Defender ATP 會偵測到裝置執行不正常的程式碼、發生處理序權限提升、被插入惡意程式碼，並發出可疑遠端殼層。 Microsoft Defender ATP 接著會提供能降低威脅的選項。

您可以使用 Intune 建立合規性原則，以判斷可接受的風險層級。 如果裝置超過此風險，該裝置將會變成不符合規範。 透過搭配 Azure Active Directory (AD) 條件式存取，系統將會封鎖該使用者存取公司資源。

本文將示範下列項目的作法：

- 在 Microsoft Defender 資訊安全中心中啟用 Intune，並在 Intune 中啟用 Microsoft Defender ATP。 這些工作會在 Intune 與 Microsoft Defender ATP 之間建立服務對服務連線。 此連線可讓 Microsoft Defender ATP 撰寫針對您 Intune 裝置的電腦風險。
- 在 Intune 中建立合規性原則。
- 根據裝置的威脅等級，在裝置上的 Azure Active Directory (AD) 中啟用條件式存取。

## <a name="prerequisites"></a>必要條件

若要搭配 Intune 使用 Microsoft Defender ATP，請確認下列項目已設定且可供使用：

- 適用於 Enterprise Mobility + Security E3 和 Windows E5 (或 Microsoft 365 企業版 E5) 的授權租用戶
- Microsoft Intune 環境，搭配已加入 Azure AD 且[受 Intune 管理的](windows-enroll.md) Windows 10 裝置
- [Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) 和 Microsoft Defender 資訊安全中心 (ATP 入口網站) 的存取權

## <a name="enable-microsoft-defender-atp-in-intune"></a>在 Intune 中啟用 Microsoft Defender ATP

當您將新的應用程式整合到 Intune Mobile Threat Defense 並啟用連線時，Intune 會在 Azure Active Directory 中建立傳統條件式存取原則。 您整合的每個 MTD 應用程式 (例如 [Defender ATP](advanced-threat-protection.md) 或任何其他 [MTD 合作夥伴](mobile-threat-defense.md#mobile-threat-defense-partners))，都會建立新的傳統條件式存取原則。  這些原則可以忽略，但不應編輯、刪除或停用。

適用於 MTD 應用程式的傳統條件式存取原則： 

- 由 Intune MTD 用於要求裝置必須在 Azure AD 中註冊，如此其才能擁有裝置識別碼。 此識別碼為必要，以便裝置成功向 Intune 報告其狀態。  
- 不同於您可能會建立用來協助管理 MTD 的條件式存取原則。
- 根據預設，不會與您用於評估的其他條件式存取原則互動。  

若要檢視傳統條件式存取原則，請前往 [Azure](https://portal.azure.com/#home) 中的 [Azure Active Directory]   > [條件式存取]   > [傳統原則]  。

### <a name="to-enable-defender-atp"></a>啟用 Defender ATP
1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [裝置合規性]   > [Microsoft Defender ATP]  ，然後選取 [連接器設定]  下的 [開啟 Microsoft Defender 資訊安全中心]  。

    ![選取以開啟 [Microsoft Defender 資訊安全中心]](./media/advanced-threat-protection/atp-device-compliance-open-microsoft-defender.png)

4. 在 **Microsoft Defender 資訊安全中心**中：
    1. 選取 [設定]   > [進階功能]  。
    2. 針對 [Microsoft Intune 連線]  ，選擇 [開啟]  ：

        ![啟用 Intune 的連線](./media/advanced-threat-protection/atp-security-center-intune-toggle.png)

    3. 選取 [儲存喜好設定]  。

4. 返回 Intune，[裝置合規性]   > [Microsoft Defender ATP]  。 將 [將 10.0.15063 版及更新版本的 Windows 裝置連線到 Microsoft Defender ATP]  設定為 [開啟]  。
5. 選取 [儲存]  。

通常您只需執行此工作一次即可。 因此，如果您的 Intune 資源中已啟用 Microsoft Defender ATP，便無需再次執行它。

## <a name="onboard-devices-using-a-configuration-profile"></a>使用組態設定檔將裝置上線

當終端使用者在 Intune 中註冊時，您可以使用組態設定檔將不同設定推送到裝置。 這也適用於 Microsoft Defender ATP。

Microsoft Defender ATP 包含上線設定套件，該套件會與 [Microsoft Defender ATP 服務](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)通訊，以掃描檔案、偵測威脅，以及向 Windows Defender ATP 報告風險。

當您上線時，Intune 會從 Microsoft Defender ATP 取得自動產生的設定套件。 當 Intune 將組態設定檔傳送至裝置時，會將設定套件推送至裝置，這允許 Microsoft Defender ATP 監視裝置是否存在威脅。

當您使用設定套件將裝置上線之後，就不需要再次執行它。 您也可以使用[群組原則或 System Center Configuration Manager (SCCM)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints) 來將裝置上線。

### <a name="create-the-configuration-profile"></a>建立組態設定檔

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [裝置設定]   > [設定檔]   > [建立設定檔]  。
3. 輸入 [名稱]  和 [描述]  。
4. 針對 [平台]  ，選取 [Windows 10 及更新版本] 
5. 針對 [設定檔類型]  ，選取 [Microsoft Defender ATP (Windows 10 Desktop)]  。
6. 設定這些設定：

    - **Microsoft Defender ATP 用戶端設定套件類型**：選取 [上架]  以將新的設定套件新增至設定檔。 選取 [下架]  可從設定檔移除設定套件。
  
    > [!NOTE]  
    > 如果您已經正確建立與 Microsoft Defender ATP 的連線，Intune 會自動為您將組態設定檔**上線**，且 [Microsoft Defender ATP 用戶端設定套件類型]  設定將無法使用。
  
    - **所有檔案的範例共用**：[啟用]  可收集樣本並與 Microsoft Defender ATP 共用。 例如，如果您看到可疑檔案，可將它提交至 Microsoft Defender ATP 以進行深入分析。 [尚未設定]  不與 Microsoft Defender ATP 共用任何樣本。
    - **加快遙測回報頻率**：針對高風險的裝置 [啟用]  此設定，系統會更頻繁地將遙測回報給 Microsoft Defender ATP 服務。

    [使用 System Center Configuration Manager 將 Windows 10 電腦上線](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints-sccm) \(部分機器翻譯\) 中有這些 Microsoft Defender ATP 設定的更多詳細資料。

7. 選取 [確定]  ，然後選取 [建立]  以儲存您的變更，這會建立設定檔。

## <a name="create-the-compliance-policy"></a>建立合規性原則
合規性原則會決定裝置上可接受的風險層級。

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [裝置合規性]   > [原則]   > [建立原則]  。
3. 輸入 [名稱]  和 [描述]  。
4. 在 [平台]  中，選取 [Windows 10 及更新版本]  。
5. 在 [Microsoft Defender ATP]  設定中，將 [裝置必須等於或低於電腦風險分數]  設定為您偏好的層級。 威脅等級分類是[由 Windows Defender ATP 所決定的](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/alerts-queue) \(部分機器翻譯\)。

   - **清除**：這個層級最安全。 裝置不能在具有任何現有威脅的情況下，繼續存取公司資源。 發現任何威脅時，即會將裝置評估為不相容。 (Microsoft Defender ATP 使用值「安全」  。)
   - **低**︰裝置只有在僅存在低層級威脅的情況下才能符合規範。 具有中或高威脅等級的裝置不符合規範。
   - **中**︰如果在裝置上發現的威脅為低或中層級，則會將裝置評估為符合規範。 如果偵測到高層級的威脅，則會將裝置判斷為不相容。
   - **高**：這個層級最不安全，且會允許所有威脅層級。 因此具有高、中或低威脅層級的裝置都會被評估為符合規範。

6. 選取 [確定]  ，然後選取 [建立]  以儲存您的變更 (並建立原則)。

## <a name="assign-the-policy"></a>指派原則

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [裝置合規性]   > [原則]  > 選取您的 Microsoft Defender ATP 合規性政策。
3. 選取 [指派]  。
4. 包含或排除您的 Azure AD 群組，以將原則指派給它們。
5. 若要將原則部署到群組中，請選取 [儲存]  。 系統將會對原則的目標使用者裝置進行合規性評估。

## <a name="create-a-conditional-access-policy"></a>建立條件式存取原則
「如果」  裝置不符合規範，條件式存取原則就會封鎖對資源的存取。 因此，如果裝置超過威脅層級，您可以封鎖該裝置對公司資源的存取，例如 SharePoint 或 Exchange Online。  

> [!TIP]  
> 條件式存取是一項 Azure Active Directory (Azure AD) 技術。 從 *Intune* 存取的條件式存取節點，與從 *Azure AD* 存取的節點相同。  

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)，然後選取 [條件式存取]   > [新原則]  。
2. 輸入原則 [名稱]  ，然後選取 [使用者和群組]  。 使用 [包含] 或 [排除] 選項來針對原則新增群組，並選取 [完成]  。
3. 選取 [雲端應用程式]  ，然後選擇要保護哪些應用程式。 例如，選擇 [選取應用程式]  ，然後選取 [Office 365 SharePoint Online]  和 [Office 365 Exchange Online]  。

    按一下 [完成]  以儲存您的變更。

4. 選取 [條件]   > [用戶端應用程式]  來將原則套用至應用程式和瀏覽器。 例如，選取 [是]  ，然後啟用 [瀏覽器]  和 [行動應用程式及桌面用戶端]  。

    按一下 [完成]  以儲存您的變更。

5. 選取 [授與]  ，以根據裝置合規性套用條件式存取。 例如，選取 [授與存取權]   > [裝置需要標記為合規]  。

    選擇 [選取]  以儲存您的變更。

6. 選取 [啟用原則]  ，然後選取 [建立]  以儲存變更。

[什麼是條件式存取？](conditional-access.md)是一個很好的資源。

## <a name="monitor-device-compliance"></a>監視裝置合規性
接下來，監視具有 Microsoft Defender ATP 合規性政策之裝置的狀態。

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [裝置合規性]   > [原則合規性]  。
3. 在清單中尋找您的 Microsoft Defender ATP 政策，並查看有哪些裝置是符合規範或不符合規範。

## <a name="more-good-stuff"></a>更多好東西
[Microsoft Defender ATP 條件式存取](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/conditional-access) \(部分機器翻譯\)  
[Microsoft Defender ATP 風險儀表板](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard) \(部分機器翻譯\)  

[裝置合規性原則入門](device-compliance-get-started.md)  
[Azure AD 中的條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)