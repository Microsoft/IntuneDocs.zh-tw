---
title: 在 Microsoft Intune - Azure 中建立憑證設定檔 | Microsoft Docs
description: 了解使用簡單憑證註冊通訊協定 (SCEP) 或公開金鑰加密標準 (PKCS) 憑證和憑證設定檔搭配 Microsoft Intune。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 63fa9f461fc9884d8c21e40cb4b5e3831f3b4b03
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576534"
---
# <a name="use-certificates-for-authentication-in-microsoft-intune"></a>在 Microsoft Intune 中使用憑證進行驗證

搭配使用憑證和 Intune，透過 VPN、Wi-Fi 或電子郵件設定檔來向應用程式和公司資源驗證您的使用者。 當您使用憑證來驗證這些連線時，您的使用者即不需要輸入使用者名稱和密碼，這可以讓他們順暢存取。 憑證也可用於使用 S/MIME 簽署和加密電子郵件。

## <a name="intune-supported-certificates-and-usage"></a>Intune 支援的憑證與使用方式

| 類型              | 驗證 | S/MIME 簽署 | S/MIME 加密  |
|--|--|--|--|
| 公開金鑰加密標準 (PKCS) 匯入的憑證 |  | ![支援](./media/certificates-configure/green-check.png) | ![支援](./media/certificates-configure/green-check.png)|
| PKCS#12 (或 PFX)    | ![支援](./media/certificates-configure/green-check.png) | ![支援](./media/certificates-configure/green-check.png) |  |
| 簡單憑證註冊通訊協定 (SCEP)  | ![支援](./media/certificates-configure/green-check.png) | ![支援](./media/certificates-configure/green-check.png) | |

若要部署這些憑證，請建立憑證設定檔並將其指派給裝置。

您所建立的每個個別憑證設定檔都支援單一平台。 例如，如果您使用 PKCS 憑證，請為 Android 建立一個 PKCS 憑證設定檔，並為 iOS/iPadOS 建立另一個 PKCS 憑證設定檔。 如果您也要將 SCEP 憑證用於這兩個平台，您可以為 Android 建立一個 SCEP 憑證設定檔，並為 iOS/iPadOS 建立另一個。

### <a name="general-considerations-when-you-use-a-microsoft-certification-authority"></a>使用 Microsoft 憑證授權單位時的一般考量

當您使用 Microsoft 憑證授權單位 (CA) 時：

- 若要使用 SCEP 憑證設定檔，您必須[設定網路裝置註冊服務 (NDES) 伺服器](certificates-scep-configure.md#set-up-ndes)以搭配 Intune 使用。
- 若要使用下列憑證設定檔類型，您必須[安裝 Microsoft Intune 憑證連接器](certificates-scep-configure.md#install-the-intune-certificate-connector)：
  - SCEP 憑證設定檔
  - PKCS 憑證設定檔

- 使用已匯入 PKCS 的憑證：
  - [安裝適用於 Microsoft Intune 的 PFX 憑證連接器](certificates-imported-pfx-configure.md#download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune)。
  - 從憑證受權單位匯出憑證，然後將它們匯入 Microsoft Intune。 請參閱 [PFXImport PowerShell 專案](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell)。

- 使用下列機制來部署憑證：
  - [受信任的憑證設定檔](certificates-configure.md#create-trusted-certificate-profiles)，以將來自您的根或中繼 (發行) CA 的受信任根 CA 憑證部署到裝置
  - SCEP 憑證設定檔
  - PKCS 憑證設定檔
  - 已匯入 PKCS 的憑證設定檔

### <a name="general-considerations-when-you-use-a-third-party-certification-authority"></a>使用協力廠商憑證授權單位時的一般考量

當您使用協力廠商 (非 Microsoft) 憑證授權單位 (CA) 時：

- 使用 SCEP 憑證設定檔：
  - 設定與來自[我們其中一個支援合作夥伴](certificate-authority-add-scep-overview.md#third-party-certification-authority-partners)的協力廠商 CA 之間的整合。 該設定會包含來自協力廠商 CA 的指示，以完成其 CA 與 Intune 之間的整合。
  - [在 Azure AD 中建立應用程式](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration)以將權限委派給 Intune 來執行 SCEP 憑證挑戰驗證。

- 已匯入 PKCS 的憑證需要您[安裝適用於 Microsoft Intune 的 PFX 憑證連接器](certificates-imported-pfx-configure.md#download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune)。

- 使用下列機制來部署憑證：
  - [受信任的憑證設定檔](certificates-configure.md#create-trusted-certificate-profiles)，以將來自您的根或中繼 (發行) CA 的受信任根 CA 憑證部署到裝置
  - SCEP 憑證設定檔
  - PKCS 憑證設定檔 (僅支援 [Digicert PKI 平台](certificates-digicert-configure.md)) 
  - 已匯入 PKCS 的憑證設定檔

## <a name="supported-platforms-and-certificate-profiles"></a>支援的平台和憑證設定檔

| 平台              | 受信任的憑證設定檔 | PKCS 憑證設定檔 | SCEP 憑證設定檔 | PKCS 匯入的憑證設定檔  |
|--|--|--|--|---|
| Android 裝置管理員 | ![支援](./media/certificates-configure/green-check.png) | ![支援](./media/certificates-configure/green-check.png) | ![支援](./media/certificates-configure/green-check.png)|  ![支援](./media/certificates-configure/green-check.png) |
| Android 企業 <br> - 完全受控 (裝置擁有者)   | ![支援](./media/certificates-configure/green-check.png) |   | ![支援](./media/certificates-configure/green-check.png) |   |
| Android 企業 <br> - 專用 (裝置擁有者)   | ![支援](./media/certificates-configure/green-check.png)  |   | ![支援](./media/certificates-configure/green-check.png)  |   |
| Android 企業 <br> - 工作設定檔    | ![支援](./media/certificates-configure/green-check.png) | ![支援](./media/certificates-configure/green-check.png) | ![支援](./media/certificates-configure/green-check.png) | ![支援](./media/certificates-configure/green-check.png) |
| iOS/iPadOS                   | ![支援](./media/certificates-configure/green-check.png) | ![支援](./media/certificates-configure/green-check.png) | ![支援](./media/certificates-configure/green-check.png) | ![支援](./media/certificates-configure/green-check.png) |
| macOS                 | ![支援](./media/certificates-configure/green-check.png) |  ![支援](./media/certificates-configure/green-check.png) |![支援](./media/certificates-configure/green-check.png)|![支援](./media/certificates-configure/green-check.png)|
| Windows Phone 8.1     |![支援](./media/certificates-configure/green-check.png)  |  | ![支援](./media/certificates-configure/green-check.png)| ![支援](./media/certificates-configure/green-check.png) |
| Windows 8.1 及更新版本 |![支援](./media/certificates-configure/green-check.png)  |  |![支援](./media/certificates-configure/green-check.png) |   |
| Windows 10 及更新版本  | ![支援](./media/certificates-configure/green-check.png) | ![支援](./media/certificates-configure/green-check.png) | ![支援](./media/certificates-configure/green-check.png) | ![支援](./media/certificates-configure/green-check.png) |

## <a name="export-the-trusted-root-ca-certificate"></a>匯出受信任的根 CA 憑證

若要使用 PKCS、SCEP 和 PKCS 匯入的憑證設定檔，裝置必須信任您的根憑證授權單位。 若要建立信任，請將受信任的根 CA 憑證，以及任何中繼或發行憑證授權單位憑證匯出為公開憑證 (.cer)。 您可以透過發行 CA 取得這些憑證，或透過信任您發行 CA 的任何裝置取得這些憑證。

若要匯出憑證，請參閱您的憑證授權單位文件。 您必須將公開憑證匯出成 .cer 檔案。  請不要匯出私密金鑰 .pfx 檔。

當您[建立受信任的憑證設定檔](#create-trusted-certificate-profiles)時，您可以使用這個 .cer 檔案，以將該憑證部署到裝置。

## <a name="create-trusted-certificate-profiles"></a>建立受信任的憑證設定檔

您必須先建立受信任的憑證設定檔，才能建立 SCEP、PKCS 或 PKCS 匯入的憑證設定檔。 部署受信任的憑證設定檔時，您可確保每部裝置都能辨識 CA 的合法性。 SCEP 憑證設定檔會直接參考受信任的憑證設定檔。 PKCS 憑證設定檔不會直接參考受信任的憑證設定檔，但會直接參考裝載 CA 的伺服器。 PKCS 匯入的憑證設定檔不會直接參考受信任的憑證設定檔，但可以在裝置上使用。 將受信任的憑證設定檔部署到裝置，即可確保建立此信任。 當裝置不信任根 CA 時，SCEP 或 PKCS 憑證設定檔便會失敗。

針對每個您想要支援的裝置平台，建立個別的受信任憑證設定檔，如同您針對 SCEP、PKCS 和 PKCS 所匯入憑證設定檔進行的作業一樣。

### <a name="to-create-a-trusted-certificate-profile"></a>建立可信任的憑證設定檔

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 選取 [裝置]   > [組態設定檔]   > [建立設定檔]  。

   ![巡覽至 Intune 並建立受信任憑證的新設定檔](./media/certficates-pfx-configure/certificates-pfx-configure-profile-new.png)

3. 輸入下列內容：

   - 設定檔的 [名稱] 
   - 選擇性設定 [描述] 
   - 要部署設定檔的目標 [平台] 
   - 將 [設定檔類型]  設為 [信任的憑證] 

4. 選取 [設定]  ，然後瀏覽至先前匯出要與此憑證設定檔搭配使用的受信任根 CA 憑證 .cer 檔案，然後選取 [確定]  。

5. 僅適用於 Windows 8.1 與 Windows 10 裝置，請為來自以下位置的受信任憑證，選取 [目的地存放區]  ︰

   - **電腦憑證存放區 - 根**
   - **電腦憑證存放區 - 中繼**
   - **使用者憑證存放區 - 中繼**

6. 當您完成時，請選擇 [確定]  返回 [建立設定檔]  窗格，然後選取 [建立]  。

[裝置 - 組態設定檔]  視窗的設定檔清單中隨即顯示設定檔，且設定檔類型為 [受信任的憑證]  。 請務必將此設定檔指派給使用 SCEP 或 PKCS 憑證的裝置。 若要將設定檔指派給群組，請參閱[指派裝置設定檔](../configuration/device-profile-assign.md)。

> [!NOTE]
> Android 裝置可能會顯示協力廠商已安裝受信任憑證的訊息。

## <a name="additional-resources"></a>其他資源

- [指派裝置設定檔](../configuration/device-profile-assign.md)  
- [使用 S/MIME 簽署和加密電子郵件](certificates-s-mime-encryption-sign.md)  
- [使用協力廠商憑證授權單位](certificate-authority-add-scep-overview.md)  

## <a name="next-steps"></a>後續步驟

為您要使用的每個平台建立 SCEP、PKCS 或 PKCS 匯入的憑證設定檔。 若要繼續，請參閱下列文章：

- [設定基礎結構以支援 SCEP 憑證與 Intune](certificates-scep-configure.md)  
- [透過 Intune 設定並管理 PKCS 憑證](certficates-pfx-configure.md)  
- [建立 PKCS 匯入的憑證設定檔](certificates-imported-pfx-configure.md#create-a-pkcs-imported-certificate-profile)
