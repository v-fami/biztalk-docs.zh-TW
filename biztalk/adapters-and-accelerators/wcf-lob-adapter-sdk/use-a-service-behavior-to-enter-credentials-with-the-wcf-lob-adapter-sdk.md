---
title: "使用服務行為來輸入認證，與 WCF LOB 配接器 SDK |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b203cfa-6331-4498-b656-8cd8339f8613
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3cc494e55aee70a9a441eccbe056f4651448752d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="use-a-service-behavior-to-enter-credentials-with-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="aa4cb-102">使用服務行為來輸入認證，與 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="aa4cb-102">Use a service behavior to enter credentials with the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="aa4cb-103">許多次，配接器取用者必須將認證傳遞給商務系統的目標一行。</span><span class="sxs-lookup"><span data-stu-id="aa4cb-103">Many times, adapter consumers will be required to pass credentials to the target line of business system.</span></span> <span data-ttu-id="aa4cb-104">若要提供這項功能，您必須提供 WCF 服務行為。</span><span class="sxs-lookup"><span data-stu-id="aa4cb-104">To provide this functionality, you will need to provide a WCF service behavior.</span></span>  
  
 <span data-ttu-id="aa4cb-105">下列程式碼範例示範如何衍生服務行為。</span><span class="sxs-lookup"><span data-stu-id="aa4cb-105">The following example code demonstrates how to derive a service behavior.</span></span> <span data-ttu-id="aa4cb-106">它會委派至配接器從配接器的取用者取得的認證。</span><span class="sxs-lookup"><span data-stu-id="aa4cb-106">It delegates the credentials obtained from the consumer of the adapter to the adapter.</span></span> <span data-ttu-id="aa4cb-107">然後配接器必須使用特定業務通訊協定來驗證的認證。</span><span class="sxs-lookup"><span data-stu-id="aa4cb-107">The adapter then must use line-of-business protocols to authenticate the credentials.</span></span> <span data-ttu-id="aa4cb-108">一旦驗證認證，服務就可以開始接聽連入事件，從企業營運應用程式。</span><span class="sxs-lookup"><span data-stu-id="aa4cb-108">Once the credentials are authenticated, the service can start listening for incoming events from the line of business application.</span></span>  
  
```  
/// <summary>  
/// This class derives from a WCF service behavior.  It is used in the inbound scenario  
/// for the Inbound Service to pass the line-of-business credentials to the adapter using  
/// WCF ClientCredentials class.  
/// </summary>  
public class InboundClientCredentialsServiceBehavior : ClientCredentials, IServiceBehavior  
{  
    public InboundClientCredentialsServiceBehavior() { }  
  
    public InboundClientCredentialsServiceBehavior(InboundClientCredentialsServiceBehavior other)  
         : base(other)  
    {  
    }  
  
    #region IServiceBehavior Members  
  
    public void AddBindingParameters(ServiceDescription serviceDescription, System.ServiceModel.ServiceHostBase serviceHostBase, System.Collections.ObjectModel.Collection<ServiceEndpoint> endpoints, System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
    {  
        bindingParameters.Add(this);  
    }  
  
    public void ApplyDispatchBehavior(ServiceDescription serviceDescription, System.ServiceModel.ServiceHostBase serviceHostBase)  
    {  
    }  
  
    public void Validate(ServiceDescription serviceDescription, System.ServiceModel.ServiceHostBase serviceHostBase)  
    {  
    }  
  
    #endregion  
  
    protected override ClientCredentials CloneCore()  
    {  
        return new InboundClientCredentialsServiceBehavior(this);  
    }  
}  
```  
  
 <span data-ttu-id="aa4cb-109">下列程式碼範例示範如何將認證傳遞給配接器使用的服務行為。</span><span class="sxs-lookup"><span data-stu-id="aa4cb-109">The following example code shows how to use the service behavior to pass credentials to the adapter.</span></span>  
  
```  
// Create a ServiceHost for the EchoServiceImpl type  
// and use the base address from app.config  
ServiceHost host = new ServiceHost(typeof(EchoServiceImpl));  
  
// Set service behavior to pass the line-of-business credentials.  
InboundClientCredentialsServiceBehavior credentialsBehavior = new InboundClientCredentialsServiceBehavior();  
credentialsBehavior.UserName.UserName = "username";  
credentialsBehavior.UserName.Password = "****";  
host.Description.Behaviors.Add(credentialsBehavior);  
  
// Open the ServiceHost to start listening for messages  
host.Open();  
  
Console.WriteLine("The service is ready.");  
Console.WriteLine("Press <ENTER> to terminate service.");  
Console.ReadLine();  
  
// Close the ServiceHost  
host.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="aa4cb-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa4cb-110">See Also</span></span>  
 [<span data-ttu-id="aa4cb-111">使用 WCF LOB 配接器 SDK 開發最佳作法</span><span class="sxs-lookup"><span data-stu-id="aa4cb-111">Development best practices using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/development-best-practices-using-the-wcf-lob-adapter-sdk.md)