---
title: "如何將應用程式指派給群組 | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰將應用程式新增至 Intune 之後，要將它指派到使用者或裝置的群組中。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: 21ccb23023e9cb4f4b827887f8191ea73474c5de
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---

# <a name="how-to-assign-apps-to-groups-with-microsoft-intune"></a>如何使用 Microsoft Intune 將應用程式指派給群組

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

將應用程式新增至 Intune 之後，要將它置入使用者及裝置中。 進行指派即可完成此作業。

不論應用程式是否由 Intune 管理，皆可指派到裝置。 使用下表有助於您了解將應用程式指派到使用者及裝置的各種選項︰

||||
|-|-|-|-|
|&nbsp;|註冊有 Intune 的裝置|未註冊有 Intune 的裝置|
|指派給使用者|是|是|
|指派給裝置|是|否|
|指派經包裝之應用程式或應用程式，與 Intune SDK (適用於應用程式保護原則) 合併運作|是|是|
|將應用程式指派為可用|是|是|
|將應用程式指派為必要項目|是|否|
|解除安裝應用程式|是|否|
|使用者從公司入口網站應用程式安裝可用的應用程式|是|否|
|使用者從 Web 架構入口網站安裝可用的應用程式|是|是|

> [!NOTE]
> 您目前可指派 iOS 與 Android 應用程式 (企業營運與市集購買兩者) 未註冊有 Intune 的裝置。

## <a name="changes-to-how-you-assign-apps-to-groups-in-the-intune-preview"></a>針對在 Intune 預覽中指派應用程式到群組之作法的變更

在 Intune Azure 預覽版中，您不再需要使用 Intune 群組來指派應用程式，並會改為使用 Azure Active Directory (Azure AD) 安全性群組。 因此，您需要了解應用程式指派運作方式的某些變更，尤其當您要指派應用程式到 Intune 子群組的時候。
最值得注意的是 Azure AD 中不存在的子群組的概念。 不過，某些群組可能會包含相同的成員。 在此情況下，傳統 Intune 和 Intune Azure 預覽版之間的行為會有差異。 如下表說明：

||||||
|-|-|-|-|-|
|**Intune 傳統型 (租用戶移轉前)**|-|**Intune Azure (租用戶移轉完成後)**|-|**詳細資訊**|
|**父群組指派用途**|**子群組指派用途**|**針對先前父群組和子群組一般成員的指派用途結果**|**針對父群組成員的指派用途動作結果**|-|    
|可用|必要|必要且可用|可用|「必要且可用」表示指派為必要的應用程式也會顯示在「公司入口網站」應用程式中。
|不適用|可用|不適用|不適用|因應措施︰從 Intune 父群組中移除「不適用」的指派用途。
|必要|可用|必要且可用|必要|-|
|必要且可用<sup>1</sup>|可用|必要且可用|必要且可用|-|    
|必要|不適用|必要|必要|-|    
|必要且可用|不適用|必要且可用|必要且可用|-|    
|必要|解除安裝|必要|必要|-|    
|必要且可用|解除安裝|必要且可用|必要且可用|-|
<sup>1</sup> 僅針對受管理的 iOS 市集應用程式，當您將這些應用程式新增到 Intune 並指派為「必要」時，系統會自動將它們建立成包含「必要」及「可用」用途。

您可以採取下列動作以避免指派衝突︰

1.    如果您先前將應用程式指派給相關的 Intune 父群組和子群組，建議您先移除這些指派，再開始進行租用戶移轉。
2.    移除父群組中的子群組，然後建立包含先前子群組成員的新群組。 接著，您可以對此群組建立新的應用程式指派。
注意：如果先前的父群組是「所有使用者」，則您需要建立不包含子群組成員的新動態群組。
您必須針對使用者和裝置群組對 [Azure 入口網站](https://portal.azure.com/)中的群組做出任何變更。 [傳統 Azure 入口網站](https://manage.windowsazure.com/)只允許您變更使用者群組。


## <a name="how-to-assign-an-app"></a>如何指派應用程式

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗上，選擇 [行動應用程式]。
1. 在**行動應用程式**工作負載中選擇 [管理]  >  [應用程式]。
2. 在應用程式刀鋒視窗清單中，按一下想要指派的應用程式。
3. 在 <*應用程式名稱*> - [概觀] 刀鋒視窗中，選擇 [管理]  >  [指派]。
4. 選擇 [選取群組]然後，在 [選取群組] 刀鋒視窗中，選擇要指派該應用程式的 Azure AD 群組。
5. 為每個您選擇的應用程式，從以下項目選擇應用程式的 [指派類型]︰
    - **可用** - 使用者從公司入口網站應用程式或網站，安裝應用程式。
    - **不適用** - 公司入口網站中未安裝或未顯示此應用程式。
    - **必要** - 此應用程式安裝所選群組中的裝置上。
    - **解除安裝** - 此應用程式會從所選群組中的裝置上解除安裝。
    - **是否有註冊皆可用** - 將此應用程式指派到其裝置未註冊有 Intune 的使用者群組。 請參閱上表中的說明。
6. 完成之後，請選擇 [儲存]。

應用程式現已指到您所選的群組。

請參閱[如何監視應用程式](monitor-apps.md)，以取得協助您監視應用程式指派的資訊。

