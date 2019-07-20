---
title: 在 Microsoft Intune 中使用範圍標籤篩選原則 - Azure | Microsoft Docs
description: 使用範圍標籤將組態設定檔篩選至特定角色。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2019
ms.topic: article
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 627899eafb2175b2d3034045bd765a10f4a203d6
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67882498"
---
# <a name="use-role-based-access-control-rbac-and-scope-tags-for-distributed-it"></a>針對分散式 IT 使用角色型存取控制 (RBAC) 和範圍標籤

您可以使用角色型存取控制和範圍標籤，以確定適當的系統管理員對適當 Intune 物件具有適當存取權和可見性。 角色決定系統管理員對哪些物件具有哪些存取權。 範圍標籤決定系統管理員可以看到哪些物件。

例如，假設我們將原則和設定檔管理員角色指派給西雅圖地區辦公室的系統管理員。 您希望此系統管理員僅查看及管理只適用於西雅圖裝置的設定檔和原則。 若要進行此操作，您需要：

1. 建立稱為「西雅圖」的範圍標籤。
2. 使用下列項目建立原則和設定檔管理員角色的角色指派： 
    - 成員 (群組) = 名為西雅圖 IT 系統管理員的安全性群組。 此群組中的所有系統管理員，都將具有管理範圍 (群組) 中使用者/裝置之原則及設定檔的權限。
    - 範圍 (群組) = 名為「西雅圖使用者」的安全性群組。 此群組中所有使用者/裝置的設定檔及原則，都能由成員 (群組) 中的系統管理員管理。 
    - 範圍 (標籤) = 「西雅圖」。 成員 (群組) 中的系統管理員，可以查看也具有「西雅圖」範圍標籤的裝置。
3. 將「西雅圖」範圍標籤新增至您希望成員 (群組) 中系統管理員能夠存取的原則及設定檔。
4. 將「西雅圖」範圍標籤新增至您希望成員 (群組) 中系統管理員能夠看見的裝置。 


## <a name="to-create-a-scope-tag"></a>建立範圍標籤

1. 在 Intune 中，選擇 [角色]   > [範圍 (標籤)]   > [建立]  。

    ![建立範圍標籤的螢幕擷取畫面。](./media/scope-tags/create-scope-tag.png)

3. 如果您想要在特定群組中的所有裝置, 請選擇 [**將範圍標籤指派給選取群組中的所有裝置**]。
    1. 在 [**選取要包含的群組**] 頁面中, 選擇包含您要指派此範圍標籤的裝置所屬的群組。
    2. 選擇 [選取]  。
4. 選擇 **[建立]** 。

## <a name="to-assign-a-scope-tag-to-a-role"></a>將範圍標籤指派給角色

1. 在 Intune 中，選擇 [角色]   > [所有角色]  > 選擇角色 > [指派]   > [指派]  。

    ![將範圍指派給角色的螢幕擷取畫面。](./media/scope-tags/assign-scope-to-role.png)

2. 提供**作業名稱**與**描述**。
3. 選擇 [成員 (群組)]   > [新增]  > 選擇您希望作為此指派一部分的群組 > [選取]   > [確定]  。 此群組中的使用者，都將具有管理範圍 (群組) 中使用者/裝置之原則及設定檔的權限。

    ![選取成員群組的螢幕擷取畫面。](./media/scope-tags/select-member-groups.png)

4. 如果您希望在一組特定群組中管理使用者/裝置，請選擇 [範圍 (群組)]   > [選取的群組]   > [選取群組以包含]  > 選擇群組 > [選取]   > [確定]  。 此群組中所有使用者/裝置的設定檔及原則，都能由成員 (群組) 中的系統管理員管理。

    ![選取範圍群組的螢幕擷取畫面。](./media/scope-tags/select-scope-groups.png)

    或者，您也可以選擇 [所有裝置]  、[所有使用者]  或 [所有使用者和所有裝置]  。

    ![選取範圍群組其他選項的螢幕擷取畫面。](./media/scope-tags/scope-group-other-options.png)
    
5. 選擇 [範圍 (標籤)]   > [新增]  > 選擇您希望新增至此角色的標籤 > [選取]   > [確定]  。 成員 (群組) 中的使用者，可以存取具有相同範圍標籤的原則及設定檔。

    ![選取範圍標籤的螢幕擷取畫面。](./media/scope-tags/select-scope-tags.png)

6. 選擇 [確定]  。 

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>將範圍標籤新增至組態設定檔
1. 在 Intune 中，選擇 [裝置設定]   > [設定檔]  > 選擇設定檔。

    ![選取設定檔的螢幕擷取畫面。](./media/scope-tags/choose-profile.png)

2. 選擇 [屬性]   > [範圍 (標籤)]   > [新增]  。

    ![新增範圍標籤的螢幕擷取畫面。](./media/scope-tags/add-scope-tags.png)

3. 在 [選取標籤]  下方，選擇您希望新增至設定檔的標籤。
4. 選擇 [選取]   > [確定]   > [儲存]  。

## <a name="to-assign-a-scope-tag-to-an-app-configuration-policy"></a>將範圍標籤指派給應用程式設定原則
針對將 [裝置註冊類型]  設為 [受控裝置]  的裝置：
1. 選擇 [用戶端應用程式]   > [應用程式設定原則]  > 選擇應用程式設定原則。
2. 選擇 [屬性]   > [範圍 (標籤)]  > 選擇您希望指派給原則的標籤。

針對將 [裝置註冊類型]  設為 [受控應用程式]  的裝置：
1. 選擇 [用戶端應用程式]   > [應用程式設定原則]  > 選擇應用程式設定原則。
2. 選擇 [範圍 (標籤)]  > 選擇您希望指派給原則的標籤。


## <a name="to-assign-a-scope-tag-to-an-ios-app-provisioning-profile"></a>將範圍標籤指派給 iOS 應用程式佈建設定檔
1. 在 Intune 中，選擇 [用戶端應用程式]   > [iOS 應用程式佈建設定檔]  > 選擇設定檔。
2. 選擇 [屬性]   > [範圍 (標籤)]  > 選擇您希望指派給設定檔的標籤。
3. 選擇 [選取]   > [確定]   > [儲存]  。

## <a name="to-assign-a-scope-tag-to-an-apple-volume-purchase-program-vpp-token"></a>將範圍標籤指派給 Apple 大量採購方案 (VPP) 權杖
1. 在 Intune 中，選擇 [用戶端應用程式]   > [Apple VPP 權杖]  > 選擇 VPP 權杖。
2. 選取 [範圍 (標籤)]  > 選擇您希望指派給設定檔的標籤。 與 VPP 權杖建立關聯的 VPP 應用程式和電子書會繼承所指派標籤。
3. 選擇 [選取]   > [確定]   > [儲存]  。

## <a name="scope-tag-details"></a>範圍標籤詳細資料
使用範圍標籤時，請記住這些詳細資料：

- 目前，您可以將範圍標籤指派給：
  - 角色指派
  - 裝置相容性原則
  - 裝置組態設定檔
  - Windows 10 更新通道
  - 受管理的裝置
  - 應用程式
  - 應用程式設定原則 - 受控裝置
  - PowerShell 指令碼
  - DEP 權杖
  - iOS 應用程式佈建設定檔
  - 大量採購方案 (VPP) 權杖
- 當系統管理員在 Intune 中建立物件時，指派給該系統管理員的所有範圍標籤都會自動都指派給新物件。
- Intune RBAC 不適用於 Azure Active Directory 角色。 因此，Intune 服務管理員和全域管理員角色具有 Intune 的完整系統管理員存取權 (不論他們具有哪些範圍標籤)。
- 具有範圍標籤之角色指派中的系統管理員，也可以查看不具有範圍標籤的 Intune 物件。
- 您只能指派角色指派中的範圍標籤。
- 您只能定位角色指派之範圍 (群組) 中列出的群組。
- 如果您已將範圍標籤指派給您的角色，則無法刪除 Intune 物件上的所有範圍標籤。 需要至少一個範圍標籤。

## <a name="next-steps"></a>後續步驟

管理您的[角色](role-based-access-control.md)和[設定檔](device-profile-assign.md)。
