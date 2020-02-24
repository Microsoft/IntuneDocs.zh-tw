---
title: 教學課程 - 使用 Apple Business Manager 或裝置註冊計劃在 Intune 中註冊 iOS/iPadOS 裝置
titleSuffix: Microsoft Intune
description: 在此教學課程中，您將會從 ABM 設定 Apple 的公司裝置註冊功能，以在 Intune 中註冊 iOS/iPadOS 裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/30/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up the Apple's corporate device enrollment features so that corporate devices can automatically enroll in Intune.
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9aab0233c05416fc50413a7889435cb221179730
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415148"
---
# <a name="tutorial-use-apples-corporate-device-enrollment-features-in-apple-business-manager-abm-to-enroll-iosipados-devices-in-intune"></a>教學課程：使用 Apple Business Manager (ABM) 中的公司裝置註冊功能在 Intune 中註冊 iOS/iPadOS 裝置
Apple Business Manager 中的裝置註冊功能簡化了註冊裝置的程序。 Intune 也支援 Apple 較舊的裝置註冊計劃 (DEP) 入口網站，但建議您使用 Apple Business Manager 重新開始。 使用 Microsoft Intune 和 Apple 公司裝置註冊，當使用者第一次開啟裝置時，就會自動安全地註冊裝置。 因此，您可以將裝置提供給許多使用者，而不必個別設定每部裝置。 

您將在本教學課程中了解如何：
> [!div class="checklist"]
> * 取得 Apple 裝置註冊權杖
> * 將受控裝置同步到 Intune
> * 建立註冊設定檔
> * 將註冊設定檔指派給裝置

如果您沒有 Intune 訂用帳戶，請[註冊免費試用帳戶](../fundamentals/free-trial-sign-up.md)。

## <a name="prerequisites"></a>先決條件
- 在 [Apple School Manager](https://business.apple.com) 或 [Apple 裝置註冊計劃](http://deploy.apple.com)中購買的裝置
- 設定[行動裝置管理授權單位](../fundamentals/mdm-authority-set.md)
- 取得 [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-device-enrollment-token"></a>取得 Apple 裝置註冊權杖
在使用 Apple 的公司註冊功能註冊 iOS/iPadOS 裝置前，您需要 Apple 裝置註冊權杖 (.pem) 檔案。 此權杖可讓 Intune 同步您公司擁有的 Apple 裝置資訊。 它也允許 Intune 將註冊設定檔上傳至 Apple，並將這些設定檔指派給裝置。

您可以使用 ABM 或 DEP 入口網站來建立裝置註冊權杖。 您也可以使用該入口網站將裝置指派給 Intune 以便管理。

1. 在 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，選擇 [裝置]   > [iOS]   > [iOS 註冊]   > [註冊方案權杖]   > [新增]  。

2. 藉由選取 [我同意]  來將權限授與 Microsoft，以將使用者和裝置資訊傳送給 Apple。

   ![[Apple 憑證] 工作區中 [註冊計劃權杖] 窗格下載公開金鑰的螢幕擷取畫面。](./media/tutorial-use-device-enrollment-program-enroll-ios/add-enrollment-program-token-pane.png)

3. 選擇 [下載您的公開金鑰]  ，在本機下載並儲存加密金鑰 (.pem) 檔案。 這個 .pem 檔案會用於向 ABM 或 DEP 入口網站要求信任關係憑證。

4. 選擇 [建立 Apple 裝置註冊計劃的權杖]  以開啟 Apple 的部署計劃入口網站，並使用您的公司 Apple ID 登入。 您可以使用此 Apple ID 來更新 DEP 權杖。

5. 在 Apple 的[部署計劃入口網站](https://deploy.apple.com)，針對 [裝置註冊計劃]  選擇 [開始使用]  。 您的程序可能會與 [Apple Business Manager](https://business.apple.com) 中的下列步驟稍有不同。

4. 在 [管理伺服器]  頁面上，選擇 [新增 MDM 伺服器]  。

5. 針對 [MDM 伺服器名稱]  輸入 *TestMDMServer*，然後選擇 [下一步]  。 您可參考這個伺服器名稱，以識別行動裝置管理 (MDM) 伺服器， 但它不是 Microsoft Intune 伺服器的名稱或 URL。

6. [新增 &lt;服器名稱&gt;]  對話方塊隨即開啟，指出**上傳您的公用金鑰**。 選取 [選擇檔案]  以上傳 .pem 檔案，然後選擇 [下一步]  。

6. 移至 [Deployment Programs] \(部署方案\)   > [裝置註冊計劃]   > [管理裝置]  。
7. 在 [Choose Devices By] \(選擇裝置依據\)  下，選擇 [序號]  。 <!--ask Tiffany about this-->

8. 針對 [選擇動作]  選擇 [Assign to Server] (指派給伺服器))  ，然後選擇指定給 Microsoft Intune 的 &lt;伺服器名稱&gt;，再選擇 [確定]  。 Apple 入口網站會將指定的裝置指派給 Intune 伺服器以便管理 ，然後顯示 [指派完成]  。

   在 Apple 入口網站中，移至 [部署計劃]  &gt; [裝置註冊計劃]  &gt; [檢視指派歷程記錄]  以查看裝置與其 MDM 伺服器指派的清單。

9. 在 Azure 入口網站的 Intune 中，提供用來建立此權杖的 Apple ID 供日後參考。

    ![指定要用於建立註冊計劃權杖的 Apple 識別碼，並瀏覽至註冊計劃權杖的螢幕擷取畫面。](./media/tutorial-use-device-enrollment-program-enroll-ios/image03.png)

10. 在 [Apple 權杖]  方塊中，瀏覽至憑證 (.pem) 檔案，選擇 [開啟]  ，然後選擇 [建立]  。 

11. 如果您想要套用範圍標籤，來限制哪些系統管理員可存取此權杖，請選取範圍。

## <a name="create-an-apple-enrollment-profile"></a>建立 Apple 註冊設定檔
安裝好權杖後，您可以開始為屬公司擁有的 iOS/iPadOS 裝置建立註冊設定檔。 裝置註冊設定檔會定義要在註冊期間套用至裝置群組的設定。

1. 在 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，選擇 [裝置]   > [iOS]   > [iOS 註冊]   > [註冊方案權杖]  。

2. 選取您剛安裝的權杖，然後選擇 [設定檔]   > [建立設定檔]  。

3. 在 [建立設定檔]  下，針對 [名稱]  輸入 *TestDEPProfile*，並針對 [描述]  輸入*測試 iOS/iPadOS 裝置的 DEP*。 使用者看不到這些詳細資料。

4. 在 [平台]  下選擇 [iOS]  。

5. 決定您希望裝置使用或不使用 [使用者親和性]  來註冊。 使用者親和性專用於特定使用者要使用的裝置。 若您的使用者要使用公司入口網站進行像是安裝應用程式等服務，選擇 [使用使用者親和性來註冊]  。 如果您的使用者不需要公司入口網站，或您想要針對許多使用者佈建裝置，請選擇 [不使用使用者親和性來註冊]  。

6. 如果您選擇使用使用者親和性來註冊，請決定要使用公司入口網站還是 Apple Setup Assistant 進行驗證。 如果您想要使用 Multi-factor Authentication，允許使用者第一次登入時變更密碼，或提示使用者在註冊期間重設其過期的密碼，請在 [使用公司入口網站，而非 Apple Setup Assistant 進行驗證]  下選擇 [是]  。 如果您想要使用 Apple 所提供透過 Apple Setup Assistant 進行的基本 HTTP 驗證，請選擇 [否]  。 如果選擇 [是]  ，且您希望公司入口網站應用程式自動在終端使用者的裝置上更新，請透過 Apple 的大量採購方案 (VPP)，將公司入口網站另行部署為這些使用者的必要應用程式。

7. 如果您選擇使用「使用者親和性」和「使用公司入口網站進行驗證」來註冊，請決定是否要使用 Apple 大量採購方案 (VPP) 安裝公司入口網站。 如果您使用 VPP 權杖安裝公司入口網站，您的使用者不須輸入 Apple ID 和密碼，即可在註冊期間從應用程式市集下載公司入口網站。 在 [使用 VPP 安裝公司入口網站]  下，選擇 [使用權杖：]  ，以選取具有公司入口網站免費授權的 VPP 權杖。 如果您不想要使用 VPP 部署公司入口網站，請在 [使用 VPP 安裝公司入口網站]  下，選擇 [不要使用 VPP]  。 

8. 如果您選擇使用使用者親和性來註冊、使用公司入口網站進行驗證，以及使用 VPP 安裝公司入口網站，請決定是否要在驗證前均於單一應用程式模式中執行公司入口網站。 此設定可讓您可確保使用者完成公司註冊前，均無法存取其他應用程式。 如果您想要限制使用者在註冊完成前只能進行此流程，請在 [在驗證前均於單一應用程式模式中執行公司入口網站]  下選擇 [是]  。 

9. 選擇 [裝置管理設定]  ，然後在 [受監督]  下選擇 [是]  。 受監督的裝置會提供公司 iOS/iPadOS 裝置適用的大部分管理選項。

10. 在 [鎖定註冊]  下選擇 [是]  ，以確保您的使用者無法移除公司裝置的管理。 

11. 選擇 [與電腦同步]  下的選項，來決定 iOS/iPadOS 裝置是否可與電腦同步。

12. 根據預設，Apple 會以裝置類型 (例如 iPad) 來命名裝置。 如果您想要提供其他名稱範本，請在 [套用裝置名稱範本]  下選擇 [是]  。 輸入要套用至裝置的名稱，其中字串 *{{SERIAL}}* 和 *{{DEVICETYPE}}* 會取代每個裝置的序號與裝置類型。 否則，請在 [套用裝置名稱範本]  下選擇 [否]  。

13. 選擇 [確定]  。

14. 選擇 [設定助理自訂]  ，並針對 [部門名稱]  輸入「教學課程部門」  。 當使用者在裝置啟用期間點選 [About configuration]\(關於設定\)  時，就會看到此字串。

15. 在 [部門電話]  下，輸入電話號碼。 當使用者在啟用期間點選 [需要協助]  按鈕時，就會顯示此號碼。

16. 您可以 [顯示]  或 [隱藏]  裝置啟用期間的各種畫面。 為使您獲得最順暢的註冊體驗，將所有畫面設定為 [隱藏]  。

17. 選擇 [確定]   > [建立]  。

## <a name="sync-managed-devices-to-intune"></a>將受控裝置同步到 Intune

在您使用 ABM、ASM 或 DEP 入口網站設定註冊計劃權杖，並將該處的裝置指派到 MDM 伺服器後，就可以等候這些裝置同步到 Intune 服務，也可以手動同步。若未手動同步，裝置可能需要 24 小時才會顯示在 Azure 入口網站中。

1. 在 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，選擇 [裝置]   >  [iOS]   >  [iOS 註冊]   >  [註冊方案權杖]  > 選擇清單中的權杖 > [裝置]   >  [同步]  。

## <a name="assign-an-enrollment-profile-to-iosipados-devices"></a>將註冊設定檔指派給 iOS/iPadOS 裝置

必須先將註冊計劃設定檔指派至裝置，裝置才能註冊。 這些裝置會從 Apple 同步至 Intune，而且必須指派給 ABM、ASM 或 DEP 入口網站中適當的 MDM 伺服器權杖。

1. 在 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)中，選擇 [裝置]   > [iOS]   > [iOS 註冊]   > [註冊方案權杖]  > 在清單中選擇您的權杖。
2. 選擇 [裝置]  > 選擇清單中的裝置 > [指派設定檔]  。
3. 在 [指派設定檔]  下，選擇裝置的設定檔 > [指派]  。

## <a name="distribute-devices-to-users"></a>將裝置散發給使用者

您已設定 Apple 與 Intune 之間的管理和同步，並指派設定檔以供您的 DEP 裝置註冊。 您現在可以將裝置散發給使用者。 具有使用者親和性的裝置會需要為每個使用者指派 Intune 授權。

## <a name="next-steps"></a>後續步驟

您可以找到可用於註冊 iOS/iPadOS 裝置的其他選項詳細資訊。

> [!div class="nextstepaction"]
> [深入了解 iOS/iPadOS DEP 註冊文章](device-enrollment-program-enroll-ios.md)

<!--commenting out because inaccurate>
## Clean up resources
<!--If you don't want to use iOS/iPadOS corporate enrolled devices anymore, you can delete them.>
<!--- If the devices are enrolled in Intune, you must first [delete them from the Azure Active Directory portal](../remote-actions/devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).>
