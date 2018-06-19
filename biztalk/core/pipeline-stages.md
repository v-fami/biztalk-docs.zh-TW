---
title: 管線階段 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipelines, properties
- CATID_AssemblingSerializer component category
- CATID_Encoder component category
- pipelines, stages
- CATID_DisassemblingParser component category
- CATID_Validate component category
- ComponentCategory class attribute
- CATID_Decoder component category
- CATID_Any component category
- CATID_PartyResolver component category
- Execution Mode property
ms.assetid: ac50c48c-6ed5-4322-95cc-af55df6bcd1c
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aeb675f39cb39ade4230e6e39f798e95115aaf78
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22265502"
---
# <a name="pipeline-stages"></a><span data-ttu-id="3176e-102">管線階段</span><span class="sxs-lookup"><span data-stu-id="3176e-102">Pipeline Stages</span></span>
<span data-ttu-id="3176e-103">本主題討論**執行模式**屬性和階段相似性。</span><span class="sxs-lookup"><span data-stu-id="3176e-103">This topic discusses the **Execution Mode** property and stage affinity.</span></span>  
  
## <a name="execution-mode-property"></a><span data-ttu-id="3176e-104">Execution Mode 屬性</span><span class="sxs-lookup"><span data-stu-id="3176e-104">Execution Mode property</span></span>  
 <span data-ttu-id="3176e-105">在管線的執行期間，管線階段只能執行第一個辨識出訊息格式的元件，不然就是執行所有的元件。</span><span class="sxs-lookup"><span data-stu-id="3176e-105">During the execution of a pipeline, the pipeline stages can run only the first component that recognizes the message format, or all components.</span></span> <span data-ttu-id="3176e-106">決定執行模式的屬性是**執行模式**。</span><span class="sxs-lookup"><span data-stu-id="3176e-106">The property that determines the execution pattern is **Execution Mode**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3176e-107">這個屬性在管線範本的階段中為唯讀，但是對它的運作方式進行瞭解是相當重要的。</span><span class="sxs-lookup"><span data-stu-id="3176e-107">This property is read-only on the stages included in the pipeline templates, but understanding how it works is an important concept.</span></span>  
  
 <span data-ttu-id="3176e-108">當**執行模式**屬性設定為**所有**，執行階段內的所有元件中設定的順序。</span><span class="sxs-lookup"><span data-stu-id="3176e-108">When the **Execution Mode** property is set to **All**, all the components within the stage are run in the configured sequence.</span></span> <span data-ttu-id="3176e-109">此模式會執行數個元件來完成邏輯工作。</span><span class="sxs-lookup"><span data-stu-id="3176e-109">This mode runs several components to complete a logical task.</span></span> <span data-ttu-id="3176e-110">在此例中，若任何元件在管線階段中處理訊息時發生錯誤，就會產生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="3176e-110">In this case, a run-time error results if any component encounters an error while processing a message during this pipeline stage.</span></span>  
  
 <span data-ttu-id="3176e-111">當管線用來接收訊息數種格式，然後在**執行模式**屬性設定為**FirstMatch**。</span><span class="sxs-lookup"><span data-stu-id="3176e-111">When a pipeline is used to receive messages in several formats, then the **Execution Mode** property is set to **FirstMatch**.</span></span> <span data-ttu-id="3176e-112">在此模式中，只會執行第一個辨識出訊息的元件。</span><span class="sxs-lookup"><span data-stu-id="3176e-112">In this mode, only the first component that recognizes the message is run.</span></span> <span data-ttu-id="3176e-113">若階段中沒有任何元件辨識出此訊息，則會發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="3176e-113">If no components in the stage recognize the message, a run-time error results.</span></span>  
  
 <span data-ttu-id="3176e-114">請注意，每個階段可以有它自己**執行模式**管線內的設定，因此不同階段可以有不同的執行模式。</span><span class="sxs-lookup"><span data-stu-id="3176e-114">Note that each stage can have its own **Execution Mode** setting, so different stages within a pipeline can have different execution modes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3176e-115">在這一版的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]、 在傳送中的所有階段都管線和接收都管線中的除了 「 解譯 」 階段中具有的值**執行模式**屬性設定為**所有**。</span><span class="sxs-lookup"><span data-stu-id="3176e-115">In this release of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], all the stages in a send pipeline and all stages except Disassemble in a receive pipeline have the value of the **Execution Mode** property set to **All**.</span></span> <span data-ttu-id="3176e-116">值**執行模式**「 解譯 」 階段的屬性設定為**FirstMatch**。</span><span class="sxs-lookup"><span data-stu-id="3176e-116">The value of the **Execution Mode** property in the Disassemble stage is set to **FirstMatch**.</span></span> <span data-ttu-id="3176e-117">您無法變更**執行模式**階段的屬性。</span><span class="sxs-lookup"><span data-stu-id="3176e-117">You cannot change the **Execution Mode** property of a stage.</span></span>  
  
#### <a name="to-read-pipeline-stage-properties"></a><span data-ttu-id="3176e-118">讀取管線階段屬性</span><span class="sxs-lookup"><span data-stu-id="3176e-118">To read pipeline stage properties</span></span>  
  
1.  <span data-ttu-id="3176e-119">在「管線設計師」中按一下階段圖形。</span><span class="sxs-lookup"><span data-stu-id="3176e-119">In Pipeline Designer, click a stage shape.</span></span>  
  
2.  <span data-ttu-id="3176e-120">在 [屬性] 視窗中**一般**區段中，讀取下列屬性：</span><span class="sxs-lookup"><span data-stu-id="3176e-120">In the Properties window, in the **General** section, read the following properties:</span></span>  
  
    |<span data-ttu-id="3176e-121">使用</span><span class="sxs-lookup"><span data-stu-id="3176e-121">Use this</span></span>|<span data-ttu-id="3176e-122">動作</span><span class="sxs-lookup"><span data-stu-id="3176e-122">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="3176e-123">**名稱**</span><span class="sxs-lookup"><span data-stu-id="3176e-123">**Name**</span></span>|<span data-ttu-id="3176e-124">表示階段的名稱。</span><span class="sxs-lookup"><span data-stu-id="3176e-124">Indicates the name of the stage.</span></span>|  
    |<span data-ttu-id="3176e-125">**執行模式**</span><span class="sxs-lookup"><span data-stu-id="3176e-125">**Execution Mode**</span></span>|<span data-ttu-id="3176e-126">表示階段的執行模式。</span><span class="sxs-lookup"><span data-stu-id="3176e-126">Indicates the execution pattern of the stage.</span></span><br /><br /> <span data-ttu-id="3176e-127">有效值：**所有**或**FirstMatch**</span><span class="sxs-lookup"><span data-stu-id="3176e-127">Valid values: **All** or **FirstMatch**</span></span>|  
    |<span data-ttu-id="3176e-128">**元件的最小數目**</span><span class="sxs-lookup"><span data-stu-id="3176e-128">**Minimum Number of Components**</span></span>|<span data-ttu-id="3176e-129">表示能夠新增至階段之管線元件的最小數目。</span><span class="sxs-lookup"><span data-stu-id="3176e-129">Indicates the minimum number of pipeline components that can be added to the stage.</span></span>|  
    |<span data-ttu-id="3176e-130">**元件的最大數目**</span><span class="sxs-lookup"><span data-stu-id="3176e-130">**Maximum Number of Components**</span></span>|<span data-ttu-id="3176e-131">表示能夠新增至階段之管線元件的最大數目。</span><span class="sxs-lookup"><span data-stu-id="3176e-131">Indicates the maximum number of pipeline components that can be added to the stage.</span></span>|  
    |<span data-ttu-id="3176e-132">**StageID**</span><span class="sxs-lookup"><span data-stu-id="3176e-132">**StageID**</span></span>|<span data-ttu-id="3176e-133">表示階段的唯一識別項。</span><span class="sxs-lookup"><span data-stu-id="3176e-133">Indicates the unique identifier for the stage.</span></span>|  
  
## <a name="stage-affinity"></a><span data-ttu-id="3176e-134">階段相似性</span><span class="sxs-lookup"><span data-stu-id="3176e-134">Stage affinity</span></span>  
 <span data-ttu-id="3176e-135">管線元件擁有階段相似性，這表示建立它們的目的是為了在管線的某個或某些特定階段中使用。</span><span class="sxs-lookup"><span data-stu-id="3176e-135">Pipeline components have stage affinity, meaning that they are created for use within a particular stage or stages in a pipeline.</span></span>  
  
 <span data-ttu-id="3176e-136">以 COM 為基礎的管線元件來註冊自己以階段 ID 作為實作類別，表示對於階段相似性時。以網路為基礎的管線元件會使用指定階段相似性**ComponentCategory**類別屬性。</span><span class="sxs-lookup"><span data-stu-id="3176e-136">COM-based pipeline components express their stage affinity by registering themselves using the stage ID as the implementation category, while .NET-based pipeline components specify their stage affinity by using the **ComponentCategory** class attribute.</span></span> <span data-ttu-id="3176e-137">請注意，它可能元件將本身與多個階段產生關聯 — 元件可以有一個以上的實作類別或**ComponentCategory**屬性。</span><span class="sxs-lookup"><span data-stu-id="3176e-137">Note that it is possible for a component to associate itself with more than one stage—components can have more than one implementation category or **ComponentCategory** attribute.</span></span>  
  
 <span data-ttu-id="3176e-138">下表顯示可用的元件類別和其關聯階段。</span><span class="sxs-lookup"><span data-stu-id="3176e-138">The following table shows the available component categories and their associated stages.</span></span>  
  
|<span data-ttu-id="3176e-139">元件類別</span><span class="sxs-lookup"><span data-stu-id="3176e-139">Component category</span></span>|<span data-ttu-id="3176e-140">可放置元件的階段</span><span class="sxs-lookup"><span data-stu-id="3176e-140">Stage where component can be placed</span></span>|<span data-ttu-id="3176e-141">Description</span><span class="sxs-lookup"><span data-stu-id="3176e-141">Description</span></span>|  
|------------------------|-----------------------------------------|-----------------|  
|<span data-ttu-id="3176e-142">CATID_Decoder {9d0e4103-4cce-4536-83fa-4a5040674ad6}</span><span class="sxs-lookup"><span data-stu-id="3176e-142">CATID_Decoder {9d0e4103-4cce-4536-83fa-4a5040674ad6}</span></span>|<span data-ttu-id="3176e-143">解碼</span><span class="sxs-lookup"><span data-stu-id="3176e-143">Decode</span></span>|<span data-ttu-id="3176e-144">所有的解碼元件都必須實作此類別。</span><span class="sxs-lookup"><span data-stu-id="3176e-144">All decoding components should implement this category.</span></span>|  
|<span data-ttu-id="3176e-145">CATID_DisassemblingParser {9d0e4105-4cce-4536-83fa-4a5040674ad6}</span><span class="sxs-lookup"><span data-stu-id="3176e-145">CATID_DisassemblingParser {9d0e4105-4cce-4536-83fa-4a5040674ad6}</span></span>|<span data-ttu-id="3176e-146">Disassemble</span><span class="sxs-lookup"><span data-stu-id="3176e-146">Disassemble</span></span>|<span data-ttu-id="3176e-147">所有的解譯和剖析元件都必須實作此類別。</span><span class="sxs-lookup"><span data-stu-id="3176e-147">All disassembling and parsing components should implement this category.</span></span>|  
|<span data-ttu-id="3176e-148">CATID_Validate {9d0e410d-4cce-4536-83fa-4a5040674ad6}</span><span class="sxs-lookup"><span data-stu-id="3176e-148">CATID_Validate {9d0e410d-4cce-4536-83fa-4a5040674ad6}</span></span>|<span data-ttu-id="3176e-149">Validate</span><span class="sxs-lookup"><span data-stu-id="3176e-149">Validate</span></span>|<span data-ttu-id="3176e-150">驗證元件都必須實作此類別。</span><span class="sxs-lookup"><span data-stu-id="3176e-150">Validation components should implement this category.</span></span>|  
|<span data-ttu-id="3176e-151">CATID_PartyResolver {9d0e410e-4cce-4536-83fa-4a5040674ad6}</span><span class="sxs-lookup"><span data-stu-id="3176e-151">CATID_PartyResolver {9d0e410e-4cce-4536-83fa-4a5040674ad6}</span></span>|<span data-ttu-id="3176e-152">ResolveParty</span><span class="sxs-lookup"><span data-stu-id="3176e-152">ResolveParty</span></span>|<span data-ttu-id="3176e-153">「合作對象解析」元件使用的階段。</span><span class="sxs-lookup"><span data-stu-id="3176e-153">Stage used for Party Resolution component.</span></span>|  
|<span data-ttu-id="3176e-154">CATID_Encoder {9d0e4108-4cce-4536-83fa-4a5040674ad6}</span><span class="sxs-lookup"><span data-stu-id="3176e-154">CATID_Encoder {9d0e4108-4cce-4536-83fa-4a5040674ad6}</span></span>|<span data-ttu-id="3176e-155">編碼</span><span class="sxs-lookup"><span data-stu-id="3176e-155">Encode</span></span>|<span data-ttu-id="3176e-156">所有的編碼元件都必須實作此類別。</span><span class="sxs-lookup"><span data-stu-id="3176e-156">All encoding components should implement this category.</span></span>|  
|<span data-ttu-id="3176e-157">CATID_AssemblingSerializer {9d0e4107-4cce-4536-83fa-4a5040674ad6}</span><span class="sxs-lookup"><span data-stu-id="3176e-157">CATID_AssemblingSerializer {9d0e4107-4cce-4536-83fa-4a5040674ad6}</span></span>|<span data-ttu-id="3176e-158">序列化</span><span class="sxs-lookup"><span data-stu-id="3176e-158">Serialize</span></span>|<span data-ttu-id="3176e-159">所有的序列化和組合元件都必須實作此類別。</span><span class="sxs-lookup"><span data-stu-id="3176e-159">All serializing and assembling components should implement this category.</span></span>|  
|<span data-ttu-id="3176e-160">CATID_Any {9d0e4101-4cce-4536-83fa-4a5040674ad6}</span><span class="sxs-lookup"><span data-stu-id="3176e-160">CATID_Any {9d0e4101-4cce-4536-83fa-4a5040674ad6}</span></span>|<span data-ttu-id="3176e-161">任一階段</span><span class="sxs-lookup"><span data-stu-id="3176e-161">Any of these stages</span></span>|<span data-ttu-id="3176e-162">若某個管線元件實作此類別，則表示該元件可以放入管線的任一階段中。</span><span class="sxs-lookup"><span data-stu-id="3176e-162">If a pipeline component implements this category, it means that the component can be placed into any stage of a pipeline.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3176e-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3176e-163">See Also</span></span>  
 <span data-ttu-id="3176e-164">[建立管線使用管線設計師](../core/creating-pipelines-using-pipeline-designer.md) </span><span class="sxs-lookup"><span data-stu-id="3176e-164">[Creating Pipelines Using Pipeline Designer](../core/creating-pipelines-using-pipeline-designer.md) </span></span>  
 [<span data-ttu-id="3176e-165">關於管線、 階段和元件</span><span class="sxs-lookup"><span data-stu-id="3176e-165">About Pipelines, Stages, and Components</span></span>](../core/about-pipelines-stages-and-components.md)