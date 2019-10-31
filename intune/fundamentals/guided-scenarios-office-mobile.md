---
title: 引導式案例 - 保護 Microsoft Office 行動應用程式
titleSuffix: Microsoft Intune
description: 了解從 Microsoft 365 裝置管理入口網站部署安全的 Microsoft Office 行動應用程式的引導式案例。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bd02e2b7f9582308109d1e6986d7e6a8014e5af7
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585705"
---
# <a name="guided-scenario---secure-microsoft-office-mobile-apps"></a>引導式案例 - 保護 Microsoft Office 行動應用程式 

藉由在裝置管理入口網站中遵循此引導式案例，您可以在 iOS 和 Android 裝置上啟用基本的 Intune 應用程式保護。

您啟用的應用程式保護將會強制執行下列動作： 
- 加密工作檔案。
- 需要 PIN 才能存取工作檔案。
- 要求在五次失敗嘗試之後重設 PIN。
- 封鎖工作檔案，使其無法在 iTunes、iCloud 或 Android 備份服務中進行備份。  
- 要求僅將工作檔案儲存到 OneDrive 或 SharePoint。
- 防止受保護的應用程式已進行越獄或 Root 的裝置上載入工作檔案。
- 如果裝置離線達 720 分鐘，則封鎖對工作檔案的存取。
- 如果裝置離線 90 天，則移除工作檔案。 

## <a name="background"></a>背景

Office 行動應用程式以及適用於行動裝置的 Microsoft Edge 都支援雙重身分識別。 雙重身分識別可讓應用程式分開管理工作檔案與個人檔案。 

![公司資料與個人資料的影像](./media/guided-scenarios-office-mobile/guided-scenarios-office-mobile-01.png)

[Intune 應用程式保護原則](~/apps/app-protection-policy.md)可協助保護您已在 Intune 中註冊之裝置上的工作檔案。 您也可以在未向 Intune 註冊管理之員工擁有的裝置上，使用應用程式保護原則。 在此情況下，即使您的公司未管理裝置，仍然需要確定工作檔案和資源受到保護。

您可以使用應用程式保護原則來防止使用者將工作檔案儲存在未受保護的位置。 您也可以限制將資料移到其他未受應用程式保護原則保護的應用程式。 應用程式保護原則設定包括︰
- 資料重新配置原則，如 [不可進行另存新檔] 和 [限制剪下、複製及貼上]。
- 存取原則設定，需要簡單的 PIN 碼才能存取，並封鎖受管理的應用程式在已進行越獄或 Root 破解的裝置上執行。

應用程式型條件式存取和用戶端應用程式管理會新增一個安全性層級，方法是確定只有支援 Intune 應用程式保護原則的用戶端應用程式才能存取 Exchange Online 和其他 Office 365 服務。

當您只允許 Microsoft Outlook 應用程式存取 Exchange Online 時，可以封鎖 iOS 和 Android 上內建的郵件應用程式。 此外，您可以封鎖沒有套用 Intune 應用程式保護原則的應用程式，阻擋它們存取 SharePoint Online。

在這個範例中，系統管理員已經將應用程式保護原則套用至 Outlook 應用程式，接著套用條件式存取規則，將 Outlook 應用程式新增到可在存取公司電子郵件時使用之應用程式的核准清單中。

![Outlook 應用程式條件式存取程序流程](./media/guided-scenarios-office-mobile/guided-scenarios-office-mobile-02.png)

## <a name="prerequisites"></a>必要條件

您將需要下列 Intune 系統管理員權限：

   - 受控應用程式讀取、建立、刪除及指派權限
   - 原則會設定讀取、建立及指派權限
   - 組織讀取權限

## <a name="step-1---introduction"></a>步驟 1 - 簡介

藉由遵循 **Intune 應用程式保護**引導式案例，您將可避免在組織外部共用或洩漏資料。 

指派的 iOS 和 Android 使用者必須在每次開啟 Office 應用程式時輸入 PIN。 在 5 次失敗的 PIN 嘗試之後，使用者必須重設其 PIN。 如果您已經需要裝置 PIN，使用者將不會受到影響。

### <a name="what-you-will-need-to-continue"></a>您需要什麼才能繼續

我們會詢問您的使用者所需的應用程式，以及存取它們所需的條件。 請確定您有下列資訊：
- 已核准供公司使用的 Office 應用程式清單。
- 在非受控裝置上啟動已核准應用程式的任何 PIN 需求。

## <a name="step-2---basics"></a>步驟 2 - 基本

在此步驟中，您必須為新的應用程式保護原則輸入 [前置詞]  和 [描述]  。 當您新增 [前置詞]  時，將會更新與引導式案例所建立之資源相關的詳細資料。 如果您需要變更指派和設定，這些詳細資料可讓您稍後輕鬆地找到您的原則。 

> [!TIP]
> 請考慮記下將要建立的資源，以便您稍後可以參考它們。

## <a name="step-3---apps"></a>步驟 3 - 應用程式

為了協助您開始使用，此引導式案例會預先選取下列行動應用程式，以在 iOS 和 Android 裝置上進行保護：
- Microsoft Excel 
- Microsoft Word 
- Microsoft Teams 
- Microsoft Edge 
- Microsoft PowerPoint 
- Microsoft Outlook 
- Microsoft OneDrive 

此引導式案例也會將這些應用程式設定為在 Microsoft Edge 中開啟網頁連結，以確保工作網站會在受保護的瀏覽器中開啟。

修改您想要保護的原則受控應用程式清單。 新增或移除此清單中的應用程式。 

選取應用程式之後，按一下 [下一步]  。

## <a name="step-4---configuration"></a>步驟 4 - 設定

在此步驟中，您必須設定在這些應用程式中存取及共用公司檔案和電子郵件的需求。 根據預設，使用者可以將資料儲存到您組織的 OneDrive 和 SharePoint 帳戶。

| 設定 | 說明 | 預設值 |
|---------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| PIN 類型 | 數字 PIN 全部由數字組成。 密碼是由英數字元和特殊字元所組成。  在 iOS/iPadOS 上，若要設定「密碼」類型，應用程式需要有 Intune SDK 版本 7.1.12 或更新版本。 數值類型沒有 Intune SDK 版本限制。 | 數字 |
| 選取 PIN 長度下限 | 指定 PIN 序列的最小位數。 | 6 |
| 重新檢查存取需求前的經過時間 (非使用中狀態分鐘數) | 應用程式啟動後，如果原則受控應用程式非使用中的時間超過指定的閒置分鐘數，應用程式會提示您重新檢查存取要求 (亦即， PIN，條件式啟動設定)。 | 30 |
| 列印組織資料 | 如果遭到封鎖，應用程式就無法列印受保護的資料。 | 封鎖 |
| 在非受控瀏覽器中開啟原則受控應用程式連結 | 如果遭到封鎖，原則管理的應用程式連結就必須開啟受控瀏覽器。 | 封鎖 |
| 將資料複製到非受控應用程式 | 如果遭到封鎖，受控資料會保留在受控應用程式中。 | Allow |

## <a name="step-5---assignments"></a>步驟 5 - 指派

在此步驟中，您可以選擇您想要包含的使用者群組，以確保他們能夠存取您的公司資料。 應用程式保護會指派給使用者，而不是裝置，因此不論使用的裝置和其註冊狀態為何，您的公司資料都將會是安全的。

未指派應用程式保護原則和條件式存取設定的使用者，將能夠將其公司設定檔中的資料儲存至個人應用程式，以及其行動裝置上非受控的本機儲存體。 他們也可以使用個人應用程式連線至公司資料服務，例如 Microsoft Exchange。

## <a name="step-6---review--create"></a>步驟 6 - 檢閱 + 建立

最後的步驟可讓您檢閱您所設定之設定的摘要。 在您檢閱自己的選擇之後，請按一下 [建立]  以完成引導式案例。 引導式案例完成之後，會顯示資源表格。 您稍後可以編輯這些資源，不過，一旦離開摘要檢視，將不會儲存該表格。

> [!IMPORTANT]
> 引導式案例完成之後，它將會顯示摘要。 您稍後可以修改列於摘要中的資源，不過系統將不會儲存顯示這些資源的表格。
## <a name="next-steps"></a>後續步驟

- 將以應用程式為基礎的條件式存取原則指派給使用者，以保護雲端服務不將工作檔案傳送到未受保護的應用程式，藉此增強工作檔案的安全性。 如需詳細資訊，請參閱[搭配 Intune 設定以應用程式為基礎的條件式存取原則](~/protect/app-based-conditional-access-intune-create.md)。

