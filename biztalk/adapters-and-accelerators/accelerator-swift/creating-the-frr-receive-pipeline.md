---
title: 建立 FRR 接收管線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- receive pipelines, creating
- FRR, creating receive pipelines
- creating, receive pipelines
ms.assetid: 5884176b-8522-4dd3-8f93-8695858b59ac
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bbf4e735019c5399e1b7f1648f3adbcffe18fed2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970799"
---
# <a name="creating-the-frr-receive-pipeline"></a><span data-ttu-id="ada5c-102">建立 FRR 接收管線</span><span class="sxs-lookup"><span data-stu-id="ada5c-102">Creating the FRR Receive Pipeline</span></span>
<span data-ttu-id="ada5c-103">若要執行 FIN 回應對帳，您必須建立包含 SWIFT 的 FRR 解碼器和 SWIFT 的 FRR CorrelationSet 解析管線元件，以及 SWIFT 解譯器的接收管線。</span><span class="sxs-lookup"><span data-stu-id="ada5c-103">To perform FIN Response Reconciliation, you must create a receive pipeline that contains the SWIFT FRR Decoder and SWIFT FRR CorrelationSet Resolver pipeline components, in addition to the SWIFT disassembler.</span></span>  

 <span data-ttu-id="ada5c-104">**摘要**</span><span class="sxs-lookup"><span data-stu-id="ada5c-104">**Summary**</span></span>  

 <span data-ttu-id="ada5c-105">建立接收管線包含下列階段/屬性：</span><span class="sxs-lookup"><span data-stu-id="ada5c-105">Create a receive pipeline with the following stages/properties:</span></span>  

|<span data-ttu-id="ada5c-106">階段/屬性</span><span class="sxs-lookup"><span data-stu-id="ada5c-106">Stage/Property</span></span>|<span data-ttu-id="ada5c-107">元件/設定</span><span class="sxs-lookup"><span data-stu-id="ada5c-107">Component/Setting</span></span>|  
|---------------------|------------------------|  
|<span data-ttu-id="ada5c-108">解譯階段</span><span class="sxs-lookup"><span data-stu-id="ada5c-108">Disassemble stage</span></span>|<span data-ttu-id="ada5c-109">SWIFT 解譯器</span><span class="sxs-lookup"><span data-stu-id="ada5c-109">SWIFT Disassembler</span></span>|  
|<span data-ttu-id="ada5c-110">BRE 驗證屬性 （SWIFT 解譯器）</span><span class="sxs-lookup"><span data-stu-id="ada5c-110">BRE Validation property (SWIFT Disassembler)</span></span>|<span data-ttu-id="ada5c-111">True</span><span class="sxs-lookup"><span data-stu-id="ada5c-111">True</span></span>|  
|<span data-ttu-id="ada5c-112">XML 驗證屬性 （SWIFT 解譯器）</span><span class="sxs-lookup"><span data-stu-id="ada5c-112">XML Validation property (SWIFT Disassembler)</span></span>|<span data-ttu-id="ada5c-113">True</span><span class="sxs-lookup"><span data-stu-id="ada5c-113">True</span></span>|  
|<span data-ttu-id="ada5c-114">SWIFT 標頭結構描述屬性 （SWIFT 解譯器）</span><span class="sxs-lookup"><span data-stu-id="ada5c-114">SWIFT Header Schema property (SWIFT Disassembler)</span></span>|<span data-ttu-id="ada5c-115">(無)</span><span class="sxs-lookup"><span data-stu-id="ada5c-115">(None)</span></span>|  
|<span data-ttu-id="ada5c-116">解碼器階段</span><span class="sxs-lookup"><span data-stu-id="ada5c-116">Decoder stage</span></span>|<span data-ttu-id="ada5c-117">SWIFT 的 FRR MQSeries 解碼器</span><span class="sxs-lookup"><span data-stu-id="ada5c-117">SWIFT FRR MQSeries Decoder</span></span>|  
|<span data-ttu-id="ada5c-118">合作對象解析階段</span><span class="sxs-lookup"><span data-stu-id="ada5c-118">Party Resolution stage</span></span>|<span data-ttu-id="ada5c-119">SWIFT 的 FRR 相互關聯集解析程式</span><span class="sxs-lookup"><span data-stu-id="ada5c-119">SWIFT FRR Correlation Set Resolver</span></span>|  

### <a name="to-create-a-custom-receive-pipeline-for-frr"></a><span data-ttu-id="ada5c-120">建立 FRR 自訂接收管線</span><span class="sxs-lookup"><span data-stu-id="ada5c-120">To create a custom receive pipeline for FRR</span></span>  

1. <span data-ttu-id="ada5c-121">在 Visual Studio 的方案總管中以滑鼠右鍵按一下專案包含您[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]管線，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="ada5c-121">In Solution Explorer of Visual Studio, right-click the project containing your [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] pipelines, point to **Add**, and then click **New Item**.</span></span>  

2. <span data-ttu-id="ada5c-122">在 加入新項目 對話方塊中，按一下**管線檔案**類別 窗格，然後選取**接收管線**範本 窗格中。</span><span class="sxs-lookup"><span data-stu-id="ada5c-122">In the Add New Item dialog box, click **Pipeline Files** in the Categories pane, and then select **Receive Pipeline** in the Templates pane.</span></span>  

3. <span data-ttu-id="ada5c-123">在 **名稱**方塊中，輸入您的接收管線的名稱，例如**FRRReceivePipeline.btp**。</span><span class="sxs-lookup"><span data-stu-id="ada5c-123">In the **Name** box, type a name for your receive pipeline, such as **FRRReceivePipeline.btp**.</span></span> <span data-ttu-id="ada5c-124">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="ada5c-124">Click **Add**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="ada5c-125">在執行步驟 4 之前，您必須新增[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]FRR 的管線元件 [工具箱] 中所述[新增 SWIFT 管線元件至工具箱](../../adapters-and-accelerators/accelerator-swift/adding-swift-pipeline-components-to-the-toolbox.md)。</span><span class="sxs-lookup"><span data-stu-id="ada5c-125">Before you perform step 4, you must have added the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] FRR pipeline components to the toolbox, as described in [Adding SWIFT Pipeline Components to the Toolbox](../../adapters-and-accelerators/accelerator-swift/adding-swift-pipeline-components-to-the-toolbox.md).</span></span>  

4. <span data-ttu-id="ada5c-126">在  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，按一下**檢視**，然後按一下**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="ada5c-126">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], click **View** and then click **Toolbox**.</span></span>  

5. <span data-ttu-id="ada5c-127">從 BizTalk 管線元件 工具箱 窗格中，拖曳**SWIFT 解譯器**要**放置到此處**在下列方塊**解譯**階段管線設計師 」 中的圖形。</span><span class="sxs-lookup"><span data-stu-id="ada5c-127">From the BizTalk Pipeline Components Toolbox pane, drag the **SWIFT Disassembler** to the **Drop Here** box below the **Disassemble** stage shape in Pipeline Designer.</span></span>  

6. <span data-ttu-id="ada5c-128">具有**SWIFT 解譯器元件**在管線設計師中，選取**屬性**，確認**BRE 驗證**並**XML 驗證**屬性會設為 **，則為 True**，而**SWIFT 標頭結構描述**屬性設為 **（無）**。</span><span class="sxs-lookup"><span data-stu-id="ada5c-128">With the **SWIFT Disassembler Component** selected in Pipeline Designer, in **Properties**, verify that the **BRE Validation** and **XML Validation** properties are set to **True**, and the **SWIFT Header Schema** property is set to **(None)**.</span></span>  

7. <span data-ttu-id="ada5c-129">在 BizTalk 管線元件工具箱拖曳**SWIFT 的 FRR MQSeries 解碼器**要**放置到此處**下面的方塊**解碼器**階段管線設計師 」 中的圖形。</span><span class="sxs-lookup"><span data-stu-id="ada5c-129">In the BizTalk Pipeline Components Toolbox, drag **SWIFT FRR MQSeries Decoder** to the **Drop Here** box below the **Decoder** stage shape in Pipeline Designer.</span></span>  

8. <span data-ttu-id="ada5c-130">從 BizTalk 管線元件 工具箱 窗格中，拖曳**FRR 相互關聯集解析程式 SWIFT**來**放置到此處**下面的方塊**解析合作對象**暫置在管線中的圖形設計工具。</span><span class="sxs-lookup"><span data-stu-id="ada5c-130">From the BizTalk Pipeline Components Toolbox pane, drag **SWIFT FRR Correlation Set Resolver** to the **Drop Here** box below the **ResolveParty** stage shape in Pipeline Designer.</span></span>  

9. <span data-ttu-id="ada5c-131">在  [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，按一下**檔案**，然後按一下**全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="ada5c-131">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], click **File**, and then click **Save All**.</span></span>
