---
title: 使用動態轉換 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1e4aac7-242a-41b6-8df4-4881371f44d1
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d7f6bc57d009e558188950d9bcb0387f808f835
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295406"
---
# <a name="using-dynamic-transformation"></a><span data-ttu-id="ca592-102">使用動態轉換</span><span class="sxs-lookup"><span data-stu-id="ca592-102">Using Dynamic Transformation</span></span>
## <a name="overview"></a><span data-ttu-id="ca592-103">概觀</span><span class="sxs-lookup"><span data-stu-id="ca592-103">Overview</span></span>  
 <span data-ttu-id="ca592-104">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]支援三種機制，用於動態轉換：</span><span class="sxs-lookup"><span data-stu-id="ca592-104">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] supports three mechanisms for dynamic transformation:</span></span>  
  
-   <span data-ttu-id="ca592-105">做為協調流程實作動態轉換代理程式</span><span class="sxs-lookup"><span data-stu-id="ca592-105">A dynamic transformation agent implemented as an orchestration</span></span>  
  
-   <span data-ttu-id="ca592-106">動態轉換包含在核心 Web 服務的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="ca592-106">A dynamic transformation Web service included with the core Web services</span></span>  
  
-   <span data-ttu-id="ca592-107">ESB 管線元件所執行的轉換</span><span class="sxs-lookup"><span data-stu-id="ca592-107">Transformations executed by ESB pipeline components</span></span>  
  
 <span data-ttu-id="ca592-108">本節著重於實作為協調流程轉換代理程式。</span><span class="sxs-lookup"><span data-stu-id="ca592-108">This section focuses on the transformation agent implemented as an orchestration.</span></span> <span data-ttu-id="ca592-109">如需轉換 Web 服務的資訊，請參閱[使用 BizTalk ESB 工具組 Web 服務](../esb-toolkit/using-the-biztalk-esb-toolkit-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="ca592-109">For information about the transformation Web service, see [Using the BizTalk ESB Toolkit Web Services](../esb-toolkit/using-the-biztalk-esb-toolkit-web-services.md).</span></span> <span data-ttu-id="ca592-110">ESB 發送器管線元件的相關資訊，請參閱[使用管線支援元件](../esb-toolkit/using-the-pipeline-support-components.md)。</span><span class="sxs-lookup"><span data-stu-id="ca592-110">For information about the ESB Dispatcher pipeline components, see [Using the Pipeline Support Components](../esb-toolkit/using-the-pipeline-support-components.md).</span></span>  
  
## <a name="how-it-works"></a><span data-ttu-id="ca592-111">運作方式</span><span class="sxs-lookup"><span data-stu-id="ca592-111">How It Works</span></span>  
 <span data-ttu-id="ca592-112">轉換傳遞代理程式是訂閱訊息的協調流程其中**名稱**屬性的目前**ServiceInstance**路線中的項目是**Microsoft.Practices.ESB.Services.Transform**。</span><span class="sxs-lookup"><span data-stu-id="ca592-112">The transformation delivery agent is an orchestration that subscribes to messages where the **Name** attribute of the current **ServiceInstance** element in the itinerary is **Microsoft.Practices.ESB.Services.Transform**.</span></span> <span data-ttu-id="ca592-113">代理程式會執行下列一系列的作業：</span><span class="sxs-lookup"><span data-stu-id="ca592-113">The agent performs the following sequence of operations:</span></span>  
  
1.  <span data-ttu-id="ca592-114">接收不具型別的的訊息 (System.Xml.XmlDocument)。</span><span class="sxs-lookup"><span data-stu-id="ca592-114">It receives an un-typed message (System.Xml.XmlDocument).</span></span>  
  
2.  <span data-ttu-id="ca592-115">如果對應的名稱可為靜態值路線，代理程式會嘗試使用解析程式管理員在對應的名稱解析。</span><span class="sxs-lookup"><span data-stu-id="ca592-115">If the name of the map is available as a static value in the itinerary, the agent attempts to resolve the name of the map using the resolver manager.</span></span>  
  
3.  <span data-ttu-id="ca592-116">它會套用適當的對應到輸入的來源訊息。</span><span class="sxs-lookup"><span data-stu-id="ca592-116">It applies the appropriate map to the inbound source message.</span></span>  
  
4.  <span data-ttu-id="ca592-117">它會將對應輸出發佈到 BizTalk Messagebox 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="ca592-117">It publishes the map output to the BizTalk Message Box database.</span></span>  
  
## <a name="how-to-configure-dynamic-transformation"></a><span data-ttu-id="ca592-118">如何設定動態轉換</span><span class="sxs-lookup"><span data-stu-id="ca592-118">How to Configure Dynamic Transformation</span></span>  
 <span data-ttu-id="ca592-119">如需如何設定動態轉換使用路線設計工具的詳細資訊，請參閱[旅使用路線設計師建立](../esb-toolkit/creating-itineraries-using-itinerary-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="ca592-119">For more information about how to configure Dynamic Transformation using Itinerary Designer, see [Creating Itineraries Using Itinerary Designer](../esb-toolkit/creating-itineraries-using-itinerary-designer.md).</span></span>  
  
## <a name="dynamic-transformation-errors"></a><span data-ttu-id="ca592-120">動態轉換錯誤</span><span class="sxs-lookup"><span data-stu-id="ca592-120">Dynamic Transformation Errors</span></span>  
 <span data-ttu-id="ca592-121">動態轉換機制將會建立，並在下列情況下發行 ESB 錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="ca592-121">The dynamic transformation mechanism will create and publish an ESB fault message in the following cases:</span></span>  
  
-   <span data-ttu-id="ca592-122">無法判斷解析程式元件，其對應至套用。</span><span class="sxs-lookup"><span data-stu-id="ca592-122">The resolver component cannot determine which map to apply.</span></span>  
  
-   <span data-ttu-id="ca592-123">不提供指定的對應 （例如，您指定不正確的地圖類型或在 BizTalk Server 2009 尚未部署的對應）。</span><span class="sxs-lookup"><span data-stu-id="ca592-123">The specified map is not available (for example, you specified an incorrect map type or a map not yet deployed in BizTalk Server 2009).</span></span>  
  
-   <span data-ttu-id="ca592-124">在對應期間發生失敗 （例如，來源文件不是正確的來源型別或外部組件中的自訂函式不會部署至 BizTalk 對應參考）。</span><span class="sxs-lookup"><span data-stu-id="ca592-124">A failure occurs during mapping (for example, the source document is not of the correct source type or the map references a custom function in an external assembly is not deployed to BizTalk).</span></span>  
  
-   <span data-ttu-id="ca592-125">在 just-in-time (JIT) 解析的地圖類型期間，發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ca592-125">An exception occurs during just-in-time (JIT) resolution of the map type.</span></span>  
  
-   <span data-ttu-id="ca592-126">沒有任何訂閱者有輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="ca592-126">No subscriber exists for the output message.</span></span>  
  
-   <span data-ttu-id="ca592-127">發生任何系統例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ca592-127">Any system exception occurs.</span></span>  
  
 <span data-ttu-id="ca592-128">它是開發人員必須負責提供用來填入例外狀況訊息，並建立回應的例外狀況處理常式的內容資訊。</span><span class="sxs-lookup"><span data-stu-id="ca592-128">It is the developer's responsibility to provide the context information used to populate the exception messages and create handlers to react to the exception.</span></span> <span data-ttu-id="ca592-129">某些資料會自動使用，而且泛型處理常式將會收取例外狀況訊息沒有目標處理常式是否指定或可用。</span><span class="sxs-lookup"><span data-stu-id="ca592-129">Some of the data is automatically available, and a generic handler will pick up the exception message if no target handler is specified or available.</span></span> <span data-ttu-id="ca592-130">如需動態轉換例外狀況處理的詳細資訊，請參閱[使用 ESB 例外狀況管理](../esb-toolkit/using-esb-exception-management.md)。</span><span class="sxs-lookup"><span data-stu-id="ca592-130">For more information about handling dynamic transformation exceptions, see [Using ESB Exception Management](../esb-toolkit/using-esb-exception-management.md).</span></span>