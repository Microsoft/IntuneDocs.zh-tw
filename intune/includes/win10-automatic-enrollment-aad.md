## <a name="enable-windows-10-automatic-enrollment"></a>啟用 Windows 10 自動註冊

使用者可利用自動註冊，在 Intune 中註冊其 Windows 10 裝置。 若要註冊，使用者必須將其公司帳戶新增至個人擁有的裝置，或將公司擁有的裝置加入 Azure Active Directory。 裝置會於背景註冊及加入 Azure Active Directory。 註冊後，就會使用 Intune 管理裝置。

**先決條件**
- Azure Active Directory Premium 訂閱 ([試用訂閱](http://go.microsoft.com/fwlink/?LinkID=816845))
- Microsoft Intune 訂閱


### <a name="configure-automatic-mdm-enrollment"></a>設定自動 MDM 註冊

1. 登入 [Azure 入口網站](https://portal.azure.com)，然後選取 [Azure Active Directory]。

  ![Azure 入口網站的螢幕擷取畫面](../media/auto-enroll-azure-main.png)

2. 選取 [行動性 (MDM 與 MAM)]。

  ![Azure 入口網站的螢幕擷取畫面](../media/auto-enroll-mdm.png)

3. 選取 [Microsoft Intune]。

  ![Azure 入口網站的螢幕擷取畫面](../media/auto-enroll-intune.png)

4. 設定 **MDM 使用者範圍**。 指定哪些使用者的裝置應該由 Microsoft Intune 管理。 這些 Windows 10 裝置將會自動註冊，而由 Microsoft Intune 管理。

  - **無**
  - **部分**
  - **全部**

   ![Azure 入口網站的螢幕擷取畫面](../media/auto-enroll-scope.png)

5. 使用下列 URL 的預設值：
    - **MDM 使用條款 URL**
    - **MDM 探索 URL**
    - **MDM 合規性 URL**

    > [!IMPORTANT]
    > 若已為群組同時啟用了 **MAM 使用者範圍**與自動 MDM 註冊 (**MDM 使用者範圍**)，則只會啟用 MAM。 當使用者將個人裝置加入工作區時，只會為該群組中的使用者新增 MAM。 裝置將不會自動 MDM 註冊。

6. 選取 [儲存]。

根據預設，不會對此服務啟用雙因素驗證。 不過，於註冊裝置時，會建議使用雙因素驗證。 若要啟用雙重要素驗證，請在 Azure AD 中設定雙重要素驗證提供者，並將您的使用者帳戶設定為進行雙重要素驗證。 請參閱[開始使用 Azure Multi-Factor Authentication Server](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud)。
