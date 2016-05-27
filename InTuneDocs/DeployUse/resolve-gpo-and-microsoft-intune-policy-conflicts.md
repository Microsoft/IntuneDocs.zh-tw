---
# required metadata

title: 解決 GPO 和 Intune 原則衝突 | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e76af5b7-e933-442c-a9d3-3b42c5f5868b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 解決群組原則物件 (GPO) 和 Microsoft Intune 原則衝突
Intune 使用原則幫助您在自己管理的電腦上管理設定。 例如，您可以使用原則來控制電腦上的 Windows 防火牆設定。 許多 Intune 設定與您透過 Windows 群組原則所做的設定很類似。 不過，有時候這兩種方法可能彼此衝突。

當發生衝突時，除非電腦無法登入網域，否則網域層級的群組原則將優先於 Intune 原則。 在這種情況下，Intune 原則會套用到用戶端電腦。

## 使用群組原則時的後續動作
請檢查您套用的任何原則，確定所有原則目前均未受群組原則管理。 您可以採用下列一種或多種方法，以協助防止衝突：

-   在安裝 Intune 用戶端之前，將您的電腦移到未套用群組原則設定的 Active Directory 組織單位 (OU)。 若 OU 包含已經在 Intune 中註冊但您不想對其套用群組原則設定的電腦，您也可以在這些 OU 上禁止群組原則繼承。

-   請使用 WMI 篩選器或安全性篩選器，將 GPO 僅限定在未受 Intune 管理的電腦。 如需有關如何執行這項作業的詳細資訊與範例，請參閱以下＜[如何篩選現有群組原則物件以避免與 Microsoft Intune 原則發生衝突](resolve-gpo-and-microsoft-intune-policy-conflicts.md#BKMK_Filter)＞一節。

-   停用或移除與 Intune 原則衝突的群組原則物件。

如需 Active Directory 和 Windows 群組原則的詳細資訊，請參閱您的 Windows Server 文件。

## 如何篩選現有 GPO 以避免與 Intune 原則發生衝突
如果您發現 GPO 的設定與 Intune 原則發生衝突，您可以使用下列其中一種篩選方法，將這些 GPO 僅限定在未受 Intune 管理的電腦。

### 使用 WMI 篩選器
WMI 篩選器會選擇性地將 GPO 套用至符合查詢條件的電腦。 若要套用 WMI 篩選器，在 Intune 服務中註冊任何電腦之前，請先將 WMI 類別執行個體部署至企業中的所有電腦。

#### 將 WMI 篩選器套用至 GPO

1.  複製以下文字並貼到文字檔中，然後在某個便利的位置將檔案儲存為 WIT.mof，就可以建立管理物件檔案。 該檔案所包含的 WMI 類別執行個體會部署到您要在 Intune 服務中註冊的電腦。

    ```
    //Beginning of MOF file.
    #pragma classflags("forceupdate")
    #pragma namespace ("\\\\.\\Root")
    instance of __Namespace
    {
       Name = "WindowsIntune";
    };

    #pragma namespace ("\\\\.\\Root\\WindowsIntune")
    [
       Description("This class defines Microsoft Intune common properties")
    ]
    class WindowsIntune_ManagedNode
    {
       [ read, Description("This defines whether Microsoft Intune Policy is enabled"): DisableOverride ToSubClass ]
       boolean WindowsIntunePolicyEnabled;
       [ read, key, Description("This property defines the version." "Example: 1.0"): ToSubClass ]
       string Version;
    };

    instance of WindowsIntune_ManagedNode
    {
       Version = "1.0";
       WindowsIntunePolicyEnabled = 1;
    };
    ```

2.  使用啟動指令碼或群組原則來部署檔案。 以下為啟動指令碼的部署命令。 在 Intune 服務中註冊用戶端電腦之前，必須先部署 WMI 類別執行個體。

    **C:/Windows/System32/Wbem/MOFCOMP &lt;MOF 檔案的路徑&gt;\wit.mof**

3.  依據您要篩選的 GPO 是套用至使用 Intune 管理的電腦，還是套用至未使用 Intune 管理的電腦而定，執行下列其中一個命令來建立 WMI 篩選器。

    -   若 GPO 套用至未使用 Intune管理的電腦，請使用下列命令：

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=0
        ```

    -   若 GPO 套用至受 Intune 管理的電腦，請使用下列命令：

        ```
        Namespace:root\WindowsIntune
        Query:  SELECT WindowsIntunePolicyEnabled FROM WindowsIntune_ManagedNode WHERE WindowsIntunePolicyEnabled=1
        ```

4.  在群組原則管理主控台中編輯 GPO，以套用先前步驟所建立的 WMI 篩選器。

    -   若 GPO 應該只套用至您要使用 Intune 管理的電腦，請套用篩選器 WindowsIntunePolicyEnabled=1

    -   若 GPO 應該只套用至您不要使用 Intune 管理的電腦，請套用篩選器 WindowsIntunePolicyEnabled=0

如需有關如何在群組原則中套用 WMI 篩選器的詳細資訊，請參閱部落格文章：[群組原則喜好設定中的安全性篩選、WMI 篩選及項目層級目標設定](http://go.microsoft.com/fwlink/?LinkId=177883)

### 使用安全性群組篩選器
群組原則可讓您將 GPO 僅套用至所選 GPO 之群組原則管理主控台的 [安全性篩選]  區域中指定的安全性群組。 根據預設，GPO 會套用至 Authenticated Users

-   在 [Active Directory 使用者和電腦] 嵌入式管理單元中，建立新的安全性群組，其中包含您不想使用 Intune 管理的電腦和使用者帳戶。 例如，您可以將群組命名為不在 Microsoft Intune 中

-   在群組原則管理主控台中，在選取之 GPO 的 [委派] 索引標籤處，以滑鼠右鍵按一下新的安全性群組，委派適當的 [讀取] 和 [套用群組原則] 權限至安全性群組中的使用者和電腦。 ([進階] 對話方塊提供 [套用群組原則]  權限。)

-   然後，將新的安全性群組篩選器套用至選取的 GPO，並移除 [已驗證的使用者]  預設篩選器。

必須隨著 Intune 服務中的註冊情形變化來維護新的安全性群組。

### 請參閱
[使用 Microsoft Intune 管理 Windows 電腦](manage-windows-pcs-with-microsoft-intune.md)


<!--HONumber=May16_HO2-->


