---
title: "控制裝置上的 Windows Hello 企業版設定 | Microsoft Intune"
description: "深入了解 Intune 如何與 Windows Hello 企業版整合，這是使用 Active Directory 或 Azure Active Directory 帳戶取代密碼、智慧卡或虛擬智慧卡的替代登入方法。"
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 09/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 402bc5a1-ada3-4c4c-a0de-292d026b4444
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 73379311acad6f2a7054e262dea701d3e7b9ad45
ms.openlocfilehash: 40344947d7c94c90258c967da36c09c95a54335c


---

# 使用 Microsoft Intune 控制裝置上的 Windows Hello 企業版設定
Microsoft Intune 與 Windows Hello 企業版 (先前稱為 Microsoft Passport for Work) 整合運作，這是使用 Active Directory 或 Azure Active Directory 帳戶取代密碼、智慧卡或虛擬智慧卡的替代登入方法。

Hello 企業版可讓您以「使用者筆勢」登入，而不使用密碼登入。 使用者筆勢可能是簡單的 PIN、生物識別驗證 (例如 Windows Hello) 或外部裝置 (例如指紋辨識器)。

Intune 以兩種方式與 Hello 企業版整合：

-   您可以使用 Intune 原則，控制使用者可以和無法用以登入的筆勢。

-   您可以將驗證憑證儲存在 Windows Hello 企業版金鑰儲存提供者 (KSP) 中。 如需詳細資訊，請參閱[使用 Microsoft Intune 中的憑證設定檔來保護資源存取](secure-resource-access-with-certificate-profiles.md)。

> [!IMPORTANT]
> 在年度更新版之前的 Windows 10 電腦和行動裝置版本中，您可以設定兩個不同的 PIN 碼，以用來驗證資源：
- 「裝置 PIN」可以用來解除鎖定裝置及連線到雲端資源。
- 「公司 PIN」是用來在使用者的個人裝置 (BYOD) 上存取 Azure AD 資源。

>在年度更新版中，這兩個 PIN 已經合併成一個單一的裝置 PIN 。
任何您設定來控制裝置 PIN 的 Intune 設定原則，以及您所設定的 Windows Hello 企業版原則，現在都會設定此一新 PIN 值。
如果您將這兩種原則都設定成可以控制該 PIN，則 Windows Hello 企業版原則將會套用到 Windows 10 電腦和行動裝置。
若要確保解決原則衝突，且正確套用 PIN 原則，請更新您的 Windows Hello 企業版原則，以符合您設定原則中的設定，並要求使用者在「公司入口網站」App 中同步他們的裝置。



## 建立 Windows Hello 企業版原則

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 [系統管理] &gt; [行動裝置管理] &gt; [Windows] &gt; [Windows Hello 企業版] 以開啟 [Windows Hello 企業版] 頁面。

    ![[Windows Hello 企業版] 頁面](../media/passport.png)

2.  選擇下列其中一項設定：
    - **停用註冊之裝置上的 Windows Hello 企業版**。 如果您不想要使用 Windows Hello 企業版，請選取此設定。 螢幕上的所有其他設定也都無法停用。
    - **啟用註冊之裝置上的 Windows Hello 企業版**。 如果您想要設定 Windows Hello 企業版設定，請選取此設定。
    - **未設定**。 如果您不想要使用 Intune 來控制 Windows Hello 企業版設定，請選取此設定。 將不會變更 Windows 10 裝置上任何現有的 Windows Hello 企業版設定。 螢幕上的所有其他設定都無法停用。
3.  如果您選取 [啟用註冊之裝置上的 Windows Hello 企業版]，請設定將會套用至所有已註冊之 Windows 10 和 Windows 10 行動裝置版裝置的必要設定。
4.  完成之後，請選擇 **[儲存]**。


## 針對 Windows Hello 企業版原則進行設定

- **使用信賴平台模組 (TPM)**。 TPM 晶片提供額外一層資料安全性。<br>選擇下列其中一個值：
    - **必要** (預設)。 只有能存取 TPM 的裝置可以佈建 Windows Hello 企業版。
    - **慣用**。 第一次嘗試使用 TPM 的裝置。 如果無法使用此值，則可以使用軟體加密。
- **需要 PIN 長度下限**/**需要 PIN 長度上限**。 設定裝置以使用您指定的最小和最大 PIN 長度，協助確保安全的登入。 預設的 PIN 長度為 6 個字元，但您可以強制執行最小長度 (4 個字元)。 PIN 長度上限為 127 個字元。
- **PIN 中需要小寫字母**/**PIN 中需要大寫字母**/**PIN 中需要特殊字元**。 您可以要求在 PIN 中使用大寫字母、小寫字母及特殊字元，以強制使用強度更高的 PIN。 從下列選項進行選擇：
    - **允許**。 使用者可在其 PIN 中使用字元類型，但不是強制性。
    - **必要**。 使用者必須在其 PIN 中包含至少一個字元類型。 比方說，是常見的作法是需要至少一個大寫字母和一個特殊字元。
    - **不允許** (預設)。 使用者不得在其 PIN 中使用這些字元  (這也是未進行設定時的行為)。<br>特殊字元包含：**! " # $ % &amp; ' ( ) &#42; + , - . / : ; &lt; = &gt; ? @ [ \ ] ^ _ &#96; { &#124; } ~**。
- **PIN 到期 (天數)**。 建議為 PIN 指定到期時間，使用者必須在該時間後變更 PIN。 預設為 41 天。
- **記住 PIN 記錄**。 限制重複使用先前用過的 PIN。 預設為不能重複使用最後 5 個 PIN。
- **允許生物識別驗證**。 啟用生物識別驗證 (例如臉部辨識或指紋) 以替代 Windows Hello 企業版的 PIN。 使用者仍然必須設定公司 PIN 以免生物識別驗證失敗。 從下列選項進行選擇：
    - **是**。 Windows Hello 企業版允許生物識別驗證。
    - **否**。 Windows Hello 企業版防止生物識別驗證 (針對所有帳戶類型)。
- **使用增強的防詐騙功能 (如其可用)**。 設定是否在支援 Windows Hello 反詐騙功能的裝置上使用該功能 (例如，偵測臉正面相片而非真正的臉孔)。<br>如果這設為 **[是]**，Windows 即要求所有使用者在支援的情況下，使用臉部特徵防詐騙。
- **使用電話登入**。 若此選項設為 [是]，使用者即可使用遠端 Passport 作為桌上型電腦驗證的可攜式配套裝置。 桌上型電腦必須已加入 Azure Active Directory，且配套裝置必須設有 Windows Hello 企業版的 PIN。

## 進一步資訊
如需 Microsoft Passport 的詳細資訊，請參閱 Windows 10 文件中的[指南](https://technet.microsoft.com/library/mt589441.aspx)。



<!--HONumber=Sep16_HO3-->


