---
title: 適用於 Exchange Online 的 Intune Exchange Connector
titleSuffix: ''
description: 將 Intune 連接到 Office 365 Exchange 服務以支援 Exchange ActiveSync 行動裝置管理 (MDM)。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 318bde24e42bfdf9bbcf15d83f42405fc06f7901
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184202"
---
# <a name="configure-the-exchange-service-connector-for-intune-and-exchange-online"></a>設定 Intune 和 Exchange Online 的 Exchange 服務連接器
本文將為您說明如何將 Microsoft Intune 服務連線到 Exchange Online 或新版 Exchange Online Dedicated 服務。 若要判斷您的 Exchange Online Dedicated 環境為**新版**或**舊版**，請連絡您的帳戶管理員。

您可以使用 [服務對服務連接器]，從單一管理主控台管理 Exchange ActiveSync (EAS) 和 Intune 受控裝置。  啟用 Exchange Online 的條件式存取時不需要連接器。

## <a name="service-to-service-connector-requirements"></a>Service to Service Connector 的需求
**Service to Service Connector** 僅支援 Exchange Online 或新版 Exchange Online Dedicated，其對於內部部署基礎結構沒有任何需求。 


|              需求               |                                                                                                            詳細資訊                                                                                                            |
|----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 已設定並執行 Exchange Online |                                                                                 [Exchange Online](https://technet.microsoft.com/library/jj200580.aspx)                                                                                 |
|   行動裝置管理授權單位   |                                                       [將行動裝置管理授權單位設定為 Microsoft Intune](mdm-authority-set.md)                                                       |
|       Microsoft Exchange 版本       |                                                                                      Exchange Online 或新版 Exchange Online Dedicated 服務                                                                                      |
|    Active Directory 同步    | 使用 Intune Connector 之前，必須先[設定 Active Directory 同步處理](/intune/users-add)，如此本機使用者及安全性群組才能與您的 Azure Active Directory 進行同步處理。 |

### <a name="exchange-cmdlet-requirements"></a>Exchange Cmdlet 需求

您也必須建立 Intune Exchange 服務連接器所使用的 Exchange Online 使用者帳戶。 帳戶必須具有執行下列必要 Windows PowerShell Exchange Cmdlet 的權限：

 - Get-ActiveSyncOrganizationSettings、Set-ActiveSyncOrganizationSettings
 - Get-MobileDeviceMailboxPolicy、Set-MobileDeviceMailboxPolicy、New-MobileDeviceMailboxPolicy、Remove-MobileDeviceMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule、Set-ActiveSyncDeviceAccessRule、New-ActiveSyncDeviceAccessRule、Remove-ActiveSyncDeviceAccessRule
 - Get-MobileDeviceStatistics
 - Get-MobileDevice
 - Get-ActiveSyncDeviceClass

## <a name="set-up-the-service-to-service-connector"></a>設定 Service to Service Connector

1. 使用具備[前文所述](#exchange-cmdlet-requirements) Exchange 管理權限、Cmdlet 權限、有效 Intune 授權與全域系統管理員角色的使用者帳戶來登入 [Azure 入口網站](http://portal.azure.com)。 Microsoft Intune 會使用目前登入之使用者的電子郵件地址來設定連線。

2. 選擇左功能表中的 [All services] (所有服務)，然後在文字方塊篩選中鍵入 **Intune**。

3. 選擇 **Intune** 以開啟 Microsoft Intune 儀表板。 選擇 [條件式存取]，然後在 [設定] 下選擇 [Exchange 服務連接器]。

4.  在 [條件式存取 - Exchange 服務連接器] 頁面上，選擇 [設定 Service to Service Connector]。 
   
     ![顯示選取 [設定 Service to Service Connector] 連結的影像](media/exchange_service_connector.png)

Service to Service Connector 會自動設定及同步您的 Exchange Online 或新版 Exchange Online Dedicated 環境。

## <a name="validate-your-exchange-connection"></a>驗證您的 Exchange 連線

在您順利設定 Exchange Service to Service Connector 後，請驗證 [條件式存取 - Exchange 服務連接器] 頁面上的 Exchange Connector 伺服器資訊。

您也可以查看上次嘗試同步作業成功的**連線狀態**與時間和日期。

 