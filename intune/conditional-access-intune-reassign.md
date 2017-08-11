---
title: "將條件式存取原則從 Intune 傳統入口網站移轉到 Azure 入口網站"
titleSuffix: Intune on Azure
description: "將條件式存取原則從 Intune 傳統入口網站移轉到 Azure 入口網站。"
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
ms.openlocfilehash: d5f1ea2b0ceb32d0aa05a28e0f01f65b80b1ddcf
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2017
---
# <a name="reassign-conditional-access-policies-from-intune-classic-portal-to-the-azure-portal"></a>將條件式存取原則從 Intune 傳統入口網站重新指派給 Azure 入口網站

自新的 Azure 入口網站開始，條件式存取支援每個應用程式可有多項原則，以及更多的自訂功能。

## <a name="before-you-begin"></a>開始之前

若已準備好移往 Azure 入口網站，請遵循本主題中的步驟，重新指派先前在 Intune 傳統入口網站中建立的條件式存取原則：

- 收集先前建立的條件式存取原則，以了解稍後重新指派時需要哪些設定。

- 遵循本主題中的步驟，在 Azure 入口網站中重新建立這些原則。

- 確認新的原則在 Azure 入口網站中能如預期運作之後，請停用 Intune 傳統主控台中的條件式原則。
<br /><br />
    - 請先規劃如何將使用者移至新的原則，**再停用** Intune 傳統入口網站中條件式存取原則。 有兩種方式：
<br /><br />
        - **使用相同的包含群組來套用在 Azure 入口網站中建立的原則，並建立新的豁免群組來使用 Intune 傳統入口網站所套用的原則**。
            - 逐漸將某些使用者移至傳統入口網站中指定的豁免群組。 這可避免 Intune 傳統入口網站套用目標原則。 除了 Intune 傳統入口網站中已套用的原則外，所有以 Azure 入口網站中相同的使用者群組為目標所建立的原則都會套用。 
<br /><br />
        - **建立新的群組，以 Azure 入口網站的條件式存取原則為目標**。 如果選擇此方式，需要執行下列作業：
            - 逐漸移除 Intune 傳統入口網站中以條件式存取原則為目標之安全性群組的使用者。
            - 確認新原則可作用於這些使用者之後，即可停用 Intune 傳統入口網站中的原則。 
<br /><br />
- 如已設定條件式存取原則設定在 Intune 傳統入口網站中使用 Exchange Active Sync (EAS)，請參閱[本主題中的指示](#to-reassign-intune-device-based-conditional-access-policies-for-eas-clients)**在 Azure 入口網站中重新指派 EAS 條件式存取原則設定**。

### <a name="to-verify-your-device-based-conditional-access-policies-in-the-intune-classic-portal"></a>在 Intune 傳統入口網站中確認裝置型條件式存取原則

1.  移至 [Intune 傳統入口網站](https://manage.microsoft.com)，並使用您的認證登入。

2.  在左側功能表中選擇 [原則]。

3.  選擇 [條件式存取]，然後選取您已為其建立條件式存取原則的 Microsoft 雲端服務 (例如 Exchange Online 或 SharePoint Online)。

4.  記下您的條件式存取設定，並在 Azure 入口網站中建立相同的條件式存取原則時參考這些設定。

### <a name="app-and-device-based-conditional-access-policies-working-together"></a>應用程式和裝置型條件式存取原則一起使用

Azure 入口網站中的 [Intune 應用程式防護] 刀鋒視窗，可讓系統管理員設定以應用程式為基礎的條件式規則，僅允許支援 Intune 應用程式防護原則的應用程式存取公司資源。 您可以選擇使用裝置型條件式存取原則，來覆寫這些以應用程式為基礎的條件式存取原則。 您可以合併裝置型和以應用程式為基礎的條件式原則 (邏輯 AND)，也可以提供任一選項 (邏輯 OR)。 如果您的條件式存取原則需求為：

- 需要相容的裝置**且**使用核准的應用程式。
    - 您應該使用 [Azure Active Directory 條件式存取刀鋒視窗](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies)和 [Intune 應用程式防護刀鋒視窗](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0)來設定條件式存取原則。
<br /><br />
- 需要相容的裝置**或**使用核准的應用程式。
    - 您應該使用 [Intune 傳統入口網站](https://manage.microsoft.com)和 [Intune 應用程式防護刀鋒視窗](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0)來設定條件式存取原則。

> [!TIP] 
> 本主題提供 Intune 傳統入口網站和 Azure 入口網站的使用者體驗比較螢幕擷取畫面。

## <a name="reassign-intune-device-based-conditional-access-policies"></a>重新指派 Intune 裝置型條件式存取原則

1. 移至 [Azure 入口網站中的條件式存取](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies)並以您的認證登入。

2. 選擇 [新增原則]。

3. 提供原則的名稱。

4. 在 [指派] 區段下，選擇 [使用者和群組]，以新的條件式存取原則為目標。
    
    ![Intune 與 Azure 入口網站之間的使用者群組 UI 比較](./media/reassign-ca-1.png)

    > [!IMPORTANT] 
    > 您在 Azure 入口網站中所做的選擇，應該會對應至您在 Intune 入口網站中所做的選擇。 例如，如已在 Intune 傳統入口網站中選取所有使用者，請在 Azure 入口網站中選取 [所有使用者]。 此外，如已在 Intune 傳統入口網站中選擇 [豁免群組] 選項，也請在 Azure 入口網站中排除這些選取的群組。

5. 選擇群組之後，按一下 [選取]，然後按一下 [完成]。

6. 在 [指派] 區段下，選擇 [雲端應用程式]。

7. 在 [雲端應用程式] 刀鋒視窗中，選擇 [選取應用程式]。

8. 選擇您想要套用新條件式存取原則的應用程式，然後按一下 [選取]。

9. 按一下 [完成]。

    ![Intune 與 Azure 入口網站之間的雲端應用程式 UI 比較](./media/reassign-ca-3.png)

    > [!TIP] 
    > 如有多個應用程式使用相同的原則，請考慮將它們合併成 Azure 入口網站中的單一原則。

10. 在 [指派] 區段下，選擇 [條件]。

11. 在 [條件] 刀鋒視窗中，選擇 [裝置平台]，然後選擇適用的裝置平台。

12. 完成選擇裝置平台後，請按兩下 [完成]。

    ![Intune 與 Azure 入口網站之間的裝置平台 UI 比較](./media/reassign-ca-4.png)

    > [!TIP] 
    > 如已在 Intune 傳統入口網站中選擇個別平台，也請在 Azure 入口網站中選擇個別平台。

    > [!NOTE] 
    > 稍後可以指定 Windows 的加入網域或相容選項。

13. 在 [指派] 區段下，選擇 [條件]。

14. 在 [條件] 刀鋒視窗中，選擇 [用戶端應用程式]，然後選擇適用的用戶端應用程式。

15. 完成選擇用戶端應用程式後，請按兩下 [完成]。

    ![Intune 與 Azure 入口網站之間的用戶端應用程式 UI 比較](./media/reassign-ca-6.png)

16. 如已在 Intune 傳統入口網站中選擇瀏覽器設定，請在 Azure 入口網站中同時選取 [瀏覽器] 和 [行動裝置 App 及桌面用戶端]。 如未在 Intune 傳統入口網站中選擇瀏覽器設定，請只選擇 [行動裝置 App 及桌面用戶端]。 

17. 在 [存取控制] 區段下，選擇 [授與]。

18. 在 [Grant Access Controls] (授與存取控制)) 下，選擇 [裝置需要標記為相容]，然後按一下 [選取]。

19. 如有要求 Windows 裝置加入網域的原則，而您也允許 Intune 已註冊且相容的 Windows 裝置，請選擇 [要求已加入網域的裝置] 和 [裝置需要標記為相容]，以及 [需要其中一個選取的控制項]。

20. 如不允許 Intune 已註冊且相容的 Windows 裝置，請從目前的原則中排除 Windows 原則。 然後另外建立原則，將 [裝置平台] 設為 [Windows]，如上述包含其他條件為一個集合，然後選擇 [Grant Access Controls] (授與存取控制) 下的 [要求已加入網域的裝置]。

21. 在 [新增] 條件式存取原則刀鋒視窗中，開啟 [啟用原則] 切換，然後按一下 [建立]。

    ![Intune 與 Azure 入口網站之間的啟用條件式存取原則 UI 比較](./media/reassign-ca-11.png)

## <a name="reassign-intune-device-based-conditional-access-policies-for-eas-clients"></a>重新指派 EAS 用戶端的 Intune 裝置型條件式存取原則

如已在 Intune 傳統入口網站中將 Exchange Active Sync 設定為 Exchange Online 原則的一部分，則您需要在 Azure 入口網站中建立第二個條件式存取原則。

1. 移至 [Azure 入口網站中的條件式存取](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies)並以您的認證登入。

2. 選擇 [新增原則]。

3. 提供原則的名稱。

4. 在 [指派] 區段下，選擇 [使用者和群組]，以新的條件式存取原則為目標。

    ![Intune 與 Azure 入口網站之間的使用者群組 UI 比較](./media/reassign-ca-12.png)

    > [!IMPORTANT] 
    > 您在 Azure 入口網站中所做的選擇，應該會對應至您在 Intune 入口網站中所做的選擇。 例如，如已在 Intune 傳統入口網站中選取所有使用者，請在 Azure 入口網站中選取 [所有使用者]。 此外，如已在 Intune 傳統入口網站中選擇 [豁免群組] 選項，也請在 Azure 入口網站中排除這些選取的群組。

5. 選擇群組之後，按一下 [選取]，然後按一下 [完成]。

6. 在 [指派] 區段下，選擇 [雲端應用程式]。

7. 在 [雲端應用程式] 刀鋒視窗中，按一下 [選取應用程式] 並選擇 [Exchange Online]。 然後按一下 [選取] 和 [完成]。

    ![Intune 與 Azure 入口網站之間的雲端應用程式 UI 比較](./media/reassign-ca-14.png)

    > [!IMPORTANT] 
    > EAS 用戶端的條件式存取原則不能包含任何其他雲端應用程式。

8. 在 [條件] 刀鋒視窗中，選擇 [用戶端應用程式]，然後選擇適用的用戶端應用程式。 如已選擇封鎖 Intune 不支援的用戶端，請使用 [僅將原則套用至支援的平台] 選項。

    ![Intune 與 Azure 入口網站之間的用戶端應用程式 UI 比較](./media/reassign-ca-15.png)

9. 完成選擇用戶端應用程式後，請按兩下 [完成]。

10. 在 [存取控制] 區段下，選擇 [授與]。

11. 在 [Grant Access Controls] (授與存取控制)) 下，選擇 [裝置需要標記為相容]，然後按一下 [選取]。

    ![Intune 與 Azure 入口網站之間的授與存取權 UI 比較](./media/reassign-ca-16.png)

12. 在 [新增] 條件式存取原則刀鋒視窗中，開啟 [啟用原則] 切換，然後按一下 [建立]。

    ![Intune 與 Azure 入口網站之間的啟用條件式存取原則 UI 比較](./media/reassign-ca-17.png)

## <a name="disable-conditional-access-policies-in-the-intune-classic-portal"></a>停用 Intune 傳統入口網站的條件式存取原則

在 Azure 入口網站中重新指派條件式存取原則之後，請務必逐漸停用先前在 Intune 傳統入口網站中建立的條件式存取原則。 此外，您可能也需要使用相同的安全性群組，以套用在 Azure 入口網站中建立的條件式存取原則。

> [!NOTE] 
    > 請先參閱本主題開頭的[開始之前](#before-you-begin)一節，再停用 Intune 傳統入口網站中的條件式存取原則。

### <a name="to-disable-the-conditional-access-policies"></a>停用條件式存取原則

1.  移至 [Intune 傳統入口網站](https://manage.microsoft.com)，並使用您的認證登入。

2.  在左側功能表中選擇 [原則]。

3.  選擇 [條件式存取]，然後選取您已為其建立條件式存取原則的 Microsoft 雲端服務 (例如 Exchange Online 或 SharePoint Online)。

4.  取消核取 [啟用 Exchange Online 的條件式存取原則] 選項，然後按一下 [儲存]。

    ![停用 Intune 傳統入口網站的條件式存取原則](./media/reassign-ca-18.png)

## <a name="see-also"></a>請參閱

- [透過 Intune 使用條件式存取的常見方式](conditional-access-intune-common-ways-use.md)
- [搭配 Intune 使用以應用程式為基礎的條件式存取](app-based-conditional-access-intune.md)
- [Azure Active Directory 中的條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
