---
ms.openlocfilehash: fbfff91d2993becc99e2132285bef78d245ff50e
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61497935"
---
## <a name="enable-windows-10-automatic-enrollment"></a>啟用 Windows 10 自動註冊

自動註冊可讓使用者在將工作帳戶新增到其個人擁有的裝置，或是將其公司擁有的裝置加入 Azure Active Directory 時，在 Intune 中註冊他們的 Windows 10 裝置。 在背景中，使用者的裝置註冊並加入 Azure Active Directory。 註冊之後，會使用 Intune 來管理裝置。

**必要條件**
- Azure Active Directory Premium 訂閱 ([試用訂閱](http://go.microsoft.com/fwlink/?LinkID=816845))
- Microsoft Intune 訂閱


### <a name="configure-automatic-mdm-enrollment"></a>設定自動 MDM 註冊

1. 登入 [Azure 管理入口網站 ](https://portal.azure.com) (https://manage.windowsazure.com) ，然後選取 **Azure Active Directory**。

   ![Azure 入口網站的螢幕擷取畫面](../media/auto-enroll-azure-main.png)

2. 選取 [行動性 (MDM 與 MAM)]。

   ![Azure 入口網站的螢幕擷取畫面](../media/auto-enroll-mdm.png)

3. 選取 [Microsoft Intune]。

   ![Azure 入口網站的螢幕擷取畫面](../media/auto-enroll-intune.png)

4. 設定 **MDM 使用者範圍**。 指定哪些使用者的裝置應該由 Microsoft Intune 管理。 這些使用者的 Windows 10 裝置將會自動註冊，以便使用 Microsoft Intune 管理。

   - **無**
   - **部分**
   - **全部**

   ![Azure 入口網站的螢幕擷取畫面](../media/auto-enroll-scope.png)

5. 使用下列 URL 的預設值：
   - **MDM 使用條款 URL**
   - **MDM 探索 URL**
   - **MDM 合規性 URL**

6. 選取 [儲存]。

根據預設，不會對此服務啟用雙因素驗證。 不過，於註冊裝置時，會建議使用雙因素驗證。 您必須先在 Azure Active Directory 中設定雙因素驗證提供者，並針對多重要素驗證來設定您的使用者帳戶之後，才會需要此服務的雙因素驗證。 請參閱[開始使用 Azure Multi-Factor Authentication Server](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud)。
