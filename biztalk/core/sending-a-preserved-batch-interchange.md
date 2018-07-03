---
title: 傳送保留批次交換 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d9bc2207-e34d-4d06-a224-bd7f8e498c27
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1fe98e5547501717c952e54f9be5a4d2f82a23bb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015759"
---
# <a name="sending-a-preserved-batch-interchange"></a><span data-ttu-id="30866-102">傳送保留的批次交換</span><span class="sxs-lookup"><span data-stu-id="30866-102">Sending a Preserved Batch Interchange</span></span>
<span data-ttu-id="30866-103">當 EDI 傳送管線處理保留的輸出批次交換時，它會將該批次交換一起處理。</span><span class="sxs-lookup"><span data-stu-id="30866-103">When the EDI send pipeline processes an outbound preserved batch interchange, it processes the batched interchange as a whole.</span></span> <span data-ttu-id="30866-104">它通常會重複使用現有信封 （控制項） 區段中建立 EDI 交換，而不是根據協議的信封套用。</span><span class="sxs-lookup"><span data-stu-id="30866-104">It normally reuses the existing envelope (control) segments in creating the EDI interchange, rather than applying an envelope based upon the agreement.</span></span> <span data-ttu-id="30866-105">發生這種情況時**輸入批次處理選項**屬性設定為**保留交換-發生錯誤時暫停交換**或**保留交換-發生時暫停交易集錯誤**。</span><span class="sxs-lookup"><span data-stu-id="30866-105">This occurs when the **Inbound batch processing option** property is set to **Preserve Interchange - suspend Interchange on Error** or **Preserve Interchange - suspend Transaction Sets on Error**.</span></span>  
  
## <a name="schema-validation"></a><span data-ttu-id="30866-106">結構描述驗證</span><span class="sxs-lookup"><span data-stu-id="30866-106">Schema Validation</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="30866-107"> 會使用批次結構描述和服務結構描述來驗證保留批次的信封。</span><span class="sxs-lookup"><span data-stu-id="30866-107"> validates the envelope of a preserved batch using the batch schemas and the service schemas.</span></span> <span data-ttu-id="30866-108">批次結構描述可用來驗證保留訊息的根節點，而服務結構描述則用於驗證交換、群組，以及交易集標頭和結尾。</span><span class="sxs-lookup"><span data-stu-id="30866-108">The batch schema is used to validate the root node of the preserved message; the service schemas are used to validate the interchange, group, and transaction set headers and trailers.</span></span> <span data-ttu-id="30866-109">如需有關批次結構描述的詳細資訊，請參閱 < [EDI 批次結構描述](../core/edi-batch-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="30866-109">For more information about the batch schemas, see [EDI Batch Schemas](../core/edi-batch-schemas.md).</span></span> <span data-ttu-id="30866-110">如需有關服務結構描述的詳細資訊，請參閱 < [EDI 服務和控制結構描述](../core/edi-service-and-control-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="30866-110">For more information on the service schemas, see [EDI Service and Control Schemas](../core/edi-service-and-control-schemas.md).</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="30866-111"> 會使用專案中的文件結構描述來驗證批次交換中的文件。</span><span class="sxs-lookup"><span data-stu-id="30866-111"> validates the documents in a batched interchange using the document schemas in your project.</span></span>  
  
## <a name="send-side-processing"></a><span data-ttu-id="30866-112">傳送端處理</span><span class="sxs-lookup"><span data-stu-id="30866-112">Send-Side Processing</span></span>  
 <span data-ttu-id="30866-113">當 EDI 組合器處理保留交換時，它通常會使用收到批次交換時該批次中現有的相同交換、群組和交易集標頭。</span><span class="sxs-lookup"><span data-stu-id="30866-113">When the EDI Assembler processes a preserved interchange, it normally uses the same interchange, group, and transaction-set headers that existed in the batched interchange when it was received.</span></span>  
  
- <span data-ttu-id="30866-114">對於 X12 交換，在單向協議索引標籤中的不同頁面上的屬性設定**協議屬性** 對話方塊中 (用來決定如何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會建立外寄的 ISA、 GS 和 ST 標頭交換） 通常不會套用。</span><span class="sxs-lookup"><span data-stu-id="30866-114">For X12 interchanges, the property settings on different pages in the one-way agreement tab in the **Agreement Properties** dialog box (which determine how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will create the ISA, GS, and ST headers of an outgoing interchange) do not normally apply.</span></span>  
  
- <span data-ttu-id="30866-115">若是 EDIFACT 交換，通常會使用協議屬性中的 UNA 設定。</span><span class="sxs-lookup"><span data-stu-id="30866-115">For EDIFACT interchanges, the UNA settings in the agreement properties are normally used.</span></span> <span data-ttu-id="30866-116">UNA 區段在 EDIFACT 編碼訊息中是選用項目，但在序列化保留的批次交換時是必要項目。</span><span class="sxs-lookup"><span data-stu-id="30866-116">The UNA segment is optional in an EDIFACT-encoded message, but it is required for serializing a preserved batch interchange.</span></span> <span data-ttu-id="30866-117">如果 XML 執行個體中的 UNA 區段沒有指定值，則會使用傳送管線元件的預設屬性值。</span><span class="sxs-lookup"><span data-stu-id="30866-117">If there is no value for the UNA segment in the XML instance, the default property values for the send pipeline component will be used.</span></span> <span data-ttu-id="30866-118">如果未指定傳送管線元件屬性的值，保留批次中繼 XML 訊息將會遭到擱置。</span><span class="sxs-lookup"><span data-stu-id="30866-118">If the send pipeline component properties are not valued, then the preserved batch intermediate XML message will be suspended.</span></span>  
  
- <span data-ttu-id="30866-119">如果您將要保留之交換上的 `EDI.PopulateInterchangeValues` 內容屬性升級為 "True" (使用自訂元件)，傳送埠中的 EdiAssembler 就會將設定在協議屬性中的值填入所有的交換、群組和交易集標頭。</span><span class="sxs-lookup"><span data-stu-id="30866-119">If you promote the `EDI.PopulateInterchangeValues` context property to "True" on the interchange being preserved (in a custom component), the EdiAssembler in the send port will populate all of the interchange, group, and transaction-set headers to the values set in the agreement properties.</span></span>  
  
- <span data-ttu-id="30866-120">如果您在傳送管線處理 `EDIOverride.OverrideEdiHeader` 內容屬性之前，在交換上將它升級為 "True"，則可以透過設定適當的 `EDIOverride` 內容屬性值來覆寫輸出文件的信封值。</span><span class="sxs-lookup"><span data-stu-id="30866-120">If you promote the `EDIOverride.OverrideEdiHeader` context property to “True” on the interchange before it is processed by the send pipeline, you can override the envelope values for the outbound document by setting the appropriate `EDIOverride` context property values.</span></span> <span data-ttu-id="30866-121">如需詳細資訊，請參閱 <<c0> [ 覆寫 EDI 標頭](../core/overriding-edi-headers.md)。</span><span class="sxs-lookup"><span data-stu-id="30866-121">For more information, see [Overriding EDI Headers](../core/overriding-edi-headers.md).</span></span>  
  
  <span data-ttu-id="30866-122">對於沒有錯誤的保留交換，組合器會保留交換群組中的交易集順序和交換中的群組順序。</span><span class="sxs-lookup"><span data-stu-id="30866-122">For a preserved interchange that has no errors, the Assembler will preserve the sequence of transaction sets in a group of the interchange and the sequence of groups in the interchange.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30866-123">您可以透過 XML 傳送管線來傳送保留批次。</span><span class="sxs-lookup"><span data-stu-id="30866-123">You can send a preserved batch with an XML send pipeline.</span></span> <span data-ttu-id="30866-124">不過，這時您必須修改該批次結構描述的命名空間。</span><span class="sxs-lookup"><span data-stu-id="30866-124">However, to do so requires that you change the namespace for the batch schema.</span></span> <span data-ttu-id="30866-125">如需詳細資訊，請參閱 <<c0> [ 透過 XML 傳送管線來傳送保留批次](../core/sending-a-preserved-batch-with-an-xml-send-pipeline.md)。</span><span class="sxs-lookup"><span data-stu-id="30866-125">For more information, see [Sending a Preserved Batch with an XML Send Pipeline](../core/sending-a-preserved-batch-with-an-xml-send-pipeline.md).</span></span>  
  
## <a name="error-processing"></a><span data-ttu-id="30866-126">錯誤處理</span><span class="sxs-lookup"><span data-stu-id="30866-126">Error Processing</span></span>  
 <span data-ttu-id="30866-127">EDI 傳送管線會因為 XML 中的保留標記，而將批次 EDI 交換辨識為保留批次。</span><span class="sxs-lookup"><span data-stu-id="30866-127">The EDI send pipeline recognizes a batched EDI interchange as a preserved batch because of a reserved tag in the XML.</span></span> <span data-ttu-id="30866-128">此標記，或是\<X12InterchangeXml\>或\<EdifactInterchangeXml\>，套用至 XML 由 EDI 接收管線。</span><span class="sxs-lookup"><span data-stu-id="30866-128">This tag, either \<X12InterchangeXml\> or \<EdifactInterchangeXml\>, is applied to the XML by the EDI receive pipeline.</span></span>  
  
 <span data-ttu-id="30866-129">下列特殊案例適用於發生錯誤時擱置交易集的情況：</span><span class="sxs-lookup"><span data-stu-id="30866-129">The following special cases apply to suspending transaction sets on error:</span></span>  
  
-   <span data-ttu-id="30866-130">如果群組中的所有交易集全都無效，EDI 傳送管線就會將群組控制區段包含到產生的 EDI 中，但該群組不會包含任何交易集 (因為已經捨棄)。</span><span class="sxs-lookup"><span data-stu-id="30866-130">If all transaction sets in a group are invalid, then the EDI send pipeline will include group control segments in the generated EDI, but the group will not contain any transaction sets (because they will have been dropped).</span></span> <span data-ttu-id="30866-131">群組尾總計會更新為零。</span><span class="sxs-lookup"><span data-stu-id="30866-131">The group footer totals are updated to zero.</span></span> <span data-ttu-id="30866-132">交換控制區段則保持不變。</span><span class="sxs-lookup"><span data-stu-id="30866-132">The interchange control segments remain unchanged.</span></span>  
  
-   <span data-ttu-id="30866-133">如果交換中的所有交易集全都無效，交換控制區段仍然會包含在產生的 EDI 交換中，但該交換不會包含任何交易集 (因為已經捨棄)。</span><span class="sxs-lookup"><span data-stu-id="30866-133">If all transaction sets in an interchange are invalid, then the interchange control segments will still be included in the generated EDI interchange, but the interchange will not contain any transaction sets (because they will have been dropped).</span></span> <span data-ttu-id="30866-134">這會構成空白交換。</span><span class="sxs-lookup"><span data-stu-id="30866-134">This would constitute an empty interchange.</span></span>  
  
-   <span data-ttu-id="30866-135">如果群組控制區段或交換控制區段無效，就不會產生 EDI 編碼交換。</span><span class="sxs-lookup"><span data-stu-id="30866-135">If the group control segments or the interchange control segments are invalid, an EDI-encoded interchange will not be generated.</span></span> <span data-ttu-id="30866-136">事件檢視器中將會建立記錄檔，表示該次交換已遭拒絕。</span><span class="sxs-lookup"><span data-stu-id="30866-136">A log will be created in the event viewer indicating that the interchange was rejected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30866-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30866-137">See Also</span></span>  
 [<span data-ttu-id="30866-138">批次處理外寄 EDI 訊息</span><span class="sxs-lookup"><span data-stu-id="30866-138">Batching Outgoing EDI Messages</span></span>](../core/batching-outgoing-edi-messages.md)