---
title: "執行設計工具擴充性範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05ac3b50-5bf2-4566-8654-472391476d1f
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b26c483568e1ceb05679d7548721c1cce818fde
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-designer-extensibility-sample"></a><span data-ttu-id="a64f4-102">執行設計工具擴充性範例</span><span class="sxs-lookup"><span data-stu-id="a64f4-102">Running the Designer Extensibility Sample</span></span>
<span data-ttu-id="a64f4-103">設計工具擴充性範例會示範如何提供設計階段組態選項，對於自訂解析程式與路線服務使用兩個範例擴充項。</span><span class="sxs-lookup"><span data-stu-id="a64f4-103">The Designer Extensibility sample uses two sample extenders to demonstrate how you can provide design-time configuration options for custom resolvers and for itinerary services.</span></span>  
  
 <span data-ttu-id="a64f4-104">**若要執行設計工具擴充性範例**</span><span class="sxs-lookup"><span data-stu-id="a64f4-104">**To run the Designer Extensibility sample**</span></span>  
  
1.  <span data-ttu-id="a64f4-105">啟動 [!INCLUDE[vs2010](../includes/vs2010-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a64f4-105">Start [!INCLUDE[vs2010](../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="a64f4-106">在 Visual Studio 中，指向**新增**上**檔案**功能表，然後再按一下**專案**。</span><span class="sxs-lookup"><span data-stu-id="a64f4-106">In Visual Studio, point to **New** on the **File** menu, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="a64f4-107">選取 [C# 類別庫] 範本類型**ItineraryLibrary**中**名稱**方塊，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="a64f4-107">Select the C# Class Library template, type **ItineraryLibrary** in the **Name** box, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="a64f4-108">在 方案總管 中，以滑鼠右鍵按一下 ItineraryLibrary 專案，指向**新增**，然後按一下 **新的行程**。</span><span class="sxs-lookup"><span data-stu-id="a64f4-108">In Solution Explorer, right-click the ItineraryLibrary project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
5.  <span data-ttu-id="a64f4-109">在**名稱**方塊中，輸入**TestItinerary**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="a64f4-109">In the **Name** box, type **TestItinerary**, and then press ENTER.</span></span>  
  
6.  <span data-ttu-id="a64f4-110">在工具箱中，按一下 On 遞增模型元素，然後將它拖曳至設計介面。</span><span class="sxs-lookup"><span data-stu-id="a64f4-110">In the Toolbox, click an On-Ramp model element, and then drag it to the design surface.</span></span>  
  
7.  <span data-ttu-id="a64f4-111">在工具箱中，按一下路線服務的模型項目上，，然後將它拖曳至設計介面。</span><span class="sxs-lookup"><span data-stu-id="a64f4-111">In the Toolbox, click an Itinerary Service model element, and then drag it to the design surface.</span></span>  
  
8.  <span data-ttu-id="a64f4-112">在工具箱中，按一下另一個行程服務模型項目，然後將它拖曳至設計介面。</span><span class="sxs-lookup"><span data-stu-id="a64f4-112">In the Toolbox, click another Itinerary Service model element, and then drag it to the design surface.</span></span>  
  
9. <span data-ttu-id="a64f4-113">在工具箱中，按一下 Off 遞增模型元素，然後將它拖曳至設計介面。</span><span class="sxs-lookup"><span data-stu-id="a64f4-113">In the Toolbox, click an Off-Ramp model element, and then drag it to the design surface.</span></span>  
  
10. <span data-ttu-id="a64f4-114">在工具箱中，按一下 [連接器工具]，，然後拖曳之間的連線**OnRamp1**模型項目和**ItineraryService1**模型項目。</span><span class="sxs-lookup"><span data-stu-id="a64f4-114">In the Toolbox, click the Connector tool, and then drag a connection between the **OnRamp1** model element and the **ItineraryService1** model element.</span></span>  
  
11. <span data-ttu-id="a64f4-115">在工具箱中，按一下 [連接器工具]，，然後拖曳之間的連線**ItineraryService1**模型項目和**ItineraryService2**模型項目。</span><span class="sxs-lookup"><span data-stu-id="a64f4-115">In the Toolbox, click the Connector tool, and then drag a connection between the **ItineraryService1** model element and the **ItineraryService2** model element.</span></span>  
  
12. <span data-ttu-id="a64f4-116">在工具箱中，按一下 [連接器工具]，，然後拖曳之間的連線**ItineraryService2**模型項目和**OffRamp1**模型項目。</span><span class="sxs-lookup"><span data-stu-id="a64f4-116">In the Toolbox, click the Connector tool, and then drag a connection between the **ItineraryService2** model element and the **OffRamp1** model element.</span></span>  
  
13. <span data-ttu-id="a64f4-117">按一下**OnRamp1**模型項目，然後再在 [屬性] 視窗中，將擴充項屬性設定為**上手 ESB 服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="a64f4-117">Click the **OnRamp1** model element, and then in the Properties window, set the Extender property to **On-Ramp ESB Service Extension**.</span></span>  
  
14. <span data-ttu-id="a64f4-118">設定**BizTalk 應用程式**屬性**Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="a64f4-118">Set the **BizTalk Application** property to **Microsoft.Practices.ESB**.</span></span>  
  
15. <span data-ttu-id="a64f4-119">設定**接收埠**屬性**OnRamp.Itinerary**。</span><span class="sxs-lookup"><span data-stu-id="a64f4-119">Set the **Receive Port** property to **OnRamp.Itinerary**.</span></span>  
  
16. <span data-ttu-id="a64f4-120">按一下**ItinearyService1**模型項目，，然後在 [屬性] 視窗中設定**Extender**屬性**範例協調流程路線服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="a64f4-120">Click the **ItinearyService1** model element, and then in the Properties window, set the **Extender** property to **Sample Orchestration Itinerary Service Extension**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a64f4-121">這是安裝為設計工具擴充性範例的一部分的自訂延伸模組。</span><span class="sxs-lookup"><span data-stu-id="a64f4-121">This is the custom extension installed as part of the Designer Extensibility sample.</span></span> <span data-ttu-id="a64f4-122">它可讓您將屬性加入至傳遞給協調流程為基礎的路線服務的屬性包。</span><span class="sxs-lookup"><span data-stu-id="a64f4-122">It allows you to add properties to the property bag passed to an orchestration-based itinerary service.</span></span>  
  
17. <span data-ttu-id="a64f4-123">設定**OtherValue**屬性**1**。</span><span class="sxs-lookup"><span data-stu-id="a64f4-123">Set the **OtherValue** property to **1**.</span></span>  
  
18. <span data-ttu-id="a64f4-124">設定**ServiceName**屬性**Microsoft.Practices.ESB.Services.Routing**。</span><span class="sxs-lookup"><span data-stu-id="a64f4-124">Set the **ServiceName** property to **Microsoft.Practices.ESB.Services.Routing**.</span></span>  
  
19. <span data-ttu-id="a64f4-125">設定**SomeValue**屬性**2**。</span><span class="sxs-lookup"><span data-stu-id="a64f4-125">Set the **SomeValue** property to **2**.</span></span>  
  
20. <span data-ttu-id="a64f4-126">以滑鼠右鍵按一下**解析程式**集合**ItineraryService1**，然後按一下 **加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="a64f4-126">Right-click the **Resolver** collection of **ItineraryService1**, and then click **Add new Resolver**.</span></span>  
  
21. <span data-ttu-id="a64f4-127">按一下**Resolver1**，然後在 [屬性] 視窗中，將**解析程式實作**屬性**範例解析程式擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="a64f4-127">Click **Resolver1**, and then in the Properties window, set the **Resolver Implementation** property to **Sample Resolver Extension**.</span></span>  
  
22. <span data-ttu-id="a64f4-128">設定**SomeResolverValue**屬性**測試**，然後將 [版本] 屬性設定為**1.0**。</span><span class="sxs-lookup"><span data-stu-id="a64f4-128">Set the **SomeResolverValue** property to **test**, and then set the version property to **1.0**.</span></span>  
  
23. <span data-ttu-id="a64f4-129">按一下**ItineraryService2**模型項目，，然後在 [屬性] 視窗中設定**路線服務的擴充項**屬性**匝道路線服務延伸模組**.</span><span class="sxs-lookup"><span data-stu-id="a64f4-129">Click the **ItineraryService2** model element, and then in the Properties window, set the **Itinerary Service Extender** property to **Off-Ramp Itinerary Service Extension**.</span></span>  
  
24. <span data-ttu-id="a64f4-130">設定**匝道**屬性**OffRamp1 > 傳送處理常式**。</span><span class="sxs-lookup"><span data-stu-id="a64f4-130">Set the **Off-Ramp** property to **OffRamp1 > Send Handlers**.</span></span>  
  
25. <span data-ttu-id="a64f4-131">按一下**OffRamp1**模型項目，，然後在 [屬性] 視窗中設定**Extender**屬性**匝道 ESB 服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="a64f4-131">Click the **OffRamp1** model element, and then in the Properties window, set the **Extender** property to **Off-Ramp ESB Service Extension**.</span></span>  
  
26. <span data-ttu-id="a64f4-132">設定**BizTalk 應用程式**屬性**GlobalBank.ESB**。</span><span class="sxs-lookup"><span data-stu-id="a64f4-132">Set the **BizTalk Application** property to **GlobalBank.ESB**.</span></span>  
  
27. <span data-ttu-id="a64f4-133">設定**傳送埠**屬性**DynamicResolutionOneWay**。</span><span class="sxs-lookup"><span data-stu-id="a64f4-133">Set the **Send Port** property to **DynamicResolutionOneWay**.</span></span>  
  
28. <span data-ttu-id="a64f4-134">以滑鼠右鍵按一下設計介面，然後按一下**匯出模型**。</span><span class="sxs-lookup"><span data-stu-id="a64f4-134">Right-click the design surface, and then click **Export Model**.</span></span>  
  
29. <span data-ttu-id="a64f4-135">檢查產生的 XML。</span><span class="sxs-lookup"><span data-stu-id="a64f4-135">Examine the generated XML.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a64f4-136">請注意**PropertyBag**項目以及它所包含的屬性。</span><span class="sxs-lookup"><span data-stu-id="a64f4-136">Notice the **PropertyBag** element and the properties it contains.</span></span> <span data-ttu-id="a64f4-137">也請注意範例解析程式的連接字串和設定方式輸入的內容為基礎。</span><span class="sxs-lookup"><span data-stu-id="a64f4-137">Also notice the Sample resolver connection string and how it was configured based on the properties entered.</span></span>