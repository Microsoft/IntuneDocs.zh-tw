---
title: 用戶端設定疑難排解
description: 針對常見用戶端安裝問題進行疑難排解。
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 02/22/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e46d292b-1d16-46db-a87f-d53eefa4d22a
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 39c0b0997bdbf229064e6b5ef25ab559b9252f83
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31028073"
---
# <a name="troubleshoot-client-setup-in-microsoft-intune"></a>Microsoft Intune 的用戶端設定疑難排解

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

請利用以下資訊協助您針對一般用戶端安裝問題進行疑難排解。 如果此資訊無法解決您的問題，請參閱[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)，以尋找更多方法來取得協助。

## <a name="client-installation-fails"></a>用戶端安裝失敗

-   如果 [Microsoft Intune 管理主控台](https://manage.microsoft.com/)中沒有顯示電腦的用戶端軟體部署警示，請檢查電腦的網際網路連線以及 Proxy 設定，並確定電腦可以與服務 URL ([https://manage.microsoft.com](https://manage.microsoft.com/)) 進行通訊。然後重試用戶端軟體的安裝。

-   您可以在 [系統管理]  工作區中設定通知規則，以在發出用戶端軟體部署失敗警示時，傳送電子郵件給選取的收件者。 如需詳細資訊，請參閱[取得 Microsoft Intune 警示通知](/intune-classic/deploy-use/get-notified-by-alerts)。

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

## <a name="computer-enrollment-package-doesnt-download"></a>電腦註冊套件未下載
**問題︰** 嘗試註冊電腦時，您遇到下列情況︰
-  無法下載註冊套件
-  出現 [下載] 對話方塊，但逾時

**解決方式︰** 在您用於下載的瀏覽器上，下載進行時，請確保下載已啟用，而且加密的檔案可以儲存至您的本機光碟。

## <a name="client-installation-hangs-with-error-code-0x80040154"></a>用戶端安裝停止並顯示錯誤碼 0x80040154
**問題**

-  註冊停止期間的用戶端安裝

-  無法註冊裝置

-  WindowsUpdate.log 中的錯誤 0x80040154

原因可能是電腦上的重大軟體更新不存在。

**解決方式：** 請確定您的軟體更新原則已啟用重大更新的安裝 (如[在 Microsoft Intune 中使用軟體更新讓 Windows 電腦維持最新狀態](/intune-classic/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)中所述)


## <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>Microsoft Intune policyplatform.log 中的原則相關錯誤
至於非 MDM Windows 裝置，policyplatform.log 檔案中的原則錯誤可能是因為裝置上 Windows 使用者帳戶控制 (UAC) 的非預設設定所造成。 某些非預設的 UAC 設定可能會影響 Microsoft Intune 用戶端安裝和原則執行。

### <a name="to-resolve-uac-issues"></a>解決 UAC 問題

1.  請如[從 Microsoft Intune 管理淘汰資料和裝置](/intune-classic/deploy-use/retire-devices-from-microsoft-intune-management)一文中所述來淘汰電腦。

2.  等候 20 分鐘讓用戶端軟體被移除。

    > [!NOTE]
    > 請勿嘗試從 [程式和功能] 移除用戶端。

3.  在 [開始] 功能表中輸入 **UAC**，開啟 [使用者帳戶控制] 設定。

4.  將通知滑桿移至預設設定。

## <a name="what-to-do-if-the-client-will-not-uninstall-from-the-microsoft-intune-administrator-console"></a>無法從 Microsoft Intune 系統管理員主控台解除安裝用戶端時的因應措施

### <a name="to-remove-the-client-software-by-using-the-microsoft-intune-command-line-tool"></a>使用 Microsoft Intune 命令列工具移除用戶端軟體

1.  以系統管理員模式開啟命令提示字元。

2.  前往資料夾 *%programfiles%\Microsoft\OnlineManagement\Common*

3.  執行下列命令：``ProvisioningUtil.exe /UninstallAgents /MicrosoftIntune``

## <a name="client-installation-error-codes"></a>用戶端安裝錯誤碼
下表說明用戶端軟體安裝失敗時 [警示]  中顯示的錯誤碼。 表中包含解決每個錯誤碼所代表之問題的建議。


|                                                                   錯誤碼                                                                    |                                                          可能的問題                                                          |                                                                                                                                                                                                建議的解決方式                                                                                                                                                                                                 |
|-------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                           <strong>0x80CF0437</strong>                                                           |                                  用戶端電腦上的時鐘未設定成正確的時間。                                  |                                                                                                                                                    確定用戶端電腦上的時鐘和時區已設成正確的時間和時區。                                                                                                                                                     |
|                              <strong>0x80240438</strong>、 <strong>0x80CF0438</strong>、 <strong>0x80CF401B</strong>                              |                               無法連線至 Intune 服務。 請檢查用戶端 Proxy 設定。                               |                   確認 Intune 支援用戶端電腦上的 Proxy 設定，而且用戶端電腦可以存取網際網路。 如需所支援之 Proxy 設定的詳細資訊，請參閱[使用 Microsoft Intune 的 Endpoint Protection 協助保護 Windows 電腦](/intune-classic/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)。                    |
|                                                           <strong>0x80CF402C</strong>                                                           |                                 無法連線至 Intune 服務。 檢查網路連線。                                  |                                                                                                                                                   確認電腦具有網路連線能力。 請確認已接上網路纜線或已開啟無線網路。                                                                                                                                                    |
|                                                     <strong>0x80240438、0x80CF0438</strong>                                                     |                              未設定 Internet Explorer 和本機系統中的 Proxy 設定。                              | 請檢查用戶端 Proxy 設定，並確認 Intune 所支援的用戶端電腦上的 Proxy 組態，且用戶端電腦可以存取網際網路。 如需所支援之 Proxy 設定的詳細資訊，請參閱[使用 Microsoft Intune 的 Endpoint Protection 協助保護 Windows 電腦](/intune-classic/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)。 |
|                                                           <strong>0x80043001</strong>                                                           |                                                 註冊套件已過期。                                                 |                                                                     從 [系統管理]  工作區下載並安裝最新的用戶端軟體套件。 如需相關指示，請參閱[使用 Microsoft Intune 安裝 Windows 電腦用戶端](/intune-classic/deploy-use/install-the-windows-pc-client-with-microsoft-intune)主題。                                                                      |
|                                                           <strong>0x80043004</strong>                                                           |                                            訂閱不存在或已停用。                                            |                                                                                                   確認您的帳戶和 Intune 訂閱仍然有效。 若要檢視您的帳戶設定，請使用您的帳戶登入 [Office 365 系統管理中心](http://go.microsoft.com/fwlink/?LinkId=698854%20)。                                                                                                   |
|                                                           <strong>0x80043002</strong>                                                           |                                                  帳戶處於維護模式。                                                   |                                                                                             您不能在帳戶處於維護模式時註冊新的用戶端電腦。 若要檢視您的帳戶設定，請使用您的帳戶登入 [Office 365 系統管理中心](http://go.microsoft.com/fwlink/?LinkId=698854%20)。                                                                                              |
|                                                           <strong>0x80043003</strong>                                                           |                                                        已刪除帳戶。                                                         |                                                                                                                                            確認您的帳戶和 Intune 訂閱仍然有效。 若要檢視您的帳戶設定，請登入您的帳戶。                                                                                                                                             |
|                                                           <strong>0x80043005</strong>                                                           |                                                  已淘汰用戶端電腦。                                                   |                                                                  等待幾個小時，並從電腦移除所有的舊版用戶端軟體，然後再次嘗試安裝用戶端軟體。 如需相關指示，請參閱上述的<strong>無法從 Microsoft Intune 系統管理員主控台解除安裝用戶端時的因應措施</strong>。                                                                  |
|                                                           <strong>0x80043006</strong>                                                           |                                  已達到帳戶允許的基座數目上限。                                   |                                                                                                                                                    貴組織必須購買額外的基座，您才可以在服務中註冊更多用戶端電腦。                                                                                                                                                     |
|                                                           <strong>0x80043007</strong>                                                           |                          在與安裝程式相同的資料夾中找不到憑證檔案。                          |                                 在開始安裝之前先解壓縮所有檔案。 請勿重新命名任何已解壓縮的檔案或改變其位置：所有檔案都必須位於同一個資料夾，否則安裝將會失敗。 如需詳細資訊，請參閱[使用 Microsoft Intune 安裝 Windows 電腦用戶端](/intune-classic/deploy-use/install-the-windows-pc-client-with-microsoft-intune)。                                  |
| <strong>0x8024D015</strong>、 <strong>0x00240005</strong>、 <strong>0x80070BC2</strong>、 <strong>0x80070BC9</strong>、 <strong>0x80CFD015</strong> |                       由於用戶端電腦仍在等待重新啟動，因此無法安裝軟體。                        |                                                                                                                                                                        重新啟動電腦，然後再次嘗試安裝用戶端軟體。                                                                                                                                                                        |
|                                                           <strong>0x80070032</strong>                                                           |                用戶端電腦不符合安裝用戶端軟體的一或多個必要條件。                 |                            確定用戶端電腦已安裝所有必要更新，然後再次嘗試安裝用戶端軟體。 如需安裝用戶端軟體之必要條件的詳細資訊，請參閱[適用於 Microsoft Intune 的網路基礎結構需求](/intune-classic/get-started/network-infrastructure-requirements-for-microsoft-intune)。                             |
|                                                           <strong>0x80043008</strong>                                                           |                                  無法啟動 Microsoft Online Management Updates 服務。                                  |                                                                                                                                               請依[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)所述連絡支援人員。                                                                                                                                                |
|                                                           <strong>0x80043009</strong>                                                           |                                     用戶端電腦已註冊到服務中。                                      |                                                                                        您必須先淘汰用戶端電腦，才能重新將它註冊到服務中。 如需指示，請參閱[從 Microsoft Intune 管理淘汰裝置](/intune-classic/deploy-use/retire-devices-from-microsoft-intune-management)。                                                                                         |
|                                                           <strong>0x8004300A</strong>                                                           |  (階段 21) 將註冊套件部署到 GPO，以安裝在使用者範圍而非電腦範圍時，發生錯誤。   |                                                               請確定 GPO 透過 GPSI 正確地將目標設為電腦範圍。 若要查看此主題的論壇文章，請參閱此 [TechNet 論壇](https://social.technet.microsoft.com/Forums/en-US/bb9fa71c-c132-4954-abb0-70be8acbd925/failed-to-install-windows-intune?forum=microsoftintuneprod)。                                                                |
|                                                           <strong>0x8004300B</strong>                                                           | 用戶端軟體安裝套件無法執行，因為不支援用戶端上執行的 Windows 版本。 |                                                               Intune 不支援用戶端電腦上執行的 Windows 版本。 如需支援的作業系統清單，請參閱[適用於 Microsoft Intune 的網路基礎結構需求](/intune-classic/get-started/network-infrastructure-requirements-for-microsoft-intune)。                                                               |
|                                                             <strong>0xAB2</strong>                                                              |                           Windows Installer 無法存取自訂動作的 VBScript 執行階段。                            |                                                      這個錯誤是由以動態連結程式庫 (DLL) 為基礎的自訂動作所造成。 在為 DLL 疑難排解時，您可能必須使用 [Microsoft 支援服務 KB198038：實用的封裝與部署工具](http://go.microsoft.com/fwlink/?LinkID=234255)中所述的工具。                                                       |
|                                                           <strong>0x8004300f</strong>                                                           |           無法安裝軟體，因為已經安裝了 System Center Configuration Manager 用戶端。            |                                                                                                                                                              移除 Configuration Manager 用戶端，然後再次嘗試安裝用戶端軟體。                                                                                                                                                               |
|                                                           <strong>0x80043010</strong>                                                           |      無法安裝軟體，因為已經安裝 Open Mobile Alliance Device Management (OMADM) 用戶端。      |                                                                                                                                                                     取消註冊 OMADM 用戶端，然後再次嘗試安裝用戶端軟體。                                                                                                                                                                     |

如果安裝問題持續發生，請依[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)所述連絡支援人員。 請備妥用戶端電腦註冊記錄檔 (位於 %*programfiles*%\Microsoft\OnlineManagement\Logs\Enrollment.log 及 %*userprofile*%\AppData\Local\Microsoft\OnlineManagement\Logs\Enrollement.log) 和 Windows Update 記錄檔 (%*windir*%\windowsupdate.log)，以供支援工程師參考。

## <a name="what-to-do-if-endpoint-protection-is-not-uninstalled-when-you-uninstall-the-client"></a>當您解除安裝用戶端時未解除安裝 Endpoint Protection 該怎麼辦

有時當您執行上述命令之後，主機保護 (Endpoint Protection) 代理程式可能會留下。 如果發生這種情況，請從提高權限的提示字元執行這個命令︰

    ```
    "C:\Program Files\Managed Defender\Setup.exe" /x /q /s
    ```


### <a name="next-steps"></a>接下來的步驟
如果此疑難排解資訊對您沒有幫助，請連絡 Microsoft 支援服務 (如[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)中所述)。
