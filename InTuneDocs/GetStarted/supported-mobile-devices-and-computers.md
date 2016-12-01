---
title: "支援的行動裝置和瀏覽器 | Microsoft Intune"
description: "Intune 支援的行動裝置和電腦"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: aeeccfa4-0f14-447e-a3df-c8435c8a4bb2
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 149f3a3310907d131affeaad4bd372aa60be9206
ms.openlocfilehash: 80541567c535cfeb7fca3eda3c9143f4b11d7abb


---

# <a name="supported-mobile-devices-and-computers"></a>支援的行動裝置和電腦

您可以先註冊，再管理下列裝置類型︰

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

註冊裝置可提供[這些功能](/Intune/get-started/choose-how-to-manage-devices)。

您也可以利用 Intune 電腦用戶端軟體管理 Windows 電腦。 Intune 電腦用戶端體支援 Windows 7 和更新版本 (Windows 10 家用版除外)。 使用用戶端軟體管理電腦可提供[這些功能](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune)。

使用企業管理套件 (EMS) 的客戶也可使用 Azure Active Directory (AAD) 註冊 Windows 10 裝置。

## <a name="microsoft-intune-supported-web-browsers"></a>Microsoft Intune 支援網頁瀏覽器

執行不同的系統管理工作時，您必須使用下列其中一個系統管理網站。

- [Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Microsoft Intune 系統管理員主控台](https://admin.manage.microsoft.com/)

> [!Note]
> 因為 Microsoft Edge 和行動瀏覽器不支援 [Microsoft Silverlight](https://msdn.microsoft.com/en-us/library/cc838158(v=vs.95).aspx)，所以系統管理員主控台不予支援。 Intune 主控台在一段時間之後會從 Silverlight 經驗移動；最後，所有 Intune 的行動裝置和應用程式管理功能都可以在[新的 Microsoft Azure 入口網站中使用](https://blogs.technet.microsoft.com/enterprisemobility/2015/11/17/enhancing-managed-mobile-productivity/)。

|Intune 功能 |支援的瀏覽器|
|---------|---------|
|Intune 管理主控台     |  Internet Explorer 10 或更新版本<br /><br />Google Chrome (42 版之前的版本)<br /><br />啟用 Silverlight 的 Mozilla Firefox<br /><br />**注意：**系統管理員主控台不支援 Microsoft Edge 及行動瀏覽器。                      
|Office 365 管理入口網站     |所有瀏覽器，包括行動瀏覽器及受管理的瀏覽器  |
|公司入口網站     |**在行動裝置上︰**使用每個受支援平台的預設網頁瀏覽器   <br /><br />**在 Windows 電腦上：**Internet Explorer 10 或更新版本，或者 Microsoft Edge<br /><br />**在 Mac OS X 10.9 或更新版本上︰**Apple Safari    |

> [!Note]
> 因為 Microsoft Edge 和行動瀏覽器不支援 [Microsoft Silverlight](https://msdn.microsoft.com/en-us/library/cc838158(v=vs.95).aspx)，所以系統管理員主控台不予支援。 Intune 主控台在一段時間之後會從 Silverlight 經驗移動；最後，所有 Intune 的行動裝置和應用程式管理功能都可以在[新的 Microsoft Azure 入口網站中使用](https://blogs.technet.microsoft.com/enterprisemobility/2015/11/17/enhancing-managed-mobile-productivity/)。

### <a name="office-365-portalhttpgomicrosoftcomfwlinkplinkid698854"></a>[Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)

**身為租用戶系統管理員，使用此入口網站可管理訂閱**，包括下列工作 (若系統管理員角色允許)：

- 管理訂閱的使用者帳戶，以及設定從內部部署 Active Directory 進行目錄同步處理。
- 管理稱為安全性群組的使用者群組。
- 將使用 Intune 的授權指派給使用者。
- 設定用於訂閱的網域名稱。 網域名稱定義使用者用來登入的帳戶。
- 管理訂閱的計費和購買詳細資料，包括您擁有的授權數目，或是您可以使用的雲端存放裝置空間容量。
- 尋找連結來檢視 Intune 服務的健全狀況。
- 身為租用戶系統管理員，即使您的帳戶未獲指派使用 Intune 的授權，您還是可以登入 Office 365 入口網站來管理訂閱。
- 任何擁有 Intune 授權但不是系統管理員的使用者，都可以使用此入口網站來重設其帳戶密碼並編輯其設定檔。
- 若要存取 Office 365 入口網站，您帳戶的登入狀態必須為 [已允許]。 此狀態與獲得訂閱的授權有所區別。 根據預設，所有使用者帳戶的狀態均為 [已允許]。


### <a name="microsoft-intune-administrator-consolehttpsmanagemicrosoftcom"></a>[Microsoft Intune 系統管理員主控台](https://manage.microsoft.com/)

**身為服務系統管理員，使用此入口網站可管理日常作業**，包括：

- 設定電腦和行動裝置的原則。
- 上傳和部署軟體，例如軟體更新和應用程式。
- 管理電腦上的 Endpoint Protection。
- 檢視裝置狀態和執行報表。
- 登入此入口網站。 您必須具有服務系統管理員權限，或必須是具有全域系統管理員角色的租用戶系統管理員，才能登入此入口網站。


唯有具有服務系統管理員權限的使用者，或是具有全域系統管理員角色的租用戶系統管理員，才能登入此入口網站。 若要存取管理主控台，您的帳戶必須擁有使用 Intune 的授權，且登入狀態必須為 [已允許]。



<!--HONumber=Nov16_HO4-->


