---
title: 網路存取控制與 Microsoft Intune 的整合 - Azure | Microsoft Docs
description: 網路存取控制 (NAC) 解決方案會向 Intune 確認裝置的註冊與合規性狀態。 NAC 包含特定的行為，並且會與條件式存取搭配運作。 請參閱步驟來開始上線，以及取得合作夥伴解決方案清單。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/18/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: aa7ecff7-8579-4009-8fd6-e17074df67de
ms.reviewer: davidra
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: edac1701de22fd94eac3990949d18389841a5444
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231515"
---
# <a name="network-access-control-nac-integration-with-intune"></a>搭配 Intune 的網路存取控制 (NAC) 整合

Intune 會與網路存取控制夥伴整合，以協助組織在裝置嘗試存取內部資源時保護公司資料。

## <a name="how-do-intune-and-nac-solutions-help-protect-your-organization-resources"></a>Intune 和 NAC 解決方案如何協助保護您的組織資源？

NAC 解決方案會向 Intune 確認裝置註冊與合規性狀態，以做出存取控制決定。 如果裝置未註冊，或是已註冊但不符合 Intune 裝置合規性原則，就應該將裝置重新導向至 Intune 來進行註冊和/或裝置合規性檢查。

### <a name="example"></a>範例

如果裝置已註冊並符合 Intune，NAC 解決方案應該允許裝置存取公司資源。 例如，在嘗試存取公司 Wi-Fi 或 VPN 資源時，可以允許或拒絕使用者存取。

## <a name="feature-behaviors"></a>功能行為

主動同步至 Intune 的裝置不能從 [符合規範] / [不符合規範] 移至 [未同步] (或 [未知])。 [未知] 是保留給尚未針對合規性進行評估之新註冊裝置的狀態。

針對被封鎖而無法存取資源的裝置，封鎖服務應該將所有使用者重新導向至[管理入口網站](https://portal.manage.microsoft.com)，以判斷該裝置被封鎖的原因。  若使用者造訪此頁面，其裝置將會同步地重新進行合規性評估。

## <a name="nac-and-conditional-access"></a>NAC 和條件式存取

NAC 會與條件式存取搭配運作以提供存取控制決定。 如需詳細資料，請參閱[搭配 Intune 使用條件式存取的常見方式](conditional-access-intune-common-ways-use.md)。

## <a name="how-the-nac-integration-works"></a>NAC 整合的運作方式

以下清單概述與 Intune 整合時，NAC 整合的運作方式。 前三個步驟 (1-3) 會說明上線程序。 在 NAC 解決方案與 Intune 整合之後，步驟 4 到 9 則說明接下來的作業。

![NAC 搭配 Intune 的運作方式](./media/ca-intune-common-ways-2.png)

1. 向 Azure Active Directory (AAD) 註冊 NAC 合作夥伴解決方案，並授權委派權限給 Intune NAC 應用程式開發介面。
2. 為 NAC 合作夥伴解決方案設定適當的設定，包括 Intune 探索 URL。
3. 設定 NAC 合作夥伴解決方案以進行憑證驗證。
4. 使用者連線到公司 Wi-Fi 存取點或進行 VPN 連線要求。
5. NAC 合作夥伴解決方案將裝置資訊轉送至 Intune，並詢問 Intune 裝置註冊與合規性狀態。
6. 如果裝置不符合規範或未註冊，NAC 合作夥伴解決方案會指示使用者註冊或修正裝置合規性。
7. 裝置會嘗試重新確認其合規性和/或註冊狀態。
8. 一旦裝置已註冊且符合規範，NCA 合作夥伴解決方案會從 Intune 取得狀態。
9. 已成功建立連線，可讓裝置存取公司資源。

## <a name="next-steps"></a>接下來的步驟

- [Integrate Cisco ISE with Intune](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html) (整合 Cisco ISE 與 Intune)
- [Integrate Citrix NetScaler with Intune](http://docs.citrix.com/en-us/netscaler-gateway/12/microsoft-intune-integration/configuring-network-access-control-device-check-for-netscaler-gateway-virtual-server-for-single-factor-authentication-deployment.html) (整合 Citrix NetScaler 與 Intune)
- [Integrate HP Aruba Clear Pass with Intune](https://support.arubanetworks.com/Documentation/tabid/77/DMXModule/512/Command/Core_Download/Default.aspx?EntryId=23757) (整合 HP Aruba Clear Pass 與 Intune)
- [整合 Squadra security Removable Media Manager (secRMM) 與 Intune ](http://www.squadratechnologies.com/StaticContent/ProductDownload/secRMM/9.9.0.0/secRMMIntuneAccessControlSetupGuide.pdf) \(英文\)