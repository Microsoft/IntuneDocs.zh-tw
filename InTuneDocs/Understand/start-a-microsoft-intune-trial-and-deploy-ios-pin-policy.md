---
title: "開始使用 Intune 試用版並部署 iOS PIN 原則 | Microsoft Intune"
description: "在 Intune 中部署 iOS PIN 原則"
keywords: 
author: Staciebarker
manager: arob98
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 06cb9a73-0f17-44b3-b334-86c98020316e
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 376e6c1ae229187ab8ec73390f091f1d534365dd
ms.openlocfilehash: b2b24492693b61a544a4adc3e878b8b212d15a21


---

# 啟動 Microsoft Intune 試用版和部署 iOS PIN 原則
這些逐步指示會協助您設定 Intune 試用版，並設定 iOS 裝置的 PIN 原則。 如需其他可嘗試的一般 Intune 評估工作的清單，請參閱[一般的 Microsoft Intune 評估工作](common-microsoft-intune-evaluation-tasks.md)。



## 檢閱這項工作的必要條件

-   使用 Internet Explorer 的 Windows 電腦 - 以執行系統管理工作

-   iOS 7.1 或更新版本的裝置以測試使用者原則驗證

-   於註冊試用版時進行自我驗證的電話號碼

## 建立免費的 Intune 試用帳戶
> [!NOTE]
> 如果已經有 Intune 訂閱，請略過本節並移至下一節。

1.  使用 Windows 電腦，以滑鼠右鍵按一下 **Internet Explorer** (IE)，然後選取 **InPrivate 瀏覽**。

    ![啟動 InPrivate 瀏覽](../media/30-day-trial-walkthrus/30day-start-trial-1-InPrivate.png)

2.  移至 [Intune 註冊入口網站](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1)，提供要求的資訊，然後按一下 **下一步**。

    ![註冊帳戶](../media/30-day-trial-walkthrus/30day-start-trial-2-abt-you.png)

3.  輸入系統管理員帳戶的使用者識別碼和密碼，然後按一下 **下一步**。 您會使用這個識別碼登入 Intune 入口網站執行管理工作。

    ![建立識別碼](../media/30-day-trial-walkthrus/30day-start-trial-3-createID.png)

4.  輸入您的行動電話號碼，然後按一下 **簡訊驗證** 來驗證您的號碼。

    ![驗證詳細資料](../media/30-day-trial-walkthrus/30day-start-trial-4-textme.png)

5.  儲存螢幕顯示的資訊，然後按一下 **您可以開始使用…**。

    ![準備就緒](../media/30-day-trial-walkthrus/30day-start-trial-5-ReadyToGo.png)

## 建立測試使用者

1.  使用 Windows 電腦，按一下 **開始** 移至使用者管理頁面。

    ![移至使用者管理頁面](../media/30-day-trial-walkthrus/30day-crt-user-6-click-start.png)

2.  按一下 **+** 按鈕加入使用者。

    ![加入使用者](../media/30-day-trial-walkthrus/30day-crt-user-7-click-plus.png)

3.  在 **建立新的使用者帳戶** 頁面︰

    1.  提供測試使用者資訊。

    2.  選取 **輸入密碼** 選項。

    3.  清除 **請使用者下次登入時變更密碼** 核取方塊。

    4.  按一下 **建立**。

    ![建立新的使用者帳戶](../media/30-day-trial-walkthrus/30day-crt-user-8-add-user-info.png)

4.  在使用者建立確認的頁面中，按一下 **關閉**。

    ![使用者建立確認頁面](../media/30-day-trial-walkthrus/30day-crt-user-9-close-confirm.png)

5.  按一下 **重新整理** 按鈕，查看您所建立的測試使用者。

    ![帳戶確認](../media/30-day-trial-walkthrus/30day-crt-user-10-refresh-user.png)

## 設定測試使用者的 iOS PIN 原則

1.  使用 Windows 電腦，將 MDM 授權單位設為 Intune︰

    1.  移至 [Intune 管理主控台](http://manage.microsoft.com/)，登入您的系統管理員帳戶，然後按一下 **開始管理行動裝置**。 [行動裝置管理授權單位] 頁面隨即開啟。

        ![在 Intune 主控台中開始使用](../media/30-day-trial-walkthrus/30day-cfg-pol-11-start-mg-mobl-dev.png)

    2.  按一下 **設定行動裝置管理授權單位** 連結。

        ![設定行動裝置管理授權單位](../media/30-day-trial-walkthrus/30day-cfg-pol-12-link-set-mdm.png)

2.  啟用 iOS 裝置註冊。 這項程序會在 Apple Push Notification Service (APNs) 和您的 Intune 訂閱之間設定受信任的憑證。

    1.  按一下 **啟用 iOS 與 Mac OS X 平台**。

        ![啟用 iOS 和 Mac OS X 註冊](../media/30-day-trial-walkthrus/30day-cfg-pol-13-enbl-ios-plat.png)

    2.  按一下 **下載 APNs 憑證要求**。

        ![下載 APNs 憑證](../media/30-day-trial-walkthrus/30day-cfg-pol-14-dwnld-cert-reqst.png)

    3.  指定憑證簽署要求 (CSR) 的檔案名稱和位置，然後按一下 **儲存**。 這個檔案中有與 Intune 訂閱所持私密金鑰相對應的公開金鑰。

        ![指定憑證簽署要求](../media/30-day-trial-walkthrus/30day-cfg-pol-15-cert-name-loc.png)

    4.  按一下 **Apple Push Certificates 入口網站** 開啟新的索引標籤。

        ![移至 APNs 憑證頁面](../media/30-day-trial-walkthrus/30day-cfg-pol-16-cert-portl-link.png)

    5.  輸入您的 Apple ID 和密碼，然後按一下 **登入**。 這可以是您在 iOS 裝置上從 iOS 應用程式市集取得應用程式所使用的識別碼。

        ![登入 Apple Push Certificates 入口網站](../media/30-day-trial-walkthrus/30day-cfg-pol-17-id-passw-signin.png)

    6.  按一下 **建立憑證**。

        ![建立 APNs 憑證](../media/30-day-trial-walkthrus/30day-cfg-pol-18-create-cert.png)

    7.  閱讀 Apple 的使用規定，選取核取方塊，然後按一下 **接受**。

        ![接受條款](../media/30-day-trial-walkthrus/30day-cfg-pol-19-TOU.png)

    8.  按一下 **瀏覽**。

        ![瀏覽至您儲存憑證的位置](../media/30-day-trial-walkthrus/30day-cfg-pol-20-browse.png)

    9. 選取您稍早儲存的 CSR 檔案，然後按一下 **開啟**。

        ![開啟憑證](../media/30-day-trial-walkthrus/30day-cfg-pol-21-CSRfile-open.png)

    10. 按一下 **上傳** 按鈕。

        ![上傳憑證](../media/30-day-trial-walkthrus/30day-cfg-pol-22-upld-reqst.png)

    11. 當系統提示您下載 JSON 檔案時，請按一下 **另存新檔**。

        ![儲存 JSON 檔案](../media/30-day-trial-walkthrus/30day-cfg-pol-23-json-saveas.png)

    12. 指定 JSON 檔案的位置，然後按一下 **儲存**。

        ![指定要儲存 JSON 檔案的位置](../media/30-day-trial-walkthrus/30day-cfg-pol-24-json-save-loc.png)

        如果幾秒之後頁面不會自動重新導向，請按一下 **取消**。

        ![頁面未重新導向時取消](../media/30-day-trial-walkthrus/30day-cfg-pol-25-json-pg-cancel.png)

    13. 若要擷取新建立的憑證檔案，請按一下 **下載**。

        ![下載憑證](../media/30-day-trial-walkthrus/30day-cfg-pol-26-dwnld-retrv-cert.png)

    14. 當系統提示您下載 PEM 檔案時，請按一下 **另存新檔**。

        ![下載 PEM 檔案](../media/30-day-trial-walkthrus/30day-cfg-pol-27-pem-saveas.png)

    15. 指定 PEM 檔案的位置，然後按一下 **儲存**。

        ![儲存 PEM 檔案](../media/30-day-trial-walkthrus/30day-cfg-pol-28-pem-save-loc.png)

    16. 返回 [Intune 管理主控台] 索引標籤，然後按一下 **上傳 APNs 憑證**。

        ![上傳 APNs 憑證](../media/30-day-trial-walkthrus/30day-cfg-pol-29-upld-cert.png)

    17. 輸入您的 Apple ID，然後按一下 **瀏覽**。

        ![輸入您的 Apple ID](../media/30-day-trial-walkthrus/30day-cfg-pol-30-app-id-browse.png)

    18. 選取剛剛儲存的 PEM 檔案，然後按一下 **開啟**。

        ![開啟 PEM 檔案](../media/30-day-trial-walkthrus/30day-cfg-pol-31-sel-pem-open.png)

    19. 按一下 **上傳**。

        ![上傳 PEM 檔案](../media/30-day-trial-walkthrus/30day-cfg-pol-32-pem-upload.png)

        現已設定好您的 APNs 憑證。

        ![APNs 憑證設定完成](../media/30-day-trial-walkthrus/30day-cfg-pol-33-apns-confgd.png)

3.  建立原則的目標測試使用者群組︰

    1.  在左窗格中，按一下 **群組**。

        ![開啟群組](../media/30-day-trial-walkthrus/30day-cfg-pol-34-clk-groups.png)

    2.  在最右邊，按一下 **建立群組**。

        ![建立群組](../media/30-day-trial-walkthrus/30day-cfg-pol-35-crt-group.png)

    3.  提供群組名稱，選取 **所有使用者** 為父群組，然後按一下 **下一步**。

        ![選取 [所有使用者] 作為父群組](../media/30-day-trial-walkthrus/30day-cfg-pol-36-name-group.png)

    4.  在 **群組成員資格啟動方式** 欄位中，選取 **父群組中的所有使用者**，然後按一下 **完成**。

        ![以父群組啟動群組成員資格](../media/30-day-trial-walkthrus/30day-cfg-pol-37-all-users-group.png)

4.  建立 iOS PIN 原則，並將測試使用者群組設定為其目標︰

    1.  在左窗格中，按一下 **原則**。

        ![開啟原則工作區](../media/30-day-trial-walkthrus/30day-cfg-pol-38-clk-policy.png)

    2.  在最右邊，按一下 **新增原則**。

        ![新增原則](../media/30-day-trial-walkthrus/30day-cfg-pol-39-add-policy.png)

    3.  展開 iOS 節點，選取 **一般設定** 資料列，然後按一下 **建立原則**。

        ![建立 iOS 一般設定原則](../media/30-day-trial-walkthrus/30day-cfg-pol-40-gen_cfg_pol.png)

    4.  輸入原則的名稱，開啟 **需要密碼才可解除鎖定行動裝置** 選項，並將 **最小密碼長度** 設為 **4**。

        ![設定密碼設定](../media/30-day-trial-walkthrus/30day-cfg-pol-41-name-policy.png)

    5.  按一下 **是** 部署原則。

        ![部署原則](../media/30-day-trial-walkthrus/30day-cfg-pol-42-yes-deploy-pol.png)

    6.  依序按一下之前建立的使用者群組及 **加入**，然後按一下 **確定**。

        ![選取原則的群組](../media/30-day-trial-walkthrus/30day-cfg-pol-43-add-pol-to-grp.png)

        您現在有以測試使用者群組為目標的 iOS PIN 原則。

        ![原則設定完成](../media/30-day-trial-walkthrus/30day-cfg-pol-44-policy-applied.png)

## 驗證 iOS 裝置上是否強制執行此原則

1.  在 iPad 上啟動 iOS 應用程式市集，安裝並開啟免費的 **Microsoft Intune 公司入口網站** 應用程式。

    ![安裝公司入口網站](../media/30-day-trial-walkthrus/30day-cfg-pol-45-cportal-installed.png)

2.  輸入您的測試使用者帳戶名稱和密碼，然後點選 **登入**。

    ![提供您的認證](../media/30-day-trial-walkthrus/30day-cfg-pol-46-cportal-signin.png)

3.  點選 **註冊** 開始在 Intune 中註冊裝置。

    ![開始註冊](../media/30-day-trial-walkthrus/30day-cfg-pol-47-tap-enroll.jpg)

4.  在 **安裝設定檔** 畫面上，點選 **安裝**。

    ![安裝設定檔](../media/30-day-trial-walkthrus/30day-cfg-pol-48-profile-install-1.jpg)

5.  在 **安裝設定檔** 對話方塊中，點選 **安裝**。

    ![繼續安裝設定檔](../media/30-day-trial-walkthrus/30day-cfg-pol-49-profile-install-2.jpg)

6.  在 **警告** 畫面上，點選 **安裝**。

    ![接受警告訊息](../media/30-day-trial-walkthrus/30day-cfg-pol-50-warning-install-3.png)

7.  在 **遠端管理** 對話方塊中，點選 **信任**。

    ![信任遠端管理](../media/30-day-trial-walkthrus/30day-cfg-pol-51-remt-mgmt-trust.jpg)

8.  當管理設定檔完成安裝時，請點選 **完成**。 註冊完成。

    ![註冊完成](../media/30-day-trial-walkthrus/30day-cfg-pol-52-profile-done.jpg)

9. 註冊完成後，請點選 **確定**，然後關閉公司入口網站應用程式。

    ![點選 [確定] 以關閉公司入口網站應用程式](../media/30-day-trial-walkthrus/30day-cfg-pol-53-devc-enrolled-ok.png)

10. 當系統提示您設定密碼時，請點選 **繼續**。

    ![接受提示來設定密碼](../media/30-day-trial-walkthrus/30day-cfg-pol-54-passcode-req-cont.png)

11. 輸入密碼，點選 **繼續**，再次輸入密碼，然後點選 **儲存**。

    ![提供密碼](../media/30-day-trial-walkthrus/30day-cfg-pol-55-passcode-enter.jpg)

12. 按下電源按鈕鎖定您的 iPad、滑動解除鎖定，您現在發現需要輸入密碼才能解除鎖定裝置。

### 請參閱
[Intune 評估指南](get-started-with-a-30-day-trial-of-microsoft-intune.md)



<!--HONumber=Jul16_HO3-->


