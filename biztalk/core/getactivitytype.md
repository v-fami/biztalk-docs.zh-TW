---
title: 將 GetActivityType |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65a5aae3-9688-4c49-a78e-1d9c1cc85fea
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67e6f31331907e20e810c11e82002fb08b89abe4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246414"
---
# <a name="getactivitytype"></a><span data-ttu-id="c83fb-102">GetActivityType</span><span class="sxs-lookup"><span data-stu-id="c83fb-102">GetActivityType</span></span>
<span data-ttu-id="c83fb-103">將目前活動類型的名稱推至堆疊上。</span><span class="sxs-lookup"><span data-stu-id="c83fb-103">Pushes the name of the current activity type onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c83fb-104">語法</span><span class="sxs-lookup"><span data-stu-id="c83fb-104">Syntax</span></span>  
  
```  
  
<wf:Operation Name="GetActivityType" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c83fb-105">參數</span><span class="sxs-lookup"><span data-stu-id="c83fb-105">Parameters</span></span>  
 <span data-ttu-id="c83fb-106">無。</span><span class="sxs-lookup"><span data-stu-id="c83fb-106">None.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="c83fb-107">推入的值</span><span class="sxs-lookup"><span data-stu-id="c83fb-107">Pushed Value</span></span>  
 <span data-ttu-id="c83fb-108">字串，包含具有組件限定類別名稱格式的目前活動類型。</span><span class="sxs-lookup"><span data-stu-id="c83fb-108">String containing the current activity type in assembly-qualified class name format.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c83fb-109">備註</span><span class="sxs-lookup"><span data-stu-id="c83fb-109">Remarks</span></span>  
 <span data-ttu-id="c83fb-110">`GetActivityType` 作業會擷取目前活動類型並以組件限定的類別名稱格式將其置於堆疊上：</span><span class="sxs-lookup"><span data-stu-id="c83fb-110">The `GetActivityType` operation retrieves the current activity type and places it on the stack in assembly-qualified class name format:</span></span>  
  
```  
TopNamespace.SubNameSpace.ContainingClass+NestedClass, MyAssembly, Version=1.3.0.0, Culture=neutral, PublicKeyToken=b17a5c561934e08, processorArchitecture=MSIL  
```  
  
 <span data-ttu-id="c83fb-111">進行比較時，您可以視需要指定類型，以滿足特定搜尋需求。</span><span class="sxs-lookup"><span data-stu-id="c83fb-111">When comparing, you can specify as much of the type as necessary to satisfy your specific search needs.</span></span> <span data-ttu-id="c83fb-112">例如，您可能會將 GetActivityType 的結果與以下常數比較：</span><span class="sxs-lookup"><span data-stu-id="c83fb-112">For example, you might compare the result of GetActivityType with the constant:</span></span>  
  
 <span data-ttu-id="c83fb-113">TopNamespace.SubNameSpace.ContainingClass+NestedClass, MyAssembly, Version=1.3.0.0</span><span class="sxs-lookup"><span data-stu-id="c83fb-113">TopNamespace.SubNameSpace.ContainingClass+NestedClass, MyAssembly, Version=1.3.0.0</span></span>  
  
 <span data-ttu-id="c83fb-114">這比組件限定的類別名稱格式的限制要少。</span><span class="sxs-lookup"><span data-stu-id="c83fb-114">This is less restrictive than the assembly-qualified class name format.</span></span>  
  
## <a name="special-filter-behavior"></a><span data-ttu-id="c83fb-115">特殊篩選行為</span><span class="sxs-lookup"><span data-stu-id="c83fb-115">Special Filter Behavior</span></span>  
 <span data-ttu-id="c83fb-116">在篩選器內部執行這項作業時，一定也會比對衍生的活動。</span><span class="sxs-lookup"><span data-stu-id="c83fb-116">When this operation is performed inside of a filter, derived activities are always matched as well.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c83fb-117">範例</span><span class="sxs-lookup"><span data-stu-id="c83fb-117">Example</span></span>  
 <span data-ttu-id="c83fb-118">下列範例包含事件篩選器運算式，此運算式會針對 `true` 執行個體和衍生自 `System.Workflow.ComponentModel.Activity` 的任何類別執行個體評估為 `System.Workflow.ComponentModel.Activity`。</span><span class="sxs-lookup"><span data-stu-id="c83fb-118">The following sample contains an event filter expression that will evaluate to `true` for `System.Workflow.ComponentModel.Activity` instances and any instances from classes that derive from `System.Workflow.ComponentModel.Activity`.</span></span>  
  
```  
<ic:Expression>  
  <wf:Operation Name="GetActivityType" />  
  <ic:Operation Name="Constant">  
    <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
  </ic:Operation>  
  <ic:Operation Name="Equals" />  
</ic:Expression>  
```