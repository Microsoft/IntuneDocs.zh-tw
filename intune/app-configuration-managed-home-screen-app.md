---
title: 設定 Microsoft Managed Home Screen 應用程式
titleSuffix: Microsoft Intune
description: 了解如何設定 Microsoft Managed Home Screen 應用程式。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 865c7f03-f525-4dfa-b3a8-d088a9106502
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a9a61b89f07bfacf1dc41be1412f79509e1e147d
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66049945"
---
# <a name="configure-the-microsoft-managed-home-screen-app-for-android-enterprise"></a>設定適用於 Android Enterprise 的 Microsoft Managed Home Screen 應用程式

Managed Home Screen 這個應用程式用於企業擁有的 Android Enterprise 專用裝置，這些裝置透過 Intune 註冊，並在多應用程式 Kiosk 模式中執行。 對於這些裝置，Managed Home Screen 扮演了啟動器的角色，讓其他經核准的應用程式可在其之上執行。 Managed Home Screen 讓 IT 系統管理員能夠自訂裝置，及限制終端使用者可以存取的功能。 

## <a name="when-to-configure-the-microsoft-managed-home-screen-app"></a>設定 Microsoft Managed Home Screen 應用程式的時機

一般而言，如果您可以透過 [裝置設定] 來進行設定，就請在該處進行。 這樣做可以節省您的時間、盡可能減少失誤，並獲得較佳的 Intune 支援體驗。 不過，有些 Managed Home Screen 設定目前僅透過 Intune 主控台中的 [應用程式設定原則] 刀鋒視窗提供。 請使用這份文件了解如何使用設定設計工具或 JSON 指令碼來進行不同的設定。 

> [!NOTE]
> 目前可以 (並建議) 透過 [用戶端應用程式] 和 [裝置設定] 來設定允許列出的應用程式及釘選的 Web 連結。 如需 [裝置設定] 中會影響 Managed Home Screen 的設定完整清單，請參閱[專用裝置設定](device-restrictions-android-for-work.md#dedicated-device-settings)。  

首先，在 Azure 入口網站中瀏覽到 Intune 主控台，然後前往 [用戶端應用程式] > [應用程式設定原則]。 為執行 **Android** 的 [受控裝置] 新增設定原則，然後選擇 [Managed Home Screen] 作為建立關聯的應用程式。 按一下 [組態設定] 來進行其他可用的 Managed Home Screen 設定。 

## <a name="choosing-a-configuration-settings-format"></a>選擇組態設定格式

有兩種方法可以用來定義 Managed Home Screen 的組態設定：

- **設定設計工具**易於使用的 UI 可讓您將功能切換為開啟或關閉及設定值，藉此進行設定。 在這個方法中，有幾個值類型為 `BundleArray` 的設定索引碼無法使用。 這些只能設定索引碼藉由輸入 JSON 資料來設定。 
- **JSON 資料**可讓您使用 JSON 指令碼定義所有可用的設定索引碼。 

若您使用設定設計工具來新增屬性，可以將這些屬性自動轉換成 JSON，方法是從 [組態設定格式] 下拉式清單選取 [輸入 JSON 資料]。

![組態設定格式選項的螢幕擷取畫面](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_01.png)

## <a name="using-configuration-designer"></a>使用設定設計工具

設定設計工具可讓您選取預先填入的設定及其相關值。 

![新增的組態設定螢幕擷取畫面](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_02.png)

下表列出 Managed Home Screen 可用的設定索引碼、值類型、預設值及描述。 描述提供取決於所選值的預期裝置行為。 在設定設計工具中無法使用的設定索引碼，不會在表中列出。

| 設定索引碼 | 數值類型 | 預設值 | 說明 |
|---------------------------------------------------------------------------------------------------------------------------|-------------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 設定格線大小 | 字串 | 自動 | 讓您可為要放置在 Managed Home Screen 上的應用程式設定格線大小。 您可以利用 `columns;rows` 格式來設定應用程式的列數與欄數以定義格線大小。 如果您定義了格線大小，在主畫面上，一列中顯示的應用程式最大數目會是您設定的列數目，而在主畫面上，一欄中顯示的應用程式最大數目會是您設定的欄數目。 |
| 啟用畫面頁首 | bool | TRUE | 為 Managed Home Screen 提供的不同檢視啟用頂端標題，例如摘要或摘要卡片。 若您啟用這項設定，裝置使用者就會看到頁首。 |
| 啟用裝置狀態列 | bool | TRUE | 在主畫面啟用狀態列 (顯示目前連線的頂端列，例如 WiFi 等)。 若您啟用這個設定索引碼，終端使用者就能夠看到顯示在狀態列上的圖示，代表連線及使用中的應用程式。 |
| 啟用通知徽章 | bool | FALSE | 針對應用程式圖示啟用通知徽章，以顯示有關應用程式的新通知數目。 若您啟用此設定，終端使用者會在有未讀通知的應用程式看到通知徽章。 若您維持停用這個設定索引碼，即使應用程式可能有未讀通知，終端使用者也不會看到任何通知徽章。 |
| 鎖定主畫面 | bool | TRUE | 讓終端使用者無法在主畫面上移動應用程式圖示。 如果您啟用這個設定索引碼，主畫面上的應用程式圖示就會鎖住，使得終端使用者無法拖放到主畫面的其他方格位置。 若改為 `false`，終端使用者就能夠在 Managed Home Screen 移動應用程式與 Web 連結圖示。  |
| 設定裝置桌布 | 字串 | 預設 | 讓您可以輸入想要設為桌布的影像 URL，以設定自選的桌布。 |
| 設定應用程式圖示大小 | 整數 | 2 | 讓您可以設定顯示在主畫面上的應用程式圖示大小。 您可以在這項設定中選擇下列值，以呈現不同大小 - 0 (最小)、1 (小)、2 (正常)、3 (大) 和 4 (最大)。 |
| 設定應用程式資料夾圖示 | 整數 | 0 | 讓您可以定義主畫面上的應用程式資料夾外觀。 您可以從下列值中選擇外觀：深色正方形 (0)；深色圓形 (1)；淺色正方形 (2)；淺色圓形 (3)。 |
| 啟用手勢 | bool | FALSE | 讓終端使用者能夠將動作指派給不同的手勢，例如向上撥動及向下撥動。 若您停用這個設定索引碼，如果有第二頁，終端使用者就只能向右撥動，以及返回首頁。 |
| 啟用垂直捲動 | bool | FALSE | 在 Managed Home Screen 啟用垂直捲動。 如果您啟用這個設定索引碼，終端使用者就只能垂直巡覽到不同頁面，而不能垂直撥動。 |
| 設定主畫面佈景主題 | 字串 | Theme.Light.Blue | 讓您可以從一組不同色彩的預先定義佈景主題中，選擇主畫面的佈景主題。 您可藉由使用下列格式輸入字串值，來選擇下列佈景主題。   Theme.Light.Green。 此處的 Light 可以代換為 Dark，成為深色佈景主題，而 Green 可以代換為 Blue、Yellow、Pink、Red、Orange 和 Purple。 |
| 啟用固定區 | bool | FALSE | 啟用主畫面底部的應用程式固定區，以顯示常設應用程式，及所有已安裝應用程式的進入點。 如果您啟用此設定索引碼，終端使用者就能夠在固定區存取應用程式，也能存取所有應用程式區段，以前往裝置上所有已安裝應用程式的清單，而不論是否已允許列出這些應用程式。 |
| 設定畫面方向 | 整數 | 1 | 讓您可將主畫面的方向設為直向模式、橫向模式或允許自動旋轉。 您可以輸入值 1 (直向模式)、2 (橫向模式)、3 (自動旋轉)，來設定方向。 |
| 啟用主畫面摘要 | bool | FALSE | 啟用主畫面摘要，查看方式為向左撥動主畫面。 此摘要會顯示不同類型的內容，例如新聞、日曆、常用應用程式及 Cortana 語音助理卡片等。若您啟用此項，終端使用者就能夠藉由向左撥動主畫面來巡覽到摘要。 |
| 啟用概觀模式 | bool | FALSE | 讓終端使用者可在主畫面上新增或移除不同的頁面，存取方式是從預設畫面向右撥動。 若您啟用此項，終端使用者就能夠在主畫面預設畫面的右方新增頁面，也可變更預設頁面，並能夠在 Managed Home Screen 上存取設定。 |
| 啟用裝置遙測 | bool | FALSE | 啟用正對 Managed Home Screen 擷取的所有遙測。 若您啟用此項，Microsoft 就能夠截取裝置使用方式遙測，例如在這部裝置上啟動某個應用程式遙測。 |
| 設定列入允許清單的應用程式 | bundleArray | FALSE | 讓您能夠從裝置上已安裝的應用程式中，定義一組可在主畫面上顯示的應用程式。 定義應用程式的方式，是依您想要顯示的應用程式輸入應用程式套件名稱，例如 com.android.settings 會讓設定可在主畫面上存取。 您允許列於此區段的應用程式應已安裝於裝置上，才能在主畫面上顯示。 |
| 設定釘選的 Web 連結 | bundleArray | FALSE | 讓您可在主畫面上，將網站釘選為快速啟動圖示。 您可以利用這項設定定義 URL，並將其新增到主畫面，讓終端使用者只要輕觸一下，即可在瀏覽器中啟動。 |
| 啟用搜尋列 | bool | FALSE | 在主畫面上啟用搜尋列。 如果您啟用此項，裝置的使用者會在主畫面上看到搜尋列，而他們能在該處輸入任何想在 Web 上搜尋的內容。 |
| 停用設定應用程式 | bool | FALSE | 停用 Managed Home Screen 的設定頁面。 若您停用此項，裝置的終端使用者就無法前往 Managed Home Screen 的設定。 |
| 啟用螢幕保護裝置 | bool | FALSE | 啟用或停用螢幕保護裝置。 若設為 true，您可以設定 **screen_saver_image**、**screen_saver_show_time**、**inactive_time_to_show_screen_saver** 及 **media_detect_screen_saver**。 |
| 螢幕保護裝置圖片 | 字串 |   | 設定螢幕保護裝置圖片的 URL。 若未設定 URL，裝置會在螢幕保護裝置啟用時，顯示預設畫面。  |
| 螢幕保護裝置顯示時間 | 整數 | 0 | 提供選項，設定裝置在螢幕保護裝置模式期間要顯示螢幕保護裝置的時間長度，以秒為單位。 若設為 0，螢幕保護裝置會在螢幕保護裝置模式無限期顯示，直到裝置進入使用狀態為止。  |
| 啟用螢幕保護裝置的閒置時間 | 整數 | 30 | 在觸發螢幕保護裝置之前的裝置閒置秒數。 若設為 0，裝置就永遠不會進入螢幕保護裝置模式。 |
| 顯示螢幕保護裝置之前的媒體偵測 | bool | TRUE | 選擇當裝置上在播放音訊/視訊時，裝置畫面是否應顯示螢幕保護裝置。 若設為 true，不論 **inactive_time_to_show_scree_saver**的值為何，裝置都不會播放音訊/視訊。 若設為 false，裝置畫面會根據 **inactive_time_to_show_screen_saver** 中設定的值來顯示螢幕保護裝置。   |
| 啟用虛擬 Home 鍵 | bool | FALSE | 將此設定改為 `True`，即允許終端使用者存取 Managed Home Screen 的 Home 鍵，讓使用者可從目前所在的工作返回 Managed Home Screen。  |
| 虛擬 Home 鍵類型 | 字串 | swipe_up | 使用 **swipe_up**，透過向上撥動的手勢存取 Home 鍵。 使用 **float** 來存取附著式、常設的 Home 鍵，可讓使用者在畫面上四處移動。 |
| 電池與訊號強度指標列 | bool | True  | 將此設定改為 `True`，會顯示電池與訊號強度指標列。 |
| 結束鎖定工作模式的密碼 | 字串 |   | 輸入 4-6 位數的代碼，用來暫時退出鎖定工作模式，以進行疑難排解。 |
| 顯示 Wi-Fi 設定 | bool | FALSE | 將此設定改為 `True` 可讓終端使用者開啟或關閉 Wi-Fi，或連線到其他 Wi-Fi 網路。  |
| 顯示藍牙設定 | bool | FALSE | 將此設定改為 `True`，可讓終端使用者開啟或關閉藍牙，以及連線到其他具藍牙功能的裝置。   |

## <a name="enter-json-data"></a>輸入 JSON 資料

輸入 JSON 資料不僅可以進行 Managed Home Screen 的所有可用設定，還可進行**設定設計工具**中無法使用的設定。

![新增的 JSON 資料螢幕擷取畫面](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_03.png)

除了**設定設計工具**表格 (上表) 中列出的可用設定之外，下表提供了只能透過 JSON 資料來設定的設定索引碼。

|    設定索引碼    |    值類型    |    預設值    |    說明    |
|-------------------------------------------------|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    設定允許列出的應用程式    |    bundleArray    | <img alt="JSON - Example 1" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson01.png" width="300"> |    讓您可從裝置上已安裝應用程式當中，定義一組在主畫面上顯示的應用程式。 定義應用程式的方式是針對您想要顯示的應用程式輸入應用程式套件名稱，例如 com.android.settings 讓設定可在主畫面上存取。 您允許列於此區段的應用程式應已安裝於裝置上，才能在主畫面上顯示。    |
|    設定釘選的 Web 連結    |    bundleArray    | <img alt="JSON - Example 2" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson02.png" width="300"> |    讓您可在主畫面上，將網站釘選為快速啟動圖示。 您可以利用這項設定定義 URL，並將其新增到主畫面，讓終端使用者只要輕觸一下，即可在瀏覽器中啟動。    |
|    建立受控資料夾以為應用程式分組    |    bundleArray    | <img alt="JSON - Example 3" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson03.png" width="300"> |    讓您可以建立資料夾並為其命名，以及將應用程式分到這些資料夾中。 終端使用者無法移動資料夾、為資料夾重新命名，或移動資料夾內的應用程式。   資料夾會依建立的順序顯示，而資料夾內的應用程式會按字母排序。         注意：您要分到資料夾中的所有應用程式，都必須指派為裝置的必要項，而且必須新增到 Managed Home Screen。     |

以下是包含所有可用設定索引碼的範例 JSON 指令碼：

```json
{
    "kind": "androidenterprise#managedConfiguration",
    "productId": "com.microsoft.launcher.enterprise",
    "managedProperty": [
        {
            "key": "grid_size",
            "valueString": "Auto"
        },
        {
            "key": "keep_page_header",
            "valueBool": true
        },
        {
            "key": "keep_status_bar",
            "valueBool": true
        },
        {
            "key": "show_notification_badge",
            "valueBool": false
        },
        {
            "key": "lock_home_screen",
            "valueBool": true
        },
        {
            "key": "wallpaper",
            "valueString": "default"
        },
        {
            "key": "icon_size",
            "valueInteger": 2
        },
        {
            "key": "app_folder_icon",
            "valueInteger": 0
        },
        {
            "key": "gesture_on",
            "valueBool": false
        },
        {
            "key": "vertical_scrolling",
            "valueBool": false
        },
        {
            "key": "theme",
            "valueString": "Theme.Light.Blue"
        },
        {
            "key": "dock_enable",
            "valueBool": false
        },
        {
            "key": "screen_orientation",
            "valueInteger": 1
        },
        {
            "key": "feed_enable",
            "valueBool": false
        },
        {
            "key": "allow_overview_mode",
            "valueBool": false
        },
        {
            "key": "enable_telemetry",
            "valueBool": false
        },
        {
            "key": "applications",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "package",
                            "valueString": “app package name here”
                        }
                    ]
                }
            ]
        },
        {
            "key": "weblinks",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "link",
                            "valueString": “link here”
                        },
                        {
                            "key": "label",
                            "valueString": “weblink label here”
                        }
                    ]
                }
            ]
        },
        {
            "key": "search_bar",
            "valueBool": false
        },
        {
            "key": "hide_settings",
            "valueBool": false
        },
        {
            "key": "show_virtual_home",
            "valueBool": false
        },
        {
            "key": "virtual_home_type",
            "valueString": "swipe_up"
        },
        {
            "key": "show_virtual_status_bar",
            "valueBool": true
        },
        {
            "key": "exit_lock_task_mode_code",
            "valueString": ""
        },
        {
            "key": "show_wifi_setting",
            "valueBool": false
        },
        {
            "key": "show_bluetooth_setting",
            "valueBool": false
        },
        {
            "key": "managed_folders",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "folder_name",
                            "valueString": "Folder name here"
                        },
                        {
                            "key": "applications",
                            "valueBundleArray": [
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.emmx"
                                        }
                                    ]
                                },
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.bing"
                                        }
                                    ]
                                },
                                {
                                    "managedProperty": [
                                        {
                                            "key": "link",
                                            "valueString": "https://microsoft.com/"
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "folder_name",
                            "valueString": "Example folder name 2"
                        },
                        {
                            "key": "applications",
                            "valueBundleArray": [
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.office.word"
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                }
            ]
        }
    ]
}

```
## <a name="next-steps"></a>後續步驟

- 如需 Android Enterprise 專用裝置的詳細資訊，請參閱[設定 Android Enterprise 專用裝置的 Intune 註冊](android-kiosk-enroll.md)。
