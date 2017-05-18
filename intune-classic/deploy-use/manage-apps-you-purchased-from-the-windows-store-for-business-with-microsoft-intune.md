---
title: "管理商務用 Windows 市集應用程式 | Microsoft Docs"
description: "如果您想要從 Intune 主控台管理和部署大量購買的應用程式，請將 Microsoft Intune 連線至商務用 Windows 市集"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e38d47d-0c5e-40ce-b379-29d3657f5c28
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: a57ac0e6cb29dbfc87bb09c04bb372228a1d72be
ms.openlocfilehash: 34e9ce6a5c0b7cb912a54644e6323574c2e041a7


---

# <a name="manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune"></a>以 Microsoft Intune 管理購自商務用 Windows 市集的應用程式

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

[商務用 Windows 市集](https://www.microsoft.com/business-store)可讓您為組織個別或大量尋找和購買應用程式。 將市集連接到 Microsoft Intune，您就可以從 Intune 主控台管理大量購買的應用程式。 例如：
* 您可以同步處理您使用 Intune 從市集購買的應用程式的清單。
* 同步處理的應用程式會出現在 Intune 管理主控台，而您可以如同任何其他應用程式一般加以部署。
* 您可以追蹤有多少可用的授權，以及 Intune 管理主控台中正使用多少授權。
* 如果可用授權數目不足，Intune 會禁止部署及安裝應用程式。

## <a name="before-you-start"></a>開始之前
從商務用 Windows 市集開始同步處理及部署應用程式之前，請檢閱下列資訊︰
* 您必須將 Intune 設定為組織的行動裝置管理授權單位。 如需詳細資訊，請參閱 [Microsoft Intune 中註冊裝置的必要條件](prerequisites-for-enrollment.md)。
* 您必須已在商務用 Windows 市集註冊帳戶。
* 一旦您將 Intune 與企業用 Windows 市集帳戶建立關聯，未來將無法變更為不同帳戶。
* 從市集購買的應用程式無法手動加入 Intune 中，或從中刪除。 它們只能與商務用 Windows 市集同步。
* Intune 只會同步處理您透過商務用 Windows 市集購買的線上授權應用程式。
* 裝置必須已加入 Active Directory 網域服務或工作場所，才能使用這項功能。
* 註冊的裝置必須使用 Windows 10 的 1511 版本。

## <a name="associate-your-windows-store-for-business-account-with-intune"></a>將您的商務用 Windows 市集帳戶與 Intune 相關聯
在 Intune 主控台中啟用同步處理之前，您必須將您的市集帳戶設定為使用 Intune 做為管理工具︰
1. 請確定使用您用來登入 Intune 的相同租用戶帳戶來登入商務用市集。
2. 在商務用市集中，選擇 **[設定]** > **[管理工具]**。
3. 在 [管理工具] 頁面上，選擇 **[Add a management tool (新增管理工具)]**，然後選擇 **[Microsoft Intune]**。

> [!NOTE]
> 如果您使用多種管理工具來部署商務用 Windows 市集應用程式，以前只能建立其中一種與商務用 Windows 市集的關聯性。 現在可以建立多種管理工具與市集的關聯性，例如，Intune 和 Configuration Manager。

您現在可以繼續進行，並在 Intune 主控台中設定同步處理。

## <a name="configure-synchronization"></a>設定同步處理

1. 在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 **[系統管理]**。
2. 在 [管理] 工作區中，展開 [行動裝置管理] > [Windows]，然後選擇 [商務用市集]。
3. 在**商務用 Windows 市集**頁面上，執行下列動作︰
 * 如果您尚未這樣做，請按一下連結以註冊使用商務用 Windows 市集。
 * 一旦註冊完成，請選擇 **[設定同步處理]**。
4. 在 **[設定商務用 Windows 市集應用程式同步]** 對話方塊中，選取 **[啟用商務用 Windows 市集同步]**。
5. 從 [語言] 下拉式清單中，選擇來自商務用 Windows 市集的應用程式將會在 Intune 主控台中顯示的語言。 無論顯示的語言為何，可用時將以使用者的語言安裝。
6. 按一下 [ **確定**]。

## <a name="synchronize-apps"></a>同步處理應用程式

1. 在 **[商務用 Windows 市集]** 頁面上，選擇 **[立即同步]** 來同步處理您使用 Intune 從市集購買的應用程式。
2. 在 [應用程式] 工作區中，選擇 [應用程式] > [大量採購應用程式] 來檢視您可以部署的應用程式，並確認已正確匯入您所購買的應用程式。 此節點中的應用程式會顯示，並加上您所擁有的授權總數，以及您可以使用的授權數目。
例如，您可以從商務用 Windows 市集購買公司入口網站應用程式 (線上授權)，將它同步到 Intune 主控台，然後做為必要 App 部署到需要的 Windows 10 裝置中。 


## <a name="deploy-apps"></a>部署 App

您可以使用與部署任何其他 Intune 應用程式的相同方式，部署來自市集的應用程式。 如需詳細資訊，請參閱[在 Microsoft Intune 中部署應用程式](deploy-apps-in-microsoft-intune.md)
當您部署商務用 Windows 市集應用程式時，安裝應用程式的每個使用者會耗用一個授權。 如果您對某個已部署的應用程式使用所有可用的授權，將無法再部署任何複本。 您必須採取下列其中一個動作：
* 從某些裝置解除安裝應用程式。
* 將目前部署的範圍減少，僅以您擁有足夠授權的使用者為目標。
* 從商務用 Windows 市集購買更多份應用程式。

> [!Important]
> 只有原先註冊裝置的使用者可使用已部署的應用程式。 其他使用者都不能存取應用程式。


### <a name="see-also"></a>請參閱
[在 Microsoft Intune 中新增行動裝置的應用程式](add-apps-for-mobile-devices-in-microsoft-intune.md)



<!--HONumber=Feb17_HO1-->


