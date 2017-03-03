---
title: "管理裝置上的 iOS 啟用鎖定 | Microsoft Docs"
description: "Microsoft Intune 可以協助您管理 iOS 啟用鎖定，這是 iOS 7.1 和更新版本裝置之「尋找我的 iPhone」應用程式中的一項功能。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb49e926-15c4-4f01-b6eb-cee6f7ee1984
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: d05c9d7a78474c19e142bca94e232289fbfba1d9
ms.openlocfilehash: a6fa910c0a8ec1a9542e03a276dbb8d0757d75b4
ms.lasthandoff: 01/10/2017


---

# <a name="help-protect-ios-devices-with-activation-lock-bypass-for-microsoft-intune"></a>使用 Microsoft Intune 的啟用鎖定略過協助保護 iOS 裝置

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune 可以協助您管理 iOS 啟用鎖定，這是 iOS 8.0 和更新版本裝置之「尋找我的 iPhone」應用程式中的一項功能。 當使用者在裝置上開啟「尋找我的 iPhone」應用程式時，啟用鎖定會自動啟用。 啟用之後，就必須輸入使用者的 Apple ID 和密碼，才能夠讓所有人： 

-   關閉「尋找我的 iPhone」

-   清除裝置

-   重新啟動裝置

## <a name="how-activation-lock-affects-you"></a>啟用鎖定對您的影響
雖然啟用鎖定可以協助保護 iOS 裝置，並提高裝置遺失或遭竊時的復原機會，但是這項功能可能會為身為 IT 系統管理員的您帶來一些挑戰。 例如：

-   一位使用者在裝置上設定啟用鎖定。 使用者之後離職並歸還裝置。 如果沒有使用者的 Apple ID 和密碼，就無法重新啟動裝置。

-   您需要一份啟用鎖定已啟用之所有裝置的報表。

-   在重新整理組織中的裝置期間，您想要將某些裝置重新指派給不同的部門。 您只能重新指派啟用鎖定未啟用的裝置。

為了協助解決這些問題，Apple 在 iOS 7.1 中引進了啟用鎖定略過。 這可讓您從沒有使用者的 Apple ID 和密碼的受監督裝置移除啟用鎖定。 受監督的裝置會產生裝置特定啟用鎖定略過碼，並儲存在 Apple 啟用伺服器上。

> [!TIP]
> iOS 裝置的受監督模式可讓您使用 Apple Configurator 鎖定裝置，並將功能限制在特定商務用途。 受監督的模式通常僅適用於屬公司擁有的裝置。

## <a name="how-intune-helps-you-manage-activation-lock"></a>Intune 如何協助您管理啟用鎖定
Intune 可以要求執行 iOS 8.0 和更新版本之受監督裝置的啟用鎖定狀態。 僅針對受監督的裝置，Intune 可以擷取啟用鎖定略過碼並直接發給裝置。 如果已抹除裝置，您可以使用空白使用者名稱和代碼作為密碼，進而直接存取裝置。

**這對公司的好處包括**：

-   使用者可以獲得「尋找我的 iPhone」應用程式的安全性優點。

-   您可以讓使用者執行工作，並使其知道在需要重新規劃裝置時，您可將裝置淘汰或解除鎖定。

## <a name="how-to-use-activation-lock-bypass-from-the-intune-admin-console"></a>如何從 Intune 管理主控台使用啟用鎖定略過
> [!IMPORTANT]
> 略過裝置上的啟用鎖定之後，如果「尋找我的 iPhone」應用程式處於開啟狀態，則會自動套用新的啟用鎖定。 因此，**您應該實際擁有裝置，才能執行這個程序**。

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 **[群組]** &gt; **[所有裝置]** &gt; **[所有屬公司擁有的裝置]**。

2.  選取您要略過啟用鎖定的裝置。 選擇 [啟用鎖定略過]。

3.  請閱讀警告訊息。 選擇 [是] 繼續進行。

您可以在裝置的詳細資料頁面上，查看解除鎖定要求的狀態。

## <a name="how-to-see-which-devices-are-using-activation-lock"></a>如何查看哪些裝置使用啟用鎖定
您可以透過兩個方式來查看哪些裝置使用啟用鎖定：

-   執行 [行動裝置清查報表] 。 這份報表顯示 **[啟用鎖定狀態]** 和 **[受監督]** 資料行，以表示裝置的狀態。 [受監督]  的值為 [是]  或 [否] ，而 [啟用鎖定狀態]  的值包括：

    -   啟用時使用略過碼

    -   啟用時不使用略過碼 (裝置不受監督)

    -   啟用時不使用略過碼 (無法連線到裝置)

    -   未啟用

    未執行 iOS 8.0 或更新版本之裝置的 [啟用鎖定狀態] 方塊為空白。

-   在群組檢視中選取一部裝置，以便在裝置詳細資料窗格中顯示啟用鎖定狀態。

    如果您在 **[所有屬公司擁有的裝置]** 節點中選取一部裝置，並啟用裝置的啟用鎖定，也會顯示略過碼。 您可以使用這個代碼，手動發出啟用鎖定略過。

    > [!IMPORTANT]
    >Intune 每七天會針對啟用鎖定對裝置進行清查。 因此，裝置可能無法立即在 Intune 主控台中顯示它們的啟用鎖定狀態。


### <a name="see-also"></a>請參閱
[淘汰裝置](retire-devices-from-microsoft-intune-management.md)
[透過遠端鎖定或密碼重設來協助保護您的裝置](use-remote-lock-and-passcode-reset-in-microsoft-intune.md)

