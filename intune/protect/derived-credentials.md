---
title: 在 Microsoft Intune 中使用行動裝置的衍生認證 - Azure | Microsoft Docs
description: 在行動裝置上使用衍生認證作為 Intune VPN、電子郵件、Wi-fi 設定檔、應用程式和 S/MIME 和加密的驗證方法。 衍生認證是特殊發行集 800-157 的 NIST 指導方針實作。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f9e8bc347dc6336f665fcabfb4e716fef4818515
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207193"
---
# <a name="use-derived-credentials-in-microsoft-intune"></a>在 Microsoft Intune 中使用衍生認證

*此文章適用於執行 iOS 的裝置*

在需要智慧卡進行驗證或加密和簽署的環境中，您現在可以使用 Intune，透過衍生自使用者智慧卡的憑證來佈建行動裝置。 該憑證稱為「衍生認證」  。 Intune [支援數個衍生認證簽發者](#supported-issuers)，但您一次只能針對每個租用戶使用單一簽發者。

衍生認證是適用於衍生個人識別驗證 (PIV) 認證的國家標準暨技術研究院 (NIST) 指導方針實作，是特殊發行集 (SP) 800-157 的一部分。

**使用 Intune 的實作**：

- Intune 管理員會將其租用戶設定為與支援的衍生認證簽發者搭配使用。 您不需要在衍生認證簽發者的系統中設定任何 Intune 特定設定。

- Intune 管理員會指定衍生認證作為下列物件的驗證方法：  

  - 常用的設定檔類型，例如 Wi-Fi、VPN 和電子郵件，其中包括 iOS 原生郵件應用程式

  - 應用程式驗證

  - S/MIME 簽署和加密

- 使用者可以使用其在電腦上的智慧卡向衍生的認證簽發者進行驗證，以取得衍生的認證。 然後簽發者會向行動裝置發出一個衍生自其智慧卡的憑證。

- 當應用程式或資源存取設定檔需要衍生認證時，裝置收到衍生的認證後，就會用於驗證和 S/MIME 簽署和加密。 

## <a name="prerequisites"></a>先決條件

將您的租用戶設定為使用衍生認證之前，請先檢閱下列資訊。

### <a name="supported-platforms"></a>支援的平台

Intune 支援下列 OS 平台上的衍生認證：

- iOS/iPadOS

### <a name="supported-issuers"></a>支援的簽發者

Intune 支援每一租用戶單一衍生認證簽發者。 您可以設定 Intune 與下列簽發者搭配使用：

- **DISA Purebred**： https://cyber.mil/pki-pke/purebred/
- **Entrust Datacard**： https://www.entrustdatacard.com/
- **Intercede**： https://www.intercede.com/

如需使用不同簽發者的重要詳細資訊，請檢閱該簽發者的指引<!-- , including the issuers end-user workflow-->。 如需詳細資訊，請參閱此文章中的[規劃衍生認證](#plan-for-derived-credentials)。

> [!IMPORTANT]  
> 如果您從租用戶刪除衍生認證簽發者，透過該簽發者所設定的衍生認證將無法再運作。
>
> 請參閱此文章稍後的[變更衍生認證簽發者](#change-the-derived-credential-issuer)。

### <a name="company-portal-app"></a>公司入口網站應用程式

規劃將 Intune 公司入口網站應用程式部署到將註冊衍生認證的裝置。 裝置使用者會使用公司入口網站應用程式來啟動認證註冊程序。

針對 iOS 裝置，請參閱[將 iOS 市集應用程式新增至 Microsoft Intune](../apps/store-apps-ios.md)。

## <a name="plan-for-derived-credentials"></a>規劃衍生認證

設定衍生認證簽發者之前，請先了解下列考量。

### <a name="1-review-the-documentation-for-your-chosen-derived-credential-issuer"></a>1) 檢閱您所選擇之衍生認證簽發者的文件  

設定簽發者之前，請先檢閱該簽發者的文件，以了解其系統如何將衍生認證提供給裝置。

視您選擇的簽發者而定，在註冊時可能需要工作人員來協助使用者完成程序。 您也應該檢閱目前的 Intune 設定，以確保它們不會封鎖裝置或使用者完成認證要求所需的存取。

例如，您可以使用條件式存取來封鎖不符合規範的裝置電子郵件存取。 如果您依賴電子郵件通知來通知使用者啟動衍生認證註冊程序，您的使用者在符合原則之前，可能不會收到這些指示。

同樣地，某些衍生認證要求工作流程需要使用裝置相機來掃描螢幕上的 QR 代碼。 此程式碼會將該裝置連結至驗證要求，該驗證要求是針對具有使用者的智慧卡認證的衍生認證簽發者所產生的。 如果裝置設定原則封鎖相機使用，則使用者無法完成衍生認證註冊要求。

一般資訊：

- 您一次只能為每個租用戶設定單一簽發者，而且該簽發者可供租用戶中的所有使用者和支援的裝置使用。

- 除非您使用需要衍生認證的原則將使用者設為目標，否則不會通知他們必須註冊衍生認證。

- 通知可以透過公司入口網站的應用程式通知、透過電子郵件或透過這兩種方式進行。 如果您選擇使用電子郵件通知，而且您使用已啟用的條件式存取，則使用者可能不會在其裝置不符合規範時收到電子郵件通知。

### <a name="2-review-the-end-user-workflow-for-your-chosen-issuer"></a>2) 檢閱您所選簽發者的終端使用者工作流程

以下是每個支援合作夥伴的重要考慮事項。  請熟悉此資訊，以確保您的 Intune 原則和設定不會封鎖使用者和裝置從該簽發者成功完成衍生認證的註冊。

#### <a name="disa-purebred"></a>DISA Purebred

請檢閱 [DISA Purebred 的使用者工作流程](https://docs.microsoft.com/intune-user-help/enroll-ios-device-disa-purebred)。 此工作流程的主要需求包括：

- 使用者需要存取電腦或 KIOSK，讓他們可以使用智慧卡向簽發者驗證。

- 將註冊衍生認證的裝置必須安裝 Intune 公司入口網站應用程式。

- 使用 Intune [部署 DISA Purebred 應用程式](#deploy-the-disa-purebred-app)到將註冊衍生認證的裝置。 此應用程式必須透過 Intune 部署，才能進行管理，並可以與 Intune 公司入口網站應用程式搭配使用。 裝置使用者會使用此應用程式來完成衍生認證要求。

- DISA Purebred 應用程式需要[個別應用程式 VPN](../configuration/vpn-settings-configure.md)，以確保應用程式可以在註冊衍生認證期間存取 DISA Purebred。

- 裝置使用者必須在註冊程序中使用即時代理程式。 在註冊期間，系統會在使用者進行註冊程序時，提供限時的一次性密碼。

如需取得和設定 DISA Purebred 應用程式的資訊，請參閱此文章稍後的[部署 DISA Purebred 應用程式](#deploy-the-disa-purebred-app)。

#### <a name="entrust-datacard"></a>Entrust Datacard

請檢閱 [Entrust Datacard 的使用者工作流程](https://docs.microsoft.com/intune-user-help/enroll-ios-device-entrust-datacard)。 此工作流程的主要需求包括：

- 使用者需要存取電腦或 KIOSK，讓他們可以使用智慧卡向簽發者驗證。

- 將註冊衍生認證的裝置必須安裝 Intune 公司入口網站應用程式。

- 使用裝置相機來掃描 QR 代碼，以將驗證要求連結至行動裝置的衍生認證要求。

#### <a name="intercede"></a>Intercede

請檢閱 [Intercede 的使用者工作流程](https://docs.microsoft.com/intune-user-help/enroll-ios-device-intercede)。 此工作流程的主要需求包括：

- 使用者需要存取電腦或 KIOSK，讓他們可以使用智慧卡向簽發者驗證。

- 將註冊衍生認證的裝置必須安裝 Intune 公司入口網站應用程式。

- 使用裝置相機來掃描 QR 代碼，以將驗證要求連結至行動裝置的衍生認證要求。

### <a name="3-deploy-a-trusted-root-certificate-to-devices"></a>3) 將受信任的根憑證部署至裝置

受信任的根憑證會與衍生認證搭配使用，以確認衍生認證信任鏈結是有效且受信任的。 即使原則未直接參考，也需要受信任的根憑證。 請參閱[在 Microsoft Intune 中設定您裝置的憑證設定檔](certificates-configure.md)。

### <a name="4-provide-end-user-instructions-for-how-to-get-the-derived-credential"></a>4) 提供如何取得衍生認證的終端使用者指示

為您的使用者建立並提供指引，以了解如何啟動衍生認證註冊程序，以及如何瀏覽您所選簽發者的衍生認證註冊工作流程。

我們建議您提供將裝載指引的 URL。 當您為租用戶設定衍生認證簽發者，而且該 URL 可從公司入口網站應用程式中取得時，您可以指定此 URL。 如果您未指定自己的 URL，Intune 會提供一般詳細資料的連結。 這些詳細資料無法涵蓋所有情節，而且對您的環境而言可能不正確。

### <a name="5-deploy-intune-policies-that-require-derived-credentials"></a>5) 部署需要衍生認證的 Intune 原則

建立新的原則，或編輯現有的原則以使用衍生認證。 衍生的認證會取代應用程式驗證、Wi-Fi、VPN、電子郵件，以及 S/MIME 簽署和加密的其他驗證方法。

避免要求使用衍生認證來存取您將用來作為取得衍生認證之程序一部分的程序，因為這可能會讓使用者無法完成要求。

## <a name="set-up-a-derived-credential-issuer"></a>設定衍生認證簽發者

在您建立需要使用衍生認證的原則之前，請先在 Intune 主控台中設定認證簽發者。 衍生認證簽發者是整個租用戶的設定。 租用戶一次只支援單一簽發者。

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [租用戶系統管理]   > [連接器與權杖]   > [衍生認證]  。

    > [!div class="mx-imgBorder"]
    > ![在主控台中設定衍生認證](./media/derived-credentials/configure-provider.png)

3. 針對衍生認證簽發者原則指定易記的**顯示名稱**。  您的裝置使用者不會看到此名稱。

4. 針對**衍生認證簽發者**，請選取您為租使用者選擇的衍生認證簽發者：
   - DISA Purebred
   - Entrust Datacard
   - Intercede  

5. 指定**衍生認證說明 URL** 以提供包含自訂指示的位置連結，以協助使用者取得貴組織的衍生認證。 這些指示應該專屬於您的組織，以及專屬於從所選簽發者取得認證所需的工作流程。 連結會出現在公司入口網站應用程式中，而且應該可從裝置存取。

   如果您未指定自己的 URL，Intune 會提供無法涵蓋所有情節之一般詳細資料的連結。 針對您的環境，此一般指引可能不正確。

6. 針對**通知類型**選取一或多個選項。 通知類型是您用來通知使用者有關下列情節的方法：

   - 向簽發者註冊裝置，以取得新的衍生認證。
   - 當目前的認證接近到期時，取得新的衍生認證。
   - 使用衍生認證搭配 Wi-Fi、VPN、電子郵件或應用程式驗證，以及 S/MIME 簽署和加密的原則。

7. 準備好時，請選取 [儲存]  以完成衍生認證簽發者的設定。

儲存設定之後，除了 [衍生認證簽發者]  以外，您可以對所有欄位進行變更。  若要變更簽發者，請參閱[變更衍生認證簽發者](#change-the-derived-credential-issuer)。

## <a name="deploy-the-disa-purebred-app"></a>部署 DISA Purebred 應用程式

本節僅適用於使用 DISA Purebred 時  。

若要使用 **DISA Purebred** 作為 Intune 的衍生認證簽發者，您必須取得 DISA Purebred 應用程式，然後使用 Intune 將應用程式部署至裝置。 裝置使用者會在其裝置上使用應用程式，以向 DISA Purebred 要求衍生認證。

除了使用 Intune 部署應用程式之外，也請針對 DISA Purebred 應用程式設定 Intune 個別應用程式 VPN。

**請完成下列工作**：
  
1. 下載 [DISA Purebred 應用程式](https://cyber.mil/pki-pke/purebred/)。
2. 在 Intune 中部署 DISA Purebred 應用程式。  請參閱[將 iOS 企業營運應用程式新增至 Microsoft Intune](../apps/lob-apps-ios.md)。
3. 針對 DISA Purebred 應用程式[建立個別應用程式 VPN](../configuration/vpn-settings-configure.md)。

## <a name="use-derived-credentials-for-authentication-and-smime-signing-and-encryption"></a>使用衍生認證進行驗證和 S/MIME 簽署和加密

您可以針對下列設定檔類型和用途，指定**衍生認證**：

- [應用程式](#use-derived-credentials-for-app-authentication)
- [電子郵件](../configuration/email-settings-ios.md)
- [VPN](../configuration/vpn-settings-ios.md)
- [S/MIME 簽署和加密](certificates-s-mime-encryption-sign.md)
- [Wi-Fi](../configuration/wi-fi-settings-ios.md)

  針對 Wi-Fi 設定檔，只有在 [EAP 類型]  設定為下列其中一個值時，才可以使用驗證方法  ：
  - EAP – TLS
  - EAP-TTLS
  - PEAP

### <a name="use-derived-credentials-for-app-authentication"></a>使用衍生認證進行應用程式驗證

針對網站和應用程式使用衍生認證進行憑證型驗證。 傳遞衍生認證進行應用程式驗證：

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [裝置]   > [組態設定檔]   > [建立設定檔]  。
3. 輸入下列設定：

    - **名稱**：為設定檔輸入描述性名稱。 命名您的設定檔，以方便之後能輕鬆識別。 例如，**iOS 裝置設定檔的衍生認證**是良好的設定檔名稱。
    - **描述**：輸入描述來概述設定和其他重要的詳細資料。
    - **平台**：選取 [iOS/iPadOS]  。
    - **設定檔類型**：選取 [衍生認證]  。

4. 按一下 [確定]  以儲存您的變更。
5. 完成時，選取 [確定]   > [建立]  以建立 Intune 設定檔。 完成時，您的設定檔會顯示在 [裝置 - 設定檔]  清單中。
6. 選取您的新設定檔 > [指派]  。 選取應接收原則的群組。
 
使用者會根據您在設定衍生認證簽發者時所指定的設定，接收應用程式或電子郵件通知。 通知會通知使用者啟動公司入口網站，以便處理衍生認證原則。

## <a name="renew-a-derived-credential"></a>更新衍生認證

無法擴充或更新衍生認證。 相反地，使用者必須使用認證要求工作流程來要求其裝置的新衍生認證。

如果您針對**通知類型**設定一或多個方法，Intune 會在目前的衍生認證達到其生命範圍的 80% 時，自動通知使用者。 通知會引導使用者完成認證要求程序，以取得新的衍生認證。

在裝置收到新的衍生認證之後，會將使用衍生認證的原則重新部署到該裝置。


## <a name="change-the-derived-credential-issuer"></a>變更衍生認證簽發者

在租用戶層級中，您可以變更認證簽發者，但一次只支援一個租用戶一個簽發者。

在您變更簽發者之後，系統會提示使用者從新的簽發者取得新的衍生認證。 他們必須先這麼做，才能使用衍生認證進行驗證。

### <a name="change-the-issuer-for-your-tenant"></a>變更租用戶的簽發者

> [!IMPORTANT]  
> 如果您刪除簽發者並立即重新設定相同的簽發者，您仍然必須更新設定檔和裝置，以使用來自該簽發者的衍生認證。 在您刪除簽發者之前取得的衍生認證已不再有效。

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [租用戶系統管理]   > [連接器與權杖]   > [衍生認證]  。
3. 選取 [刪除]  以移除目前的衍生認證簽發者。
4. 設定新的簽發者。

### <a name="update-profiles-that-use-derived-credentials"></a>更新使用衍生認證的設定檔

當您刪除簽發者，然後新增一個新的之後，請編輯每個使用衍生認證的設定檔。 即使您還原先前的簽發者，也適用此規則。 設定檔的任何編輯都會觸發更新，包括針對設定檔 [描述]  進行簡單編輯。

### <a name="update-derived-credentials-on-devices"></a>更新裝置上的衍生認證

當您刪除簽發者，然後新增一個新的之後，裝置使用者必須要求新的衍生認證。 即使您加入所移除的相同簽發者，也適用此規則。 要求新衍生認證的程序，與註冊新裝置或更新現有認證的程序相同。

## <a name="next-steps"></a>後續步驟

[建立裝置組態設定檔](../configuration/device-profile-create.md)。
