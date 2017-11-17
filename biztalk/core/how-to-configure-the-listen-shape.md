---
title: "如何設定待命圖形 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Listen shape [Orchestration Designer], about Listen shape
- Listen shape [Orchestration Designer], configuring
- Listen shape [Orchestration Designer]
- Listen shape [Orchestration Designer], branching
- configuring [Orchestration Designer], Listen shapes
ms.assetid: 4765dc0a-a30e-4515-83bc-72b4f37268cf
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5bd8f8bbcc08d41430b95a9d177aeb06a5288be4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-listen-shape"></a><span data-ttu-id="cd68e-102">如何設定待命圖形</span><span class="sxs-lookup"><span data-stu-id="cd68e-102">How to Configure the Listen Shape</span></span>
<span data-ttu-id="cd68e-103">待命動作讓應用程式能在一個或多個連接埠等候數個訊息之一，或是在指定的逾時間隔後停止等候，然後根據結果分支。</span><span class="sxs-lookup"><span data-stu-id="cd68e-103">Listen actions enable applications to wait for one of several messages on one or more ports, or to stop waiting after a specified time-out interval, and branch based upon the results.</span></span>  
  
 ![](../core/media/ebiz-orch-listen.gif "ebiz_orch_listen")  
<span data-ttu-id="cd68e-104">待命圖形</span><span class="sxs-lookup"><span data-stu-id="cd68e-104">Listen shape</span></span>  
  
 <span data-ttu-id="cd68e-105">您可以視需要盡量新增分支。</span><span class="sxs-lookup"><span data-stu-id="cd68e-105">You can add as many branches as you like.</span></span> <span data-ttu-id="cd68e-106">您可以將任何其他圖形下方初始放**接收**或**延遲**圖形。</span><span class="sxs-lookup"><span data-stu-id="cd68e-106">You can place any other shape below the initial **Receive** or **Delay** shape.</span></span>  
  
 <span data-ttu-id="cd68e-107">您可使用啟動接收中**接聽**圖形。</span><span class="sxs-lookup"><span data-stu-id="cd68e-107">It is possible to use an activation receive in a **Listen** shape.</span></span> <span data-ttu-id="cd68e-108">如果的其中一個分支**接聽**圖形包含啟動接收，則所有分支都必須都包含啟動接收，且可以使用不會逾時。</span><span class="sxs-lookup"><span data-stu-id="cd68e-108">If one branch of the **Listen** shape contains an activation receive, then all branches must contain activation receives, and no timeout can be used.</span></span> <span data-ttu-id="cd68e-109">啟動接收必須是每個分支中的第一個動作。</span><span class="sxs-lookup"><span data-stu-id="cd68e-109">The activation receive must be the first action in each branch.</span></span>  
  
 <span data-ttu-id="cd68e-110">您可以使用**接聽**圖形至協調流程的分支會根據一或多個事件的發生。</span><span class="sxs-lookup"><span data-stu-id="cd68e-110">You can use the **Listen** shape to branch orchestration flow based on the occurrence of one or more events.</span></span> <span data-ttu-id="cd68e-111">每個分支中的第一個圖形必須是**延遲**或**接收**圖形。</span><span class="sxs-lookup"><span data-stu-id="cd68e-111">The first shape in each branch must be either a **Delay** or a **Receive** shape.</span></span> <span data-ttu-id="cd68e-112">符合其條件的第一個分支 — 的逾時的出現項目**延遲**圖形或接收的訊息**接收**圖形，將會執行。</span><span class="sxs-lookup"><span data-stu-id="cd68e-112">The first branch that meets its condition—the occurrence of a time-out for a **Delay** shape or the receipt of a message for a **Receive** shape—will execute.</span></span> <span data-ttu-id="cd68e-113">您可以視需要新增其他分支。</span><span class="sxs-lookup"><span data-stu-id="cd68e-113">You can add additional branches if needed.</span></span>  
  
### <a name="to-configure-a-listen-shape"></a><span data-ttu-id="cd68e-114">若要設定待命圖形</span><span class="sxs-lookup"><span data-stu-id="cd68e-114">To configure a Listen shape</span></span>  
  
1.  <span data-ttu-id="cd68e-115">選取某個分支。</span><span class="sxs-lookup"><span data-stu-id="cd68e-115">Select a branch.</span></span>  
  
2.  <span data-ttu-id="cd68e-116">在 [屬性] 視窗中，指定**分支類型**屬性。</span><span class="sxs-lookup"><span data-stu-id="cd68e-116">In the Properties window, specify the **Branch Type** property.</span></span>  
  
     <span data-ttu-id="cd68e-117">-或者-</span><span class="sxs-lookup"><span data-stu-id="cd68e-117">—Or—</span></span>  
  
     <span data-ttu-id="cd68e-118">拖曳**延遲**或**接收**圖形拖曳到分支。</span><span class="sxs-lookup"><span data-stu-id="cd68e-118">Drag a **Delay** or **Receive** shape onto the branch.</span></span>  
  
### <a name="to-add-a-branch-to-a-listen-shape"></a><span data-ttu-id="cd68e-119">若要將分支新增到待命圖形</span><span class="sxs-lookup"><span data-stu-id="cd68e-119">To add a branch to a Listen shape</span></span>  
  
-   <span data-ttu-id="cd68e-120">以滑鼠右鍵按一下**接聽**圖形，然後按一下**新待命分支**。</span><span class="sxs-lookup"><span data-stu-id="cd68e-120">Right-click the **Listen** shape and then click **New Listen Branch**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cd68e-121">若要移除的分支**接聽**圖形中，以滑鼠右鍵按一下您想要移除，然後按一下的分支**刪除**。</span><span class="sxs-lookup"><span data-stu-id="cd68e-121">To remove a branch from a **Listen** shape, right-click the branch you want to remove, and then click **Delete**.</span></span>