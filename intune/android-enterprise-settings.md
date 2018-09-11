---
title: Microsoft Intune 中的 Android kiosk 設定 - Azure | Microsoft Docs
description: 設定 Android 企業 kiosk 裝置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4e43ab0d088edc87e814ad2c4317d7b7336d34d5
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2018
ms.locfileid: "43312891"
---
# <a name="android-enterprise-kiosk-settings-in-intune"></a>Intune 中的 Android 企業 kiosk 設定

Android kiosk 設定檔支援下列組態設定。 建立設定檔時，這些設定會在您選擇 [設定檔類型] > [僅限裝置擁有者] > [裝置限制] 時顯示。 若要查看這些設定，請從 Android 企業裝置限制設定檔中選擇 [內容]，然後選擇 [設定]。

## <a name="general-settings"></a>一般設定

- **螢幕擷取**：選擇 [封鎖] 以防止使用者擷取裝置的螢幕。
- **相機**：選擇 [封鎖] 以停用裝置的相機。
- **預設權限原則**：此設定會定義執行階段權限要求的預設權限原則。 可能的值包括：
    - **裝置預設**：使用裝置的預設值。
    - **提示**：系統會提示使用者核准權限。
    - **自動授與**：自動授與權限。
    - **自動拒絕**：自動拒絕權限。
- **磁碟區變更**：選擇 [封鎖] 以防止使用者變更裝置的磁碟區。
- **抹除**：選擇 [封鎖] 以防止使用者抹除裝置。
- **安全開機**：選擇 [封鎖] 以防止使用者將裝置重新開機進入安全模式。
- **狀態列**：選擇 [封鎖] 以防止使用者存取狀態列，包括通知和快速設定。
- **Wi-Fi 設定變更**：選擇 [封鎖] 以防止使用者變更裝置擁有者所建立的 Wi-Fi 設定。 使用者可以建立自己的 Wi-Fi 設定。
- **Wi-Fi 存取點設定**：選擇 [封鎖] 以防止使用者建立或編輯任何 Wi-Fi 設定。
- **偵錯功能**：選擇 [允許] 可讓使用者使用偵錯功能。
- **麥克風調整**：選擇 [封鎖] 以防止使用者調整麥克風音量或將麥克風靜音。
- **抹除保護電子郵件**：選擇 [Google 帳戶電子郵件地址]，以定義抹除之後可以解除鎖定裝置的電子郵件地址 (以分號分開)。 若未指定電子郵件，任何人都可以在抹除之後解除鎖定裝置。
- **網路備案**：選擇 [啟用] 以開啟網路備案功能。 若在開機時無法進行網路連線，備案就會提示使用者暫時連線至網路，以便重新整理裝置原則。 套用原則之後，就會遺忘暫時性網路，且裝置會繼續開機。 若最後一個原則中沒有任何適當的網路，且裝置開機進入處於鎖定工作模式的應用程式，或使用者無法觸達裝置設定時，這可防止無法連線至網路。
- **允許從不明來源安裝**：選擇 [允許] 讓使用者從不明來源安裝。
- **系統更新**：選擇此選項以定義裝置如何處理無線更新：
    - **裝置預設**：使用裝置的預設值。
    - **自動**：自動安裝更新。
    - **延後**：更新會延後到較晚的日期。
    - **維護期間**：維護期間會提示使用者核准更新。

## <a name="kiosk-settings"></a>Kiosk 設定

- **kiosk 模式**：定義裝置只能執行單一應用程式，或是可以執行多個應用程式。 如需詳細資訊，請參閱[適用於 Android 裝置的 Kiosk 設定](android-kiosk-settings.md)。
    - **單一應用程式 kiosk**：使用者只能存取單一應用程式。
    - **多應用程式 kiosk**：使用者可以存取一組有限的應用程式。

## <a name="device-password-settings"></a>裝置密碼設定

- **Keyguard**：選擇 [停用] 以防止使用者在裝置上使用 Keyguard。
- **必要的密碼類型**：定義裝置所需的密碼類型。
- **密碼長度下限**：定義裝置所需的密碼長度下限。
- **登入失敗幾次後即抹除裝置**：定義抹除裝置前必須發生的失敗登入次數。

## <a name="power-settings"></a>電源設定

- **螢幕鎖定時間**：設定在裝置鎖定前所需的閒置時間量。
- **裝置充電時開啟螢幕**：選擇充電時哪些電源會導致裝置的螢幕開啟。

## <a name="users-and-accounts-settings"></a>使用者和帳戶設定

- **新增使用者**：選擇 [封鎖] 以防止使用者新增新的使用者。
- **移除使用者**：選擇 [封鎖] 以防止使用者移除使用者。
- **帳戶變更**：選擇 [封鎖] 以防止使用者修改帳戶。

## <a name="next-steps"></a>接下來的步驟
[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。



