---
title: "Ops 配接器實作詳細資料 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, Ops adapters
- Ops adapters, batching
- Ops adapters, creating ports
- Ops adapters, implementing
- Ops adapters, transaction handling
- process management solution tutorial, Ops adapters
ms.assetid: dbca31ca-c3d8-4a25-9356-ef4bbab671e1
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d68a55ce0f6eba835313075e8ab3753ec825db2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="ops-adapter-implementation-details"></a><span data-ttu-id="7c550-102">Ops 配接器實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="7c550-102">Ops Adapter Implementation Details</span></span>
<span data-ttu-id="7c550-103">您會發現以程式設計方式修改或設定配接器時，瞭解 Ops 配接器的下列層面是非常有用的。</span><span class="sxs-lookup"><span data-stu-id="7c550-103">You may find it useful to understand the following aspects of the Ops adapter when modifying the adapter or configuring it programmatically.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c550-104">Ops 配接器是使用配接器架構所建置的。</span><span class="sxs-lookup"><span data-stu-id="7c550-104">The Ops Adapter is built using the Adapter Framework.</span></span> <span data-ttu-id="7c550-105">建置配接器架構的相關資訊，請參閱[開發自訂配接器](../core/developing-custom-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="7c550-105">For information about building adapters with the framework, see [Developing Custom Adapters](../core/developing-custom-adapters.md).</span></span>  
  
## <a name="batch-processing"></a><span data-ttu-id="7c550-106">批次處理</span><span class="sxs-lookup"><span data-stu-id="7c550-106">Batch Processing</span></span>  
 <span data-ttu-id="7c550-107">配接器一次處理一個訊息，因此每個訊息都是分開處理，而回復作業一次只針對一個訂單進行處理。</span><span class="sxs-lookup"><span data-stu-id="7c550-107">The adapter processes one message at a time so that each message is processed separately, and rollback operations are done on only one order at a time.</span></span> <span data-ttu-id="7c550-108">雖然配接器一次只處理一個訊息，但它會使用批次處理，以訊息的一個批次大小來處理訊息。</span><span class="sxs-lookup"><span data-stu-id="7c550-108">Although the adapter processes one message at a time, it does so using batching with a batch size of one.</span></span> <span data-ttu-id="7c550-109">這可讓您更輕鬆地修改配接器處理批次中的訊息。</span><span class="sxs-lookup"><span data-stu-id="7c550-109">This makes it easier to modify the adapter to handle messages in batches.</span></span>  
  
## <a name="transaction-handling"></a><span data-ttu-id="7c550-110">交易處理</span><span class="sxs-lookup"><span data-stu-id="7c550-110">Transaction Handling</span></span>  
 <span data-ttu-id="7c550-111">配接器會使用由 Microsoft 提供的交易設施[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] **System.Transactions**設備。</span><span class="sxs-lookup"><span data-stu-id="7c550-111">The adapter uses the transaction facilities provided by the Microsoft [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]**System.Transactions** facilities.</span></span> <span data-ttu-id="7c550-112">配接器建立新**CommittableTransaction** ，並使用它與**TransactionScope**。</span><span class="sxs-lookup"><span data-stu-id="7c550-112">The adapter creates a new **CommittableTransaction** and uses it with a **TransactionScope**.</span></span> <span data-ttu-id="7c550-113">配接器呼叫**初始化**和**Execute**此交易內容中的方法。</span><span class="sxs-lookup"><span data-stu-id="7c550-113">The adapter calls the **Initialize** and **Execute** methods within the context of this transaction.</span></span> <span data-ttu-id="7c550-114">呼叫的組件中的程式碼可以參與交易中使用**Transaction.Current**靜態方法來取得交易內容。</span><span class="sxs-lookup"><span data-stu-id="7c550-114">Code in the called assembly can participate in the transaction by using **Transaction.Current** static method to get the transaction context.</span></span> <span data-ttu-id="7c550-115">範例錯誤處理常式不會利用此功能。</span><span class="sxs-lookup"><span data-stu-id="7c550-115">The sample error handler does not make use of this facility.</span></span> <span data-ttu-id="7c550-116">如需有關**System.Transactions**，請參閱.NET Framework 類別庫版本中的 < System.Transactions 命名空間 >。</span><span class="sxs-lookup"><span data-stu-id="7c550-116">For more information about **System.Transactions**, see "System.Transactions Namespace" in the .NET Framework Class Library version.</span></span>  
  
## <a name="handling-data-other-than-error-reports"></a><span data-ttu-id="7c550-117">處理錯誤報告以外的資料</span><span class="sxs-lookup"><span data-stu-id="7c550-117">Handling Data Other Than Error Reports</span></span>  
 <span data-ttu-id="7c550-118">在解決方案中，配接器會從新的錯誤報告功能來處理錯誤報告訊息。</span><span class="sxs-lookup"><span data-stu-id="7c550-118">In the solution, the adapter handles error report messages from the new error reporting feature.</span></span> <span data-ttu-id="7c550-119">不過，因為**Execute**方法採用位元組陣列做為其唯一的引數，所以不會特別限制可以傳遞至**Execute**方法。</span><span class="sxs-lookup"><span data-stu-id="7c550-119">However, because the **Execute** method takes a byte array as its only argument, there is nothing that specifically limits what can be passed to the **Execute** method.</span></span>  
  
## <a name="using-the-adapter-when-creating-ports-programmatically"></a><span data-ttu-id="7c550-120">以程式設計方式建立連接埠時使用配接器</span><span class="sxs-lookup"><span data-stu-id="7c550-120">Using the Adapter When Creating Ports Programmatically</span></span>  
 <span data-ttu-id="7c550-121">您可以在從程式碼建立連接埠時指定配接器。</span><span class="sxs-lookup"><span data-stu-id="7c550-121">You can specify the adapter when creating ports from code.</span></span> <span data-ttu-id="7c550-122">下表顯示自訂屬性名稱以及它們如何對應到顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="7c550-122">The following table shows the custom property names and how they correspond to the display names.</span></span>  
  
|<span data-ttu-id="7c550-123">傳送自訂屬性名稱</span><span class="sxs-lookup"><span data-stu-id="7c550-123">Send Custom Property Name</span></span>|<span data-ttu-id="7c550-124">顯示名稱</span><span class="sxs-lookup"><span data-stu-id="7c550-124">Display Name</span></span>|  
|-------------------------------|------------------|  
|<span data-ttu-id="7c550-125">**DotNetAssemblyStrongName**</span><span class="sxs-lookup"><span data-stu-id="7c550-125">**DotNetAssemblyStrongName**</span></span>|<span data-ttu-id="7c550-126">**DotNetAssemblyStrongName**</span><span class="sxs-lookup"><span data-stu-id="7c550-126">**DotNetAssemblyStrongName**</span></span>|  
|<span data-ttu-id="7c550-127">**DotNetClassName**</span><span class="sxs-lookup"><span data-stu-id="7c550-127">**DotNetClassName**</span></span>|<span data-ttu-id="7c550-128">**DotNetClassName**</span><span class="sxs-lookup"><span data-stu-id="7c550-128">**DotNetClassName**</span></span>|  
|<span data-ttu-id="7c550-129">**InitializationData**</span><span class="sxs-lookup"><span data-stu-id="7c550-129">**InitializationData**</span></span>|<span data-ttu-id="7c550-130">**InitializationData**</span><span class="sxs-lookup"><span data-stu-id="7c550-130">**InitializationData**</span></span>|  
|<span data-ttu-id="7c550-131">**TransportLocationUri**</span><span class="sxs-lookup"><span data-stu-id="7c550-131">**TransportLocationUri**</span></span>|<span data-ttu-id="7c550-132">不適用。</span><span class="sxs-lookup"><span data-stu-id="7c550-132">Not applicable.</span></span>|  
  
 <span data-ttu-id="7c550-133">所有屬性均為字串值。</span><span class="sxs-lookup"><span data-stu-id="7c550-133">All of the properties are string values.</span></span> <span data-ttu-id="7c550-134">您可以從組件名稱和類別名稱建構 TransportLocationUri 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="7c550-134">You construct the value of the TransportLocationUri property from the assembly name and the class name.</span></span> <span data-ttu-id="7c550-135">URI 具有 OPS 的值: / /\<DotNetAssemblyStrongName > /\<DotNetClassName > 其中對應的自訂屬性的值會取代預留位置。</span><span class="sxs-lookup"><span data-stu-id="7c550-135">The URI has the value OPS://\<DotNetAssemblyStrongName>/\<DotNetClassName> where the placeholders are replaced by the values of the corresponding custom property.</span></span>  
  
 <span data-ttu-id="7c550-136">從程式碼建立連接埠的詳細資訊，請參閱[如何建立 MSMQ 接收位置和傳送埠的程式碼](../core/how-to-create-msmq-receive-locations-and-send-ports-from-code.md)。</span><span class="sxs-lookup"><span data-stu-id="7c550-136">For information about creating ports from code, see [How to Create MSMQ Receive Locations and Send Ports from Code](../core/how-to-create-msmq-receive-locations-and-send-ports-from-code.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c550-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c550-137">See Also</span></span>  
 [<span data-ttu-id="7c550-138">Ops 配接器</span><span class="sxs-lookup"><span data-stu-id="7c550-138">The Ops Adapter</span></span>](../core/the-ops-adapter.md)