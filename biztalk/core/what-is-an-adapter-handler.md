---
title: "什麼是配接器處理常式？ | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- handlers [adapters]
- adapters, handlers
- handlers [adapters], about handlers
ms.assetid: 4d1afa39-6320-467f-a7e8-f5f18236648e
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c8a1b60661427776dd4e35ffce27bf120bf94a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-an-adapter-handler"></a><span data-ttu-id="51fcb-103">什麼是配接器處理常式？</span><span class="sxs-lookup"><span data-stu-id="51fcb-103">What Is an Adapter Handler?</span></span>
<span data-ttu-id="51fcb-104">配接器處理常式是 BizTalk 主控件的執行個體，配接器程式碼會在其中執行。</span><span class="sxs-lookup"><span data-stu-id="51fcb-104">An adapter handler is an instance of a BizTalk host in which the adapter code runs.</span></span> <span data-ttu-id="51fcb-105">當您指定配接器的傳送或接收處理常式時，就是指定配接器程式碼將在哪個主控件執行個體的內容中執行。</span><span class="sxs-lookup"><span data-stu-id="51fcb-105">When you specify a send or receive handler for an adapter you are specifying which host instance the adapter code will run in the context of.</span></span> <span data-ttu-id="51fcb-106">配接器處理常式負責執行配接器，並且含有配接器的特定執行個體之屬性。</span><span class="sxs-lookup"><span data-stu-id="51fcb-106">An adapter handler is responsible for executing the adapter and contains properties for a specific instance of an adapter.</span></span> <span data-ttu-id="51fcb-107">預設的 BizTalk Server 組態將為所有已安裝的配接器建立配接器處理常式，但您可能想為負載平衡考量而建立其他配接器處理常式，或為特定配接器處理常式提供程序隔離。</span><span class="sxs-lookup"><span data-stu-id="51fcb-107">A default BizTalk Server configuration will create adapter handlers for all of the installed adapters, but you may want to create additional adapter handlers for purposes of load balancing or to provide process isolation for a particular adapter handler.</span></span>  
  
 <span data-ttu-id="51fcb-108">配接器處理常式與 BizTalk 主控件執行個體繫結，而 BizTalk 主控件執行個體與 BizTalk 伺服器繫結。</span><span class="sxs-lookup"><span data-stu-id="51fcb-108">Adapter handlers are bound to a BizTalk Host instance, and BizTalk Host instances are bound to a BizTalk server.</span></span> <span data-ttu-id="51fcb-109">因此，若想要負載平衡所有 BizTalk 伺服器的配接器處理，必須新增其他 BizTalk 伺服器到 BizTalk 群組中。</span><span class="sxs-lookup"><span data-stu-id="51fcb-109">Therefore, you must add additional BizTalk servers to your BizTalk group if you want to load balance adapter processing across BizTalk servers.</span></span> <span data-ttu-id="51fcb-110">若針對程序隔離考量而建立其他配接器處理常式，就不需新增其他 BizTalk 伺服器到 BizTalk 群組中。</span><span class="sxs-lookup"><span data-stu-id="51fcb-110">You do not need to add additional BizTalk servers to your BizTalk group if you are creating additional adapter handlers for the purpose of process isolation.</span></span>  
  
 <span data-ttu-id="51fcb-111">若需要建立執行配接器處理常式的新主控件執行個體，必須先建立主控件，然後建立該主控件的執行個體以在其中一個 BizTalk 伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="51fcb-111">If you need to create a new host instance to run an adapter handler in, you must first create a host and then create an instance of that host to run on one of your BizTalk servers.</span></span> <span data-ttu-id="51fcb-112">如需詳細資訊，請參閱[如何建立新的主控件](../core/how-to-create-a-new-host.md)和[如何新增主控件執行個體](../core/how-to-add-a-host-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="51fcb-112">For more information, see [How to Create a New Host](../core/how-to-create-a-new-host.md) and [How to Add a Host Instance](../core/how-to-add-a-host-instance.md).</span></span>  
  
 <span data-ttu-id="51fcb-113">除了 HTTP 與 SOAP 配接器接收處理常式以外的所有配接器處理常式，都必須設定成在內含式主控件中執行。</span><span class="sxs-lookup"><span data-stu-id="51fcb-113">All adapter handlers except for HTTP and SOAP adapter receive handlers must be configured to run in an in-process host.</span></span> <span data-ttu-id="51fcb-114">HTTP 和 SOAP 配接器接收處理常式只能在外掛式主控件中執行。</span><span class="sxs-lookup"><span data-stu-id="51fcb-114">HTTP and SOAP adapter receive handlers can only be run in an isolated host.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51fcb-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51fcb-115">See Also</span></span>  
 [<span data-ttu-id="51fcb-116">建立和刪除配接器處理常式</span><span class="sxs-lookup"><span data-stu-id="51fcb-116">Creating and Deleting Adapter Handlers</span></span>](../core/creating-and-deleting-adapter-handlers.md)