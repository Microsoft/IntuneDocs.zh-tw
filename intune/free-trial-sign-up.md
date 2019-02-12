---
title: 快速入門 - 免費試用 Microsoft Intune
titlesuffix: ''
description: 在此快速入門中，您將建立免費試用訂用帳戶、了解支援的設定和網路需求，並選擇性地設定您的網域名稱。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/06/2019
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 195931c0-8208-43bd-b0af-b1f8e469a32c
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b0ed363acca7fc0021569009b1f672a06101e29f
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/07/2019
ms.locfileid: "55834172"
---
# <a name="quickstart-try-microsoft-intune-for-free"></a>快速入門：免費試用 Microsoft Intune 

Microsoft Intune 透過管理裝置和應用程式來協助您保護員工的公司資料。 在此快速入門中，您將建立免費訂用帳戶，以在測試環境中試用 Intune。

Intune 從透過 Microsoft Azure 入口網站管理的安全雲端式服務，提供行動裝置管理 (MDM) 與行動應用程式管理 (MAM)。 使用 Intune，您可以確保正確設定、存取及更新員工的公司資源 (資料、裝置和應用程式)，以符合您公司的合規性原則和需求。 

## <a name="prerequisites"></a>必要條件
設定 Microsoft Intune 之前，請先檢閱下列需求：

   - [支援的作業系統與瀏覽器](supported-devices-browsers.md) 
   - [網路設定需求與頻寬](network-bandwidth-use.md)

## <a name="sign-up-for-a-microsoft-intune-free-trial"></a>註冊 Microsoft Intune 免費試用

免費試用 Intune 30 天。 如果您已經有工作或學校帳戶，請**登入**該帳戶，並將 Intune 新增您的訂閱。 否則，您可以**註冊**新帳戶供您的組織使用 Intune。

> [!IMPORTANT]
> 註冊新帳戶後，無法合併現有的工作或學校帳戶。

1. 前往 [Microsoft Intune 試用](https://go.microsoft.com/fwlink/?linkid=2019088)頁面並填寫表單。

    ![Microsoft Intune 試用帳戶註冊網頁的螢幕擷取畫面](./media/account-sign-up-site-full-browser.png)

    若您大部分的 IT 作業與使用者分屬於不同的地區設定，建議您在 [國家或地區] 下選取該地區設定。 Azure 會使用您的區域資訊來提供適當的服務。 稍後無法變更此設定。

2. 使用您的公司名稱後面接著 **.onmicrosoft.com** 來建立帳戶。 

    ![Intune 試用版帳戶新增認證程序的螢幕擷取畫面](./media/account-sign-up-site-user-id.png)

    如果您組織本身有您想要使用但不含 **.onmicrosoft.com** 的自訂網域，您可以在 Office 365 管理入口網站中進行變更，如本文稍後所述。

3. 在註冊程序結束時，檢視您的新帳戶資訊。

    ![帳戶資訊的影像](./media/intune-end-of-sign-up-process.png) 

## <a name="sign-in-to-the-azure-portal"></a>登入 Azure 入口網站

1. 開啟新的瀏覽器視窗，然後在網址列中輸入 **https://portal.azure.com** 。 
2. 使用上述步驟中提供給您的認證登入。

    ![Azure 入口網站登入頁面的影像](./media/azure-portal-signin.png)

3. 若要在 Azure 入口網站中檢視 Microsoft Intune，請從頁面左側邊欄，選取 [所有服務]。
4. 在篩選方塊中，搜尋並選取 **Microsoft Intune**。
5. 選取**星狀**以將 Intune 新增至我的最愛服務清單底部，然後開啟 Intune 儀表板。

當您註冊試用版時，您也會收到電子郵件訊息，其中包含您在註冊程序期間提供的帳戶資訊和電子郵件地址。 本電子郵件可確認您的試用版是使用中的狀態。

> [!TIP]
> 使用 Azure 入口網站時，在一般模式下使用瀏覽器可能會獲得更好的結果，而不是私用模式。

## <a name="set-the-mdm-authority-to-intune"></a>將 MDM 授權單位設定為 Intune

在登入 Azure 入口網站並選取 Intune 後，您可能會看到橙色橫幅，指出您尚未設定 MDM 授權單位。 行動裝置管理 (MDM) 授權單位設定會決定您管理裝置的方式。 在使用者可以註冊裝置以進行管理之前，必須先設定 MDM 授權單位。

若要將 MDM 授權單位設定為 Intune，請執行下列步驟。

1. 開啟新的瀏覽器視窗，然後在網址列中輸入 **https://portal.azure.com** 。 
2. 選擇 [所有服務] > [Microsoft Intune]。
3. 選取指出您尚未啟用裝置管理的橫幅，或如果您沒有立即看到橫幅，請選取 [裝置註冊]。 如果您尚未啟用裝置管理，會顯示 [選擇 MDM 授權單位] 刀鋒視窗。

    > [!NOTE]
    > 只有在您尚未設定 MDM 授權單位時，才會顯示橙色橫幅。

    ![選擇 MDM 授權單位刀鋒視窗的影像](./media/choose-mdm-authority.png) 

4. 在 [選擇 MDM 授權單位] 下，將您的 MDM 授權單位設定為 [Intune MDM 授權單位]。

如需 MDM 授權單位的詳細資訊，請參閱[設定行動裝置管理授權單位](mdm-authority-set.md)。

## <a name="configure-your-custom-domain-name-optional"></a>設定您的自訂網域名稱 (選擇性)

如上所述，如果您的組織本身有您想要使用但不含 **.onmicrosoft.com** 的自訂網域，您可以在 Office 365 管理入口網站中進行變更。 您將新增、驗證及設定自訂網域名稱。  

> [!IMPORTANT]
> 您無法重新命名或移除初始的 **onmicrosoft.com** 網域名稱。 您可以新增、驗證或移除 Intune 使用的自訂網域名稱，以利企業識別。

1. 前往 [Office 365 管理入口網站](https://portal.office.com/Admin/Default.aspx) 並使用您的系統管理員帳戶登入。

2. 在瀏覽窗格中，選擇 [設定] > [網域] > [新增網域]。

3. 鍵入您的自訂網域名稱。 然後，選取 [下一步]。

   ![Office 365 系統管理中心 - [新增網域] 的螢幕擷取畫面](./media/domain-custom-add.png)

4. 確認您是如上所輸入的網域擁有者。 
    
    選取 [透過電子郵件傳送驗證碼] 會傳送電子郵件給您網域中已註冊的連絡人。 收到電子郵件之後，請複製驗證碼，並在標示為 [在這裡輸入您的驗證碼]  的欄位中輸入。 如果驗證碼符合，則會將網域新增至您的租用戶。 顯示的電子郵件看起來可能很陌生。 某些註冊機構會隱藏註冊網域時所提供的實際電子郵件地址。

   ![Office 365 系統管理中心 - [驗證網域] 的螢幕擷取畫面](./media/domain-custom-verify.png)

   > [!NOTE]
   > 如需 TXT 記錄驗證詳細資料，請參閱[在任一 DNS 主機服務提供者建立 Office 365 的 DNS 記錄](https://support.office.com/article/Create-DNS-records-at-any-DNS-hosting-provider-for-Office-365-7B7B075D-79F9-4E37-8A9E-FB60C1D95166)。

## <a name="admin-experiences"></a>管理體驗

您可能使用的有兩個入口網站：
- Azure ([portal.azure.com](https://portal.azure.com)) 中的 Intune 儀表板是您可以瀏覽 [Intune 功能](what-is-intune.md)的位置。 一般是在 Intune 儀表板中執行工作。
- Office 365 系統管理中心 ([portal.office.com](https://portal.office.com)) 是您可以新增及管理使用者的位置 (若未使用 Azure Active Directory)。 您也可以管理您帳戶的其他事宜，包括計費及支援。

## <a name="next-steps"></a>後續步驟

在此快速入門中，您已建立免費訂用帳戶，以在測試環境中試用 Intune。 如需設定 Intune 的詳細資訊，請參閱[設定 Intune](setup-steps.md)。

若要遵循此 Intune 快速入門系列，請繼續前往下一個快速入門。

> [!div class="nextstepaction"]
> [快速入門：建立使用者並為其指派授權](quickstart-create-user.md)
