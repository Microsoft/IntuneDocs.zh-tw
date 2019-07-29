---
title: 在 Microsoft Intune 中設定 Endpoint Protection 設定 - Azure | Microsoft Docs
description: 您可以在於 Microsoft Intune 中建立 macOS 或 Windows 10 裝置設定檔時，建立 Endpoint Protection 設定。
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
mr.reviewer: karthib
ms.openlocfilehash: d0e3e67cd227c5ce8ac2cb42f79bdea1da8e2d75
ms.sourcegitcommit: c3a4fefbac8ff7badc42b1711b7ed2da81d1ad67
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375118"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>在 Intune 中新增 Endpoint Protection 設定  

透過 Intune，您可以使用裝置組態設定檔，來管理裝置上的一般端點保護安全性功能，包括：  
- 防火牆   
- BitLocker  
- 允許和封鎖應用程式  
- Windows Defender 和加密  

例如，您可以建立一個只允許 macOS 使用者從 Mac App Store 安裝應用程式的 Endpoint Protection 設定檔。 或者，在於 Windows 10 裝置上執行應用程式時，啟用 Windows SmartScreen。  

建立設定檔之前，請檢閱下列文章，這些文章將詳細說明 Intune 可基於每個支援平台來管理的端點保護設定：  
   - [macOS 設定](endpoint-protection-macos.md)  
   - [Windows 10 設定](endpoint-protection-windows-10.md)  

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>建立包含 Endpoint Protection 設定的裝置設定檔  

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。  
3. 選取 [裝置設定]   > [設定檔]   > [建立設定檔]  。  
4. 輸入 Endpoint Protection 設定檔的 [名稱]  和 [描述]  。  
5. 從 [平台]  下拉式清單中，選取要套用自訂設定的裝置平台。 您目前可選擇下列平台之一，進行裝置限制設定︰  
   - **macOS**  
   - **Windows 10 及更新版本**  
6. 從 [設定檔類型]  下拉式清單中，選擇 [Endpoint Protection]  。  
7. 您可設定的設定會視您選擇的平台而不同。 請參閱：  
   - [macOS 設定](endpoint-protection-macos.md)  
   - [Windows 10 設定](endpoint-protection-windows-10.md)  

8. 設定適用的設定之後，選取 [建立設定檔]  頁面上的 [建立]  。  

   設定檔隨即建立，並出現在 [設定檔清單] 頁面上。 若要將此設定檔指派給群組，請參閱[指派裝置設定檔](device-profile-assign.md)。  

## <a name="add-custom-firewall-rules-for-windows-10-devices"></a>新增適用於 Windows 10 裝置的自訂防火牆規則  
自訂防火牆規則已提供公開預覽。  

當您將 Windows Defender 防火牆設定為包含適用於 Windows 10 Endpoint Protection 規則的設定檔一部分時，您可以設定防火牆的自訂規則。 自訂規則可讓您擴充 Windows 10 支援的一組預先定義防火牆規則。  

當您規劃使用自訂防火牆規則的設定檔時，請考量下列資訊，這可能會影響您在設定檔中選擇將防火牆規則分組的方式：  
- 每個設定檔最多支援 150 個防火牆規則。 需使用超過 150 個規則時，請建立額外的設定檔，每個都限制為 150 個規則。  
- 針對每個設定檔，若有任何一個規則無法套用，則該設定檔中的所有規則都會失敗，且不會將任何規則套用至裝置。  
- 當某規則無法套用時，設定檔中的所有規則都會回報為失敗。 Intune 無法識別哪一個個別規則失敗。  

Intune 可以管理的防火牆規則詳述於 Windows [防火牆設定服務提供者]( https://docs.microsoft.com/windows/client-management/mdm/firewall-csp) (CSP)。 若要檢閱 Intune 所支援 Windows 10 裝置的自訂防火牆設定清單，請參閱[自訂防火牆規則](endpoint-protection-windows-10.md#custom-firewall-rules)。  

### <a name="to-add-custom-firewall-rules-to-an-endpoint-protection-profile"></a>將自訂防火牆規則新增至 Endpoint Protection 設定檔  

1. 在 Intune 中，前往 [裝置設定]   > [設定檔]   > [建立設定檔]  。  

2. 針對「平台」  選取 [Windows10 及更新版本]  ，然後針對「設定檔類型」  選取 [Endpoint Protection]  。  

3. 選取 [Windows Defender 防火牆]  以開啟設定頁面，然後針對「防火牆規則」  選取 [新增]  以開啟 [建立規則]  頁面。  

4. 指定防火牆規則的設定，然後選取 [確定]  以儲存。 若要在文件中檢閱可用的自訂防火牆規則選項，請參閱[自訂防火牆規則](endpoint-protection-windows-10.md#custom-firewall-rules)。  

5. 儲存規則之後，該規則會顯示在規則清單中的「Windows Defender 防火牆」  頁面上。  

6. 若要修改規則，請從清單中選取規則以開啟 [編輯規則] 頁面  。  

7. 若要從設定檔刪除規則，請選取規則的省略符號 [...]  ，然後選取 [刪除]  。  

8. 若要變更規則顯示的順序，請選取規則清單頂端的「向上和向下箭號」  圖示。  


## <a name="next-steps"></a>後續步驟  

若要將設定檔指派給群組，請參閱[指派裝置設定檔](device-profile-assign.md)。  
