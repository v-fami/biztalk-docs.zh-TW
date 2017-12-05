---
title: "如何： 解決使用 UDDI 類別目錄搜尋之服務端點 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61ac5d37-5529-4509-a948-415453944e01
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 207c50c8f2dc61c0e7e86f865fec470dae4d2e84
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-resolve-a-service-endpoint-using-a-uddi-category-search"></a><span data-ttu-id="d2bd0-102">如何： 解決使用 UDDI 類別目錄搜尋之服務端點</span><span class="sxs-lookup"><span data-stu-id="d2bd0-102">How to: Resolve a Service Endpoint Using a UDDI Category Search</span></span>
## <a name="goal"></a><span data-ttu-id="d2bd0-103">目標</span><span class="sxs-lookup"><span data-stu-id="d2bd0-103">Goal</span></span>  
 <span data-ttu-id="d2bd0-104">本節示範如何使用 ESB 設計工具的特定領域語言 (DSL) 來建立行程型路由名單使用 「 通用描述、 探索與整合 (UDDI) 3 解析程式找到服務端點使用類別目錄搜尋。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-104">This section demonstrates how to use the ESB Designer domain-specific language (DSL) to create an itinerary-based routing slip that uses the Universal Description, Discovery, and Integration (UDDI) 3 resolver to locate a service endpoint using a category search.</span></span> <span data-ttu-id="d2bd0-105">在此案例中，服務端點會在 UDDI 中發行檔案端點。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-105">In this scenario, the service endpoint will be a file endpoint published in UDDI.</span></span>  
  
 <span data-ttu-id="d2bd0-106">在此 「 如何 」 主題，您將完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="d2bd0-106">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="d2bd0-107">建立路由的路線名單，若要解決服務端點。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-107">Create an itinerary routing slip to resolve a service endpoint.</span></span>  
  
-   <span data-ttu-id="d2bd0-108">設定將訊息路由至服務端點使用的 UDDI 3 解析程式路線。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-108">Configure the itinerary to route the message to a service endpoint using a UDDI 3 resolver.</span></span>  
  
-   <span data-ttu-id="d2bd0-109">測試使用路線測試用戶端範例應用程式的路線。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-109">Test the itinerary using the Itinerary Test Client sample application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d2bd0-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="d2bd0-110">Prerequisites</span></span>  
 <span data-ttu-id="d2bd0-111">在此 「 如何 」 主題中的程序需要完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-111">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="steps"></a><span data-ttu-id="d2bd0-112">步驟</span><span class="sxs-lookup"><span data-stu-id="d2bd0-112">Steps</span></span>  
  
#### <a name="to-create-an-itinerary-model"></a><span data-ttu-id="d2bd0-113">若要建立路線的模型</span><span class="sxs-lookup"><span data-stu-id="d2bd0-113">To create an itinerary model</span></span>  
  
1.  <span data-ttu-id="d2bd0-114">在 Visual Studio 中開啟 C:\HowTos\Patterns\Patterns.sln。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-114">In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="d2bd0-115">在 方案總管 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下 **新的行程**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-115">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="d2bd0-116">在**加入新項目** 對話方塊中，輸入**UDDI3CategorySearch**中**名稱**方塊，然後再按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-116">In the **Add New Item** dialog box, type **UDDI3CategorySearch** in the **Name** box, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a><span data-ttu-id="d2bd0-117">若要設定的路線屬性</span><span class="sxs-lookup"><span data-stu-id="d2bd0-117">To configure the properties of the itinerary</span></span>  
  
1.  <span data-ttu-id="d2bd0-118">在 Visual Studio 中，按一下設計介面的**UDDI3CategorySearch.itinerary**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-118">In Visual Studio, click the design surface of **UDDI3CategorySearch.itinerary**.</span></span> <span data-ttu-id="d2bd0-119">在**UDDI3CategorySearch**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="d2bd0-119">In the **UDDI3CategorySearch** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="d2bd0-120">在**模型匯出工具**下拉式清單中，按一下  **XML 路線匯出工具**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-120">In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="d2bd0-121">下**Extender 設定**區段中，旁邊**路線 XML 檔案**屬性中，按一下省略符號按鈕 （...）。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-121">Under the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).</span></span>  
  
    3.  <span data-ttu-id="d2bd0-122">在**選取 XML 檔案** 對話方塊中，輸入**C:\HowTos\Itineraries\UDDI3CategorySearch**中**檔案名稱**方塊，然後再按一下**儲存**.</span><span class="sxs-lookup"><span data-stu-id="d2bd0-122">In the **Select XML File** dialog box, type **C:\HowTos\Itineraries\UDDI3CategorySearch** in the **File name** box, and then click **Save**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="d2bd0-123">這個步驟可讓您匯出成 XML 的路線，到本機檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-123">This step enables you to export the itinerary as XML to a local file location.</span></span> <span data-ttu-id="d2bd0-124">藉由將行程至本機檔案的位置，而不匯出至路線的資料庫，可讓測試使用 ESB 測試用戶端應用程式的路線。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-124">By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application.</span></span> <span data-ttu-id="d2bd0-125">您將完成此程序，稍後在本使用說明主題。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-125">You will complete this process later in this How-to topic.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="d2bd0-126">若要定義路線結構</span><span class="sxs-lookup"><span data-stu-id="d2bd0-126">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="d2bd0-127">從 [工具箱] 拖曳**上手**至設計介面的模型項目。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-127">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="d2bd0-128">在**OnRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="d2bd0-128">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="d2bd0-129">按一下**名稱**屬性，，然後輸入**ReceiveNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-129">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="d2bd0-130">在**Extender**下拉式清單中，按一下 **上手 ESB Extender**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-130">In the **Extender** drop-down list, click **On-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="d2bd0-131">在**BizTalk 應用程式**下拉式清單中，按一下  **Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-131">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="d2bd0-132">在**接收埠**下拉式清單中，按一下  **OnRamp.Itinerary**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-132">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="d2bd0-133">從 [工具箱] 拖曳**路線服務**至設計介面的模型項目。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-133">From the Toolbox, drag an **Itinerary Service** model element to the design surface.</span></span> <span data-ttu-id="d2bd0-134">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="d2bd0-134">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="d2bd0-135">按一下**名稱**屬性，，然後輸入**CategoryRoute**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-135">Click the **Name** property, and then type **CategoryRoute**.</span></span>  
  
    2.  <span data-ttu-id="d2bd0-136">在**路線服務的擴充項**下拉式清單中，按一下 **傳訊 Extender**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-136">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  
  
    3.  <span data-ttu-id="d2bd0-137">在**容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-137">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="d2bd0-138">在**服務名稱**下拉式清單中，按一下  **Microsoft.Practices.ESB.Services.Routing**</span><span class="sxs-lookup"><span data-stu-id="d2bd0-138">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Routing**</span></span>  
  
3.  <span data-ttu-id="d2bd0-139">以滑鼠右鍵按一下**解析程式**集合**CategoryRoute**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-139">Right-click the **Resolver** collection of the **CategoryRoute** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="d2bd0-140">在**Resolver1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="d2bd0-140">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="d2bd0-141">按一下**名稱**屬性，，然後輸入**CategorySearch**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-141">Click the **Name** property, and then type **CategorySearch**.</span></span>  
  
    2.  <span data-ttu-id="d2bd0-142">在**解析程式實作**下拉式清單中，按一下  **Uddi3 解析程式擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-142">In the **Resolver Implementation** drop-down list, click **Uddi3 Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="d2bd0-143">在**解析程式 Moniker**下拉式清單中，按一下  **UDDI3**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-143">In the **Resolver Moniker** drop-down list, click **UDDI3**.</span></span>  
  
    4.  <span data-ttu-id="d2bd0-144">按一下**類別目錄搜尋**屬性，然後按一下省略符號按鈕 （...）。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-144">Click the **Category Search** property, and then click the ellipsis button (…).</span></span>  
  
    5.  <span data-ttu-id="d2bd0-145">在**名稱值屬性編輯器**對話方塊中，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-145">In the **Name Value Property Editor** dialog box, click **Add**.</span></span>  
  
    6.  <span data-ttu-id="d2bd0-146">按一下**名稱**屬性，，然後輸入**uddi:esb:biztalkapplication**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-146">Click the **Name** property, and then type **uddi:esb:biztalkapplication**.</span></span>  
  
    7.  <span data-ttu-id="d2bd0-147">按一下**值**屬性，，然後輸入**GlobalBank.ESB**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-147">Click the **Value** property, and then type **GlobalBank.ESB**.</span></span>  
  
    8.  <span data-ttu-id="d2bd0-148">在**名稱值屬性編輯器**對話方塊中，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-148">In the **Name Value Property Editor** dialog box, click **Add**.</span></span>  
  
    9. <span data-ttu-id="d2bd0-149">按一下**名稱**屬性，，然後輸入**uddi:esb:portname**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-149">Click the **Name** property, and then type **uddi:esb:portname**.</span></span>  
  
    10. <span data-ttu-id="d2bd0-150">按一下**值**屬性，，然後輸入**OrderFileServicev3**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-150">Click the **Value** property, and then type **OrderFileServicev3**.</span></span>  
  
    11. <span data-ttu-id="d2bd0-151">在**名稱值屬性編輯器**對話方塊中，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-151">In the **Name Value Property Editor** dialog box, click **Add**.</span></span>  
  
    12. <span data-ttu-id="d2bd0-152">按一下**名稱**屬性，，然後輸入**uddi:esb:version**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-152">Click the **Name** property, and then type **uddi:esb:version**.</span></span>  
  
    13. <span data-ttu-id="d2bd0-153">按一下**值**屬性，，然後輸入**1**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-153">Click the **Value** property, and then type **1**.</span></span>  
  
    14. <span data-ttu-id="d2bd0-154">按一下**確定**關閉**名稱值屬性編輯器** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-154">Click **OK** to close the **Name Value Property Editor** dialog box.</span></span>  
  
4.  <span data-ttu-id="d2bd0-155">以滑鼠右鍵按一下**CategorySearch**解析程式，然後再按一下**測試解析程式組態**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-155">Right-click the **CategorySearch** resolver, and then click **Test Resolver Configuration**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2bd0-156">確認 [輸出] 視窗中顯示的輸出。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-156">Verify the output displayed in the Output window.</span></span>  
  
5.  <span data-ttu-id="d2bd0-157">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-157">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="d2bd0-158">拖曳連接**ReceiveNAOrder**模型項目的**CategoryRoute**模型項目。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-158">Drag a connection from the **ReceiveNAOrder** model element to the **CategoryRoute** model element.</span></span>  
  
6.  <span data-ttu-id="d2bd0-159">從 [工具箱] 拖曳**匝道**模型項目至設計介面，然後再將它放右邊的**CategoryRoute**模型項目。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-159">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **CategoryRoute** model element.</span></span> <span data-ttu-id="d2bd0-160">在**OffRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="d2bd0-160">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="d2bd0-161">按一下**名稱**屬性，，然後輸入**SendNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-161">Click the **Name** property, and then type **SendNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="d2bd0-162">在**Extender**下拉式清單中，按一下 **匝道 ESB Extender**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-162">In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="d2bd0-163">在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-163">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="d2bd0-164">在**傳送埠**下拉式清單中，按一下  **DynamicResolutionOneWay**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-164">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
7.  <span data-ttu-id="d2bd0-165">從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**CategoryRoute**模型項目和**SendNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-165">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **CategoryRoute** model element and the **SendNAOrder** model element.</span></span> <span data-ttu-id="d2bd0-166">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="d2bd0-166">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="d2bd0-167">按一下**名稱**屬性，，然後輸入**SendPortFilter**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-167">Click the **Name** property, and then type **SendPortFilter**.</span></span>  
  
    2.  <span data-ttu-id="d2bd0-168">在**路線服務的擴充項**下拉式清單中，按一下 **匝道 Extender**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-168">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="d2bd0-169">在**匝道**下拉式清單中，展開**SendNAOrder**，然後按一下 **傳送處理常式**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-169">In the **Off-Ramp** drop-down list, expand **SendNAOrder**, and then click **Send Handlers**.</span></span>  
  
8.  <span data-ttu-id="d2bd0-170">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-170">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="d2bd0-171">拖曳連接**CategoryRoute**模型項目的**SendPortFilter**模型項目。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-171">Drag a connection from the **CategoryRoute** model element to the **SendPortFilter** model element.</span></span>  
  
9. <span data-ttu-id="d2bd0-172">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-172">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="d2bd0-173">拖曳連接**SendPortFilter**模型項目的**SendNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-173">Drag a connection from the **SendPortFilter** model element to the **SendNAOrder** model element.</span></span>  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a><span data-ttu-id="d2bd0-174">若要匯出的行程測試用戶端使用的模型</span><span class="sxs-lookup"><span data-stu-id="d2bd0-174">To export the model for use with the Itinerary Test Client</span></span>  
  
1.  <span data-ttu-id="d2bd0-175">在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**UDDI3CategorySearch**路線，然後再按一下**匯出模型**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-175">In Visual Studio, right-click the design surface of the **UDDI3CategorySearch** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2bd0-176">在 Visual Studio 中，開啟路線的 XML 版本。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-176">The XML version of the itinerary opens in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="d2bd0-177">儲存專案的所有成品。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-177">Save all project artifacts.</span></span>  
  
3.  <span data-ttu-id="d2bd0-178">在 Windows 檔案總管，瀏覽至 C:\HowTos\Itineraries 並注意您路線 XML (UDDI3CategorySearch.xml) 建立。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-178">In Windows Explorer, browse to C:\HowTos\Itineraries and notice the creation of your itinerary XML (UDDI3CategorySearch.xml).</span></span>  
  
#### <a name="to-test-the-itinerary"></a><span data-ttu-id="d2bd0-179">若要測試路線</span><span class="sxs-lookup"><span data-stu-id="d2bd0-179">To test the itinerary</span></span>  
  
1.  <span data-ttu-id="d2bd0-180">開啟路線測試用戶端範例應用程式使用期間建立的捷徑[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)(C:\HowTos\ESB。Itinerary.Test.exe-捷徑)。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-180">Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).</span></span>  
  
2.  <span data-ttu-id="d2bd0-181">在路線測試用戶端中，清除**使用 WCF 服務**核取方塊，然後**負載路線**。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-181">In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.</span></span>  
  
3.  <span data-ttu-id="d2bd0-182">在**開啟路線檔案**對話方塊中，瀏覽至 C:\HowTos\Itineraries。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-182">In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="d2bd0-183">選取**UDDI3CategorySearch.xml**，然後按一下 **開啟**載入路線。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-183">Select **UDDI3CategorySearch.xml**, and then click **Open** to load the itinerary.</span></span>  
  
4.  <span data-ttu-id="d2bd0-184">按一下**確定**清除**路線成功載入**訊息。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-184">Click **OK** to clear the **Itinerary Loaded Successfully** message.</span></span>  
  
5.  <span data-ttu-id="d2bd0-185">在路線測試用戶端中，按一下旁邊的省略符號按鈕 （...）**載入訊息**方塊。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-185">In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.</span></span>  
  
6.  <span data-ttu-id="d2bd0-186">在**選取要載入的 XML 文件**對話方塊中，瀏覽至 C:\HowTos。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-186">In the **Select XML Document to load** dialog box, browse to C:\HowTos.</span></span> <span data-ttu-id="d2bd0-187">選取 NAOrderDoc.xml，，然後按一下**開啟**載入測試訊息。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-187">Select NAOrderDoc.xml, and then click **Open** to load the test message.</span></span>  
  
7.  <span data-ttu-id="d2bd0-188">按一下**送出要求** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-188">Click the **Submit Request** button.</span></span> <span data-ttu-id="d2bd0-189">測試完成時，按一下**確定**解除顯示的確認。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-189">When the test completes, click **OK** to dismiss the confirmation that appears.</span></span>  
  
8.  <span data-ttu-id="d2bd0-190">在 Windows 檔案總管，瀏覽至**C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Test\Filedrop\Out**並確認**%MessageID%.xml**已寫入訊息目錄。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-190">In Windows Explorer, browse to **C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Test\Filedrop\Out** and verify that the **%MessageID%.xml** message has been written to the directory.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="d2bd0-191">其他資源</span><span class="sxs-lookup"><span data-stu-id="d2bd0-191">Additional Resources</span></span>  
 <span data-ttu-id="d2bd0-192">如需詳細資訊，請參閱下列相關主題：</span><span class="sxs-lookup"><span data-stu-id="d2bd0-192">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="d2bd0-193">如何：使用 UDDI 繫結索引鍵搜尋解決服務端點</span><span class="sxs-lookup"><span data-stu-id="d2bd0-193">How to: Resolve a Service Endpoint Using a UDDI Binding Key Search</span></span>](../esb-toolkit/how-to-resolve-a-service-endpoint-using-a-uddi-binding-key-search.md)  
  
-   [<span data-ttu-id="d2bd0-194">開發活動</span><span class="sxs-lookup"><span data-stu-id="d2bd0-194">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="d2bd0-195">使用動態解析和路由</span><span class="sxs-lookup"><span data-stu-id="d2bd0-195">Using Dynamic Resolution and Routing</span></span>](../esb-toolkit/using-dynamic-resolution-and-routing.md)