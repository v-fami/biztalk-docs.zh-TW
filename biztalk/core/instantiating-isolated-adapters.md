---
title: "具現化外掛式配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b8359a3-b098-4bb6-87b4-d3432d2671b1
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e3090252f63221547604a4fdf88388bcbf8296f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="instantiating-isolated-adapters"></a><span data-ttu-id="94e55-102">讓外掛式配接器具現化</span><span class="sxs-lookup"><span data-stu-id="94e55-102">Instantiating Isolated Adapters</span></span>
<span data-ttu-id="94e55-103">之前討論過，外掛式配接器不會由 BizTalk Server 具現化，</span><span class="sxs-lookup"><span data-stu-id="94e55-103">As discussed earlier, isolated adapters are not instantiated by BizTalk Server.</span></span> <span data-ttu-id="94e55-104">而是在另一個處理序中具現化及裝載。</span><span class="sxs-lookup"><span data-stu-id="94e55-104">Rather, they are instantiated and hosted in another process.</span></span> <span data-ttu-id="94e55-105">要建立它的傳輸 proxy 的配接器負責**QueryInterface**，如**IBTTransportProxy**，然後呼叫**IBTTransportProxy**。**RegisterIsolatedReceiver**向 「 傳訊引擎。</span><span class="sxs-lookup"><span data-stu-id="94e55-105">It is the responsibility of the adapter to create its transport proxy, **QueryInterface**, for **IBTTransportProxy**, and then call **IBTTransportProxy**.**RegisterIsolatedReceiver** to register with the Messaging Engine.</span></span>  
  
 <span data-ttu-id="94e55-106">註冊作業會要求配接器傳遞它的其中一個已設定及啟用的接收位置給傳訊引擎。</span><span class="sxs-lookup"><span data-stu-id="94e55-106">Registration requires that the adapter pass one of its configured and enabled receive locations to the Messaging Engine.</span></span> <span data-ttu-id="94e55-107">此配接器的主控件處理序認證必須是 BizTalk 外掛式主控件使用者群組的成員。</span><span class="sxs-lookup"><span data-stu-id="94e55-107">The adapter's host process credentials must be a member of the BizTalk Isolated Host Users group.</span></span> <span data-ttu-id="94e55-108">除非使用者為該群組的成員，否則在這裡單單使用模擬是不夠的。</span><span class="sxs-lookup"><span data-stu-id="94e55-108">Simply using impersonation here is insufficient unless the user is a member of that group.</span></span> <span data-ttu-id="94e55-109">此外，查詢此配接器是以確定它具有正確**ClassID** ，且已設定該主控件執行個體之電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="94e55-109">In addition, the adapter is queried to ensure it has the correct **ClassID** and is running on the computer that was configured for that host instance.</span></span> <span data-ttu-id="94e55-110">配接器已順利註冊其傳輸 proxy 之後，其設定傳送給它所呼叫的 Load 方法使用**IPersistPropertyBag**介面。</span><span class="sxs-lookup"><span data-stu-id="94e55-110">After the adapter has successfully registered with its transport proxy, its configuration is sent to it using by calling the Load method of the **IPersistPropertyBag** interface.</span></span>  
  
 <span data-ttu-id="94e55-111">下圖顯示 API 呼叫的順序。</span><span class="sxs-lookup"><span data-stu-id="94e55-111">The following figure illustrates this sequence of API calls.</span></span> <span data-ttu-id="94e55-112">藍色的介面是此配接器實作的介面。</span><span class="sxs-lookup"><span data-stu-id="94e55-112">The interfaces in blue are implemented by the adapter.</span></span>  
  
 ![](../core/media/isolated-adapter-init.gif "Isolated_adapter_init")  
  
 <span data-ttu-id="94e55-113">下列程式碼片段說明註冊 API 呼叫：</span><span class="sxs-lookup"><span data-stu-id="94e55-113">The following code fragment illustrates the registration API calls:</span></span>  
  
```  
using Microsoft.BizTalk.TransportProxy.Interop;  
using Microsoft.BizTalk.Component.Interop;  
using Microsoft.BizTalk.Message.Interop;  
  
public class MyAdapter : IBTTransport,   
 IBTTransportConfig,   
 IBTTransportControl,   
 IBaseComponent  
{  
...  
private IBTTransportProxy transportProxy;  
  
 public void Register(string uri)  
 {  
 // Create the Transport Proxy...  
 this.transportProxy =   
 (IBTTransportProxy)new BTTransportProxy();  
  
// Register on of the adapters uri’s with the TP  
 this.transportProxy.RegisterIsolatedReceiver(  
 uri,   
 (IBTTransportConfig)this );  
 }  
}  
```  
  
 <span data-ttu-id="94e55-114">**實作秘訣：**建議配接器應進行中的計數。</span><span class="sxs-lookup"><span data-stu-id="94e55-114">**Implementation Tip:** We recommend that the adapter keep a count of the work in progress.</span></span> <span data-ttu-id="94e55-115">此配接器應封鎖**Terminate**訊息計數達到零以前。</span><span class="sxs-lookup"><span data-stu-id="94e55-115">The adapter should block **Terminate** until the message count has reached zero.</span></span> <span data-ttu-id="94e55-116">在接收端，這項工作包含尚未發佈至 BizTalk Server 的任何未完成的要求。</span><span class="sxs-lookup"><span data-stu-id="94e55-116">On the receive side this work includes any outstanding requests that have not been published to BizTalk Server.</span></span> <span data-ttu-id="94e55-117">回應訊息不會傳遞至接收配接器之後**Terminate**已呼叫。</span><span class="sxs-lookup"><span data-stu-id="94e55-117">Response messages are not delivered to a receive adapter after **Terminate** has been called.</span></span>  
  
 <span data-ttu-id="94e55-118">對於傳送配接器而言，應該會以適當方式處理進行中的訊息。</span><span class="sxs-lookup"><span data-stu-id="94e55-118">For send adapters, messages that are in progress should be handled appropriately.</span></span> <span data-ttu-id="94e55-119">這表示，已成功傳遞的任何訊息都應該從配接器的私用應用程式訊息佇列中刪除，以免將訊息傳送一次以上。</span><span class="sxs-lookup"><span data-stu-id="94e55-119">This means any message that was successfully delivered should be deleted from the adapter's private application message queue to prevent messages from being sent more than once.</span></span>  
  
 <span data-ttu-id="94e55-120">之後**Terminate**稱為 「 傳訊引擎不接受發佈新訊息，除了請求-回應組的回應訊息的要求。</span><span class="sxs-lookup"><span data-stu-id="94e55-120">After **Terminate** is called the Messaging Engine does not accept requests to publish new messages, with the exception of response messages for solicit-response pairs.</span></span>