---
title: "設定 PFX 的憑證基礎結構 | Microsoft Intune"
description: "建立及部署 .PFX 憑證設定檔。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/17/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2c543a02-44a5-4964-8000-a45e3bf2cc69
ms.reviewer: vinaybha
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7d1f37a2ba2e634fb75058d33eaaccf3aa5845b0
ms.openlocfilehash: 8fc1cc718fd0edae8b8ec4a0a8dc25487eafda2b



---
# <a name="configure-certificate-infrastructure"></a>設定憑證基礎結構
本主題說明建立及部署 .PFX 憑證設定檔需要什麼。

若要在組織中執行任何以憑證為基礎的驗證，您需要企業憑證授權單位。

若要使用 .PFX 憑證設定檔，除了企業憑證授權單位外，您還需要︰

-   可以與憑證授權單位通訊的電腦，或者您可以使用憑證授權單位電腦本身。

-  Intune Certificate Connector，其在可與憑證授權單位通訊的電腦上執行。

## <a name="onpremises-infrastructure-description"></a>內部部署基礎結構描述


-    **Active Directory 網域**：本節所列的所有伺服器 (除了 Web 應用程式 Proxy 伺服器) 均須加入 Active Directory 網域。

-  **憑證授權單位**：在企業版 Windows Server 2008 R2 或更新版本上執行的企業憑證授權單位 (CA)。 不支援獨立 CA。 如需如何設定憑證授權單位的指示，請參閱 [安裝憑證授權單位](http://technet.microsoft.com/library/jj125375.aspx)。
    如果您的 CA 執行 Windows Server 2008 R2，您必須 [從 KB2483564 安裝 Hotfix](http://support.microsoft.com/kb/2483564/)。

-  **可以與憑證授權單位通訊的電腦**：也可以使用憑證授權單位電腦本身。
-  **Microsoft Intune Certificate Connector**：您可使用 Intune 管理主控台來下載 **Certificate Connector** 安裝程式 (**ndesconnectorssetup.exe**)。 然後您可以在要安裝 Certificate Connector 的電腦上執行 **ndesconnectorssetup.exe** 。 針對 .PFX 憑證設定檔，將 Certificate Connector安裝在可與憑證授權單位通訊的電腦上。
-  **Web 應用程式 Proxy 伺服器** (選用)︰您可以將執行 Windows Server 2012 R2 或更新版本的伺服器用作 Web 應用程式 Proxy (WAP) 伺服器。 此組態：
    -  允許裝置使用網際網路連線接收憑證。
    -  是裝置連線透過網際網路來接收和更新憑證時的安全性建議。

 > [!NOTE]           
> -    裝載 WAP 的伺服器[必須安裝更新](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx)，以允許支援網路裝置註冊服務 (NDES) 所使用的長 URL。 此更新隨附於 [2014 年 12 月更新彙總套件](http://support.microsoft.com/kb/3013769)，或個別提供於 [KB3011135](http://support.microsoft.com/kb/3011135)。
>-  此外，裝載 WAP 的伺服器必須有 SSL 憑證，該憑證符合發佈給外部用戶端的名稱，並且信任 NDES 伺服器上使用的 SSL 憑證。 這些憑證讓 WAP 伺服器能從用戶端終止 SSL 連線，以及建立與 NDES 伺服器的新 SSL 連線。
    如需 WAP 憑證的相關資訊，請參閱[計劃使用 Web 應用程式 Proxy 發行應用程式](https://technet.microsoft.com/library/dn383650.aspx)的**規劃憑證**小節。 如需 WAP 伺服器的一般資訊，請參閱[使用 Web 應用程式 Proxy](http://technet.microsoft.com/library/dn584113.aspx)。|


### <a name="certificates-and-templates"></a>憑證和範本

|物件|詳細資料|
|----------|-----------|
|**憑證範本**|在發行的 CA 上所設定的範本。|
|**可信任的根 CA 憑證**|從發行 CA (或任何信任發行 CA 的裝置) 匯出為 **.cer** 檔案，並使用受信任的 CA 憑證加以部署至裝置之中的憑證。<br /><br />您針對每個作業系統平台使用單一受信任根 CA 憑證，並將它與您建立的每個受信任根憑證設定檔產生關聯。<br /><br />您可以在需要時使用其他受信任根 CA 憑證。 比方說，當您需要向 CA 提供信任，好讓它為您簽署 Wi-Fi 存取點的伺服器驗證憑證時，您可能就會這麼做。|


## <a name="configure-your-infrastructure"></a>設定基礎結構
在您設定憑證設定檔前，必須先完成下列工作。 執行這些工作需要對 Windows Server 2012 R2 及 Active Directory 憑證服務 (ADCS) 有一定程度的了解：

- **工作 1** - 設定憑證授權單位上的憑證範本。
- **工作 2** - 啟用、安裝及設定 Intune 憑證連接器。

### <a name="task-1-configure-certificate-templates-on-the-certification-authority"></a>工作 1 - 設定憑證授權單位上的憑證範本
在此工作中，您將發行憑證範本。

##### <a name="to-configure-the-certification-authority"></a>設定憑證授權單位

1.  在發行 CA 上，使用 [憑證範本] 嵌入式管理單元來建立新的自訂範本或複製並編輯現有的範本 (例如使用者範本) 以搭配 .PFX 使用。

    範本必須包含下列項目：

    -   指定範本的易記「範本顯示名稱」  。

    -   在 [主體名稱]  索引標籤上，選取 [在要求中提供] 。 

    -   在 [延伸]  索引標籤上，確定 [應用程式原則描述]  包含 [用戶端驗證] 。

        > [!IMPORTANT]
        > 若為 iOS 和 Mac OS X 憑證範本，請在 [延伸模組] 索引標籤上，編輯 [金鑰使用方法]，並確認未選取 [簽章是原件證明]。

2.  檢閱範本 [一般]  索引標籤上的 [有效期間]  。 根據預設，Intune 使用範本中所設定的值。 不過，您可以選擇設定 CA 以允許要求者指定不同的值，然後您可以從 Intune 管理主控台內設定該值。 如果您想要一律使用範本中的值，請略過此步驟中的其餘部分。

    > [!IMPORTANT]
    > iOS 和 Mac OS X 平台一律會使用在範本中設定的值，而不論您進行的其他設定。

    若要設定 CA 以允許要求者指定有效期間，請在 CA 上執行下列命令：

    a.  **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**

    b。  **net stop certsvc**

    c.  **net start certsvc**

3.  在發行的 CA 上使用 [憑證授權單位] 嵌入式管理單元來發行憑證範本。

    a.  選取 [憑證範本] 節點，並按一下 [動作]-&gt; [新增]&gt; [要發出的憑證範本]，然後選取您在步驟 2 中建立的範本。

    b。  檢視 [憑證範本]  資料夾下的發行範本來加以驗證。

4.  在 CA 電腦上，確認裝載 Intune 憑證連接器的電腦有註冊權限，使其能夠存取用來建立 .PFX 設定檔的範本。 在 CA 電腦內容的 [安全性]  索引標籤上設定該權限。

### <a name="task-2-enable-install-and-configure-the-intune-certificate-connector"></a>工作 2 - 啟用、安裝及設定 Intune Certificate Connector
在這項工作中，您將會：

下載、安裝及設定憑證連接器。

##### <a name="to-enable-support-for-the-certificate-connector"></a>啟用 Certificate Connector 的支援

1.  開啟 [Intune 管理主控台](https://manage.microsoft.com)，然後選擇 [管理] &gt; [憑證連接器]。

2.  選擇 [設定內部部署憑證連接器]。

3.  選取 [啟用憑證連接器]，然後選擇 [確定]。

##### <a name="to-download-install-and-configure-the-certificate-connector"></a>下載、安裝及設定憑證連接器

1.  開啟 [Intune 管理主控台](https://manage.microsoft.com)，然後選擇 [管理] &gt; [行動裝置管理] &gt; [憑證連接器] &gt; [下載憑證連接器]。

2.  下載完成後，執行下載的安裝程式 (**ndesconnectorssetup.exe**)。

  在可連接至憑證授權單位的電腦上執行安裝程式。 選擇 [.PFX 發佈] 選項，然後選擇 [安裝]。 安裝完成後，接著繼續依[設定憑證設定檔](configure-intune-certificate-profiles.md)中所述建立憑證設定檔。

   <!-- Not sure about step 3 below -->

3.  系統提示輸入憑證連接器的用戶端憑證時，請選擇 [選取]，然後選取您在工作 3 安裝的**用戶端驗證**憑證。

    選取用戶端驗證憑證之後，您會回到 [Microsoft Intune Certificate Connector 的用戶端憑證]  介面。 雖然您選取的憑證未顯示，請選擇 [下一步] 檢視該憑證的屬性。 然後依序選擇 [下一步] 與 [安裝]。

4.  在精靈完成後，但在關閉精靈之前，按一下 [啟動 Certificate Connector UI] 。

    > [!TIP]
    > 如果您在啟動 Certificate Connector UI 之前關閉精靈，您可以藉由執行下列命令重新加以開啟：
    >
    > **&lt;安裝路徑&gt;\NDESConnectorUI\NDESConnectorUI.exe**

5.  在 **Certificate Connector** UI 中：

    a. 選擇 [登入] 並輸入您的 Intune 服務管理員認證，或擁有全域管理權限的租用戶管理員認證。

    b。 選取 [進階] 索引標籤，然後提供對您的發行憑證授權單位具有 [發行及管理憑證] 權限的帳戶認證。

    c. 選擇 [套用]。

    您現在可以關閉 Certificate Connector UI。

6.  開啟命令提示字元，然後鍵入 **services.msc**。 然後按 **Enter**，以滑鼠右鍵按一下 [Intune 連接器服務]，再選擇 [重新啟動]。


### <a name="next-steps"></a>後續步驟
您現在已可設定憑證設定檔，如[設定憑證設定檔](Configure-Intune-certificate-profiles.md)中所述。



<!--HONumber=Nov16_HO3-->


