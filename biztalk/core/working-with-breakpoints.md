---
title: "處理中斷點 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Orchestration Debugger, breakpoints
- Orchestration Debugger, suspended orchestrations
- Orchestration Debugger, Message Flow view
- Orchestration Debugger, service options
- Message Flow view [Orchestration Debugger]
ms.assetid: aad1a2b0-d705-49cd-85f7-b0ab2e473bcc
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60e9cee77f105b132438e621651ee90c0090c1be
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="working-with-breakpoints"></a><span data-ttu-id="6ee04-102">處理中斷點</span><span class="sxs-lookup"><span data-stu-id="6ee04-102">Working with Breakpoints</span></span>
<span data-ttu-id="6ee04-103">您可以將中斷點附加到擱置的協調流程，或在類別上設定中斷點，以設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="6ee04-103">You can set breakpoints by attaching to a suspended orchestration, or by setting a breakpoint on a class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ee04-104">當您解除部署組件時，資料庫會保留該組件的追蹤選項與中斷點資訊。</span><span class="sxs-lookup"><span data-stu-id="6ee04-104">When you undeploy an assembly, the database maintains the tracking options and breakpoint information for that assembly.</span></span> <span data-ttu-id="6ee04-105">若您之後再次部署相同的組件，就會還原該組件的選項與中斷點資訊。</span><span class="sxs-lookup"><span data-stu-id="6ee04-105">If you subsequently deploy the same assembly again, the options and breakpoint information for that assembly are restored.</span></span>  
  
### <a name="to-attach-to-a-suspended-orchestration"></a><span data-ttu-id="6ee04-106">附加到擱置的協調流程</span><span class="sxs-lookup"><span data-stu-id="6ee04-106">To attach to a suspended orchestration</span></span>  
  
1.  <span data-ttu-id="6ee04-107">使用擱置圖形選取自動擱置的協調流程，然後移至步驟 3。</span><span class="sxs-lookup"><span data-stu-id="6ee04-107">Select an automatically suspended orchestration using a suspend shape, and then go to Step 3.</span></span>  
  
2.  <span data-ttu-id="6ee04-108">重新整理檢視以檢查執行個體現在顯示為「已擱置」狀態。</span><span class="sxs-lookup"><span data-stu-id="6ee04-108">Refresh the view to check that the instance now appears in a Suspended state.</span></span>  
  
3.  <span data-ttu-id="6ee04-109">按一下**在偵錯繼續**。</span><span class="sxs-lookup"><span data-stu-id="6ee04-109">Click **Resume in Debug**.</span></span>  
  
     <span data-ttu-id="6ee04-110">協調流程會於「在中斷點」狀態下繼續。</span><span class="sxs-lookup"><span data-stu-id="6ee04-110">The orchestration resumes in an In Breakpoint state.</span></span> <span data-ttu-id="6ee04-111">您現在可以互動方式進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="6ee04-111">You can now debug interactively.</span></span>  
  
### <a name="to-switch-to-the-message-flow-view"></a><span data-ttu-id="6ee04-112">切換至 [訊息流程] 檢視</span><span class="sxs-lookup"><span data-stu-id="6ee04-112">To switch to the Message Flow view</span></span>  
  
-   <span data-ttu-id="6ee04-113">以滑鼠右鍵按一下 [結果] 清單中的資料格，然後選取**訊息流程**從捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="6ee04-113">Right-click a cell in the Results list and select **Message Flow** from the shortcut menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ee04-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ee04-114">See Also</span></span>  
 [<span data-ttu-id="6ee04-115">使用協調流程偵錯工具檢視</span><span class="sxs-lookup"><span data-stu-id="6ee04-115">Working with the Orchestration Debugger View</span></span>](../core/working-with-the-orchestration-debugger-view.md)