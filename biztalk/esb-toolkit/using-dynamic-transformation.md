---
title: 使用動態轉換 |Microsoft Docs
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
ms.openlocfilehash: ccb83c4dc90a513367d2c914dc546eb0fd931d67
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006133"
---
# <a name="using-dynamic-transformation"></a><span data-ttu-id="f8721-102">使用動態轉換</span><span class="sxs-lookup"><span data-stu-id="f8721-102">Using Dynamic Transformation</span></span>
## <a name="overview"></a><span data-ttu-id="f8721-103">概觀</span><span class="sxs-lookup"><span data-stu-id="f8721-103">Overview</span></span>  
 <span data-ttu-id="f8721-104">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]動態轉換支援三種機制：</span><span class="sxs-lookup"><span data-stu-id="f8721-104">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] supports three mechanisms for dynamic transformation:</span></span>  
  
- <span data-ttu-id="f8721-105">實作為協調流程的動態轉換代理程式</span><span class="sxs-lookup"><span data-stu-id="f8721-105">A dynamic transformation agent implemented as an orchestration</span></span>  
  
- <span data-ttu-id="f8721-106">動態轉換隨附的核心 Web 服務的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="f8721-106">A dynamic transformation Web service included with the core Web services</span></span>  
  
- <span data-ttu-id="f8721-107">ESB 管線元件所執行的轉換</span><span class="sxs-lookup"><span data-stu-id="f8721-107">Transformations executed by ESB pipeline components</span></span>  
  
  <span data-ttu-id="f8721-108">本節著重於實作為協調流程轉換代理程式。</span><span class="sxs-lookup"><span data-stu-id="f8721-108">This section focuses on the transformation agent implemented as an orchestration.</span></span> <span data-ttu-id="f8721-109">如需轉換 Web 服務的資訊，請參閱[使用 BizTalk ESB 工具組 Web 服務](../esb-toolkit/using-the-biztalk-esb-toolkit-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f8721-109">For information about the transformation Web service, see [Using the BizTalk ESB Toolkit Web Services](../esb-toolkit/using-the-biztalk-esb-toolkit-web-services.md).</span></span> <span data-ttu-id="f8721-110">ESB 發送器管線元件的相關資訊，請參閱[使用管線支援元件](../esb-toolkit/using-the-pipeline-support-components.md)。</span><span class="sxs-lookup"><span data-stu-id="f8721-110">For information about the ESB Dispatcher pipeline components, see [Using the Pipeline Support Components](../esb-toolkit/using-the-pipeline-support-components.md).</span></span>  
  
## <a name="how-it-works"></a><span data-ttu-id="f8721-111">運作方式</span><span class="sxs-lookup"><span data-stu-id="f8721-111">How It Works</span></span>  
 <span data-ttu-id="f8721-112">轉換傳遞代理程式是訂閱訊息的協調流程所在**名稱**屬性的目前**ServiceInstance**路線中的項目是**Microsoft.Practices.ESB.Services.Transform**。</span><span class="sxs-lookup"><span data-stu-id="f8721-112">The transformation delivery agent is an orchestration that subscribes to messages where the **Name** attribute of the current **ServiceInstance** element in the itinerary is **Microsoft.Practices.ESB.Services.Transform**.</span></span> <span data-ttu-id="f8721-113">代理程式會執行下列一連串作業：</span><span class="sxs-lookup"><span data-stu-id="f8721-113">The agent performs the following sequence of operations:</span></span>  
  
1.  <span data-ttu-id="f8721-114">接收不具型別的的訊息 (System.Xml.XmlDocument)。</span><span class="sxs-lookup"><span data-stu-id="f8721-114">It receives an un-typed message (System.Xml.XmlDocument).</span></span>  
  
2.  <span data-ttu-id="f8721-115">是否可為路線中的靜態值對應的名稱，代理程式會嘗試解析對應使用解析程式管理員的名稱。</span><span class="sxs-lookup"><span data-stu-id="f8721-115">If the name of the map is available as a static value in the itinerary, the agent attempts to resolve the name of the map using the resolver manager.</span></span>  
  
3.  <span data-ttu-id="f8721-116">它適用於適當的對應輸入的來源訊息。</span><span class="sxs-lookup"><span data-stu-id="f8721-116">It applies the appropriate map to the inbound source message.</span></span>  
  
4.  <span data-ttu-id="f8721-117">它會將對應輸出發佈到 BizTalk Messagebox 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="f8721-117">It publishes the map output to the BizTalk Message Box database.</span></span>  
  
## <a name="how-to-configure-dynamic-transformation"></a><span data-ttu-id="f8721-118">如何設定動態轉換</span><span class="sxs-lookup"><span data-stu-id="f8721-118">How to Configure Dynamic Transformation</span></span>  
 <span data-ttu-id="f8721-119">如需如何設定使用路線設計工具的動態轉換的詳細資訊，請參閱[建立路線使用路線設計工具](../esb-toolkit/creating-itineraries-using-itinerary-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="f8721-119">For more information about how to configure Dynamic Transformation using Itinerary Designer, see [Creating Itineraries Using Itinerary Designer](../esb-toolkit/creating-itineraries-using-itinerary-designer.md).</span></span>  
  
## <a name="dynamic-transformation-errors"></a><span data-ttu-id="f8721-120">動態轉換錯誤</span><span class="sxs-lookup"><span data-stu-id="f8721-120">Dynamic Transformation Errors</span></span>  
 <span data-ttu-id="f8721-121">動態轉換機制會建立，並在下列情況下發行 ESB 錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="f8721-121">The dynamic transformation mechanism will create and publish an ESB fault message in the following cases:</span></span>  
  
- <span data-ttu-id="f8721-122">解析程式元件無法判斷其對應至套用。</span><span class="sxs-lookup"><span data-stu-id="f8721-122">The resolver component cannot determine which map to apply.</span></span>  
  
- <span data-ttu-id="f8721-123">指定的對應不提供 （例如，您指定了不正確的對應型別或尚未部署在 BizTalk Server 2009 對應）。</span><span class="sxs-lookup"><span data-stu-id="f8721-123">The specified map is not available (for example, you specified an incorrect map type or a map not yet deployed in BizTalk Server 2009).</span></span>  
  
- <span data-ttu-id="f8721-124">在對應期間發生失敗 （例如，來源文件不是正確的來源型別或外部組件中的自訂函式未部署到 BizTalk 對應參考）。</span><span class="sxs-lookup"><span data-stu-id="f8721-124">A failure occurs during mapping (for example, the source document is not of the correct source type or the map references a custom function in an external assembly is not deployed to BizTalk).</span></span>  
  
- <span data-ttu-id="f8721-125">在 just-in-time (JIT) 解析的地圖類型期間，發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f8721-125">An exception occurs during just-in-time (JIT) resolution of the map type.</span></span>  
  
- <span data-ttu-id="f8721-126">沒有任何訂閱者存在於輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="f8721-126">No subscriber exists for the output message.</span></span>  
  
- <span data-ttu-id="f8721-127">系統中的任何例外狀況，就會發生。</span><span class="sxs-lookup"><span data-stu-id="f8721-127">Any system exception occurs.</span></span>  
  
  <span data-ttu-id="f8721-128">它是開發人員必須負責提供用來填入的例外狀況訊息，並建立處理常式來回應例外狀況的內容資訊。</span><span class="sxs-lookup"><span data-stu-id="f8721-128">It is the developer's responsibility to provide the context information used to populate the exception messages and create handlers to react to the exception.</span></span> <span data-ttu-id="f8721-129">某些資料會自動提供，以及泛型處理常式將會挑選例外狀況訊息沒有目標處理常式是否指定或可用。</span><span class="sxs-lookup"><span data-stu-id="f8721-129">Some of the data is automatically available, and a generic handler will pick up the exception message if no target handler is specified or available.</span></span> <span data-ttu-id="f8721-130">如需有關處理動態轉換例外狀況的詳細資訊，請參閱[使用 ESB 例外狀況管理](../esb-toolkit/using-esb-exception-management.md)。</span><span class="sxs-lookup"><span data-stu-id="f8721-130">For more information about handling dynamic transformation exceptions, see [Using ESB Exception Management](../esb-toolkit/using-esb-exception-management.md).</span></span>