---
title: "為已註冊的裝置新增 App"
description: "您必須先將應用程式新增至 Intune，才能部署它。 然後它便會提供於 Intune 主控台中，您可以在其中加以部署和管理。"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 01/11/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5b1f1ae-f177-450a-9af9-936a02d052e3
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: c688bf0912ec1150924743a9211a1268427fb13a
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2017
---
# <a name="add-apps-for-enrolled-devices-to-intune"></a>將已註冊裝置的應用程式新增至 Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

您必須先將應用程式新增至 Microsoft Intune，才能部署或管理它。 本主題說明如何新增已註冊裝置的應用程式。


> [!IMPORTANT]
> 本主題的資訊可協助您新增想要的應用程式，以部署至註冊的裝置與註冊的 Windows 電腦。 如果您想要使用 Intune 用戶端軟體，為您管理的 Windows 電腦新增應用程式，請參閱[在 Microsoft Intune 中新增 Windows 電腦的應用程式](add-apps-for-windows-pcs-in-microsoft-intune.md)。

## <a name="add-the-app"></a>新增應用程式
您將使用 Intune 軟體發行者設定應用程式的內容，並在適用時將應用程式上傳至您的雲端儲存空間。 使用下列程序：

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 [應用程式] &gt; [新增應用程式]，以啟動 Intune 軟體發行者。

    > [!TIP]
    > 您可能需要輸入 Intune 使用者名稱和密碼，才能啟動發行者。

2.  在發行者的 [軟體安裝程式] 頁面上，為 [選取將此軟體開放給裝置使用的方式] 選擇下列其中一個選項：
    - [軟體安裝程式]，適用於副檔名為 **.msi** 的應用程式︰
        - [選取軟體安裝程式檔案類型]。 這會指出您要部署的軟體類型。 例如，如果您想要安裝 iOS 應用程式，請選取 [iOS 應用程式套件 (*.ipa 檔案)]。
        - [指定軟體安裝檔的位置]。 輸入安裝檔的位置，或選擇 [瀏覽] 以從清單中選取位置。
        - [包含同一個資料夾的其他檔案和子資料夾]。 這個選項僅適用於 [Windows Installer] 檔案類型。<br>某些使用 Windows Installer 的軟體需要支援檔案，這些檔案通常位於與安裝檔所在的相同資料夾中。 如果您也想要部署這些檔案，請選取這個選項。<br>這個安裝類型會佔用部分雲端儲存空間。

  -   **外部連結**，適用於您想要藉由指定 App Store 連結來建立的應用程式：

        - **指定 URL**。 指定下列其中一項的 URL︰
            - 您所要部署應用程式的 App Store URL。 例如，如果您想要部署適用於 Android 的 Microsoft 遠端桌面應用程式，請指定 **https://play.google.com/store/apps/details?id=com.microsoft.rdc.android**。<br>若要尋找應用程式的 URL，請使用搜尋引擎來尋找包含該應用程式的商店頁面。 例如，若要尋找遠端桌面應用程式，您可以搜尋 **Microsoft 遠端桌面 Android**。
            - 網站。 Intune 會在裝置上部署該網站的捷徑圖示 (又稱為網路美工圖案)。
            - 網站上的應用程式。 Intune 將捷徑圖示部署到裝置上的應用程式。
        - **必須是受管理的瀏覽器，才可開啟此連結 (僅限 Android 及 iOS)**。 當您部署使用者的網站或 Web 應用程式連結時，它們只能在受 Intune 管理的瀏覽器中開啟。 他們的裝置上必須安裝此瀏覽器。<br>如需受管理瀏覽器的詳細資訊，請參閱[透過 Microsoft Intune 使用受管理的瀏覽器原則管理網際網路存取](manage-internet-access-using-managed-browser-policies.md)。<br>這個安裝類型不會佔用任何雲端儲存空間。

  -   **App Store 中的受管理 iOS 應用程式**，適用於 iTunes Store 中您想要使用行動應用程式管理 (MAM) 原則來管理的免費應用程式︰

        - **指定 URL**。 輸入您所要部署應用程式的 App Store URL。 例如，如果您想要部署 iOS 的 Microsoft 工作資料夾應用程式，請指定 **https://itunes.apple.com/us/app/work-folders/id950878067?mt=8**。<br>這個安裝類型不會佔用任何雲端儲存空間。

        例如，如果您想要將 iTunes Store 的 Microsoft Word 應用程式部署到裝置，頁面將如下所示︰

        ![Intune 軟體發行者](./media/publisher-for-mobile.png)

> [!NOTE]
> 當您加入及部署來自存放區的應用程式時，使用者必須擁有該存放區的帳戶，才能安裝應用程式。

3.  在 [軟體描述] 頁面上，設定下列項目：

    > [!TIP]
    > 根據您使用的安裝程式類型，可能已自動輸入其中的某些值。

    - **發行者**。 輸入應用程式發行者的名稱。
    - **名稱**。 輸入要顯示在公司入口網站中的應用程式名稱。<br>確定您使用的所有應用程式名稱都是唯一的。 如果有重複的應用程式名稱，使用者只會在公司入口網站中看到其中一個應用程式。
    - **描述**。 輸入應用程式的描述。 使用者會在公司入口網站中看到這個描述。
    - **軟體資訊的 URL**。 這只有在您選取 [軟體安裝程式] 後才能使用。 (選用) 輸入包含此應用程式相關資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **隱私權 URL**。 這只有在您選取 [軟體安裝程式] 後才能使用。 (選擇性) 輸入包含這個應用程式之隱私權資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **類別** (選用)。 選取其中一個內建應用程式類別。 這可以讓使用者在瀏覽公司入口網站時，更輕鬆地找到應用程式。
    - **在公司入口網站中將此項目顯示為熱門應用程式並將它反白**。 當使用者瀏覽應用程式時，在公司入口網站的主頁面上，以突顯的方式顯示應用程式。
    - **圖示** (選用)。 上傳要與應用程式相關聯的圖示。 這是使用者瀏覽公司入口網站時，會隨應用程式一起顯示的圖示。

        在此範例中，您可以設定 iOS 的 Microsoft Word 應用程式的描述︰

        ![軟體描述範例](./media/ios-software-description.png)

4.  在 [需求] 頁面上，選取必須符合才能在裝置上安裝應用程式的需求。 例如，針對 iOS 應用程式套件，您可以選取所需的 iOS 最低版本。 此外，您可以選取必須是哪種裝置類型，例如 iPhone 或 iPad。

    > [!TIP]
    > 並非所有類型的應用程式都會顯示[需求] 頁面。

5.  當您選取 [Windows Installer] 檔案類型時，會顯示進一步的精靈頁面。 您將軟體部署到執行 Windows 10 或更新版本的電腦 (其向 Intune 註冊) 上時，會使用此檔案類型。

6.  在 [摘要] 頁面上，檢閱您指定的資訊。 當您準備好時，選擇 [上傳]。

7.  選擇 [關閉] 來完成。

應用程式會顯示在 [應用程式] 工作區的 [應用程式] 節點上。

## <a name="example---deploying-msi-applications-to-windows-10-devices"></a>範例 - 將 .msi 應用程式部署至 Windows 10 裝置
在這段四分鐘的影片中，您將了解如何將 Windows Installer (.msi) 應用程式部署至執行 Windows 10 的已註冊裝置。<br><br>

<iframe src="https://channel9.msdn.com/Series/How-to-Control-the-Uncontrolled/6--How-to-Deploy-MSI-Applications-to-Windows-10-Using-Intune-and-Mobile-Device-Management-MDM/player" width="640" height="360" allowFullScreen frameBorder="0"></iframe>

## <a name="next-steps"></a>後續步驟

完成建立應用程式後，下一個步驟是進行部署。 若要深入了解，請參閱[在 Microsoft Intune 中部署應用程式](deploy-apps.md)。
