---
title: "電子郵件設定檔疑難排解 |Microsoft Intune"
description: "電子郵件設定檔問題，以及進行疑難排解並解決它們的方法。"
keywords: 
author: Nbigman
manager: angrobe
ms.date: 08/01/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ms.reviewer: tscott
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb0aeac2f94dfde50d9398b09c6b21c7ae40624
ms.openlocfilehash: 79076b65fe85adeaffd5435915cb5eca2a15413f


---

# Microsoft Intune 的電子郵件設定檔疑難排解
本文列出一些電子郵件設定檔問題，並說明如何進行疑難排解及解決問題。

如果此資訊無法解決您的問題，請參閱[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)，以尋找更多方法來取得協助。


## 無法從電子郵件帳戶傳送映像
已自動設定電子郵件帳戶的使用者將無法從他們的裝置傳送圖片或映像。
未啟用**允許從協力廠商應用程式傳送電子郵件**選項時就會發生這種情況。

### Intune 解決方案

1.  開啟 Microsoft Intune 管理主控台，並選取 **[原則]** 工作負載 &gt; **[設定原則]**。

2.  選取電子郵件設定檔，然後選擇 **[編輯]**。

3.  選取 [允許從協力廠商應用程式傳送電子郵件]。

### Configuration Manager 與 Intune 解決方案整合

1.  開啟 Configuration Manager 主控台 &gt; **[資產與相容性]**。

2.  展開 **[概觀]** -&gt; **[相容性設定]** -&gt; **[公司資源存取]**，然後選取 **[電子郵件設定檔]**。

3.  以滑鼠右鍵按一下電子郵件設定檔，然後開啟 **[內容]**。

4.  選取 **[同步處理設定]** 索引標籤上的 **[允許從協力廠商應用程式傳送電子郵件]**。


## 裝置已經安裝電子郵件設定檔

如果使用者在 Intune 佈建設定檔前已經安裝電子郵件設定檔，Intune 電子郵件設定檔部署的結果取決於裝置平台：

-**iOS**：Intune 依據主機名稱和電子郵件地址偵測到現有的重複電子郵件設定檔。 使用者建立的重複電子郵件設定檔會封鎖 Intune 系統管理員所建立設定檔的部署作業。 這是常見的問題，因為 iOS 使用者通常會建立電子郵件設定檔，然後註冊。 公司入口網站會通知使用者，他們因為手動設定電子郵件設定檔而不相容，並且會提示使用者移除該設定檔。使用者應該移除其電子郵件設定檔，以便可以部署 Intune 設定檔。 若要避免問題，請指示使用者先進行註冊，再安裝電子郵件設定檔，並允許 Intune 部署設定檔。

-**Windows**：Intune 依據主機名稱和電子郵件地址偵測到現有的重複電子郵件設定檔。 Intune 會覆寫使用者建立的現有電子郵件設定檔。

-**Samsung KNOX**：Intune 會依據電子郵件地址識別重複的電子郵件帳戶，並用 Intune 設定檔加以覆寫。 如果使用者設定了該帳戶，Intune 設定檔會再次加以覆寫。 請注意，這可能會對帳戶組態經過覆寫的使用者造成混淆。

由於 Samsung KNOX 不會使用主機名稱識別設定檔，因此建議您不要建立多個電子郵件設定檔以部署到不同主機上的同一個電子郵件地址，避免彼此覆寫。

## KNOX 裝置的錯誤 0x87D1FDE8
**問題**：針對各種 Android 裝置建立及部署 Samsung KNOX 的 Exchange Active Sync 電子郵件設定檔之後，在 [裝置內容] &gt; [原則] 索引標籤中，回報錯誤 **0x87D1FDE8** 或 [補救失敗]。

檢閱 Samsung KNOX 的 EAS 設定檔和來源原則的組態。 不再支援 Samsung Note 同步處理選項，因此不應該在您的設定檔中選取該選項。 請確定裝置有足夠的時間來處理原則，最多 24 小時。

## 後續步驟
如果這項疑難排解資訊對您沒有幫助，請連絡 Microsoft 支援服務 (如[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)中所述)。



<!--HONumber=Aug16_HO1-->


