## <a name="set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium"></a>設定 Windows 10 及 Windows 10 行動裝置版自動向 Azure Active Directory Premium 註冊

自動註冊可讓使用者在 Intune 中註冊公司擁有或個人 Windows 10 電腦與 Windows 10 行動裝置，方法是新增工作或學校帳戶並同意進行管理。 就是這麼簡單。 在背景中，使用者的裝置註冊並加入 Azure Active Directory。 註冊後，就會使用 Intune 管理裝置。

**先決條件**
- Azure Active Directory Premium 訂閱 ([試用訂閱](http://go.microsoft.com/fwlink/?LinkID=816845))
- Microsoft Intune 訂閱


### <a name="configure-automatic-mdm-enrollment"></a>設定自動 MDM 註冊

1. 在 [Azure 管理入口網站](https://portal.azure.com) (https://manage.windowsazure.com) 中，巡覽至 **Active Directory** 節點並選取您的目錄。

2. 選擇 [應用程式] 索引標籤。 **Microsoft Intune** 會出現在應用程式清單中。

    ![Azure AD 應用程式與 Microsoft Intune](../media/aad-intune-app.png)

3. 選取 **Microsoft Intune** 的箭頭。 螢幕上會開啟一個頁面讓您設定 Microsoft Intune。

4. 選取 [設定]，以開始設定自動向 Microsoft Intune 執行 MDM 註冊。

5. 指定 Intune 的 URL：

  - **MDM 註冊 URL** - 使用預設值。
  - **MDM 使用條款 URL** – 使用預設值。 使用者註冊裝置時，此 URL 會顯示使用條款。
  - **MDM 相容性 URL** – 使用預設值。 如果發現裝置與合規性不符，即會顯示 [拒絕存取] 與此 URL。 此 URL 會指向可以協助使用者了解裝置不合規範的原因，以及其如何讓裝置符合規範的頁面。

6.  指定哪些使用者的裝置應該由 Microsoft Intune 管理。 這些使用者的 Windows 10 裝置將會自動註冊，以便使用 Microsoft Intune 管理。

  - **全部**
  - **群組**
  - **無**

7. 選擇 [儲存]。


<!--HONumber=Feb17_HO2-->


