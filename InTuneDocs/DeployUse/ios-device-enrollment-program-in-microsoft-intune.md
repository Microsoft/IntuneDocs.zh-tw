---
# required metadata

title: 使用 Microsoft Intune 管理 iOS 裝置的 Apple DEP | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8ff9d9e7-eed8-416c-8508-efc20fca8578

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 註冊屬公司擁有的裝置註冊方案 iOS 裝置
Microsoft Intune 可以部署註冊設定檔，以「無線」註冊透過裝置註冊方案 (DEP) 所購買的 iOS 裝置。 註冊套件可以包括裝置的設定助理選項。 透過 DEP 註冊的裝置不能由使用者取消註冊。

## 使用 Microsoft Intune 管理 iOS 裝置的 Apple DEP
若要使用 Apple 的裝置註冊方案 (DEP) 來管理屬公司擁有的 iOS 裝置，您的組織必須加入 Apple DEP，並透過該方案取得裝置。 下列網址提供該程序的詳細資料：  [https://deploy.apple.com](https://deploy.apple.com)。 這個方案的優點包括無操作安裝裝置，而不需要透過 USB 將每部裝置連線到電腦。

在您以 DEP 註冊公司所擁有的 iOS 裝置之前，您須要從 Apple 取得 DEP 權杖。 此權杖可讓 Intune 同步處理貴公司所擁有的 DEP 參與裝置資訊。 它也允許 Intune 執行註冊設定檔上傳至 Apple ，並將這些設定檔指定給裝置。

1.  **使用 Microsoft Intune 開始管理 iOS 裝置**
    您必須先完成啟用 Intune 的 iOS 管理，才能夠註冊 iOS 裝置註冊方案 (DEP) 裝置。

2.  **取得加密金鑰**
    以系統管理使用者身分開啟 [Microsoft Intune 管理主控台](http://manage.microsoft.com)，並移至 [管理] &gt; [行動裝置管理] &gt; [iOS] &gt; [裝置註冊方案]，然後按一下 [下載加密金鑰]。 將加密金鑰 (.pem) 檔案儲存在本機。 這個 .pem 檔案會用於向 Apple 裝置註冊程式入口網站要求信任關係憑證。

      ![更新裝置註冊方案 Token](../media/dev-sa-ios-dep.png)

3.  **取得裝置註冊方案 Token**
    前往[裝置註冊方案入口網站](https://deploy.apple.com) (https://deploy.apple.com)，並使用公司的 Apple ID 登入。 未來必須使用這個 Apple 識別碼來更新 DEP 權杖。

    1.  在[裝置註冊方案](https://deploy.apple.com)入口網站中，移至 [裝置註冊方案] &gt; [管理伺服器]，然後按一下 [新增 MDM 伺服器].

    2.  輸入 [MDM 伺服器名稱]  ，然後按 [下一步] 。 伺服器名稱可用於識別 MDM 伺服器。 其不是 Microsoft Intune 伺服器的名稱或 URL。

    3.  [新增 &lt;伺服器名稱&gt;] 對話方塊隨即開啟。 按一下 [選擇檔案] 上傳 .pem 檔案，然後按 [下一步].

    4.  [新增 &lt;伺服器名稱&gt;] 對話方塊會顯示 [您的伺服器 Token] 連結。 將伺服器權杖 (.p7m) 檔案下載到您的電腦，然後按一下 [完成].

    此憑證 (.p7m) 檔案會用於建立 Intune 與 Apple 裝置註冊程式伺服器之間的信任關係。

4.  **將 DEP Token 新增至 Intune**
    在 [Microsoft Intune 管理主控台](http://manage.microsoft.com)中，移至 [管理] &gt; [行動裝置管理] &gt; [iOS] &gt; [裝置註冊方案]，然後按一下 [上傳 DEP Token]. [瀏覽] 到憑證 (.p7m) 檔案，並輸入 [Apple 識別碼]，然後按一下 [上傳].

5.  **新增公司裝置註冊原則**
    在 [Microsoft Intune 管理主控台](http://manage.microsoft.com)中，移至 [原則] &gt; [公司裝置註冊]，然後按一下 [新增]。 提供 [一般]  詳細資料，包括 [名稱]  和 [描述] ；指定指派給設定檔的裝置是否具有使用者親和性，或隸屬於某個群組；然後啟用 [設定此原則的裝置註冊方案設定]  來支援 DEP。 [設定助理]  窗格會定義在安裝期間設定的 iOS 裝置設定。

      ![設定助理窗格](../media/pol-sa-corp-enroll.png)

6.  **指派要管理的 DEP 裝置**
    前往[裝置註冊方案入口網站](https://deploy.apple.com) (https://deploy.apple.com)，並使用公司的 Apple ID 登入。 移至 [部署方案] &gt; [裝置註冊方案] &gt; [管理裝置]。 指定您 選擇裝置的方式、提供裝置資訊，並利用裝置的 [序號] 、[訂單號碼] 或 [上傳 CSV 檔案] 指定詳細資料。 接著，選取 [指派給伺服器]，然後選取針對 Microsoft Intune 指定的 &lt;伺服器名稱&gt;，然後按一下 [確定].

7.  **同步處理 DEP 管理的裝置**
    以系統管理使用者身分開啟 [Microsoft Intune 管理主控台](http://manage.microsoft.com)，並移至 [管理] &gt; [行動裝置管理] &gt; [iOS] &gt; [裝置註冊方案]，然後按一下 [立即同步處理]。 同步處理要求會傳送至 Apple。 若要在同步處理之後查看 DPE 管理的裝置，請在 [Microsoft Intune 管理主控台](http://manage.microsoft.com)中，移至 [群組] &gt; [所有屬公司擁有的裝置]。 在 [屬公司擁有的裝置] 工作區中，受管理裝置的 [狀態] 會顯示為 [未連線]，直到裝置開機並執行 [設定助理] 來註冊裝置為止。

    若要符合可接受 DEP 流量的 Apple 詞彙，Intune 具有下列限制︰
     -  完整 DEP 同步處理每 7 天只能執行一次。 在完整同步處理期間，Intune 會重新整理 Apple 已指派給 Intune 的每個序號，不論先前是否已同步處理序號。 如果在前一個完整同步處理的 7 天內嘗試進行完整同步處理，Intune 只會重新整理尚未列在 Intune 中的序號。
     -  任何同步處理要求都會在 10 分鐘內完成。 在此期間或直到要求成功，會停用 [同步處理] 按鈕。

8.  **將裝置散發給使用者**
    現在您可以將屬公司擁有的裝置散發給使用者。 當 iOS 裝置開機時，就會加以註冊交由 Intune 管理。



### 請參閱
[準備註冊裝置](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=May16_HO1-->


