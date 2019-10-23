---
title: 使用 Microsoft Intune 來檢視裝置詳細資料 - Azure | Microsoft Docs
description: 檢視您的裝置詳細資料，包括作業系統、儲存空間、製造商和型號等等。 在 Azure 中使用 Microsoft Intune 取得已安裝的應用程式清單、檢查相容性原則，以及設定 TeamViewer。 類似檢視清查您管理的裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a72477351425e9230200995658cc6f73a8565fb7
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509485"
---
# <a name="see-device-details-in-intune"></a>在 Intune 中查看裝置詳細資料

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

[裝置]  功能提供您管理之裝置其他詳細資料，包括其硬體及安裝的應用程式。

這篇文章會示範如何在 Azure 入口網站中檢視您的所有裝置及其屬性。

## <a name="view-the-device-details"></a>檢視裝置詳細資料

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 選取 [裝置]   > [所有裝置]  > 選取其中一個列出的裝置以開啟其詳細資料：

   - [概觀]  會顯示裝置名稱，並列出該裝置的一些重要屬性，包括它是否為「攜帶您自己的裝置」(BYOD) 裝置、簽入時間等。 您可以在裝置上執行下列動作：
      - [淘汰](devices-wipe.md#retire)
      - [抹除](devices-wipe.md#wipe)
      - [遠端鎖定](device-remote-lock.md)
      - [同步裝置](device-sync.md)
      - [重設密碼](device-passcode-reset.md)
      - [重新啟動](device-restart.md) (僅限 Windows)
      - [全新開始](device-fresh-start.md) (僅限 Windows)
      - 啟動遠端協助工作階段
   - 使用 [內容]  來指派[您所建立的類別](../enrollment/device-group-mapping.md)，以及將裝置的擁有權變更為個人裝置或公司裝置。
   - [硬體]  會包括許多裝置相關的詳細資料，例如裝置識別碼、作業系統與版本、儲存空間，以及更多詳細資料。
   - [探索到的應用程式]  會列出 Intune 找到已安裝在裝置上的所有應用程式，以及應用程式版本。 如需詳細資訊，請參閱 [Intune 探索到的應用程式](../apps/app-discovered-apps.md)。
   - [裝置合規性]  會列出所有已指派的合規性原則，以及裝置是否符合規範。
   - [裝置設定]  會顯示已指派給裝置的所有裝置設定原則，以及原則是否成功。

## <a name="hardware-device-details"></a>硬體裝置詳細資料
視裝置使用的電訊廠商而定，可能不會收集所有詳細資料

> [!Note]  
> 在 Intune 服務中，每 7 天就會重新整理硬體和軟體清查。

|詳細資料|說明|平台| 
|--------------|----------------------|----|  
|名稱|裝置的名稱。|Windows、iOS|
|管理名稱|裝置名稱只會用於主控台中。 變更此名稱不會變更裝置上的名稱。|Windows、iOS|
|UDID|裝置的唯一裝置識別碼。|Windows、iOS|
|Intune 裝置識別碼|可唯一識別裝置的 GUID。|Windows、iOS|
|序號|由製造商提供的裝置序號。|Windows、iOS|
|共用裝置|若為 [是]  ，則會有多名使用者共用裝置。|Windows、iOS|
|通過使用者核准的註冊|若為 [是]  ，則裝置會具備使用者核准的註冊，讓管理員能夠管理裝置上的特定安全性設定。|Windows、iOS|
|作業系統|在裝置上使用的作業系統。|Windows、iOS|
|作業系統版本|裝置上的作業系統版本。|Windows、iOS|
|作業系統語言|為裝置上作業系統設定的語言。|Windows、iOS|
|組建編號|作業系統的組建編號。|Android|
|安全性修補等級|適用於裝置的安全性修補等級。|Android|
|儲存空間總計|裝置上的儲存空間總計 (GB)。|Windows、iOS|
|可用儲存空間|裝置上的未使用儲存空間總計 (GB)。|Windows、iOS|
|IMEI|裝置的國際行動設備識別碼。|Windows、iOS、Android|
|MEID|裝置的行動設備識別碼。|Windows、iOS、Android|
|製造商|裝置的製造商。|Windows、iOS、Android|
|型號|裝置的型號。|Windows、iOS、Android|
|電話號碼|指派給裝置的手機號碼。|Windows、iOS、Android|
|訂閱電訊廠商|裝置的無線電訊廠商。|Windows、iOS、Android|
|行動電話通訊技術|裝置使用的無線電話系統。|Windows、iOS、Android|
|Wi-Fi MAC|裝置的媒體存取控制位址。|Windows、iOS、Android|
|ICCID|積體電路卡識別碼，這是 SIM 卡的唯一識別碼。|Windows、iOS、Android|
|註冊日期|裝置在 Intune 中註冊的日期與時間。|Windows、iOS、Android|
|上次連絡時間|裝置最後連線至 Intune 的日期與時間。|Windows、iOS、Android|
|啟用鎖定略過碼|此代碼可用來略過啟用鎖定。|Windows、iOS、Android|
|已註冊 Azure AD|若為 [是]  ，表示裝置已向 Azure Directory 註冊。|Windows、iOS、Android|
|Intune 已註冊|若為 [是]  ，表示裝置已向 Intune 註冊|Windows、iOS、Android|
|合規性|裝置的合規性狀態。|Windows、iOS、Android|
|EAS 已啟用|若為 [是]  ，裝置便會與 Exchange 信箱同步處理。|Windows、iOS、Android|
|EAS 啟用識別碼|裝置的 Exchange ActiveSync 識別碼。|Windows、iOS、Android|
|受監督|若為 [是]  ，表示系統管理員對裝置有加強的控制力。|Windows、iOS、Android|
|已加密|若為 [是]  ，表示會加密儲存在裝置上的資料。|Windows、iOS、Android|



## <a name="next-steps"></a>後續步驟
看看您還可以怎麼使用 Intune [管理您的裝置](device-management.md)。
