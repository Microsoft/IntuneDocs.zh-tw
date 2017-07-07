---
title: "如何使用 Intune 設定憑證"
titleSuffix: Intune on Azure
description: "了解如何使用 Intune 來建立及指派憑證，協助您保護 Wi-Fi、VPN 與其他連線的安全。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 06/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: da23a0c79c5e0e178e52e956561e2764268d09df
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-configure-certificates-in-microsoft-intune"></a>如何在 Microsoft Intune 中設定憑證

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

當您授與使用者透過 VPN、Wi-Fi 或電子郵件設定檔存取公司資源的權限時，您可以使用憑證來驗證這些連線。 這樣就不必輸入使用者名稱和密碼來驗證連線。

您可以使用 Intune 來將這些憑證指派到您管理的裝置。 Intune 支援指派及管理這些憑證類型：

- 簡單憑證註冊通訊協定 (SCEP)
- PKCS#12 (或 PFX)

其中的每種憑證都有各自的先決條件，以及基礎結構需求。

## <a name="general-workflow"></a>一般工作流程

1. 確定您已備妥正確的憑證基礎結構。 您可使用 [SCEP 憑證](certificates-scep-configure.md) 與 [PKCS 憑證](certficates-pfx-configure.md)。
2. 在每部裝置上安裝根憑證或中繼憑證授權單位 (CA) 憑證，讓裝置可以辨識 CA 的合法性。 若要執行此作業，請建立並指派**信任的憑證設定檔**。 當您指派此設定檔時，您以 Intune 管理的裝置就會要求並收到根憑證。 每個平台必須分別建立各自的設定檔。 提供以下這些平台的受信任憑證設定檔︰
    - iOS 8.0 和更新版本
    - macOS 10.9 及更新版本
    - Android 4.0 及更新版本
    - Android for Work
    - Windows 8.1 及更新版本
    - Windows Phone 8.1 和更新版本
    - Windows 10 及更新版本
3. 建立憑證設定檔，讓每個裝置要求一個用於驗證 VPN、Wi-Fi 和電子郵件存取的憑證。 您可為執行這些平台的裝置，建立並指派 **PKCS** 或 **SCEP** 憑證設定檔︰
    - iOS 8.0 和更新版本
    - Android 4.0 及更新版本
    - Android for Work
    - Windows 10 (桌面版和行動裝置版) 和更新版本

    只有這些平台才可使用 SCEP 憑證設定檔：

-   macOS 10.9 及更新版本
-   Windows Phone 8.1 和更新版本

您必須為每個裝置平台建立自己的設定檔。 當您建立設定檔時，請將該設定檔與您已建立之受信任的根憑證設定檔相關聯。

### <a name="further-considerations"></a>進一步考量

- 如果沒有企業憑證授權單位，您必須建立一個。
- 如果您決定 (根據裝置平台) 使用簡單憑證註冊通訊協定 (SCEP) 設定檔，您也需要設定網路裝置註冊服務 (NDES) 伺服器。
- 無論是否預計會使用 SCEP 或 PKCS 設定檔，您都必須下載及設定 Microsoft Intune 憑證連接器。


## <a name="step-1--configure-your-certificate-infrastructure"></a>步驟 1：設定您的憑證基礎結構

如需設定憑證設定檔每種類型基礎結構的說明，請參閱下列主題之一：

- [透過 Intune 設定並管理 SCEP 憑證](certificates-scep-configure.md)
- [透過 Intune 設定並管理 PKCS 憑證](certficates-pfx-configure.md)


## <a name="step-2---export-your-trusted-root-ca-certificate"></a>步驟 2：匯出受信任的根 CA 憑證

從發行 CA 或信任發行 CA 的任何裝置，將可信任的根憑證授權單位匯出為 **.cer** 檔案。 不要匯出私密金鑰。

當您設定受信任的憑證設定檔時，會匯入此憑證。

## <a name="step-3-create-trusted-certificate-profiles"></a>步驟 3：建立可信任的憑證設定檔
您必須先建立受信任的憑證設定檔，然後才可建立 SCEP 或 PKCS 憑證設定檔。 每個裝置平台都需要一個受信任的憑證設定檔以及 SCEP 或 PKCS 設定檔。 針對每種裝置平台，建立受信任憑證的流程皆相似。

### <a name="to-create-a-trusted-certificate-profile"></a>建立可信任的憑證設定檔

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置設定]。
2. 在 [裝置設定] 刀鋒視窗中，選擇 [管理]  >  [設定檔]。
3. 在設定檔刀鋒視窗中，選擇 [建立設定檔]。
4. 在 [建立設定檔] 刀鋒視窗中，為受信任的憑證設定檔輸入 [名稱] 及 [描述]。
5. 從 [平台] 下拉式清單中，選取此受信任憑證的裝置平台。 您目前可為憑證設定選擇下列其中一個平台︰
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 及更新版本**
    - **Windows 10 及更新版本**
6. 從 [設定檔類型] 下拉式清單中，選擇 [信任的憑證]。
7. 瀏覽至您於工作 1 中所儲存的憑證，然後按一下 [確定]。
8. 僅適用於 Windows 8.1 與 Windows 10 裝置，請為來自以下位置的受信任憑證，選取 [目的地存放區]︰
    - **電腦憑證存放區 - 根**
    - **電腦憑證存放區 - 中繼**
    - **使用者憑證存放區 - 中繼**
8. 完成後，請選擇 [確定]返回 [建立設定檔] 刀鋒視窗，然後點擊 [建立]。

隨即會建立設定檔，並會出現在 [設定檔清單] 刀鋒視窗上。

若想繼續，並將此設定檔指派給群組，請參閱[如何指派裝置設定檔](device-profile-assign.md)。


> [!Note]
> Android 裝置會顯示協力廠商已安裝受信任憑證的通知。

## <a name="step-4-create-scep-or-pkcs-certificate-profiles"></a>步驟 4：建立 SCEP 或 PKCS 憑證設定檔

如需設定及指派憑證設定檔每種類型的說明，請參閱下列主題之一：

- [透過 Intune 設定並管理 SCEP 憑證](certificates-scep-configure.md)
- [透過 Intune 設定並管理 PKCS 憑證](certficates-pfx-configure.md)

建立受信任的憑證設定檔之後，請為您要使用的每個平台，建立 SCEP 或 PKCS 憑證設定檔。 建立 SCEP 憑證設定檔時，必須為該相同的平台指定受信任的憑證設定檔。 如此即會連結兩個憑證設定檔，但您仍然必須分別指派每個設定檔。


## <a name="next-steps"></a>後續步驟
請參閱[如何指派裝置設定檔](device-profile-assign.md)，以取得如何指派裝置設定檔的一般資訊。
