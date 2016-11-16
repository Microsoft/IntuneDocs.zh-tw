---
title: "Lookout 整合疑難排解 | Microsoft Intune"
description: "本主題描述如何針對 Lookout 整合的常見問題進行疑難排解"
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbe0b5f4-b8bc-49f3-85a9-51fb2f226fca
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9bf5764d1e1bd73fd62e5033b2309fc8d5a912e4
ms.openlocfilehash: aa29f702803d657f783ff0dfc6ea66981484c569


---

# <a name="troubleshoot-lookout-integration-with-intune"></a>Lookout 與 Intune 整合疑難排解
本主題描述設定 Lookout 行動裝置威脅保護 (MTP) 時可能遇到的一些常見問題。
## <a name="troubleshoot-login-errors"></a>登入錯誤疑難排解
### <a name="403-errors"></a>403 錯誤
當您登入 [Lookout MTP 主控台](https://aad.lookout.com)時可能會看到 403 錯誤：**您沒有存取服務的授權**  當您指定的使用者名稱不是設定為存取 Lookout MTP 的 Azure Active Directory (Azure AD) 群組成員時，就會發生此錯誤。

Lookout MTP 已設定為只允許所設定之 Azure AD 群組中的使用者進行存取。 如果您不確定哪個群組已設定為可存取 Lookout MTP，請連絡 Lookout 支援部門。

您可以透過下列方法連絡 Lookout 支援部門：

* 電子郵件：enterprisesupport@lookout.com
* 登入 [MTP 主控台](http://aad.lookout.com)，然後巡覽至 [支援] 模組。
* 前往 https://enterprise.support.lookout.com/hc/en-us/requests 並提出支援要求。

### <a name="unable-to-sign-in"></a>無法登入
當 Azure AD 全域管理員使用者尚未接受 Lookout 的初始設定時，您可能會看到下列錯誤。

![顯示登入錯誤之 Lookout 登入畫面的螢幕擷取畫面](../media/mtp/lookout-mtp-consent-not-accepted-error.png)

若要解決此問題，全域管理員使用者必須登入 https://aad.lookout.com/les?action=consent 並接受初始化設定的提示。 您可以在[設定訂用帳戶使用 Lookout MTP](set-up-your-subscription-with-lookout-mtp.md) 主題中找到更詳細的資訊

## <a name="troubleshoot-device-status-issues"></a>裝置狀態問題疑難排解

### <a name="device-not-showing-up-in-the-lookout-mtp-console-device-list"></a>裝置未顯示在 Lookout MTP 主控台裝置清單中

在下列任一情況下可能會發生此問題：
* 當擁有此裝置的使用者不在 **Lookout MTP 主控台**中指定的**註冊群組**時。  從 [系統] 模組，移至 [Intune 連接器] 索引標籤，然後檢視 **[Enrollment Management]** (註冊管理) 設定。  您應該會看到設定要註冊的一或多個 Azure AD 群組。  確認擁有遺失裝置的使用者是否屬於其中一個指定的 Azure AD 群組。  新增使用者至註冊群組之後，最多需要經過設定的輪詢間隔 (預設為 5 分鐘)，才會看到裝置顯示在 Lookout MTP 主控台的 [裝置] 模組中。

* 如果裝置不受 Lookout MTP 支援。  不支援的裝置將會出現在 MTP Lookout MTP 主控台之連接器設定的 [受管理的裝置] 區段中。

### <a name="device-continues-to-be-reported-as-pending"></a>系統會繼續將裝置回報為 [擱置中]

顯示 [擱置中] 的裝置表示使用者尚未開啟 Lookout for Work 應用程式及點選 [啟動] 按鈕。 如需使用 Lookout for Work 應用程式啟用裝置的詳細資訊，請閱讀下列主題：

[系統提示在您的 Android 裝置上安裝 Lookout for Work ](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

### <a name="in-the-lookout-mtp-console-a-device-is-showing-as-active-but-does-not-have-a-device-id"></a>在 Lookout MTP 主控台中，裝置顯示為作用中，但沒有裝置識別碼。  
這表示擁有此裝置的使用者不在 Lookout MTP 主控台中指定的註冊群組。   如果已從註冊群組移除擁有裝置的使用者，或已移除使用者所屬的註冊群組，則裝置可能會進入此狀態。

從 Lookout MTP 主控台的 [系統] 模組，移至 [Intune 連接器] 索引標籤，然後檢閱 [註冊] 設定。  您應該會看到設定要註冊的一或多個 Azure AD 群組。  確認擁有此裝置的使用者是否屬於其中一個指定的 Azure AD 群組。  

當裝置處於此狀態時，Lookout 會繼續通知使用者任何偵測到的威脅，但不會將任何威脅資訊傳送至 Intune。

### <a name="device-shows-disconnected-state"></a>裝置顯示已中斷連線狀態

已中斷連線表示 Lookout MTP 在預先設定的時間間隔內沒有裝置的任何消息 (預設為 30 天，最少為 7 天)。 這表示公司入口網站應用程式或 Lookout for Work 應用程式未安裝在裝置上，或者已解除安裝。 重新安裝應用程式應該可以解決這個問題。 當使用者開啟 Lookout for Work 並啟動應用程式時，裝置會與 Lookout MTP 和 Intune 重新同步處理。    

### <a name="forcing-a-resync-on-the-device"></a>強制在裝置上重新同步處理
系統管理員可以從 Lookout MTP 主控台的 [裝置] 模組選取裝置，並選擇將它刪除。   裝置擁有者下次開啟 Lookout for Work 應用程式並點選 [啟動] 時，裝置狀態會進行完整重新同步處理。

### <a name="the-owner-of-the-device-is-no-longer-using-this-device"></a>裝置的擁有者不再使用此裝置
您必須抹除裝置，並請新的使用者註冊。  從 [Intune 系統管理員主控台](https://manage.microsoft.com)選取裝置，按一下滑鼠右鍵並選擇 [淘汰/抹除]，以移除受管理的裝置。 淘汰裝置之後，您可以將它刪除。

![Intune 管理主控台中顯示 [淘汰/抹除] 選項之 [裝置] 模組的螢幕擷取畫面](../media/mtp/mtp-retire-device-intune-console.png)

您也可以移至 Lookout MTP 主控台的 [裝置] 模組，然後選擇 [刪除]。  

只要新使用者是在 Lookout MTP 主控台中指定的其中一個註冊群組，當 Azure AD 將裝置與新使用者相關聯之後，就會出現此裝置。

## <a name="compliance-remediation-workflows"></a>相容性補救工作流程
[系統提示在您的 Android 裝置上安裝 Lookout for Work]( http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

[您必須解決 Lookout for Work 在 Android 裝置上找到的威脅](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)


### <a name="see-also"></a>請參閱
[設定訂用帳戶使用 Lookout MTP](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-your-subscription-with-lookout-mtp)



<!--HONumber=Nov16_HO2-->


