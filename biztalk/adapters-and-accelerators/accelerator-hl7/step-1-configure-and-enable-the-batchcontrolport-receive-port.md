---
title: "步驟 1： 設定和啟用 BatchControlPort 接收連接埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be248a05-e740-497a-b112-8ba3a57b020b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d50289924062268db078844f2b3d2eaaccda23a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-configure-and-enable-the-batchcontrolport-receive-port"></a><span data-ttu-id="e0f6d-102">步驟 1： 設定和啟用 BatchControlPort 接收連接埠</span><span class="sxs-lookup"><span data-stu-id="e0f6d-102">Step 1: Configure and Enable the BatchControlPort Receive Port</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="e0f6d-103">BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 安裝程式會建立接收埠、 批次控制連接埠，來處理訊息批次協調流程用來啟動、 停止，和時間的批次。</span><span class="sxs-lookup"><span data-stu-id="e0f6d-103"> BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) setup creates a receive port, the batch control port, to handle the messages that the batch orchestration uses to start, stop, and time batches.</span></span> <span data-ttu-id="e0f6d-104">這些訊息包含批次啟動、 批次終止和批次計時器訊息。</span><span class="sxs-lookup"><span data-stu-id="e0f6d-104">These messages include the batch activation, batch termination, and batch timer messages.</span></span> <span data-ttu-id="e0f6d-105">在此步驟中，您會設定批次控制連接埠的接收管線，及啟用的通訊埠。</span><span class="sxs-lookup"><span data-stu-id="e0f6d-105">In this step, you configure the receive pipeline for the batch control port, and enable the port.</span></span>  
  
### <a name="to-configure-and-enable-batchcontrolport"></a><span data-ttu-id="e0f6d-106">若要設定並啟用 BatchControlPort</span><span class="sxs-lookup"><span data-stu-id="e0f6d-106">To configure and enable BatchControlPort</span></span>  
  
1.  <span data-ttu-id="e0f6d-107">啟動**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="e0f6d-107">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="e0f6d-108">在 BizTalk Server 管理主控台中，展開**BizTalk Server 管理**， **BizTalk 群組**，**應用程式**，和**BizTalk 應用程式1**。</span><span class="sxs-lookup"><span data-stu-id="e0f6d-108">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, and **BizTalk Application 1**.</span></span> <span data-ttu-id="e0f6d-109">按一下**接收位置**。</span><span class="sxs-lookup"><span data-stu-id="e0f6d-109">Click **Receive Locations**.</span></span>  
  
3.  <span data-ttu-id="e0f6d-110">以滑鼠右鍵按一下**BatchControlLocation**，然後按一下 **停用**。</span><span class="sxs-lookup"><span data-stu-id="e0f6d-110">Right-click **BatchControlLocation**, and then click **Disable**.</span></span>  
  
4.  <span data-ttu-id="e0f6d-111">以滑鼠右鍵按一下**BatchControlLocation**，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="e0f6d-111">Right-click **BatchControlLocation**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="e0f6d-112">在 [接收位置屬性] 對話方塊的**接收管線**，選取**BTAHL72XPipelines.BTAHL72XReceivePipeline**。按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="e0f6d-112">In the Receive Location Properties dialog box, for **Receive Pipeline**, select **BTAHL72XPipelines.BTAHL72XReceivePipeline**.Click **OK**.</span></span>  
  
6.  <span data-ttu-id="e0f6d-113">在 BizTalk 管理主控台中，以滑鼠右鍵按一下**BatchControlLocation**，然後按一下 **啟用**。</span><span class="sxs-lookup"><span data-stu-id="e0f6d-113">In the BizTalk Administration Console, right-click **BatchControlLocation**, and then click **Enable**.</span></span>  
  
 <span data-ttu-id="e0f6d-114">若要繼續[步驟 2： 啟用批次協調流程](../../adapters-and-accelerators/accelerator-hl7/step-2-enable-the-batch-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="e0f6d-114">Proceed to [Step 2: Enable the Batch Orchestration](../../adapters-and-accelerators/accelerator-hl7/step-2-enable-the-batch-orchestration.md).</span></span>