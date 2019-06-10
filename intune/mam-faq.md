---
title: MAM 和應用程式保護的相關常見問題
description: 本文章提供 Intune 行動應用程式管理 (MAM) 與 Intune 應用程式保護相關常見問題的解答。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 06/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 149def73-9d08-494b-97b7-4ba1572f0623
ms.reviewer: erikre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9884f1c5d794b527aeaf8fb522d9118d59468b3b
ms.sourcegitcommit: 095fd4c324850aae8ebe32be43fa074361816a4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66506890"
---
# <a name="frequently-asked-questions-about-mam-and-app-protection"></a>MAM 和應用程式保護的相關常見問題

本文章提供 Intune 行動應用程式管理 (MAM) 與 Intune 應用程式保護相關常見問題的解答。

## <a name="mam-basics"></a>MAM 基本概念

**什麼是 MAM？**<br></br>
[Intune 行動應用程式管理](/intune/app-lifecycle)指的是 Intune 管理功能套件，可讓您針對您的使用者發行、推送、設定、保護、監視與更新行動應用程式。

**MAM 應用程式保護的優點有哪些？**<br></br>
MAM 可保護應用程式內組織的資料。 透過不需註冊的 MAM (MAM-WE)，包含機密資料的工作或學校相關應用程式幾乎可在任何裝置上管理，包含攜帶您自己的裝置 (BYOD) 案例中的個人裝置。 許多生產力應用程式 (例如 Microsoft Office 應用程式) 可以由 Intune MAM 管理。 請參閱可供公開使用的 [Intune 受控應用程式](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)官方清單。

**MAM 支援哪些裝置組態？**<br></br>
Intune MAM 支援兩個組態︰
- **Intune MDM + MAM**：IT 系統管理員只能管理已在 Intune 行動裝置管理 (MDM) 註冊之裝置上使用 MAM 與應用程式保護原則的應用程式。 若要使用 MDM + MAM 管理應用程式，客戶應該在 Azure 入口網站中使用 Intune 主控台，網址為 [https://portal.azure.com](https://portal.azure.com)。

- **沒有裝置註冊的 MAM**：沒有裝置註冊的 MAM (或 MAM-WE) 允許 IT 系統管理員管理未在 Intune MDM 註冊之裝置上使用 MAM 與應用程式保護原則的應用程式。 這表示應用程式可由向協力廠商 EMM 提供者註冊之裝置上的 Intune 來管理。 若要使用 MAM-WE 管理應用程式，客戶應該在 Azure 入口網站中使用 Intune 主控台，網址為 [https://portal.azure.com](https://portal.azure.com)。 此外，向協力廠商企業行動管理 (EMM) 提供者註冊的裝置，或是完全不註冊 MDM 的裝置，也可使用 Intune 來管理應用程式。


## <a name="app-protection-policies"></a>應用程式防護原則

**什麼是應用程式保護原則？**<br></br>
應用程式保護原則是確保組織資料能夠在受管理的應用程式中保持安全或受到管制的規則。 原則可以是在使用者嘗試存取或移動「公司」資料時，強制執行的一項規則，或者是當使用者在應用程式內時，禁止執行或受到監視的一組動作。

**應用程式保護原則的範例有哪些？**<br></br>
如需每個應用程式保護原則設定的詳細資訊，請參閱 [Android 應用程式保護原則設定](app-protection-policy-settings-android.md)和 [iOS 應用程式保護原則設定](app-protection-policy-settings-ios.md)。

**可能會針對不同的裝置，同時將 MDM 與 MAM 原則套用至相同使用者嗎？例如，假設使用者能夠從他們自己已啟用 MAM 的機器中存取工作資源，同時也要開始處理並使用 Intune MDM 管理的裝置。針對此想法是否有任何需要注意的事項？**<br></br>
如果您在未設定裝置狀態的情況下將 MAM 原則套用至使用者，則使用者將在 BYOD 裝置和 Intune 管理的裝置上取得 MAM 原則。 您也可以根據受控狀態來套用 MAM 原則。 因此，當您建立應用程式保護原則時，要在所有應用程式類型的目標旁邊選取 [否]。 接著，執行下列其中一項動作：
- 將較不嚴格的 MAM 原則套用至 Intune 管理的裝置，並將較嚴格的 MAM 原則套用至非 MDM 註冊的裝置。
- 僅將 MAM 原則套用至未註冊的裝置。

如需詳細資料，請參閱[如何監視應用程式保護原則](app-protection-policies-monitor.md)。

## <a name="apps-you-can-manage-with-app-protection-policies"></a>您可以使用應用程式保護原則管理的應用程式

**應用程式保護原則可以管理哪些應用程式？**<br></br>
與 [Intune App SDK](/intune/app-sdk) 整合或由 [Intune App Wrapping Tool](/intune/apps-prepare-mobile-application-management) 包裝的應用程式，都可以使用應用程式保護原則加以管理。 請參閱可供公開使用的 [Intune 受控應用程式](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)官方清單。

**在 Intune 受控應用程式上，使用應用程式保護原則的基本需求為何？**

- 終端使用者必須擁有 Azure Active Directory (AAD) 帳戶。 請參閱[新增使用者並提供管理權限給 Intune](/intune/users-permissions-add)，以了解如何在 Azure Active Directory 中建立 Intune 使用者。

- 終端使用者必須擁有指派給其 Azure Active Directory 帳戶的 Microsoft Intune 授權。 請參閱[管理 Intune 授權](/intune/licenses-assign)，以了解如何將 Intune 授權指派給終端使用者。

- 終端使用者必須隸屬於由應用程式保護原則設為目標的安全性群組。 相同的應用程式保護原則必須將已使用的特定應用程式設為目標。 應用程式保護原則可在 [Azure 入口網站](https://portal.azure.com)中的 Intune 主控台中建立與部署。 安全群組目前可在 [Microsoft 365 糸統管理中心](https://admin.microsoft.com)內建立。

- 終端使用者必須使用其 AAD 帳戶來登入應用程式。

**如果我想要搭配 Intune 應用程式防護啟用應用程式，但它並沒有使用支援的應用程式開發平台時該怎麼辦？** 

Intune SDK 開發小組會針對搭配原生 Android、iOS (Obj-C、Swift)、Xamarin、Xamarin.Forms 及 Cordova 平台所建置的應用程式，主動地進行測試並維護支援。 雖然有部分客戶成功搭配其他平台 (例如 React Native 和 NativeScript) 整合 Intune SDK，我們並沒有針對使用我們所不支援之平台的應用程式開發人員提供明確的指引或外掛程式。

**Intune APP SDK 支援 Microsoft 驗證程式庫 (MSAL) 或社交帳戶？**<br></br>
Intune APP SDK 會針對第一方及協力廠商 SDK 版本使用部分進階 ADAL 功能。 因此，MSAL 並不適用於我們的許多核心案例，例如向 Intune 應用程式防護服務進行驗證，以及條件式啟動。 有鑑於來自 Microsoft 身分識別小組的整體指示是要將所有 Microsoft Office 應用程式切換至 MSAL，Intune SDK 未來一定會需要支援它，但目前尚未有確切計畫。

**使用 [Outlook 行動裝置應用程式 (英文)](https://products.office.com/outlook) 時有哪些其他需求？**

- 終端使用者必須在其裝置上安裝 Outlook 行動裝置應用程式。

- 終端使用者必須具有連結到其 Azure Active Directory 帳戶的 [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online) 信箱和授權。

  >[!NOTE]
  > Outlook 行動應用程式目前僅針對 Microsoft Exchange Online 和[具有混合式新式驗證的 Exchange Server](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx) 支援「Intune 應用程式防護」，而不支援「Office 365 專用」中的 Exchange。

**使用 [Word、Excel 與 PowerPoint](https://products.office.com/business/office) 應用程式時有哪些其他需求？**

- 終端使用者必須擁有連結到其 Azure Active Directory 帳戶的 [Office 365 商務版或企業版](https://products.office.com/business/compare-more-office-365-for-business-plans)授權。 訂用帳戶必須包括行動裝置版 Office 應用程式，而且可以包括可搭配[商務用 OneDrive](https://onedrive.live.com/about/business/) 使用的雲端儲存體帳戶。 Office 365 授權可在 [Microsoft 365 系統管理中心](https://admin.microsoft.com)內遵循下列[指示](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc)指派。

- 終端使用者必須有受控的位置，此位置是使用 [不可進行另存新檔] 應用程式保護原則設定下的細微另存新檔功能設定的。 例如，若受控位置是 OneDrive，則 [OneDrive](https://onedrive.live.com/about/) 應用程式應該在終端使用者的 Word、Excel 或 PowerPoint 應用程式中設定。

- 若受控位置是 OneDrive，則應用程式必須是部署到終端使用者之應用程式保護原則的目標。

  >[!NOTE]
  > Office 行動裝置應用程式目前僅支援 SharePoint Online，不支援 SharePoint 內部部署。

**Office 為何需要受控位置 (例如 OneDrive)？**<br></br>
Intune 會將應用程式中所有資料標示為「公司」或「個人」。 當資料來自公司地點時，會將資料視為「公司」資料。 針對 Office 應用程式，Intune 會將下列位置視為公司地點：電子郵件 (Exchange) 或雲端儲存體 (包含商務用 OneDrive 帳戶的 OneDrive 應用程式)。

**使用商務用 Skype 有哪些其他需求？**<br></br>
請參閱[商務用 Skyp](https://products.office.com/skype-for-business/it-pros) 授權需求。 如需商務用 Skype (SfB) 的混合式和內部部署設定，請分別參閱 [Hybrid Modern Auth for SfB and Exchange goes GA](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Hybrid-Modern-Auth-for-SfB-and-Exchange-goes-GA/ba-p/134756) (正式推出適用於 SfB 和 Exchange 的混合式新式驗證) 和 [Modern Auth for SfB OnPrem with AAD](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Modern-Auth-for-SfB-OnPrem-with-AAD/ba-p/180910) (使用 AAD 啟用適用於 SfB 內部部署的新式驗證)。

## <a name="app-protection-features"></a>應用程式保護功能

**什麼是多重身分識別支援？**<br></br>
多重身分識別支援是 Intune App SDK 僅將應用程式保護原則套用至已登入應用程式之工作或學校帳戶的功能。 如果個人帳戶已登入應用程式，就不會更動資料。

**多重身分識別支援的用途為何？**<br></br>
多重身分識別支援允許公開發行同時包含「公司」與消費者對象的應用程式 (例如，Office 應用程式)，並且讓「公司」帳戶具有 Intune 應用程式保護功能。

**Outlook 以及多重身分識別呢？**<br></br>
因為 Outlook 有合併個人與「公司」電子郵件的電子郵件檢視，所以 Outlook 應用程式會在啟動時提示 Intune PIN。

**什麼是 Intune 應用程式 PIN？**<br></br>
個人識別碼 (PIN) 是一組密碼，用來驗證在應用程式中存取組織資料的是正確的使用者。

- **何時會提示使用者輸入 PIN？**<br></br> Intune 會在使用者要存取「公司」資料時，提示使用者提供應用程式 PIN。 在多重身分識別應用程式 (例如 Word/Excel/PowerPoint) 中，系統會在使用者嘗試開啟「公司」文件或檔案時提示他們提供 PIN。 在單一身分識別應用程式 (例如，使用 Intune App Wrapping Tool 管理的企業營運應用程式) 中，會在啟動時提示提供 PIN，因為 Intune App SDK 知道使用者一定是在「公司」環境中使用應用程式。

- **使用者收到 Intune PIN 提示的頻率為何？**<br></br> IT 系統管理員可以在 Intune 管理主控台中定義 Intune 應用程式保護原則設定「重新檢查存取需求前的剩餘時間 (分鐘)」。 這項設定會指定多久之後要在裝置上檢查存取要求，並再次顯示應用程式 PIN 畫面。 不過，還有下列關於 PIN 的重要詳細資料會影響使用者收到通知的頻率： 

    - **PIN會在相同發行者的應用程式間共用，以改進可用性：** 在 iOS 上，應用程式個人識別碼會在**相同應用程式發行者**的所有應用程式之間共用。 在 Android，一組應用程式 PIN 會在所有應用程式間共用。
    - **裝置重新開機後「重新檢查存取需求前等候時間 (分鐘)」行為：** [PIN 計時器] 會追蹤非使用狀態的分鐘數，可判斷何時顯示下一個 Intune 應用程式個人識別碼。 在 iOS 上，PIN 計時器不會受到裝置重新開機的影響。 因此，裝置重新啟動不會影響使用者在使用 Intune PIN 原則的 iOS 應用程式中閒置的分鐘數。 在 Android 上，PIN 計時器會在裝置重新開機時重設。 因此，使用 Intune PIN 原則的 Android 應用程式可能會提示輸入應用程式 PIN，而不論**裝置重新開機之後**的「重新檢查存取需求前的剩餘時間 (分鐘)」設定值。  
    - **與 PIN 相關的計時器過時性質：** 在輸入 PIN 以存取應用程式 (應用程式 A) 之後，應用程式會離開裝置的前景 (主要輸入焦點)，而該組 PIN 的 PIN 計時器會重設。 由於計時器已經重設，共用這組 PIN 任何應用程式 (應用程式 B) 都不會提示使用者輸入 PIN。 提示會在再次達到「重新檢查存取需求前的剩餘時間 (分鐘)」值時再度顯示。

若為 iOS 裝置，即使在不同發行者的應用程式之間共用 PIN，當非主要輸入焦點之應用程式的 [重新檢查存取需求前等候時間 (分鐘)]  值再次達到時，就會再度顯示提示。 例如，使用者有發行者 _X_ 的應用程式 _A_ 和發行者 _Y_ 的應用程式 _B_，而且這兩個應用程式共用相同的 PIN。 使用者將焦點放在應用程式 _A_ (前景)，並將應用程式 _B_ 最小化。 達到 [重新檢查存取需求前等候時間 (分鐘)]  值，而且使用者切換至應用程式 _B_ 之後，則需要 PIN。

  >[!NOTE] 
  > 為了提高驗證使用者存取需求的頻率 (亦即 PIN 提示)，尤其是經常使用的應用程式，建議您降低「重新檢查存取需求前的剩餘時間 (分鐘)」設定的值。 
      
- **Intune PIN 如何搭配使用 Outlook 和 OneDrive 的內建應用程式 PIN ？**<br></br>
Intune PIN 會根據以閒置為基礎的計時器 (又稱為「重新檢查存取需求前的剩餘時間 (分鐘)」值) 運作。 因此，Intune PIN 提示會與 Outlook 和 OneDrive 的內建應用程式 PIN 提示分開顯示，後者預設通常與應用程式啟動相關。 如果使用者同時收到兩個 PIN 提示，預期的行為應該是優先使用 Intune PIN。 

- **PIN 安全嗎？**<br></br> PIN 是用來允許僅有正確的使用者可以存取應用程式中的組織資料。 因此，終端使用者必須使用他們的公司或學校帳戶登入，之後才能設定或重設其 Intune 應用程式 PIN。 這項驗證是由 Azure Active Directory 透過安全語彙基元交換來處理，且未向 Intune App SDK 公開。 從安全性角度來看，保護工作或學校資料的最佳方式是將資料加密。 加密與應用程式 PIN 無關，而是其本身的應用程式保護原則。

- **Intune 如何針對暴力密碼破解攻擊保護 PIN？**<br></br> 做為應用程式 PIN 原則的一部份，IT 系統管理員可以設定在鎖定應用程式之前，使用者可以嘗試驗證其 PIN 的次數上限。 當嘗試次數達到上限之後，Intune App SDK 可以抹除應用程式中的「公司」資料。
  
- **為何我需要在來自同一個發行者的應用程式上設定兩次 PIN？**<br></br> MAM (在 iOS 上) 目前允許應用程式層級 PIN 包含英數字元與特殊字元 (稱為「密碼」)，這需要應用程式參與 (亦即 WXP、Outlook、Managed Browser、Yammer) 以整合適用於 iOS 的 Intune APP SDK。 如果沒有，密碼設定將不會正確地針對目標應用程式強制執行。 這是在「適用於 iOS 7.1.12 版的 Intune SDK」中推出的功能 。 <br><br> 為了支援此功能，並確保對其他版本「適用於 iOS 的 Intune SDK」的回溯相容性，7.1.12 及更新版本中的所有 PIN (不論數字或密碼)，都與先前 SDK 版本中的數字 PIN 分開處理。 因此，如果裝置上有來自同一個發行者的多個應用程式，且其使用的「適用於 iOS 的 Intune SDK」有 7.1.12 之前和 7.1.12 之後的版本，則這些應用程式必須設定兩次 PIN。 <br><br> 雖然如此，這兩個 PIN (針對每個應用程式) 沒有任何關係，亦即，它們必須遵守套用至應用程式的應用程式保護原則。 確切地說，只有  當應用程式 A 和 B 套用相同的原則 (相對於 PIN) 時，使用者才需要設定相同的 PIN 兩次。 <br><br> 針對啟用了「Intune 行動裝置應用程式管理」的 iOS 應用程式，這是應用程式上的 PIN 特有的行為。 一段時間之後，隨著應用程式採用較新版的「適用於 iOS 的 Intune SDK」，需要針對同一個發行者的應用程式設定 PIN 兩次的問題就會減少。 如需範例，請查看下面的注意事項。

  >[!NOTE]
  > 例如，若應用程式 A 是使用 7.1.12 前的版本建置，且應用程式 B 是使用 7.1.12 或之後的版本建置，當 A 和 B 安裝在同一部 iOS 裝置上時，終端使用者將需要針對兩者分別設定 PIN。 <br><br> 如果 SDK 版本是 7.1.9 的應用程式 C 安裝在該裝置上，則它會和應用程式 A 共用相同的 PIN。 <br><br> SDK 版本是 7.1.14 的應用程式 D 會和應用程式 B 共用相同的 PIN。 <br><br> 如果只有應用程式 A 和 C 安裝在同一部裝置上，則只需要設定一個 PIN。 只有應用程式 B 和 D 安裝在同一部裝置上的情況也是如此。

**那加密呢？**<br></br>
IT 系統管理員可以部署要求將應用程式資料加密的應用程式保護原則。 做為原則的一部分，IT 系統管理員也可以指定將內容加密的時機。

- **Intune 如何加密資料？**<br></br> 如需加密應用程式保護原則設定的詳細資訊，請參閱 [Android 應用程式保護原則設定](app-protection-policy-settings-android.md)和 [iOS 應用程式保護原則設定](app-protection-policy-settings-ios.md)。

- **哪些項目會加密？**<br></br> 僅有標示為「公司」的資料會根據 IT 系統管理員的應用程式保護原則加密。 當資料來自公司地點時，會將資料視為「公司」資料。 針對 Office 應用程式，Intune 會將下列位置視為公司地點：電子郵件 (Exchange) 或雲端儲存體 (包含商務用 OneDrive 帳戶的 OneDrive 應用程式)。 針對 Intune App Wrapping Tool 管理的企業營運應用程式，所有的應用程式資料都將視為「公司」資料。

**Intune 如何從遠端抹除資料？**<br></br>
Intune 可以透過三種不同的方式抹除資料：完整的裝置抹除、MDM 選擇性抹除和 MAM 選擇性抹除。 如需 MDM 遠端抹除的詳細資訊，請參閱[使用抹除或淘汰來移除裝置](devices-wipe.md)。 如需使用 MAM 選擇性抹除的詳細資訊，請參閱[淘汰動作](devices-wipe.md#retire)和[如何只抹除應用程式中的公司資料](apps-selective-wipe.md)。

- **什麼是抹除？**<br></br> [抹除](devices-wipe.md)會移除**裝置**的所有使用者資料和設定，方法是將裝置還原為其原廠預設設定。 並從 Intune 移除裝置。
  >[!NOTE]
  > 抹除只能在已向 Intune 行動裝置管理 (MDM) 註冊的裝置上執行。

- **什麼是 MDM 選擇性抹除？**<br></br> 請參閱[移除裝置 - 淘汰](devices-wipe.md#retire)，以閱讀移除公司資料的相關資訊。

- **什麼是 MAM 選擇性抹除？**<br></br> MAM 選擇性抹除僅會從應用程式移除公司應用程式資料。 要求是使用 Intune Azure 入口網站來起始。 若要了解如何起始抹除要求，請參閱[如何只抹除應用程式中的公司資料](apps-selective-wipe.md)。

- **MAM 選擇性抹除發生的速度有多快？**<br></br> 如果使用者在起始選擇性抹除時正在使用應用程式，Intune App SDK 每隔 30 分鐘就會檢查來自 Intune MAM 服務的選擇性抹除要求。 它也會在使用者首次啟動應用程式並以其工作或學校帳戶登入時檢查選擇性抹除。

**為什麼內部部署 (on-prem) 服務無法搭配受 Intune 保護的應用程式運作？**<br></br>
Intune 應用程式保護取決於使用者的身分識別在應用程式與 Intune App SDK 之間保持一致。 保證一致的唯一方式是透過新式驗證。 有些案例中，應用程式可搭配內部部署組態運作，但是不一致也不保證。

**是否有安全的方式能夠從受管理的應用程式開啟網頁連結？**<br></br>
可以！ IT 系統管理員可以針對 [Intune Managed Browser 應用程式](app-configuration-managed-browser.md)部署與設定應用程式保護原則，這是由 Microsoft Intune 開發的網頁瀏覽器，可輕鬆地利用 Intune 加以管理。 針對 Intune 受控應用程式，IT 系統管理員可以要求其中的所有網頁連結都必須使用 Managed Browser 應用程式來開啟。



## <a name="app-experience-on-android"></a>Android 上的應用程式體驗

**為什麼需要公司入口網站應用程式，才能讓 Intune 應用程式保護在 Android 裝置上運作呢？**<br></br>
大部分的應用程式保護功能是內建在公司入口網站應用程式中。 即使公司入口網站應用程式一律為必要，也_不需要_註冊裝置。 若是 MAM-WE，終端使用者只需要在裝置上安裝公司入口網站應用程式即可。

**已設定為相同應用程式和使用者集合的多個 Intune 應用程式保護存取設定，在 Android 上如何運作？**<br></br>
Intune 應用程式保護存取原則，在使用者嘗試從其公司帳戶存取目標應用程式時，會以特定順序套用在終端使用者裝置上。 一般情況下，封鎖會優先，然後是可以關閉的警告。 例如，如果適用於特定的使用者/應用程式，警告使用者進行修補程式升級的最低 Android 修補程式版本設定，將在封鎖使用者使其無法存取的最低 Android 修補程式版本設定之後套用。 因此，當情況是 IT 系統管理員將最低 Android 修補程式版本設定為 2018-03-01，最低 Android 修補程式版本 (僅警告) 設定為 2018-02-01 時，如果嘗試存取應用程式的裝置使用修補程式版本 2018-01-01，則因為導致封鎖存取的最低 Android 修補程式版本設定限制更多，而使得終端使用者將會被封鎖。 

處理不同類型的設定時，應用程式版本需求會優先，然後是 Android 作業系統版本需求和 Android 修補程式版本需求。 接著會以相同順序檢查所有類型之設定的任何警告。

**Intune 應用程式防護原則提供一項功能，讓系統管理員要求終端使用者裝置通過 Google 適用於 Android 裝置的 SafetyNet 證明。將新 SafetyNet 證明結果傳送至服務的頻率為何？** <br><br> 新 Google Play 服務判斷將會依照 Intune 服務所決定的間隔報告給 IT 系統管理員。 進行服務呼叫的頻率已由於負載而節流處理，因此這個值會在內部維護，且無法設定。 將會根據條件式啟動時上次回報給 Intune 服務的結果，來採取任何 IT 系統管理員針對 Google SafetyNet 證明設定所設定的動作。 如果沒有任何資料，將會根據沒有其他的條件式啟動檢查失敗來允許存取，而 Google Play 服務用來判斷證明結果的「往返」動作將在後端開始，並在裝置未通過時以非同步方式提示使用者。 如果有過時的資料，將會根據上次回報的結果封鎖或允許存取，同樣地，Google Play 服務用來判斷證明結果的「往返」動作將會開始，並在裝置未通過時以非同步方式提示使用者。

**Intune 應用程式防護原則提供一項功能，讓系統管理員要求終端使用者裝置透過 Google 適用於 Android 裝置的 Verify Apps API 傳送訊號。終端使用者如何開啟應用程式掃描，讓它們不會因此而被封鎖存取？**<br><br> 有關如何執行這項操作的指示會因裝置而稍有差異。 一般程序包含前往 Google Play 商店，然後按一下 [我的應用程式與遊戲]  ，再按一下上次應用程式掃描結果，其會將您引導至「Play 安全防護」功能表。 確定 [掃描裝置中的安全性威脅]  的切換開關已切換為開啟。

**Google 的 SafetyNet Attestation API 實際上會在 Android 裝置上檢查什麼項目？[檢查基本完整性] 與 [檢查基本完整性與經過認證的裝置] 的可設定值之間有何差異？** <br><br>
Intune 會利用 Google Play Protect SafetyNet API，在我們現有 Root 破解偵測檢查中新增對已取消註冊裝置的檢查。 如果不想在 Root 破解的裝置上執行其應用程式，Google 已開發和維護這個 API 集合供 Android 應用程式採用。 例如，Android Pay 應用程式已併入此集合。 雖然 Google 不會公開共用所發生 Root 破解偵測檢查的全部內容，但我們預期這些 API 會偵測到其裝置遭到 Root 破解的使用者。 接著可防止這些使用者存取，或從其啟用原則的應用程式抹除其公司帳戶。 [檢查基本完整性] 會告訴您有關裝置的一般完整性。 Root 破解的裝置、模擬器、虛擬裝置，以及具有竄改跡象的裝置都無法通過基本完整性。 [檢查基本完整性與經認證的裝置] 會告訴您有關裝置與 Google 服務的相容性。 只有經過 Google 認證且未修改的裝置可以通過這項檢查。 將會失敗的裝置包括下列各項：
* 無法通過基本完整性的裝置
* 其開機載入器已解除鎖定的裝置
* 具有自訂系統映像/ROM 的裝置
* 製造商未為其申請或通過 Google 認證的裝置 
* 直接從 Android Open Source Program 來源檔案建置系統映像的裝置
* 具有搶鮮版 (Beta)/開發人員預覽系統映像的裝置

如需技術詳細資料，請參閱 [Google 有關 SafetyNet 證明的文件](https://developer.android.com/training/safetynet/attestation)。

**為 Android 裝置建立 Intune 應用程式防護原則時，[條件式啟動] 區段中有兩個類似的檢查。我應該需要 [SafetyNet 裝置證明] 設定或 [已越獄/Root 破解的裝置] 設定嗎？** <br><br>
「Google Play 安全防護」的 SafetyNet API 檢查，需要終端使用者至少在判斷證明結果之「往返」動作執行的時間範圍內已連線。 如果終端使用者已離線，IT 系統管理員還是能夠預期從 [已越獄或 Root 破解的裝置] 設定強制執行結果。 話雖如此，如果終端使用者離線太久，[離線寬限期] 值就會起作用，一旦達到該計時器值，對公司或學校資料的存取便會遭到封鎖，直到可以存取網路為止。 開啟這兩個設定可允許採用分層方式來保持終端使用者裝置的良好狀況，這在終端使用者存取行動裝置上的公司或學校資料時非常重要。 

**利用 Google Play Protect API 的應用程式保護原則設定需要 Google Play Services 正常運作。如果終端使用者所在位置中不允許使用 Google Play Services，該怎麼辦？**<br><br>
[SafetyNet 裝置證明] 和 [對應用程式進行威脅掃描] 設定，需要 Google 決定的 Google Play Services 版本才能正確運作。 由於這些都是屬於安全性領域的設定，如果終端使用者是這些設定的目標，但不符合適當的 Google Play Services 版本或無法存取 Google Play 服務，則會封鎖這些使用者。 

## <a name="app-experience-on-ios"></a>iOS 上的應用程式體驗
**如果我將指紋或臉部新增至我的裝置，或是從中移除，會發生什麼情況？**<br></br>
Intune 應用程式防護原則可控制應用程式只存取 Intune 授權使用者。 控制應用程式存取的其中一種方式，就是在支援裝置上要求 Apple 的 Touch ID 或 Face ID。 如果裝置的生物特徵辨識資料庫有任何變更，Intune 會實作一項行為，那就是 Intune 會在達到下次非使用狀態逾時值時，提示使用者輸入 PIN。 對生物特徵辨識資料所做的變更包括新增或移除指紋或臉部。 如果 Intune 使用者未設定 PIN，則會引導他們設定一個 Intune PIN。
 
這樣做的用意是為了持續確保應用程式中的組織資料安全，並在應用程式層級受到保護。 此功能僅適用於 iOS，並需要整合 Intune APP SDK for iOS 9.0.1 版或更新版本的應用程式參與。 您必須整合此 SDK，才能針對目標應用程式強制執行該行為。 這項整合會輪流發生並取決於特定的應用程式小組。 參與的一些應用程式包括 WXP、Outlook、Managed Browser 和 Yammer。 
  
**我可以使用 iOS 共用延伸模組在不受管理的應用程式中開啟工作或學校資料，甚至可將資料傳輸原則設為 [僅限受管理的應用程式] 或 [沒有應用程式]。這樣不會流失資料嗎？**<br></br>
Intune 應用程式保護原則必須管理裝置才能控制 iOS 共用延伸模組。 因此，Intune _**會先加密「公司」資料，才會在應用程式之外共用**_ 。 您可以嘗試在受管理的應用程式外開啟「公司」檔案來加以驗證。 檔案應已加密且無法在受管理的應用程式之外開啟。

**已設定為相同應用程式和使用者集合的多個 Intune 應用程式保護存取設定，在 iOS 上如何運作？**<br></br>
Intune 應用程式保護存取原則，在使用者嘗試從其公司帳戶存取目標應用程式時，會以特定順序套用在終端使用者裝置上。 一般情況下，其順序會是抹除、封鎖及可關閉的警告。 例如，如果適用於特定的使用者/應用程式，警告使用者更新其 iOS 版本的最低 iOS 作業系統設定，將在封鎖使用者使其無法存取的最低 iOS 作業系統設定之後套用。 因此，當情況是 IT 系統管理員將最低 iOS 作業系統設定為 11.0.0.0，最低 iOS 作業系統 (僅警告) 設定為 11.1.0.0 時，如果嘗試存取應用程式的裝置使用 iOS 10，則因為導致封鎖存取的最低 iOS 作業系統版本設定限制更多，而使得終端使用者將會被封鎖。

處理不同類型的設定時，Intune 應用程式 SDK 版本需求會優先，然後是應用程式版本需求，再然後是 iOS 作業系統版本需求。 接著會以相同順序檢查所有類型之設定的任何警告。 我們建議您只針對基本的封鎖情況，在 Intune 產品小組的指導下，設定 Intune App SDK 版本需求。


## <a name="see-also"></a>請參閱
- [實作您的 Intune 計劃](planning-guide-onboarding.md)
- [Intune 測試與驗證](planning-guide-test-validation.md)
- [Microsoft Intune 中的 Android 行動應用程式管理原則設定](app-protection-policy-settings-android.md)
- [iOS 行動應用程式管理原則設定](app-protection-policy-settings-ios.md)
- [應用程式防護原則的原則重新整理](app-protection-policy-delivery.md)
- [驗證應用程式保護原則](app-protection-policy-delivery.md)
- [在不註冊裝置的情況下新增受控應用程式的應用程式設定原則](app-configuration-policies-managed-app.md)
- [如何取得 Microsoft Intune 支援](get-support.md)
