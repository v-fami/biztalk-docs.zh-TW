---
title: 如何： 實作內容架構路由使用訊息內容屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 952af792-5762-4b04-9087-980bb3323568
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be099923fea9d5dbb22559203b297fadf5dd1fdc
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26010119"
---
# <a name="how-to-implement-content-based-routing-using-message-context-properties"></a><span data-ttu-id="4506e-102">如何： 實作內容架構路由使用訊息內容屬性</span><span class="sxs-lookup"><span data-stu-id="4506e-102">How to: Implement Content-Based Routing Using Message Context Properties</span></span>
## <a name="goal"></a><span data-ttu-id="4506e-103">目標</span><span class="sxs-lookup"><span data-stu-id="4506e-103">Goal</span></span>  
 <span data-ttu-id="4506e-104">本節示範如何使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]路線設計工具建立行程選取訊息收件者根據訊息內容屬性，然後將訊息路由傳送至該收件者，使用行程 Broker 訊息服務。</span><span class="sxs-lookup"><span data-stu-id="4506e-104">This section demonstrates how to use the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Itinerary Designer to create an itinerary that selects a message recipient based on the message context property and then routes a message to that recipient using the Itinerary Broker messaging service.</span></span>  
  
 <span data-ttu-id="4506e-105">在本主題中，您將完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="4506e-105">In this topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="4506e-106">建立行程路線的 broker 與使用靜態的解析程式的兩個路由服務。</span><span class="sxs-lookup"><span data-stu-id="4506e-106">Create an itinerary with an itinerary broker and two routing services with static resolvers.</span></span>  
  
-   <span data-ttu-id="4506e-107">測試使用路線測試用戶端範例應用程式的路線。</span><span class="sxs-lookup"><span data-stu-id="4506e-107">Test the itinerary using the Itinerary Test Client sample application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4506e-108">在目前的實作不提供任何協調流程為基礎的 broker 服務。</span><span class="sxs-lookup"><span data-stu-id="4506e-108">No orchestration-based broker service is provided in the current implementation.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4506e-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="4506e-109">Prerequisites</span></span>  
 <span data-ttu-id="4506e-110">在此 「 如何 」 主題中的程序需要完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="4506e-110">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="steps"></a><span data-ttu-id="4506e-111">步驟</span><span class="sxs-lookup"><span data-stu-id="4506e-111">Steps</span></span>  
  
#### <a name="to-create-an-esb-itinerary-dsl-model"></a><span data-ttu-id="4506e-112">若要建立 ESB 行程 DSL 模型</span><span class="sxs-lookup"><span data-stu-id="4506e-112">To create an ESB Itinerary DSL model</span></span>  
  
1.  <span data-ttu-id="4506e-113">在 Visual Studio 中開啟 C:\HowTos\Patterns\Patterns.sln。</span><span class="sxs-lookup"><span data-stu-id="4506e-113">In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="4506e-114">在 方案總管 中，以滑鼠右鍵按一下**ItineraryLibrary**，指向 **新增**，然後按一下 **新的行程**。</span><span class="sxs-lookup"><span data-stu-id="4506e-114">In Solution Explorer, right-click **ItineraryLibrary**, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="4506e-115">在**加入新項目**對話方塊中，按一下  **ItineraryDsl**在範本窗格中。</span><span class="sxs-lookup"><span data-stu-id="4506e-115">In the **Add New Item** dialog box, click **ItineraryDsl** in the Templates pane.</span></span>  
  
4.  <span data-ttu-id="4506e-116">在**名稱**方塊中，輸入**ChoiceRouter**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="4506e-116">In the **Name** box, type **ChoiceRouter**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a><span data-ttu-id="4506e-117">若要設定的路線屬性</span><span class="sxs-lookup"><span data-stu-id="4506e-117">To configure the properties of the itinerary</span></span>  
  
1.  <span data-ttu-id="4506e-118">在 Visual Studio 中，按一下設計介面的**ChoiceRouter**路線。</span><span class="sxs-lookup"><span data-stu-id="4506e-118">In Visual Studio, click the design surface of the **ChoiceRouter** itinerary.</span></span> <span data-ttu-id="4506e-119">在**ChoiceRouter**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="4506e-119">In the **ChoiceRouter** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="4506e-120">在**模型匯出工具**下拉式清單中，按一下  **XML 路線匯出工具**。</span><span class="sxs-lookup"><span data-stu-id="4506e-120">In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="4506e-121">在**Extender 設定**區段中，按一下旁邊的省略符號按鈕 （...）**路線 XML 檔案**屬性。</span><span class="sxs-lookup"><span data-stu-id="4506e-121">In the **Extender Settings** section, click the ellipsis button (...) next to the **Itinerary XML file** property.</span></span>  
  
    3.  <span data-ttu-id="4506e-122">在**匯出模式**屬性下拉式清單中，按一下  **Strict**。</span><span class="sxs-lookup"><span data-stu-id="4506e-122">In the **Export Mode** property drop-down list, click **Strict**.</span></span>  
  
    4.  <span data-ttu-id="4506e-123">在**選取 XML 檔案** 對話方塊中，輸入**C:\HowTos\Itineraries\ChoiceRouter**中**檔案名稱**方塊，然後再按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="4506e-123">In the **Select XML File** dialog box, type **C:\HowTos\Itineraries\ChoiceRouter** in the **File name** box, and then click **Save**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4506e-124">這個步驟可讓您匯出成 XML 的路線，到本機檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="4506e-124">This step enables you to export the itinerary as XML to a local file location.</span></span> <span data-ttu-id="4506e-125">藉由將行程至本機檔案的位置，而不匯出至路線的資料庫，您可以測試使用 ESB 測試用戶端應用程式的路線。</span><span class="sxs-lookup"><span data-stu-id="4506e-125">By exporting an itinerary to a local file location, instead of to the itinerary database, you can test the itinerary using the ESB Test Client application.</span></span> <span data-ttu-id="4506e-126">您將完成此程序，稍後在本使用說明主題。</span><span class="sxs-lookup"><span data-stu-id="4506e-126">You will complete this process later in this How-to topic.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="4506e-127">若要定義路線結構</span><span class="sxs-lookup"><span data-stu-id="4506e-127">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="4506e-128">從 [工具箱] 拖曳**上手**至設計介面的模型項目。</span><span class="sxs-lookup"><span data-stu-id="4506e-128">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="4506e-129">在 [OnRamp1 屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="4506e-129">In the OnRamp1 Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="4506e-130">按一下**名稱**屬性，，然後輸入**ReceiveNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="4506e-130">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="4506e-131">在**Extender**下拉式清單中，按一下 **上手 Extender**。</span><span class="sxs-lookup"><span data-stu-id="4506e-131">In the **Extender** drop-down list, click **On-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="4506e-132">在**BizTalk 應用程式**下拉式清單中，按一下  **Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="4506e-132">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="4506e-133">在**接收埠**下拉式清單中，按一下  **OnRamp.Itinerary**。</span><span class="sxs-lookup"><span data-stu-id="4506e-133">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="4506e-134">從 [工具箱] 拖曳**路線 Broker 服務**模型設計工具介面中，項目，然後將它放到右側**上手**模型項目。</span><span class="sxs-lookup"><span data-stu-id="4506e-134">From the Toolbox, drag an **Itinerary Broker Service** model element to the designer surface, and then place it to the right side of the **On-Ramp** model element.</span></span> <span data-ttu-id="4506e-135">在**ItineraryBrokerService1**，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="4506e-135">In the **ItineraryBrokerService1**, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="4506e-136">按一下**名稱**屬性，，然後輸入**RouteBrokerService**。</span><span class="sxs-lookup"><span data-stu-id="4506e-136">Click the **Name** property, and then type **RouteBrokerService**.</span></span>  
  
    2.  <span data-ttu-id="4506e-137">在**Extender**下拉式清單中，按一下 **傳訊 Broker Extender**。</span><span class="sxs-lookup"><span data-stu-id="4506e-137">In the **Extender** drop-down list, click **Messaging Broker Extender**.</span></span>  
  
    3.  <span data-ttu-id="4506e-138">在**容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。</span><span class="sxs-lookup"><span data-stu-id="4506e-138">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="4506e-139">在**服務名稱**下拉式清單中，按一下  **Microsoft.Practices.ESB.Itinerary.Services.Broker.MessagingBroker**。</span><span class="sxs-lookup"><span data-stu-id="4506e-139">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Itinerary.Services.Broker.MessagingBroker**.</span></span>  
  
3.  <span data-ttu-id="4506e-140">以滑鼠右鍵按一下**篩選**集合，然後再按一下**加入新的篩選器**。</span><span class="sxs-lookup"><span data-stu-id="4506e-140">Right-click the **Filter** collection, and then click **Add new Filter**.</span></span> <span data-ttu-id="4506e-141">在**Filter1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="4506e-141">In the **Filter1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="4506e-142">按一下**名稱**屬性，，然後輸入**ASMXFilter**。</span><span class="sxs-lookup"><span data-stu-id="4506e-142">Click the **Name** property, and then type **ASMXFilter**.</span></span>  
  
    2.  <span data-ttu-id="4506e-143">按一下**篩選**實作下拉式清單中，，然後按一下**XPath 篩選條件**。</span><span class="sxs-lookup"><span data-stu-id="4506e-143">Click the **Filter** Implementation drop-down list, and then click **XPath Filter**.</span></span>  
  
    3.  <span data-ttu-id="4506e-144">按一下**運算式**屬性，，然後輸入**計數 (ContextProperties/屬性 [@name= 'InboundTransportLocation'] [包含 (。，'ProcessItinerary.asmx')]) > 0**。</span><span class="sxs-lookup"><span data-stu-id="4506e-144">Click the **Expression** property, and then type **count(/ContextProperties/Property[@name='InboundTransportLocation'][contains(., 'ProcessItinerary.asmx')]) > 0**.</span></span>  
  
4.  <span data-ttu-id="4506e-145">以滑鼠右鍵按一下**篩選**集合，然後再按一下**加入新的篩選器**。</span><span class="sxs-lookup"><span data-stu-id="4506e-145">Right-click the **Filter** collection, and then click **Add new Filter**.</span></span> <span data-ttu-id="4506e-146">在**Filter1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="4506e-146">In the **Filter1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="4506e-147">按一下**名稱**屬性，，然後輸入**WCFFilter**。</span><span class="sxs-lookup"><span data-stu-id="4506e-147">Click the **Name** property, and then type **WCFFilter**.</span></span>  
  
    2.  <span data-ttu-id="4506e-148">按一下**篩選器實作**下拉式清單，然後按一下**XPath 篩選條件**。</span><span class="sxs-lookup"><span data-stu-id="4506e-148">Click the **Filter Implementation** drop-down list, and click **XPath Filter**.</span></span>  
  
    3.  <span data-ttu-id="4506e-149">按一下**運算式**屬性，，然後輸入**計數 (ContextProperties/屬性 [@name= 'InboundTransportLocation'] [包含 (。，' ESB。ItineraryServices.WCF')]) > 0**。</span><span class="sxs-lookup"><span data-stu-id="4506e-149">Click the **Expression** property, and then type **count(/ContextProperties/Property[@name='InboundTransportLocation'][contains(., 'ESB.ItineraryServices.WCF')]) > 0**.</span></span>  
  
5.  <span data-ttu-id="4506e-150">以滑鼠右鍵按一下**解析程式**集合**RouteBrokerService**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="4506e-150">Right-click the **Resolver** collection of the **RouteBrokerService** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="4506e-151">在**Resolver1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="4506e-151">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="4506e-152">按一下**名稱**屬性，，然後輸入**ResolverBrokerRoute**。</span><span class="sxs-lookup"><span data-stu-id="4506e-152">Click the **Name** property, and then type **ResolverBrokerRoute**.</span></span>  
  
    2.  <span data-ttu-id="4506e-153">在**解析程式實作**下拉式清單中，按一下  **MessageContext 解析程式擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="4506e-153">In the **Resolver Implementation** drop-down list, click **MessageContext Resolver Extension**.</span></span>  
  
6.  <span data-ttu-id="4506e-154">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="4506e-154">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="4506e-155">拖曳連接**ReceiveNAOrder**模型項目的**RouteBrokerService**模型項目。</span><span class="sxs-lookup"><span data-stu-id="4506e-155">Drag a connection from the **ReceiveNAOrder** model element to the **RouteBrokerService** model element.</span></span>  
  
7.  <span data-ttu-id="4506e-156">從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其下放置**RouteBrokerService**模型項目。</span><span class="sxs-lookup"><span data-stu-id="4506e-156">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it under the **RouteBrokerService** model element.</span></span> <span data-ttu-id="4506e-157">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="4506e-157">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="4506e-158">按一下**名稱**屬性，，然後輸入**RouteToFileFromASMX**。</span><span class="sxs-lookup"><span data-stu-id="4506e-158">Click the **Name** property, and then type **RouteToFileFromASMX**.</span></span>  
  
    2.  <span data-ttu-id="4506e-159">在**路線服務的擴充項**下拉式清單中，按一下 **傳訊 Extender**。</span><span class="sxs-lookup"><span data-stu-id="4506e-159">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="4506e-160">這個屬性會定義程序將需要 (messaging) 在管線中的位置。</span><span class="sxs-lookup"><span data-stu-id="4506e-160">This property defines that the process will take place in a pipeline (messaging).</span></span> <span data-ttu-id="4506e-161">或者，如果處理程序，就會進行協調流程中，設定**路線服務的擴充項**屬性**協調流程 Extender**。</span><span class="sxs-lookup"><span data-stu-id="4506e-161">Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Extender**.</span></span>  
  
    3.  <span data-ttu-id="4506e-162">在**容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。</span><span class="sxs-lookup"><span data-stu-id="4506e-162">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="4506e-163">在**服務名稱**下拉式清單中，按一下  **Microsoft.Practices.ESB.Services.Routing**。</span><span class="sxs-lookup"><span data-stu-id="4506e-163">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**.</span></span>  
  
8.  <span data-ttu-id="4506e-164">以滑鼠右鍵按一下**解析程式**集合**RouteToFileFromASMX**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="4506e-164">Right-click the **Resolver** collection of the **RouteToFileFromASMX** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="4506e-165">在**Resolver1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="4506e-165">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="4506e-166">按一下**名稱**屬性，，然後輸入**ResolverFromAsmx**。</span><span class="sxs-lookup"><span data-stu-id="4506e-166">Click the **Name** property, and then type **ResolverFromAsmx**.</span></span>  
  
    2.  <span data-ttu-id="4506e-167">在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="4506e-167">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="4506e-168">在**傳輸名稱**下拉式清單中，按一下 **檔案**。</span><span class="sxs-lookup"><span data-stu-id="4506e-168">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    4.  <span data-ttu-id="4506e-169">按一下**傳輸位置**屬性，，然後輸入**c:\howtos\out\asmx%MessageId%.xml**。</span><span class="sxs-lookup"><span data-stu-id="4506e-169">Click the **Transport Location** property, and then type **c:\howtos\out\asmx%MessageId%.xml**.</span></span>  
  
9. <span data-ttu-id="4506e-170">從 [工具箱] 拖曳**匝道**模型項目至設計介面，然後再將它放右邊的**RouteToFileFromASMX**模型項目。</span><span class="sxs-lookup"><span data-stu-id="4506e-170">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **RouteToFileFromASMX** model element.</span></span> <span data-ttu-id="4506e-171">在**OffRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="4506e-171">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="4506e-172">按一下**名稱**屬性，，然後輸入**SendASMXOrder**。</span><span class="sxs-lookup"><span data-stu-id="4506e-172">Click the **Name** property, and then type **SendASMXOrder**.</span></span>  
  
    2.  <span data-ttu-id="4506e-173">在**Extender**下拉式清單中，按一下 **匝道 ESB Extender**。</span><span class="sxs-lookup"><span data-stu-id="4506e-173">In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="4506e-174">在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。</span><span class="sxs-lookup"><span data-stu-id="4506e-174">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="4506e-175">在**傳送埠**下拉式清單中，按一下  **DynamicResolutionOneWay**。</span><span class="sxs-lookup"><span data-stu-id="4506e-175">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
10. <span data-ttu-id="4506e-176">從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**RouteToFileFromASMX**模型項目和**SendASMXOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="4506e-176">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **RouteToFileFromASMX** model element and the **SendASMXOrder** model element.</span></span> <span data-ttu-id="4506e-177">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="4506e-177">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="4506e-178">按一下**名稱**屬性，，然後輸入**SendPortFilterASMX**。</span><span class="sxs-lookup"><span data-stu-id="4506e-178">Click the **Name** property, and then type **SendPortFilterASMX**.</span></span>  
  
    2.  <span data-ttu-id="4506e-179">在**路線服務的擴充項**下拉式清單中，按一下 **匝道 Extender**。</span><span class="sxs-lookup"><span data-stu-id="4506e-179">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="4506e-180">在**匝道**下拉式清單中，展開**SendASMXOrder**，然後按一下 **傳送處理常式**。</span><span class="sxs-lookup"><span data-stu-id="4506e-180">In the **Off-Ramp** drop-down list, expand **SendASMXOrder**, and then click **Send Handlers**.</span></span>  
  
11. <span data-ttu-id="4506e-181">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="4506e-181">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="4506e-182">拖曳連接**RouteToFileFromASMX**模型項目的**SendPortFilterASMX**模型項目。</span><span class="sxs-lookup"><span data-stu-id="4506e-182">Drag a connection from the **RouteToFileFromASMX** model element to the **SendPortFilterASMX** model element.</span></span>  
  
12. <span data-ttu-id="4506e-183">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="4506e-183">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="4506e-184">拖曳連接**SendPortFilterASMX**模型項目的**SendASMXOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="4506e-184">Drag a connection from the **SendPortFilterASMX** model element to the **SendASMXOrder** model element.</span></span>  
  
13. <span data-ttu-id="4506e-185">從 [工具箱] 拖曳**路線服務**模型項目至設計介面，然後再將它放右邊的**RouteBrokerService**模型項目。</span><span class="sxs-lookup"><span data-stu-id="4506e-185">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it to the right of **RouteBrokerService** model element.</span></span> <span data-ttu-id="4506e-186">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="4506e-186">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="4506e-187">按一下**名稱**屬性，，然後輸入**RouteToFileFromWCF**。</span><span class="sxs-lookup"><span data-stu-id="4506e-187">Click the **Name** property, and then type **RouteToFileFromWCF**.</span></span>  
  
    2.  <span data-ttu-id="4506e-188">在**路線服務的擴充項**下拉式清單中，按一下 **傳訊 Extender**。</span><span class="sxs-lookup"><span data-stu-id="4506e-188">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="4506e-189">這個屬性會定義程序將需要 (messaging) 在管線中的位置。</span><span class="sxs-lookup"><span data-stu-id="4506e-189">This property defines that the process will take place in a pipeline (messaging).</span></span> <span data-ttu-id="4506e-190">或者，如果處理程序，就會進行協調流程中，設定**路線服務的擴充項**屬性**協調流程 Extender**。</span><span class="sxs-lookup"><span data-stu-id="4506e-190">Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Extender**.</span></span>  
  
    3.  <span data-ttu-id="4506e-191">在**容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。</span><span class="sxs-lookup"><span data-stu-id="4506e-191">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="4506e-192">在**服務名稱**下拉式清單中，按一下  **Microsoft.Practices.ESB.Services.Routing**。</span><span class="sxs-lookup"><span data-stu-id="4506e-192">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**.</span></span>  
  
14. <span data-ttu-id="4506e-193">以滑鼠右鍵按一下**解析程式**集合**RouteToFileFromWCF**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="4506e-193">Right-click the **Resolver** collection of the **RouteToFileFromWCF** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="4506e-194">在**Resolver1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="4506e-194">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="4506e-195">按一下**名稱**屬性，，然後輸入**ResolverFromWCF**。</span><span class="sxs-lookup"><span data-stu-id="4506e-195">Click the **Name** property, and then type **ResolverFromWCF**.</span></span>  
  
    2.  <span data-ttu-id="4506e-196">在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="4506e-196">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="4506e-197">在**傳輸名稱**下拉式清單中，按一下 **檔案**。</span><span class="sxs-lookup"><span data-stu-id="4506e-197">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    4.  <span data-ttu-id="4506e-198">按一下**傳輸位置**屬性，，然後輸入**c:\howtos\out\wcf%MessageId%.xml**。</span><span class="sxs-lookup"><span data-stu-id="4506e-198">Click the **Transport Location** property, and then type **c:\howtos\out\wcf%MessageId%.xml**.</span></span>  
  
15. <span data-ttu-id="4506e-199">從 [工具箱] 拖曳**匝道**模型項目至設計介面，然後再將它放右邊的**RouteToFileFromWCF**模型項目。</span><span class="sxs-lookup"><span data-stu-id="4506e-199">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **RouteToFileFromWCF** model element.</span></span> <span data-ttu-id="4506e-200">在**OffRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="4506e-200">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="4506e-201">按一下**名稱**屬性，，然後輸入**SendWCFOrder**。</span><span class="sxs-lookup"><span data-stu-id="4506e-201">Click the **Name** property, and then type **SendWCFOrder**.</span></span>  
  
    2.  <span data-ttu-id="4506e-202">在**Extender**下拉式清單中，按一下 **匝道 ESB Extender**。</span><span class="sxs-lookup"><span data-stu-id="4506e-202">In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="4506e-203">在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。</span><span class="sxs-lookup"><span data-stu-id="4506e-203">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="4506e-204">在**傳送埠**下拉式清單中，按一下  **DynamicResolutionOneWay**。</span><span class="sxs-lookup"><span data-stu-id="4506e-204">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
16. <span data-ttu-id="4506e-205">從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**RouteToFileFromWCF**模型項目和**SendWCFOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="4506e-205">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **RouteToFileFromWCF** model element and the **SendWCFOrder** model element.</span></span> <span data-ttu-id="4506e-206">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="4506e-206">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="4506e-207">按一下**名稱**屬性，，然後輸入**SendPortFilterWCF**。</span><span class="sxs-lookup"><span data-stu-id="4506e-207">Click the **Name** property, and then type **SendPortFilterWCF**.</span></span>  
  
    2.  <span data-ttu-id="4506e-208">在**路線服務的擴充項**下拉式清單中，按一下 **匝道 Extender**。</span><span class="sxs-lookup"><span data-stu-id="4506e-208">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="4506e-209">在**匝道**下拉式清單中，展開**SendWCFOrder**，然後按一下 **傳送處理常式**。</span><span class="sxs-lookup"><span data-stu-id="4506e-209">In the **Off-Ramp** drop-down list, expand **SendWCFOrder**, and then click **Send Handlers**.</span></span>  
  
17. <span data-ttu-id="4506e-210">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="4506e-210">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="4506e-211">拖曳連接**RouteToFileFromWCF**模型項目的**SendPortFilterWCF**模型項目。</span><span class="sxs-lookup"><span data-stu-id="4506e-211">Drag a connection from the **RouteToFileFromWCF** model element to the **SendPortFilterWCF** model element.</span></span>  
  
18. <span data-ttu-id="4506e-212">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="4506e-212">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="4506e-213">拖曳連接**SendPortFilterWCF**模型項目的**SendWCFOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="4506e-213">Drag a connection from the **SendPortFilterWCF** model element to the **SendWCFOrder** model element.</span></span>  
  
19. <span data-ttu-id="4506e-214">從 [工具箱] 拖曳**路線 Outport**到右框線的模型項目**RouteBrokerService**。</span><span class="sxs-lookup"><span data-stu-id="4506e-214">From the Toolbox, drag an **Itinerary Outport** model element to right border of **RouteBrokerService**.</span></span> <span data-ttu-id="4506e-215">在**ItineraryBrokerOutPort1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="4506e-215">In the **ItineraryBrokerOutPort1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="4506e-216">按一下**名稱**屬性，，然後輸入**WCF 連接埠**。</span><span class="sxs-lookup"><span data-stu-id="4506e-216">Click the **Name** property, and then type **WCF Port**.</span></span>  
  
    2.  <span data-ttu-id="4506e-217">在**篩選**下拉式清單中，按一下  **WCFFilter**。</span><span class="sxs-lookup"><span data-stu-id="4506e-217">In the **Filter** drop-down list, click **WCFFilter**.</span></span>  
  
    3.  <span data-ttu-id="4506e-218">在**解析程式**下拉式清單中，按一下  **ResolverBrokerRoute**。</span><span class="sxs-lookup"><span data-stu-id="4506e-218">In the **Resolver** drop-down list, click **ResolverBrokerRoute**.</span></span>  
  
20. <span data-ttu-id="4506e-219">從 [工具箱] 拖曳**路線 Outport**模型項目的下框線的**RouteBrokerService**。</span><span class="sxs-lookup"><span data-stu-id="4506e-219">From the Toolbox, drag an **Itinerary Outport** model element to the bottom border of **RouteBrokerService**.</span></span> <span data-ttu-id="4506e-220">在**ItineraryBrokerOutPort1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="4506e-220">In the **ItineraryBrokerOutPort1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="4506e-221">按一下**名稱**屬性，，然後輸入**ASMX 連接埠**。</span><span class="sxs-lookup"><span data-stu-id="4506e-221">Click the **Name** property, and then type **ASMX Port**.</span></span>  
  
    2.  <span data-ttu-id="4506e-222">在**篩選**下拉式清單中，按一下  **ASMXFilter**。</span><span class="sxs-lookup"><span data-stu-id="4506e-222">In the **Filter** drop-down list, click **ASMXFilter**.</span></span>  
  
    3.  <span data-ttu-id="4506e-223">在**解析程式**下拉式清單中，按一下  **ResolverBrokerRoute**。</span><span class="sxs-lookup"><span data-stu-id="4506e-223">In the **Resolver** drop-down list, click **ResolverBrokerRoute**.</span></span>  
  
21. <span data-ttu-id="4506e-224">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="4506e-224">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="4506e-225">拖曳連接**WCF 連接埠**模型項目的**RouteToFileFromWCF**模型項目。</span><span class="sxs-lookup"><span data-stu-id="4506e-225">Drag a connection from the **WCF Port** model element to the **RouteToFileFromWCF** model element.</span></span>  
  
22. <span data-ttu-id="4506e-226">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="4506e-226">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="4506e-227">拖曳連接**ASMX 連接埠**模型項目的**RouteToFileFromASMX**模型項目。</span><span class="sxs-lookup"><span data-stu-id="4506e-227">Drag a connection from the **ASMX Port** model element to the **RouteToFileFromASMX** model element.</span></span>  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a><span data-ttu-id="4506e-228">若要匯出的行程測試用戶端使用的模型</span><span class="sxs-lookup"><span data-stu-id="4506e-228">To export the model for use with the Itinerary Test Client</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4506e-229">您必須匯出路線兩次： 一次在 XML 中，另一個時間來測試路由的 broker 透過資料庫。</span><span class="sxs-lookup"><span data-stu-id="4506e-229">You will need to export the itinerary twice: one time in XML and one time to the database to test the routing through the broker.</span></span>  
  
1.  <span data-ttu-id="4506e-230">在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**ChoiceRouter**路線，然後再按一下**匯出模型**。</span><span class="sxs-lookup"><span data-stu-id="4506e-230">In Visual Studio, right-click the design surface of the **ChoiceRouter** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4506e-231">在 Visual Studio 中，開啟路線的 XML 版本。</span><span class="sxs-lookup"><span data-stu-id="4506e-231">The XML version of the itinerary opens in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="4506e-232">在 Windows 檔案總管，瀏覽 C:\HowTos\Itineraries，並注意您路線 XML (ChoiceRouter.xml) 建立。</span><span class="sxs-lookup"><span data-stu-id="4506e-232">In Windows Explorer, browse to C:\HowTos\Itineraries, and then notice the creation of your itinerary XML (ChoiceRouter.xml).</span></span>  
  
3.  <span data-ttu-id="4506e-233">在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**ChoiceRouter**路線，然後再按一下**匯出模型**。</span><span class="sxs-lookup"><span data-stu-id="4506e-233">In Visual Studio, right-click the design surface of the **ChoiceRouter** itinerary, and then click **Export Model**.</span></span>  
  
4.  <span data-ttu-id="4506e-234">在 [屬性] 視窗中，按一下**資料庫路線匯出工具**中**模型匯出工具**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="4506e-234">In the Properties window, click **Database Itinerary Exporter** in the **Model Exporter** drop-down list.</span></span>  
  
5.  <span data-ttu-id="4506e-235">在 [屬性] 視窗中，設定**路線資料庫**屬性指向路線資料庫的連接字串。</span><span class="sxs-lookup"><span data-stu-id="4506e-235">In the Properties window, set the **Itinerary Database** property connection string to point to the itinerary database.</span></span>  
  
6.  <span data-ttu-id="4506e-236">在**路線狀態**屬性下拉式清單中，選取**部署**。</span><span class="sxs-lookup"><span data-stu-id="4506e-236">In the **Itinerary Status** property drop-down list select **Deployed**.</span></span>  
  
7.  <span data-ttu-id="4506e-237">在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**ChoiceRouter**路線，然後再按一下**匯出模型**。</span><span class="sxs-lookup"><span data-stu-id="4506e-237">In Visual Studio, right-click the design surface of the **ChoiceRouter** itinerary, and then click **Export Model**.</span></span>  
  
#### <a name="to-test-the-itinerary"></a><span data-ttu-id="4506e-238">若要測試路線</span><span class="sxs-lookup"><span data-stu-id="4506e-238">To test the itinerary</span></span>  
  
1.  <span data-ttu-id="4506e-239">開啟路線測試用戶端範例應用程式使用期間建立的捷徑[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)(C:\HowTos\ESB。Itinerary.Test.exe-捷徑)。</span><span class="sxs-lookup"><span data-stu-id="4506e-239">Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).</span></span>  
  
2.  <span data-ttu-id="4506e-240">在路線測試用戶端中，清除**使用 WCF 服務**核取方塊，然後**負載路線**。</span><span class="sxs-lookup"><span data-stu-id="4506e-240">In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.</span></span>  
  
3.  <span data-ttu-id="4506e-241">在**開啟路線檔案**對話方塊中，瀏覽至 C:\HowTos\Itineraries。</span><span class="sxs-lookup"><span data-stu-id="4506e-241">In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="4506e-242">選取**ChoiceRouter.xml**，然後按一下 **開啟**載入路線。</span><span class="sxs-lookup"><span data-stu-id="4506e-242">Select **ChoiceRouter.xml**, and then click **Open** to load the itinerary.</span></span>  
  
4.  <span data-ttu-id="4506e-243">按一下**確定**關閉 「 路線載入成功 」 訊息。</span><span class="sxs-lookup"><span data-stu-id="4506e-243">Click **OK** to close the "Itinerary Loaded Successfully" message.</span></span>  
  
5.  <span data-ttu-id="4506e-244">在路線測試用戶端中，按一下旁邊的省略符號按鈕 （...）**載入訊息**方塊。</span><span class="sxs-lookup"><span data-stu-id="4506e-244">In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.</span></span>  
  
6.  <span data-ttu-id="4506e-245">在**選取要載入的 XML 文件**對話方塊中，瀏覽至 C:\Patterns\HowTos。</span><span class="sxs-lookup"><span data-stu-id="4506e-245">In the **Select XML Document to load** dialog box, browse to C:\Patterns\HowTos.</span></span> <span data-ttu-id="4506e-246">選取 NAOrderDoc.xml，，然後按一下**開啟**載入測試訊息。</span><span class="sxs-lookup"><span data-stu-id="4506e-246">Select NAOrderDoc.xml, and then click **Open** to load the test message.</span></span>  
  
7.  <span data-ttu-id="4506e-247">按一下**送出要求** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4506e-247">Click the **Submit Request** button.</span></span> <span data-ttu-id="4506e-248">測試完成時，按一下**確定**關閉出現的確認訊息。</span><span class="sxs-lookup"><span data-stu-id="4506e-248">When the test completes, click **OK** to close the confirmation message that appears.</span></span>  
  
8.  <span data-ttu-id="4506e-249">在 Windows 檔案總管，瀏覽至 C:\HowTos\Out。請確認 ASMX%MessageID%.xml 訊息已寫入至這個目錄。</span><span class="sxs-lookup"><span data-stu-id="4506e-249">In Windows Explorer, browse to C:\HowTos\Out. Verify that the ASMX%MessageID%.xml messages have been written to this directory.</span></span>  
  
9. <span data-ttu-id="4506e-250">按一下 路線測試用戶端**使用 WCF 服務**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="4506e-250">Click the Itinerary Test client **Use WCF Service** check box.</span></span> <span data-ttu-id="4506e-251">在**路線名稱**方塊中，輸入**ChoiceRouter**，然後按一下 [**送出要求**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4506e-251">In the **Itinerary Name** box, type **ChoiceRouter**, and then click the **Submit Request** button.</span></span> <span data-ttu-id="4506e-252">測試完成時，按一下**確定**關閉確認訊息。</span><span class="sxs-lookup"><span data-stu-id="4506e-252">When the test completes, click **OK** to close the confirmation message.</span></span>  
  
10. <span data-ttu-id="4506e-253">在 Windows 檔案總管，瀏覽至 C:\HowTos\Out。請確認 WCF%MessageID%.xml 訊息已寫入至這個目錄。</span><span class="sxs-lookup"><span data-stu-id="4506e-253">In Windows Explorer, browse to C:\HowTos\Out. Verify that the WCF%MessageID%.xml messages have been written to this directory.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="4506e-254">其他資源</span><span class="sxs-lookup"><span data-stu-id="4506e-254">Additional Resources</span></span>  
 <span data-ttu-id="4506e-255">如需詳細資訊，請參閱下列相關主題：</span><span class="sxs-lookup"><span data-stu-id="4506e-255">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="4506e-256">如何：使用商務規則原則選取路線</span><span class="sxs-lookup"><span data-stu-id="4506e-256">How to: Select an Itinerary Using a Business Rules Policy</span></span>](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
-   [<span data-ttu-id="4506e-257">如何：使用商務規則原則根據訊息內容來動態路由訊息</span><span class="sxs-lookup"><span data-stu-id="4506e-257">How to: Dynamically Route a Message Based on Message Context Using a Business Rules Policy</span></span>](../esb-toolkit/dynamically-route-messages-based-on-message-context-using-business-rules-policy.md)  
  
-   [<span data-ttu-id="4506e-258">開發活動</span><span class="sxs-lookup"><span data-stu-id="4506e-258">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="4506e-259">訊息路由模式</span><span class="sxs-lookup"><span data-stu-id="4506e-259">Message Routing Patterns</span></span>](../esb-toolkit/message-routing-patterns.md)