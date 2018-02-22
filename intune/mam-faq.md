---
title: "MAM 和應用程式保護的相關常見問題"
description: "本文章提供 Intune 行動應用程式管理 (MAM) 與 Intune 應用程式保護相關常見問題的解答。"
keywords: 
author: Erikre
ms.author: erikre
manager: angrobe
ms.date: 02/06/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 149def73-9d08-494b-97b7-4ba1572f0623
ms.reviewer: erikre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 23ab21e21ff2ffd471523f8132acffd7545358f0
ms.sourcegitcommit: 9bd6278d129fa29f184b2d850138f8f65f3674ea
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="frequently-asked-questions-about-mam-and-app-protection"></a>MAM 和應用程式保護的相關常見問題

本文章提供 Intune 行動應用程式管理 (MAM) 與 Intune 應用程式保護相關常見問題的解答。

## <a name="mam-basics"></a>MAM 基本概念


**什麼是 MAM？** [Intune 行動應用程式管理](/intune/app-lifecycle)指的是 Intune 管理功能套件，可讓您針對您的使用者發行、推送、設定、保護、監視與更新行動應用程式。

**MAM 應用程式保護的優點有哪些？** MAM 可保護應用程式內組織的資料。 透過不需註冊的 MAM (MAM-WE)，包含機密資料的工作或學校相關應用程式幾乎可在任何裝置上管理，包含攜帶您自己的裝置 (BYOD) 案例中的個人裝置。 許多生產力應用程式 (例如 Microsoft Office 應用程式) 可以由 Intune MAM 管理。 請參閱可供公開使用的 [Intune 受控應用程式](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)官方清單。

**MAM 支援哪些裝置組態？** Intune MAM 支援兩個組態︰
- **Intune MDM + MAM**：IT 系統管理員只能針對已在 Intune 行動裝置管理 (MDM) 註冊的裝置，使用 MAM 與應用程式保護原則來管理應用程式。 若要使用 MDM + MAM 管理應用程式，客戶應該在 Azure 入口網站中使用 Intune 主控台，網址為 https://portal.azure.com。

- **沒有裝置註冊的 MAM**：沒有裝置註冊的 MAM (或 MAM-WE) 允許 IT 系統管理員管理未在 Intune MDM 註冊之裝置上使用 MAM 與應用程式保護原則的應用程式。 這表示應用程式可由向協力廠商 EMM 提供者註冊之裝置上的 Intune 來管理。 若要使用 MAM-WE 管理應用程式，客戶應該在 Azure 入口網站中使用 Intune 主控台，網址為 http://portal.azure.com。此外，向協力廠商企業行動管理 (EMM) 提供者註冊的裝置，或是完全不註冊 MDM 的裝置，也可使用 Intune 來管理應用程式。


## <a name="app-protection-policies"></a>應用程式保護原則

**什麼是應用程式保護原則**？ 應用程式保護原則是確保組織資料能夠在受管理的應用程式中保持安全或受到管制的規則。 原則可以是在使用者嘗試存取或移動「公司」資料時，強制執行的一項規則，或者是當使用者在應用程式內時，禁止執行或受到監視的一組動作。

**應用程式保護原則的範例有哪些？** 如需每個應用程式保護原則設定的詳細資訊，請參閱 [Android 應用程式保護原則設定](app-protection-policy-settings-android.md)和 [iOS 應用程式保護原則設定](app-protection-policy-settings-ios.md)。

## <a name="apps-you-can-manage-with-app-protection-policies"></a>您可以使用應用程式保護原則管理的應用程式

**應用程式保護原則可以管理哪些應用程式？** 與 [Intune App SDK](/intune/app-sdk) 整合或由 [Intune App Wrapping Tool](/intune/apps-prepare-mobile-application-management) 包裝的應用程式，都可以使用應用程式保護原則加以管理。 請參閱可供公開使用的 [Intune 受控應用程式](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)官方清單。

**在 Intune 受控應用程式上，使用應用程式保護原則的基本需求為何？**
- 終端使用者必須擁有 Azure Active Directory (AAD) 帳戶。 請參閱[新增使用者並提供管理權限給 Intune](/intune/users-permissions-add)，以了解如何在 Azure Active Directory 中建立 Intune 使用者。

- 終端使用者必須擁有指派給其 Azure Active Directory 帳戶的 Microsoft Intune 授權。 請參閱[管理 Intune 授權](/intune/licenses-assign)，以了解如何將 Intune 授權指派給終端使用者。

- 終端使用者必須隸屬於由應用程式保護原則設為目標的安全性群組。 相同的應用程式保護原則必須將已使用的特定應用程式設為目標。 應用程式保護原則可在 [Azure 入口網站](http://portal.azure.com)中的 Intune 主控台中建立與部署。 安全群組目前可以在 [Office 入口網站](http://portal.office.com)中建立。

- 終端使用者必須使用其 AAD 帳戶來登入應用程式。

**使用 [Outlook 行動裝置應用程式 (英文)](https://products.office.com/outlook) 時有哪些其他需求？**

- 終端使用者必須在其裝置上安裝 Outlook 行動裝置應用程式。

- 終端使用者必須具有連結到其 Azure Active Directory 帳戶的 [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online) 信箱和授權。

  >[!NOTE]
  > Outlook 行動裝置應用程式目前僅支援 Microsoft Exchange Online，而不支援 Exchange 內部部署或 Office 365 專用中的 Exchange。

**使用 [Word、Excel 與 PowerPoint](https://products.office.com/business/office) 應用程式時有哪些其他需求？**

- 終端使用者必須擁有連結到其 Azure Active Directory 帳戶的 [Office 365 商務版或企業版](https://products.office.com/business/compare-more-office-365-for-business-plans)授權。 訂用帳戶必須包括行動裝置版 Office 應用程式，而且可以包括可搭配[商務用 OneDrive](https://onedrive.live.com/about/business/) 使用的雲端儲存體帳戶。 Office 365 授權可以在 [Office 入口網站](http://portal.office.com)中依照下列[指示](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc)指派。

- 終端使用者必須有受控的位置，此位置是使用 [不可進行另存新檔] 應用程式保護原則設定下的細微另存新檔功能設定的。 例如，若受控位置是 OneDrive，則 [OneDrive](https://onedrive.live.com/about/) 應用程式應該在終端使用者的 Word、Excel 或 PowerPoint 應用程式中設定。

- 若受控位置是 OneDrive，則應用程式必須是部署到終端使用者之應用程式保護原則的目標。

  >[!NOTE]
  > Office 行動裝置應用程式目前僅支援 SharePoint Online，不支援 SharePoint 內部部署。

**Office 為何需要受控位置 (例如 OneDrive)？** Intune 會將應用程式中所有資料標示為「公司」或「個人」。 當資料來自公司地點時，會將資料視為「公司」資料。 針對 Office 應用程式，Intune 會將下列位置視為公司地點：電子郵件 (Exchange) 或雲端儲存體 (包含商務用 OneDrive 帳戶的 OneDrive 應用程式)。

**使用商務用 Skype 有哪些其他需求？** 請參閱[商務用 Skyp](https://products.office.com/skype-for-business/it-pros) 授權需求。
  >[!NOTE]
  > 商務用 Skyp 行動裝置應用程式目前僅支援商務用 Skype Online。

## <a name="app-protection-features"></a>應用程式保護功能

**什麼是多重身分識別支援？** 多重身分識別支援是 Intune App SDK 僅將應用程式保護原則套用至已登入應用程式之工作或學校帳戶的功能。 如果個人帳戶已登入應用程式，就不會更動資料。

**多重身分識別支援的用途為何？** 多重身分識別支援允許公開發行同時包含「公司」與消費者對象的應用程式 (例如，Office 應用程式)，並且讓「公司」帳戶具有 Intune 應用程式保護功能。

**Outlook 以及多重身分識別呢？** 因為 Outlook 有合併個人與「公司」電子郵件的電子郵件檢視，所以 Outlook 應用程式會在啟動時提示 Intune PIN。

**什麼是 Intune 應用程式 PIN？** 個人識別碼 (PIN) 是一組密碼，用來驗證在應用程式中存取組織資料的是正確的使用者。

- **何時會提示使用者輸入 PIN？** Intune 會在使用者要存取「公司」資料時，提示使用者提供應用程式 PIN。 在多重身分識別應用程式 (例如 Word/Excel/PowerPoint) 中，系統會在使用者嘗試開啟「公司」文件或檔案時提示他們提供 PIN。 在單一身分識別應用程式 (例如，使用 Intune App Wrapping Tool 管理的企業營運應用程式) 中，會在啟動時提示提供 PIN，因為 Intune App SDK 知道使用者一定是在「公司」環境中使用應用程式。

- **使用者收到 Intune PIN 提示的頻率為何？**
  IT 系統管理員可以在 Intune 管理主控台中定義 Intune 應用程式保護原則設定「重新檢查存取需求前的剩餘時間 (分鐘)」。 這項設定會指定多久之後要在裝置上檢查存取要求，並再次顯示應用程式 PIN 畫面。 不過，還有下列關於 PIN 的重要詳細資料會影響使用者收到通知的頻率： 

    - **PIN 會在相同發行者的多個應用程式間共用，以提升可用性：**在 iOS，一組應用程式 PIN 會在**相同發行者**的所有應用程式間共用。 在 Android，一組應用程式 PIN 會在所有應用程式間共用。
    - **與 PIN 相關的計時器過時性質：**在輸入 PIN 以存取應用程式 (應用程式 A) 之後，應用程式會離開裝置的前景 (主要輸入焦點)，而該組 PIN 的 PIN 計時器會重設。 由於計時器已經重設，共用這組 PIN 任何應用程式 (應用程式 B) 都不會提示使用者輸入 PIN。 提示會在再次達到「重新檢查存取需求前的剩餘時間 (分鐘)」值時再度顯示。 

      >[!NOTE] 
      > 為了提高驗證使用者存取需求的頻率 (亦即 PIN 提示)，尤其是經常使用的應用程式，建議您降低「重新檢查存取需求前的剩餘時間 (分鐘)」設定的值。 

- **PIN 安全嗎？** PIN 是用來允許僅有正確的使用者可以存取應用程式中的組織資料。 因此，終端使用者必須使用他們的公司或學校帳戶登入，之後才能設定或重設其 Intune 應用程式 PIN。 這項驗證是由 Azure Active Directory 透過安全語彙基元交換來處理，且未向 Intune App SDK 公開。 從安全性角度來看，保護工作或學校資料的最佳方式是將資料加密。 加密與應用程式 PIN 無關，而是其本身的應用程式保護原則。

- **Intune 如何針對暴力密碼破解攻擊保護 PIN？** 做為應用程式 PIN 原則的一部份，IT 系統管理員可以設定在鎖定應用程式之前，使用者可以嘗試驗證其 PIN 的次數上限。 當嘗試次數達到上限之後，Intune App SDK 可以抹除應用程式中的「公司」資料。
  
- **為何我需要在來自同一個發行者的應用程式上設定兩次 PIN？**
  MAM (在 iOS 上) 目前允許應用程式層級 PIN 包含英數字元與特殊字元 (稱為「密碼」)，這需要應用程式參與 (亦即 WXP、Outlook、Managed Browser、Yammer) 以整合適用於 iOS 的 Intune APP SDK。 如果沒有，密碼設定將不會正確地針對目標應用程式強制執行。 這是在「適用於 iOS 7.1.12 版的 Intune SDK」中推出的功能 。 <br><br> 為了支援此功能，並確保對其他版本「適用於 iOS 的 Intune SDK」的回溯相容性，7.1.12 及更新版本中的所有 PIN (不論數字或密碼)，都與先前 SDK 版本中的數字 PIN 分開處理。 因此，如果裝置上有來自同一個發行者的多個應用程式，且其使用的「適用於 iOS 的 Intune SDK」有 7.1.12 之前和 7.1.12 之後的版本，則這些應用程式必須設定兩次 PIN。 <br><br> 雖然如此，這兩個 PIN (針對每個應用程式) 沒有任何關係，亦即，它們必須遵守套用至應用程式的應用程式保護原則。 確切地說，只有當應用程式 A 和 B 套用相同的原則 (相對於 PIN) 時，使用者才需要設定相同的 PIN 兩次。 <br><br> 針對啟用了「Intune 行動裝置應用程式管理」的 iOS 應用程式，這是應用程式上的 PIN 特有的行為。 一段時間之後，隨著應用程式採用較新版的「適用於 iOS 的 Intune SDK」，需要針對同一個發行者的應用程式設定 PIN 兩次的問題就會減少。 如需範例，請查看下面的注意事項。

  >[!NOTE]
  > 例如，若應用程式 A 是使用 7.1.12 前的版本建置，且應用程式 B 是使用 7.1.12 或之後的版本建置，當 A 和 B 安裝在同一部 iOS 裝置上時，終端使用者將需要針對兩者分別設定 PIN。 <br><br> 如果 SDK 版本是 7.1.9 的應用程式 C 安裝在該裝置上，則它會和應用程式 A 共用相同的 PIN。 <br><br> SDK 版本是 7.1.14 的應用程式 D 會和應用程式 B 共用相同的 PIN。 <br><br> 如果只有應用程式 A 和 C 安裝在同一部裝置上，則只需要設定一個 PIN。 只有應用程式 B 和 D 安裝在同一部裝置上的情況也是如此。

**那加密呢？** IT 系統管理員可以部署要求將應用程式資料加密的應用程式保護原則。 做為原則的一部分，IT 系統管理員也可以指定將內容加密的時機。

- **Intune 如何加密資料？** 如需加密應用程式保護原則設定的詳細資訊，請參閱 [Android 應用程式保護原則設定](app-protection-policy-settings-android.md)和 [iOS 應用程式保護原則設定](app-protection-policy-settings-ios.md)。

- **哪些項目會加密？** 僅有標示為「公司」的資料會根據 IT 系統管理員的應用程式保護原則加密。 當資料來自公司地點時，會將資料視為「公司」資料。 針對 Office 應用程式，Intune 會將下列位置視為公司地點：電子郵件 (Exchange) 或雲端儲存體 (包含商務用 OneDrive 帳戶的 OneDrive 應用程式)。 針對 Intune App Wrapping Tool 管理的企業營運應用程式，所有的應用程式資料都將視為「公司」資料。

**Intune 如何從遠端抹除資料？** Intune 可以透過三種不同的方式抹除資料：完整的裝置抹除、MDM 選擇性抹除和 MAM 選擇性抹除。 如需 MDM 遠端抹除的詳細資訊，請參閱[使用重設成出廠預設值或移除公司資料來移除裝置](devices-wipe.md#factory-reset)。 如需使用 MAM 選擇性抹除的詳細資訊，請參閱[移除公司資料](devices-wipe.md#remove-company-data)和[如何只抹除應用程式中的公司資料](apps-selective-wipe.md)。

- **什麼是重設成出廠預設值？** [重設成出廠預設值](devices-wipe.md)會將裝置還原為其出廠預設設定，進而從**裝置**上移除所有的使用者資料和設定。 並從 Intune 移除裝置。
  >[!NOTE]
  > 「重設成出廠預設值」只能在已向 Intune 行動裝置管理 (MDM) 註冊的裝置上執行。

- **什麼是 MDM 選擇性抹除？** 請參閱[移除裝置 - 移除公司資料](devices-wipe.md#remove-company-data)，以閱讀移除公司資料的相關資訊。

- **什麼是 MAM 選擇性抹除？** MAM 選擇性抹除僅會從應用程式移除公司應用程式資料。 要求是使用 Intune Azure 入口網站來起始。 若要了解如何起始抹除要求，請參閱[如何只抹除應用程式中的公司資料](apps-selective-wipe.md)。

- **MAM 選擇性抹除發生的速度有多快？** 如果使用者在起始選擇性抹除時正在使用應用程式，Intune App SDK 每隔 30 分鐘就會檢查來自 Intune MAM 服務的選擇性抹除要求。 它也會在使用者首次啟動應用程式並以其工作或學校帳戶登入時檢查選擇性抹除。

**為什麼內部部署 (on-prem) 服務無法搭配受 Intune 保護的應用程式運作？** Intune 應用程式保護取決於使用者的身分識別在應用程式與 Intune App SDK 之間保持一致。 保證一致的唯一方式是透過新式驗證。 有些案例中，應用程式可搭配內部部署組態運作，但是不一致也不保證。

**是否有安全的方式能夠從受管理的應用程式開啟網頁連結？** 可以！ IT 系統管理員可以針對 [Intune Managed Browser 應用程式](app-configuration-managed-browser.md)部署與設定應用程式保護原則，這是由 Microsoft Intune 開發的網頁瀏覽器，可輕鬆地利用 Intune 加以管理。 針對 Intune 受控應用程式，IT 系統管理員可以要求其中的所有網頁連結都必須使用 Managed Browser 應用程式來開啟。


## <a name="app-experience-on-android"></a>Android 上的應用程式體驗

**為什麼需要公司入口網站應用程式，才能讓 Intune 應用程式保護在 Android 裝置上運作呢？** 大部分的應用程式保護功能是內建在公司入口網站應用程式中。 即使公司入口網站應用程式一律為必要，也_不需要_註冊裝置。 若是 MAM-WE，終端使用者只需要在裝置上安裝公司入口網站應用程式即可。

## <a name="app-experience-on-ios"></a>iOS 上的應用程式體驗

**我可以使用 iOS 共用延伸模組在不受管理的應用程式中開啟工作或學校資料，甚至可將資料傳輸原則設為 [僅限受管理的應用程式] 或 [沒有應用程式]。這樣不會流失資料嗎？** Intune 應用程式保護原則必須管理裝置才能控制 iOS 共用延伸模組。 因此，Intune _**會先加密「公司」資料，才會在應用程式之外共用**_。 您可以嘗試在受管理的應用程式外開啟「公司」檔案來加以驗證。 檔案應已加密且無法在受管理的應用程式之外開啟。

## <a name="see-also"></a>另請參閱
- [實作您的 Intune 計劃](planning-guide-onboarding.md)
- [Intune 測試與驗證](planning-guide-test-validation.md)
- [Microsoft Intune 中的 Android 行動應用程式管理原則設定](app-protection-policy-settings-android.md)
- [iOS 行動應用程式管理原則設定](app-protection-policy-settings-ios.md)
- [驗證應用程式保護原則](app-protection-policies-validate.md)
- [在不註冊裝置的情況下新增受控應用程式的應用程式設定原則](app-configuration-policies-managed-app.md)
- [如何取得 Microsoft Intune 支援](get-support.md)
