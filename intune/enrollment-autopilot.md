---
title: "使用 Windows AutoPilot Deployment 方案註冊 Windows 裝置"
description: "了解如何使用 Windows AutoPilot Deployment 方案註冊新的 Windows 10 裝置。"
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 11/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.openlocfilehash: 736eda24e355024e2abadd57206c0f0423e6d4b4
ms.sourcegitcommit: af958afce3070a3044aafea490c8afc55301d9df
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2017
---
# <a name="enroll-windows-devices-using-windows-autopilot-deployment-program"></a>使用 Windows AutoPilot Deployment 方案註冊 Windows 裝置
Windows AutoPilot Deployment 方案可簡化裝置佈建。 現在，需要許多時間來建置和維護自訂的作業系統映像。 您也可能會花很多時間將這些自訂的作業系統映像套用至新的裝置，以在送交使用者之前，先將它們做好使用的準備。 使用 Microsoft Intune 和 AutoPilot，您可以將新的裝置提供給使用者而不需要建置、維護及套用自訂作業系統映像至裝置。 當您使用 Intune 來管理 AutoPilot 裝置時，可以在它們註冊之後管理裝置上的原則、設定檔、應用程式等。 如需優點、案例和必要條件的概觀，請參閱 [Overview of Windows AutoPilot](https://docs.microsoft.com/windows/deployment/windows-10-auto-pilot) (Windows AutoPilot 概觀)。

## <a name="prerequisites"></a>必要條件
- [裝置必須註冊到您的組織](https://docs.microsoft.com/windows/deployment/windows-10-auto-pilot#registering-devices-to-your-organization)
- [已啟用 Windows 自動註冊](https://docs.microsoft.com/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune#enable-windows-10-automatic-enrollment)
- [Azure Active Directory Premium 訂用帳戶](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="synchronize-devices"></a>同步處理的裝置
將您的已註冊裝置同步到 Intune，以便設定它們。

1. 登入 [Azure](https://portal.azure.com/)。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置註冊]。
4. 在 [Windows 註冊] 刀鋒視窗的 [Windows AutoPilot Deployment 方案] 區段，選擇 [裝置]。
5. 按一下 [同步處理] 匯入已註冊的裝置。 訊息會顯示正在進行同步處理。
6. 重新整理檢視可查看新的裝置。 程序可能需要幾分鐘才能完成，取決於有多少裝置正在進行同步處理。  

## <a name="create-an-autopilot-deployment-profile"></a>建立 AutoPilot 部署設定檔
AutoPilot 部署設定檔用來設定 AutoPilot 裝置。
1. 登入 [Azure](https://portal.azure.com/)。 
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置註冊]。
4. 在 [Windows 註冊] 刀鋒視窗的 [Windows AutoPilot Deployment 方案] 區段，選擇 [部署設定檔]。
5. 按一下 [建立設定檔]，然後選擇名稱和選擇性描述。 
6. 針對 [聯結類型]，選取 [已加入 Azure AD]。
7. 針對 [全新體驗 (OOBE)] 設定下列選項，然後按一下 [確定]： 
   - **隱私權設定**：選擇是否顯示隱私權設定給使用者。 
   - **使用者授權合約 (EULA)**：選擇是否顯示 EULA 給使用者。
   - **使用者帳戶類型**：選擇使用者的帳戶類型為 [系統管理員] 或 [標準] 使用者。

     > [!Note]    
     > 此設定不適用於 Global Administrator 或 Company Administrator 帳戶。 這些帳戶不能是標準使用者，因為這些帳戶可以存取 Azure AD 中的所有系統管理功能。
8. 按一下 [建立] 建立設定檔。 現在可以指派 AutoPilot 部署設定檔給裝置。
     
> [!Note]    
> 所有 AutoPilot 部署設定檔都設定了下列設定：
> - 略過 Cortana、OneDrive 和 OEM 登錄設定頁面
> - 針對工作或學校自動設定
> - 公司或學校品牌的登入體驗    

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Windows AutoPilot 未指派裝置的警示 <!-- 163236 -->
您可以檢視 Windows AutoPilot 未指派裝置的警示，查看有多少來自 AutoPilot 程式的裝置未指派 AutoPilot 部署設定檔。 您可以使用警示中的資訊來建立設定檔，並加以指派至未指派的裝置。 當您按一下警示時，會看到 Windows AutoPilot 裝置的完整清單，以及這些裝置的詳細資訊。 
1. 登入 [Azure](https://portal.azure.com/)。 
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置註冊]。
4. 選擇 [概觀] 查看警示。 按一下警示查看 AutoPilot 裝置的清單。  

## <a name="assign-an-autopilot-deployment-profile"></a>指派 AutoPilot 部署設定檔
建立 AutoPilot 部署設定檔之後，可以將它們指派給選取的裝置。

1. 登入 [Azure](https://portal.azure.com/)。 
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置註冊]。
4. 在 [Windows 註冊] 刀鋒視窗的 [Windows AutoPilot Deployment 方案] 區段，選擇 [裝置]。
5. 選取您要指派部署設定檔的目標裝置。 您可以篩選 [狀態] 資料行以輕鬆找出沒有指派設定檔的裝置。 
6. 按一下 [指派設定檔]並選取 AutoPilot 部署設定檔，然後按一下 [指派]。 訊息會顯示正在進行指派。
7. 重新整理檢視來查看設定檔已指派到裝置。 程序可能需要幾分鐘才能完成，取決於您選取了多少部裝置。 

> [!Note]
> 新的設定檔會指派給裝置。 不過，設定檔不會套用到已在 Intune 註冊的裝置，直到裝置已重設並重新註冊為止。

### <a name="assign-a-different-autopilot-deployment-profile"></a>指派不同的 AutoPilot 部署設定檔
指派 AutoPilot 部署設定檔給裝置之後，如果您決定要指派不同的設定檔，請指派新設定檔給裝置。  

## <a name="edit-an-autopilot-deployment-profile"></a>編輯 AutoPilot 部署設定檔 
建立 AutoPilot 部署設定檔之後，您可以編輯部署設定檔的某些部分。   
1. 登入 [Azure](https://portal.azure.com/)。 
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置註冊]。
4. 在 [Windows 註冊] 刀鋒視窗的 [Windows AutoPilot Deployment 方案] 區段，選擇 [部署設定檔]。 
5. 選取您想要編輯的設定檔。 
6. 按一下左邊的 [屬性]，變更部署設定檔的名稱或描述。 進行變更之後請按一下 [儲存]。 
7. 按一下 [設定] 以變更 OOBE 設定。 進行變更之後請按一下 [儲存]。 

> [!NOTE]
> 更新的設定檔會指派給裝置。 不過，更新的設定檔不會套用到已在 Intune 註冊的裝置，直到裝置已重設並重新註冊為止。 

## <a name="using-autopilot-in-other-portals"></a>在其他入口網站中使用 AutoPilot
如果您對行動裝置管理沒有興趣，可以在 Microsoft Store for Business (舉例來說) 中使用 AutoPilot。 雖然可以選擇使用其他入口網站，我們建議您只使用 Intune 來管理 AutoPilot 部署。 如果您使用 Intune 與另一個入口網站，Intune 將無法：
- 顯示在 Intune 中建立但在另一個入口網站中編輯之設定檔的變更
- 同步處理在另一個入口網站中建立的設定檔
- 顯示在另一個入口網站中進行的設定檔指派變更
- 同步處理在另一個入口網站中進行的設定檔指派

## <a name="next-steps"></a>後續步驟
您為已註冊的 Windows 10 裝置設定 Windows AutoPilot 之後，請了解如何管理這些裝置。 如需詳細資料，請參閱[什麼是 Microsoft Intune 裝置管理？](https://docs.microsoft.com/intune/device-management)