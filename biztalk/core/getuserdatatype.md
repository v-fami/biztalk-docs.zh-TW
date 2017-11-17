---
title: "GetUserDataType |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0605919-a733-4a9d-a725-109346db11a2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5525dba034571acd91d1f3dd99f2b56069f81fc2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="getuserdatatype"></a><span data-ttu-id="1fbfb-102">GetUserDataType</span><span class="sxs-lookup"><span data-stu-id="1fbfb-102">GetUserDataType</span></span>
<span data-ttu-id="1fbfb-103">將目前的使用者資料類型名稱推入到堆疊上。</span><span class="sxs-lookup"><span data-stu-id="1fbfb-103">Pushes the name of the current user data type onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fbfb-104">語法</span><span class="sxs-lookup"><span data-stu-id="1fbfb-104">Syntax</span></span>  
  
```  
  
<wf:Operation Name="GetUserDataType" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1fbfb-105">參數</span><span class="sxs-lookup"><span data-stu-id="1fbfb-105">Parameters</span></span>  
 <span data-ttu-id="1fbfb-106">無。</span><span class="sxs-lookup"><span data-stu-id="1fbfb-106">None.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="1fbfb-107">推入的值</span><span class="sxs-lookup"><span data-stu-id="1fbfb-107">Pushed Value</span></span>  
 <span data-ttu-id="1fbfb-108">字串，包含組件限定格式的目前使用者資料類型。</span><span class="sxs-lookup"><span data-stu-id="1fbfb-108">String containing the current user data type in assembly-qualified format.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1fbfb-109">備註</span><span class="sxs-lookup"><span data-stu-id="1fbfb-109">Remarks</span></span>  
 <span data-ttu-id="1fbfb-110">不同於**GetActivityType**，這項作業不會使用組件限定類別名稱格式，相反地，它將推入型別名稱：</span><span class="sxs-lookup"><span data-stu-id="1fbfb-110">Unlike **GetActivityType**, this operation does not use the assembly-qualified class name format; instead, it pushes only the type name:</span></span>  
  
```  
MyLibrary.MyObject  
```  
  
> [!NOTE]
>  <span data-ttu-id="1fbfb-111">如果您在比較值時使用組件限定的類別名稱格式做為常數，它一定會評估為 `false`。</span><span class="sxs-lookup"><span data-stu-id="1fbfb-111">If you use the assembly-qualified class name format as a constant when comparing values it will always evaluate to `false`.</span></span>  
  
## <a name="special-filter-behavior"></a><span data-ttu-id="1fbfb-112">特殊篩選行為</span><span class="sxs-lookup"><span data-stu-id="1fbfb-112">Special Filter Behavior</span></span>  
 <span data-ttu-id="1fbfb-113">在篩選器內部執行這項作業時，一定也會比對衍生的使用者資料類型。</span><span class="sxs-lookup"><span data-stu-id="1fbfb-113">When this operation is performed inside of a filter, derived user data types are always matched as well.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fbfb-114">範例</span><span class="sxs-lookup"><span data-stu-id="1fbfb-114">Example</span></span>  
 <span data-ttu-id="1fbfb-115">下列範例包含事件篩選器運算式，此運算式會針對 `true` 執行個體和衍生自 `MyLibrary.MyObject` 的任何類別執行個體評估為 `MyLibrary.MyObject`。</span><span class="sxs-lookup"><span data-stu-id="1fbfb-115">The following sample contains an event filter expression that will evaluate to `true` for `MyLibrary.MyObject` instances and for any instances from classes that derive from `MyLibrary.MyObject`.</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyLibrary.MyObject</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
  </ic:Expression>  
</ic:Filter>  
```