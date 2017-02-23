---

title: "安裝電腦用戶端軟體 | Microsoft Docs"
description: "使用本指南可協助您透過 Microsoft Intune 用戶端軟體管理 Windows 電腦。"
keywords: 
author: staciebarker
ms.author: stabar
ms.date: 01/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64c11e53-8d64-41b9-9550-4b4e395e8c52
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 39f7de3a94b813cbd7b353cd319ecc54fcbf8694
ms.openlocfilehash: 4b1b466c62ac1c8e03bc6cebd5e214649160185f


---

# <a name="install-the-intune-software-client-on-windows-pcs"></a>在 Windows 電腦上安裝 Intune 軟體用戶端
Windows 電腦可藉由安裝 Intune 用戶端軟體進行註冊。 Intune 用戶端軟體可以使用下列方式安裝：

- 由 IT 管理員：
  - 手動安裝
  - 使用群組原則安裝
  - 安裝包含在磁碟映像中

- 由手動安裝軟體用戶端的使用者安裝

IT 管理員部署至使用者或使用者下載的 Intune 軟體用戶端，包含在 Intune 管理中註冊電腦時所需的最小軟體。 註冊電腦之後，Intune 軟體用戶端會接著下載管理電腦時所需的完整用戶端軟體。

此系列下載可降低對網路頻寬的影響，並將在 Intune 中初次註冊電腦時所需的時間縮到最短。 同時也可確保第二個下載完成之後，用戶端都是安裝最新可用的軟體。

## <a name="download-the-intune-client-software"></a>下載 Intune 用戶端軟體

除了使用者自行安裝 Intune 用戶端軟體以外的所有方法，都必須由 IT 管理員先下載軟體，然後才能部署至使用者。

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com/)中，按一下 [系統管理] &gt; [用戶端軟體下載]。

  ![下載 Intune 電腦用戶端](../media/pc-sa-client-download.png)

2.  在 [用戶端軟體下載] 頁面上，按一下 [下載用戶端軟體]。 接著將包含軟體的 **Microsoft_Intune_Setup.zip** 套件儲存到網路上的安全位置。

    > [!NOTE]
    > Intune 用戶端軟體安裝套件包含和您的帳戶有關的唯一且專屬的資訊，並可透過內嵌憑證取得。 若未經授權的使用者能夠取該安裝套件，其便能將電腦註冊到其內嵌憑證所代表的帳戶，從而獲取存取公司資源的權限。

3.  將安裝套件的內容解壓縮到您的網路上安全的位置。

    > [!IMPORTANT]
    > 請勿重新命名或移除已解壓縮的 **ACCOUNTCERT** 檔案，否則用戶端軟體安裝將會失敗。

## <a name="deploy-the-client-software-manually"></a>手動部署用戶端軟體

在將要安裝軟體用戶端的電腦上，移至用戶端軟體安裝檔案所在的資料夾。 接著執行 **Microsoft_Intune_Setup.exe** 安裝用戶端軟體。

> [!NOTE]
> 當您將游標停留在用戶端電腦上工作列中的圖示上時，即可顯示安裝的狀態。

## <a name="deploy-the-client-software-by-using-group-policy"></a>使用群組原則部署用戶端軟體

1.  在包含 **Microsoft_Intune_Setup.exe** 和 **MicrosoftIntune.accountcert** 檔案的資料夾中，執行下列命令以解壓縮適用於 32 位元和 64 位元電腦的 Windows Installer 安裝程式：

    ```
    Microsoft_Intune_Setup.exe/Extract <destination folder>
    ```

2.  將 **Microsoft_Intune_x86.msi** 檔案、**Microsoft_Intune_x64.msi** 檔案及 **MicrosoftIntune.accountcert** 檔案複製到要安裝用戶端軟體，並可供所有電腦可存取的網路位置。

    > [!IMPORTANT]
    > 請勿將這些檔案分開或重新命名，否則用戶端軟體安裝將會失敗。

3.  使用群組原則將軟體部署到您網路上的電腦。

    如需有關如何使用群組原則來自動部署軟體的詳細資訊，請參閱[適用於新手的群組原則](https://technet.microsoft.com/library/hh147307.aspx)。

## <a name="deploy-the-client-software-as-part-of-an-image"></a>隨映像一起部署用戶端軟體
您可以使用下列程序作為前導，將 Intune 用戶端軟體隨著作業系統映像一起部署到電腦：

1.  將用戶端安裝檔案 **Microsoft_Intune_Setup.exe** 及 **MicrosoftIntune.accountcert** 複製到參考電腦的 **%系統磁碟機%\Temp\Microsoft_Intune_Setup** 資料夾。

2.  將下列命令新增至 **SetupComplete.cmd** 指令碼，以建立 **WindowsIntuneEnrollPending** 登錄項目：

    ```
    %windir%\system32\reg.exe add HKEY_LOCAL_MACHINE\Software\Microsoft\Onlinemanagement\Deployment /v
    WindowsIntuneEnrollPending /t REG_DWORD /d 1
    ```

3.  將下列命令新增至 **setupcomplete.cmd**，以使用 /PrepareEnroll 命令列引數執行註冊套件：

    ```
    %systemdrive%\temp\Microsoft_Intune_Setup\Microsoft_Intune_Setup.exe /PrepareEnroll
    ```
    > [!TIP]
    > **SetupComplete.cmd** 指令碼可讓 Windows 安裝程式在使用者登入之前修改系統。 **/PrepareEnroll** 命令列引數會準備目標電腦，以在 Windows 安裝程式完成後自動註冊到 Intune 中。

4.  將 **SetupComplete.cmd** 放在參照電腦的 **%Windir%\Setup\Scripts** 資料夾中。

5.  擷取參照電腦的映像，然後將映像部署到目標電腦。

    當目標電腦在 Windows 安裝程式完成後重新啟動時，便會建立 **WindowsIntuneEnrollPending** 登錄機碼。 註冊套件會檢查電腦是否已經註冊。 如果電腦已註冊，將不會採取進一步的動作。 如果電腦未註冊，註冊套件會建立「Microsoft Intune 自動註冊工作」。

    當自動註冊工作在下次排程時間執行時，會檢查 **WindowsIntuneEnrollPending** 登錄值是否存在，並會嘗試在 Intune 中註冊目標電腦。 如果註冊因為任何原因失敗，工作下次執行時會重新嘗試註冊。 重試會持續一個月。

    當註冊成功或經過一個月之後 (取先達到者)，將會從目標電腦刪除 Intune 自動註冊工作、**WindowsIntuneEnrollPending** 登錄值與帳戶憑證。

## <a name="instruct-users-to-self-enroll"></a>指示使用者自行註冊

使用者可以前往[公司入口網站](http://portal.manage.microsoft.com)安裝 Intune 用戶端軟體。 若入口網站能偵測出裝置為 Windows 電腦，就會提示使用者下載 Intune 軟體用戶端來註冊電腦。 下載軟體之後，使用者可以加以安裝來管理其電腦。

使用者在 Web 入口網站中看到的實際資訊可能有所不同，視您帳戶的 MDM 授權和使用者電腦的平台與版本而定。

![Intune 入口網站將會提示您下載 Intune 軟體用戶端](../media/software-client-download.png)

## <a name="monitor-and-validate-successful-client-deployment"></a>監視並驗證成功的用戶端部署
請使用下列其中一個程序協助您監視及驗證成功的用戶端部署。

### <a name="to-verify-the-installation-of-the-client-software-from-the-microsoft-intune-administrator-console"></a>若要從 Microsoft Intune 系統管理員主控台確認用戶端軟體的安裝

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com/)中，按一下 [群組] &gt; [所有裝置] &gt; [所有電腦]。

2.  在清單中，尋找正與 Intune 通訊的受管理電腦，或在 [搜尋裝置] 方塊中，輸入電腦名稱或局部名稱來搜尋特定的受管理電腦。

3.  從主控台的下方窗格中，查看電腦的狀態。 解決任何錯誤。

### <a name="to-create-a-computer-inventory-report-to-display-all-enrolled-computers"></a>若要建立電腦清查報表以顯示所有已註冊的電腦

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com/)中，按一下 [報表] &gt; [電腦清查報表]。

2.  在 [建立新報表] 頁面上，保留所有欄位的預設值 (除非您要套用篩選器)，然後按一下 [檢視報表]。

3.  [電腦清查報表] 頁面會隨即在新視窗中開啟，顯示已在 Intune 中註冊成功的所有電腦。

    > [!TIP]
    > 按一下報表中的任意欄標題，依該欄的內容排序清單。


### <a name="see-also"></a>請參閱
[使用 Microsoft Intune 管理 Windows 電腦](manage-windows-pcs-with-microsoft-intune.md)
[為用戶端安裝進行疑難排解](../troubleshoot/troubleshoot-client-setup-in-microsoft-intune.md)



<!--HONumber=Feb17_HO1-->


