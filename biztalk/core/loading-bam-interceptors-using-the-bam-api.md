---
title: 載入使用 BAM API 的 BAM 攔截器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d77ea5fb-a796-48f1-8c77-173e995c5252
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 363c4fc43092e63b664d42bb0420263bd7439dad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22261926"
---
# <a name="loading-bam-interceptors-using-the-bam-api"></a><span data-ttu-id="0a4ee-102">使用 BAM API 載入 BAM 攔截器</span><span class="sxs-lookup"><span data-stu-id="0a4ee-102">Loading BAM Interceptors Using the BAM API</span></span>
<span data-ttu-id="0a4ee-103">本主題會針對從程式碼 (而不是從組態檔案) 載入 WF 和 WCF 攔截器提供相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0a4ee-103">This topic provides information about loading the WF and WCF interceptors from your code rather than through a configuration file.</span></span>  
  
## <a name="loading-the-wf-interceptor-from-code"></a><span data-ttu-id="0a4ee-104">從程式碼載入 WF 攔截器</span><span class="sxs-lookup"><span data-stu-id="0a4ee-104">Loading the WF Interceptor from Code</span></span>  
 <span data-ttu-id="0a4ee-105">若要從程式碼載入 WF 攔截器，您必須建立新的 WorkflowRuntime 執行個體，並使用新的 BamTrackingService 執行個體來呼叫 AddService 方法。</span><span class="sxs-lookup"><span data-stu-id="0a4ee-105">To load the WF interceptor runtime from your code, you must create a new instance of WorkflowRuntime and call the AddService method with a new instance of BamTrackingService.</span></span> <span data-ttu-id="0a4ee-106">這項作業示範如下：</span><span class="sxs-lookup"><span data-stu-id="0a4ee-106">This is demonstrated below.</span></span>  
  
```csharp  
string connectionString = "Integrated Security=SSPI;Data Source=.;Initial Catalog=BAMPrimaryImport";  
int PollingIntervalSec = 300;  
  
WorkflowRuntime workflowRuntime = new WorkflowRuntime();  
workflowRuntime.AddService(new BamTrackingService(connectionString, interceptorConfigurationPollingInterval));  
```  
  
## <a name="loading-the-wcf-interceptor-from-code"></a><span data-ttu-id="0a4ee-107">從程式碼載入 WCF 攔截器</span><span class="sxs-lookup"><span data-stu-id="0a4ee-107">Loading the WCF Interceptor from Code</span></span>  
 <span data-ttu-id="0a4ee-108">若要載入 WCF 攔截器，您必須建立可開啟此服務並供您的實作存取的衍生類別。</span><span class="sxs-lookup"><span data-stu-id="0a4ee-108">To load the WCF interceptor, you must create a derived class that opens the service and is accessible to your implementation.</span></span> <span data-ttu-id="0a4ee-109">這項作業示範如下：</span><span class="sxs-lookup"><span data-stu-id="0a4ee-109">This is demonstrated below.</span></span>  
  
```csharp  
// Your project must have a reference to Microsoft.BizTalk.BAM.Interceptors.dll.  
// Create a derived class accessible to the implementation that opens the service.  
internal class MyBamBehaviorExtension : BamBehaviorExtension  
{  
    internal MyBamBehaviorExtension(string connectionString, int pollingInterval)  
        : base()  
    {  
        this.ConnectionString = connectionString;  
        this.PollingIntervalSec = pollingInterval.ToString();  
    }  
  
    internal IEndpointBehavior Create()  
    {  
        return (IEndpointBehavior) this.CreateBehavior();  
    }  
}  
  
// Add the endpoint behavior just before the service is opened.   
// In this example the connection string and polling intervals are being read from appSettings in App.config.  
MyBamBehaviorExtension bamBehaviorExtension = new MyBamBehaviorExtension(ConfigurationManager.AppSettings["ConnectionString"], int.Parse(ConfigurationManager.AppSettings["PollingIntervalSec"]));  
IEndpointBehavior bamBehavior = bamBehaviorExtension.Create();  
foreach (System.ServiceModel.Description.ServiceEndpoint endpoint in myServiceHost.Description.Endpoints)  
{  
    if (endpoint.Behaviors.Find<MyBamBehaviorExtension>() == null)  
        endpoint.Behaviors.Add(bamBehavior);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a4ee-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a4ee-110">See Also</span></span>  
 [<span data-ttu-id="0a4ee-111">使用 BAM WCF 和 WF 攔截器</span><span class="sxs-lookup"><span data-stu-id="0a4ee-111">Using the BAM WCF and WF Interceptors</span></span>](../core/using-the-bam-wcf-and-wf-interceptors.md)