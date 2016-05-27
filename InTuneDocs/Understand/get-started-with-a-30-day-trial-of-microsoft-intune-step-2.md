---
# required metadata

title: 將使用者新增至 Microsoft Intune 30 天評估 | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 9e40999b-46f7-447b-8974-72af82bec7ef

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 將使用者新增至 Microsoft Intune 30 天評估
完成設定您的帳戶之後，您將使用 [新增使用者精靈] 將個別使用者帳戶新增至 Intune，或使用 [大量新增使用者精靈] 大量新增使用者 (請參閱本節中的指示)。  開始之前，請務必了解 Intune 如何處理系統管理員帳戶。

租用戶系統管理員使用 Office 365 系統管理中心將使用者新增至 Microsoft Intune Users 群組。 將使用者新增至  Users 群組 會將 Intune 訂閱授權指派給使用者，這也是讓這些使用者在 Microsoft Intune 系統管理主控台中顯示的方式。

Intune 的系統管理員帳戶與一般使用者帳戶不同，不會在 Office 365 系統管理中心中建立。 相反地，您可以使用 [管理] 工作區之 [管理] 下的管理主控台，將唯讀存取權或完整存取系統管理權限指派給使用者。 指派唯讀存取權的服務系統管理員無法變更 Intune 設定，但可以檢視資料及執行報表。 具有完整存取權的服務系統管理員具有所有可用的系統管理權限。

您可以使用 Intune 系統管理主控台來檢視租用戶系統管理員資訊，但無法在此建立租用戶系統管理員。 根據預設，訂閱擁有者會成為 Microsoft Intune 服務的租用戶系統管理員，並具有 Office 365 系統管理中心與 Intune 管理主控台的完整存取權。 建議您使用 Office 365 系統管理中心至少建立一個額外的租用戶系統管理員帳戶，以協助委派工作，並確保當您忘記密碼時，不會遭到鎖定而無法使用 Intune 服務系統管理員帳戶。

## 新增個別使用者帳戶
使用下列步驟可在您的評估版租用戶中建立額外的使用者帳戶。 請記住，您新增的每個使用者帳戶都會視為從 Intune 免費評估版取得的 100 個授權之一。

1.  在 [Office 365 系統管理中心](http://go.microsoft.com/fwlink/p/?LinkId=698854)中，選擇 [新增使用者] &gt; [新增]&gt; [使用者] 啟動 [新增使用者精靈]。

2.  在 [詳細資料] 頁面上，填寫必要的欄位。

3.  在 [設定]  頁面上，設定使用者的 [位置]  。

4.  在 [群組] 頁面上，選擇 [下一步] 接受預設值，並將 Intune 的授權指派給使用者帳戶。

5.  在 [電子郵件] 頁面上，指定最多五個電子郵件地址，以接收該帳戶的使用者名稱和暫時密碼的通知。 請以分號 (;) 分隔多個電子郵件地址。 完成時，選擇 [建立]，將使用者新增到訂閱。

6.  在 [結果]  頁面上，您可以檢視新的帳戶名稱及其暫時密碼。 Intune 會自動建立暫時密碼。

7.  當新的使用者出現在 Office 365 系統管理中心時，請確認是否成功建立新使用者：

    1.  在 [Intune 管理主控台](https://manage.microsoft.com/)中，選擇 [管理] &gt; [公司入口網站]，然後捲動至畫面底部。 複製顯示於 [Intune 公司入口網站] 下方的 URL

    2.  以「隱私權模式」開啟新的瀏覽器視窗 (在 Internet Explorer 中，選擇 [工具] &gt; [InPrivate 瀏覽])，或在不同裝置上開啟一個新的瀏覽器視窗，然後瀏覽至您在前一個步驟中複製的 URL。 使用者第一次登入時，他們必須為帳戶提供新密碼。

## 大量新增使用者
若要大量新增使用者到 Intune，請使用 [大量新增使用者精靈] 上傳包含使用者資料的逗號分隔值 (CSV) 檔案。 精靈中的連結可讓您下載空白的範本和範例 CSV 檔案。 CSV 檔案的第一個資料列必須依正確順序包含每個使用者資料的資料行標籤。 然後，針對 CSV 檔案中的每個使用者，您必須包括 [使用者名稱] (例如 bob@contoso.com) 和 [顯示名稱] (例如 Bob Kelly)

1.  在 [Office 365 系統管理中心](http://go.microsoft.com/fwlink/p/?LinkId=698854)中，選擇 [使用者] &gt; [新增]

2.  選擇 [大量新增]，啟動 [大量新增使用者精靈]。

3.  在 [選取檔案] 頁面上，選擇 [瀏覽]，指定並載入電腦中的現有 CSV 檔案。 您也可以使用精靈中的連結，下載範例 CSV 檔案或空白的範本檔案。

4.  在 [驗證] 頁面上，檢閱結果，然後選擇 [檢視] 以顯示更多詳細資料。

5.  在 [設定] 頁面上，確認登入狀態為 [已允許]，然後設定 [位置]。 這些設定會套用到 CSV 檔案新增的所有使用者帳戶。

6.  在 [群組] 頁面上，選擇 [下一步] 接受預設值，並將 Intune 的授權指派給 CSV 檔案所新增的所有使用者帳戶。 根據預設，已經選取該核取方塊，這會將 Intune 的授權指派給每個帳戶。

7.  在 [電子郵件] 頁面上，指定最多五個電子郵件地址，以接收 Intune 為每個帳戶建立使用者名稱和暫時密碼的通知。 請以分號 (;) 分隔多個電子郵件地址。 選擇 [建立]，將使用者新增到訂閱。

8.  在 [結果]  頁面上，您可以檢視每個使用者帳戶的帳戶名稱和暫時密碼。

您藉由匯入方式新增的每個使用者帳戶會立即出現在 Office 365 系統管理中心的 [使用者]節點中。 新使用者第一次登入時，他們必須為其使用者帳戶指定新密碼。

### 後續步驟
恭喜！ 您剛剛已完成 Microsoft Intune 評估逐步解說的步驟 2。

>[!div class="step-by-step"]

>[&larr; 註冊評估](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-1.md)     [建立群組 &rarr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md)  


<!--HONumber=May16_HO2-->


