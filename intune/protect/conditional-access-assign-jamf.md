---
title: Jamf 裝置的裝置相容性原則
titleSuffix: Microsoft Intune
description: 搭配 Azure Active Directory 條件式存取使用 Microsoft Intune 合規性政策，來協助保護受 Jamf 管理的裝置。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c87fd2bd-7f53-4f1b-b985-c34f2d85a7bc
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b09b30fd32caace9ed3259350c01548d5e5fae15
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74161601"
---
# <a name="enforce-compliance-on-macs-managed-with-jamf-pro"></a>在使用 Jamf Pro 管理的 Mac 上強制執行合規性

當您[將 Jamf Pro 與 Intune 整合](conditional-access-integrate-jamf.md)時，可以使用條件式存取原則，以根據您的組織需求在 Mac 裝置上強制執行合規性。  此文章將協助您進行以下工作：  

- 建立條件式存取原則。
- 設定 Jamf Pro，以將 Intune 公司入口網站應用程式部署到您使用 Jamf 管理的裝置。
- 設定裝置，以在裝置使用者從 Jamf 自助服務應用程式內開始登入公司入口網站應用程式時，向 Azure AD 註冊。 裝置註冊會在 Azure AD 中建立身分識別，以允許透過條件式存取原則來評估裝置，以存取公司資源。  
 
此文章中的程序需要 Intune 和 Jamf Pro 主控台的存取權。

## <a name="set-up-device-compliance-policies-in-intune"></a>在 Intune 中設定裝置合規性原則

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 選取 [裝置]   > [合規性政策]  。 如果您是使用先前建立的原則，請在主控台中選取該原則，然後移至此程序的下一個步驟。 若要建立新原則，請選取 [建立原則]  ，然後指定 [平台]  為 [macOS]  的原則詳細資料。 設定 [設定]  和 [因不符合規範而採取的動作]  ，以符合您的組織需求，然後選取 [建立]  以儲存原則。

3. 在原則的 [概觀]  窗格上，選取 [指派]  。 使用可用的選項來設定會收到此原則的 Azure Active Directory (Azure AD) 使用者與安全性群組。 Jamf 與 Intune 的整合不支援以裝置群組為目標的合規性政策。

4. 當您選取 [儲存]  時，原則就會部署至使用者。  

您部署的原則會以指派的使用者所使用的裝置為目標。 系統會評估那些裝置的合規性。 符合規範的裝置會標示為符合規範，表示符合 Azure AD 中 [裝置需要標記為合規]  這個設定的規範。  

> [!NOTE]
> Intune 需要完整磁碟加密符合規範。

## <a name="deploy-the-company-portal-app-for-macos-in-jamf-pro"></a>在 Jamf Pro 中部署 macOS 的公司入口網站應用程式

在 Jamf Pro 中建立原則，以部署 Intune 公司入口網站。 此原則會部署公司入口網站應用程式，讓它能在 Jamf 自助服務中使用。 請在您於 Jamf Pro 中為使用者建立原則之前，先建立此原則，以便能在 Azure AD 註冊裝置。  

若要完成下列程序，您需要 macOS 裝置和 Jamf Pro 入口網站的存取權。 

### <a name="to-deploy-the-company-portal-app"></a>部署公司入口網站應用程式  

1. 在 macOS 裝置上，下載 [macOS 版公司入口網站應用程式](https://go.microsoft.com/fwlink/?linkid=862280)的目前版本，但不要安裝。 您只需要應用程式複本，以便上傳至 Jamf Pro。  

2. 開啟 Jamf Pro，然後前往 [電腦管理]   > [套件]  。

3. 搭配 macOS 版公司入口網站應用程式建立新的套件，然後選取 [儲存]  。

4. 開啟 [電腦]   > [原則]  ，然後選取 [新增]  。

5. 使用**一般**承載來設定原則設定。 這些設定應為：
   - 觸發程序：選取 [註冊完成]  和 [Recurring Check-in] (重複簽入) 
   - 執行頻率：選取 [每部電腦一次] 

6. 選取 [套件]  承載並按一下 [設定]  。

7. 按一下 [新增]  以選取搭配公司入口網站應用程式的套件。

8. 從 [動作]  快顯功能表選取 [安裝]  。
9. 設定套件的設定。

10. 選取 [範圍]  索引標籤以指定要安裝公司入口網站應用程式的電腦。 選取 [儲存]  。 當下次選取的觸發程序在電腦上發生，且符合 [一般]  承載的準則時，原則將會執行範圍裝置。

## <a name="create-a-policy-in-jamf-pro-to-have-users-register-their-devices-with-azure-active-directory"></a>在 Jamf Pro 中建立原則讓使用者使用 Azure Active Directory 註冊其裝置  

在您透過 Jamf Pro 自助服務[部署公司入口網站 ](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro) (macOS 版) 之後，您可以建立 Jamf Pro 原則，以向 Azure AD 註冊使用者的裝置。 

裝置註冊需要裝置使用者手動從 Jamf 自助服務中選取 Intune 公司入口網站應用程式。 我們建議您透過電子郵件、Jamf Pro 通知，或貴組織用來指示他們完成此動作來註冊其裝置的任何其他方法，來[連絡您的終端使用者](../fundamentals/end-user-educate.md)。 

> [!WARNING]
> 以手動方式啟動公司入口網站應用程式 (例如，從 [應用程式] 或 [下載] 資料夾) 時不會註冊裝置。 如果使用者以手動方式啟動公司入口網站，他們將會看到 **'AccountNotOnboarded'** 警告。

### <a name="to-create-the-registration-policy"></a>建立註冊原則  

1. 在 Jamf Pro 中，移至 [電腦]   > [原則]  ，然後針對裝置註冊建立新的原則。

2. 設定 [Microsoft Intune 整合]  承載，包括觸發程序和執行頻率。

3. 選取 [範圍]  索引標籤，然後將原則的範圍設定為所有目標裝置。

4. 選取 [自助服務]  索引標籤，使原則可在 Jamf 自助服務中使用。 將原則包含在 [裝置合規性]  類別中。 按一下 **[儲存]** 。

## <a name="validate-intune-and-jamf-integration"></a>驗證 Intune 和 Jamf 整合  

使用 Jamf Pro 主控台確認 Jamf Pro 和 Microsoft Intune 之間可順利通訊。 

- 在 Jamf Pro 中，移至 [設定]   > [全域管理]   > [Microsoft Intune 整合]  ，然後選取 [測試]  。

    主控台會顯示訊息，其中包含連線成功或失敗的資訊。  

如果從 Jamf Pro 主控台執行的連線測試失敗，請檢查 Jamf 設定。 


## <a name="removing-a-jamf-managed-device-from-intune"></a>從 Intune 移除受控於 Jamf 的裝置

若要移除 Jamf 受控裝置，請開啟 Microsoft Endpoint Manager 系統管理中心，然後選取 [裝置]   > [所有裝置]  選取該裝置，然後選取 [刪除]  。  選取多個裝置，並按一下 [刪除]  ，即可啟用刪除大量裝置。

在 Jamf Pro 文件中取得如何[移除 Jamf 受控裝置](https://www.jamf.com/jamf-nation/articles/80/unmanaging-computers-while-preserving-their-inventory-information)的相關資訊。您也可以透過 [Jamf 支援](https://www.jamf.com/support/)提出支援票證，以取得其他支援。 

## <a name="next-steps"></a>後續步驟

- [Azure Active Directory 中的條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)
- [開始使用 Azure Active Directory 中的條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
