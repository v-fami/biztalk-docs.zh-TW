---
title: "關係節點 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- definition files [BAM], relationships
- definition files [BAM], Tracking Profile Editor
- Relationship nodes [Tracking Profile Editor]
- activities [BAM], relationships
- activities [BAM], Tracking Profile Editor
- Tracking Profile Editor, node descriptions
- Tracking Profile Editor, definition files [BAM]
ms.assetid: 74090133-24d1-4aba-a4fc-f12d19c881fb
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f670c62b4e883b124d849ab61396f6f5216e7182
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="relationship-nodes"></a><span data-ttu-id="ba73f-102">關係節點</span><span class="sxs-lookup"><span data-stu-id="ba73f-102">Relationship Nodes</span></span>
<span data-ttu-id="ba73f-103">當活動定義檔案包含一個以上的活動時，就會用到關係資料夾。</span><span class="sxs-lookup"><span data-stu-id="ba73f-103">Relationship folders are used whenever an activity definition file contains more than one activity.</span></span> <span data-ttu-id="ba73f-104">資料夾的名稱會與關聯活動的名稱相符。</span><span class="sxs-lookup"><span data-stu-id="ba73f-104">The names of the folders match the name of the associated activity.</span></span> <span data-ttu-id="ba73f-105">將關係資料夾的名稱與相關活動的活動識別碼配對，並配上資料項目的值，即可形成連結。</span><span class="sxs-lookup"><span data-stu-id="ba73f-105">You form the link by matching the name of the relationship folder to the activity ID of the related activity and by matching the values for the data items.</span></span> <span data-ttu-id="ba73f-106">請使用不同的節點定義每個關係。</span><span class="sxs-lookup"><span data-stu-id="ba73f-106">You define each relationship using a separate node.</span></span>  
  
## <a name="working-with-relationship-nodes"></a><span data-ttu-id="ba73f-107">使用關係節點</span><span class="sxs-lookup"><span data-stu-id="ba73f-107">Working with Relationship nodes</span></span>  
 <span data-ttu-id="ba73f-108">指示可連結活動資料項目的唯一執行個體識別項：</span><span class="sxs-lookup"><span data-stu-id="ba73f-108">To indicate the unique instance identifier that links the data item between activities:</span></span>  
  
-   <span data-ttu-id="ba73f-109">將資料項目對應到主協調流程的 ActivityId 節點。</span><span class="sxs-lookup"><span data-stu-id="ba73f-109">Map a data item to the ActivityId node of the main orchestration.</span></span>  
  
-   <span data-ttu-id="ba73f-110">將具有與上述資料項目相同名稱的資料項目拖放到相關活動的關係節點中。</span><span class="sxs-lookup"><span data-stu-id="ba73f-110">Drag and drop a data item with the same name as above to the Relationship node in the related activity.</span></span> <span data-ttu-id="ba73f-111">此關係節點的名稱與主活動的活動節點名稱相同。</span><span class="sxs-lookup"><span data-stu-id="ba73f-111">The Relationship node has the same name as the Activity node of the main activity.</span></span>  
  
 <span data-ttu-id="ba73f-112">舉例來說，在範例實例中，可能有個用名稱為 RefinanceOrchestration 的協調流程來表示相關但不同的商務程序。</span><span class="sxs-lookup"><span data-stu-id="ba73f-112">For example, in the sample scenario, there could be a related but separate business process represented in an orchestration called RefinanceOrchestration.</span></span> <span data-ttu-id="ba73f-113">該協調流程可能含有 LoanRefinance 活動節點、Refinance ActivityID，以及如「接收評估要求」的協調流程圖形。</span><span class="sxs-lookup"><span data-stu-id="ba73f-113">That orchestration could contain a LoanRefinance Activity node, a Refinance ActivityID, and orchestration shapes such as Receive Appraisal Request.</span></span> <span data-ttu-id="ba73f-114">不過，關係節點和關係識別碼可能是 LoanID，表示與原始 LoanProcess 活動的連結。</span><span class="sxs-lookup"><span data-stu-id="ba73f-114">The Relationship node and relationship ID, however, could be LoanID, indicating the link to the original LoanProcess activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba73f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba73f-115">See Also</span></span>  
 [<span data-ttu-id="ba73f-116">TPE 活動檢視節點</span><span class="sxs-lookup"><span data-stu-id="ba73f-116">TPE Activity View Nodes</span></span>](../core/tpe-activity-view-nodes.md)