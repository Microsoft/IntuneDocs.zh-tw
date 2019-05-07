---
title: 適用於 Windows 裝置的 Intune 註冊方法
titleSuffix: Microsoft Intune
description: 了解您可在 Intune 中註冊 Windows 裝置的各種不同方式
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/02/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: ''
ms.openlocfilehash: 346b74871b7519e03ca3e68061f690ef1a4e6d6a
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61514781"
---
# <a name="intune-enrollment-methods-for-windows-devices"></a>適用於 Windows 裝置的 Intune 註冊方法

若要在 Intune 中管理裝置，必須先在 Intune 服務中註冊裝置。 個人擁有和公司擁有的裝置都可註冊進行 Intune 管理。 

在 Intune 中註冊裝置的方式有兩種：
- 使用者可以自行註冊其 Windows 電腦 
- 系統管理員可以設定原則來強制自動註冊，而不需要任何使用者參與

## <a name="user-self-enrollment-in-intune"></a>Intune 中的使用者自行註冊

使用者可以使用下列任何方法來自行註冊其 Windows 裝置：

- [攜帶您自己的裝置 (BYOD)](https://docs.microsoft.com/intune-user-help/enroll-windows-10-device)：使用者可以從裝置的 [設定] 選擇連線到**公司或學校**帳戶，來註冊其個人擁有的裝置。 此程序會：
    - 向 Azure Active Directory 註冊裝置，以存取電子郵件等公司資源。
    - 在 Intune 中註冊裝置作為個人擁有的裝置 (BYOD)。
如果系統管理員已設定自動註冊 (適用於 Azure AD Premium 訂閱)，使用者只需輸入其認證一次。 否則，他們必須透過僅限 MDM 註冊個別註冊，並重新輸入其認證。  
- **僅限 MDM 註冊**可讓使用者將現有的工作群組、Active Directory 或加入 Azure Active Directory 的電腦註冊到 Intune 中。 使用者可從現有 Windows 電腦上的 [設定] 進行註冊。 但不建議此方法，因為這並不會將裝置註冊到 Azure Active Directory 中。 它也會防止使用條件式存取等功能。
- [Azure Active Directory (Azure AD) Join](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network) - 向 Azure Active Directory 加入裝置，並讓使用者使用其 Azure AD 認證登入 Windows。 如已啟用自動註冊，則會在 Intune 中自動註冊裝置。 自動註冊的優點是使用者只需經過單一步驟程序。 否則，他們必須透過僅限 MDM 註冊個別註冊，並重新輸入其認證。 使用者可在初始 Windows OOBE 或從 [設定] 進行此註冊。 裝置會在 Intune 中標示為公司擁有的裝置。
- [Autopilot](enrollment-autopilot.md) - 將 Azure AD Join 自動化，並將公司擁有的新裝置註冊到 Intune 中。 此方法可簡化現成的體驗，而不需要將自訂作業系統映像套用到裝置。 當系統管理員使用 Intune 來管理 Autopilot 裝置時，可在裝置註冊之後管理原則、設定檔、應用程式等。  Autopilot 部署類型有兩種：[自我部署模式](https://docs.microsoft.com/windows/deployment/windows-autopilot/self-deploying) (適用 kiosk、數位告示板或共用裝置)，以及[使用者驅動模式](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven) (適用於傳統使用者)。 

## <a name="administrator-based-enrollment-in-intune"></a>Intune 中的系統管理員註冊

系統管理員可以設定下列無需使用者互動的註冊方法：

- [混合式 Azure AD Join](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy) 可讓系統管理員設定 Active Directory 群組原則，以自動註冊加入混合式 Azure AD 的裝置。 
- [Configuration Manager 共同管理](https://docs.microsoft.com/sccm/comanage/overview)可讓系統管理員將其現有的 Configuration Manager 受控裝置註冊到 Intune 中，以獲得 Intune 和 Configuration Manager 的雙重效益。 
- [裝置註冊管理員](device-enrollment-manager-enroll.md) (DEM) 是特殊的服務帳戶。 DEM 帳戶具有權限，可讓授權使用者註冊及管理公司擁有的多部裝置。 比方說，這些類型的裝置適合銷售點或公用程式應用程式，但對於需要存取電子郵件或公司資源的使用者而言則不適合。 此外，此方法不允許使用條件式存取等功能。 
- [大量註冊](windows-bulk-enroll.md)可讓授權使用者將公司擁有的大量新裝置加入到 Azure Active Directory 和 Intune。 您可以使用 Windows 設定設計工具 (WCD) 應用程式來建立佈建套件。 然後，藉由在初始 Windows OOBE 體驗期間或從現有的 Windows 電腦使用 USB 媒體，您就可以安裝佈建套件，將裝置自動註冊到 Intune 中。 

## <a name="next-steps"></a>後續步驟

[了解 Windows 註冊方法的功能](enrollment-method-capab.md)
