---
title: 從 Intune 公司入口網站網站取得 macOS 裝置的修復金鑰
description: 查看已註冊、受管理的 macOS 裝置的修復金鑰。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/04/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 1e7831712b4c07d015aa0f587ff6ba6183940897
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75855231"
---
# <a name="get-a-recovery-key-for-a-macos-device"></a>取得 macOS 裝置的修復金鑰

使用公司入口網站網站來取得已鎖定 macOS 裝置的修復金鑰。 如果您忘記您的裝置密碼，您可以從其他裝置登入公司入口網站以取得金鑰。  

## <a name="get-recovery-key-from-company-portal-website"></a>從公司入口網站網站取得修復金鑰

此選項適用于您的組織使用 FileVault 加密的裝置。 其不適用於您個人加密的裝置。

1. 在任何裝置上，登入[公司入口網站網站](https://portal.manage.microsoft.com)，然後選取 [>**裝置**]**功能表**按鈕。  
2. 選取加密的 macOS 裝置。  
3. 選取 [取得修復金鑰]  。  

    ![公司入口網站網站的螢幕擷取畫面，反白顯示 [取得修復金鑰] 區段。](./media/1907-recovery2-cpweb-intune.PNG)  

4. 您的修復金鑰隨即出現。

    ![公司入口網站網站的螢幕擷取畫面，其中顯示修復金鑰。](./media/1907-recovery-cpweb-intune.PNG)  

    基於安全性理由，金鑰會在五分鐘後消失。 若要再次查看金鑰，請選取 [**取得修復金鑰**]。

如果找不到金鑰，但您的裝置已正確加密，請洽詢您組織的支援人員。 如需連絡資訊，請查看[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)。  

## <a name="get-recovery-key-from-company-portal-app-for-ios"></a>從適用于 iOS 的公司入口網站應用程式取得修復金鑰

您可以使用適用于 iOS 的公司入口網站應用程式來抓取您的個人修復金鑰（FileVault 金鑰）。 具有個人修復金鑰的裝置必須向 Intune 註冊，並透過 Intune 以 FileVault 加密。 您個人加密的裝置無法使用此選項。 

使用公司入口網站應用程式，您可以開啟 Safari web view 並取出您的個人修復金鑰。 

1. 開啟 [公司入口網站]。
2. 按一下 [**取得修復金鑰**]。

    ![IOS 公司入口網站應用程式的螢幕擷取畫面，顯示修復金鑰](./media/get-recovery-key-cpweb-02.png)  

公司入口網站網站會在 Safari web view 中開啟，並顯示金鑰。 

## <a name="it-pro-support"></a>IT 專業人員支援

如果您是 IT 支援人員，而且想要設定和管理 macOS 裝置的 FileVault 加密，請參閱搭配[Intune 使用裝置加密](/intune/protect/encrypt-devices)。

## <a name="next-steps"></a>後續步驟

瞭解您可以從公司入口網站網站執行的其他工作。 如需動作清單，請參閱[使用 Intune 公司入口網站網站](using-the-intune-company-portal-website.md)。  

是否仍需要協助？ 請洽詢您的 IT 支援人員。 如需連絡資訊，請查看[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)。  
