---
title: "如何： 啟用 BAM 追蹤在 ESB 路線服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58859937-f8d0-4c33-9a7a-62fec8441936
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 011de667e06f4275fe75a28b6566a6bc393cf841
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-enable-bam-tracking-in-an-esb-itinerary-service"></a><span data-ttu-id="f8ce1-102">如何： 啟用 BAM 追蹤 ESB 路線服務中</span><span class="sxs-lookup"><span data-stu-id="f8ce1-102">How to: Enable BAM Tracking in an ESB Itinerary Service</span></span>
## <a name="goal"></a><span data-ttu-id="f8ce1-103">目標</span><span class="sxs-lookup"><span data-stu-id="f8ce1-103">Goal</span></span>  
 <span data-ttu-id="f8ce1-104">本節示範如何啟用商務活動監視器 (BAM) 追蹤現有的路線。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-104">This section demonstrates how to enable Business Activity Monitor (BAM) tracking for an existing itinerary.</span></span>  
  
 <span data-ttu-id="f8ce1-105">在此 「 如何 」 主題，您將完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="f8ce1-105">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="f8ce1-106">啟用用來追蹤使用 「 商務活動監視器的路線服務的內容。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-106">Enable the property used for tracking Itinerary Services using Business Activity Monitor.</span></span>  
  
-   <span data-ttu-id="f8ce1-107">測試路線測試用戶端範例應用程式中的 BAM 追蹤。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-107">Test BAM tracking using the Itinerary Test Client sample application.</span></span>  
  
-   <span data-ttu-id="f8ce1-108">驗證 BAM 結果使用 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-108">Verify the BAM results using a SQL query.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f8ce1-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="f8ce1-109">Prerequisites</span></span>  
 <span data-ttu-id="f8ce1-110">在此 「 如何 」 主題中的程序需要完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-110">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="f8ce1-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="f8ce1-111">Before You Begin</span></span>  
 <span data-ttu-id="f8ce1-112">在執行本使用說明主題中稍後的步驟之前，請完成下列工作：</span><span class="sxs-lookup"><span data-stu-id="f8ce1-112">Complete the following tasks before you perform the steps later in this How-to topic:</span></span>  
  
-   <span data-ttu-id="f8ce1-113">建立 ESB 路線網域特定領域語言 (DSL) 模型。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-113">Create an ESB itinerary domain-specific language (DSL) model.</span></span>  
  
-   <span data-ttu-id="f8ce1-114">設定屬性的路線。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-114">Configure the properties of the itinerary.</span></span>  
  
-   <span data-ttu-id="f8ce1-115">定義結構的路線。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-115">Define the structure of the itinerary.</span></span>  
  
 <span data-ttu-id="f8ce1-116">下列程序說明如何執行每一種。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-116">The following procedures describe how to do each of these.</span></span>  
  
#### <a name="to-create-an-esb-itinerary-dsl-model"></a><span data-ttu-id="f8ce1-117">若要建立 ESB 路線 DSL 模型</span><span class="sxs-lookup"><span data-stu-id="f8ce1-117">To create an ESB itinerary DSL model</span></span>  
  
1.  <span data-ttu-id="f8ce1-118">在 Visual Studio 中開啟 C:\HowTos\Patterns\Patterns.sln。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-118">In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="f8ce1-119">在 方案總管 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下 **新的行程**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-119">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="f8ce1-120">在**加入新項目**對話方塊中，按一下  **ItineraryDsl**在範本窗格中。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-120">In the **Add New Item** dialog box, click  **ItineraryDsl** in the Templates pane.</span></span>  
  
4.  <span data-ttu-id="f8ce1-121">在**名稱**方塊中，輸入**BamTracking**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-121">In the **Name** box, type **BamTracking**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a><span data-ttu-id="f8ce1-122">若要設定的路線屬性</span><span class="sxs-lookup"><span data-stu-id="f8ce1-122">To configure the properties of the itinerary</span></span>  
  
1.  <span data-ttu-id="f8ce1-123">在 Visual Studio 中，按一下設計介面的**BamTracking.itinerary**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-123">In Visual Studio, click the design surface of **BamTracking.itinerary**.</span></span> <span data-ttu-id="f8ce1-124">在**BamTracking**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="f8ce1-124">In the **BamTracking** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="f8ce1-125">在**模型匯出工具**下拉式清單中，按一下  **XML 路線匯出工具**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-125">In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="f8ce1-126">在**Extender 設定**區段中，旁邊**路線 XML 檔案**屬性，按一下省略符號按鈕 （...）。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-126">In the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).</span></span>  
  
    3.  <span data-ttu-id="f8ce1-127">在**選取 XML 檔案**對話方塊中，於**檔案名稱**方塊中，輸入**C:\HowTos\Itineraries\BamTracking** ，然後按一下 **儲存**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-127">In the **Select XML File** dialog box, in the **File name** box, type **C:\HowTos\Itineraries\BamTracking** and then click **Save**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f8ce1-128">這個步驟可讓您匯出成 XML 的路線，到本機檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-128">This step enables you to export the itinerary as XML to a local file location.</span></span> <span data-ttu-id="f8ce1-129">藉由將行程至本機檔案的位置，而不匯出至路線的資料庫，可讓測試使用 ESB 測試用戶端應用程式的路線。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-129">By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application.</span></span> <span data-ttu-id="f8ce1-130">您將完成此程序，稍後在本使用說明主題。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-130">You will complete this process later in this How-to topic.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="f8ce1-131">若要定義路線結構</span><span class="sxs-lookup"><span data-stu-id="f8ce1-131">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="f8ce1-132">從 [工具箱] 拖曳**上手**至設計介面的模型項目。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-132">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="f8ce1-133">在**OnRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="f8ce1-133">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="f8ce1-134">按一下**名稱**屬性，，然後輸入**ReceiveNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-134">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="f8ce1-135">在**Extender**下拉式清單中，按一下 **上手 ESB 服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-135">In the **Extender** drop-down list, click **On-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="f8ce1-136">在**BizTalk 應用程式**下拉式清單中，按一下  **Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-136">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="f8ce1-137">在**接收埠**下拉式清單中，按一下  **OnRamp.Itinerary**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-137">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="f8ce1-138">從 [工具箱] 拖曳**路線服務**模型項目至設計介面，然後再將它放右邊的**上手**模型項目。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-138">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it to the right of the **On-Ramp** model element.</span></span> <span data-ttu-id="f8ce1-139">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="f8ce1-139">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="f8ce1-140">按一下**名稱**屬性，，然後輸入**MapNAOrderToCNOrder**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-140">Click the **Name** property, and then type **MapNAOrderToCNOrder**.</span></span>  
  
    2.  <span data-ttu-id="f8ce1-141">在**路線服務的擴充項**下拉式清單中，按一下 **傳訊路線服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-141">In the **Itinerary Service Extender** drop-down list, click **Messaging Itinerary Service Extension**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f8ce1-142">這個屬性會定義程序將需要 (messaging) 在管線中的位置。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-142">This property defines that the process will take place in a pipeline (messaging).</span></span> <span data-ttu-id="f8ce1-143">或者，如果處理程序，就會進行協調流程中，設定**路線服務的擴充項**屬性**協調流程路線服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-143">Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Itinerary Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="f8ce1-144">在**容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-144">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="f8ce1-145">在**服務名稱**下拉式清單中，按一下  **Microsoft.Practices.ESB.Services.Transform**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-145">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Transform**.</span></span>  
  
3.  <span data-ttu-id="f8ce1-146">以滑鼠右鍵按一下**解析程式**集合**MapNAOrderToCNOrder**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-146">Right-click the **Resolver** collection of the **MapNAOrderToCNOrder** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="f8ce1-147">在**Resolver1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="f8ce1-147">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="f8ce1-148">按一下**名稱**屬性，，然後輸入**StaticallySpecifyTheMap**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-148">Click the **Name** property, and then type **StaticallySpecifyTheMap**.</span></span>  
  
    2.  <span data-ttu-id="f8ce1-149">在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-149">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="f8ce1-150">在**轉換類型**下拉式清單中，按一下  **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-150">In the **Transform Type** drop-down list, click **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**.</span></span>  
  
    4.  <span data-ttu-id="f8ce1-151">在**TransportName**下拉式清單中，按一下 **檔案**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-151">In the **TransportName** drop-down list, click **FILE**.</span></span>  
  
4.  <span data-ttu-id="f8ce1-152">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-152">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="f8ce1-153">拖曳連接**ReceiveNAOrder**模型項目的**MapNAOrderToCNOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-153">Drag a connection from the **ReceiveNAOrder** model element to the **MapNAOrderToCNOrder** model element.</span></span>  
  
5.  <span data-ttu-id="f8ce1-154">從 [工具箱] 拖曳**匝道**模型項目至設計介面，然後再將它放右邊的**MapNAOrderToCNOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-154">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **MapNAOrderToCNOrder** model element.</span></span> <span data-ttu-id="f8ce1-155">在**OffRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="f8ce1-155">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="f8ce1-156">按一下**名稱**屬性，，然後輸入**SendCNOrder**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-156">Click the **Name** property, and then type **SendCNOrder**.</span></span>  
  
    2.  <span data-ttu-id="f8ce1-157">在**Extender**下拉式清單中，按一下 **匝道 ESB 服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-157">In the **Extender** drop-down list, click **Off-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="f8ce1-158">在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-158">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="f8ce1-159">在**傳送埠**下拉式清單中，按一下  **DynamicResolutionOneWay**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-159">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
6.  <span data-ttu-id="f8ce1-160">從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**MapNAOrderToCNOrder**模型項目和**SendCNOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-160">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **MapNAOrderToCNOrder** model element and the **SendCNOrder** model element.</span></span> <span data-ttu-id="f8ce1-161">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="f8ce1-161">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="f8ce1-162">按一下**名稱**屬性，，然後輸入**SendPortFilter**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-162">Click the **Name** property, and then type **SendPortFilter**.</span></span>  
  
    2.  <span data-ttu-id="f8ce1-163">在**路線服務的擴充項**下拉式清單中，按一下 **匝道路線服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-163">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Itinerary Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="f8ce1-164">在**匝道**下拉式清單中，展開**SendCNOrder**，然後按一下 **傳送處理常式**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-164">In the **Off-Ramp** drop-down list, expand **SendCNOrder**, and then click **Send Handlers**.</span></span>  
  
7.  <span data-ttu-id="f8ce1-165">以滑鼠右鍵按一下**解析程式**集合**SendPortFilter**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-165">Right-click the **Resolver** collection of the **SendPortFilter** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="f8ce1-166">在**Resolver1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="f8ce1-166">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="f8ce1-167">按一下**名稱**屬性，，然後輸入**ConfigureFolderSettings**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-167">Click the **Name** property, and then type **ConfigureFolderSettings**.</span></span>  
  
    2.  <span data-ttu-id="f8ce1-168">在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-168">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="f8ce1-169">在**傳輸名稱**下拉式清單中，按一下 **檔案**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-169">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    4.  <span data-ttu-id="f8ce1-170">按一下**傳輸位置**屬性，，然後輸入**C:\HowTos\Out\BAM%MessageID%.xml**</span><span class="sxs-lookup"><span data-stu-id="f8ce1-170">Click the **Transport Location** property, and then type **C:\HowTos\Out\BAM%MessageID%.xml**</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f8ce1-171">每個匝道會有相關聯的路線服務結合的路線服務屬性以及匝道的屬性來定義動態傳送埠的訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-171">Each off-ramp will have an itinerary service associated with it; the combination of the itinerary service properties and the properties of the off-ramp define the subscription of the dynamic send port.</span></span>  
  
8.  <span data-ttu-id="f8ce1-172">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-172">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="f8ce1-173">拖曳連接**MapNAOrderToCNOrder**模型項目的**SendPortFilter**模型項目。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-173">Drag a connection from the **MapNAOrderToCNOrder** model element to the **SendPortFilter** model element.</span></span>  
  
9. <span data-ttu-id="f8ce1-174">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-174">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="f8ce1-175">拖曳連接**SendPortFilter**模型項目的**SendCNOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-175">Drag a connection from the **SendPortFilter** model element to the **SendCNOrder** model element.</span></span>  
  
10. <span data-ttu-id="f8ce1-176">儲存專案的所有成品。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-176">Save all project artifacts.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="f8ce1-177">步驟</span><span class="sxs-lookup"><span data-stu-id="f8ce1-177">Steps</span></span>  
  
#### <a name="to-modify-the-itinerary"></a><span data-ttu-id="f8ce1-178">若要修改路線</span><span class="sxs-lookup"><span data-stu-id="f8ce1-178">To modify the itinerary</span></span>  
  
1.  <span data-ttu-id="f8ce1-179">在 Visual Studio 中開啟 C:\HowTos\Patterns\Patterns.sln。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-179">In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="f8ce1-180">在 [方案總管] 中，按兩下**BamTracking.itinerary**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-180">In Solution Explorer, double-click **BamTracking.itinerary**.</span></span>  
  
3.  <span data-ttu-id="f8ce1-181">按一下**MapNAOrderToCNOrder**路線服務項目。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-181">Click the **MapNAOrderToCNOrder** itinerary service element.</span></span>  
  
4.  <span data-ttu-id="f8ce1-182">在**MapNAOrderToCNOrder**屬性] 視窗中，按一下 [ **True**中**啟用追蹤**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-182">In the **MapNAOrderToCNOrder** Properties window, click **True** in the **Tracking Enabled** drop-down list.</span></span>  
  
5.  <span data-ttu-id="f8ce1-183">按一下**SendPortFilter**路線服務項目。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-183">Click the **SendPortFilter** itinerary service element.</span></span>  
  
6.  <span data-ttu-id="f8ce1-184">在**SendPortFilter**屬性] 視窗中，按一下 [ **True**中**啟用追蹤**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-184">In the **SendPortFilter** Properties window, click **True** in the **Tracking Enabled** drop-down list.</span></span>  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a><span data-ttu-id="f8ce1-185">若要匯出的行程測試用戶端使用的模型</span><span class="sxs-lookup"><span data-stu-id="f8ce1-185">To export the model for use with the Itinerary Test Client</span></span>  
  
1.  <span data-ttu-id="f8ce1-186">在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**BamTracking**路線，然後再按一下**匯出模型**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-186">In Visual Studio, right-click the design surface of the **BamTracking** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f8ce1-187">在 Visual Studio 中，開啟路線的 XML 版本。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-187">The XML version of the itinerary opens in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="f8ce1-188">儲存專案的所有成品。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-188">Save all project artifacts.</span></span>  
  
3.  <span data-ttu-id="f8ce1-189">在 Windows 檔案總管，瀏覽至 C:\HowTos\Itineraries 並注意您路線 XML (BamTracking.xml) 建立。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-189">In Windows Explorer, browse to C:\HowTos\Itineraries and notice the creation of your itinerary XML (BamTracking.xml).</span></span>  
  
#### <a name="to-test-the-itinerary"></a><span data-ttu-id="f8ce1-190">若要測試路線</span><span class="sxs-lookup"><span data-stu-id="f8ce1-190">To test the itinerary</span></span>  
  
1.  <span data-ttu-id="f8ce1-191">開啟路線測試用戶端範例應用程式使用期間建立的捷徑[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)(C:\HowTos\ESB。Itinerary.Test.exe-捷徑)。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-191">Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).</span></span>  
  
2.  <span data-ttu-id="f8ce1-192">在路線測試用戶端中，清除**使用 WCF 服務**核取方塊，然後**負載路線**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-192">In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.</span></span>  
  
3.  <span data-ttu-id="f8ce1-193">在**開啟路線檔案**對話方塊中，瀏覽至 C:\HowTos\Itineraries。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-193">In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="f8ce1-194">選取**BamTracking.xml**，然後按一下 **開啟**載入路線。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-194">Select **BamTracking.xml**, and then click **Open** to load the itinerary.</span></span>  
  
4.  <span data-ttu-id="f8ce1-195">按一下**確定**清除**路線成功載入**訊息。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-195">Click **OK** to clear the **Itinerary Loaded Successfully** message.</span></span>  
  
5.  <span data-ttu-id="f8ce1-196">在路線測試用戶端中，按一下旁邊的省略符號按鈕 （...）**載入訊息**方塊。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-196">In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.</span></span>  
  
6.  <span data-ttu-id="f8ce1-197">在**選取要載入的 XML 文件**對話方塊中，瀏覽至 C:\HowTos。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-197">In the **Select XML Document to load** dialog box, browse to C:\HowTos.</span></span> <span data-ttu-id="f8ce1-198">選取**NAOrderDoc.xml**，然後按一下 **開啟**載入測試訊息。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-198">Select **NAOrderDoc.xml**, and then click **Open** to load the test message.</span></span>  
  
7.  <span data-ttu-id="f8ce1-199">按一下**送出要求** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-199">Click the **Submit Request** button.</span></span> <span data-ttu-id="f8ce1-200">測試完成時，按一下**確定**解除顯示的確認。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-200">When the test completes, click **OK** to dismiss the confirmation that appears.</span></span>  
  
8.  <span data-ttu-id="f8ce1-201">在 Windows 檔案總管，瀏覽至 C:\HowTos\Out。請確認 BAM%MessageID%.xml 訊息已寫入至目錄。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-201">In Windows Explorer, browse to C:\HowTos\Out. Verify that the BAM%MessageID%.xml message has been written to the directory.</span></span>  
  
#### <a name="to-verify-message-tracking"></a><span data-ttu-id="f8ce1-202">若要驗證的訊息追蹤</span><span class="sxs-lookup"><span data-stu-id="f8ce1-202">To verify message tracking</span></span>  
  
1.  <span data-ttu-id="f8ce1-203">按一下**啟動**在工作列上，指向**所有程式**，指向  [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)]，然後按一下  **SQL Server Management Studio**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-203">Click **Start** on the taskbar, point to **All Programs**, point to [!INCLUDE[SQLServer2008or2005](../includes/sqlserver2008or2005-md.md)], and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="f8ce1-204">按一下 **[新增查詢]**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-204">Click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f8ce1-205">在 [查詢] 窗格中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="f8ce1-205">In the query pane, type the following:</span></span>  
  
    ```  
    SELECT *  
    FROM [BAMPrimaryImport].[dbo].[bam_ItineraryServiceActivity_Completed]  
    GO  
    ```  
  
4.  <span data-ttu-id="f8ce1-206">按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-206">Click **Execute**.</span></span>  
  
5.  <span data-ttu-id="f8ce1-207">在 [結果] 窗格中，使用**時間戳記**找到最新的項目資料行。</span><span class="sxs-lookup"><span data-stu-id="f8ce1-207">In the Results pane, use the **TimeStamp** column to locate the most recent entry.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="f8ce1-208">其他資源</span><span class="sxs-lookup"><span data-stu-id="f8ce1-208">Additional Resources</span></span>  
 <span data-ttu-id="f8ce1-209">如需詳細資訊，請參閱下列相關主題：</span><span class="sxs-lookup"><span data-stu-id="f8ce1-209">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="f8ce1-210">開發活動</span><span class="sxs-lookup"><span data-stu-id="f8ce1-210">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="f8ce1-211">訊息路由模式</span><span class="sxs-lookup"><span data-stu-id="f8ce1-211">Message Routing Patterns</span></span>](../esb-toolkit/message-routing-patterns.md)  
  
-   [<span data-ttu-id="f8ce1-212">使用動態解析和路由</span><span class="sxs-lookup"><span data-stu-id="f8ce1-212">Using Dynamic Resolution and Routing</span></span>](../esb-toolkit/using-dynamic-resolution-and-routing.md)