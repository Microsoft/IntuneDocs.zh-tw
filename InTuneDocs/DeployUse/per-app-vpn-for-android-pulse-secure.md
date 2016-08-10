---
title: "使用 Pulse Secure 之 Android 的個別應用程式 VPN | Microsoft Intune"
description: "您可以為 Intune 所管理的 Android 裝置建立個別應用程式 VPN 設定檔。"
keywords: 
author: nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ac65e906-3922-429f-8d9c-d313d3126645
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 52d9d2ad912de7bc775cde2c40c8de27a09ba2af
ms.openlocfilehash: d37630d2aaf4a260acf98a57aa2d38c95711f12b


---

# 使用自訂原則來建立 Android 裝置的個別應用程式 VPN 設定檔

您可以為 Intune 所管理的 Android 裝置建立個別應用程式 VPN 設定檔。 首先，您將建立使用 Pulse Secure 連線類型的 VPN 設定檔，然後建立該設定檔與特定應用程式之關聯的自訂設定原則。 將這些原則部署至 Android 裝置或使用者群組之後，在這些裝置上開啟其中一個指定的應用程式，即會開啟該應用程式的 VPN 連線。

> [注意]
> 
> 此設定檔僅支援 Pulse Secure 連線類型。


### 步驟 1︰建立 VPN 設定檔

1. 在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，按一下 [原則] > [新增原則]。
2. 展開 [Android]，然後選擇 [VPN 設定檔 (Android 4 及更新版本)])，以選取新原則的範本。

3. 在範本中，針對 [連線類型]，選擇 [Pulse Secure]。
4. 完成並儲存 VPN 設定檔。 如需 VPN 設定檔的詳細資訊，請參閱 [VPN 連線](vpn-connections-in-microsoft-intune.md)。

> [!NOTE]
記下下一步中所使用的 VPN 設定檔名稱。 例如，**MyAppVpnProfile**。

### 步驟 2：建立自訂設定原則

   1. 在 Intune 管理主控台中，[原則] -> [新增原則][Android] -> [自訂設定] ->  -> [建立原則]。
   2. 提供原則的名稱。
   3. 在 [OMA-URI 設定] 下，按一下 [新增]。
   4. 提供設定名稱。
   5. 針對 [資料類型] 請指定 [String]。
   6. 針對 [OMA-URI]，指定這個字串：**./Vendor/MSFT/VPN/Profile/*Name*/PackageList**，其中 *Name* 是您在步驟 1 記下的 VPN 設定檔名稱。 在這個範例中，字串會是 **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList**。
   7.   在 [值] 中，提供應該與設定檔相關聯的套件清單 (以分號區隔)。  例如，如果您想要 Excel 和 Google Chrome 瀏覽器使用 VPN 連線，則會輸入︰**com.microsoft.office.excel;com.android.chrome**。


   ![Android 個別應用程式 VPN 自訂原則範例](..\media\android_per_app_vpn_oma_uri.png)
#### 將應用程式清單設定為封鎖清單或允許清單 (選用)
使用 [BLACKLIST] 值，即可指定*不*允許應用程式清單使用 VPN 連線。  所有其他應用程式都會透過 VPN 進行連線。

或者，使用 [WHITELIST] 值，即可指定*只*有指定的應用程式才能使用 VPN 連線。


1.  在 [OMA-URI 設定] 下，按一下 [新增]。
2.  提供設定名稱。
3.  針對 [資料類型] 請指定 [String]。
4.  針對 [OMA-URI]，指定這個字串：**./Vendor/MSFT/VPN/Profile/*Name*/Mode**，其中 *Name* 是您在步驟 1 記下的 VPN 設定檔名稱。 在這個範例中，字串會是 **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode**。
5.  在 [值] 中，輸入 **BLACKLIST** 或 **WHITELIST**。



### 步驟 3︰兩個原則都部署

您必須將*兩個*原則部署至*相同的* Intune 群組。

   1.  在 [原則]  工作區中，選取您要部署的原則，然後按一下 [管理部署] 。

2.  在 [管理部署]  對話方塊中：

    -   **部署原則** - 選取您要部署原則的一或多個群組，然後按一下 [新增] &gt; [確定]。

    -   **關閉對話方塊但不加以部署** - 按一下 [取消]。

在 [原則]  工作區的 [概觀]  頁面上，狀態摘要和警示可識別需要注意的原則問題。 此外，狀態摘要還會顯示在 [儀表板] 工作區中。



<!--HONumber=Aug16_HO1-->


