---
title: 如何： 啟用 BAM 追蹤在 ESB 路線服務 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58859937-f8d0-4c33-9a7a-62fec8441936
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27d0338ad56daa342fce1d339b9e7aa43fd7e25e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991543"
---
# <a name="how-to-enable-bam-tracking-in-an-esb-itinerary-service"></a><span data-ttu-id="b7149-102">如何： 啟用 BAM 追蹤在 ESB 路線服務</span><span class="sxs-lookup"><span data-stu-id="b7149-102">How to: Enable BAM Tracking in an ESB Itinerary Service</span></span>
## <a name="goal"></a><span data-ttu-id="b7149-103">目標</span><span class="sxs-lookup"><span data-stu-id="b7149-103">Goal</span></span>  
 <span data-ttu-id="b7149-104">本節示範如何啟用追蹤現有路線 「 商務活動監視器 」 (BAM)。</span><span class="sxs-lookup"><span data-stu-id="b7149-104">This section demonstrates how to enable Business Activity Monitor (BAM) tracking for an existing itinerary.</span></span>  
  
 <span data-ttu-id="b7149-105">在本使用說明主題中，您將完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="b7149-105">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="b7149-106">啟用用來追蹤使用 「 商務活動監視器的路線服務的屬性。</span><span class="sxs-lookup"><span data-stu-id="b7149-106">Enable the property used for tracking Itinerary Services using Business Activity Monitor.</span></span>  
  
-   <span data-ttu-id="b7149-107">測試使用路線測試用戶端的範例應用程式的 BAM 追蹤。</span><span class="sxs-lookup"><span data-stu-id="b7149-107">Test BAM tracking using the Itinerary Test Client sample application.</span></span>  
  
-   <span data-ttu-id="b7149-108">驗證 BAM 結果使用 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="b7149-108">Verify the BAM results using a SQL query.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b7149-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="b7149-109">Prerequisites</span></span>  
 <span data-ttu-id="b7149-110">本使用說明主題中的程序必須完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="b7149-110">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="b7149-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="b7149-111">Before You Begin</span></span>  
 <span data-ttu-id="b7149-112">您執行本使用說明主題中稍後的步驟之前，請完成下列工作：</span><span class="sxs-lookup"><span data-stu-id="b7149-112">Complete the following tasks before you perform the steps later in this How-to topic:</span></span>  
  
- <span data-ttu-id="b7149-113">建立 ESB 路線的特定領域語言 (DSL) 模型。</span><span class="sxs-lookup"><span data-stu-id="b7149-113">Create an ESB itinerary domain-specific language (DSL) model.</span></span>  
  
- <span data-ttu-id="b7149-114">設定路線的屬性。</span><span class="sxs-lookup"><span data-stu-id="b7149-114">Configure the properties of the itinerary.</span></span>  
  
- <span data-ttu-id="b7149-115">定義結構的路線。</span><span class="sxs-lookup"><span data-stu-id="b7149-115">Define the structure of the itinerary.</span></span>  
  
  <span data-ttu-id="b7149-116">下列程序描述如何進行每一種。</span><span class="sxs-lookup"><span data-stu-id="b7149-116">The following procedures describe how to do each of these.</span></span>  
  
#### <a name="to-create-an-esb-itinerary-dsl-model"></a><span data-ttu-id="b7149-117">若要建立的 ESB 路線 DSL 模型</span><span class="sxs-lookup"><span data-stu-id="b7149-117">To create an ESB itinerary DSL model</span></span>  
  
1.  <span data-ttu-id="b7149-118">在 Visual Studio 中，開啟 [C:\HowTos\Patterns\Patterns.sln]。</span><span class="sxs-lookup"><span data-stu-id="b7149-118">In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="b7149-119">在 [方案總管] 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下**新路線**。</span><span class="sxs-lookup"><span data-stu-id="b7149-119">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="b7149-120">在 **加入新項目** 對話方塊中，按一下**ItineraryDsl**範本 窗格中。</span><span class="sxs-lookup"><span data-stu-id="b7149-120">In the **Add New Item** dialog box, click  **ItineraryDsl** in the Templates pane.</span></span>  
  
4.  <span data-ttu-id="b7149-121">在 **名稱**方塊中，輸入**BamTracking**，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="b7149-121">In the **Name** box, type **BamTracking**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a><span data-ttu-id="b7149-122">若要設定的路線屬性</span><span class="sxs-lookup"><span data-stu-id="b7149-122">To configure the properties of the itinerary</span></span>  
  
1.  <span data-ttu-id="b7149-123">在 Visual Studio 中，按一下設計介面**BamTracking.itinerary**。</span><span class="sxs-lookup"><span data-stu-id="b7149-123">In Visual Studio, click the design surface of **BamTracking.itinerary**.</span></span> <span data-ttu-id="b7149-124">在 [ **BamTracking**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="b7149-124">In the **BamTracking** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="b7149-125">在 **模型匯出工具**下拉式清單中，按一下**XML 路線匯出工具**。</span><span class="sxs-lookup"><span data-stu-id="b7149-125">In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="b7149-126">在  **Extender 設定**區段中，旁邊**路線 XML 檔案**屬性，按一下省略符號按鈕 （...）。</span><span class="sxs-lookup"><span data-stu-id="b7149-126">In the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).</span></span>  
  
    3.  <span data-ttu-id="b7149-127">在 **選取 XML 檔案**對話方塊中，於**檔案名稱**方塊中，輸入**C:\HowTos\Itineraries\BamTracking** ，然後按一下 **儲存**。</span><span class="sxs-lookup"><span data-stu-id="b7149-127">In the **Select XML File** dialog box, in the **File name** box, type **C:\HowTos\Itineraries\BamTracking** and then click **Save**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="b7149-128">此步驟可讓您將匯出為 XML 的路線，到本機檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="b7149-128">This step enables you to export the itinerary as XML to a local file location.</span></span> <span data-ttu-id="b7149-129">而不是匯出至本機檔案位置，路線，路線資料庫，可讓測試使用 ESB 測試用戶端應用程式的路線。</span><span class="sxs-lookup"><span data-stu-id="b7149-129">By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application.</span></span> <span data-ttu-id="b7149-130">您將完成此程序，稍後在本使用說明主題。</span><span class="sxs-lookup"><span data-stu-id="b7149-130">You will complete this process later in this How-to topic.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="b7149-131">若要定義的路線結構</span><span class="sxs-lookup"><span data-stu-id="b7149-131">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="b7149-132">從 [工具箱] 拖曳**匝道**模型項目到設計介面。</span><span class="sxs-lookup"><span data-stu-id="b7149-132">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="b7149-133">在 [ **OnRamp1**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="b7149-133">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="b7149-134">按一下 **名稱**屬性，然後按**ReceiveNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="b7149-134">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="b7149-135">在  **Extender**下拉式清單中，按一下**匝道 ESB 服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="b7149-135">In the **Extender** drop-down list, click **On-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="b7149-136">在  **BizTalk 應用程式**下拉式清單中，按一下**Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="b7149-136">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="b7149-137">在 **接收埠**下拉式清單中，按一下**OnRamp.Itinerary**。</span><span class="sxs-lookup"><span data-stu-id="b7149-137">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="b7149-138">從 [工具箱] 拖曳**路線服務**模型項目到設計介面，並再將其放置在右邊**匝道**模型項目。</span><span class="sxs-lookup"><span data-stu-id="b7149-138">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it to the right of the **On-Ramp** model element.</span></span> <span data-ttu-id="b7149-139">在 [ **ItineraryService1**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="b7149-139">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="b7149-140">按一下 **名稱**屬性，然後按**MapNAOrderToCNOrder**。</span><span class="sxs-lookup"><span data-stu-id="b7149-140">Click the **Name** property, and then type **MapNAOrderToCNOrder**.</span></span>  
  
    2.  <span data-ttu-id="b7149-141">在 **路線服務的擴充項**下拉式清單中，按一下**傳訊路線服務延伸**。</span><span class="sxs-lookup"><span data-stu-id="b7149-141">In the **Itinerary Service Extender** drop-down list, click **Messaging Itinerary Service Extension**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="b7149-142">這個屬性會定義此程序需要 （傳訊） 的管線中的位置。</span><span class="sxs-lookup"><span data-stu-id="b7149-142">This property defines that the process will take place in a pipeline (messaging).</span></span> <span data-ttu-id="b7149-143">或者，如果協調流程中的位置時，會進行的程序，設定**路線服務 Extender**屬性設**協調流程路線服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="b7149-143">Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Itinerary Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="b7149-144">在 **容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。</span><span class="sxs-lookup"><span data-stu-id="b7149-144">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="b7149-145">在 **服務名稱**下拉式清單中，按一下**Microsoft.Practices.ESB.Services.Transform**。</span><span class="sxs-lookup"><span data-stu-id="b7149-145">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Transform**.</span></span>  
  
3.  <span data-ttu-id="b7149-146">以滑鼠右鍵按一下**解析**的集合**MapNAOrderToCNOrder**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="b7149-146">Right-click the **Resolver** collection of the **MapNAOrderToCNOrder** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="b7149-147">在 [ **Resolver1**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="b7149-147">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="b7149-148">按一下 **名稱**屬性，然後按**StaticallySpecifyTheMap**。</span><span class="sxs-lookup"><span data-stu-id="b7149-148">Click the **Name** property, and then type **StaticallySpecifyTheMap**.</span></span>  
  
    2.  <span data-ttu-id="b7149-149">在 **解析程式實作**下拉式清單中，按一下**靜態的解析程式擴充**。</span><span class="sxs-lookup"><span data-stu-id="b7149-149">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="b7149-150">在 **轉換的型別**下拉式清單中，按一下**GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**。</span><span class="sxs-lookup"><span data-stu-id="b7149-150">In the **Transform Type** drop-down list, click **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**.</span></span>  
  
    4.  <span data-ttu-id="b7149-151">在  **TransportName**下拉式清單中，按一下**檔案**。</span><span class="sxs-lookup"><span data-stu-id="b7149-151">In the **TransportName** drop-down list, click **FILE**.</span></span>  
  
4.  <span data-ttu-id="b7149-152">在 [工具箱] 中，按一下**連接器**。</span><span class="sxs-lookup"><span data-stu-id="b7149-152">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="b7149-153">拖曳連接，以從**ReceiveNAOrder**模型項目**MapNAOrderToCNOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="b7149-153">Drag a connection from the **ReceiveNAOrder** model element to the **MapNAOrderToCNOrder** model element.</span></span>  
  
5.  <span data-ttu-id="b7149-154">從 [工具箱] 拖曳**出口匝**模型項目到設計介面，並再將其放置在右邊**MapNAOrderToCNOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="b7149-154">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **MapNAOrderToCNOrder** model element.</span></span> <span data-ttu-id="b7149-155">在 [ **OffRamp1**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="b7149-155">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="b7149-156">按一下 **名稱**屬性，然後按**SendCNOrder**。</span><span class="sxs-lookup"><span data-stu-id="b7149-156">Click the **Name** property, and then type **SendCNOrder**.</span></span>  
  
    2.  <span data-ttu-id="b7149-157">在  **Extender**下拉式清單中，按一下**出口匝 ESB 服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="b7149-157">In the **Extender** drop-down list, click **Off-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="b7149-158">在  **BizTalk 應用程式**下拉式清單中，按一下**GlobalBank.ESB**。</span><span class="sxs-lookup"><span data-stu-id="b7149-158">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="b7149-159">在 **傳送埠**下拉式清單中，按一下**DynamicResolutionOneWay**。</span><span class="sxs-lookup"><span data-stu-id="b7149-159">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
6.  <span data-ttu-id="b7149-160">從 [工具箱] 拖曳**路線服務**模型項目到設計介面，並將其之間放置**MapNAOrderToCNOrder**模型項目和**SendCNOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="b7149-160">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **MapNAOrderToCNOrder** model element and the **SendCNOrder** model element.</span></span> <span data-ttu-id="b7149-161">在 [ **ItineraryService1**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="b7149-161">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="b7149-162">按一下 **名稱**屬性，然後按**SendPortFilter**。</span><span class="sxs-lookup"><span data-stu-id="b7149-162">Click the **Name** property, and then type **SendPortFilter**.</span></span>  
  
    2.  <span data-ttu-id="b7149-163">在 **路線服務的擴充項**下拉式清單中，按一下**出口匝路線服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="b7149-163">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Itinerary Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="b7149-164">在 **出口匝**下拉式清單中，展開**SendCNOrder**，然後按一下 **傳送處理常式**。</span><span class="sxs-lookup"><span data-stu-id="b7149-164">In the **Off-Ramp** drop-down list, expand **SendCNOrder**, and then click **Send Handlers**.</span></span>  
  
7.  <span data-ttu-id="b7149-165">以滑鼠右鍵按一下**解析**的集合**SendPortFilter**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="b7149-165">Right-click the **Resolver** collection of the **SendPortFilter** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="b7149-166">在 [ **Resolver1**屬性] 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="b7149-166">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="b7149-167">按一下 **名稱**屬性，然後按**ConfigureFolderSettings**。</span><span class="sxs-lookup"><span data-stu-id="b7149-167">Click the **Name** property, and then type **ConfigureFolderSettings**.</span></span>  
  
    2.  <span data-ttu-id="b7149-168">在 **解析程式實作**下拉式清單中，按一下**靜態的解析程式擴充**。</span><span class="sxs-lookup"><span data-stu-id="b7149-168">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="b7149-169">在 **傳輸名稱**下拉式清單中，按一下**檔案**。</span><span class="sxs-lookup"><span data-stu-id="b7149-169">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    4.  <span data-ttu-id="b7149-170">按一下 **傳輸位置**屬性，然後按**C:\HowTos\Out\BAM%MessageID%.xml**</span><span class="sxs-lookup"><span data-stu-id="b7149-170">Click the **Transport Location** property, and then type **C:\HowTos\Out\BAM%MessageID%.xml**</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="b7149-171">每個出口匝會有相關聯，路線服務結合的路線服務的屬性和出口匝屬性來定義動態傳送埠的訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="b7149-171">Each off-ramp will have an itinerary service associated with it; the combination of the itinerary service properties and the properties of the off-ramp define the subscription of the dynamic send port.</span></span>  
  
8.  <span data-ttu-id="b7149-172">在 [工具箱] 中，按一下**連接器**。</span><span class="sxs-lookup"><span data-stu-id="b7149-172">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="b7149-173">拖曳連接，以從**MapNAOrderToCNOrder**模型項目**SendPortFilter**模型項目。</span><span class="sxs-lookup"><span data-stu-id="b7149-173">Drag a connection from the **MapNAOrderToCNOrder** model element to the **SendPortFilter** model element.</span></span>  
  
9. <span data-ttu-id="b7149-174">在 [工具箱] 中，按一下**連接器**。</span><span class="sxs-lookup"><span data-stu-id="b7149-174">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="b7149-175">拖曳連接，以從**SendPortFilter**模型項目**SendCNOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="b7149-175">Drag a connection from the **SendPortFilter** model element to the **SendCNOrder** model element.</span></span>  
  
10. <span data-ttu-id="b7149-176">儲存專案的所有成品。</span><span class="sxs-lookup"><span data-stu-id="b7149-176">Save all project artifacts.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="b7149-177">步驟</span><span class="sxs-lookup"><span data-stu-id="b7149-177">Steps</span></span>  
  
#### <a name="to-modify-the-itinerary"></a><span data-ttu-id="b7149-178">若要修改的路線</span><span class="sxs-lookup"><span data-stu-id="b7149-178">To modify the itinerary</span></span>  
  
1.  <span data-ttu-id="b7149-179">在 Visual Studio 中，開啟 [C:\HowTos\Patterns\Patterns.sln]。</span><span class="sxs-lookup"><span data-stu-id="b7149-179">In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="b7149-180">在 [方案總管] 中，按兩下**BamTracking.itinerary**。</span><span class="sxs-lookup"><span data-stu-id="b7149-180">In Solution Explorer, double-click **BamTracking.itinerary**.</span></span>  
  
3.  <span data-ttu-id="b7149-181">按一下  **MapNAOrderToCNOrder**路線服務項目。</span><span class="sxs-lookup"><span data-stu-id="b7149-181">Click the **MapNAOrderToCNOrder** itinerary service element.</span></span>  
  
4.  <span data-ttu-id="b7149-182">在 [ **MapNAOrderToCNOrder**屬性] 視窗中，按一下 **，則為 True**中**追蹤已啟用**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="b7149-182">In the **MapNAOrderToCNOrder** Properties window, click **True** in the **Tracking Enabled** drop-down list.</span></span>  
  
5.  <span data-ttu-id="b7149-183">按一下  **SendPortFilter**路線服務項目。</span><span class="sxs-lookup"><span data-stu-id="b7149-183">Click the **SendPortFilter** itinerary service element.</span></span>  
  
6.  <span data-ttu-id="b7149-184">在 [ **SendPortFilter**屬性] 視窗中，按一下 **，則為 True**中**追蹤已啟用**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="b7149-184">In the **SendPortFilter** Properties window, click **True** in the **Tracking Enabled** drop-down list.</span></span>  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a><span data-ttu-id="b7149-185">若要匯出使用路線測試用戶端使用的模型</span><span class="sxs-lookup"><span data-stu-id="b7149-185">To export the model for use with the Itinerary Test Client</span></span>  
  
1.  <span data-ttu-id="b7149-186">在 Visual Studio 中，以滑鼠右鍵按一下設計介面**BamTracking**路線，，然後按一下**匯出模型**。</span><span class="sxs-lookup"><span data-stu-id="b7149-186">In Visual Studio, right-click the design surface of the **BamTracking** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b7149-187">在 Visual Studio 中，開啟路線的 XML 版本。</span><span class="sxs-lookup"><span data-stu-id="b7149-187">The XML version of the itinerary opens in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="b7149-188">儲存專案的所有成品。</span><span class="sxs-lookup"><span data-stu-id="b7149-188">Save all project artifacts.</span></span>  
  
3.  <span data-ttu-id="b7149-189">在 Windows 檔案總管中，瀏覽至 C:\HowTos\Itineraries 並注意您的路線 XML (BamTracking.xml) 建立。</span><span class="sxs-lookup"><span data-stu-id="b7149-189">In Windows Explorer, browse to C:\HowTos\Itineraries and notice the creation of your itinerary XML (BamTracking.xml).</span></span>  
  
#### <a name="to-test-the-itinerary"></a><span data-ttu-id="b7149-190">若要測試的路線</span><span class="sxs-lookup"><span data-stu-id="b7149-190">To test the itinerary</span></span>  
  
1.  <span data-ttu-id="b7149-191">開啟路線測試用戶端範例應用程式使用期間建立的捷徑[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)(C:\HowTos\ESB。Itinerary.Test.exe-捷徑)。</span><span class="sxs-lookup"><span data-stu-id="b7149-191">Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).</span></span>  
  
2.  <span data-ttu-id="b7149-192">在路線測試用戶端中，清除**使用 WCF 服務**核取方塊，然後按一下**負載路線**。</span><span class="sxs-lookup"><span data-stu-id="b7149-192">In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.</span></span>  
  
3.  <span data-ttu-id="b7149-193">在 [**開啟路線檔案**] 對話方塊中，瀏覽至 C:\HowTos\Itineraries。</span><span class="sxs-lookup"><span data-stu-id="b7149-193">In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="b7149-194">選取  **BamTracking.xml**，然後按一下**開啟**載入路線。</span><span class="sxs-lookup"><span data-stu-id="b7149-194">Select **BamTracking.xml**, and then click **Open** to load the itinerary.</span></span>  
  
4.  <span data-ttu-id="b7149-195">按一下  **確定**清除**路線成功載入**訊息。</span><span class="sxs-lookup"><span data-stu-id="b7149-195">Click **OK** to clear the **Itinerary Loaded Successfully** message.</span></span>  
  
5.  <span data-ttu-id="b7149-196">在路線測試用戶端中，按一下 [旁的省略符號按鈕 （...）**載入訊息**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="b7149-196">In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.</span></span>  
  
6.  <span data-ttu-id="b7149-197">在 [**選取要載入的 XML 文件**] 對話方塊中，瀏覽至 C:\HowTos。</span><span class="sxs-lookup"><span data-stu-id="b7149-197">In the **Select XML Document to load** dialog box, browse to C:\HowTos.</span></span> <span data-ttu-id="b7149-198">選取  **NAOrderDoc.xml**，然後按一下**開啟**載入測試訊息。</span><span class="sxs-lookup"><span data-stu-id="b7149-198">Select **NAOrderDoc.xml**, and then click **Open** to load the test message.</span></span>  
  
7.  <span data-ttu-id="b7149-199">按一下 [**送出要求**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b7149-199">Click the **Submit Request** button.</span></span> <span data-ttu-id="b7149-200">測試完成時，按一下**確定**關閉顯示的確認。</span><span class="sxs-lookup"><span data-stu-id="b7149-200">When the test completes, click **OK** to dismiss the confirmation that appears.</span></span>  
  
8.  <span data-ttu-id="b7149-201">在 Windows 檔案總管中，瀏覽至 C:\HowTos\Out。確認目錄中已寫入 BAM%MessageID%.xml 訊息。</span><span class="sxs-lookup"><span data-stu-id="b7149-201">In Windows Explorer, browse to C:\HowTos\Out. Verify that the BAM%MessageID%.xml message has been written to the directory.</span></span>  
  
#### <a name="to-verify-message-tracking"></a><span data-ttu-id="b7149-202">若要確認訊息追蹤</span><span class="sxs-lookup"><span data-stu-id="b7149-202">To verify message tracking</span></span>  
  
1. <span data-ttu-id="b7149-203">按一下 **開始**在工作列上，指向**所有程式**，指向[!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)]，然後按一下**SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="b7149-203">Click **Start** on the taskbar, point to **All Programs**, point to [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)], and then click **SQL Server Management Studio**.</span></span>  
  
2. <span data-ttu-id="b7149-204">按一下 **[新增查詢]**。</span><span class="sxs-lookup"><span data-stu-id="b7149-204">Click **New Query**.</span></span>  
  
3. <span data-ttu-id="b7149-205">在 [查詢] 窗格中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="b7149-205">In the query pane, type the following:</span></span>  
  
   ```  
   SELECT *  
   FROM [BAMPrimaryImport].[dbo].[bam_ItineraryServiceActivity_Completed]  
   GO  
   ```  
  
4. <span data-ttu-id="b7149-206">按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="b7149-206">Click **Execute**.</span></span>  
  
5. <span data-ttu-id="b7149-207">在 [結果] 窗格中，使用**時間戳記**欄找出最新的項目。</span><span class="sxs-lookup"><span data-stu-id="b7149-207">In the Results pane, use the **TimeStamp** column to locate the most recent entry.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="b7149-208">其他資源</span><span class="sxs-lookup"><span data-stu-id="b7149-208">Additional Resources</span></span>  
 <span data-ttu-id="b7149-209">如需詳細資訊，請參閱下列相關主題：</span><span class="sxs-lookup"><span data-stu-id="b7149-209">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="b7149-210">開發活動</span><span class="sxs-lookup"><span data-stu-id="b7149-210">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="b7149-211">訊息路由模式</span><span class="sxs-lookup"><span data-stu-id="b7149-211">Message Routing Patterns</span></span>](../esb-toolkit/message-routing-patterns.md)  
  
-   [<span data-ttu-id="b7149-212">使用動態解析和路由</span><span class="sxs-lookup"><span data-stu-id="b7149-212">Using Dynamic Resolution and Routing</span></span>](../esb-toolkit/using-dynamic-resolution-and-routing.md)