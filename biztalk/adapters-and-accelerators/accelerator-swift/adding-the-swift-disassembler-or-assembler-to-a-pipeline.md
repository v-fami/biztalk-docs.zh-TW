---
title: "加入 SWIFT 解譯器 」 或 「 組合器管線 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines, adding assembler
- assembler, adding to pipelines
- pipelines, adding disassembler
- disassembler, adding to pipelines
ms.assetid: f39eb340-fe58-4c8f-b3f2-f7686a245095
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a6a8e45d8f11e6dad977e42c6e9272e9b594e83
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="adding-the-swift-disassembler-or-assembler-to-a-pipeline"></a><span data-ttu-id="8f6d0-102">管線中新增 SWIFT 解譯器或組譯工具</span><span class="sxs-lookup"><span data-stu-id="8f6d0-102">Adding the SWIFT Disassembler or Assembler to a Pipeline</span></span>
<span data-ttu-id="8f6d0-103">您可以使用與 BizTalk 管線設計師[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]以建立自訂的 BizTalk 接收和傳送管線。</span><span class="sxs-lookup"><span data-stu-id="8f6d0-103">You can use BizTalk Pipeline Designer with [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] to create custom BizTalk receive and send pipelines.</span></span> <span data-ttu-id="8f6d0-104">您可以使用 SWIFT 解譯器的自訂接收管線的 「 解譯 」 階段。</span><span class="sxs-lookup"><span data-stu-id="8f6d0-104">You can use the SWIFT disassembler for the "disassemble" stage in a custom receive pipeline.</span></span> <span data-ttu-id="8f6d0-105">同樣地，您可以使用 SWIFT 組譯工具中自訂傳送管線的 「 組合 」 階段。</span><span class="sxs-lookup"><span data-stu-id="8f6d0-105">Similarly, you can use the SWIFT assembler for the "assemble" stage in a custom send pipeline.</span></span> <span data-ttu-id="8f6d0-106">要叫用的 SWIFT 解譯器 」 或 「 組合器 [管線設計師工具箱] 中，您將解譯器 」 或組譯工具拖曳至對應的管線階段管線設計工具畫布上。</span><span class="sxs-lookup"><span data-stu-id="8f6d0-106">To invoke the SWIFT disassembler or assembler from the Pipeline Designer toolbox, you drag the disassembler or assembler onto the corresponding pipeline stage on the Pipeline Designer canvas.</span></span> <span data-ttu-id="8f6d0-107">如需叫用的解譯器 」 或 「 組合器的逐步指示，請參閱[模組 3： 新增管線專案](../../adapters-and-accelerators/accelerator-swift/module-3-adding-a-pipeline-project.md)在端對端教學課程。</span><span class="sxs-lookup"><span data-stu-id="8f6d0-107">For step-by-step instructions about invoking the disassembler or assembler, see [Module 3: Adding a Pipeline Project](../../adapters-and-accelerators/accelerator-swift/module-3-adding-a-pipeline-project.md) in the End-to-End Tutorial.</span></span> <span data-ttu-id="8f6d0-108">「 管線設計師 」 的詳細資訊，或使用管線專案，請參閱[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="8f6d0-108">For more information about the Pipeline Designer or working with pipeline projects, see [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
 <span data-ttu-id="8f6d0-109">根據設計，SWIFT 解譯器必須要有 「 解譯 」 階段的*最終*叫用的接收管線的階段。</span><span class="sxs-lookup"><span data-stu-id="8f6d0-109">By design, the SWIFT disassembler expects the "disassemble" stage to be the *final* stage of the receive pipeline that is invoked.</span></span> <span data-ttu-id="8f6d0-110">使用任何後續的階段時，將會導致非預期的行為 （不叫用後續的階段，這類反組譯工具或移除內容屬性具有先前填入且升級之前將訊息發佈至 MessageBox 的反組譯工具資料庫）。</span><span class="sxs-lookup"><span data-stu-id="8f6d0-110">Using any subsequent stages will result in unexpected behavior (such the disassembler not invoking subsequent stages, or the disassembler removing context properties that it had previously populated and promoted before publishing the message to the MessageBox database).</span></span> <span data-ttu-id="8f6d0-111">同樣地，SWIFT 組合器必須要有 「 組合 」 階段的*第一個*傳送管線階段。</span><span class="sxs-lookup"><span data-stu-id="8f6d0-111">Similarly, the SWIFT assembler expects the "assemble" stage to be the *first* stage of the send pipeline.</span></span> <span data-ttu-id="8f6d0-112">使用任何上述的階段，可能會影響到 SWIFT 組合器的訊息動態類型探索。</span><span class="sxs-lookup"><span data-stu-id="8f6d0-112">Using any preceding stages may impair dynamic message type discovery by the SWIFT assembler.</span></span>  
  
 <span data-ttu-id="8f6d0-113">您必須手動加入 SWIFT 解譯器和組合器使用它們的管線設計師工具箱第一個時間。</span><span class="sxs-lookup"><span data-stu-id="8f6d0-113">You must manually add the SWIFT disassembler and assembler to the Pipeline Designer toolbox the first time you use them.</span></span> <span data-ttu-id="8f6d0-114">執行此作業的逐步指示的詳細[模組 3： 新增管線專案](../../adapters-and-accelerators/accelerator-swift/module-3-adding-a-pipeline-project.md)在端對端教學課程。</span><span class="sxs-lookup"><span data-stu-id="8f6d0-114">Step-by-step instructions for doing this are detailed in [Module 3: Adding a Pipeline Project](../../adapters-and-accelerators/accelerator-swift/module-3-adding-a-pipeline-project.md) in the End-to-End Tutorial.</span></span> <span data-ttu-id="8f6d0-115">元件將會繼續出現在工具箱中，一旦您手動加入這些 (直到您手動移除或解除安裝[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="8f6d0-115">The components will continue to appear in the toolbox once you manually add them (until you manually remove them or until you uninstall [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f6d0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f6d0-116">See Also</span></span>  
 [<span data-ttu-id="8f6d0-117">SWIFT 解譯器和組合器</span><span class="sxs-lookup"><span data-stu-id="8f6d0-117">Working with the SWIFT Disassembler and Assembler</span></span>](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)