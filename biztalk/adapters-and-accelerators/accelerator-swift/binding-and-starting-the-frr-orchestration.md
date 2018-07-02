---
title: 繫結和啟動 FRR 協調流程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FRR, binding orchestrations
- FRR, starting orchestrations
- bindings, orchestrations
- orchestrations, bindings
ms.assetid: b74a0116-e98b-4fec-b386-710ce421a1e2
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b01386cedbd25148e5ea0ce2ac44fb56e9fe3d03
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987439"
---
# <a name="binding-and-starting-the-frr-orchestration"></a><span data-ttu-id="84737-102">繫結和啟動 FRR 協調流程</span><span class="sxs-lookup"><span data-stu-id="84737-102">Binding and Starting the FRR Orchestration</span></span>
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="84737-103"> 包含 FRR 協調流程做為已部署的組件 (Microsoft。Solutions.FinancialServices.SWIFT.FrrOrchestration)。</span><span class="sxs-lookup"><span data-stu-id="84737-103"> includes the FRR orchestration as a deployed assembly (Microsoft .Solutions.FinancialServices.SWIFT.FrrOrchestration).</span></span> <span data-ttu-id="84737-104">您要啟動此協調流程。</span><span class="sxs-lookup"><span data-stu-id="84737-104">You need to start this orchestration.</span></span>  
  
 <span data-ttu-id="84737-105">**摘要**</span><span class="sxs-lookup"><span data-stu-id="84737-105">**Summary**</span></span>  
  
 <span data-ttu-id="84737-106">若要啟動 FRR 協調流程，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="84737-106">To start the FRR orchestration, do the following:</span></span>  
  
-   <span data-ttu-id="84737-107">藉由設定主應用程式 [biztalkserverapplication]，繫結 FrrOrchestration.FrrMain 協調流程。</span><span class="sxs-lookup"><span data-stu-id="84737-107">Bind the FrrOrchestration.FrrMain orchestration by setting the host to BizTalkServerApplication.</span></span>  
  
-   <span data-ttu-id="84737-108">啟動 FrrOrchestration.FrrMain 協調流程。</span><span class="sxs-lookup"><span data-stu-id="84737-108">Start the FrrOrchestration.FrrMain orchestration.</span></span>  
  
### <a name="to-bind-and-start-the-frr-orchestration"></a><span data-ttu-id="84737-109">若要繫結和啟動 FRR 協調流程</span><span class="sxs-lookup"><span data-stu-id="84737-109">To bind and start the FRR orchestration</span></span>  
  
1.  <span data-ttu-id="84737-110">在 [BizTalk Server 管理主控台中，展開**BizTalk Server 管理]**， **BizTalk 群組**，**應用程式**，然後**BizTalk應用程式 1**。</span><span class="sxs-lookup"><span data-stu-id="84737-110">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, and then **BizTalk Application 1**.</span></span> <span data-ttu-id="84737-111">按一下 **協調流程**。</span><span class="sxs-lookup"><span data-stu-id="84737-111">Click **Orchestrations**.</span></span>  
  
2.  <span data-ttu-id="84737-112">在 [協調流程] 窗格中，以滑鼠右鍵按一下**FrrOrchestration.FrrMain**協調流程，然後再按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="84737-112">In the Orchestrations pane, right-click the **FrrOrchestration.FrrMain** orchestration, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="84737-113">在 [協調流程屬性] 對話方塊中，按一下**繫結**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="84737-113">In the Orchestration Properties dialog box, click **Bindings** in the left pane.</span></span> <span data-ttu-id="84737-114">針對**主機**，選取**BizTalkServerApplication**。</span><span class="sxs-lookup"><span data-stu-id="84737-114">For **Host**, select **BizTalkServerApplication**.</span></span> <span data-ttu-id="84737-115">按一下 **套用**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="84737-115">Click **Apply**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="84737-116">在 [協調流程] 窗格中，以滑鼠右鍵按一下**FrrMain**協調流程，然後再按一下**開始**。</span><span class="sxs-lookup"><span data-stu-id="84737-116">In the Orchestrations pane, right-click the **FrrMain** orchestration, and then click **Start**.</span></span>