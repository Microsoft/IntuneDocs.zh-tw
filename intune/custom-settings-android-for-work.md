---
title: "針對 Android for Work 的 Intune 自訂設定檔設定"
titlesuffix: Azure portal
description: "了解如何針對 Android for Work 裝置建立 Intune 自訂設定檔設定。"
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4724d6e5-05e5-496c-9af3-b74f083141f8
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f12d71b9477e3072b7952d3f9331ed0cefc33ac7
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2017
---
# <a name="create-intune-custom-profile-settings-for-android-for-work-devices"></a>針對 Android for Work 裝置建立 Intune 自訂設定檔設定

使用 Intune Android for Work 自訂設定原則來指派 OMA-URI 設定，以用於控制 Android for Work 裝置上的功能。 這些是許多行動裝置製造商用來控制裝置功能的標準設定。

此功能的目的是讓您指派無法使用 Intune 原則設定的 Android 設定。 Intune 目前支援有限數目的 Android 自訂原則。 請參閱本主題中的範例，以找出您可以設定的原則。

## <a name="create-a-custom-profile"></a>建立自訂設定檔

1. 請使用[如何設定自訂裝置設定](custom-settings-configure.md)中的指示以便開始。
2. 在 [自訂 OMA-URI 設定] 刀鋒視窗上，選擇 [新增] 以新增新的設定。
3. 在 [新增資料列] 刀鋒視窗上，設定下列各項︰
    - **名稱**：為 Android for Work 自訂設定輸入唯一名稱，以協助您在 Azure 入口網站中識別。
    - **描述**：提供可給予 Android 自訂原則概觀的描述，以及其他可協助您找到該原則的相關資訊。
    - **OMA-URI**：輸入您想要提供設定的 OMA-URI。
    - **資料類型**：選取要指定此 OMA-URI 設定的資料類型。 選擇 [字串]、[字串 (XML 檔案)]、[日期和時間]、[整數]、[浮點數]、[布林值] 或 [Base64 (檔案)]。
    - **值**：指定要與您先前指定的 OMA-URI 產生關聯的值。 您用來提供此值的方法，將視您所選取的檔案類型而有所不同。 例如，如果您選擇 [日期和時間]，您將會從日期選擇器選取值。
4. 當您完成後，請選擇 [確定] 以返回 [自訂 OMA-URI 設定]，然後請新增更多設定，或是選擇 [建立] 以建立自訂設定檔。


## <a name="example"></a>範例

在此範例中，您將會建立自訂設定檔，以用來限制是否在受管理的 Android for Work 裝置上允許工作和個人應用程式的複製和貼上動作。

1. 透過本主題中的程序來使用下列值針對 Android for Work 裝置建立自訂設定檔：
    - **名稱**：輸入「封鎖複製和貼上」或是您自行選擇的文字。
    - **描述**：輸入「封鎖工作和個人應用程式的複製/貼上」或是您自行選擇的文字。
    - **OMA-URI**：輸入 **./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste**。
    - **資料類型**：選取 [布林值] 以表示此 OMA-URI 的值只會是 **True** 或 **False**。
    - **值**︰選取 [True]。
2. 您應該會得到看起來類似此影像的設定。
![針對 Android for Work 封鎖複製和貼上](./media/custom-policy-afw-copy-paste.png)。
3. 現在，當您將此自訂設定檔指派至您所管理的 Android for Work 裝置時，工作設定檔和個人設定檔中的應用程式，將無法在彼此之間進行複製和貼上。