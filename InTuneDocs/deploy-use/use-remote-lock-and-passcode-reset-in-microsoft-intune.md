---
title: "遠端鎖定和密碼重設 | Microsoft Docs"
description: "Intune 提供遠端鎖定和密碼重設功能。"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 03/06/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 970f8c81-7c7f-4789-9ed4-2133d50b9db6
ms.reviewer: chrisgre
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 665d3347636d5ec0c698ffb93b768028c9d59ce3
ms.openlocfilehash: b918c9843bdc6cfbbfd9c2da9d698b255487152c
ms.lasthandoff: 03/07/2017

---
# <a name="help-protect-your-devices-with-remote-lock-and-passcode-reset"></a>透過遠端鎖定或密碼重設來協助保護您的裝置

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune 提供遠端鎖定和密碼重設功能。

## <a name="lock-a-device-remotely"></a>從遠端鎖定裝置
如果使用者遺失裝置，您可以從遠端鎖定裝置。 裝置上必須已設定 PIN 或密碼，您才能使用遠端鎖定。

下表列出遠端鎖定在不同行動平台上的運作方式。

|平台|遠端鎖定|
|------------|---------------|
|macOS|不支援|
|iOS|支援|
|Android|支援|
|Android for Work|支援|
|Windows 10 (行動裝置)|支援|
|Windows 10 (桌面)|不支援|
|Windows Phone 8 和 Windows Phone 8.1|支援|
|Windows RT 8.1 和 Windows RT|如果目前的裝置使用者和註冊裝置的使用者是同一位時便支援。|
|Windows 8.1|如果目前的裝置使用者和註冊裝置的使用者是同一位時便支援。|

註冊了 Intune 軟體用戶端的 Windows 電腦不支援遠端鎖定。

### <a name="lock-a-mobile-device-remotely-through-the-intune-console"></a>透過 Intune 主控台從遠端鎖定行動裝置

1.  在 [Intune 系統管理員主控台](https://manage.microsoft.com/)中，選擇 [群組] &gt; [所有裝置] &gt; [所有行動裝置]。

2.  對已在 Intune 註冊的裝置選擇 [所有受直接管理的裝置] 或按一下 [所有受 Exchange ActiveSync 管理的裝置]。

    > [!TIP]
    > 您也可以導覽到各使用者的裝置。 選擇 [所有使用者]。 在使用者的內容頁面上，選擇 [裝置]，然後選擇您要鎖定之行動裝置的名稱。

3.  在清單中，選擇您要鎖定的一或多部裝置。 在工作列上，選擇 [遠端工作]，然後選取 [遠端鎖定]。

## <a name="reset-the-passcode-on-a-device"></a>重設裝置上的密碼
如果使用者忘記密碼，您可以從裝置移除密碼或是在裝置上強制套用新的暫時密碼，以幫助使用者。 下表列出密碼重設在不同行動平台上的運作方式。

|平台|密碼重設|
|------------|------------------|
|macOS|不支援|
|iOS|支援從裝置清除密碼。 不會建立新的暫時密碼。|
|Android|支援 Android 7.0 之前的版本。 建立暫時密碼。|
|Android for Work|不支援|
|Windows 10 Mobile|支援|
|Windows Phone 8 和 Windows Phone 8.1|支援|
|Windows RT 8.1|不支援|
|Windows 8.1|不支援|
|Windows 10 Desktop|不支援|

註冊了 Intune 軟體用戶端的 Windows 電腦不支援密碼重設。

### <a name="reset-a-passcode"></a>重設密碼

1.  在 [Intune 系統管理員主控台](https://manage.microsoft.com/)中，選擇 [群組] &gt; [所有裝置] &gt; [所有行動裝置]。

2.  對已在 Intune 註冊的裝置選擇 [所有受直接管理的裝置] 或按一下 [所有受 Exchange ActiveSync 管理的裝置]。

    > [!TIP]
    > 您也可以導覽到各使用者的裝置。 按一下 [所有使用者]。 在使用者的 [內容] 頁面上，按一下 [裝置]，然後按一下您要抹除之行動裝置的名稱。

3.  在清單中，選擇您要鎖定的一或多部裝置。 在工作列上，選擇 [遠端工作]，然後選取 [密碼重設]。


### <a name="see-also"></a>請參閱
[淘汰裝置](retire-devices-from-microsoft-intune-management.md)和 [Windows Selective Wipe for Device Data Management](http://technet.microsoft.com/library/dn486874.aspx) (裝置資料管理的 Windows 選擇性抹除)

