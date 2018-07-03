---
title: 步驟 7： 啟動協調流程，並重新啟動 BizTalk Server |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa5168b0-4642-4842-a57a-ed7fa35fe161
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7bf1541edcd5341461a2ff948ef82839c623ea51
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006487"
---
# <a name="step-7-start-the-orchestration-and-restart-biztalk-server"></a><span data-ttu-id="21655-102">步驟 7： 啟動協調流程，並重新啟動 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="21655-102">Step 7: Start the Orchestration and Restart BizTalk Server</span></span>
<span data-ttu-id="21655-103">在此步驟中，啟動協調流程，並再重新啟動[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，讓您在本教學課程中所做的變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="21655-103">In this step, you start the orchestration, and then restart [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] so that the changes that you made in this tutorial will take effect.</span></span>  
  
### <a name="to-start-the-orchestration-and-restart-biztalk-server"></a><span data-ttu-id="21655-104">若要啟動協調流程，然後重新啟動 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="21655-104">To start the orchestration and restart BizTalk Server</span></span>  
  
1. <span data-ttu-id="21655-105">在 BizTalk 管理主控台中，按一下**協調流程**，以滑鼠右鍵按一下**BatchOrchestration.Orchestration_1**，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="21655-105">In the BizTalk Administration Console, click **Orchestrations**, right-click **BatchOrchestration.Orchestration_1**, and then click **Start**.</span></span>  
  
2. <span data-ttu-id="21655-106">依序展開**平台設定**，然後按一下**主控件執行個體**。</span><span class="sxs-lookup"><span data-stu-id="21655-106">Expand **Platform Settings**, and then click **Host Instances**.</span></span> <span data-ttu-id="21655-107">以滑鼠右鍵按一下**BizTalkServerApplication**，然後按一下**重新啟動**。</span><span class="sxs-lookup"><span data-stu-id="21655-107">Right-click **BizTalkServerApplication**, and then click **Restart**.</span></span> <span data-ttu-id="21655-108">確認狀態指出**Stopped**，然後**執行**。</span><span class="sxs-lookup"><span data-stu-id="21655-108">Verify that the status indicates **Stopped**, and then **Running**.</span></span>  
  
   <span data-ttu-id="21655-109">請繼續進行[步驟 8： 測試建立批次案例](../../adapters-and-accelerators/accelerator-hl7/step-8-test-the-create-batch-scenario.md)。</span><span class="sxs-lookup"><span data-stu-id="21655-109">Proceed to [Step 8: Test the Create-Batch Scenario](../../adapters-and-accelerators/accelerator-hl7/step-8-test-the-create-batch-scenario.md).</span></span>