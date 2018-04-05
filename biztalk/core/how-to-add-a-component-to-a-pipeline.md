---
title: 如何新增元件至管線 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipelines, components
ms.assetid: 6b1dbeab-6acc-46d7-8ddd-79b79da3591c
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a9f11f03e818ae1067bc22027822bfeef202260
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-component-to-a-pipeline"></a><span data-ttu-id="10a4e-102">如何新增元件至管線</span><span class="sxs-lookup"><span data-stu-id="10a4e-102">How to Add a Component to a Pipeline</span></span>
<span data-ttu-id="10a4e-103">從工具箱拖曳元件至設計介面以新增元件至管線。</span><span class="sxs-lookup"><span data-stu-id="10a4e-103">You add components to pipelines by dragging from the Toolbox to the design surface.</span></span>  
  
### <a name="to-add-a-component-to-a-pipeline"></a><span data-ttu-id="10a4e-104">新增元件至管線</span><span class="sxs-lookup"><span data-stu-id="10a4e-104">To add a component to a pipeline</span></span>  
  
-   <span data-ttu-id="10a4e-105">在 工具箱 拖曳 管線元件拖曳至**放置到此處 ！**</span><span class="sxs-lookup"><span data-stu-id="10a4e-105">In the Toolbox, drag the pipeline component onto a **Drop Here!**</span></span> <span data-ttu-id="10a4e-106">在設計介面上的方塊。</span><span class="sxs-lookup"><span data-stu-id="10a4e-106">box on the design surface.</span></span>  
  
 <span data-ttu-id="10a4e-107">以下圖例顯示管線設計介面如何說明管線。</span><span class="sxs-lookup"><span data-stu-id="10a4e-107">The following illustration shows how the pipeline design surface illustrates pipelines.</span></span> <span data-ttu-id="10a4e-108">此管線有兩個階段：「組合」階段和「編碼」階段。</span><span class="sxs-lookup"><span data-stu-id="10a4e-108">This pipeline has two stages, the Assemble stage and the Encode stage.</span></span> <span data-ttu-id="10a4e-109">XML 組合器管線元件已加入至 「 組合 」 階段，但 「 編碼 」 階段仍為空白，因為它仍顯示**放置到此處 ！**</span><span class="sxs-lookup"><span data-stu-id="10a4e-109">The XML Assembler pipeline component was added to the Assemble stage, but the Encode stage is still empty, because it still shows **Drop Here!**</span></span> <span data-ttu-id="10a4e-110">表示管線元件，可以新增至階段。</span><span class="sxs-lookup"><span data-stu-id="10a4e-110">to indicate that a pipeline component can be added to the stage.</span></span>  
  
 <span data-ttu-id="10a4e-111">![階段與 BizTalk 管線中的元件](../core/media/ebiz-pipe-stages02.gif "ebiz_pipe_stages02")</span><span class="sxs-lookup"><span data-stu-id="10a4e-111">![Stages and components in a BizTalk pipeline](../core/media/ebiz-pipe-stages02.gif "ebiz_pipe_stages02")</span></span>  
<span data-ttu-id="10a4e-112">說明 BizTalk 管線中的階段和元件。</span><span class="sxs-lookup"><span data-stu-id="10a4e-112">Illustrates stages and components in a BizTalk pipeline.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10a4e-113">管線元件只能放置在設計介面上的特定位置。</span><span class="sxs-lookup"><span data-stu-id="10a4e-113">A pipeline component can only be dropped at specific places on the design surface.</span></span> <span data-ttu-id="10a4e-114">管線元件只能放置在與它有階段相關性的階段中。</span><span class="sxs-lookup"><span data-stu-id="10a4e-114">The pipeline component can only be dropped in a stage in which it has stage affinity.</span></span> <span data-ttu-id="10a4e-115">指標旁邊若出現有線條劃過的圓圈將無法放置管線元件。</span><span class="sxs-lookup"><span data-stu-id="10a4e-115">A circle with a line through it appears next to the pointer where the pipeline component cannot be dropped.</span></span> <span data-ttu-id="10a4e-116">管線元件可以放置在出現箭號且設計介面反白的部分。</span><span class="sxs-lookup"><span data-stu-id="10a4e-116">An arrow appears, and a portion of the design surface is highlighted where a pipeline component can be placed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10a4e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10a4e-117">See Also</span></span>  
 <span data-ttu-id="10a4e-118">[如何建立新的管線](../core/how-to-create-a-new-pipeline.md) </span><span class="sxs-lookup"><span data-stu-id="10a4e-118">[How to Create a New Pipeline](../core/how-to-create-a-new-pipeline.md) </span></span>  
 <span data-ttu-id="10a4e-119">[如何開啟管線](../core/how-to-open-a-pipeline.md) </span><span class="sxs-lookup"><span data-stu-id="10a4e-119">[How to Open a Pipeline](../core/how-to-open-a-pipeline.md) </span></span>  
 <span data-ttu-id="10a4e-120">[如何使用 [工具箱]](../core/how-to-use-the-toolbox.md) </span><span class="sxs-lookup"><span data-stu-id="10a4e-120">[How to Use the Toolbox](../core/how-to-use-the-toolbox.md) </span></span>  
 <span data-ttu-id="10a4e-121">[如何使用鍵盤巡覽](../core/how-to-navigate-with-the-keyboard.md) </span><span class="sxs-lookup"><span data-stu-id="10a4e-121">[How to Navigate with the Keyboard](../core/how-to-navigate-with-the-keyboard.md) </span></span>  
 [<span data-ttu-id="10a4e-122">使用管線設計師建立管線</span><span class="sxs-lookup"><span data-stu-id="10a4e-122">Creating Pipelines with Pipeline Designer</span></span>](../core/creating-pipelines-with-pipeline-designer.md)