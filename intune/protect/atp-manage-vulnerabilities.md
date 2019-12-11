---
title: 使用 Intune 來補救 Microsoft Defender ATP 所找到的弱點 - Azure | Microsoft Docs
description: 了解如何從威脅和弱點管理中管理安全性工作，其為 Intune 主控台內 Microsoft Defender 進階威脅防護 (ATP) 的一部分。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/06/2019
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
ms.openlocfilehash: a9529f5b3047a8d4ca2a1e9c22d2c4427761078c
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "73754884"
---
# <a name="use-intune-to-remediate-vulnerabilities-identified-by-microsoft-defender-atp"></a>使用 Intune 來補救 Microsoft Defender ATP 識別出的弱點

當您整合 Intune 與 Microsoft Defender 進階威脅防護 (ATP) 時，可利用 ATP 的威脅和弱點管理 (TVM)，並使用 Intune 來補救 TVM 識別出的端點弱點。 這項整合會產生一種以風險為基礎的方法來探索及優先處理弱點，可改善整個環境中的補救回應時間。

[威脅和弱點管理](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/next-gen-threat-and-vuln-mgt) \(部分機器翻譯\) 為 [Microsoft Defender 進階威脅防護](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection) \(部分機器翻譯\) 的一部分。

## <a name="how-integration-works"></a>整合的運作方式

將 Intune 連線至 Microsoft Defender 進階威脅防護之後，ATP 就會接收來自受控裝置的威脅和弱點詳細資料。

在 Microsoft Defender 資訊安全中心的主控台內，ATP 安全性管理員會檢閱有關端點弱點的資料。 管理員接著會使用按一下的方式來建立安全性工作，為有弱點的裝置加上旗標以進行補救。 安全性工作會立即傳遞至 Intune 主控台，讓 Intune 管理員能夠檢視它們。 安全性工作會識別弱點的類型、優先順序、狀態，以及要採取來補救弱點的步驟。 Intune 管理員選擇接受或拒絕工作。

接受工作時，Intune 管理員接著會透過 Intune，使用提供來作為安全性工作一部分的指引來補救弱點。

進行補救的常見動作包括：

- **封鎖**應用程式執行
- **部署**作業系統更新以降低弱點的風險。
- **修改**登錄值。
- **停用**或**啟用**會對弱點產生作用的設定。
- **需要注意**會在未提供任何適當的建議時，為管理員警示威脅。

範例工作流程：

- 在 Microsoft Defender ATP 內，發現了名為 Contoso Media Player v4 之應用程式的弱點，而管理員建立了安全性工作來更新該應用程式。 Contoso Media Player 是使用 Intune 部署的非受控應用程式。

  此安全性工作會出現在 Intune 主控台中且狀態為「擱置」：

  ![在 Intune 主控台中檢視安全性工作的清單](./media/atp-manage-vulnerabilities/temp-security-tasks.png)

- Intune 管理員會選取安全性工作來檢視有關工作的詳細資料。  管理員接著選取 [接受]  ，這會更新 Intune 中的狀態，且在 ATP 中為 [已接受]  。

  ![接受或拒絕安全性工作](./media/atp-manage-vulnerabilities/temp-accept-task.png)

- 管理員接著根據所提供的指引來補救工作。 這份指引會根據所需的補救類型而異。 可供使用時，補救指引會包含可在 Intune 中開啟設定相關窗格的連結。

  因為此範例中的媒體播放器不是受控應用程式，所以 Intune 只會提供文字指示。 如果應用程式是受控的，Intune 就會提供指示來下載更新的版本，並提供連結來開啟適用於應用程式的部署，如此即可將已更新的檔案新增至部署。

- 完成補救之後，Intune 管理員會開啟安全性工作並選取 [完成工作]  。  系統會針對 Intune 及在 ATP 中更新補救狀態，而安全性管理員會確認已修訂的弱點狀態。

## <a name="prerequisites"></a>必要條件  

**訂閱**：

- Microsoft Intune  
- Microsoft Defender 進階威脅防護 ([註冊免費試用版](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-main-abovefoldlink))。

**適用於 ATP 的 Intune 設定**：

- 設定與 Microsoft Defender ATP 的服務對服務連線。
- 將包含 **Microsoft Defender ATP (Windows 10 Desktop)** 設定檔類型的裝置設定原則，部署至將由 ATP 評估風險的裝置。

  如需如何設定 Intune 來與 ATP 一同運作的相關資訊，請參閱[在 Intune 中使用條件式存取強制符合 Windows Defender ATP 的合規性](advanced-threat-protection.md#enable-microsoft-defender-atp-in-intune)。

## <a name="work-with-security-tasks"></a>使用安全性工作

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 選取 [端點安全性]   > [安全性工作]  。

3. 從清單中選取工作來開啟資源視窗，以顯示該安全性工作的其他詳細資料。

   檢視安全性工作資源視窗時，您可以選取其他連結：

   - 受控應用程式：檢視有弱點的應用程式。 當弱點適用於多個應用程式時，您將看到篩選過的應用程式清單。
   - 裝置：檢視「有弱點的裝置」  清單，您可以從此處連結至含有更多該裝置弱點之詳細資料的項目。
   - 要求者：使用連結以將郵件傳送給提交此安全性工作的管理員。
   - 附註：開啟安全性工作時，讀取要求者所提交的自訂訊息。

4. 選取 [接受]  或 [拒絕]  ，以針對您規劃的動作來將通知傳送給 ATP。 當您接受或拒絕工作時，您可以提交要傳送給 ATP 的附註。

5. 接受工作之後，重新開啟安全性工作 (如果它已關閉)，並遵循補救詳細資料來補救此弱點。 安全性工作詳細資料中由 ATP 提供的指示會根據所涉及的弱點而有所不同。

   如果可以執行此動作，則補救指示會包含連結以在 Intune 主控台中開啟相關設定物件。

6. 完成補救步驟之後，開啟安全性工作，然後選取 [完成工作]  。  此動作會在 Intune 與 ATP 中更新安全性工作狀態。

補救成功之後，ATP 中風險暴露程度的分數就會根據來自已補救裝置的新資訊而下降。

## <a name="next-steps"></a>後續步驟
深入了解 Intune 和 [Microsoft Defender ATP](advanced-threat-protection.md)。

檢閱 Intune [Mobile Threat Defense](mobile-threat-defense.md)。

檢閱 Microsoft Defender ATP 中的[威脅與弱點管理儀表板](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/tvm-dashboard-insights)。
