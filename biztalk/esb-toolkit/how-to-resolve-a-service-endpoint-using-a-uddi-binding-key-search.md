---
title: 如何： 解決使用繫結機碼搜尋 UDDI 服務端點 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a685641-2beb-4153-a9ba-c766679ce48e
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d286f3dd48daa7cc0ddd16f4abda601cf9e8a5f7
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26010559"
---
# <a name="how-to-resolve-a-service-endpoint-using-a-uddi-binding-key-search"></a><span data-ttu-id="2256a-102">如何： 解決使用繫結機碼搜尋 UDDI 服務端點</span><span class="sxs-lookup"><span data-stu-id="2256a-102">How to: Resolve a Service Endpoint Using a UDDI Binding Key Search</span></span>
## <a name="goal"></a><span data-ttu-id="2256a-103">目標</span><span class="sxs-lookup"><span data-stu-id="2256a-103">Goal</span></span>  
 <span data-ttu-id="2256a-104">本節示範如何使用 ESB 設計工具的特定領域語言 (DSL) 來建立行程型路由名單使用 「 通用描述、 探索與整合 (UDDI) 3 找出使用繫結索引鍵之服務端點的解析程式搜尋。</span><span class="sxs-lookup"><span data-stu-id="2256a-104">This section demonstrates how to use the ESB Designer domain-specific language (DSL) to create an itinerary-based routing slip that uses the Universal Description, Discovery, and Integration (UDDI) 3 resolver to locate a service endpoint using a binding key search.</span></span> <span data-ttu-id="2256a-105">在此案例中，服務端點會在 UDDI 中發行檔案端點。</span><span class="sxs-lookup"><span data-stu-id="2256a-105">In this scenario, the service endpoint will be a file endpoint published in UDDI.</span></span>  
  
 <span data-ttu-id="2256a-106">在此 「 如何 」 主題，您將完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="2256a-106">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="2256a-107">建立路由的路線名單，若要解決服務端點。</span><span class="sxs-lookup"><span data-stu-id="2256a-107">Create an itinerary routing slip to resolve a service endpoint.</span></span>  
  
-   <span data-ttu-id="2256a-108">設定將訊息路由至服務端點使用的 UDDI 3 解析程式路線。</span><span class="sxs-lookup"><span data-stu-id="2256a-108">Configure the itinerary to route the message to a service endpoint using a UDDI 3 resolver.</span></span>  
  
-   <span data-ttu-id="2256a-109">測試使用路線測試用戶端範例應用程式的路線。</span><span class="sxs-lookup"><span data-stu-id="2256a-109">Test the itinerary using the Itinerary Test Client sample application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2256a-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="2256a-110">Prerequisites</span></span>  
 <span data-ttu-id="2256a-111">在此 「 如何 」 主題中的程序需要完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="2256a-111">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="steps"></a><span data-ttu-id="2256a-112">步驟</span><span class="sxs-lookup"><span data-stu-id="2256a-112">Steps</span></span>  
  
#### <a name="to-create-an-itinerary-model"></a><span data-ttu-id="2256a-113">若要建立路線的模型</span><span class="sxs-lookup"><span data-stu-id="2256a-113">To create an itinerary model</span></span>  
  
1.  <span data-ttu-id="2256a-114">在 Visual Studio 中開啟 C:\HowTos\Patterns\Patterns.sln。</span><span class="sxs-lookup"><span data-stu-id="2256a-114">In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="2256a-115">在 方案總管 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下 **新的行程**。</span><span class="sxs-lookup"><span data-stu-id="2256a-115">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="2256a-116">在**加入新項目**對話方塊中，於**名稱**方塊中，輸入**UDDI3BindingKeySearch**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="2256a-116">In the **Add New Item** dialog box, in the **Name** box, type **UDDI3BindingKeySearch**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a><span data-ttu-id="2256a-117">若要設定的路線屬性</span><span class="sxs-lookup"><span data-stu-id="2256a-117">To configure the properties of the itinerary</span></span>  
  
1.  <span data-ttu-id="2256a-118">在 Visual Studio 中，按一下設計介面的**UDDI3BindingKeySearch.itinerary**。</span><span class="sxs-lookup"><span data-stu-id="2256a-118">In Visual Studio, click the design surface of **UDDI3BindingKeySearch.itinerary**.</span></span> <span data-ttu-id="2256a-119">在**UDDI3BindingKeySearch**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="2256a-119">In the **UDDI3BindingKeySearch** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="2256a-120">在**模型匯出工具**下拉式清單中，按一下  **XML 路線匯出工具**。</span><span class="sxs-lookup"><span data-stu-id="2256a-120">In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="2256a-121">下**Extender 設定**區段中，旁邊**路線 XML 檔案**屬性中，按一下省略符號按鈕 （...）。</span><span class="sxs-lookup"><span data-stu-id="2256a-121">Under the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).</span></span>  
  
    3.  <span data-ttu-id="2256a-122">在**選取 XML 檔案** 對話方塊中，輸入**C:\HowTos\Itineraries\UDDI3BindingKeySearch**中**檔案名稱**方塊，然後再按一下**儲存**.</span><span class="sxs-lookup"><span data-stu-id="2256a-122">In the **Select XML File** dialog box, type **C:\HowTos\Itineraries\UDDI3BindingKeySearch** in the **File name** box, and then click **Save**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="2256a-123">這個步驟可讓您匯出成 XML 的路線，到本機檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="2256a-123">This step enables you to export the itinerary as XML to a local file location.</span></span> <span data-ttu-id="2256a-124">藉由將行程至本機檔案的位置，而不匯出至路線的資料庫，可讓測試使用 ESB 測試用戶端應用程式的路線。</span><span class="sxs-lookup"><span data-stu-id="2256a-124">By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application.</span></span> <span data-ttu-id="2256a-125">您將完成此程序，稍後在本使用說明主題。</span><span class="sxs-lookup"><span data-stu-id="2256a-125">You will complete this process later in this How-to topic.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="2256a-126">若要定義路線結構</span><span class="sxs-lookup"><span data-stu-id="2256a-126">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="2256a-127">從 [工具箱] 拖曳**上手**至設計介面的模型項目。</span><span class="sxs-lookup"><span data-stu-id="2256a-127">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="2256a-128">在**OnRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="2256a-128">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="2256a-129">按一下**名稱**屬性，，然後輸入**ReceiveNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="2256a-129">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="2256a-130">在**Extender**下拉式清單中，按一下 **上手 ESB Extender**。</span><span class="sxs-lookup"><span data-stu-id="2256a-130">In the **Extender** drop-down list, click **On-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="2256a-131">在**BizTalk 應用程式**下拉式清單中，按一下  **Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="2256a-131">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="2256a-132">在**接收埠**下拉式清單中，按一下  **OnRamp.Itinerary**。</span><span class="sxs-lookup"><span data-stu-id="2256a-132">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="2256a-133">從 [工具箱] 拖曳**路線服務**至設計介面的模型項目。</span><span class="sxs-lookup"><span data-stu-id="2256a-133">From the Toolbox, drag an **Itinerary Service** model element to the design surface.</span></span> <span data-ttu-id="2256a-134">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="2256a-134">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="2256a-135">按一下**名稱**屬性，，然後輸入**BindingKeyRoute**。</span><span class="sxs-lookup"><span data-stu-id="2256a-135">Click the **Name** property, and then type **BindingKeyRoute**.</span></span>  
  
    2.  <span data-ttu-id="2256a-136">在**路線服務的擴充項**下拉式清單中，按一下 **傳訊 Extender**。</span><span class="sxs-lookup"><span data-stu-id="2256a-136">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  
  
    3.  <span data-ttu-id="2256a-137">在**容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。</span><span class="sxs-lookup"><span data-stu-id="2256a-137">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="2256a-138">在**服務名稱**下拉式清單中，按一下  **Microsoft.Practices.ESB.Services.Routing**。</span><span class="sxs-lookup"><span data-stu-id="2256a-138">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**.</span></span>  
  
3.  <span data-ttu-id="2256a-139">以滑鼠右鍵按一下**解析程式**集合**BindingKeyRoute**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="2256a-139">Right-click the **Resolver** collection of the **BindingKeyRoute** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="2256a-140">在**Resolver1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="2256a-140">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="2256a-141">按一下**名稱**屬性，，然後輸入**BindingKeySearch**。</span><span class="sxs-lookup"><span data-stu-id="2256a-141">Click the **Name** property, and then type **BindingKeySearch**.</span></span>  
  
    2.  <span data-ttu-id="2256a-142">在**解析程式實作**下拉式清單中，按一下  **Uddi3 解析程式擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="2256a-142">In the **Resolver Implementation** drop-down list, click **Uddi3 Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="2256a-143">在**解析程式 Moniker**下拉式清單中，按一下  **UDDI3**。</span><span class="sxs-lookup"><span data-stu-id="2256a-143">In the **Resolver Moniker** drop-down list, click **UDDI3**.</span></span>  
  
    4.  <span data-ttu-id="2256a-144">按一下**繫結索引鍵**屬性，，然後輸入**uddi:esb:orderfileservicev3.1**。</span><span class="sxs-lookup"><span data-stu-id="2256a-144">Click the **Binding key** property, and then type **uddi:esb:orderfileservicev3.1**.</span></span>  
  
4.  <span data-ttu-id="2256a-145">以滑鼠右鍵按一下**BindingKeySearch**解析程式，然後再按一下**測試解析程式組態**。</span><span class="sxs-lookup"><span data-stu-id="2256a-145">Right-click the **BindingKeySearch** resolver, and then click **Test Resolver Configuration**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2256a-146">確認 [輸出] 視窗中顯示的輸出。</span><span class="sxs-lookup"><span data-stu-id="2256a-146">Verify the output displayed in the Output window.</span></span>  
  
5.  <span data-ttu-id="2256a-147">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="2256a-147">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="2256a-148">拖曳連接**ReceiveNAOrder**模型項目的**BindingKeyRoute**模型項目。</span><span class="sxs-lookup"><span data-stu-id="2256a-148">Drag a connection from the **ReceiveNAOrder** model element to the **BindingKeyRoute** model element.</span></span>  
  
6.  <span data-ttu-id="2256a-149">從 [工具箱] 拖曳**匝道**模型項目至設計介面，然後再將它放右邊的**BindingKeyRoute**模型項目。</span><span class="sxs-lookup"><span data-stu-id="2256a-149">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **BindingKeyRoute** model element.</span></span> <span data-ttu-id="2256a-150">在**OffRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="2256a-150">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="2256a-151">按一下**名稱**屬性，，然後輸入**SendNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="2256a-151">Click the **Name** property, and then type **SendNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="2256a-152">在**Extender**下拉式清單中，按一下 **匝道 ESB Extender**。</span><span class="sxs-lookup"><span data-stu-id="2256a-152">In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="2256a-153">在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。</span><span class="sxs-lookup"><span data-stu-id="2256a-153">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="2256a-154">在**傳送埠**下拉式清單中，按一下  **DynamicResolutionOneWay**。</span><span class="sxs-lookup"><span data-stu-id="2256a-154">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
7.  <span data-ttu-id="2256a-155">從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**BindingKeyRoute**模型項目和**SendNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="2256a-155">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **BindingKeyRoute** model element and the **SendNAOrder** model element.</span></span> <span data-ttu-id="2256a-156">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="2256a-156">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="2256a-157">按一下**名稱**屬性，，然後輸入**SendPortFilter**。</span><span class="sxs-lookup"><span data-stu-id="2256a-157">Click the **Name** property, and then type **SendPortFilter**.</span></span>  
  
    2.  <span data-ttu-id="2256a-158">在**路線服務的擴充項**下拉式清單中，按一下 **匝道 Extender**。</span><span class="sxs-lookup"><span data-stu-id="2256a-158">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="2256a-159">在**匝道**下拉式清單中，展開**SendNAOrder**，然後按一下 **傳送處理常式**。</span><span class="sxs-lookup"><span data-stu-id="2256a-159">In the **Off-Ramp** drop-down list, expand **SendNAOrder**, and then click **Send Handlers**.</span></span>  
  
8.  <span data-ttu-id="2256a-160">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="2256a-160">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="2256a-161">拖曳連接**BindingKeyRoute**模型項目的**SendPortFilter**模型項目。</span><span class="sxs-lookup"><span data-stu-id="2256a-161">Drag a connection from the **BindingKeyRoute** model element to the **SendPortFilter** model element.</span></span>  
  
9. <span data-ttu-id="2256a-162">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="2256a-162">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="2256a-163">拖曳連接**SendPortFilter**模型項目的**SendNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="2256a-163">Drag a connection from the **SendPortFilter** model element to the **SendNAOrder** model element.</span></span>  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a><span data-ttu-id="2256a-164">若要匯出的行程測試用戶端使用的模型</span><span class="sxs-lookup"><span data-stu-id="2256a-164">To export the model for use with the Itinerary Test Client</span></span>  
  
1.  <span data-ttu-id="2256a-165">在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**UDDI3BindingKeySearch**路線，然後再按一下**匯出模型**。</span><span class="sxs-lookup"><span data-stu-id="2256a-165">In Visual Studio, right-click the design surface of the **UDDI3BindingKeySearch** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2256a-166">在 Visual Studio 中，開啟路線的 XML 版本。</span><span class="sxs-lookup"><span data-stu-id="2256a-166">The XML version of the itinerary opens in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="2256a-167">儲存專案的所有成品。</span><span class="sxs-lookup"><span data-stu-id="2256a-167">Save all project artifacts.</span></span>  
  
3.  <span data-ttu-id="2256a-168">在 Windows 檔案總管，瀏覽至 C:\HowTos\Itineraries 並注意您路線 XML (UDDI3BindingKeySearch.xml) 建立。</span><span class="sxs-lookup"><span data-stu-id="2256a-168">In Windows Explorer, browse to C:\HowTos\Itineraries and notice the creation of your itinerary XML (UDDI3BindingKeySearch.xml).</span></span>  
  
#### <a name="to-test-the-itinerary"></a><span data-ttu-id="2256a-169">若要測試路線</span><span class="sxs-lookup"><span data-stu-id="2256a-169">To test the itinerary</span></span>  
  
1.  <span data-ttu-id="2256a-170">開啟路線測試用戶端範例應用程式使用期間建立的捷徑[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)(C:\HowTos\ESB。Itinerary.Test.exe-捷徑)。</span><span class="sxs-lookup"><span data-stu-id="2256a-170">Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).</span></span>  
  
2.  <span data-ttu-id="2256a-171">在路線測試用戶端中，清除**使用 WCF 服務**核取方塊，然後**負載路線**。</span><span class="sxs-lookup"><span data-stu-id="2256a-171">In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.</span></span>  
  
3.  <span data-ttu-id="2256a-172">在 [開啟路線檔案] 對話方塊中，瀏覽至 C:\HowTos\Itineraries。</span><span class="sxs-lookup"><span data-stu-id="2256a-172">In the Open Itinerary File dialog box, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="2256a-173">選取 UDDI3BindingKeySearch.xml，，然後按一下 [開啟] 以載入路線。</span><span class="sxs-lookup"><span data-stu-id="2256a-173">Select UDDI3BindingKeySearch.xml, and then click Open to load the itinerary.</span></span>  
  
4.  <span data-ttu-id="2256a-174">按一下**確定**清除**路線成功載入**訊息。</span><span class="sxs-lookup"><span data-stu-id="2256a-174">Click **OK** to clear the **Itinerary Loaded Successfully** message.</span></span>  
  
5.  <span data-ttu-id="2256a-175">在路線測試用戶端中，按一下旁邊的省略符號按鈕 （...）**載入訊息**方塊。</span><span class="sxs-lookup"><span data-stu-id="2256a-175">In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.</span></span>  
  
6.  <span data-ttu-id="2256a-176">在**選取要載入的 XML 文件**對話方塊中，瀏覽至 C:\HowTos。</span><span class="sxs-lookup"><span data-stu-id="2256a-176">In the **Select XML Document to load** dialog box, browse to C:\HowTos.</span></span> <span data-ttu-id="2256a-177">選取**NAOrderDoc.xml**，然後按一下 **開啟**載入測試訊息。</span><span class="sxs-lookup"><span data-stu-id="2256a-177">Select **NAOrderDoc.xml**, and then click **Open** to load the test message.</span></span>  
  
7.  <span data-ttu-id="2256a-178">按一下**送出要求** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="2256a-178">Click the **Submit Request** button.</span></span> <span data-ttu-id="2256a-179">測試完成時，按一下**確定**解除顯示的確認。</span><span class="sxs-lookup"><span data-stu-id="2256a-179">When the test completes, click **OK** to dismiss the confirmation that appears.</span></span>  
  
8.  <span data-ttu-id="2256a-180">在 Windows 檔案總管，瀏覽至 C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Test\Filedrop\Out。請確認 %MessageID%.xml 訊息已寫入至目錄。</span><span class="sxs-lookup"><span data-stu-id="2256a-180">In Windows Explorer, browse to C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Test\Filedrop\Out. Verify that the %MessageID%.xml message has been written to the directory.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="2256a-181">其他資源</span><span class="sxs-lookup"><span data-stu-id="2256a-181">Additional Resources</span></span>  
 <span data-ttu-id="2256a-182">如需詳細資訊，請參閱下列相關主題：</span><span class="sxs-lookup"><span data-stu-id="2256a-182">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="2256a-183">如何：使用 UDDI 類別搜尋解決服務端點</span><span class="sxs-lookup"><span data-stu-id="2256a-183">How to: Resolve a Service Endpoint Using a UDDI Category Search</span></span>](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-category-search.md)  
  
-   [<span data-ttu-id="2256a-184">開發活動</span><span class="sxs-lookup"><span data-stu-id="2256a-184">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="2256a-185">使用動態解析和路由</span><span class="sxs-lookup"><span data-stu-id="2256a-185">Using Dynamic Resolution and Routing</span></span>](../esb-toolkit/using-dynamic-resolution-and-routing.md)