---
title: "用戶端設定疑難排解 | Microsoft Intune"
description: "針對常見用戶端安裝問題進行疑難排解。"
keywords: 
author: Nbigman
manager: angrobe
ms.date: 08/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e46d292b-1d16-46db-a87f-d53eefa4d22a
ms.reviewer: tscott
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb0aeac2f94dfde50d9398b09c6b21c7ae40624
ms.openlocfilehash: 3f7e5752780d7159ce3081ec7a194f4e81e4cd16


---

# Microsoft Intune 的用戶端設定疑難排解
請利用以下資訊協助您針對一般用戶端安裝問題進行疑難排解。 如果此資訊無法解決您的問題，請參閱[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)，以尋找更多方法來取得協助。

## 用戶端安裝失敗

-   如果 [Microsoft Intune 管理主控台](https://manage.microsoft.com/)中沒有顯示電腦的用戶端軟體部署警示，請檢查電腦的網際網路連線以及 Proxy 組態，並確定電腦可以與 服務 URL ([https://manage.microsoft.com](https://manage.microsoft.com/)) 進行通訊。 然後重試用戶端軟體的安裝。

-   您可以在 [系統管理]  工作區中設定通知規則，以在發出用戶端軟體部署失敗警示時，傳送電子郵件給選取的收件者。 如需詳細資訊，請參閱[取得 Microsoft Intune 警示通知](/intune/deploy-use/get-notified-by-alerts)。

-   如果用戶端軟體無法部署，Intune 會顯示重要警示：**用戶端軟體部署失敗**。 這會顯示在 [Microsoft Intune 管理主控台](https://manage.microsoft.com/)的 [系統概觀] 頁面與 [警示] 頁面中。 以下是如何檢查警示的方法︰

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com/)中，選擇 **[警示]** &gt; **[概觀]**。

2.  您可以在 [警示概觀]  頁面上檢閱下列資訊：

    -   前三個警示 (可依日期、類別或嚴重性排序)

    -   作用中警示總數

3.  選擇 **[所有警示]**，以在 **[警示]** 頁面上顯示下列資訊。 重要警示會顯示在最前面：

    -   [名稱] – 產生警示之警示類型的名稱。

    -   [來源] – 警示來源的連結。  如果警示類型的顯示閾值設定為 [全部] ，這個連結將會顯示單一的受影響裝置。  如果警示類型的顯示閾值設定為某個值，則這個連結將會顯示受此警示影響的所有裝置清單。

    -   [上次更新日期] – 這代表上次修改警示的時間。 若關閉警示，系統就會顯示關閉警示的時間。

    -   **嚴重性** – 這代表警示的嚴重性

## 電腦註冊套件未下載
**問題︰**嘗試註冊電腦時，您遇到下列情況︰
-  無法下載註冊套件
-  出現 [下載] 對話方塊，但逾時

**解決方式︰**在您用於下載的瀏覽器上，下載進行時，請確保下載已啟用，而且加密的檔案可以儲存至您的本機光碟。

## 用戶端安裝停止並顯示錯誤碼 0x80040154
**問題：**

-  註冊停止期間的用戶端安裝

-  無法註冊裝置

-  WindowsUpdate.log 中的錯誤 0x80040154

原因可能是電腦上的重大軟體更新不存在。

**解決方式**：請確定您的軟體更新原則已啟用重大更新的安裝 (如[在 Microsoft Intune 中使用軟體更新讓 Windows 電腦維持最新狀態](/intune/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)中所述)。


## Microsoft Intune policyplatform.log 中的原則相關錯誤
至於非 MDM Windows 裝置，policyplatform.log 檔案中的原則錯誤可能是因為裝置上 Windows 使用者帳戶控制 (UAC) 的非預設設定所造成。 某些非預設的 UAC 設定可能會影響 Microsoft Intune 用戶端安裝和原則執行。

### 解決 UAC 問題

1.  請如[從 Microsoft Intune 管理淘汰資料和裝置](/intune/deploy-use/retire-devices-from-microsoft-intune-management)一文中所述來淘汰電腦。

2.  等候 20 分鐘讓用戶端軟體被移除。

    > [!NOTE]
    > 請勿嘗試從 [程式和功能] 移除用戶端。

3.  在 [開始] 功能表中輸入 **UAC**，開啟 [使用者帳戶控制] 設定。

4.  將通知滑桿移至預設設定。

## 無法從 Microsoft Intune 系統管理員主控台解除安裝用戶端時的因應措施

### 使用 Microsoft Intune 命令列工具移除用戶端軟體

1.  以系統管理員模式開啟命令提示字元。

2.  前往資料夾 *%programfiles%\Microsoft\OnlineManagement\Common*

3.  執行下列命令 ``ProvisioningUtil.exe /UninstallAgents /MicrosoftIntune``

## 用戶端安裝錯誤碼
下表說明用戶端軟體安裝失敗時 [警示]  中顯示的錯誤碼。 表中包含解決每個錯誤碼所代表之問題的建議。

|錯誤碼|可能的問題|建議的解決方式|
|--------------|--------------------|------------------------|
|**0x80CF0437**|用戶端電腦上的時鐘未設定成正確的時間。|確定用戶端電腦上的時鐘和時區已設成正確的時間和時區。|
|**0x80240438**、 **0x80CF0438**、 **0x80CF401B**|無法連線至 Intune 服務。 請檢查用戶端 Proxy 設定。|確認 Intune 支援用戶端電腦上的 Proxy 設定，而且用戶端電腦可以存取網際網路。 如需所支援之 Proxy 設定的詳細資訊，請參閱[使用 Microsoft Intune 的 Endpoint Protection 協助保護 Windows 電腦](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)。|
|**0x80CF402C**|無法連線至 Intune 服務。 檢查網路連線。|確認電腦具有網路連線能力。 請確認已接上網路纜線或已開啟無線網路。|
|**0x80240438、0x80CF0438**|未設定 Internet Explorer 和本機系統中的 Proxy 設定。|請檢查用戶端 Proxy 設定，並確認 Intune 所支援的用戶端電腦上的 Proxy 組態，且用戶端電腦可以存取網際網路。 如需所支援之 Proxy 設定的詳細資訊，請參閱[使用 Microsoft Intune 的 Endpoint Protection 協助保護 Windows 電腦](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)。|
|**0x80043001**|註冊套件已過期。|從 [系統管理]  工作區下載並安裝最新的用戶端軟體套件。 如需相關指示，請參閱[使用 Microsoft Intune 安裝 Windows 電腦用戶端](/intune/deploy-use/install-the-windows-pc-client-with-microsoft-intune)主題。|
|**0x80043004**|訂閱不存在或已停用。|確認您的帳戶和 Intune 訂閱仍然有效。 若要檢視您的帳戶設定，請使用您的帳戶登入 [Office 365 系統管理中心](http://go.microsoft.com/fwlink/?LinkId=698854%20)。|
|**0x80043002**|帳戶處於維護模式。|您不能在帳戶處於維護模式時註冊新的用戶端電腦。 若要檢視您的帳戶設定，請使用您的帳戶登入 [Office 365 系統管理中心](http://go.microsoft.com/fwlink/?LinkId=698854%20)。|
|**0x80043003**|已刪除帳戶。|確認您的帳戶和 Intune 訂閱仍然有效。 若要檢視您的帳戶設定，請登入您的帳戶。|
|**0x80043005**|已淘汰用戶端電腦。|等待幾個小時，並從電腦移除所有的舊版用戶端軟體，然後再次嘗試安裝用戶端軟體。 如需相關指示，請參閱上述的**無法從 Microsoft Intune 系統管理員主控台解除安裝用戶端時的因應措施**。|
|**0x80043006**|已達到帳戶允許的基座數目上限。|貴組織必須購買額外的基座，您才可以在服務中註冊更多用戶端電腦。|
|**0x80043007**|在與安裝程式相同的資料夾中找不到憑證檔案。|在開始安裝之前先解壓縮所有檔案。 請勿重新命名任何已解壓縮的檔案或改變其位置：所有檔案都必須位於同一個資料夾，否則安裝將會失敗。 如需詳細資訊，請參閱[使用 Microsoft Intune 安裝 Windows 電腦用戶端](/intune/deploy-use/install-the-windows-pc-client-with-microsoft-intune)。|
|**0x8024D015**、 **0x00240005**、 **0x80070BC2**、 **0x80070BC9**、 **0x80CFD015**|由於用戶端電腦仍在等待重新啟動，因此無法安裝軟體。|重新啟動電腦，然後再次嘗試安裝用戶端軟體。|
|**0x80070032**|用戶端電腦不符合安裝用戶端軟體的一或多個必要條件。|確定用戶端電腦已安裝所有必要更新，然後再次嘗試安裝用戶端軟體。 如需安裝用戶端軟體之必要條件的詳細資訊，請參閱[適用於 Microsoft Intune 的網路基礎結構需求](/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)。|
|**0x80043008**|無法啟動 Microsoft Online Management Updates 服務。|請依[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)所述連絡支援人員。|
|**0x80043009**|用戶端電腦已註冊到服務中。|您必須先淘汰用戶端電腦，才能重新將它註冊到服務中。 如需指示，請參閱[從 Microsoft Intune 管理淘汰裝置](/intune/deploy-use/retire-devices-from-microsoft-intune-management)。|
|**0x8004300B**|用戶端軟體安裝套件無法執行，因為不支援用戶端上執行的 Windows 版本。|Intune 不支援用戶端電腦上執行的 Windows 版本。 如需支援的作業系統清單，請參閱[適用於 Microsoft Intune 的網路基礎結構需求](/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)。|
|**0xAB2**|Windows Installer 無法存取自訂動作的 VBScript 執行階段。|這個錯誤是由以動態連結程式庫 (DLL) 為基礎的自訂動作所造成。 在疑難排解 DLL 時，您可能必須使用 [Microsoft Support KB198038: Useful Tools for Package and Deployment Issues (Microsoft 技術支援 KB198038：套件與部署問題的實用工具)](http://go.microsoft.com/fwlink/?LinkID=234255)中所述的工具。|
|**0x8004300f**|無法安裝軟體，因為已經安裝了 System Center Configuration Manager 用戶端。|移除 Configuration Manager 用戶端，然後再次嘗試安裝用戶端軟體。|
|**0x80043010**|無法安裝軟體，因為已經安裝 Open Mobile Alliance Device Management (OMADM) 用戶端。|取消註冊 OMADM 用戶端，然後再次嘗試安裝用戶端軟體。|
如果安裝問題持續發生，請依[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)所述連絡支援人員。 請備妥用戶端電腦註冊記錄檔 (位於 %*programfiles*%\Microsoft\OnlineManagement\Logs\Enrollment.log 及 %*userprofile*%\AppData\Local\Microsoft\OnlineManagement\Logs\Enrollement.log) 和 Windows Update 記錄檔 (%*windir*%\windowsupdate.log)，以供支援工程師參考。

### 後續步驟
如果這項疑難排解資訊對您沒有幫助，請連絡 Microsoft 支援服務 (如[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)中所述)。



<!--HONumber=Aug16_HO1-->


