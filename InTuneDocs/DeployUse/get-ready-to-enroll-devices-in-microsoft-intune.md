---
# required metadata

title: 準備在 Microsoft Intune 中註冊裝置 | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 44fd4af0-f9b0-493a-b590-7825139d9d40

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 準備在 Microsoft Intune 中註冊裝置
若要讓員工向 Intune 註冊行動裝置 (包括 Android、iOS 和 Windows Phone，以及 Windows 電腦)，您必須啟用裝置註冊。 若要允許註冊，您必須設定行動裝置管理授權單位、設定 Intune 公司入口網站、指派授權，以及啟用裝置平台的註冊。

## <a name="BKMK_Set_MDM_Authority"></a>設定行動裝置管理授權單位
MDM 授權單位會定義有權管理一組裝置的管理服務。 MDM 授權單位選項包括 Intune 自身己以及具備 Intune 的 Configuration Manager。 如果您將 Configuration Manager 設定為管理授權單位，就不能使用其他服務管理行動裝置。

>[!IMPORTANT]
> 請仔細考慮只要使用 Intune (線上服務) 還是具備 Intune 的 System Center Configuration Manager (內部部署軟體解決方案與線上服務搭配使用) 來管理行動裝置。 行動裝置管理授權單位在設定之後便無法再做變更。



1.  在 [Microsoft Intune 管理主控台](http://manage.microsoft.com)中，按一下 [管理] &gt; [行動裝置管理]。

2.  在 [工作]  清單中，按一下 [設定行動裝置管理授權單位] 。 [設定 MDM 授權單位]  對話方塊隨即開啟。

    ![[設定 MDM 授權單位] 對話方塊](../media/intune-mdm-authority.png)

3.  Intune 要求您確認是否要以 Intune 做為 MDM 授權單位。 核取該方塊，然後按一下 [是]  ，以使用 Microsoft Intune 管理行動裝置。

## 設定 Intune 公司入口網站並指派授權
Intune 公司入口網站可協助使用者存取公司資源 (例如應用程式)、尋找技術支援資訊，以及註冊和取消註冊裝置。 註冊裝置之前，您應該[設定公司入口網站](/intune/get-started/get-started-with-a-paid-subscription-to-microsoft-intune-step-7)。 您也必須[指派使用者授權](/intune/get-started/get-started-with-a-paid-subscription-to-microsoft-intune-step-4)，才能允許存取 Intune。

## 設定裝置管理
設定 MDM 授權單位之後，您需要設定您組織想要支援之作業系統的裝置管理。 設定裝置管理所需的步驟會因作業系統而不同。 例如，Android 作業系統不需要您在 Intune 管理主控台中採取任何動作。 另一方面，Windows 和 iOS 需要裝置與 Intune 之間有信任關係，才能允許管理。

> [!div class="op_single_selector"]
- [在 Microsoft Intune 上設定 Android 管理](set-up-android-management-with-microsoft-intune.md)
- [Set up iOS and Mac management with Microsoft Intune](set-up-ios-and-mac-management-with-microsoft-intune.md)
- [使用 Microsoft Intune 設定 Windows Phone 管理](set-up-windows-phone-management-with-microsoft-intune.md)
- [使用 Microsoft Intune 設定 Windows 裝置管理](set-up-windows-device-management-with-microsoft-intune.md)

您也可以：
 - 使用[裝置註冊管理員帳戶](enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune.md)註冊多部裝置
 - [使用 IMEI 數字指定公司擁有的裝置](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md)協助註冊裝置和目標原則


<!--HONumber=May16_HO2-->


