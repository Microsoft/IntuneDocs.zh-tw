---
title: "將條件式存取原則從 Intune 傳統入口網站移轉到新的 Azure 入口網站。"
titleSuffix: Intune on Azure
description: "將條件式存取原則從 Intune 傳統入口網站移轉到新的 Azure 入口網站。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 301159ad-5f7e-4fcc-86c7-f72a71701ff4
ms.reviewer: chrisgree
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2450a878424d8c992a43e8028ba59b7136e1d530
ms.sourcegitcommit: fd5b7aa26446d2fa92c21638cb29371e43fe169f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2017
---
# <a name="reassign-conditional-access-policies-from-intune-classic-portal-to-the-new-azure-portal"></a>將條件式存取原則從 Intune 傳統入口網站重新指派給新的 Azure 入口網站。

自新的 Azure 入口網站開始，條件式存取支援每個應用程式可有多項原則，以及更多的自訂功能。

## <a name="before-you-begin"></a>開始之前

若已準備好移往新的 Azure 入口網站，可以遵循下列步驟，重新指派先前在 Intune 傳統入口網站中建立的條件式存取原則：

- 收集之前在 Intune 傳統入口網站中建立的條件式存取原則，以了解稍後重新指派時需要哪些設定。

- 遵循本主題的步驟，在新的 Azure 入口網站中重新建立這些原則。

- 一旦確認新的原則在新的 Azure 入口網站中能如預期運作，請即停用 Intune 傳統主控台中的條件式原則。
<br /><br />
    - 請先規劃如何將使用者移至新的原則，**再停用** Intune 傳統入口網站中條件式存取原則。 有兩種方式：
<br /><br />
        - **在相同的包含群組中套用新 Azure 入口網站中建立的原則，建立新的豁免群組，使用 Intune 傳統入口網站所套用的原則**。
            - 逐漸將某些使用者移至傳統入口網站中指定的豁免群組。  這可避免 Intune 傳統入口網站套用目標原則。 除了 Intune 傳統入口網站中已套用的原則外，所有以新 Azure 入口網站中相同的使用者群組為目標所建立的原則都會套用。 
<br /><br />
        - **建立新的群組，以新的 Azure 入口網站的條件式存取原則為目標**。 如果選擇此方式，需要執行下列作業：
            - 逐漸移除 Intune 傳統入口網站中以條件式存取原則為目標之安全性群組的使用者。
            - 一旦確認新原則可作用於這些使用者，即可停用 Intune 傳統入口網站中的原則。 
<br /><br />
- 如已設定條件式存取原則設定在 Intune 傳統入口網站中使用 Exchange Active Sync (EAS)，請參閱[本主題的指示](#to-reassign-intune-device-based-conditional-access-policies-for-eas-clients)**在新的 Azure 入口網站中重新指派 EAS 條件式存取原則設定**。

### <a name="to-verify-your-device-based-conditional-access-policies-in-the-intune-classic-portal"></a>在 Intune 傳統入口網站中確認裝置型條件式存取原則

1.  移至 [Intune 傳統入口網站](https://manage.microsoft.com)，並使用您的認證登入。

2.  在左側功能表中選擇 [原則]。

3.  選擇 [條件式存取]，然後選取您已為其建立條件式存取原則的 Microsoft 雲端服務 (Exchange Online、SharePoint Online 等等)。

4.  記下您的條件式存取設定，並使用這些資訊作為參考，在新的 Azure 入口網站中建立相同的條件式存取原則。

### <a name="app-and-device-based-conditional-access-policies-working-together"></a>應用程式和裝置型條件式存取原則一起使用

新的 Azure 入口網站中的 [Intune 應用程式防護] 刀鋒視窗，可讓管理員設定應用程式為基礎的條件式規則，讓僅支援 Intune 應用程式防護原則的應用程式也可以存取公司資源。 您可以選擇使用裝置型條件式存取原則來重疊這些以應用程式為基礎的條件式存取原則。 取決於您要合併裝置型和以應用程式為基礎的條件式原則 (邏輯 AND)，還是要提供選項 (邏輯 OR)。 如果您的條件式存取原則需求為：

- 需要相容的裝置**且**使用核准的應用程式。
    - 您應該使用 [Azure AD 條件式存取刀鋒視窗](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies)和 [Intune 應用程式防護刀鋒視窗](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0)來設定條件式存取原則。
<br /><br />
- 需要相容的裝置**或**使用核准的應用程式。
    - 您應該使用 [Intune 傳統入口網站](https://manage.microsoft.com)和 [Intune 應用程式防護刀鋒視窗](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0)來設定條件式存取原則。

> [!TIP] 
> 本主題提供 Intune 傳統入口網站和新版 Azure 入口網站的使用者體驗比較螢幕擷取畫面。

## <a name="to-re-assign-intune-device-based-conditional-access-policies"></a>重新指派 Intune 裝置型條件式存取原則

1. 移至[新 Azure 入口網站中的條件式存取](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies)並以您的認證登入。

2. 選擇 [新增原則]。

3. 提供原則的名稱。

4. 選擇 [指派] 區段下的 [使用者和群組]，以新的條件式存取原則為目標。
    
    ![Intune 傳統和新 Azure 入口網站之間的使用者群組 UI 比較](./media/reassign-ca-1.png)

    > [!IMPORTANT] 
    > 如已在 Intune 傳統入口網站中選取所有使用者，會包含「所有」使用者。 這同樣適用於群組，如已選取群組，您必須選擇 [select individual users and groups] (選取個別的使用者和群組) 来包含這些群組。 此外，如已選擇 Intune 傳統入口網站的 [豁免群組] 選項，您需要排除新 Azure 入口網站中的選取群組。

5. 選擇群組之後，請按一下 [選取]，然後按一下 [完成]。

6. 選擇 [指派] 區段下的 [雲端應用程式]。

7. 在 [雲端應用程式] 刀鋒視窗中，選擇 [選取應用程式]。

8. 選擇您想要套用新條件式存取原則的應用程式，按一下 [選取]。

9. 按一下 [完成]。

    ![Intune 傳統和新 Azure 入口網站之間的雲端應用程式 UI 比較](./media/reassign-ca-3.png)

    > [!TIP] 
    > 如有多個應用程式使用相同的原則，您可以考慮將它們合併成新 Azure 入口網站中的單一原則。

10. 選擇 [指派] 區段下的 [條件]。

11. 在 [條件] 刀鋒視窗中，選擇 [裝置平台]，然後選擇適用的裝置平台。

12. 完成選擇裝置平台後，請按兩下 [完成]。

    ![Intune 傳統和新 Azure 入口網站之間的裝置平台 UI 比較](./media/reassign-ca-4.png)

    > [!TIP] 
    > 如已選擇 Intune 傳統入口網站中的個別平台，新的 Azure 入口網站也請選擇個別的平台。

    > [!NOTE] 
    > 稍後可以指定 Windows 的加入網域或相容選項。

13. 選擇 [指派] 區段下的 [條件]。

14. 在 [條件] 刀鋒視窗中選擇 [用戶端應用程式]，然後選擇合適的用戶端應用程式。

15. 完成選擇用戶端應用程式後，請按兩下 [完成]。

    ![Intune 傳統和新 Azure 入口網站之間的用戶端應用程式 UI 比較](./media/reassign-ca-6.png)

16. 如已選擇 Intune 傳統入口網站的瀏覽器設定，新的 Azure 入口網站請同時選取 [瀏覽器] 和 [行動裝置 App 及桌面用戶端]。 如未在 Intune 傳統入口網站中選擇瀏覽器設定，請只選擇 [行動裝置 App 及桌面用戶端]。 

17. 選擇 [存取控制] 區段下的 [授與]。

18. 選擇 [Grant Access Controls] (授與存取控制) 下的 [裝置需要標記為合規]，然後按一下 [選取]。

19. 如有要求 Windows 裝置加入網域的原則，而您也允許在 Intune 註冊過且符合規範的 Windows 裝置，請選擇 [要求已加入網域的裝置] 和 [裝置需要標記為合規] 以及 [需要其中一個選取的控制項]。

20. 如不允許在 Intune 註冊過且符合規範的 Windows 裝置，請從目前的原則中排除 Windows 原則，然後另外建立原則，將 [裝置平台] 設為 [Windows]，如上述包含其他條件為一個集合，然後選擇 [Grant Access Controls] (授與存取控制) 下的 [要求已加入網域的裝置]。

21. 開啟 [新增] 條件式存取原則刀鋒視窗的 [啟用原則] 切換，然後按一下 [建立]。

    ![啟用 Intune 傳統和新 Azure 入口網站之間的條件式存取原則 UI 比較](./media/reassign-ca-11.png)

## <a name="to-reassign-intune-device-based-conditional-access-policies-for-eas-clients"></a>重新指派 EAS 用戶端的 Intune 裝置型條件式存取原則

如已在 Intune 傳統入口網站中設定 Exchange Active Sync (EAS) 設定為 Exchange Online 原則的一部分，您需要在新的 Azure 入口網站中建立第二個條件式存取原則。

1. 移至[新 Azure 入口網站中的條件式存取](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies)並以您的認證登入。

2. 選擇 [新增原則]。

3. 提供原則的名稱。

4. 選擇 [指派] 區段下的 [使用者和群組]，以新的條件式存取原則為目標。

    ![Intune 傳統和新 Azure 入口網站之間的使用者群組 UI 比較](./media/reassign-ca-12.png)

    > [!IMPORTANT] 
    > 如已在 Intune 傳統入口網站中選取所有使用者，會包含「所有」使用者。 這同樣適用於群組，如已選取群組，您必須選擇 [select individual users and groups] (選取個別的使用者和群組) 來包含這些群組。 此外，如已選擇 Intune 傳統入口網站的 [豁免群組] 選項，您需要排除新 Azure 入口網站中的選取群組。

5. 選擇群組之後，請按一下 [選取]，然後按一下 [完成]。

6. 選擇 [指派] 區段下的 [雲端應用程式]。

7. 在 [雲端應用程式] 刀鋒視窗中，按一下 [選取的應用程式]，選擇 [Exchange Online]，按一下 [選取]，然後按一下 [完成]。

    ![Intune 傳統和新 Azure 入口網站之間的雲端應用程式 UI 比較](./media/reassign-ca-14.png)

    > [!IMPORTANT] 
    > EAS 用戶端的條件式存取原則不能包含任何其他雲端應用程式。

8. 在 [條件] 刀鋒視窗中選擇 [用戶端應用程式]，然後選擇合適的用戶端應用程式。 如已選擇封鎖 Intune 不支援的用戶端，請使用 [僅將原則套用至支援的平台] 選項。

    ![Intune 傳統和新 Azure 入口網站之間的用戶端應用程式 UI 比較](./media/reassign-ca-15.png)

9. 完成選擇用戶端應用程式後，請按兩下 [完成]。

10. 選擇 [存取控制] 區段下的 [授與]。

11. 選擇 [Grant Access Controls] (授與存取控制) 下的 [裝置需要標記為合規]，然後按一下 [選取]。

    ![Intune 傳統和新 Azure 入口網站之間的授與存取權 UI 比較](./media/reassign-ca-16.png)

12. 開啟 [新增] 條件式存取原則刀鋒視窗的 [啟用原則] 切換，然後按一下 [建立]。

    ![啟用 Intune 傳統和新 Azure 入口網站之間的條件式存取原則 UI 比較](./media/reassign-ca-17.png)

## <a name="disable-conditional-access-policies-in-the-intune-classic-portal"></a>停用 Intune 傳統入口網站的條件式存取原則
### <a name="before-you-start"></a>開始之前

一旦在新的 Azure 入口網站中重新指派了條件式存取原則，請務必逐漸停用先前在 Intune 傳統入口網站中建立的條件式存取原則。 此外，您可能也需要使用相同的安全性群組，以套用在新 Azure 入口網站中建立的條件式存取原則。

- 請先參閱本主題開頭的[開始之前](#before-you-begin)一節，再停用 Intune 傳統入口網站中的條件式存取原則。

### <a name="to-disable-the-conditional-access-policies"></a>停用條件式存取原則

1.  移至 [Intune 傳統入口網站](https://manage.microsoft.com)，並使用您的認證登入。

2.  在左側功能表中選擇 [原則]。

3.  選擇 [條件式存取]，然後選取您已為其建立條件式存取原則的 Microsoft 雲端服務 (Exchange Online、SharePoint Online 等等)。

4.  取消核取 [啟用 Exchange Online 的條件式存取原則] 選項，然後按一下 [儲存]。

    ![停用 Intune 傳統入口網站的條件式存取原則](./media/reassign-ca-18.png)

## <a name="see-also"></a>請參閱

- [透過 Intune 使用條件式存取的常見方式](conditional-access-intune-common-ways-use.md)
- [搭配 Intune 使用以應用程式為基礎的條件式存取](app-based-conditional-access-intune.md)
- [Azure Active Directory 中的條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)