---
# required metadata

title: Microsoft Intune 中的 Windows 版本升級原則設定 | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8589866a-3f13-489b-a5cd-cee017d16d54

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune 中的 Windows 版本升級原則設定
Microsoft Intune 版本升級原則可讓您自動將執行下列 Windows 10 版本之一的裝置升級至較新版本：
* Windows 10 Desktop
* Windows 10 Holographic

## 開始之前
在開始將裝置升級至最新版本之前，您需要下列其中一項：
* 可以在您以原則設為目標的所有裝置上 (適用於 Windows 10 Desktop 版本)，安裝新版本 Windows 的有效產品金鑰。
* 來自 Microsoft 的授權檔案，其中包含在您以原則為目標的所有裝置上 (適用於 Windows 10 Mobile 和 Windows 10 Holographic 版本) 安裝新版本 Windows 的授權資訊。
* 必須在 Microsoft Intune 中註冊您的目標 Windows 10 裝置。

## 版本升級原則設定

|設定名稱|詳細資料|
|-|-|
|**Name**|輸入版本升級原則的名稱。|
|**說明**|選擇性地輸入可協助您在 Intune 主控台中識別該原則的描述。
|**要升級到的版本**|從下拉式清單選取您想將目標裝置升級到的 Windows 10 Desktop、Windows 10 Holographic 或 Windows 10 Mobile 版本。
|**產品金鑰**|指定您從 Microsoft 取得的產品金鑰，可用來升級所有 Windows 10 Desktop 目標裝置。<br>建立包含產品金鑰的原則之後，您便無法在稍後編輯產品金鑰。 這是因為金鑰基於安全性考量而隱藏。 若要變更產品金鑰，您必須重新輸入完整金鑰。
|**授權檔**|按一下 [瀏覽] 以選取您從 Microsoft 取得的授權檔，包含要將目標裝置升級到的 Windows Holographic 版本的授權資訊。

### 請參閱
[透過 Microsoft Intune 原則管理裝置上的設定和功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

<!--HONumber=May16_HO1-->


