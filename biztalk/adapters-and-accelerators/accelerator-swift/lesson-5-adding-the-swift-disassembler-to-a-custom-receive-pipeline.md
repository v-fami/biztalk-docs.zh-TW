---
title: "第 5 課： 加入自訂接收管線 SWIFT 解譯器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive pipelines, adding disassembler
- custom pipelines
- disassembler, custom pipelines
- disassembler, adding to pipelines
ms.assetid: 96e26d97-bfab-448f-b7b6-3bc2ec3ccebf
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04feeaf88cef2f4ab876b22eda1b1e060a1e0173
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-5-adding-the-swift-disassembler-to-a-custom-receive-pipeline"></a><span data-ttu-id="f7671-102">第 5 課： 加入自訂接收管線 SWIFT 反組譯工具</span><span class="sxs-lookup"><span data-stu-id="f7671-102">Lesson 5: Adding the SWIFT Disassembler to a Custom Receive Pipeline</span></span>
<span data-ttu-id="f7671-103">在這一課，您可以加入自訂 SWIFT 的解譯器 (DASM) 到您的管線。</span><span class="sxs-lookup"><span data-stu-id="f7671-103">In this lesson, you add the custom SWIFT disassembler (DASM) to your pipeline.</span></span> <span data-ttu-id="f7671-104">DASM 管線元件是將一批訊息分割成個別文件的管線元件。</span><span class="sxs-lookup"><span data-stu-id="f7671-104">A DASM pipeline component is a pipeline component that divides messages in a batch into individual documents.</span></span>  
  
 <span data-ttu-id="f7671-105">DASM 管線元件中提供[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]是：</span><span class="sxs-lookup"><span data-stu-id="f7671-105">The DASM pipeline components provided in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] are:</span></span>  
  
-   <span data-ttu-id="f7671-106">一般檔案解譯器</span><span class="sxs-lookup"><span data-stu-id="f7671-106">Flat file disassembler</span></span>  
  
-   <span data-ttu-id="f7671-107">BizTalk Framework 解譯器</span><span class="sxs-lookup"><span data-stu-id="f7671-107">BizTalk Framework disassembler</span></span>  
  
-   <span data-ttu-id="f7671-108">XML 解譯器</span><span class="sxs-lookup"><span data-stu-id="f7671-108">XML disassembler</span></span>  
  
 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="f7671-109">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]新增額外的 SWIFT 解譯器。</span><span class="sxs-lookup"><span data-stu-id="f7671-109"> [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] adds an additional SWIFT disassembler.</span></span>  
  
### <a name="to-add-the-swift-custom-disassembler-to-your-pipeline"></a><span data-ttu-id="f7671-110">將 SWIFT 的自訂解譯器新增至您的管線</span><span class="sxs-lookup"><span data-stu-id="f7671-110">To add the SWIFT custom disassembler to your pipeline</span></span>  
  
1.  <span data-ttu-id="f7671-111">從 檢視 功能表中，按一下 **工具箱**。</span><span class="sxs-lookup"><span data-stu-id="f7671-111">From the View menu, click **Toolbox**.</span></span>  
  
2.  <span data-ttu-id="f7671-112">從**BizTalk 管線元件工具箱**，按一下  **SWIFT 解譯器**將它拖曳到**放置到此處**下列方塊**解譯**階段中的圖形**BizTalk 管線設計師**。</span><span class="sxs-lookup"><span data-stu-id="f7671-112">From the **BizTalk Pipeline Components Toolbox**, click **SWIFT Disassembler** and drag it to the **Drop Here** box below the **Disassemble** stage shape in **BizTalk Pipeline Designer**.</span></span> <span data-ttu-id="f7671-113">保留**SWIFT 解譯器**圖形中選取**BizTalk 管線設計師**。</span><span class="sxs-lookup"><span data-stu-id="f7671-113">Leave the **SWIFT Disassembler** shape selected in the **BizTalk Pipeline Designer**.</span></span>  
  
3.  <span data-ttu-id="f7671-114">在**屬性**窗格中，選取**Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema**如**SWIFT 標頭結構描述**屬性。</span><span class="sxs-lookup"><span data-stu-id="f7671-114">In the **Properties** pane, select **Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema** for the **SWIFT Header Schema** property.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f7671-115">請勿混淆**SWIFT 標頭結構描述**和訊息標頭結構描述。</span><span class="sxs-lookup"><span data-stu-id="f7671-115">Do not confuse **SWIFT Header Schema** and Message Header Schema.</span></span> <span data-ttu-id="f7671-116">您必須設定**SWIFT 標頭結構描述**步驟 3 中。</span><span class="sxs-lookup"><span data-stu-id="f7671-116">You must set **SWIFT Header Schema** in step 3.</span></span>  
  
4.  <span data-ttu-id="f7671-117">在**屬性** 窗格中，確定**BRE 驗證**屬性設定為**True**。</span><span class="sxs-lookup"><span data-stu-id="f7671-117">In the **Properties** pane, ensure that the **BRE Validation** property is set to **True**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f7671-118">稍後在本教學課程會遵循說明商務規則引擎 (BRE)。</span><span class="sxs-lookup"><span data-stu-id="f7671-118">An explanation of the Business Rule Engine (BRE) follows later in this tutorial.</span></span>  
  
5.  <span data-ttu-id="f7671-119">在**屬性** 窗格中，確定**XML 驗證**屬性設定為**True**。</span><span class="sxs-lookup"><span data-stu-id="f7671-119">In the **Properties** pane, ensure that the **XML Validation** property is set to **True**.</span></span>  
  
6.  <span data-ttu-id="f7671-120">在**屬性** 窗格中，確定**輸入解除批次處理即將**屬性設定為**False**。</span><span class="sxs-lookup"><span data-stu-id="f7671-120">In the **Properties** pane, ensure that the **Inbound Debatching** property is set to **False**.</span></span>  
  
7.  <span data-ttu-id="f7671-121">在**檔案**功能表上，選取**全部儲存**以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="f7671-121">On the **File** menu, select **Save All** to save your changes.</span></span>  
  
 <span data-ttu-id="f7671-122">若要繼續[第 6 課： 建立自訂傳送管線](../../adapters-and-accelerators/accelerator-swift/lesson-6-creating-a-custom-send-pipeline.md)。</span><span class="sxs-lookup"><span data-stu-id="f7671-122">Proceed to [Lesson 6: Creating a Custom Send Pipeline](../../adapters-and-accelerators/accelerator-swift/lesson-6-creating-a-custom-send-pipeline.md).</span></span>