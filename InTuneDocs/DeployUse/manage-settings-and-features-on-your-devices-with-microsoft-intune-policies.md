---
title: "透過原則管理裝置設定 | Microsoft Intune"
description: "使用 Intune 建立和部署原則，控制您所管理之已註冊裝置上的設定和功能。"
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 09bae0b9-4f79-4658-8ca1-a71ab992c1b2
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6716a3d1fb53dc3de0189f637d5664d0a2023d05
ms.openlocfilehash: 70b980c045d8d37aa4ea5bee5858c0c728d54114


---

# 透過 Microsoft Intune 原則管理裝置上的設定和功能
Microsoft Intune *原則*是控制行動裝置和電腦功能的設定群組。 您可以使用包含建議或自訂設定的範本建立原則，然後將原則部署到裝置或使用者群組。

## 原則類型

Intune 原則可分為以下類別。 您使用的類別會影響您建立和部署原則的方式。


- [設定原則]︰這些原則通常用來管理您裝置的安全性設定和功能。 使用本主題中的資訊來了解如何建立及部署這些原則，以及瀏覽可用的設定。
- [裝置相容性原則]：這些原則定義裝置必須符合才能被條件式存取原則視為相容的規則與設定。 您也可以使用相容性原則，來監視和修復與條件式存取無關的裝置相容性。
如需詳細資訊，請參閱 [Microsoft Intune 的裝置相容性原則](introduction-to-device-compliance-policies-in-microsoft-intune.md)。
- [條件式存取原則]：這些原則可協助您依據指定的條件保護電子郵件及其他服務。
如需詳細資訊，請參閱[使用 Microsoft Intune 限制電子郵件和 O365 服務的存取](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)。
- [公司裝置註冊原則]：如需公司裝置註冊原則的資訊，請參閱[使用 Microsoft Intune 設定 iOS 和 Mac 管理](set-up-ios-and-mac-management-with-microsoft-intune.md)。
- [資源存取原則]：搭配使用這些原則，可協助您的使用者隨時隨地都能存取順利完成其工作所需的檔案及資源。
如需詳細資訊，請參閱[使用 Microsoft Intune 存取公司資源](enable-access-to-company-resources-with-microsoft-intune.md)。


如需 Intune 原則的完整清單，請參閱 [Microsoft Intune 原則參考](microsoft-intune-policy-reference.md)。




## 建立設定原則

1.  在 [Microsoft Intune 管理主控台][](https://manage.microsoft.com/)中，選擇**原則**&gt;**設定原則**&gt;**新增**。

2.  選擇您想要的原則，然後選擇使用原則的建議設定 (如果有；稍後可變更這些設定)，或者選擇使用您自己的設定來建立自訂原則。

    > [!TIP]
    > 如需選擇正確原則的說明，請參閱 [Microsoft Intune 原則參考](microsoft-intune-policy-reference.md)。

3.  當您準備好時，選擇 [建立原則]。

4.  在 [建立原則] 頁面上，設定原則的名稱和選擇性描述。

5.  設定必要的原則設定，然後選擇 [儲存原則]。

    如果您需要的任何原則設定的協助，請從下列清單選擇原則類型︰

    - [iOS 裝置的設定](ios-policy-settings-in-microsoft-intune.md)
    - [Android 裝置的設定](android-policy-settings-in-microsoft-intune.md)
    - [Windows 8 和 Windows 8.1 裝置的設定](windows-configuration-policy-settings-in-microsoft-intune.md)
    - [Windows Phone 8.1 裝置的設定](windows-phone-8-1-policy-settings-in-microsoft-intune.md)
    - [Windows 10 桌上型電腦和行動裝置的設定](windows-10-policy-settings-in-microsoft-intune.md)
    - [Windows Team 裝置的設定](windows-team-configuration-policy-settings-in-microsoft-intune.md)
    - [Windows 版本升級的設定](edition-upgrade-policy-settings-in-microsoft-intune.md)
    - [Mac OS X 裝置的設定](mac-os-x-policy-settings-in-microsoft-intune.md)
    - [Exchange ActiveSync 的設定](exchange-activesync-policy-settings-in-microsoft-intune.md)
    - [條款和條件原則的設定](terms-and-condition-policy-settings-in-microsoft-intune.md)
    - [行動裝置的一般設定 (舊版)](mobile-device-security-policy-settings-in-microsoft-intune.md)

4.  在確認對話方塊中，選擇 [是] 立即部署原則，或選擇 [否] 建立原則但不加以部署。

您可以瀏覽 [原則] 工作區中每種原則類型的各個區段，以檢視及編輯新的原則。

當您建立使用建議設定的原則時，新原則的名稱是由範本名稱、日期和時間組合而成。 當您編輯原則時，會以編輯的時間和日期更新名稱。

建立原則之後，您通常需要將它部署到一或多個使用者或裝置群組。

> [!TIP]
> 您不會部署所有原則類型。 例如，您不會部署行動應用程式管理 (MAM) 原則。 這種原則類型會先與應用程式建立關聯，再由您部署應用程式。

## 部署組態原則

1.  在 [原則] 工作區中，選取您要部署的原則，然後選擇 [管理部署]。

2.  在 [管理部署]  對話方塊中：

    -   若要部署原則，選取您要部署原則的一或多個群組，然後選擇 [新增] &gt; [確定]。

    -   若要關閉對話方塊而不部署原則，選擇 [取消]。

當您選取某項已部署的原則時，您可以在原則清單下方檢視有關部署的進一步資訊。

## 管理原則

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com/)中，選擇 [原則]，然後瀏覽至您要管理的原則並加以選取。

2.  選取下列其中一個動作：

- [編輯]：開啟所選原則的內容讓您進行變更。
- [刪除]：刪除選取的原則。<br>當您刪除原則時，會從部署該原則的所有群組移除它。
- [管理部署]：選取您要部署原則的群組，然後選擇 [新增]。


## Intune 原則常見問題

### 部署原則或應用程式之後，行動裝置需要多久時間才能取得這些原則或應用程式？
部署原則或應用程式後，Intune 會立即開始嘗試通知裝置，指出裝置應該簽入 Intune 服務。 這通常只需要不到 5 分鐘的時間。

如果在送出第一個通知之後，裝置未簽入以取得原則，Intune 還會另外嘗試三次。  如果裝置處於離線狀態 (例如已關閉或未連線到網路)，則可能不會收到通知。 在這種情況下，裝置會在其下次排定簽入 Intune 服務的時間取得原則，如下所示：

- iOS 和 Mac OS X：每 6 小時。
- Android：每 8 小時。
- Windows Phone：每 8 小時。
- 註冊的 Windows RT 裝置：每 24 小時。
- 註冊為裝置的 Windows 8.1 和 Windows 10 電腦：每 8 小時。

如果裝置剛註冊，簽入頻率會更頻繁，如下所示：

- iOS 和 Mac OS X：前 6 小時每 15 分鐘，之後每 6 小時。
- Android：前 15 分鐘每 3 分鐘，之後 2 小時每 15 分鐘，再來每 8 小時。
- Windows Phone：前 15 分鐘每 5 分鐘，之後 2 小時每 15 分鐘，再來每 8 小時。
- Windows 電腦註冊為裝置：前 30 分鐘每 3 分鐘，之後每 8 小時。

使用者也可以開啟公司入口網站應用程式並同步處理裝置，以隨時立即檢查是否有原則。

### 哪些動作會導致 Intune 立即傳送通知給裝置？
裝置可在收到簽入通知時簽入 Intune，或在它們的排定簽入時間定期簽入。  當您想要對目標裝置或使用者執行抹除、鎖定、密碼重設、應用程式部署、設定檔部署 (Wi-Fi、VPN、電子郵件等) 或原則部署等特定動作時，Intune 會立即開始嘗試通知裝置，指出裝置應該簽入 Intune 服務才能接收這些更新。

修訂公司入口網站中的連絡資訊等其他變更，則不會對裝置傳送立即通知。

> [!TIP]
> 包含設定的原則部署到 Android 裝置時，系統會提示使用者，採取動作以符合此原則。 在使用者採取此動作，或重新啟動裝置之前，新的原則設定不會生效。

### 如果有多項原則部署到同一位使用者或同一部裝置，如何得知將套用哪些設定？
請注意，當有兩項或多項原則部署到同一位使用者或同一部裝置時，會在個別的設定層級評估要套用哪項設定：

-   相容性原則設定一律優先於設定原則設定。

-   如果與不同相容性原則中的相同設定一起評估，則會套用限制最嚴格的相容性原則設定。

-   如果設定原則的設定與不同設定原則中的設定衝突，這項衝突會顯示在 Intune 主控台中。 您必須以手動方式解決此類衝突。

### 當行動應用程式管理原則彼此衝突時，會發生什麼情況？ 哪一項原則會套用至應用程式？
除了數字輸入欄位 (例如重設前的 PIN 嘗試次數) 之外，衝突值是 MAM 原則中限制最嚴格的設定。  數字輸入欄位會設定為相同的值，如同您在主控台中使用建議的設定選項建立 MAM 原則一樣。

當兩項原則設定相同時，就會發生衝突。  例如，您設定了兩項 MAM 原則，其中除了複製/貼上設定之外，這兩項原則完全相同。  在這種情況下，複製/貼上設定會設定為限制最嚴格的值，但其餘設定則會依照設定來套用。

如果其中一項原則部署到應用程式並生效，然後再部署第二項原則，則會優先使用並持續套用第一項原則，而第二項原則會顯示為衝突的原則。 如果同時套用這兩項原則，代表沒有優先的原則，則兩者皆處於衝突狀態。 任何衝突的設定將設為限制最嚴格的值。

### iOS 自訂原則衝突時，會發生什麼情況？
Intune 不會評估 Apple 組態檔或自訂 OMA-URI 原則的承載。 它只做為傳遞機制。

當您部署自訂原則時，請確定所進行的設定未與相容性、組態或其他自訂原則衝突。 如果自訂原則與設定衝突，則會依隨機順序來套用設定。

### 當原則已刪除或不再適用時，會發生什麼情況？
當您刪除原則，或從群組中移除已經部署原則的裝置時，將會依照以下清單，從裝置移除該原則及設定。

#### 已註冊的裝置

- Wi-Fi、VPN、憑證及電子郵件設定檔：這些設定檔會從所有支援的已註冊裝置中移除。
- 所有其他原則類型：
    - [Windows 和 Android 裝置]：設定不會從裝置中移除。
    - [Windows Phone 8.1 裝置]：會移除下列設定：
        - 需要密碼來解除鎖定行動裝置
        - 允許簡單密碼
        - 最小密碼長度
        - 所需的密碼類型
        - 密碼到期 (天數)
        - 記住密碼歷程記錄
        - 抹除裝置前允許的重複登入失敗次數
        - 要求密碼前的閒置分鐘數
        - 需要的密碼類型 – 最小字元集數
        - 允許相機
        - 在行動裝置上要求加密
        - 允許卸除式存放裝置
        - 允許網頁瀏覽器
        - 允許應用程式市集
        - 允許螢幕擷取
        - 允許地理位置
        - 允許 Microsoft 帳戶
        - 允許複製並貼上
        - 允許 Wi-Fi 網際網路共用功能
        - 允許自動連線到免費的 Wi-Fi 熱點
        - 允許 Wi-Fi 熱點回報
        - 允許原廠重設
        - 允許藍芽
        - 允許 NFC
        - 允許 Wi-Fi

    - [iOS]：移除所有設定，除了︰
        - 允許語音漫遊
        - 允許數據漫遊
        - 允許漫遊時自動同步處理

#### 執行 Intune 用戶端軟體的 Windows 電腦

- [Endpoint Protection 設定]：設定會還原回其建議值。 唯一例外是 [加入 Microsoft Active Protection Service] 設定，其預設值為 [否]。 如需詳細資訊，請參閱[使用 Microsoft Intune 的 Endpoint Protection 協助保護 Windows 電腦](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)。
- [軟體更新設定]：設定會重設為作業系統的預設狀態。 如需詳細資訊，請參閱[在 Microsoft Intune 中使用軟體更新讓 Windows 電腦維持最新狀態](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)。
- [Microsoft Intune Center 設定]：由原則設定的任何支援連絡資訊都會從電腦刪除。
- [Windows 防火牆設定]：設定會重設為電腦作業系統的預設值。 如需詳細資訊，請參閱[使用 Microsoft Intune 的 Endpoint Protection 協助保護 Windows 電腦](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)。


### 我該如何重新整理裝置上的原則，以確保它們為最新狀態 (僅適用於執行 Intune 用戶端軟體的 Windows 電腦)？

1.  在任何裝置群組中，選取您要重新整理原則的裝置，然後選擇 [遠端工作] &gt; [重新整理原則]。
2.  選擇 Intune 管理主控台右下角的 [遠端工作] 以檢查工作狀態。

### 哪裡可以找到疑難排解原則的說明？

請參閱[Microsoft Intune 的原則疑難排解](/intune/troubleshoot/troubleshoot-policies-in-microsoft-intune)。



<!--HONumber=Jul16_HO4-->


