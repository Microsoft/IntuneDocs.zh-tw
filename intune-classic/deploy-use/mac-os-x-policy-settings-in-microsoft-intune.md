---
title: Mac OS X 原則設定
description: Intune 提供一些內建的一般設定，您可在 Mac OS X 裝置上加以設定。 此外，您可以使用 Apple Configurator 工具建立 Intune 所沒有的自訂設定。
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 98b2f19b-bee8-42d7-a215-a716d56a25a3
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 873b1041ec7f5a993195e4a988580fd88100b282
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="mac-os-x-configuration-policy-settings-in-microsoft-intune"></a>Microsoft Intune 的 Mac OS X 設定原則設定

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune 提供一些內建的一般設定，您可在 Mac OS X 裝置上加以設定。 此外，您可以使用 Apple Configurator 工具建立 Intune 所沒有的自訂設定。

## <a name="general-configuration-policy-settings"></a>一般設定原則設定

使用 Microsoft Intune **Mac OS X 一般設定原則**進行下列設定：

-   **裝置安全性設定**。 您可以從預先定義的設定清單中選擇，以控制裝置上某個功能範圍。

-   **相容和不相容的應用程式**。 指定在公司中相容或不相容的應用程式清單。 「不相容的應用程式報告」可用來檢視您在清單中指定的應用程式與使用者已安裝的應用程式是否相容 (但無法實際封鎖應用程式的安裝作業)。

如果這份清單中未包含您所需要的設定，您可以使用 Mac OS X 自訂原則加以建立，以便使用 Apple Configurator 工具匯入您所建立的設定。 如需詳細資訊，請參閱本主題稍後的＜自訂原則設定＞。

### <a name="password-settings"></a>密碼設定

|設定名稱|詳細資料|
|----------------|---------------|
|**需要密碼才可解除鎖定裝置**|指定使用者是否必須使用密碼來存取其 Mac 電腦。 **重要事項：** 不同於 iOS 裝置，在 Mac OS X 裝置上，使用者不會立即收到要更新密碼才能符合這項設定的通知。|
|**必要的密碼類型**|指定密碼是否只能是**數字**，或者是否必須為**英數字元** (包含字母和數字)。 **重要：**只有 Mac OS X 10.10.3 版與更新版本才支援這項設定。|
|**密碼所需的複合字元數**|指定密碼所需的複合字元數 (**0** 到 **4** 個)。<br /><br />複合字元是一種符號，例如 **?**。|
|**密碼長度下限**|指定密碼長度下限 (**4** 到 **14** 個字元)。|
|**允許簡單密碼**|允許使用簡單密碼，例如 **0000** 或 **1234**。|
|**在非使用狀態幾分鐘後需要輸入密碼**|指定電腦必須處於非使用狀態多久的時間，才需要密碼來解除鎖定。|
|**密碼到期 (天數)**|指定使用者經過多少天後必須變更密碼 (**1** 到 **255** 天)。|
|**記住密碼歷程記錄**|防止使用者使用之前用過的密碼。 完成此設定後，您也可同時設定 **[避免重複使用先前的密碼]**，以指定不得重複使用的先前密碼數目 (**1** 到 **24** 個)。|
|**在非使用狀態幾分鐘後啟用螢幕保護**|指定電腦必須閒置多久的時間，才會啟用螢幕保護程式。|

### <a name="settings-for-compliant-and-noncompliant-apps"></a>相容與不相容之應用程式的設定
在 **[Mac OS X 相容和不相容的應用程式清單]** 中，啟用 **[裝置的受管理設定]**，然後使用下列資訊來指定相容或不相容的應用程式清單。

> [!NOTE]
> 單一原則只能包含一份相容應用程式的清單或不相容應用程式的清單。 您不能在相同的原則中同時指定兩者。
>
> Intune 可讓您回報具有不相容應用程式的裝置， 但不會封鎖安裝作業，也不會移除不相容的應用程式。

|設定名稱|詳細資料|
|----------------|---------------|
|**當使用者安裝列出的應用程式時回報不符合規範**|顯示不允許使用者安裝的 Mac OS X 應用程式。 如果使用者安裝上述任何應用程式，**[不相容的應用程式報告]** 中會回報這些應用程式。|
|**當使用者安裝未列出的應用程式時回報不符合規範**|顯示允許使用者安裝的 Mac OS X 應用程式。 如果使用者安裝其他任何應用程式，**[不相容的應用程式報告]**中會回報這些應用程式。|
|**新增**|將應用程式加入選取的清單中。 指定您選擇的名稱，並選擇性地指定應用程式發行者及應用程式套件組合識別碼。 提示：若要尋找應用程式套件組合識別碼，請在已安裝應用程式的 Mac 電腦上，執行下列步驟：<ol><li>開啟應用程式安裝所在的資料夾 (例如 **/Applications**)。</li><li>選取 &lt;應用程式名稱&gt;***.app* 搭售方案，然後選擇 [Show Package Contents] (顯示套件內容)。</li><li>開啟 **Info.plist** 檔案。</li><li>檢查已與索引鍵 **CFBundleIdentifier** 建立關聯的值。</li></ol>套件組合識別碼的格式為 **com.contoso.appname**。|
|**匯入應用程式**|匯入逗點分隔值檔案中所指定的應用程式清單。 請在檔案中使用「應用程式名稱, 發行者, 套件組合識別碼」格式。|
|**編輯**|編輯所選應用程式的名稱、發行者和應用程式套件組合識別碼。|
|**刪除**|從清單中刪除選取的應用程式。|
> [!TIP]
> 如需 Intune 報表的詳細資訊，請參閱[透過報表來了解 Microsoft Intune 作業](understand-microsoft-intune-operations-by-using-reports.md)。

> [!IMPORTANT]
> 當 Mac OS X 裝置處於睡眠模式時，無法傳送或清查原則與設定檔。 因此，Intune 主控台可能會在下次裝置從睡眠模式喚醒之前，暫時顯示 **[錯誤的原則設定]** 狀態。

### <a name="monitor-compliant-and-noncompliant-apps"></a>監視相容與不相容的應用程式
使用 **[不相容的應用程式報告]** 檢視指定應用程式的相容性。

#### <a name="to-run-a-report"></a>若要執行報表

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 **[報表]** &gt; **[不相容的應用程式報表]**。

2.  選取您想要檢查的裝置群組、選取是否要檢查相容應用程式和 (或) 不相容應用程式，然後選擇 **[檢視報告]**。

## <a name="mac-os-x-custom-policy-settings-in-microsoft-intune"></a>Microsoft Intune 的 Mac OS X 自訂原則設定
使用 Microsoft Intune **Mac OS X 自訂組態原則**，將您使用 [Apple Configurator 工具](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)建立的設定部署至 Mac OS X 裝置。 此工具讓您能夠建立許多設定來控制這些裝置的操作，並將它們匯出到組態設定檔。 您接著可將這個組態設定檔匯入 Intune Mac OS X 自訂原則，並將設定部署到組織中的使用者和裝置。

這項功能可讓您部署無法使用 Intune Mac OS X 一般組態原則設定的 Mac OS X 設定。

### <a name="prerequisites"></a>必要條件
開始之前，您必須安裝 Apple Configurator，並建立包含您要部署到使用者或裝置之設定的組態檔。 您可以從 [Mac App Store](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)下載並了解 Apple Configurator。

> [!NOTE]
> Intune 不會回報 Mac OS X 自訂原則中個別設定的合規性。 不過，會報告原則的整體相容性。

### <a name="general-settings"></a>一般設定

|設定名稱|詳細資料|
    |----------------|--------------------|
    |**名稱**|輸入 Mac OS X 自訂原則的專用名稱，有助於您在 Intune 主控台中識別該原則。|
    |**描述**|提供可給予 Mac OS X 自訂原則概觀的描述，以及可協助您找到該描述的其他相關資訊。|


### <a name="custom-settings"></a>自訂設定

|設定名稱|詳細資料|
    |----------------|--------------------|
    |**自訂組態設定檔名稱 (對使用者顯示)**|提供原則的名稱，其將顯示於裝置上和 Intune 原則報告中。|
    |**組態設定檔**|選擇 **[匯入]**，然後瀏覽到您使用 Apple Configurator 建立的組態設定檔。 **提示：**如需建立組態設定檔的說明，請參閱本主題中的＜如何建立組態設定檔＞。|
    |**組態設定檔詳細資料**|顯示您所匯入組態設定檔的 XML 程式碼。|



### <a name="how-to-create-a-configuration-profile-file"></a>如何建立組態設定檔
您可以透過兩種方式來建立自訂原則所使用的組態設定檔：

-   從 Apple Configurator 工具匯出檔案 (副檔名為 **.mobileconfig**)。

-   使用 [Apple 組態設定檔金鑰參考](https://developer.apple.com/library/ios/featuredarticles/iPhoneConfigurationProfileRef/Introduction/Introduction.html)中的適當結構描述，自行製作檔案。


### <a name="see-also"></a>另請參閱
[使用 Microsoft Intune 原則管理裝置的設定及功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
