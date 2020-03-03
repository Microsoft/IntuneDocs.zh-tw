---
title: 引導式案例 - 部署適用於行動裝置的 Microsoft Edge
titleSuffix: Microsoft Intune
description: 了解從 Microsoft 365 裝置管理入口網站部署適用於行動裝置的 Microsoft Edge 的引導式案例。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9afb8f431ae301fe74f420c11205a7ed2637434b
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514620"
---
# <a name="guided-scenario---deploy-microsoft-edge-for-mobile"></a>引導式案例 - 部署適用於行動裝置的 Microsoft Edge 

透過遵循此[引導式案例](~/fundamentals/guided-scenarios-overview.md)，您可以將 Microsoft Edge 應用程式指派至組織中使用 iOS/iPadOS 或 Android 裝置的使用者。 指派此應用程式將能讓您的使用者順暢地使用其公司裝置瀏覽內容。 

Microsoft Edge 能讓使用者透過能協助他們合併、排列及管理工作內容的內建功能，來釐清網路上的雜亂內容。 在 Microsoft Edge 應用程式中使用其企業 Azure AD 帳戶來登入的 iOS/iPadOS 和 Android 裝置使用者，將會在瀏覽器中看見已預先載入的工作區 [我的最愛]  ，以及您定義的網站篩選。

> [!NOTE]
> 如果您已封鎖使用者註冊 iOS/iPadOS 或 Android 裝置的能力，則此案例將不會啟用註冊，且使用者必須自行安裝 Edge。
下列依據 Intune 原則啟用的 Microsoft Edge 企業功能包括： 

- **雙重識別** - 使用者可以新增工作帳戶與個人帳戶以進行瀏覽。 系統會完整區隔兩個身分識別，類似於 Office 365 和 Outlook 中的架構與體驗。 Intune 系統管理員可以在工作帳戶內，針對受保護的瀏覽體驗設定所需原則。 
- **Intune 應用程式保護原則整合** - 系統管理員現在可以將應用程式保護原則的目標設為 Microsoft Edge，藉此控制下列功能：剪下、複製及貼上、防止擷取螢幕畫面，以及確保使用者選取的連結只會在其他受控應用程式中開啟。
- **Azure 應用程式 Proxy 整合** - 系統管理員可以控制對 SaaS 應用程式和 Web 應用程式的存取，協助確保無論使用者是從公司網路連線或從網際網路連線，瀏覽器型應用程式都只會在安全的 Microsoft Edge 瀏覽器中執行。 
- **受控我的最愛和首頁捷徑** - 為了方便存取，系統管理員可以設定 URL，以在終端使用者進入公司內容中時，顯示在 [我的最愛] 底下。 系統管理員可以設定首頁捷徑，就會在公司的使用者於 Microsoft Edge 中開啟新的頁面或新的索引標籤時，顯示為主要捷徑。

## <a name="prerequisites"></a>先決條件

- [將 MDM 授權單位設定為 Intune](mdm-authority-set.md#set-mdm-authority-to-intune)：行動裝置管理 (MDM) 授權單位設定會決定您管理裝置的方式。 身為 IT 系統管理員，您必須在使用者可以註冊裝置以進行管理之前，設定 MDM 授權單位。
- 所需的 Intune 系統管理權限：
    - 受控應用程式讀取、建立、刪除及指派權限
    - 行動應用程式讀取、建立及指派權限
    - 原則會設定讀取、建立及指派權限
    - 組織讀取、更新權限

## <a name="step-1---introduction"></a>步驟 1 - 簡介

透過遵循**部署適用於行動裝置的 Microsoft Edge** 引導式案例，您將會針對所選取 iOS/iPadOS 和 Android 使用者群組設定 Microsoft Edge 的基本部署。 此部署將會實作**雙重身分識別**與**受控我的最愛和首頁捷徑**。 此外，由選取使用者註冊的裝置，將會由 Intune 自動安裝 Microsoft Edge 應用程式。 此自動化安裝將會在所有使用者驅動的註冊類型上發生，這包含： 
- 透過公司入口網站應用程式進行 iOS/iPadOS 註冊 
- 透過 Apple Business Manager 進行的 iOS/iPadOS 使用者親和性註冊 
- 透過公司入口網站應用程式的舊版 Android 註冊 

此引導式案例將會自動使 **MyApps** 出現在 Microsoft Edge [我的最愛] 之中，並以您針對 Intune 公司入口網站應用程式設定的相同商標來設定瀏覽器。 

### <a name="what-you-will-need-to-continue"></a>您需要什麼才能繼續
我們會詢問您有關您使用者所需的工作場所我的最愛，以及您針對網頁瀏覽所需的篩選。 在您繼續之前，請確定您已完成下列工作：

- 將使用者新增至 Azure AD 群組。 如需詳細資訊，請參閱[使用 Azure Active Directory 建立基本群組並新增成員](https://go.microsoft.com/fwlink/?linkid=2102458)。
- 在 Intune 中註冊 iOS/iPadOS 或 Android 裝置。 如需詳細資訊，請參閱[裝置註冊](https://go.microsoft.com/fwlink/?linkid=2102547)。
- 收集要新增至 Microsoft Edge 的工作場所我的最愛清單。
- 收集要在 Microsoft Edge 中強制執行的網站篩選清單。

## <a name="step-2---basics"></a>步驟 2 - 基本

在此步驟中，您必須為您的新 Microsoft Edge 原則輸入名稱和描述。 如果您稍後需要變更指派和設定，便可以參考這些原則。 引導式案例會為您的 iOS/iPadOS 裝置新增並指派 Microsoft Edge iOS/iPadOS 應用程式，也會為 Android 裝置新增並指派 Microsoft Edge Android 應用程式。 此外，此步驟將會為這些應用程式建立設定原則。

## <a name="step-3---configuration"></a>步驟 3 - 設定

在此步驟中，引導式案例將會設定 Microsoft Edge 以顯示透過 Intune 指派給使用者的所有其他應用程式，並共用與 Microsoft Intune 公司入口網站應用程式相同的商標。 您可以搭配 [首頁捷徑 URL]  、[受控書籤]  清單，以及[封鎖的 URL]  清單來進一步設定 Microsoft Edge。 在使用者於裝置上的 Microsoft Edge 中開啟新索引標籤時，[首頁捷徑 URL]  將會以搜尋列下方第一個圖示的形式向使用者顯示。 [受控書籤]  是供您的使用者在其工作內容中使用 Microsoft Edge 時可用的最愛 URL 清單。 [封鎖的 URL]  會指定針對您的使用者在其工作內容中封鎖的網站。 系統會允許所有其他網站。 

## <a name="step-4---assignments"></a>步驟 4 - 指派

在此步驟中，您可以選擇想要包含以針對工作設定 Microsoft Edge 行動版的使用者群組。 Microsoft Edge 也將會安裝在由這些使用者所註冊的所有 iOS/iPadOS 和 Android 裝置上。

## <a name="step-5---review--create"></a>步驟 5 - 檢閱 + 建立

最後的步驟可讓您檢閱您所設定之設定的摘要。 在您檢閱自己的選擇之後，請按一下 [建立]  以完成引導式案例。 

> [!NOTE]
> Edge 最多可能會需要 12 小時才能接收到該設定。 如需詳細資訊，請參閱 [Microsoft Intune 的應用程式設定原則](~/apps/app-configuration-policies-overview.md)。

> [!IMPORTANT]
> 引導式案例完成之後，它將會顯示摘要。 您稍後可以修改列於摘要中的資源，不過系統將不會儲存顯示這些資源的表格。

## <a name="next-steps"></a>後續步驟

- 設定 Intune 應用程式防護原則整合，來強化使用 Microsoft Edge 的安全性。 如需詳細資訊，請參閱 [Microsoft Edge 的應用程式保護原則](~/apps/manage-microsoft-edge.md#application-protection-policies-for-microsoft-edge)。
- 如果您有要包含的內部網路網站，請探索透過 Azure 應用程式 Proxy 整合來保護存取。 如需詳細資訊，請參閱[針對 Microsoft Edge 設定應用程式 Proxy 設定](~/apps/manage-microsoft-edge.md#configure-application-proxy-settings-for-microsoft-edge)。

