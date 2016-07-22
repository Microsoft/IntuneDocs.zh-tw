---
title: "設定託管 Exchange 的 Microsoft Intune Exchange Connector | Microsoft Intune"
description: 
keywords: 
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 05fa5dc9-9bad-4557-987a-9b8ce4edebb0
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6951ccdb0e37489217ef939f0cbf6fc1133a6d3c
ms.openlocfilehash: 6cfc532cba2f53034c4c3ef0c2df3d6c1e6e7841


---

# 為 Exchange Online 設定 Intune Service to Service Connector

使用這項資訊可連線 Office 365 所裝載的 Microsoft Intune 和 Exchange Online 服務。

## Service to Service Connector 的需求
**Service to Service Connector** 僅支援託管 Exchange，且對內部部署基礎結構沒有任何需求。

|需求|詳細資訊|
|---------------|--------------------|
|已設定並執行託管 Exchange|[Exchange Online](https://technet.microsoft.com/library/jj200580.aspx) |
|行動裝置管理授權單位| [將行動裝置管理授權單位設定為 Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority)|
|Microsoft Exchange 版本|您必須有一項 Office 365 訂閱擁有 Exchange Server 2013 或更新版本的租用戶。 只要租用戶是 Exchange Server 2013 或更新版本，連接器便可在同一個環境中支援 Exchange Server 2010。|
|設定 Active Directory 同步處理。|使用 Intune Connector 之前，必須先[設定 Active Directory 同步處理](/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3)，如此本機使用者及安全性群組才能與您的 Azure Active Directory 進行同步處理。|

### Exchange Cmdlet 需求

您也必須建立 Intune Exchange Connector 所使用的 Exchange Online 使用者帳戶。 這個帳戶必須具有使用 Intune 管理主控台以及執行下列必要 Windows PowerShell Exchange Cmdlet 的權限：

 - Get-ActiveSyncOrganizationSettings、Set-ActiveSyncOrganizationSettings
 - Get-MobileDeviceMailboxPolicy、Set-MobileDeviceMailboxPolicy、New-MobileDeviceMailboxPolicy、Remove-MobileDeviceMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule、Set-ActiveSyncDeviceAccessRule、New-ActiveSyncDeviceAccessRule、Remove-ActiveSyncDeviceAccessRule
 - Get-MobileDeviceStatistics
 - Get-MobileDevice
 - Get-ActiveSyncDeviceClass

## 設定 Service to Service Connector

1. 使用具有[上方](#exchange-cmdlet-requirements) Cmdlet 之 Exchange 管理權限的使用者帳戶，開啟 [Microsoft Intune 管理主控台](http://manage.microsoft.com)。 Microsoft Intune 會使用目前登入使用者的電子郵件地址來設定連線。

2.  在工作區捷徑窗格中，選擇 [管理]，然後移至 [行動裝置管理]  >  [Microsoft Exchange]  >  [設定 Exchange 連線]。
![設定 Service to Service Connector 頁面](../media/intunesa5cservicetoserviceconnector.png)

3.  在 [設定 Exchange 連線] 頁面上，選擇 [設定 Service to Service Connector]。


Service to Service Connector 將會自動設定您的 Exchange 託管環境，並與之進行同步處理。

## 驗證您的 Exchange 連線

在您順利設定 Exchange Connector 之後，請在 Intune 管理主控台中選擇 [管理] 工作區，然後移至 [行動裝置管理]  >  [Microsoft Exchange]，並確認您提供的詳細資料是否出現在 [Exchange 連線資訊] 下方。

您也可以查看上次嘗試同步作業成功的時間和日期。



<!--HONumber=Jun16_HO4-->


