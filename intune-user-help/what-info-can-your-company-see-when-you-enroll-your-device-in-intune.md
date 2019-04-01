---
title: 當您註冊您的裝置時，貴公司會看到什麼內容？
description: 說明 IT 在您受控裝置上可以看到及不能看到的內容。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 12655728-a1af-4d89-97bc-925fe36c0dc4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.collection: M365-identity-device-management
ms.openlocfilehash: 91ea3aab5cd04624bfa036615b8d7710573bcae1
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "55846973"
---
# <a name="what-information-can-my-organization-see-when-i-enroll-my-device"></a>當我註冊裝置時，我的組織可以看到哪些資訊？

當您向 Microsoft Intune 註冊裝置時，組織不會看到您的個人資訊。 當您註冊裝置時，會授與組織檢視裝置上特定資訊的權限，例如裝置型號和序號。 組織會使用這項資訊來協助保護裝置上的公司資料。

**組織絕對不會看到的資訊：**

- 電話和 Web 瀏覽歷程記錄
- 電子郵件和簡訊
- 連絡人
- 行事曆
-   密碼
- 圖片，包括相片應用程式或手機相簿的內容
- 檔案

**組織一律會看到的資訊：**

- 裝置型號，例如 Google Pixel
- 裝置製造商，例如 Microsoft
- 作業系統和版本，例如 iOS 12.0.1
- 應用程式名稱，例如 Microsoft Word：在個人裝置上，組織只能看到您的受控應用程式清查。 在公司擁有的裝置上，組織可以看到所有的應用程式清查。
- 裝置擁有者
- 裝置名稱
- 裝置序號
- IMEI

**組織可能會看到的資訊：**

-  電話號碼：如果是**公司**所擁有的裝置，組織能看到完整的電話號碼。 如果是**個人**所擁有的裝置，組織便只能看到電話號碼的最後四個數字。 開啟裝置的 [裝置詳細資料] 頁面，便可查看每個裝置的 [擁有權類型]。
- 裝置儲存空間：如果您無法安裝必要的應用程式，您的組織可以查看裝置儲存空間，以確定空間是否不足。  
-  組織：組織一律無法看到裝置的位置，除非您需要復原某個已遺失的受監督 iOS 裝置。 請瀏覽 [Apple iOS 文件](https://go.microsoft.com/fwlink/?linkid=853816)，以深入了解受監督的裝置。  
- 應用程式清查：如果您的組織使用 Mobile Threat Defense，其將能夠檢視您 iOS 裝置上應用程式的相關詳細資料。 深入了解 [Mobile Threat Defense](you-are-prompted-to-install-mtd-ios.md)。
- 網路資訊：有關 Android 裝置網路連線的一些資訊，可能可以提供給您組織的支援人員。 例如，如果您的組織要求裝置保留在某個建築物內，則您的裝置會識別網路連線位置。 
