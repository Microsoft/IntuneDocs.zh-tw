---
title: 如果您已拒絕使用條款，請從 Intune 移除您的裝置 | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 4278f000-0258-4de5-93a1-195b48e5061e
searchScope:
- User help
ROBOTS: ''
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: f54f0d9453e93ad54a1d2a96ff25051f3d8bd3a1
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75857668"
---
# <a name="remove-your-device-from-management-if-you-declined-terms-of-use"></a>如果您已拒絕「使用條款」，請從 Intune 移除您的裝置

如果您在嘗試登入公司入口網站應用程式時拒絕使用條款，未來就無法嘗試登入公司入口網站應用程式，因此您必須使用這些「因應措施」指示，從 Intune 移除您的裝置。

當您將公司入口網站應用程式解除安裝時，會一併從 Intune 移除您的裝置。 您的裝置將無法再存取公司資源。 如需有關將裝置自管理中移除時所發生情況的詳細資訊，請參閱[如果將裝置從 Intune 取消註冊，會發生什麼情況？](what-happens-if-you-unenroll-your-device-from-intune-android.md)。

在您可以解除安裝公司入口網站應用程式之前，您必須移至 [裝置系統管理員]  設定，然後關閉 [公司入口網站]  。 步驟可能根據您擁有的 Android 裝置稍有不同。

## <a name="removing-the-device-from-the-company-portal-app"></a>從公司入口網站應用程式移除裝置

從 Intune 移除裝置並將公司入口網站應用程式解除安裝：

1. 前往 [**設定**] &gt; [**安全性 &amp; 螢幕鎖定**] &gt; [**裝置系統管理員**]。

    完成這個步驟後會立即取消註冊您的裝置。

2. 取消核取 [公司入口網站]  旁的方塊，或將其關閉。

    您現在可以解除安裝公司入口網站應用程式。

## <a name="removing-data-collected-by-the-company-portal-app"></a>移除公司入口網站應用程式所收集的資料

移除 Android 版公司入口網站應用程式在您裝置上安裝的所有資料：

- 清除應用程式資料，方法是在 [應用程式] 中 -> 按一下應用程式 -> 按一下 [清除資料] 按鈕
- 刪除 '\storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal' 資料夾


是否仍需要協助？ 請連絡公司支援人員 (可查看[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)以取得連絡資訊)，或是撰寫電子郵件給 <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having unenrolling my Android device&body=Describe the issue you're experiencing here.">Microsoft Android 小組</a>。
