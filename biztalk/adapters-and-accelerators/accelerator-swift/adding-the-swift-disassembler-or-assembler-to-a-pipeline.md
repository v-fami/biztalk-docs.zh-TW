---
title: 將 SWIFT 解譯器或組合器新增至管線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipelines, adding assembler
- assembler, adding to pipelines
- pipelines, adding disassembler
- disassembler, adding to pipelines
ms.assetid: f39eb340-fe58-4c8f-b3f2-f7686a245095
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f48317c21942e0912f88d3e48523e07728c16ad3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967999"
---
# <a name="adding-the-swift-disassembler-or-assembler-to-a-pipeline"></a><span data-ttu-id="51f3e-102">將 SWIFT 解譯器或組合器新增至管線</span><span class="sxs-lookup"><span data-stu-id="51f3e-102">Adding the SWIFT Disassembler or Assembler to a Pipeline</span></span>
<span data-ttu-id="51f3e-103">您可以搭配 Microsoft BizTalk 管線設計師[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]以建立自訂的 BizTalk 接收和傳送管線。</span><span class="sxs-lookup"><span data-stu-id="51f3e-103">You can use BizTalk Pipeline Designer with Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] to create custom BizTalk receive and send pipelines.</span></span> <span data-ttu-id="51f3e-104">您可以使用 SWIFT 解譯器的自訂接收管線中的 「 解譯 」 階段。</span><span class="sxs-lookup"><span data-stu-id="51f3e-104">You can use the SWIFT disassembler for the "disassemble" stage in a custom receive pipeline.</span></span> <span data-ttu-id="51f3e-105">同樣地，您可以使用 SWIFT 組合器自訂傳送管線中的 「 組合 」 階段。</span><span class="sxs-lookup"><span data-stu-id="51f3e-105">Similarly, you can use the SWIFT assembler for the "assemble" stage in a custom send pipeline.</span></span> <span data-ttu-id="51f3e-106">要叫用的 SWIFT 解譯器或組合器 [管線設計師工具箱] 中，您將解譯器或組合器拖曳至對應的管線階段管線設計工具畫布上。</span><span class="sxs-lookup"><span data-stu-id="51f3e-106">To invoke the SWIFT disassembler or assembler from the Pipeline Designer toolbox, you drag the disassembler or assembler onto the corresponding pipeline stage on the Pipeline Designer canvas.</span></span> <span data-ttu-id="51f3e-107">如需叫用的解譯器或組合器的逐步指示，請參閱[模組 3： 新增管線專案](../../adapters-and-accelerators/accelerator-swift/module-3-adding-a-pipeline-project.md)在端對端教學課程。</span><span class="sxs-lookup"><span data-stu-id="51f3e-107">For step-by-step instructions about invoking the disassembler or assembler, see [Module 3: Adding a Pipeline Project](../../adapters-and-accelerators/accelerator-swift/module-3-adding-a-pipeline-project.md) in the End-to-End Tutorial.</span></span> <span data-ttu-id="51f3e-108">「 管線設計師 」 的詳細資訊或使用管線專案，請參閱 BizTalk Server 說明。</span><span class="sxs-lookup"><span data-stu-id="51f3e-108">For more information about the Pipeline Designer or working with pipeline projects, see BizTalk Server Help.</span></span>  
  
 <span data-ttu-id="51f3e-109">根據設計，SWIFT 解譯器會預期要的 「 解譯 」 階段*最終*叫用的接收管線階段。</span><span class="sxs-lookup"><span data-stu-id="51f3e-109">By design, the SWIFT disassembler expects the "disassemble" stage to be the *final* stage of the receive pipeline that is invoked.</span></span> <span data-ttu-id="51f3e-110">使用任何後續的階段時，將會導致非預期的行為 （不叫用後續的階段，這類反組譯工具或移除它先前已填入並發佈到 MessageBox 的訊息之前升級內容屬性的解譯器資料庫）。</span><span class="sxs-lookup"><span data-stu-id="51f3e-110">Using any subsequent stages will result in unexpected behavior (such the disassembler not invoking subsequent stages, or the disassembler removing context properties that it had previously populated and promoted before publishing the message to the MessageBox database).</span></span> <span data-ttu-id="51f3e-111">同樣地，SWIFT 組合器預期為 「 組合 」 階段*第一個*傳送管線階段。</span><span class="sxs-lookup"><span data-stu-id="51f3e-111">Similarly, the SWIFT assembler expects the "assemble" stage to be the *first* stage of the send pipeline.</span></span> <span data-ttu-id="51f3e-112">使用任何上述的階段，可能會降低 SWIFT 組合器的動態訊息類型探索。</span><span class="sxs-lookup"><span data-stu-id="51f3e-112">Using any preceding stages may impair dynamic message type discovery by the SWIFT assembler.</span></span>  
  
 <span data-ttu-id="51f3e-113">您可以使用它們的管線設計師工具箱第一個時間，您必須手動將 SWIFT 解譯器和組合器。</span><span class="sxs-lookup"><span data-stu-id="51f3e-113">You must manually add the SWIFT disassembler and assembler to the Pipeline Designer toolbox the first time you use them.</span></span> <span data-ttu-id="51f3e-114">執行此動作的逐步指示的詳細[模組 3： 新增管線專案](../../adapters-and-accelerators/accelerator-swift/module-3-adding-a-pipeline-project.md)在端對端教學課程。</span><span class="sxs-lookup"><span data-stu-id="51f3e-114">Step-by-step instructions for doing this are detailed in [Module 3: Adding a Pipeline Project](../../adapters-and-accelerators/accelerator-swift/module-3-adding-a-pipeline-project.md) in the End-to-End Tutorial.</span></span> <span data-ttu-id="51f3e-115">元件將會繼續出現在工具箱中，一旦您以手動方式加入 (直到您手動加以移除，或直到您解除安裝[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="51f3e-115">The components will continue to appear in the toolbox once you manually add them (until you manually remove them or until you uninstall [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51f3e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51f3e-116">See Also</span></span>  
 [<span data-ttu-id="51f3e-117">使用 SWIFT 解譯器和組合器</span><span class="sxs-lookup"><span data-stu-id="51f3e-117">Working with the SWIFT Disassembler and Assembler</span></span>](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)