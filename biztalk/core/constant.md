---
title: 常數 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0af49bf5-e7de-41da-ac27-70301b8ee4d4
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 674307acea439bc260399cc01da4165eedaa2da5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22237790"
---
# <a name="constant"></a><span data-ttu-id="168e6-102">常數</span><span class="sxs-lookup"><span data-stu-id="168e6-102">Constant</span></span>
<span data-ttu-id="168e6-103">將單一常數值推入至堆疊。</span><span class="sxs-lookup"><span data-stu-id="168e6-103">Pushes a single constant value onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="168e6-104">語法</span><span class="sxs-lookup"><span data-stu-id="168e6-104">Syntax</span></span>  
  
```  
  
<ic:Operation Name="Constant">  
  <ic:Argument>val</ic:Argument>  
</ic:Operation>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="168e6-105">參數</span><span class="sxs-lookup"><span data-stu-id="168e6-105">Parameters</span></span>  
 <span data-ttu-id="168e6-106">常數值。</span><span class="sxs-lookup"><span data-stu-id="168e6-106">Constant value.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="168e6-107">推入的值</span><span class="sxs-lookup"><span data-stu-id="168e6-107">Pushed Value</span></span>  
 <span data-ttu-id="168e6-108">包含常數值的字串。</span><span class="sxs-lookup"><span data-stu-id="168e6-108">String containing the constant value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="168e6-109">備註</span><span class="sxs-lookup"><span data-stu-id="168e6-109">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="168e6-110">範例</span><span class="sxs-lookup"><span data-stu-id="168e6-110">Example</span></span>  
 <span data-ttu-id="168e6-111">下列範例篩選條件運算式使用**常數**運算推入值，然後將使用在**等於**作業以確定目前的活動名稱為"FoodAndDrinksPolicy"。</span><span class="sxs-lookup"><span data-stu-id="168e6-111">The following sample filter expression uses the **Constant** operation to push a value that will then be used in an **Equals** operation to ensure that the current activity name is "FoodAndDrinksPolicy".</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>FoodAndDrinksPolicy</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
  </ic:Expression>  
</ic:Filter>  
```  
  
 <span data-ttu-id="168e6-112">這是常見的使用方式模式**常數**作業。</span><span class="sxs-lookup"><span data-stu-id="168e6-112">This is a common usage pattern for the **Constant** operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="168e6-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="168e6-113">See Also</span></span>  
 [<span data-ttu-id="168e6-114">攔截器作業</span><span class="sxs-lookup"><span data-stu-id="168e6-114">Interceptor Operations</span></span>](../core/interceptor-operations.md)