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
# <a name="how-to-create-a-net-application-to-test-a-wcf-service-published-with-the-biztalk-wcf-service-publishing-wizard"></a><span data-ttu-id="41180-102">如何建立 .NET 應用程式以測試使用 BizTalk WCF 服務發佈精靈發佈的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="41180-102">How to Create a .NET Application to Test a WCF Service Published with the BizTalk WCF Service Publishing Wizard</span></span>
<span data-ttu-id="41180-103">若要測試已發佈的 WCF 服務，您可以建立 .NET 應用程式，讓它使用您已發佈的 WCF 服務的。</span><span class="sxs-lookup"><span data-stu-id="41180-103">To test your published WCF service, you can create a .NET application that consumes your published WCF service.</span></span> <span data-ttu-id="41180-104">本主題說明如何建立 .NET 應用程式來測試已發佈的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="41180-104">This topic describes how to create a .NET application to test a published WCF service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41180-105">Visual Studio 說明集合中包含實用的逐步解說，說明如何建立使用 WCF 服務的 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="41180-105">The Visual Studio Help Collection contains a valuable walkthrough for creating a .NET application that consumes WCF services.</span></span> <span data-ttu-id="41180-106">您可以使用這個逐步解說來測試您已發佈的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="41180-106">You can use the walkthrough to test your published WCF service.</span></span> <span data-ttu-id="41180-107">如資訊和程序，需建立 WCF 用戶端專案，請參閱 「 逐步解說:: 存取 XML Web Service 使用 Visual Basic 或 Visual C# 」 中[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]說明的集合，在[ http://go.microsoft.com/fwlink/?LinkId=62263 ](http://go.microsoft.com/fwlink/?LinkId=62263)。</span><span class="sxs-lookup"><span data-stu-id="41180-107">For information and procedures about creating a WCF client project, see "Walkthrough: Accessing an XML Web Service Using Visual Basic or Visual C#" in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Help Collection at [http://go.microsoft.com/fwlink/?LinkId=62263](http://go.microsoft.com/fwlink/?LinkId=62263).</span></span>  
> 
> [!NOTE]
>  <span data-ttu-id="41180-108">本主題使用 Service Model Metadata Utility 工具 (SvcUtil.exe) 建立 WCF Proxy 類別和應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="41180-108">This topic uses the Service Model Metadata Utility tool (SvcUtil.exe) to create the WCF proxy classes and application configuration file.</span></span> <span data-ttu-id="41180-109">SvcUtil.exe 包含在 Windows Vista 和 .NET Framework 執行階段元件的 Microsoft Windows 軟體開發套件 (SDK) 中。</span><span class="sxs-lookup"><span data-stu-id="41180-109">SvcUtil.exe is included in the Microsoft Windows Software Development Kit (SDK) of Windows Vista and .NET Framework Runtime Components.</span></span>  
  
### <a name="to-create-a-simple-wcf-proxy-class-and-application-configuration-file"></a><span data-ttu-id="41180-110">若要建立簡單的 WCF Proxy 類別和應用程式組態檔</span><span class="sxs-lookup"><span data-stu-id="41180-110">To create a simple WCF proxy class and application configuration file</span></span>  
  
1.  <span data-ttu-id="41180-111">以下列方式開啟 CMD Shell： 按一下**開始**，指向**所有程式**，指向**Microsoft Windows SDK**，然後按一下  **CMD Shell**。</span><span class="sxs-lookup"><span data-stu-id="41180-111">Open CMD Shell as follows: click **Start**, point to **All Programs**, point to **Microsoft Windows SDK**, and then click **CMD Shell**.</span></span>  
  
2.  <span data-ttu-id="41180-112">在 [CMD Shell] 中，移到您要放置 Proxy 類別和應用程式組態檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="41180-112">In CMD Shell, go to the directory where you want to place the proxy class and application configuration file.</span></span>  
  
3.  <span data-ttu-id="41180-113">在 [CMD Shell] 中，執行 ServiceModel 中繼資料公用程式工具 (SvcUtil.exe)，使用下列程式碼為已發佈的 WCF 服務建立 Proxy 類別和應用程式組態檔：</span><span class="sxs-lookup"><span data-stu-id="41180-113">In CMD Shell, run the ServiceModel Metadata Utility Tool (SvcUtil.exe) to create the WCF proxy class and application configuration file for the published WCF service as follows:</span></span>  
  
    ```  
    svcutil <http://servername/apppath/wcfservicename.svc> /config:App.config  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="41180-114">這個命令列會產生 BizTalkServiceInstance.cs 和 App.config，前者為 Proxy 類別，後者則為應用程式組態。</span><span class="sxs-lookup"><span data-stu-id="41180-114">This command line generates BizTalkServiceInstance.cs for the proxy class and App.config for the application configuration.</span></span> <span data-ttu-id="41180-115">Svcutil.exe 的詳細資訊，請參閱 「 服務模型中繼資料公用程式工具 （Svcutil.exe) >，網址[ http://go.microsoft.com/fwlink/?LinkId=74696 ](http://go.microsoft.com/fwlink/?LinkId=74696)。</span><span class="sxs-lookup"><span data-stu-id="41180-115">For more information about Svcutil.exe, see "Service Model Metadata Utility Tool (Svcutil.exe)" at [http://go.microsoft.com/fwlink/?LinkId=74696](http://go.microsoft.com/fwlink/?LinkId=74696).</span></span>  
  
### <a name="to-compile-your-net-application-that-consumes-the-published-wcf-service"></a><span data-ttu-id="41180-116">若要編譯使用已發佈之 WCF 服務的 .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="41180-116">To compile your .NET application that consumes the published WCF service</span></span>  
  
1. <span data-ttu-id="41180-117">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的 [方案總管] 中，將 SvcUtil.exe 建立的檔案 (BizTalkServiceInstance 和 App.config) 加入專案中。</span><span class="sxs-lookup"><span data-stu-id="41180-117">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer, add the files that SvcUtil.exe creates, BizTalkServiceInstance and App.config, to your project.</span></span>  
  
2. <span data-ttu-id="41180-118">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的 [方案總管] 中，確定加入 System.ServiceModel.dll 的參考，以編譯 Proxy 程式碼。</span><span class="sxs-lookup"><span data-stu-id="41180-118">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Solution Explorer, make sure to add a reference to the System.ServiceModel.dll to compile the proxy code.</span></span>  
  
3. <span data-ttu-id="41180-119">建立程式碼，以使用產生的 Proxy 程式碼。</span><span class="sxs-lookup"><span data-stu-id="41180-119">Create the code to use the generated proxy code.</span></span> <span data-ttu-id="41180-120">下列程式碼顯示如何使用產生的 Proxy：</span><span class="sxs-lookup"><span data-stu-id="41180-120">The following code shows how to use the generated proxy:</span></span>  
  
   ```  
   DeliveryNotification deliveryNotification= new DeliveryNotification();  
   deliveryNotification.TrackingNumber = "001";  
               Microsoft_Samples_BizTalk_WCFBasicHttp_BizTalkApp_DliveryRequestProcess_DeliveryNotificatonReceivePortClient service = new Microsoft_Samples_BizTalk_WCFBasicHttp_BizTalkApp_DliveryRequestProcess_DeliveryNotificatonReceivePortClient("BasicHttpBinding_ITwoWayAsyncVoid");  
   service.Submit(deliveryNotification);  
   ```  
  
4. <span data-ttu-id="41180-121">執行 .NET 應用程式，將訊息傳送到已發佈的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="41180-121">Run your .NET application to send messages to the published WCF service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41180-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41180-122">See Also</span></span>  
 [<span data-ttu-id="41180-123">利用 WCF 接收配接器發佈 WCF 服務時的考量</span><span class="sxs-lookup"><span data-stu-id="41180-123">Considerations When Publishing WCF Services with the WCF Receive Adapters</span></span>](../core/considerations-when-publishing-wcf-services-with-the-wcf-receive-adapters.md)