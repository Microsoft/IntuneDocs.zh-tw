---
title: "與 Intune 的網路存取控制整合"
titleSuffix: Intune on Azure
description: "與 Intune 的網路存取控制 (NAC) 整合"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: aa7ecff7-8579-4009-8fd6-e17074df67de
ms.reviewer: davidra
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6037ec4638b487c0bae8fcecf2d9bd010e3bc59a
ms.sourcegitcommit: fd2e8f6f8761fdd65b49f6e4223c2d4a013dd6d9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2017
---
# <a name="network-access-control-nac-integration-with-intune"></a>與 Intune 的網路存取控制 (NAC) 整合

Intune 會與網路存取控制夥伴整合，以協助組織在裝置嘗試存取內部資源時保護公司資料。

## <a name="how-do-intune-and-nac-solutions-help-protect-your-organization-resources"></a>Intune 和 NAC 解決方案如何協助保護您的組織資源？

NAC 解決方案負責檢查裝置註冊與合規性狀態，Intune 則進行存取控制決定。 如果裝置未註冊，或是已註冊但不符合 Intune 裝置合規性原則，裝置應該重新導向至 Intune 進行註冊及/或裝置合規性檢查。

### <a name="example"></a>範例

如果裝置已註冊並符合 Intune，NAC 解決方案應該允許裝置存取公司資源。 例如，在嘗試存取公司 Wi-Fi 或 VPN 資源時，可以允許或拒絕使用者存取。

## <a name="nac-and-conditional-access"></a>NAC 和條件式存取

NAC 搭配條件式存取，以提供存取控制決定。

- 如需詳細資訊，請參閱[透過 Intune 使用條件式存取的常見方式](conditional-access-intune-common-ways-use.md)。

## <a name="how-the-nac-integration-works"></a>NAC 整合的運作方式

以下是在與 Intune 整合時，NAC 整合的運作方式概觀，前三個步驟說明上架程序。 一旦 NAC 解決方案與 Intune 整合之後，步驟 4 至 9 說明進行中的作業。

![NAC 搭配 Intune 的運作方式](./media/ca-intune-common-ways-2.png)

1.  向 Azure Active Directory (AAD) 註冊 NAC 合作夥伴解決方案，並授權委派權限給 Intune NAC 應用程式開發介面。

2.  為 NAC 合作夥伴解決方案設定適當的設定，包括 Intune 探索 URL。

3.  設定 NAC 合作夥伴解決方案以進行憑證驗證。

4.  使用者連線到公司 Wi-Fi 存取點或進行 VPN 連線要求。

5.  NAC 合作夥伴解決方案將裝置資訊轉送至 Intune，並詢問 Intune 裝置註冊與合規性狀態。

6.  如果裝置不符合規範或未註冊，NAC 合作夥伴解決方案會指示使用者註冊或修正裝置合規性。

7.  裝置會嘗試重新確認其合規性和/或註冊狀態。

8.  一旦裝置已註冊且符合規範，NCA 合作夥伴解決方案會從 Intune 取得狀態。

9.  已成功建立連線，可讓裝置存取公司資源。

## <a name="next-steps"></a>後續步驟

-   [Integrate Cisco ISE with Intune](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html) (整合 Cisco ISE 與 Intune)

-   [Integrate Citrix NetScaler with Intune](https://docs.citrix.com/netscaler-gateway/11-1/microsoft-intune-integration/configuring-network-access-control-device-check-for-netscaler-gateway-virtual-server-for-single-factor-authentication-deployment.html) (整合 Citrix NetScaler 與 Intune)

-   [Integrate HP Aruba Clear Pass with Intune](https://support.arubanetworks.com/Documentation/tabid/77/DMXModule/512/Command/Core_Download/Default.aspx?EntryId=23757) (整合 HP Aruba Clear Pass 與 Intune)
