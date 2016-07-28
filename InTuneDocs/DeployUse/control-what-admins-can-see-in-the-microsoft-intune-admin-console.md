---
title: "自訂系統管理員角色的主控台檢視 | Microsoft Intune"
description: "使用本主題來協助您篩選 Intune 管理主控台檢視，以讓您的管理員僅查看其角色所需的項目。"
keywords: 
author: robstackmsft
manager: arob98
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e0783eaa-67dc-410e-9e80-4d3aa72f36d8
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a409d36c1c5fcfd3d81ce0cbdf1f69af4747157a
ms.openlocfilehash: 132648f4c4d13983b169fa8497deae9787fe6db5


---

# 根據系統管理員角色自訂 Intune 主控台檢視
您可以篩選 Microsoft Intune 管理主控台檢視，讓您的管理員僅查看其角色需要看到的項目。 例如，您可以允許只有管理主控台操作員能夠更新惡意程式碼定義，或重設裝置上的密碼。 這可以藉由使用您指派給特定使用者的預設**指定**來完成。 當這些使用者存取管理主控台時，他們只會看見其指定特定的項目。

## 如何建立自訂檢視

1.  在 [Microsoft Intune 管理主控台](https://manage.microsoft.com)中，選擇 [管理] &gt; [服務系統管理員]。

2.  從服務系統管理員清單中，選擇要變更其指定的使用者，然後選擇 [管理存取]。

3.  在 [管理存取]  對話方塊中，選擇要授與所選取使用者的存取層級。 您可以選擇：

    -   **完整存取**
    -   **唯讀存取權**
    -   **技術服務人員 - 群組節點**

    完整存取權和唯讀存取權都一目了然。 <!--- **Helpdesk - Groups Node** allows users to choose from one of the following designations that provide custom levels of access to the [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] admin console:--->

    **技術服務人員 - 群組節點**會限制哪些系統管理員可以看到並執行下列工作︰

    -   請參閱使用者和裝置清單。 系統管理員無法使用篩選器來修改檢視。 不過，您可以使用群組篩選來修改系統管理員可看到的內容。 如需詳細資訊，請參閱[利用 Microsoft Intune，使用群組管理使用者和裝置](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)。

    -   列印使用者和裝置的清單

    -   匯出使用者和裝置的清單

    -   檢視使用者或裝置的內容

    -   執行下列遠端工作：

        -   執行完整的惡意程式碼掃描

        -   執行快速的惡意程式碼掃描

        -   重新啟動電腦

        -   更新惡意程式碼定義

        -   重新整理原則

        -   重新整理清查

        -   遠端鎖定裝置

        -   密碼重設

當您設定的系統管理員隨後開啟 Intune 管理主控台時，即會授與您指定的存取層級。



<!--HONumber=Jul16_HO3-->


