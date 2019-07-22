---
title: 在 Microsoft Intune 中於 macOS 上新增 Endpoint Protection - Azure | Microsoft Docs
description: 在 macOS 裝置上，使用閘道管理員來判斷可安裝應用程式的位置，包括 Mac App Store。 此外，也使用 Microsoft Intune 來啟用或設定防火牆以允許特定應用程式、封鎖特定應用程式、使用隱形模式，甚至是封鎖特定類型的連入連線。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d110013c10f0330c0edbbf230c508009fb47b2a6
ms.sourcegitcommit: 11a31cd39b727f2254e2705b07d18924e103bd2e
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341306"
---
# <a name="macos-endpoint-protection-settings-in-intune"></a>Intune 中的 macOS Endpoint Protection 設定  

此文章說明您可以為執行 macOS 的裝置設定的 Endpoint Protection 設定。 您可以在 Intune 中使用 macOS 裝置設定設定檔來進行這些設定, 以進行[endpoint protection](endpoint-protection-configure.md) 。  

## <a name="gatekeeper"></a>閘道管理員  

- **允許從這些位置下載的應用程式**  
  根據下載應用程式的位置, 限制裝置可以啟動的應用程式。 用意是要保護裝置免於惡意程式碼危害，而只允許來自您所信任來源的應用程式。  

  - **未設定**  
  - **Mac App Store**  
  - **Mac App Store 和已識別的開發人員**  
  - **任何位置**  

  **預設**：未設定  

- **使用者可以覆寫閘道管理員**  
  防止使用者覆寫閘道管理員設定，並防止使用者透過按住 Control 鍵再按一下來安裝應用程式。 啟用時，使用者可以按住 Control 鍵再按一下任何應用程式來安裝該應用程式。  
 
  - **未設定**-使用者可以按一下 ctrl 來安裝應用程式。  
  - **封鎖**-防止使用者使用按一下控制來安裝應用程式。  

  **預設**：未設定  

## <a name="firewall"></a>防火牆  

使用防火牆來控制個別應用程式 (而非個別連接埠) 的連線。 使用個別應用程式設定可讓您更容易獲得防火牆保護的好處。 這還有助於防止不想要的應用程式控制為合法應用程式開啟的網路連接埠。  

**一般**
- **防火牆**  
  啟用防火牆以設定您環境中處理連入連線的方式。  
  - **未設定**  
  - **啟用**  

  **預設**：未設定  

- **連入連線**  
  除了基本網際網路服務所需的連線 (例如 DHCP、Bonjour 及 IPSec) 之外，封鎖所有連入連線。 此功能也會封鎖所有共用服務，例如「檔案共用」和「螢幕共用」。 如果您目前使用共用服務，請將此設定保持為 [未設定]  。  
  - **未設定**  
  - **封鎖**  

  **預設**：未設定  

**允許或封鎖特定應用程式的連入連線。**  

  - **允許的應用程式**  
    選取明確允許接收連入連線的應用程式。  

  - **封鎖的應用程式**  
    選取應封鎖連入連線的應用程式。  

  - **隱形模式**  
    若要防止電腦回應探查要求，請啟用隱形模式。 電腦會繼續回應已授權應用程式的連入要求。 ICMP (ping) 等未預期的要求都會予以忽略。  
    - **未設定**  
    - **啟用**  

    **預設**：未設定  

## <a name="filevault"></a>FileVault  
如需 Apple FileVault 設定的詳細資訊, 請參閱 Apple 開發人員內容中的[FDEFileVault](https://developer.apple.com/documentation/devicemanagement/fdefilevault) 。 

- **FileVault**  
  您可以在執行 macOS 10.13 和更新版本的裝置上, 使用 XTS-AES 128 與 FileVault 來*啟用*完整磁片加密。  
  - **未設定**  
  - **啟用**  

  **預設**：未設定  

  - **修復金鑰類型**  
    系統會為裝置建立*個人金鑰*修復金鑰。 設定個人金鑰的下列設定。  

     - **個人修復金鑰的位置**-指定簡短的訊息給使用者, 說明他們可以如何取得其個人修復金鑰。 此文字會插入至使用者在啟用 FileVault 時看到的訊息。  
      
     - **個人修復金鑰輪替**-指定裝置的個人修復金鑰要旋轉的頻率。 您可以選取 [**未設定**] 的預設值, 或 [ **1** ] 到 [ **12** ] 個月的值。  

  - **延遲 FileVault 直到登出** 
    > [!NOTE]
    > FileVault 的支援會受到限制, 直到7月發行完成幾天的推出。 在首度發行完成之前, 如果您設定 FileVault, 則必須將 [*延遲 FileVault* ] 設為 [登出], 才可**啟用**。   

    FileVault 將不會啟用, 直到使用者登出為止。本機使用者或行動帳戶使用者將會收到提示, 讓您在登出或下一次登入時啟用 FileVault。  
    - **未設定**  
    - **啟用**  
    
    **預設**：未設定  



    - **登出時停用提示**  
      當使用者登出時, 請避免提示要求他們啟用 FileVault。  
      - **未設定**  
      - **啟用**  

      **預設**：未設定  

    - **允許略過的次數**  
      設定使用者在需要 FileVault 以讓使用者登入之前, 可以忽略提示以啟用 FileVault 的次數。  

      - **未設定**-在允許下一次登入之前, 裝置上的加密是必要的。  
      -  **1**到**10** -允許使用者在裝置上要求加密之前, 略過1到10次的提示。  
      - **無限制, 一律提示**-系統會提示使用者啟用 FileVault, 但不需要加密。  
 
      **預設**：未設定  


