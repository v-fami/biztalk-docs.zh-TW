---
title: 如何： 轉換訊息及使用要求-回應訊息交換模式的服務端點的路由 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b1e656fb-6c5f-4b2b-a1b6-4c812b78ee22
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 071227182eb9b5550b23e23463800cc7dd5a22c4
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26010351"
---
# <a name="how-to-transform-a-message-and-route-to-a-service-endpoint-using-a-request-response-message-exchange-pattern"></a><span data-ttu-id="8dc2f-102">如何： 轉換訊息及使用要求-回應訊息交換模式的服務端點的路由</span><span class="sxs-lookup"><span data-stu-id="8dc2f-102">How to: Transform a Message and Route to a Service Endpoint Using a Request-Response Message Exchange Pattern</span></span>
## <a name="goal"></a><span data-ttu-id="8dc2f-103">目標</span><span class="sxs-lookup"><span data-stu-id="8dc2f-103">Goal</span></span>  
 <span data-ttu-id="8dc2f-104">本節示範如何使用 ESB 設計工具的特定領域語言 (DSL) 來建立適用於雙向上手要求-回應路線。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-104">This section demonstrates how to use the ESB Designer domain-specific language (DSL) to create a request-response itinerary that can be used with a two-way on-ramp.</span></span> <span data-ttu-id="8dc2f-105">您將建立接收訊息、 將訊息轉換、 提交訊息至服務，並返回原始訊息的傳送者的服務回應訊息的路由受控滑動。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-105">You will create a routing slip to receive a message, transform the message, submit the message to a service, and return the service response message to the submitter of the original message.</span></span>  
  
 <span data-ttu-id="8dc2f-106">在此 「 如何 」 主題，您將完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="8dc2f-106">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="8dc2f-107">建立轉換路線實作的服務，Microsoft BizTalk Server 對應路線的路由受控滑動。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-107">Create an itinerary routing slip with a transform itinerary service that implements a Microsoft BizTalk Server map.</span></span>  
  
-   <span data-ttu-id="8dc2f-108">設定轉換後的訊息路由至服務端點路線。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-108">Configure the itinerary to route the transformed message to a service endpoint.</span></span>  
  
-   <span data-ttu-id="8dc2f-109">設定服務回應訊息回到原始的傳送合作對象路線。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-109">Configure the itinerary to return the service response message to the original sending party.</span></span>  
  
-   <span data-ttu-id="8dc2f-110">測試使用路線測試用戶端範例應用程式的路線。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-110">Test the itinerary using the Itinerary Test Client sample application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8dc2f-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="8dc2f-111">Prerequisites</span></span>  
 <span data-ttu-id="8dc2f-112">在此 「 如何 」 主題中的程序需要完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-112">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="steps"></a><span data-ttu-id="8dc2f-113">步驟</span><span class="sxs-lookup"><span data-stu-id="8dc2f-113">Steps</span></span>  
  
#### <a name="to-create-an-esb-itinerary-dsl-model"></a><span data-ttu-id="8dc2f-114">若要建立 ESB 路線 DSL 模型</span><span class="sxs-lookup"><span data-stu-id="8dc2f-114">To create an ESB itinerary DSL model</span></span>  
  
1.  <span data-ttu-id="8dc2f-115">在 Visual Studio 中開啟 C:\HowTos\Patterns\Patterns.sln。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-115">In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="8dc2f-116">在 方案總管 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下 **新的行程**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-116">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="8dc2f-117">在**加入新項目**對話方塊中，於**名稱**方塊中，輸入**RequestResponse**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-117">In the **Add New Item** dialog box, in the **Name** box, type **RequestResponse**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a><span data-ttu-id="8dc2f-118">若要設定的路線屬性</span><span class="sxs-lookup"><span data-stu-id="8dc2f-118">To configure the properties of the itinerary</span></span>  
  
1.  <span data-ttu-id="8dc2f-119">在 Visual Studio 中，按一下設計介面的**RequestResponse.itinerary**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-119">In Visual Studio, click the design surface of **RequestResponse.itinerary**.</span></span> <span data-ttu-id="8dc2f-120">在**RequestResponse**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="8dc2f-120">In the **RequestResponse** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="8dc2f-121">在**為要求回應**下拉式清單中，按一下  **True**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-121">In the **Is Request Response** drop-down list, click **True**.</span></span>  
  
    2.  <span data-ttu-id="8dc2f-122">在**模型匯出工具**下拉式清單中，按一下  **XML 路線匯出工具**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-122">In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.</span></span>  
  
    3.  <span data-ttu-id="8dc2f-123">在**Extender 設定**區段中，旁邊**路線 XML 檔案**屬性，按一下省略符號按鈕 （...）。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-123">In the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).</span></span>  
  
    4.  <span data-ttu-id="8dc2f-124">在**選取 XML 檔案**對話方塊中，於**檔案名稱**方塊中，輸入**C:\HowTos\Itineraries\RequestResponse**，然後按一下 **儲存**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-124">In the **Select XML File** dialog box, in the **File name** box, type **C:\HowTos\Itineraries\RequestResponse**, and then click **Save**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="8dc2f-125">這個步驟可讓您匯出成 XML 的路線，到本機檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-125">This step enables you to export the itinerary as XML to a local file location.</span></span> <span data-ttu-id="8dc2f-126">藉由將行程至本機檔案的位置，而不匯出至路線的資料庫，可讓測試使用 ESB 測試用戶端應用程式的路線。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-126">By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application.</span></span> <span data-ttu-id="8dc2f-127">您將完成此程序，稍後在本使用說明主題。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-127">You will complete this process later in this How-to topic.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="8dc2f-128">若要定義路線結構</span><span class="sxs-lookup"><span data-stu-id="8dc2f-128">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="8dc2f-129">從 [工具箱] 拖曳**上手**至設計介面的模型項目。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-129">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="8dc2f-130">在**OnRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="8dc2f-130">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="8dc2f-131">按一下**名稱**屬性，，然後輸入**ReceiveNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-131">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="8dc2f-132">在**Extender**下拉式清單中，按一下 **上手 ESB Extender**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-132">In the **Extender** drop-down list, click **On-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="8dc2f-133">在**BizTalk 應用程式**下拉式清單中，按一下  **Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-133">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="8dc2f-134">在**接收埠**下拉式清單中，按一下  **OnRamp.Itinerary.Response**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-134">In the **Receive Port** drop-down list, click **OnRamp.Itinerary.Response**.</span></span>  
  
2.  <span data-ttu-id="8dc2f-135">從 [工具箱] 拖曳**路線服務**模型項目至設計介面，然後再將它放右邊的**上手**模型項目。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-135">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it to the right of the **On-Ramp** model element.</span></span> <span data-ttu-id="8dc2f-136">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="8dc2f-136">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="8dc2f-137">按一下**名稱**屬性，，然後輸入**MapNAOrderToCNOrder**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-137">Click the **Name** property, and then type **MapNAOrderToCNOrder**.</span></span>  
  
    2.  <span data-ttu-id="8dc2f-138">在**路線服務的擴充項**下拉式清單中，按一下 **傳訊 Extender**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-138">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="8dc2f-139">這個屬性會定義程序將需要 (messaging) 在管線中的位置。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-139">This property defines that the process will take place in a pipeline (messaging).</span></span> <span data-ttu-id="8dc2f-140">或者，如果處理程序，就會進行協調流程中，設定**路線服務的擴充項**屬性**協調流程 Extender**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-140">Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Extender**.</span></span>  
  
    3.  <span data-ttu-id="8dc2f-141">在**容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-141">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="8dc2f-142">在**服務名稱**下拉式清單中，按一下  **Microsoft.Practices.ESB.Services.Transform**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-142">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Transform**.</span></span>  
  
3.  <span data-ttu-id="8dc2f-143">以滑鼠右鍵按一下**解析程式**集合**MapNAOrderToCNOrder**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-143">Right-click the **Resolver** collection of the **MapNAOrderToCNOrder** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="8dc2f-144">在**Resolver1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="8dc2f-144">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="8dc2f-145">按一下**名稱**屬性，，然後輸入**StaticallySpecifyTheMap**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-145">Click the **Name** property, and then type **StaticallySpecifyTheMap**.</span></span>  
  
    2.  <span data-ttu-id="8dc2f-146">在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-146">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="8dc2f-147">在**轉換類型**下拉式清單中，按一下  **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-147">In the **Transform Type** drop-down list, click **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**.</span></span>  
  
4.  <span data-ttu-id="8dc2f-148">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-148">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="8dc2f-149">拖曳連接**ReceiveNAOrder**模型項目的**MapNAOrderToCNOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-149">Drag a connection from the **ReceiveNAOrder** model element to the **MapNAOrderToCNOrder** model element.</span></span>  
  
5.  <span data-ttu-id="8dc2f-150">從 [工具箱] 拖曳**路線服務**模型項目至設計介面，然後再將它放右邊的**MapNAOrderToCNOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-150">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it to the right of the **MapNAOrderToCNOrder** model element.</span></span> <span data-ttu-id="8dc2f-151">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="8dc2f-151">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="8dc2f-152">按一下**名稱**屬性，，然後輸入**RouteToCNService**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-152">Click the **Name** property, and then type **RouteToCNService**.</span></span>  
  
    2.  <span data-ttu-id="8dc2f-153">在**路線服務的擴充項**下拉式清單中，按一下 **傳訊 Extender**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-153">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="8dc2f-154">這個屬性會定義程序將需要 (messaging) 在管線中的位置。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-154">This property defines that the process will take place in a pipeline (messaging).</span></span> <span data-ttu-id="8dc2f-155">或者，如果處理程序，就會進行協調流程中，設定**路線服務的擴充項**屬性**協調流程 Extender**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-155">Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Extender**.</span></span>  
  
    3.  <span data-ttu-id="8dc2f-156">在**容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-156">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="8dc2f-157">在**服務名稱**下拉式清單中，按一下  **Microsoft.Practices.ESB.Services.Routing**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-157">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**.</span></span>  
  
6.  <span data-ttu-id="8dc2f-158">以滑鼠右鍵按一下**解析程式**集合**RouteToCNService**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-158">Right-click the **Resolver** collection of the **RouteToCNService** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="8dc2f-159">在**Resolver1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="8dc2f-159">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="8dc2f-160">按一下**名稱**屬性，，然後輸入**StaticallySpecifyTheService**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-160">Click the **Name** property, and then type **StaticallySpecifyTheService**.</span></span>  
  
    2.  <span data-ttu-id="8dc2f-161">在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-161">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="8dc2f-162">在**傳輸名稱**下拉式清單中，按一下  **Wcf-basichttp**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-162">In the **Transport Name** drop-down list, click **WCF-BasicHttp**.</span></span>  
  
    4.  <span data-ttu-id="8dc2f-163">按一下**傳輸位置**屬性，，然後輸入**http://localhost/ESB.CanadianServices/SubmitPOService.asmx**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-163">Click the **Transport Location** property, and then type **http://localhost/ESB.CanadianServices/SubmitPOService.asmx**.</span></span>  
  
    5.  <span data-ttu-id="8dc2f-164">按一下**目標命名空間**屬性，，然後輸入**http://globalbank.esb.dynamicresolution.com/canadianservices**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-164">Click the **Target Namespace** property, and then type **http://globalbank.esb.dynamicresolution.com/canadianservices**.</span></span>  
  
    6.  <span data-ttu-id="8dc2f-165">按一下**動作**屬性，，然後輸入**submitOrder**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-165">Click the **Action** property, and then type **submitOrder**.</span></span>  
  
7.  <span data-ttu-id="8dc2f-166">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-166">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="8dc2f-167">拖曳連接**MapNAOrderToCNOrder**模型項目的**RouteToCNService**模型項目。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-167">Drag a connection from the **MapNAOrderToCNOrder** model element to the **RouteToCNService** model element.</span></span>  
  
8.  <span data-ttu-id="8dc2f-168">從 [工具箱] 拖曳**匝道**模型項目至設計介面，然後再將它放右邊的**RouteToCNService**模型項目。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-168">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **RouteToCNService** model element.</span></span> <span data-ttu-id="8dc2f-169">在**OffRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="8dc2f-169">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="8dc2f-170">按一下**名稱**屬性，，然後輸入**InvokeCNService**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-170">Click the **Name** property, and then type **InvokeCNService**.</span></span>  
  
    2.  <span data-ttu-id="8dc2f-171">在**Extender**下拉式清單中，按一下 **匝道 ESB Extender**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-171">In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="8dc2f-172">在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-172">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="8dc2f-173">在**傳送埠**下拉式清單中，按一下  **DynamicResolutionSolicitResp**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-173">In the **Send Port** drop-down list, click **DynamicResolutionSolicitResp**.</span></span>  
  
9. <span data-ttu-id="8dc2f-174">從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**RouteToCNService**模型項目和**InvokeCNService**模型項目。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-174">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **RouteToCNService** model element and the **InvokeCNService** model element.</span></span> <span data-ttu-id="8dc2f-175">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="8dc2f-175">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="8dc2f-176">按一下**名稱**屬性，，然後輸入**SendPortFilter**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-176">Click the **Name** property, and then type **SendPortFilter**.</span></span>  
  
    2.  <span data-ttu-id="8dc2f-177">在**路線服務的擴充項**下拉式清單中，按一下 **匝道 Extender**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-177">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="8dc2f-178">在**匝道**下拉式清單中，展開**InvokeCNService**，然後按一下 **傳送處理常式**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-178">In the **Off-Ramp** drop-down list, expand **InvokeCNService**, and then click **Send Handlers**.</span></span>  
  
10. <span data-ttu-id="8dc2f-179">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-179">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="8dc2f-180">拖曳連接**RouteToCNService**模型項目的**SendPortFilter**模型項目。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-180">Drag a connection from the **RouteToCNService** model element to the **SendPortFilter** model element.</span></span>  
  
11. <span data-ttu-id="8dc2f-181">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-181">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="8dc2f-182">拖曳連接**SendPortFilter**模型項目的**InvokeCNService**模型項目。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-182">Drag a connection from the **SendPortFilter** model element to the **InvokeCNService** model element.</span></span>  
  
12. <span data-ttu-id="8dc2f-183">以滑鼠右鍵按一下設計介面，然後按一下**驗證**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-183">Right-click the design surface, and then click **Validate**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8dc2f-184">路線驗證;您不需要連線匝道回到上遞增，以便將回應訊息傳送回提出要求的合作對象。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-184">The itinerary validates; it is not necessary to connect the off-ramp back to the on-ramp in order to send the response message back to the requesting party.</span></span> <span data-ttu-id="8dc2f-185">藉由使用雙向上手，最後的訊息會自動傳回到發出要求的合作對象。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-185">By using a two-way on-ramp, the final message is automatically returned to the requesting party.</span></span>  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a><span data-ttu-id="8dc2f-186">若要匯出的行程測試用戶端使用的模型</span><span class="sxs-lookup"><span data-stu-id="8dc2f-186">To export the model for use with the Itinerary Test Client</span></span>  
  
1.  <span data-ttu-id="8dc2f-187">在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**RequestResponse**路線，然後再按一下**匯出模型**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-187">In Visual Studio, right-click the design surface of the **RequestResponse** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8dc2f-188">在 Visual Studio 中，開啟路線的 XML 版本。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-188">The XML version of the itinerary opens in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="8dc2f-189">儲存專案的所有成品。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-189">Save all project artifacts.</span></span>  
  
3.  <span data-ttu-id="8dc2f-190">在 Windows 檔案總管，瀏覽至 C:\HowTos\Itineraries。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-190">In Windows Explorer, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="8dc2f-191">請注意您路線 XML (RequestResponse.xml) 建立。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-191">Notice the creation of your itinerary XML (RequestResponse.xml).</span></span>  
  
#### <a name="to-test-the-itinerary"></a><span data-ttu-id="8dc2f-192">若要測試路線</span><span class="sxs-lookup"><span data-stu-id="8dc2f-192">To test the itinerary</span></span>  
  
1.  <span data-ttu-id="8dc2f-193">開啟路線測試用戶端範例應用程式使用期間建立的捷徑[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)(C:\HowTos\ESB。Itinerary.Test.exe-捷徑)。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-193">Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).</span></span>  
  
2.  <span data-ttu-id="8dc2f-194">在路線測試用戶端中，清除**使用 WCF 服務**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-194">In the Itinerary Test Client, clear the **Use WCF Service** check box.</span></span>  
  
3.  <span data-ttu-id="8dc2f-195">在**Web 服務選項**區段中，選取**兩個方式服務**核取方塊，然後**負載路線**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-195">In the **Web Service Options** section, select the **Two Way Service** check box, and then click **Load Itinerary**.</span></span>  
  
4.  <span data-ttu-id="8dc2f-196">在**開啟路線檔案**對話方塊中，瀏覽至 C:\HowTos\Itineraries。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-196">In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="8dc2f-197">選取**RequestResponse.xml**，然後按一下 **開啟**載入路線。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-197">Select **RequestResponse.xml**, and then click **Open** to load the itinerary.</span></span>  
  
5.  <span data-ttu-id="8dc2f-198">按一下**確定**清除**路線成功載入**訊息。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-198">Click **OK** to clear the **Itinerary Loaded Successfully** message.</span></span>  
  
6.  <span data-ttu-id="8dc2f-199">在路線測試用戶端中，按一下旁邊的省略符號按鈕 （...）**載入訊息**方塊。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-199">In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.</span></span>  
  
7.  <span data-ttu-id="8dc2f-200">在**選取要載入的 XML 文件**對話方塊中，瀏覽至 C:\HowTos。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-200">In the **Select XML Document to load** dialog box, browse to C:\HowTos.</span></span> <span data-ttu-id="8dc2f-201">選取**NAOrderDoc.xml**，然後按一下 **開啟**載入測試訊息。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-201">Select **NAOrderDoc.xml**, and then click **Open** to load the test message.</span></span>  
  
8.  <span data-ttu-id="8dc2f-202">按一下**送出要求** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-202">Click the **Submit Request** button.</span></span> <span data-ttu-id="8dc2f-203">測試完成時，按一下**確定**解除顯示的確認。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-203">When the test completes, click **OK** to dismiss the confirmation that appears.</span></span>  
  
9. <span data-ttu-id="8dc2f-204">在**結果**方塊中，注意到訊息的根節點是**submitOrderResponse**和預設命名空間是...**canadianservices**。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-204">In the **Results** box, notice the message's root node is **submitOrderResponse** and the default namespace is ... **canadianservices**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8dc2f-205">如果回應訊息需要其他轉換之前，回應會傳送到提出要求的合作對象，您必須使用包含 ESB 轉寄站元件的管線。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-205">If the response message requires additional transformation before the response is sent to the requesting party, you must use a pipeline that contains the ESB Forwarder component.</span></span> <span data-ttu-id="8dc2f-206">如需這項功能的範例，請參閱[安裝及執行多個 Web 服務範例](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="8dc2f-206">For an example of this functionality, see the [Installing and Running the Multiple Web Services Sample](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md).</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="8dc2f-207">其他資源</span><span class="sxs-lookup"><span data-stu-id="8dc2f-207">Additional Resources</span></span>  
 <span data-ttu-id="8dc2f-208">如需詳細資訊，請參閱下列相關主題：</span><span class="sxs-lookup"><span data-stu-id="8dc2f-208">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="8dc2f-209">如何：轉換訊息，並使用路線傳閱名單將產生的訊息路由至檔案位置</span><span class="sxs-lookup"><span data-stu-id="8dc2f-209">How to: Transform a Message and Route the Resulting Message to a File Location Using an Itinerary Routing Slip</span></span>](../esb-toolkit/transform-message-and-route-the-message-to-a-location-using-itinerary-routing.md)  
  
-   [<span data-ttu-id="8dc2f-210">開發活動</span><span class="sxs-lookup"><span data-stu-id="8dc2f-210">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="8dc2f-211">訊息路由模式</span><span class="sxs-lookup"><span data-stu-id="8dc2f-211">Message Routing Patterns</span></span>](../esb-toolkit/message-routing-patterns.md)  
  
-   [<span data-ttu-id="8dc2f-212">安裝和執行多個 Web 服務範例</span><span class="sxs-lookup"><span data-stu-id="8dc2f-212">Installing and Running the Multiple Web Services Sample</span></span>](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md)