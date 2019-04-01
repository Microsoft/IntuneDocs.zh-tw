---
title: 在 Microsoft Intune 中使用範圍標籤篩選原則 - Azure | Microsoft Docs
description: 使用範圍標籤將組態設定檔篩選至特定角色。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bca2d52bb47a149c6a36bc1b8cbc4d65e50c0f4c
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57756797"
---
# <a name="use-rbac-and-scope-tags-for-distributed-it"></a>使用 RBAC 和範圍的標記，分散式 IT

您可以使用角色型存取控制 (RBAC) 和範圍標籤，以確定正確的系統管理員具有正確的存取權和權限的 Intune 物件的可見性。 角色判斷何種存取權系統管理員有哪些物件。 範圍標籤判斷系統管理員可以看到哪些物件。

例如，假設西雅圖地區辦公室系統管理員，則會指派的原則和設定檔管理員角色。 您想要檢視及管理只設定檔和原則只會套用到西雅圖的裝置，此系統管理員。 若要這樣做，您需要：

1. 建立稱為 「 西雅圖的範圍標籤。
2. 建立原則和設定檔管理員角色的角色指派： 
    - 成員 （群組） = 名為西雅圖 IT 系統管理員的安全性群組。 此群組中的所有系統管理員必須管理原則及範圍 （群組） 中的使用者/裝置的設定檔的權限。
    - 範圍 （群組） = 安全性群組命名為西雅圖的使用者。 所有的使用者/裝置在此群組中可以有其設定檔和成員 （群組） 的系統管理員所管理的原則。 
    - 範圍 （標籤） = Seattle。 成員 （群組） 中的系統管理員可以看到裝置也有 Seattle 範圍標籤。
3. 西雅圖範圍將標籤新增至原則與您想要在成員 （群組），若要能夠存取的系統管理員的設定檔。
4. 西雅圖範圍將標籤新增至您想要顯示給成員 （群組） 中的系統管理員的裝置。 


## <a name="to-create-a-scope-tag"></a>建立範圍標籤

1. 在 Intune 中，選擇**角色** > **範圍 （標籤）** > **建立**。

    ![螢幕擷取畫面的建立範圍標籤。](./media/scope-tags/create-scope-tag.png)

2. 提供 [名稱] 和 [描述]。
3. 選擇 **[建立]**。

## <a name="to-assign-a-scope-tag-to-a-role"></a>將範圍標籤指派給角色

1. 在 Intune 中，選擇**角色** > **所有角色**> 選擇角色 >**指派** > **指派**。

    ![螢幕擷取畫面會指派給某個角色的範圍。](./media/scope-tags/assign-scope-to-role.png)

2. 提供**作業的名稱**並**描述**。
3. 選擇**成員 （群組）** > **新增**> 選擇您要做為屬於此指派之一部份的群組 >**選取** >  **確定**。 此群組中的 mUsers 必須管理原則和範圍 （群組） 中的使用者/裝置的設定檔的權限。

    ![選取 [成員] 群組的螢幕擷取畫面。](./media/scope-tags/select-member-groups.png)

4. 如果您想要管理使用者/裝置在一組特定的群組中，選擇**範圍 （群組）** > **選取的群組** > **選取群組以包含**> 選擇的群組 >**選取** > **[確定]**。 所有的使用者/裝置在此群組中可以有其設定檔和成員 （群組） 的系統管理員所管理的原則。

    ![選取的範圍群組的螢幕擷取畫面。](./media/scope-tags/select-scope-groups.png)

    或者，您可以選擇**所有裝置**，**所有使用者**，或**所有使用者和所有裝置**。

    ![選取的範圍群組的其他選項的螢幕擷取畫面。](./media/scope-tags/scope-group-other-options.png)
    
5. 選擇**範圍 （標籤）** > **新增**> 選擇您想要新增至此角色的標記 >**選取** > **確定**. 成員 （群組） 中的使用者會有存取權的原則和設定檔，也有相同的範圍標籤。

    ![選取的範圍標籤的螢幕擷取畫面。](./media/scope-tags/select-scope-tags.png)

6. 選擇 [確定]。 

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>將範圍標籤新增至組態設定檔
1. 在 Intune 中，選擇**裝置組態** > **設定檔**> 選擇的設定檔。

    ![選取的設定檔的螢幕擷取畫面。](./media/scope-tags/choose-profile.png)

2. 選擇**屬性** > **範圍 （標籤）** > **新增**。

    ![新增範圍標籤的螢幕擷取畫面。](./media/scope-tags/add-scope-tags.png)

3. 底下**選取標記**，選擇您想要新增至設定檔的標記。
4. 選擇**選取**  > **確定** > **儲存**。

## <a name="scope-tag-details"></a>範圍標記詳細資料
當使用範圍標籤，請記住這些詳細資料：

- 目前，您可以指派至範圍標籤：
    - 角色指派
    - 裝置相容性原則
    - 裝置組態設定檔
    - Windows 10 更新通道
    - 受管理的裝置
    - 應用程式
    - 應用程式設定原則： 受管理的裝置
    - PowerShell 指令碼
    - DEP 權杖
- 當系統管理員在 Intune 中建立物件時，指派給該系統管理員的所有範圍標籤會自動都指派給新的物件。
- Intune RBAC 不適用於 Azure Active Directory 角色。 因此，Intune 服務管理員和全域管理員角色有 Intune 的 「 完整的系統管理員 」 存取權，不論它們有何種範圍標籤。
- 在角色指派範圍標籤使用的系統管理員也可以查看 Intune 沒有範圍標籤物件。
- 您只能指派您在您的角色指派範圍標籤。
- 您可以在您的角色指派範圍 （群組） 中所列目標群組。
- 如果您有指派給您的角色的範圍標籤時，您無法刪除 Intune 物件上的所有範圍標籤。 需要至少一個範圍標籤。
- 如果使用者有多個角色指派，在這些角色指派的權限延伸至不同的物件，如下所示：
    - 指派權限只套用至該角色指派範圍 （群組） 中的物件 （例如原則或應用程式）。 指派權限不套用到其他角色指派中的物件，除非其他指派明確地授與它們。
    - 其他權限 （例如建立和讀取），套用至相同的類型 （例如所有的原則或所有應用程式） 的所有物件中任何使用者的指派。
    - （例如原則或應用程式） 的不同類型的物件權限不適用於彼此。 比方說，讀取權限的原則，並不提供應用程式中使用者的指派 [讀取] 權限。





## <a name="next-steps"></a>後續步驟

管理您的[角色](role-based-access-control.md)和[設定檔](device-profile-assign.md)。
