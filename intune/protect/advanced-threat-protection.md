---
title: 在 Microsoft Intune 中使用 Microsoft Defender ATP - Azure | Microsoft Docs
description: 搭配 Intune 使用 Microsoft Defender 進階威脅防護 (Microsoft Defender ATP)，包括安裝及設定、使用 ATP 讓您的 Intune 裝置上線，然後搭配您的 Intune 裝置相容性與條件式存取原則使用裝置 ATP 風險評量來保護網路資源。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 889b0a7562f1a663556e955271681e0747aeb3c4
ms.sourcegitcommit: 01fb3d844958a0e66c7b87623160982868e675b0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74199175"
---
# <a name="enforce-compliance-for-microsoft-defender-atp-with-conditional-access-in-intune"></a>在 Intune 中使用條件式存取強制執行 Microsoft Defender ATP 的合規性

您可以將 Microsoft Defender 進階威脅防護 (Microsoft Defender ATP) 與 Microsoft Intune 整合，作為 Mobile Threat Defense 解決方案。 整合可以協助防止安全性缺口，並協助限制因缺口而在組織內所造成的影響。 Microsoft Defender ATP 適用於執行 Windows 10 或更新版本的裝置。

若要成功，您必須使用下列設定：

- **Intune 與 Microsoft Defender ATP 之間建立服務對服務連線**。 此連線可讓 Microsoft Defender ATP 從您使用 Intune 管理的 Windows 10 裝置收集機器風險的相關資料。
- **使用裝置組態設定檔將裝置上線至 Microsoft Defender ATP**。 您會將裝置上線，將其設定為與 Microsoft Defender ATP 通訊，以及提供有助於評估其風險層級的資料。
- **使用裝置合規性政策來設定您想要允許的風險層級**。 風險層級是由 Microsoft Defender ATP 回報。 超過允許之風險層級的裝置會被識別為不符合規範。
- **使用條件式存取原則**來防止使用者從不符合規範的裝置存取公司資源。

當您將 Intune 與 Microsoft Defender 進階威脅防護 (ATP) 整合時，可以利用 ATP 的威脅與弱點管理 (TVM)，並[使用 Intune 來補救 TVM 識別出的端點弱點](atp-manage-vulnerabilities.md)。

## <a name="example-of-using-microsoft-defender-atp-with-intune"></a>搭配 Intune 使用 Microsoft Defender ATP 的範例

下列範例會協助說明這些解決方案如何搭配使用，來協助保護您的組織。 在此範例中，Microsoft Defender ATP 與 Intune 已整合。

考慮有人傳送具有內嵌惡意程式碼的 Word 附件給組織內使用者的事件。

- 使用者開啟該附件並啟用內容。
- 權限提升的攻擊將會展開，而來自遠端電腦的攻擊者將會擁有受害者裝置的系統管理員權限。
- 攻擊者接著會從遠端存取該使用者的其他裝置。 此安全性缺口可能會影響整個組織。

Microsoft Defender ATP 有助於解決此類安全性事件。

- 在我們的範例中，Microsoft Defender ATP 會偵測到裝置執行不正常的程式碼、發生處理序權限提升、被插入惡意程式碼，並發出可疑遠端殼層。
- 根據來自裝置的這些動作，Microsoft Defender ATP [會將裝置分類為高風險](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/alerts-queue#severity)，並在 Microsoft Defender 資訊安全中心入口網站中包含可疑活動的詳細報告。

因為您有 Intune 裝置合規性政策，可將具有「中等」  或「高」  風險的裝置分類為不符合規範，所以遭到入侵的裝置會被分類為不符合規範。 此分類可讓您的條件式存取原則開始介入，並防止該裝置存取您的公司資源。

## <a name="prerequisites"></a>必要條件

若要搭配 Intune 使用 Microsoft Defender ATP，請確認下列項目已設定且可供使用：

- 適用於 Enterprise Mobility + Security E3 和 Windows E5 (或 Microsoft 365 企業版 E5) 的授權租用戶
- Microsoft Intune 環境，搭配已加入 Azure AD 且[受 Intune 管理的](../enrollment/windows-enroll.md) Windows 10 裝置
- [Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) 和 Microsoft Defender 資訊安全中心 (ATP 入口網站) 的存取權

> [!NOTE]
> iOS 和 Android 的 Intune 應用程式保護原則不支援 Microsoft Defender ATP。

## <a name="enable-microsoft-defender-atp-in-intune"></a>在 Intune 中啟用 Microsoft Defender ATP

您必須執行的第一個步驟是在 Intune 與 Microsoft Defender ATP 之間設定服務對服務連線。 這需要對 Microsoft Defender 資訊安全中心與 Intune 的存取權。

### <a name="to-enable-defender-atp"></a>啟用 Defender ATP

您只需要為每個租用戶啟用 Defender ATP 一次。

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 選取 [端點安全性]   > [Microsoft Defender ATP]  ，然後選取 [開啟 Microsoft Defender 資訊安全中心]  。

   ![選取以開啟 [Microsoft Defender 資訊安全中心]](./media/advanced-threat-protection/atp-device-compliance-open-microsoft-defender.png)

4. 在 **Microsoft Defender 資訊安全中心**中：
    1. 選取 [設定]   > [進階功能]  。
    2. 針對 [Microsoft Intune 連線]  ，選擇 [開啟]  ：

        ![啟用 Intune 的連線](./media/advanced-threat-protection/atp-security-center-intune-toggle.png)

    3. 選取 [儲存喜好設定]  。

4. 回到 Microsoft Endpoint Manager 系統管理中心內的 [Microsoft Defender ATP]  。 在 [MDM 合規性原則設定]  底下，將 [將 10.0.15063 版及更新版本的 Windows 裝置連線到 Microsoft Defender ATP]  設定為 [開啟]  。

5. 選取 [儲存]  。

> [!TIP]
> 當您將新的應用程式整合到 Intune Mobile Threat Defense 並啟用 Intune 連線時，Intune 會在 Azure Active Directory 中建立傳統條件式存取原則。 您整合的每個 MTD 應用程式 (包括 [Defender ATP](advanced-threat-protection.md) 或任何其他 [MTD 合作夥伴](mobile-threat-defense.md#mobile-threat-defense-partners)) 都會建立新的傳統條件式存取原則。 這些原則可以忽略，但不應編輯、刪除或停用。
>
> 如已刪除傳統原則，則將需要刪除負責建立該原則的 Intune 連線，然後再次設定。 這會重新建立此傳統原則。 不支援將 MTD 應用程式傳統原則移轉至條件式存取的新原則類型。
>
> 適用於 MTD 應用程式的傳統條件式存取原則：
>
> - 由 Intune MTD 用於要求裝置必須在 Azure AD 中註冊，以便它們與 MTD 合作夥伴通訊之前擁有裝置識別碼。 此識別碼為必要，以便裝置成功向 Intune 報告其狀態。
> - 不會影響任何其他雲端應用程式或資源。
> - 不同於您可能會建立用來協助管理 MTD 的條件式存取原則。
> - 根據預設，不會與您用於評估的其他條件式存取原則互動。
>
> 若要檢視傳統條件式存取原則，請前往 [Azure](https://portal.azure.com/#home) 中的 [Azure Active Directory]   > [條件式存取]   > [傳統原則]  。

## <a name="onboard-devices-by-using-a-configuration-profile"></a>使用組態設定檔將裝置上線

在 Intune 與 Microsoft Defender ATP 之間建立服務對服務連線之後，您會將由 Intune 管理的裝置上線到 ATP，以便收集並使用其風險層級相關資料。 若要讓裝置上線，您必須使用 Microsoft Defender ATP 的裝置組態設定檔。

當您建立與 Microsoft Defender ATP 的連線之後，Intune 會從 Microsoft Defender ATP 收到 Microsoft Defender ATP 上線組態套件。 此套件會使用裝置組態設定檔部署到裝置。 該組態套件會設定裝置，使其與 [Microsoft Defender ATP 服務](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)通訊，以掃描檔案、偵測威脅，以及向 Microsoft Defender ATP 回報風險。

當您使用組態套件將裝置上線之後，您不需要再次執行此動作。 您也可以使用[群組原則或 System Center Configuration Manager (SCCM)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints) 來將裝置上線。

### <a name="create-the-device-configuration-profile"></a>建立裝置組態設定檔

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [裝置]   > [組態設定檔]   > [建立設定檔]  。
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
8. [指派裝置組態設定檔](../configuration/device-profile-assign.md)給您要使用 Microsoft Defender ATP 評估的裝置。

## <a name="create-and-assign-the-compliance-policy"></a>建立及指派合規性政策

合規性政策會決定您視為可接受的裝置風險層級。

### <a name="create-the-compliance-policy"></a>建立合規性原則

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [裝置]   > [合規性原則]   > [建立原則]  。
3. 輸入 [名稱]  和 [描述]  。
4. 在 [平台]  中，選取 [Windows 10 及更新版本]  。
5. 在 [設定]  底下，選取 [Microsoft Defender ATP]  。
6. 將 [要求裝置不高於電腦風險分數]  設定為您偏好的層級。

   威脅等級分類是[由 Windows Defender ATP 所決定的](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/alerts-queue) \(部分機器翻譯\)。

   - **清除**：這個層級最安全。 裝置不能在具有任何現有威脅的情況下，繼續存取公司資源。 發現任何威脅時，即會將裝置評估為不相容。 (Microsoft Defender ATP 使用值「安全」  。)
   - **低**︰裝置只有在僅存在低層級威脅的情況下才能符合規範。 具有中或高威脅等級的裝置不符合規範。
   - **中**︰如果在裝置上發現的威脅為低或中層級，則會將裝置評估為符合規範。 如果偵測到高層級的威脅，則會將裝置判斷為不相容。
   - **高**：這個層級最不安全，且會允許所有威脅層級。 因此具有高、中或低威脅層級的裝置都會被評估為符合規範。

7. 選取 [確定]  ，然後選取 [建立]  以儲存您的變更 (並建立原則)。
8. [指派裝置合規性政策](create-compliance-policy.md#assign-the-policy)給適用的群組。

## <a name="create-a-conditional-access-policy"></a>建立條件式存取原則

條件式存取原則會封鎖超出您在合規性政策中設定之威脅層級的裝置，使其無法存取資源。 您可以封鎖裝置，使其無法存取公司資源，例如 SharePoint 或 Exchange Online。

> [!TIP]
> 條件式存取是一項 Azure Active Directory (Azure AD) 技術。 從 Microsoft Endpoint Manager 系統管理中心所存取條件式存取節點與從 *Azure AD* 存取的節點相同。

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 選取 [端點安全性]   > [條件式存取]   > [新增原則]  。

3. 輸入原則 [名稱]  ，然後選取 [使用者和群組]  。 使用 [包含] 或 [排除] 選項來針對原則新增群組，並選取 [完成]  。

4. 選取 [雲端應用程式]  ，然後選擇要保護哪些應用程式。 例如，選擇 [選取應用程式]  ，然後選取 [Office 365 SharePoint Online]  和 [Office 365 Exchange Online]  。

   按一下 [完成]  以儲存您的變更。

5. 選取 [條件]   > [用戶端應用程式]  來將原則套用至應用程式和瀏覽器。 例如，選取 [是]  ，然後啟用 [瀏覽器]  和 [行動應用程式及桌面用戶端]  。

   按一下 [完成]  以儲存您的變更。

6. 選取 [授與]  ，以根據裝置合規性套用條件式存取。 例如，選取 [授與存取權]   > [裝置需要標記為合規]  。

    選擇 [選取]  以儲存您的變更。

7. 選取 [啟用原則]  ，然後選取 [建立]  以儲存變更。

## <a name="monitor-device-compliance"></a>監視裝置合規性

接下來，監視具有 Microsoft Defender ATP 合規性政策之裝置的狀態。

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 選取 [裝置]   > [監視]   > [原則合規性]  。

3. 在清單中尋找您的 Microsoft Defender ATP 政策，並查看有哪些裝置是符合規範或不符合規範。

## <a name="view-onboarding-status"></a>檢視上線狀態

若要檢視所有受 Intune 管理的 Windows 10 裝置上線狀態，您可以前往 [裝置相容性]   > [Microsoft Defender ATP]  。 您也可以在此頁面中開始建立裝置組態設定檔，以便將更多裝置上線至 Microsoft Defender ATP。

## <a name="next-steps"></a>後續步驟

[Microsoft Defender ATP 條件式存取](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/conditional-access) \(部分機器翻譯\)

[Microsoft Defender ATP 風險儀表板](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard) \(部分機器翻譯\)

[搭配 ATP 弱點管理使用安全性工作來補救裝置上的問題](atp-manage-vulnerabilities.md)。

[裝置合規性原則入門](device-compliance-get-started.md)
