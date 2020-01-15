---
title: 適用於 GCC High 與 DoD 環境的應用程式
titleSuffix: Microsoft Intune
description: 深入了解使用 Microsoft Intune 涉及 GCC High 與 DoD 環境的應用程式。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 29329f86-1aa5-434f-9925-8dc28bf35348
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5d37bf060f11be9e295a9ef2743fa0ba33844df7
ms.sourcegitcommit: 637375a390b6e34f9c4415c77b99fe2980bbf554
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75839342"
---
# <a name="deploying-apps-using-intune-on-the-gcc-high-and-dod-environments"></a>使用 Intune 在 GCC High 與 DoD 環境上部署應用程式 

租用戶系統管理員可以使用 Microsoft Intune 將應用程式散發給其工作人員。 工作人員是公司員工，即應用程式的使用者。 有許多種您可在 GCC High 或 DoD 環境上從 Intune 部署的應用程式。 如果系統管理員需要上傳及散發以 GCC High 或 DoD 為適用對象且由協力廠商建立的自訂 Windows 應用程式，或作為從[商務用 Microsoft Store](https://businessstore.microsoft.com/store) 下載的離線應用程式，系統管理員可以選擇將其作為[企業營運應用程式](apps-add.md#app-types-in-microsoft-intune)散發。  

> [!NOTE]
> 在商業環境中，租用戶系統管理員可以同步處理其商務用市集與 Intune，但對於 GCC High 與 DoD 環境，則不提供這項服務。 在此情況下，系統管理員必須直接上傳至 Intune 來部署應用程式。  

## <a name="add-line-of-business-apps-using-intune"></a>使用 Intune 新增企業營運應用程式 

若要使用 Intune 新增適用於 GCC High 或 DoD 環境的企業營運應用程式，您可以遵循 [Windows LOB 應用程式](lob-apps-windows.md)指示。 您可以選擇先從商務用 Microsoft Store 部署公司入口網站。 如果您選擇使用公司入口網站，則可以手動安裝並部署公司入口網站。 如需詳細資訊，請參閱[如何設定 Microsoft Intune 公司入口網站應用程式](company-portal-app.md)。 

## <a name="distribute-offline-apps-from-the-store-for-business-using-intune"></a>使用 Intune 散發商務用市集中的離線應用程式  

如果您需要從商務用 Microsoft Store 中[下載離線授權應用程式](https://docs.microsoft.com/microsoft-store/distribute-offline-apps#download-an-offline-licensed-app)，請遵循下列步驟來下載應用程式： 

1. 登入[商務用市集](https://businessstore.microsoft.com/)。
2. 選取 [管理]   > [設定]  。
3. 在 [購物體驗]  下方，將 [顯示離線應用程式]  設定為 [開啟]  。

購買應用程式時，若離線版本可供使用，您可以選擇將授權類型變更為離線。 取得應用程式之後，接著進行管理的方法是選取[商務用市集](https://businessstore.microsoft.com/)中的 [管理]   > [產品與服務]  。 此外，您還可以下載應用程式和其相依性。 然後，您可以使用 Intune 為使用者部署此下載的應用程式 (和其相依性)。  

## <a name="syncing-intune-to-the-store-for-business"></a>將 Intune 同步處理到商務用市集 

在商業 (非政府) 環境中，系統管理員可以將 Intune 同步處理到商務用 Microsoft Store。 這不是政府環境上的可用功能。 如需商業環境 Intune 與政府環境 Intune 之間差異的詳細資料，請參閱 [Enterprise Mobility + Security for US Government 服務描述](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-govt-service-description)。  

若要將 Intune 同步處理到商務用市集帳戶，請參閱[如何以 Microsoft Intune 管理購自商務用 Microsoft Store 的應用程式](windows-store-for-business.md)。  

## <a name="compliance"></a>合規性 

在評估這些服務的適當使用方式時，請檢閱應用程式的隱私權和合規性聲明，並將其與貴組織的合規性、安全性及隱私權需求比較。   

## <a name="next-steps"></a>後續步驟

若要深入了解如何部署及指派應用程式，請參閱[使用 Microsoft Intune 將應用程式指派給群組](apps-deploy.md)。

 
