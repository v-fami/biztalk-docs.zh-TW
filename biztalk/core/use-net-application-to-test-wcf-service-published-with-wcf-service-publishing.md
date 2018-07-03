---
title: 如何建立.NET 應用程式來測試 WCF 服務使用 BizTalk WCF 服務發佈精靈發佈 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF services, .NET applications
- WCF services, WCF Service Publishing Wizard
- creating, .NET applications [WCF services]
- WCF Service Publishing Wizard
ms.assetid: 17e39db2-8471-4f6f-a7f1-833023cdbc39
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d81b18e4fe2180ed3d4e58bfb7bec5e31c1d6a84
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996639"
---
# <a name="how-to-create-a-net-application-to-test-a-wcf-service-published-with-the-biztalk-wcf-service-publishing-wizard"></a>如何建立 .NET 應用程式以測試使用 BizTalk WCF 服務發佈精靈發佈的 WCF 服務
若要測試已發佈的 WCF 服務，您可以建立 .NET 應用程式，讓它使用您已發佈的 WCF 服務的。 本主題說明如何建立 .NET 應用程式來測試已發佈的 WCF 服務。  
  
> [!NOTE]
>  Visual Studio 說明集合中包含實用的逐步解說，說明如何建立使用 WCF 服務的 .NET 應用程式。 您可以使用這個逐步解說來測試您已發佈的 WCF 服務。 如資訊和程序，需建立 WCF 用戶端專案，請參閱 「 逐步解說:: 存取 XML Web Service 使用 Visual Basic 或 Visual C# 」 中[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]說明的集合，在[ http://go.microsoft.com/fwlink/?LinkId=62263 ](http://go.microsoft.com/fwlink/?LinkId=62263)。  
> 
> [!NOTE]
>  本主題使用 Service Model Metadata Utility 工具 (SvcUtil.exe) 建立 WCF Proxy 類別和應用程式組態檔。 SvcUtil.exe 包含在 Windows Vista 和 .NET Framework 執行階段元件的 Microsoft Windows 軟體開發套件 (SDK) 中。  
  
### <a name="to-create-a-simple-wcf-proxy-class-and-application-configuration-file"></a>若要建立簡單的 WCF Proxy 類別和應用程式組態檔  
  
1.  以下列方式開啟 CMD Shell： 按一下**開始**，指向**所有程式**，指向**Microsoft Windows SDK**，然後按一下  **CMD Shell**。  
  
2.  在 [CMD Shell] 中，移到您要放置 Proxy 類別和應用程式組態檔的目錄。  
  
3.  在 [CMD Shell] 中，執行 ServiceModel 中繼資料公用程式工具 (SvcUtil.exe)，使用下列程式碼為已發佈的 WCF 服務建立 Proxy 類別和應用程式組態檔：  
  
    ```  
    svcutil <http://servername/apppath/wcfservicename.svc> /config:App.config  
    ```  
  
    > [!NOTE]
    >  這個命令列會產生 BizTalkServiceInstance.cs 和 App.config，前者為 Proxy 類別，後者則為應用程式組態。 Svcutil.exe 的詳細資訊，請參閱 「 服務模型中繼資料公用程式工具 （Svcutil.exe) >，網址[ http://go.microsoft.com/fwlink/?LinkId=74696 ](http://go.microsoft.com/fwlink/?LinkId=74696)。  
  
### <a name="to-compile-your-net-application-that-consumes-the-published-wcf-service"></a>若要編譯使用已發佈之 WCF 服務的 .NET 應用程式  
  
1. 在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的 [方案總管] 中，將 SvcUtil.exe 建立的檔案 (BizTalkServiceInstance 和 App.config) 加入專案中。  
  
2. 在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的 [方案總管] 中，確定加入 System.ServiceModel.dll 的參考，以編譯 Proxy 程式碼。  
  
3. 建立程式碼，以使用產生的 Proxy 程式碼。 下列程式碼顯示如何使用產生的 Proxy：  
  
   ```  
   DeliveryNotification deliveryNotification= new DeliveryNotification();  
   deliveryNotification.TrackingNumber = "001";  
               Microsoft_Samples_BizTalk_WCFBasicHttp_BizTalkApp_DliveryRequestProcess_DeliveryNotificatonReceivePortClient service = new Microsoft_Samples_BizTalk_WCFBasicHttp_BizTalkApp_DliveryRequestProcess_DeliveryNotificatonReceivePortClient("BasicHttpBinding_ITwoWayAsyncVoid");  
   service.Submit(deliveryNotification);  
   ```  
  
4. 執行 .NET 應用程式，將訊息傳送到已發佈的 WCF 服務。  
  
## <a name="see-also"></a>另請參閱  
 [利用 WCF 接收配接器發佈 WCF 服務時的考量](../core/considerations-when-publishing-wcf-services-with-the-wcf-receive-adapters.md)