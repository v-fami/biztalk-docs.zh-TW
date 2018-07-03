---
title: 設定外寄批次 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 75e6f41a-0e24-47bf-9234-125791c62044
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 267616af46eeb08e46d35d3a6fd5fdde2a22e877
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003407"
---
# <a name="configuring-an-outgoing-batch"></a><span data-ttu-id="c2769-102">設定外寄批次</span><span class="sxs-lookup"><span data-stu-id="c2769-102">Configuring an Outgoing Batch</span></span>
<span data-ttu-id="c2769-103">若要定義 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將交易集批次處理成 EDI 交換的方式，您必須為協議建立一或多個批次組態。</span><span class="sxs-lookup"><span data-stu-id="c2769-103">To define the way that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] batches transaction sets into an EDI interchange, you must create one or more batch configurations for an agreement.</span></span> <span data-ttu-id="c2769-104">所有由 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 關聯至該協議且符合批次篩選條件準則的交換，都會根據該批次組態的相同釋放準則進行批次處理和釋放。</span><span class="sxs-lookup"><span data-stu-id="c2769-104">All interchanges that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] associates to that agreement and that meet the filter criteria for a batch will be batched and released according to the same release criteria for that batch configuration.</span></span>  
  
 <span data-ttu-id="c2769-105">批次組態包括了批次名稱、批次識別碼、篩選條件定義、群組定義、批次釋放準則和批次啟動準則。</span><span class="sxs-lookup"><span data-stu-id="c2769-105">Batch configuration consists of a batch name, batch ID, filter definition, group definition, batch release criteria, and batch activation criteria.</span></span> <span data-ttu-id="c2769-106">所有屬性和與批次相關的選項都位於**批次組態**單向協議索引標籤中的頁面**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c2769-106">All properties and options related to batches are available on the **Batch Configuration** page of the one-way agreement tab in the **Agreement Properties** dialog box.</span></span> <span data-ttu-id="c2769-107">若要建立協議的批次組態，請參閱[設定批次處理 (X12)](../core/configuring-batching-x12.md)。</span><span class="sxs-lookup"><span data-stu-id="c2769-107">To create a batch configuration for an agreement, see [Configuring Batching (X12)](../core/configuring-batching-x12.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2769-108">批次的文件標準是由協議屬性本身決定。</span><span class="sxs-lookup"><span data-stu-id="c2769-108">The document standard for the batch is ascertained from the agreement properties itself.</span></span> <span data-ttu-id="c2769-109">例如，如果協議是針對 X12 訊息，則批次的文件標準會是 X12。</span><span class="sxs-lookup"><span data-stu-id="c2769-109">For example, if the agreement is for X12 messages, the document standard for the batches will be X12.</span></span>  
  
## <a name="batch-categories"></a><span data-ttu-id="c2769-110">批次類別</span><span class="sxs-lookup"><span data-stu-id="c2769-110">Batch Categories</span></span>  
 <span data-ttu-id="c2769-111">使用右上角的下拉式清單**批次組態**頁面，來決定所顯示的批次組態。</span><span class="sxs-lookup"><span data-stu-id="c2769-111">Use the drop-down list on the top-right corner of the **Batch Configuration** page to determine which batch configurations are displayed.</span></span>  
  
-   <span data-ttu-id="c2769-112">**所有**： 顯示所有批次組態。</span><span class="sxs-lookup"><span data-stu-id="c2769-112">**All**: Display all batch configurations.</span></span>  
  
-   <span data-ttu-id="c2769-113">**Active**： 僅顯示作用中批次組態。</span><span class="sxs-lookup"><span data-stu-id="c2769-113">**Active**: Display only the active batch configurations.</span></span>  
  
-   <span data-ttu-id="c2769-114">**非使用中**： 只顯示非作用中批次組態。</span><span class="sxs-lookup"><span data-stu-id="c2769-114">**Inactive**: Display only the inactive batch configurations.</span></span>  
  
## <a name="batch-identification"></a><span data-ttu-id="c2769-115">批次識別</span><span class="sxs-lookup"><span data-stu-id="c2769-115">Batch Identification</span></span>  
 <span data-ttu-id="c2769-116">批次識別包含批次名稱、描述、批次識別碼和批次協調流程執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="c2769-116">Batch identification contains batch name, description, batch ID, and the batching orchestration instance ID.</span></span>  
  
### <a name="batch-name"></a><span data-ttu-id="c2769-117">批次名稱</span><span class="sxs-lookup"><span data-stu-id="c2769-117">Batch Name</span></span>  
 <span data-ttu-id="c2769-118">根據指定的批次名稱建立批次組態**批次組態**單向協議索引標籤中的頁面**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c2769-118">A batch configuration is created based on the batch name specified in **Batch Configuration** page of the one-way agreement tab in the **Agreement Properties** dialog box.</span></span> <span data-ttu-id="c2769-119">多個批次可以共用相同的組態設定，但是必須具有唯一的批次名稱。</span><span class="sxs-lookup"><span data-stu-id="c2769-119">Multiple batches can share the same configuration settings, but must have a unique batch name.</span></span>  
  
### <a name="batch-description"></a><span data-ttu-id="c2769-120">批次描述</span><span class="sxs-lookup"><span data-stu-id="c2769-120">Batch Description</span></span>  
 <span data-ttu-id="c2769-121">批次描述文字方塊可提供批次組態的描述。</span><span class="sxs-lookup"><span data-stu-id="c2769-121">Batch description text box provides a description of the batch configuration.</span></span>  
  
### <a name="batch-id"></a><span data-ttu-id="c2769-122">批次識別碼</span><span class="sxs-lookup"><span data-stu-id="c2769-122">Batch ID</span></span>  
 <span data-ttu-id="c2769-123">批次識別碼自動產生[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中建立新的批次組態時**批次組態**頁面。</span><span class="sxs-lookup"><span data-stu-id="c2769-123">The batch ID is generated automatically by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] when a new batch configuration is created in the **Batch Configuration** page.</span></span> <span data-ttu-id="c2769-124">BatchMarker 管線元件使用此值，為符合特定批次組態之批次篩選條件的內送交換加上旗標。</span><span class="sxs-lookup"><span data-stu-id="c2769-124">This value is used by the BatchMarker pipeline component to flag incoming interchanges that match the batch filter of a specific batch configuration.</span></span> <span data-ttu-id="c2769-125">此值也會做為與特定批次組態相關聯之批次處理協調流程的訂閱篩選條件。</span><span class="sxs-lookup"><span data-stu-id="c2769-125">This value is also used as a subscription filter of the batching orchestration associated with a specific batch configuration.</span></span>  
  
### <a name="orchestration-instance-id"></a><span data-ttu-id="c2769-126">協調流程執行個體識別碼</span><span class="sxs-lookup"><span data-stu-id="c2769-126">Orchestration Instance ID</span></span>  
 <span data-ttu-id="c2769-127">針對此批次組態啟動之批次協調流程執行個體的協調流程執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="c2769-127">The orchestration instance ID of the batch orchestration instance that is activated for this batch configuration.</span></span>  
  
## <a name="batch-filter"></a><span data-ttu-id="c2769-128">批次篩選條件</span><span class="sxs-lookup"><span data-stu-id="c2769-128">Batch Filter</span></span>  
 <span data-ttu-id="c2769-129">批次建立時根據套用的批次篩選條件定義**批次組態**單向協議索引標籤中的頁面**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c2769-129">A batch is created based upon the batch filter definition applied in the **Batch Configuration** page of the one-way agreement tab in the **Agreement Properties** dialog box.</span></span> <span data-ttu-id="c2769-130">在這個篩選條件中，您會決定要批次處理哪些交易集或訊息。</span><span class="sxs-lookup"><span data-stu-id="c2769-130">In this filter, you determine which transaction sets or messages will be batched.</span></span> <span data-ttu-id="c2769-131">您可以在批次協調流程的執行個體已啟動的情況下，同時變更這個篩選條件的值。</span><span class="sxs-lookup"><span data-stu-id="c2769-131">You can change the value of this filter while an instance of the batch orchestration is activated.</span></span> <span data-ttu-id="c2769-132">變更這個篩選條件並不會影響批次釋放準則。</span><span class="sxs-lookup"><span data-stu-id="c2769-132">Changing the filter does not affect the batch release criteria.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2769-133">如果您變更作用中批次的批次篩選條件，則由於 Biztalk Server 會快取此資訊的關係，您將需要等候 15 分鐘的時間讓新的篩選條件準則變成作用中。</span><span class="sxs-lookup"><span data-stu-id="c2769-133">If you change the batch filter for an active batch, it will take 15 minutes for the new filter criteria to become active as this information is cached by Biztalk Server.</span></span> <span data-ttu-id="c2769-134">無法修改此重新整理間隔。</span><span class="sxs-lookup"><span data-stu-id="c2769-134">This refresh interval cannot be modified.</span></span>  
> 
>  <span data-ttu-id="c2769-135">若要強制將新的篩選條件立即變成作用中，請重新啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 主控件程序。</span><span class="sxs-lookup"><span data-stu-id="c2769-135">To force the new filter to become active immediately, restart the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] host process.</span></span>  
  
 <span data-ttu-id="c2769-136">外寄批次可包含多個群組，但一種交易類型只能有一個群組。</span><span class="sxs-lookup"><span data-stu-id="c2769-136">Outgoing batches can include multiple groups, but only one group per transaction type.</span></span> <span data-ttu-id="c2769-137">一個群組可以包含多個交易集，但每個交易集的交易類型都必須相同。</span><span class="sxs-lookup"><span data-stu-id="c2769-137">A group can contain multiple transaction sets, but each must have the same transaction type.</span></span>  
  
 <span data-ttu-id="c2769-138">多個批次組態可以共用同一個批次篩選條件，而符合多個批次篩選條件的文件將會路由至所有相符的批次。</span><span class="sxs-lookup"><span data-stu-id="c2769-138">Multiple batch configurations can share the same batch filter, if a document matches more than one batch filter it will be routed to all matching batches.</span></span>  
  
## <a name="group-definition"></a><span data-ttu-id="c2769-139">群組定義</span><span class="sxs-lookup"><span data-stu-id="c2769-139">Group Definition</span></span>  
 <span data-ttu-id="c2769-140">您可以透過在協議屬性中定義功能群組標頭 (X12 編碼為 GS，EDIFACT 編碼為 UNG)，決定批次輸出中的群組組成方式。</span><span class="sxs-lookup"><span data-stu-id="c2769-140">You determine how groups will be composed in the batch output by defining the Functional Group Headers (GS for X12 and UNG for EDIFACT) in the agreement properties.</span></span> <span data-ttu-id="c2769-141">群組則會根據其「交易集識別代碼」(ST1，X12 適用) 或「訊息類型」(UNH2.1，EDIFACT 適用)、所屬版本及其目標命名空間來加以定義。</span><span class="sxs-lookup"><span data-stu-id="c2769-141">Groups are defined according to their Transaction Set Identifier (ST1) for X12 or the Message Type (UNH2.1) for EDIFACT, their version, and their target namespace.</span></span> <span data-ttu-id="c2769-142">例如，交換可以包含組合了一種訊息類型的一個群組，以及另一個組合有其他種訊息類型的群組。</span><span class="sxs-lookup"><span data-stu-id="c2769-142">For example, an interchange can contain one group composed of one message type, and a second group composed of another message type.</span></span> <span data-ttu-id="c2769-143">如需有關設定群組的詳細資訊，請參閱 <<c0> [ 設定 EDI 屬性](../core/configuring-edi-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="c2769-143">For more information on configuring groups, see [Configuring EDI Properties](../core/configuring-edi-properties.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2769-144">交換中的群組則未定義順序。</span><span class="sxs-lookup"><span data-stu-id="c2769-144">The order of groups within an interchange is not defined.</span></span>  
  
## <a name="batch-release-criteria"></a><span data-ttu-id="c2769-145">批次釋放準則</span><span class="sxs-lookup"><span data-stu-id="c2769-145">Batch Release Criteria</span></span>  
 <span data-ttu-id="c2769-146">會根據設定的準則釋放批次**批次組態**單向協議索引標籤中的頁面**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c2769-146">Batches will be released according to criteria set in the **Batch Configuration** page of the one-way agreement tab in the **Agreement Properties** dialog box.</span></span> <span data-ttu-id="c2769-147">批次可能會根據下列任一方法來加以釋放：</span><span class="sxs-lookup"><span data-stu-id="c2769-147">Batches can be released in any of the following ways:</span></span>  
  
- <span data-ttu-id="c2769-148">根據每小時、每天或每週一次的排程。</span><span class="sxs-lookup"><span data-stu-id="c2769-148">According to a schedule, on an hourly, daily, or weekly basis.</span></span>  
  
- <span data-ttu-id="c2769-149">當交易集達到可湊成群組的特定數目。</span><span class="sxs-lookup"><span data-stu-id="c2769-149">When a specific number of transaction sets is available for a group.</span></span>  
  
- <span data-ttu-id="c2769-150">當交易集達到可湊成交換的特定數目。</span><span class="sxs-lookup"><span data-stu-id="c2769-150">When a specific number of transaction sets is available for an interchange.</span></span>  
  
- <span data-ttu-id="c2769-151">當字元達到可處理成批次的特定數目。</span><span class="sxs-lookup"><span data-stu-id="c2769-151">When a specific number of characters is available for batch processing.</span></span>  
  
- <span data-ttu-id="c2769-152">當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 外部的應用程式執行了外部觸發程序。</span><span class="sxs-lookup"><span data-stu-id="c2769-152">When an external trigger is executed by an application external to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
  <span data-ttu-id="c2769-153">如果您選取**傳送空的批次訊號**屬性上的**批次排程** 對話方塊中，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]排定即使已經沒有訊息要傳送的批次時，將傳送空的批次訊息收到的批次處理協調流程。</span><span class="sxs-lookup"><span data-stu-id="c2769-153">If you select the **Send empty batch signal** property on the **Batch Schedule** dialog box, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will send an empty batch message when the batch is scheduled to be sent even if no messages have been received by the batching orchestration.</span></span>  
  
## <a name="batch-activation-criteria"></a><span data-ttu-id="c2769-154">批次啟動準則</span><span class="sxs-lookup"><span data-stu-id="c2769-154">Batch Activation Criteria</span></span>  
 <span data-ttu-id="c2769-155">只有在符合批次啟動準則時，才會根據批次釋放準則來釋放批次。</span><span class="sxs-lookup"><span data-stu-id="c2769-155">Batches will be released according to the batch release criteria only when the batch activation criterion has been met.</span></span> <span data-ttu-id="c2769-156">若要啟動的協調流程執行個體，您必須按下**開始**按鈕**批次組態**單向協議索引標籤中的頁面**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c2769-156">To activate an instance of the orchestration, you must press the **Start** button in the **Batch Configuration** page of the one-way agreement tab in the **Agreement Properties** dialog box.</span></span> <span data-ttu-id="c2769-157">這樣會建立批次組態的協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="c2769-157">This creates an instance of the orchestration for the batch configuration.</span></span> <span data-ttu-id="c2769-158">如果**啟動**按鈕為可按，目前尚未啟動的批次組態的協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="c2769-158">If the **Start** button is available for clicking, an instance of the orchestration for the batch configuration is not currently activated.</span></span>  
  
 <span data-ttu-id="c2769-159">您按下後**啟動** 按鈕，只有當下列條件成立時，將批次收集訊息：</span><span class="sxs-lookup"><span data-stu-id="c2769-159">After you press the **Start** button, messages will be collected for a batch only if the following are true:</span></span>  
  
- <span data-ttu-id="c2769-160">這些訊息符合批次篩選條件中的準則。</span><span class="sxs-lookup"><span data-stu-id="c2769-160">The messages meet the criteria in the batch filter.</span></span>  
  
- <span data-ttu-id="c2769-161">日期和時間是之後輸入的日期時間**啟動**欄位。</span><span class="sxs-lookup"><span data-stu-id="c2769-161">The date and time are after the datetime entered in the **Start** field.</span></span>  
  
- <span data-ttu-id="c2769-162">日期和時間會在輸入值之前**來結束** 欄位中或處理的批次的數字是小於或等於在發生次數**發生幾次之後結束** 欄位中或**沒有結束日期**選項。</span><span class="sxs-lookup"><span data-stu-id="c2769-162">The date and time are before the value entered in the **End by** field, or the numbers of batches processed is less than or equal to the number of occurrences in the **End after (occurrences)** field, or the **No end date** option is selected.</span></span> <span data-ttu-id="c2769-163">底下的所有三個選項可**終止**一節。</span><span class="sxs-lookup"><span data-stu-id="c2769-163">All the three options are available under the **Termination** section.</span></span>  
  
  <span data-ttu-id="c2769-164">中所設定的啟動準則**批次組態**單向協議索引標籤中的頁面**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c2769-164">The activation criteria are set in the **Batch Configuration** page of the one-way agreement tab in the **Agreement Properties** dialog box.</span></span>  
  
  <span data-ttu-id="c2769-165">您已按下後**開始**按鈕來啟動批次處理協調流程執行個體，訊息將不會收集批次之前提及的時間**開始**屬性已通過。</span><span class="sxs-lookup"><span data-stu-id="c2769-165">After you have pressed the **Start** button to activate an instance of the batching orchestration, messages will not be collected for a batch until the time mentioned for the **Start** property has passed.</span></span>  <span data-ttu-id="c2769-166">在**批次組態**頁面上，如果**立即開始**未選取，**啟動**日期時間設定為早於您按時間值**啟動** 按鈕，批次處理將立即啟動協調流程變作用。</span><span class="sxs-lookup"><span data-stu-id="c2769-166">In the **Batch Configuration** page, if **Start immediately** is not selected and the **Start** datetime is set to a value prior to the time at which you press the **Start** button, batching will start as soon as the orchestration is active.</span></span> <span data-ttu-id="c2769-167">如果啟動日期時間是在未來時間，批次處理將會在該時間開始。</span><span class="sxs-lookup"><span data-stu-id="c2769-167">If the activation datetime is in the future, batching will start at that time.</span></span>  
  
  <span data-ttu-id="c2769-168">您可以設定**啟動**為未來的日期時間的日期時間。</span><span class="sxs-lookup"><span data-stu-id="c2769-168">You can set the **Start** datetime to be a datetime in the future.</span></span> <span data-ttu-id="c2769-169">不過，如果您按一下**開始**按鈕時**開始**日期時間是在未來，將會啟動協調流程執行個體，但會收集訊息，直到開始的日期時間，就會發生。</span><span class="sxs-lookup"><span data-stu-id="c2769-169">However, if you click the **Start** button when the **Start** datetime is in the future, the orchestration instance will be activated, but no messages will be collected until the start datetime occurs.</span></span> <span data-ttu-id="c2769-170">BatchMarker 管線元件會等到開始日期時間到了，才會升級要將訊息路由到路由協調流程或是批次處理協調流程時所需要的適當屬性。</span><span class="sxs-lookup"><span data-stu-id="c2769-170">The BatchMarker pipeline component will not promote the appropriate properties needed to route a message to the routing orchestration or the batching orchestration until the start datetime.</span></span> <span data-ttu-id="c2769-171">這樣一來，系統就不會批次處理該訊息。</span><span class="sxs-lookup"><span data-stu-id="c2769-171">As a result, the message will not be batched.</span></span> <span data-ttu-id="c2769-172">不過，訊息會收取任何傳送埠或個別的訊息訂閱的協調流程。</span><span class="sxs-lookup"><span data-stu-id="c2769-172">However, the messages will be picked up by any send port or orchestration subscribing to them as individual messages.</span></span> <span data-ttu-id="c2769-173">如需 BatchMarker 管線元件功用的詳細資訊，請參閱[組合批次 EDI 交換](../core/assembling-a-batched-edi-interchange.md)。</span><span class="sxs-lookup"><span data-stu-id="c2769-173">For more information on what the BatchMarker pipeline component does, see [Assembling a Batched EDI Interchange](../core/assembling-a-batched-edi-interchange.md).</span></span>  
  
## <a name="batch-termination-criteria"></a><span data-ttu-id="c2769-174">批次終止準則</span><span class="sxs-lookup"><span data-stu-id="c2769-174">Batch Termination Criteria</span></span>  
 <span data-ttu-id="c2769-175">訊息將會停止收集批次**來結束**日期時間或之後的中的發生次數**發生幾次之後結束**屬性。</span><span class="sxs-lookup"><span data-stu-id="c2769-175">Messages will cease to be collected for a batch after the **End by** datetime or after the number of occurrences in the **End after (occurrences)** property.</span></span> <span data-ttu-id="c2769-176">如果您不想要停用批次處理協調流程，請選取**沒有結束日期**選項。</span><span class="sxs-lookup"><span data-stu-id="c2769-176">If you do not want the batching orchestration to be deactivated, select the **No end date** option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2769-177">如果**發生幾次之後結束**選取的屬性，空的批次訊號計數朝結束批次啟動範圍所需的次數。</span><span class="sxs-lookup"><span data-stu-id="c2769-177">If the **End after (occurrences)** property has been selected, empty batch signals count toward the number of occurrences required to end the batch activation range.</span></span> <span data-ttu-id="c2769-178">如果發生通常會導致發出空批次訊號的情況 (在批次已排程傳送時，批次處理協調流程卻沒有收到任何訊息)，但是卻由於該訊號未設定而沒有傳送任何空的批次訊號時，發生次數也會進行遞增。</span><span class="sxs-lookup"><span data-stu-id="c2769-178">The number of occurrences will also be incremented if the conditions that would normally lead to an empty batch signal occur (no messages have been received by the batching orchestration when the batch is scheduled to be sent), but no empty batch signal is sent because the signal is not configured.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2769-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2769-179">See Also</span></span>  
 [<span data-ttu-id="c2769-180">批次處理外寄 EDI 訊息</span><span class="sxs-lookup"><span data-stu-id="c2769-180">Batching Outgoing EDI Messages</span></span>](../core/batching-outgoing-edi-messages.md)