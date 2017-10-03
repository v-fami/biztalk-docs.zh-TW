---
title: "資料項目節點 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- definition files [BAM], data items
- Data Item nodes [Tracking Profile Editor]
- Tracking Profile Editor, node descriptions
- Tracking Profile Editor, definition files [BAM]
ms.assetid: 95856bfa-90e3-49d9-b55b-5f1b35a23f78
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a968bf7533697922938eeb8953f17813c77147c2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="data-item-nodes"></a><span data-ttu-id="f50d8-102">資料項目節點</span><span class="sxs-lookup"><span data-stu-id="f50d8-102">Data Item Nodes</span></span>
<span data-ttu-id="f50d8-103">資料項目節點存在於開發人員從商務分析師所建立觀察模型匯入的活動定義檔案中。</span><span class="sxs-lookup"><span data-stu-id="f50d8-103">Data Item nodes exist in the activity definition file that the developer imports from the created observation model created by the business analyst.</span></span> <span data-ttu-id="f50d8-104">追蹤設定檔編輯器 (TPE) 將這些節點命名為節點所追蹤的資料項目，例如 Customer Name。</span><span class="sxs-lookup"><span data-stu-id="f50d8-104">The Tracking Profile Editor (TPE) names them for the data items they are tracking, such as Customer Name.</span></span> <span data-ttu-id="f50d8-105">接著，您將「訊息結構描述檢視」(Message Schema View) 中的一或多個資料項目放到對應於 Customer Name 的節點。</span><span class="sxs-lookup"><span data-stu-id="f50d8-105">You then drop one or more data items from the Message Schema View onto the node that corresponds to Customer Name.</span></span>  
  
## <a name="working-with-data-item-nodes"></a><span data-ttu-id="f50d8-106">使用資料項目節點</span><span class="sxs-lookup"><span data-stu-id="f50d8-106">Working with data item nodes</span></span>  
 <span data-ttu-id="f50d8-107">對應資料項目節點時，若商務程序跨越多個追蹤設定檔，則每個商務程序只應該追蹤一次資料項目。</span><span class="sxs-lookup"><span data-stu-id="f50d8-107">When mapping Data Item nodes you should only track data items once per business process when that business process spans multiple tracking profiles.</span></span> <span data-ttu-id="f50d8-108">如果協調流程中含有條件路徑，您可以同時選取兩個路徑中的資料，因為將只有一個會執行。</span><span class="sxs-lookup"><span data-stu-id="f50d8-108">If you have a conditional path in your orchestration, you can select the data item from both paths because only one will run.</span></span> <span data-ttu-id="f50d8-109">不過，您不可以選擇迴圈內的圖形，除非資料項目的值會隨著每一次反覆運算而有所不同。</span><span class="sxs-lookup"><span data-stu-id="f50d8-109">However, you should not choose a shape inside a loop unless the values will be different for the data item with each iteration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f50d8-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f50d8-110">See Also</span></span>  
 <span data-ttu-id="f50d8-111">[如何對應項目資料](../core/how-to-map-item-data.md) </span><span class="sxs-lookup"><span data-stu-id="f50d8-111">[How to Map Item Data](../core/how-to-map-item-data.md) </span></span>  
 [<span data-ttu-id="f50d8-112">TPE 活動檢視節點</span><span class="sxs-lookup"><span data-stu-id="f50d8-112">TPE Activity View Nodes</span></span>](../core/tpe-activity-view-nodes.md)