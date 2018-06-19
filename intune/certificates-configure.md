---
title: 在 Microsoft Intune - Azure 中建立憑證設定檔 | Microsoft Docs
description: 針對您的裝置，設定 SCEP 或 PKCS 憑證環境來新增或建立憑證設定檔、匯出公開憑證、在 Azure 入口網站中建立設定檔，然後將 SCEP 或 PKCS 指派給 Azure 入口網站之 Microsoft Intune 中憑證設定檔
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 89f8ddc105787bc7ff4f7cfc1e226d28589ecbbf
ms.sourcegitcommit: 9536300a6211bac4bdc733593a40c1ae47611de3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2018
ms.locfileid: "31771800"
---
# <a name="configure-a-certificate-profile-for-your-devices-in-microsoft-intune"></a>在 Microsoft Intune 中設定您裝置的憑證設定檔

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

當您授與使用者透過 VPN、Wi-Fi 或電子郵件設定檔存取公司資源的權限時，您可以使用憑證來驗證這些連線。 當您使用憑證時，不需要輸入使用者名稱和密碼來驗證連線

您可以使用 Intune 來將這些憑證指派到您管理的裝置。 Intune 支援指派和管理下列憑證類型：

- 簡單憑證註冊通訊協定 (SCEP)
- PKCS#12 (或 PFX)

其中的每種憑證都有各自的必要條件，以及基礎結構需求。

## <a name="overview"></a>概觀

1. 確定您已備妥正確的憑證基礎結構。 您可使用 [SCEP 憑證](certificates-scep-configure.md) 與 [PKCS 憑證](certficates-pfx-configure.md)。

2. 在每部裝置上安裝根憑證或中繼憑證授權單位 (CA) 憑證，讓裝置可以辨識 CA 的合法性。 若要執行此作業，請建立並指派**信任的憑證設定檔**。 當您指派此設定檔時，您以 Intune 管理的裝置就會要求並收到根憑證。 您必須為每個平台分別建立設定檔。 提供下列平台可用的受信任憑證設定檔︰

    - iOS 8.0 和更新版本
    - macOS 10.11 及更新版本
    - Android 4.0 及更新版本
    - Android for Work
    - Windows 8.1 及更新版本
    - Windows Phone 8.1 和更新版本
    - Windows 10 及更新版本

3. 建立憑證設定檔，讓每個裝置要求一個用於驗證 VPN、Wi-Fi 和電子郵件存取的憑證。 您可為執行下列平台的裝置，建立並指派 **PKCS** 或 **SCEP** 憑證設定檔︰

   - iOS 8.0 和更新版本
   - Android 4.0 及更新版本
   - Android for Work
   - Windows 10 (桌面版和行動裝置版) 和更新版本

   針對執行下列平台的裝置，您只能使用 **SCEP 憑證設定檔**：

   - macOS 10.9 及更新版本
   - Windows Phone 8.1 和更新版本

請務必為每個裝置平台建立不同的設定檔。 當您建立設定檔時，請將該設定檔與您已建立之受信任的根憑證設定檔相關聯。

### <a name="further-considerations"></a>進一步考量

- 如果您沒有企業憑證授權單位，則必須建立一個
- 如果您使用 SCEP 設定檔，請設定網路裝置註冊服務 (NDES) 伺服器
- 不論是否預計使用 SCEP 或 PKCS 設定檔，都請下載和設定 Microsoft Intune 憑證連接器


## <a name="step-1-configure-your-certificate-infrastructure"></a>步驟 1：設定您的憑證基礎結構

如需設定憑證設定檔每種類型基礎結構的說明，請參閱下列主題之一：

- [透過 Intune 設定並管理 SCEP 憑證](certificates-scep-configure.md)
- [透過 Intune 設定並管理 PKCS 憑證](certficates-pfx-configure.md)


## <a name="step-2-export-your-trusted-root-ca-certificate"></a>步驟 2：匯出受信任的根 CA 憑證

從發行 CA 或信任發行 CA 的任何裝置，將可信任的根憑證授權單位匯出為公開憑證 (.cer)。 不要匯出私密金鑰 (.pfx)。

在設定受信任的憑證設定檔時，匯入此憑證。

## <a name="step-3-create-trusted-certificate-profiles"></a>步驟 3：建立可信任的憑證設定檔
先建立受信任的憑證設定檔，才能建立 SCEP 或 PKCS 憑證設定檔。 每個裝置平台都需要一個受信任的憑證設定檔以及 SCEP 或 PKCS 設定檔。 針對每個裝置平台，建立受信任憑證的步驟皆相似。

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 窗格中，選擇 [裝置設定]。
2. 在 [裝置設定] 窗格中，選擇 [管理] >  [設定檔]。
3. 在 [設定檔] 窗格中，選擇 [建立設定檔]。
4. 在 [建立設定檔] 窗格中，為受信任的憑證設定檔輸入 [名稱] 及 [描述]。
5. 從 [平台] 下拉式清單中，選取此受信任憑證的裝置平台。 您目前可為憑證設定選擇下列其中一個平台︰

    - **Android**
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 及更新版本**
    - **Windows 10 及更新版本**

6. 從 [設定檔類型] 下拉式清單中，選擇 [受信任的憑證]。
7. 瀏覽至您於工作 1 中所儲存的憑證，然後按一下 [確定]。
8. 僅適用於 Windows 8.1 與 Windows 10 裝置，請為來自以下位置的受信任憑證，選取 [目的地存放區]︰
    - **電腦憑證存放區 - 根**
    - **電腦憑證存放區 - 中繼**
    - **使用者憑證存放區 - 中繼**
8. 當您完成時，請選擇 [確定] 返回 [建立設定檔] 窗格，然後選取 [建立]。

會建立設定檔，而且會出現在清單中。 若要將此設定檔指派給群組，請參閱[指派裝置設定檔](device-profile-assign.md)。

Android 裝置可能會顯示協力廠商已安裝受信任憑證的訊息。

## <a name="step-4-create-scep-or-pkcs-certificate-profiles"></a>步驟 4：建立 SCEP 或 PKCS 憑證設定檔

如需設定及指派憑證設定檔每種類型的說明，請參閱下列主題之一：

- [透過 Intune 設定並管理 SCEP 憑證](certificates-scep-configure.md)
- [透過 Intune 設定並管理 PKCS 憑證](certficates-pfx-configure.md)

建立受信任的憑證設定檔之後，請為您要使用的每個平台，建立 SCEP 或 PKCS 憑證設定檔。 建立 SCEP 憑證設定檔時，請輸入該相同平台的受信任憑證設定檔。 此步驟會連結兩個憑證設定檔，但您仍然必須分別指派每個設定檔。

## <a name="next-steps"></a>接下來的步驟
請參閱[如何指派裝置設定檔](device-profile-assign.md)，以取得如何指派裝置設定檔的一般資訊。
