---
title: 如何設定 「 終止 」 圖形 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Terminate shape [Orchestration Designer], about Terminate shape
- Terminate shape [Orchestration Designer], literal strings
- configuring [Orchestration Designer], Terminate shapes
- Terminate shape [Orchestration Designer], configuring
- Terminate shape [Orchestration Designer]
ms.assetid: 2c4f2c94-2bab-4af3-8954-7275696ca147
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a5eb4867970c6acafc8903eb474b67541d22764
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247926"
---
# <a name="how-to-configure-the-terminate-shape"></a><span data-ttu-id="8245a-102">如何設定終止圖形</span><span class="sxs-lookup"><span data-stu-id="8245a-102">How to Configure the Terminate Shape</span></span>
![](../core/media/ebiz-orch-terminate.gif "ebiz_orch_terminate")  
<span data-ttu-id="8245a-103">終止圖形</span><span class="sxs-lookup"><span data-stu-id="8245a-103">Terminate shape</span></span>  
  
 <span data-ttu-id="8245a-104">終止圖形的用途為結束協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="8245a-104">The Terminate shape is used to end an orchestration instance.</span></span> <span data-ttu-id="8245a-105">您可以指定會隨著圖形檢視中 [群組中樞] 頁面的輸出時出現的訊息字串。</span><span class="sxs-lookup"><span data-stu-id="8245a-105">You can specify a message string to accompany the shape when viewed in the output from the Group Hub page.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="8245a-106">如果您將放入**Terminate**圖形放**平行動作**圖形，並包含分支**終止**執行時，在執行個體完成立即不論其他分支是否完成執行。</span><span class="sxs-lookup"><span data-stu-id="8245a-106">If you place a **Terminate** shape inside a **Parallel Actions** shape, and the branch with the **Terminate** on it is run, the instance completes immediately, regardless of whether other branches have finished running.</span></span> <span data-ttu-id="8245a-107">取決於您的設計，在此情況下的結果可能會無法預料。</span><span class="sxs-lookup"><span data-stu-id="8245a-107">Depending on your design, results might be unpredictable in this case.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="8245a-108">如果**Terminate**圖形在協調流程同步呼叫發生 (如同**呼叫**圖形) 的另一個協調流程、 巢狀的執行個體和所有封閉式協調流程執行個體將會終止。</span><span class="sxs-lookup"><span data-stu-id="8245a-108">If a **Terminate** shape is encountered in an orchestration that has been called synchronously (as with the **Call** shape) by another orchestration, the nested instance and all enclosing orchestration instances will be terminated.</span></span>  
  
### <a name="to-configure-a-terminate-shape"></a><span data-ttu-id="8245a-109">設定終止圖形</span><span class="sxs-lookup"><span data-stu-id="8245a-109">To configure a Terminate shape</span></span>  
  
-   <span data-ttu-id="8245a-110">您可以使用**錯誤訊息**屬性來指定您想要與圖形檢視中的 [群組中樞] 頁面上的查詢輸出時產生關聯的文字。</span><span class="sxs-lookup"><span data-stu-id="8245a-110">You can use the **Error Message** property to specify text that you want to associate with the shape when viewed in the query output on the Group Hub page.</span></span> <span data-ttu-id="8245a-111">此文字可能是常值字串或運算式評估為**System.String**。</span><span class="sxs-lookup"><span data-stu-id="8245a-111">This text may be a literal string, or an expression that evaluates to a **System.String**.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="8245a-112">如果您輸入常值字串，就必須將其括在引號中。</span><span class="sxs-lookup"><span data-stu-id="8245a-112">If you enter a literal string, you must enclose it in quotation marks.</span></span>