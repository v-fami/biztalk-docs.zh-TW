---
title: 配接器裝載模型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf9a8e6b-8c8d-47ec-b2a3-aed58206121d
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 645a1fcd41650c98c442549a898f7083be770842
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
ms.locfileid: "22225166"
---
# <a name="adapter-hosting-model"></a><span data-ttu-id="00ba7-102">配接器裝載模型</span><span class="sxs-lookup"><span data-stu-id="00ba7-102">Adapter Hosting Model</span></span>
<span data-ttu-id="00ba7-103">BizTalk 配接器通常裝載 BizTalk 服務 Btsntsvc.exe 中。</span><span class="sxs-lookup"><span data-stu-id="00ba7-103">In general BizTalk adapters are hosted in the BizTalk service, Btsntsvc.exe.</span></span> <span data-ttu-id="00ba7-104">這表示[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理配接器的存留期間。</span><span class="sxs-lookup"><span data-stu-id="00ba7-104">This means that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] manages the lifetime of the adapter.</span></span> <span data-ttu-id="00ba7-105">不過也有某些情況 (說明如下) 是由其他處理序負責管理配接器。</span><span class="sxs-lookup"><span data-stu-id="00ba7-105">There are also situations, described below, where other processes manage the adapter.</span></span>  
  
## <a name="in-process-adapters"></a><span data-ttu-id="00ba7-106">內含式配接器</span><span class="sxs-lookup"><span data-stu-id="00ba7-106">In-Process Adapters</span></span>  
 <span data-ttu-id="00ba7-107">配接器所管理的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]稱為內含式配接器。</span><span class="sxs-lookup"><span data-stu-id="00ba7-107">Adapters that are managed by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] are called in-process adapters.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="00ba7-108"> 會執行下列這些配接器：</span><span class="sxs-lookup"><span data-stu-id="00ba7-108"> does the following for these adapters:</span></span>  
  
-   <span data-ttu-id="00ba7-109">在啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時產生配接器</span><span class="sxs-lookup"><span data-stu-id="00ba7-109">Instantiate the adapter when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is started</span></span>  
  
-   <span data-ttu-id="00ba7-110">在初始化期間將配接器的傳輸 Proxy 傳遞給配接器</span><span class="sxs-lookup"><span data-stu-id="00ba7-110">Passes the adapter's transport proxy to the adapter during initialization</span></span>  
  
-   <span data-ttu-id="00ba7-111">為配接器的要求提供服務</span><span class="sxs-lookup"><span data-stu-id="00ba7-111">Services the adapter's requests</span></span>  
  
-   <span data-ttu-id="00ba7-112">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 服務關閉時終止配接器</span><span class="sxs-lookup"><span data-stu-id="00ba7-112">Terminates the adapter on shutdown of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] service</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="00ba7-113"> 會在執行階段將處理常式組態和端點組態資訊傳遞到配接器。</span><span class="sxs-lookup"><span data-stu-id="00ba7-113"> delivers handler configuration and endpoint configuration information to the adapter at run time.</span></span> <span data-ttu-id="00ba7-114">組態的其他部分則是用指定的，例如定義特定時間週期的服務視窗，在這些時間週期內，將會啟用配接器以主動處理要求。</span><span class="sxs-lookup"><span data-stu-id="00ba7-114">Other aspects of configuration are specified, such as service windows that define specific time periods during which the adapter is enabled to actively handle requests.</span></span>  
  
 <span data-ttu-id="00ba7-115">BizTalk 服務可透過 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台或服務控制管理員，以手動方式關閉。</span><span class="sxs-lookup"><span data-stu-id="00ba7-115">The BizTalk service may be manually shut down by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console or by using the service control manager.</span></span> <span data-ttu-id="00ba7-116">如果與 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫的連線中斷，此服務便會自行回收。</span><span class="sxs-lookup"><span data-stu-id="00ba7-116">If connectivity to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases is lost the service automatically recycles itself.</span></span>  
  
 <span data-ttu-id="00ba7-117">在一般裝載模型中，接收端配接器和傳送端配接器都會連同傳訊引擎和協調流程引擎，裝載在與 BizTalk 服務相同的處理序中。</span><span class="sxs-lookup"><span data-stu-id="00ba7-117">In the typical hosting model, receive-side adapters and send-side adapters are hosted in the same process as the BizTalk service, along with the Messaging Engine and the Orchestration Engine.</span></span> <span data-ttu-id="00ba7-118">這種裝載模型十分彈性靈活，可以將接收、傳送和協調流程等主控件分開，也可以合併這些主控件。</span><span class="sxs-lookup"><span data-stu-id="00ba7-118">The hosting model is flexible enough to allow for separation of receive, send, and orchestration hosts and combinations of these.</span></span> <span data-ttu-id="00ba7-119">在下圖中，主控件會在相同的處理序中執行這三項作業。</span><span class="sxs-lookup"><span data-stu-id="00ba7-119">In the following figure, the host is executing all three in the same process.</span></span>  
  
 <span data-ttu-id="00ba7-120">由於裝載模型的豐富多變，因此開發配接器時請務必牢記，傳送配接器和接收配接器可能永遠不會設定在相同的主控件中，</span><span class="sxs-lookup"><span data-stu-id="00ba7-120">Because of the rich hosting model, it is important when developing adapters to remember that the send and receive adapters may never be configured in the same host.</span></span> <span data-ttu-id="00ba7-121">甚至可能設定成在不同的電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="00ba7-121">They may even be configured to run on different computers.</span></span>  
  
 <span data-ttu-id="00ba7-122">![](../core/media/regularadapterhostingmodel.gif "RegularAdapterHostingModel")</span><span class="sxs-lookup"><span data-stu-id="00ba7-122">![](../core/media/regularadapterhostingmodel.gif "RegularAdapterHostingModel")</span></span>  
<span data-ttu-id="00ba7-123">內含式配接器裝載模型</span><span class="sxs-lookup"><span data-stu-id="00ba7-123">The in-process adapter hosting model</span></span>  
  
## <a name="isolated-adapters"></a><span data-ttu-id="00ba7-124">外掛式配接器</span><span class="sxs-lookup"><span data-stu-id="00ba7-124">Isolated Adapters</span></span>  
 <span data-ttu-id="00ba7-125">在某些情況下，在 BizTalk 服務中裝載接收配接器並不可行。</span><span class="sxs-lookup"><span data-stu-id="00ba7-125">There are scenarios when hosting receive adapters in the BizTalk service is not possible.</span></span> <span data-ttu-id="00ba7-126">例如，Internet Information Services (IIS) 程序模型是由 IIS 負責管理 ASP.NET 應用程式和 ISAPI 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="00ba7-126">For example, the Internet Information Services (IIS) process model is such that IIS manages the lifetime of ASP.NET applications and ISAPI extensions.</span></span> <span data-ttu-id="00ba7-127">BizTalk SOAP 配接器必須與 IIS 在相同的程序空間中執行，因而導致 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法控制任何 SOAP 配接器執行個體的存留期間。</span><span class="sxs-lookup"><span data-stu-id="00ba7-127">The BizTalk SOAP adapter must run within the same process space as IIS, thus making it impossible for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to control the lifetime of any instances of the SOAP adapter.</span></span>  
  
 <span data-ttu-id="00ba7-128">這種類型的配接器，有另外一種適用的裝載模型，稱為外接式接收配接器，或簡稱為外接式配接器</span><span class="sxs-lookup"><span data-stu-id="00ba7-128">For these types of adapters there is another hosting model referred to as isolated receive adapters, or simply isolated adapters.</span></span> <span data-ttu-id="00ba7-129">(並沒有外接式傳送配接器的概念)。</span><span class="sxs-lookup"><span data-stu-id="00ba7-129">There is no concept of an isolated send adapter.</span></span>  
  
 <span data-ttu-id="00ba7-130">因為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 不能建立外接式配接器，所以配接器必須取得其本身的傳輸 Proxy，並將自己登錄到該傳輸 Proxy 中。</span><span class="sxs-lookup"><span data-stu-id="00ba7-130">Because [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cannot create an isolated adapter, the adapter must acquire its own transport proxy and register itself with that transport proxy.</span></span>  
  
 <span data-ttu-id="00ba7-131">下圖說明 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 裝載架構。</span><span class="sxs-lookup"><span data-stu-id="00ba7-131">The following figure illustrates the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hosting architecture.</span></span> <span data-ttu-id="00ba7-132">基於效能的考量，外接式主控件架構會嘗試排除任何非必要的處理序間通訊。</span><span class="sxs-lookup"><span data-stu-id="00ba7-132">For the sake of performance, the isolated host architecture tries to eliminate any unnecessary interprocess communication.</span></span> <span data-ttu-id="00ba7-133">因為外接式配接器和 BizTalk 傳訊引擎位於相同的處理序，所以在配接器呼叫傳訊引擎時，並不會有任何處理序間的通訊。</span><span class="sxs-lookup"><span data-stu-id="00ba7-133">Because the isolated adapter and the BizTalk Messaging Engine stack are in the same process, there is no interprocess communication when the adapter is calling the Messaging Engine.</span></span> <span data-ttu-id="00ba7-134">在這種案例中，唯一也是無法避免的處理序間通訊發生在傳訊引擎和資料庫之間。</span><span class="sxs-lookup"><span data-stu-id="00ba7-134">In that scenario the only interprocess communication is between the Messaging Engine and the database, which is unavoidable.</span></span>  
  
 <span data-ttu-id="00ba7-135">![](../core/media/isolatedadapters.gif "IsolatedAdapters")</span><span class="sxs-lookup"><span data-stu-id="00ba7-135">![](../core/media/isolatedadapters.gif "IsolatedAdapters")</span></span>  
<span data-ttu-id="00ba7-136">外接式配接器裝載模型</span><span class="sxs-lookup"><span data-stu-id="00ba7-136">The isolated adapter hosting model</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00ba7-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00ba7-137">See Also</span></span>  
 [<span data-ttu-id="00ba7-138">何謂配接器架構？</span><span class="sxs-lookup"><span data-stu-id="00ba7-138">What Is the Adapter Framework?</span></span>](../core/what-is-the-adapter-framework.md)