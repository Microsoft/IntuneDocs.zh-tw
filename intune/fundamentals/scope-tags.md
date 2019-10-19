---
title: 在 Intune 中使用角色型存取控制（RBAC）和範圍標籤來散發它 |Microsoft Docs
description: 使用範圍標籤將組態設定檔篩選至特定角色。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.technology: ''
ms.assetid: a21d3039-f2ed-4f43-b6fa-d00c071edbc4
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6b92dca399afeb035bf58d998efdd469318de389
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504952"
---
# <a name="use-role-based-access-control-rbac-and-scope-tags-for-distributed-it"></a>針對分散式 IT 使用角色型存取控制 (RBAC) 和範圍標籤

您可以使用角色型存取控制和範圍標籤，以確定適當的系統管理員對適當 Intune 物件具有適當存取權和可見性。 角色決定系統管理員對哪些物件具有哪些存取權。 範圍標籤決定系統管理員可以看到哪些物件。

例如，假設西雅圖地區辦公室的系統管理員具備原則和設定檔管理員角色。 您希望此系統管理員僅查看及管理只適用於西雅圖裝置的設定檔和原則。 若要設定此存取權，您可以：

1. 建立稱為「西雅圖」的範圍標籤。
2. 使用下列項目建立原則和設定檔管理員角色的角色指派： 
    - 成員 (群組) = 名為西雅圖 IT 系統管理員的安全性群組。 此群組中的所有系統管理員，都將具有管理範圍 (群組) 中使用者/裝置之原則及設定檔的權限。
    - 範圍 (群組) = 名為「西雅圖使用者」的安全性群組。 此群組中所有使用者/裝置的設定檔及原則，都能由成員 (群組) 中的系統管理員管理。 
    - 範圍 (標籤) = 「西雅圖」。 成員 (群組) 中的系統管理員，可以查看也具有「西雅圖」範圍標籤的 Intune 物件。
3. 將「西雅圖」範圍標籤新增至您希望成員 (群組) 中系統管理員可存取的原則及設定檔。
4. 將「西雅圖」範圍標籤新增至您希望成員 (群組) 中系統管理員能夠看見的裝置。 

## <a name="default-scope-tag"></a>預設範圍標籤
預設範圍標籤會自動新增至所有支援範圍標記的未標記物件。

預設範圍標籤功能與 System Center Configuration Manager 中的安全性範圍功能類似。 

## <a name="to-create-a-scope-tag"></a>建立範圍標籤

1. 在 Intune 中，選擇 [角色]   > [範圍 (標籤)]   > [建立]  。

    ![建立範圍標籤的螢幕擷取畫面。](./media/scope-tags/create-scope-tag.png)

3. 如果您想要在特定群組中的所有裝置，請選擇 [**將範圍標籤指派給選取群組中的所有裝置**]。
    1. 在 [**選取要包含的群組**] 頁面中，選擇包含您要指派此範圍標籤的裝置所屬的群組。
    2. 選擇 [選取]  。
4. 選擇 **[建立]** 。

## <a name="to-assign-a-scope-tag-to-a-role"></a>將範圍標籤指派給角色

1. 在 Intune 中，選擇 [角色]   > [所有角色]  > 選擇角色 > [指派]   > [指派]  。

    ![將範圍指派給角色的螢幕擷取畫面。](./media/scope-tags/assign-scope-to-role.png)

2. 提供**作業名稱**與**描述**。
3. 選擇 [成員 (群組)]   > [新增]  > 選擇您希望作為此指派一部分的群組 > [選取]   > [確定]  。 此群組中的使用者將有權管理範圍（群組）中的使用者/裝置。

    ![選取成員群組的螢幕擷取畫面。](./media/scope-tags/select-member-groups.png)

4. 如果您希望在一組特定群組中管理使用者/裝置，請選擇 [範圍 (群組)]   > [選取的群組]   > [選取群組以包含]  > 選擇群組 > [選取]   > [確定]  。 此群組中的所有使用者/裝置都會由成員（群組）中的系統管理員所管理。

    ![選取範圍群組的螢幕擷取畫面。](./media/scope-tags/select-scope-groups.png)

    或者，您也可以選擇 [所有裝置]  、[所有使用者]  或 [所有使用者和所有裝置]  。

    ![選取範圍群組其他選項的螢幕擷取畫面。](./media/scope-tags/scope-group-other-options.png)
    
5. 選擇 [範圍 (標籤)]   > [新增]  > 選擇您希望新增至此角色的標籤 > [選取]   > [確定]  。 成員（群組）中的使用者將可存取也具有相同範圍標記的 Intune 物件。

    ![選取範圍標籤的螢幕擷取畫面。](./media/scope-tags/select-scope-tags.png)

6. 選擇 [確定]  。 

## <a name="assign-scope-tags-to-other-objects"></a>將範圍標籤指派給其他物件

針對支援範圍標記的物件，範圍標籤通常會出現在 [**屬性**] 底下。 例如，若要將範圍標籤指派給設定設定檔，請遵循下列步驟：

1. 在 Intune 中，選擇 [裝置設定]   > [設定檔]  > 選擇設定檔。

    ![選取設定檔的螢幕擷取畫面。](./media/scope-tags/choose-profile.png)

2. 選擇 [屬性]   > [範圍 (標籤)]   > [新增]  。

    ![新增範圍標籤的螢幕擷取畫面。](./media/scope-tags/add-scope-tags.png)

3. 在 [選取標籤]  下方，選擇您希望新增至設定檔的標籤。
4. 選擇 [選取]   > [確定]   > [儲存]  。


## <a name="scope-tag-details"></a>範圍標籤詳細資料
使用範圍標籤時，請記住這些詳細資料： 

- 如果租使用者可以擁有該物件的多個版本（例如角色指派或應用程式），您可以將範圍標籤指派給 Intune 物件類型。
  下列 Intune 物件是此規則的例外狀況，目前不支援範圍標籤：
    - Windows ESP 設定檔
    - 裝置類別
    - 註冊限制
    - 公司裝置識別碼
    - Autopilot 裝置
    - 裝置合規性位置
    - Jamf 裝置
- 與 VPP 權杖相關聯的 VPP 應用程式和電子書會繼承指派給相關 VPP 權杖的範圍標籤。
- 與 DEP 權杖相關聯的裝置註冊計劃（DEP）裝置和 DEP 設定檔，會繼承指派給相關 DEP 權杖的範圍標籤。
- 當系統管理員在 Intune 中建立物件時，指派給該系統管理員的所有範圍標籤都會自動都指派給新物件。
- Intune RBAC 不適用於 Azure Active Directory 角色。 因此，Intune 服務管理員和全域管理員角色具有 Intune 的完整系統管理員存取權 (不論他們具有哪些範圍標籤)。
- 如果角色指派沒有範圍標籤，IT 系統管理員可以看到以 IT 系統管理員許可權為基礎的所有物件。 沒有範圍標籤的系統管理員基本上具有所有範圍標籤。
- 您只能指派角色指派中的範圍標籤。
- 您只能定位角色指派之範圍 (群組) 中列出的群組。
- 如果您已將範圍標籤指派給您的角色，則無法刪除 Intune 物件上的所有範圍標籤。 需要至少一個範圍標籤。

## <a name="next-steps"></a>後續步驟

瞭解當有[多個角色指派](role-based-access-control.md#multiple-role-assignments)時，範圍標籤的行為方式。
管理您的[角色](role-based-access-control.md)和[設定檔](../configuration/device-profile-assign.md)。
