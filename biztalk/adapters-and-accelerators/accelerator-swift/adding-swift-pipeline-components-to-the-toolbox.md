---
title: "SWIFT 的管線元件新增至工具箱 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbox, adding pipelines
- pipelines, adding to toolbox
ms.assetid: 3821c10e-ef9b-4657-b934-cff6d096f654
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aaef345994a1d849e09025d9ad1bb0f133c1b224
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="adding-swift-pipeline-components-to-the-toolbox"></a><span data-ttu-id="3f9c2-102">SWIFT 的管線元件新增至工具箱</span><span class="sxs-lookup"><span data-stu-id="3f9c2-102">Adding SWIFT Pipeline Components to the Toolbox</span></span>
<span data-ttu-id="3f9c2-103">您必須加入 SWIFT 的管線元件[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]工具箱中，好讓您可以建立使用這些元件的自訂管線。</span><span class="sxs-lookup"><span data-stu-id="3f9c2-103">You must add the SWIFT pipeline components to the [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] Toolbox, so that you can create custom pipelines using these components.</span></span> <span data-ttu-id="3f9c2-104">如此才能建立 Message Repair 和 New Submission 或 FIN 回應對帳的管線。</span><span class="sxs-lookup"><span data-stu-id="3f9c2-104">This is required to create pipelines for either Message Repair and New Submission or FIN Response Reconciliation.</span></span>  
  
 <span data-ttu-id="3f9c2-105">**摘要**</span><span class="sxs-lookup"><span data-stu-id="3f9c2-105">**Summary**</span></span>  
  
 <span data-ttu-id="3f9c2-106">新增下列 SWIFT 的管線元件才能[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]工具箱：</span><span class="sxs-lookup"><span data-stu-id="3f9c2-106">Add the following SWIFT pipeline components to the [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] Toolbox:</span></span>  
  
-   <span data-ttu-id="3f9c2-107">SWIFT 的組譯工具 （適用於 Message Repair 和 New Submission 或 FIN 回應對帳 (FRR)）</span><span class="sxs-lookup"><span data-stu-id="3f9c2-107">SWIFT Assembler (for Message Repair and New Submission or FIN Response Reconciliation (FRR))</span></span>  
  
-   <span data-ttu-id="3f9c2-108">（針對 Message Repair 和 New Submission 或 FRR） SWIFT 反組譯工具</span><span class="sxs-lookup"><span data-stu-id="3f9c2-108">SWIFT Disassembler (for Message Repair and New Submission or FRR)</span></span>  
  
-   <span data-ttu-id="3f9c2-109">SWIFT Frr 相互關聯集 （適用於 FRR) 解析程式</span><span class="sxs-lookup"><span data-stu-id="3f9c2-109">SWIFT Frr Correlation Set Resolver (for FRR)</span></span>  
  
-   <span data-ttu-id="3f9c2-110">（適用於 FRR) SWIFT Frr MQSeries 解碼器</span><span class="sxs-lookup"><span data-stu-id="3f9c2-110">SWIFT Frr MQSeries Decoder (for FRR)</span></span>  
  
-   <span data-ttu-id="3f9c2-111">（適用於 FRR) SWIFT Frr MQSeries 傳送元件</span><span class="sxs-lookup"><span data-stu-id="3f9c2-111">SWIFT Frr MQSeries Send Component (for FRR)</span></span>  
  
### <a name="to-add-a4swift-pipeline-components-to-the-toolbox"></a><span data-ttu-id="3f9c2-112">將 A4SWIFT 管線元件新增至工具箱</span><span class="sxs-lookup"><span data-stu-id="3f9c2-112">To add A4SWIFT pipeline components to the toolbox</span></span>  
  
1.  <span data-ttu-id="3f9c2-113">在 Visual Studio 中，在**工具**功能表上，按一下 **選擇工具箱項目**。</span><span class="sxs-lookup"><span data-stu-id="3f9c2-113">In Visual Studio, on the **Tools** menu, click **Choose Toolbox Items**.</span></span>  
  
2.  <span data-ttu-id="3f9c2-114">在**選擇工具箱項目**對話方塊**BizTalk 管線元件**索引標籤上，選取**SWIFT 組譯工具**和**SWIFT 解譯器**.</span><span class="sxs-lookup"><span data-stu-id="3f9c2-114">In the **Choose Toolbox Items** dialog box, on the **BizTalk Pipeline Components** tab, select **SWIFT Assembler** and **SWIFT Disassembler**.</span></span> <span data-ttu-id="3f9c2-115">如果您將使用 FIN 回應重新調整，選取**SWIFT Frr 相互關聯集解析程式**， **SWIFT Frr MQSeries 解碼器**，和**SWIFT Frr MQSeries 傳送元件**。</span><span class="sxs-lookup"><span data-stu-id="3f9c2-115">If you will be using FIN Response Reconciliation, select **SWIFT Frr Correlation Set Resolver**, **SWIFT Frr MQSeries Decoder**, and **SWIFT Frr MQSeries Send Component**.</span></span>  
  
3.  <span data-ttu-id="3f9c2-116">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="3f9c2-116">Click **OK**.</span></span>