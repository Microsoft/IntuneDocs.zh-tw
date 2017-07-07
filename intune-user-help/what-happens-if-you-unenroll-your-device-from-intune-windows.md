---
title: "如果取消註冊 Windows 裝置，會發生什麼情況？ | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47e03edb-0c57-4e25-8e89-4a1069267b8c
searchScope: User help
ROBOTS: 
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 3de9589c46250727b1994381c24c68e6e2b90da2
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="what-happens-if-you-unenroll-your-windows-device-from-intune"></a>如果從 Intune 取消註冊 Windows 裝置，會發生什麼情況？

您可以使用此頁面右側之 [本文內容]下方的連結，尋找您要使用之裝置類型的相關資訊。


## <a name="windows-10-windows-81-windows-8-windows-7-windows-vista"></a>Windows 10、Windows 8.1、Windows 8、Windows 7、Windows Vista

-   您的裝置將不再顯示於公司入口網站，而且您將無法再從公司入口網站安裝應用程式。

-   如果您已安裝 Intune 用戶端軟體，則會從電腦予以移除。

-   從電腦移除 Intune Endpoint Protection 軟體。 若電腦上已有安裝並停用其他病毒防護軟體，可以在移除 Intune Endpoint Protection 之後重新啟用。 從公司入口網站移除之後，請檢查您的電腦。

    > [!IMPORTANT]
    > 如果其他防毒軟體未重新啟用，或是沒有安裝其他病毒防護軟體，您的電腦可能容易遭受病毒和惡意程式碼威脅。

-   您在新增裝置時變更的任何裝置設定 (例如停用相機) 皆會失效。

-   您的電腦不會再會收到 Intune 服務所發送的自動軟體更新或防毒軟體更新， 但可能仍會繼續收到 Windows Server Update Services、Windows Update 或 Microsoft Update 的發送的更新，視電腦的設定而定。

此外，針對 Windows 8.1：

-   您無法再使用裝置上的公司應用程式和公司資料。

-   有一些電子郵件應用程式 (例如 Windows Mail) 將無法再存取儲存在您裝置上的公司電子郵件。

-   您可能無法使用 Wi-Fi 或虛擬私人網路連線到您的公司網路。

-   您可能無法再存取裝置上的某些公司資源，例如檔案共用或內部網站。

## <a name="windows-10-mobile-and-windows-phone-81"></a>Windows 10 Mobile 和 Windows Phone 8.1

-   公司入口網站應用程式會從您的裝置解除安裝。 這表示您的裝置將不再顯示於公司入口網站，而且您也無法再從公司入口網站應用程式或公司入口網站安裝應用程式。

-   您無法再使用裝置上的公司應用程式和公司資料。

-   您在新增裝置時變更的任何裝置設定 (例如停用相機或要求特定密碼長度) 皆會失效。

    > [!IMPORTANT]
    > 唯一例外是加密原則，其仍然有效。 若您的公司原則要求您加密您的 Windows Phone，唯一將手機解密的方法是使用 [設定] 功能表進行重設。

## <a name="windows-rt-running-windows-81"></a>執行 Windows 8.1 的 Windows RT

-   公司入口網站應用程式會從您的裝置解除安裝。 這表示您的裝置將不再顯示於公司入口網站，而且您將無法再從公司入口網站安裝應用程式。

-   您無法再使用裝置上的公司應用程式和公司資料。

-   您在新增裝置時變更的任何裝置設定 (例如停用相機或要求特定密碼長度) 皆會失效。

-   您可能無法再使用 Wi-Fi 或虛擬私人網路連線到您的公司網路。

-   您可能無法再存取裝置上的某些公司資源，例如檔案共用或內部網站。

-   有一些電子郵件應用程式 (例如 Windows Mail) 將無法再存取儲存在您裝置上的公司電子郵件。

當您移除 Windows RT 裝置時，將會發生下列情況：

-   公司入口網站應用程式會從您的裝置解除安裝。 這表示您的裝置將不再顯示於公司入口網站，而且您將無法再從公司入口網站安裝應用程式。

-   您無法再使用裝置上的公司應用程式和公司資料。

-   您在新增裝置時變更的任何裝置設定 (例如停用相機或要求特定密碼長度) 皆會失效。

如有任何問題，請連絡您的 IT 系統管理員。 如需連絡資訊，請查看[公司入口網站](http://portal.manage.microsoft.com)。
