---
title: 設定註冊狀態頁面
titleSuffix: Microsoft Intune
description: 針對註冊 Windows 10 裝置的使用者設定問候語頁面。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8518d8fa-a0de-449d-89b6-8a33fad7b3eb
ms.reviewer: ericor
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a3a470c9a92f7792af2b371acf873807ad344afb
ms.sourcegitcommit: b752acefec077c719e169e665c955adb944e85c6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74781102"
---
# <a name="set-up-an-enrollment-status-page"></a>設定註冊狀態頁面
 
[!INCLUDE [azure_portal](../includes/azure_portal.md)]
 
註冊狀態頁面 (ESP) 會在初始裝置註冊期間顯示 Windows 10 裝置 (1803 版和更新版本) 的安裝資訊。 例如：
- 使用 [Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/) 時 
- 或在套用註冊狀態頁面原則後，第一次啟動受控裝置時。 

註冊狀態頁面可協助使用者了解其裝置在裝置設定期間的狀態。 您可以建立多個註冊狀態頁面設定檔，並將其套用至包含使用者的不同群組。 設定檔可設定為：
- 顯示安裝進度。
- 封鎖使用直到安裝完成。
- 指定裝置設定失敗時使用者可採取的動作。

您也可以設定每個設定檔的優先順序，來解決將設定檔指派給相同使用者時所發生的衝突。

> [!NOTE]
> 註冊狀態頁面只能以屬於已指派群組的使用者為目標，且在註冊時，會在裝置上設定所有使用該裝置之使用者的原則。  

## <a name="available-settings"></a>可用的設定

 下列設定可以設定為註冊狀態頁面的自訂行為：

<table>
<th align="left">設定<th align="left">是<th align="left">否
<tr><td>顯示應用程式與設定檔的安裝進度<td>註冊狀態頁面隨即顯示。<td>註冊狀態頁面不會顯示。
<tr><td>所有應用程式與設定檔未完成安裝之前，禁止使用裝置<td>此表格中的設定可讓您自訂註冊狀態頁面的行為，讓使用者可以解決潛在的安裝問題。
<td>註冊狀態頁面隨即顯示，且沒有其他選項可解決安裝失敗。
<tr><td>允許使用者在發生安裝錯誤時重設裝置<td>如果安裝失敗，則會顯示 [重設裝置]<b></b> 按鈕。<td>如果安裝失敗，則不會顯示 [重設裝置]<b></b> 按鈕。
<tr><td>允許使用者在發生安裝錯誤時使用裝置<td>如果安裝失敗，則會顯示 [仍要繼續]<b></b> 按鈕。<td>如果安裝失敗，則不會顯示 [仍要繼續]<b></b> 按鈕。
<tr><td>當安裝時間超過指定的分鐘數時顯示逾時錯誤<td colspan="2">指定等待安裝完成的分鐘數。 輸入的預設值為 60 分鐘。
<tr><td>發生錯誤時顯示自訂訊息<td>系統會提供一個文字方塊，您可以在其中指定發生安裝錯誤時要顯示的自訂訊息。<td>顯示的預設訊息： <br><b>安裝超過您組織所設定的時間限制。 請再試一次，或連絡 IT 支援人員以取得協助。<b>
<tr><td>允許使用者收集有關安裝錯誤的記錄<td>如果發生安裝錯誤，則會顯示 [收集記錄]<b></b> 按鈕。 <br>如果使用者按一下這個按鈕，系統就會要求他們選擇一個位置來儲存記錄檔 <b>MDMDiagReport.cab</b><td>如果發生安裝錯誤，則不會顯示 [收集記錄]<b></b> 按鈕。
<tr><td>若這些必要的應用程式已指派給使用者/裝置，請在安裝這些應用程式之前，封鎖裝置使用它們<td colspan="2">選擇 [全部]<b></b> 或 [已選取]<b></b>。 <br><br>如果選擇 [已選取]<b></b>，則會顯示 [選取應用程式]<b></b> 按鈕，讓您在啟用裝置之前，選擇必須安裝的應用程式。
</table>

## <a name="turn-on-default-enrollment-status-page-for-all-users"></a>為所有使用者開啟預設註冊狀態頁面

若要開啟註冊狀態頁面，請遵循下列步驟。
 
1. 在 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，選擇 [裝置]   > [Windows]   > [Windows 註冊]   > [註冊狀態頁面]  。
2. 在 [註冊狀態頁面]  刀鋒視窗中，選擇 [預設]   > [設定]  。
3. 針對 [顯示應用程式和設定檔安裝進度]  ，選擇 [是]  。
4. 選擇您想要開啟的其他設定，然後選擇 [儲存]  。

## <a name="create-enrollment-status-page-profile-and-assign-to-a-group"></a>建立註冊狀態頁面設定檔並指派給群組

1. 在 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，選擇 [裝置]   > [Windows]   > [Windows 註冊]   > [註冊狀態頁面]   > [建立設定檔]  。
2. 提供 [名稱]  和 [描述]  。
3. 選擇 **[建立]** 。
4. 在 [註冊狀態頁面]  清單選擇新的設定檔。
5. 選擇 指派   > 選取群組  > 選擇您想要採用這個設定檔的群組 > 選取   >  儲存  。
6. 選擇 [設定]  > 選擇您想要套用至這個設定檔的設定 > [儲存]  。

## <a name="set-the-enrollment-status-page-priority"></a>設定註冊狀態頁面優先順序

使用者可以處於多個群組中，並具有多個註冊狀態頁面設定檔。 為了處理這類衝突，您可以設定每個設定檔的優先順序。 在註冊過程中，如果某人具有多個註冊狀態頁面設定檔，則僅將最高優先順序的設定檔套用至該註冊裝置。

1. 在 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，選擇 [裝置]   > [Windows]   > [Windows 註冊]   > [註冊狀態頁面]  。
2. 將滑鼠移到清單中的設定檔上方。
3. 使用三個垂直點，將設定檔拖曳到所要的清單位置。

## <a name="block-access-to-a-device-until-a-specific-application-is-installed"></a>封鎖對裝置的存取，直到已安裝特定應用程式

您可以指定需要先安裝哪些應用程式，使用者才能存取桌面。

1. 在 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，選擇 [裝置]   > [Windows]   > [Windows 註冊]   > [註冊狀態頁面]  。
2. 選擇定檔 > [設定]  。
3. 對於 [顯示應用程式與設定檔的安裝進度]  ，選擇 [是]  。
4. 對於 [所有應用程式與設定檔未完成安裝之前，禁止使用裝置]  ，選擇 [是]  。
5. 對於 [若這些必要的應用程式已指派給使用者/裝置，請在安裝這些應用程式之前，封鎖裝置使用它們]  ，選擇 [已選取]  。
6. 選擇 [選取應用程式]  > 選擇應用程式 > [選取]   > [儲存]  。

## <a name="enrollment-status-page-tracking-information"></a>註冊狀態頁面追蹤資訊

註冊狀態頁面會追蹤三個階段的資訊；裝置準備、裝置設定和帳戶設定。

### <a name="device-preparation"></a>裝置準備

針對裝置準備，註冊狀態頁面會追蹤：
- 信賴平台模組 (TPM) 金鑰證明 (如果適用)
- 加入 Azure Active Directory 的進度
- 註冊至 Intune
- Intune 管理延伸模組的安裝

### <a name="device-setup"></a>裝置設定

註冊狀態頁面會追蹤下列裝置設定項目 (如果它們指派給 [所有裝置]，或是註冊裝置所屬的裝置群組)：
- 安全性原則
  - 適用於所有註冊的一個設定服務提供者 (CSP) 。
  - 這裡不會追蹤 Intune 所設定的實際 CSP。
- 應用程式
  - 每個機器的特定業務 (LOB) MSI 應用程式。
  - 具有安裝內容 = 裝置的 LOB 存放區應用程式。
  - 具有安裝內容 = 裝置的離線存放區 LOB 存放區應用程式。
  - Win32 應用程式 (僅限 Windows 10 1903 版和更新版本) 
- 連線設定檔
  - 指派給**所有裝置**，或是註冊裝置為其成員之裝置群組的 VPN 或 Wi-Fi 設定檔，但僅適用於 Autopilot 裝置
- 指派給**所有裝置**，或是註冊裝置為其成員之裝置群組的憑證設定檔，但僅適用於 Autopilot 裝置

### <a name="account-setup"></a>帳戶設定
針對帳戶設定，註冊狀態頁面會追蹤下列項目，如果它們指派給目前已登入的使用者的話：
- 安全性原則
  - 適用於所有註冊的一個 CSP 。
  - 這裡不會追蹤 Intune 所設定的實際 CSP。
- 應用程式
  - 指派給所有裝置、所有使用者，或是註冊裝置的使用者為其成員之使用者群組的每個使用者 LOB MSI 應用程式。
  - 指派給所有使用者，或是註冊裝置的使用者為其成員之使用者群組的每個機器 LOB MSI 應用程式。
  - 指派給下列任何一個對象的 LoB 市集應用程式、線上市集應用程式和離線市集應用程式：
    - 所有裝置
    - 所有使用者
    - 使用者群組，其中註冊裝置的使用者為其成員，且安裝內容設定至「使用者」。
  - Win32 應用程式 (僅限 Windows 10 1903 版和更新版本) 
- 連線設定檔
  - 指派給所有使用者，或是註冊裝置的使用者為其成員之使用者群組的 VPN 或 Wi-Fi 設定檔。
- 憑證
  - 指派給所有使用者，或是註冊裝置的使用者為其成員之使用者群組的憑證設定檔。

### <a name="troubleshooting"></a>疑難排解
疑難排解的主要問題。

- 為什麼在使用註冊狀態頁面的 Autopilot 部署期間，在裝置設定階段期間未安裝我的應用程式？
  - 若要保證應用程式會在 Autopilot 裝置設定階段期間安裝，請確定 
        1. 已選取應用程式，以在選取的應用程式清單中封鎖存取
        2. 您的目標是將應用程式設為 Autopilot 設定檔所指派的相同 Azure AD 裝置群組。 

- 為什麼會顯示非 Autopilot 部署的註冊狀態頁面，例如當使用者第一次登入 Configuration Manager 共同管理註冊的裝置時？  
  - 註冊狀態頁面會列出所有註冊方法的安裝狀態，包括
      - Autopilot
      - Configuration Manager 共同管理
      - 當有任何新使用者登入第一次套用註冊狀態頁面原則的裝置時

- 如果裝置上已設定註冊狀態頁面，如何將它停用？
  - 註冊狀態頁面原則會在註冊時於裝置上設定。 若要停用註冊狀態頁面，您必須停用使用者和裝置註冊狀態頁面區段。 您可以使用下列設定來建立自訂 OMA-URI 設定，以停用區段。

      停用使用者註冊狀態頁面：

      ```
      Name:  Disable User ESP (choose a name you desire)
      Description:  (enter a description)
      OMA-URI:  ./Vendor/MSFT/DMClient/Provider/MS DM Server/FirstSyncStatus/SkipUserStatusPage
      Data type:  Boolean
      Value:  True 
      ```
      停用裝置註冊狀態頁面：

      ```
      Name:  Disable Device ESP (choose a name you desire)
      Description:  (enter a description)
      OMA-URI:  ./Vendor/MSFT/DMClient/Provider/MS DM Server/FirstSyncStatus/SkipDeviceStatusPage
      Data type:  Boolean
      Value:  True 
      ```
- 如何收集記錄檔？
  - 有兩種方式可以收集註冊狀態頁面記錄檔：
      - 讓使用者能夠收集 ESP 原則中的記錄。 當註冊狀態頁面發生逾時時，終端使用者可以選擇 [收集記錄]  的選項。 藉由插入 USB 磁碟機，可以將記錄檔複製到磁碟機中
      - 輸入 Shift-F10 按鍵序列以開啟命令提示字元，然後輸入下列命令列來產生記錄檔： 

      ```
      mdmdiagnosticstool.exe -area Autopilot -cab <pathToOutputCabFile>.cab 
      ```

### <a name="known-issues"></a>已知問題
以下是已知問題。 
- 停用 ESP 設定檔並不會從裝置移除 ESP 原則，而且使用者在第一次登入裝置時，仍會取得 ESP。 停用 ESP 設定檔時，不會移除原則。 您必須部署 OMA-URI 以停用 ESP。 如需有關如何使用 OMA-URI 停用 ESP 的指示，請參閱上述。 
- 擱置重新開機一律會造成逾時。 因為裝置需要重新開機，所以會發生逾時。 需要重新開機才有時間完成註冊狀態頁面中所追蹤的項目。 重新開機會導致註冊狀態頁面結束，而且在重新開機後，裝置將不會進入帳戶設定。  請考慮不需要重新開機進行應用程式安裝。 
- 裝置設定期間的重新開機會強制使用者在轉換至帳戶設定階段之前輸入其認證。 重新開機期間不會保留使用者認證。 請讓使用者輸入其認證，然後註冊狀態頁面才能繼續。 
- 在低於 1903 的 Windows 10 版本上進行 [新增工作和學校帳戶] 註冊期間，註冊狀態頁面一律會逾時。 註冊狀態頁面會等待 Azure AD 註冊完成。 Windows 10 1903 版和更新版本中已修正此問題。  
- 使用 ESP 的混合式 Azure AD Autopilot 部署所花的時間超過 ESP 設定檔中所定義的逾時期間。 在混合式 Azure AD Autopilot 部署上，ESP 會花費 40 分鐘的時間，超過 ESP 設定檔中所設定的值。 此延遲使內部部署 AD 連接器有時間建立 Azure AD 的新裝置記錄。 
- Windows 登入頁面未預先填入 Autopilot 使用者驅動模式中的使用者名稱。 如果在 ESP 的裝置設定階段期間重新開機：
    - 使用者認證不會保留
    - 使用者必須再次輸入認證，才能從裝置設定階段繼續至帳戶設定階段
- ESP 長時間停滯，或永遠不會完成「識別」階段。 Intune 會在識別階段計算 ESP 原則。 如果目前的使用者未獲指派 Intune 授權，裝置可能永遠不會完成計算 ESP 原則。  
- 設定 Microsoft Defender 應用程式控制會導致在 Autopilot 期間提示重新開機。 設定 Microsoft Defender 應用程式 (AppLocker CSP) 需要重新開機。 設定此原則後，可能會導致裝置在 Autopilot 期間重新開機。 目前沒有任何方法可以抑制或延後重新開機。
- 當 DeviceLock 原則 (https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) 作為 ESP 設定檔的一部分啟用時，OOBE 或使用者桌面登入可能會因為兩個原因而意外失敗。
  - 如果裝置在結束 ESP 裝置設定階段之前未重新開機，系統可能會提示使用者輸入其 Azure AD 認證。 發生此提示時，使用者會看到 Windows 第一個登入動畫，而不是成功的自動登入。
  - 如果裝置在使用者輸入其 Azure AD 認證之後，但結束 ESP 裝置設定階段之前重新開機，則自動登入將會失敗。 發生此失敗的原因是 ESP 裝置設定階段永遠不會完成。 解決方法是重設裝置。

## <a name="next-steps"></a>後續步驟
設定 Windows 註冊頁面之後，了解如何管理 Windows 裝置。 如需詳細資訊，請參閱[什麼是 Microsoft Intune 裝置管理？](../remote-actions/device-management.md)
