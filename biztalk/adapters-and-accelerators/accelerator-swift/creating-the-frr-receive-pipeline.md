---
title: 建立 FRR 接收管線 |Microsoft 文件
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
ms.openlocfilehash: ad31a69d579cf2bbe9f646fc87be1bea9f561a10
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22210374"
---
# <a name="creating-the-frr-receive-pipeline"></a><span data-ttu-id="60127-102">建立 FRR 接收管線</span><span class="sxs-lookup"><span data-stu-id="60127-102">Creating the FRR Receive Pipeline</span></span>
<span data-ttu-id="60127-103">若要執行 FIN 回應重新調整，您必須建立包含 SWIFT FRR 解碼器和 SWIFT FRR CorrelationSet 解決器管線元件，除了 SWIFT 解譯器的接收管線。</span><span class="sxs-lookup"><span data-stu-id="60127-103">To perform FIN Response Reconciliation, you must create a receive pipeline that contains the SWIFT FRR Decoder and SWIFT FRR CorrelationSet Resolver pipeline components, in addition to the SWIFT disassembler.</span></span>  
  
 <span data-ttu-id="60127-104">**摘要**</span><span class="sxs-lookup"><span data-stu-id="60127-104">**Summary**</span></span>  
  
 <span data-ttu-id="60127-105">建立接收管線包含下列階段/屬性：</span><span class="sxs-lookup"><span data-stu-id="60127-105">Create a receive pipeline with the following stages/properties:</span></span>  
  
|<span data-ttu-id="60127-106">階段/屬性</span><span class="sxs-lookup"><span data-stu-id="60127-106">Stage/Property</span></span>|<span data-ttu-id="60127-107">元件/設定</span><span class="sxs-lookup"><span data-stu-id="60127-107">Component/Setting</span></span>|  
|---------------------|------------------------|  
|<span data-ttu-id="60127-108">解譯階段</span><span class="sxs-lookup"><span data-stu-id="60127-108">Disassemble stage</span></span>|<span data-ttu-id="60127-109">SWIFT 反組譯工具</span><span class="sxs-lookup"><span data-stu-id="60127-109">SWIFT Disassembler</span></span>|  
|<span data-ttu-id="60127-110">BRE 驗證屬性 （SWIFT 解譯器）</span><span class="sxs-lookup"><span data-stu-id="60127-110">BRE Validation property (SWIFT Disassembler)</span></span>|<span data-ttu-id="60127-111">True</span><span class="sxs-lookup"><span data-stu-id="60127-111">True</span></span>|  
|<span data-ttu-id="60127-112">XML 驗證屬性 （SWIFT 解譯器）</span><span class="sxs-lookup"><span data-stu-id="60127-112">XML Validation property (SWIFT Disassembler)</span></span>|<span data-ttu-id="60127-113">True</span><span class="sxs-lookup"><span data-stu-id="60127-113">True</span></span>|  
|<span data-ttu-id="60127-114">SWIFT 標頭結構描述屬性 （SWIFT 解譯器）</span><span class="sxs-lookup"><span data-stu-id="60127-114">SWIFT Header Schema property (SWIFT Disassembler)</span></span>|<span data-ttu-id="60127-115">(無)</span><span class="sxs-lookup"><span data-stu-id="60127-115">(None)</span></span>|  
|<span data-ttu-id="60127-116">解碼器階段</span><span class="sxs-lookup"><span data-stu-id="60127-116">Decoder stage</span></span>|<span data-ttu-id="60127-117">SWIFT FRR MQSeries 解碼器</span><span class="sxs-lookup"><span data-stu-id="60127-117">SWIFT FRR MQSeries Decoder</span></span>|  
|<span data-ttu-id="60127-118">合作對象解析階段</span><span class="sxs-lookup"><span data-stu-id="60127-118">Party Resolution stage</span></span>|<span data-ttu-id="60127-119">SWIFT FRR 相互關聯集解析程式</span><span class="sxs-lookup"><span data-stu-id="60127-119">SWIFT FRR Correlation Set Resolver</span></span>|  
  
### <a name="to-create-a-custom-receive-pipeline-for-frr"></a><span data-ttu-id="60127-120">若要建立自訂接收管線 FRR</span><span class="sxs-lookup"><span data-stu-id="60127-120">To create a custom receive pipeline for FRR</span></span>  
  
1.  <span data-ttu-id="60127-121">在 方案總管的 Visual Studio 中，以滑鼠右鍵按一下專案包含您[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]管線，指向**新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="60127-121">In Solution Explorer of Visual Studio, right-click the project containing your [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] pipelines, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="60127-122">在 [加入新項目] 對話方塊中，按一下**管線檔案**在分類窗格中，然後選取**接收管線**在範本窗格中。</span><span class="sxs-lookup"><span data-stu-id="60127-122">In the Add New Item dialog box, click **Pipeline Files** in the Categories pane, and then select **Receive Pipeline** in the Templates pane.</span></span>  
  
3.  <span data-ttu-id="60127-123">在**名稱**方塊中，輸入您的接收管線的名稱，例如**FRRReceivePipeline.btp**。</span><span class="sxs-lookup"><span data-stu-id="60127-123">In the **Name** box, type a name for your receive pipeline, such as **FRRReceivePipeline.btp**.</span></span> <span data-ttu-id="60127-124">按一下 **[加入]**。</span><span class="sxs-lookup"><span data-stu-id="60127-124">Click **Add**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="60127-125">在執行步驟 4 之前，您必須新增[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]FRR 中所述，管線元件至工具箱，[加入 SWIFT 管線元件至工具箱](../../adapters-and-accelerators/accelerator-swift/adding-swift-pipeline-components-to-the-toolbox.md)。</span><span class="sxs-lookup"><span data-stu-id="60127-125">Before you perform step 4, you must have added the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] FRR pipeline components to the toolbox, as described in [Adding SWIFT Pipeline Components to the Toolbox](../../adapters-and-accelerators/accelerator-swift/adding-swift-pipeline-components-to-the-toolbox.md).</span></span>  
  
4.  <span data-ttu-id="60127-126">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，按一下 **檢視**，然後按一下 **工具箱**。</span><span class="sxs-lookup"><span data-stu-id="60127-126">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], click **View** and then click **Toolbox**.</span></span>  
  
5.  <span data-ttu-id="60127-127">從 BizTalk 管線元件 工具箱 窗格中，拖曳**SWIFT 解譯器**至**放置到此處**下列方塊**解譯**暫置在管線設計師中的圖形。</span><span class="sxs-lookup"><span data-stu-id="60127-127">From the BizTalk Pipeline Components Toolbox pane, drag the **SWIFT Disassembler** to the **Drop Here** box below the **Disassemble** stage shape in Pipeline Designer.</span></span>  
  
6.  <span data-ttu-id="60127-128">與**SWIFT 解譯器元件**在管線設計師中，選取**屬性**，確認**BRE 驗證**和**XML 驗證**屬性會設為**True**，而**SWIFT 標頭結構描述**屬性設定為 **（無）**。</span><span class="sxs-lookup"><span data-stu-id="60127-128">With the **SWIFT Disassembler Component** selected in Pipeline Designer, in **Properties**, verify that the **BRE Validation** and **XML Validation** properties are set to **True**, and the **SWIFT Header Schema** property is set to **(None)**.</span></span>  
  
7.  <span data-ttu-id="60127-129">在 BizTalk 管線元件工具箱拖曳**SWIFT FRR MQSeries 解碼器**至**放置到此處**下列方塊**解碼器**暫置在管線設計師中的圖形。</span><span class="sxs-lookup"><span data-stu-id="60127-129">In the BizTalk Pipeline Components Toolbox, drag **SWIFT FRR MQSeries Decoder** to the **Drop Here** box below the **Decoder** stage shape in Pipeline Designer.</span></span>  
  
8.  <span data-ttu-id="60127-130">從 BizTalk 管線元件 工具箱 窗格中，拖曳**SWIFT FRR 相互關聯集解析程式**至**放置到此處**下列方塊**解析合作對象**暫置在管線中的圖形設計工具。</span><span class="sxs-lookup"><span data-stu-id="60127-130">From the BizTalk Pipeline Components Toolbox pane, drag **SWIFT FRR Correlation Set Resolver** to the **Drop Here** box below the **ResolveParty** stage shape in Pipeline Designer.</span></span>  
  
9. <span data-ttu-id="60127-131">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，按一下 **檔案**，然後按一下 **全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="60127-131">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], click **File**, and then click **Save All**.</span></span>