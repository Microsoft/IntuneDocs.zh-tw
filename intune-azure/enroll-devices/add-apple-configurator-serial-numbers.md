---
title: "新增 Apple Configurator 序號"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解如何將序號新增至公司擁有並使用 Apple Configurator 的 iOS 裝置。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d408aa38-7d1e-40df-9067-246e53f6e26f
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 26d253f013195cc18f9a97b8259c603d707d22bf
ms.lasthandoff: 02/18/2017


---

# <a name="add-apple-configurator-serial-numbers"></a>新增 Apple Configurator 序號

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

想要[使用設定輔助程式的 Apple Configurator 註冊公司擁有的 iOS 裝置](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md)時，請使用下列步驟將序號新增至 Intune。 您可以一次新增一個序號，或上傳序號的逗點分隔值 (CSV) 檔案。 新增序號之後，可以為其指派一個設定檔。 設定檔包含您要套用到裝置的特定管理設定。

註冊 iOS 裝置的其他方法，詳述於 [Choose how to enroll iOS devices in Intune](choose-ios-enrollment-method.md) (選擇如何在 Intune 中註冊 iOS 裝置)。

**將 Apple Configurator 序號新增至 Intune**

1. 建立內含兩個資料行，但不含標題的逗點分隔值 (.csv) 清單。 在左資料行中新增 IMEI 識別碼，在右資料行中新增詳細資料。 清單目前最多可容納 500 個資料列。 在文字編輯器中，.csv 的外觀類似如下：

    F7TLWCLBX196,device details</br>
    DLXQPCWVGHMJ,device details

2. 在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。

3.  在 Intune 刀鋒視窗上，選擇 [註冊裝置]，然後選擇 [Apple 註冊]。

4. 從 [管理 Apple Configurator 註冊設定] 下選取[Apple Configurator 序號]。

5. 在 [Apple Configurator 序號] 刀鋒視窗中選取 [新增]。

6. 在 [新增序號] 刀鋒視窗中，選取要套用到所匯入之序號的設定檔。 若要匯入的檔案內含會覆寫現有詳細資料的新詳細資料，請選取 [覆寫現有識別碼的詳細資料]，以新的詳細資料取代現有的詳細資料。

7. 瀏覽至序號的 .csv 檔案，並選取 [新增]。

## <a name="assign-a-profile-to-specific-serial-numbers"></a>將設定檔指派給特定的序號

Intune 可讓您從 Azure 入口網站中兩個的不同位置指派設定檔。 您可以使用下列步驟，或從您建立設定檔所在的 [Apple Configurator 註冊設定檔] 刀鋒視窗中指派設定檔 (請參閱[使用設定輔助程式的 Apple Configurator 註冊 iOS 裝置](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md))。 您必須先建立設定檔，才能使用下列步驟指派設定檔。

1. 在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。

2. 在 Intune 刀鋒視窗上，選擇 [註冊裝置]，然後選擇 [Apple 註冊]。

3. 在 [Apple Configurator 序號] 刀鋒視窗中，選取您要指派以設定檔的序號，然後選取 [指派設定檔]。

4. 在 [指派設定檔] 刀鋒視窗中，選取您要指派的設定檔，然後選取 [指派]。

## <a name="delete-serial-numbers"></a>刪除序號
您可以刪除先前所匯入的序號。 必須先取消註冊裝置，才能刪除序號。 當您移除序號之後，除非重新新增序號，否則將無法再透過設定助理使用 Apple Configurator。

## <a name="view-the-state-of-a-device"></a>檢視裝置狀態
裝置序號的狀態可以是下列兩種之一︰

- 已註冊 - 裝置已註冊，並已連線到 Intune 服務
- 未連線 - 裝置從未連線到 Intune 服務。
- 待重設 - 裝置已註冊，但有所變更 (例如註冊設定或已套用的 DEP 設定檔有所變更)。 若變更裝置的 DEP 設定檔，必須在取消註冊再重新註冊裝置之後，才會套用變更。

**檢視序號的狀態**

在 [Apple Configurator 序號] 刀鋒視窗中選取您要檢視狀態的序號，再檢視 [狀態]項目下方。

