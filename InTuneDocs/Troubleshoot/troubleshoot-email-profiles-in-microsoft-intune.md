---
# required metadata

title: 電子郵件設定檔疑難排解 |Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune 的電子郵件設定檔疑難排解
本文列出一些電子郵件設定檔問題，並說明如何進行疑難排解及解決問題。

如果此資訊無法解決您的問題，請參閱[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)，以尋找更多方法來取得協助。


## 無法從電子郵件帳戶傳送映像
已自動設定電子郵件帳戶的使用者將無法從他們的裝置傳送圖片或映像。
未啟用允許從協力廠商應用程式傳送電子郵件選項時就會發生這種情況。

### Intune 解決方案

1.  在 Microsoft Intune 系統管理主控台中，按一下 [原則] 工作負載 &gt;  [組態原則]

2.  選取電子郵件設定檔，然後按一下 [編輯]

3.  選取 [允許從協力廠商應用程式傳送電子郵件]。

### Configuration Manager 與 Intune 解決方案整合

1.  開啟 Configuration Manager 主控台 &gt;  [資產與相容性]

2.  展開 [概觀]  -&gt;  [相容性設定]  -&gt;  [公司資源存取]，然後選取 [電子郵件設定檔]

3.  以滑鼠右鍵按一下電子郵件設定檔，然後開啟 [屬性]

4.  選取 [同步處理設定] 索引標籤上的 [允許從協力廠商應用程式傳送電子郵件]

## 後續步驟
如果這項疑難排解資訊對您沒有幫助，請連絡 Microsoft 支援服務，如[如何取得 Microsoft Intune 的支援](how-to-get-support-for-microsoft-intune.md)中所述


<!--HONumber=May16_HO2-->


