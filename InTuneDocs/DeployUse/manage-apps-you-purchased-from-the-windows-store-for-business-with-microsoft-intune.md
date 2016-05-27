---
# required metadata

title: 管理購自商務用 Windows 市集的應用程式 | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8e38d47d-0c5e-40ce-b379-29d3657f5c28

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 以 Microsoft Intune 管理購自商務用 Windows 市集的應用程式
[商務用 Windows 市集](https://www.microsoft.com/business-store)可讓您為組織個別或大量尋找和購買應用程式。 藉由連接到 Microsoft Intune 的市集，您可以從 Intune 主控台管理大量購買的應用程式，例如︰
* 您可以同步處理您使用 Intune 從市集購買的應用程式的清單。
* 同步處理的應用程式會出現在 Intune 管理主控台，而您可以如同任何其他應用程式一般加以部署
* 您可以追蹤有多少可用的授權，以及 Intune 管理主控台中正使用多少授權
* 如果沒有足夠的可用授權，Intune 會封鎖應用程式的部署和安裝

## 開始之前
從商務用 Windows 市集開始同步處理及部署應用程式之前，請檢閱下列資訊︰
* 您必須將 Intune 設定為組織的行動裝置管理授權單位。 如需詳細資訊，請參閱[準備在 Microsoft Intune 中註冊裝置](get-ready-to-enroll-devices-in-microsoft-intune.md)
* 您在商務用 Windows 市集上必須已註冊取得帳戶
* 一旦您將 Intune 與企業用 Windows 市集帳戶建立關聯，未來將無法變更為不同帳戶。
* 從市集購買的應用程式無法手動加入至 Intune，或從其刪除。 它們只能與商務用 Windows 市集同步。
* Intune 只會同步處理您透過商務用 Windows 市集購買的線上授權應用程式。

## 將您的商務用 Windows 市集帳戶與 Intune 相關聯
在 Intune 主控台中啟用同步處理之前，您必須將您的市集帳戶設定為使用 Intune 做為管理工具︰
1. 請確定使用您用來登入 Intune 的相同租用戶帳戶來登入商務用市集。
2. 在商務用市集中，選擇 [設定] > [管理工具].
3. 在 [管理工具] 頁面上，選擇 [加入管理工具]，然後選擇 [Microsoft Intune]。

您現在可以繼續進行，並在 Intune 主控台中設定同步處理。

## 設定同步處理

1. 在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，按一下 [管理].
2. 在 [系統管理] 工作區中，展開 [行動裝置管理]，然後按一下 [商務用市集].
3. 在商務用 Windows 市集頁面上，執行下列動作︰
* 如果您尚未這樣做，請按一下連結以註冊使用商務用 Windows 市集
* 一旦註冊完成，請按一下 [設定同步處理]
4. 在 [設定商務用 Windows 市集應用程式同步處理] 對話方塊中，選取 [啟用商務用 Windows 市集同步處理].
5. 從 [語言] 下拉式清單中，選擇來自商務用 Windows 市集的應用程式將會在 Intune 主控台中顯示的語言。 無論顯示的語言為何，可用時將以使用者的語言安裝。
6. 按一下 [確定].

## 同步處理應用程式

1. 在商務用 Windows 市集頁面上，按一下 [立即同步] 來同步處理您使用 Intune 從市集購買的應用程式。
2. 在 [應用程式] 工作區中，按一下 [受管理的軟體] > [授權軟體] 來檢視可用的應用程式，並確認已正確匯入您所購買的應用程式。
此節點中的應用程式會顯示，並加上您所擁有的授權總數，以及您可以使用的授權數目。

## 部署應用程式

您可以使用與部署任何其他 Intune 應用程式的相同方式，部署來自市集的應用程式。 如需詳細資訊，請參閱[在 Microsoft Intune 中部署應用程式](deploy-apps-in-microsoft-intune.md).
當您部署商務用 Windows 市集應用程式時，安裝應用程式的每個使用者會耗用一個授權。 如果您對某個已部署的應用程式使用所有可用的授權，將無法再部署任何副本，並且必須採取下列動作之一︰
* 從某些裝置解除安裝應用程式
* 將目前部署的範圍減少，僅以您擁有足夠授權的使用者為目標
* 從商務用 Windows 市集購買更多份應用程式


### 請參閱
[在 Microsoft Intune 中新增行動裝置的應用程式](add-apps-for-mobile-devices-in-microsoft-intune.md)




<!--HONumber=May16_HO1-->


