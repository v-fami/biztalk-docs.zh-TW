---
title: 與接收訊息 」 圖形使用篩選器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- filters, receive messages
- messages, filters
ms.assetid: 5310039b-6719-4971-933a-2da0573fb5e7
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1434e9704e073cfef1503ef550409e6d6414bb7c
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
ms.locfileid: "22287878"
---
# <a name="using-filters-with-the-receive-message-shape"></a><span data-ttu-id="9dc32-102">使用篩選器與接收訊息 」 圖形</span><span class="sxs-lookup"><span data-stu-id="9dc32-102">Using Filters With the Receive Message Shape</span></span>
<span data-ttu-id="9dc32-103">篩選條件運算式是選擇性的參數，可以套用至將 [啟動] 屬性指定為 True 值的協調流程接收圖形。</span><span class="sxs-lookup"><span data-stu-id="9dc32-103">A filter expression is an optional parameter that can be applied to an orchestration receive shape that specifies a value of True for the Activate property.</span></span> <span data-ttu-id="9dc32-104">如果有指定篩選條件運算式，協調流程便只會在內送訊息符合篩選條件運算式中指定的條件時啟動。</span><span class="sxs-lookup"><span data-stu-id="9dc32-104">If a filter expression is specified then the orchestration will only be activated if an incoming message matches the condition(s) specified in the filter expression.</span></span> <span data-ttu-id="9dc32-105">如果沒有指定篩選條件運算式，協調流程所訂閱的任何內送訊息都會啟動該協調流程。</span><span class="sxs-lookup"><span data-stu-id="9dc32-105">If no filter expression is specified then any incoming message that the orchestration subscribes to will activate the orchestration.</span></span>  
  
 <span data-ttu-id="9dc32-106">若要建立篩選條件運算式，您可以比較運算式左邊的內送訊息屬性和運算式右邊的常數。</span><span class="sxs-lookup"><span data-stu-id="9dc32-106">To create a filter expression, you compare a property of an incoming message on the left side of the expression with a constant on the right side of the expression.</span></span> <span data-ttu-id="9dc32-107">您也可以將 AND 和 OR 運算子套用至兩個或多個運算式，以便建立複合運算式。</span><span class="sxs-lookup"><span data-stu-id="9dc32-107">You can also create compound expressions by applying the AND and OR operators to two or more expressions.</span></span> <span data-ttu-id="9dc32-108">您也可以將篩選條件運算式留白，在此情況下，便會接受所有的訊息。</span><span class="sxs-lookup"><span data-stu-id="9dc32-108">You can also leave blank the filter expression, in which case all messages will be accepted.</span></span>  
  
 <span data-ttu-id="9dc32-109">篩選條件運算式可能會與下列相似：</span><span class="sxs-lookup"><span data-stu-id="9dc32-109">A filter expression might look like the following:</span></span>  
  
```  
InvoiceSchema.Quantity >= 1000  
```  
  
 <span data-ttu-id="9dc32-110">在此範例中，會對協調流程展示內送訊息。</span><span class="sxs-lookup"><span data-stu-id="9dc32-110">In this example, an incoming message is presented to the orchestration.</span></span> <span data-ttu-id="9dc32-111">協調流程具有啟動 **接收** 圖形 ( **啟用** 屬性設定為 **True** 以便接收特定訊息會造成執行協調流程) 與先前套用的篩選運算式。</span><span class="sxs-lookup"><span data-stu-id="9dc32-111">The orchestration has an activation **Receive** shape (the **Activation** property is set to **True** so that receipt of a certain message will cause the orchestration to be run) with the preceding filter expression applied to it.</span></span> <span data-ttu-id="9dc32-112">內送訊息都應該要有屬性的命名空間中稱為 Quantity **InvoiceSchema**。</span><span class="sxs-lookup"><span data-stu-id="9dc32-112">The incoming message is expected to have property called Quantity in the namespace **InvoiceSchema**.</span></span> <span data-ttu-id="9dc32-113">協調流程只接受 1000 個以上項目的發票，因此執行階段引擎會在執行之前檢查內送訊息。</span><span class="sxs-lookup"><span data-stu-id="9dc32-113">The orchestration accepts only invoices for 1000 or more items, so the runtime engine checks the incoming message before it runs.</span></span>  
  
 <span data-ttu-id="9dc32-114">下表顯示您可以在篩選條件運算式中使用的運算子。</span><span class="sxs-lookup"><span data-stu-id="9dc32-114">The following table shows operators that you can use in filter expressions.</span></span>  
  
|<span data-ttu-id="9dc32-115">運算子</span><span class="sxs-lookup"><span data-stu-id="9dc32-115">Operator</span></span>|<span data-ttu-id="9dc32-116">Description</span><span class="sxs-lookup"><span data-stu-id="9dc32-116">Description</span></span>|<span data-ttu-id="9dc32-117">範例</span><span class="sxs-lookup"><span data-stu-id="9dc32-117">Example</span></span>|  
|--------------|-----------------|-------------|  
|==|<span data-ttu-id="9dc32-118">等於</span><span class="sxs-lookup"><span data-stu-id="9dc32-118">equal to</span></span>|<span data-ttu-id="9dc32-119">ReqMsg(Total) == 100</span><span class="sxs-lookup"><span data-stu-id="9dc32-119">ReqMsg(Total) == 100</span></span>|  
|<span data-ttu-id="9dc32-120">!=</span><span class="sxs-lookup"><span data-stu-id="9dc32-120">!=</span></span>|<span data-ttu-id="9dc32-121">不等於</span><span class="sxs-lookup"><span data-stu-id="9dc32-121">not equal to</span></span>|<span data-ttu-id="9dc32-122">ReqMsg(Total) != 100</span><span class="sxs-lookup"><span data-stu-id="9dc32-122">ReqMsg(Total) != 100</span></span>|  
|<|<span data-ttu-id="9dc32-123">小於</span><span class="sxs-lookup"><span data-stu-id="9dc32-123">less than</span></span>|<span data-ttu-id="9dc32-124">ReqMsg(Total) \< 100</span><span class="sxs-lookup"><span data-stu-id="9dc32-124">ReqMsg(Total) \< 100</span></span>|  
|>|<span data-ttu-id="9dc32-125">大於</span><span class="sxs-lookup"><span data-stu-id="9dc32-125">greater than</span></span>|<span data-ttu-id="9dc32-126">ReqMsg(Total) > 100</span><span class="sxs-lookup"><span data-stu-id="9dc32-126">ReqMsg(Total) > 100</span></span>|  
|<=|<span data-ttu-id="9dc32-127">小於或等於</span><span class="sxs-lookup"><span data-stu-id="9dc32-127">less than or equal to</span></span>|<span data-ttu-id="9dc32-128">ReqMsg(Total) \<= 100</span><span class="sxs-lookup"><span data-stu-id="9dc32-128">ReqMsg(Total) \<= 100</span></span>|  
|>=|<span data-ttu-id="9dc32-129">大於或等於</span><span class="sxs-lookup"><span data-stu-id="9dc32-129">greater than or equal to</span></span>|<span data-ttu-id="9dc32-130">ReqMsg(Total) > = 100</span><span class="sxs-lookup"><span data-stu-id="9dc32-130">ReqMsg(Total) >= 100</span></span>|  
|<span data-ttu-id="9dc32-131">exists</span><span class="sxs-lookup"><span data-stu-id="9dc32-131">exists</span></span>|<span data-ttu-id="9dc32-132">exists</span><span class="sxs-lookup"><span data-stu-id="9dc32-132">exists</span></span>|<span data-ttu-id="9dc32-133">ReqMsg(Description) exists</span><span class="sxs-lookup"><span data-stu-id="9dc32-133">ReqMsg(Description) exists</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="9dc32-134">在篩選條件運算式的字串值會以引號括住，例如︰ ReqMsg(Description) ="訂單狀態 」。</span><span class="sxs-lookup"><span data-stu-id="9dc32-134">String values in filter expressions are enclosed in quotation marks, for example: ReqMsg(Description) = "Purchase Order Status".</span></span> <span data-ttu-id="9dc32-135">您無法在篩選條件運算式中使用字元值。</span><span class="sxs-lookup"><span data-stu-id="9dc32-135">You cannot use a character value in a filter expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9dc32-136">如果您的啟動接收與某個直接繫結連接埠關聯，而且後來針對篩選條件所測試的屬性，傳送具有相同值之相同類型的訊息，就會建立無限的迴圈。</span><span class="sxs-lookup"><span data-stu-id="9dc32-136">If your activate receive is associated with a direct-bound port, and you subsequently send a message of the same type with the same value for the property tested in your filter, you will create an infinite loop.</span></span> <span data-ttu-id="9dc32-137">該訊息會移至 MessageBox，並會因為符合篩選準則，而被再度收取。</span><span class="sxs-lookup"><span data-stu-id="9dc32-137">The message will go to the MessageBox, where it will be picked up again because it matches the filter criteria.</span></span> <span data-ttu-id="9dc32-138">若要避免這個問題，您應該針對不同的屬性篩選、傳送不同類型的訊息，或是確定在將相同類型的訊息傳送出去之前變更屬性的值。</span><span class="sxs-lookup"><span data-stu-id="9dc32-138">To avoid this, you should either filter on a different property, send a message of a different type, or be sure to change the value of the property before sending out a message of the same type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dc32-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9dc32-139">See Also</span></span>  
 <span data-ttu-id="9dc32-140">[如何設定 「 接收 」 圖形](../core/how-to-configure-the-receive-shape.md) </span><span class="sxs-lookup"><span data-stu-id="9dc32-140">[How to Configure the Receive Shape](../core/how-to-configure-the-receive-shape.md) </span></span>  
 <span data-ttu-id="9dc32-141">[協調流程中使用的相互關聯](../core/using-correlations-in-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="9dc32-141">[Using Correlations in Orchestrations](../core/using-correlations-in-orchestrations.md) </span></span>  
 <span data-ttu-id="9dc32-142">[使用辨別的欄位和屬性欄位](../core/using-distinguished-fields-and-property-fields.md) </span><span class="sxs-lookup"><span data-stu-id="9dc32-142">[Using Distinguished Fields and Property Fields](../core/using-distinguished-fields-and-property-fields.md) </span></span>  
 [<span data-ttu-id="9dc32-143">協調流程中使用訊息</span><span class="sxs-lookup"><span data-stu-id="9dc32-143">Using Messages in Orchestrations</span></span>](../core/using-messages-in-orchestrations.md)