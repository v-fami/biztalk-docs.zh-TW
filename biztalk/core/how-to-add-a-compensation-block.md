---
title: "如何新增補償區塊 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- compensations, compensation blocks
- compensation blocks, adding
ms.assetid: 1bdeed92-3144-44ef-ad0d-1c6976f46a36
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2dec4f4dd01c2bbf522dfff44ec8aaf0c2f5e89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-compensation-block"></a><span data-ttu-id="70323-102">如何新增補償區塊</span><span class="sxs-lookup"><span data-stu-id="70323-102">How to Add a Compensation Block</span></span>
<span data-ttu-id="70323-103">如果您不新增自己的補償，執行階段引擎便會執行預設的補償，叫用目前交易內任何巢狀交易的補償。</span><span class="sxs-lookup"><span data-stu-id="70323-103">If you do not add your own compensation, the runtime engine performs a default compensation that invokes the compensations of any nested transactions within the current transaction.</span></span> <span data-ttu-id="70323-104">它首先會叫用最近完成之交易的補償，然後回溯處理直到補償了所有的巢狀交易為止。</span><span class="sxs-lookup"><span data-stu-id="70323-104">It first invokes the compensation of the most recently completed transaction, and works backward until all nested transactions have been compensated.</span></span>  
  
 <span data-ttu-id="70323-105">如此即使當您進行補償 「 迴圈 」 圖形： 補償將會依照反向順序執行。</span><span class="sxs-lookup"><span data-stu-id="70323-105">This holds true even when your compensation takes place inside a Loop shape: the compensations will be run in reverse order.</span></span> <span data-ttu-id="70323-106">首先，會叫用迴圈最後一次反覆的補償，然後叫用前一次反覆的補償，依此類推。</span><span class="sxs-lookup"><span data-stu-id="70323-106">First, the compensation for the last iteration of the loop will be invoked, then the compensation for the previous iteration, and so on.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="70323-107">由於資料會保存到實體記憶體中供補償處理，因此在迴圈內使用補償會影響效能，而這在大量反覆運算的情況下，可能造成問題。</span><span class="sxs-lookup"><span data-stu-id="70323-107">Because data is persisted to physical memory for compensation to work, using compensations inside a loop might affect performance, which might be an issue given a large number of iterations.</span></span>  
  
 <span data-ttu-id="70323-108">如果預設的處理順序不符需求，您可以自行撰寫補償處理常式，依您指定的順序明確呼叫巢狀範圍的補償處理常式。</span><span class="sxs-lookup"><span data-stu-id="70323-108">If the default ordering does not fit your requirements, you can write your own compensation handler to explicitly call the compensation handlers of the nested scopes in the order you specify.</span></span>  
  
### <a name="to-add-a-compensation-block"></a><span data-ttu-id="70323-109">若要新增補償區塊</span><span class="sxs-lookup"><span data-stu-id="70323-109">To add a Compensation Block</span></span>  
  
1.  <span data-ttu-id="70323-110">以滑鼠右鍵按一下**範圍**圖形，您要新增的交易**補償區塊**，然後按一下 **新補償區塊**。</span><span class="sxs-lookup"><span data-stu-id="70323-110">Right-click the **Scope** shape for the transaction to which you want to add a **Compensation Block**, and then click **New Compensation Block**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="70323-111">若要加入**補償區塊**至**範圍**圖形，**交易類型**屬性**範圍**圖形必須設定為**不可部分完成**或**長時間執行的**。</span><span class="sxs-lookup"><span data-stu-id="70323-111">To add a **Compensation Block** to a **Scope** shape, the **Transaction Type** property of the **Scope** shape must be set to **Atomic** or **Long Running**.</span></span>  
  
     <span data-ttu-id="70323-112">A**補償區塊**緊接相關聯的協調流程加入**範圍**圖形。</span><span class="sxs-lookup"><span data-stu-id="70323-112">A **Compensation Block** is added to the orchestration immediately following the associated **Scope** shape.</span></span>  
  
2.  <span data-ttu-id="70323-113">內部**補償區塊**圖形中，新增圖形以建立恢復認可的交易的處理序。</span><span class="sxs-lookup"><span data-stu-id="70323-113">Inside the **Compensation Block** shape, add shapes to create the process for undoing a committed transaction.</span></span>