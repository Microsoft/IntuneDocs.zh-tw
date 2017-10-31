---
title: "準備好設定適用於 Windows 10 的應用程式保護原則"
titlesuffix: Azure portal
description: "設定 Azure AD 中的行動應用程式管理 (MAM) 提供者"
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 09f3edbe8b53371514ae4826246c99201c005762
ms.sourcegitcommit: b5692ee05e8be1842cb1007facf80c9bce972dc4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/26/2017
---
# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>準備好設定適用於 Windows 10 的應用程式保護原則

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

透過在 Azure AD 中設定 MAM 提供者，針對 Windows 10 啟用行動應用程式管理 (MAM)。 在 Azure AD 中設定 MAM 提供者可讓您在使用 Intune 建立新的 Windows 資訊保護 (WIP) 原則時定義註冊狀態。 註冊狀態可以是 MAM 或行動裝置管理 (MDM)。

> [!NOTE]
> 需要具有 MAM 註冊狀態的裝置才能加入 Azure AD。

## <a name="to-configure-the-mam-provider"></a>設定 MAM 提供者

1. 登入 Azure 入口網站，然後選擇 [Azure Active Directory]。

2. 選擇 [管理] 群組中的 [行動性 (MDM 與 MAM)]。

3. 按一下 [Microsoft Intune]。

4. 在 [設定] 刀鋒視窗上的 [還原預設的 MAM URL] 群組中進行設定。

    **MAM 使用者範圍**  
      使用 MAM 自動註冊來管理您員工之 Windows 裝置上的企業資料。 將會針對攜帶您自己的裝置案例設定 MAM 自動註冊。<ul><li>**無**<br>若所有使用者都可以在 MAM 中註冊，請選取此選項。</li><li>**部分**<br>選取包含將要在 MAM 中註冊之使用者的 Azure AD 群組。</li><li>**全部**<br>若所有使用者都可以在 MAM 中註冊，請選取此選項。</li></ul>

    **MDM 使用規定 URL**  
     MAM 服務之使用規定端點的 URL。 使用規定端點是用來在使用者註冊其裝置以供管理之前顯示服務條款給使用者。 使用規定文字會通知使用者關於在行動裝置上強制執行的原則。

    **MAM 探索 URL**  
    MAM 服務註冊端點的 URL。 註冊端點用來註冊裝置，以使用 MAM 服務進行管理。

    **MAM 合規性 URL**  
      MAM 服務的合規性端點的 URL。 當使用者從不符合規範的裝置存取資源遭拒時，將會對該使用者顯示此合規性 URL。 使用者可以瀏覽至 MDM 服務主控的此 URL，了解他們的裝置被視為不符合規範的原因。 使用者也可起始自助式補救，讓裝置變為符合規範，以繼續存取資源。

5.  按一下 [儲存]。

## <a name="next-steps"></a>後續步驟

[建立 WIP 應用程式保護原則](windows-information-protection-policy-create.md)
