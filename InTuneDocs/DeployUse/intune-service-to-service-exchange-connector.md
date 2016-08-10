---
title: "適用於 Exchange Online 的 Exchange Connector | Microsoft Intune"
description: "將 Intune 連接到 Office 365 Exchange 服務以支援 Exchange ActiveSync 行動裝置管理 (MDM)。"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 05fa5dc9-9bad-4557-987a-9b8ce4edebb0
ms.reviewer: muhosabe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: de3296e81c88b3ac04e3ba3f3d3ca222a59df7bd
ms.openlocfilehash: 1aabf820170483eacc83bec5e2b275e84dc07ffd


---

# 為 Exchange Online 設定 Intune Service to Service Connector

使用這項資訊可連線 Microsoft Intune 和 Exchange Online 或新 Exchange Online Dedicated 服務。 若要判斷您的 Exchange Online Dedicated 環境為**新**或**舊版**，請連絡您的帳戶管理員。 Intune 僅支援每個訂用帳戶一個任一種類的 Exchange Connector 連線。

## Service to Service Connector 的需求
**Service to Service Connector** 僅支援 Exchange Online 或新 Exchange Online Dedicated，且對內部部署基礎結構沒有任何需求。

|需求|詳細資訊|
|---------------|--------------------|
|已設定並執行 Exchange Online|[Exchange Online](https://technet.microsoft.com/library/jj200580.aspx) |
|行動裝置管理授權單位| [將行動裝置管理授權單位設定為 Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority)|
|Microsoft Exchange 版本|Exchange Online 或新 Exchange Online Dedicated 服務|
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


Service to Service Connector 將會自動設定您的 Exchange Online 或新 Exchange Online Dedicated 環境，並與之進行同步處理。

## 驗證您的 Exchange 連線

在您順利設定 Exchange Connector 之後，請在 [Microsoft Intune 管理主控台](http://manage.microsoft.com)中選擇 [系統管理]，然後移至 [行動裝置管理]  >  [Microsoft Exchange]，並確認您提供的詳細資料是否出現在 [Exchange 連線資訊] 下方。

您也可以查看上次嘗試同步作業成功的時間和日期。



<!--HONumber=Jul16_HO5-->


