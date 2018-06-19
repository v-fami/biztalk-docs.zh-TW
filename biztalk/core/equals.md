---
title: 等於 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac93031a-9d18-443d-9e38-71ef9edd5a30
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b82ac5c779dc6b4d3624b48cebe9df1bc3d1966
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239814"
---
# <a name="equals"></a><span data-ttu-id="abc8e-102">等於</span><span class="sxs-lookup"><span data-stu-id="abc8e-102">Equals</span></span>
<span data-ttu-id="abc8e-103">從堆疊移除前兩個項目，比較這兩個項目，然後將結果推入至堆疊。</span><span class="sxs-lookup"><span data-stu-id="abc8e-103">Removes the top two items from the stack, compares the two items, and then pushes the result onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abc8e-104">語法</span><span class="sxs-lookup"><span data-stu-id="abc8e-104">Syntax</span></span>  
  
```  
  
<ic:Operation Name="Equals" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="abc8e-105">參數</span><span class="sxs-lookup"><span data-stu-id="abc8e-105">Parameters</span></span>  
 <span data-ttu-id="abc8e-106">堆疊上的前兩個項目。</span><span class="sxs-lookup"><span data-stu-id="abc8e-106">Top two items on the stack.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="abc8e-107">推入的值</span><span class="sxs-lookup"><span data-stu-id="abc8e-107">Pushed Value</span></span>  
 <span data-ttu-id="abc8e-108">比較作業的字串結果。</span><span class="sxs-lookup"><span data-stu-id="abc8e-108">String result of the comparison operation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abc8e-109">備註</span><span class="sxs-lookup"><span data-stu-id="abc8e-109">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="abc8e-110">範例</span><span class="sxs-lookup"><span data-stu-id="abc8e-110">Example</span></span>  
 <span data-ttu-id="abc8e-111">下列範例篩選條件運算式會使用**等於**運算，比較目前的活動名稱與常數"CheckPO"。</span><span class="sxs-lookup"><span data-stu-id="abc8e-111">The following example filter expression uses the **Equals** operation to compare the current activity name to the constant "CheckPO".</span></span> <span data-ttu-id="abc8e-112">如果兩者相等，運算式會評估為 `true`。</span><span class="sxs-lookup"><span data-stu-id="abc8e-112">If the two are equal, the expression evaluates to `true`.</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>CheckPO</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
  </ic:Expression>  
</ic:Filter>  
```  
  
 <span data-ttu-id="abc8e-113">您可能想要以撰寫 C# 陳述式執行比較的相同方式來建置運算式。</span><span class="sxs-lookup"><span data-stu-id="abc8e-113">You may be tempted to build your expression exactly as you would write a statement in C# when performing comparisons.</span></span> <span data-ttu-id="abc8e-114">例如，您可能要比較三個值，在 C# 中，您會撰寫類似下面的陳述式：</span><span class="sxs-lookup"><span data-stu-id="abc8e-114">For example, you might want to compare three values; in C# you would write something like:</span></span>  
  
```  
bool res = a == b == c;  
```  
  
 <span data-ttu-id="abc8e-115">不過，做為運算式篩選條件的模型，這不太符合標準。</span><span class="sxs-lookup"><span data-stu-id="abc8e-115">However, as a model for your expression filter this falls a little short.</span></span> <span data-ttu-id="abc8e-116">因此，請考慮已修改 (但相等) 的陳述式：</span><span class="sxs-lookup"><span data-stu-id="abc8e-116">Instead, consider the modified (but equivalent) statement:</span></span>  
  
```  
Bool res = (a == b) && (a == c);  
```  
  
 <span data-ttu-id="abc8e-117">這比較符合用來執行比較的篩選條件運算式。</span><span class="sxs-lookup"><span data-stu-id="abc8e-117">This more closely matches the filter expression you would use to perform the comparison.</span></span> <span data-ttu-id="abc8e-118">如需詳細資訊和範例，請參閱[和](../core/and.md)。</span><span class="sxs-lookup"><span data-stu-id="abc8e-118">For more details and an example, see [And](../core/and.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abc8e-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abc8e-119">See Also</span></span>  
 [<span data-ttu-id="abc8e-120">攔截器作業</span><span class="sxs-lookup"><span data-stu-id="abc8e-120">Interceptor Operations</span></span>](../core/interceptor-operations.md)