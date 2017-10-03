---
title: "反組譯階段 （可復原交換處理） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 552b1e90-f75d-4713-8c7b-155a52819308
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f36dd7a9d8bb10180d4af0562ba1e869957415d8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="disassembly-stage-recoverable-interchange-processing"></a><span data-ttu-id="3b9e0-102">反組譯階段 (可復原交換處理)</span><span class="sxs-lookup"><span data-stu-id="3b9e0-102">Disassembly Stage (Recoverable Interchange Processing)</span></span>
<span data-ttu-id="3b9e0-103">在解譯階段可以使用兩種模式處理交換：</span><span class="sxs-lookup"><span data-stu-id="3b9e0-103">Interchanges are processed at the disassembly stage in two modes:</span></span>  
  
-   <span data-ttu-id="3b9e0-104">**標準模式。**</span><span class="sxs-lookup"><span data-stu-id="3b9e0-104">**Standard mode.**</span></span> <span data-ttu-id="3b9e0-105">當接收管線的解譯器元件設定為執行標準解譯時，包含在交換中的訊息會被擷取、由接收管線處理、對應並發佈為交易式工作單位。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-105">When the disassembler component of a receive pipeline is configured to perform standard disassembly, the messages contained in an interchange are extracted, processed by the receive pipeline, mapped, and published as a transactional unit of work.</span></span> <span data-ttu-id="3b9e0-106">也就是說，會完整地處理整個交換及其包含的訊息並發佈到 MessageBox 資料庫，或是將交換放置在已擱置佇列中。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-106">That is, either the entire interchange and its contained messages are fully processed and published into the MessageBox database, or the interchange is placed in the Suspended queue.</span></span>  
  
-   <span data-ttu-id="3b9e0-107">**可復原模式。**</span><span class="sxs-lookup"><span data-stu-id="3b9e0-107">**Recoverable mode.**</span></span> <span data-ttu-id="3b9e0-108">當接收管線的解譯器元件設定為執行**可復原交換處理**，各自擷取包含在交換中的訊息。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-108">When the disassembler component of a receive pipeline is configured to perform **recoverable interchange processing**, the messages contained in an interchange are extracted independently of each other.</span></span> <span data-ttu-id="3b9e0-109">成功擷取的訊息會進一步傳播到接收管線。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-109">Messages that are successfully extracted are propagated further down the receive pipeline.</span></span> <span data-ttu-id="3b9e0-110">在交換中已識別但未成功擷取的訊息，會放置在已擱置佇列中。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-110">Messages that are identified within an interchange but are not successfully extracted are placed in the Suspended queue.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="3b9e0-111">範例</span><span class="sxs-lookup"><span data-stu-id="3b9e0-111">Examples</span></span>  
 <span data-ttu-id="3b9e0-112">下列範例說明交換處理實例。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-112">The following examples illustrate interchange processing scenarios.</span></span>  
  
### <a name="example-1"></a><span data-ttu-id="3b9e0-113">範例 1</span><span class="sxs-lookup"><span data-stu-id="3b9e0-113">Example 1</span></span>  
 <span data-ttu-id="3b9e0-114">在此範例中，下列虛擬交換在標準交換接收位置上提交。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-114">In this example, the following pseudo-interchange is submitted on a standard interchange receive location.</span></span> <span data-ttu-id="3b9e0-115">也就是說，接收管線中的解譯器元件為標準交換處理所設定。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-115">That is, the disassembler component in the receive pipeline is configured for standard interchange processing.</span></span>  
  
```  
<Interchange>  
<Document1>...</Document1>  
<Document2 failure=”routing”>...</Document2>  
<Document3>...</Document3>  
<Document4 failure=”pipeline” recoverableError=”true”>...</Document4>  
<Document5>...</Document5>  
</Interchange>  
```  
  
 <span data-ttu-id="3b9e0-116">此交換包含五個訊息，解譯器可成功地從交換擷取所有這些訊息。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-116">This interchange contains five messages, all of which the disassembler successfully extracts from the interchange.</span></span> <span data-ttu-id="3b9e0-117">處理方式如下所示：</span><span class="sxs-lookup"><span data-stu-id="3b9e0-117">They are processed as follows:</span></span>  
  
-   <span data-ttu-id="3b9e0-118">第一個、第二個以及第三個訊息透過管線傳播並準備發佈。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-118">The first, second, and third messages propagate through the pipeline and are ready to be published.</span></span>  
  
-   <span data-ttu-id="3b9e0-119">第四個訊息在管線的解譯階段處理失敗。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-119">The fourth message fails processing at the disassembling stage in the pipeline.</span></span> <span data-ttu-id="3b9e0-120">這造成所有已經處理的訊息回復，而且原始交換訊息被擱置為可繼續。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-120">This causes all the messages that have already been processed to roll back and the original interchange message to be suspended as resumable.</span></span>  
  
 <span data-ttu-id="3b9e0-121">提交的結果為：</span><span class="sxs-lookup"><span data-stu-id="3b9e0-121">The result of submission is:</span></span>  
  
-   <span data-ttu-id="3b9e0-122">沒有發佈任何訊息。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-122">Nothing is published.</span></span> <span data-ttu-id="3b9e0-123">原始交換已擱置，因為在標準交換處理中，在交換處理期間或之後的任一點失敗的任何已擷取訊息，將導致所有已擷取訊息被捨棄，且原始交換以可繼續狀態放置在已擱置佇列中。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-123">The original interchange is suspended because in standard interchange processing, any extracted message that fails at any point during or after interchange processing results in all extracted messages being discarded and the original interchange being placed on the Suspended queue as resumable.</span></span>  
  
### <a name="example-2"></a><span data-ttu-id="3b9e0-124">範例 2</span><span class="sxs-lookup"><span data-stu-id="3b9e0-124">Example 2</span></span>  
 <span data-ttu-id="3b9e0-125">本範例使用與上一個範例相同的交換處理與傳播實例，除了解譯階段設定為執行可復原交換處理之外。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-125">The example uses the same interchange processing and propagation scenario as the previous example, except that the disassembly stage is configured to do recoverable interchange processing.</span></span>  
  
 <span data-ttu-id="3b9e0-126">提交的結果是個別擷取的訊息已全部處理，並捨棄原始交換。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-126">The result of submission is that individual extracted messages are all processed and the original interchange is discarded.</span></span> <span data-ttu-id="3b9e0-127">個別訊息的處理方式如下所示：</span><span class="sxs-lookup"><span data-stu-id="3b9e0-127">The individual messages are processed as follows:</span></span>  
  
-   <span data-ttu-id="3b9e0-128">第一個、第二個以及第三個訊息透過管線傳播並準備發佈。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-128">The first, second, and third messages propagate through the pipeline and are ready to be published.</span></span>  
  
-   <span data-ttu-id="3b9e0-129">第四個訊息解譯處理失敗 (也就是說，在擷取此訊息之後發生錯誤)，並已準備將它擱置。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-129">The fourth message fails disassembly processing (that is, something goes wrong after it is extracted) and is ready to be suspended.</span></span>  
  
-   <span data-ttu-id="3b9e0-130">第五個訊息透過管線傳播並準備發佈。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-130">The fifth message propagates through the pipeline and is ready to be published.</span></span>  
  
-   <span data-ttu-id="3b9e0-131">從交換擷取所有訊息之後，就會將訊息 1、2、3 及 5 發佈到 MessageBox 資料庫，並將訊息 4 放置在已擱置佇列中。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-131">After all messages are extracted from the interchange, messages 1, 2, 3, and 5 are published into the MessageBox database, and message 4 is placed on the Suspended queue.</span></span> <span data-ttu-id="3b9e0-132">訊息 2 由於沒有符合的訂閱者而造成路由失敗，也會重新導向至已擱置佇列。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-132">Message 2 is also redirected to the Suspended queue because of a routing failure due to no matching subscriber.</span></span>  
  
## <a name="configuring-recoverable-interchange-processing"></a><span data-ttu-id="3b9e0-133">設定可復原交換處理</span><span class="sxs-lookup"><span data-stu-id="3b9e0-133">Configuring Recoverable Interchange Processing</span></span>  
 <span data-ttu-id="3b9e0-134">可復原交換處理是接收管線解譯器元件的屬性。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-134">Recoverable interchange processing is a property of the disassembler component of a receive pipeline.</span></span> <span data-ttu-id="3b9e0-135">並非所有解譯器元件都可讓您指定可復原交換處理，例如，原生 BizTalk Framework 解譯器就不允許。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-135">Not all disassembler components allow you to specify recoverable interchange processing; for example, the native BizTalk Framework disassembler does not.</span></span> <span data-ttu-id="3b9e0-136">若解譯器支援可復原交換處理，則當您將解譯器元件新增至所設計管線的解譯階段時，就可以在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的管線設計師中指定此行為。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-136">If a disassembler supports recoverable interchange processing, then you specify this behavior in Pipeline Designer within [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] when you add the disassembler component to the Disassemble stage of the pipeline being designed.</span></span> <span data-ttu-id="3b9e0-137">您將選取的解譯器拖曳到管線的解譯階段之後，您會設定可復原交換處理屬性，該解譯器元件的`true`。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-137">After you drag the selected disassembler onto the Disassemble stage of the pipeline, you set the recoverable interchange processing property of that disassembler component to `true`.</span></span>  
  
### <a name="party-resolution"></a><span data-ttu-id="3b9e0-138">合作對象解析</span><span class="sxs-lookup"><span data-stu-id="3b9e0-138">Party Resolution</span></span>  
 <span data-ttu-id="3b9e0-139">在可復原交換處理中成功擷取的訊息，則根據為父交換已到達之接收埠所設定的合作對象，來識別傳送合作對象。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-139">Messages that are successfully extracted in recoverable interchange processing have their sending party identified according to the party configured for the receive port on which the parent interchange arrived.</span></span> <span data-ttu-id="3b9e0-140">若有任何從指定交換擷取的訊息之合作對象解析失敗，則整個交換的合作對象解析會被視為已失敗。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-140">If party resolution fails for any message extracted from a given interchange, then party resolution is considered to have failed for the entire interchange.</span></span>  
  
### <a name="restrictions"></a><span data-ttu-id="3b9e0-141">限制</span><span class="sxs-lookup"><span data-stu-id="3b9e0-141">Restrictions</span></span>  
  
-   <span data-ttu-id="3b9e0-142">當交換在解譯器中失敗時，交換會被擱置為可繼續。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-142">When an interchange fails in the disassembler, the interchange is suspended as resumable.</span></span> <span data-ttu-id="3b9e0-143">不過，若系統管理繼續此交換，它會再次失敗，因為造成解譯失敗的這些類型錯誤只是交換內容的結果，當交換繼續時，仍會維持相同結果。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-143">However, if the interchange is administratively resumed, it will fail again because the kinds of errors that cause disassembly failure are solely a result of the interchange content, which stays the same when the interchange is resumed.</span></span> <span data-ttu-id="3b9e0-144">必須修改這類失敗的交換並透過接收位置重新提交。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-144">Such a failed interchange must be modified and resubmitted through a receive location.</span></span>  
  
-   <span data-ttu-id="3b9e0-145">若訊息已從交換成功擷取，之後在透過傳訊傳播時由於不相符的訂閱者而失敗，則會將訊息擱置為可繼續。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-145">If a message that was successfully extracted from an interchange subsequently fails to propagate through messaging due to an unmatched subscriber, the message is suspended as resumable.</span></span> <span data-ttu-id="3b9e0-146">若已修正路由失敗的原因，則此訊息可由系統管理繼續。</span><span class="sxs-lookup"><span data-stu-id="3b9e0-146">This message can be administratively resumed if the cause of the routing failure is fixed.</span></span>  
  
-   <span data-ttu-id="3b9e0-147">儘管在解譯器元件中發生下列錯誤，解譯器元件仍會繼續從交換擷取訊息：</span><span class="sxs-lookup"><span data-stu-id="3b9e0-147">The disassembler component continues to extract messages from an interchange despite the following errors in disassembler components:</span></span>  
  
    -   <span data-ttu-id="3b9e0-148">找不到結構描述</span><span class="sxs-lookup"><span data-stu-id="3b9e0-148">Schema not found</span></span>  
  
    -   <span data-ttu-id="3b9e0-149">結構描述模擬兩可未解析 (也就是說，相同訊息類型有一個以上的結構描述)</span><span class="sxs-lookup"><span data-stu-id="3b9e0-149">Schema ambiguity not resolved (that is, more than one schema exists for the same message type)</span></span>  
  
    -   <span data-ttu-id="3b9e0-150">XML 驗證失敗</span><span class="sxs-lookup"><span data-stu-id="3b9e0-150">XML validation failed</span></span>  
  
    -   <span data-ttu-id="3b9e0-151">一般檔案剖析失敗</span><span class="sxs-lookup"><span data-stu-id="3b9e0-151">Flat-file parsing failed</span></span>  
  
-   <span data-ttu-id="3b9e0-152">解譯器元件**不**繼續從交換擷取訊息，如果解譯器元件中就會發生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="3b9e0-152">The disassembler component does **not** continue to extract messages from an interchange if the following error occurs in disassembler components:</span></span>  
  
    -   <span data-ttu-id="3b9e0-153">文件資料不是格式正確的 XML—任何會造成 System.Xml.XmlReader 失敗的文件屬性</span><span class="sxs-lookup"><span data-stu-id="3b9e0-153">Document data is not well-formed XML—any document properties that would cause System.Xml.XmlReader to fail</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b9e0-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b9e0-154">See Also</span></span>  
 <span data-ttu-id="3b9e0-155">[如何設定 XML 解譯器管線元件](../core/how-to-configure-the-xml-disassembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="3b9e0-155">[How to Configure the XML Disassembler Pipeline Component](../core/how-to-configure-the-xml-disassembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="3b9e0-156">如何設定一般檔案解譯器管線元件</span><span class="sxs-lookup"><span data-stu-id="3b9e0-156">How to Configure the Flat File Disassembler Pipeline Component</span></span>](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md)