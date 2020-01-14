---
title: 整合 Windows Hello 企業版與 Microsoft Intune
titleSuffix: Microsoft Intune
description: 了解如何建立原則，以控制在受管理的裝置上使用 Windows Hello 企業版。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/25/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: shpate
ms.openlocfilehash: 001e68fdbab7074abb4e1bbefc697d3e34c47762
ms.sourcegitcommit: 107fef144013b01ed768ca8973373f9cb3f0f7dc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2020
ms.locfileid: "75683777"
---
# <a name="integrate-windows-hello-for-business-with-microsoft-intune"></a>整合 Windows Hello 企業版與 Microsoft Intune  

您可以整合 Windows Hello 企業版 (先前稱為 Microsoft Passport for Work) 與 Microsoft Intune。

 Hello 企業版是使用 Active Directory 或 Azure Active Directory 帳戶取代密碼、智慧卡或虛擬智慧卡的替代登入方法。 您可使用其提供的「使用者筆勢」  登入，而不使用密碼登入。 使用者筆勢可以是 PIN、生物識別驗證 (例如 Windows Hello) 或外部裝置 (例如指紋辨識器)。

Intune 以兩種方式與 Hello 企業版整合：

- 您可以在 [裝置註冊]  下建立 Intune 原則。 此原則以整個組織 (整個租用戶) 為目標。 它支援 Windows AutoPilot 全新體驗 (OOBE)，並會在裝置註冊時套用。 
- 您可以在 [裝置設定]  下建立 Identity Protection 設定檔。 此設定檔以指派的使用者和裝置為目標，並會在簽入期間套用。 

本文可用來建立以您整個組織為目標的預設 Windows Hello 企業版原則。 若要建立套用至所選使用者和裝置群組的 Identity Protection 設定檔，請參閱[設定 Identity Protection 設定檔](identity-protection-configure.md)。  

<!--- - You can store authentication certificates in the Windows Hello for Business key storage provider (KSP). For more information, see [Secure resource access with certificate profiles in Microsoft Intune](secure-resource-access-with-certificate-profiles.md). --->

> [!IMPORTANT]
> 在年度更新版之前的 Windows 10 電腦和行動裝置版本中，您可以設定兩個不同的 PIN 碼，以用來驗證資源：
> - 「裝置 PIN」  可以用來解除鎖定裝置及連線到雲端資源。
> - 「公司 PIN」  是用來在使用者的個人裝置 (BYOD) 上存取 Azure AD 資源。
> 
> 在年度更新版中，這兩個 PIN 已經合併成一個單一的裝置 PIN 。
> 任何您設定來控制裝置 PIN 的 Intune 設定原則，以及您所設定的 Windows Hello 企業版原則，現在都會設定此一新 PIN 值。
> 如果您將這兩種原則都設定成可以控制該 PIN，則 Windows Hello 企業版原則會套用到 Windows 10 Desktop 和行動裝置。
> 若要確保解決原則衝突，且正確套用 PIN 原則，請更新您的 Windows Hello 企業版原則，以符合您設定原則中的設定，並要求使用者在「公司入口網站」App 中同步他們的裝置。



## <a name="create-a-windows-hello-for-business-policy"></a>建立 Windows Hello 企業版原則

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 移至 [裝置]   >  [註冊]   > [註冊裝置]   > [Windows 註冊]   > [Windows Hello 企業版]  。 [Windows Hello 企業版] 窗格隨即開啟。

3. 針對 [設定 Windows Hello 企業版]  ，從下列選項中選取：

    - **Disabled**。 如果您不想要使用 Windows Hello 企業版，請選取此設定。 若停用，除了在可能需要佈建的已加入 Azure Active Directory 的行動電話上，使用者將無法佈建 Windows Hello 企業版。
    - **Enabled**。 如果您想要設定 Windows Hello 企業版設定，請選取此設定。  當您選取 [已啟用]  時，將會顯示 Windows Hello 的其他設定。
    - **未設定**。 如果您不想要使用 Intune 來控制 Windows Hello 企業版設定，請選取此設定。 不會變更 Windows 10 裝置上任何現有的 Windows Hello 企業版設定。 窗格上的所有其他設定，都無法使用。

4. 如果在前一步驟選取了 [已啟用]  ，請設定會套用到所有已註冊之 Windows 10 與 Windows 10 行動裝置版裝置所需的設定。 在您已設定這些設定之後，請選取 [儲存]  。

   - **使用信賴平台模組 (TPM)** ：

     TPM 晶片提供額外一層資料安全性。 選擇下列其中一個值：

     - **必要** (預設)。 只有能存取 TPM 的裝置可以佈建 Windows Hello 企業版。
     - **慣用**。 第一次嘗試使用 TPM 的裝置。 如果無法使用此選項，則可以使用軟體加密。

   - [PIN 長度下限]  和 [PIN 的長度上限]  ：

     設定裝置以使用您指定的最小和最大 PIN 長度，協助確保安全的登入。 預設的 PIN 長度為 6 個字元，但您可以強制執行最小長度 (4 個字元)。 PIN 長度上限為 127 個字元。

   - [PIN 的小寫字母]  、[PIN 中的大寫字母]  和 [PIN 中的特殊字元]  。

     您可以要求在 PIN 中使用大寫字母、小寫字母及特殊字元，以強制使用強度更高的 PIN。 針對每個設定，請從下列選項中選取：

     - **允許**。 使用者可在其 PIN 中使用字元類型，但不是強制性。

     - **必要**。 使用者必須在其 PIN 中包含至少一個字元類型。 比方說，是常見的作法是需要至少一個大寫字母和一個特殊字元。

     - **不允許** (預設)。 使用者不得在其 PIN 中使用這些字元 (這也是未進行設定時的行為)。

       特殊字元包含： **! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**

   - **PIN 到期 (天數)** ：

     建議為 PIN 指定到期時間，使用者必須在該時間後變更 PIN。 預設為 41 天。

   - **記住 PIN 碼歷程記錄**：

     限制重複使用先前用過的 PIN。 預設不能重複使用最後 5 個 PIN。

   - **允許生物識別驗證**：

     啟用生物識別驗證 (例如臉部辨識或指紋) 以替代 Windows Hello 企業版的 PIN。 使用者仍然必須設定公司 PIN 以免生物識別驗證失敗。 從下列選項進行選擇：

     - **是**。 Windows Hello 企業版允許生物識別驗證。
     - **否**。 Windows Hello 企業版防止生物識別驗證 (針對所有帳戶類型)。

   - **使用進階防詐騙 (如可使用)** ：

     設定是否要在支援的裝置上使用 Windows Hello 的反詐騙功能。 例如，偵測出前方為包含臉部的相片，而非實際的臉部。

     設定為 [是]  時，Windows 便會要求所有使用者在支援的情況下使用臉部特徵的防詐騙功能。

   - **允許手機登入**：

     若此選項設為 [是]  ，使用者即可使用遠端 Passport 作為桌上型電腦驗證的可攜式配套裝置。 桌上型電腦必須已加入 Azure Active Directory，且配套裝置必須設有 Windows Hello 企業版的 PIN。

## <a name="windows-holographic-for-business-support"></a>Windows Holographic for Business 支援

Windows Holographic for Business 支援下列 Windows Hello 企業版設定：

- 使用信賴平台模組 (TPM)
- PIN 長度下限
- PIN 長度上限
- PIN 中的小寫字母
- PIN 中的大寫字母
- PIN 中的特殊字元
- PIN 碼到期 (天數)
- 記住 PIN 碼歷程記錄

## <a name="next-steps"></a>後續步驟

如需 Windows Hello 企業版的詳細資訊，請參閱 Windows 10 文件中的[指南](https://technet.microsoft.com/library/mt589441.aspx)。
