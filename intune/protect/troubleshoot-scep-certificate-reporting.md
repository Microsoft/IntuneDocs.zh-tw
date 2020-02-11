---
title: 當您搭配 Microsoft Intune 使用 SCEP 時，針對成功將憑證部署至裝置的報告進行疑難排解 | Microsoft Docs
description: 針對 NDES 與 Intune 連接器有關成功部署憑證 (使用 SCEP 憑證設定檔佈建) 的報告進行疑難排解。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/30/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2ccc738626efc140efca46d1b997164ed36dd37f
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "76916015"
---
# <a name="troubleshoot-ndes-reporting-of-certificate-deployments-in-microsoft-intune"></a>針對 Microsoft Intune 中憑證部署的 NDES 報告進行疑難排解

使用下列資訊來確認 NDES 與 Microsoft Intune 憑證連接器成功向 Intune 報告憑證已傳遞至裝置。 向 Intune 報告是使用 SCEP 憑證設定檔以憑證佈建 Windows 裝置的最後一個階段。

此文章適用於 [SCEP 通訊工作流程](troubleshoot-scep-certificate-profiles.md)的步驟 6。

## <a name="review-for-signs-of-successful-reporting"></a>檢閱成功報告的跡象

如果報告成功，您會在 NDES 伺服器上找到類似下列範例的項目：

- **IIS 記錄**：

  `fe80::f53d:89b8:c3e8:5fec%13 POST /CertificateRegistrationSvc/Certificate/Notify - 443 - fe80::f53d:89b8:c3e8:5fec%13 NDES_Plugin - 204 0 0 277 62`

- **NDESPlugin.log**：

  ```
  Calling Notifyrequest ...
  Sending request to certificate registration point.
  Exiting Notify with 0x0
  ```

- **CertificateRegistrationPoint.svclog**：

  ![Intune 憑證連接器記錄](../protect/media/troubleshoot-scep-certificate-reporting/certificate-registration-point-log.png)

- **NDESConnector.svclog**：

  ![Intune 憑證連接器記錄](../protect/media/troubleshoot-scep-certificate-reporting/ndesconnector-log.png)

- **CertificateRequestStatus**：

  前往 *%ProgramFiles%\Microsoft Intune\CertificateRequestStatus* 資料夾，其中您將看到包含憑證要求狀態檔案的 **Failed**、**Processing** 與 **Succeed** 資料夾。

  如果成功處理憑證要求，您將會在 **Succeed** 資料夾中看到新的檔案。 您可以使用 *Notepad.exe* 開啟檔案，並透過 Intune 憑證連接器來檢視已上傳至 Intune 服務的資料。 上傳的資料包含 **CertificateSerialNumber**、**UserID**、**DeviceID** 與 **Thumbprint** 等詳細資訊。

### <a name="troubleshoot-stuck-files"></a>針對停滯的檔案進行疑難排解

如果您沒有在 *Succeed* 資料夾中看到任何新檔案，請檢查 *Processing* 資料夾中是否有任何檔案停滯。

確認已在 NDES 伺服器上啟動 Intune 連接器服務，且 Ndesconnector.svclog 中沒有任何錯誤。

## <a name="next-steps"></a>後續步驟

[如何取得 Microsoft Intune 支援](../fundamentals/get-support.md)
