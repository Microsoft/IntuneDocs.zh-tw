---
title: "將 Windows Holographic 升級至 Windows Holographic for Business"
titleSuffix: Microsoft Intune
description: "了解如何將執行 Windows Holographic 的裝置升級至 Windows Holographic for Business"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e7c750b372c297637abcdb9e941dae17714d081b
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2018
---
# <a name="upgrade-devices-running-windows-holographic-to-windows-holographic-for-business"></a>將執行 Windows Holographic 的裝置升級至 Windows Holographic for Business


若要使用 Microsoft Intune 管理執行 Windows Holographic 的裝置，您必須將裝置從 Windows Holographic 升級至 Windows Holographic for Business。 您可以建立版本升級設定檔來進行升級。 至於 Microsoft HoloLens，您則可購買 Commercial Suite，以取得升級所需的授權。 如需詳細資訊，請參閱[解除鎖定 Windows Holographic for Business 功能](https://docs.microsoft.com/en-us/hololens/hololens-upgrade-enterprise)。

## <a name="to-set-up-an-edition-upgrade-device-configuration-profile"></a>設定版本升級裝置組態設定檔

1. 使用系統管理員帳戶登入 [Azure 入口網站](https://portal.azure.com)。


2.  按一下 [裝置設定]、[設定檔]，然後按一下 [+ 建立設定檔]。

    ![建立設定檔](media/Holographic-create-profile.png)

3.  在 [建立設定檔] 頁面中，鍵入設定檔的名稱，將平台選取為 [Windows 10 和更新版]，然後將設定檔類型選取為 [版本升級]。 按一下 [進行設定]。

5. 在 [版本升級] 頁面中，在 [要升級到的版本] 上，選取 [Windows 10 Holographic for Business]。 在 [授權檔案] 上，瀏覽至提供給您的 XML 授權檔案並加以選取。

    ![輸入 XML 檔案名稱](media/Holographic-edition-upgrade.png)
 
5.  按一下 [確定]，然後按一下 [建立] 來建立設定檔。


## <a name="deploy-the-edition-upgrade-policy"></a>部署版本升級原則

接下來，將版本升級設定檔指派給選取的群組或裝置。

1. 在您上一步建立的設定檔上，按一下 [指派]。

2. 在 [指派] 頁面中，選取您想要包含與排除原則的使用者群組與裝置。

![包含與排除群組](media/Holographic-groups.PNG)

當這些使用者或裝置在 Intune 中註冊時，會套用版本升級設定檔。 

## <a name="next-steps"></a>接下來的步驟

如需詳細資訊，請參閱[開始使用群組](get-started-groups.md)。


