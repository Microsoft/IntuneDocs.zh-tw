---
title: 使用 Microsoft Intune - Azure 在 Windows 裝置上重設密碼 | Microsoft Docs
description: 若要重設 Windows 裝置上的密碼，請安裝 Microsoft PIN 重設服務和 Microsoft PIN 重設用戶端、使用您 Azure Active Directory 目錄識別碼來建立裝置原則，然後使用 Microsoft Intune 在 Azure 入口網站中重設密碼。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/07/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5027d012-d6c2-4971-a9ac-217f91d67d87
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e9e9fde8969de0690919b52c2f4d662470eb15ca
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66048151"
---
# <a name="reset-the-passcode-on-windows-devices-using-intune"></a>使用 Intune 重設 Windows 裝置的密碼

您可以重設 Windows 裝置的密碼。 重設密碼功能使用了 Microsoft PIN 重設服務，來為執行 Windows 10 行動裝置版的裝置產生新密碼。 

## <a name="supported-platforms"></a>支援的平台

- 執行 Creators Update 和更新版本 (已聯結 Azure AD) 的 Windows 10 行動裝置版。

以下是**不支援**的平台：
- Windows
- iOS
- macOS
- Android

## <a name="authorize-the-pin-reset-services"></a>授權 PIN 重設服務

若要重設 Windows 裝置上的密碼，請將 PIN 重設服務導入您的 Intune 租用戶。

1. 移至 [Microsoft PIN 重設服務生產](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=b8456c59-1230-44c7-a4a2-99b085333e84&resource=https%3A%2F%2Fgraph.windows.net&redirect_uri=https%3A%2F%2Fcred.microsoft.com&state=e9191523-6c2f-4f1d-a4f9-c36f26f89df0&prompt=admin_consent)，並使用租用戶系統管理員帳戶登入。
2. **接受**以同意 PIN 重設服務存取您的帳戶：![接受 PIN 重設伺服器的權限要求](./media/pin-reset-service-home-screen.png)
3. 移至 [Microsoft PIN 重設客戶端生產](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=9115dd05-fad5-4f9c-acc7-305d08b1b04e&resource=https%3A%2F%2Fcred.microsoft.com%2F&redirect_uri=ms-appx-web%3A%2F%2FMicrosoft.AAD.BrokerPlugin%2F9115dd05-fad5-4f9c-acc7-305d08b1b04e&state=6765f8c5-f4a7-4029-b667-46a6776ad611&prompt=admin_consent)，並使用租用戶系統管理員帳戶登入。 **接受**以同意 PIN 重設用戶端存取您的帳戶。
4. 在 [Azure 入口網站](https://portal.azure.com)中，確認 PIN 重設服務已列在企業應用程式 (所有應用程式) 中：![PIN 重設服務權限頁面](./media/pin-reset-service-application.png)

> [!NOTE]
> 接受 PIN 重設要求之後，您可能會收到 `Page not found` 訊息，或可能看似沒有任何反應。 此為正常現象。 請務必確認該兩項 PIN 重設應用程式均已列給您的租用戶。

## <a name="configure-windows-devices-to-use-pin-reset"></a>設定 Windows 裝置使用 PIN 重設

若要在您管理的 Windows 裝置上設定 PIN 重設，請使用 [Intune Windows 10 自訂裝置原則](custom-settings-windows-10.md)。 使用下列 Windows 原則設定服務提供者 (CSP) 設定原則：

**使用裝置原則** - `./Device/Vendor/MSFT/PassportForWork/*tenant ID*/Policies/EnablePinRecovery`

以您 Azure AD 目錄的識別碼取代*租用戶識別碼*，這會列在 [Azure 入口網站](https://portal.azure.com)中 Azure Active Directory 的**屬性**裡。

針對此 CSP 將值設定為 **True**。

> [!TIP]
> 建立原則之後，將其指派 (或部署) 給群組。 原則可以指派給使用者群組或裝置群組。 如果您指派給使用者群組，該群組可能包含其他裝置 (例如 IOS) 的使用者。 技術上來說並不會套用原則，但這些裝置仍然會包含在狀態詳細資料中。

## <a name="reset-the-passcode"></a>重設密碼

1. 登入 [Azure 入口網站](https://portal.azure.com)。 
2. 選取 [All services] (所有服務)，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選取 [裝置]，然後選取 [所有裝置]。
4. 選取您要重設密碼的裝置。 在裝置屬性中，選取 [新密碼]。
5. 選取 [是] 確認。 密碼即產生，而且會在入口網站中顯示七天。

## <a name="next-step"></a>後續步驟

如果密碼重設失敗，入口網站會提供連結供您取得更多詳細資訊。
