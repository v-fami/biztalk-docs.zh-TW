---
title: "執行預先定義的路線上手範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4400193-20ac-479a-8bf9-b1c99eb35231
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 167d18f0eba624d62b03b3b0a5386fcac04e5b18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="run-a-predefined-itinerary-on-ramp-sample"></a><span data-ttu-id="bcbde-102">執行預先定義的路線上手範例</span><span class="sxs-lookup"><span data-stu-id="bcbde-102">Run a Predefined Itinerary On-Ramp Sample</span></span>
<span data-ttu-id="bcbde-103">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含 20 預先定義的行程使用案例可以執行。</span><span class="sxs-lookup"><span data-stu-id="bcbde-103">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] includes 20 predefined Itinerary use cases you can execute.</span></span> <span data-ttu-id="bcbde-104">如需這些使用案例，請參閱[路線案例範例](../esb-toolkit/the-sample-itinerary-scenarios.md)。</span><span class="sxs-lookup"><span data-stu-id="bcbde-104">For a list of these use cases, see [The Sample Itinerary Scenarios](../esb-toolkit/the-sample-itinerary-scenarios.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bcbde-105">執行範例之前，您必須以手動方式匯適當路線繫結檔案從 \Source\Samples\Itinerary\Install\Binding 資料夾 GlobalBank.ESB BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="bcbde-105">Before you run any of the samples, you must manually import the appropriate itinerary binding file from the \Source\Samples\Itinerary\Install\Binding folder into the GlobalBank.ESB BizTalk application.</span></span> <span data-ttu-id="bcbde-106">此繫結檔案會重設兩個動態傳送埠上的屬性。</span><span class="sxs-lookup"><span data-stu-id="bcbde-106">This binding file resets the properties on the two dynamic send ports.</span></span> <span data-ttu-id="bcbde-107">匯入名為 GlobalBank.ESB.Itinerary_Bindings.xml 繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="bcbde-107">Import the binding file named GlobalBank.ESB.Itinerary_Bindings.xml.</span></span>  
  
### <a name="to-run-one-of-the-pre-defined-itinerary-on-ramp-samples"></a><span data-ttu-id="bcbde-108">若要執行的其中一個預先定義的行程上手範例</span><span class="sxs-lookup"><span data-stu-id="bcbde-108">To run one of the pre-defined Itinerary On-Ramp samples</span></span>  
  
1.  <span data-ttu-id="bcbde-109">如果尚未執行 GlobalBank.ESB 應用程式，使用 BizTalk 管理主控台來啟動它。</span><span class="sxs-lookup"><span data-stu-id="bcbde-109">If the GlobalBank.ESB application is not already running, use the BizTalk Administration Console to start it.</span></span>  
  
2.  <span data-ttu-id="bcbde-110">在 Windows 檔案總管 中，開啟子資料夾 \Source\Samples\Itinerary\Source\ESB。您已安裝 BizTalk ESB 工具組範例中，並再啟動應用程式的 Itinerary.Test\bin\Debug 名為 Esb.Itinerary.Test.exe。</span><span class="sxs-lookup"><span data-stu-id="bcbde-110">In Windows Explorer, open the subfolder \Source\Samples\Itinerary\Source\ESB.Itinerary.Test\bin\Debug where you installed the BizTalk ESB Toolkit samples, and then start the application named Esb.Itinerary.Test.exe.</span></span>  
  
3.  <span data-ttu-id="bcbde-111">按一下**LoadItinerary**按鈕，然後再選取 範例路線名為 TwoWay-OrchTransform-OrchRoutingGroup-OrchTwoWayCustom.xml \Source\Samples\Itinerary\Itineraries 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="bcbde-111">Click the **LoadItinerary** button, and then select the sample itinerary named TwoWay-OrchTransform-OrchRoutingGroup-OrchTwoWayCustom.xml from the \Source\Samples\Itinerary\Itineraries folder.</span></span>  
  
4.  <span data-ttu-id="bcbde-112">在**Web 服務選項**區段中，選取**雙向服務**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="bcbde-112">In the **Web Service Options** section, select the **Two-Way Service** check box.</span></span> <span data-ttu-id="bcbde-113">這會指示測試用戶端執行的要求-回應路線的服務作業。</span><span class="sxs-lookup"><span data-stu-id="bcbde-113">This instructs the test client to perform a request-response itinerary service operation.</span></span>  
  
5.  <span data-ttu-id="bcbde-114">（選擇性）選取**使用 WCF 服務**核取方塊，如果您想要使用 OnRamp.Itinerary.Response.WCF 應用程式接收位置而不使用預設 OnRamp.Itinerary.Response.SOAP 接收位置。</span><span class="sxs-lookup"><span data-stu-id="bcbde-114">(Optional) Select the **Use WCF Service** check box if you want the application to use the OnRamp.Itinerary.Response.WCF receive location instead of the default OnRamp.Itinerary.Response.SOAP receive location.</span></span>  
  
6.  <span data-ttu-id="bcbde-115">按一下**LoadMessage**按鈕，然後再從 \Source\Samples\Itinerary\Test\Data 資料夾選取 NAOrderDoc.xml 範例訊息。</span><span class="sxs-lookup"><span data-stu-id="bcbde-115">Click the **LoadMessage** button, and then select the NAOrderDoc.xml sample message from the \Source\Samples\Itinerary\Test\Data folder.</span></span>  
  
7.  <span data-ttu-id="bcbde-116">按一下**SubmitRequest**  按鈕，將要求傳送至路線上手服務。</span><span class="sxs-lookup"><span data-stu-id="bcbde-116">Click the **SubmitRequest** button to send the request to the Itinerary On-Ramp service.</span></span> <span data-ttu-id="bcbde-117">圖 1 顯示的結果。</span><span class="sxs-lookup"><span data-stu-id="bcbde-117">Figure 1 shows the result.</span></span>  
  
 <span data-ttu-id="bcbde-118">![在遞增路線](../esb-toolkit/media/ch6-itineraryonramp.gif "第 6 章第 ItineraryOnRamp")</span><span class="sxs-lookup"><span data-stu-id="bcbde-118">![Itinerary On Ramp](../esb-toolkit/media/ch6-itineraryonramp.gif "Ch6-ItineraryOnRamp")</span></span>  
  
 <span data-ttu-id="bcbde-119">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="bcbde-119">**Figure 1**</span></span>  
  
 <span data-ttu-id="bcbde-120">**行程上手用戶端應用程式執行的其中一個行程上手範例**</span><span class="sxs-lookup"><span data-stu-id="bcbde-120">**The Itinerary On-Ramp client application running one of the Itinerary On-Ramp samples**</span></span>  
  
 <span data-ttu-id="bcbde-121">路線的定義中指定的服務名稱對應到直接**ServiceName**服務範例會訂閱的屬性。</span><span class="sxs-lookup"><span data-stu-id="bcbde-121">The name of the service specified in the itinerary definition corresponds directly to the **ServiceName** property of the service to which the sample subscribes.</span></span> <span data-ttu-id="bcbde-122">在上一個程序 (TwoWay-OrchTransform-OrchRoutingGroup-OrchTwoWayCustom.xml) 中執行路線範例中，第一個執行的服務是執行轉換，協調流程服務。</span><span class="sxs-lookup"><span data-stu-id="bcbde-122">In the itinerary sample executed in the previous procedure (TwoWay-OrchTransform-OrchRoutingGroup-OrchTwoWayCustom.xml), the first service executed is an orchestration-based service that performs a transformation.</span></span> <span data-ttu-id="bcbde-123">路線的下列區段會指定此服務。</span><span class="sxs-lookup"><span data-stu-id="bcbde-123">The following section of the itinerary specifies this service.</span></span>  
  
```  
<Service uuid="" beginTime="" completeTime=""   
    name="Microsoft.Practices.ESB.Services.Transform"  
    type="Orchestration" state="Pending" isRequestResponse="false"  
    position="0" serviceInstanceId="" />  
```  
  
 <span data-ttu-id="bcbde-124">在此協調流程服務**\<服務 >**項目會指定直接繫結協調流程具有在圖 2 所顯示的篩選內容。</span><span class="sxs-lookup"><span data-stu-id="bcbde-124">The orchestration service in this **\<Service>** element specifies the direct-bound orchestration that has the filter properties shown in Figure 2.</span></span> <span data-ttu-id="bcbde-125">請注意，協調流程會訂閱只能有值的訊息**Microsoft.Practices.ESB.Services.Transform**如**ServiceName**內容屬性、 值**暫止**如**ServiceState**內容屬性和值的協調流程的**ServiceType**內容屬性。</span><span class="sxs-lookup"><span data-stu-id="bcbde-125">Notice that the orchestration subscribes only to messages that have the value **Microsoft.Practices.ESB.Services.Transform** for the **ServiceName** context property, the value **Pending** for the **ServiceState** context property, and the value Orchestration for the **ServiceType** context property.</span></span>  
  
 <span data-ttu-id="bcbde-126">![篩選運算式](../esb-toolkit/media/ch6-filterexpression.gif "第 6 章第 FilterExpression")</span><span class="sxs-lookup"><span data-stu-id="bcbde-126">![Filter Expression](../esb-toolkit/media/ch6-filterexpression.gif "Ch6-FilterExpression")</span></span>  
  
 <span data-ttu-id="bcbde-127">**圖 2**</span><span class="sxs-lookup"><span data-stu-id="bcbde-127">**Figure 2**</span></span>  
  
 <span data-ttu-id="bcbde-128">**直接繫結協調流程路線上手範例中所使用的篩選條件運算式**</span><span class="sxs-lookup"><span data-stu-id="bcbde-128">**The filter expression for the direct-bound orchestration used in the Itinerary On-Ramp sample**</span></span>