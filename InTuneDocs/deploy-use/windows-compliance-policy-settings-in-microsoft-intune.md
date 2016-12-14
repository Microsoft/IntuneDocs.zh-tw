---
title: "Windows 裝置的相容性原則設定| Microsoft Intune"
description: "本主題說明您能為 Windows 裝置之相容性原則設定的規則與設定。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f996842c-e9a4-4819-acb4-ee66e8fb35b8
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d6ff74f0b46baf384dbdedf13ad75538dd33a089
ms.openlocfilehash: e079fea47a10296067fe82fc05d82f0a863ae7bd


---

# <a name="compliance-policy-settings-for-windows-devices-in-microsoft-intune"></a>Microsoft Intune 中 Windows 裝置的相容性原則設定

本主題中所述的原則設定適用於執行 Windows 作業系統的裝置。 下列各節說明支援的 Windows 版本。

如果您正在尋找其他平台的相關資訊，請選取下列其中一項︰
> [!div class="op_single_selector"]
- [iOS 裝置的法務遵循政策設定](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Android 裝置的法務遵循政策設定](android-compliance-policy-settings-in-microsoft-intune.md)
- [Android for Work 的法務遵循政策設定](afw-compliance-policy-settings-in-microsoft-intune.md)

## <a name="compliance-policy-settings-for-windows-phone-devices"></a>Windows Phone 裝置的相容性原則設定
Windows Phone 8.1 及更新版本支援這一節所列的設定。

### <a name="system-security-settings"></a>系統安全性設定
#### <a name="password"></a>密碼
- **需要密碼來解除鎖定行動裝置**︰將此設為 [是] 以要求使用者在存取他們的裝置前輸入密碼。

- **允許簡單密碼**︰將此設為 [是]，讓使用者建立簡單密碼，例如 **1234** 或 **1111**。

-  **密碼長度下限**：指定使用者密碼中至少必須含有的數字位數或字元數。
- **必要的密碼類型**：指定使用者是否必須建立**英數**密碼或**數值**密碼。

  對於執行 Windows 並使用 Microsoft 帳戶存取的裝置，若密碼長度下限超過八個字元，或字元集數目下限大於二，相容性原則將無法正確進行評估。

- **字元集數目下限：**如果**必要的密碼類型**設定為**英數**，則此設定可指定密碼至少必須包含的字元集數目下限。 四個字元集為：
  -   小寫字母
  -   大寫字母
  -   符號
  -   數字

  此設定的數值若設得較高，使用者就必須建立較複雜的密碼。 對於執行 Windows 並使用 Microsoft 帳戶存取的裝置，若密碼長度下限超過八個字元，或字元集數目下限大於二，相容性原則將無法正確進行評估。

- **要求密碼前的閒置分鐘數：**此設定指定使用者必須重新輸入密碼之前的閒置時間。

- **密碼到期天數**：選擇使用者在經過多少天數之後密碼到期，並必須建立新的密碼。

- **記住密碼歷程記錄**：此設定請與 [不得重複使用以前用過的密碼] 一起使用，以限制使用者建立以前用過的密碼。

- **不得重複使用以前用過的密碼：**如果已選取 [記住密碼歷程記錄]，請指定不得重複使用的舊密碼數目。
- **當裝置從閒置狀態返回時，需要密碼**：請搭配使用這項設定與 [在非使用狀態幾分鐘後需要輸入密碼] 設定。 如果裝置達到 [在非使用狀態幾分鐘後需要輸入密碼] 設定所指定的閒置時間，系統會提示使用者輸入密碼，才能存取該裝置。

  > [!NOTE]
  > 這項設定只適用於 Windows 10 行動裝置版裝置。

#### <a name="encryption"></a>加密
- **行動裝置需要加密︰將此**設為 [是]，要求裝置加密才能連線到資源。

### <a name="device-health-settings"></a>裝置健全狀況設定
- **需要裝置回報為狀況良好：**您可以設定規則，要求在新的或現有的相容性原則中，**Windows 10 行動裝置版**裝置必須回報為狀況良好。  如果啟用這項設定，則會針對這些資料點，透過健全情況證明服務 (HAS) 評估 Windows 10 裝置︰
  -  **啟用 BitLocker：**如果開啟 BitLocker，則系統已關閉或進入休眠時，裝置可以保護磁碟機上所儲存的資料不受未經授權地存取。 Windows BitLocker 磁碟機加密會加密儲存在 Windows 作業系統磁碟區上的所有資料。 BitLocker 使用 TPM 協助保護 Windows 作業系統和使用者資料。 BitLocker 也有助於確保電腦在無人看管、遺失或遭竊的情況下，不遭竄改。 如果電腦配備相容的 TPM，BitLocker 會使用 TPM 來鎖定有利保護資料的加密金鑰。 因此，除非 TPM 驗證電腦的狀態，否則無法存取金鑰。
  -  **啟用程式碼完整性：**程式碼完整性是一種功能，可在每次將驅動程式或系統檔案載入記憶體時驗證其完整性。 程式碼完整性會偵測核心是否正在載入未簽署的驅動程式或系統檔案。 它也會偵測是否有具系統管理員權限的使用者帳戶，執行惡意軟體以修改系統檔案。
  - **啟用安全開機：**啟用安全開機時，強迫系統開機到原廠信任狀態。 此外，啟用安全開機時，用來啟動電腦的核心元件必須具有製造裝置之組織所信任的正確密碼編譯簽章。 UEFI 韌體會先驗證這項作業，再啟動電腦。 如果有任何檔案已遭竄改 (即中斷其簽章)，則無法啟動系統。

  如需 HAS 服務運作方式的資訊，請參閱 [Health Attestation CSP (健全情況證明 CSP)](https://msdn.microsoft.com/library/dn934876.aspx)。
###  <a name="device-property-settings"></a>裝置屬性設定
- **最低作業系統版本需求**︰當裝置不符合最低作業系統版本需求時，它會回報為不相容。
    會顯示如何升級的資訊連結。 使用者可以選擇升級其裝置，之後便可以存取公司資源。

- **允許的最高作業系統版本**：當裝置使用的作業系統版本高於規則指定的版本時，會封鎖對公司資源的存取，並要求使用者連絡其 IT 系統管理員。 在將規則變更為允許該 OS 版本之前，此裝置無法用來存取公司資源。


## <a name="compliance-policy-settings-for-windows-pcs"></a>Windows 電腦的相容性原則設定
Windows 電腦支援這一節所列的設定。
### <a name="system-security-settings"></a>系統安全性設定
#### <a name="password"></a>密碼
- **密碼長度下限︰**Windows 8.1 上支援。

  指定使用者密碼中至少必須具有的數字位數或字元數。

  對於使用 Microsoft 帳戶存取的裝置，若 [密碼長度下限] 超過八個字元，或 [字元集數目下限] 大於兩個字元，相容性原則將無法正確進行評估。

- **所需的密碼類型︰**Windows RT、Windows RT 8.1 和 Windows 8.1 上支援。

  指定使用者是否必須建立**英數**密碼或**數值**密碼。

- **字元集數目下限︰**Windows RT、Windows RT 8.1 和 Windows 8.1 上支援。

  若將 [必要的密碼類型] 設為 [英數字元]，此設定即會指定密碼至少須具有的字元集數下限。 四個字元集為：
  -   小寫字母
  -   大寫字母
  -   符號
  -   數字     

  此設定的數值若設得較高，使用者就必須建立較複雜的密碼。 對於使用 Microsoft 帳戶存取的裝置，若 [密碼長度下限] 超過八個字元，或 [字元集數目下限] 大於兩個字元，相容性原則將無法正確進行評估。

- **要求密碼前的閒置分鐘數︰**Windows RT、Windows RT 8.1 和 Windows 8.1 上支援。

  指定使用者必須重新輸入密碼之前的閒置時間。

- **密碼到期 (天數)**︰Windows RT、Windows RT 8.1 和 Windows 8.1 上支援。

  選擇使用者密碼到期，必須建立新密碼的天數。

- **記住密碼歷程記錄**︰Windows RT、Windows RT 和 Windows 8.1 上支援。

  共同使用此設定與 [不得重複使用以前用過的密碼] 可限制建立先前使用過的密碼。

- **不得重複使用以前用過的密碼︰**Windows RT、Windows RT 8.1 和 Windows 8.1 上支援。

  若選取 [記住密碼歷程記錄]，必須指定不得重複使用的舊密碼數。

### <a name="device-health-settings"></a>裝置健全狀況設定
- **需要裝置回報為狀況良好︰**Windows 10 裝置上支援。
您可以設定規則，要求在新的或現有的相容性原則中，Windows 10 裝置必須回報為狀況良好。 如果啟用這項設定，則會針對這些資料點，透過健全情況證明服務 (HAS) 評估 Windows 10 裝置︰
  -  **啟用 BitLocker：**如果開啟 BitLocker，則系統已關閉或進入休眠時，裝置可以保護磁碟機上所儲存的資料不受未經授權地存取。 Windows BitLocker 磁碟機加密會加密儲存在 Windows 作業系統磁碟區上的所有資料。 BitLocker 使用 TPM 協助保護 Windows 作業系統和使用者資料。 BitLocker 也有助於確保電腦在無人看管、遺失或遭竊的情況下，不遭竄改。 如果電腦配備相容的 TPM，BitLocker 會使用 TPM 來鎖定有利保護資料的加密金鑰。 因此，除非 TPM 驗證電腦的狀態，否則無法存取金鑰。
  -  **啟用程式碼完整性：**程式碼完整性是一種功能，可在每次將驅動程式或系統檔案載入記憶體時驗證其完整性。 程式碼完整性會偵測核心是否正在載入未簽署的驅動程式或系統檔案。 它也會偵測是否有具系統管理員權限的使用者帳戶，執行惡意軟體以修改系統檔案。
  - **啟用安全開機：**啟用安全開機時，強迫系統開機到原廠信任狀態。 此外，啟用安全開機時，用來啟動電腦的核心元件必須具有製造裝置之組織所信任的正確密碼編譯簽章。 UEFI 韌體會先驗證這項作業，再啟動電腦。 如果有任何檔案已遭竄改 (即中斷其簽章)，則無法啟動系統。
  - **啟用早期啟動反惡意程式碼：**早期啟動反惡意程式碼 (ELAM) 可在啟動電腦時，以及協力廠商驅動程式初始化之前，保護網路中的電腦。

  如需 HAS 服務運作方式的資訊，請參閱 [Health Attestation CSP (健全情況證明 CSP)](https://msdn.microsoft.com/library/dn934876.aspx)。

### <a name="device-property-settings"></a>裝置屬性設定
- **所需的 OS 下限︰**Windows 8.1 和 Windows 10 上支援。

  在此指定 major.minor.build 數目。 版本號碼必須對應至 **winver** 命令所傳回的版本。

  當裝置版本比指定的作業系統版本更早時，就會回報為不相容。 會顯示如何升級的資訊連結。 使用者可以選擇升級其裝置，之後便可以存取公司資源。

- **允許的最高 OS 版本︰**Windows 8.1 和 Windows 10 上支援。

  當裝置使用的 OS 版本晚於規則中所指定的版本時，系統便會封鎖對公司資源的存取權，並要求使用者連絡其 IT 管理員。 在將規則變更為允許該 OS 版本之前，此裝置無法用來存取公司資源。

若要尋找要用於 [Minimum OS required] (所需的 OS 下限)和 [Maximum OS version allowed] (允許的最高 OS 版本) 設定的 OS 版本，請從命令提示字元執行 **winver** 命令。 **winver** 命令會傳回 OS 的回報版本。

- Windows 8.1 電腦會傳回 **6.3** 版。 如果 Windows 的 OS 版本規則設為 Windows 8.1，則即使裝置具有 Windows 8.1，還是會回報為不相容。

- 執行 Windows 10 的電腦，其版本應該設為 **10.0** 加上 **winver** 命令所傳回的作業系統組建編號。 例如，可能類似於 10.0.10586。
> ![[關於 Windows] 對話方塊會反白顯示作業系統組建版本](./media/ca_win10-os-version.png)



<!--HONumber=Dec16_HO2-->


