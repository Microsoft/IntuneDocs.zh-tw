---
title: "行動裝置的 Exchange 存取規則"
description: "Exchange ActiveSync 存取規則，允許或封鎖裝置與 EAS 的連線"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 208b9f45-02d9-413a-b86a-8bad9b5008fa
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: a57b1f51fabfdc8896ecbb5bfbe6422f40672b18
ms.contentlocale: zh-tw
ms.lasthandoff: 06/08/2017


---

# <a name="exchange-access-rules-for-mobile-devices"></a>行動裝置的 Exchange 存取規則

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

行動裝置的 Exchange 存取規則決定那些裝置對 Exchange ActiveSync 的存取層級。 這些設定會影響所有行動裝置 (包含未在 Microsoft Intune 中註冊的裝置)。 您可以先定義 [預設規則]，這個預設規則會套用到沒有套用自訂規則的任何行動裝置。

下表包含 Exchange ActiveSync 管理的存取層級：

|存取層級|說明|
|----------------|---------------|
|**允許裝置存取 Exchange**|在「允許存取」狀態中，行動裝置可以透過 Exchange ActiveSync 進行同步處理，並連線到 Exchange 伺服器以擷取電子郵件並管理行事曆、連絡人、工作和記事。 只要裝置符合任何您已在 Exchange 中設定的 Exchange ActiveSync 信箱原則，便可維持允許存取的狀態 (除非 Exchange 系統管理員已封鎖使用者或特定行動裝置)。|
|**封鎖行動裝置存取 Exchange**|在「封鎖存取」狀態中，會封鎖行動裝置，也不允許行動裝置連線到 Exchange 伺服器。 裝置會收到「HTTP 403 禁止」錯誤。 使用者會收到 Exchange 伺服器寄出的電子郵件，通知他們行動裝置遭到封鎖，無法存取其信箱。 此訊息不能在封鎖的行動裝置上。 藉由使用 [設定使用者通知] 工作，您可以在這封訊息中加上自訂文字，以提供指示給裝置遭到封鎖的使用者。 |
|**隔離行動裝置以便您稍後再加以允許或封鎖**|當行動裝置遭到隔離時，行動裝置可以連線到 Exchange 伺服器， 但是對資料的存取將會受到限制。 使用者可以新增內容到自己的 [行事曆]、[連絡人]、[工作] 和 [記事] 資料夾，但是伺服器不會允許該裝置從使用者的信箱擷取任何內容。 使用者會收到一封電子郵件訊息，說明行動裝置已遭到隔離。 此訊息會傳送到裝置及使用者的信箱。 藉由使用 [設定使用者通知] 工作，您可以在這封訊息中加上自訂文字，以提供指示給裝置遭到隔離的使用者。|

存取策略是套用到連線至 Exchange 之所有行動裝置的 [預設規則] 及 [平台例外狀況] 的組合。 下表列出部分的存取策略範例。

|存取策略|說明|
|-------------------|---------------|
|允許清單|您可以使用「允許清單」來授與存取權給已知的裝置清單，並限制所有其他裝置的存取權。 若要這樣做，您必須建立自訂規則，使允許的裝置平台能夠存取使用者的信箱。 建立這種規則後，您必須盡快設定預設存取規則以封鎖或隔離其他所有裝置。 若要新增新裝置到允許清單，請建立新的自訂規則。|
|封鎖清單|您可以使用*封鎖清單*，依預設授與存取權給所有裝置，但針對您不想讓其存取貴組織的一組裝置，封鎖其存取權。 建立自訂規則來建立封鎖清單，以封鎖您不想與組織信箱同步的裝置平台。 建議將預設規則設為允許存取現有規則未明確封鎖的所有裝置。 若要新增單一裝置或一組裝置到封鎖清單，請建立新的自訂規則。|
|混合允許與封鎖|除了建立允許和封鎖清單之外，您還可以在組織引入新的行動裝置時隔離這些裝置以對其進行評估。 例如，如果您有一份封鎖清單和一份允許清單 (前者包含組織不允許的行動裝置，後者包含組織允許的行動裝置)，您可以將預設規則設定成隔離。 系統會自動隔離其他所有裝置。 這可讓您在組織引入新裝置時探索到這些裝置，並決定要將新裝置新增到允許清單或封鎖清單。|
下列程序說明如何建立自訂規則。

## <a name="create-a-default-access-rule"></a>建立預設存取規則

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 [原則] &gt; [Exchange ActiveSync]。

2.  在 [預設規則] 清單中，選取您要套用至不受規則或個人免除涵蓋之所有行動裝置的存取規則。 選擇 [儲存]。

下列程序說明如何建立自訂規則：

## <a name="create-a-custom-access-rule"></a>建立自訂存取規則

1. 在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 [原則] &gt; [Exchange ActiveSync]。

2.  在 [平台例外狀況] 清單中，選擇 [新增規則] 然後建立自訂規則。 選擇 [儲存]。

