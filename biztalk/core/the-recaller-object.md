---
title: Recaller 物件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Recaller object
- Invoke method
- process management solution tutorial, Recaller object
- process management solution tutorial, errors
ms.assetid: b30ad1ae-475f-4913-b402-4d3263fcf072
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 731f7703eb9145b1249872902d0b867fe22622ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279886"
---
# <a name="the-recaller-object"></a><span data-ttu-id="c1b3c-102">Recaller 物件</span><span class="sxs-lookup"><span data-stu-id="c1b3c-102">The Recaller Object</span></span>
<span data-ttu-id="c1b3c-103">商務程序管理解決方案會以一般的方法來重試某些失敗的物件方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-103">The business process management solution provides for retrying, in a generic way, some failed object method calls.</span></span> <span data-ttu-id="c1b3c-104">這個解決方案會執行透過**Recaller**物件存放至**ExceptionHandler**協調流程。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-104">The solution does this through the **Recaller** object in the **ExceptionHandler** orchestration.</span></span> <span data-ttu-id="c1b3c-105">**ExceptionHandler**協調流程會使用重試物件方法呼叫的物件。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-105">The **ExceptionHandler** orchestration uses the object to retry object method calls.</span></span> <span data-ttu-id="c1b3c-106">如需詳細資訊，請參閱[ExceptionHandler 協調流程](../core/the-exceptionhandler-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-106">For more information, see [The ExceptionHandler Orchestration](../core/the-exceptionhandler-orchestration.md).</span></span>  
  
## <a name="the-invoke-method"></a><span data-ttu-id="c1b3c-107">Invoke 方法</span><span class="sxs-lookup"><span data-stu-id="c1b3c-107">The Invoke Method</span></span>  
 <span data-ttu-id="c1b3c-108">**Recaller**物件有一個單一的靜態方法， **Invoke**。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-108">The **Recaller** object has a single, static method, **Invoke**.</span></span> <span data-ttu-id="c1b3c-109">因為它是靜態的您永遠不需要建立的執行個體**Recaller**物件。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-109">Because it is static, you never need to create an instance of the **Recaller** object.</span></span> <span data-ttu-id="c1b3c-110">您可以使用**Invoke**方法，以三種方式： 來建構物件，請呼叫靜態方法或呼叫物件的非靜態方法的物件。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-110">You can use the **Invoke** method in three ways: to construct an object, to call a static method for an object, or to call a non-static method for an object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1b3c-111">**Invoke**方法做為包裝函式**Type.InvokeMember**方法中的[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]類別庫。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-111">The **Invoke** method serves as a wrapper for the **Type.InvokeMember** method in the [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] Class Library.</span></span>  
  
### <a name="arguments-for-the-invoke-method"></a><span data-ttu-id="c1b3c-112">Invoke 方法的引數</span><span class="sxs-lookup"><span data-stu-id="c1b3c-112">Arguments for the Invoke Method</span></span>  
 <span data-ttu-id="c1b3c-113">下表描述的引數**Invoke**方法：</span><span class="sxs-lookup"><span data-stu-id="c1b3c-113">The following table describes arguments for the **Invoke** method:</span></span>  
  
|<span data-ttu-id="c1b3c-114">參數</span><span class="sxs-lookup"><span data-stu-id="c1b3c-114">Parameter</span></span>|<span data-ttu-id="c1b3c-115">類型</span><span class="sxs-lookup"><span data-stu-id="c1b3c-115">Type</span></span>|<span data-ttu-id="c1b3c-116">Description</span><span class="sxs-lookup"><span data-stu-id="c1b3c-116">Description</span></span>|  
|---------------|----------|-----------------|  
|<span data-ttu-id="c1b3c-117">*t*</span><span class="sxs-lookup"><span data-stu-id="c1b3c-117">*t*</span></span>|<span data-ttu-id="c1b3c-118">**型別**</span><span class="sxs-lookup"><span data-stu-id="c1b3c-118">**Type**</span></span>|<span data-ttu-id="c1b3c-119">呼叫方法的物件類型。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-119">The type of the object on which to call the method.</span></span>|  
|<span data-ttu-id="c1b3c-120">*obj*</span><span class="sxs-lookup"><span data-stu-id="c1b3c-120">*obj*</span></span>|<span data-ttu-id="c1b3c-121">**物件**</span><span class="sxs-lookup"><span data-stu-id="c1b3c-121">**Object**</span></span>|<span data-ttu-id="c1b3c-122">要使用的物件執行個體。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-122">The instance of the object to use.</span></span>|  
|<span data-ttu-id="c1b3c-123">*方法名稱*</span><span class="sxs-lookup"><span data-stu-id="c1b3c-123">*methodName*</span></span>|<span data-ttu-id="c1b3c-124">**string**</span><span class="sxs-lookup"><span data-stu-id="c1b3c-124">**string**</span></span>|<span data-ttu-id="c1b3c-125">要叫用的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-125">The name of the method to invoke.</span></span>|  
|<span data-ttu-id="c1b3c-126">*引數*</span><span class="sxs-lookup"><span data-stu-id="c1b3c-126">*args*</span></span>|<span data-ttu-id="c1b3c-127">**陣列**</span><span class="sxs-lookup"><span data-stu-id="c1b3c-127">**Array**</span></span>|<span data-ttu-id="c1b3c-128">類型的陣列**物件**包含方法的引數。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-128">An array of type **Object** containing the method's arguments.</span></span>|  
  
 <span data-ttu-id="c1b3c-129">若要呼叫物件建構函式，請使用空字串 ("") 或**null**如*methodName*。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-129">To call the constructor for an object, use an empty string ("") or **null** for *methodName*.</span></span>  
  
 <span data-ttu-id="c1b3c-130">若要呼叫靜態方法，使用**null**如*obj*。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-130">To call a static method, use **null** for *obj*.</span></span>  
  
 <span data-ttu-id="c1b3c-131">若要呼叫非靜態方法，請提供所有引數。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-131">To call a non-static method, supply all of the arguments.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1b3c-132">使用**null**做為型別引數的值*t*，會導致**Invoke**擲回**ArgumentNullException**例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-132">Using **null** as the value of the Type argument, *t*, causes **Invoke** to throw an **ArgumentNullException** exception.</span></span> <span data-ttu-id="c1b3c-133">引數*t*不應為 null 因為**Invoke**方法會使用**Type.InvokeMember** [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]方法。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-133">The argument *t* should not be null because the **Invoke** method uses the **Type.InvokeMember** [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] method.</span></span>  
  
## <a name="calling-invoke"></a><span data-ttu-id="c1b3c-134">呼叫 Invoke</span><span class="sxs-lookup"><span data-stu-id="c1b3c-134">Calling Invoke</span></span>  
 <span data-ttu-id="c1b3c-135">在方案中，只有**ExceptionHandler**協調流程使用**Recaller**物件。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-135">In the solution, only the **ExceptionHandler** orchestration uses the **Recaller** object.</span></span> <span data-ttu-id="c1b3c-136">**ExceptionHandler** ，接著，正由其他協調流程。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-136">The **ExceptionHandler** is, in turn, used by other orchestrations.</span></span> <span data-ttu-id="c1b3c-137">若要傳送的值， **Invoke**方法是從這些其他協調流程。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-137">The values passed to the **Invoke** method come from these other orchestrations.</span></span> <span data-ttu-id="c1b3c-138">例如，下列程式碼會出現在**Activate**中的協調流程**InitialException**運算式 」 圖形：</span><span class="sxs-lookup"><span data-stu-id="c1b3c-138">For example, the following code appears in the **Activate** orchestration in the **InitialException** Expression shape:</span></span>  
  
```  
Ex = CodeEx;  
ObjectType = orderHandler.GetType();  
CalledObject = orderHandler;  
Reason = "Standard Activate Failed";  
MethodName = "Activate";  
ParameterArray = System.Array.CreateInstance(typeof(System.Object),  
                                              3 );  
ParameterArray.SetValue(ServiceType, 0);  
ParameterArray.SetValue(OrderMsg.CustNum, 1);  
ParameterArray.SetValue(OrderMsg.OrderNum, 2);  
ReturnValue = null; // no return value expected  
  
```  
  
 <span data-ttu-id="c1b3c-139">請注意程式碼建立陣列使用**System.Array.CreateInstance**並用**SetValue**方法，可儲存在它所使用的值。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-139">Notice how the code creates an array using **System.Array.CreateInstance** and uses the **SetValue** method to store the values used in it.</span></span>  
  
 <span data-ttu-id="c1b3c-140">在運算式圖形之後呼叫 Activate 協調流程**ExceptionHandler**協調流程。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-140">After the Expression shape, the Activate orchestration calls the **ExceptionHandler** orchestration.</span></span> <span data-ttu-id="c1b3c-141">下列程式碼顯示協調流程設計師如何轉譯「呼叫」圖形：</span><span class="sxs-lookup"><span data-stu-id="c1b3c-141">The following code shows how the orchestration designer translates the Call shape:</span></span>  
  
```  
call Microsoft.Samples.  
    BizTalk.SouthridgeVideo.  
        OrderManager.ExceptionHandlerOrch  
            (  
                Reason,  
                Ex,  
                CalledObject,  
                MethodName,   
                ParameterArray,   
                OrderCorrelation,   
                OrderMsg,   
                out ReturnValue,   
                ObjectType  
            );  
  
```  
  
 <span data-ttu-id="c1b3c-142">在**ExceptionHandler**協調流程中，下列程式碼會出現在**Call Original Code**運算式 」 圖形：</span><span class="sxs-lookup"><span data-stu-id="c1b3c-142">In the **ExceptionHandler** orchestration, the following code appears in the **Call Original Code** Expression shape:</span></span>  
  
```  
ReturnValue =   
    Microsoft.Samples.  
        BizTalk.SouthridgeVideo.  
            Utilities.Recaller.  
                Invoke(  
                    ObjectType,  
                    CalledObject,  
                    MethodName,  
                    ParameterArray  
                );  
```  
  
 <span data-ttu-id="c1b3c-143">請注意，雖然引數名稱符合 Activate 協調流程呼叫中的引數名稱，但呼叫協調流程時，是依照順序而不是名稱來對應引數。</span><span class="sxs-lookup"><span data-stu-id="c1b3c-143">Notice that, although the argument names match those in the Activate orchestration's call, arguments are matched by order and not by name when calling orchestrations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1b3c-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1b3c-144">See Also</span></span>  
 <span data-ttu-id="c1b3c-145">[商務程序管理解決方案的實作重點](../core/implementation-highlights-of-the-business-process-management-solution.md) </span><span class="sxs-lookup"><span data-stu-id="c1b3c-145">[Implementation Highlights of the Business Process Management Solution](../core/implementation-highlights-of-the-business-process-management-solution.md) </span></span>  
 [<span data-ttu-id="c1b3c-146">ExceptionHandler 協調流程</span><span class="sxs-lookup"><span data-stu-id="c1b3c-146">The ExceptionHandler Orchestration</span></span>](../core/the-exceptionhandler-orchestration.md)