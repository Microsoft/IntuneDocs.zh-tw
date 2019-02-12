---
title: Jamf 裝置的裝置合規性政策 | Microsoft Intune
titlesuffix: Microsoft Intune
description: 使用 Azure Active Directory 條件式存取搭配 Microsoft Intune 合規性政策來協助保護受 Jamf 管理的裝置。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 65a82a171253a40b05c42abec3a12371c471e860
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55837387"
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>在使用 Jamf Pro 管理的 Mac 上強制執行合規性

適用於：Azure 入口網站中的 Intune

您可以使用 Azure Active Directory 和 Microsoft Intune 的條件式存取原則，確定您的使用者符合組織需求的規範。 您可以將這些原則套用至[使用 Jamf Pro 管理的](conditional-access-integrate-jamf.md) Mac 上。 這需要 Intune 和 Jamf Pro 主控台的存取權。

## <a name="set-up-device-compliance-policies-in-intune"></a>在 Intune 中設定裝置合規性原則

1. 開啟 Microsoft Azure，然後瀏覽至 [Intune] > [裝置合規性] > [原則]。 您可以建立 macOS 的原則，包括針對不符合規範的使用者及群組選擇一系列的動作 (例如傳送警告電子郵件)。
2. 搜尋想要的群組，然後對它們套用原則。

> [!Note]
> Intune 需要完整磁碟加密符合規範。

## <a name="deploy-the-company-portal-app-for-macos-in-jamf-pro"></a>在 Jamf Pro 中部署 macOS 的公司入口網站應用程式

您應該遵循下列程序，在 Jamf Pro 中將 macOS 公司入口網站應用程式部署為背景安裝：

1. 在 macOS 裝置上，下載 [macOS 版公司入口網站應用程式](https://go.microsoft.com/fwlink/?linkid=862280)的目前版本。 不要安裝它。您需要將應用程式複本上傳至 Jamf Pro。
2. 開啟 Jamf Pro，然後瀏覽至[電腦管理] > [套件]。
3. 搭配 macOS 版公司入口網站應用程式建立新的套件，然後按一下 [儲存]。
4. 開啟 [電腦] > [原則]，然後選取 [新增]。
5. 使用**一般**承載來設定原則設定。 這些設定應為：
   - 觸發程序：選取 [註冊完成] 和 [Recurring Check-in] (重複簽入)
   - 執行頻率：選取 [每部電腦一次]
6. 選取 [套件] 承載並按一下 [設定]。
7. 按一下 [新增] 以選取搭配公司入口網站應用程式的套件。
8. 從 [動作] 快顯功能表選擇 [安裝]。
9. 設定套件的設定。
10. 按一下 [範圍] 索引標籤以指定要安裝公司入口網站應用程式的電腦。 按一下 **[儲存]**。 當選取的觸發程序下次發生於電腦上，且符合 [一般] 承載的準則時，原則將會執行範圍裝置。

## <a name="create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory"></a>在 Jamf Pro 中建立原則讓使用者使用 Azure Active Directory 註冊其裝置

> [!NOTE]
> 您需要[部署 macOS 版公司入口網站](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro)，才能繼續進行下一個步驟。  

使用者必須透過 Jamf 自助服務啟動公司入口網站應用程式，以向 Azure AD 將裝置註冊為由 Jamf Pro 管理的裝置。 這會需要使用者採取行動。 我們建議您透過電子郵件、Jamf Pro 通知[連絡您的使用者](end-user-educate.md)，或使用任何其他方法通知您的使用者，按一下 Jamf 自助服務中的按鈕。

> [!WARNING]
> 公司入口網站應用程式必須從 Jamf 自助服務啟動，才能開始裝置註冊。 <br><br>以手動方式啟動公司入口網站應用程式 (例如，從 [應用程式] 或 [下載] 資料夾)，不會註冊裝置。 如果使用者以手動方式啟動公司入口網站，他們會看到 'AccountNotOnboarded' 警告。

1. 在 Jamf Pro 中，瀏覽至 [電腦] > [原則]，然後針對裝置註冊建立新的原則。
2. 設定 [Microsoft Intune 整合] 承載，包括觸發程序和執行頻率。
3. 按一下 [範圍] 索引標籤，然後將原則的範圍設定為所有目標裝置。
4. 按一下 [自助服務] 索引標籤，使原則可在 Jamf 自助服務中使用。 將原則包含在 [裝置合規性] 類別中。 按一下 **[儲存]**。

## <a name="removing-a-jamf-managed-device-from-intune"></a>從 Intune 移除受控於 Jamf 的裝置

您可以在 [所有裝置] 檢視中選取 [刪除]，以從 Intune 主控台移除 Jamf 受控裝置。 選取多個裝置，並按一下 [刪除]，即可啟用刪除大量裝置。

在 Jamf Pro 文件中取得如何[移除 Jamf 受控裝置](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information)的相關資訊。您也可以透過 [Jamf 支援](https://www.jamf.com/support/)提出支援票證，以取得其他支援。 

## <a name="next-steps"></a>後續步驟

- [Azure Active Directory 中的條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [開始使用 Azure Active Directory 中的條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
