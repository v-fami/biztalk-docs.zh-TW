---
title: "組合批次的 EDI 交換 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18f64595-935e-4d52-9ec2-5edf7c2b9e83
caps.latest.revision: "45"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c4274362e5ec8441e203d0b2b97f27e95235fd9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="assembling-a-batched-edi-interchange"></a><span data-ttu-id="78991-102">組合批次 EDI 交換</span><span class="sxs-lookup"><span data-stu-id="78991-102">Assembling a Batched EDI Interchange</span></span>
<span data-ttu-id="78991-103">若要將個別的交易集批次元素組合成 EDI 交換， [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI 和 AS2 會進行下列作業：</span><span class="sxs-lookup"><span data-stu-id="78991-103">To assemble individual transaction-set batch elements into an EDI interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI and AS2 does the following:</span></span>  
  
-   <span data-ttu-id="78991-104">識別用於批次處理的批次元素</span><span class="sxs-lookup"><span data-stu-id="78991-104">Identifies batch elements for batching</span></span>  
  
-   <span data-ttu-id="78991-105">在收到批次元素時個別進行驗證及緩衝處理</span><span class="sxs-lookup"><span data-stu-id="78991-105">Validates and buffers individual batch elements upon receipt</span></span>  
  
-   <span data-ttu-id="78991-106">擷取特定批次項目，並將批次的交換的組合，符合釋放準則時</span><span class="sxs-lookup"><span data-stu-id="78991-106">Retrieves specific batch elements and assembles a batched interchange when the release criteria is met</span></span>  
  
 <span data-ttu-id="78991-107">個別訊息集合組合成批次的開始時間是由批次啟動準則所決定，</span><span class="sxs-lookup"><span data-stu-id="78991-107">The start time for collection of individual messages to go into a batch is determined by the batch activation criteria.</span></span> <span data-ttu-id="78991-108">而釋放批次的時間則是由批次釋放準則所決定。</span><span class="sxs-lookup"><span data-stu-id="78991-108">The time at which the batch is released is determined by the batch release criteria.</span></span> <span data-ttu-id="78991-109">如需這兩個集合的準則的詳細資訊，請參閱[設定外寄批次](../core/configuring-an-outgoing-batch.md)。</span><span class="sxs-lookup"><span data-stu-id="78991-109">For more information about these two sets of criteria, see [Configuring an Outgoing Batch](../core/configuring-an-outgoing-batch.md).</span></span>  
  
## <a name="message-flow-for-outgoing-batched-messages"></a><span data-ttu-id="78991-110">外寄批次訊息的訊息流程</span><span class="sxs-lookup"><span data-stu-id="78991-110">Message Flow for Outgoing Batched Messages</span></span>  
 <span data-ttu-id="78991-111">當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 設定為批次處理外送訊息時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 元件將會執行一系列如下的步驟，以準備傳送批次的訊息。</span><span class="sxs-lookup"><span data-stu-id="78991-111">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is configured to batch an outgoing message, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] components will perform the following series of steps to prepare the batched message for sending.</span></span> <span data-ttu-id="78991-112">這一系列步驟說明的案例是以具有 BatchMarker 管線元件的 EDIReceive 管線來處理收到的交換，而這些交換中包含要進行批次處理以供傳送的交易集。</span><span class="sxs-lookup"><span data-stu-id="78991-112">This series of steps describes the case in which the EDIReceive pipeline with the BatchMarker pipeline component processes the received interchanges that contain transaction sets to be batched for sending.</span></span>  
  
1.  <span data-ttu-id="78991-113">EDIReceive 管線中的 BatchMarker 管線元件會透過合作對象屬性的 EDI 批次篩選條件設定，判斷需要進行批次處理的訊息</span><span class="sxs-lookup"><span data-stu-id="78991-113">The BatchMarker pipeline component in the EDIReceive pipeline determines which messages need to be batched from the EDI batch filter settings in the party properties.</span></span> <span data-ttu-id="78991-114">(這是唯一可查看批次篩選條件設定並根據這些設定運作的批次處理元件)。</span><span class="sxs-lookup"><span data-stu-id="78991-114">(This is the only batching component that looks at the batch filter settings and acts upon them.)</span></span>  
  
2.  <span data-ttu-id="78991-115">如果只有一個批次組態的篩選設定訂閱了訊息，BatchMarker 元件將會升級 `EDI.ToBeBatched = True` 屬性。</span><span class="sxs-lookup"><span data-stu-id="78991-115">If the filter settings of only one batch configuration subscribes to a message, the BatchMarker component will promote the property `EDI.ToBeBatched = True`.</span></span> <span data-ttu-id="78991-116">這可確保批次處理或協調流程一定會收取訊息。</span><span class="sxs-lookup"><span data-stu-id="78991-116">This ensures that the batching orchestration will pick up the message.</span></span>  
  
3.  <span data-ttu-id="78991-117">如果多個批次組態的篩選設定符合訊息的內容，BatchMarker 元件會升級屬性`EDI.ToBeRouted = True`並設定`EDI.BatchIds`屬性，以空格分隔清單，其中包含相符的批次識別碼。</span><span class="sxs-lookup"><span data-stu-id="78991-117">If the filter settings of more than one batch configuration match the context of a message, the BatchMarker component promotes the properties `EDI.ToBeRouted = True` and sets the `EDI.BatchIds` property to a space delimited list containing the matching batch IDs.</span></span>  <span data-ttu-id="78991-118">這可確保路由或協調流程一定會訂閱訊息。</span><span class="sxs-lookup"><span data-stu-id="78991-118">This ensures that the routing orchestration will subscribe to the message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="78991-119">您可以升級自訂接收管線或自訂協調流程中適當的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="78991-119">You can promote the appropriate context properties in a custom receive pipeline or a custom orchestration.</span></span> <span data-ttu-id="78991-120">自訂接收管線可以使用 BatchMarker 管線元件，或是不使用 BatchMarker 管線元件，直接升級屬性。</span><span class="sxs-lookup"><span data-stu-id="78991-120">The custom receive pipeline can use the BatchMarker pipeline component, or can promote the properties without using the BatchMarker pipeline component.</span></span>  
  
4.  <span data-ttu-id="78991-121">路由協調流程才能收取任何交易集的`EDI.ToBeRouted = True`和`EDI.BatchIds`升級，而且接著會建立交易集，確保識別碼包含在每個批次的副本份`EDI.BatchIds`。</span><span class="sxs-lookup"><span data-stu-id="78991-121">The routing orchestration picks up any transaction set for which `EDI.ToBeRouted = True` and `EDI.BatchIds` is promoted, and then creates copies of the transaction set, ensuring that there is a copy for each batch ID contained in `EDI.BatchIds`.</span></span> <span data-ttu-id="78991-122">路由協調流程設定`EDI.ToBeBatched = True`和`EDI.BatchId`設為相符批次設定針對每個複本的交易集的批次識別碼。</span><span class="sxs-lookup"><span data-stu-id="78991-122">The routing orchestration sets `EDI.ToBeBatched = True` and `EDI.BatchId` is set to the batch ID of the matching batch configuration for each copy of the transaction set.</span></span> <span data-ttu-id="78991-123">這可確保批次處理協調流程將會收取交易集以進行批次處理。</span><span class="sxs-lookup"><span data-stu-id="78991-123">This ensures that the transaction sets will be picked up by the batching orchestration for batching.</span></span>  
  
5.  <span data-ttu-id="78991-124">批次處理協調流程會收取已升級下列屬性的所有訊息：</span><span class="sxs-lookup"><span data-stu-id="78991-124">The batching orchestration picks up all messages for which the following properties have been promoted:</span></span>  
  
    -   <span data-ttu-id="78991-125">`EDI.ToBeBatched = True`和 EDI。批次識別碼 = 批次處理協調流程的這個執行個體相關聯的批次的批次識別碼。</span><span class="sxs-lookup"><span data-stu-id="78991-125">`EDI.ToBeBatched = True` and EDI.BatchId = the batch id of the batch associated with this instance of the batching orchestration.</span></span>  
  
    -   <span data-ttu-id="78991-126">`EDI.ToBeBatched = True`和 EDI。BatchName = 設定批次和 EDI 的名稱。DestinationPartyName = 包含批次組態的合作對象名稱。</span><span class="sxs-lookup"><span data-stu-id="78991-126">`EDI.ToBeBatched = True` and EDI.BatchName = the name of the configured batch and EDI.DestinationPartyName = the party name that contains the batch configuration.</span></span>  
  
     <span data-ttu-id="78991-127">當 EDIReceive 管線處理內送訊息 (使用 BatchMarker 管線元件) 時，批次處理協調流程只會批次處理 X12 或 EDIFACT 編碼的交易集。</span><span class="sxs-lookup"><span data-stu-id="78991-127">When the incoming messages are processed by the EDIReceive pipeline (with the BatchMarker pipeline component), the batching orchestration will batch only X12- or EDIFACT-encoded transaction sets.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="78991-128">每個作用中批次組態都有一個批次處理協調流程執行個體，而且每個執行個體都會訂閱特定批次識別碼。</span><span class="sxs-lookup"><span data-stu-id="78991-128">There will be one instance of the batching orchestration for each active batch configuration, each subscribing to a specific batch ID.</span></span> <span data-ttu-id="78991-129">當建立新的批次組態中的批次識別碼值會自動設定**識別**區段**批次組態**單向協議索引標籤的頁面**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="78991-129">The batch ID value is set automatically when creating a new batch configuration in the **Identification** section of the **Batching Configuration** page of the one-way agreement tab of the **Agreement Properties** dialog box.</span></span>  
  
6.  <span data-ttu-id="78991-130">批次處理協調流程會驗證要批次處理的每個交易集。</span><span class="sxs-lookup"><span data-stu-id="78991-130">The batching orchestration validates each transaction set to be batched.</span></span> <span data-ttu-id="78991-131">如果交易集驗證失敗，它會設定`EDI.BatchItemValidationFailure`內容屬性為"True"。</span><span class="sxs-lookup"><span data-stu-id="78991-131">If the transaction set fails validation, it sets the `EDI.BatchItemValidationFailure` context property to "True".</span></span> <span data-ttu-id="78991-132">**BatchSuspend**協調流程收取該內容屬性為基礎的訊息、 發佈錯誤資訊，和再擱置訊息。</span><span class="sxs-lookup"><span data-stu-id="78991-132">The **BatchSuspend** orchestration picks up the message based upon that context property, posts error information, and then is suspended.</span></span>  
  
7.  <span data-ttu-id="78991-133">當已符合批次釋放準則時，批次處理協調流程會將批次元素組合成一個批次，並建立信封。</span><span class="sxs-lookup"><span data-stu-id="78991-133">When the batch release criteria has been met, the batching orchestration assembles the batch elements into a batch and creates an envelope.</span></span>  
  
8.  <span data-ttu-id="78991-134">批次處理協調流程完成交換的批次處理後，它會升級該交換上的下列屬性： EDI。DestinationPartyName = %partyname%EDI。BatchEncodingType = X12 或 EDIFACT，以及 EDI。ToBeBatched = False。</span><span class="sxs-lookup"><span data-stu-id="78991-134">After the batching orchestration completes batching an interchange, it promotes the following properties on that interchange: EDI.DestinationPartyName = %PartyName%, EDI.BatchEncodingType = X12 or EDIFACT, and EDI.ToBeBatched = False.</span></span>  
  
9. <span data-ttu-id="78991-135">傳送埠會拾取 EDI 為基礎的批次的交易集。DestinationPartyName = \<PartyName\>，EDI。BatchEncodingType = EDIFACT 或 X12，以及 EDI。ToBeBatched = False。</span><span class="sxs-lookup"><span data-stu-id="78991-135">A send port picks up the batched transaction sets based on EDI.DestinationPartyName = \<PartyName\>, EDI.BatchEncodingType = EDIFACT or X12, and EDI.ToBeBatched = False.</span></span>  
  
## <a name="batching-orchestration-control-messages"></a><span data-ttu-id="78991-136">批次處理協調流程控制訊息</span><span class="sxs-lookup"><span data-stu-id="78991-136">Batching Orchestration Control Messages</span></span>  
 <span data-ttu-id="78991-137">批次處理協調流程由下列控制訊息啟動、終止或覆寫：</span><span class="sxs-lookup"><span data-stu-id="78991-137">The batching orchestration is activated, terminated, or overridden by the following control messages:</span></span>  
  
-   <span data-ttu-id="78991-138">**BatchActivation**： 當協調流程收到這個訊息，會建立批次處理協調流程執行個體，而且協調流程作用狀態以便接收批次元素 （其是否符合批次啟動準則）。</span><span class="sxs-lookup"><span data-stu-id="78991-138">**BatchActivation**: When the orchestration receives this message, an instance of the batching orchestration is created and the orchestration is active to receive batch elements (if it meets the batch activation criteria).</span></span> <span data-ttu-id="78991-139">按一下 [傳送這個控制訊息**啟動**按鈕上的批次組態的**批次組態**單向協議索引標籤的頁面**協議屬性** ] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="78991-139">This control message is sent by clicking the **Start** button of a batch configuration on the **Batching Configuration** page of the one-way agreement tab of the **Agreement Properties** dialog box.</span></span>  
  
-   <span data-ttu-id="78991-140">**BatchTermination**： 當協調流程收到這個訊息時，從現有的批次元素建立批次、 將訊息發佈至 MessageBox，並終止。</span><span class="sxs-lookup"><span data-stu-id="78991-140">**BatchTermination**: When the orchestration receives this message, it creates a batch from existing batch elements, publishes the message to the MessageBox, and terminates.</span></span> <span data-ttu-id="78991-141">按一下 [傳送這個控制訊息**停止**按鈕上的批次組態的**批次組態**單向協議索引標籤的頁面**協議屬性** ] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="78991-141">This control message is sent by clicking the **Stop** button of a batch configuration on the **Batching Configuration** page of the one-way agreement tab of the **Agreement Properties** dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="78991-142">如果在達到指定的時間內，也會終止協調流程**結尾所**屬性**終止**區段**批次組態**頁面單向協議索引標籤**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="78991-142">The orchestration is also terminated if it reaches the time specified for the **End-by** property in the **Termination** section of the **Batching Configuration** page of the one-way agreement tab of the **Agreement Properties** dialog box.</span></span>  
  
-   <span data-ttu-id="78991-143">**BatchOverride**： 協調流程收到這個訊息時，它從現有的項目建立批次、 將訊息發佈至 MessageBox，，然後等候下一個批次的訊息。</span><span class="sxs-lookup"><span data-stu-id="78991-143">**BatchOverride**: When the orchestration receives this message, it creates a batch from existing elements, publishes the message to the MessageBox, and then waits for messages for the next batch.</span></span> <span data-ttu-id="78991-144">按一下 [傳送這個控制訊息**覆寫**按鈕上的批次組態的**批次組態**單向協議索引標籤的頁面**協議屬性** ] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="78991-144">This control message is sent by clicking the **Override** button of a batch configuration on the **Batching Configuration** page of the one-way agreement tab of the **Agreement Properties** dialog box.</span></span>  
  
 <span data-ttu-id="78991-145">批次處理協調流程會透過 BatchControlMessageRecvLoc 接收位置接收控制訊息。</span><span class="sxs-lookup"><span data-stu-id="78991-145">The batching orchestration receives the control messages via the BatchControlMessageRecvLoc receive location.</span></span> <span data-ttu-id="78991-146">這個 SQL 接收位置的輪詢間隔預設為 30 秒，但是可以變更在**SQL 傳輸屬性**接收位置 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="78991-146">The polling interval for this SQL receive location is set by default to 30 seconds, but can be changed in the **SQL Transport Properties** dialog box for the receive location.</span></span> <span data-ttu-id="78991-147">縮短輪詢間隔可確保在您執行傳送控制訊息的動作之後 (例如在您啟動批次處理協調流程時)，BatchControlMessageRecvLoc 接收位置可以立即收到控制訊息。</span><span class="sxs-lookup"><span data-stu-id="78991-147">Decreasing the polling interval will ensure that the BatchControlMessageRecvLoc receive location will receive a control message soon after you perform the action that sent the control message (such as when you start the batching orchestration).</span></span>  
  
 <span data-ttu-id="78991-148">啟動批次協調流程時執行的步驟如下：</span><span class="sxs-lookup"><span data-stu-id="78991-148">The following steps occur when you start a batch orchestration:</span></span>  
  
1.  <span data-ttu-id="78991-149">當您按一下**啟動** 按鈕，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會指出您要啟用的批次協調流程的合作對象和批次識別碼的表格建立記錄。</span><span class="sxs-lookup"><span data-stu-id="78991-149">When you click the **Start** button, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] creates a record in a table indicating which party and batch id you are activating the batch orchestration for.</span></span>  
  
2.  <span data-ttu-id="78991-150">與 BatchControlMessageRecvLoc 接收位置關聯的 SQL 配接器會進行輪詢，確定資料庫中是否有該筆記錄。</span><span class="sxs-lookup"><span data-stu-id="78991-150">The SQL adapter associated with the BatchControlMessageRecvLoc receive location polls to see if the record exists in the database.</span></span>  
  
3.  <span data-ttu-id="78991-151">如果記錄存在，SQL 配接器會使用記錄中的資訊建置控制訊息。</span><span class="sxs-lookup"><span data-stu-id="78991-151">If the record exists, the SQL adapter builds a control message, using information in the record.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="78991-152">以這種方式建置訊息可確保無效的控制訊息將無法啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="78991-152">Building the control message in this way ensures that the orchestration cannot be started by an invalid control message.</span></span>  
  
4.  <span data-ttu-id="78991-153">BatchControlMessageRecvLoc 接收位置接收控制訊息，和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]啟動批次處理協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="78991-153">The BatchControlMessageRecvLoc receive location receives the control message, and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] activates a batching orchestration instance.</span></span>  
  
## <a name="batch-components"></a><span data-ttu-id="78991-154">批次元件</span><span class="sxs-lookup"><span data-stu-id="78991-154">Batch Components</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="78991-155">EDI 批次處理成 EDI 交換，使用下列元件的 XML 交易集：</span><span class="sxs-lookup"><span data-stu-id="78991-155"> EDI batches XML transaction sets into EDI interchanges using the following components:</span></span>  
  
-   <span data-ttu-id="78991-156">EDI 接收管線中的 BatchMarkerReceivePipelineComponent</span><span class="sxs-lookup"><span data-stu-id="78991-156">BatchMarkerReceivePipelineComponent in the EDI receive pipeline</span></span>  
  
-   <span data-ttu-id="78991-157">路由協調流程</span><span class="sxs-lookup"><span data-stu-id="78991-157">Routing Orchestration</span></span>  
  
-   <span data-ttu-id="78991-158">批次處理協調流程</span><span class="sxs-lookup"><span data-stu-id="78991-158">Batching Orchestration</span></span>  
  
-   <span data-ttu-id="78991-159">升級批次處理協調流程</span><span class="sxs-lookup"><span data-stu-id="78991-159">Upgrade Batching Orchestration</span></span>  
  
-   <span data-ttu-id="78991-160">BatchSuspend 協調流程</span><span class="sxs-lookup"><span data-stu-id="78991-160">BatchSuspend Orchestration</span></span>  
  
-   <span data-ttu-id="78991-161">EDI 傳送管線</span><span class="sxs-lookup"><span data-stu-id="78991-161">EDI Send Pipeline</span></span>  
  
 <span data-ttu-id="78991-162">當您安裝並設定這些元件都會安裝成 Dll [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI 和 AS2。</span><span class="sxs-lookup"><span data-stu-id="78991-162">These components are installed as DLLs when you install and configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI and AS2.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="78991-163">中的批次處理元件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI 和 AS2 不保證批次中交易的順序設定。</span><span class="sxs-lookup"><span data-stu-id="78991-163">The batching components in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI and AS2 do not guarantee the ordering of the transaction sets in a batch.</span></span>  
  
### <a name="batchmarkerreceivepipelinecomponent"></a><span data-ttu-id="78991-164">BatchMarkerReceivePipelineComponent</span><span class="sxs-lookup"><span data-stu-id="78991-164">BatchMarkerReceivePipelineComponent</span></span>  
 <span data-ttu-id="78991-165">EDI 接收管線中的 BatchMarkerReceivePipelineComponent 可讓批次處理協調流程收取要批次處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="78991-165">BatchMarkerReceivePipelineComponent in the EDI receive pipeline enables the batching orchestration to pick up messages to be batched.</span></span> <span data-ttu-id="78991-166">這個管線元件是在 EDI 接收管線中的解譯器之後套用。</span><span class="sxs-lookup"><span data-stu-id="78991-166">This pipeline component is applied after the Disassembler in the EDI Receive Pipeline.</span></span> <span data-ttu-id="78991-167">這個元件會評估設定的篩選準則**篩選**區段**批次組態**單向協議索引標籤的頁面**協議屬性**對話方塊中，並標示交易集與下列內容屬性來處理路由和批次處理協調流程</span><span class="sxs-lookup"><span data-stu-id="78991-167">The component evaluates the filter criteria set in the **Filter** section of the **Batching Configuration** page of the one-way agreement tab of the **Agreement Properties** dialog box, and marks the transaction sets with the following context properties for processing by the routing and batching orchestrations</span></span>  
  
-   <span data-ttu-id="78991-168">如果單一合作對象訂閱要批次處理的訊息，它會升級 `ToBeBatched = True`，而且 BatchId 會設定為相符批次組態之批次識別碼的值。</span><span class="sxs-lookup"><span data-stu-id="78991-168">If a single party subscribes to a message to be batched, it promotes `ToBeBatched = True` and BatchId is set to the value of the batch ID of the matching batch configuration.</span></span> <span data-ttu-id="78991-169">這可讓批次處理協調流程收取訊息。</span><span class="sxs-lookup"><span data-stu-id="78991-169">This enables pickup by the batching orchestration.</span></span>  
  
-   <span data-ttu-id="78991-170">如果多個批次訂閱要批次處理的訊息，它會升級`ToBeRouted = True`，並設定`EDI.BatchIds`屬性設定為以空格分隔批次識別碼的清單。</span><span class="sxs-lookup"><span data-stu-id="78991-170">If multiple batches subscribe to a message to be batched, it promotes `ToBeRouted = True`, and sets the `EDI.BatchIds` property set to a space-delimited list of batch IDs.</span></span> <span data-ttu-id="78991-171">這啟用路由協調流程收取。</span><span class="sxs-lookup"><span data-stu-id="78991-171">This enables pickup by the routing orchestration.</span></span>  
  
-   <span data-ttu-id="78991-172">如果沒有任何訂閱存在，它就不會升級內容屬性。</span><span class="sxs-lookup"><span data-stu-id="78991-172">If no subscriptions exist, it does not promote a context property.</span></span> <span data-ttu-id="78991-173">這表示交易集不會進行批次處理。</span><span class="sxs-lookup"><span data-stu-id="78991-173">This indicates that the transaction set is not to be batched.</span></span>  
  
 <span data-ttu-id="78991-174">管線元件會忽略 XML 以外的訊息，並使用訊息`ReuseEnvelope`（保留批次） 的屬性。</span><span class="sxs-lookup"><span data-stu-id="78991-174">The pipeline component ignores messages other than XML and messages with the `ReuseEnvelope` property (preserved batches).</span></span> <span data-ttu-id="78991-175">如果不要對通知進行批次處理，此管線元件便會忽略 ACK 訊息類型 (CONTRL、TA1 和 997)。</span><span class="sxs-lookup"><span data-stu-id="78991-175">If acknowledgments are not to be batched, the pipeline component will ignore the ACK message types (CONTRL, TA1, and 997).</span></span> <span data-ttu-id="78991-176">為了讓路由和批次處理協調流程達到最佳效果，如果解譯器將訊息內容屬性 `MessageDestination` 設定為 "SuspendedQueue"，BatchMarkerPipelineComponent 便會將訊息傳遞到 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="78991-176">To optimize processing of the routing and batching orchestrations, the BatchMarkerPipelineComponent passes the message through to the MessageBox if the message context property `MessageDestination` is set to "SuspendedQueue" by the disassembler.</span></span>  
  
 <span data-ttu-id="78991-177">如果您使用的是自訂管線，而不是 EDIReceive 管線，可以使用自訂管線中的 BatchMarker 元件。</span><span class="sxs-lookup"><span data-stu-id="78991-177">If you are using a custom pipeline, rather than the EDIReceive pipeline, you can use the BatchMarker component in your custom pipeline.</span></span> <span data-ttu-id="78991-178">如果您不是使用 EDIReceive 管線，而且要從協調流程發佈訊息，則必須升級 `ToBeBatched = True` 並將 `BatchID` 設定為其中一個元件內作用中批次的識別碼。</span><span class="sxs-lookup"><span data-stu-id="78991-178">If you are not using the EDIReceive pipeline, and are publishing messages from an orchestration, you will have to promote `ToBeBatched = True` and `BatchID` to the ID of an active batch in one of your components.</span></span>  
  
### <a name="routing-orchestration"></a><span data-ttu-id="78991-179">路由協調流程</span><span class="sxs-lookup"><span data-stu-id="78991-179">Routing Orchestration</span></span>  
 <span data-ttu-id="78991-180">路由協調流程會訂閱具有內容屬性 `ToBeRouted = True`，並將內容屬性 `EDI.BatchIds` 設定為批次識別碼之空格分隔清單的任何訊息。</span><span class="sxs-lookup"><span data-stu-id="78991-180">The routing orchestration subscribes to any message with the context property `ToBeRouted = True` and the context property `EDI.BatchIds` set to a space-delimited list of batch IDs.</span></span> <span data-ttu-id="78991-181">會發生這種情況是當多個批次篩選條件訂閱要批次處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="78991-181">This occurs when multiple batch filters subscribe to a message to be batched.</span></span> <span data-ttu-id="78991-182">路由協調流程會針對 `EDI.BatchIds` 中包含的每個批次識別碼建立訊息的複本。</span><span class="sxs-lookup"><span data-stu-id="78991-182">The routing orchestration will make a copy of the message for each batch ID contained in `EDI.BatchIds`.</span></span> <span data-ttu-id="78991-183">加上戳記每個複本的兩個新的內容屬性：</span><span class="sxs-lookup"><span data-stu-id="78991-183">It stamps each copy with two new context properties:</span></span>  
  
-   <span data-ttu-id="78991-184">`EDI.BatchID`會設定為僅供這則訊息批次的識別碼。</span><span class="sxs-lookup"><span data-stu-id="78991-184">`EDI.BatchID`, which is set to the ID of the batch that this message is intended for.</span></span>  
  
-   <span data-ttu-id="78991-185">`EDI.ToBeBatched`會設定為 True。</span><span class="sxs-lookup"><span data-stu-id="78991-185">`EDI.ToBeBatched`, which is set to True.</span></span>  
  
 <span data-ttu-id="78991-186">接著，它會將這些複本傳送到 MessageBox，供批次處理協調流程收取。</span><span class="sxs-lookup"><span data-stu-id="78991-186">It then routes the copies to the MessageBox to be picked up by the batching orchestration.</span></span> <span data-ttu-id="78991-187">每個目的地的批次識別碼將相同的協調流程的單一執行個體使用特定批次識別碼的篩選</span><span class="sxs-lookup"><span data-stu-id="78991-187">Each destination batch ID use a singleton instance of the same orchestration, with a filter on the specific batch ID.</span></span>  
  
### <a name="batching-orchestration"></a><span data-ttu-id="78991-188">批次處理協調流程</span><span class="sxs-lookup"><span data-stu-id="78991-188">Batching Orchestration</span></span>  
 <span data-ttu-id="78991-189">批次處理協調流程是一種可設定狀態的服務，它會緩衝一段時間內的批次元素 (交易集)、將它們組合成交換，然後再根據釋放準則將交換釋放到傳送管線。</span><span class="sxs-lookup"><span data-stu-id="78991-189">The batching orchestration is a stateful service that buffers batch elements (transaction sets) over a period of time, assembles them into an interchange, and then releases the interchange to the send pipeline based upon the release criteria.</span></span>  
  
 <span data-ttu-id="78991-190">之後啟動批次處理協調流程執行個體可以開始批次處理到指定的合作對象的特定編碼類型的訊息 (如果**啟動**經過 datetime)。</span><span class="sxs-lookup"><span data-stu-id="78991-190">After being activated, an instance of the batching orchestration can start batching messages of a particular encoding type to a given party (if the **Start** datetime has passed).</span></span> <span data-ttu-id="78991-191">在任何一個時間點，每個合作對象的批次處理協調流程可以具有許多執行個體，但是每個作用中批次組態只能有一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="78991-191">At any one time there can be many instances of the batching orchestration for each party, one per active batch configuration.</span></span> <span data-ttu-id="78991-192">批次處理協調流程的單一執行個體可以發行單一批次組態的多個批次。</span><span class="sxs-lookup"><span data-stu-id="78991-192">A single instance of the batching orchestration can release multiple batches for a single  batch configuration.</span></span> <span data-ttu-id="78991-193">在符合結束準則後，批次處理協調流程執行個體將會終止。</span><span class="sxs-lookup"><span data-stu-id="78991-193">After the end criteria is met, the batching orchestration instance will terminate.</span></span> <span data-ttu-id="78991-194">批次處理協調流程的新執行個體必須以手動方式建立交易夥伴管理 (TPM) 從使用**啟動** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="78991-194">A new instance of the batching orchestration will need to be created manually from the Trading Partner Management (TPM) using the **Start** button.</span></span>  
  
 <span data-ttu-id="78991-195">如果批次協調流程啟動之前顯示的開始日期時間中**啟用**區段的**批次組態**單向協議索引標籤的頁面**協議屬性**對話方塊中，它只會接收啟動範圍中指定的訊息。</span><span class="sxs-lookup"><span data-stu-id="78991-195">If the batch orchestration starts before the start date time shown in the **Activation** section on the of the **Batching Configuration** page of the one-way agreement tab of the **Agreement Properties** dialog box, it will only receive messages that are specified in the activation range.</span></span> <span data-ttu-id="78991-196">不會接收在開始日期時間之前傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="78991-196">It will not receive messages sent before the start date time.</span></span>  
  
 <span data-ttu-id="78991-197">批次處理協調流程執行的作業包括：</span><span class="sxs-lookup"><span data-stu-id="78991-197">The batching orchestration does the following:</span></span>  
  
-   <span data-ttu-id="78991-198">訂閱具有下列內容屬性的 XML 批次元素：`EDI.ToBeBatched = True` 以及 `EDI.BatchId` = 批次組態識別碼，或是 `EDI.ToBeBatched = True`、EDI.BatchName = 已設定批次的名稱，以及 EDI.DestinationPartyName = 包含批次組態的合作對象名稱。</span><span class="sxs-lookup"><span data-stu-id="78991-198">Subscribes to XML batch elements with the context properties `EDI.ToBeBatched = True` and `EDI.BatchId` the ID of the batch configuration, or `EDI.ToBeBatched = True` and EDI.BatchName = the name of the configured batch and EDI.DestinationPartyName = the party name that contains the batch configuration.</span></span> <span data-ttu-id="78991-199">它會接收批次項目使用**接收**動作在迴圈中的作業。</span><span class="sxs-lookup"><span data-stu-id="78991-199">It receives batch elements using a **Receive** action operation in a loop.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="78991-200">批次處理協調流程不會批次處理的篩選區段中設定的篩選準則為基礎的交易集**批次組態**單向協議索引標籤的頁面**協議屬性**  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="78991-200">The batching orchestration does not batch transaction sets based upon the filter criteria set in the Filter section of the **Batching Configuration** page of the one-way agreement tab of the **Agreement Properties** dialog box.</span></span> <span data-ttu-id="78991-201">它會訂閱已設定前述內容屬性的交易集。</span><span class="sxs-lookup"><span data-stu-id="78991-201">It subscribes to transaction sets that have the above context properties set on them.</span></span> <span data-ttu-id="78991-202">BatchMarker 管線元件會根據合作對象屬性中的篩選設定來設定及升級這些內容屬性。</span><span class="sxs-lookup"><span data-stu-id="78991-202">The BatchMarker pipeline component sets and promotes those context properties based upon the filter settings in the party properties.</span></span>  
  
-   <span data-ttu-id="78991-203">擷取中所識別的合作對象的批次組態設定`BatchId`內容屬性。</span><span class="sxs-lookup"><span data-stu-id="78991-203">Retrieves the batch configuration settings for the party identified in the `BatchId` context property.</span></span>  
  
-   <span data-ttu-id="78991-204">根據合作對象設定來驗證批次元素 (交易集)。</span><span class="sxs-lookup"><span data-stu-id="78991-204">Validates the batch element (transaction set) based on party settings.</span></span>  
  
-   <span data-ttu-id="78991-205">如果批次項目中有錯誤，批次處理協調流程將會升級該交易集的下列屬性： `EDI.BatchItemValidationFailure = True`。</span><span class="sxs-lookup"><span data-stu-id="78991-205">If there is an error in a batch element, the batching orchestration will promoted the following property on that transaction set: `EDI.BatchItemValidationFailure = True`.</span></span> <span data-ttu-id="78991-206">**BatchElementSuspend**協調流程會訂閱設定已升級這個屬性的任何交易。</span><span class="sxs-lookup"><span data-stu-id="78991-206">The **BatchElementSuspend** orchestration subscribes to any transaction set for which this property has been promoted.</span></span> <span data-ttu-id="78991-207">這個協調流程將會提供在批次處理交換時所遇到的第一個錯誤。</span><span class="sxs-lookup"><span data-stu-id="78991-207">This orchestration will provide detailed error information for the first error encountered in batching the interchange.</span></span>  
  
-   <span data-ttu-id="78991-208">如果批次元素中沒有任何錯誤，則保留該批次元素的參考。</span><span class="sxs-lookup"><span data-stu-id="78991-208">If there is no error in a batch element, holds a reference to that batch element.</span></span>  
  
-   <span data-ttu-id="78991-209">當收到適當的控制訊息或符合批次處理釋放準則時，中斷**接收**動作 」 迴圈、 從 MessageBox 擷取所有批次元素並組合交換。</span><span class="sxs-lookup"><span data-stu-id="78991-209">When the appropriate control message is received or the batching release criteria is met, breaks out of the **Receive** action loop, retrieves all batch elements from the MessageBox, and assembles the interchange.</span></span>  
  
-   <span data-ttu-id="78991-210">將內容屬性設定`ToBeBatched = False`針對交換和內容屬性 DestinationPartyName = %partyname%其中 %partyname%是訊息適用之合作對象名稱。</span><span class="sxs-lookup"><span data-stu-id="78991-210">Sets the context property `ToBeBatched = False` for the interchange and the context property DestinationPartyName = %PartyName% where %PartyName% is the name of the party for which the message is intended.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="78991-211">如果傳送埠訂閱一個或兩個屬性`EDI.ToBeBatched = False`和 EDI。DestinationPartyName = %partyname%、 傳送埠可以收取批次交換。</span><span class="sxs-lookup"><span data-stu-id="78991-211">If a send port subscribes to either or both of the properties `EDI.ToBeBatched = False` and EDI.DestinationPartyName = %PartyName%, that send port can pick up the batched interchange.</span></span> <span data-ttu-id="78991-212">請確定傳送埠的篩選條件已設定成讓傳送埠只收取它應該收取的批次交換。</span><span class="sxs-lookup"><span data-stu-id="78991-212">Make sure that a send port's filters are configured such that the send port picks up only those batched interchanges that it is intended to pick up.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="78991-213">批次處理協調流程放入 MessageBox 中的交換必須只有屬性`EDI.ToBeBatched = False`，EDI。DestinationPartyName = %partyname%以及 EDI。BatchEncodingType ="X12"或"EDIFACT"升級至內容。</span><span class="sxs-lookup"><span data-stu-id="78991-213">Interchanges dropped by the batching orchestration into the MessageBox have only the properties `EDI.ToBeBatched = False`, EDI.DestinationPartyName = %PartyName%, and EDI.BatchEncodingType = "X12" or "EDIFACT" promoted to the context.</span></span> <span data-ttu-id="78991-214">原始交易集裡的所有內容屬性都會遺失。</span><span class="sxs-lookup"><span data-stu-id="78991-214">All context properties from the original transaction sets are lost.</span></span>  
  
-   <span data-ttu-id="78991-215">針對 X12 編碼的交換，將下列屬性套用到信封：</span><span class="sxs-lookup"><span data-stu-id="78991-215">For an X12-encoded interchange, applies the following properties to the envelope:</span></span>  
  
    -   <span data-ttu-id="78991-216">ISA6： 交換傳送者識別碼</span><span class="sxs-lookup"><span data-stu-id="78991-216">ISA6: Interchange Sender ID</span></span>  
  
    -   <span data-ttu-id="78991-217">ISA8： 交換接收者識別碼</span><span class="sxs-lookup"><span data-stu-id="78991-217">ISA8: Interchange Receiver ID</span></span>  
  
    -   <span data-ttu-id="78991-218">ISA15：使用狀況指示符號</span><span class="sxs-lookup"><span data-stu-id="78991-218">ISA15: Usage indicator</span></span>  
  
    -   <span data-ttu-id="78991-219">ISA_Blob (寫入內容中)</span><span class="sxs-lookup"><span data-stu-id="78991-219">ISA_Blob (written to context)</span></span>  
  
-   <span data-ttu-id="78991-220">針對 EDIFACT 編碼的交換，將下列屬性套用到信封：</span><span class="sxs-lookup"><span data-stu-id="78991-220">For an EDIFACT-encoded interchange, applies the following properties to the envelope:</span></span>  
  
    -   <span data-ttu-id="78991-221">UNB2.1：交換傳送者識別碼</span><span class="sxs-lookup"><span data-stu-id="78991-221">UNB2.1: Interchange Sender ID</span></span>  
  
    -   <span data-ttu-id="78991-222">UNB3.1：交換收件者識別碼</span><span class="sxs-lookup"><span data-stu-id="78991-222">UNB3.1: Interchange Recipient ID</span></span>  
  
    -   <span data-ttu-id="78991-223">UNB2.3：反向路由的位址</span><span class="sxs-lookup"><span data-stu-id="78991-223">UNB2.3: Address for Reverse Routing</span></span>  
  
    -   <span data-ttu-id="78991-224">UNB11：使用狀況指示符號</span><span class="sxs-lookup"><span data-stu-id="78991-224">UNB11: Usage indicator</span></span>  
  
    -   <span data-ttu-id="78991-225">UNA_Blob (寫入內容中)</span><span class="sxs-lookup"><span data-stu-id="78991-225">UNA_Blob (written to context)</span></span>  
  
    -   <span data-ttu-id="78991-226">UNB_Blob (寫入內容中)</span><span class="sxs-lookup"><span data-stu-id="78991-226">UNB_Blob (written to context)</span></span>  
  
-   <span data-ttu-id="78991-227">將批次交換傳送至 MessageBox，供 EDI 傳送管線收取。</span><span class="sxs-lookup"><span data-stu-id="78991-227">Delivers the batched interchange to the MessageBox for pickup by the EDI send pipeline.</span></span>  
  
### <a name="upgradebatching-orchestration"></a><span data-ttu-id="78991-228">UpgradeBatching 協調流程</span><span class="sxs-lookup"><span data-stu-id="78991-228">UpgradeBatching Orchestration</span></span>  
 <span data-ttu-id="78991-229">UpgradeBatching 協調流程會處理將 `EDI.ToBeBatched` 屬性設定為 true，但是沒有設定 `EDI.BatchID` 屬性的訊息。</span><span class="sxs-lookup"><span data-stu-id="78991-229">The UpgradeBatching orchestration handles messages that are have the `EDI.ToBeBatched` property set to true, but do not have the `EDI.BatchID` property set.</span></span>  
  
 <span data-ttu-id="78991-230">在舊版 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，每個合作對象都只能有一個批次組態。</span><span class="sxs-lookup"><span data-stu-id="78991-230">In previous versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], each party could have only one batch configuration.</span></span>  <span data-ttu-id="78991-231">處理將 `EDI.ToBeBatched` 設定為 true 的訊息時，`EDI.DestinationPartyId` 就會用來判斷合作對象，然後從協議屬性中讀取批次組態。</span><span class="sxs-lookup"><span data-stu-id="78991-231">When processing messages that had `EDI.ToBeBatched` set to true, the `EDI.DestinationPartyId` was used to determine the party and then the batch configuration was read from the agreement properties.</span></span>  
  
 <span data-ttu-id="78991-232">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，每個合作對象可以有多個批次組態相關聯，所以`EDI.DestinationPartyId`不提供足夠的資訊來決定應使用哪一個批次組態。</span><span class="sxs-lookup"><span data-stu-id="78991-232">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], each party can have multiple batch configurations associated with it, so the `EDI.DestinationPartyId` does not provide enough information to determine which batch configuration should be used.</span></span>  <span data-ttu-id="78991-233">當[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]接收訊息，`EDI.BatchId`屬性用來識別處理訊息時，就應該使用哪一個特定批次組態。</span><span class="sxs-lookup"><span data-stu-id="78991-233">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives messages, the `EDI.BatchId` property is used to identify which specific batch configuration should be used when processing a message.</span></span>  
  
 <span data-ttu-id="78991-234">升級到之後[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您可能仍有使用的自訂管線`EDI.DestinationPartyId`以指定的合作對象組態屬性。</span><span class="sxs-lookup"><span data-stu-id="78991-234">After upgrading to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you may still have custom pipelines that use the `EDI.DestinationPartyId` property to specify the party configuration.</span></span> <span data-ttu-id="78991-235">當收到的訊息具有`EDI.ToBeBatched`設為 true，且具有`EDI.DestinationPartyID`而不是 EDI 設定。批次識別碼，UpgradeBatching 協調流程會嘗試決定應使用哪一個批次組態。</span><span class="sxs-lookup"><span data-stu-id="78991-235">When a message is received that has `EDI.ToBeBatched` set to true, and has `EDI.DestinationPartyID` set instead of EDI.BatchID, the UpgradeBatching orchestration attempts to determine which batch configuration should be used.</span></span>  
  
 <span data-ttu-id="78991-236">UpgradeBatching 協調流程會使用下列訂用帳戶篩選來訂閱被標示為要批次處理，但不是指定批次識別碼的文件：</span><span class="sxs-lookup"><span data-stu-id="78991-236">The UpgradeBatching orchestration uses the following subscription filters to subscribe to documents that are marked for batching, but do not specify a batch ID:</span></span>  
  
-   `EDI.ToBeBatched=True`  
  
-   <span data-ttu-id="78991-237">`EDI.EncodingType`存在</span><span class="sxs-lookup"><span data-stu-id="78991-237">`EDI.EncodingType` exists</span></span>  
  
-   <span data-ttu-id="78991-238">`EDI.DestinationPartyId`存在</span><span class="sxs-lookup"><span data-stu-id="78991-238">`EDI.DestinationPartyId` exists</span></span>  
  
 <span data-ttu-id="78991-239">當協調流程接收訊息時，它會嘗試尋找相符的批次組態訊息所使用的合作對象名稱和編碼類型。</span><span class="sxs-lookup"><span data-stu-id="78991-239">When the orchestration receives a message, it will try to find a matching batch configuration for the message by using the party name and encoding type.</span></span>  <span data-ttu-id="78991-240">`EDI.DestinationPartyID`屬性用來判斷合作對象名稱，以及協調流程接著會尋找符合批次名稱\<PartyName\>+\<EncodingType\>+ 預設值。</span><span class="sxs-lookup"><span data-stu-id="78991-240">The `EDI.DestinationPartyID` property is used to determine the party name, and then the orchestration looks for a batch name that matches \<PartyName\>+\<EncodingType\>+Default.</span></span>  <span data-ttu-id="78991-241">例如，如果合作對象名稱是 Contoso，且值`EDI.EncodingType`為 X12，則協調流程會尋找名為 ContosoX12Default 批次。</span><span class="sxs-lookup"><span data-stu-id="78991-241">For example if the party name is Contoso, and the value of `EDI.EncodingType` is X12, then the orchestration will look for a batch named ContosoX12Default.</span></span>  
  
 <span data-ttu-id="78991-242">如果找到相符的批次組態，訊息會放入訊息方塊具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="78991-242">If a matching batch configuration is found, the message is placed back in the message box with the following properties:</span></span>  
  
-   `EDI.ToBeBatched = True`  
  
-   `EDI.ToBeRouted = False`  
  
-   <span data-ttu-id="78991-243">EDI。批次識別碼 = 相符的批次的批次識別碼</span><span class="sxs-lookup"><span data-stu-id="78991-243">EDI.BatchId = the batch ID for the matching batch</span></span>  
  
 <span data-ttu-id="78991-244">批次處理協調流程接著會處理訊息</span><span class="sxs-lookup"><span data-stu-id="78991-244">The batching orchestration will then process the message</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="78991-245">如果找到相符的批次，則會發生下列：</span><span class="sxs-lookup"><span data-stu-id="78991-245">If no matching batch is found, then the following will happen:</span></span>  
>   
>  -   <span data-ttu-id="78991-246">將訊息傳送至 BatchSuspend 協調流程。</span><span class="sxs-lookup"><span data-stu-id="78991-246">The message will not be sent to the BatchSuspend orchestration.</span></span>  
> -   <span data-ttu-id="78991-247">UpgradeBatching 協調流程執行個體和訊息將遭擱置。</span><span class="sxs-lookup"><span data-stu-id="78991-247">The UpgradeBatching orchestration instance and message will be suspended.</span></span>  
> -   <span data-ttu-id="78991-248">錯誤會記錄到事件記錄檔指出找不到批次。</span><span class="sxs-lookup"><span data-stu-id="78991-248">An error will be logged to the event log stating that a batch was not found.</span></span>  
  
### <a name="batchsuspend-orchestration"></a><span data-ttu-id="78991-249">BatchSuspend 協調流程</span><span class="sxs-lookup"><span data-stu-id="78991-249">BatchSuspend Orchestration</span></span>  
 <span data-ttu-id="78991-250">BatchSuspend 協調流程可處理批次處理協調流程所收到的無效訊息。</span><span class="sxs-lookup"><span data-stu-id="78991-250">The BatchSuspend orchestration handles invalid messages received by the batching orchestration.</span></span> <span data-ttu-id="78991-251">BatchSuspend 是必要的協調流程，因為沒有任何方法可以直接從協調流程 (在此案例中為批次處理協調流程) 擱置訊息，而不需要停止執行協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="78991-251">The BatchSuspend orchestration is needed because there is no direct way to suspend a message from an orchestration (in this case, the batching orchestration) without stopping the execution of the instance of the orchestration.</span></span>  
  
 <span data-ttu-id="78991-252">當批次處理協調流程的執行個體收到訊息時，它會嘗試驗證該訊息。</span><span class="sxs-lookup"><span data-stu-id="78991-252">When an instance of the batching orchestration receives a message, it attempts to validate it.</span></span> <span data-ttu-id="78991-253">如果訊息驗證失敗，批次處理協調流程便會建立 BatchSuspend 協調流程的執行個體，並將 `EDI.BatchItemValidationFailure` 內容屬性設定為 True。</span><span class="sxs-lookup"><span data-stu-id="78991-253">If the message fails validation, the batching orchestration creates an instance of the BatchSuspend orchestration, and sets the `EDI.BatchItemValidationFailure` context property to True.</span></span> <span data-ttu-id="78991-254">BatchSuspend 協調流程訂閱與該內容屬性設定為 True 的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="78991-254">The BatchSuspend orchestration subscribes to all messages with that context property set to True.</span></span> <span data-ttu-id="78991-255">在將無效的交易集傳送至 BatchSuspend 協調流程之後，BatchSuspend 協調流程執行個體便會擱置。</span><span class="sxs-lookup"><span data-stu-id="78991-255">After the invalid transaction set is routed to the BatchSuspend orchestration, the BatchSuspend orchestration instance is suspended.</span></span>  
  
 <span data-ttu-id="78991-256">BatchSuspend 協調流程會提供遇到的第一個錯誤的詳細錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="78991-256">Detailed error information for the first error encountered is provided by the BatchSuspend orchestration.</span></span>  
  
 <span data-ttu-id="78991-257">您可以建立自訂協調流程，利用篩選條件中的 `EDI.BatchElementValidationFailure` 屬性，依據批次處理協調流程來處理驗證失敗的交易集。</span><span class="sxs-lookup"><span data-stu-id="78991-257">You can create a custom orchestration to handle transaction sets that fail validation by the batching orchestration, by using the `EDI.BatchElementValidationFailure` property in a filter.</span></span>  
  
### <a name="edi-send-pipeline"></a><span data-ttu-id="78991-258">EDI 傳送管線</span><span class="sxs-lookup"><span data-stu-id="78991-258">EDI Send Pipeline</span></span>  
 <span data-ttu-id="78991-259">從批次處理協調流程接收批次交換之後，EDI 傳送管線會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="78991-259">After receiving a batched interchange from the batching orchestration, the EDI send pipeline does the following:</span></span>  
  
-   <span data-ttu-id="78991-260">針對 X12 編碼的交換，傳送管線會將下列屬性套用到信封：</span><span class="sxs-lookup"><span data-stu-id="78991-260">For an X12-encoded interchange, the send pipeline applies the following properties to the envelope:</span></span>  
  
    -   <span data-ttu-id="78991-261">ISA2：授權資訊</span><span class="sxs-lookup"><span data-stu-id="78991-261">ISA2: Authorization Information</span></span>  
  
    -   <span data-ttu-id="78991-262">ISA4： 安全性資訊</span><span class="sxs-lookup"><span data-stu-id="78991-262">ISA4: Security Information</span></span>  
  
    -   <span data-ttu-id="78991-263">ISA9： 交換日期</span><span class="sxs-lookup"><span data-stu-id="78991-263">ISA9: Interchange Date</span></span>  
  
    -   <span data-ttu-id="78991-264">ISA10： 交換時間</span><span class="sxs-lookup"><span data-stu-id="78991-264">ISA10: Interchange Time</span></span>  
  
    -   <span data-ttu-id="78991-265">ISA13： 交換控制編號</span><span class="sxs-lookup"><span data-stu-id="78991-265">ISA13: Interchange Control Number</span></span>  
  
    -   <span data-ttu-id="78991-266">GS4： 日期</span><span class="sxs-lookup"><span data-stu-id="78991-266">GS4: Date</span></span>  
  
    -   <span data-ttu-id="78991-267">GS5： 時間</span><span class="sxs-lookup"><span data-stu-id="78991-267">GS5: Time</span></span>  
  
    -   <span data-ttu-id="78991-268">GS6： 群組控制編號</span><span class="sxs-lookup"><span data-stu-id="78991-268">GS6: Group Control Number</span></span>  
  
    -   <span data-ttu-id="78991-269">ST2： 交易集控制編號</span><span class="sxs-lookup"><span data-stu-id="78991-269">ST2: Transaction Set Control Number</span></span>  
  
-   <span data-ttu-id="78991-270">針對 EDIFACT 編碼的交換，傳送管線會將下列屬性套用到信封：</span><span class="sxs-lookup"><span data-stu-id="78991-270">For an EDIFACT-encoded interchange, the send pipeline applies the following properties to the envelope:</span></span>  
  
    -   <span data-ttu-id="78991-271">UNB4.1： 日期</span><span class="sxs-lookup"><span data-stu-id="78991-271">UNB4.1: Date</span></span>  
  
    -   <span data-ttu-id="78991-272">UNB4.2：時間</span><span class="sxs-lookup"><span data-stu-id="78991-272">UNB4.2: Time</span></span>  
  
    -   <span data-ttu-id="78991-273">UNB5：交換控制參考</span><span class="sxs-lookup"><span data-stu-id="78991-273">UNB5: Interchange Control Reference</span></span>  
  
    -   <span data-ttu-id="78991-274">UNB6.1：收件者參考密碼</span><span class="sxs-lookup"><span data-stu-id="78991-274">UNB6.1: Recipient Reference Password</span></span>  
  
    -   <span data-ttu-id="78991-275">UNG4.1：日期</span><span class="sxs-lookup"><span data-stu-id="78991-275">UNG4.1: Date</span></span>  
  
    -   <span data-ttu-id="78991-276">UNG4.2：時間</span><span class="sxs-lookup"><span data-stu-id="78991-276">UNG4.2: Time</span></span>  
  
    -   <span data-ttu-id="78991-277">UNG5：功能群組參考</span><span class="sxs-lookup"><span data-stu-id="78991-277">UNG5: Functional Group Reference</span></span>  
  
    -   <span data-ttu-id="78991-278">UNG8：應用程式密碼</span><span class="sxs-lookup"><span data-stu-id="78991-278">UNG8: Application Password</span></span>  
  
-   <span data-ttu-id="78991-279">透過關聯配接器傳遞訊息</span><span class="sxs-lookup"><span data-stu-id="78991-279">Delivers the message via the associated adapter</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78991-280">請參閱</span><span class="sxs-lookup"><span data-stu-id="78991-280">See Also</span></span>  
 [<span data-ttu-id="78991-281">批次處理外寄 EDI 訊息</span><span class="sxs-lookup"><span data-stu-id="78991-281">Batching Outgoing EDI Messages</span></span>](../core/batching-outgoing-edi-messages.md)