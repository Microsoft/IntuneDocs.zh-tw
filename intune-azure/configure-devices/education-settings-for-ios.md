---
title: "設定 iOS 的 Intune 教育設定 | Intune Azure 預覽版 | Microsoft Docs"
description: "Intune Azure 預覽版︰了解您可用於控制 iOS 裝置上教育設定之設定。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 44c427f8-0f22-43c2-8c29-e0f9fa533b1f
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3f05e0018fb202ab5774e935c3f59855e4aa2e75
ms.openlocfilehash: e52fdf8c30a680d62071cd31e308dd0180e8b9dc


---

# <a name="how-to-configure-intune-education-settings-for-ios-devices-in-intune-azure-preview"></a>如何設定 Intune Azure 預覽中 iOS 裝置的 Intune 教育設定

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


## <a name="create-a-device-profile-containing-ios-education-settings"></a>建立內含 iOS 教育設定的裝置設定檔

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [其他]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中選擇 [設定裝置]。
2. 在 [裝置設定] 刀鋒視窗中，選取 [管理]  >  [設定檔]。
3. 在設定檔刀鋒視窗中，選擇 [建立設定檔]。
4. 在 [建立設定檔] 刀鋒視窗中，為教育升級設定檔輸入 [名稱] 及 [描述]。
5. 從 [平台] 下拉式清單中，選擇 [iOS]。
6. 從 [設定檔類型] 下拉式清單中，選擇 [教育]。
7. 在 [教育] 刀鋒視窗中，選取下列項目︰
    - **教師根憑證檔案**
    - **教師 PKCS12 / PFX 設定檔**
    - **學生根憑證檔案**
    - **學生 PKCS12 / PFX 設定檔**
8. 當您完成時，請返回 [建立設定檔] 刀鋒視窗，然後點擊 [建立]。

隨即會建立設定檔，並會出現在 [設定檔清單] 刀鋒視窗上。



<!--HONumber=Feb17_HO1-->


