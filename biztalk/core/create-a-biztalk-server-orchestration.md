---
title: "建立 BizTalk Server 協調流程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16c637ae-f94f-40f8-8ce7-73a7b7df9f8f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6223ab8d8aa3c8d1c20559a88257dd0dccaa22e
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="create-a-biztalk-server-orchestration"></a><span data-ttu-id="a7a34-102">建立 BizTalk Server 協調流程</span><span class="sxs-lookup"><span data-stu-id="a7a34-102">Create a BizTalk Server orchestration</span></span>
> [!NOTE]
>  <span data-ttu-id="a7a34-103">本教學課程僅適用於 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="a7a34-103">This tutorial applies to BizTalk Server only.</span></span>  
  
 <span data-ttu-id="a7a34-104">建立一個 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 協調流程，在部署時，接收 JSON 訂單訊息，並將其轉換為 XML 發票，再傳送出 JSON 發票。</span><span class="sxs-lookup"><span data-stu-id="a7a34-104">Create a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration that, when deployed, receives a JSON purchase order message, transforms it to an XML invoice, and then sends out a JSON invoice.</span></span>  
  
## <a name="define-message-and-message-types"></a><span data-ttu-id="a7a34-105">定義訊息及訊息類型</span><span class="sxs-lookup"><span data-stu-id="a7a34-105">Define message and message types</span></span>  
 <span data-ttu-id="a7a34-106">此方案適用於兩個基本訊息，也就是訂單及發票。</span><span class="sxs-lookup"><span data-stu-id="a7a34-106">This solution works with two basic messages – purchase order and invoice.</span></span> <span data-ttu-id="a7a34-107">我們已經使用 JSON 結構描述精靈從 JSON 訊息產生了訂單結構描述。</span><span class="sxs-lookup"><span data-stu-id="a7a34-107">We already generated the schema of the purchase order from a JSON message using the JSON schema wizard.</span></span> <span data-ttu-id="a7a34-108">本教學課程提供的範例已具備發票訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="a7a34-108">The sample provided for this tutorial already has the schema for the invoice message.</span></span> <span data-ttu-id="a7a34-109">我們使用這些結構描述在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式中建立訊息類型。</span><span class="sxs-lookup"><span data-stu-id="a7a34-109">We use these schemas to create the message types in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application.</span></span>  
  
1.  <span data-ttu-id="a7a34-110">在 BizTalk 專案中新增協調流程，並開啟協調流程檢視。</span><span class="sxs-lookup"><span data-stu-id="a7a34-110">Add an orchestration to the BizTalk project and open the Orchestration view.</span></span>  
  
2.  <span data-ttu-id="a7a34-111">在協調流程檢視中，以滑鼠右鍵按一下**訊息**，然後按一下 **新訊息**。</span><span class="sxs-lookup"><span data-stu-id="a7a34-111">In the Orchestration View, right-click **Messages**, and then click **New Message**.</span></span>  
  
3.  <span data-ttu-id="a7a34-112">以滑鼠右鍵按一下新建立的訊息，然後選取**屬性 視窗**。</span><span class="sxs-lookup"><span data-stu-id="a7a34-112">Right-click the newly created message, and then select **Properties Window**.</span></span>  
  
4.  <span data-ttu-id="a7a34-113">在**屬性**窗格**Message_1**，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a7a34-113">In the **Properties** pane for the **Message_1**, do the following:</span></span>  
  
    |<span data-ttu-id="a7a34-114">使用</span><span class="sxs-lookup"><span data-stu-id="a7a34-114">Use this</span></span>|<span data-ttu-id="a7a34-115">動作</span><span class="sxs-lookup"><span data-stu-id="a7a34-115">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="a7a34-116">識別碼</span><span class="sxs-lookup"><span data-stu-id="a7a34-116">Identifier</span></span>|<span data-ttu-id="a7a34-117">輸入 `PurchaseOrder`</span><span class="sxs-lookup"><span data-stu-id="a7a34-117">Type `PurchaseOrder`</span></span>|  
    |<span data-ttu-id="a7a34-118">訊息類型</span><span class="sxs-lookup"><span data-stu-id="a7a34-118">Message Type</span></span>|<span data-ttu-id="a7a34-119">從下拉式清單中，展開 **結構描述**，然後選取*BTSJSO。PO*，其中*BTSJSO*是您的 BizTalk 專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="a7a34-119">From the drop-down list, expand **Schemas**, and then select *BTSJSON.PO*, where *BTSJSON* is the name of your BizTalk project.</span></span>|  
  
5.  <span data-ttu-id="a7a34-120">重覆上述步驟為發票訊息建立新的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="a7a34-120">Repeat the previous step to create a new message type for the invoice message.</span></span> <span data-ttu-id="a7a34-121">在**屬性**窗格新訊息中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="a7a34-121">In the **Properties** pane for the new message, do the following:</span></span>  
  
    |<span data-ttu-id="a7a34-122">使用</span><span class="sxs-lookup"><span data-stu-id="a7a34-122">Use this</span></span>|<span data-ttu-id="a7a34-123">動作</span><span class="sxs-lookup"><span data-stu-id="a7a34-123">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="a7a34-124">識別碼</span><span class="sxs-lookup"><span data-stu-id="a7a34-124">Identifier</span></span>|<span data-ttu-id="a7a34-125">輸入 `InvoiceMsg`</span><span class="sxs-lookup"><span data-stu-id="a7a34-125">Type `InvoiceMsg`</span></span>|  
    |<span data-ttu-id="a7a34-126">訊息類型</span><span class="sxs-lookup"><span data-stu-id="a7a34-126">Message Type</span></span>|<span data-ttu-id="a7a34-127">從下拉式清單中，展開 **結構描述**，然後選取*BTSJSO。發票*。</span><span class="sxs-lookup"><span data-stu-id="a7a34-127">From the drop-down list, expand **Schemas**, and then select *BTSJSON.Invoice*.</span></span>|  
  
## <a name="set-up-the-orchestration"></a><span data-ttu-id="a7a34-128">設定協調流程</span><span class="sxs-lookup"><span data-stu-id="a7a34-128">Set up the orchestration</span></span>  
 <span data-ttu-id="a7a34-129">在這個步驟中，您會新增訊息圖形以及連接埠來建立協調流程。</span><span class="sxs-lookup"><span data-stu-id="a7a34-129">In this step, you add message shapes and ports to create an orchestration.</span></span>  
  
### <a name="add-message-shapes"></a><span data-ttu-id="a7a34-130">新增訊息圖形</span><span class="sxs-lookup"><span data-stu-id="a7a34-130">Add message shapes</span></span>  
 <span data-ttu-id="a7a34-131">從 [方案總管] 中開啟協調流程檔案，並新增下列訊息圖形。</span><span class="sxs-lookup"><span data-stu-id="a7a34-131">Open the orchestration file from Solution Explorer, and add the following message shapes.</span></span>  
  
-   <span data-ttu-id="a7a34-132">新增 「 接收 」 圖形，將其名稱設**ReceivePO**，訊息類型來**PurchaseOrder**。</span><span class="sxs-lookup"><span data-stu-id="a7a34-132">Add a Receive shape, set its name to **ReceivePO**, and message type to **PurchaseOrder**.</span></span>  
  
-   <span data-ttu-id="a7a34-133">新增 「 傳送 」 圖形，將其名稱設**SendInvoice**，訊息類型來**InvoiceMsg**。</span><span class="sxs-lookup"><span data-stu-id="a7a34-133">Add a Send shape, set its name to **SendInvoice**, and message type to **InvoiceMsg**.</span></span>  
  
-   <span data-ttu-id="a7a34-134">新增 [建構訊息圖形，並設定**建構的訊息**屬性建構訊息] 圖形的**InvoiceMsg**。</span><span class="sxs-lookup"><span data-stu-id="a7a34-134">Add a Construct Message shape and set the **Messages Constructed** property of the Construct Message shape to **InvoiceMsg**.</span></span>  
  
-   <span data-ttu-id="a7a34-135">在建構訊息圖形中，新增轉換圖形。</span><span class="sxs-lookup"><span data-stu-id="a7a34-135">Add a Transform shape within the Construct Message shape.</span></span> <span data-ttu-id="a7a34-136">按兩下 「 轉換 」 圖形和**轉換組態**對話方塊中，選取**現有對應**選項，然後再選取**BTSJSO。Testmap**對應。</span><span class="sxs-lookup"><span data-stu-id="a7a34-136">Double-click the Transform shape and in the **Transform Configuration** dialog box, select the **Existing Map** option, and then select **BTSJSON.POToInvoice** map.</span></span> <span data-ttu-id="a7a34-137">此對應為範例的一部分。</span><span class="sxs-lookup"><span data-stu-id="a7a34-137">This map is provided as part of the sample.</span></span> <span data-ttu-id="a7a34-138">在對話方塊中，設定**來源**至**PurchaseOrder**並設定**目的地**至**InvoiceMsg**。</span><span class="sxs-lookup"><span data-stu-id="a7a34-138">In the dialog box, set **Source** to **PurchaseOrder** and set **Destination** to **InvoiceMsg**.</span></span> <span data-ttu-id="a7a34-139">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="a7a34-139">Click **OK**.</span></span>  
  
### <a name="add-ports"></a><span data-ttu-id="a7a34-140">新增連接埠</span><span class="sxs-lookup"><span data-stu-id="a7a34-140">Add ports</span></span>  
 <span data-ttu-id="a7a34-141">在協調流程中新增兩個連接埠，一個供接收訊息用，另一個供傳送訊息用。</span><span class="sxs-lookup"><span data-stu-id="a7a34-141">Add two ports to the orchestration – one for receiving messages and one for sending messages.</span></span> <span data-ttu-id="a7a34-142">使用連接埠的下列屬性。</span><span class="sxs-lookup"><span data-stu-id="a7a34-142">Use the following properties for the ports.</span></span>  
  
|<span data-ttu-id="a7a34-143">通訊埠</span><span class="sxs-lookup"><span data-stu-id="a7a34-143">Port</span></span>|<span data-ttu-id="a7a34-144">屬性</span><span class="sxs-lookup"><span data-stu-id="a7a34-144">Properties</span></span>|  
|----------|----------------|  
|<span data-ttu-id="a7a34-145">MessageIn</span><span class="sxs-lookup"><span data-stu-id="a7a34-145">MessageIn</span></span>|<span data-ttu-id="a7a34-146">-設定**識別碼**至*ReceiveJSONPO*</span><span class="sxs-lookup"><span data-stu-id="a7a34-146">-   Set **Identifier** to *ReceiveJSONPO*</span></span><br /><span data-ttu-id="a7a34-147">-設定**通訊模式**至*單向*</span><span class="sxs-lookup"><span data-stu-id="a7a34-147">-   Set **Communication Pattern** to *One-Way*</span></span><br /><span data-ttu-id="a7a34-148">-設定**通訊方向**至*接收*</span><span class="sxs-lookup"><span data-stu-id="a7a34-148">-   Set **Communication Direction** to *Receive*</span></span>|  
|<span data-ttu-id="a7a34-149">ResponseOut</span><span class="sxs-lookup"><span data-stu-id="a7a34-149">ResponseOut</span></span>|<span data-ttu-id="a7a34-150">-設定**識別碼**至*SendJSONInvoice*</span><span class="sxs-lookup"><span data-stu-id="a7a34-150">-   Set **Identifier** to *SendJSONInvoice*</span></span><br /><span data-ttu-id="a7a34-151">-設定**通訊模式**至*單向*</span><span class="sxs-lookup"><span data-stu-id="a7a34-151">-   Set **Communication Pattern** to *One-Way*</span></span><br /><span data-ttu-id="a7a34-152">-設定**通訊方向**至*傳送*</span><span class="sxs-lookup"><span data-stu-id="a7a34-152">-   Set **Communication Direction** to *Send*</span></span>|  
  
 <span data-ttu-id="a7a34-153">連接連接埠和訊息圖形，如以下螢幕擷取畫面所示，再儲存專案的變更。</span><span class="sxs-lookup"><span data-stu-id="a7a34-153">Connect the ports and message shape, as shown in the screenshot below, and save changes to the project.</span></span>  
  
 <span data-ttu-id="a7a34-154">![處理 JSON 訊息的協調流程](../core/media/btsjson-orchestration.png "BTSJSON_Orchestration")</span><span class="sxs-lookup"><span data-stu-id="a7a34-154">![Orchestration to process JSON messages](../core/media/btsjson-orchestration.png "BTSJSON_Orchestration")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7a34-155">請參閱</span><span class="sxs-lookup"><span data-stu-id="a7a34-155">See Also</span></span>  
 [<span data-ttu-id="a7a34-156">使用 BizTalk Server 處理 JSON 訊息</span><span class="sxs-lookup"><span data-stu-id="a7a34-156">Processing JSON messages using BizTalk Server</span></span>](../core/processing-json-messages-using-biztalk-server.md)