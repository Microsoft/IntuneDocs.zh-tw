---
title: 使用 Intune 設定裝置型條件式存取
titleSuffix: Microsoft Intune
description: 了解如何根據 Microsoft Intune 裝置合規性和行動應用程式管理來建立裝置型條件式存取原則。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fde15da898a70e9557aabb9ed7a7ae8324cfb304
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74188325"
---
# <a name="create-a-device-based-conditional-access-policy"></a>建立裝置型條件式存取原則

使用 Intune，將行動裝置合規性新增到存取控制項，以增強 Azure Active Directory 中的條件式存取。 使用定義裝置合規性需求的 Intune 合規性政策，您就可以使用裝置的合規性狀態，以允許或封鎖其對應用程式和服務的存取。 您可以建立使用 [裝置需要標記為合規]  設定的條件式存取原則來執行此動作。

條件式存取原則會指定要保護的應用程式或服務、可存取應用程式或服務的條件，以及套用原則的使用者。 雖然條件式存取是 Azure AD Premium 功能，但您從 *Intune* 所存取條件式存取節點和從 *Azure AD* 所存取節點是一樣的。

> [!IMPORTANT]
> 設定條件式存取之前，您必須先設定 Intune 裝置合規性政策，根據裝置是否符合特定需求來評估裝置。 請參閱 [Intune 中的裝置合規性政策入門](device-compliance-get-started.md)。

## <a name="create-conditional-access-policy"></a>建立條件式存取原則

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。

2. 選取 [裝置]   > [條件式存取]   > [原則]   > [新原則]  。
  ![建立新的條件式存取原則](./media/create-conditional-access-intune/create-ca.png)

3. 在 [指派]  底下，選取 [使用者和群組]  。

4. 在 [包含]  索引標籤上，找出您要套用此條件式存取原則的使用者或群組。 選擇要包含的群組或使用者後，如有想從此原則中排除的任何使用者、角色或群組，請使用 [排除]  索引標籤。

   - **所有使用者**：選取此選項以將原則套用至所有使用者和群組，包括內部使用者和來賓使用者。

   - **選取使用者和群組**：選取此選項並指定下列一或多個選項：
  
     1. **所有來賓使用者**：選取此選項以包含或排除外部來賓使用者 (例如合作夥伴、外部共同作業者)

     2. **目錄角色**：選取一或多個 Azure AD 角色，以包含或排除被指派這些角色的使用者。

     3. **使用者和群組**：選取此選項以搜尋並選取要包含或排除的個別使用者或群組。

        > [!TIP]
        > 針對較小型的使用者群組測試原則，確定它如預期般運作。

5. 選取 [完成]  。

6. 在 [指派]  底下，選取 [雲端應用程式或動作]  。

7. 在 [包含]  索引標籤上，使用可用的選項找出要使用此條件式存取原則來保護的應用程式和服務。 接著，如果您有想從此原則排除的應用程式或服務，可以使用 [排除]  索引標籤。

   - **所有雲端應用程式**：選取此選項以將原則套用至所有應用程式。
     > [!IMPORTANT]
     > 用於存取 Azure 入口網站的 Microsoft Azure 管理應用程式包含在此清單中。 請務必在此處或 [使用者和群組]  選項中使用 [排除]  索引標籤，以確保您 (或您指定的使用者或群組) 能夠登入 Azure 入口網站。 

   - **選取應用程式**：選取此選項，選擇 [選取]  ，然後使用應用程式清單來搜尋並選取您要保護的應用程式或服務。

   準備就緒時，請選取 [完成]  。

8. 在 [指派]  底下，選取 [條件]  。

   - **登入風險**：選取 [是]  來將 Azure AD Identity Protection 登入風險偵測與此原則搭配使用，然後選擇原則應套用的登入風險層級。

   - **裝置平台**：在 [包含]  索引標籤上，找出您要套用此條件式存取原則的裝置平台。 使用 [排除]  索引標籤將平台從此原則排除。

   - **位置**：在 [包含]  索引標籤上，指定是否將原則套用至：
     - 任何位置
     - 受 IT 部門控制的受信任網路位置
     - 特定的網路位置。

     使用 [排除]  索引標籤將網路位置從此原則排除。

   - **用戶端應用程式**：選取 [是]  來指定是否應將此原則套用至瀏覽器應用程式、行動裝置應用程式和桌面用戶端。

   - **裝置狀態**：除非您選擇 [是]，並特別排除狀態「已加入裝置混合式 Azure AD」或「標示為符合規範的裝置」(或兩者)，否則，條件式存取原則將套用至所有裝置狀態。

     > [!TIP]
     > 如果您想要保護**新式驗證**用戶端和 **Exchange ActiveSync 用戶端**，請建立兩個不同的條件式存取原則，每個用戶端類型各一個。 雖然 Exchange ActiveSync 支援新式驗證，但 Exchange ActiveSync 支援的唯一條件是平台。 不支援其他條件 (包含多重要素驗證)。 若要有效地保護從 Exchange ActiveSync 存取 Exchange Online，請建立條件式存取原則，選取 [僅將原則套用至支援的平台]，來指定雲端應用程式 Office 365 Exchange Online 和用戶端應用程式 Exchange ActiveSync。

9. 選取 [完成]  。

10. 在 [存取控制]  底下，選取 [授與]  。 根據您所設定的條件，設定會發生的事。  您可以從下列選項中選取：

    - **封鎖存取**：此原則中指定的使用者處於您所指定的條件時，將會被拒絕存取應用程式。
    - **授與存取權**：此原則中指定的使用者將會被授與存取權，但您可以要求下列任意進一步的動作：
      - **需要多重要素驗證**：使用者必須完成額外的安全性需求，例如電話或簡訊。
      - **裝置需要標記為合規**：裝置必須符合 Intune 規範。 如果裝置不符規範，將會提供使用者在 Intune 中註冊裝置的選項。
      - **需要已加入混合式 Azure AD 的裝置**：裝置必須已加入混合式 Azure AD。
      - **需要經過核准的用戶端應用程式**：裝置必須使用經過核准的用戶端應用程式。 
      - **針對多個控制項**：選取 [需要所有選取的控制項]  ，以在裝置嘗試存取應用程式時，強制執行上述所有需求。

      ![存取控制授與設定](./media/create-conditional-access-intune/create-ca-grant-access-settings.png)

11. 在 [啟用原則]  底下，選取 [開啟]  。

12. 選取 [建立]  。

## <a name="next-steps"></a>後續步驟

[搭配 Intune 使用以應用程式為基礎的條件式存取](app-based-conditional-access-intune.md)

[針對 Intune 條件式存取進行疑難排解](https://support.microsoft.com/help/4456106) \(機器翻譯\)
