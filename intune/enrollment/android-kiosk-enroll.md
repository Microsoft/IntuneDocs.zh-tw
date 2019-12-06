---
title: 針對 Android Enterprise 專用裝置設定 Intune 註冊
titleSuffix: Microsoft Intune
description: 了解如何在 Intune 中註冊 Android Enterprise 專用裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d4ff9126fec182d1e0d2f3eb75297ede8a632e2e
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390713"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-dedicated-devices"></a>設定 Android Enterprise 專用裝置的 Intune 註冊

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Android Enterprise 使用其專屬的裝置解決方案集合，支援公司所擁有、單次使用的 kiosk 形式裝置。 這類裝置用於單一用途，例如數位招牌、票證列印或庫存管理等等。 系統管理員會針對一組有限的應用程式和 Web 連結鎖定裝置使用。 它也會防止使用者新增其他應用程式，或在裝置上採取其他動作。

Intune 可協助您將應用程式和設定部署至 Android Enterprise 專用裝置。 如需 Android Enterprise 的相關特定詳細資訊，請參閱 [Android Enterprise 的需求](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012) \(英文\)。

您以這種方式管理的裝置不需要使用者帳戶即可在 Intune 中註冊，也不會與任何終端使用者建立關聯。 它們不適用於個人使用的應用程式，或對使用者特定帳戶資料 (例如 Outlook 或 Gmail) 有強烈需求的應用程式。

## <a name="device-requirements"></a>裝置需求

裝置必須符合這些需求，才能視為 Android Enterprise 專用裝置加以管理：

- Android OS 5.1 版和更新版本。
- 裝置必須執行具有 Google Mobile Services (GMS) 連線能力的 Android 發行版本。 裝置必須有可用的 GMS ，而且必須能夠連線至 GMS。

## <a name="set-up-android-enterprise-dedicated-device-management"></a>設定 Android Enterprise 專用裝置管理

若要設定 Android Enterprise 專用裝置管理，請遵循下列步驟進行：

1. 若要準備管理行動裝置，您必須[將行動裝置管理 (MDM) 授權單位設定為 **Microsoft Intune**](../fundamentals/mdm-authority-set.md) 以取得相關指示。 此項目只會設定一次，也就是第一次為行動裝置管理設定 Intune 之時。
2. [將您的 Intune 租用戶帳戶連線到受控 Google Play 帳戶](connect-intune-android-enterprise.md)。
3. [建立註冊設定檔](#create-an-enrollment-profile)
4. [建立裝置群組](#create-a-device-group)。
5. [註冊專用裝置](#enroll-the-dedicated-devices)。

### <a name="create-an-enrollment-profile"></a>建立註冊設定檔

> [!NOTE]
> 如果權杖已過期，與它相關聯的設定檔將不會顯示於 [裝置註冊]   > [Android 註冊]   > [公司擁有的專用裝置]  。 若要查看所有與作用中和非作用中權杖相關聯的設定檔，請按一下 [篩選]  ，然後勾選 [作用中] 與 [非作用中] 原則狀態的方塊。 

您必須建立註冊設定檔，才能註冊您的專用裝置。 建立設定檔時，它會為您提供註冊權杖 (隨機字串) 和 QR 代碼。 視 Android OS 和裝置的版本而定，您可以使用權杖或 QR 代碼來[註冊專用裝置](#enroll-the-dedicated-devices)。

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)，然後選擇 [裝置註冊]   > [Android 註冊]   > [公司擁有的專用裝置]  。
2. 選擇 [建立]  並填寫必要的欄位。
    - **名稱**：輸入將設定檔指派給動態裝置群組時，您要使用的名稱。
    - **權杖到期日**：權杖到期的日期。 Google 最多可強制執行 90 天。
3. 選擇 [建立]  以儲存該設定檔。

### <a name="create-a-device-group"></a>建立裝置群組

您可以將應用程式和原則的目標設為指派的裝置群組或動態裝置群組。 透過遵循下列步驟，即可設定動態 AAD 裝置群組，以自動填入使用特定註冊設定檔註冊的裝置：

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)，然後選擇 [群組]   > [所有群組]   > [新增群組]  。
2. 在 [群組]  刀鋒視窗中填寫必要的欄位，如下所示：
    - **群組類型**：安全性
    - **群組名稱**：輸入直覺式名稱 (例如 Factory 1 裝置)
    - **成員資格類型**：動態裝置
3. 選擇 [新增動態查詢]  。
4. 在 [動態成員資格規則]  刀鋒視窗中填寫欄位，如下所示：
    - **新增動態成員資格規則**：簡易規則
    - **新增裝置，其中**：enrollmentProfileName
    - 在中間方塊中，選擇 [等於]  。
    - 在最後一個欄位中，輸入您稍早建立的註冊設定檔名稱。
    如需動態成員資格規則的詳細資訊，請參閱 [AAD 中群組的動態成員資格規則](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership)。 
5. 選擇 [新增查詢]   > [建立]  。

### <a name="replace-or-remove-tokens"></a>取代或移除權杖

- **取代權杖**：您可以在權杖/QR 代碼接近到期日時，使用 [取代權杖] 產生新的權杖/QR 代碼。
- **撤銷權杖**：您可以立即使權杖/QR 代碼過期。 從此時開始，權杖/QR 代碼不再可用。 在下列情況下，您可以使用此選項：
  - 意外地與未經授權的合作對象共用權杖/QR 代碼
  - 完成所有註冊，而不再需要權杖/QR 代碼

取代或撤銷權杖/QR 代碼不會對已註冊的裝置產生任何影響。

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)，然後選擇 [裝置註冊]   > [Android 註冊]   > [公司擁有的專用裝置]  。
2. 選擇您想要使用的設定檔。
3. 選擇 [權杖]  。
4. 若要取代權杖，請選擇 [取代權杖]  。
5. 若要撤銷權杖，請選擇 [撤銷權杖]  。

## <a name="enroll-the-dedicated-devices"></a>註冊專用裝置

您現在可以[註冊您的專用裝置](android-dedicated-devices-fully-managed-enroll.md)。

> [!NOTE]
> **Microsoft Intune** 應用程式會在註冊專用裝置期間自動安裝。  進行註冊需要此應用程式，您無法將它解除安裝。 

## <a name="managing-apps-on-android-enterprise-dedicated-devices"></a>管理 Android Enterprise 專用裝置上的應用程式

只有指派類型[設定為 [必要]](../apps/apps-deploy.md#assign-an-app) 的應用程式，才能在 Android Enterprise 專用裝置中安裝。 應用程式會以和 Android Enterprise 工作設定檔裝置相同的方式，從受控 Google Play 商店安裝。

當應用程式開發人員將更新發佈至 Google Play 時，應用程式就會在受控裝置上自動更新。

若要從 Android Enterprise 專用裝置移除應用程式，可以執行下列其中一項：
- 刪除所需的應用程式部署。
- 建立應用程式的解除安裝部署。

## <a name="next-steps"></a>後續步驟
- [部署 Android 應用程式](../apps/apps-deploy.md)
- [新增 Android 設定原則](../configuration/device-profiles.md)
