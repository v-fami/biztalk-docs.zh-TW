---
title: 關於旅 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d34632f-8652-49dd-97b7-2513aacc1bd7
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66a9a759a6afdd55c3c1646d02c480aa193261aa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22290606"
---
# <a name="about-itineraries"></a><span data-ttu-id="7eade-102">有關行程</span><span class="sxs-lookup"><span data-stu-id="7eade-102">About Itineraries</span></span>
<span data-ttu-id="7eade-103">路線是表示，執行一連串的處理指示為基礎的 ESB 中繼原則[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]可擴充的格式。</span><span class="sxs-lookup"><span data-stu-id="7eade-103">An itinerary is a representation of an ESB mediation policy for executing a sequence of processing instructions based on the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] extensible format.</span></span> <span data-ttu-id="7eade-104">行程都可視為說明宣告式路線服務的組態與中繼元件相關聯的一系列的高層級的中繼語言[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]核心引擎。</span><span class="sxs-lookup"><span data-stu-id="7eade-104">An itinerary can be viewed as a high-level mediation language that describes a sequence of declarative itinerary services that are associated with mediation components by configuration of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] core engine.</span></span> <span data-ttu-id="7eade-105">您可以設計中繼流程，以描述訊息應該如何處理，以及您可以將組織為視覺繪圖的整個流程。</span><span class="sxs-lookup"><span data-stu-id="7eade-105">You can design mediation flows to describe how messages should be processed, and you can organize the entire flow as a visual drawing.</span></span> <span data-ttu-id="7eade-106">在執行階段，[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]核心引擎會執行路線設計工具所產生的路線。</span><span class="sxs-lookup"><span data-stu-id="7eade-106">At run time, the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] core engine executes the itinerary produced by Itinerary Designer.</span></span>  
  
## <a name="the-itinerary-designer-surface"></a><span data-ttu-id="7eade-107">在路線設計工具介面</span><span class="sxs-lookup"><span data-stu-id="7eade-107">The Itinerary Designer Surface</span></span>  
 <span data-ttu-id="7eade-108">在路線設計工具介面是用來建立的視覺化設計工具[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]行程並為執行時期格式匯出這些行程。</span><span class="sxs-lookup"><span data-stu-id="7eade-108">The Itinerary Designer surface is a visual designer that is used to create [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] itineraries and to export these itineraries into run-time format.</span></span> <span data-ttu-id="7eade-109">圖 1 所示，它是的畫布，您可以從 [工具箱] 拖曳項目。</span><span class="sxs-lookup"><span data-stu-id="7eade-109">It is a canvas to which you can drag items from the Toolbox, as illustrated in Figure 1.</span></span>  
  
 <span data-ttu-id="7eade-110">![路線設計工具](../esb-toolkit/media/ch5-itinerarydesigner.gif "Ch5 ItineraryDesigner")</span><span class="sxs-lookup"><span data-stu-id="7eade-110">![Itinerary Designer](../esb-toolkit/media/ch5-itinerarydesigner.gif "Ch5-ItineraryDesigner")</span></span>  
  
 <span data-ttu-id="7eade-111">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="7eade-111">**Figure 1**</span></span>  
  
 <span data-ttu-id="7eade-112">**路線設計工具介面**</span><span class="sxs-lookup"><span data-stu-id="7eade-112">**Itinerary Designer surface**</span></span>  
  
 <span data-ttu-id="7eade-113">路線的名稱會顯示在路線設計工具和 Microsoft Visual Studio 標題列中的最上層索引標籤上。</span><span class="sxs-lookup"><span data-stu-id="7eade-113">The name of the itinerary is displayed on the top tab of the Itinerary Designer and in the Microsoft Visual Studio title bar.</span></span> <span data-ttu-id="7eade-114">在設計介面本身是單一區域，並包含描述路線的實際訊息流程的模型項目。</span><span class="sxs-lookup"><span data-stu-id="7eade-114">The design surface itself is a single area and contains model elements that describe the actual message flow of the itinerary.</span></span> <span data-ttu-id="7eade-115">ItineraryDSL 可讓您修改模型項目屬性，使用 Visual Studio 屬性 視窗。</span><span class="sxs-lookup"><span data-stu-id="7eade-115">The ItineraryDSL enables you to modify the model element properties using the Visual Studio Properties window.</span></span>  
  
## <a name="itinerary-designer-toolbox"></a><span data-ttu-id="7eade-116">路線設計工具的工具箱</span><span class="sxs-lookup"><span data-stu-id="7eade-116">Itinerary Designer Toolbox</span></span>  
 <span data-ttu-id="7eade-117">Visual Studio [工具箱] 包含索引標籤，其代表的工具集。</span><span class="sxs-lookup"><span data-stu-id="7eade-117">The Visual Studio Toolbox contains tabs, which represent sets of tools.</span></span> <span data-ttu-id="7eade-118">當您開啟使用路線設計工具的 Visual Studio 專案時，工具箱 包含兩個索引標籤：**一般** 索引標籤和**ItineraryDsl**索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7eade-118">When you open a Visual Studio project that uses Itinerary Designer, the Toolbox contains two tabs: the **General** tab and the **ItineraryDsl** tabs.</span></span> <span data-ttu-id="7eade-119">**ItineraryDsl**  索引標籤包含下列工具：</span><span class="sxs-lookup"><span data-stu-id="7eade-119">The **ItineraryDsl** tab contains the following tools:</span></span>  
  
-   <span data-ttu-id="7eade-120">**路線服務工具**。</span><span class="sxs-lookup"><span data-stu-id="7eade-120">**Itinerary Service tool**.</span></span> <span data-ttu-id="7eade-121">這個模型項目對應至路線中繼服務，並且表示處理指示。</span><span class="sxs-lookup"><span data-stu-id="7eade-121">This model element corresponds to the itinerary mediation service and represents a processing instruction.</span></span>  
  
-   <span data-ttu-id="7eade-122">**連接器工具**。</span><span class="sxs-lookup"><span data-stu-id="7eade-122">**Connector tool**.</span></span> <span data-ttu-id="7eade-123">這個模型項目定義在路線設計工具介面上的個別模型項目之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="7eade-123">This model element defines the relationship between individual model elements on the Itinerary Designer surface.</span></span>  
  
-   <span data-ttu-id="7eade-124">**匝道工具**。</span><span class="sxs-lookup"><span data-stu-id="7eade-124">**Off-Ramp tool**.</span></span> <span data-ttu-id="7eade-125">這個模型項目會對應至匝道傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="7eade-125">This model element corresponds to the off-ramp that sends a message.</span></span> <span data-ttu-id="7eade-126">路線設計工具可讓多個關閉-坡道提升每個模型。</span><span class="sxs-lookup"><span data-stu-id="7eade-126">The Itinerary Designer allows multiple off-ramps per model.</span></span>  
  
-   <span data-ttu-id="7eade-127">**上手工具**。</span><span class="sxs-lookup"><span data-stu-id="7eade-127">**On-Ramp tool**.</span></span> <span data-ttu-id="7eade-128">這個模型項目會對應至上手接收訊息。</span><span class="sxs-lookup"><span data-stu-id="7eade-128">This model element corresponds to an on-ramp that receives a message.</span></span> <span data-ttu-id="7eade-129">路線設計工具可讓您只有一個上手每個模型。</span><span class="sxs-lookup"><span data-stu-id="7eade-129">The Itinerary Designer allows only one on-ramp per model.</span></span>  
  
-   <span data-ttu-id="7eade-130">**路線 Broker 服務工具**。</span><span class="sxs-lookup"><span data-stu-id="7eade-130">**Itinerary Broker Service tool**.</span></span> <span data-ttu-id="7eade-131">這個模型項目對應至路線中繼服務，可讓具有多個輸入和多個輸出的已定義的訊息流程。</span><span class="sxs-lookup"><span data-stu-id="7eade-131">This model element corresponds to the itinerary mediation service that allows defined message flow with multiple inputs and multiple outputs.</span></span>  
  
-   <span data-ttu-id="7eade-132">**路線 Broker 輸出連接埠**。</span><span class="sxs-lookup"><span data-stu-id="7eade-132">**Itinerary Broker Output port**.</span></span> <span data-ttu-id="7eade-133">這個模型項目對應至單一輸出連接埠的行程 Broker 服務。</span><span class="sxs-lookup"><span data-stu-id="7eade-133">This model element corresponds to the single output port of the Itinerary Broker Service.</span></span> <span data-ttu-id="7eade-134">行程 Broker 服務的模型項目可讓多個輸出連接埠。</span><span class="sxs-lookup"><span data-stu-id="7eade-134">The Itinerary Broker Service model element allows multiple output ports.</span></span>  
  
## <a name="steps-in-itinerary-development"></a><span data-ttu-id="7eade-135">路線開發的步驟</span><span class="sxs-lookup"><span data-stu-id="7eade-135">Steps in Itinerary Development</span></span>  
 <span data-ttu-id="7eade-136">若要開發的路線，代表 ESB 中繼流程，您通常應該執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="7eade-136">To develop an itinerary, which represents ESB mediation flow, you should typically perform the following actions:</span></span>  
  
-   <span data-ttu-id="7eade-137">加入模型項目來代表訊息處理步驟，為您的路線。</span><span class="sxs-lookup"><span data-stu-id="7eade-137">Add model elements to represent the message processing steps for your itinerary.</span></span> <span data-ttu-id="7eade-138">路線設計工具提供 [工具箱] 包含用來表示不同的動作或索引鍵的抽象圖案。</span><span class="sxs-lookup"><span data-stu-id="7eade-138">The Itinerary Designer provides a toolbox that contains shapes used to represent different actions or key abstractions.</span></span>  
  
-   <span data-ttu-id="7eade-139">指定路線模型屬性，其中包括 Microsoft BizTalk Server 管理資料庫和模型匯出工具設定的連接字串。</span><span class="sxs-lookup"><span data-stu-id="7eade-139">Specify itinerary model properties, which include a connection string to the Microsoft BizTalk Server management database and model exporter configuration.</span></span>  
  
-   <span data-ttu-id="7eade-140">上手和匝道模型項目繫結實體的 BizTalk 接收位置和傳送埠將這些模型項目與對應的技術擴充項產生關聯。</span><span class="sxs-lookup"><span data-stu-id="7eade-140">Bind on-ramp and off-ramp model elements to physical BizTalk receive locations and send ports by associating these model elements with corresponding technology extenders.</span></span>  
  
-   <span data-ttu-id="7eade-141">關聯 extender 路線服務的模型項目，以及定義所需的擴充項的技術專屬屬性。</span><span class="sxs-lookup"><span data-stu-id="7eade-141">Associate itinerary services model elements with extenders and define technology-specific properties required by an extender.</span></span> <span data-ttu-id="7eade-142">這些屬性而異的特定類型的擴充性;其可代表路線中繼服務屬性和相關聯的執行階段元件和成品的 BizTalk 特定屬性。</span><span class="sxs-lookup"><span data-stu-id="7eade-142">These properties may vary for a particular type of the extender; they can represent itinerary mediation service properties and BizTalk-specific properties associated with its run-time components and artifacts.</span></span>  
  
-   <span data-ttu-id="7eade-143">識別要參考為路線中繼服務自訂元件。</span><span class="sxs-lookup"><span data-stu-id="7eade-143">Identify custom components that you might want to reference as itinerary mediation services.</span></span> <span data-ttu-id="7eade-144">例如，您可能會開發為路線服務的協調流程。</span><span class="sxs-lookup"><span data-stu-id="7eade-144">For example, you may develop an orchestration as the itinerary service.</span></span>  
  
-   <span data-ttu-id="7eade-145">請確認針對解析程式模型項目設定[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]叫用從設計工具介面的解析程式服務的執行階段組態。</span><span class="sxs-lookup"><span data-stu-id="7eade-145">Verify resolver model element settings against [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] run-time configuration by invoking resolver service from the designer surface.</span></span>  
  
-   <span data-ttu-id="7eade-146">驗證並匯出路線使用匯出工具的執行階段原則。</span><span class="sxs-lookup"><span data-stu-id="7eade-146">Validate and export the itinerary run-time policy using an exporter.</span></span> <span data-ttu-id="7eade-147">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]與路線設計工具提供兩個匯出工具： 檔案匯出工具和資料庫匯出工具。</span><span class="sxs-lookup"><span data-stu-id="7eade-147">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] provides two exporters with the Itinerary Designer: file exporter and database exporter.</span></span> <span data-ttu-id="7eade-148">或者，您可以實作自訂匯出工具。</span><span class="sxs-lookup"><span data-stu-id="7eade-148">Alternatively, you can implement a custom exporter.</span></span>  
  
-   <span data-ttu-id="7eade-149">測試使用測試用戶端應用程式或 BizUnit framework 您路線。</span><span class="sxs-lookup"><span data-stu-id="7eade-149">Test your itinerary using test client applications or BizUnit framework.</span></span>  
  
## <a name="security-considerations-for-developing-itineraries"></a><span data-ttu-id="7eade-150">開發行程的安全性考量</span><span class="sxs-lookup"><span data-stu-id="7eade-150">Security Considerations for Developing Itineraries</span></span>  
 <span data-ttu-id="7eade-151">當您設計旅時，您應該考慮潛在的安全性問題：</span><span class="sxs-lookup"><span data-stu-id="7eade-151">When you design itineraries, you should consider potential security issues:</span></span>  
  
-   <span data-ttu-id="7eade-152">應避免指定使用者認證，而不使用模型內容中的憑證。</span><span class="sxs-lookup"><span data-stu-id="7eade-152">Avoid specifying user credentials without using a certificate from the model properties.</span></span>  
  
-   <span data-ttu-id="7eade-153">並未參考 BizTalk 接收埠與接收 允許匿名存取的位置。</span><span class="sxs-lookup"><span data-stu-id="7eade-153">Do not refer to BizTalk receive ports with receive locations that allow anonymous access.</span></span>  
  
-   <span data-ttu-id="7eade-154">如果路線訊息包含敏感性資料，請保護訊息或傳輸通道。</span><span class="sxs-lookup"><span data-stu-id="7eade-154">Protect the message or transport channel if the itinerary message contains sensitive data.</span></span>  
  
-   <span data-ttu-id="7eade-155">如果訊息包含需要保護傳輸中的敏感性資料來保護訊息的訊息方塊具有管線元件中。</span><span class="sxs-lookup"><span data-stu-id="7eade-155">Protect messages in the Message box with a pipeline component if the messages contain sensitive data that needs to be protected while in transit.</span></span>