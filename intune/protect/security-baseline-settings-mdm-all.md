---
title: 適用於 Windows 10 MDM 的 Intune 安全性基準設定
titleSuffix: Microsoft Intune
description: 請參閱您可以使用 Microsoft Intune 管理的不同 Windows MDM 安全性基準版本的預設值和可用設定。
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
zone_pivot_groups: windows-mdm-versions
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6b2cb1b277f78ed81dea8c2d82eff6860182ea5d
ms.sourcegitcommit: 7cc45ef52dda08479bc6bdff7d11d2f6c0e7b93b
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 12/06/2019
ms.locfileid: "74899260"
---
# <a name="windows-mdm-security-baseline-settings-for-intune"></a>適用於 Intune 的 Windows MDM 安全性基準設定

針對執行 Windows 10 或更新版本的裝置，查看 Microsoft Intune 支援的 MDM 安全性基準設定。 此基準中設定的預設值代表適用裝置的建議設定。 一個基準的預設值可能不符合其他安全性基準的預設值，或來自此基準的其他版本。

- 若要瞭解如何使用安全性基準搭配 Intune，以及如何在您的安全性基準設定檔中升級基準版本，請參閱[使用安全性基準](../security-baselines.md)。
- 最新的基準版本為**5 月2019的 MDM 安全性基準**

請務必選取您想要查看的基準版本。
<!-- Cookies might be required to enable some browsers to display the zone options -->

::: zone pivot="mdm-may-2019"
**2019 年 5 月的 MDM 安全性基準**：  
> [!NOTE]
> 在2019年6月，「5月2019」範本的*MDM 安全性基準*已發行為正式推出（不在預覽階段）。 此版本的安全性基準會取代先前的基準，也就是*2018 年10月的 MDM 安全性基準*。  在2019版之前建立的設定檔不會更新，以反映5月2019版本中的設定和值。  雖然您無法根據預覽範本來建立新的設定檔，您可以編輯並繼續使用先前根據預覽範本建立的設定檔。

若要深入瞭解此版本的基準在舊版中的變更內容，請參閱[新範本中的變更](#whats-changed-in-the-new-template)。

::: zone-end
::: zone pivot="mdm-preview"
**預覽 - 2018 年 10 月的 MDM 安全性基準**：  
> [!NOTE]
> 這是在2018年10月發行之 MDM 安全性基準的預覽版本。 此預覽基準已于2019年6月（已正式推出（非預覽版）的*MDM 安全性基準（2019可能*為預覽版本））中取代。 *5 月2019基準的 Mdm 安全性基準*可用性之前所建立的設定檔不會更新，以反映5月2019版的 Mdm 安全性基準中的設定和值。 雖然您無法根據預覽範本來建立新的設定檔，您可以編輯並繼續使用先前根據預覽範本建立的設定檔。

::: zone-end
::: zone pivot="mdm-may-2019,mdm-preview"

## <a name="above-lock"></a>上方鎖定

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) (原則 CSP - AboveLock)。  

- **封鎖快顯通知的顯示**：  
  此原則設定可讓您防止應用程式通知出現在鎖定畫面上。 如果您啟用此原則設定，任何應用程式通知都不會顯示在鎖定畫面上。 如果您停用或未設定此原則設定，則使用者可以選擇哪些應用程式會在鎖定畫面上顯示通知。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067101)

  **預設值**：是

::: zone-end
::: zone pivot="mdm-may-2019"

- **語音從鎖定的畫面啟用應用程式**：  
  **預設**：停用

::: zone-end
::: zone pivot="mdm-may-2019,mdm-preview"

## <a name="app-runtime"></a>應用程式執行階段

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - AppRuntime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime) (原則 CSP - AppRuntime)。

- **Microsoft 帳戶對 Windows 市集應用程式為選擇性項目**：  
  此原則設定可讓您控制 Microsoft 帳戶對需要帳戶來登入的 Windows 市集應用程式是否為選擇性項目。 此原則只會影響支援它的 Windows 市集應用程式。 如果您啟用此原則設定，通常需要 Microsoft 帳戶登入的 Windows 市集應用程式可讓使用者改為使用企業帳戶登入。 如果您停用或未設定此原則設定，則使用者必須使用 Microsoft 帳戶登入。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067104)
  
  **預設**：啟用

## <a name="application-management"></a>應用程式管理

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) (原則 CSP - ApplicationManagement)。

::: zone-end
::: zone pivot="mdm-may-2019"

- **封鎖使用者對安裝的控制**：  
  此原則設定允許使用者變更通常僅供系統管理員使用的安裝選項。 如果您啟用此原則設定，則會略過 Windows Installer 的部分安全性功能。 它允許安裝完成，否則會因為安全性違規而暫停。 如果您停用或未設定此原則設定，Windows Installer 的安全性功能可防止使用者變更通常保留給系統管理員的安裝選項，例如指定要安裝檔案的目錄。 如果 Windows Installer 偵測到安裝套件已允許使用者變更受保護的選項，則會停止安裝並顯示訊息。 這些安全性功能只有在安裝程式在具有許可權的安全性內容中執行時才會運作，其可存取使用者拒絕的目錄。 此原則設定是針對較不嚴格的環境所設計。 它可以用來規避安裝程式中防止安裝軟體的錯誤。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067060)

  **預設值**：是

- **以較高的許可權封鎖 MSI 應用程式安裝**：  
  此原則設定會指示 Windows Installer 在系統上安裝任何程式時使用較高的權限。

  - *如果您啟用此原則設定*，許可權會延伸至 [所有程式]。 一般而言，這些許可權會保留給指派給使用者的程式（在桌面上提供）、指派給電腦（自動安裝），或可在 [控制台] 的 [新增或移除程式] 中使用。 此設定檔設定可讓使用者安裝需要存取使用者可能沒有許可權可查看或變更之目錄的程式，包括高度受限電腦上的目錄。

  - *如果您停用或未設定此原則設定*，系統會在安裝系統管理員不會發佈或提供的程式時，套用目前使用者的許可權。 注意：此原則設定會出現在 [電腦設定] 和 [使用者設定] 資料夾中。 若要讓此原則設定生效，您必須在這兩個資料夾中啟用它。 注意：熟練的使用者可以利用此原則設定授與的許可權來變更其許可權，並取得受限制檔案和資料夾的永久存取權。 此原則設定的使用者設定版本不一定是安全的。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067134)

  **預設值**：是

::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

- **封鎖遊戲 DVR (僅限桌面版)** ：  
  設定是否允許錄製和廣播遊戲。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067056)

  **預設值**：是

## <a name="auto-play"></a>自動播放

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - Autoplay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay) (原則 CSP - 自動播放)。

- **自動播放預設的自動執行行為**：  
  此設定會影響 Autorun 命令的預設行為。 Autorun 命令儲存在 autorun.inf 檔案中，可以啟動安裝程式或其他常式。 [啟用]  時，系統管理員可以變更 Windows Vista 或更新版本執行所在裝置上的預設自動執行行為。 行為可以設定為：a) 完全停用 autorun 命令，或 b) 還原回 Windows Vista 之前自動執行 autorun 命令的行為。 當設定為 [停用]  或 [未設定]  時，執行 Windows Vista 或更新版本的裝置會提示使用者是否應執行 autorun 命令。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067133)

  **預設值**：不執行

- **自動播放模式**：  
  此原則設定可讓您關閉自動播放功能。 當您將媒體插入磁碟機中，自動播放就會開始從磁碟機讀取。 如此一來，音訊媒體上的程式安裝檔和音樂便會立即啟動。 在 Windows XP SP2 和更早版本中，抽取式磁碟機 (例如軟碟機，但不是 CD-ROM 光碟機) 和網路磁碟機預設會停用自動播放。 從 Windows XP SP2 開始，也會為抽取式磁碟機啟用自動播放，包括 ZIP 磁碟和某些 USB 大型存放裝置。 如果您啟用此原則設定，則會在 CD-ROM 和抽取式媒體磁碟機上停用自動播放，或在所有磁碟機上停用自動播放。 此原則設定會停用其他類型磁碟機的自動播放。 您無法在預設會停用自動播放的磁碟機上使用此設定來啟用自動播放。 如果您停用或未設定此原則設定，就會啟用自動播放。 注意：此原則設定會出現在 [電腦設定] 和 [使用者設定] 資料夾中。 如果原則設定有衝突，則 [電腦設定] 的原則設定優先於 [使用者設定] 的原則設定。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2066793)

  **預設**：停用

- **封鎖非磁碟區裝置的自動播放**：  
  此原則設定為不允許 MTP 裝置 (例如相機或手機) 進行自動播放。 如果您啟用此原則設定，則相機或手機等 MTP 裝置不允許進行自動播放。 如果您停用或未設定此原則設定，就會針對非磁碟區裝置啟用自動播放。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067106)

  **預設**：啟用

## <a name="bitlocker"></a>BitLocker

如需詳細資訊，請參閱 Windows 文件中的[原則 CSP - Bitlocker](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker) \(部分機器翻譯\)。

- **BitLocker 抽取式磁碟機原則**：  
  此原則設定用來控制加密方法與加密強度。 此原則的值決定 BitLocker 用於加密的加密強度。 企業可能想要控制加密層級以提高安全性 (AES-256 強於 AES-128)。 如果您啟用此設定，則能夠為固定資料磁碟機、作業系統磁碟機和抽取式資料磁碟機個別設定加密演算法和金鑰加密強度。 如果是固定磁碟機和作業系統磁碟機，建議您使用 XTS-AES 演算法。 如果是抽取式磁碟機，若在其他未執行 Windows 10 1511 版或更新版本的裝置上使用該磁碟機，您應該使用 AES-CBC 128 位元或 AES-CBC 256 位元。 如果磁碟機已加密或加密正在進行中，變更加密方法就沒有任何作用。 在這些情況下，會忽略這個原則設定。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067140)

  針對 BitLocker 抽取式磁碟機原則，請設定下列設定：

  - **寫入存取需要加密**：  
    **預設值**：是

::: zone-end
::: zone pivot="mdm-preview"

- **BitLocker 抽取式磁碟機原則**：  
  此原則設定用來控制加密方法與加密強度。 此原則的值決定 BitLocker 用於加密的加密強度。 企業可能想要控制加密層級以提高安全性 (AES-256 強於 AES-128)。 如果您啟用此設定，則能夠為固定資料磁碟機、作業系統磁碟機和抽取式資料磁碟機個別設定加密演算法和金鑰加密強度。 如果是固定磁碟機和作業系統磁碟機，建議您使用 XTS-AES 演算法。 如果是抽取式磁碟機，若在其他未執行 Windows 10 1511 版或更新版本的裝置上使用該磁碟機，您應該使用 AES-CBC 128 位元或 AES-CBC 256 位元。 如果磁碟機已加密或加密正在進行中，變更加密方法就沒有任何作用。 在這些情況下，會忽略這個原則設定。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067140)

  針對 BitLocker 抽取式磁碟機原則，請設定下列設定：

  - **寫入存取需要加密**：  
    **預設值**：是  

  - **加密方法**：  
    **預設值**：AES 256 位元 CBC  

- **BitLocker 固定磁碟機原則**：  
  此原則設定用來控制加密方法與加密強度。 此原則的值決定 BitLocker 用於加密的加密強度。 企業可能想要控制加密層級以提高安全性 (AES-256 強於 AES-128)。 如果您啟用此設定，則能夠為固定資料磁碟機、作業系統磁碟機和抽取式資料磁碟機個別設定加密演算法和金鑰加密強度。 如果是固定磁碟機和作業系統磁碟機，建議您使用 XTS-AES 演算法。 如果是抽取式磁碟機，若在其他未執行 Windows 10 1511 版或更新版本的裝置上使用該磁碟機，您應該使用 AES-CBC 128 位元或 AES-CBC 256 位元。 如果磁碟機已加密或加密正在進行中，變更加密方法就沒有任何作用。 在這些情況下，會忽略這個原則設定。

  針對 BitLocker 固定式磁碟機原則，請設定下列設定：

  - **加密方法**：  
    **預設值**：AES 256 位元 XTS  

- **BitLocker 系統磁碟機原則**：  
  此原則設定用來控制加密方法與加密強度。 此原則的值決定 BitLocker 用於加密的加密強度。 企業可能想要控制加密層級以提高安全性 (AES-256 強於 AES-128)。 如果您啟用此設定，則能夠為固定資料磁碟機、作業系統磁碟機和抽取式資料磁碟機個別設定加密演算法和金鑰加密強度。 如果是固定磁碟機和作業系統磁碟機，建議您使用 XTS-AES 演算法。 如果是抽取式磁碟機，若在其他未執行 Windows 10 1511 版或更新版本的裝置上使用該磁碟機，您應該使用 AES-CBC 128 位元或 AES-CBC 256 位元。 如果磁碟機已加密或加密正在進行中，變更加密方法就沒有任何作用。 在這些情況下，會忽略這個原則設定。

  針對 BitLocker 系統磁碟機原則，請設定下列設定：

  - **加密方法**：  
    **預設值**：AES 256 位元 XTS

::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

## <a name="browser"></a>瀏覽器

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - Browser](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) (原則 CSP - 瀏覽器)。

- **Microsoft Edge 需要 SmartScreen**：  
  Microsoft Edge 預設會使用 Microsoft Defender SmartScreen (已開啟)，以保護使用者免於遭受潛在的網路釣魚詐騙和惡意軟體攻擊。 此外，根據預設，使用者無法停用 (關閉) Microsoft Defender SmartScreen。 啟用此原則時，會關閉 Microsoft Defender SmartScreen，並防止使用者開啟它。 不設定此原則可讓使用者選擇開啟或關閉 Microsoft Defender SmartScreen。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067029)

  **預設值**：是

- **封鎖惡意網站存取**：  
  根據預設，Microsoft Edge 可讓使用者略過 (忽略) 有關潛在惡意網站的 Microsoft Defender SmartScreen 警告，讓他們可以繼續前往該網站。 但是透過此原則，您可以設定 Microsoft Edge 來防止使用者略過警告，讓他們無法繼續前往該網站。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067040)
  
  **預設值**：是
  
- **封鎖未經驗證的檔案下載**：  
  根據預設，Microsoft Edge 可讓使用者略過 (忽略) 有關潛在惡意檔案的 Microsoft Defender SmartScreen 警告，讓他們可以繼續下載未經驗證的檔案。 啟用此原則可防止使用者略過警告，讓他們無法下載未經驗證的檔案。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067023)
  
  **預設值**：是
  
- **封鎖密碼管理員**：  
  根據預設，Microsoft Edge 會自動使用密碼管理員，讓使用者能夠在本機管理密碼。 停用此原則會限制 Microsoft Edge，使其無法使用密碼管理員。 如果您想要讓使用者選擇使用密碼管理員在本機儲存並管理密碼，就不要設定此原則。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067128)
  
  **預設值**：是
  
- **防止憑證錯誤覆寫**：  
  此原則設定可防止使用者忽略 Internet Explorer 中會中斷瀏覽的安全通訊端層/傳輸層安全性 (SSL/TLS) 憑證錯誤 (例如「已過期」、「已撤銷」或「名稱不符」錯誤)。 如果您啟用此原則設定，使用者將無法繼續瀏覽。 如果您停用或未設定此原則設定，則使用者可以選擇忽略憑證錯誤並繼續瀏覽。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067126)
  
  **預設值**：是

## <a name="connectivity"></a>連線能力

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - Connectivity](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) (原則 CSP - 連線性)。

- **封鎖 Web 發佈和線上訂購精靈的網際網路下載**：  
  此原則設定可指定 Windows 是否應該為 Web 發佈和線上訂購精靈下載提供者清單。 這些精靈可讓使用者從提供線上儲存空間和相片列印等服務的公司清單中進行選取。 根據預設，除了登錄中指定的提供者之外，Windows 也會顯示從 Windows 網站下載的提供者。 如果您啟用此原則設定，Windows 不會下載提供者，且只會顯示本機登錄中快取的服務提供者。 如果您停用或未設定此原則設定，當使用者使用 Web 發佈或線上訂購精靈時，就會下載提供者清單。 如需詳細資訊 (包括在登錄中指定服務提供者的詳細資料)，請參閱 Web 發佈和線上訂購精靈的文件。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067136)
  
  **預設**：啟用

::: zone-end
::: zone pivot="mdm-may-2019"

- **設定對 UNC 路徑的安全存取**：  
  此原則設定會設定 UNC 路徑的安全存取。 如果您啟用此原則，只有在完成額外的安全性需求之後，Windows 才允許存取指定的 UNC 路徑。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067243)

  **預設值**：在完成額外的安全性需求之後，將 Windows 設定為只允許存取指定的 UNC 路徑。

  當您選取 [在*完成額外的安全性需求後，將 Windows 設定為只允許存取指定的 unc 路徑*] 時，您可以設定 [*強化的 unc 路徑] 清單*。

  - **強化的 UNC 路徑清單**：  
    選取 [**新增**] 以指定其他安全性旗標和伺服器路徑。

::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

- **封鎖透過 HTTP 的列印驅動程式下載**：  
  此原則設定指定是否允許此用戶端透過 HTTP 下載列印驅動程式套件。 若要設定 HTTP 列印，您必須透過 HTTP 下載非內建驅動程式。 注意：此原則設定不會防止用戶端透過 HTTP 列印到內部網路或網際網路上的印表機。 它只會禁止下載尚未安裝在本機的驅動程式。 如果您啟用此原則設定，就無法透過 HTTP 下載列印驅動程式。 如果您停用或未設定此原則設定，則使用者可以透過 HTTP 下載列印驅動程式。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067141)
  
  **預設**：啟用

## <a name="credentials-delegation"></a>認證委派

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - CredentialsDelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation) (原則 CSP - CredentialsDelegation)。

- **不可匯出認證的遠端主機委派**：  
  遠端主機允許委派不可匯出認證。 使用認證委派時，裝置會提供可匯出的認證版本給遠端主機，這會造成使用者可能會面臨來自遠端主機攻擊者的認證竊取風險。 如果您啟用此原則設定，主機會支援「受限的系統管理」或「遠端 Credential Guard」模式。 如果您停用或未設定此原則設定，則不支援「受限的系統管理」和「遠端 Credential Guard」模式。 使用者一律必須將他們的認證傳遞給主應用程式。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067103)
  
  **預設**：啟用

## <a name="credentials-ui"></a>認證 UI

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui) (原則 CSP - CredentialsUI)。

- **列舉系統管理員**：  
  此原則設定可控制當使用者嘗試提高執行中應用程式的權限時，是否會顯示系統管理員帳戶。 根據預設，當使用者嘗試提高執行中應用程式的權限時，不會顯示系統管理員帳戶。 如果您啟用此原則設定，即會顯示電腦上的所有本機系統管理員帳戶，讓使用者可以選擇其中一個並輸入正確的密碼。 如果您停用此原則設定，使用者一律必須鍵入使用者名稱和密碼來提高權限。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067021)

  **預設**：停用

## <a name="data-protection"></a>資料保護

如需詳細資訊，請參閱 Windows 文件中的 [olicy CSP - DataProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection) (原則 CSP - DataProtection)。

- **封鎖直接記憶體存取**：  
  此原則設定可讓您封鎖對所有隨插即用 PCI 下游連接埠的直接記憶體存取 (DMA)，直到使用者登入 Windows 為止。 使用者登入後，Windows 就會列舉連接至隨插即用 PCI 連接埠的 PCI 裝置。 只要使用者鎖定電腦，在使用者再次登入之前，將會在沒有子裝置的隨插即用 PCI 連接埠上封鎖 DMA。 電腦解除鎖定時已列舉的裝置將繼續運作，直到遭拔除為止。 只有在啟用 BitLocker 或裝置加密時，才會強制執行此原則設定。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067031)

  **預設值**：是

## <a name="device-guard"></a>Device Guard

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - DeviceGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard) (原則 CSP - DeviceGuard)。

- **Credential Guard**：  
  此設定可讓使用者使用虛擬化安全性開啟 Credential Guard，以協助在下次重新開機期間保護認證。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067044)

  **預設值**：連同 UEFI 鎖定一起啟用

::: zone-end
::: zone pivot="mdm-may-2019"

- **以虛擬化為基礎的安全性**：  
  **預設值**：使用安全開機來啟用 VBS

::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

- **啟用以虛擬化為基礎的安全性**：  
  在下次重新開機期間開啟虛擬化安全性 (VBS)。 虛擬化型安全性會使用 Windows Hypervisor 來提供安全性服務的支援。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067066)
  
  **預設值**：是

- **啟動系統防護**：  
  **預設**：啟用

## <a name="device-installation"></a>裝置安裝

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - DeviceInstallation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation) (原則 CSP - DeviceInstallation)。

- **依裝置識別碼的硬體裝置安裝**：  
  此原則設定可讓您針對 Windows 防止安裝的裝置，指定隨插即用硬體識別碼與相容識別碼的清單。 此原則設定優先於任何其他允許 Windows 安裝裝置的原則設定。 如果您啟用此原則設定，Windows 會無法安裝其硬體識別碼或相容識別碼出現在您所建立清單中的裝置。 如果您在遠端桌面伺服器上啟用此原則設定，此原則設定會影響指定裝置從遠端桌面用戶端到遠端桌面伺服器的重新導向。 如果您停用或未設定此原則設定，裝置可以按照其他原則設定的允許或防止來進行安裝及更新。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2066794)

  **預設**：封鎖硬體裝置安裝

  選取 [封鎖硬體裝置安裝]  時，有下列設定可用。

  - **移除相符的硬體裝置**：  
    只有在 [依裝置識別碼的硬體裝置安裝]  設定為 [封鎖硬體裝置安裝]  時，才能使用此設定。

    **預設值**：是

  - **已封鎖的硬體裝置識別碼**：  
    只有在 [依裝置識別碼的硬體裝置安裝]  設定為 [封鎖硬體裝置安裝]  時，才能使用此設定。

    **預設值**：是

- **依安裝類別的硬體裝置安裝**：  
  此原則設定可讓您針對 Windows 防止安裝的裝置驅動程式，指定裝置安裝類別全域唯一識別碼 (GUID) 的清單。 此原則設定優先於任何其他允許 Windows 安裝裝置的原則設定。 如果您啟用此原則設定，Windows 會無法安裝或更新其裝置安裝類別 GUID 出現在您所建立清單中的裝置驅動程式。 如果您在遠端桌面伺服器上啟用此原則設定，此原則設定會影響指定裝置從遠端桌面用戶端到遠端桌面伺服器的重新導向。 如果您停用或未設定此原則設定，Windows 可以按照其他原則設定的允許或防止來安裝及更新裝置。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067048)

  **預設**：封鎖硬體裝置安裝

  選取 [封鎖硬體裝置安裝]  時，有下列設定可用。

  - **移除相符的硬體裝置**：  
    只有在 [Hardware device installation by setup classes]  \(依安裝類別安裝硬體裝置\) 設定為 [Block hardware device installation]  \(封鎖硬體裝置安裝\) 時，才能使用此設定。

    **預設**：沒有任何預設設定 

  - **已封鎖的硬體裝置識別碼**：  
    只有在 [Hardware device installation by setup classes]  \(依安裝類別安裝硬體裝置\) 設定為 [Block hardware device installation]  \(封鎖硬體裝置安裝\) 時，才能使用此設定。

    **預設**：沒有任何預設設定 

## <a name="device-lock"></a>裝置鎖定

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) (原則 CSP - DeviceLock)。

- **防止使用相機**：  
  在 [電腦設定] 中停用鎖定畫面相機切換開關，來防止在鎖定畫面上叫用相機。 根據預設，使用者可在鎖定畫面上，啟用可用相機的引動過程。 如果您啟用此設定，使用者就無法繼續在 [電腦設定] 中，啟用或停用鎖定畫面相機存取，且無法於鎖定畫面上叫用相機。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067052)

  **預設**：啟用

- **需要密碼**：  
  指定是否已啟用裝置鎖定。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067049)  

  **預設值**：是
  
  當 [需要密碼]  設定為 [是]  時，有下列設定可用。

  - **密碼字元集計數下限**：  
    強式 PIN 或密碼所需的複雜元素類型 (大寫和小寫字母、數字和標點符號) 數目。 PIN 會為電腦與行動裝置強制套用下列行為：1 - 僅限數字 2 - 數字及小寫字母為必要項 3 - 數字、小寫字母及大寫字母為必要項。 在電腦 Microsoft 帳戶及網域帳戶中不受支援。 4 - 數字、小寫字母、大寫字母及特殊字元為必要項。 在電腦中不受支援。 預設值為 1。  
    [深入了解](https://go.microsoft.com/fwlink/?linkid=2067055)

    **預設**：3

  - **登入失敗幾次後即抹除裝置**：  
    抹除裝置之前，允許的驗證失敗數目。 值為 0 就會停用裝置抹除功能。  
    [深入了解](https://go.microsoft.com/fwlink/?linkid=2067030)

    **預設**：10  

  - **密碼到期 (天數)** ：  
    密碼最長使用期限原則設定，可決定系統要求使用者變更密碼前，可以使用該密碼多久 (天)。 您可將密碼到期的天數設為 1 到 999 之間，或可將天數設定為 0 來指定密碼無使用期限。 若密碼最長使用期限介於 1 到 999 天之間，則密碼最短使用期限必須小於密碼最長使用期限。 若密碼最長使用期限設為 0，則密碼最長使用期限可為 0 到 998 天之間的任意值。  
    [深入了解](https://go.microsoft.com/fwlink/?linkid=2067028)

    **預設**：60

  - **必要的密碼類型**：  
    決定必要的 PIN 或密碼類型。  
    [深入了解](https://go.microsoft.com/fwlink/?linkid=2067027)

    **預設值** ：英數字元

  - **密碼長度下限**：  
    密碼最短長度原則設定，可決定使用者帳戶密碼的最少字元數目。 您可設定 1 到 14 個字元之間的值，或可透過將字元數目設為 0 來設定無需密碼。  
    [深入了解](https://go.microsoft.com/fwlink/?linkid=2067024)

    **預設**：8

  - **封鎖簡單密碼**：  
    指定是否允許 "1111" 或 "1234" 這類 PIN 及密碼。 若為電腦，這也會控制圖片密碼的使用方式。  
    [深入了解](https://go.microsoft.com/fwlink/?linkid=2067127)

    **預設值**：是  
    *設為 [是]，可防止使用簡單密碼。*

  - **避免重複使用以前用過的密碼**：  
    指定可以將多少密碼儲存於無法使用的記錄中。 值會包含使用者的目前密碼。 例如，設定為 *1* 時，使用者在選擇新密碼時無法重複使用其目前的密碼。 設定為 *5* 表示使用者無法將其新密碼設定為其目前的密碼或先前使用過的四個密碼。  
    [深入了解](https://go.microsoft.com/fwlink/?linkid=2066795)

    **預設**：24

- **防止投影片放映**：  
  在 [電腦設定] 中停用鎖定畫面投影片放映設定，來避免在鎖定畫面上放映投影片。 根據預設，使用者可啟用在鎖定機器後執行投影片放映。 若您啟用此設定，使用者就無法在 [電腦設定] 中修改投影片放映設定，且不會啟動任何投影片放映。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067105)

  **預設**：啟用  

  [已啟用] 設定可防止執行投影片放映。 

- **密碼最短使用期限 (天)** ：  
  密碼最短使用期限原則設定，可決定使用者可變更密碼前，必須使用密碼多久的時間 (天)。 您可設定 1 到 998 天之間的值，或透過將 天數設為 0 來立即允許密碼變更。 密碼最短使用期限必須小於密碼最長使用期限，除非密碼最長使用期限設為 0，表示密碼無使用期限。 若密碼最長使用期限設為 0，則密碼最短使用期限可設為 0 到 998 之間的任意值。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067022)

  **預設**：1

::: zone-end
::: zone pivot="mdm-may-2019"

## <a name="dma-guard"></a>DMA 防護

如需詳細資訊，請參閱 Windows 文件中的 [原則 CSP - DmaGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard) \(英文\)。

- **列舉與 Kernel DMA Protection 不相容的外部裝置**：  
  此原則的目的是要針對具備外部 DMA 功能的裝置提供額外的安全性。 它可讓您更有效地控制與 DMA 重新對應/裝置記憶體隔離和沙箱處理不相容之外部 DMA 裝置的列舉。 只有當支援 Kernel DMA Protection 並由系統韌體啟用它時，此原則才會生效。 核心 DMA 保護是無法透過原則或使用者控制的平臺功能。 系統製造時即必須支援此功能。 若要檢查系統是否支援核心 DMA 保護，請檢查 appcmd.exe [摘要] 頁面中的 [核心 DMA 保護] 欄位。  
  [深入了解](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard#dmaguard-deviceenumerationpolicy)

  **預設值**：全部封鎖

::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

## <a name="event-log-service"></a>事件記錄服務

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - EventLogService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice) (原則 CSP - EventLogService)。

- **安全性記錄檔案大小上限 (KB)** ：  
  此原則設定可指定記錄檔的大小上限 (KB)。 若您啟用此原則設定，即可將記錄檔大小上限設為 1 MB (1024 KB) 到 2 TB (2147483647 KB) 之間，以 KB 遞增。 如果您停用或未進行此原則設定，則記錄檔大小上限會設為本機設定的值。 本機系統管理員可使用 [記錄內容] 對話方塊來變更此值，且此值預設為 20 MB。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067042)

   **預設**：196608

- **系統記錄檔案大小上限 (KB)** ：  
  此原則設定可指定記錄檔的大小上限 (KB)。 若您啟用此原則設定，即可將記錄檔大小上限設為 1 MB (1024 KB) 到 2 TB (2147483647 KB) 之間，以 KB 遞增。 如果您停用或未進行此原則設定，則記錄檔大小上限會設為本機設定的值。 本機系統管理員可使用 [記錄內容] 對話方塊來變更此值，且此值預設為 20 MB。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2066798)

  **預設**：32768

- **應用程式記錄檔案大小上限 (KB)** ：  
  此原則設定可指定記錄檔的大小上限 (KB)。 若您啟用此原則設定，即可將記錄檔大小上限設為 1 MB (1024 KB) 到 2 TB (2147483647 KB) 之間，以 KB 遞增。 如果您停用或未進行此原則設定，則記錄檔大小上限會設為本機設定的值。 本機系統管理員可使用 [記錄內容] 對話方塊來變更此值，且此值預設為 20 MB。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067125)

  **預設**：32768

## <a name="experience"></a>體驗

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - Experience](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) (原則 CSP - 體驗)。

- **封鎖 Windows 焦點**：  
  讓 IT 系統管理員得以關閉所有的 Windows 焦點功能 - 鎖定畫面、Windows 提示、Microsoft 消費者功能，以及其他相關功能。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067037)

  **預設值**：是

  當 [封鎖 Windows 焦點]  設定為 [是]  時，有下列設定可用。

  - **封鎖 Windows 焦點中的協力廠商建議**：  
    指定是否允許來自 Windows 焦點功能 (例如鎖定畫面焦點、[開始] 功能表中建議的應用程式，及 Windows 提示) 中協力廠商軟體提供者的應用程式及內容建議。 使用者仍能夠看到 Microsoft 功能、應用程式及服務的建議。  
    [深入了解](https://go.microsoft.com/fwlink/?linkid=2067045)

    **預設值**：是

  - **封鎖消費者特定功能**：  
    讓 IT 系統管理員得以開啟通常僅供消費者使用的體驗，例如開始建議、成員資格通知、OOBE 後的應用程式安裝及重新導向磚。  
    [深入了解](https://go.microsoft.com/fwlink/?linkid=2067054)

    **預設值**：是

## <a name="exploit-guard"></a>惡意探索防護

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard) (原則 CSP - ExploitGuard)。

- **惡意探索保護 XML**：  
  讓 IT 系統管理員得以將代表想要的系統及應用程式風險降低選項設定，推送至組織中的所有裝置。 此設定是以 XML 表示。 惡意探索保護可協助保護裝置，以防惡意程式碼利用惡意探索散播和感染。 您可以使用 Windows 安全性應用程式或 PowerShell 建立風險降低集合 (稱為設定)。 然後，您可以將此設定匯出為 XML 檔案，並在您網路上的多部電腦之間共用，以便所有檔案都有相同的風險降低設定集合。 您也可以將現有的 EMET 設定 XML 檔案轉換並匯入到惡意探索保護設定 XML。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067035)

  **預設值**：*提供範例 xml*

## <a name="file-explorer"></a>檔案總管

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - FileExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer) (原則 CSP - FileExplorer)。  

- **封鎖資料執行防止**：  
  停用資料執行防止可允許特定舊版外掛程式應用程式運作，而不需要終止檔案總管。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067043)  

  **預設**：停用

- **封鎖損毀時終止堆積**：  
  停用損毀時終止堆積可讓特定舊版外掛應用程式不需要終止檔案總管即可立即運作，但檔案總管稍後可能仍會未預期地終止。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067107)

  **預設**：停用

## <a name="internet-explorer"></a>Internet Explorer

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer) (原則 CSP - InternetExplorer)。

- **Internet Explorer 受限區域透過指令碼更新狀態列**：  
  此原則設定可讓您管理是否允許指令碼更新區域內的狀態列。

  - 如果您啟用此原則設定  ，即允許指令碼更新狀態列。
  - 如果您停用或未設定此原則設定  ，則不允許指令碼更新狀態列。

  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067074)

  **預設**：停用

::: zone-end
::: zone pivot="mdm-may-2019"

- **Internet Explorer 網際網路區域拖放或複製並貼上檔案**：  
  此原則設定可讓您管理使用者是否可以從區域的來源中拖曳檔案或複製並貼上檔案。 如果您啟用此原則設定，使用者可以從此區域自動拖曳檔案或複製並貼上檔案。 如果您在下拉式方塊中選取 [提示]，則會請使用者選擇是要從此區域拖曳還是複製檔案。 如果您停用此原則設定，使用者將無法從此區域拖曳檔案或複製並貼上檔案。 如果您未設定此原則設定，使用者可以從此區域自動拖曳檔案或複製並貼上檔案。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067076)

  **預設值**：停用

- **Internet Explorer 受限區域 .NET Framework 相依元件**：  
  使用此原則設定管理是否可以從 Internet Explorer 執行使用 Authenticode 簽署的 .NET Framework 元件。 這些元件包含從物件標記參考的受控控制項，以及從連結參考的受控可執行檔。 如果您啟用此原則設定，Internet Explorer 將會執行未簽署的受控元件。 如果您在下拉式方塊中選取 [提示]，Internet Explorer 將會提示使用者決定是否要執行未簽署的受控元件。 如果您停用此原則設定，Internet Explorer 將不會執行未簽署的受控元件。 如果您未設定此原則設定，Internet Explorer 將會執行未簽署的受控元件。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067077)

  **預設值**：停用

- **Internet Explorer 本機電腦區域不會對 ActiveX 控制項執行反惡意程式碼軟體**：  
  此原則設定可決定 Internet Explorer 是否會對 ActiveX 控制項執行反惡意程式碼程式，來檢查這些控制項是否可安全載入到頁面。 如果您啟用此原則設定，Internet Explorer 將不會使用您的反惡意程式碼程式，來檢查是否可以安全建立 ActiveX 控制項的執行個體。 如果您停用此原則設定，Internet Explorer 一律會使用您的反惡意程式碼程式，來檢查是否可以安全建立 ActiveX 控制項的執行個體。 如果您未設定此原則設定，Internet Explorer 將不會使用您的反惡意程式碼程式，來檢查是否可以安全建立 ActiveX 控制項的執行個體。 使用者可以透過 Internet Explorer [安全性] 設定來開啟或關閉此行為。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067152)

  **預設**：停用

::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

- **在 Internet Explorer 網際網路區域中存取資料來源**：  
  此原則設定可讓您管理 Internet Explorer 是否可以從使用 Microsoft XML 剖析器 (MSXML) 或 ActiveX Data Objects (ADO) 的其他安全性區域存取資料。 如果您啟用此原則設定，使用者就可以將網頁載入使用 MSXML 或 ADO 的區域來存取該區域中其他網站的資料。 如果您在下拉式方塊中選取 [提示]，則會請使用者選擇是否允許將網頁載入至使用 MSXML 或 ADO 的區域來存取該區域中其他網站資料。 如果您停用此原則設定，使用者就無法將網頁載入使用 MSXML 或 ADO 的區域來存取該區域中其他網站資料。 如果您未設定此原則設定，使用者就無法將網頁載入使用 MSXML 或 ADO 的區域來存取該區域中其他網站資料。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067078)  

  **預設值**：停用

- **在 Internet Explorer 限制區域中從視窗內的不同網域拖曳內容**：  
  此原則設定可讓您設定當來源與目的地位於相同視窗時，將內容從一個網域拖曳至另一個網域的選項。 如果您啟用此原則設定並按一下 [啟用]，當來源與目的地位於相同視窗時，使用者就可以將內容從一個網域拖曳至另一個網域。 使用者無法變更此設定。 如果您啟用此原則設定並按一下 [停用]，當來源與目的地位於相同視窗時，使用者就無法將內容從一個網域拖曳至另一個網域。 使用者無法在 [網際網路選項] 對話方塊中變更此設定。 在 Internet Explorer 10 中，如果您停用或未設定此原則設定，當來源與目的地位於相同視窗時，使用者就無法將內容從一個網域拖曳至另一個網域。 使用者可以在 [網際網路選項] 對話方塊中變更此設定。 在 Internet Explorer 9 和舊版中，如果您停用或未設定此原則設定，當來源與目的地位於相同視窗時，使用者就可將內容從一個網域拖曳至另一個網域。 使用者無法在 [網際網路選項] 對話方塊中變更此設定。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067079)  

  **預設**：停用

- **Internet Explorer 憑證位址不符警告**：  
  此原則設定可讓您開啟憑證位址不符安全性警告。 如果開啟此原則設定，當使用者瀏覽的安全 HTTP (HTTPS) 網站呈現針對其他網址核發的憑證時，使用者會收到警告。 此警告可協助防止詐騙攻擊。 如果您啟用此原則設定，則一律會顯示憑證位址不符警告。 如果您停用或未設定此原則設定，則使用者可以選擇是否顯示憑證位址不符警告 (藉由使用 [網際網路控制台] 中的 [進階] 畫面)。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067153)  

  **預設**：啟用

- **Internet Explorer 限制區域較少特殊權限的網站**：  
  此原則設定可讓您管理較少特殊權限區域中的網站 (例如網際網路網站) 是否可以巡覽至此區域。 如果您啟用此原則設定，較少特殊權限區域中的網站可以在此區域中開啟新視窗，或巡覽至此區域。 安全性區域會在不具備 [來自區域高度的保護] 安全性功能所提供額外安全性階層的狀況下執行。 如果您在下拉式方塊中選取 [提示]，則會對使用者發出警告，指出即將發生可能具風險的瀏覽。 如果您停用此原則設定，則會禁止可能有害的瀏覽。 Internet Explorer 安全性功能會在此區域中開啟，如 [來自區域高度的保護] 功能控制所設定。 如果您未設定此原則設定，則會禁止可能有害的瀏覽。 Internet Explorer 安全性功能會在此區域中開啟，如 [來自區域高度的保護] 功能控制所設定。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067148)

  **預設值**：停用

- **Internet Explorer 限制區域自動提示檔案下載**：  
  此原則設定可決定是否要在出現非使用者起始的檔案下載時提示使用者。 無論此設定為何，針對使用者起始的下載，使用者將會收到檔案下載對話方塊。 如果您啟用此設定，針對自動下載嘗試，使用者將會收到檔案下載對話方塊。 如果您停用或未設定此設定，非使用者起始的檔案下載會遭到封鎖，且使用者會看到通知列而非檔案下載對話方塊。 使用者可以接著按一下通知列來允許檔案下載提示。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067150)

  **預設**：停用

- **Internet Explorer 網際網路區域 .NET Framework 相依元件**：  
  此原則設定可讓您管理是否可以從 Internet Explorer 執行使用 Authenticode 簽署的 .NET Framework 元件。 這些元件包含從物件標記參考的受控控制項，以及從連結參考的受控可執行檔。 如果您啟用此原則設定，Internet Explorer 將會執行未簽署的受控元件。 如果您在下拉式方塊中選取 [提示]，Internet Explorer 將會提示使用者決定是否要執行未簽署的受控元件。 如果您停用此原則設定，Internet Explorer 將不會執行未簽署的受控元件。 如果您未設定此原則設定，Internet Explorer 將會執行未簽署的受控元件。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067073)

  **預設值**：停用

- **Internet Explorer 網際網路區域只允許核准的網域使用 TDC ActiveX 控制項**：  
  此原則設定可控制使用者是否可以執行網站上的 TDC ActiveX 控制項。 如果您啟用此原則設定，則不會執行來自此區域網站的 TDC ActiveX 控制項。 如果您停用此原則設定，則會執行來自此區域所有網站的 TDC ActiveX 控制項。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067151)

  **預設**：啟用

- **Internet Explorer 限制區域以指令碼起始的視窗**：  
  此原則設定可讓您管理以指令碼起始的快顯視窗限制，以及包含標題和狀態列的視窗限制。 如果您啟用此原則設定，Windows 限制安全性將不會套用至此區域。 安全性區域會在不具備此功能所提供額外安全性階層的狀況下執行。 如果您停用此原則設定，將不可執行以指令碼起始的快顯視窗，以及包含標題和狀態列的視窗中所包含可能有害動作。 Internet Explorer 安全性功能會在此區域中開啟，如處理序的 [已撰寫指令碼的 Windows 安全性限制] 功能控制設定所指定。 如果您未設定此原則設定，將不可執行以指令碼起始的快顯視窗，以及包含標題和狀態列的視窗中所包含可能有害動作。 Internet Explorer 安全性功能會在此區域中開啟，如處理序的 [已撰寫指令碼的 Windows 安全性限制] 功能控制設定所指定。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067075)

  **預設**：停用

- **Internet Explorer 網際網路區域在上傳檔案至伺服器時包含本機路徑**：  
  此原則設定可控制使用者透過 HTML 表單上傳檔案時是否傳送本機路徑資訊。 如果傳送本機路徑資訊，可能會不小心對伺服器揭露某些資訊。 例如，從使用者桌面傳送之檔案可能包含使用者名稱作為路徑的一部分。 如果您啟用此原則設定，使用者透過 HTML 表單上傳檔案時會傳送路徑資訊。 如果您停用此原則設定，使用者透過 HTML 表單上傳檔案時就會移除路徑資訊。 如果您未設定此原則設定，則使用者可以在透過 HTML 表單上傳檔案時選擇是否傳送路徑資訊。 預設會傳送路徑資訊。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067072)

  **預設**：停用

- **Internet Explorer 在加強的受保護模式中停用處理序**：  
  此原則設定可決定 Internet Explorer 11 在 64 位元版本 Windows 上以加強的受保護模式執行時，使用的是 64 位元處程序 (安全性更高) 或 32 位元處理序 (相容性更高)。 重要：使用 64 位元處理序時，可能無法使用某些 ActiveX 控制項和工具列。 如果您啟用此原則設定，在 64 位元版本的 Windows 上執行加強的受保護模式時，Internet Explorer 11 將使用 64 位元索引標籤處理序。 如果您停用此原則設定，在 64 位元版本的 Windows 上執行加強的受保護模式時，Internet Explorer 11 將使用 32 位元索引標籤處理序。 如果您未設定此原則設定，使用者可以透過 Internet Explorer 設定來開啟或關閉此功能。 此功能預設為關閉。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067149)

  **預設**：啟用

- **Internet Explorer 忽略憑證錯誤**：  
  此原則設定可防止使用者忽略 Internet Explorer 中會中斷瀏覽的安全通訊端層/傳輸層安全性 (SSL/TLS) 憑證錯誤 (例如「已過期」、「已撤銷」或「名稱不符」錯誤)。 如果您啟用此原則設定，使用者將無法繼續瀏覽。 如果您停用或未設定此原則設定，則使用者可以忽略憑證錯誤並繼續瀏覽。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067071)

  **預設**：停用

- **在 Internet Explorer 網際網路區域中載入 XAML 檔案**：  
  此原則設定可讓您管理 Extensible Application Markup Language (XAML) 檔案的載入。 XAML 是以 XML 為基礎的宣告式標記語言，常用來建立利用 Windows Presentation Foundation 的豐富使用者介面和圖形。 如果您啟用此原則設定並將下拉式方塊設定為 [啟用]，則會在 Internet Explorer 內自動載入 XAML 檔案。 使用者無法變更此行為。 如果您將下拉式方塊設定為 [提示]，則會提示使用者載入 XAML 檔案。 如果您停用此原則設定，則不會在 Internet Explorer 內載入 XAML 檔案。 使用者無法變更此行為。 如果您未設定此原則設定，則使用者可以決定是否要在 Internet Explorer 內載入 XAML 檔案。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067147)

  **預設值**：停用

::: zone-end
::: zone pivot="mdm-may-2019"

- **Internet Explorer 網際網路區域自動提示檔案下載**：  
  此原則設定可決定是否要在出現非使用者起始的檔案下載時提示使用者。 無論此設定為何，針對使用者起始的下載，使用者將會收到檔案下載對話方塊。 如果您啟用此設定，針對自動下載嘗試，使用者將會收到檔案下載對話方塊。 如果您停用或未設定此設定，非使用者起始的檔案下載會遭到封鎖，且使用者會看到通知列而非檔案下載對話方塊。 使用者可以接著按一下通知列來允許檔案下載提示。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067117)

  **預設**：停用

::: zone-end
::: zone pivot="mdm-preview"

- **Internet Explorer 網際網路區域自動提示檔案下載**：  
  此原則設定可決定是否要在出現非使用者起始的檔案下載時提示使用者。 無論此設定為何，針對使用者起始的下載，使用者將會收到檔案下載對話方塊。 如果您啟用此設定，針對自動下載嘗試，使用者將會收到檔案下載對話方塊。 如果您停用或未設定此設定，非使用者起始的檔案下載會遭到封鎖，且使用者會看到通知列而非檔案下載對話方塊。 使用者可以接著按一下通知列來允許檔案下載提示。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067117)

  **預設**：啟用

::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

- **Internet Explorer 限制區域潛在不安全檔案的安全性警告**：  
  此原則設定可控制當使用者嘗試開啟可執行檔或其他潛在不安全的檔案時 (例如使用檔案總管從內部網路檔案共用開啟)，是否顯示「開啟檔案 - 安全性警告」訊息。 如果您啟用此原則設定並將下拉式方塊設定為 [啟用]，開啟這些檔案時不會有安全性警告。 如果您將下拉式方塊設定為 [提示]，開啟檔案之前會先顯示安全性警告。 如果您停用此原則設定，則不會開啟這些檔案。 如果您未設定此原則設定，則使用者可以設定電腦處理這些檔案的方式。 根據預設，這些檔案在限制區域中會被封鎖、在內部網路和本機電腦區域中會啟用，而在網際網路和受信任區域中會設定為 [提示]。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2066797)

  **預設值**：停用

- **Internet Explorer 網際網路區域跨網站指令碼篩選器**：  
  此原則可控制跨網站指令碼 (XSS) 篩選器是否會偵測並防止此區域網站中的跨網站指令碼插入。 如果您啟用此原則設定，則會開啟此區域網站的 XSS 篩選器，且 XSS 篩選器會嘗試封鎖跨網站指令碼插入。 如果您停用此原則設定，則會關閉此區域網站的 XSS 篩選器，且 Internet Explorer 會允許跨網站指令碼插入。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067053)

  **預設**：啟用

- **Internet Explorer 使用 SSL3 來遞補**：  
  此原則設定可讓您封鎖以不安全的方式使用 SSL 3.0 來遞補。 如果啟用此原則，Internet Explorer 將會在 TLS 1.0 (含) 以上版本失敗時，嘗試使用 SSL 3.0 (含) 以下版本連線到網站。 若要防止中間人攻擊，建議您不要允許不安全的遞補。 此原則不會影響要啟用哪些安全性通訊協定。 如果您停用此原則，則會使用系統預設值。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067118)

  **預設值**：沒有網站

::: zone-end
::: zone pivot="mdm-may-2019"

- **Internet Explorer 加密支援**：  
  此原則設定可讓您在瀏覽器中關閉傳輸層安全性（TLS）1.0、TLS 1.1、TLS 1.2、安全通訊端層（SSL）2.0 或 SSL 3.0 的支援。 TLS 和 SSL 是協助保護瀏覽器與目標伺服器之間通訊的通訊協定。 當瀏覽器嘗試設定與目標伺服器的受保護通訊時，瀏覽器和伺服器會協商所要使用的通訊協定和版本。 瀏覽器和伺服器嘗試比對彼此支援的通訊協定和版本清單，並選取最慣用的相符項。 如果您啟用此原則設定，瀏覽器就會使用您從下拉式清單中選取的加密方法，來協商或不協調加密通道。 如果您停用或未設定此原則設定，使用者可以選取瀏覽器支援的加密方法。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067057)

  **預設值**：2個專案： TLS V1.1 和 tls v 1。2  
  *選取向下箭號，以顯示您可以為此設定選取的選項。*

::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

- **Internet Explorer 鎖定的網際網路區域 SmartScreen**：  
  此原則設定可控制 SmartScreen 篩選工具是否要掃描此區域中的網頁有無惡意內容。 如果您啟用此原則設定，SmartScreen 篩選工具將會掃描此區域中的網頁有無惡意內容。 如果您停用此原則設定，SmartScreen 篩選工具將不會掃描此區域中的網頁有無惡意內容。 如果您未設定此原則設定，則使用者可以選擇 SmartScreen 篩選工具是否要掃描此區域中的網頁有無惡意內容。 注意：在 Internet Explorer 7 中，此原則設定可控制網路釣魚篩選工具是否要掃描此區域中的網頁有無惡意內容。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067059)

  **預設**：啟用

- **在 Internet Explorer 限制區域中從 iFrame 啟動應用程式和檔案**：  
  此原則設定可讓您管理是否可以從此區域網頁 HTML 中的 IFRAME 參考執行應用程式及下載檔案。 如果您啟用此原則設定，無需使用者操作，即可從此區域網頁上的 IFRAME 執行應用程式及下載檔案。 如果您在下拉式方塊中選取 [提示]，則會請使用者選擇是否要從此區域網頁上的 IFRAME 執行應用程式及下載檔案。 如果您停用此原則設定，使用者將無法從這個區域的頁面上的 Iframe 執行應用程式及下載檔案。 如果您未設定此原則設定，則使用者無法從此區域網頁上的 IFRAME 執行應用程式及下載檔案。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067061)

  **預設值**：停用

- **Internet Explorer 略過有關非常見檔案的 SmartScreen 警告**：  
  此原則設定可決定使用者是否可以略過 SmartScreen 篩選工具的警告。 對於不是 Internet Explorer 使用者經常從網際網路下載的可執行檔，SmartScreen 篩選工具會向使用者發出警告。 如果您啟用此原則設定，SmartScreen 篩選工具警告將會封鎖使用者。 如果您停用或未設定此原則設定，使用者即可略過 SmartScreen 篩選工具警告。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067068)

  **預設**：停用

- **Internet Explorer 網際網路區域快顯封鎖程式**：  
  此原則設定可讓您管理是否要顯示不需要的快顯視窗。 這不會封鎖終端使用者按一下連結時所開啟的快顯視窗。 如果您啟用此原則設定，即可防止顯示大部分不需要的快顯視窗。 如果您停用此原則設定，則無法防止顯示快顯視窗。 如果您未設定此原則設定，即可防止顯示大部分不需要的快顯視窗。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067069)

  **預設值**：啟用

- **Internet Explorer 處理序一致的 MIME 處理**：  
  Internet Explorer 包含動態二進位行為：用來封裝 HTML 元素所附加特定功能的元件。 此原則設定可控制要禁止或允許 [二進位行為安全性限制] 設定。 如果您啟用此原則設定，則會禁止檔案總管和 Internet Explorer 處理序的二進位行為。 如果您停用此原則設定，則會允許檔案總管和 Internet Explorer 處理序的二進位行為。 如果您未設定此原則設定，則會禁止檔案總管和 Internet Explorer 處理序的二進位行為。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067144)  

  **預設**：啟用

- **Internet Explorer 受限制區域 Java 權限**：  
  此原則設定可讓您管理 Java Applet 的權限。 如果您啟用此原則設定，即可從下拉式方塊中選擇選項。 [自訂] 可個別控制權限設定。 [低安全性] 可讓 Applet 執行所有作業。 [中安全性] 可讓 Applet 在其沙箱 (記憶體中無法供外部應用程式呼叫的一個區域) 中執行，以及啟用暫存空間 (用戶端電腦上安全且受保護的存放區域) 和使用者控制的檔案 I/O 等功能。 [高安全性] 可讓 Applet 在其沙箱中執行。 停用 Java 可防止執行任何 Applet。 如果您停用此原則設定，則無法執行 Java Applet。 如果您未設定此原則設定，則會停用 Java Applet。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067132)

  **預設值**：停用 Java

- **受保護模式的 Internet Explorer ActiveX 控制項**：  
  此原則設定可防止 ActiveX 控制項在啟用加強的受保護模式時，於受保護模式下執行。 當使用者所安裝的 ActiveX 控制項與加強的受保護模式不相容，且網站嘗試載入該控制項時，Internet Explorer 會通知使用者，並讓他們選擇在一般受保護模式下執行網站。 此原則設定可停用這項通知，並強制所有網站都在加強的受保護模式下執行。 加強的受保護模式在 64 位元版本的 Windows 上使用 64 位元處理序，藉此提供額外的保護來防範惡意網站。 對於至少執行 Windows 8 的電腦，加強的受保護模式也會限制 Internet Explorer 可從登錄和檔案系統讀取的位置。 當啟用加強的受保護模式，且使用者遇到網站所嘗試載入 ActiveX 控制項與加強的受保護模式不相容情況時，Internet Explorer 會通知使用者，並讓他們選擇針對該特定網站停用加強的受保護模式。 如果您啟用此原則設定，Internet Explorer 就無法讓使用者選擇停用加強的受保護模式。 所有受保護模式的網站都會在加強的受保護模式下執行。 如果您停用或未設定此原則設定，Internet Explorer 會通知使用者，讓他們選擇在一般受保護模式下執行具有不相容 ActiveX 控制項的網站。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067145)

  **預設**：停用

- **Internet Explorer 限制區域 XAML 檔案載入**：  
  此原則設定可讓您管理 Extensible Application Markup Language (XAML) 檔案的載入。 XAML 是以 XML 為基礎的宣告式標記語言，常用來建立利用 Windows Presentation Foundation 的豐富使用者介面和圖形。 如果您啟用此原則設定並將下拉式方塊設定為 [啟用]，則會在 Internet Explorer 內自動載入 XAML 檔案。 使用者無法變更此行為。 如果您將下拉式方塊設定為 [提示]，則會提示使用者載入 XAML 檔案。 如果您停用此原則設定，則不會在 Internet Explorer 內載入 XAML 檔案。 使用者無法變更此行為。 如果您未設定此原則設定，則使用者可以決定是否要在 Internet Explorer 內載入 XAML 檔案。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067070)

  **預設值**：停用

- **Internet Explorer 處理序已撰寫指令碼的視窗安全性限制**：  
  Internet Explorer 可讓指令碼來以程式設計方式來開啟各種類型的視窗、調整其大小並重新置放。 視窗限制安全性功能會限制快顯視窗並防止指令碼顯示視窗，讓使用者看不到標題和狀態列，或是模糊化其他視窗的標題和狀態列。 如果您啟用此原則設定，則會限制所有處理序使用已撰寫指令碼的視窗。 如果您停用或未設定此原則設定，則不會限制使用已撰寫指令碼的視窗。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067146)

  **預設**：啟用

- **在 Internet Explorer 限制區域中執行 ActiveX 控制項和外掛程式**：  
  此原則設定可讓您管理是否可以在指定區域的網頁上執行 ActiveX 控制項和外掛程式。 如果您啟用此原則設定，不需要使用者操作，即可執行控制項和外掛程式。 如果您在下拉式方塊中選取 [提示]，則會請使用者選擇是否允許執行控制項或外掛程式。 如果您停用此原則設定，則無法執行控制項和外掛程式。 如果您未設定此原則設定，則無法執行控制項和外掛程式。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067114)

  **預設值**：停用

- **在 Internet Explorer 限制區域中對標示為安全的 ActiveX 控制項執行指令碼**：  
  此原則設定可讓您管理標示為可安全處理指令碼的 ActiveX 控制項是否能夠與指令碼互動。 如果您啟用此原則設定，不需要使用者操作，就會自動發生指令碼互動。 如果您在下拉式方塊中選取 [提示]，則會請使用者選擇是否允許指令碼互動。 如果您停用此原則設定，指令碼互動不會發生。 如果您未設定此原則設定，則不會發生指令碼互動。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067062)

  **預設值**：停用

- **Internet Explorer 限制區域登入選項**：  
  此原則設定可讓您管理登入選項的設定。 如果您啟用此原則設定，即可從下列登入選項中進行選擇。

  - 匿名  - 使用匿名登入可停用 HTTP 驗證，並只針對 Common Internet File System (CIFS) 通訊協定使用來賓帳戶。

  - 提示  - 使用提示輸入使用者名稱及密碼可詢問使用者的使用者識別碼和密碼。 詢問使用者之後，即可在工作階段的其餘部分以無訊息模式使用這些值。

  - *只在內部網路區域自動登入* - 使用此選項詢問使用者在其他區域的使用者識別碼和密碼。 詢問使用者之後，即可在工作階段的其餘部分以無訊息模式使用這些值。

  - *使用目前的使用者名稱及密碼來自動登入* - 使用此選項嘗試使用 Windows NT 查問回應 (也稱為 NTLM 驗證) 進行登入。 如果伺服器支援 Windows NT 查問回應，登入會使用使用者的網路使用者名稱與密碼進行登入。 如果伺服器不支援 Windows NT 挑戰回應，則會請使用者提供使用者名稱和密碼。

  如果您停用此原則設定，登入會設定為 [只在內部網路區域自動登入]  。 如果您未設定此原則設定，登入會設定為 [提示]  輸入使用者名稱及密碼。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067110)

  **預設值**：匿名

- **在 Internet Explorer 受信任區域中初始化及撰寫未標示為安全的 ActiveX 控制項**：  
  此原則設定可讓您管理未標示為安全的 ActiveX 控制項。 如果您啟用此原則設定，不需要設定未受信任資料或指令碼的物件安全性，即可執行 ActiveX 控制項、對其載入參數並撰寫指令碼。 除了安全且受管理的區域之外，不建議使用此設定。 此設定會導致不安全和安全的控制項都會初始化和撰寫指令碼，並忽略 [對標示為安全的 ActiveX 控制項執行指令碼] 選項。 如果您啟用此原則設定並在下拉式方塊中選取 [提示]，則會詢問使用者是否允許對控制項載入參數或撰寫指令碼。 如果您停用此原則設定，則不會對無法標示為安全的 ActiveX 控制項載入參數或撰寫指令碼。 如果您未設定此原則設定，則會詢問使用者是否允許對控制項載入參數或撰寫指令碼。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067137)

  **預設值**：停用

- **Internet Explorer 會檢查伺服器憑證撤銷**：  
  此原則設定可讓您管理 Internet Explorer 是否會檢查伺服器憑證的撤銷狀態。 憑證遭入侵或不再有效時會予以撤銷，且此選項可防止使用者將機密資料提交給可能是詐騙或不安全的網站。 如果您啟用此原則設定，Internet Explorer 將會檢查伺服器憑證是否已被撤銷。 如果您停用此原則設定，Internet Explorer 將不會檢查伺服器憑證是否已被撤銷。 如果您未設定此原則設定，Internet Explorer 將不會檢查伺服器憑證是否已被撤銷。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067046)

  **預設**：啟用

- **Internet Explorer 網際網路區域較少特殊權限的網站**：  
  此原則設定可讓您管理較少特殊權限區域中的網站 (例如受限制的網站) 是否可以巡覽至此區域。 如果您啟用此原則設定，較少特殊權限區域中的網站可以在此區域中開啟新視窗，或巡覽至此區域。 安全性區域會在不具備 [來自區域高度的保護] 安全性功能所提供額外安全性階層的狀況下執行。 如果您在下拉式方塊中選取 [提示]，則會對使用者發出警告，指出即將發生可能具風險的瀏覽。 如果您停用此原則設定，則會禁止可能有害的瀏覽。 Internet Explorer 安全性功能會在此區域中開啟，如 [來自區域高度的保護] 功能控制所設定。 如果您未設定此原則設定，則較少特殊權限區域中的網站可以在此區域中開啟新視窗，或巡覽至此區域。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067109)

  **預設值**：停用

- **Internet Explorer 限制區域檔案下載**：  
  此原則設定可讓您管理是否允許從區域下載檔案。 此選項取決於含有下載連結的網頁所在區域，而不是傳遞檔案的來源區域。 如果您啟用此原則設定，即可從區域下載檔案。 如果您停用此原則設定，則無法從區域下載檔案。 如果您未設定此原則設定，則無法從區域下載檔案。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067038)

  **預設值**：停用

- **在 Internet Explorer 網際網路區域中執行使用 Authenticode 簽署的 .NET Framework 相依元件**：  
  此原則設定可讓您管理是否可以從 Internet Explorer 執行使用 Authenticode 簽署的 .NET Framework 元件。 這些元件包含從物件標記參考的受控控制項，以及從連結參考的受控可執行檔。 如果您啟用此原則設定，Internet Explorer 將會執行已簽署的受控元件。 如果您在下拉式方塊中選取 [提示]，Internet Explorer 將會提示使用者決定是否要執行已簽署的受控元件。 如果您停用此原則設定，Internet Explorer 將不會執行已簽署的受控元件。 如果您未設定此原則設定，Internet Explorer 將不會執行已簽署的受控元件。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067033)

  **預設值**：停用

- **Internet Explorer 可防止個別使用者安裝 ActiveX 控制項**：  
  此原則設定可讓您防止個別使用者安裝 ActiveX 控制項。 如果您啟用此原則設定，個別使用者將無法安裝 ActiveX 控制項。 如果您停用或未設定此原則設定，個別使用者可以安裝 ActiveX 控制項。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067058)

  **預設**：啟用

- **Internet Explorer 可防止管理 SmartScreen 篩選工具**：  
  此原則設定可防止使用者管理 SmartScreen 篩選工具，如果所瀏覽的網站已知會透過「網路釣魚」意圖詐騙個人資訊，或已知會裝載惡意程式碼，則這項工具會警告使用者。 如果您啟用此原則設定，將不會提示使用者開啟 SmartScreen 篩選工具。 不在篩選工具允許清單上的所有網址都會自動傳送給 Microsoft，而不會提示使用者。 如果您停用或未設定此原則設定，則會在初次執行體驗期間提示使用者決定是否要開啟 SmartScreen 篩選工具。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067135)

  **預設值**：啟用

- **Internet Explorer 處理序 MIME 探查安全功能**：  
  此原則設定可決定 Internet Explorer MIME 探查是否會防止某個類型的檔案提升為較危險的檔案類型。 如果您啟用此原則設定，MIME 探查永遠不會將某個類型的檔案提升為較危險的檔案類型。 如果您停用此原則設定，Internet Explorer 處理序將會允許 MIME 探查將某個類型的檔案提升為較危險的檔案類型。 如果您未設定此原則設定，MIME 探查永遠不會將某個類型的檔案提升為較危險檔案類型。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067124)

  **預設**：啟用

- **在 Internet Explorer 限制區域中下載已簽署的 ActiveX 控制項**：  
  此原則設定可讓您管理使用者是否可以從此區域中的網頁下載已簽署的 ActiveX 控制項。 如果您啟用此原則，使用者無須操作即可下載已簽署的控制項。 如果您在下拉式方塊中選取 [提示]，則會詢問使用者是否要下載未受信任發行者所簽署的控制項。 受信任發行者所簽署的程式碼會以無訊息方式下載。 如果您停用此原則設定，則無法下載已簽署的控制項。 如果您未設定此原則設定，則會詢問使用者是否要下載未受信任發行者所簽署的控制項。 受信任發行者所簽署的程式碼會以無訊息方式下載。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067120)

  **預設值**：停用

- **Internet Explorer 自動完成**：  
  此 [自動完成] 功能可以記住並建議表單上的使用者名稱和密碼。 如果您啟用此設定，使用者將無法變更 [表單上的使用者名稱和密碼] 或 [提示我儲存密碼]。 [表單上的使用者名稱和密碼] 的 [自動完成] 功能已開啟。 決定是否選取 [提示我儲存密碼]。 如果您停用此設定，使用者將無法變更 [表單上的使用者名稱和密碼] 或 [提示我儲存密碼]。 [表單上的使用者名稱和密碼] 的 [自動完成] 功能將會關閉。 使用者也無法選擇收到儲存密碼的提示。 如果您未進行此設定，則使用者可以自由開啟 [表單上的使用者名稱和密碼] 的 [自動完成] 功能，以及提示儲存密碼的選項。 若要顯示此選項，使用者可以開啟 [網際網路選項] 對話方塊，按一下 [內容] 索引標籤，然後按一下 [設定] 按鈕。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067122)

  **預設**：停用

- **Internet Explorer 網際網路區域允許執行 VBScript**：  
  此原則設定可讓您決定是否可以在特定 Internet Explorer 區域的網頁上執行 VBScript。 這些選項包括：

  - 啟用  - 不需要任何操作即可在特定區域的網頁上執行 VBScript。

  - 提示  - 系統會提示員工是否要允許在區域中執行 VBScript。

  - 停用  - 防止在區域中執行 VBScript。 如果您停用或未設定此原則設定，則不需要任何操作即可在指定的區域中執行 VBScript。

  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067119)

  **預設值**：停用

- **Internet Explorer 限制區域只允許核准的網域使用 TDC ActiveX 控制項**：  
  此原則設定可控制使用者是否可以執行網站上的 TDC ActiveX 控制項。 如果您啟用此原則設定，則不會執行來自此區域網站的 TDC ActiveX 控制項。 如果您停用此原則設定，則會執行來自此區域所有網站的 TDC ActiveX 控制項。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067032)

  **預設**：啟用

- **Internet Explorer 受信任區域不會對 ActiveX 控制項執行反惡意程式碼軟體**：  
  此原則設定可決定 Internet Explorer 是否會對 ActiveX 控制項執行反惡意程式碼程式，來檢查這些控制項是否可安全載入到頁面。 如果您啟用此原則設定，Internet Explorer 將不會使用您的反惡意程式碼程式，來檢查是否可以安全建立 ActiveX 控制項的執行個體。 如果您停用此原則設定，Internet Explorer 一律會使用您的反惡意程式碼程式，來檢查是否可以安全建立 ActiveX 控制項的執行個體。 如果您未設定此原則設定，Internet Explorer 一律會使用您的反惡意程式碼程式，來檢查是否可以安全建立 ActiveX 控制項的執行個體。 使用者可以透過 Internet Explorer [安全性] 設定來開啟或關閉此行為。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067115)

  **預設**：停用

- **Internet Explorer 本機電腦區域 Java 權限**：  
  此原則設定可讓您管理 Java Applet 的權限。 如果您啟用此原則設定，即可從下拉式方塊中選擇選項。 [自訂] 可個別控制權限設定。 [低安全性] 可讓 Applet 執行所有作業。 [中安全性] 可讓 Applet 在其沙箱 (記憶體中無法供外部應用程式呼叫的一個區域) 中執行，以及啟用暫存空間 (用戶端電腦上安全且受保護的存放區域) 和使用者控制的檔案 I/O 等功能。 [高安全性] 可讓 Applet 在其沙箱中執行。 停用 Java 可防止執行任何 Applet。 如果您停用此原則設定，則無法執行 Java Applet。 如果您未設定此原則設定，權限會設定為 [中安全性]。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067113)

  **預設值**：停用 Java

- **Internet Explorer 內部網路區域不會對 ActiveX 控制項執行反惡意程式碼軟體**：  
  此原則設定可決定 Internet Explorer 是否會對 ActiveX 控制項執行反惡意程式碼程式，來檢查這些控制項是否可安全載入到頁面。 如果您啟用此原則設定，Internet Explorer 將不會使用您的反惡意程式碼程式，來檢查是否可以安全建立 ActiveX 控制項的執行個體。 如果您停用此原則設定，Internet Explorer 一律會使用您的反惡意程式碼程式，來檢查是否可以安全建立 ActiveX 控制項的執行個體。 如果您未設定此原則設定，Internet Explorer 將不會使用您的反惡意程式碼程式，來檢查是否可以安全建立 ActiveX 控制項的執行個體。 使用者可以透過 Internet Explorer [安全性] 設定來開啟或關閉此行為。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067138)

  **預設**：停用

- **Internet Explorer 限制區域程式碼片段**：  
  此原則設定可讓您管理使用者是否可以執行程式碼片段。 如果您啟用此原則設定，使用者可以執行程式碼片段。 如果您停用此原則設定，使用者無法執行程式碼片段。 如果您未設定此原則設定，則使用者可以啟用或停用程式碼片段。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067112)

  **預設**：停用

- **Internet Explorer 處理序通知列**：  
  此原則設定可讓您管理檔案或程式碼安裝受到限制時，是否要顯示 Internet Explorer 處理序的通知列。 預設會顯示 Internet Explorer 處理序的通知列。 如果您啟用此原則設定，則會顯示 Internet Explorer 處理序的通知列。 如果您停用此原則設定，則不會顯示 Internet Explorer 處理序的通知列。 如果您未設定此原則設定，則不會顯示 Internet Explorer 處理序的通知列。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067139)

  **預設**：啟用

- **在 Internet Explorer 網際網路區域中下載已簽署的 ActiveX 控制項**：  
  此原則設定可讓您管理使用者是否可以從此區域中的網頁下載已簽署的 ActiveX 控制項。 如果您啟用此原則，使用者無須操作即可下載已簽署的控制項。 如果您在下拉式方塊中選取 [提示]，則會詢問使用者是否要下載未受信任發行者所簽署的控制項。 受信任發行者所簽署的程式碼會以無訊息方式下載。 如果您停用此原則設定，則無法下載已簽署的控制項。 如果您未設定此原則設定，則會詢問使用者是否要下載未受信任發行者所簽署的控制項。 受信任發行者所簽署的程式碼會以無訊息方式下載。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067064)

  **預設值**：停用

- **Internet Explorer 限制區域 SmartScreen**：  
  此原則設定可控制 SmartScreen 篩選工具是否要掃描此區域中的網頁有無惡意內容。 如果您啟用此原則設定，SmartScreen 篩選工具將會掃描此區域中的網頁有無惡意內容。 如果您停用此原則設定，SmartScreen 篩選工具將不會掃描此區域中的網頁有無惡意內容。 如果您未設定此原則設定，則使用者可以選擇 SmartScreen 篩選工具是否要掃描此區域中的網頁有無惡意內容。 注意：在 Internet Explorer 7 中，此原則設定可控制網路釣魚篩選工具是否要掃描此區域中的網頁有無惡意內容。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067034)

  **預設**：啟用

- **Internet Explorer 移除已過期 ActiveX 控制項的 [這次執行] 按鈕**：  
  此原則設定可讓您防止使用者在 Internet Explorer 中看到 [這次執行] 按鈕，以及執行特定的已過期 ActiveX 控制項。 如果您啟用此原則設定，當 Internet Explorer 封鎖已過期的 ActiveX 控制項時，使用者就不會在出現的警告訊息中看到 [這次執行] 按鈕。 如果您停用或未設定此原則設定，當 Internet Explorer 封鎖已過期的 ActiveX 控制項時，使用者將會在出現的警告訊息中看到 [這次執行] 按鈕。 按一下此按鈕可讓使用者執行一次已過期的 ActiveX 控制項。 如需詳細資訊，請參閱 Internet Explorer TechNet 文件庫中的＜已過期的 ActiveX 控制項＞。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067123)

  **預設**：啟用

- **Internet Explorer 網際網路區域從 iFrame 啟動應用程式和檔案**：  
  此原則設定可讓您管理是否可以從此區域網頁 HTML 中的 IFRAME 參考執行應用程式及下載檔案。 如果您啟用此原則設定，無需使用者操作，即可從此區域網頁上的 IFRAME 執行應用程式及下載檔案。 如果您在下拉式方塊中選取 [提示]，則會請使用者選擇是否要從此區域網頁上的 IFRAME 執行應用程式及下載檔案。 如果您停用此原則設定，使用者將無法從這個區域的頁面上的 Iframe 執行應用程式及下載檔案。 如果您未設定此原則設定，則會請使用者選擇是否要從此區域網頁上的 IFRAME 執行應用程式及下載檔案。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067020)

  **預設值**：停用

- **Internet Explorer 限制區域跨不同網域巡覽視窗和畫面**：  
  此原則設定可讓您設定當來源與目的地位於不同視窗時，將內容從某個網域拖曳至另一個網域的選項。 如果您啟用此原則設定並按一下 [啟用]，當來源與目的地位於不同視窗時，使用者就可以將內容從某個網域拖曳至另一個網域。 使用者無法變更此設定。 如果您啟用此原則設定並按一下 [停用]，當來源與目的地位於不同視窗時，使用者就無法將內容從某個網域拖曳至另一個網域。 使用者無法變更此設定。 在 Internet Explorer 10 中，如果您停用或未設定此原則設定，當來源與目的地位於不同視窗時，使用者就無法將內容從某個網域拖曳至另一個網域。 使用者可以在 [網際網路選項] 對話方塊中變更此設定。 在 Internet Explorer 9 和更舊版本中，如果您停用或未設定此原則，當來源與目的地位於不同視窗時，使用者就可將內容從某個網域拖曳至另一個網域。 使用者無法變更此設定。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067050)

  **預設值**：停用

- **Internet Explorer 網際網路區域 SmartScreen**：  
  此原則設定可控制 SmartScreen 篩選工具是否要掃描此區域中的網頁有無惡意內容。 如果您啟用此原則設定，SmartScreen 篩選工具將會掃描此區域中的網頁有無惡意內容。 如果您停用此原則設定，SmartScreen 篩選工具將不會掃描此區域中的網頁有無惡意內容。 如果您未設定此原則設定，則使用者可以選擇 SmartScreen 篩選工具是否要掃描此區域中的網頁有無惡意內容。 注意：在 Internet Explorer 7 中，此原則設定可控制網路釣魚篩選工具是否要掃描此區域中的網頁有無惡意內容。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067047)

  **預設**：啟用

- **Internet Explorer 鎖定的受信任區域 Java 權限**：  
  此原則設定可讓您管理 Java Applet 的權限。 如果您啟用此原則設定，即可從下拉式方塊中選擇選項。 [自訂] 可個別控制權限設定。 [低安全性] 可讓 Applet 執行所有作業。 [中安全性] 可讓 Applet 在其沙箱 (記憶體中無法供外部應用程式呼叫的一個區域) 中執行，以及啟用暫存空間 (用戶端電腦上安全且受保護的存放區域) 和使用者控制的檔案 I/O 等功能。 [高安全性] 可讓 Applet 在其沙箱中執行。 停用 Java 可防止執行任何 Applet。 如果您停用此原則設定，則無法執行 Java Applet。 如果您未設定此原則設定，則會停用 Java Applet。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067142)

  **預設值**：停用 Java

- **Internet Explorer 檢查已下載程式的簽章**：  
  此原則設定可讓您管理 Internet Explorer 在下載可執行程式之前，是否會檢查使用者電腦上的數位簽章 (這可識別已簽署軟體的發行者，並確認它尚未經過修改或竄改)。 如果您啟用此原則設定，Internet Explorer 在將可執行程式下載到使用者電腦之前，會檢查其數位簽章並顯示其身分識別。 如果您停用此原則設定，Internet Explorer 在將可執行程式下載到使用者電腦之前，不會檢查其數位簽章或顯示其身分識別。 如果您未設定此原則，Internet Explorer 在將可執行程式下載到使用者電腦之前，不會檢查其數位簽章或顯示其身分識別。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067051)

  **預設**：啟用

- **Internet Explorer 限制區域對網頁瀏覽器控制項執行指令碼**：  
  此原則設定會判斷頁面是否可以透過指令碼控制內嵌的 WebBrowser 控制項。 如果您啟用此原則設定，即允許對 WebBrowser 控制項進行指令碼存取。 如果您停用此原則設定，則不允許對 WebBrowser 控制項進行指令碼存取。 如果您未設定此原則設定，則使用者可以啟用或停用對 WebBrowser 控制項的指令碼存取。 根據預設，只有在本機電腦和內部網路區域中才允許對 WebBrowser 控制項的指令碼存取。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067098)

  **預設**：停用

- **Internet Explorer 限制區域跨網站指令碼篩選器**：  
  此原則可控制跨網站指令碼 (XSS) 篩選器是否會偵測並防止此區域網站中的跨網站指令碼插入。 如果您啟用此原則設定，則會開啟此區域網站的 XSS 篩選器，且 XSS 篩選器會嘗試封鎖跨網站指令碼插入。 如果您停用此原則設定，則會關閉此區域網站的 XSS 篩選器，且 Internet Explorer 會允許跨網站指令碼插入。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067178)

  **預設**：啟用

- **Internet Explorer 限制區域二進位檔和指令碼行為**：  
  此原則設定可讓您管理動態的二進位檔和指令碼行為：封裝其附加目標 HTML 元素之特定功能的元件。 如果您啟用此原則設定，則可以使用二進位檔和指令碼行為。 如果您在下拉式方塊中選取 [系統管理員已核准]，則只能使用 [二進位檔行為安全性限制] 原則下 [系統管理員核准的行為] 所列出的行為。 如果您停用此原則設定，除非應用程式已實作自訂安全性管理員，否則無法使用二進位和指令碼行為。 如果您未設定此原則設定，除非應用程式已實作自訂安全性管理員，否則無法使用二進位和指令碼行為。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067224)

  **預設值**：停用

- **Internet Explorer 安全性設定檢查**：  
  此原則設定會關閉安全性設定檢查功能，該功能可檢查 Internet Explorer 安全性設定以判斷設定何時會讓 Internet Explorer 面臨風險。 如果您啟用此原則設定，就會關閉此功能。 如果您停用或未設定此原則設定，則會開啟此功能。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067182)

  **預設**：啟用

- **Internet Explorer 網際網路區域潛在不安全檔案的安全性警告**：  
  此原則設定可控制當使用者嘗試開啟可執行檔或其他潛在不安全的檔案時 (例如使用檔案總管從內部網路檔案共用開啟)，是否顯示「開啟檔案 - 安全性警告」訊息。 如果您啟用此原則設定並將下拉式方塊設定為 [啟用]，開啟這些檔案時不會有安全性警告。 如果您將下拉式方塊設定為 [提示]，開啟檔案之前會先顯示安全性警告。 如果您停用此原則設定，則不會開啟這些檔案。 如果您未設定此原則設定，則使用者可以設定電腦處理這些檔案的方式。 根據預設，這些檔案在限制區域中會被封鎖、在內部網路和本機電腦區域中會啟用，而在網際網路和受信任區域中會設定為 [提示]。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067204)

  **預設值**：提示

- **Internet Explorer 內部網路區域 Java 權限**：  
  此原則設定可讓您管理 Java Applet 的權限。 如果您啟用此原則設定，即可從下拉式方塊中選擇選項。 [自訂] 可個別控制權限設定。 [低安全性] 可讓 Applet 執行所有作業。 [中安全性] 可讓 Applet 在其沙箱 (記憶體中無法供外部應用程式呼叫的一個區域) 中執行，以及啟用暫存空間 (用戶端電腦上安全且受保護的存放區域) 和使用者控制的檔案 I/O 等功能。 [高安全性] 可讓 Applet 在其沙箱中執行。 停用 Java 可防止執行任何 Applet。 如果您停用此原則設定，則無法執行 Java Applet。 如果您未設定此原則設定，權限會設定為 [中安全性]。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067206)

  **預設值**：高安全性

- **Internet Explorer 封鎖已過期的 ActiveX 控制項**：  
  此原則設定可決定 Internet Explorer 是否會封鎖特定的已過期 ActiveX 控制項。 內部網路區域永遠不會封鎖已過期的 ActiveX 控制項。 如果您啟用此原則設定，Internet Explorer 就會停止封鎖已過期的 ActiveX 控制項。 如果您停用或未設定此原則設定，Internet Explorer 會繼續封鎖特定的已過期 ActiveX 控制項。 如需詳細資訊，請參閱 Internet Explorer TechNet 文件庫中的＜已過期的 ActiveX 控制項＞。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067203)

  **預設**：啟用

- **Internet Explorer 限制區域快顯封鎖程式**：  
  此原則設定可讓您管理是否要顯示不需要的快顯視窗。 這不會封鎖終端使用者按一下連結時所開啟的快顯視窗。 如果您啟用此原則設定，即可防止顯示大部分不需要的快顯視窗。 如果您停用此原則設定，則無法防止顯示快顯視窗。 如果您未設定此原則設定，即可防止顯示大部分不需要的快顯視窗。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067180)

  **預設值**：啟用

- **Internet Explorer 處理序 MK 通訊協定安全性限制**：  
  [MK 通訊協定安全性限制] 原則設定可避免 MK 通訊協定來減少攻擊面區域。 MK 通訊協定上裝載的資源將會失敗。 如果您啟用此原則設定，檔案總管和 Internet Explorer 都無法使用 MK 通訊協定，因此 MK 通訊協定上裝載的資源將會失敗。 如果您停用此原則設定，應用程式可以使用 MK 通訊協定 API。 MK 通訊協定上裝載的資源適用於檔案總管和 Internet Explorer 處理序。 如果您未設定此原則設定，檔案總管和 Internet Explorer 都無法使用 MK 通訊協定，因此 MK 通訊協定上裝載的資源將會失敗。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067179)

  **預設**：啟用

- **Internet Explorer 受信任區域 Java 權限**：  
  此原則設定可讓您管理 Java Applet 的權限。 如果您啟用此原則設定，即可從下拉式方塊中選擇選項。 [自訂] 可個別控制權限設定。 [低安全性] 可讓 Applet 執行所有作業。 [中安全性] 可讓 Applet 在其沙箱 (記憶體中無法供外部應用程式呼叫的一個區域) 中執行，以及啟用暫存空間 (用戶端電腦上安全且受保護的存放區域) 和使用者控制的檔案 I/O 等功能。 [高安全性] 可讓 Applet 在其沙箱中執行。 停用 Java 可防止執行任何 Applet。 如果您停用此原則設定，則無法執行 Java Applet。 如果您未設定此原則設定，權限會設定為 [低安全性]。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067200)

  **預設值**：高安全性

- **Internet Explorer 限制區域 Java Applet 的指令碼處理**：  
  此原則設定可讓您管理是否要將 Applet 公開到區域內的指令碼。 如果您啟用此原則設定，無需使用者操作，指令碼就會自動存取 Applet。 如果您在下拉式方塊中選取 [提示]，則會請使用者選擇是否允許指令碼存取 Applet。 如果您停用此原則設定，指令碼無法存取 Applet。 如果您未設定此原則設定，則指令碼無法存取 Applet。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067202)

  **預設值**：停用

- **Internet Explorer 鎖定的限制區域 Java 權限**：  
  此原則設定可讓您管理 Java Applet 的權限。 如果您啟用此原則設定，即可從下拉式方塊中選擇選項。 [自訂] 可個別控制權限設定。 [低安全性] 可讓 Applet 執行所有作業。 [中安全性] 可讓 Applet 在其沙箱 (記憶體中無法供外部應用程式呼叫的一個區域) 中執行，以及啟用暫存空間 (用戶端電腦上安全且受保護的存放區域) 和使用者控制的檔案 I/O 等功能。 [高安全性] 可讓 Applet 在其沙箱中執行。 停用 Java 可防止執行任何 Applet。 如果您停用此原則設定，則無法執行 Java Applet。 如果您未設定此原則設定，則會停用 Java Applet。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067181)

  **預設值**：停用 Java

- **Internet Explorer 網際網路區域只允許核准的網域使用 ActiveX 控制項**：  
  此原則設定可控制是否提示使用者允許 ActiveX 控制項在非 ActiveX 控制項安裝網站上執行。 如果您啟用此原則設定，則會在可從此區域的網站執行 ActiveX 控制項之前提示使用者。 使用者可以選擇允許控制項從目前的網站或所有網站執行。 如果您停用此原則設定，使用者不會看到每個網站的 ActiveX 提示，且 ActiveX 控制項可以從此區域的所有網站執行。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067091)

  **預設**：啟用

- **Internet Explorer 包含所有的網路路徑**：  
  Internet Explorer 包含所有的網路路徑。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067090)

  **預設**：停用

- **Internet Explorer 網際網路區域受保護模式**：  
  此原則設定可讓您開啟受保護模式。 受保護模式會藉由減少 Internet Explorer 可在登錄和檔案系統中寫入的位置，協助保護 Internet Explorer 免於遭受弱點入侵。 如果您啟用此原則設定，就會開啟受保護模式。 使用者無法關閉受保護模式。 如果您停用此原則設定，就會關閉受保護模式。 使用者無法開啟受保護模式。 如果您未設定此原則設定，則使用者可以開啟或關閉受保護模式。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067171)

  **預設值**：啟用

- **Internet Explorer 網際網路區域初始化未標示為安全的 ActiveX 控制項並對其撰寫指令碼**：  
  此原則設定可讓您管理未標示為安全的 ActiveX 控制項。 如果您啟用此原則設定，不需要設定未受信任資料或指令碼的物件安全性，即可執行 ActiveX 控制項、對其載入參數並撰寫指令碼。 除了安全且受管理的區域之外，不建議使用此設定。 此設定會導致不安全和安全的控制項都會初始化和撰寫指令碼，並忽略 [對標示為安全的 ActiveX 控制項執行指令碼] 選項。 如果您啟用此原則設定並在下拉式方塊中選取 [提示]，則會詢問使用者是否允許對控制項載入參數或撰寫指令碼。 如果您停用此原則設定，則不會對無法標示為安全的 ActiveX 控制項載入參數或撰寫指令碼。 如果您未設定此原則設定，則不會對無法標示為安全的 ActiveX 控制項載入參數或撰寫指令碼。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067170)

  **預設值**：停用

- **Internet Explorer 鎖定的限制區域 SmartScreen**：  
  此原則設定可控制 SmartScreen 篩選工具是否要掃描此區域中的網頁有無惡意內容。 如果您啟用此原則設定，SmartScreen 篩選工具將會掃描此區域中的網頁有無惡意內容。 如果您停用此原則設定，SmartScreen 篩選工具將不會掃描此區域中的網頁有無惡意內容。 如果您未設定此原則設定，則使用者可以選擇 SmartScreen 篩選工具是否要掃描此區域中的網頁有無惡意內容。 注意：在 Internet Explorer 7 中，此原則設定可控制網路釣魚篩選工具是否要掃描此區域中的網頁有無惡意內容。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067092)

  **預設**：啟用

- **Internet Explorer 當機偵測**：  
  此原則設定可讓您管理附加元件管理的當機偵測功能。 如果您啟用此原則設定，Internet Explorer 中的當機將展現 Windows XP Professional Service Pack 1 和較舊版本通常叫用 Windows 錯誤報告的行為。 Windows 錯誤報告的所有原則設定仍會繼續套用。 如果您停用或未設定此原則設定，附加元件管理的當機偵測功能將會運作。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067094)

  **預設**：停用

- **Internet Explorer 網際網路區域 Java 權限**：  
  此原則設定可讓您管理 Java Applet 的權限。 如果您啟用此原則設定，即可從下拉式方塊中選擇選項。 [自訂] 可個別控制權限設定。 [低安全性] 可讓 Applet 執行所有作業。 [中安全性] 可讓 Applet 在其沙箱 (記憶體中無法供外部應用程式呼叫的一個區域) 中執行，以及啟用暫存空間 (用戶端電腦上安全且受保護的存放區域) 和使用者控制的檔案 I/O 等功能。 [高安全性] 可讓 Applet 在其沙箱中執行。 停用 Java 可防止執行任何 Applet。 如果您停用此原則設定，則無法執行 Java Applet。 如果您未設定此原則設定，權限會設定為 [高安全性]。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067174)

  **預設值**：停用 Java

- **Internet Explorer 限制區域動態指令碼處理**：  
  此原則設定可讓您管理是否執行區域中的網頁指令碼。 如果您啟用此原則設定，即可自動執行區域中的網頁指令碼。 如果您在下拉式方塊中選取 [提示]，則會請使用者選擇是否允許執行區域中的網頁指令碼。 如果您停用此原則設定，則無法執行區域中的網頁指令碼。 如果您未設定此原則設定，則無法執行區域中的網頁指令碼。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067172)

  **預設值**：停用

- **Internet Explorer 網際網路區域登入選項**：  
  此原則設定可讓您管理登入選項的設定。 如果您啟用此原則設定，即可從下列登入選項中進行選擇。 [匿名登入] 可停用 HTTP 驗證並只針對 Common Internet File System (CIFS) 通訊協定使用來賓帳戶。 [提示輸入使用者名稱及密碼] 可詢問使用者的使用者識別碼和密碼。 詢問使用者之後，即可在工作階段的其餘部分以無訊息模式使用這些值。 [只在內部網路區域自動登入] 可詢問使用者在其他區域的使用者識別碼和密碼。 詢問使用者之後，即可在工作階段的其餘部分以無訊息模式使用這些值。 使用目前的使用者名稱及密碼來自動登入可嘗試使用 Windows NT 挑戰回應 (也稱為 NTLM 驗證) 進行登入。 如果伺服器支援 Windows NT 查問回應，登入會使用使用者的網路使用者名稱與密碼進行登入。 如果伺服器不支援 Windows NT 挑戰回應，則會請使用者提供使用者名稱和密碼。 如果您停用此原則設定，登入會設定為 [只在內部網路區域自動登入]。 如果您未設定此原則設定，登入會設定為 [只在內部網路區域自動登入]。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067194)

  **預設值**：提示

- **Internet Explorer 限制區域允許執行 VBScript**：  
  此原則設定可讓您管理是否可以在 Internet Explorer 指定區域的網頁上執行 VBScript。 如果您在下拉式方塊中選取 [啟用]，無需使用者操作即可執行 VBScript。 如果您在下拉式方塊中選取 [提示]，則會請使用者選擇是否允許執行 VBScript。 如果您在下拉式方塊中選取 [停用]，則無法執行 VBScript。 如果您未設定或停用此原則設定，則無法執行 VBScript。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067173)

  **預設值**：停用

- **Internet Explorer 網際網路區域跨視窗拖曳來自不同網域的內容**：  
  此原則設定可讓您設定當來源與目的地位於不同視窗時，將內容從某個網域拖曳至另一個網域的選項。 如果您啟用此原則設定並按一下 [啟用]，當來源與目的地位於不同視窗時，使用者就可以將內容從某個網域拖曳至另一個網域。 使用者無法變更此設定。 如果您啟用此原則設定並按一下 [停用]，當來源與目的地位於不同視窗時，使用者就無法將內容從某個網域拖曳至另一個網域。 使用者無法變更此設定。 在 Internet Explorer 10 中，如果您停用或未設定此原則設定，當來源與目的地位於不同視窗時，使用者就無法將內容從某個網域拖曳至另一個網域。 使用者可以在 [網際網路選項] 對話方塊中變更此設定。 在 Internet Explorer 9 和更舊版本中，如果您停用或未設定此原則，當來源與目的地位於不同視窗時，使用者就可將內容從某個網域拖曳至另一個網域。 使用者無法變更此設定。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067093)

  **預設**：停用

- **Internet Explorer 內部網路區域初始化未標示為安全的 ActiveX 控制項並對其撰寫指令碼**：  
  此原則設定可讓您管理未標示為安全的 ActiveX 控制項。 如果您啟用此原則設定，不需要設定未受信任資料或指令碼的物件安全性，即可執行 ActiveX 控制項、對其載入參數並撰寫指令碼。 除了安全且受管理的區域之外，不建議使用此設定。 此設定會導致不安全和安全的控制項都會初始化和撰寫指令碼，並忽略 [對標示為安全的 ActiveX 控制項執行指令碼] 選項。 如果您啟用此原則設定並在下拉式方塊中選取 [提示]，則會詢問使用者是否允許對控制項載入參數或撰寫指令碼。 如果您停用此原則設定，則不會對無法標示為安全的 ActiveX 控制項載入參數或撰寫指令碼。 如果您未設定此原則設定，則不會對無法標示為安全的 ActiveX 控制項載入參數或撰寫指令碼。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067175)

  **預設值**：停用

- **Internet Explorer 下載隨函附件**：  
  此原則設定可防止使用者將隨函附件 (檔案附件) 從摘要下載到使用者的電腦。 如果您啟用此原則設定，使用者無法透過 [摘要] 屬性頁將 Feed Sync Engine 設成下載隨函附件。 開發人員無法透過摘要 API 來變更下載設定。 如果您停用或未設定此原則設定，則使用者可以透過 [摘要] 屬性頁將 Feed Sync Engine 設成下載隨函附件。 開發人員可以透過摘要 API 來變更下載設定。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067245)

  **預設**：停用

- **Internet Explorer 限制區域下載未簽署的 ActiveX 控制項**：  
  此原則設定可讓您管理使用者是否可以從區域下載未簽署的 ActiveX 控制項。 這類程式碼可能有害，尤其是來自未受信任區域的程式碼。 如果您啟用此原則設定，使用者無須操作即可執行未簽署的控制項。 如果您在下拉式方塊中選取 [提示]，則會請使用者選擇是否允許執行未簽署的控制項。 如果您停用此原則設定，使用者將無法執行未簽署的控制項。 如果您未設定此原則設定，使用者將無法執行未簽署的控制項。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067177)

  **預設值**：停用

- **Internet Explorer 網際網路區域從視窗內的不同網域拖曳內容**：  
  此原則設定可讓您管理使用者是否可以從區域下載未簽署的 ActiveX 控制項。 這類程式碼可能有害，尤其是來自未受信任區域的程式碼。 如果您啟用此原則設定，使用者無須操作即可執行未簽署的控制項。 如果您在下拉式方塊中選取 [提示]，則會請使用者選擇是否允許執行未簽署的控制項。 如果您停用此原則設定，使用者將無法執行未簽署的控制項。 如果您未設定此原則設定，使用者將無法執行未簽署的控制項。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067095)

  **預設**：停用

- **Internet Explorer 處理序限制 ActiveX 安裝**：  
  此原則設定可讓裝載網頁瀏覽器控制項的應用程式，封鎖 ActiveX 控制項安裝的自動提示。 如果您啟用此原則設定，網頁瀏覽器控制項將會為所有處理序封鎖 ActiveX 控制項安裝的自動提示。 如果您停用或未設定此原則設定，網頁瀏覽器控制項不會為所有處理序封鎖 ActiveX 控制項安裝的自動提示。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067250)

  **預設**：啟用

- **Internet Explorer 網際網路區功能變數代碼段**：  
  此原則設定可讓您管理使用者是否可以執行程式碼片段。 如果您啟用此原則設定，使用者可以執行程式碼片段。 如果您停用此原則設定，使用者無法執行程式碼片段。 如果您未設定此原則設定，則使用者可以啟用或停用程式碼片段。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067176)

  **預設值**：停用

- **Internet Explorer 限制區域拖放或複製並貼上檔案**：  
  此原則設定可讓您管理使用者是否可以從區域的來源中拖曳檔案或複製並貼上檔案。 如果您啟用此原則設定，使用者可以從此區域自動拖曳檔案或複製並貼上檔案。 如果您在下拉式方塊中選取 [提示]，則會請使用者選擇是要從此區域拖曳還是複製檔案。 如果您停用此原則設定，使用者將無法從此區域拖曳檔案或複製並貼上檔案。 如果您未設定此原則設定，則會請使用者選擇是否要從此區域拖曳或複製檔案。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067096)

  **預設值**：停用

- **簽章無效時的 Internet Explorer 軟體**：  
  此原則設定可讓您管理 ActiveX 控制項和檔案下載等軟體是否可以由使用者安裝或執行，即使簽章無效也一樣。 無效的簽章可能表示有人已竄改檔案。 如果您啟用此原則設定，則會提示使用者安裝或執行具有無效簽章的檔案。 如果您停用此原則設定，使用者將無法執行或安裝具有無效簽章的檔案。 如果您未設定此原則，則使用者可以選擇執行或安裝具有無效簽章的檔案。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067201)

  **預設**：停用

- **Internet Explorer 限制區域透過指令碼複製並貼上**：  
  此原則設定可讓您管理指令碼是否可以在指定區域中執行剪貼簿作業 (例如剪下、複製及貼上)。 如果您啟用此原則設定，指令碼將可以執行剪貼簿作業。 如果您在下拉式方塊中選取 [提示]，則會詢問使用者是否要執行剪貼簿作業。 如果您停用此原則設定，則指令碼無法執行剪貼簿作業。 如果您未設定此原則設定，則指令碼無法執行剪貼簿作業。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067165)

  **預設值**：停用

- **Internet Explorer 限制區域跨視窗拖曳來自不同網域的內容**：  
  此原則設定可讓您設定當來源與目的地位於不同視窗時，將內容從某個網域拖曳至另一個網域的選項。 如果您啟用此原則設定並按一下 [啟用]，當來源與目的地位於不同視窗時，使用者就可以將內容從某個網域拖曳至另一個網域。 使用者無法變更此設定。 如果您啟用此原則設定並按一下 [停用]，當來源與目的地位於不同視窗時，使用者就無法將內容從某個網域拖曳至另一個網域。 使用者無法變更此設定。 在 Internet Explorer 10 中，如果您停用或未設定此原則設定，當來源與目的地位於不同視窗時，使用者就無法將內容從某個網域拖曳至另一個網域。 使用者可以在 [網際網路選項] 對話方塊中變更此設定。 在 Internet Explorer 9 和更舊版本中，如果您停用或未設定此原則，當來源與目的地位於不同視窗時，使用者就可將內容從某個網域拖曳至另一個網域。 使用者無法變更此設定。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067166)

  **預設**：停用

- **Internet Explorer 使用者新增網站**：  
  防止使用者從安全性區域新增或移除網站。 安全性區域是一組具有相同安全性等級的網站。 如果您啟用此原則，則會停用安全性區域的網站管理設定 (如果要查看安全性區域的網站管理設定，請在 [網際網路選項] 對話方塊中，按一下 [安全性] 索引標籤，然後按一下 [網站] 按鈕)。如果您停用或未設定此原則，則使用者可以從 [信任的網站] 和 [限制的網站] 區域新增或移除網站，以及變更 [近端內部網路] 區域的設定。 此原則可防止使用者變更系統管理員所建立安全性區域的網站管理設定。 注意：[停用安全性頁面] 原則 (位於 \使用者設定\系統管理範本\Windows 元件\Internet Explorer\網際網路控制台) 可從介面移除 [安全性] 索引標籤，其優先於此原則。 如果已啟用該原則，則會忽略此原則。 此外，請參閱「安全性區域: 只使用電腦設定」原則。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067167)

  **預設**：停用

- **Internet Explorer 網際網路區域以指令碼起始的視窗**：  
  此原則設定可讓您管理以指令碼起始的快顯視窗限制，以及包含標題和狀態列的視窗限制。 如果您啟用此原則設定，Windows 限制安全性將不會套用至此區域。 安全性區域會在不具備此功能所提供額外安全性階層的狀況下執行。 如果您停用此原則設定，將不可執行以指令碼起始的快顯視窗，以及包含標題和狀態列的視窗中所包含可能有害動作。 Internet Explorer 安全性功能會在此區域中開啟，如處理序的 [已撰寫指令碼的 Windows 安全性限制] 功能控制設定所指定。 如果您未設定此原則設定，將不可執行以指令碼起始的快顯視窗，以及包含標題和狀態列的視窗中所包含可能有害動作。 Internet Explorer 安全性功能會在此區域中開啟，如處理序的 [已撰寫指令碼的 Windows 安全性限制] 功能控制設定所指定。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067088)

  **預設**：停用

- **Internet Explorer 安全性區域只使用機器設定**：  
  將安全性區域資訊套用至相同電腦的所有使用者。 安全性區域是一組具有相同安全性等級的網站。 如果您啟用此原則，使用者對某個安全性區域的變更將會套用至該電腦的所有使用者。 如果您停用或未設定此原則，則相同電腦使用者可以建立自己的安全性區域設定。 使用此原則可確保安全性區域設定會一致套用至相同電腦，而不會因使用者而異。 此外，請參閱「安全性區域: 不允許使用者變更原則」原則。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067086)

  **預設**：啟用

- **Internet Explorer 鎖定的本機電腦區域 Java 權限**：  
  此原則設定可讓您管理 Java Applet 的權限。 如果您啟用此原則設定，即可從下拉式方塊中選擇選項。 [自訂] 可個別控制權限設定。 [低安全性] 可讓 Applet 執行所有作業。 [中安全性] 可讓 Applet 在其沙箱 (記憶體中無法供外部應用程式呼叫的一個區域) 中執行，以及啟用暫存空間 (用戶端電腦上安全且受保護的存放區域) 和使用者控制的檔案 I/O 等功能。 [高安全性] 可讓 Applet 在其沙箱中執行。 停用 Java 可防止執行任何 Applet。 如果您停用此原則設定，則無法執行 Java Applet。 如果您未設定此原則設定，則會停用 Java Applet。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067253)

  **預設值**：停用 Java

- **Internet Explorer 限制區域不會對 ActiveX 控制項執行反惡意程式碼軟體**：  
  此原則設定可決定 Internet Explorer 是否會對 ActiveX 控制項執行反惡意程式碼程式，來檢查這些控制項是否可安全載入到頁面。 如果您啟用此原則設定，Internet Explorer 將不會使用您的反惡意程式碼程式，來檢查是否可以安全建立 ActiveX 控制項的執行個體。 如果您停用此原則設定，Internet Explorer 一律會使用您的反惡意程式碼程式，來檢查是否可以安全建立 ActiveX 控制項的執行個體。 如果您未設定此原則設定，Internet Explorer 一律會使用您的反惡意程式碼程式，來檢查是否可以安全建立 ActiveX 控制項的執行個體。 使用者可以透過 Internet Explorer [安全性] 設定來開啟或關閉此行為。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067089)

  **預設**：停用

- **在 Internet Explorer 限制區域中執行使用 Authenticode 簽署的 .NET Framework 相依元件**：  
  此原則設定可讓您管理是否可以從 Internet Explorer 執行使用 Authenticode 簽署的 .NET Framework 元件。 這些元件包含從物件標記參考的受控控制項，以及從連結參考的受控可執行檔。 如果您啟用此原則設定，Internet Explorer 將會執行已簽署的受控元件。 如果您在下拉式方塊中選取 [提示]，Internet Explorer 將會提示使用者決定是否要執行已簽署的受控元件。 如果您停用此原則設定，Internet Explorer 將不會執行已簽署的受控元件。 如果您未設定此原則設定，Internet Explorer 將不會執行已簽署的受控元件。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067169)

  **預設值**：停用

- **在 Internet Explorer 限制區域中存取資料來源**：  
  此原則設定可讓您管理 Internet Explorer 是否可以從使用 Microsoft XML 剖析器 (MSXML) 或 ActiveX Data Objects (ADO) 的其他安全性區域存取資料。 如果您啟用此原則設定，使用者就可以將網頁載入使用 MSXML 或 ADO 的區域來存取該區域中其他網站的資料。 如果您在下拉式方塊中選取 [提示]，則會請使用者選擇是否允許將網頁載入至使用 MSXML 或 ADO 的區域來存取該區域中其他網站資料。 如果您停用此原則設定，使用者就無法將網頁載入使用 MSXML 或 ADO 的區域來存取該區域中其他網站資料。 如果您未設定此原則設定，使用者就無法將網頁載入使用 MSXML 或 ADO 的區域來存取該區域中其他網站資料。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067161)

  **預設值**：停用

- **Internet Explorer 網際網路區域不會對 ActiveX 控制項執行反惡意程式碼軟體**：  
  此原則設定可決定 Internet Explorer 是否會對 ActiveX 控制項執行反惡意程式碼程式，來檢查這些控制項是否可安全載入到頁面。 如果您啟用此原則設定，Internet Explorer 將不會使用您的反惡意程式碼程式，來檢查是否可以安全建立 ActiveX 控制項的執行個體。 如果您停用此原則設定，Internet Explorer 一律會使用您的反惡意程式碼程式，來檢查是否可以安全建立 ActiveX 控制項的執行個體。 如果您未設定此原則設定，Internet Explorer 一律會使用您的反惡意程式碼程式，來檢查是否可以安全建立 ActiveX 控制項的執行個體。 使用者可以透過 Internet Explorer [安全性] 設定來開啟或關閉此行為。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067162)

  **預設**：停用

- **Internet Explorer 網際網路區域透過指令碼複製和貼上**：  
  此原則設定可讓您管理指令碼是否可以在指定區域中執行剪貼簿作業 (例如剪下、複製及貼上)。 如果您啟用此原則設定，指令碼將可以執行剪貼簿作業。 如果您在下拉式方塊中選取 [提示]，則會詢問使用者是否要執行剪貼簿作業。 如果您停用此原則設定，則指令碼無法執行剪貼簿作業。 如果您未設定此原則設定，則指令碼可以執行剪貼簿作業。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067084)

  **預設值**：停用

- **Internet Explorer 使用 ActiveX 安裝程式服務**：  
  此原則設定可讓您指定如何安裝 ActiveX 控制項。 如果您啟用此原則設定，只有在 ActiveX 安裝程式服務存在，且已設定為允許安裝 ActiveX 控制項時，才會安裝 ActiveX 控制項。 如果您停用或未設定此原則設定，則會透過標準安裝程序安裝 ActiveX 控制項 (包括每一使用者控制項)。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067163)

  **預設**：啟用

- **Internet Explorer 處理來自區域高度的保護**：  
  Internet Explorer 會對每個開啟的網頁設定限制。 這些限制會視網頁所在位置而定 (網際網路、內部網路、本機電腦區域等)。 例如，本機電腦上的網頁擁有最少安全性限制且位於本機電腦區域內，使得本機電腦安全性區域成為惡意使用者的主要攻擊目標。 如果您啟用此原則設定，則在所有處理序中，任何區域都可能會受到來自區域高度的保護。 如果您停用或未設定此原則設定，Internet Explorer 或處理序清單所列以外的處理序都不會受到這類保護。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067160)

  **預設**：啟用

- **在 Internet Explorer 網際網路區域中下載未簽署的 ActiveX 控制項**：  
  此原則設定可讓您管理使用者是否可以從區域下載未簽署的 ActiveX 控制項。 這類程式碼可能有害，尤其是來自未受信任區域的程式碼。 如果您啟用此原則設定，使用者無須操作即可執行未簽署的控制項。 如果您在下拉式方塊中選取 [提示]，則會請使用者選擇是否允許執行未簽署的控制項。 如果您停用此原則設定，使用者將無法執行未簽署的控制項。 如果您未設定此原則設定，使用者將無法執行未簽署的控制項。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067325)

  **預設值**：停用

- **Internet Explorer 網際網路區域跨不同網域巡覽視窗和畫面**：  
  此原則設定可讓您管理跨不同網域開啟視窗和畫面以及存取應用程式的作業。 如果您啟用此原則設定，則使用者可以從其他網域開啟視窗和畫面，並存取其他網域中的應用程式。 如果您在下拉式清單方塊中選取 [提示]，即會詢問使用者是否允許開啟視窗和畫面來存取其他網域中的應用程式。 如果您停用此原則設定，使用者將無法開啟視窗和畫面來存取不同網域中的應用程式。 如果您未設定此原則設定，則使用者可以從其他網域開啟視窗和畫面，並存取其他網域中的應用程式。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067083)

  **預設值**：停用

- **Internet Explorer 網際網路區域透過指令碼更新狀態列**：  
  此原則設定可讓您管理指令碼是否可以更新區域內的狀態列。 如果您啟用此原則設定，指令碼可以更新狀態列。 如果您停用或未設定此原則設定，則不允許指令碼更新狀態列。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067087)

  **預設**：停用

- **Internet Explorer 限制區域在上傳檔案至伺服器時包含本機路徑**：  
  此原則設定可控制使用者透過 HTML 表單上傳檔案時是否傳送本機路徑資訊。 如果傳送本機路徑資訊，可能會不小心對伺服器揭露某些資訊。 例如，從使用者桌面傳送之檔案可能包含使用者名稱作為路徑的一部分。 如果您啟用此原則設定，使用者透過 HTML 表單上傳檔案時會傳送路徑資訊。 如果您停用此原則設定，使用者透過 HTML 表單上傳檔案時就會移除路徑資訊。 如果您未設定此原則設定，則使用者可以在透過 HTML 表單上傳檔案時選擇是否傳送路徑資訊。 預設會傳送路徑資訊。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067085)

  **預設**：停用

- **Internet Explorer 處理序限制檔案下載**：  
  此原則設定可讓裝載網頁瀏覽器控制項的應用程式，針對不是由使用者起始的檔案下載封鎖其自動提示。 如果您啟用此原則設定，網頁瀏覽器控制項將會針對不是由使用者為所有處理序起始的檔案下載封鎖其自動提示。 如果您停用此原則設定，網頁瀏覽器控制項就不會針對不是由使用者為所有處理序起始的檔案下載封鎖其自動提示。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067164)

  **預設**：啟用

- **Internet Explorer 限制區域只允許核准的網域使用 ActiveX 控制項**：  
  此原則設定可控制是否提示使用者允許 ActiveX 控制項在非 ActiveX 控制項安裝網站上執行。 如果您啟用此原則設定，則會在可從此區域的網站執行 ActiveX 控制項之前提示使用者。 使用者可以選擇允許控制項從目前的網站或所有網站執行。 如果您停用此原則設定，使用者不會看到每個網站的 ActiveX 提示，且 ActiveX 控制項可以從此區域的所有網站執行。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067233)

  **預設**：啟用

- **Internet Explorer 限制區域初始化未標示為安全的 ActiveX 控制項並對其撰寫指令碼**：  
  此原則設定可讓您管理未標示為安全的 ActiveX 控制項。 如果您啟用此原則設定，不需要設定未受信任資料或指令碼的物件安全性，即可執行 ActiveX 控制項、對其載入參數並撰寫指令碼。 除了安全且受管理的區域之外，不建議使用此設定。 此設定會導致不安全和安全的控制項都會初始化和撰寫指令碼，並忽略 [對標示為安全的 ActiveX 控制項執行指令碼] 選項。 如果您啟用此原則設定並在下拉式方塊中選取 [提示]，則會詢問使用者是否允許對控制項載入參數或撰寫指令碼。 如果您停用此原則設定，則不會對無法標示為安全的 ActiveX 控制項載入參數或撰寫指令碼。 如果您未設定此原則設定，則不會對無法標示為安全的 ActiveX 控制項載入參數或撰寫指令碼。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067097)

  **預設值**：停用

- **Internet Explorer 使用者變更原則**：  
  防止使用者變更安全性區域設定。 安全性區域是一組具有相同安全性等級的網站。 如果您啟用此原則，則會停用 [網際網路選項] 對話方塊中 [安全性] 索引標籤上的 [自訂等級] 按鈕和安全性等級滑桿。 如果您停用或未設定此原則，則使用者可以變更安全性區域的設定。 此原則可防止使用者變更系統管理員所建立的安全性區域設定。 注意：[停用安全性頁面] 原則 (位於 \使用者設定\系統管理範本\Windows 元件\Internet Explorer\網際網路控制台) 可從 [控制台] 的 Internet Explorer 中移除 [安全性] 索引標籤，其優先於此原則。 如果已啟用該原則，則會忽略此原則。 此外，請參閱「安全性區域: 只使用電腦設定」原則。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067155)

  **預設**：停用

- **Internet Explorer 限制區域受保護模式**：  
  此原則設定可讓您開啟受保護模式。 受保護模式會藉由減少 Internet Explorer 可在登錄和檔案系統中寫入的位置，協助保護 Internet Explorer 免於遭受弱點入侵。 如果您啟用此原則設定，就會開啟受保護模式。 使用者無法關閉受保護模式。 如果您停用此原則設定，就會關閉受保護模式。 使用者無法開啟受保護模式。 如果您未設定此原則設定，則使用者可以開啟或關閉受保護模式。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067080)

  **預設值**：啟用

- **Internet Explorer 網際網路區域使用者資料持續性**：  
  此原則設定可讓您管理在瀏覽器歷程記錄、我的最愛、XML 存放區中保留資訊的作業，或是直接在儲存到磁碟之網頁中保留資訊的作業。 當使用者回到保存的頁面時，如果已適當設定此原則設定，則可以還原該頁面的狀態。 如果您啟用此原則設定，使用者可以在瀏覽器歷程記錄、我的最愛、XML 存放區中保留資訊，或是直接在儲存到磁碟的網頁中保留資訊。 如果您停用此原則設定，使用者將無法在瀏覽器歷程記錄、我的最愛及 XML 存放區中保留資訊，或是直接在儲存到磁碟的網頁中保留資訊。 如果您未設定此原則設定，則使用者可以在瀏覽器歷程記錄、我的最愛及 XML 存放區中保留資訊，或是直接在儲存到磁碟的網頁中保留資訊。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067156)

  **預設**：停用

- **Internet Explorer 網際網路區域對網頁瀏覽器控制項執行指令碼**：  
  此原則設定會判斷頁面是否可以透過指令碼控制內嵌的 WebBrowser 控制項。 如果您啟用此原則設定，即允許對 WebBrowser 控制項進行指令碼存取。 如果您停用此原則設定，則不允許對 WebBrowser 控制項進行指令碼存取。 如果您未設定此原則設定，則使用者可以啟用或停用對 WebBrowser 控制項的指令碼存取。 根據預設，只有在本機電腦和內部網路區域中才允許對 WebBrowser 控制項的指令碼存取。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067157)

  **預設**：停用

- **Internet Explorer 限制區域使用者資料持續性**：  
  此原則設定可讓您管理在瀏覽器歷程記錄、我的最愛、XML 存放區中保留資訊的作業，或是直接在儲存到磁碟之網頁中保留資訊的作業。 當使用者回到保存的頁面時，如果已適當設定此原則設定，則可以還原該頁面的狀態。 如果您啟用此原則設定，使用者可以在瀏覽器歷程記錄、我的最愛、XML 存放區中保留資訊，或是直接在儲存到磁碟的網頁中保留資訊。 如果您停用此原則設定，使用者將無法在瀏覽器歷程記錄、我的最愛及 XML 存放區中保留資訊，或是直接在儲存到磁碟的網頁中保留資訊。 如果您未設定此原則設定，使用者將無法在瀏覽器歷程記錄、我的最愛及 XML 存放區中保留資訊，或是直接在儲存到磁碟的網頁中保留資訊。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067081)

  **預設**：停用

- **Internet Explorer 鎖定的內部網路區域 Java 權限**：  
  此原則設定可讓您管理 Java Applet 的權限。 如果您啟用此原則設定，即可從下拉式方塊中選擇選項。 [自訂] 可個別控制權限設定。 [低安全性] 可讓 Applet 執行所有作業。 [中安全性] 可讓 Applet 在其沙箱 (記憶體中無法供外部應用程式呼叫的一個區域) 中執行，以及啟用暫存空間 (用戶端電腦上安全且受保護的存放區域) 和使用者控制的檔案 I/O 等功能。 [高安全性] 可讓 Applet 在其沙箱中執行。 停用 Java 可防止執行任何 Applet。 如果您停用此原則設定，則無法執行 Java Applet。 如果您未設定此原則設定，則會停用 Java Applet。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067082)

  **預設值**：停用 Java

- **Internet Explorer 加強的受保護模式**：  
  加強的受保護模式在 64 位元版本的 Windows 上使用 64 位元處理序，藉此提供額外的保護來防範惡意網站。 對於至少執行 Windows 8 的電腦，加強的受保護模式也會限制 Internet Explorer 可從登錄和檔案系統讀取的位置。 如果您啟用此原則設定，則會開啟加強的受保護模式。 任何已啟用受保護模式之區域將會使用加強的受保護模式。 使用者無法停用加強的受保護模式。 如果您停用此原則設定，則會關閉加強的受保護模式。 啟用受保護模式之所有區域都將使用 Internet Explorer 7 (適用於 Windows Vista) 中所引進的受保護模式版本。 如果您未設定此原則，則使用者可以在 [網際網路選項] 對話方塊的 [進階] 索引標籤中，開啟或關閉加強的受保護模式。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067158)

  **預設**：啟用

- **Internet Explorer 略過 SmartScreen 警告**：  
  此原則設定可決定使用者是否可以略過 SmartScreen 篩選工具的警告。 對於不是 Internet Explorer 使用者經常從網際網路下載的可執行檔，SmartScreen 篩選工具會向使用者發出警告。 如果您啟用此原則設定，SmartScreen 篩選工具警告將會封鎖使用者。 如果您停用或未設定此原則設定，使用者即可略過 SmartScreen 篩選工具警告。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067159)

  **預設**：停用

- **Internet Explorer 限制區域 Meta Refresh**：  
  如果網頁作者使用 [Meta Refresh] 設定 (標記) 將瀏覽器重新導向到其他網頁，此原則設定可讓您管理是否可以將使用者的瀏覽器重新導向到其他網頁。 如果您啟用此原則設定，當使用者瀏覽器載入含有使用中 [Meta Refresh] 設定的網頁時，將可以重新導向到其他網頁。 如果您停用此原則設定，當使用者瀏覽器載入含有使用中 Meta Refresh 設定的網頁時，將無法重新導向到其他網頁。 如果您未設定此原則設定，當使用者瀏覽器載入含有使用中 Meta Refresh 設定的網頁時，將無法重新導向到其他網頁。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067154)

  **預設**：停用

## <a name="local-policies-security-options"></a>本機原則安全性選項

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - LocalPoliciesSecurityOptions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions) (原則 - LocalPoliciesSecurityOptions)。

- **限制具名管道和共用的匿名存取**：  
  啟用時，此安全性設定會限制對共用與管道的匿名存取至下列設定：(1) 可以匿名存取的具名管道 (2) 可以匿名存取的共用。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067212)

  **預設值**：是

- **NTLM SSP 為主之伺服器的最小工作階段安全性**：  
  此安全性設定允許伺服器要求 128 位元加密和 NTLMv2 工作階段安全性的交涉。 這些值相依於 LAN Manager 驗證等級安全性設定值。 選項包括：要求 NTLMv2 工作階段安全性：若未交涉訊息完整性，連線將會失敗。 要求 128 位元加密。 若未交涉增強式加密 (128 位元)，連線將會失敗。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067246)

  **預設**：要求 NTLMv2 和 128 位元加密

- **鎖定畫面閒置，直到螢幕保護裝置啟動的分鐘數**：  
  Windows 會通知登入工作階段處於未使用狀態，如果未使用的時間量超過未使用時間限制，則螢幕保護裝置將會執行，並鎖住該工作階段。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067210)

  **預設**：15

- **要求用戶端一律以數位方式簽署通訊**：  
  此安全性設定可決定網域成員起始的所有安全通道流量是否必須經簽署或加密。 當電腦加入網域時，會建立電腦帳戶。 之後，當系統啟動時，就會使用電腦帳戶密碼為其網域建立一個與網域控制站的安全通道。 此安全通道可用來執行 NTLM 傳遞驗證、LSA SID/名稱查閱等作業。 此設定可決定網域成員起始的所有安全通道流量是否符合最低安全性需求。 具體而言，它可決定網域成員啟動的所有安全通道流量是否必須經簽章或加密。 如果啟用此原則，除非交涉所有安全通道流量的簽章或加密，否則不會建立安全通道。 如果停用此原則，就會與網域控制站交涉所有安全通道流量的加密和簽章；在此情況下，簽章和加密層級取決於網域控制站版本及下列兩項原則的設定：網域成員: 安全通道資料加以數位加密 (可能的話) 網域成員: 安全通道資料加以數位簽章 (自動)。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067187)

  **預設值**：是

- **驗證等級**：  
  此安全性設定可決定用於網路登入的挑戰/回應驗證通訊協定。 此選擇會影響用戶端所使用的驗證通訊協定等級、交涉的工作階段安全性等級，以及伺服器接受的驗證等級，如下所示：

  - 傳送 LM 和 NTLM 回應  - 用戶端使用 LM 和 NTLM 驗證，且絕不使用 NTLMv2 工作階段安全性；網域控制站接受 LM、NTLM 及 NTLMv2 驗證。

  - *傳送 LM 和 ntlm-NTLMv2 （如果已協商*）-用戶端使用 LM 和 ntlm 驗證，並在伺服器支援時使用 ntlmv2 會話安全性。 網域控制站接受 LM、NTLM 及 NTLMv2 驗證。

  - 只傳送 NTLM 回應  - 用戶端只使用 NTLM 驗證，且若伺服器支援，則會使用 NTLMv2 工作階段安全性；網域控制站接受 LM、NTLM 及 NTLMv2 驗證。

  - 只傳送 NTLMv2 回應  - 用戶端只使用 NTLMv2 驗證，且若伺服器支援，則會使用 NTLMv2 工作階段安全性；網域控制站接受 LM、NTLM 及 NTLMv2 驗證。

  - *只傳送 NTLMv2 回應。拒絕 LM*-用戶端只使用 NTLMv2 驗證，並在伺服器支援時使用 NTLMv2 會話安全性。 網域控制站拒絕 LM （只接受 NTLM 與 NTLMv2 驗證）。

  - *只傳送 NTLMv2 回應。拒絕 LM 和 NTLM*-用戶端只使用 NTLMv2 驗證，並在伺服器支援時使用 NTLMv2 會話安全性。 網域控制站會拒絕 LM 和 NTLM （只接受 NTLMv2 驗證）。

  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067189)

  **預設**：只傳送 NTLMv2 回應。 拒絕 LM 和 NTLM

- **防止用戶端將未加密的密碼傳送到協力廠商 SMB 伺服器**：  
  如果啟用此安全性設定，則伺服器訊息區 (SMB) 重新導向程式可將純文字密碼傳送給驗證期間不支援密碼加密的非 Microsoft SMB 伺服器。 傳送未加密的密碼會有安全性風險。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067235)

  **預設值**：是

- **要求伺服器一律數位簽署通訊**：  
  此安全性設定可決定 SMB 用戶端是否會嘗試交涉 SMB 封包簽章。 伺服器訊息區 (SMB) 通訊協定為 Microsoft 檔案及列印共用與許多其他網路作業 (例如遠端 Windows 系統管理) 提供基礎。 為防止會修改傳輸中 SMB 封包的中間人攻擊，SMB 通訊協定支援 SMB 封包的數位簽章。 此原則設定可決定 SMB 用戶端元件在連線到 SMB 伺服器時，是否嘗試交涉 SMB 封包簽章。 如果啟用此設定，Microsoft 網路用戶端將在設定工作階段時，要求伺服器執行 SMB 封包簽署。 如果伺服器上已啟用封包簽署，則會交涉封包簽署。 如果停用此原則，SMB 用戶端絕不會交涉 SMB 封包簽章。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067319)

  **預設值**：是

- **系統管理員提高權限提示行為**：  
  此原則設定可控制系統管理員的提高權限提示行為。 其選項包括：

  - 提高權限而不提示  - 允許特殊權限帳戶執行需要提高權限的作業，無須取得同意或認證。 注意：這個選項只能用於條件最有限的環境中。

  - 在安全桌面提示輸入認證  - 當某個作業需要提高權限時，安全桌面會提示使用者輸入特殊權限使用者名稱和密碼。 如果使用者輸入有效的認證，會利用使用者最高的權限，繼續執行該項作業。

  - 在安全桌面提示要求同意  - 當某個作業需要提高權限時，安全桌面會提示使用者選取 [允許] 或 [拒絕]。 如果使用者選取 [允許]，則會利用使用者最高的權限，繼續執行該項作業。

  - 提示輸入認證  - 當某個作業需要提高權限時，會提示使用者輸入系統管理使用者名稱和密碼。 如果使用者輸入有效的認證，會利用可用的權限，繼續執行該項作業。

  - 提示要求同意  - 當某項作業需要提高權限時，會提示使用者選取 [允許] 或 [拒絕]。 如果使用者選取 [允許]，則會利用使用者最高的權限，繼續執行該項作業。

  - 提示要求同意非 Windows 二進位檔案  - 當非 Microsoft 應用程式的某個作業需要提高權限時，安全桌面會提示使用者選取 [允許] 或 [拒絕]。 如果使用者選取 [允許]，則會利用使用者最高的權限，繼續執行該項作業。

  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067215)

  **預設**：在安全桌面提示要求同意

- **NTLM SSP 為主之用戶端的最小工作階段安全性**：  
  此安全性設定允許用戶端要求 128 位元加密和 NTLMv2 工作階段安全性的交涉。 這些值相依於 LAN Manager 驗證等級安全性設定值。 其選項包括：

  - *要求 NTLMv2 工作階段安全性* - 若未交涉 NTLMv2 通訊協定，連線將會失敗。

  - *要求 128 位元加密* - 若未交涉增強式加密 (128 位元)，連線將會失敗。

  - 要求 NTLMv2 和 128 位元加密  。

  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067324)

  **預設**：要求 NTLM V2 128 加密

- **智慧卡移除行為**：  
  此安全性設定可決定從智慧卡讀卡機中移除登入使用者之智慧卡時會發生的情況。 其選項包括：

  - 沒有動作  。

  - *鎖定工作站* - 移除智慧卡時會鎖定工作站，讓使用者可以離開電腦並隨身帶著智慧卡，並仍維持受保護的工作階段。

  - 強制登出  - 移除智慧卡時，使用者會自動登出。

  - 中斷遠端桌面工作階段的連線  - 移除智慧卡會中斷工作階段的連線，但無需登出使用者。 這可讓使用者插入智慧卡並在稍後繼續工作階段，或在另一部配備智慧卡讀卡機的電腦上，而不需要再次登入。 如果工作階段是本機，則此原則的功能與鎖定工作站相同。

  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067331)

  **預設值**：鎖定工作站

- **封鎖 SAM 帳戶和共用的匿名列舉**：  
  此安全性設定可決定是否允許 SAM 帳戶和共用的匿名列舉。 Windows 允許匿名使用者執行特定活動，例如列舉網域帳戶和網路共用的名稱。 當系統管理員想要授與使用者在受信任網域上的存取權，而該網域不會保持交互信任時，此功能相當方便。 如果您不想要允許 SAM 帳戶和共用的匿名列舉，則將此原則設定為 [是]  。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067191)

  **預設值**：是

- **封鎖使用空白密碼進行遠端登入**：  
  此安全性設定可決定是否可以使用未受密碼保護的本機帳戶，從實體電腦主控台以外的位置登入。 如果啟用，則未受密碼保護的本機帳戶必須使用電腦的鍵盤登入。

  警告  ：不在實際安全位置的電腦一律應該對所有本機使用者帳戶施行強式密碼原則。 否則，可實際存取電腦之任何人都能使用沒有密碼的使用者帳戶登入。 這對可攜式電腦來說尤其重要。

  如果您將此安全性原則套用到 Everyone 群組，則任何人都不能透過遠端桌面服務登入。 此設定對於使用網域帳戶的登入沒有影響。 應用程式若使用遠端互動式登入，則可以略過此設定。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067219)

  **預設值**：是

- **標準使用者提高權限提示行為**：  
  此原則設定可控制標準使用者的提高權限提示行為。

  - 自動拒絕提高權限要求  - 當某個作業需要提高權限時，會顯示可設定的拒絕存取錯誤訊息。 以標準使用者身分執行桌面的企業，可以選擇這項設定，以降低客服中心電話。

  - 在安全桌面提示輸入認證  - 當某個作業需要提高權限時，安全桌面會提示使用者輸入不同的使用者名稱和密碼。 如果使用者輸入有效的認證，會利用可用的權限，繼續執行該項作業。

  - 提示輸入認證  - 當某個作業需要提高權限時，會提示使用者輸入系統管理使用者名稱和密碼。 如果使用者輸入有效的認證，會利用可用的權限，繼續執行該項作業。

  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067183)

  **預設**：自動拒絕提高權限要求

- **需要系統管理員的管理員核准模式**：  
  此原則設定可控制電腦的所有使用者帳戶控制 (UAC) 原則設定行為。 如果您變更此原則設定，就必須重新啟動電腦。 其選項包括：

  - 未設定  - 管理員核准模式及所有相關 UAC 原則設定已停用。 注意：如果停用此原則設定，資訊安全中心會通知您作業系統的整體安全性已降低。

  - *是* - 管理員核准模式已啟用。 此原則必須啟用，且相關的 UAC 原則設定必須適當地設定，這樣內建的 Administrator 帳戶及 Administrators 群組成員的所有其他使用者，才能夠在管理員核准模式下執行。

  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067184)

  **預設值**：是

- **防止 SAM 帳戶的匿名列舉**：  
  此安全性設定可決定將授與電腦匿名連線哪些其他權限。 Windows 允許匿名使用者執行特定活動，例如列舉網域帳戶和網路共用的名稱。 當系統管理員想要授與使用者在受信任網域上的存取權，而該網域不會保持交互信任時，此功能相當方便。 此安全性選項允許在匿名連線中設定其他限制，如下所示：

  - *是* - 不允許列舉 SAM 帳戶。 此選項會將資源安全性權限中的 Everyone 取代為 Authenticated Users。

  - *尚未設定* - 沒有其他限制。 視預設權限而定。

  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067318)

  **預設值**：是

- **允許對安全性帳戶管理員發出遠端呼叫**：  
  此原則設定可讓您限制對 SAM 的遠端 RPC 連線。 如果未選取，則會使用預設安全性描述元。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067209)

  **預設值**：*O:BAG:BAD:(A;;RC;;;BA)*

- **使用管理員核准模式**：  
  此原則設定可控制內建 Administrator 帳戶的管理員核准模式行為。 其選項包括：

  - 是  - 內建的 Administrator 帳戶使用管理員核准模式。 根據預設值，任何需要提高權限的作業會提示使用者核准該作業。

  - 未設定  - 內建的 Administrator 帳戶使用完整系統管理權限執行所有應用程式。

  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067186)

  **預設值**：是
  
- **允許 UI 存取安全位置中的應用程式**：  
  此原則設定可控制使用者介面協助工具 (UIAccess 或 UIA) 程式是否可以為標準使用者所使用的提高權限提示自動停用安全桌面。

  - 是  - UIA 程式 (包括 Windows 遠端協助) 會自動停用提高權限提示的安全桌面。 如果未停用 [使用者帳戶控制: 提示提升權限時切換到安全桌面] 原則設定，該提示就會顯示在互動式使用者桌面，而不是安全桌面。

  - 未設定  - 只有互動式桌面的使用者，或透過停用 [使用者帳戶控制：提示提升權限時切換到安全桌面] 原則設定，才能停用安全桌面。

  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067185)

  **預設值**：是

- **偵測應用程式安裝，並提示提高權限**：  
  此原則設定可控制電腦的應用程式安裝偵測行為。 其選項包括：

  - 啟用  - 偵測到需要提高權限的應用程式安裝套件時，會提示使用者輸入系統管理使用者名稱和密碼。 如果使用者輸入有效的認證，會利用可用的權限，繼續執行該項作業。

  - 停用  - 不會偵測應用程式安裝套件，也不會提示提高權限。 企業執行標準使用者桌面和使用者代理安裝技術，如群組原則軟體安裝或系統管理伺服器 (SMS) 時，應該停用這項原則設定。 在這種情況下，就不需要偵測安裝程式了。

  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067208)

  **預設值**：是

- **防止在下次密碼變更時儲存 LAN Manager 雜湊值**：  
  此安全性設定可決定是否要在下次密碼變更時儲存新密碼的 LAN Manager (LM) 雜湊值。 和密碼編譯較強的 Windows NT 雜湊相比，LM 雜湊相對較不安全，且容易遭到攻擊。 因為 LM 雜湊儲存於本機電腦的安全性資料庫中，若安全性資料庫遭到攻擊，密碼可能就會被破解。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067213)

  **預設值**：是

- **將檔案與登錄寫入失敗虛擬化到各自位置**：  
  此原則設定可控制應用程式寫入失敗是否會重新導向至定義的登錄和檔案系統位置。 此原則設定會抑制以系統管理員身分而執行並將執行資料寫入 *%ProgramFiles%* 、 *%Windir%* 、 *%Windir%\system32* 或 *HKLM\Software* 的應用程式。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067321)

  **預設值**：是

## <a name="ms-security-guide"></a>MS 安全性指南

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide) (原則 CSP - MSSecurityGuide)。

- **登入網路時將 UAC 限制套用至本機帳戶**：  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067188)

  **預設**：啟用

- **SMB v1 用戶端驅動程式啟動設定**：  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067214)

  **預設值**：已停用驅動程式

- **SMB v1 伺服器**：  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067190)

  **預設**：停用

- **摘要式驗證**：  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067193)

  **預設**：停用

- **結構化例外處理覆寫保護**：  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067217)

  **預設**：啟用

## <a name="mss-legacy"></a>MSS 舊版

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy) (原則 CSP - MSSLegacy)。

- **網路 IP 來源路由保護層級**：  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067220)

  **預設值**：最高保護  

- **網路忽略 WINS 伺服器除外的 NetBIOS 名稱發行要求**：  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067218)

  **預設**：啟用

- **網路 IPv6 來源路由保護層級**：  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067216)

  **預設值**：最高保護

- **網路 ICMP 重新導向所產生的覆寫 OSPF**：  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067326)

  **預設**：停用

## <a name="power"></a>電源

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power) (原則 CSP - Power)。

- **插入電源期間喚醒時需要密碼**：  
  此原則設定可指定系統從睡眠狀態中恢復時，是否會提示使用者輸入密碼。 如果您啟用或未設定此原則設定，當系統從睡眠狀態中恢復時，就會提示使用者輸入密碼。 如果您停用此原則設定，當系統從睡眠狀態中恢復時，就不會提示使用者輸入密碼。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067221)

  **預設**：啟用

- **使用電池期間睡眠時進入待命狀態**：  
  此原則設定可管理 Windows 是否可以使用待命狀態讓電腦進入睡眠狀態。 如果您啟用或未設定此原則設定，Windows 將會使用待命狀態讓電腦進入睡眠狀態。 如果您停用此原則設定，則不允許待命狀態 (S1-S3)。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067195)

  **預設**：停用

- **插入電源期間睡眠時進入待命狀態**：  
  此原則設定可管理 Windows 是否可以使用待命狀態讓電腦進入睡眠狀態。 如果您啟用或未設定此原則設定，Windows 將會使用待命狀態讓電腦進入睡眠狀態。 如果您停用此原則設定，則不允許待命狀態 (S1-S3)。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067196)

  **預設**：停用

- **使用電池期間喚醒時需要密碼**：  
  此原則設定可指定系統從睡眠狀態中恢復時，是否會提示使用者輸入密碼。 如果您啟用或未設定此原則設定，當系統從睡眠狀態中恢復時，就會提示使用者輸入密碼。 如果您停用此原則設定，當系統從睡眠狀態中恢復時，就不會提示使用者輸入密碼。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067322)

  **預設**：啟用

::: zone-end
::: zone pivot="mdm-may-2019"

## <a name="remote-assistance"></a>遠端協助

如需詳細資訊，請參閱 Windows 文件中的[原則 CSP - RemoteAssistance](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteassistance#remoteassistance-solicitedremoteassistance) \(部分機器翻譯\)。

- **請求遠端協助**：  
  此原則設定可讓您開啟或關閉這部電腦上的 [請求（詢問）] 遠端協助。
  
  - *如果您啟用此原則設定*，這部電腦上的使用者可以使用電子郵件或檔案傳輸來詢問其他人的協助。 此外，使用者也可以使用立即訊息程式來允許此電腦的連線，而且您可以設定其他遠端協助設定。

  - *如果您停用此原則設定*，這部電腦上的使用者將無法使用電子郵件或檔案傳輸來詢問他人的協助。 此外，使用者也無法使用立即訊息程式來允許連線到這部電腦。

  - *如果您未設定此原則設定*，使用者可以在 [控制台] 的 [系統內容] 中，開啟或關閉 [要求（詢問）] 遠端協助。 使用者也可以設定遠端協助設定。

  如果您啟用此原則設定，您有兩種方式可讓協助專家提供遠端協助：「僅允許協助程式查看電腦」或「允許協助程式遠端控制電腦」。 「最長票證時間」原則設定會設定使用電子郵件或檔案傳輸所建立的遠端協助邀請可以保持開啟的時間長度限制。 「選取傳送電子郵件邀請的方法」設定會指定要使用哪個電子郵件標準來傳送遠端協助邀請。 視您的電子郵件程式而定，您可以使用*Mailto*標準（邀請收件者透過網際網路連結連線）或 SMAPI （簡單 MAPI）標準（邀請會附加至您的電子郵件訊息）。 此原則設定無法在 Windows Vista 中使用，因為 SMAPI 是唯一支援的方法。 如果您啟用此原則設定，您也應該啟用適當的防火牆例外，以允許遠端協助通訊。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067198)

  **預設值**：停用遠端協助

  設定為 [*啟用遠端協助*] 時，請進行下列其他設定：

  - **遠端協助請求的許可權**：  
    **預設值**：檢視

  - **最大票證時間值**：  
    **預設值**：*未設定*

  - **最長票證時間週期**：  
    **預設值**：分鐘

  - **電子郵件邀請方法**：  
    **預設值**：簡單 MAPI

::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

## <a name="remote-desktop-services"></a>遠端桌面服務

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices) (原則 CSP - RemoteDesktopServices)。

- **封鎖密碼儲存**：  
  控制是否可以從遠端桌面連線將密碼儲存在這部電腦上。 如果您啟用此設定，遠端桌面連線的密碼儲存核取方塊會停用，且使用者無法儲存密碼。 當使用者使用遠端桌面連線來開啟 RDP 檔案並儲存其設定時，所有先前存在於 RDP 檔案中的密碼都會予以刪除。 如果您停用此設定或保持未設定，則使用者可以使用遠端桌面連線來儲存密碼。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067301)

   **預設**：啟用

- **安全 RPC 通訊**：  
  指定遠端桌面工作階段主機伺服器需要與所有用戶端進行安全 RPC 通訊，還是允許不安全的通訊。 您可以使用此設定，藉由只允許已驗證及已加密的要求，來加強與用戶端的 RPC 通訊安全性。 如果狀態設定為 [啟用]，遠端桌面服務會接受支援安全要求的 RPC 用戶端所提出要求，且不允許與未受信任用戶端進行不安全的通訊。 如果狀態設定為 [停用]，遠端桌面服務一律會對所有 RPC 流量要求安全性。 不過，如果 RPC 用戶端未回應要求，即允許不安全的通訊。 如果狀態設定為 [未設定]，則允許不安全的通訊。 注意：RPC 介面可用於管理和設定遠端桌面服務。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067248)

  **預設**：啟用

- **封鎖磁碟機重新導向**：  
  此原則設定可指定是否要防止在遠端桌面服務工作階段中對應用戶端磁碟機 (磁碟機重新導向)。 根據預設，RD 工作階段主機伺服器會在連線時自動對應用戶端磁碟機。 對應的磁碟機會以 \<電腦名稱>   上 \<磁碟機代號> 的格式，顯示在檔案總管或電腦的工作階段資料夾樹狀目錄中。 您可以使用此原則設定來覆寫此行為。 如果您啟用此原則設定，則不允許在遠端桌面服務工作階段中進行用戶端磁碟機重新導向，且不允許在執行 Windows Server 2003、Windows 8 和 Windows XP 的電腦上進行剪貼簿檔案複製重新導向。 如果您停用此原則設定，則一律允許用戶端磁碟機重新導向。 此外，如果允許剪貼簿重新導向，則一律允許剪貼簿檔案複製重新導向。 如果您未設定此原則設定，則不會在群組原則層級指定用戶端磁碟機重新導向和剪貼簿檔案複製重新導向。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067197)

  **預設**：啟用

- **連線時提示輸入密碼**：  
  此原則設定可指定遠端桌面服務是否一律會在連線時提示用戶端輸入密碼。 您可以使用此設定，強制對登入遠端桌面服務的使用者提示輸入密碼，即使他們在遠端桌面連線用戶端中已提供密碼也一樣。 根據預設，遠端桌面服務允許使用者透過在遠端桌面連線用戶端中輸入密碼來自動登入。 如果您啟用此原則設定，使用者將無法透過在遠端桌面連線用戶端中提供密碼來自動登入遠端桌面服務。 而是會提示他們輸入密碼進行登入。 如果您停用此原則設定，使用者一律可以透過在遠端桌面連線用戶端中提供密碼來自動登入遠端桌面服務。 如果您未設定此原則設定，則不會在群組原則層級指定自動登入。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067328)

  **預設**：啟用

- **遠端桌面服務用戶端連線加密層級**：  
  指定在遠端桌面通訊協定 (RDP) 連線期間，是否必須使用特定的加密層級，來確保用戶端電腦與 RD 工作階段主機伺服器之間的通訊安全。 當您使用原生 RDP 加密時才適用此原則。 不過，不建議使用原生 RDP 加密 (相對於 SSL 加密)。 此原則不適用於 SSL 加密。 如果您啟用此原則設定，在遠端連線期間，用戶端與 RD 工作階段主機伺服器之間的所有通訊都必須使用此設定中指定的加密方法。 加密層級預設為 [高]。 可用的加密方法如下：

  - 高  - [高] 設定會使用增強式 128 位元加密，來加密從用戶端傳送到伺服器的資料，以及從伺服器傳送到用戶端的資料。 請在只包含 128 位元用戶端 (例如執行遠端桌面連線的用戶端) 的環境中使用此加密層級。 不支援此加密層級的用戶端將無法連線到 RD 工作階段主機伺服器。

  - 用戶端相容  - [用戶端相容] 設定會以用戶端所支援最大金鑰效力來加密用戶端與伺服器之間傳送的資料。 請在所包含用戶端不支援 128 位元加密的環境中使用此加密層級。

  - 低  - [低] 設定只會使用 56 位元加密來加密從用戶端傳送到伺服器的資料。  
  
  如果您停用或未設定此設定，則不會透過群組原則強制執行要對 RD 工作階段主機伺服器遠端連線使用的加密層級。 重要：您可以透過系統密碼編譯來設定 FIPS 合規性。 在群組原則中 (位於 [電腦設定]\[Windows 設定]\[安全性設定]\[本機原則]\[安全性選項] 下)，使用符合 FIPS 規範的演算法來進行加密、雜湊和簽章設定。符合 FIPS 規範的設定會使用 Microsoft 密碼編譯模組，以聯邦資訊處理標準 (FIPS) 140 加密演算法，來加密及解密從用戶端傳送到伺服器的資料，以及從伺服器傳送到用戶端的資料。 請在用戶端與 RD 工作階段主機伺服器之間的通訊需要最高加密層級時使用此加密層級。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067222)

  **預設值**：高

## <a name="remote-management"></a>遠端管理

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement) (原則 CSP - RemoteManagement)。

- **封鎖儲存執行為認證**：  
  用戶端基本驗證。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067300)

  **預設**：啟用

- **基本驗證**：  
  此原則設定可讓您管理 Windows 遠端管理 (WinRM) 服務是否接受來自遠端用戶端的基本驗證。 如果您啟用此原則設定，WinRM 服務會接受來自遠端用戶端的基本驗證。 如果您停用或未設定此原則設定，則 WinRM 服務不會接受來自遠端用戶端的基本驗證。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067223)

  **預設**：停用

- **封鎖用戶端摘要式驗證**：  
  此原則設定可讓您管理 Windows 遠端管理 (WinRM) 用戶端是否使用摘要式驗證。 如果您啟用此原則設定，則 WinRM 用戶端將不會使用摘要式驗證。 如果您停用或未設定此原則設定，則 WinRM 用戶端將會使用摘要式驗證。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067302)

  **預設**：啟用

- **未加密的流量**：  
  此原則設定可讓您管理 Windows 遠端管理 (WinRM) 服務是否透過網路傳送和接收未加密的訊息。 如果您啟用此原則設定，WinRM 用戶端將會透過網路傳送和接收未加密的訊息。 如果您停用或未設定此原則設定，則 WinRM 用戶端只會透過網路傳送或接收加密的訊息。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067226)

  **預設**：停用

- **用戶端未加密的流量**：  
  此原則設定可讓您管理 Windows 遠端管理 (WinRM) 用戶端是否透過網路傳送及接收未加密的訊息。 如果您啟用此原則設定，WinRM 用戶端將會透過網路傳送和接收未加密的訊息。 如果您停用或未設定此原則設定，則 WinRM 用戶端只會透過網路傳送或接收加密的訊息。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067304)

  **預設**：停用

- **用戶端基本驗證**：  
  此原則設定可讓您管理 Windows 遠端管理 (WinRM) 用戶端是否使用基本驗證。 如果您啟用此原則設定，WinRM 用戶端將會使用基本驗證。 如果將 WinRM 設定為使用 HTTP 傳輸，使用者名稱及密碼就會以純文字在網路上傳送。 如果您停用或未設定此原則設定，則 WinRM 用戶端將不會使用基本驗證。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067252)

  **預設**：停用

## <a name="remote-procedure-call"></a>遠端程序呼叫

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall) (原則 CSP - RemoteProcedureCall)。

- **未經驗證的 RPC 用戶端選項**：  
  此原則設定可控制 RPC 伺服器執行階段處理未經驗證的 RPC 用戶端連線到 RPC 伺服器的方式。 此原則設定會影響所有 RPC 應用程式。 在網域環境中，請謹慎使用此原則設定，因為它會影響廣泛的功能，包括群組原則處理本身。 若要還原此原則設定的變更，需要在每部受影響的電腦上手動操作。 請勿將此原則設定套用至網域控制站。 如果您停用此原則設定，RPC 伺服器執行階段會在 Windows 用戶端使用 [已驗證] 值，並在支援此原則設定的 Windows 伺服器版本使用 [無] 值。 如果您未設定此原則設定，則會保持停用。 RPC 伺服器執行階段運作起來，就像是針對 Windows 用戶端使用 [已驗證] 值，並針對支援此原則設定的伺服器 SKU 使用 [無] 值將它啟用。 如果您啟用此原則設定，它會指示 RPC 執行階段限制未經驗證的 RPC 用戶端連線到電腦上執行的 RPC 伺服器。 如果用戶端使用具名管道來與伺服器通訊，或是使用 RPC 安全性，該用戶端會視為已驗證的用戶端。 視您為此原則設定選取的值而定，特別要求可供未經驗證用戶端存取的 RPC 介面可能不受此限制。

  - [無]  允許所有 RPC 用戶端連線到已套用原則設定之電腦上執行的 RPC 伺服器。

  - [已驗證]  只允許已驗證的 RPC 用戶端 (如上述定義) 連線到已套用原則設定之電腦上執行的 RPC 伺服器。 已要求的介面會得到豁免。

  - [已在無例外下驗證]  只允許已驗證的 RPC 用戶端 (如上述定義) 連線到已套用原則設定之電腦上執行的 RPC 伺服器。 不允許例外。 注意：系統必須重新開機才能套用此原則設定。

  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067225)

  **預設值**：已驗證

## <a name="search"></a>搜尋

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - Search](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) (原則 CSP - Search)。

- **停用編製加密項目的索引**：  
  允許或不允許編製項目的索引。 這個參數是針對 Windows 搜尋索引子，它控制是否將編製加密項目的索引，例如 Windows 資訊保護 (WIP) 保護的檔案。 啟用此原則時，會編製 WIP 保護項目的索引，而其相關中繼資料會儲存在未加密的位置。 中繼資料包含像是檔案路徑和修改日期等事項。 停用此原則時，不會編製 WIP 保護項目的索引，且這些項目不會出現在 Cortana 或檔案總管的結果中。 如果裝置上有許多 WIP 保護的媒體檔案，也可能影響相片和 Groove 應用程式的效能。  
  [深入了解]( https://go.microsoft.com/fwlink/?linkid=2067303)

  **預設值**：是

## <a name="smart-screen"></a>Smart Screen

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) (原則 CSP - SmartScreen)。

- **封鎖未經驗證檔案的執行**：  
  防止使用者執行未經驗證的檔案。

  - 未設定  - 員工可以忽略 SmartScreen 警告並執行惡意檔案。

  - 是  - 員工不可忽略 SmartScreen 警告並執行惡意檔案。

  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067228)

  **預設值**：是

- **應用程式和檔案需要 SmartScreen**：  
  允許 IT 系統管理員設定 Windows 的 SmartScreen。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067168)

  **預設值**：是

## <a name="system"></a>System (系統)

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - System](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system) (原則 CSP - System)。

- **系統開機啟動驅動程式初始化**：  
  此原則設定可讓您根據由開機初期啟動的反惡意程式碼開機啟動驅動程式決定的分類，指定要初始化哪些開機啟動驅動程式。 開機初期啟動的反惡意程式碼開機啟動驅動程式針對每個開機啟動驅動程式可傳回下列分類：

  - 良好  - 驅動程式已經過簽署且未遭竄改。

  - 不良  - 驅動程式已識別為惡意程式碼。 我們建議您不要允許初始化已知不良的驅動程式。

  - 不良，但為開機所需  - 驅動程式已識別為惡意程式碼，但電腦必須載入此驅動程式才能成功開機。

  - 不明  - 此驅動程式尚未經由您的惡意程式碼偵測應用程式保證，也尚未經由開機初期啟動的反惡意程式碼開機啟動驅動程式分類。

  如果您啟用此原則設定，您可以選擇下次啟動電腦時要初始化的開機啟動驅動程式。 如果您停用或未設定此原則設定，則會初始化判定為 [良好]、[不明] 或 [不良，但為開機關鍵] 的開機啟動驅動程式，並跳過判定為 [不良] 的驅動程式初始化。 如果您的惡意程式碼偵測應用程式不含開機初期啟動惡意程式碼開機啟動驅動程式，或如果已停用開機初期啟動的反惡意程式碼開機啟動驅動程式，則此設定沒有作用，且會初始化所有的開機啟動驅動程式。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067307)

  **預設**：良好、不明及不良但關鍵

## <a name="wi-fi"></a>Wi-Fi

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - Wifi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) (原則 CSP - Wifi)。

- **禁止網際網路共用**：  
  指定是否可以在裝置上共用網際網路。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067327)

  **預設值**：是

- **封鎖自動連線到 Wi-Fi 熱點**：  
  允許或不允許裝置自動連線到 Wi-Fi 熱點。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067320)

  **預設值**：是

## <a name="windows-connection-manager"></a>Windows 連線管理員

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager) (原則 CSP - WindowsConnectionManager)。

- **封鎖連線到非網域網路**：  
  此原則設定可防止電腦同時連線到網域型網路和非網域型網路。 如果啟用此原則設定，電腦會依據下列情況，回應自動及手動網路連線嘗試：

  - 自動連線嘗試  - 當電腦已經連線到網域型網路時，會封鎖連線到非網域型網路的所有自動連線嘗試。 當電腦已經連線到非網域型網路時，會封鎖連線到網域型網路的自動連線嘗試。

  - 手動連線嘗試  - 當電腦已經透過非乙太網路的媒體連線到非網域型網路或網域型網路，且使用者嘗試違反此原則設定來建立連線到其他網路的手動連線時，現有的網路連線會中斷，並允許手動連線。 當電腦已經透過乙太網路連線到非網域型網路或網域型網路，而且使用者嘗試違反此原則設定來建立連線到其他網路的手動連線時，會維持現有的乙太網路連線，而封鎖手動連線嘗試。

  如果未設定或停用此原則設定，則允許電腦同時連線到網域及非網域網路。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067323)

  **預設**：啟用

## <a name="microsoft-defender"></a>Microsoft Defender

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) (原則 CSP - Defender)。

- **掃描內送郵件訊息**：  
  允許或不允許掃描電子郵件。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067116)

  **預設值**：是

- **Office 應用程式啟動子處理序類型**：  
  不允許 Office 應用程式建立子處理序。 這包括 Word、Excel、PowerPoint、OneNote 和 Access。 這是典型的惡意程式碼行為，特別是針對試圖使用 Office 應用程式啟動或下載惡意可執行檔的巨集型攻擊。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067121)

  **預設值**：封鎖

- **Defender 範例提交同意類型**：  
  檢查 Microsoft Defender 中針對傳送資料的使用者同意層級。 如果已獲得必要的同意，Microsoft Defender 將會提交同意。 如果沒有 (而且指定了一律不再詢問使用者)，您可以啟動 UI，要求使用者同意 (允許 Defender/AllowCloudProtection 時) 再傳送資料。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067131)

  **預設**：自動傳送安全的範例

- **病毒碼更新間隔 (小時)** ：  
  Defender 特徵碼更新間隔 (小時)。

  **預設**：4

- **指令碼下載的承載執行類型**：  
  Defender 指令碼下載的承載執行類型。

  **預設值**：封鎖
  
- **防止認證竊取類型**：  
  Microsoft Defender Credential Guard 使用以虛擬化為基礎的安全性來隔離祕密，只有具特殊權限的系統軟體才能進行存取。 未經授權存取這些機密資料可能會導致認證竊取攻擊，例如傳遞雜湊或傳遞票證。 Microsoft Defender Credential Guard 會保護 NTLM 密碼雜湊、Kerberos 票證授權票證及應用程式儲存為網域認證的認證，以防止這些攻擊。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067065)
  
  **預設值**：啟用

- **電子郵件內容執行類型**：  
  此規則會封鎖下列檔案類型，使它們無法執行或從 Microsoft Outlook 或 Web 郵件 (例如 Gmail.com 或 Outlook.com) 中的電子郵件啟動：可執行檔 (例如 .exe、.dll 或 .scr) 指令碼檔案 (例如 PowerShell .ps、VisualBasic .vbs 或 JavaScript .js 檔案) 指令碼封存檔案。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067063)

  **預設值**：封鎖

::: zone-end
::: zone pivot="mdm-may-2019"

- **Adobe Reader 在子處理序中啟動**：  
  **預設值**：啟用

::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

- **網路保護**：  
  此原則可讓您在 Microsoft Defender 惡意探索防護中，開啟或關閉網路保護 (封鎖/稽核)。 網路保護是 Microsoft Defender 惡意探索防護的一個功能，可防止使用任何應用程式的員工存取網路釣魚詐騙、裝載入侵程式網站及網際網路上的惡意內容。 這包括防止第三方瀏覽器連線到危險的網站。 值類型是整數。 如果您啟用此設定，則會開啟網路保護，且員工無法將它關閉。 其行為可透過下列選項來控制：[封鎖] 和 [稽核]。 如果您使用 [封鎖] 選項來啟用此原則，則會防止使用者和應用程式連線到危險的網域。 您可以在 Microsoft Defender 資訊安全中心看到此活動。 如果您使用 [稽核] 選項來啟用此原則，則不會防止使用者/應用程式連線到危險的網域。 不過，您仍然會在 Microsoft Defender 資訊安全中心看到此活動。 如果您停用此原則，則不會防止使用者/應用程式連線到危險的網域。 您不會在 Microsoft Defender 資訊安全中心看到任何網路活動。 如果您未設定此原則，預設會停用網路封鎖。  
  [深入了解](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/enable-network-protection)

  **預設值**：啟用

- **Defender 排程掃描日**：  
  Defender 排程掃描日。

  **預設值**：每天

- **雲端提供的保護**：  
  為加強對電腦的保護，Microsoft Defender 會將找到的任何問題相關資訊傳送給 Microsoft。 Microsoft 將分析該資訊、深入了解影響您與其他客戶的問題，並提供改善的解決方案。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067039)

  **預設值**：是  

- **Defender 潛在的垃圾應用程式動作**：  
  Microsoft Defender 防毒軟體中潛在的垃圾應用程式 (PUA) 防護功能可以識別 PUA，並防止將它下載並安裝到您網路中的端點。 這些應用程式不會視為病毒、惡意程式碼或其他類型的威脅，但可能會在端點上執行對其效能或使用造成不良影響的動作。 PUA 也可能是指那些評價不佳的應用程式。 典型 PUA 行為包括：各種綑綁 AD 並會將其插入網頁瀏覽器的軟體。偵測問題的驅動程式與登入最佳化程式，此類程式會要求付款以修正錯誤，但仍存在於端點且沒有進行任何變更或最佳化 (亦稱為「流氓防毒」程式)。 這些應用程式會造成您網路受惡意程式碼感染的風險變高、導致更難找出惡意程式碼，而且會使得 IT 資源浪費在清除這些應用程式上。  
  [深入了解](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection)

  **預設值**：封鎖  

- **撰寫混淆的巨集程式碼類型**：  
  惡意軟體和其他威脅可能會在某些指令檔中，嘗試混淆或隱藏其惡意程式碼。 此規則可防止看似混淆的指令碼執行。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067026)

  **預設值**：封鎖

- **在完整掃描期間掃描抽取式磁碟機**：  
  允許 Microsoft Defender 在完整掃描期間，掃描抽取式磁碟機 (例如快閃磁碟機) 中是否有惡意和垃圾軟體。 Microsoft Defender 防毒軟體會掃描 USB 裝置上的所有檔案，再執行這些檔案。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067036)

  **預設值**：是  

- **掃描封存檔**：  
  Defender 會掃描封存檔案。

  **預設值**：是

- **行為監視**：  
  允許或禁止 Microsoft Defender 行為監視功能。 這些內建在 Windows 10 中的感應器可以收集並處理作業系統的行為訊號，並將此感應器資料傳送至您私人獨立的 Microsoft Defender ATP 雲端執行個體。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067111)

  **預設值**：是

- **掃描從網路資料夾中開啟的檔案**：  
  如果檔案是唯讀的，使用者將無法移除任何偵測到的惡意程式碼。

  **預設值**：是

- **不受信任的 USB 處理序類型**：  
  透過此規則，系統管理員可以防止從 USB 抽取式磁碟機 (包括 SD 記憶卡) 執行未簽署或未受信任的可執行檔。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067100)

  **預設值**：封鎖

- **Office 應用程式的其他處理序插入類型**：  
  Office 應用程式 (包括 Word、Excel、PowerPoint 和 OneNote) 無法將程式碼插入其他處理序。 惡意軟體通常會利用這點來執行惡意程式碼，試圖隱藏活動不讓防毒掃描引擎發現。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067019)

  **預設值**：封鎖

- **Office 巨集程式碼允許 Win32 匯入類型**：  
  惡意程式碼可能會利用 Office 檔案中的巨集程式碼來匯入及載入 Win32 DLL，這些 DLL 可用來進行 API 呼叫，允許進一步感染整個系統。 此規則會嘗試封鎖包含可匯入 Win32 Dll 之宏程式碼的 Office 檔案。 這包括 Word、Excel、PowerPoint 和 OneNote。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067130)

  **預設值**：封鎖

- **Defender 雲端封鎖層級**：  
  Defender 雲端封鎖層級。

  **預設值**：尚未設定

- **即時監視**：  
  Defender 需要即時監視。

  **預設值**：是

::: zone-end
::: zone pivot="mdm-may-2019"

- **Office 通訊應用程式在子處理序中啟動**：  
  **預設值**：啟用

::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

- **Office 應用程式可執行的內容建立或啟動類型**：  
  此規則會將目標鎖定在可疑且惡意附加元件和指令碼 (延伸模組) 為建立或啟動可執行檔所使用的典型行為。 這是典型的惡意軟體手段。 延伸模組會被封鎖而無法供 Office 應用程式使用。 一般而言，這些延伸模組會使用 Windows Scripting Host (.WSH 檔案) 執行指令碼，來將特定工作自動化或提供使用者建立的附加元件功能。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067108)

  **預設值**：封鎖

::: zone-end
::: zone pivot="mdm-may-2019"

## <a name="microsoft-defender-firewall"></a>Microsoft Defender 防火牆

如需詳細資訊，請參閱 Windows 通訊協定檔中的[2.2.2 FW_PROFILE_TYPE]( https://docs.microsoft.com/openspecs/windows_protocols/ms-fasp/7704e238-174d-4a5e-b809-5f3787dd8acc) 。

- **防火牆設定檔網域**：  
  指定規則所屬設定檔：網域、私人、公用。 此值代表連結到網域之網路的設定檔。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2066796)

  - **已封鎖輸入連線**：  
    **預設值**：是

  - **需要輸出連線**：  
    **預設值**：是

  - **已封鎖輸入通知**：  
    **預設值**：是

  - **已啟用防火牆**：  
    **預設值**：允許

- **防火牆設定檔公用**：  
  指定規則所屬設定檔：網域、私人、公用。 此值代表公用網路的設定檔。 這些網路是由系統管理員在伺服器主機中分類為公用。 主機第一次連線到網路時即會進行分類。 這些網路通常位於機場、咖啡廳與其他公共場所，其中網路中的同儕節點或網路系統管理員不受信任。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067143)

  - **已封鎖輸入連線**：  
    **預設值**：是

  - **需要輸出連線**：  
    **預設值**：是

  - **已封鎖輸入通知**：  
    **預設值**：是

  - **已啟用防火牆**：  
    **預設值**：允許

  - **來自群組原則的連線安全性規則已合併**：  
    **預設值**：是

  - **來自群組原則的原則規則已合併**：  
    **預設值**：是

- **防火牆設定檔私**用：  
  指定規則所屬設定檔：網域、私人、公用。 此值代表私人網路的設定檔。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067041)

  - **已封鎖輸入連線**：  
    **預設值**：是

  - **需要輸出連線**：  
    **預設值**：是

  - **已封鎖輸入通知**：  
    **預設值**：是

  - **已啟用防火牆**：  
    **預設值**：允許

## <a name="windows-hello-for-business"></a>Windows Hello 企業版

- **要求使用進階防詐騙 (如可使用)** ：

  如果是，裝置會使用增強的防詐騙功能（如果有的話）。 若為否，將會封鎖反詐騙。 [未設定] 會接受在用戶端上完成的設定。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067192)

  **預設值**：是

- **設定 Windows Hello 企業版**

  Windows Hello 企業版是一種能取代密碼、智慧卡及虛擬智慧卡來登入 Windows 的方法。

  > [!IMPORTANT]
  > 此設定的選項會反轉其隱含意義。 相反地，值為 *[是]* 並不會啟用 Windows Hello，而是會被視為*未設定*。 當此設定設為 [*未*設定] 時，會在接收此基準的裝置上啟用 Windows Hello。
  >
  > 下列說明已修訂以反映此行為。 在未來的此安全性基準更新中，將會修正設定的反轉。

  - 當設定為 [*未*設定] 時，會啟用 windows hello，而裝置會布建 Windows Hello 企業版。
  - 設定為 *[是]* 時，基準不會影響裝置的原則設定。 這表示如果裝置上的 Windows Hello 企業版已停用，它就會保持停用狀態。 如果已啟用，則會保持啟用狀態。
  <!-- expected behavior 
  - When set to *Yes*, you  enable this policy and the device provisions Windows Hello for Business.  
  - When set to *Not configured*, the baseline does not affect the policy setting of the device. This means that if Windows Hello for Business is disabled on a device, it remains disabled. If its enabled, it remains enabled. 
  -->

  您無法透過此基準停用 Windows Hello 企業版。 您可以在設定[windows 註冊](windows-hello.md)時停用 Windows Hello 企業版，或做為身分[識別保護](identity-protection-configure.md)裝置設定檔的一部分。  

  **預設值**：是

- **PIN 中需要有小寫字母**：  
  如有需要，使用者 PIN 必須至少包含一個小寫字母。

  **預設值**：允許

- **PIN 中需要有特殊字元**：  
  如有需要，使用者 PIN 必須至少包含一個特殊字元。

  **預設值**：允許

- **PIN 長度下限**：  
  PIN 長度下限必須介於4到127之間。

  **預設值**：6

- **PIN 中需要有大寫字母**：  
  如有需要，使用者 PIN 必須至少包含一個大寫字母。

  **預設值**：允許

::: zone-end
::: zone pivot="mdm-preview,mdm-may-2019"

## <a name="windows-ink-workspace"></a>Windows Ink 工作區

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) (原則 CSP - WindowsInkWorkspace)。

- **Ink 工作區**：  
  指定是否允許使用者存取 Ink 工作區。

  - 停用  - 停用 Ink 工作區的存取。 這會關閉功能。

  - 啟用  - 開啟 Ink 工作區功能，但使用者無法在鎖定畫面上存取它。

  - *尚未設定* - 開啟 Ink 工作區功能，而且使用者可以在鎖定畫面上存取它。

  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067241)

  **預設**：啟用

## <a name="windows-powershell"></a>Windows PowerShell

如需詳細資訊，請參閱 Windows 文件中的 [Policy CSP - WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell) (原則 CSP - WindowsPowerShell)。

- **PowerShell Shell 指令碼區塊記錄**：  
  此原則設定可將所有的 PowerShell 指令碼輸入記錄到 Microsoft-Windows-PowerShell/Operational 事件記錄檔。 如果您啟用此原則設定，Windows PowerShell 將會記錄命令、指令碼區塊、函式和指令碼的處理，而不論是以互動方式或透過自動化叫用。 如果您停用此原則設定，則會停用 PowerShell 指令碼輸入的記錄功能。 如果您啟用指令碼區塊引動過程記錄，PowerShell 會額外記錄命令、指令碼區塊、函式或指令碼啟動或停止時的事件。 啟用引動過程記錄會產生大量的事件記錄檔。 注意：群組原則編輯器的 [電腦設定] 和 [使用者設定] 下都有此原則設定。 [電腦設定] 原則設定會優先於 [使用者設定] 原則設定。  
  [深入了解](https://go.microsoft.com/fwlink/?linkid=2067330)

  **預設**：啟用

::: zone-end
::: zone pivot="mdm-may-2019"

## <a name="whats-changed-in-the-new-template"></a>新範本的變更內容

*5 月2019範本的 MDM 安全性基準*具有來自*預覽*範本的下列變更。

### <a name="changes-to-the-baseline-settings"></a>基準設定的變更

下列設定是：

- 此最新版本基準的*新*功能。
- *已*從這個最新的基準版本中移除，但存在於之前的版本中。
- 從設定在舊版中的顯示方式進行*修訂*。

*[新增]* [**上方鎖定**](#above-lock)：

- **語音從鎖定的畫面啟用應用程式**

*[新]* [**應用程式管理**](#application-management)：

- **封鎖使用者對安裝的控制**
- **以更高的許可權封鎖 MSI 應用程式安裝**

*[已移除]* [**BitLocker**](#bitlocker)：

- BitLocker 卸載式磁片磁碟機原則 >**加密方法**
- **BitLocker 固定磁片磁碟機原則** *（所有設定）*
- **BitLocker 系統磁片磁碟機原則** *（所有設定）*

*[新]* [**連線能力**](#connectivity)：

- **設定對 UNC 路徑的安全存取**

*[新]* [**Device Guard**](#device-guard)：

- **虛擬化型安全性**

*[新增]* [**DMA Guard**](#dma-guard)：

- **列舉與 Kernel DMA Protection 不相容的外部裝置**

*[新]* [**Internet Explorer**](#internet-explorer)：

- **Internet Explorer 網際網路區域透過指令碼更新狀態列**
- **Internet Explorer 網際網路區域拖放或複製並貼上檔案**
- **Internet Explorer 受限區域 .NET Framework 相依元件**
- **Internet Explorer 本機電腦區域不會對 ActiveX 控制項執行反惡意程式碼軟體**
- **Internet Explorer 加密支援**

*[已修訂]* [**Internet Explorer**](#internet-explorer)：

- **Internet Explorer 網際網路區域自動提示檔案下載**> 預設值現在已**停用**。 在預覽中，這項設定設為 [已啟用]。

*[新]* [**遠端協助**](#remote-assistance)：

- **要求的遠端協助**
  - **遠端協助請求許可權**
  - **最大票證時間值**
  - **最長票證時間週期**
  - **電子郵件邀請方法**

*[新增]* [**Microsoft Defender**](#microsoft-defender)：

- **Adobe Reader 在子處理序中啟動**
- **Office 通訊應用程式在子處理序中啟動**

*[新增]* [**Microsoft Defender 防火牆**](#microsoft-defender-firewall)

- **防火牆設定檔網域**
  - **已封鎖輸入連線**
  - **需要輸出連線**
  - **已封鎖輸入通知**
  - **已啟用防火牆**
- **防火牆設定檔公用**
  - **已封鎖輸入連線**
  - **需要輸出連線**
  - **已封鎖輸入通知**
  - **已啟用防火牆**
  - **來自群組原則的連線安全性規則已合併**
  - **來自群組原則的原則規則已合併**
- **防火牆設定檔私人**
  - **已封鎖輸入連線**
  - **需要輸出連線**
  - **已封鎖輸入通知**
  - **已啟用防火牆**

*[新]* [**Windows Hello 企業版**](#windows-hello-for-business)：

- **要求使用進階防詐騙 (如可使用)** ：
- **設定 Windows Hello 企業版**
- **PIN 中需要有小寫字母**
- **PIN 中需要有特殊字元**
- **PIN 長度下限**
- **PIN 中需要有大寫字母**

::: zone-end
