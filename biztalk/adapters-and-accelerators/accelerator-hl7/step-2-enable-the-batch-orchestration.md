---
title: 步驟 2： 啟用批次協調流程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4badf807-f461-4d0a-a3b6-9f671e580d91
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b44dd71c44f2510b6ccd80a731dd21739ed7055
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996167"
---
# <a name="step-2-enable-the-batch-orchestration"></a><span data-ttu-id="50785-102">步驟 2： 啟用批次協調流程</span><span class="sxs-lookup"><span data-stu-id="50785-102">Step 2: Enable the Batch Orchestration</span></span>
<span data-ttu-id="50785-103">批次協調流程會控制建立批次程序。</span><span class="sxs-lookup"><span data-stu-id="50785-103">The batch orchestration controls the create batch process.</span></span> <span data-ttu-id="50785-104">它會維護要包含在批次中的所有訊息的參考、 控制輸出批次交易、 產生批次訊息、 路由傳送外寄批次中，並處理內送通知批次。</span><span class="sxs-lookup"><span data-stu-id="50785-104">It maintains references for all messages to be included in the batch, controls the outbound batch transaction, generates the batch message, routes the outgoing batch, and processes incoming acknowledgment batches.</span></span> <span data-ttu-id="50785-105">您必須登錄建立批次程序運作的批次協調流程。</span><span class="sxs-lookup"><span data-stu-id="50785-105">You need to enlist the batch orchestration for the create batch process to work.</span></span>  
  
### <a name="to-enable-the-batch-orchestration"></a><span data-ttu-id="50785-106">若要啟用批次協調流程</span><span class="sxs-lookup"><span data-stu-id="50785-106">To enable the batch orchestration</span></span>  
  
1. <span data-ttu-id="50785-107">在 BizTalk 管理主控台中，按一下**協調流程**，以滑鼠右鍵按一下**BatchOrchestration.Orchestration_1**，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="50785-107">In the BizTalk Administration Console, click **Orchestrations**, right-click **BatchOrchestration.Orchestration_1**, and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="50785-108">在 [協調流程屬性] 對話方塊的主控台樹狀目錄中，按一下**繫結**。</span><span class="sxs-lookup"><span data-stu-id="50785-108">In the Orchestration Properties dialog box, in the console tree, click **Bindings**.</span></span>  
  
3. <span data-ttu-id="50785-109">在**繫結**窗格中，如**主機**，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="50785-109">In the **Bindings** pane, for **Host**, select **BizTalkServerApplication**.</span></span> <span data-ttu-id="50785-110">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="50785-110">Click **OK**.</span></span>  
  
4. <span data-ttu-id="50785-111">在 BizTalk 管理主控台中，以滑鼠右鍵按一下**BatchOrchestration.Orchestration_1**，然後按一下**登錄**。</span><span class="sxs-lookup"><span data-stu-id="50785-111">In the BizTalk Administration Console, right-click **BatchOrchestration.Orchestration_1**, and then click **Enlist**.</span></span>  
  
   <span data-ttu-id="50785-112">請繼續進行[步驟 3： 建立和設定目的合作對象](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-configure-a-destination-party.md)。</span><span class="sxs-lookup"><span data-stu-id="50785-112">Proceed to [Step 3: Create and Configure a Destination Party](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-configure-a-destination-party.md).</span></span>