---
title: "補償 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- compensations, errors
- compensations
- errors, compensations
- compensations, about compensations
- compensations, atomic transactions
- atomic transactions, compensations
- transactions, compensations
ms.assetid: 0a80dd16-fd35-4f45-95b7-52bb9df80cbb
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c572638ea6212c3fb79e6b239aa8ffbe713c3c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="compensation"></a><span data-ttu-id="472ea-102">補償</span><span class="sxs-lookup"><span data-stu-id="472ea-102">Compensation</span></span>
<span data-ttu-id="472ea-103">如果發生錯誤，而您必須復原或回復已成功認可之交易的結果，則可以將補償程式碼加入協調流程中，以達到此目的。</span><span class="sxs-lookup"><span data-stu-id="472ea-103">If an error occurs and you need to undo or reverse the effects of a successfully committed transaction, you can do so by adding compensation code to your orchestration.</span></span>  
  
 <span data-ttu-id="472ea-104">您可以在交易順利完成其動作後叫用補償。</span><span class="sxs-lookup"><span data-stu-id="472ea-104">The compensation can be invoked after the transaction has completed its actions successfully.</span></span> <span data-ttu-id="472ea-105">此時，協調流程的狀態是已知的，補償中的程式碼能夠取得狀態資訊；這表示您可以撰寫程式碼，在交易認可時，根據協調流程的狀態執行適當的動作。</span><span class="sxs-lookup"><span data-stu-id="472ea-105">At that point, the state of the orchestration is known, and state information is available to the code in the compensation, which means that you can write code to act appropriately depending on the state of the orchestration when the transaction commits.</span></span>  
  
 <span data-ttu-id="472ea-106">在不可部分完成的交易上也可以提供補償，</span><span class="sxs-lookup"><span data-stu-id="472ea-106">Compensations can also be provided on atomic transactions.</span></span> <span data-ttu-id="472ea-107">但只有在不可部分完成的交易認可之後，才能呼叫這些補償。</span><span class="sxs-lookup"><span data-stu-id="472ea-107">These compensations can only be called after the atomic transaction commits.</span></span> <span data-ttu-id="472ea-108">您需要撰寫程式碼，在補償中復原或回復正常執行的路徑。</span><span class="sxs-lookup"><span data-stu-id="472ea-108">You need to write code to undo or reverse the path of the normal execution in the compensation.</span></span>  
  
 <span data-ttu-id="472ea-109">補償區塊相當有彈性，可以容納任何其他圖形，甚至包括另一個交易範圍。</span><span class="sxs-lookup"><span data-stu-id="472ea-109">The compensation block is flexible; it can contain any other shape, including another transaction scope.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="472ea-110">您只能在指定範圍中進行補償一次。</span><span class="sxs-lookup"><span data-stu-id="472ea-110">You can do a compensation only once on a given scope.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="472ea-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="472ea-111">In This Section</span></span>  
  
-   [<span data-ttu-id="472ea-112">如何設定補償圖形</span><span class="sxs-lookup"><span data-stu-id="472ea-112">How to Configure the Compensate Shape</span></span>](../core/how-to-configure-the-compensate-shape.md)  
  
-   [<span data-ttu-id="472ea-113">如何新增自訂補償至協調流程</span><span class="sxs-lookup"><span data-stu-id="472ea-113">How to Add Custom Compensation to an Orchestration</span></span>](../core/how-to-add-custom-compensation-to-an-orchestration.md)  
  
-   [<span data-ttu-id="472ea-114">如何新增補償區塊</span><span class="sxs-lookup"><span data-stu-id="472ea-114">How to Add a Compensation Block</span></span>](../core/how-to-add-a-compensation-block.md)