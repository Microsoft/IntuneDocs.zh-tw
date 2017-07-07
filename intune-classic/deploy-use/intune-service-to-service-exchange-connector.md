---
title: "適用於 Exchange Online 的 Exchange Connector"
description: "將 Intune 連接到 Office 365 Exchange 服務以支援 Exchange ActiveSync 行動裝置管理 (MDM)。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 05fa5dc9-9bad-4557-987a-9b8ce4edebb0
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: c2f30e7827db280ba49fc49b6b7a00c9a8d9eade
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="configure-the-intune-service-to-service-connector-for-exchange-online"></a>設定 Intune 服務為 Exchange Online 的連接器提供服務

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

您可以使用此資訊連線到 Microsoft Intune 及 Exchange Online 或新版 Exchange Online Dedicated 服務。 若要判斷您的 Exchange Online Dedicated 環境為**新版**或**舊版**，請連絡您的帳戶管理員。 Intune 僅支援每個訂用帳戶一個任一種類的 Exchange Connector 連線。

## <a name="service-to-service-connector-requirements"></a>Service to Service Connector 的需求
**Service to Service Connector** 僅支援 Exchange Online 或新版 Exchange Online Dedicated，其對於內部部署基礎結構沒有任何需求。

|需求|詳細資訊|
|---------------|--------------------|
|已設定並執行 Exchange Online|[Exchange Online](https://technet.microsoft.com/library/jj200580.aspx) |
|行動裝置管理授權單位| [將行動裝置管理授權單位設定為 Microsoft Intune](prerequisites-for-enrollment.md#step-2-set-mdm-authority)|
|Microsoft Exchange 版本|Exchange Online 或新版 Exchange Online Dedicated 服務|/intune/users-permissions-add
|Active Directory 同步處理|使用 Intune Connector 之前，必須先[設定 Active Directory 同步處理](/intune/users-permissions-add)，如此本機使用者及安全性群組才能與您的 Azure Active Directory 進行同步處理。|

### <a name="exchange-cmdlet-requirements"></a>Exchange Cmdlet 需求

您也必須建立 Intune Exchange Connector 所使用的 Exchange Online 使用者帳戶。 此帳戶必須具備權限才能使用 Intune 管理主控台及執行下列必要的 Windows PowerShell Exchange Cmdlet：

 - Get-ActiveSyncOrganizationSettings、Set-ActiveSyncOrganizationSettings
 - Get-MobileDeviceMailboxPolicy、Set-MobileDeviceMailboxPolicy、New-MobileDeviceMailboxPolicy、Remove-MobileDeviceMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule、Set-ActiveSyncDeviceAccessRule、New-ActiveSyncDeviceAccessRule、Remove-ActiveSyncDeviceAccessRule
 - Get-MobileDeviceStatistics
 - Get-MobileDevice
 - Get-ActiveSyncDeviceClass

## <a name="set-up-the-service-to-service-connector"></a>設定 Service to Service Connector

1. 使用具備[前文所述](#exchange-cmdlet-requirements)之 Exchange 管理權限與 Cmdlet 權限的使用者帳戶開啟 [Microsoft Intune 管理主控台](https://manage.microsoft.com)。 Microsoft Intune 會使用目前登入之使用者的電子郵件地址來設定連線。

2.  在工作區捷徑窗格中，選擇 [管理] > [行動裝置管理]  >  [Microsoft Exchange]  >  [設定 Exchange 連線]。
![設定 Service to Service Connector 頁面](../media/intunesa5cservicetoserviceconnector.png)

3.  在 [設定 Exchange 連線] 頁面上，選擇 [設定 Service to Service Connector]。


Service to Service Connector 會自動設定及同步您的 Exchange Online 或新版 Exchange Online Dedicated 環境。

## <a name="validate-your-exchange-connection"></a>驗證您的 Exchange 連線

當您成功設定 Exchange Connector 之後，請前往 [Microsoft Intune 管理主控台](https://manage.microsoft.com)。 選擇 [管理] >  [行動裝置管理]  >  [Microsoft Exchange]。 接著在 [Exchange 連線資訊] 下方檢查您提供的詳細資料。

您也可以查看上次嘗試同步作業成功的時間和日期。
