---
title: 自訂例外狀況 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- process management solution tutorial, compensation blocks
- compensation blocks, process management solutions
- process management solution tutorial, custom exceptions
- Terminate shape [Orchestration Designer], called orchestrations
- process management solution tutorial, errors
ms.assetid: 0c923303-82ad-4a20-9c7c-5e38c477993a
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bfead2aadc237d27e0fb8ed28a776dd1e4f5c6f6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22240134"
---
# <a name="custom-exceptions"></a><span data-ttu-id="f8447-102">自訂例外狀況</span><span class="sxs-lookup"><span data-stu-id="f8447-102">Custom Exceptions</span></span>
<span data-ttu-id="f8447-103">出現無法復原的錯誤時，「商務程序管理」解決方案會使用例外狀況處理常式搭配自訂例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f8447-103">For situations where there is an unrecoverable error, the Business Process Management solution uses a combination of exception handlers and custom exceptions.</span></span>  
  
## <a name="handling-exceptions"></a><span data-ttu-id="f8447-104">處理例外狀況</span><span class="sxs-lookup"><span data-stu-id="f8447-104">Handling Exceptions</span></span>  
 <span data-ttu-id="f8447-105">而不是使用**Terminate**呼叫的協調流程中的圖形，您可以使用擲回例外狀況由根協調流程處理模式。</span><span class="sxs-lookup"><span data-stu-id="f8447-105">Rather than using **Terminate** shapes in called orchestrations you can use the pattern of throwing exceptions that are handled by the root orchestration.</span></span> <span data-ttu-id="f8447-106">如此可讓具有最廣內容範圍的協調流程做出處理例外狀況的決定。</span><span class="sxs-lookup"><span data-stu-id="f8447-106">This allows the orchestration with the widest knowledge of context to make the decision about handling the exception.</span></span> <span data-ttu-id="f8447-107">讓附屬協調流程擲回自訂例外狀況可讓您與根協調流程交流更明確的資訊。</span><span class="sxs-lookup"><span data-stu-id="f8447-107">Having the subordinate orchestrations throw custom exceptions enables you to communicate more specific information to the root orchestration.</span></span>  
  
 <span data-ttu-id="f8447-108">商務程序管理解決方案遵循此模式。</span><span class="sxs-lookup"><span data-stu-id="f8447-108">The business process management solution follows this pattern.</span></span> <span data-ttu-id="f8447-109">有四個根，或在方案中的使用未呼叫，協調流程： **OrderBroker**， **OrderManager**， **CableOrder1**，和**CableOrder2**.</span><span class="sxs-lookup"><span data-stu-id="f8447-109">There are four root, or uncalled, orchestrations in the solution: **OrderBroker**, **OrderManager**, **CableOrder1**, and **CableOrder2**.</span></span> <span data-ttu-id="f8447-110">三個根協調流程接收和處理自訂例外狀況： **OrderManager**， **CableOrder1**，和**CableOrder2**。</span><span class="sxs-lookup"><span data-stu-id="f8447-110">Three of the root orchestrations receive and handle custom exceptions: **OrderManager**, **CableOrder1**, and **CableOrder2**.</span></span>  
  
 <span data-ttu-id="f8447-111">請注意，某些根協調流程使用**Terminate**圖形，且該**Terminate** 」 圖形會顯示一般結束點的協調流程之前。</span><span class="sxs-lookup"><span data-stu-id="f8447-111">Note that some of the root orchestrations use the **Terminate** shape and that the **Terminate** shape appears just before the normal end point of the orchestration.</span></span> <span data-ttu-id="f8447-112">協調流程仍會使用**Terminate**圖形發生錯誤時，讓協調流程會記錄為已終止，而不是已完成但有錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="f8447-112">The orchestration still uses the **Terminate** shape in case of an error so that the orchestration is recorded as terminated, rather than as completed but with an error message.</span></span> <span data-ttu-id="f8447-113">這種方式可讓解決方案除了記錄錯誤外，也能輕鬆地追蹤失敗的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f8447-113">This allows the solution to track failed instances easily in addition to recording the error.</span></span>  
  
 <span data-ttu-id="f8447-114">如需有關**Terminate**圖形，請參閱[如何設定終止圖形](../core/how-to-configure-the-terminate-shape.md)。</span><span class="sxs-lookup"><span data-stu-id="f8447-114">For more information about the **Terminate** shape, see [How to Configure the Terminate Shape](../core/how-to-configure-the-terminate-shape.md).</span></span> <span data-ttu-id="f8447-115">如需有關**ThrowException**圖形，請參閱[如何設定擲回例外狀況圖形](../core/how-to-configure-the-throw-exception-shape.md)。</span><span class="sxs-lookup"><span data-stu-id="f8447-115">For more information about the **ThrowException** shape, see [How to Configure the Throw Exception Shape](../core/how-to-configure-the-throw-exception-shape.md).</span></span>  
  
## <a name="the-custom-exceptions"></a><span data-ttu-id="f8447-116">自訂例外狀況</span><span class="sxs-lookup"><span data-stu-id="f8447-116">The Custom Exceptions</span></span>  
 <span data-ttu-id="f8447-117">下列三種自訂例外狀況都是遵循相同的模式。</span><span class="sxs-lookup"><span data-stu-id="f8447-117">Each of the following three custom exceptions follows the same pattern.</span></span> <span data-ttu-id="f8447-118">擁有不同的類型可讓程式碼分辨不同的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f8447-118">Having distinct types allows the code to distinguish different exceptions.</span></span>  
  
|<span data-ttu-id="f8447-119">Exception</span><span class="sxs-lookup"><span data-stu-id="f8447-119">Exception</span></span>|<span data-ttu-id="f8447-120">擲回 (協調流程)</span><span class="sxs-lookup"><span data-stu-id="f8447-120">Thrown By (Orchestration)</span></span>|  
|---------------|---------------------------------|  
|<span data-ttu-id="f8447-121">**ActivateException**</span><span class="sxs-lookup"><span data-stu-id="f8447-121">**ActivateException**</span></span>|<span data-ttu-id="f8447-122">**變更**</span><span class="sxs-lookup"><span data-stu-id="f8447-122">**Change**</span></span>|  
|<span data-ttu-id="f8447-123">**CableOrderException**</span><span class="sxs-lookup"><span data-stu-id="f8447-123">**CableOrderException**</span></span>|<span data-ttu-id="f8447-124">**啟動**， **CableOrder1**</span><span class="sxs-lookup"><span data-stu-id="f8447-124">**Activate**, **CableOrder1**</span></span>|  
|<span data-ttu-id="f8447-125">**InterruptException**</span><span class="sxs-lookup"><span data-stu-id="f8447-125">**InterruptException**</span></span>|<span data-ttu-id="f8447-126">**CableOrder1**， **CheckInterrupt**， **ErrorHandlerOrch**</span><span class="sxs-lookup"><span data-stu-id="f8447-126">**CableOrder1**, **CheckInterrupt**, **ErrorHandlerOrch**</span></span>|  
  
 <span data-ttu-id="f8447-127">所有的自訂例外狀況都定義在**公用程式**組件。</span><span class="sxs-lookup"><span data-stu-id="f8447-127">All of the custom exceptions are defined in the **Utilities** assembly.</span></span> <span data-ttu-id="f8447-128">自訂例外狀況都是 .NET 類別。</span><span class="sxs-lookup"><span data-stu-id="f8447-128">The custom exceptions are all .NET classes.</span></span> <span data-ttu-id="f8447-129">所有的自訂例外狀況類別繼承自.NET **ApplicationException**類別繼承自該類別**System.Exception**類別。</span><span class="sxs-lookup"><span data-stu-id="f8447-129">All of the custom exception classes inherit from the .NET **ApplicationException** class which in turn inherits from the **System.Exception** class.</span></span> <span data-ttu-id="f8447-130">由於例外狀況可以凍結 (序列化並儲存於資料庫)，因此例外狀況必須實作還原序列化建構函式。</span><span class="sxs-lookup"><span data-stu-id="f8447-130">Because there is a possibility that the exception may be dehydrated (serialized and stored in the database), the exceptions must implement a deserialization constructor.</span></span> <span data-ttu-id="f8447-131">還原序列化建構函式會採用兩個引數的建構函式： SerializationInfo 物件和一個 StreamingContext 物件。</span><span class="sxs-lookup"><span data-stu-id="f8447-131">A deserialization constructor is a constructor that takes two arguments: a SerializationInfo object, and a StreamingContext object.</span></span> <span data-ttu-id="f8447-132">此還原序列化建構函式將用於例外狀況的解除凍結期間。</span><span class="sxs-lookup"><span data-stu-id="f8447-132">The deserialization constructor will be used during rehydration of the exception.</span></span> <span data-ttu-id="f8447-133">因為**ApplicationException**類別已經實作還原序列化建構函式、 自訂例外狀況的建構函式只會叫用的基底 (ApplicationException) 還原序列化建構函式。</span><span class="sxs-lookup"><span data-stu-id="f8447-133">Because the **ApplicationException** class already implements a deserialization constructor, the constructor for the custom exception simply invokes the base (ApplicationException) deserialization constructor.</span></span> <span data-ttu-id="f8447-134">例如， **InterruptException**包含下列建構函式：</span><span class="sxs-lookup"><span data-stu-id="f8447-134">For example, the **InterruptException** includes the following constructor:</span></span>  
  
```  
// "info" is the object holding the serialized object data.  
// "context" is the contextual information about the source  
// or destination.  
public InterruptException(SerializationInfo info,  
                  StreamingContext context) : base(info, context) { }  
```  
  
 <span data-ttu-id="f8447-135">如需有關自訂序列化的詳細資訊，請參閱《[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] 開發人員手冊》中的＜自訂序列化＞。</span><span class="sxs-lookup"><span data-stu-id="f8447-135">For more detailed information about custom serialization, see Custom Serialization in the [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] Developer's Guide.</span></span>  
  
## <a name="nested-exception-handlers-and-compensation-blocks"></a><span data-ttu-id="f8447-136">巢狀例外狀況處理常式和補償區塊</span><span class="sxs-lookup"><span data-stu-id="f8447-136">Nested Exception Handlers and Compensation Blocks</span></span>  
 <span data-ttu-id="f8447-137">自訂例外狀況除了可以做為特製化例外狀況之外，在某些地方也做為排序旗標。</span><span class="sxs-lookup"><span data-stu-id="f8447-137">In addition to serving as specialized exceptions, the custom exceptions in several places also serve as a sort flag.</span></span> <span data-ttu-id="f8447-138">在**變更**協調流程中，取消作業必須復原的兩個地方。</span><span class="sxs-lookup"><span data-stu-id="f8447-138">In the **Change** orchestration, there are two places that the Cancel operation must be rolled back.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8447-139">您可能想要閱讀本節**變更**Visual Studio 中開啟協調流程。</span><span class="sxs-lookup"><span data-stu-id="f8447-139">You may want to read this section with the **Change** orchestration open in Visual Studio.</span></span>  
  
 <span data-ttu-id="f8447-140">頂端的協調流程中，如果呼叫**取消**協調流程失敗， **CancelCompensation**區塊會執行並回復**取消**交易。</span><span class="sxs-lookup"><span data-stu-id="f8447-140">At the top of the orchestration, if the call to the **Cancel** orchestration fails, the **CancelCompensation** block executes and rolls back the **Cancel** transaction.</span></span> <span data-ttu-id="f8447-141">如果一切順利，協調流程接著會呼叫**Activate**協調流程。</span><span class="sxs-lookup"><span data-stu-id="f8447-141">If all goes well, the orchestration then calls the **Activate** orchestration.</span></span>  
  
 <span data-ttu-id="f8447-142">如果**Activate**作業將會失敗，**取消**必須也會回復交易。</span><span class="sxs-lookup"><span data-stu-id="f8447-142">If the **Activate** operation fails, the **Cancel** transaction must also be rolled back.</span></span> <span data-ttu-id="f8447-143">不過，若要呼叫的例外狀況處理常式**Activate**不會知道**取消**交易。</span><span class="sxs-lookup"><span data-stu-id="f8447-143">However, the exception handler for the call to **Activate** knows nothing about the **Cancel** transaction.</span></span> <span data-ttu-id="f8447-144">若要處理這種情形，有適用整個協調流程的例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="f8447-144">To handle this, there is an exception handler for the entire orchestration.</span></span> <span data-ttu-id="f8447-145">這個處理常式，因為它包含**取消**範圍，知道**取消**交易。</span><span class="sxs-lookup"><span data-stu-id="f8447-145">This handler, because it contains the **Cancel** scope, knows about the **Cancel** transaction.</span></span> <span data-ttu-id="f8447-146">處理常式會攔截擲回的例外狀況**Activate**範圍 ( **ActivateException**)，回復**取消**交易，然後擲回的例外狀況如此一來協調流程呼叫**變更**協調流程可以執行任何額外的處理。</span><span class="sxs-lookup"><span data-stu-id="f8447-146">The handler catches the exception thrown from the **Activate** scope (the **ActivateException**), rolls back the **Cancel** transaction, and then throws the exception again so that the orchestration that called the **Change** orchestration can perform any additional processing.</span></span>  
  
 <span data-ttu-id="f8447-147">請注意，此設計只補償**取消**如果**Activate**失敗。</span><span class="sxs-lookup"><span data-stu-id="f8447-147">Notice that this design only compensates the **Cancel** if the **Activate** fails.</span></span> <span data-ttu-id="f8447-148">如果**取消**失敗並擲回例外狀況，**取消**不會發生，所以不需要補償。</span><span class="sxs-lookup"><span data-stu-id="f8447-148">If the **Cancel** fails and throws an exception, the **Cancel** never took place and should not be compensated.</span></span>  
  
 <span data-ttu-id="f8447-149">如需有關補償區塊和**補償**圖形，請參閱[如何設定補償圖形](../core/how-to-configure-the-compensate-shape.md)。</span><span class="sxs-lookup"><span data-stu-id="f8447-149">For more information about compensation blocks and the **Compensate** shape, see [How to Configure the Compensate Shape](../core/how-to-configure-the-compensate-shape.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8447-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8447-150">See Also</span></span>  
 <span data-ttu-id="f8447-151">[在商務程序管理解決方案中處理的例外狀況](../core/exception-handling-in-the-business-process-management-solution.md) </span><span class="sxs-lookup"><span data-stu-id="f8447-151">[Exception Handling in the Business Process Management Solution](../core/exception-handling-in-the-business-process-management-solution.md) </span></span>  
 [<span data-ttu-id="f8447-152">ExceptionHandler 協調流程</span><span class="sxs-lookup"><span data-stu-id="f8447-152">The ExceptionHandler Orchestration</span></span>](../core/the-exceptionhandler-orchestration.md)