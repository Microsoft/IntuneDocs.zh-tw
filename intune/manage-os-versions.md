---
title: 使用 Microsoft Intune 管理作業系統版本 | Microsoft Intune
description: 了解如何使用 Microsoft Intune 跨平台管理作業系統版本。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 361ef17b-1ee0-4879-b7b1-d678b0787f5a
search.appverid: MET150
ms.openlocfilehash: 27a581a72c20c940a04a791ef9e63a2dc8bf5b24
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53816985"
---
# <a name="manage-operating-system-versions-with-intune"></a>使用 Intune 管理作業系統版本
在現代化行動和桌面平台上，主要更新、修補程式以及新版本的發行速度很快。 您有控制方法可以完全管理 Windows 上的更新和修補程式，但像是 iOS 和 Android 等其他平台則需要終端使用者參與此程序。  Microsoft Intune 具有可協助在不同平台之間組織作業系統版本管理結構的功能。

Intune 可協助您解決這些常見的案例： 
- 判斷使用者裝置上有哪些作業系統版本
- 控制對裝置上組織資料的存取權，同時驗證新的作業系統版本
- 鼓勵/要求終端使用者升級至您的組織所核准的最新作業系統版本
- 管理整個組織推出到新的作業系統版本
  
## <a name="operating-system-version-control-using-intune-mobile-device-management-mdm-enrollment-restrictions"></a>使用 Intune 行動裝置管理 (MDM) 註冊限制的作業系統版本控制
Intune MDM 註冊限制可讓您定義用戶端裝置需求，然後才允許裝置註冊。 目標是要求您的終端使用者只註冊符合規範的裝置，然後才能存取組織資源。 裝置需求包括支援平台的最低和最高允許作業系統版本。
 
![平台設定限制刀鋒視窗](./media/os-version-platform-configurations.png) 
 
### <a name="in-practice"></a>在實務上
組織使用裝置類型限制，藉由使用下列設定來控制組織資源的存取權： 
1. 使用最低作業系統版本，來讓使用者維持在組織中的最新且支援的平台上。 
2. 將最高作業系統保留為未指定 (無限制)，或將它設定為組織中的最後一個驗證版本，以允許提供時間進行新作業系統版本的內部測試。

如需詳細資料，請參閱[設定裝置類型限制](https://docs.microsoft.com/intune/enrollment-restrictions-set#set-device-type-restrictions)。
 
## <a name="operating-system-version-reporting-and-compliance-with-intune-mdm-device-compliance-policies"></a>作業系統版本報告和對 Intune MDM 裝置合規性原則的合規性
Intune MDM 裝置合規性原則提供您下列工具： 
- 指定合規性規則
- 透過報告檢視合規性狀態
- 透過裝置隔離和條件式存取處理不合規性

如同註冊限制，裝置合規性原則會包含最低和最高作業系統版本。 原則也有合規性時間表，提供寬限期讓使用者符合規範。 裝置合規性原則會讓您的已註冊終端使用者裝置保持符合組織原則。

![裝置合規性 - 不符合規範之裝置的動作](./media/os-version-actions-noncompliance.png) 

### <a name="in-practice"></a>在實務上
組織使用裝置合規性原則的案例與註冊限制相同。 這些原則會讓使用者維持在組織中的最新且已驗證的作業系統版本。 當終端使用者裝置不符合規範時，可以透過條件式存取封鎖對組織資源的存取權，直到終端使用者在組織的受支援作業系統範圍內。 終端使用者會收到通知其不符合規範，並提供他們重新取得存取權的步驟。   

如需詳細資料，請參閱[開始使用裝置合規性](https://docs.microsoft.com/intune/device-compliance-get-started)。
 
## <a name="operating-system-version-controls-using-intune-app-protection-policies"></a>使用 Intune 應用程式保護原則的作業系統版本控制    
Intune 應用程式保護原則與行動應用程式管理 (MAM) 存取設定，可讓您指定在應用程式層的最低作業系統版本。 這可讓您通知和建議 (或要求) 您的終端使用者將其作業系統更新為指定的最低版本。
 
您有兩個不同的選項： 
- **警告** - 警告會在下列情況通知終端使用者應該升級：如果其開啟的應用程式具有應用程式防護原則或 MAM 存取設定，而他們的裝置作業系統版本低於指定的版本。 會針對應用程式和組織資料允許存取。
  ![[Android 更新警告] 對話方塊影像](./media/os-version-update-warning.png) 

- **封鎖** - 封鎖會在下列情況通知終端使用者必須升級：如果其開啟的應用程式具有應用程式防護原則或 MAM 存取設定，而他們的裝置作業系統版本低於指定的版本。 不會針對應用程式和組織資料允許存取。
  ![[已封鎖應用程式存取] 對話方塊影像](./media/os-version-access-blocked.png)

### <a name="in-practice"></a>在實務上
組織現在會在應用程式開啟或繼續時使用應用程式保護原則設定，作為教育終端使用者需要保持其應用程式為最新的方式。 一個範例設定是，終端使用者會在目前版本減一時收到警告，並在目前版本減二時遭到封鎖。
 
如需詳細資料，請參閱[如何建立及指派應用程式保護原則](https://docs.microsoft.com/intune/app-protection-policies)。

## <a name="managing-a-new-operating-system-version-rollout"></a>管理新的作業系統版本推出
您可以使用本文中所述的 Intune 功能，協助您在您定義的時間表內，讓組織移到較新的作業系統版本。 下列步驟提供範例部署模型，在七天內將您的使用者從作業系統 v1 移到作業系統 v2。
- **步驟 1**：使用註冊限制，要求作業系統 v2 作為註冊裝置的最低版本。 這可確保新的終端使用者裝置在註冊時即符合規範。
- **步驟 2a**：使用 Intune 應用程式防護原則在應用程式開啟或繼續時，警告使用者需要作業系統 v2。
- **步驟 2b**： 使用裝置合規性原則，要求作業系統 v2 作為裝置要符合規範時的最低版本。 針對不相容使用 [動作]，以允許七天的寬限期，並傳送電子郵件通知給終端使用者，告知您的時間表和要求。
  -  這些原則會透過電子郵件、Intune 公司入口網站，以及已啟用應用程式保護原則的應用程式開啟時通知終端使用者，需要更新現有的裝置。
  - 您可以執行合規性報告，以識別不符合規範的使用者。 
- **步驟 3a**：使用 Intune 應用程式防護原則，當應用程式開啟或繼續時，如果裝置不在執行作業系統 v2 即封鎖使用者。
- **步驟 3b**：使用裝置合規性原則，要求作業系統 v2 作為裝置要符合規範時的最低版本。
  - 這些原則會要求裝置更新，以便它們能繼續存取組織的資料。 搭配裝置條件式存取使用時，受保護的服務會遭到封鎖。 已啟用應用程式保護原則的應用程式，會在開啟時或存取組織資料時遭到封鎖。

## <a name="next-steps"></a>後續步驟
使用下列資源來管理組織中的作業系統版本： 

- [設定裝置類型限制](https://docs.microsoft.com/intune/enrollment-restrictions-set#set-device-type-restrictions)
- [開始使用裝置合規性](https://docs.microsoft.com/intune/device-compliance-get-started)
- [如何建立及部署應用程式保護原則](https://docs.microsoft.com/intune/app-protection-policies)
