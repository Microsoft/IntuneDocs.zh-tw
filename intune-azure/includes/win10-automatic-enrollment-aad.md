## <a name="enable-windows-10-automatic-enrollment"></a>啟用 Windows 10 自動註冊

自動註冊可讓使用者在 Intune 中註冊公司擁有或個人 Windows 10 電腦與 Windows 10 行動裝置，方法是新增工作或學校帳戶並同意進行管理。 就是這麼簡單。 在背景中，使用者的裝置註冊並加入 Azure Active Directory。 註冊後，就會使用 Intune 管理裝置。

**先決條件**
- Azure Active Directory Premium 訂閱 ([試用訂閱](http://go.microsoft.com/fwlink/?LinkID=816845))
- Microsoft Intune 訂閱


### <a name="configure-automatic-mdm-enrollment"></a>設定自動 MDM 註冊

1. 登入 [Azure 管理入口網站](https://portal.azure.com) (https://manage.windowsazure.com)，然後選取 [Azure Active Directory]。

  ![Azure 入口網站的螢幕擷取畫面](../media/auto-enroll-azure-main.png)

2. 選取 [行動性 (MDM 與 MAM)]。

  ![Azure 入口網站的螢幕擷取畫面](../media/auto-enroll-mdm.png)

3. 選取 [Microsoft Intune]。

  ![Azure 入口網站的螢幕擷取畫面](../media/auto-enroll-intune.png)

4. 設定哪些使用者將會自動註冊。

  ![Azure 入口網站的螢幕擷取畫面](../media/auto-enroll-scope.png)

  使用下列 URL 的預設值：
  - **MDM 註冊**
  - **MDM 使用條款**
  - **MDM 合規性**

5. 指定哪些使用者的裝置應該由 Microsoft Intune 管理。 這些使用者的 Windows 10 裝置將會自動註冊，以便使用 Microsoft Intune 管理。

  - **全部**
  - **群組**
  - **無**

6. 選取 [儲存]。
