---
title: "Lookout 整合疑難排解 | Microsoft Docs"
description: "本主題描述如何針對 Lookout 整合的常見問題進行疑難排解"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bbe0b5f4-b8bc-49f3-85a9-51fb2f226fca
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: e10453155343bb7fd91a4fd3874d393ef78d0b1a
ms.openlocfilehash: 0b5586a06af7658c0c7a328ae1a824f88129039f
ms.contentlocale: zh-tw
ms.lasthandoff: 04/25/2017


---

# <a name="troubleshoot-lookout-integration-with-intune"></a>Lookout 與 Intune 整合疑難排解

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

本主題描述設定 Lookout 行動裝置威脅保護 (MTP) 時可能遇到的一些常見問題。

**登入錯誤**

## <a name="403-errors"></a>403 錯誤
當您登入 [Lookout MTP 主控台](https://aad.lookout.com)時看到 403 錯誤：**您沒有存取服務的授權**。當指定的使用者名稱不是設定為存取 Lookout MTP 的 Azure Active Directory (Azure AD) 群組成員時，就會發生此錯誤。

Lookout MTP 只允許已設定 Azure AD 群組的使用者存取服務。 若要判斷哪個群組已設定為可存取 Lookout MTP，請連絡 Lookout 支援部門：

* 電子郵件：enterprisesupport@lookout.com
* 登入 [MTP 主控台](http://aad.lookout.com)，並瀏覽至 [支援] 模組。
* 移至：https://enterprise.support.lookout.com/hc/requests，並提出支援要求。

## <a name="unable-to-sign-in"></a>無法登入
當 Azure AD 全域系統管理員使用者尚未接受 Lookout 的初始設定時，您會看到下列錯誤。

![顯示登入錯誤之 Lookout 登入畫面的螢幕擷取畫面](../media/mtp/lookout-mtp-consent-not-accepted-error.png)

若要解決此問題，全域系統管理員使用者必須登入 https://aad.lookout.com/les?action=consent，並接受起始安裝程式的提示。 您可以在[設定訂用帳戶使用 Lookout MTP](../deploy-use/set-up-your-subscription-with-lookout-mtp.md) 主題中找到更詳細的資訊

**裝置狀態問題**

## <a name="device-missing-from-lookout-device-list"></a>Lookout 裝置清單中遺漏裝置

在下列任一情況下可能會發生此問題：
* **Lookout MTP 主控台**指定的**註冊群組**中沒有裝置使用者。  在 [Lookout 主控台](http://aad.lookout.com)中移至 [系統] > [Intune 連接器] > [註冊管理]。  檢閱設定進行註冊的 Azure AD 群組，並確認裝置使用者是 Azure AD 群組的成員之一。  新增使用者至註冊群組之後，最多需要經過設定的輪詢間隔 (預設為 5 分鐘)，才會看到裝置出現在 Lookout MTP 主控台的 [裝置] 模組中。
* 如果裝置不受 Lookout MTP 支援。  不支援的裝置將會出現在 MTP Lookout MTP 主控台之連接器設定的 [受管理的裝置] 區段中。

### <a name="device-reported-as-pending"></a>裝置回報為**擱置**

如果使用者尚未開啟 Lookout for Work 應用程式即點選 [啟用] 按鈕，裝置會顯示 [擱置]。 如需以 Lookout for Work 應用程式啟用裝置的詳細資訊，請參閱[系統提示您在 Android 裝置上安裝 Lookout for Work](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android) 或[系統提示您在 iOS 裝置上安裝 Lookout for Work](https://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-ios)。

## <a name="device-whos-active-but-has-no-device-id"></a>作用中但沒有裝置識別碼的裝置
在 Lookout MTP 主控台中，如果作用中的裝置沒有裝置識別碼，則裝置使用者不在註冊群組中。 如果裝置的使用者已從註冊群組中移除，或已移除註冊群組，則裝置就會進入此狀態。

在 [Lookout 主控台](http://aad.lookout.com)中移至 [系統] > [Intune 連接器] > [註冊] 並檢閱設定。  檢閱 Azure AD 群組，並確認裝置使用者是 Azure AD 群組的成員之一。

當裝置處於此狀態時，Lookout 會繼續通知使用者任何偵測到的威脅，但不會將任何威脅資訊傳送至 Intune。

## <a name="device-reported-as-disconnected"></a>裝置回報為**已中斷連線**

**已中斷連線**表示裝置未在設定的間隔中與 Lookout MTP 同步處理，預設為 30 天，至少 7 天。 裝置缺少公司入口網站應用程式或 Lookout for Work 應用程式。 重新安裝應用程式應該可以解決此問題。 當使用者開啟 Lookout for Work 並啟用應用程式時，裝置會與 Lookout MTP 和 Intune 重新同步處理。

### <a name="forcing-a-device-sync"></a>強制執行裝置同步處理
系統管理員可以從 Lookout MTP 主控台的 [裝置] 模組選取裝置，並選擇將它刪除。   裝置擁有者下次開啟 Lookout for Work 應用程式並點選 [啟用] 時，裝置狀態會進行完整重新同步處理。

## <a name="device-has-a-new-user"></a>裝置有新的使用者
您應該抹除裝置，並要求新使用者註冊。  從 [Intune 系統管理員主控台](https://manage.microsoft.com)選取裝置，按一下滑鼠右鍵並選擇 [淘汰/抹除]，以移除受管理的裝置。 淘汰裝置之後，您可以將它刪除。

![Intune 系統管理主控台中顯示 [淘汰/抹除] 選項之 [裝置] 模組的螢幕擷取畫面](../media/mtp/mtp-retire-device-intune-console.png)

您也可以移至 [Lookout 主控台](http://aad.lookout.com)的 [裝置] 模組，然後選擇 [刪除]。

如果新使用者屬於 Lookout MTP 註冊群組，則當 Azure AD 建立裝置與新使用者的關聯後，就會顯示該裝置。

## <a name="compliance-remediation-workflows"></a>合規性補救工作流程
- [系統提示您在 Android 裝置上安裝 Lookout for Work]( http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)
- [您必須解決 Lookout for Work 在 Android 裝置上找到的威脅](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)
- [您必須解決 Lookout for Work 在 iOS 裝置上找到的威脅](https://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-ios)


### <a name="see-also"></a>另請參閱
[設定訂用帳戶使用 Lookout MTP](https://docs.microsoft.com/intune/deploy-use/set-up-your-subscription-with-lookout-mtp)

