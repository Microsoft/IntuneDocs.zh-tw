---
title: 引導式案例 - 雲端管理的新式桌面
titleSuffix: Microsoft Intune
description: 了解引導式案例以設從 Microsoft 365 裝置管理入口網站設定現代化電腦。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f78f3696827ebd50084f0e4b012c5f94427eeb35
ms.sourcegitcommit: 15e099a9a1e18296580bb345610aee7cc4acd126
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2019
ms.locfileid: "74164576"
---
# <a name="guided-scenario---cloud-managed-modern-desktop"></a>引導式案例 - 雲端管理的新式桌面

現代化電腦是適用於資訊工作者最先進的生產力平台。 Office 365 專業增強版與 Windows 10 是具有 Windows 10 最新安全性基準和 Microsoft Defender 進階威脅防護的現代化電腦核心元件。 

從雲端管理現代化電腦帶來網際網路遠端動作的另一層優點。 雲端管理利用內建的 Windows 行動裝置管理原則並去除對本機 Active Directory 群組原則的依賴。 

若要在您自己的組織中評估雲端管理的現代化電腦，此引導式案例預先定義基本部署的所有必要設定。 在此引導式案例中，您將會建立一個安全的環境，並在其中嘗試 Intune 裝置管理功能。 

## <a name="prerequisites"></a>必要條件
- [將 MDM 授權單位設定為 Intune](~/fundamentals/mdm-authority-set.md#set-mdm-authority-to-intune)：行動裝置管理 (MDM) 授權單位設定會決定您管理裝置的方式。 身為 IT 系統管理員，您必須在使用者可以註冊裝置以進行管理之前，設定 MDM 授權單位。
- 最低 M365 E3 (或 M365 E5 以獲得最佳安全性)
- Windows 10 1903 裝置 (已向 Windows Autopilot 註冊以獲得最佳終端使用者體驗)
- 需要 Intune 管理員權限以完成此引導式案例：
  - 設定裝置設定讀取、建立、刪除、指派及更新
  - 註冊計畫讀取裝置、讀取設定檔、建立設定檔、指派設定檔、刪除設定檔
  - 行動裝置應用程式讀取、建立、刪除、指派及更新
  - 組織讀取及更新
  - 安全性基準讀取、建立、刪除、指派及更新
  - 原則集合讀取、建立、刪除、指派及更新

## <a name="step-1---introduction"></a>步驟 1 - 簡介

使用此引導式案例，您將會設定測試使用者、在 Intune 中註冊裝置，以及使用 Intune 建議的設定部署裝置，以及 Windows 10 與 Office 專業增強版。 若您選擇[在 Intune 啟用此保護](~/protect/advanced-threat-protection.md#enable-microsoft-defender-atp-in-intune)，您的裝置也會針對 Microsoft Defender 進階威脅防護設定。 您設定的使用者與您註冊的裝置將會新增到新的安全性群組中，而且會使用安全性與生產力建議設定來設定。 

### <a name="what-you-will-need-to-continue"></a>您需要什麼才能繼續

您必須在引導式案例中提供您的測試裝置與測試使用者。 確定您已完成下列工作：
- 在 Azure Active Directory 中設定測試使用者帳戶。
- 建立執行 Windows 10 1903 版或更新版本的測試裝置。
- (選擇性) [向 Windows Autopilot 註冊測試裝置](~/enrollment/enrollment-autopilot.md#add-devices)。
- (選擇性) 啟用[將商標新增至組織的 Azure Active Directory 登入頁面](https://go.microsoft.com/fwlink/?linkid=2102455)。

## <a name="step-2---user"></a>步驟 2 - 使用者

選擇要在裝置上設定的使用者。 該使用者將會是裝置的主要使用者。

若要新增更多使用者或裝置到此設定，只要將使用者或裝置新增到精靈產生的 AAD 安全性群組即可。 與其他引導式案例不一樣，您不需要多次執行精靈，因為設定並非可設定的。 只要新增更多使用者與裝置到建立的 AAD 群組即可。 完成精靈之後，您將能檢視在已部署建議原則的情況下產生的群組。 

## <a name="step-3---device"></a>步驟 3 - 裝置

確定您的裝置執行 Windows 10 1903 版或更新版本。  主要使用者將必須在收到裝置時設定裝置。 使用者有兩個可用的設定選項。 

### <a name="option-a--windows-autopilot"></a>選項 A：Windows Autopilot
Windows Autopilot 會將設定新裝置的程序自動化，因此使用者可以自行設定裝置，而不需要 IT 人員的協助。 若您的裝置已向 Windows Autopilot 註冊，請依序號選取裝置。 如需有關使用 Windows Autopilot 的詳細資訊，請參閱[向 Windows Autopilot 註冊裝置 (選擇性)](~/fundamentals/guided-scenarios-cloud-managed-pc.md#register-device-with-windows-autopilot-optional)。

### <a name="option-b--manual-device-enrollment"></a>選項 B：手動裝置註冊
使用者將必須手動在行動裝置管理中設定並註冊其新裝置。 當您完成此案例之後，請重設裝置並為主要使用者提供 Windows 裝置註冊指示。 如需詳細資訊，請參閱[在初次執行體驗將 Windows 10 裝置加入 Azure AD](https://docs.microsoft.com/azure/active-directory/devices/azuread-joined-devices-frx#joining-a-device) \(部分機器翻譯\)。

## <a name="step-4---review--create"></a>步驟 4 - 檢閱 + 建立

最後的步驟可讓您檢閱您所設定之設定的摘要。 在您檢閱自己的選擇之後，請按一下 [部署]  以完成引導式案例。 引導式案例完成之後，會顯示資源表格。 您稍後可以編輯這些資源，不過，一旦離開摘要檢視，將不會儲存該表格。

> [!IMPORTANT]
> 引導式案例完成之後，它將會顯示摘要。 您稍後可以修改列於摘要中的資源，不過系統將不會儲存顯示這些資源的表格。

### <a name="verification"></a>驗證
1. 確認選取的是指派的 MDM 使用者範圍
    - 確定 [MDM 使用者範圍](~/enrollment/windows-enroll.md#enable-windows-10-automatic-enrollment)是：
        - 針對 [Microsoft Intune]  應用程式，設定為 [全部]  或，
        - 設定為 [部分]  。 此外，新增此引導式案例建立的使用者群組。
2. 確認選取的使用者可以將裝置加入 Azure Active Directory。
    - 確定 AAD 加入已：
        - 設定為 [全部]  或，
        - 設定為 [部分]  。 此外，新增此引導式案例建立的使用者群組。
3. 根據下列設定，在裝置上依照適當步驟執行，以將裝置加入 Azure AD：
    - 使用 Autopilot。 如需詳細資訊，請參閱 [Windows Autopilot 使用者驅動模式](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven) \(部分機器翻譯\)。
    - 不使用 Autopilot：如需詳細資訊，請參閱[在初次執行體驗將 Windows 10 裝置加入 Azure AD](https://docs.microsoft.com/azure/active-directory/devices/azuread-joined-devices-frx#joining-a-device) \(部分機器翻譯\)。

### <a name="what-happens-when-i-click-deploy"></a>當我按一下 [部署] 時，會發生什麼事？
使用者與裝置將會新增至新的安全性群組。 系統也會根據裝置位於公司或學校使用 Intune 建議的安全性與生產力設定來加以設定。 當使用者將裝置加入 Azure AD 之後，系統會將額外的應用程式與設定加入裝置。 若要深入了解這些額外設定，請參閱[快速入門：註冊您的 Windows 10 裝置](~/enrollment/quickstart-enroll-windows-device.md)。

## <a name="additional-information"></a>其他資訊

### <a name="register-device-with-windows-autopilot-optional"></a>向 Windows Autopilot 註冊測試裝置 (選擇性)

您也可以選擇使用已註冊的 Autopilot 裝置。 針對 Autopilot，這個引導式案例將會指派 Autopilot 部署設定檔與註冊狀態頁面設定檔。 Autopilot 部署設定檔將以如下方式設定：
- 使用者驅動模式，亦即要求使用者必須在 Windows 安裝期間輸入使用者名稱與密碼。
- Azure AD 加入。
- 自訂 Windows 安裝程式：
  - 隱藏 [Microsoft 軟體授權條款] 畫面
  - 隱藏隱私權設定 
  - 在沒有本機系統管理員權限的情況下建立使用者的本機設定檔
  - 隱藏公司登入頁面上的 [變更帳戶] 選項

註冊狀態頁面將會設定為只針對 Autopilot 裝置啟用，而且將不會封鎖等候所有應用程式安裝完成。

引導式案例也會將使用者指派到選取的 Autopilot 裝置以提供個人化的安裝體驗。

#### <a name="post-requisites"></a>後續先決條件
使用者將裝置加入 Azure Active Directory 之後，下列設定將套用到裝置：
1. 將自動在雲端管理的電腦上安裝 Office 365 專業增強版。 它包括您熟悉的應用程式，包括 Access、Excel、OneNote、Outlook、PowerPoint、Publisher、商務用 Skype 與 Word。 您可以使用這些應用程式來與 Office 365 服務 (例如 SharePoint Online、Exchange Online 與商務用 Skype Online) 連線。 Office 365 專業增強版會定期更新新功能，這與非 Office 訂閱版本不同。 如需新功能清單，請參閱＜Office 365 的新增功能＞。
2. 將在雲端管理電腦上安裝 Windows 安全性基準。 若您已安裝 Microsoft Defender 進階威脅防護，引導式案例也會設定 Defender 的安全性基準。 Defender 進階威脅防護為 Windows 10 安全性堆疊提供新的入侵後保護層。 由於我們已將用戶端技術組合建置到 Windows 10 與強固的雲端服務中，它將有助於偵測其他防護方式未發現的威脅。 

## <a name="next-steps"></a>後續步驟

- 若正在使用 Microsoft Defender 進階威脅偵測，則請建立 [Intune 合規性政策](~/protect/advanced-threat-protection.md#create-and-assign-the-compliance-policy)以要求 Defender 威脅分析符合合規性。
- 建立[裝置型條件式存取原則](~/protect/advanced-threat-protection.md#create-a-conditional-access-policy)以在裝置不符合 Intune 合規性時封鎖存取。
