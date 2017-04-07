---
title: "不符合標準時所採取的動作"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解如何為不符合標準的裝置建立動作"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d0e0c4b-a562-44f3-82a4-80eb688d4733
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: deea78dcea9ade031441bf12b388a862235a8e9c
ms.openlocfilehash: 16da087e741e335144266c838c0a91050bd7d520
ms.lasthandoff: 03/15/2017


---

# <a name="create-actions-for-non-compliance"></a>為不符合標準的情況建立動作

[不符合標準時所採取的動作] 可讓您設定按時間順序的動作序列，以套用到不符合標準的裝置。 例如，您可以透過電子郵件通知不合標準裝置的使用者，或透過條件式存取封鎖這些裝置對公司資源的存取。

## <a name="use-case-scenario"></a>使用案例

根據預設，一旦裝置由 Intune 裝置合規性政策回報為不符合標準時，條件式存取會立即封鎖該裝置，而且使用者會收到一封電子郵件說明符合標準的指示。 [不符合標準時所採取的動作] 讓您可以更靈活地決定該怎麼處置不符合標準的裝置。 例如，您可以決定不立即封鎖裝置，然後給使用者一個寬限期，讓其符合標準。

動作有兩種：

-   透過電子郵件通知使用者

-   透過條件式存取封鎖對公司資源的存取

## <a name="notify-the-user-via-email"></a>透過電子郵件通知使用者

您可以選擇預先建立的預設電子郵件範本，或建立完全自訂的電子郵件通知。 我們提供主旨、郵件內文的自訂功能，包含公司標誌、連絡資訊和其他收件者。

## <a name="block-corporate-resource-access-through-conditional-access"></a>透過條件式存取封鎖對公司資源的存取

您可以設定一個天數排程，而裝置在這幾天內存取公司資源的權限將遭到封鎖。 這可以是立即執行，但您也可以給使用者一個寬限期，讓其符合裝置合規性政策。

## <a name="before-you-begin"></a>開始之前

您需要至少建立一個裝置合規性政策，才可以設定不合標準時的動作。

-   了解如何在這些環境中建立裝置合規性政策：

    -   [Android](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-android)

    -   [Android for Work](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-android-for-work)

    -   [iOS](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-ios)

    -   [Windows](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-windows)

當您計劃使用裝置合規性政策來封鎖使用公司資源的裝置，您需要已設定好的 EMS 條件式存取。

- 了解[如何設定 EMS 條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)。

此外，您需要已建立好的通知郵件範本。 通知郵件範本稍後會在建立不符合標準動作程序中使用，做為傳送給使用者的電子郵件之用。

### <a name="to-add-a-notification-message-template"></a>新增通知郵件範本

在 [裝置合規性政策] 刀鋒視窗中：

1.  在 [管理] 底下，選擇 [通知]，[通知] 郵件範本刀鋒視窗隨即開啟。

    ![如何新增通知範本](../media/afnc-1.png)

2.  選擇 [新增]，然後您必須定義下列內容︰

    a.  說明

    b。  寄件者

    c.  主體

    d.  訊息

    e.  電子郵件標頭 – 包含公司標誌

    f.  電子郵件頁尾 – 包含公司名稱

    g.  電子郵件頁尾 – 包含連絡資訊

     ![通知郵件範本](../media/afnc-2.png)

完成新增資訊後，按一下 [建立]。 [通知] 郵件範本便可供使用。

> [!NOTE] 
> 您也可以編輯先前建立的 [通知] 範本。

## <a name="to-create-actions-for-non-compliance"></a>為不符合標準的情況建立動作

您可以在建立新的裝置合規性政策時新增動作，或編輯現有裝置合規性政策的動作。

1.  在 [裝置合規性政策] 刀鋒視窗中的 [管理] 底下，選擇 [政策]。

2.  按一下裝置合規性政策即可選擇它。

    ![合規性政策](../media/afnc-3.png)

3.  [裝置合規性政策內容] 刀鋒視窗隨即開啟，選擇 [不符合標準時所採取的動作]。

4.  [不符合標準時所採取的動作] 刀鋒視窗隨即開啟，選擇 [新增] 並指定動作的參數。

    ![不符合標準時所採取的動作刀鋒視窗](../media/afnc-4.png)

不符合標準時所採取的動作有：

-   **強制條件式存取政策**

-   **傳送電子郵件給使用者**

### <a name="enforce-conditional-access-policy"></a>強制條件式存取政策

為不符合標準的情況新增此動作：

1.  在 [不符合標準時所採取的動作] 刀鋒視窗中選擇 [新增]。

2.  在 [動作參數] 刀鋒視窗中，選取 [動作] 下拉式清單中的 [強制條件式存取原則]。

3.  在 [排程]中，您可以指定強制執行條件式存取原則的天數 (0 到 255)。 如果您指定 **0** 天，表示一旦裝置不符合裝置合規性政策，條件式存取必須「立即」封鎖存取公司資源。

    ![排程不符合標準時所採取的動作](../media/afnc-5.png)

4.  選擇 [新增]，然後在 [動作] 刀鋒視窗中選擇 [確定]。

5.  在 [裝置合規性政策內容] 刀鋒視窗中，選擇 [儲存]。

### <a name="send-e-mail-to-end-user"></a>傳送電子郵件給使用者

您可以使用電子郵件範本傳送給不符合標準的使用者。 這些電子郵件有助於加強整個組織的裝置合規性。

為不符合標準的情況新增此動作：

1.  在 [不符合標準時所採取的動作] 刀鋒視窗中選擇 [新增]。

2.  在 [動作參數] 刀鋒視窗中，選取 [動作] 下拉式清單中的 [傳送電子郵件給使用者]。

3.  按一下 [訊息範本] 即可選擇先前建立的郵件範本。 您可以檢視郵件範本的內容，然後選擇 [選取]。

    ![郵件範本](../media/afnc-6.png)

> [!NOTE] 
> 您可以檢視郵件範本但不編輯。 如果您想要編輯郵件範本，必須回到 [通知] 刀鋒視窗。

1.  在 [排程] 中，輸入發現不符合標準後幾天要將這封電子郵件傳送給使用者。 如果指定 **0** 天，表示「立即」傳送電子郵件。

2.  選擇 [新增]，然後在 [動作] 刀鋒視窗中選擇 [確定]。

3.  在 [裝置合規性政策內容] 刀鋒視窗中，選擇 [儲存]。

