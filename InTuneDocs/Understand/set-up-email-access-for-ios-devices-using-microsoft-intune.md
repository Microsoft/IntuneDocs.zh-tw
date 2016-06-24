---
# required metadata

title: 使用 Microsoft Intune 設定 iOS 裝置的電子郵件存取 | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3853673d-290a-400f-8e45-d55e39d42acd

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 使用 Microsoft Intune 設定 iOS 裝置的電子郵件存取
向 Intune 註冊裝置後，您可以設定裝置讓使用者可以存取公司電子郵件。 針對特定裝置類型這麼做的方法之一是建立和部署電子郵件設定檔。 電子郵件設定檔是一種 Intune 原則，可設定使用者的裝置來連線至公司電子郵件服務。
使用電子郵件設定檔可讓已註冊的裝置自動存取電子郵件，不必手動設定裝置。 電子郵件設定檔也可確保所有使用者以相同方式設定存取，且使用相同的基本設定。

## 此逐步解說的目標

- 建立及部署適用於 iOS 裝置的電子郵件設定檔
- 確認已成功套用電子郵件設定檔原則

## 開始本逐步解說之前所需的項目

- Exchange Server，在內部部署或在 Office/E3 訂用帳戶中由 Azure 託管。
- 公司 Exchange 伺服器的主機名稱。 這是完整網域名稱 (FQDN)，例如 contosodemo55.onmicrosoft.com
- 電子郵件設定檔部署的目標使用者群組。 如果您已完成[啟動 Microsoft Intune 試用版和部署 iOS PIN 原則](start-a-microsoft-intune-trial-and-deploy-ios-pin-policy.md)逐步解說，您可以使用已為它建立的 GroupDemo 使用者群組。
- 設定檔部署的已註冊目標 iOS 裝置 同樣地，如果您已完成[啟動 Microsoft Intune 試用版和部署 iOS PIN 原則](start-a-microsoft-intune-trial-and-deploy-ios-pin-policy.md)逐步解說，則您已註冊一些 iOS 裝置。

## 建立及部署適用於 iOS 裝置的電子郵件設定檔的步驟

此逐步解說中，我們將使用試用版訂用帳戶隨附的託管 Exchange 伺服器。
1. 在 Intune 主控台中，按一下 [原則]，然後按一下 [新增原則]
![<add-policy>](./media/Email-Walkthrough/Email-Walkthrough-1.png)
2. 在 [建立新的原則] 對話方塊中，展開 [iOS]，選取 [電子郵件設定檔]，然後按一下 [建立原則]
![<ios-email-profile-policy>](./media/Email-Walkthrough/Email-Walkthrough-2.png)
3. 在 [建立原則] 頁面中，輸入原則名稱 (例如 iOS 電子郵件設定檔 - 使用者密碼) 和描述。 針對不同的裝置類型和不同的驗證方法，您可能有多個電子郵件設定檔，您可以使用名稱來顯示設定檔的用途。
4. 輸入 Exchange 主機名稱。 因為我們使用 Azure 託管的 Exchange 伺服器，所以直接輸入主機名稱︰outlook.office365.com](./media/Email-Walkthrough/Email-Walkthrough-3.png)
5. <add-exchange-host-name> 輸入將顯示給裝置使用者的帳戶名稱，協助他們識別電子郵件服務。
6. 例如，Contoso Email
7. 因為我們以使用者名稱和密碼來驗證 Exchange 服務的使用者，只要保留原本的使用者名稱和密碼設定即可。 調整同步處理設定以符合您的需求。  
8. 現在，除非想要變更特定的預設值，否則都使用預設值即可。
9. 按一下 [儲存原則] 此時會出現對話方塊，詢問您現在是否要部署原則。
![按一下 [是]](./media/Email-Walkthrough/Email-Walkthrough-4.png)
10. <deploy-policy-now-dialog>
![在接著出現的視窗中，選取電子郵件設定檔部署的目標使用者群組，按一下 [新增]新增，然後按一下 [確定]

## <finish-add-policy>

按一下 [確定] 之後，原則在一兩分鐘內會開始流向已註冊的裝置。
1. 確認已成功套用設定檔的步驟
若要確認已套用設定檔，您必須存取其中一個已部署電子郵件設定檔的裝置。
![在 iOS 裝置上，開啟 [郵件] 應用程式。](./media/Email-Walkthrough/Email-Walkthrough-6.png)
2. 應用程式會提示您輸入使用者的電子郵件使用者名稱和密碼。
 <verify-policy-add-password>
![輸入使用者 Exchange 電子郵件帳戶的使用者名稱和密碼，然後點選 [確定]](./media/Email-Walkthrough/Email-Walkthrough-7.png)
3. 將以 Exchange 帳戶開啟 [郵件] 應用程式，而郵件會開始同步到裝置。
![<exchange-account-opens>
1. 簽入 [郵件] 應用程式的帳戶設定，以確定帳戶名稱與您在電子郵件設定檔中輸入的帳戶名稱相同 (例如，Contoso Mail)，而且同步處理設定正確。
2. <check-account-settings>
3. <check-email-account-name>
![如果發現電子郵件設定檔尚未自動套用至裝置，您可以在裝置上使用公司入口網站應用程式，手動套用原則。](./media/Email-Walkthrough/Email-Walkthrough-10.png)
4. 開啟公司入口網站應用程式。
![點選 [我的裝置] 點選您的裝置名稱。

## <tap-device-name
[點選 [同步] > [檢查相容性]](get-started-with-a-30-day-trial-of-microsoft-intune.md)


<!--HONumber=May16_HO2-->


