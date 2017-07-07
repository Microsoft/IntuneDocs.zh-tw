---
title: "Windows 10 的大量註冊"
description: "建立 Microsoft Intune 的大量註冊套件"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 03/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0053e37a-f26e-452f-9524-5039a635b52e
ms.reviewer: damionw
ms.custom: intune-classic
ms.openlocfilehash: ab52ba70403da5192cd3539dfd6d1e64bd79268c
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="bulk-enrollment-for-windows-devices"></a>Windows 裝置的大量註冊

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

身為系統管理員，您可以將大量的新 Windows 裝置加入 Azure Active Directory 和 Intune。 若要為您的 Azure AD 租用戶大量註冊裝置，請使用 Windows Configuration Designer (WCD) 應用程式來建立佈建套件。 將佈建套件套用到公司擁有的裝置，就會將裝置加入您的 Azure AD 租用戶，並加以註冊以供 Intune 管理。 套用套件之後，Azure AD 使用者即可登入。

Azure AD 使用者是這些裝置上的標準使用者，並且會接收指派的 Intune 原則和必要應用程式。 目前不支援自助式和公司入口網站案例。

## <a name="prerequisites-for-windows-devices-bulk-enrollment"></a>Windows 裝置大量註冊的先決條件

Window 裝置大量註冊需要下列事項：

- 執行 Windows 10 Creator Update 或更新版本的裝置
- [Windows 自動註冊](/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune#enable-windows-10-automatic-enrollment)

## <a name="create-a-provisioning-package"></a>建立佈建套件

1. 從 Windows 市集下載 [Windows Configuration Designer (WCD)](https://www.microsoft.com/store/apps/9nblggh4tx22)。
![Windows Configuration Designer 應用程式在市集中之螢幕擷取畫面和描述的螢幕擷取畫面](../media/bulk-enroll-store.png)

2. 開啟 **Windows Configuration Designer** 應用程式並選取 [Provision desktop devices (佈建電腦裝置)]。
![在 Windows Configuration Designer 應用程式中選取佈建電腦裝置的螢幕擷取畫面](../media/bulk-enroll-select.png)

3. 隨即開啟 [New project (新增專案)] 視窗，您可在其中指定下列項目：
  - **Name (名稱)** - 專案名稱
  - **Project folder (專案資料夾)** - 儲存新專案的位置
  - **Description (描述)** - 專案的選擇性描述 ![在 Windows Configuration Designer 應用程式中指定名稱、專案資料夾和描述的螢幕擷取畫面](../media/bulk-enroll-name.png)

4.  輸入您裝置的唯一名稱。 名稱可以包含序號 (%%SERIAL%%) 或一組隨機字元。 您也可以選擇輸入產品金鑰 (如果您正在升級 Windows 的版本)、將裝置設定為共用，以及移除預先安裝的軟體。<BR>
![在 Windows 設定設計工具應用程式中指定名稱、專案資料夾和描述的螢幕擷取畫面](../media/bulk-enroll-device.png)

5.  您可以選擇設定裝置第一次啟動時要連線的 Wi-Fi 網路。  如果未設定，則裝置第一次啟動時需要有線網路連線。
![在 Windows Configuration Designer 中啟用 Wi-Fi (包含網路 SSID 和網路類型選項) 的螢幕擷取畫面](../media/bulk-enroll-network.png)

6.  選取 [Enroll in Azure AD (在 Azure AD 中註冊)]，輸入 [Bulk Token Expiry (大量權杖到期)] 日期，然後選取 [Get Bulk Token (取得大量權杖)]。
![在 Windows Configuration Designer 應用程式中指定名稱、專案資料夾和描述的螢幕擷取畫面](../media/bulk-enroll-account.png)

7. 提供您的 Azure AD 認證以取得大量權杖。
![在 Windows Configuration Designer 應用程式中指定名稱、專案資料夾和描述的螢幕擷取畫面](../media/bulk-enroll-cred.png)

8.  成功擷取「大量權杖」之後，按一下 [Next (下一步)]。

9. 您可以選擇 [Add applications (新增應用程式)] 和 [Add certificates (新增憑證)]。 這些應用程式和憑證都佈建在該裝置上。

10. 您可以選擇以密碼保護佈建套件。  按一下 **建立**。
![在 Windows Configuration Designer 應用程式中指定名稱、專案資料夾和描述的螢幕擷取畫面](../media/bulk-enroll-create.png)

## <a name="provision-devices"></a>佈建裝置

1. 存取應用程式所指定 [Project folder (專案資料夾)] 中指定的佈建套件位置。

2. 選擇將佈建套件套用到裝置的方式。  您可以使用下列其中一種方式將佈建套件套用到裝置：
 - 將佈建套件置於 USB 磁碟機，將 USB 磁碟機插入要大量註冊的裝置，並在初始安裝期間套用佈建套件
 - 將佈建套件置於網路資料夾，並在初始安裝之後，針對您要大量註冊的裝置套用佈建套件

 如需套用佈建套件的逐步指示，請參閱[套用佈建套件](https://technet.microsoft.com/itpro/windows/configure/provisioning-apply-package)。

3. 套用套件之後，裝置會在 1 分鐘內自動重新啟動。
 ![在 Windows Configuration Designer 應用程式中指定名稱、專案資料夾和描述的螢幕擷取畫面](../media/bulk-enroll-add.png)

4. 當裝置重新啟動時，它會連線到 Azure Active Directory 並在 Microsoft Intune 中註冊。

## <a name="troubleshooting-windows-bulk-enrollment"></a>針對 Windows 大量註冊進行疑難排解

佈建是要用於新的 Windows 裝置上。 佈建如果失敗，可能需要進行裝置原廠重設，或使用開機映像進行裝置還原。 下列例子說明佈建失敗的某些原因：

- 嘗試加入 Active Directory 網域或 Azure Active Directory 租用戶的佈建套件，如果未建立本機帳戶，當沒有網路連線而造成網域加入程序失敗時，會使得裝置無法使用。
- 由佈建套件執行的指令碼是在系統內容中執行，且能夠對裝置檔案系統和設定做任意的變更。 惡意或不良的指令碼可能會使裝置處於某種狀態，而只能透過重新安裝映像或進行原廠重設才能還原裝置。
