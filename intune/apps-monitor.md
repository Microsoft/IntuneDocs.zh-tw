---
title: "如何監視應用程式資訊和指派"
titlesuffix: Azure portal
description: "將應用程式指派給使用者或裝置之後，可以使用此資訊協助您監視其狀態。"
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 85ecc9729d7c03cb760c14bda0ca4d6321af548e
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-monitor-app-information-and-assignments-with-microsoft-intune"></a>如何使用 Microsoft Intune 監視應用程式資訊和指派

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune 提供了許多方式，可讓您監視您所管理之應用程式的內容，以及它們的指派狀態。

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  +  [Intune]。
3. 在 [Mobile Apps] 工作負載中，選擇 [管理] 群組中的 [應用程式]。
5. 在應用程式清單的刀鋒視窗中，選擇應用程式。 您會看到 [<應用程式名稱> 裝置安裝狀態] 刀鋒視窗。

## <a name="app-overview-blade"></a>應用程式概觀刀鋒視窗

您可以使用 <應用程式名稱> [Device install status] (裝置安裝狀態) 刀鋒視窗，檢閱您環境中的應用程式狀態的詳細資料。

### <a name="essentials"></a>Essentials

[程式集] 區段包含應用程式下列資訊：

 - **發佈者**  
應用程式的發行者。
 - **作業系統**  
應用程式的作業系統 (Windows、iOS、Android 等等)
 - **建立**  
此修訂建立的時間。
 - **已指派**  
如已指派應用程式則為 [是] 或 [否]。

### <a name="status"></a>狀態
每個圖形都會顯示下列狀態的計數：

 - **已安裝**  
安裝的應用程式數目。
 - **未安裝**  
未安裝的應用程式數目。
 - **安裝擱置中**  
正在安裝的應用程式數目。
 - **失敗**  
安裝失敗的數目。
 - **不明**  
狀態不明的應用程式數目。

### <a name="device-status"></a>裝置狀態

裝置狀態。 顯示裝置上應用程式安裝狀態的環圈圖。 按一下圖形以開啟裝置狀態的詳細清單。 詳細資料表包含下列資料行：

 - **裝置名稱**  
允許命名裝置之平台上的裝置名稱。 在其他平台上，Intune 會從其他屬性建立名稱。 此屬性不能提供所有裝置使用。
 - **使用者名稱**  
使用者的名稱。
 - **平台**  
裝置的作業系統 (Windows、iOS、Android 等等)
 - **版本**  
應用程式的版本號碼。 針對企業營運應用程式顯示的應用程式完整版本號碼。 完整的版本號碼可識別特定的應用程式版本。 此號碼會顯示為_版本_(_組建_)。 例如，2.2(2.2.17560800)
 - **狀態**  
應用程式的狀態。
 - **狀態詳細資料**  
狀態的詳細資料。
 - **上次簽入**  
裝置上次與 Intune 同步處理的日期。


### <a name="user-status"></a>使用者狀態

使用者狀態。 顯示使用者應用程式安裝狀態的環圈圖。 按一下圖形以開啟裝置狀態的詳細清單。 詳細資料表包含下列資料行：
 - **名稱**  
Azure AD 中的使用者名稱。
 - **使用者名稱**  
使用者的唯一名稱。
 - **安裝**  
使用者所用的應用程式安裝數目。
 - **失敗**  
使用者安裝失敗的數目。
 - **未安裝**  
使用者未安裝的應用程式數目。


## <a name="next-steps"></a>接下來的步驟

若要深入了解如何使用 Intune 資料，請參閱[使用 Intune 資料倉儲](reports-nav-create-intune-reports.md)。