---
title: "Intune 與 Microsoft 雲端服務的整合 | Microsoft Intune"
description: "Intune 與 Microsoft 雲端服務和產品，以及與其他 Microsoft 產品的整合"
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 49675811-08a3-408f-810b-89552ff404bd
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2a192c71b1b82f59b34ea614d09d895174f8112b
ms.openlocfilehash: 6523c731e8351b121cba46f6c5d2ef46db656c2c


---

# Intune 與 Microsoft 雲端服務和產品的整合

設定 [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] 之前，請檢閱本主題及[啟動 Microsoft Intune 前的須知事項](what-to-know-before-you-start-microsoft-intune.md)中列出的其他需求。
##與其他 Microsoft 雲端服務整合


[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 與其他 Microsoft 雲端服務共用通用的基礎。 當您使用同一個帳戶來訂閱多項雲端服務時，這些服務會使用相同的 Microsoft Azure AD 基礎結構，而且是 Azure AD 的租用戶。 Azure AD 為 Microsoft 雲端服務提供核心目錄和身分識別管理功能。

深入了解 TechNet 技術文件庫中的[管理 Azure AD](http://technet.microsoft.com/library/hh967611.aspx)。

## 與其他 Microsoft 產品整合
您可以將 [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] 用為獨立雲端服務或與其他產品整合的雲端服務。 目前只有 [!INCLUDE[cmshort](../includes/cmshort_md.md)] 才能直接與 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 整合。

將 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 與 [!INCLUDE[cmshort](../includes/cmshort_md.md)] 整合的決定是永久性的選擇，您需要從 [!INCLUDE[cmshort](../includes/cmshort_md.md)] 主控台而不是 [!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)] 中來設定行動裝置管理授權單位。 設定行動裝置管理授權單位後，您就無法變更或回復此設定。

當您搭配使用 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 與 [!INCLUDE[cmshort](../includes/cmshort_md.md)] 時，請不要使用 [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] 管理 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]，並改用 [!INCLUDE[cmshort](../includes/cmshort_md.md)] 主控台。 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 仍會在 Azure 中使用其雲端儲存體來裝載軟體，而您會將此軟體部署到使用 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 管理的裝置上。

如需詳細資訊，請參閱 [!INCLUDE[cm5short](../includes/cm5short_md.md)] SP1 文件中的[使用 Configuration Manager 和 Microsoft Intune 管理行動裝置](http://msdn.microsoft.com/library/2c6bd0e5-d436-41c8-bf38-30152d76be10)。

### 請參閱
[啟動 Microsoft Intune 前的須知事項](what-to-know-before-you-start-microsoft-intune.md)



<!--HONumber=Jul16_HO4-->


