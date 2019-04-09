---
title: 教學課程 - 使用裝置註冊計劃在 Intune 中註冊 iOS 裝置
titleSuffix: Microsoft Intune
description: 您將在此教學課程中設定 Apple 的 DEP，以在 Intune 中註冊 iOS 裝置。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/29/2019
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up the Device Enrollment Program so that users can automatically enroll in Intune.
ms.collection: M365-identity-device-management
ms.openlocfilehash: f9cd0eec492f5131e4015aa64eccb4c081c663ee
ms.sourcegitcommit: 8e6f4acb592dbe5de63aa7642ee9487288740714
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2019
ms.locfileid: "58646466"
---
# <a name="tutorial-use-the-device-enrollment-program-to-enroll-ios-devices-in-intune"></a>教學課程：使用裝置註冊計劃在 Intune 中註冊 iOS 裝置
Apple 的裝置註冊計劃 (DEP) 可簡化裝置註冊。 使用 Microsoft Intune 和 DEP，當使用者第一次啟動裝置時，就會自動註冊裝置。 因此，您可以將裝置提供給許多使用者，而不必個別設定每部裝置。 

在此教學課程中，您將了解如何：
> [!div class="checklist"]
> * 取得 Apple DEP 權杖
> * 建立 Autopilot 裝置群組
> * 建立 AutoPilot 部署設定檔
> * 指派 AutoPilot 部署設定檔至裝置群組
> * 將 Windows 裝置散發給使用者

如果您沒有 Intune 訂用帳戶，請[註冊免費試用帳戶](free-trial-sign-up.md)。

## <a name="prerequisites"></a>必要條件
- [Apple 的裝置註冊計劃](http://deploy.apple.com)中所購買的裝置
- 設定[行動裝置管理授權單位](mdm-authority-set.md)
- 取得 [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>取得 Apple DEP 權杖
您需要 Apple DEP 權杖 (.pem) 檔案，才能向 DEP 註冊 iOS 裝置。 此權杖可讓 Intune 同步貴公司所擁有的 DEP 裝置資訊。 它也允許 Intune 將註冊設定檔上傳至 Apple，並將這些設定檔指派給裝置。

您可以使用 Apple DEP 入口網站建立 DEP 權杖。 您也可以使用 DEP 入口網站將裝置指派給 Intune 以便管理。

1. 在 [Azure 入口網站的 Intune](https://aka.ms/intuneportal) 中，選擇 [裝置註冊] > [Apple 註冊] > [註冊方案權杖] > [新增]。

2. 藉由選取 [我同意] 來將權限授與 Microsoft，以將使用者和裝置資訊傳送給 Apple。

   ![[Apple 憑證] 工作區中 [註冊計劃權杖] 窗格下載公開金鑰的螢幕擷取畫面。](./media/device-enrollment-program-enroll-ios-newui/add-enrollment-program-token-pane.png)

3. 選擇 [下載您的公開金鑰]，在本機下載並儲存加密金鑰 (.pem) 檔案。 這個 .pem 檔案會用於向 Apple 裝置註冊程式入口網站要求信任關係憑證。

4. 選擇 [建立 Apple 裝置註冊計劃的權杖] 以開啟 Apple 的部署計劃入口網站，並使用您的公司 Apple ID 登入。 您可以使用此 Apple ID 來更新 DEP 權杖。

5.  在 Apple 的[部署計劃入口網站](https://deploy.apple.com)，針對 [裝置註冊計劃] 選擇 [開始使用]。

4. 在 [管理伺服器] 頁面上，選擇 [新增 MDM 伺服器]。

5. 針對 [MDM 伺服器名稱] 輸入 *TestMDMServer*，然後選擇 [下一步]。 您可參考這個伺服器名稱，以識別行動裝置管理 (MDM) 伺服器， 但它不是 Microsoft Intune 伺服器的名稱或 URL。

6. [新增 &lt;服器名稱&gt;] 對話方塊隨即開啟，指出**上傳您的公用金鑰**。 選取 [選擇檔案] 以上傳 .pem 檔案，然後選擇 [下一步]。

6. 移至 [Deployment Programs] \(部署方案\) > [裝置註冊計劃] > [管理裝置]。
7. 在 [Choose Devices By] \(選擇裝置依據\) 下，選擇 [序號]。 <!--ask Tiffany about this-->

8. 針對 [選擇動作] 選擇 [Assign to Server] (指派給伺服器))，然後選擇指定給 Microsoft Intune 的 &lt;伺服器名稱&gt;，再選擇 [確定]。 Apple 入口網站會將指定的裝置指派給 Intune 伺服器以便管理 ，然後顯示 [指派完成]。

   在 Apple 入口網站中，移至 [部署計劃] &gt; [裝置註冊計劃] &gt; [檢視指派歷程記錄] 查看裝置及其 MDM 伺服器指派的清單。

9. 在 Azure 入口網站的 Intune 中，提供用來建立此權杖的 Apple ID 供日後參考。

    ![指定要用於建立註冊計劃權杖的 Apple 識別碼，並瀏覽至註冊計劃權杖的螢幕擷取畫面。](./media/device-enrollment-program-enroll-ios/image03.png)

10. 在 [Apple 權杖] 方塊中，瀏覽至憑證 (.pem) 檔案，選擇 [開啟]，然後選擇 [建立]。 

## <a name="create-an-apple-enrollment-profile"></a>建立 Apple 註冊設定檔
安裝權杖之後，您可以為 DEP 裝置建立註冊設定檔。 裝置註冊設定檔會定義要在註冊期間套用至裝置群組的設定。

1. 在 Azure 入口網站的 Intune 中，選擇 [裝置註冊] > [Apple 註冊] > [註冊計劃權杖]。

2. 選取您剛安裝的權杖，然後選擇 [設定檔] > [建立設定檔]。

3. 在 [建立設定檔] 下，針對 [名稱] 輸入 *TestDEPProfile*，並針對 [描述] 輸入「測試 iOS 裝置的 DEP」。 使用者看不到這些詳細資料。

4. 針對 [使用者親和性]，選擇 [搭配使用者親和性進行註冊]。 此選項適用於想要使用公司入口網站進行像是安裝應用程式等服務的使用者所屬裝置。

5. 在 [不向 Apple 設定輔助程式驗證，而向公司入口網站驗證] 下，選擇 [否]。

6. 選擇 [裝置管理設定]，然後在 [受監督] 下選擇 [否]。 受監督裝置可提供您更多管理選項，但您不會在此教學課程中用到。

7. 選擇 [確定]。

8. 選擇 [設定助理自訂]，並針對 [部門名稱] 輸入「教學課程部門」。 當使用者在裝置啟用期間點選 [About configuration]\(關於設定\) 時，就會看到此字串。

9. 在 [部門電話] 下，輸入電話號碼。 當使用者在啟用期間點選 [需要協助] 按鈕時，就會顯示此號碼。

10. 您可以 [顯示] 或 [隱藏] 裝置啟用期間的各種畫面。 基於此教學課程的目的，將 [密碼] 設定為 [顯示]，並將所有其他選項設定為 [隱藏]。

11. 選擇 [確定] > [建立]。

## <a name="sync-managed-devices"></a>同步受管理裝置

您現在可以看到哪些裝置指派給此權杖。

1. 在 Azure 入口網站的 Intune 中，選擇 [裝置註冊] > [Apple 註冊] > [註冊計劃權杖] > 在清單中選擇一個權杖 > [裝置] > [同步]。

## <a name="assign-an-enrollment-profile-to-ios-devices"></a>將註冊設定檔指派給 iOS 裝置

必須先將註冊計劃設定檔指派至裝置，裝置才能註冊。

1. 在 Azure 入口網站的 Intune 中，選擇 [裝置註冊] > [Apple 註冊] > [註冊計劃權杖] > 在清單中選擇您的權杖。
2. 選擇 [裝置] > 選擇清單中的裝置 > [指派設定檔]。
3. 在 [指派設定檔] 下，選擇裝置的設定檔 > [指派]。

## <a name="distribute-devices-to-users"></a>將裝置散發給使用者

您已設定 Apple 與 Intune 之間的管理和同步，並指派設定檔以供您的 DEP 裝置註冊。 您現在可以將裝置散發給使用者。 具有使用者親和性的裝置會需要為每個使用者指派 Intune 授權。

## <a name="clean-up-resources"></a>清除資源

如果不想再使用 Autopilot 裝置，可以將它們刪除。

- 如果裝置已在 Intune 中註冊，則必須先[從 Azure Active Directory 入口網站中加以刪除](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal)。

<!--ask tiffany how to do this-->

## <a name="next-steps"></a>後續步驟

您可以找到可用於註冊 iOS 裝置的其他選項詳細資訊。

> [!div class="nextstepaction"]
> [深入了解 iOS DEP 註冊文章](device-enrollment-program-enroll-ios.md)
