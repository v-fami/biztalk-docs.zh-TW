---
title: 使用 BAM WCF 和 WF 攔截器的已知問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2407809-1f71-41a9-b305-722a7f86af5b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42078eb2b1272072016ded9a117e88ddf4fda038
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262022"
---
# <a name="known-issues-with-the-bam-wcf-and-wf-interceptors"></a><span data-ttu-id="428a9-102">BAM WCF 與 WF 攔截器的已知問題</span><span class="sxs-lookup"><span data-stu-id="428a9-102">Known Issues with the BAM WCF and WF Interceptors</span></span>
<span data-ttu-id="428a9-103">本節會提供在使用 Windows Workflow Foundation 或 Windows Communication Foundation 的 BAM 攔截器時，可能發生之已知問題的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="428a9-103">This section provides information about known issues that you may experience when using the BAM interceptors for Windows Workflow Foundation or Windows Communication Foundation.</span></span>  
  
## <a name="intercepting-a-dynamically-generated-wcf-assembly-hosted-in-iis"></a><span data-ttu-id="428a9-104">攔截在 IIS 中裝載的動態產生 WFC</span><span class="sxs-lookup"><span data-stu-id="428a9-104">Intercepting a dynamically generated WCF assembly hosted in IIS</span></span>  
 <span data-ttu-id="428a9-105">當您使用 IIS 來裝載內嵌的 Windows Communication Foundation 應用程式時 (例如，指定組件來源的服務檔案)，系統便會動態產生 WCF 組件，並為其指定任意檔案名稱，並將它放置在 asp.net 暫存資料夾中。</span><span class="sxs-lookup"><span data-stu-id="428a9-105">When you are using IIS to host an embedded Windows Communication Foundation application (for example, a service file that specifies the assembly source), the WCF assembly will be dynamically generated, assigned an arbitrary file name, and placed in the asp.net temporary folder.</span></span> <span data-ttu-id="428a9-106">由於攔截器組態檔需要資訊清單資訊，而且在攔截器組態檔中無法使用萬用字元或其他動態方法來指定資訊清單，所以，您必須重新編譯服務，接著再建置您的攔截組態檔，或是在部署過包含內嵌 WCF 程式碼的所有 .asp.net 網頁後，再重新部署您的攔截器組態檔。</span><span class="sxs-lookup"><span data-stu-id="428a9-106">Since the interceptor configuration file requires manifest information and since wildcard characters or other dynamic methods for specifying the manifest are not available with interceptor configuration files, you must recompile your service and then build your interceptor configuration file or redeploy your interceptor configuration file after you have deployed all of the asp.net web pages containing embedded WCF code.</span></span>  
  
## <a name="use-of-the-bam-interceptor-for-windows-workflow-foundation-is-not-supported-in-office-and-sharepoint-server"></a><span data-ttu-id="428a9-107">在 Office 和 Sharepoint Server 中並不支援使用 Windows Workflow Foundation 的 BAM 攔截器。</span><span class="sxs-lookup"><span data-stu-id="428a9-107">Use of the BAM interceptor for Windows Workflow Foundation is not supported in Office and Sharepoint Server</span></span>  
 <span data-ttu-id="428a9-108">Office 與 Windows Sharepoint Server 兩者，都不會在初始化 WF 執行階段時讀取應用程式組態檔的內容。</span><span class="sxs-lookup"><span data-stu-id="428a9-108">Both office and Windows Sharepoint Server do not read from the application configuration file when initializing the WF runtime.</span></span> <span data-ttu-id="428a9-109">因此，或許您可以針對應用程式設定 WF 適用的 BAM 攔截器，但在裝載於這些環境時，這項設定並不會載入到工作流程執行階段。</span><span class="sxs-lookup"><span data-stu-id="428a9-109">As a result, the BAM interceptor for WF may be configured for an application but it will not be loaded into the workflow runtime when hosted within these environments.</span></span>  
  
## <a name="client-service-locks-when-intiating-a-distributed-transaction"></a><span data-ttu-id="428a9-110">初始化分散式交易時的用戶端服務鎖定</span><span class="sxs-lookup"><span data-stu-id="428a9-110">Client service locks when intiating a distributed transaction</span></span>  
 <span data-ttu-id="428a9-111">如果服務作業不會參與由用戶端啟始的交易，而該用戶端是從交易範圍的內容叫用服務，這時可能會發生鎖死情形。如果在傳送要求之前會從用戶端收集資料，以及接收要求針對相同活動而從服務收集資料時，就更容易發生這種鎖死情形。</span><span class="sxs-lookup"><span data-stu-id="428a9-111">If the service operation will not be participating in the transaction initiated by the client and the client is invoking the service from the context of a transaction scope, a deadlock could result, especially if there is data being collected from the client before the send request and from the service by the receive request for the same activity.</span></span>  
  
 <span data-ttu-id="428a9-112">若要避免這種狀況，您應該依照以下所示，藉由在用戶端之 app.config 檔案的 BAM 行為擴充的用戶端 `ConnectionString` 屬性 (Attribute) 中宣告 "Enlist = false"，指定該用戶端不參與交易。</span><span class="sxs-lookup"><span data-stu-id="428a9-112">To avoid this situation, you should specify that the client does not participate in the transaction by declaring "Enlist = false" in the client `ConnectionString` attribute for the BAM behavior extension in the client's app.config file as demonstrated below.</span></span>  
  
```  
<behavior name="bamClientBehavior">  
  <bamClientBehaviorExtension ConnectionString="Integrated Security=SSPI;Initial Catalog=BAMPrimaryImport;Data Source=.;  Enlist=false"  PollingIntervalSec="1500" />  
</behavior>  
```  
  
## <a name="open-wcf-channel-before-sending-a-message-when-bam-interceptors-are-used"></a><span data-ttu-id="428a9-113">使用 BAM 攔截器時先 開啟 WCF 通道再傳送訊息</span><span class="sxs-lookup"><span data-stu-id="428a9-113">Open WCF Channel Before Sending a Message when BAM Interceptors are used</span></span>  
 <span data-ttu-id="428a9-114">使用 BasicHttp 繫結為 WCF 啟用 BAM 攔截器時，Proxy 應該呼叫 proxy.Open() 以明確開啟通道。</span><span class="sxs-lookup"><span data-stu-id="428a9-114">When BAM interceptor is enabled for WCF with BasicHttp binding, proxy should call proxy.Open() to explicitly open the channel.</span></span> <span data-ttu-id="428a9-115">如果未明確開啟通道，BAM 攔截可能會失敗並傳回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="428a9-115">If the channel is not opened explicitly, BAM interception can fail with an exception.</span></span>