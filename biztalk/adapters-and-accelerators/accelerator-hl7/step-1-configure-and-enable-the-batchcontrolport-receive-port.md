---
title: 步驟 1： 設定和啟用 BatchControlPort 接收連接埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: be248a05-e740-497a-b112-8ba3a57b020b
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1fb11e0638a66fa7d22332d1cbca103a14490528
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988247"
---
# <a name="step-1-configure-and-enable-the-batchcontrolport-receive-port"></a><span data-ttu-id="5da11-102">步驟 1： 設定和啟用 BatchControlPort 接收埠</span><span class="sxs-lookup"><span data-stu-id="5da11-102">Step 1: Configure and Enable the BatchControlPort Receive Port</span></span>
<span data-ttu-id="5da11-103">Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 安裝程式會建立接收埠，批次控制項即通訊埠，處理的訊息批次協調流程用來啟動、 停止，和時間的批次。</span><span class="sxs-lookup"><span data-stu-id="5da11-103">Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) setup creates a receive port, the batch control port, to handle the messages that the batch orchestration uses to start, stop, and time batches.</span></span> <span data-ttu-id="5da11-104">這些訊息包含批次啟動批次終止，批次計時器訊息。</span><span class="sxs-lookup"><span data-stu-id="5da11-104">These messages include the batch activation, batch termination, and batch timer messages.</span></span> <span data-ttu-id="5da11-105">在此步驟中，您可以設定批次的控制連接埠，接收管線，並啟用連接埠。</span><span class="sxs-lookup"><span data-stu-id="5da11-105">In this step, you configure the receive pipeline for the batch control port, and enable the port.</span></span>  
  
### <a name="to-configure-and-enable-batchcontrolport"></a><span data-ttu-id="5da11-106">若要設定及啟用 BatchControlPort</span><span class="sxs-lookup"><span data-stu-id="5da11-106">To configure and enable BatchControlPort</span></span>  
  
1. <span data-ttu-id="5da11-107">開始**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="5da11-107">Start **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="5da11-108">在 [BizTalk Server 管理主控台中，展開**BizTalk Server 管理]**， **BizTalk 群組**，**應用程式**，和**BizTalk 應用程式1**。</span><span class="sxs-lookup"><span data-stu-id="5da11-108">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, and **BizTalk Application 1**.</span></span> <span data-ttu-id="5da11-109">按一下 **接收位置**。</span><span class="sxs-lookup"><span data-stu-id="5da11-109">Click **Receive Locations**.</span></span>  
  
3. <span data-ttu-id="5da11-110">以滑鼠右鍵按一下**BatchControlLocation**，然後按一下**停用**。</span><span class="sxs-lookup"><span data-stu-id="5da11-110">Right-click **BatchControlLocation**, and then click **Disable**.</span></span>  
  
4. <span data-ttu-id="5da11-111">以滑鼠右鍵按一下**BatchControlLocation**，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="5da11-111">Right-click **BatchControlLocation**, and then click **Properties**.</span></span>  
  
5. <span data-ttu-id="5da11-112">在 接收位置屬性 對話方塊中，如**接收管線**，選取**BTAHL72XPipelines.BTAHL72XReceivePipeline**。按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="5da11-112">In the Receive Location Properties dialog box, for **Receive Pipeline**, select **BTAHL72XPipelines.BTAHL72XReceivePipeline**.Click **OK**.</span></span>  
  
6. <span data-ttu-id="5da11-113">在 BizTalk 管理主控台中，以滑鼠右鍵按一下**BatchControlLocation**，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="5da11-113">In the BizTalk Administration Console, right-click **BatchControlLocation**, and then click **Enable**.</span></span>  
  
   <span data-ttu-id="5da11-114">請繼續進行[步驟 2： 啟用批次協調流程](../../adapters-and-accelerators/accelerator-hl7/step-2-enable-the-batch-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="5da11-114">Proceed to [Step 2: Enable the Batch Orchestration](../../adapters-and-accelerators/accelerator-hl7/step-2-enable-the-batch-orchestration.md).</span></span>