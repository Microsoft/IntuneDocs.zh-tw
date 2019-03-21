---
title: 針對條件式存取進行疑難排解 | Microsoft Intune
description: 您的使用者無法透過 Intune 條件式存取取得資源的存取權時該怎麼辦。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/25/2018
ms.topic: troubleshooting
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 5fa59501-5f33-46b7-a5f5-75eeae9f1209
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 50c147e13a59df00ce9527a0843784d223afec20
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57460711"
---
# <a name="troubleshoot-conditional-access"></a>條件式存取的疑難排解

您可以使用 Intune 和條件式存取，保護對 Office 365 服務 (例如 Exchange Online、SharePoint Online、商務用 Skype Online、Exchange 內部部署和其他服務) 的存取。 此功能可確保只有當裝置向 Intune 註冊並符合您透過 Intune 管理主控台或 Azure Active Directory 所設定的條件式存取規則時，才能存取公司資源。 本文描述您的使用者無法存取使用條件式存取所保護的資源時，或使用者可以存取受保護資源但應該封鎖受保護資源時，該怎麼辦。

## <a name="requirements-for-conditional-access"></a>條件式存取的需求

必須符合下列需求，條件式存取才能運作：

- 裝置必須由 Intune 註冊和管理。
- 使用者和裝置都必須符合所指派的 Intune 合規性政策。
- 根據預設，使用者必須獲指派裝置合規性政策。 這可能取決於如何在 Intune 管理入口網站的 [裝置合規性] > [合規性政策設定] 下設定 [將未指派合規性政策的裝置標記為] 設定。
-   如果使用者使用裝置的原生郵件用戶端，而非 Outlook，則必須在裝置上啟用 Exchange ActiveSync。 這在 iOS、Windows Phone 和 Android 裝置上都會自動進行。
-   您的 Intune Exchange Connector 必須已正確設定。 如需詳細資訊，請參閱[為 Microsoft Intune 中的 Exchange Connector 進行疑難排解](troubleshoot-exchange-connector.md)。

您可在 Azure 入口網站和裝置清查報表中，檢視每個裝置的這些狀況。

## <a name="devices-appear-compliant-but-users-are-still-blocked"></a>裝置會顯示符合規範，但使用者仍然會遭到封鎖

- 除非使用者按一下所收到之隔離電子郵件中的 [立即開始使用] 連結，否則非 Knox Android 裝置將不會獲授與存取。 即使已在 Intune 中註冊使用者，這也適用。 如果使用者未透過手機收到包含該連結的電子郵件，則可以使用電腦存取其電子郵件，並將它轉寄至其裝置上的電子郵件帳戶。
- 第一次註冊裝置時，可能需要一些時間來註冊裝置的合規性資訊。 請稍候幾分鐘，然後再試一次。
- 針對 iOS 裝置，現有電子郵件設定檔可能會封鎖部署指派給該使用者的 Intune 管理員所建立的電子郵件設定檔，因此讓裝置不符合規範。 在此情節中，公司入口網站應用程式將會通知使用者有關它們因其手動設定的電子郵件設定檔而不符合規範，並提示使用者移除該設定檔。 使用者移除現有電子郵件設定檔之後，接著就可以成功部署 Intune 電子郵件設定檔。 若要避免此問題，請指示使用者先移除其裝置上的任何現有電子郵件設定檔，再註冊。
- 裝置可能會卡在檢查合規性狀態，造成使用者無法起始另一個簽入。 如果您的裝置處於此狀態，則請嘗試下列作業：
  - 確定裝置使用公司入口網站應用程式的最新版本。
  - 重新啟動裝置。
  - 請查看問題是否仍然存在於不同的網路 (例如行動數據、Wi-Fi 等等)。

  如果仍然發生問題，請連絡 Microsoft 支援服務 (如[取得 Microsoft Intune 支援](get-support.md)所述)。
- 某些 Android 裝置似乎已加密，但公司入口網站應用程式會將這些裝置辨識為未加密，因此將它們標示為不符合規範。 在此情節中，使用者將會在公司入口網站應用程式中看到通知，要求他們設定裝置的啟動密碼。 點選通知並確認現有 PIN 或密碼之後，請在 [Secure start-up]\(安全啟動\) 畫面上選擇 [Require PIN to start device]\(需要 PIN 碼才能啟動裝置\) 選項，然後從公司入口網站應用程式中點選裝置的 [Check Compliance] \(檢查合規性\) 按鈕。 現在裝置應該偵測為已加密。 
  > [!NOTE]
  > 有些裝置製造商會使用預設 PIN 來加密其裝置，而不是使用者所設定的 PIN。 除非使用者建立新的非預設 PIN，否則 Intune 會將使用預設 PIN 的加密視為不安全，並將這些裝置標記為不符合規範。
- 已註冊且符合規範的 Android 裝置可能仍然會遭到封鎖，並在第一次嘗試存取公司資源時收到隔離通知。 如果發生這種情況，請確定公司入口網站應用程式未執行，然後按一下隔離電子郵件中的 [立即開始使用] 連結以觸發評估。 應該只有在第一次啟用條件式存取時，才需要完成此作業。

## <a name="devices-are-blocked-and-no-quarantine-email-is-received"></a>封鎖裝置，而且不會收到任何隔離電子郵件

- 請確認裝置是否在 Intune 管理主控台中顯示為 Exchange ActiveSync 裝置。 如果沒有，則裝置探索可能將失敗，而原因可能是發生 Exchange Connector 問題。 如需詳細資訊，請參閱[針對 Intune on-premises Exchange Connector 進行疑難排解](troubleshoot-exchange-connector.md)。
- Exchange Connector 封鎖裝置之前，會傳送啟用 (隔離) 電子郵件。 如果裝置離線，則可能不會收到啟用電子郵件。 
- 確認裝置上的電子郵件用戶端是否設定成使用 [推送] (而非 [輪詢]) 來擷取電子郵件。 如果是這樣，這可能會造成使用者遺漏電子郵件。 切換到 [輪詢]，並查看裝置是否收到電子郵件。

## <a name="devices-are-noncompliant-but-users-are-not-blocked"></a>裝置不符合規範，但不會封鎖使用者

- 在 Windows 電腦中，條件式存取只會封鎖原生電子郵件應用程式：含新式驗證的 Office 2013 或 Office 2016。 根據[設定 SharePoint Online 和 Exchange Online，以便採用 Azure Active Directory 條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-no-modern-authentication)，封鎖 Windows 電腦上的舊版 Outlook 或所有郵件應用程式需要 AAD 裝置註冊和 Active Directory Federation Services (AD FS) 設定。 
- 如果選擇性地從 Intune 抹除或淘汰裝置，則可能會在淘汰之後繼續存取裝置數個小時。 這是因為 Exchange 會快取存取權限長達 6 小時。 在此案例中，請考慮其他方法來保護已淘汰裝置上的資料。
- Surface Hub 裝置支援條件式存取；不過，您必須將合規性政策部署至裝置群組 (非使用者群組) 進行正確評估。
- 請檢查您合規性政策和條件式存取原則的指派。 如果使用者不在獲指派這些原則的群組中，或在所排除的群組中，則不會封鎖使用者。 只會檢查所指派群組中使用者的裝置合規性。

## <a name="noncompliant-device-is-not-blocked"></a>未封鎖不符合規範的裝置

如果您遇到不相容但可以繼續存取的裝置，請採取下列步驟。
- 檢閱您的目標和排除群組。 如果使用者不在正確的目標群組，或不在排除群組中，即不會遭到封鎖。 只會檢查目標群組中使用者的裝置相容性。
- 確定已探索到該裝置。 Exchange Connector 指向 Exchange 2010 CAS，但使用者卻在 Exchange 2013 伺服器上？ 在此情況下，如果預設 Exchange 規則為 [允許]，即使是目標群組中的使用者，Intune 仍無法知道該裝置的 Exchange 連線。
- 檢查 Exchange 中的裝置存在/存取狀態︰
  - 使用這個 PowerShell Cmdlet，取得信箱的所有行動裝置清單："Get-ActiveSyncDeviceStatistics -mailbox mbx'。 如果裝置未列在其中，表示它並未存取 Exchange。
  - 如果列出該裝置，請使用 Get-CASmailbox -identity:’upn’ | fl Cmdlet，取得其存取狀態的詳細資訊，並將該資訊提供給 Microsoft 支援服務。

## <a name="next-steps"></a>後續步驟
如果這項資訊對您沒有幫助，您也可以[取得 Microsoft Intune 支援](get-support.md)。
