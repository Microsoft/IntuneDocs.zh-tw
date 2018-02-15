---
title: "將合規性原則強制執行於 Jamf 受控裝置"
titlesuffix: Azure portal
description: "使用合規性以協助保護受 Jamf 管理的裝置。"
keywords: 
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 12/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0844852aaa1e5833e0d5013ac9dea8862d7d752b
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>在使用 Jamf Pro 管理的 Mac 上強制執行合規性

|適用對象：Azure 入口網站的 Intune |
|--|
|您需要傳統入口網站的 Intune 相關文件嗎？ [請移至這裡](/intune/introduction-intune?toc=/intune-classic/toc.json)。|
| |

您可以使用 Azure Active Directory 和 Microsoft Intune 的條件式存取原則，確定您的使用者符合組織需求的規範。 您可以將這些原則套用至[使用 Jamf Pro 管理的](conditional-access-integrate-jamf.md) Mac 上。 這需要 Intune 和 Jamf Pro 主控台的存取權。

## <a name="set-up-device-compliance-policies-in-intune"></a>在 Intune 中設定裝置合規性原則

1. 開啟 Microsoft Azure，然後瀏覽至 [Intune] > [裝置合規性] > [原則]。 您可以建立 macOS 的原則，包括針對不符合規範的使用者及群組選擇一系列的動作 (例如，傳送警告電子郵件)。
2. 搜尋想要的群組，然後對它們套用原則。

## <a name="deploy-the-company-portal-app-for-macos-in-jamf-pro"></a>在 Jamf Pro 中部署 macOS 的公司入口網站應用程式

您應該遵循下列程序，在 Jamf Pro 中將 macOS 公司入口網站應用程式部署為背景安裝：

1. 在 macOS 裝置上，下載 [macOS 版公司入口網站應用程式](https://go.microsoft.com/fwlink/?linkid=862280)的目前版本。 不要安裝它。您需要將應用程式複本上傳至 Jamf Pro。
2. 開啟 Jamf Pro，然後瀏覽至[電腦管理] > [套件]。
3. 搭配 macOS 版公司入口網站應用程式建立新的套件，然後按一下 [儲存]。
4. 開啟 [電腦] > [原則]，然後選取 [新增]。
5. 使用**一般**承載來設定原則設定。 這些設定應為：
   - 觸發程序：選取 [註冊完成] 和 [Recurring Check-in] \(重複簽入)
   - 執行頻率：選取 [每部電腦一次]
6. 選取 [套件] 承載並按一下 [設定]。
7. 按一下 [新增] 以選取搭配公司入口網站應用程式的套件。
8. 從 [動作] 快顯功能表選擇 [安裝]。
9. 設定套件的設定。
10. 按一下 [範圍] 索引標籤以指定要安裝公司入口網站應用程式的電腦。 按一下 **[儲存]**。 當選取的觸發程序下次發生於電腦上，且符合 [一般] 承載的準則時，原則將會執行範圍裝置。

## <a name="create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory"></a>在 Jamf Pro 中建立原則讓使用者使用 Azure Active Directory 註冊其裝置

> [!NOTE]
> 您需要[部署 macOS 版公司入口網站](conditional-access-assign-jamf.md#require-the-company-portal-app-for-macos)，才能繼續進行下一個步驟。  

使用者必須透過 Jamf 自助服務啟動公司入口網站應用程式，以向 Azure AD 將裝置註冊為由 Jamf Pro 管理的裝置。 這會需要使用者採取行動。 我們建議您透過電子郵件、Jamf Pro 通知[連絡您的使用者](end-user-educate.md)，或使用任何其他方法通知您的使用者，按一下 Jamf 自助服務中的按鈕。

> [!WARNING]
> 公司入口網站應用程式必須從 Jamf 自助服務啟動，才能開始裝置註冊。 <br><br>以手動方式啟動公司入口網站應用程式 (例如，從 [應用程式] 或 [下載] 資料夾)，不會註冊裝置。 如果使用者以手動方式啟動公司入口網站，他們會看到 'AccountNotOnboarded' 警告。

1. 在 Jamf Pro 中，瀏覽至 [電腦] > [原則]，然後針對裝置註冊建立新的原則。
2. 設定 [Microsoft Intune 整合] 承載，包括觸發程序和執行頻率。
3. 按一下 [範圍] 索引標籤，然後將原則的範圍設定為所有目標裝置。
4. 按一下 [自助服務] 索引標籤，使原則可在 Jamf 自助服務中使用。 將原則包含在 [裝置合規性] 類別中。 按一下 **[儲存]**。

## <a name="next-steps"></a>接下來的步驟

- [Azure Active Directory 中的條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [開始使用 Azure Active Directory 中的條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
