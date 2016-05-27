---
# required metadata

title: 您的電腦已註冊 | Microsoft Intune
description:
keywords:
author: staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8d3a40f5-99e9-48dc-9706-f7a3a23e5704

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# 您的電腦已註冊
因為您已執行 Intune 用戶端軟體的安裝程式，所以會看到此頁面。 不過，您的電腦上已安裝軟體，因此無法繼續安裝程式。

其原因是：

-   之前已安裝用戶端軟體，並再次執行安裝程式。

-   IT 系統管理員淘汰 Intune 中的裝置之後，已在電腦上執行安裝程式。 淘汰您的裝置之後，可能需要數小時，才能從電腦中移除用戶端軟體。

-   安裝程式偵測到最近安裝或移除用戶端軟體失敗。

## 安裝在電腦上的安裝程式
安裝程式會安裝 Intune 用戶端。 安裝程式完成之後，用戶端軟體會在背景繼續執行，以設定電腦與 Intune 搭配使用。 此程序可能需要一些時間才能完成，並且包含：

-   使用 Intune 註冊電腦

-   提交電腦硬體和已安裝軟體的清查

-   設定 Intune 原則 (包括安裝 Endpoint Protection (如果已設定))

-   安裝 Intune Center

安裝 Intune 中心之後，就可以使用它來存取可將電腦連結到工作帳戶的公司入口網站。

## Microsoft Intune Center
電腦順利安裝用戶端軟體並使用 Intune 註冊電腦之後，Intune Center 會安裝成您電腦上的應用程式。 您可以使用 Intune Center 執行下列作業：

-   從公司入口網站取得應用程式 - 尋找並安裝 IT 系統管理員所部署的應用程式。 當您第一次在新註冊電腦上登入公司入口網站時，會有連結工作帳戶與該電腦的選項。

-   檢查軟體更新 - 尋找 Intune 系統管理員所部署的軟體更新。

-   啟動電腦的 Endpoint Protection 掃描 - 您可以在電腦上啟動惡意軟體的掃描。

-   尋求遠端協助 - 只有在電腦作業系統支援遠端協助時，才能使用這個選項。

## 驗證已安裝或已移除用戶端軟體
**驗證已安裝用戶端：**
電腦上具有下列應用程式時，表示 Intune 用戶端安裝已完成：

-   **Intune Center**

-   Intune Endpoint Protection (如果 IT 系統管理員啟用 Endpoint Protection)

如果您想要使用工作管理員，則可以搜尋應該執行的 Intune 用戶端服務：

-   **OmcSvc**

**驗證已移除用戶端：**
從電腦解除安裝 Intune 用戶端之後，會移除安裝用戶端時所安裝的應用程式 (包括 Intune Center)。

已移除 Intune 用戶端服務 OmcSvc。

## 如何從電腦移除用戶端軟體
在 IT 系統管理員從 Intune 管理主控台淘汰電腦之後的數個小時，預設會解除安裝 Intune 用戶端軟體。

若要手動從電腦解除安裝 Intune 用戶端軟體，您可以使用下列步驟來強制解除安裝：

1.  在電腦上，以系統管理員模式開啟命令提示字元。

2.  前往資料夾 %programfiles%\Microsoft\OnlineManagement\Common

3.  執行下列命令：ProvisioningUtil.exe /UninstallAgents /MicrosoftIntune

這會排程移除用戶端軟體。



<!--HONumber=May16_HO1-->


