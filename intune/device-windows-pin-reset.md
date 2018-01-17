---
title: "使用 Intune 在 Windows 裝置上重設密碼"
titlesuffix: Azure portal
description: "了解如何使用 Intune 在整合了 Microsoft PIN 重設服務的 Windows 裝置上重設密碼。」"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5027d012-d6c2-4971-a9ac-217f91d67d87
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 144313b63c1a6349a59220c901072dbf9d4c6f43
ms.sourcegitcommit: 22ab1c6a6bfeb4fef9850d12b29829c3fecbbeed
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/12/2018
---
# <a name="reset-the-passcode-on-windows-devices-integrated-with-the-microsoft-pin-reset-service-using-intune"></a>使用 Intune 在整合了 Microsoft PIN 重設服務的 Windows 裝置上重設密碼

與 Microsoft Pin 重設服務整合的 Windows 裝置重設密碼功能，能讓您為執行 Windows 10 行動裝置版的裝置產生新的密碼。 這些裝置必須執行 Windows 10 Creators Update 或更新版本。

## <a name="supported-platforms"></a>支援的平台

- Windows - 支援 Windows 10 Creators Update 和更新版本 (已加入 Azure AD)
- Windows Phone - 不支援
- iOS - 不支援
- macOS - 不支援
- Android - 不支援


## <a name="before-you-start"></a>開始之前

您必須先將 PIN 重設服務上架到您的 Intune 租用戶，並設定您管理的裝置，才能在您可以管理的 Windows 裝置上遠端重設密碼。 請依照這些指示開始作業：

### <a name="connect-intune-with-the-pin-reset-service"></a>連接 Intune 與 PIN 重設服務

1. 前往 [Microsoft PIN 重設服務整合網站](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=b8456c59-1230-44c7-a4a2-99b085333e84&resource=https%3A%2F%2Fgraph.windows.net&redirect_uri=https%3A%2F%2Fcred.microsoft.com&state=e9191523-6c2f-4f1d-a4f9-c36f26f89df0&prompt=admin_consent)，以管理 Intune 租用戶所用的租用戶管理員帳戶登入。
2. 登入之後，按一下 [接受] 同意 PIN 重設服務，以存取您的帳戶。<br>
![PIN 重設服務權限頁面](./media/pin-reset-service-application.png)
3. 在 Azure 入口網站中，您可以從企業應用程式中確認 Intune 和 PIN 重設服務是否整合，所有的應用程式刀鋒視窗如以下螢幕擷取畫面所示：<br>
![Azure 中的 PIN 重設服務應用程式](./media/pin-reset-service-home-screen.png)
4. 使用您的 Intune 租用戶管理員認證登入[此網站](https://login.windows.net/common/oauth2/authorize?response_type=code&client_id=9115dd05-fad5-4f9c-acc7-305d08b1b04e&resource=https%3A%2F%2Fcred.microsoft.com%2F&redirect_uri=ms-appx-web%3A%2F%2FMicrosoft.AAD.BrokerPlugin%2F9115dd05-fad5-4f9c-acc7-305d08b1b04e&state=6765f8c5-f4a7-4029-b667-46a6776ad611&prompt=admin_consent)，再次選擇同意 [接受] 服務以存取您的帳戶。

### <a name="configure-windows-devices-to-use-pin-reset"></a>設定 Windows 裝置使用 PIN 重設

若要在您管理的 Windows 裝置上設定 PIN 重設，請使用 [Intune Windows 10 自訂裝置原則](custom-settings-windows-10.md)啟用功能。 使用下列 Windows 原則設定服務提供者 (CSP) 設定原則：


- **裝置為** - **./Device/Vendor/MSFT/PassportForWork/<租用戶識別碼>**/Policies/EnablePinRecovery**

<租用戶識別碼>是指您的 Azure Active Directory，您可以從 Azure Active Directory 的 [屬性] 頁面取得 Directory 識別碼。

針對此 CSP 將值設定為 **True**。

## <a name="steps-to-reset-the-passcode"></a>重設密碼的步驟

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置]。
4. 在 [裝置] 刀鋒視窗中，選擇 [管理] > [所有裝置]。
5. 選取您要重設密碼的裝置，然後在該裝置的 [裝置內容] 刀鋒視窗中選擇 [新密碼]。
6. 從顯示的確認畫面中選擇 [是]。 密碼即產生，而且會在入口網站中顯示七天。

## <a name="next-steps"></a>接下來的步驟

如果密碼重設失敗，入口網站會提供連結供您取得詳細資訊。


