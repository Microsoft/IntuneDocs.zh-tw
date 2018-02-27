---
title: "如何建立 Windows 的合規性政策"
titleSuffix: Azure portal
description: "了解如何為 Windows 裝置建立合規性政策。"
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 2/13/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fe5a66ca91181d0cebdaea846f0ee08f9252d76b
ms.sourcegitcommit: 754fcc31155b28d6910bba45419c6be745f8793e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="how-to-create-a-device-compliance-policy-for-windows-devices-in-intune"></a>如何在 Intune 中為 Windows 裝置建立裝置合規性政策


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

每個平台都會建立合規性政策。 您可以在 Azure 入口網站中建立合規性政策。 如需深入了解什麼是合規性政策，請參閱[什麼是裝置合規性](device-compliance.md)主題。 如需了解建立合規性政策之前必須滿足的先決條件，請參閱[裝置合規性入門](device-compliance-get-started.md)主題。

下表描述搭配使用合規性政策與條件式存取原則時，不相容設定的管理方式。

---------------------------

| **原則設定** | **Windows 8.1 及更新版本** | **Windows Phone 8.1 及更新版本** |
|----| ----| --- |
| **PIN 或密碼設定** | 已修復 | 已修復 |   
| **裝置加密** | 不適用 | 已修復 |   
| **已越獄或 Root 的裝置** | 不適用 | 不適用 |  
| **電子郵件設定檔** | 不適用 | 不適用 |   
| **最低 OS 版本** | 已隔離 | 已隔離 |   
| **最高 OS 版本** | 已隔離 | 已隔離 |   
| **Windows 健康情況證明** | 已隔離：Windows 10 和 Windows 10 行動裝置版|不適用：Windows 8.1 |

-------------------------------

**已補救** = 裝置作業系統強制符合規範。 (例如強制使用者設定 PIN 碼)。

**已隔離** = 裝置作業系統不強制符合規範。 (例如，Android 裝置不強制使用者為裝置加密。)裝置不相容時，會採取下列動作︰

- 如果對使用者套用了條件式存取原則，裝置會遭到封鎖。
- 公司入口網站會通知使用者任何合規性問題的相關事項。

## <a name="create-a-compliance-policy-in-the-azure-portal"></a>在 Azure 入口網站中建立合規性政策

1. 從 **Intune** 刀鋒視窗中，選擇 [設定裝置合規性]。 在 [管理] 中選擇 [All device compliance policies]\(所有裝置合規性政策) 及 [建立]。
2. 輸入名稱及描述，然後選擇要套用此原則的平台。
3. 選擇 [合規性需求]，以開啟 [合規性需求] 刀鋒視窗。  您可以在此指定 [安全性]、[裝置健全狀況] 及 [裝置屬性]，設定完成後，請選擇 [確定]。

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** blade, choose **Add** to create a new action.  The action parameters blade allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="assign-user-groups"></a>指派使用者群組

若要將合規性政策指派給使用者，請選擇您先前設定的原則。 現有的原則可以在 [合規性 - 政策] 刀鋒視窗中找到。

1. 選擇您想要指派給使用者的原則，然後選擇 [指派]。 這會開啟刀鋒視窗讓您從中選取 [Azure Active Directory 安全性群組]，並將其指派給原則。
2. 選擇 [選取群組] 會開啟刀鋒視窗顯示 Azure AD 安全性群組。  選擇 [選取] 會將原則部署給使用者。

您已對使用者套用此原則。 要套用原則之使用者的裝置將會接受合規性評估。

<!---## Compliance policy settings--->

## <a name="system-security-settings"></a>系統安全性設定

### <a name="password"></a>密碼

- **需要密碼來解除鎖定行動裝置︰**將此設定為 [是]，以要求使用者在存取他們的裝置前輸入密碼。
- **允許簡單密碼**︰將此項目設定為 [是] 可允許使用者建立簡單密碼，例如 **1234** 或 **1111**。
- **最小密碼長度**：指定使用者密碼中至少須包含的數字位數或字元數。
- **必要的密碼類型：**指定使用者是否必須建立**英數**或**數值**密碼。

對於執行 Windows 並使用 Microsoft 帳戶存取的裝置，若密碼長度下限超過八個字元，或字元集數目下限大於二，合規性政策將無法正確進行評估。

- **字元集數目下限**：若將 [需要的密碼類型] 設定為 [英數字元]，則此設定可指定密碼至少須包含的最少字元集數。 四個字元集為：
  - 小寫字母
  - 大寫字母
  - 符號
  - 數字

若要將此設定設為較高的數目，使用者必須建立更複雜的密碼。 對於執行 Windows 並使用 Microsoft 帳戶存取的裝置，若密碼長度下限超過八個字元，或字元集數目下限大於二，合規性政策將無法正確進行評估。

- **停止活動幾分鐘後需要輸入密碼**：指定閒置多久後使用者必須重新輸入密碼。
- **密碼到期 (天數)**：選取使用者密碼到期，必須建立新密碼前的天數。
- **記住密碼歷程記錄：**此設定請與 [不得重複使用以前用過的密碼] 一起使用，以限制使用者建立以前用過的密碼。
- **不得重複使用以前用過的密碼：**如果已選取 [記住密碼歷程記錄]，請指定不得重複使用的舊密碼數目。
- **當裝置從閒置狀態返回時，需要密碼：**這項設定應該與 [在非使用狀態幾分鐘後需要輸入密碼] 設定一起使用。 系統會提示使用者輸入密碼，來存取 [在非使用狀態幾分鐘後需要輸入密碼] 設定所指定時間未作用的裝置。

**這項設定只適用於 Windows 10 行動裝置版裝置。**

### <a name="encryption"></a>加密

- **行動裝置需要加密︰將此**設為 [是]，以要求裝置加密才能連線到資源。



## <a name="device-health-settings"></a>裝置健全狀況設定

- **需要裝置回報為狀況良好：**您可以設定規則，要求在新的或現有的合規性政策中，**Windows 10 Mobile** 裝置必須回報為狀況良好。 如有啟用此設定，將會透過健全情況證明服務 (HAS) 在下列資料點時評估 Windows 10 裝置︰
  - **啟用 BitLocker：**如果開啟 BitLocker，則系統已關閉或進入休眠時，裝置可以保護磁碟機上所儲存的資料不受未經授權地存取。 Windows BitLocker 磁碟機加密會加密儲存在 Windows 作業系統磁碟區上的所有資料。 BitLocker 使用 TPM 來協助保護 Windows 作業系統和使用者資料，並可協助確保電腦即使無人看管、遺失或遭竊，也不會遭到竄改。 如果電腦配備相容的 TPM，BitLocker 會使用 TPM 來鎖定可保護資料的加密金鑰。 因此，除非 TPM 驗證電腦的狀態，否則無法存取金鑰
  - **啟用程式碼完整性：**程式碼完整性是一種功能，可在每次將驅動程式或系統檔案載入記憶體時驗證其完整性。 程式碼完整性會偵測是否將未簽署的驅動程式或系統檔案載入到核心；或者，以具有系統管理員權限的使用者帳戶所執行的惡意軟體是否已修改系統檔案。
  - **啟用安全開機：**啟用安全開機時，強迫系統開機到原廠信任狀態。 此外，啟用安全開機時，用來啟動電腦的核心元件必須具有製造裝置之組織所信任的正確密碼編譯簽章。 UEFI 韌體會在讓電腦啟動之前先驗證此簽章。 如果有任何檔案已遭竄改 (即中斷其簽章)，則無法啟動系統。

如需 HAS 服務運作方式的資訊，請參閱 [Health Attestation CSP (健全情況證明 CSP)](https://msdn.microsoft.com/library/dn934876.aspx)。

## <a name="device-property-settings"></a>裝置屬性設定

- **最低作業系統版本需求︰**當裝置不符合最低作業系統版本需求時，它會回報為不相容。 會顯示如何升級的資訊連結。 終端使用者可以選擇升級其裝置，之後便可以存取公司資源。
- **允許的最高作業系統版本：**當裝置使用的作業系統版本高於規則指定的版本時，會封鎖對公司資源的存取，並要求使用者連絡其 IT 管理員。在將規則變更為允許該 OS 版本之前，此裝置無法用來存取公司資源。

<!---## Compliance policy settings for Windows PCs--->

## <a name="system-security-settings"></a>系統安全性設定

### <a name="password"></a>密碼

- **密碼長度下限︰** - Windows 8.1 上支援。

指定使用者密碼中至少須包含的數字位數或字元數。

對於使用 Microsoft 帳戶存取的裝置，若 [密碼長度下限] 超過八個字元，或 [字元集數目下限] 大於兩個字元，相容性原則將無法正確進行評估。

- **需要的密碼類型**︰Windows RT、Windows RT 8.1 及 Windows 8.1 支援此設定

指定使用者必須建立**英數字元**或**數字**密碼。

- **字元集數目下限**︰Windows RT、Windows RT 8.1 及 Windows 8.1 支援此設定。 若將 [必要的密碼類型] 設為 [英數字元]，此設定即會指定密碼至少須包含的字元集數下限。 四個字元集為：
  - 小寫字母
  - 大寫字母
  - 符號
  - 數字：若要將此設定設為較高的數目，使用者必須建立更複雜的密碼。

對於使用 Microsoft 帳戶存取的裝置，若 [密碼長度下限] 超過八個字元，或 [字元集數目下限] 大於兩個字元，相容性原則將無法正確進行評估。

- **要求密碼前的閒置分鐘數︰** - Windows RT、Windows RT 8.1 和 Windows 8.1 上支援

指定使用者必須重新輸入密碼之前的閒置時間。

- **密碼到期 (天數)**︰Windows RT、Windows RT 8.1 及 Windows 8.1 支援此設定。

選取使用者密碼到期，必須建立新密碼前的天數。

- **所需的密碼歷程記錄︰** - Windows RT、Windows RT 和 Windows 8.1 上支援。

共同使用此設定與 [不得重複使用以前用過的密碼] 可限制建立先前使用過的密碼。

- **不得重複使用以前用過的密碼︰** - Windows RT、Windows RT 8.1 和 Windows 8.1 上支援

若選取 [記住密碼歷程記錄]，必須指定不得重複使用的舊密碼數。


## <a name="device-health-settings"></a>裝置健全狀況設定

- **需要裝置回報為狀況良好︰** - Windows 10 裝置上支援。 您可以設定規則，要求在新的或現有的合規性政策中，Windows 10 裝置必須回報為狀況良好。 如有啟用此設定，將會透過健全情況證明服務 (HAS) 在下列資料點時評估 Windows 10 裝置︰
  - **啟用 BitLocker：**如果開啟 BitLocker，則系統已關閉或進入休眠時，裝置可以保護磁碟機上所儲存的資料不受未經授權地存取。 Windows BitLocker 磁碟機加密會加密儲存在 Windows 作業系統磁碟區上的所有資料。 BitLocker 使用 TPM 來協助保護 Windows 作業系統和使用者資料，並可協助確保電腦即使無人看管、遺失或遭竊，也不會遭到竄改。 如果電腦配備相容的 TPM，BitLocker 會使用 TPM 來鎖定可保護資料的加密金鑰。 因此，除非 TPM 驗證電腦的狀態，否則無法存取金鑰
  - **啟用程式碼完整性：**程式碼完整性是一種功能，可在每次將驅動程式或系統檔案載入記憶體時驗證其完整性。 程式碼完整性會偵測是否將未簽署的驅動程式或系統檔案載入到核心；或者，以具有系統管理員權限的使用者帳戶所執行的惡意軟體是否已修改系統檔案。
  - **啟用安全開機：**啟用安全開機時，強迫系統開機到原廠信任狀態。 此外，啟用安全開機時，用來啟動電腦的核心元件必須具有製造裝置之組織所信任的正確密碼編譯簽章。 UEFI 韌體會在讓電腦啟動之前先驗證此簽章。 如果有任何檔案已遭竄改 (即中斷其簽章)，則無法啟動系統。
  - **啟用早期啟動反惡意程式碼：**早期啟動反惡意程式碼 (ELAM) 可在啟動電腦時，以及協力廠商驅動程式初始化之前，保護網路中的電腦。

如需 HAS 服務運作方式的資訊，請參閱 [Health Attestation CSP (健全情況證明 CSP)](https://msdn.microsoft.com/library/dn934876.aspx)。

## <a name="device-property-settings"></a>裝置屬性設定

- **所需的 OS 下限︰** - Windows 8.1 和 Windows 10 上支援。

在此指定 major.minor.build 數目。 此版本號碼與 ```winver``` 命令傳回的版本必須一致。

若裝置上的 OS 版本較指定版本舊，會將其回報為不相容。 會顯示如何升級的資訊連結。 終端使用者可以選擇升級其裝置，之後便可以存取公司資源。

- **允許的最高 OS 版本︰** - Windows 8.1 和 Windows 10 上支援。

當裝置使用的 OS 版本晚於規則中所指定的版本時，系統便會封鎖對公司資源的存取權，並要求使用者連絡其 IT 管理員。在將規則變更為允許該 OS 版本之前，此裝置無法用來存取公司資源。

若要尋找要用於**所需的 OS 下限**和**允許的最高 OS 版本**設定的 OS 版本，請從命令提示字元執行 **winver** 命令。 winver 命令會傳回回報的 OS 版本。

- Windows 8.1 電腦會傳回版本 **3**。 如果 Windows 的 OS 版本規則設為 Windows 8.1，則即使裝置具有 Windows 8.1，還是會回報為不相容。
- 執行 Windows 10 之電腦的版本應設定為 &quot;10.0&quot;+ winver 命令傳回的 OS 組建編號。

## <a name="windows-holographic-for-business-support"></a>Windows Holographic for Business 支援

Windows Holographic for Business 支援下列設定：

- 系統安全性/加密

  **裝置上資料儲存的加密**。

若要在 Microsoft HoloLens 上驗證裝置加密，請參閱[驗證裝置加密](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption)。

## <a name="next-steps"></a>接下來的步驟

請參閱下列主題來了解如何監視裝置合規性：

- [如何監視裝置合規性](device-compliance-monitor.md)
