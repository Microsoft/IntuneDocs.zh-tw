---
title: 在 Microsoft Intune 中使用 Windows Defender ATP - Azure | Microsoft Docs
description: 了解如何在端對端案例中啟用 Windows Defender 進階威脅防護 (ATP)，包括在 Intune 和 Windows Defender 資訊安全中心 (ATP 入口網站) 中開啟 ATP、使用 ATP 組態設定檔將裝置上線、建立 Intune 裝置合規性原則、建立 Azure AD 條件式存取原則，以及監視裝置合規性。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: de80092647462f83fb92303080239fd30198bd3c
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180229"
---
# <a name="enable-windows-defender-atp-with-conditional-access-in-intune"></a>在 Intune 中使用條件式存取啟用 Windows Defender ATP

Windows Defender 進階威脅防護 (ATP) 和 Microsoft Intune 能夠一起運作以協助防止安全性缺口，並協助限制因缺口而在組織內所造成的影響。

此功能適用於：Windows 10 裝置

例如，有人傳送內嵌惡意程式碼的 Word 附件給組織內的使用者。 使用者開啟該附件並啟用內容。 權限提升的攻擊將會展開，而來自遠端電腦的攻擊者將會擁有受害者裝置的系統管理員權限。 攻擊者接著會從遠端存取該使用者的其他裝置。

此安全性缺口可能會影響整個組織。

Windows Defender ATP 可以解決這類的安全性事件。 Windows Defender 資訊安全中心 (ATP 主控台) 會將該裝置報告為「高風險」，並包含可疑活動的詳細報表。 在本例中，Windows Defender ATP 會偵測到裝置執行不正常的程式碼，發生處理程序權限提升，插入惡意程式碼，並發出可疑的遠端殼層。 Windows Defender ATP 接著會提供能降低威脅的選項。

您可以使用 Intune 建立合規性原則，以判斷可接受的風險層級。 如果裝置超過此風險，該裝置將會變成不符合規範。 透過搭配 Azure Active Directory (AD) 條件式存取，系統將會封鎖該使用者存取公司資源。

本文將示範下列項目的作法：

- 在 ATP 中啟用 Intune，並在 Intune 中啟用 ATP。 這些工作會在 Intune 與 Windows Defender ATP 之間建立服務對服務的連線。 此連線可讓 Windows Defender ATP 撰寫針對您 Intune 裝置的電腦風險。
- 在 Intune 中建立合規性原則。
- 根據裝置的威脅層級，針對裝置啟用 Azure Active Directory (AD) 中的條件式存取。

## <a name="prerequisites"></a>必要條件

若要搭配 Intune 使用 ATP，請確認您已設定下列項目，並已可供使用：

- 適用於 Enterprise Mobility + Security E3 和 Windows E5 (或 Microsoft 365 企業版 E5) 的授權租用戶
- Microsoft Intune 環境，搭配已加入 Azure AD 且[受 Intune 管理的](windows-enroll.md) Windows 10 裝置
- [Windows Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) 和 Windows Defender 資訊安全中心 (ATP 入口網站) 的存取權

## <a name="enable-windows-defender-atp-in-intune"></a>在 Intune 中啟用 Windows Defender ATP

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [All services] (所有服務)，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選取 [裝置合規性] > [Windows Defender ATP] > [開啟 Windows Defender 資訊安全中心]。

    ![選取以開啟 [Windows Defender 資訊安全中心]](./media/atp-device-compliance-open-windows-defender.png)

4. 在 [Windows Defender 資訊安全中心] 中：
    1. 選取 [設定] > [進階功能]。
    2. 針對 [Microsoft Intune 連線]，選擇 [開啟]：

        ![啟用 Intune 的連線](./media/atp-security-center-intune-toggle.png)

    3. 選取 [儲存喜好設定]。

5. 返回 Intune，[裝置合規性] > [Windows Defender ATP]。 將 [將 Windows 裝置 10.0.15063 版和更高版本連線至 Windows Defender ATP] 設定為 [開啟]。
6. 選取 [儲存]。

通常您只需執行此工作一次即可。 因此，如果您的 Intune 資源中已啟用 ATP，便無需再次執行它。

## <a name="onboard-devices-using-a-configuration-profile"></a>使用組態設定檔將裝置上線

當終端使用者在 Intune 中註冊時，您可以使用組態設定檔將不同設定推送到裝置。 這也適用於 Windows Defender ATP。

Windows Defender 包含上架設定套件，該套件會與 [Windows Defender ATP 服務](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection)通訊，以掃描檔案、偵測威脅，以及向 Windows Defender ATP 報告風險。

當您上架時，Intune 會從 Windows Defender ATP 取得自動產生的設定套件。 當將設定檔推送或部署到裝置時，也會將此設定套件推送至裝置。 這可讓 Windows Defender ATP 為裝置監視威脅。

當您使用設定套件將裝置上線之後，就不需要再次執行它。 您也可以使用[群組原則或 System Center Configuration Manager (SCCM)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-windows-defender-advanced-threat-protection) 來將裝置上線。

### <a name="create-the-configuration-profile"></a>建立組態設定檔

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務]，篩選 [Intune]，然後選取 [Microsoft Intune]。
2. 選取 [裝置設定] > [設定檔] > [建立設定檔]。
3. 輸入 [名稱] 和 [描述]。
4. 針對 [平台]，選取 [Windows 10 及更新版本]
5. 針對 [設定檔類型]，選取 [Windows Defender ATP (Windows 10 Desktop)]。
6. 設定這些設定：

  - **Windows Defender ATP 用戶端設定套件類型**：選取 [上架] 可將設定套件新增至設定檔。 選取 [下架] 可從設定檔移除設定套件。
  
    > [!NOTE] 
    > 如果您已經與 Windows Defender ATP 正確建立連線，則 Intune 會自動將您的組態設定檔**上架**。
  
  - **所有檔案的範例共用**：[啟用] 可收集範例並與 Windows Defender ATP 共用。 例如，如果您看到可疑檔案，可將它提交至 Windows Defender ATP 以進行深入分析。 **未設定**不與 Windows Defender ATP 共用任何範例。
  - **加快遙測回報頻率**：針對高風險的裝置 [啟用] 此設定，以便更頻繁地將遙測回報給 Windows Defender ATP 服務。

    [使用 System Center Configuration Manager 將 Windows 10 電腦上線](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-sccm-windows-defender-advanced-threat-protection)中有這些 Windows Defender ATP 設定的更多詳細資料。

7. 選取 [確定]，然後選取 [建立] 以儲存您的變更，這會建立設定檔。

## <a name="create-the-compliance-policy"></a>建立合規性原則
合規性原則會決定裝置上可接受的風險層級。

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務]，篩選 [Intune]，然後選取 [Microsoft Intune]。
2. 選取 [裝置合規性] > [原則] > [建立原則]。
3. 輸入 [名稱] 和 [描述]。
4. 在 [平台] 中，選取 [Windows 10 及更新版本]。
5. 在 [Windows Defender ATP] 設定中，將 [要求裝置不高於電腦風險分數] 設定為您偏好的層級：

  - **清除**︰這個層級最安全。 裝置不能在具有任何現有威脅的情況下，繼續存取公司資源。 發現任何威脅時，即會將裝置評估為不相容。
  - **低**︰裝置只有在僅存在低層級威脅的情況下才能符合規範。 具有中或高威脅層級的裝置，將會不符合規範。
  - **中**︰如果在裝置上發現的威脅為低或中層級，則會將裝置評估為符合規範。 如果偵測到高層級的威脅，則會將裝置判斷為不相容。
  - **高**：這個層級最不安全，且會允許所有威脅層級。 因此具有高、中或低威脅層級的裝置，都會被評估為符合規範。

6. 選取 [確定]，然後選取 [建立] 以儲存您的變更 (並建立原則)。

## <a name="assign-the-policy"></a>指派原則

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務]，篩選 [Intune]，然後選取 [Microsoft Intune]。
2. 選取 [裝置合規性] > [原則] > 選取您的 Windows Defender ATP 合規性原則。
3. 選取 [指派]。
4. 包含或排除您的 Azure AD 群組，以將原則指派給它們。
5. 若要將原則部署到群組中，請選取 [儲存]。 系統將會對原則的目標使用者裝置進行合規性評估。

## <a name="create-an-azure-ad-conditional-access-policy"></a>建立 Azure AD 條件式存取原則
*如果*裝置不符合規範，條件式存取原則會封鎖對資源的存取。 因此，如果裝置超過威脅層級，您可以封鎖該裝置對公司資源的存取，例如 SharePoint 或 Exchange Online。

1. 在 [Azure 入口網站](https://portal.azure.com)中，開啟 [Azure Active Directory] > [條件式存取] > [新增原則]。
2. 輸入原則 [名稱]，然後選取 [使用者和群組]。 使用 [包含] 或 [排除] 選項來針對原則新增群組，並選取 [完成]。
3. 選取 [雲端應用程式]，然後選擇要保護哪些應用程式。 例如，選擇 [選取應用程式]，然後選取 [Office 365 SharePoint Online] 和 [Office 365 Exchange Online]。

    按一下 [完成] 以儲存您的變更。

4. 選取 [條件] > [用戶端應用程式] 來將原則套用至應用程式和瀏覽器。 例如，選取 [是]，然後啟用 [瀏覽器] 和 [行動應用程式及桌面用戶端]。

    按一下 [完成] 以儲存您的變更。

5. 選取 [授與] 以根據裝置合規性套用條件式存取。 例如，選取 [授與存取權] > [裝置需要標記為合規]。

    選擇 [選取] 以儲存您的變更。

6. 選取 [啟用原則]，然後選取 [建立] 以儲存變更。

[什麼是條件式存取？](conditional-access.md)是很好的資源。

## <a name="monitor-device-compliance"></a>監視裝置合規性
接下來，監視具有 Windows Defender ATP 合規性原則之裝置的狀態。

1. 在 [Azure 入口網站](https://portal.azure.com)中，選取 [所有服務]，篩選 [Intune]，然後選取 [Microsoft Intune]。
2. 選取 [裝置合規性] > [原則合規性]。
3. 在清單中尋找您的 Windows Defender ATP 原則，並查看有哪些裝置是符合規範或不符合規範。

## <a name="more-good-stuff"></a>更多好東西
[Windows Defender ATP 條件式存取](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/conditional-access-windows-defender-advanced-threat-protection) \(英文\)  
[Windows Defender ATP 風險儀表板](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) \(英文\)  
[裝置合規性原則入門](device-compliance-get-started.md)  
[Azure AD 中的條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
