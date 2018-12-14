---
title: 將公司識別碼新增至 Intune
titlesuffix: ''
description: 了解如何將公司識別碼 (註冊方法、IMEI 和序號) 新增至 Microsoft Intune。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 566ed16d-8030-42ee-bac9-5f8252a83012
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 38c1d982dc627ccddf2844bf7a6334157e1f0b92
ms.sourcegitcommit: fff179f59bd542677cbd4bf3bacc24bb880e2cb6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2018
ms.locfileid: "53032243"
---
# <a name="identify-devices-as-corporate-owned"></a>識別公司所擁有的裝置

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

身為 Intune 系統管理員，您可以識別公司擁有的裝置，以縮小管理及識別的範圍。 Intune 可執行其他管理工作，以及從公司擁有的裝置收集其他資訊，像是完整電話號碼和應用程式的清查。 您也可以設定裝置限制，以禁止非公司擁有的裝置進行註冊。

在註冊時，Intune 會自動將公司擁有的狀態指派給符合下列條件的裝置：

- 使用[裝置註冊管理員](device-enrollment-manager-enroll.md)帳戶進行註冊 (所有平台)
- 使用 Apple [裝置註冊計劃](device-enrollment-program-enroll-ios.md)、[Apple School Manager](apple-school-manager-set-up-ios.md) 或 [Apple Configurator](apple-configurator-enroll-ios.md) 進行註冊 (僅限 iOS)
- 已使用國際行動設備識別碼 (IMEI) 編號 (所有具有 IMEI 編號的平台) 或序號 (iOS 和 Android) [先識別為屬公司擁有再註冊](#identify-corporate-owned-devices-with-imei-or-serial-number)
- 已加入 Azure Active Directory 作為 Windows 10 企業版裝置
- 在[裝置的屬性清單](#change-device-ownership)中設為公司

在註冊後，[擁有權設定可以變更](#change-device-ownership)為**個人**或**公司**。

## <a name="identify-corporate-owned-devices-with-imei-or-serial-number"></a>使用 IMEI 或序號識別公司擁有的裝置

身為 Intune 管理員，您可以建立和匯入逗點分隔值 (.csv) 檔案，其會列出 IMEI 編號或序號。 在裝置註冊期間，Intune 會使用這些識別碼，將裝置擁有權指定為公司所擁有。 您可以為所有支援的平台宣告 IMEI 編號。 您只能宣告適用於 iOS、macOS 和 Android 裝置的序號。 基於管理目的，每個 IMEI 或序號均可含有清單中指定的詳細資料。

<!-- When you upload serial numbers for company-owned iOS devices, they must be paired with a corporate enrollment profile. Devices must then be enrolled using either Apple’s device enrollment program (DEP) or Apple Configurator to have them appear as company-owned. -->

[了解如何尋找 Apple 裝置序號](https://support.apple.com/HT204308)。<br>
[了解如何尋找您的 Android 裝置序號](https://support.google.com/store/answer/3333000)。

## <a name="add-corporate-identifiers-by-using-a-csv-file"></a>使用 .csv 檔案新增公司識別碼
建立此清單時，請建立內含兩個資料行，但不含標題的逗點分隔值 (.csv) 清單。 在左資料行中新增 IMEI 或序號，然後在右資料行中新增詳細資料。 單一 .csv 檔案只能匯入某一類型的識別碼、IMEI 或序號。 詳細資料限制為 128 個字元，且僅能供系統管理使用。 詳細資料不會顯示在裝置上。 目前限制是每個 .csv 檔案 5,000 列。

**上傳內含序號的 .csv 檔案** - 建立只有兩個資料行而沒有標題的逗點分隔值 (.csv) 清單，並限制清單只可包含 5000 部裝置，或每個.csv 檔案不得超過 5 MB。

|||
|-|-|
|&lt;識別碼 #1&gt;|&lt;裝置 #1 詳細資料&gt;|
|&lt;識別碼 #2&gt;|&lt;裝置 #2 詳細資料&gt;|

在文字編輯器中檢視此 .csv 檔案時，其外觀大致如下：

```
01234567890123,device details
02234567890123,device details
```

> [!IMPORTANT]
> 某些 Android 裝置有多個 IMEI 編號。 Intune 根據每個已註冊的裝置，只會讀取一個 IMEI 編號。 若您匯入的 IMEI 編號並非由 Intune 所清查，裝置將會分類為個人裝置而非公司擁有的裝置。 若某部裝置有多個 IMEI 編號匯入，未清查編號的註冊狀態將會顯示**未知**。<br>
>也請注意︰Android 序號可能重複，或是不存在。 請洽詢裝置供應商，以了解序號是否為可靠的裝置識別碼。
>裝置回報給 Intune 的序號，可能與裝置上 Android [設定/關於] 功能表中顯示的識別碼不符。 請驗證裝置製造商所回報的序號類型。
>嘗試上傳序號含有點 (.) 的檔案會導致上傳失敗。 不支援含有點的序號。

### <a name="upload-a-csv-list-of-corporate-identifiers"></a>上傳公司識別碼的 .csv 清單

1. 在 [Azure 入口網站的 Intune](https://portal.azure.com) 中，選擇 [裝置註冊] > [公司裝置識別碼] > [新增] > [上傳 CSV 檔案]。

   ![反白顯示 [新增] 按鈕的公司裝置識別碼工作區](./media/add-corp-id.png)

2. 在 [新增識別碼] 刀鋒視窗中，指定識別碼類型：[IMEI] 或 [序號]。

3. 按一下資料夾圖示並指定要匯入之清單的路徑。 巡覽至 .csv 檔案，然後選擇 [新增]。 

4. 如果 .csv 檔案包含已在 Intune 中的公司識別碼，但具有不同的詳細資料，[檢閱重複的識別碼] 快顯視窗即會出現。 選取您想要覆寫到 Intune 的識別碼，並選擇 [確定] 來新增識別碼。 對於每個識別碼，只會比較第一個重複的識別碼。

## <a name="manually-enter-corporate-identifiers"></a>手動輸入公司識別碼

1. 在 [Azure 入口網站的 Intune](https://portal.azure.com) 中，選擇 [裝置註冊] > [公司裝置識別碼] > [新增] > [手動輸入]。

2. 在 [新增識別碼] 刀鋒視窗中，指定識別碼類型：[IMEI] 或 [序號]。

3. 請為每個您想要新增的識別碼輸入 [識別碼] 和 [詳細資料]。 完成輸入識別碼時，請選擇 [新增]。

5. 如果您輸入了已在 Intune 中的公司識別碼，但具有不同的詳細資料，[檢閱重複的識別碼] 快顯視窗即會出現。 選取您想要覆寫到 Intune 的識別碼，並選擇 [確定] 來新增識別碼。 對於每個識別碼，只會比較第一個重複的識別碼。

您可以按一下 [重新整理] 來查看新的裝置識別碼。

匯入的裝置不一定經過註冊。 裝置的狀態可能為 [已註冊] 或 [未連線]。 「未連線」表示裝置從未與 Intune 服務通訊。

## <a name="delete-corporate-identifiers"></a>刪除公司識別碼

1. 在 [Azure 入口網站的 Intune](https://portal.azure.com) 中，選擇 [裝置註冊] > [公司裝置識別碼]。
2. 選取您想要刪除的裝置識別碼，然後選擇 [刪除]。
3. 確認刪除。

刪除已註冊裝置的公司識別碼並不會變更裝置的擁有權。 若要變更裝置的擁有權，請移至 [裝置]，並選取裝置，然後選擇 [屬性]，並變更 [裝置擁有權]。

## <a name="imei-specifications"></a>IMEI 規格
如需國際行動設備識別碼的詳細規格，請參閱 [3GGPP TS 23.003 (英文)](https://portal.3gpp.org/desktopmodules/Specifications/SpecificationDetails.aspx?specificationId=729)。

## <a name="change-device-ownership"></a>變更裝置擁有權

裝置內容會顯示 Intune 中每筆裝置記錄的 [擁有權]。 身為系統管理員，您可以將裝置指定為 [個人] 或 [公司]。

**變更裝置擁有權：**
1. 在 [Azure 入口網站的 Intune](https://portal.azure.com) 中，移至 [裝置]，然後選擇裝置。
2. 選擇 [內容]。
3. 將 [裝置擁有權] 指定為 [個人] 或 [公司]。

   ![顯示裝置類別及裝置擁有權選項的裝置內容](./media/device-properties.png)
