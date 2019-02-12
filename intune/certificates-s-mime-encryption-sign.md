---
title: 使用 S/MIME 簽署和加密電子郵件 - Microsoft Intune - Azure | Micrososft Docs
description: 了解如何使用 Microsoft Intune 中的電子郵件數位憑證來簽署和加密裝置上的電子郵件。 這些憑證稱為 S/MIME，並使用裝置組態設定檔加以設定。 簽署和加密憑證會用 PKCS 或私人憑證，並使用連接器來匯入憑證。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: eee495e1294392e495a1f8f632fa33c37325a9dd
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55842536"
---
# <a name="smime-overview-to-sign-and-encrypt-email-in-intune"></a>在 Intune 中簽署和加密電子郵件的 S/MIME 概觀

電子郵件憑證 (也就是 S/MIME 憑證) 可使用加密和解密，為您的電子郵件通訊提供額外的安全性。 Microsoft Intune 可以在執行下列平台的行動裝置上，使用 S/MIME 憑證來簽署及加密電子郵件：

- Android
- iOS
- macOS
- Windows 10 及更新版本
- Windows Phone

在 iOS 裝置上，您可以建立受 Intune 管理的電子郵件設定檔，使用 S/MIME 和憑證來簽署及加密內送和外寄電子郵件。 至於其他平台，則不一定支援 S/MIME。 如果支援，請安裝使用 S/MIME 簽署和加密的憑證。 然後，終端使用者會在其電子郵件應用程式中啟用 S/MIME。

如需使用 Exchange 進行 S/MIME 電子郵件簽署和加密的詳細資訊，請參閱 [S/MIME for message signing and encryption](https://docs.microsoft.com/Exchange/policy-and-compliance/smime) (用於訊息簽署和加密的 S/MIME)。

本文提供使用 S/MIME 憑證來簽署和加密裝置上電子郵件的概觀。

## <a name="signing-certificates"></a>簽署憑證

用於簽署的憑證可讓用戶端電子郵件應用程式安全地與電子郵件伺服器通訊。

若要使用簽署憑證，請在您的憑證授權單位 (CA) 建立專注於簽署的範本。 在 Microsoft Active Directory 憑證授權單位，[Configure the server certificate template](https://docs.microsoft.com/windows-server/networking/core-network-guide/cncg/server-certs/configure-the-server-certificate-template) (設定伺服器的憑證範本) 會列出建立憑證範本的步驟。

Intune 中的簽署憑證使用 PKCS 憑證。 [設定並使用 PKCS 憑證](certficates-pfx-configure.md)說明如何在您的 Intune 環境中部署及使用 PKCS 憑證。 這些步驟包括：

- 下載並安裝 Microsoft Intune 憑證連接器以支援 PKCS 憑證要求。
- 為您的裝置建立受信任的根憑證設定檔。 此步驟包含針對您的憑證授權單位使用受信任的根和中繼憑證，然後將設定檔部署到裝置。
- 使用您建立的憑證範本來建立 PKCS 憑證設定檔。 此設定檔會將簽署憑證發行給裝置，並將 PKCS 憑證設定檔部署到裝置。

您也可以匯入特定使用者的簽署憑證。 簽署憑證會部署到使用者註冊的任何裝置。 若要將憑證匯入 Intune，請使用 [GitHub 中的 PowerShell Cmdlet](https://github.com/Microsoft/Intune-Resource-Access)。 若要部署匯入 Intune 以用於電子郵件簽署的 PKCS 憑證，請依照[透過 Intune 設定並使用 PKCS 憑證](certficates-pfx-configure.md)中的步驟進行。 這些步驟包括：

- 下載並安裝適用於 Microsoft Intune 的 PFX 憑證連接器。 此連接器會將匯入的 PKCS 憑證提供給裝置。
- 將 S/MIME 電子郵件簽署憑證匯入 Intune。
- 建立 PKCS 匯入憑證設定檔。 此設定檔會將匯入的 PKCS 憑證提供給適當的使用者裝置。

## <a name="encryption-certificates"></a>加密憑證

用於加密的憑證會確認只有預定收件者才能將加密的電子郵件解密。 S/MIME 加密是可用於電子郵件通訊的額外一層安全性。

將加密的電子郵件傳送給其他使用者時，系統會取得該使用者加密憑證的公開金鑰，然後將您傳送的電子郵件加密。 收件者會使用其裝置上的私密金鑰將電子郵件解密。 使用者可以有用來加密電子郵件之憑證的記錄。 您必須將每個憑證部署到特定使用者的所有裝置，才能將其電子郵件成功解密。

建議不要在 Intune 中建立電子郵件加密憑證。 雖然 Intune 支援發行支援加密的 PKCS 憑證，但 Intune 會針對每部裝置建立唯一的憑證。 每部裝置有唯一憑證並不適合 S/MIME 加密案例，其中加密憑證應該在使用者的所有裝置之間共用。

若要使用 Intune 部署 S/MIME 憑證，您必須將使用者的所有加密憑證匯入 Intune。 Intune 接著會將所有憑證部署到使用者註冊的每部裝置。 若要將憑證匯入 Intune，請使用 [GitHub 中的 PowerShell Cmdlet](https://github.com/Microsoft/Intune-Resource-Access)。

若要部署匯入 Intune 以用於電子郵件加密的 PKCS 憑證，請依照[透過 Intune 設定並使用 PKCS 憑證](certficates-pfx-configure.md)中的步驟進行。 這些步驟包括：

- 下載並安裝適用於 Microsoft Intune 的 PFX 憑證連接器。 此連接器會將匯入的 PKCS 憑證提供給裝置。
- 將 S/MIME 電子郵件加密憑證匯入 Intune。
- 建立 PKCS 匯入憑證設定檔。 此設定檔會將匯入的 PKCS 憑證提供給適當的使用者裝置。

 > [!NOTE]
 > 當移除公司資料時，或當使用者從管理中取消註冊時，Intune 會移除匯入的 S/MIME 加密憑證。 但不會在憑證授權單位撤銷憑證。

## <a name="smime-email-profiles"></a>S/MIME 電子郵件設定檔

建立 S/MIME 簽署和加密憑證設定檔之後，您可以[為 iOS 原生郵件啟用 S/MIME](email-settings-ios.md)。

## <a name="next-steps"></a>後續步驟

- [使用 SCEP 憑證](certificates-scep-configure.md)
- [使用 PKCS 憑證](certficates-pfx-configure.md)
- [使用合作夥伴 CA](certificate-authority-add-scep-overview.md)
- [從 Symantec PKI Manager Web 服務發行 PKCS 憑證](certificates-symantec-configure.md)
