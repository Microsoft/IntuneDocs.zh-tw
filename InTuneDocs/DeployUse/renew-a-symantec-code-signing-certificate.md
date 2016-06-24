---
# required metadata

title: 更新 Symantec 企業程式碼簽署憑證以搭配 Microsoft Intune 一起使用 | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: c4813044-a925-4273-b0ec-e992fd55850a

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 針對 Windows 裝置更新 Symantec 企業程式碼簽署憑證

用來管理特定 Windows 和 Windows Phone 行動裝置的 Symantec 憑證必須定期更新。 Windows Phone 8.0 裝置必須具備已簽署的公司入口網站應用程式及程式碼簽署憑證，才能註冊裝置。 更新的 Windows Phone 裝置可以使用從商店下載的公司入口網站應用程式。 在部署企業營運系統應用程式時，也需要提供程式碼簽署憑證。

## 如何更新 Symantec 企業程式碼簽署憑證

1.  在憑證到期約 14 天前，請尋找 Symantec 寄來的更新電子郵件。 這封電子郵件會包含來自 Symantec 有關更新您企業憑證的指引。

    如需 Symantec 憑證的詳細資訊，請瀏覽 [www.symantec.com](http://www.symantec.com)，或致電 1-877-438-8776 或 1-650-426-3400。

2.  移至網站 (例如， [https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do))，並使用 Symantec 發行者識別碼和與憑證相關的電子郵件位址登入。 請務必使用您用以下載憑證的電腦來啟動更新。

3.  一旦更新核准，且已支付，即可下載憑證。

## 如何安裝 Windows Phone 8.0 的更新憑證

1.  下載並簽署此處最新的 Windows Phone 公司入口網站：[http://www.microsoft.com/en-us/download/details.aspx?id=36060](http://www.microsoft.com/en-us/download/details.aspx?id=36060)

2.  開啟 Intune 管理主控台 ([https://admin.manage.microsoft.com](https://admin.manage.microsoft.com))，移至 [系統管理]、[行動裝置管理] &gt; [Windows Phone]，然後按一下 [上傳已簽署的應用程式]

3.  上傳新簽署的公司入口網站。 您會需要新簽署的 SSP.xap，以及您從 Symantec 收到的 .PFX 檔案，或由此 .PFX 檔案所建立的應用程式註冊權杖。

4.  當上傳完成時，請移除 Intune 管理主控台之 **[軟體]** 工作區中舊的公司入口網站版本。

5.  再次簽署所有的企業營運系統應用程式，使用相同的憑證上傳並取代現有的應用程式。

提供經過簽署的 SSP.xap 檔案，是目前唯一能夠更新之程式碼簽署憑證的方法。 若要支援已簽署的企業營運系統應用程式，您必須簽署並上傳公司入口網站應用程式，即使您的使用者將從市集安裝公司入口網站應用程式也一樣。

## 如何安裝適用於 Windows Phone 8.1 及更新版裝置的更新的證

1.  從此處的下載中心下載並簽署最新的 Windows Phone 公司入口網站：[http://www.microsoft.com/en-us/download/details.aspx?id=36060](http://www.microsoft.com/en-us/download/details.aspx?id=36060)

2.  開啟 [Intune 管理主控台](https://admin.manage.microsoft.com) (https://admin.manage.microsoft.com)，移至 [系統管理] &gt; [行動裝置管理] &gt; [Windows Phone]，然後按一下 [上傳已簽署的應用程式]

3.  上傳新簽署的公司入口網站。 您會需要新簽署的 SSP.xap，以及您從 Symantec 收到的 .PFX 檔案，或由此 .PFX 檔案所建立的應用程式註冊權杖。

4.  上傳完成時，移除舊的公司入口網站版本，在 **軟體**  工作區。

5.  使用新的憑證簽署所有新增及更新的企業營運應用程式。 現有的應用程式無須重新簽署，也無須重新部署。


### 請參閱
設定 Windows Phone 8.0 管理


<!--HONumber=May16_HO2-->


