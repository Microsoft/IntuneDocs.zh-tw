---
title: Microsoft Intune 中 Android 的 kiosk 設定 - Azure | Microsoft Docs
description: 將您的 Android kiosk 裝置設定為單一應用程式和多應用程式 kiosk。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 9/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0b2a31a90dc0d88386a829756116edebd28990f9
ms.sourcegitcommit: bea4a81d262607c6e9dd1e26f5cd1a2faf7d051b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45602175"
---
# <a name="kiosk-settings-for-android-devices-in-intune"></a>Intune 中 Android 裝置的 kiosk 設定

您可以使用裝置組態設定，將裝置設定成單一或多個應用程式 kiosk 模式。 當裝置處於 kiosk 模式時，裝置的使用僅限於限制設定檔所定義的應用程式或 Web 連結。 

## <a name="restrict-an-android-kiosk-device-to-a-single-app"></a>將 Android kiosk 裝置限制為單一應用程式

若 kiosk 裝置的限制設定檔設定為 **kiosk 模式** = **單一應用程式 kiosk**，使用者只能存取單一應用程式。 啟動此模式中設定的裝置時，就會啟動特定的應用程式。 也會限制使用者無法開啟新應用程式或變更執行中應用程式。

1. 確定您要用於 kiosk 裝置的應用程式已[部署到裝置](apps-deploy.md)，且您已將應用程式指派給您為 kiosk 裝置所建立的裝置群組。
2. 前往 [Intune 入口網站](https://portal.azure.com)，然後選擇 [裝置設定] > [設定檔] > [建立設定檔]。
3. 在 [建立設定檔] 刀鋒視窗中，設定下列欄位：
     - **名稱**
     - **平台**：Android 企業
     - **設定檔類型**：[僅限裝置擁有者] > [裝置限制]
4. 選擇 [設定] > [kiosk]。
5. 針對 [kiosk 模式]，選擇 [單一應用程式 kiosk]。
6. 選擇 [選取受控應用程式]，然後選取受控 Google Play 應用程式，這是您想要利用此設定檔供裝置使用的唯一應用程式。
7. 選擇 [確定] > [確定] > [確定] > [建立]。
8. 選擇您剛才建立的設定檔 > [指派]。
9. 在 [指派給] 底下選擇 [選取的群組]。
10. 選擇 [選取要包含的群組] > 選擇您為 kiosk 裝置建立的裝置群組 > [選取]。

## <a name="restrict-a-kiosk-device-to-a-set-of-apps-or-web-links"></a>將 kiosk 裝置限制為一組應用程式或 Web 連結

若 kiosk 裝置的限制設定檔設定為 **Kiosk 模式** = **多應用程式 kiosk**，使用者只能存取您所設定之有限數目的應用程式。 您也可以定義一組使用者可以瀏覽的 Web 連結。 套用原則時，使用者會在主畫面上看到所允許之應用程式的圖示。

若要為多個應用程式設定 Android kiosk 裝置，請遵循下列主要步驟：

1. [從受控 Google Play 匯入和部署受控主畫面應用程式](#import-and -deploy-the-managed-home-screen-app)
2. [新增和指派可用於 kiosk 模式的應用程式](#add-and-assign-apps-that-can-be-used-in-kiosk-mode)
3. (選擇性) [新增可用於 kiosk 模式的 Web 連結](#add-web-links-that-can-be-used-in-kiosk-mode)

### <a name="import-and-deploy-the-managed-home-screen-app"></a>匯入和部署受控主畫面應用程式

1. 瀏覽至 [Google Play 上的受控主畫面頁面](https://play.google.com/work/apps/details?id=com.microsoft.launcher.enterprise)，並使用您用於其他受控 Google Play 應用程式的相同帳戶登入。
2. 選擇 [核准]。
3. 前往 [Intune 入口網站](https://portal.azure.com)，並選擇 [用戶端應用程式] > [受控 Google Play] > [同步]。
4. 選擇 [應用程式] > [管理主畫面] > [指派] > [新增群組]。
5. 在 [指派類型] 底下選擇 [必要]。
6. 選擇 [包含的群組] > [選取要包含的群組] > 選擇您為 kiosk 裝置建立的裝置群組 > [選取] > [確定] > [確定] > [儲存]。

> [!NOTE]
> 當您將受控主畫面應用程式新增至多應用程式 kiosk 設定檔時，會新增一個圖示。 但選取該圖示時卻沒有任何作用。 因此，您不需要將受控主畫面應用程式新增至多應用程式 kiosk 設定檔。

### <a name="add-and-assign-apps-that-can-be-used-in-kiosk-mode"></a>新增和指派可用於 kiosk 模式的應用程式

針對您想要在 kiosk 裝置上提供的每個應用程式，請遵循下列步驟：

1. [將應用程式新增至 Intune](store-apps-android.md)。
2. 選擇 [用戶端應用程式] > [應用程式] > 選擇應用程式 > [指派] > [新增群組]。
3. 在 [指派類型] 底下選擇 [必要]。
4. 選擇 [包含的群組] > [選取要包含的群組] > 選擇您為 kiosk 裝置建立的裝置群組 > [選取] > [確定] > [確定] > [儲存]。

### <a name="add-web-links-that-can-be-used-in-kiosk-mode"></a>新增可用於 kiosk 模式的 Web 連結

1. 前往 [Intune 入口網站](https://portal.azure.com)，並選擇 [用戶端應用程式] > [應用程式] > [新增]。
2. 在 [應用程式類型] 底下選擇 [Web 連結]。
3. 選擇 [設定]，並提供所需的資訊。 您不需要新增標誌影像，因為它會自動從網站的 favicon.ico 擷取。
4. 選擇 [確定] > [新增]。

請確定您已將 Web 應用程式部署到 kiosk 裝置。 如需詳細資訊，請參閱[將 Web 應用程式新增至 Microsoft Intune](web-app.md)。

### <a name="create-a-multi-app-kiosk-profile"></a>建立多應用程式 kiosk 設定檔

1. 前往 [Intune 入口網站](https://portal.azure.com)，然後選擇 [裝置設定] > [設定檔] > [建立設定檔]。
3. 在 [建立設定檔] 刀鋒視窗中，設定下列欄位：
     - **名稱**：鍵入直覺式名稱
     - **平台**：Android 企業
     - **設定檔類型**：[僅限裝置擁有者] > [裝置限制]
4. 選擇 [設定] > [kiosk]。
5. 針對 [Kiosk 模式]，選擇 [多應用程式 kiosk]。
6. 選擇 [新增]，然後選取您要利用此設定檔供裝置使用的應用程式或 Web 連結。
7. 選擇 [確定] > [確定] > [確定] > [建立]。
8. 選擇您剛才建立的設定檔 > [指派]。
9. 在 [指派給] 底下選擇 [選取的群組]。
10. 選擇 [選取要包含的群組] > 選擇您為 kiosk 裝置建立的裝置群組 > [選取] > [儲存]。

## <a name="next-steps"></a>接下來的步驟
[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。
