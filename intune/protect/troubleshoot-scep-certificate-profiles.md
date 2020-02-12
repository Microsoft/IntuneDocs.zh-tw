---
title: 針對使用 Microsoft Intune 以 SCEP 憑證設定檔佈建憑證進行疑難排解 | Microsoft Docs
description: 針對由裝置使用 SCEP 要求與 Intune 搭配使用的憑證進行疑難排解，包括從裝置至 NDES、NDES 至憑證授權單位，以及從 Intune 憑證連接器至 Intune 服務的通訊。
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
ms.openlocfilehash: 38bc86b1b9ba85eb7885a0e00673e551821063c1
ms.sourcegitcommit: 459b0ee01eb6e69cc0ce66d4c4b81d73f510f96d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2020
ms.locfileid: "77034238"
---
# <a name="overview-for-troubleshooting-scep-certificate-profiles-with-microsoft-intune"></a>針對 SCEP 憑證設定檔搭配 Microsoft Intune 進行疑難排解的概觀

在 Intune 中針對使用簡單憑證註冊通訊協定 (SCEP) 憑證設定檔進行疑難排解可能是很困難的。 此文章提供概觀，可協助您透過下列方式解決問題：

- 說明 SCEP 程序的架構與通訊流程
- 協助您縮小問題在通訊流程中所在位置的範圍
- 識別後續文章中參照的金鑰記錄檔，以針對憑證設定檔進行疑難排解

此文章與相關 SCEP 憑證疑難排解文章中的資訊，適用於搭配 Android、iOS/iPad 與 Windows 裝置使用 SCEP 憑證設定檔。 目前未提供 macOS 的類似資訊。

若要針對網路裝置註冊服務 (NDES) 進行疑難排解，請參閱下列來自 support.microsoft.com 的文章：

- [在 Intune 中確認 SCEP 憑證的內部部署 NDES 設定](https://support.microsoft.com/help/4490130/ndes-configuration-on-premises-for-scep-certificates-in-intune) \(機器翻譯\)
- [針對要與 Microsoft Intune 憑證設定檔搭配使用的 NDES 設定進行疑難排解]( https://support.microsoft.com/help/4459540/troubleshoot-ndes-configuration-for-use-with-intune) \(機器翻譯\)

在繼續之前，請確定您已符合[使用 SCEP 憑證設定檔的必要條件](certificates-scep-configure.md#prerequisites-for-using-scep-for-certificates)，包括透過受信任的憑證設定檔部署根憑證。

## <a name="scep-communication-flow-overview"></a>SCEP 通訊流程概觀

下圖示範 Intune 中 SCEP 通訊程序的基本概觀。

![SCEP 憑證設定檔流程](../protect/media/troubleshoot-scep-certificate-profiles/scep-certificate-profile-flow.png)

1. [部署 SCEP 憑證設定檔](troubleshoot-scep-certificate-profile-deployment.md)。 Intune 會產生挑戰字串，此字串需要特定的使用者、憑證目的與憑證類型。

2. [裝置至 NDES 伺服器通訊](troubleshoot-scep-certificate-device-to-ndes.md)。 裝置會使用來自設定檔的 NDES URI 來連絡 NDES 伺服器，以便其可以提出挑戰。

3. [NDES 至原則模組通訊](troubleshoot-scep-certificate-ndes-policy-module.md)。 NDES 會將挑戰轉送到伺服器上的 Intune 憑證連接器原則模組，以驗證要求。

4. [NDES 至憑證授權單位單位](troubleshoot-scep-certificate-ndes-policy-module.md)。 NDES 將核發憑證的有效要求傳遞到憑證授權單位單位 (CA)。

5. [憑證傳遞到裝置](troubleshoot-scep-certificate-delivery.md)。 憑證會傳遞到裝置。

6. [部署到 Intune 的報告](troubleshoot-scep-certificate-reporting.md)。 Intune 憑證連接器會向 Intune 報告憑證發行事件。

## <a name="log-files"></a>記錄檔

若要識別通訊與憑證佈建工作流程的問題，請檢閱來自伺服器基礎結構與裝置的記錄檔。 疑難排解 SCEP 憑證設定檔的後續各節會提及此節所參考的記錄檔。

- [基礎結構與伺服器記錄檔](#logs-for-on-premises-infrastructure)

裝置記錄檔相依於裝置平台：  

- [iOS 與 iPadOS](#logs-for-ios-and-ipados-devices)
- [Android](#logs-for-android-devices)
- [Windows](#logs-for-windows-devices)

### <a name="logs-for-on-premises-infrastructure"></a>內部部署基礎結構的記錄
  
支援使用 SCEP 憑證設定檔進行憑證部署的內部部署基礎結構包括 Microsoft Intune 憑證連接器、在 Windows Server 上執行的 NDES，以及憑證授權單位。

這些角色的記錄檔包括 Windows 事件檢視器、憑證主控台，以及各種特定於 Intune 憑證連接器、NDES 或其他角色與作業 (屬於內部部署基礎結構) 的各種記錄檔。

下列清單包括後續 SCEP 疑難排解文章中所參考的記錄檔或主控台。 

- **NDESConnector_date_time.svclog**：

  此記錄顯示從 Microsoft Intune 憑證連接器到 Intune 雲端服務的通訊。 您可以使用[服務追蹤檢視器工具](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) \(部分機器翻譯\) 來檢視此記錄檔。

  相關的登錄機碼：*HKLM\SW\Microsoft\MicrosoftIntune\NDESConnector\ConnectionStatus*

  位置：在裝載 NDES 之伺服器的 *%program_files%\Microsoft intune\ndesconnectorsvc\logs\logs*

- **CertificateRegistrationPoint_date_time.svclog**：

  此記錄顯示接收及驗證憑證要求的 NDES 原則模組。 您可以使用[服務追蹤檢視器工具](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) \(部分機器翻譯\) 來檢視此記錄檔。

  位置：在裝載 NDES 之伺服器的 *%program_files%\Microsoft intune\ndesconnectorsvc\logs\logs*

- **NDESPlugin.log**：

  此記錄檔顯示憑證要求傳遞至憑證登錄點，以及針對那些要求產生的驗證結果。

  位置：在裝載 NDES 之伺服器上的 *%program_files%\Microsoft Intune\NDESPolicyModule\logs*

- **IIS 記錄檔**：

  IIS 記錄檔顯示來自行動裝置的憑證要求進入 NDES。

  位置：在裝載 NDES 之伺服器上的 *c:\inetpub\logs\LogFiles\W3SVC1*

- **Windows 應用程式記錄檔**：

  此記錄在調查 IIS 問題 (例如 SCEP 應用程式集區) 時很有用。

  位置：在裝載 NDES 的伺服器上：執行 **eventvwr.msc** 以開啟 Windows 事件檢視器




### <a name="logs-for-android-devices"></a>Android 裝置的記錄

針對執行 Android 的裝置，請使用 **Android 公司入口網站**應用程式記錄檔 (**OMADM.log**)。 在您收集及檢閱記錄之前，請先確認[詳細資訊記錄](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android)已啟用，然後重現問題。

若要從裝置收集 OMADM.logs，請參閱[使用 USB 纜線上傳記錄並以電子郵件傳送](/intune-user-help/send-logs-to-your-it-admin-using-cable-android)。

您也可以[上傳記錄並以電子郵件傳送](/intune-user-help/send-logs-to-your-it-admin-by-email-android#upload-and-email-logs-from-microsoft-intune-app)給技術支援。

### <a name="logs-for-ios-and-ipados-devices"></a>iOS 與 iPadOS 裝置的記錄

針對執行 iOS 或 iPadOS 的裝置，您可以使用偵錯記錄與在 Mac 電腦上執行的 **Xcode**：

1. 將 iOS 裝置連接到 Mac，然後移至 [應用程式]   > [工具程式]  以開啟 [終端機] 應用程式。 

2. 在 [動作]  下，選取 [包含資訊訊息]  和 [包含偵錯訊息]  。

   ![選取記錄選項](../protect/media/troubleshoot-scep-certificate-profiles/message-options.png)

3. 重現問題，並將記錄儲存至文字檔：
   1. 選取 [編輯]   > [全選]  以選取目前畫面上的所有訊息，然後選取 [編輯]   > [複製]  以將訊息複製到剪貼簿。 
   2. 開啟 [文字編輯] 應用程式，將複製的記錄貼入新文字檔中，然後儲存檔案。


適用於 iOS 與 iPadOS 裝置的公司入口網站記錄不包含 SCEP 憑證設定檔的相關資訊。

### <a name="logs-for-windows-devices"></a>Windows 裝置的記錄

針對執行 Windows 的裝置，請使用 Windows 事件記錄檔來診斷裝置 (使用 Intune 管理) 的註冊或裝置管理問題。

在裝置上，開啟 [事件檢視器]   > [應用程式及服務記錄檔]   > [Microsoft]   > [Windows]   > [DeviceManagement-Enterprise-Diagnostic-Provider] 

![Windows 事件記錄檔](../protect/media/troubleshoot-scep-certificate-profiles/windows-event-log.png)

## <a name="next-steps"></a>後續步驟

檢閱 [SCEP 憑證設定檔的部署](troubleshoot-scep-certificate-profile-deployment.md) 
