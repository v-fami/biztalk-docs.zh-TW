---
title: "如何： 將單一訊息路由至多個收件者使用路線路由名單 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42c30493-4fe1-4fd5-8bc7-af091535b091
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fa96603bc93c9d5d19ef102695a1189a50d00ac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-route-a-single-message-to-multiple-recipients-using-an-itinerary-routing-slip"></a><span data-ttu-id="fcc1a-102">如何： 將單一訊息路由至多個收件者使用路線路由名單</span><span class="sxs-lookup"><span data-stu-id="fcc1a-102">How to: Route a Single Message to Multiple Recipients Using an Itinerary Routing Slip</span></span>
## <a name="goal"></a><span data-ttu-id="fcc1a-103">目標</span><span class="sxs-lookup"><span data-stu-id="fcc1a-103">Goal</span></span>  
 <span data-ttu-id="fcc1a-104">本節示範如何使用設計工具的特定領域語言 (DSL) 來建立將訊息傳送行程給三個的相異收件者使用靜態的解析程式和[!INCLUDE[prague](../includes/prague-md.md)]FILE 配接器。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-104">This section demonstrates how to use the Designer domain-specific language (DSL) to create an itinerary that routes a message to three distinct recipients using a static resolver and the [!INCLUDE[prague](../includes/prague-md.md)] FILE adapter.</span></span>  
  
 <span data-ttu-id="fcc1a-105">在此 「 如何 」 主題，您將完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="fcc1a-105">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="fcc1a-106">建立具有三個靜態的解析程式將訊息路由至多個收件者的路線。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-106">Create an itinerary with three static resolvers to route messages to multiple recipients.</span></span>  
  
-   <span data-ttu-id="fcc1a-107">測試使用路線測試用戶端範例應用程式的路線。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-107">Test the itinerary using the Itinerary Test Client sample application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fcc1a-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="fcc1a-108">Prerequisites</span></span>  
 <span data-ttu-id="fcc1a-109">在此 「 如何 」 主題中的程序需要完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-109">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="steps"></a><span data-ttu-id="fcc1a-110">步驟</span><span class="sxs-lookup"><span data-stu-id="fcc1a-110">Steps</span></span>  
  
#### <a name="to-create-an-esb-itinerary-dsl-model"></a><span data-ttu-id="fcc1a-111">若要建立 ESB 路線 DSL 模型</span><span class="sxs-lookup"><span data-stu-id="fcc1a-111">To create an ESB itinerary DSL model</span></span>  
  
1.  <span data-ttu-id="fcc1a-112">在[!INCLUDE[vs2010](../includes/vs2010-md.md)]，開啟 C:\HowTos\Patterns\Patterns.sln。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-112">In [!INCLUDE[vs2010](../includes/vs2010-md.md)], open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="fcc1a-113">在 方案總管 中，以滑鼠右鍵按一下**ItineraryLibrary**，指向 **新增**，然後按一下 **新的行程**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-113">In Solution Explorer, right-click **ItineraryLibrary**, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="fcc1a-114">在**加入新項目**對話方塊中，按一下  **ItineraryDsl**在範本窗格中。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-114">In the **Add New Item** dialog box, click **ItineraryDsl** in the Templates pane.</span></span>  
  
4.  <span data-ttu-id="fcc1a-115">在**名稱**方塊中，輸入**RecipientList**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-115">In the **Name** box, type **RecipientList**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a><span data-ttu-id="fcc1a-116">若要設定的路線屬性</span><span class="sxs-lookup"><span data-stu-id="fcc1a-116">To configure the properties of the itinerary</span></span>  
  
1.  <span data-ttu-id="fcc1a-117">在 Visual Studio 中，按一下 RecipientList.itinerary 的設計介面。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-117">In Visual Studio, click the design surface of RecipientList.itinerary.</span></span> <span data-ttu-id="fcc1a-118">在 [RecipientList 屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="fcc1a-118">In the RecipientList Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="fcc1a-119">在**模型匯出工具**下拉式清單中，按一下  **XML 路線匯出工具**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-119">In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="fcc1a-120">在**Extender 設定**區段中，旁邊**路線 XML 檔案**屬性，按一下省略符號按鈕 （...）。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-120">In the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).</span></span>  
  
    3.  <span data-ttu-id="fcc1a-121">在**選取 XML 檔案**對話方塊中，於**檔案名稱**方塊中，輸入**C:\HowTos\Itineraries\RecipientList**，然後按一下 **儲存**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-121">In the **Select XML File** dialog box, in the **File name** box, type **C:\HowTos\Itineraries\RecipientList**, and then click **Save**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="fcc1a-122">這個步驟可讓您匯出成 XML 的路線，到本機檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-122">This step enables you to export the itinerary as XML to a local file location.</span></span> <span data-ttu-id="fcc1a-123">藉由將行程至本機檔案的位置，而不匯出至路線的資料庫，可讓測試使用 ESB 測試用戶端應用程式的路線。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-123">By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application.</span></span> <span data-ttu-id="fcc1a-124">您將完成此程序，稍後在本使用說明主題。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-124">You will complete this process later in this How-to topic.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="fcc1a-125">若要定義路線結構</span><span class="sxs-lookup"><span data-stu-id="fcc1a-125">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="fcc1a-126">從 [工具箱] 拖曳**上手**至設計介面的模型項目。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-126">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="fcc1a-127">在**OnRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="fcc1a-127">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="fcc1a-128">按一下**名稱**屬性，，然後輸入**ReceiveNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-128">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="fcc1a-129">在**Extender**下拉式清單中，按一下 **上手 Extender**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-129">In the **Extender** drop-down list, click **On-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="fcc1a-130">在**BizTalk 應用程式**下拉式清單中，按一下  **Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-130">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="fcc1a-131">在**接收埠**下拉式清單中，按一下  **OnRamp.Itinerary**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-131">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="fcc1a-132">從 [工具箱] 拖曳**路線服務**模型項目至設計介面，然後再將它放右邊的**上手**模型項目。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-132">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it to the right of the **On-Ramp** model element.</span></span> <span data-ttu-id="fcc1a-133">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="fcc1a-133">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="fcc1a-134">按一下**名稱**屬性，，然後輸入**RouteToThreeRecipients**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-134">Click the **Name** property, and then type **RouteToThreeRecipients**.</span></span>  
  
    2.  <span data-ttu-id="fcc1a-135">在**路線服務的擴充項**下拉式清單中，按一下 **傳訊 Extender**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-135">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="fcc1a-136">這個屬性會定義程序將需要 (messaging) 在管線中的位置。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-136">This property defines that the process will take place in a pipeline (messaging).</span></span> <span data-ttu-id="fcc1a-137">或者，如果處理程序，就會進行協調流程中，設定**路線服務的擴充項**屬性**協調流程 Extender**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-137">Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Extender**.</span></span>  
  
    3.  <span data-ttu-id="fcc1a-138">在**容器**下拉式清單中，展開**ReceiveNaOrderDoc**，然後按一下 **接收處理常式**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-138">In the **Container** drop-down list, expand **ReceiveNaOrderDoc**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="fcc1a-139">在**服務名稱**下拉式清單中，按一下  **Microsoft.Practices.ESB.Services.Routing**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-139">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**.</span></span>  
  
3.  <span data-ttu-id="fcc1a-140">以滑鼠右鍵按一下**解析程式**集合**RouteToThreeRecipients**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-140">Right-click the **Resolver** collection of the **RouteToThreeRecipients** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="fcc1a-141">在**Resolver1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="fcc1a-141">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="fcc1a-142">按一下**名稱**屬性，，然後輸入**FirstResolver**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-142">Click the **Name** property, and then type **FirstResolver**.</span></span>  
  
    2.  <span data-ttu-id="fcc1a-143">在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-143">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="fcc1a-144">在**傳輸名稱**下拉式清單中，按一下 **檔案**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-144">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    4.  <span data-ttu-id="fcc1a-145">按一下**傳輸位置**屬性，，然後輸入**C:\HowTos\Out\First%MessageID%.xml**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-145">Click the **Transport Location** property, and then type **C:\HowTos\Out\First%MessageID%.xml**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="fcc1a-146">您已加入此路線服務的三個解決器的第一個。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-146">You have added the first of three resolvers for this itinerary service.</span></span> <span data-ttu-id="fcc1a-147">您現在要加入更多的兩個解析程式將訊息路由至其他收件者。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-147">You will now add two more resolvers to route the message to additional recipients.</span></span>  
  
4.  <span data-ttu-id="fcc1a-148">以滑鼠右鍵按一下**解析程式**集合**RouteToThreeRecipients**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-148">Right-click the **Resolver** collection of the **RouteToThreeRecipients** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="fcc1a-149">在**Resolver1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="fcc1a-149">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="fcc1a-150">按一下**名稱**屬性，，然後輸入**SecondResolver**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-150">Click the **Name** property, and then type **SecondResolver**.</span></span>  
  
    2.  <span data-ttu-id="fcc1a-151">在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-151">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="fcc1a-152">在**傳輸名稱**下拉式清單中，按一下 **檔案**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-152">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    4.  <span data-ttu-id="fcc1a-153">按一下**傳輸位置**屬性，，然後輸入**C:\HowTos\Out\Second%MessageID%.xml**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-153">Click the **Transport Location** property, and then type **C:\HowTos\Out\Second%MessageID%.xml**.</span></span>  
  
5.  <span data-ttu-id="fcc1a-154">以滑鼠右鍵按一下**解析程式**集合**RouteToThreeRecipients**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-154">Right-click the **Resolver** collection of the **RouteToThreeRecipients** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="fcc1a-155">在**Resolver1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="fcc1a-155">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="fcc1a-156">按一下**名稱**屬性，，然後輸入**ThirdResolver**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-156">Click the **Name** property, and then type **ThirdResolver**.</span></span>  
  
    2.  <span data-ttu-id="fcc1a-157">在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-157">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="fcc1a-158">在**傳輸名稱**下拉式清單中，按一下 **檔案**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-158">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    4.  <span data-ttu-id="fcc1a-159">按一下**傳輸位置**屬性，，然後輸入**C:\HowTos\Out\Third%MessageID%.xml**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-159">Click the **Transport Location** property, and then type **C:\HowTos\Out\Third%MessageID%.xml**.</span></span>  
  
6.  <span data-ttu-id="fcc1a-160">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-160">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="fcc1a-161">拖曳連接**ReceiveNAOrder**模型項目的**RouteToThreeRecipients**模型項目。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-161">Drag a connection from the **ReceiveNAOrder** model element to the **RouteToThreeRecipients** model element.</span></span>  
  
7.  <span data-ttu-id="fcc1a-162">從 [工具箱] 拖曳**匝道**模型項目至設計介面，然後再將它放右邊的**RouteToThreeRecipients**模型項目。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-162">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **RouteToThreeRecipients** model element.</span></span> <span data-ttu-id="fcc1a-163">在**OffRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="fcc1a-163">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="fcc1a-164">按一下**名稱**屬性，，然後輸入**SendThreeMessages**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-164">Click the **Name** property, and then type **SendThreeMessages**.</span></span>  
  
    2.  <span data-ttu-id="fcc1a-165">在**Extender**下拉式清單中，按一下 **匝道 ESB Extender**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-165">In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="fcc1a-166">在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-166">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="fcc1a-167">在**傳送埠**下拉式清單中，按一下  **DynamicResolutionOneWay**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-167">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
8.  <span data-ttu-id="fcc1a-168">從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**RouteToThreeRecipients**模型項目和**SendThreeMessages**模型項目。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-168">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **RouteToThreeRecipients** model element and the **SendThreeMessages** model element.</span></span> <span data-ttu-id="fcc1a-169">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="fcc1a-169">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="fcc1a-170">按一下**名稱**屬性，，然後輸入**SendPortFilter**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-170">Click the **Name** property, and then type **SendPortFilter**.</span></span>  
  
    2.  <span data-ttu-id="fcc1a-171">在**路線服務的擴充項**下拉式清單中，按一下 **匝道 Extender**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-171">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="fcc1a-172">在**匝道**下拉式清單中，展開**SendThreeMessages**，然後按一下 **傳送處理常式**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-172">In the **Off-Ramp** drop-down list, expand **SendThreeMessages**, and then click **Send Handlers**.</span></span>  
  
9. <span data-ttu-id="fcc1a-173">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-173">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="fcc1a-174">拖曳連接**RouteToThreeRecipients**模型項目的**SendPortFilter**模型項目。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-174">Drag a connection from the **RouteToThreeRecipients** model element to the **SendPortFilter** model element.</span></span>  
  
10. <span data-ttu-id="fcc1a-175">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-175">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="fcc1a-176">拖曳連接**SendPortFilter**模型項目的**SendThreeMessages**模型項目。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-176">Drag a connection from the **SendPortFilter** model element to the **SendThreeMessages** model element.</span></span>  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a><span data-ttu-id="fcc1a-177">若要匯出的行程測試用戶端使用的模型</span><span class="sxs-lookup"><span data-stu-id="fcc1a-177">To export the model for use with the Itinerary Test Client</span></span>  
  
1.  <span data-ttu-id="fcc1a-178">在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**RecipientList**路線，然後再按一下**匯出模型**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-178">In Visual Studio, right-click the design surface of the **RecipientList** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fcc1a-179">在 Visual Studio 中，開啟路線的 XML 版本。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-179">The XML version of the itinerary opens in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="fcc1a-180">儲存專案的所有成品。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-180">Save all project artifacts.</span></span>  
  
3.  <span data-ttu-id="fcc1a-181">在 Windows 檔案總管，瀏覽 C:\HowTos\Itineraries，並注意您路線 XML (RecipientList.xml) 建立。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-181">In Windows Explorer, browse to C:\HowTos\Itineraries, and then notice the creation of your itinerary XML (RecipientList.xml).</span></span>  
  
#### <a name="to-test-the-itinerary"></a><span data-ttu-id="fcc1a-182">若要測試路線</span><span class="sxs-lookup"><span data-stu-id="fcc1a-182">To test the itinerary</span></span>  
  
1.  <span data-ttu-id="fcc1a-183">開啟路線測試用戶端範例應用程式使用期間建立的捷徑[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)(C:\HowTos\ESB。Itinerary.Test.exe-捷徑)。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-183">Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).</span></span>  
  
2.  <span data-ttu-id="fcc1a-184">在路線測試用戶端中，清除**使用 WCF 服務**核取方塊，然後**負載路線**。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-184">In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.</span></span>  
  
3.  <span data-ttu-id="fcc1a-185">在**開啟路線檔案**對話方塊中，瀏覽至 C:\HowTos\Itineraries。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-185">In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="fcc1a-186">選取**RecipientList.xml**，然後按一下 **開啟**載入路線。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-186">Select **RecipientList.xml**, and then click **Open** to load the itinerary.</span></span>  
  
4.  <span data-ttu-id="fcc1a-187">按一下**確定**清除 「 路線成功載入： 訊息。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-187">Click **OK** to clear the "Itinerary Loaded Successfully: message.</span></span>  
  
5.  <span data-ttu-id="fcc1a-188">在路線測試用戶端中，按一下旁邊的省略符號按鈕 （...）**載入訊息**方塊。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-188">In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.</span></span>  
  
6.  <span data-ttu-id="fcc1a-189">在**選取要載入的 XML 文件**對話方塊中，瀏覽至 C:\Patterns。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-189">In the **Select XML Document to load** dialog box, browse to C:\Patterns.</span></span> <span data-ttu-id="fcc1a-190">選取 NAOrderDoc.xml，，然後按一下**開啟**載入測試訊息。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-190">Select NAOrderDoc.xml, and then click **Open** to load the test message.</span></span>  
  
7.  <span data-ttu-id="fcc1a-191">按一下**送出要求** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-191">Click the **Submit Request** button.</span></span> <span data-ttu-id="fcc1a-192">測試完成時，按一下**確定**解除顯示的確認。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-192">When the test completes, click **OK** to dismiss the confirmation that appears.</span></span>  
  
8.  <span data-ttu-id="fcc1a-193">在 Windows 檔案總管，瀏覽至 C:\HowTos\Out\\。</span><span class="sxs-lookup"><span data-stu-id="fcc1a-193">In Windows Explorer, browse to C:\HowTos\Out\\.</span></span> <span data-ttu-id="fcc1a-194">請確認下列訊息的已寫入到目錄：</span><span class="sxs-lookup"><span data-stu-id="fcc1a-194">Verify that the following messages have been written to the directory:</span></span>  
  
    -   <span data-ttu-id="fcc1a-195">First%MessageID%.xml</span><span class="sxs-lookup"><span data-stu-id="fcc1a-195">First%MessageID%.xml</span></span>  
  
    -   <span data-ttu-id="fcc1a-196">Second%MessageID%.xml</span><span class="sxs-lookup"><span data-stu-id="fcc1a-196">Second%MessageID%.xml</span></span>  
  
    -   <span data-ttu-id="fcc1a-197">Third%MessageID%.xml</span><span class="sxs-lookup"><span data-stu-id="fcc1a-197">Third%MessageID%.xml</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="fcc1a-198">其他資源</span><span class="sxs-lookup"><span data-stu-id="fcc1a-198">Additional Resources</span></span>  
 <span data-ttu-id="fcc1a-199">如需詳細資訊，請參閱下列相關主題：</span><span class="sxs-lookup"><span data-stu-id="fcc1a-199">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="fcc1a-200">開發活動</span><span class="sxs-lookup"><span data-stu-id="fcc1a-200">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="fcc1a-201">訊息的路由模式</span><span class="sxs-lookup"><span data-stu-id="fcc1a-201">Message Routing Patterns</span></span>](../esb-toolkit/message-routing-patterns.md)  
  
-   [<span data-ttu-id="fcc1a-202">使用動態解析和路由</span><span class="sxs-lookup"><span data-stu-id="fcc1a-202">Using Dynamic Resolution and Routing</span></span>](../esb-toolkit/using-dynamic-resolution-and-routing.md)