---
title: "邏輯運算子 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8aaceb64-a5a0-462a-a0eb-8352bed999e5
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e3b3c187e353babafd86590fdeacdc19fc115b6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="logical-operators"></a><span data-ttu-id="47f48-102">邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="47f48-102">Logical Operators</span></span>
<span data-ttu-id="47f48-103">「商務規則架構」可支援使用邏輯 AND、邏輯 OR 和邏輯 NOT 運算子來建立商務規則。</span><span class="sxs-lookup"><span data-stu-id="47f48-103">The Business Rules Framework supports using the logical AND, logical OR, and logical NOT operators in creating business rules.</span></span> <span data-ttu-id="47f48-104">下表描述可用的邏輯運算子。</span><span class="sxs-lookup"><span data-stu-id="47f48-104">The following table describes the logical operators.</span></span>  
  
|<span data-ttu-id="47f48-105">邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="47f48-105">Logical Operator</span></span>|<span data-ttu-id="47f48-106">Description</span><span class="sxs-lookup"><span data-stu-id="47f48-106">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="47f48-107">**AND**</span><span class="sxs-lookup"><span data-stu-id="47f48-107">**AND**</span></span>|<span data-ttu-id="47f48-108">傳回**true**如果這兩個運算元都評估為**true**; 否則會傳回**false**。</span><span class="sxs-lookup"><span data-stu-id="47f48-108">Returns **true** if both the operands evaluate to **true**; otherwise returns **false**.</span></span>|  
|<span data-ttu-id="47f48-109">**OR**</span><span class="sxs-lookup"><span data-stu-id="47f48-109">**OR**</span></span>|<span data-ttu-id="47f48-110">傳回**true**如果其中一個運算元判斷值為**true**，否則會傳回**false**。</span><span class="sxs-lookup"><span data-stu-id="47f48-110">Returns **true** if one of the operands evaluates to **true**, otherwise returns **false**.</span></span>|  
|<span data-ttu-id="47f48-111">**NOT**</span><span class="sxs-lookup"><span data-stu-id="47f48-111">**NOT**</span></span>|<span data-ttu-id="47f48-112">傳回**true**如果運算元等於**false**，否則會傳回**false**。</span><span class="sxs-lookup"><span data-stu-id="47f48-112">Returns **true** if the operand evaluates to **false**, otherwise returns **false**.</span></span>|  
  
 <span data-ttu-id="47f48-113">當運算元的類型不同時，規則引擎在評估運算式之前，會轉換其中一個參數的類型，使其符合另一個參數的類型，或是同時將兩個參數的類型轉換為共同的類型。</span><span class="sxs-lookup"><span data-stu-id="47f48-113">When operands are of different types, the rule engine converts type of one of the parameters to match the type of the other parameter or converts types of both the parameters to a common type before evaluating the expression.</span></span>  
  
## <a name="to-use-a-logical-operator-in-a-business-rule"></a><span data-ttu-id="47f48-114">在商務規則中使用邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="47f48-114">To use a logical operator in a business rule</span></span>  
 <span data-ttu-id="47f48-115">使用下列程序可在商務規則中使用邏輯運算子。</span><span class="sxs-lookup"><span data-stu-id="47f48-115">Use the following procedure to use a logical operator in a business rule.</span></span>  
  
1.  <span data-ttu-id="47f48-116">在**如果**的商務規則編輯器 窗格以滑鼠右鍵按一下**條件**節點，然後再選取您想要加入邏輯運算式的邏輯運算子。</span><span class="sxs-lookup"><span data-stu-id="47f48-116">In the **IF** pane of Business Rule Composer, right-click the **Conditions** node, and then select the logical operator that you wish to add to the logical expression.</span></span>  
  
2.  <span data-ttu-id="47f48-117">以滑鼠右鍵按一下此邏輯運算子，然後加入述詞或是您想要加入的巢狀邏輯運算子。</span><span class="sxs-lookup"><span data-stu-id="47f48-117">Right-click the logical operator, and add the predicates or nested logical operators you want to add.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47f48-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47f48-118">See Also</span></span>  
 [<span data-ttu-id="47f48-119">算術運算子</span><span class="sxs-lookup"><span data-stu-id="47f48-119">Arithmetic Operators</span></span>](../core/arithmetic-operators.md)