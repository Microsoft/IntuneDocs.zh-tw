---
title: 教學課程 - 使用 AutoPilot 在 Intune 中註冊裝置
titleSuffix: Microsoft Intune
description: 您將在本教學課程中設定 Windows AutoPilot，以在 Intune 中註冊裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/19/2018
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up Windows Autopilot so that users can enroll in Intune.
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: c2d137945325d8ec11801aec225fd0e89196ed05
ms.sourcegitcommit: f8bbd9bac2016a77f36461bec260f716e2155b4a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2019
ms.locfileid: "65733000"
---
# <a name="tutorial-use-autopilot-to-enroll-windows-devices-in-intune"></a>教學課程：使用 Autopilot 在 Intune 中註冊 Windows 裝置
Windows AutoPilot 簡化了裝置註冊程序。 您可以使用 Microsoft Intune 和 AutoPilot，將新的裝置提供給使用者而不需要建置、維護及套用自訂作業系統映像。 

您將在本教學課程中了解如何：
> [!div class="checklist"]
> * 將裝置新增至 Intune
> * 建立 AutoPilot 裝置群組
> * 建立 AutoPilot 部署設定檔
> * 指派 AutoPilot 部署設定檔至裝置群組
> * 將 Windows 裝置散發給使用者

如果您沒有 Intune 訂用帳戶，請[註冊免費試用帳戶](free-trial-sign-up.md)。

如需 Autopilot 的優點、案例和必要條件的概觀，請參閱 [Windows AutoPilot 概觀](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot)。


## <a name="prerequisites"></a>必要條件
- [設定 Windows 自動註冊](quickstart-setup-auto-enrollment.md)
- [Azure Active Directory Premium 訂用帳戶](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->


## <a name="add-devices"></a>新增裝置

設定 Windows AutoPilot 的第一個步驟是將 Windows 裝置新增至 Intune。 您只需要建立 CSV 檔案，然後將它匯入 Intune。

1. 在任何文字編輯器中，建立以逗號區隔值 (CSV，可識別 Windows 裝置) 的清單。 使用下列格式：
    
    *serial-number*、*windows-product-id*、*hardware-hash*、*optional-order-id*
    
    前三個是必要項目，而順序識別碼是選擇性的。

2. 儲存 CSV 檔案。

3. 在 [Azure 入口網站的 Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊] > [Windows 註冊] > [裝置] > [匯入]。

    ![Windows Autopilot 裝置的螢幕擷取畫面](media/enrollment-autopilot/autopilot-import-device.png)

4. 在 [新增 Windows AutoPilot 裝置] 底下，瀏覽至您儲存的 CSV 檔案。

    ![新增 Windows Autopilot 裝置的螢幕擷取畫面](media/enrollment-autopilot/autopilot-import-device2.png)

5. 選擇 [匯入] 開始匯入裝置資訊。 匯入可能需要幾分鐘的時間。

4. 匯入完成後，選擇 [裝置註冊] > [Windows 註冊] > [Windows Autopilot] > [裝置] > [同步處理]。訊息會顯示正在進行同步處理。 程序可能需要幾分鐘才能完成，取決於您同步處理多少部裝置。

5. 重新整理檢視可查看新的裝置。

## <a name="create-an-autopilot-device-group"></a>建立 Autopilot 裝置群組

接下來，您會建立裝置群組，並將您剛載入的 Autopilot 裝置放到群組中。

1. 在 [Azure 入口網站的 Intune](https://aka.ms/intuneportal) 中，選擇 [群組] > [新增群組]。
2. 在 [群組] 刀鋒視窗中：
    1. 針對 [群組類型]，請選擇 [安全性]。
    2. 針對 [群組名稱] 輸入 *Autopilot 群組*。 針對 [群組描述] 輸入 *Autopilot 裝置的測試群組*。
    3. 針對 [成員資格類型] 選擇 [已指派]。
3. 在 [群組] 刀鋒視窗中，選擇 [成員] 並將 Autopilot 裝置加到群組中。 尚未註冊的 Autopilot 裝置為裝置名稱與序號相同的裝置。
4. 選擇 **[建立]**。  

## <a name="create-an-autopilot-deployment-profile"></a>建立 Autopilot 部署設定檔

建立裝置群組之後，必須建立部署設定檔，才能設定 Autopilot 裝置。

1. 在 [Azure 入口網站的 Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊] > [Windows 註冊] > [部署設定檔] > [建立設定檔]。
2. 在 [基本] 頁面上，針對 [名稱] 輸入 *Autopilot 設定檔*。 針對 [描述] 輸入 *Autopilot 裝置的測試設定檔*。
3. 把 [將所有目標裝置轉換為 Autopilot] 設為 [是]。 此設定可確保清單中的所有裝置都會向 AutoPilot 部署服務註冊。 等候 48 小時讓註冊處理完畢。
4. 選取 [下一步]。
5. 在 [首次體驗 (OOBE)] 頁面上，針對 [部署模式] 選擇 [使用者驅動]。 具有此設定檔的裝置會與註冊裝置的使用者相關聯。 需有使用者認證，才能註冊裝置。
6. 在 [加入Azure AD] 方塊中，選擇 [已加入 Azure AD]。
7. 設定下列選項，並將其他選項的設定保留為預設值：
    - **使用者授權合約 (EULA)**：[隱藏]
    - **隱私權設定**：[顯示]
    - **使用者帳戶類型**：[標準]
8. 選取 [下一步]。
9. 在 [指派] 頁面上，針對 [指派至] 選擇 [選取的群組]。
10. 選擇 [選取要納入的群組]，然後選擇 [Autopilot 群組]。
11. 選取 [下一步]。
12. 在 [檢閱 + 建立] 頁面上，選擇 [建立] 以建立設定檔。

## <a name="distribute-devices-to-users"></a>將裝置散發給使用者

您現在就可以將 Windows 裝置散發給您的使用者。 當他們第一次登入時，AutoPilot 系統會自動註冊並設定裝置。 

## <a name="clean-up-resources"></a>清除資源

如果不想再使用 Autopilot 裝置，可以將它們刪除。

1. 如果裝置已在 Intune 中註冊，則必須先[從 Azure Active Directory 入口網站中加以刪除](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal)。

2. 在 [Azure 入口網站的 Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊] > [Windows 註冊] > [裝置]。

3. 在 [Windows Autopilot 裝置] 下，選擇您要刪除的裝置，然後選擇 [刪除]。

4. 選擇 [是] 以確認刪除。 可能需要幾分鐘才能刪除。

## <a name="next-steps"></a>後續步驟

您可以找到 Windows AutoPilot 其他可用選項的相關詳細資訊。

> [!div class="nextstepaction"]
> [深入了解 AutoPilot 註冊文章](enrollment-autopilot.md)


