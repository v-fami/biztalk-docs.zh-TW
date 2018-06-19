---
title: 和 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80bd8f1f-edae-476d-b488-78e6c5ee70bf
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 676940dfa5cbc23d0c8127923d292e382a4e3cad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230014"
---
# <a name="and"></a><span data-ttu-id="3de7f-102">And</span><span class="sxs-lookup"><span data-stu-id="3de7f-102">And</span></span>
<span data-ttu-id="3de7f-103">移除前兩個項目從堆疊中，執行布林**AND**的兩個項目，並再將推送至堆疊的結果。</span><span class="sxs-lookup"><span data-stu-id="3de7f-103">Removes the top two items from the stack, performs a Boolean **AND** of the two items, and then pushes the result onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3de7f-104">語法</span><span class="sxs-lookup"><span data-stu-id="3de7f-104">Syntax</span></span>  
  
```  
  
<ic:Operation Name="And" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3de7f-105">參數</span><span class="sxs-lookup"><span data-stu-id="3de7f-105">Parameters</span></span>  
 <span data-ttu-id="3de7f-106">堆疊上的前兩個項目。</span><span class="sxs-lookup"><span data-stu-id="3de7f-106">Top two items on the stack.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="3de7f-107">推入的值</span><span class="sxs-lookup"><span data-stu-id="3de7f-107">Pushed Value</span></span>  
 <span data-ttu-id="3de7f-108">布林值的字串結果**AND**作業。</span><span class="sxs-lookup"><span data-stu-id="3de7f-108">String result of the Boolean **AND** operation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3de7f-109">備註</span><span class="sxs-lookup"><span data-stu-id="3de7f-109">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="3de7f-110">範例</span><span class="sxs-lookup"><span data-stu-id="3de7f-110">Example</span></span>  
 <span data-ttu-id="3de7f-111">**和**作業時，您需要評估多個陳述式。</span><span class="sxs-lookup"><span data-stu-id="3de7f-111">The **And** operation is useful when you need to evaluate multiple statements.</span></span> <span data-ttu-id="3de7f-112">下列範例篩選條件運算式檢查是否活動名稱為"CheckPO"，並使用關閉活動事件**和**作業。</span><span class="sxs-lookup"><span data-stu-id="3de7f-112">The following example filter expression checks whether the activity name is "CheckPO" and the activity event is closed by using the **And** operation.</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>CheckPO</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <wf:Operation Name="GetActivityEvent"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <ic:Operation Name="And"/>  
  </ic:Expression>  
</ic:Filter>  
```  
  
 <span data-ttu-id="3de7f-113">在此範例中**和**是在運算式中的最終作業，因為它依賴比較結果 （並取出它們從堆疊來執行比較）。</span><span class="sxs-lookup"><span data-stu-id="3de7f-113">In this example **And** is the final operation in the expression because it relies on the results of the comparisons (and pops them from the stack to perform the comparison).</span></span> <span data-ttu-id="3de7f-114">您可以延伸這個概念，若要執行**和**兩個以上的項目上的作業。</span><span class="sxs-lookup"><span data-stu-id="3de7f-114">You can extend this idea to perform **And** operations on more than two items.</span></span> <span data-ttu-id="3de7f-115">例如，若要評估「條件 A」、「條件 B」和「條件 C」是否為 true，您可以使用如下所示的運算式：</span><span class="sxs-lookup"><span data-stu-id="3de7f-115">For example, to evaluate whether Condition A and Condition B and Condition C are true, you would use an expression like the following:</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>CheckPO</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <wf:Operation Name="GetActivityEvent"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <wf:Operation Name="GetActivityType"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyType</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <ic:Operation Name="And"/>  
    <ic:Operation Name="And"/>  
  </ic:Expression>  
</ic:Filter>   
```  
  
## <a name="see-also"></a><span data-ttu-id="3de7f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3de7f-116">See Also</span></span>  
 [<span data-ttu-id="3de7f-117">攔截器作業</span><span class="sxs-lookup"><span data-stu-id="3de7f-117">Interceptor Operations</span></span>](../core/interceptor-operations.md)