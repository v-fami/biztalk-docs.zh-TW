---
title: 如何： 轉換訊息，並將產生的訊息路由至使用路線的路由名單的檔案位置 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c27749ba-c228-4cd4-827e-e8009a0c999d
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 01a20c7c4a58a12f242cbd412c23e2d2fa9fe24f
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26010543"
---
# <a name="how-to-transform-a-message-and-route-the-resulting-message-to-a-file-location-using-an-itinerary-routing-slip"></a><span data-ttu-id="5ea3d-102">如何： 轉換訊息，並將產生的訊息路由至使用路線的路由名單的檔案位置</span><span class="sxs-lookup"><span data-stu-id="5ea3d-102">How to: Transform a Message and Route the Resulting Message to a File Location Using an Itinerary Routing Slip</span></span>
## <a name="goal"></a><span data-ttu-id="5ea3d-103">目標</span><span class="sxs-lookup"><span data-stu-id="5ea3d-103">Goal</span></span>  
 <span data-ttu-id="5ea3d-104">本節示範如何建立實作訊息轉換，藉由叫用 BizTalk 對應，行程使用 ESB 設計工具的特定領域語言 (DSL)，然後將使用的訊息路由傳送[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]FILE 配接器。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-104">This section demonstrates how to use the ESB Designer domain-specific language (DSL) to create an itinerary that implements message transformation by invoking a BizTalk map, and then it routes the messages using the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] FILE adapter.</span></span>  
  
 <span data-ttu-id="5ea3d-105">在此 「 如何 」 主題，您將完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="5ea3d-105">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="5ea3d-106">建立路線的路由名單實作 BizTalk 對應轉換路線服務。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-106">Create an itinerary routing slip with a transform itinerary service that implements a BizTalk map.</span></span>  
  
-   <span data-ttu-id="5ea3d-107">設定轉換後的訊息路由傳送至檔案位置路線。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-107">Configure the itinerary to route the transformed message to a file location.</span></span>  
  
-   <span data-ttu-id="5ea3d-108">測試使用路線測試用戶端範例應用程式的路線。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-108">Test the itinerary using the Itinerary Test Client sample application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5ea3d-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="5ea3d-109">Prerequisites</span></span>  
 <span data-ttu-id="5ea3d-110">在此 「 如何 」 主題中的程序需要完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-110">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="steps"></a><span data-ttu-id="5ea3d-111">步驟</span><span class="sxs-lookup"><span data-stu-id="5ea3d-111">Steps</span></span>  
  
#### <a name="to-create-an-esb-itinerary-dsl-model"></a><span data-ttu-id="5ea3d-112">若要建立 ESB 路線 DSL 模型</span><span class="sxs-lookup"><span data-stu-id="5ea3d-112">To create an ESB itinerary DSL model</span></span>  
  
1.  <span data-ttu-id="5ea3d-113">在 Visual Studio 中開啟 C:\HowTos\Patterns\Patterns.sln。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-113">In Visual Studio, open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="5ea3d-114">在 方案總管 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下 **新的行程**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-114">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="5ea3d-115">在**加入新項目**對話方塊中，按一下  **ItineraryDsl**在範本窗格中。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-115">In the **Add New Item** dialog box, click **ItineraryDsl** in the Templates pane.</span></span>  
  
4.  <span data-ttu-id="5ea3d-116">在**名稱**方塊中，輸入**DataModelTransformation**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-116">In the **Name** box, type **DataModelTransformation**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a><span data-ttu-id="5ea3d-117">若要設定的路線屬性</span><span class="sxs-lookup"><span data-stu-id="5ea3d-117">To configure the properties of the itinerary</span></span>  
  
1.  <span data-ttu-id="5ea3d-118">在 Visual Studio 中，按一下設計介面的**DataModelTransformation.itinerary**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-118">In Visual Studio, click the design surface of **DataModelTransformation.itinerary**.</span></span> <span data-ttu-id="5ea3d-119">在**DataModelTransformation**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="5ea3d-119">In the **DataModelTransformation** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="5ea3d-120">在**模型匯出工具**下拉式清單中，按一下  **XML 路線匯出工具**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-120">In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="5ea3d-121">在**Extender 設定**區段中，旁邊**路線 XML 檔案**屬性，按一下省略符號按鈕 （...）。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-121">In the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).</span></span>  
  
    3.  <span data-ttu-id="5ea3d-122">在**選取 XML 檔案**對話方塊中，於**檔案名稱**方塊中，輸入**C:\HowTos\Itineraries\DataModelTransformation**，然後按一下 **儲存**.</span><span class="sxs-lookup"><span data-stu-id="5ea3d-122">In the **Select XML File** dialog box, in the **File name** box, type **C:\HowTos\Itineraries\DataModelTransformation**, and then click **Save**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="5ea3d-123">這個步驟可讓您匯出成 XML 的路線，到本機檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-123">This step enables you to export the itinerary as XML to a local file location.</span></span> <span data-ttu-id="5ea3d-124">藉由將行程至本機檔案的位置，而不匯出至路線的資料庫，可讓測試使用 ESB 測試用戶端應用程式的路線。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-124">By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application.</span></span> <span data-ttu-id="5ea3d-125">您將完成此程序，稍後在本使用說明主題。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-125">You will complete this process later in this How-to topic.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="5ea3d-126">若要定義路線結構</span><span class="sxs-lookup"><span data-stu-id="5ea3d-126">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="5ea3d-127">從 [工具箱] 拖曳**上手**至設計介面的模型項目。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-127">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="5ea3d-128">在**OnRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="5ea3d-128">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="5ea3d-129">按一下**名稱**屬性，，然後輸入**ReceiveNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-129">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="5ea3d-130">在**Extender**下拉式清單中，按一下 **上手 ESB 服務延伸模組**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-130">In the **Extender** drop-down list, click **On-Ramp ESB Service Extension**.</span></span>  
  
    3.  <span data-ttu-id="5ea3d-131">在**BizTalk 應用程式**下拉式清單中，按一下  **Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-131">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="5ea3d-132">在**接收埠**下拉式清單中，按一下  **OnRamp.Itinerary**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-132">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="5ea3d-133">從 [工具箱] 拖曳**路線服務**模型項目至設計介面，然後再將它放右邊的**上手**模型項目。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-133">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it to the right of the **On-Ramp** model element.</span></span> <span data-ttu-id="5ea3d-134">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="5ea3d-134">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="5ea3d-135">按一下**名稱**屬性，，然後輸入**MapNAOrderToCNOrder**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-135">Click the **Name** property, and then type **MapNAOrderToCNOrder**.</span></span>  
  
    2.  <span data-ttu-id="5ea3d-136">在**路線服務的擴充項**下拉式清單中，按一下 **傳訊 Extender**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-136">In the **Itinerary Service Extender** drop-down list, click **Messaging Extender**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="5ea3d-137">這個屬性會定義程序將需要 (messaging) 在管線中的位置。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-137">This property defines that the process will take place in a pipeline (messaging).</span></span> <span data-ttu-id="5ea3d-138">或者，如果處理程序，就會進行協調流程中，設定**路線服務的擴充項**屬性**協調流程 Extender**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-138">Alternately, if the process will take place in an orchestration, set the **Itinerary Service Extender** property to **Orchestration Extender**.</span></span>  
  
    3.  <span data-ttu-id="5ea3d-139">在**容器**下拉式清單中，展開**ReceiveNAOrder**，然後按一下 **接收處理常式**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-139">In the **Container** drop-down list, expand **ReceiveNAOrder**, and then click **Receive Handlers**.</span></span>  
  
    4.  <span data-ttu-id="5ea3d-140">在**服務名稱**下拉式清單中，按一下  **Microsoft.Practices.ESB.Services.Transform**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-140">In the **Service Name** drop-down list, click **Microsoft.Practices.ESB.Services.Transform**.</span></span>  
  
3.  <span data-ttu-id="5ea3d-141">以滑鼠右鍵按一下**解析程式**集合**MapNAOrderToCNOrder**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-141">Right-click the **Resolver** collection of the **MapNAOrderToCNOrder** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="5ea3d-142">在**Resolver1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="5ea3d-142">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="5ea3d-143">按一下**名稱**屬性，，然後輸入**StaticallySpecifyTheMap**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-143">Click the **Name** property, and then type **StaticallySpecifyTheMap**.</span></span>  
  
    2.  <span data-ttu-id="5ea3d-144">在**解析程式實作**下拉式清單中，按一下 **靜態解析程式擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-144">In the **Resolver Implementation** drop-down list, click **Static Resolver Extension**.</span></span>  
  
    3.  <span data-ttu-id="5ea3d-145">在**轉換類型**下拉式清單中，按一下  **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-145">In the **Transform Type** drop-down list, click **GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN**.</span></span>  
  
    4.  <span data-ttu-id="5ea3d-146">在**傳輸名稱**下拉式清單中，按一下 **檔案**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-146">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
4.  <span data-ttu-id="5ea3d-147">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-147">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="5ea3d-148">拖曳連接**ReceiveNAOrder**模型項目的**MapNAOrderToCNOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-148">Drag a connection from the **ReceiveNAOrder** model element to the **MapNAOrderToCNOrder** model element.</span></span>  
  
5.  <span data-ttu-id="5ea3d-149">從 [工具箱] 拖曳**匝道**模型項目至設計介面，然後再將它放右邊的**MapNAOrderToCNOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-149">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **MapNAOrderToCNOrder** model element.</span></span> <span data-ttu-id="5ea3d-150">在**OffRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="5ea3d-150">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="5ea3d-151">按一下**名稱**屬性，，然後輸入**SendCNOrder**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-151">Click the **Name** property, and then type **SendCNOrder**.</span></span>  
  
    2.  <span data-ttu-id="5ea3d-152">在**Extender**下拉式清單中，按一下 **匝道 ESB Extender**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-152">In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="5ea3d-153">在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-153">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="5ea3d-154">在**傳送埠**下拉式清單中，按一下  **DynamicResolutionOneWay**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-154">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
6.  <span data-ttu-id="5ea3d-155">從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**MapNAOrderToCNOrder**模型項目和**SendCNOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-155">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **MapNAOrderToCNOrder** model element and the **SendCNOrder** model element.</span></span> <span data-ttu-id="5ea3d-156">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="5ea3d-156">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="5ea3d-157">按一下**名稱**屬性，，然後輸入**SendPortFilter**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-157">Click the **Name** property, and then type **SendPortFilter**.</span></span>  
  
    2.  <span data-ttu-id="5ea3d-158">在**路線服務的擴充項**下拉式清單中，按一下 **匝道 Extender**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-158">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="5ea3d-159">在**匝道**下拉式清單中，展開**SendCNOrder**，然後按一下 **傳送處理常式**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-159">In the **Off-Ramp** drop-down list, expand **SendCNOrder**, and then click **Send Handlers**.</span></span>  
  
7.  <span data-ttu-id="5ea3d-160">以滑鼠右鍵按一下**解析程式**集合**SendPortFilter**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-160">Right-click the **Resolver** collection of the **SendPortFilter** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="5ea3d-161">在**Resolver1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="5ea3d-161">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="5ea3d-162">按一下**名稱**屬性，，然後輸入**ConfigureFolderSettings**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-162">Click the **Name** property, and then type **ConfigureFolderSettings**.</span></span>  
  
    2.  <span data-ttu-id="5ea3d-163">在**傳輸名稱**下拉式清單中，按一下 **檔案**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-163">In the **Transport Name** drop-down list, click **FILE**.</span></span>  
  
    3.  <span data-ttu-id="5ea3d-164">按一下**傳輸位置**屬性，，然後輸入**C:\HowTos\Out\\%MessageID%.xml**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-164">Click the **Transport Location** property, and then type **C:\HowTos\Out\\%MessageID%.xml**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="5ea3d-165">每個匝道會有相關聯路線服務結合的行程服務屬性以及匝道的屬性來定義動態傳送埠的訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-165">Each off-ramp will have an Itinerary Service associated with it; the combination of the Itinerary Service properties and the properties of the off-ramp define the subscription of the dynamic send port.</span></span>  
  
8.  <span data-ttu-id="5ea3d-166">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-166">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="5ea3d-167">拖曳連接**MapNAOrderToCNOrder**模型項目的**SendPortFilter**模型項目。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-167">Drag a connection from the **MapNAOrderToCNOrder** model element to the **SendPortFilter** model element.</span></span>  
  
9. <span data-ttu-id="5ea3d-168">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-168">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="5ea3d-169">拖曳連接**SendPortFilter**模型項目的**SendCNOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-169">Drag a connection from the **SendPortFilter** model element to the **SendCNOrder** model element.</span></span>  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a><span data-ttu-id="5ea3d-170">若要匯出的行程測試用戶端使用的模型</span><span class="sxs-lookup"><span data-stu-id="5ea3d-170">To export the model for use with the Itinerary Test Client</span></span>  
  
1.  <span data-ttu-id="5ea3d-171">在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**DataModelTransformation**路線，然後再按一下**匯出模型**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-171">In Visual Studio, right-click the design surface of the **DataModelTransformation** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5ea3d-172">在 Visual Studio 中，開啟路線的 XML 版本。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-172">The XML version of the itinerary opens in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="5ea3d-173">儲存專案的所有成品。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-173">Save all project artifacts.</span></span>  
  
3.  <span data-ttu-id="5ea3d-174">在 Windows 檔案總管，瀏覽至 C:\HowTos\Itineraries 並注意您路線 XML (DataModelTransformation.xml) 建立。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-174">In Windows Explorer, browse to C:\HowTos\Itineraries and notice the creation of your itinerary XML (DataModelTransformation.xml).</span></span>  
  
#### <a name="to-test-the-itinerary"></a><span data-ttu-id="5ea3d-175">若要測試路線</span><span class="sxs-lookup"><span data-stu-id="5ea3d-175">To test the itinerary</span></span>  
  
1.  <span data-ttu-id="5ea3d-176">開啟路線測試用戶端範例應用程式使用期間建立的捷徑[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)(C:\HowTos\ESB。Itinerary.Test.exe-捷徑)。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-176">Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).</span></span>  
  
2.  <span data-ttu-id="5ea3d-177">在路線測試用戶端中，清除**使用 WCF 服務**核取方塊，然後**負載路線**。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-177">In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.</span></span>  
  
3.  <span data-ttu-id="5ea3d-178">在**開啟路線檔案**對話方塊中，瀏覽至 C:\HowTos\Itineraries。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-178">In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="5ea3d-179">選取**DataModelTransformation.xml**，然後按一下 **開啟**載入路線。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-179">Select **DataModelTransformation.xml**, and then click **Open** to load the itinerary.</span></span>  
  
4.  <span data-ttu-id="5ea3d-180">按一下**確定**清除**路線成功載入**訊息。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-180">Click **OK** to clear the **Itinerary Loaded Successfully** message.</span></span>  
  
5.  <span data-ttu-id="5ea3d-181">在路線測試用戶端中，按一下旁邊的省略符號按鈕 （...）**載入訊息**方塊。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-181">In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.</span></span>  
  
6.  <span data-ttu-id="5ea3d-182">在**選取要載入的 XML 文件**對話方塊中，瀏覽至 C:\HowTos。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-182">In the **Select XML Document to load** dialog box, browse to C:\HowTos.</span></span> <span data-ttu-id="5ea3d-183">選取**NAOrderDoc.xml**，然後按一下 **開啟**載入測試訊息。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-183">Select **NAOrderDoc.xml**, and then click **Open** to load the test message.</span></span>  
  
7.  <span data-ttu-id="5ea3d-184">按一下**送出要求** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-184">Click the **Submit Request** button.</span></span> <span data-ttu-id="5ea3d-185">測試完成時，按一下**確定**解除顯示的確認。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-185">When the test completes, click **OK** to dismiss the confirmation that appears.</span></span>  
  
8.  <span data-ttu-id="5ea3d-186">在 Windows 檔案總管，瀏覽至 C:\HowTos\Out。確認 **%MessageID%.xml**訊息寫入目錄。</span><span class="sxs-lookup"><span data-stu-id="5ea3d-186">In Windows Explorer, browse to C:\HowTos\Out. Verify that the **%MessageID%.xml** message has been written to the directory.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="5ea3d-187">其他資源</span><span class="sxs-lookup"><span data-stu-id="5ea3d-187">Additional Resources</span></span>  
 <span data-ttu-id="5ea3d-188">如需詳細資訊，請參閱這些相關主題：</span><span class="sxs-lookup"><span data-stu-id="5ea3d-188">For more information, see these related topics:</span></span>  
  
1.  [<span data-ttu-id="5ea3d-189">如何：分割交換，並使用不同路線將產生的訊息路由至多個檔案位置</span><span class="sxs-lookup"><span data-stu-id="5ea3d-189">How to: Split an Interchange and Route the Resulting Messages to Multiple File Locations Using Distinct Itineraries</span></span>](../esb-toolkit/split-an-interchange-and-route-messages-to-multiple-locations-using-itineraries.md)  
  
2.  [<span data-ttu-id="5ea3d-190">開發活動</span><span class="sxs-lookup"><span data-stu-id="5ea3d-190">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
3.  [<span data-ttu-id="5ea3d-191">訊息轉換模式</span><span class="sxs-lookup"><span data-stu-id="5ea3d-191">Message Transformation Patterns</span></span>](../esb-toolkit/message-transformation-patterns.md)