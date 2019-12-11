---
title: 原則集合
titleSuffix: Microsoft Intune
description: 在 Microsoft Intune 中使用原則集合將管理物件集合組成群組。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e539f44fc9c9b4e7382368c0f3ad9f79bb1c98b1
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72585653"
---
# <a name="use-policy-sets-to-group-collections-of-management-objects"></a>使用原則集合將管理物件集合組成群組

原則集合可讓您建立現有管理實體的參考組合；這些實體必須以單一概念單元進行識別、設為目標及監視。 原則集合是應用程式、原則及您所建立之其他管理物件的可指派集合。 建立原則集合可讓您同時選取許多不同的物件，然後從單一位置指派它們。 隨著您組織的變更，您可以重新造訪原則集合來新增或移除其物件及指派。 您可以使用原則集合來以單一套件的形式關聯及指派現有物件，例如應用程式、原則及 VPN。 

> [!IMPORTANT]
> 如需與原則集合相關的已知問題清單，請參閱[原則集合已知問題](~/fundamentals/policy-sets.md#policy-sets-known-issues)。

原則集合不會取代現有的概念或物件。 您可以繼續指派個別物件，也能以原則集合之一部分的形式參考個別物件。 因此，對那些個別物件所做的任何變更都會反映在原則集合中。 

您可以使用原則集合來：

- 將需要一起指派的物件組成群組
- 在所有受控裝置上指派您組織的最小設定需求
- 將常用或相關的應用程式指派給所有使用者

您可以在原則集合中包含下列管理物件：
- 應用程式
- 應用程式設定原則
- 應用程式防護原則
- 裝置組態設定檔
- 裝置相容性原則
- 裝置類型限制
- Windows AutoPilot 部署設定檔
- 註冊狀態頁面

當您建立原則集合時，您會建立單一指派單位，並管理不同物件之間的關聯性。 對於位於原則集合外部的物件來說，原則集合將會是參考。 所包含物件中的任何變更也都會影響原則集合。 在您建立原則集合之後，您可以重複檢視及編輯其物件和指派。 

> [!NOTE]
> 原則集合支援 Windows、Android、macOS 及 iOS 設定，並可以跨平台指派。

## <a name="how-to-create-a-policy-set"></a>如何建立原則集合

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 在 [Intune]  刀鋒視窗上，選擇 [原則集合]   > [原則集合]   > [建立]  。
3. 在 [基本]  頁面上，新增下列值：
    - **原則集合名稱**：為此原則集合提供名稱。
    - **描述**：選擇性地為原則集合提供描述。
   <p>
   <img alt="Create policy set - Basics" src="~/fundamentals/media/policy-sets/policy-sets-01.png">

4. 按一下 [下一步:  應用程式管理]。<br>
   在 [應用程式管理]  頁面上，您可以選擇性地將[應用程式](~/apps/apps-add.md)、[應用程式設定原則](~/apps/app-configuration-policies-overview.md)，以及[應用程式防護原則](~/apps/app-protection-policy.md)新增至您的原則集合。 如需應用程式管理的詳細資訊，請參閱[什麼是 Microsoft Intune 應用程式管理？](~/apps/app-management.md)。 
5. 按一下 [下一步:  裝置管理]。<br>
   [裝置管理]  頁面可讓您將裝置管理物件新增至您的原則集合，例如[裝置組態設定檔](~/configuration/device-profiles.md)和[裝置合規性原則](~/protect/device-compliance-get-started.md)。 請務必包含所有相關聯的物件，例如其他原則、憑證及安全性基準設定檔。
6. 按一下 [下一步:  裝置註冊]。<br>
   [裝置註冊]  頁面可讓您將裝置註冊物件新增至您的原則集合，例如[裝置類型限制](~/enrollment/enrollment-restrictions-set.md)、[Windows Autopilot 部署設定檔](~/enrollment/enrollment-autopilot.md)，以及[註冊狀態頁面設定檔](~/enrollment/windows-enrollment-status.md)。
7. 按一下 [下一步:  指派]。<br>
   [指派]  頁面可讓您將原則集合指派給使用者和裝置。 請務必注意，不論裝置是否由 Intune 管理，您都可以將原則集合指派給該裝置。
8. 按一下 [下一步:  檢閱 + 建立]，以檢閱您針對設定檔輸入的值。
9. 完成後，請按一下 [建立]  以在 Intune 中建立原則集合。 

## <a name="policy-sets-known-issues"></a>原則集合已知問題

在 1910 中新推出的原則集合具有下列已知問題。

- 建立原則集合時，如果具範圍的系統管理員嘗試在沒有選取任何範圍標籤的情況下建立原則集合，在抵達 [檢閱 + 建立]  頁面時，驗證將會失敗，且系統會在狀態列上顯示錯誤。 系統管理員必須切換到程序中不同的頁面，然後再返回 [檢閱 + 建立]  頁面。 這將會啟用 [建立]  選項。  
 
- 原則集合目前支援下列應用程式類型：
    - iOS 市集應用程式
    - iOS 企業營運應用程式
    - 受控 iOS 企業營運應用程式
    - Android 市集應用程式
    - Android 企業營運應用程式
    - 受控 Android 企業營運應用程式
    - Office 365 專業增強版套件 (Windows 10)
    - 網頁連結
    - 內建 iOS 應用程式
    - 內建 Android 應用程式

- 不支援將原則設定指派從 [所有使用者]  設定為 [Autopilot 設定檔]  。

- 原則集合具有下列註冊限制和註冊狀態頁面 (ESP) 問題：
    - 限制和 ESP 不支援虛擬群組指派。
    - 限制和 ESP 不嚴格支援排除群組指派。 
    - 限制 ESP 會使用以優先順序為基礎的衝突解決。 如果限制和 ESP 同時也是較高優先順序的限制和 ESP 的目標，則該限制和 ESP 可能不會與原則集合的其餘承載一起套用至相同的使用者。
    - 無法將預設的限制和 ESP 新增至原則集合。

- 支援原則集合的 MAM 原則類型包含下列項目： 
    - 以 MAM WIP(Windows) MDM 為目標的受控應用程式保護 
    - 以 MAM iOS 為目標的受控應用程式保護
    - 以 MAM Android 為目標的受控應用程式保護
    - 以 MAM iOS 為目標的受控應用程式設定
    - 以 MAM Android 為目標的受控應用程式設定

- 不支援原則集合的 MAM 原則類型包含下列項目： 
    - 以 MAM WIP(Windows) 為目標的受控應用程式保護

- MAM 會針對下列原則類型將原則集合指派以直接指派的形式處理：
    - 以 MAM iOS 為目標的受控應用程式保護
    - 以 MAM Android 為目標的受控應用程式保護
    - 以 MAM iOS 為目標的受控應用程式設定
    - 以 MAM Android 為目標的受控應用程式設定

    如果將原則新增至已部署至群組的原則集合，該群組將會在工作負載中顯示為已直接指派，而非「透過原則集合指派」。 因此，MAM 並不會處理來自原則集合的群組指派刪除。

- MAM 針對任何原則類型皆不支援部署至 [所有使用者]  和 [所有裝置]  虛擬群組。

## <a name="next-steps"></a>後續步驟

- [在 Microsoft Intune 中註冊裝置](~/enrollment/index.yml)。