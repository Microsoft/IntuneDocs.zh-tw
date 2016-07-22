---
title: "如果從 Intune 取消註冊裝置，會發生什麼情況？ | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47e03edb-0c57-4e25-8e89-4a1069267b8c
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1244d931d1bd3db012fbcfe0bd055d1fd4f2d88a
ms.openlocfilehash: f0108b884439aac9661c9f36f85b47d80209d155


---


# 如果從 Intune 取消註冊裝置，會發生什麼情況？

如需會發生什麼情況的其他資訊，請使用符合您所使用之裝置類型的連結，如上述＜在本文中＞一節所示。

- [Windows 10 mobile、8.1、Windows 8、Windows 7、Vista](#windows-10-mobile--8-1,-windows-8,-windows-7,-vista)
- [Windows 10、Windows 8.1 或 Windows Phone 8](#windows-10--windows-8-1-or-windows-phone-8)
- [執行 Windows 8.1 或 Windows RT 的 Windows RT](#windows-rt-running-windows-8-1-or-windows-rt)


## Windows 10、Windows 8.1、Windows 8、Windows 7、Vista

-   您的裝置將不再顯示於公司入口網站中，而且您無法再從公司入口網站安裝應用程式。

-   如果您已安裝 Intune 用戶端軟體，則會從電腦予以移除。

-   從電腦移除 Intune Endpoint Protection 軟體。 如果電腦已安裝其他病毒防護軟體且已將它停用，則在移除 Intune Endpoint Protection 之後，可能會重新啟用該軟體。 在您將電腦從公司入口網站移除之後，應該檢查電腦。

    > [!IMPORTANT]
    > 如果其他防毒軟體未重新啟用，或是沒有安裝其他病毒防護軟體，您的電腦可能容易遭受病毒和惡意程式碼威脅。

-   您在新增裝置時變更的任何裝置設定 (例如，停用相機) 都將失效。

-   電腦不會再從 Intune 服務接收自動軟體更新或防毒軟體更新。 不過，依據其設定方式，電腦可能仍然會從 Windows Server Update Services、Windows Update 或 Microsoft Update 接收更新。

此外，針對 Windows 8.1：

-   您無法再使用裝置上的公司應用程式和公司資料。

-   某些郵件應用程式，例如 Windows Mail，將無法再存取您的裝置上儲存的公司電子郵件。

-   您可能無法使用 Wi-Fi 或虛擬私人網路連線到公司網路。

-   您可能無法再存取裝置上的某些公司資源，例如檔案共用或內部網站。

## Windows 10 mobile、Windows Phone 8.1 或 Windows Phone 8

-   已從您的裝置解除安裝公司入口網站應用程式，這表示您的裝置將不再顯示於公司入口網站中，而且您無法從公司入口網站應用程式或公司入口網站安裝應用程式。

-   您無法再使用裝置上的公司應用程式和公司資料。

-   您在新增裝置時變更的任何裝置設定 (例如停用相機或需要特定密碼長度) 都將失效。

    > [!IMPORTANT]
    > 唯一例外仍然有效的設定是加密原則。 如果您的公司原則要求必須加密 Windows Phone，將手機解密的唯一方式是使用 Windows Phone 上的 [設定] 功能表來重設手機。

## 執行 Windows 8.1 或 Windows RT 的 Windows RT

-   已從您的裝置解除安裝公司入口網站應用程式，這表示您的裝置將不再顯示於公司入口網站中，而且您無法從公司入口網站安裝應用程式。

-   您無法再使用裝置上的公司應用程式和公司資料。

-   您在新增裝置時變更的任何裝置設定 (例如停用相機或需要特定密碼長度) 都將失效。

-   您可能無法再使用 Wi-Fi 或虛擬私人網路連線到公司網路。

-   您可能無法再存取裝置上的某些公司資源，例如檔案共用或內部網站。

-   某些郵件應用程式，例如 Windows Mail，將無法再存取您的裝置上儲存的公司電子郵件。

當您移除 Windows RT 裝置時，將會發生下列情況：

-   已從您的裝置解除安裝公司入口網站應用程式，這表示您的裝置將不再顯示於公司入口網站中，而且您無法從公司入口網站安裝應用程式。

-   您無法再使用裝置上的公司應用程式和公司資料。

-   您在新增裝置時變更的任何裝置設定 (例如停用相機或需要特定密碼長度) 都將失效。

如有任何問題，請連絡您的 IT 系統管理員。 如需其連絡資訊，請查看[公司入口網站](http://portal.manage.microsoft.com)。

### 請參閱
[使用具有 Intune 的 Windows 裝置](using-your-windows-device-with-intune.md)


<!--HONumber=Jun16_HO4-->


