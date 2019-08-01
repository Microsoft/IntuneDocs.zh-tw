---
title: 在 Microsoft Intune 中使用 Windows 更新的更新合規性報表
titleSuffix: Microsoft Intune
description: 若要檢視使用 Intune 所部署 Windows 更新的報表資料，請使用 OMS 更新合規性。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 09f3cafc16d8a08885731aa244a089367c6c0933
ms.sourcegitcommit: c715c93bb242f4fe44bbdf2fd585909854ed72b6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68660399"
---
# <a name="intune-compliance-reports-for-updates"></a>更新的 Intune 合規性報表
當您使用 Intune 將 Windows 更新部署到 Windows 10 裝置時，請檢視更新合規性的詳細資料，做法是使用 Intune 或稱為「更新合規性」  的免費解決方案，該解決方案是 Microsoft Operations Management Suite (OMS) 的一部分。

## <a name="use-intune"></a>使用 Intune
若要針對您已設定之 Windows 10 更新通道的部署狀態檢閱其原則報表： 
1. 登入 [Azure 入口網站](https://portal.azure.com/)。
2. 選擇 [所有服務]  ，篩選 [Intune]  ，然後選取 [Microsoft Intune]  。
3. 選取 [軟體更新]   > [概觀]  。 您可以看到所指派任何更新通道的狀態一般資訊。
4. 請開啟下列其中一個報表：  

   **針對所有部署通道**：
   1. 在 [軟體更新] 上   > [Windows 10 更新通道] 
   2. 在 [監視]  區段，選擇 [依更新通道別部署狀態]  。  

   **針對特定部署通道**：  

   1. 在 [軟體更新]   > [Windows 10 更新通道]  中，選擇要檢閱的部署通道。  
   2. 在 [監視]  區段中，從下列報表選擇，以檢視更新通道的更多詳細資訊：  
      - **裝置狀態**  
      - **使用者狀態**  

## <a name="use-update-compliance"></a>使用更新合規性
您可以使用[更新合規性](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor)這個 Windows Analytics 解決方案來監視 Windows 10 更新的首度發行。 更新合規性是透過 Azure 入口網站提供，並可免費用於符合其[先決條件](https://docs.microsoft.com/windows/deployment/update/update-compliance-get-started#update-compliance-prerequisites)的裝置。  

當您使用此解決方案時，可將商業識別碼部署至任何您以 Intune 管理、且要報告更新合規性的 Windows 10 裝置。  

在 Intune 主控台中，您可使用自訂原則的 OMA-URI 設定來設定商業識別碼。 如需詳細資訊，請參閱 [Microsoft Intune 中 Windows 10 裝置的 Intune 原則設定](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune)。  

用於設定商業識別碼的 OMA-URI (區分大小寫) 路徑為： *./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID*  

例如，您可以在 [新增或編輯 OMA-URI 設定]  中使用下列值：
- **設定名稱**：Windows Analytics 商業識別碼
- **設定描述**：設定 Windows Analytics 解決方案的商業識別碼
- **OMA-URI** (區分大小寫)： *./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID*
- **資料類型**：字串
- **值**：\<使用 OMS 工作區中 [Windows 遙測] 索引標籤上顯示的 GUID>
 
> [!NOTE]  
> 如需有關 MS DM 伺服器的詳細資訊，請參閱 [DMClient 設定服務提供者 (CSP)]( https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp)。

## <a name="next-steps"></a>後續步驟
[管理 Intune 中的軟體更新](windows-update-for-business-configure.md)

