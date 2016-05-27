---
# required metadata

title: 裝置註冊到 Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8fc415f7-0053-4aa5-8d2b-03202eca4b87

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 註冊裝置以在 Intune 中管理
Microsoft Intune 行動裝置管理 (MDM) 會使用註冊來管理裝置，並允許其存取資源。 註冊裝置的方式取決於裝置類型、擁有權和需要的管理層級。 「攜帶您自己的裝置」(BYOD) 和公司擁有的裝置 (CYOD) 案例都需要註冊程序。 不論使用 Exchange ActiveSync 的組織是在內部部署或雲端中託管，都可以進行較少的管理而不需要註冊。 也可以使用 Intune 用戶端軟體來管理 Windows 電腦。

## 啟用裝置註冊  
 註冊可讓使用者在其個人裝置上存取公司資源，並讓系統管理員確保這些裝置遵守保護公司資源的原則。 這是使用 Intune 啟用「攜帶您自己的裝置」案例的最佳方式。 系統管理員必須在 Intune 主控台中啟用註冊，可能需要與裝置建立信任關係，並將授權指派給使用者。 接著會註冊裝置，通常由使用者輸入其公司或學校認證完成。 裝置隨後會從 Intune 接收原則，並取得資源的存取權。

[準備好在 Intune 中註冊裝置](get-ready-to-enroll-devices-in-microsoft-intune.md)

## 註冊公司擁有的裝置
可使用 Intune 主控台管理公司擁有的裝置 (CYOD)。 可直接透過 Apple 提供的工具註冊 iOS 裝置。 系統管理員或管理員可使用裝置註冊管理員來註冊所有裝置類型。 也可以將包含 IMEI 號碼的裝置識別和標記為公司擁有，以啟用 COD 案例。

[註冊公司擁有的裝置](manage-corporate-owned-devices.md)

## 使用 Exchange ActiveSync 和 Intune 的行動裝置管理
Intune 可使用 EAS MDM 原則來管理未註冊、但連線到 Exchange ActiveSync (EAS) 的行動裝置。 Intune 會使用 Exchange Connector 與內部部署和雲端託管的 EAS 通訊。



[使用 Exchange ActiveSync 和 Intune 的行動裝置管理](mobile-device-management-with-exchange-activesync-and-microsoft-intune.md)


## 使用 Intune 管理 Windows 電腦  
您也可以使用 Intune Windows PC 用戶端軟體，使用 Microsoft Intune 來管理 Windows 電腦。 使用 Intune 用戶端管理的電腦可以︰

 - 報告軟體和硬體清查
 - 安裝桌面應用程式 (例如 .exe 和 .msi 檔案)
 - 防火牆設定

使用 Intune 用戶端軟體管理的電腦無法選擇性地抹除或淘汰，而且無法利用許多 Intune 管理功能，例如條件式存取、VPN 和 Wi-Fi 設定，或憑證和電子郵件組態部署。

[使用 Intune 管理 Windows 電腦](manage-windows-pcs-with-microsoft-intune.md)


<!--HONumber=May16_HO2-->


