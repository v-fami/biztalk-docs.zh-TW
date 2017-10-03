---
title: "使用 WCF LOB 配接器 SDK 設定發送器起始或配接器起始交易 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 85b9ef8d-3922-4838-a41a-32db5e005dc0
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aa8105b4b6f8eb77d68471faf9b702419f6a1f90
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-dispatcher-initiated-or-adapter-initiated-transactions-with-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="985f0-102">使用 WCF LOB 配接器 SDK 設定發送器起始或配接器起始交易</span><span class="sxs-lookup"><span data-stu-id="985f0-102">Configure dispatcher-initiated or adapter-initiated transactions with the WCF LOB Adapter SDK</span></span>
## <a name="inbound-transactions"></a><span data-ttu-id="985f0-103">輸入的交易</span><span class="sxs-lookup"><span data-stu-id="985f0-103">Inbound Transactions</span></span>  
 <span data-ttu-id="985f0-104">有兩種方法的實作與輸入操作的交易： 發送器起始或配接器起始。</span><span class="sxs-lookup"><span data-stu-id="985f0-104">There are two methods of implementing transactions with inbound operations: dispatcher-initiated or adapter-initiated.</span></span> <span data-ttu-id="985f0-105">配接器的需求會指定應該使用哪一種方法。</span><span class="sxs-lookup"><span data-stu-id="985f0-105">The requirements of the adapter dictate which method should be used.</span></span> <span data-ttu-id="985f0-106">值`SupportsTransactedInbound`屬性會指出您的配接器將實作哪一種交易。</span><span class="sxs-lookup"><span data-stu-id="985f0-106">The value of the `SupportsTransactedInbound` property indicates which type of transaction your adapter will implement.</span></span>  
  
 <span data-ttu-id="985f0-107">下表比較發送器起始與配接器起始的交易。</span><span class="sxs-lookup"><span data-stu-id="985f0-107">The following table compares dispatcher-initiated with adapter-initiated transactions.</span></span>  
  
|<span data-ttu-id="985f0-108">SupportsTransactedInbound</span><span class="sxs-lookup"><span data-stu-id="985f0-108">SupportsTransactedInbound</span></span>|<span data-ttu-id="985f0-109">交易式行為</span><span class="sxs-lookup"><span data-stu-id="985f0-109">Transactional Behavior</span></span>|  
|-------------------------------|----------------------------|  
|<span data-ttu-id="985f0-110">True （發送器啟動）</span><span class="sxs-lookup"><span data-stu-id="985f0-110">True (dispatcher-initiated)</span></span>|<span data-ttu-id="985f0-111">-TryReceive 一律會在交易內容中呼叫。</span><span class="sxs-lookup"><span data-stu-id="985f0-111">-   TryReceive will always be called within the context of a transaction.</span></span><br /><span data-ttu-id="985f0-112">的之後的訊息傳回至服務實作，將會認可交易。</span><span class="sxs-lookup"><span data-stu-id="985f0-112">-   The transaction will be committed after the message is returned to the service implementation.</span></span><br /><span data-ttu-id="985f0-113">-新的交易將會建立每個 IInputChannel.Receive 呼叫。</span><span class="sxs-lookup"><span data-stu-id="985f0-113">-   A new transaction will be created for each IInputChannel.Receive call.</span></span> <span data-ttu-id="985f0-114">跨多個跨越交易接收依存於服務主機，而不是配接器開發。</span><span class="sxs-lookup"><span data-stu-id="985f0-114">Spanning a transaction across multiple receives is dependent on the service host and not the adapter developer.</span></span> <span data-ttu-id="985f0-115">**注意：**如果主機不使用 WCF 發送器 （服務主機），且會改為使用通道層級的程式設計，主應用程式應該接受**TransactedReceiveEnabled**屬性的 WCF 繫結，並應該讓所有在交易內 IInputChannel.Receive 呼叫。</span><span class="sxs-lookup"><span data-stu-id="985f0-115">**Note:**  If the host is not using the WCF dispatcher (service host) and is instead using channel level programming, the host should honor the **TransactedReceiveEnabled** property of the WCF binding, and should make all calls to IInputChannel.Receive within a transaction.</span></span> <span data-ttu-id="985f0-116">**注意：**如果配接器使用發送器起始交易，並使用與 Biztalk Server，設定`SupportedInboundChannels`屬性`SupportedInboundChannels.IInputChannel`表示配接器只支援單向通道。</span><span class="sxs-lookup"><span data-stu-id="985f0-116">**Note:**  If the adapter uses dispatcher-initiated transactions, and is used with Biztalk Server, set the `SupportedInboundChannels` property to `SupportedInboundChannels.IInputChannel` to indicate that the adapter only supports one-way channels.</span></span> <span data-ttu-id="985f0-117">如果未設定，BizTalk Server 會嘗試使用雙向通道。</span><span class="sxs-lookup"><span data-stu-id="985f0-117">If this is not set, BizTalk Server will attempt to use two-way channels.</span></span>|  
|<span data-ttu-id="985f0-118">False （配接器啟動）</span><span class="sxs-lookup"><span data-stu-id="985f0-118">False (adapter-initiated)</span></span>|<span data-ttu-id="985f0-119">-配接器開發人員必須實作配接器內的交易邏輯。</span><span class="sxs-lookup"><span data-stu-id="985f0-119">-   The adapter developer must implement transaction logic within the adapter.</span></span><br /><span data-ttu-id="985f0-120">配接器-起始交易只能使用雙向的訊息 （回覆通道） 模型。</span><span class="sxs-lookup"><span data-stu-id="985f0-120">-   Adapter-initiated transactions can only work with a two-way messaging (Reply Channel) model.</span></span><br /><span data-ttu-id="985f0-121">-一筆交易可以跨越多個訊息，因為每個訊息的發送器所建立相依的複製品。</span><span class="sxs-lookup"><span data-stu-id="985f0-121">-   One transaction can span multiple messages, since dependent clones will be created for each message by the dispatcher.</span></span>|  
  
### <a name="dispatcher-initiated-transactions"></a><span data-ttu-id="985f0-122">發送器起始的交易</span><span class="sxs-lookup"><span data-stu-id="985f0-122">Dispatcher-initiated Transactions</span></span>  
 <span data-ttu-id="985f0-123">SupportsTransactedInbound 當設定為**true**，WCF 發送器會再自動建立的交易時呼叫**TryReceive**方法的配接器，並將認可交易之後的訊息傳回到服務實作。</span><span class="sxs-lookup"><span data-stu-id="985f0-123">When SupportsTransactedInbound is set to **true**, the WCF dispatcher will then automatically create a transaction when calling the **TryReceive** method of the adapter, and will commit the transaction after the message is returned to the service implementation.</span></span> <span data-ttu-id="985f0-124">這不需要任何特定交易的程式碼中的實作配接器而設定`SupportsTransactedInbound`屬性**true**。</span><span class="sxs-lookup"><span data-stu-id="985f0-124">This does not require any specific transactional code implementation within the adapter other than setting the `SupportsTransactedInbound` property to **true**.</span></span> <span data-ttu-id="985f0-125">不過，這取決於配接器內使用 WCF 發送器，服務主機所裝載，而且將不會發生，如果您要使用通道層級的程式設計。</span><span class="sxs-lookup"><span data-stu-id="985f0-125">However, this is dependent on the adapter being hosted within a service host that uses the WCF dispatcher, and will not occur if you are using channel level programming.</span></span> <span data-ttu-id="985f0-126">當使用通道層級的程式設計時，主應用程式應該接受`TransactedReceiveEnabled`WCF 繫結，以及讓所有呼叫在交易中接收的屬性。</span><span class="sxs-lookup"><span data-stu-id="985f0-126">When using channel level programming, the host should honor the `TransactedReceiveEnabled` property of the WCF binding and make all calls to Receive within a transaction.</span></span>  
  
 <span data-ttu-id="985f0-127">下列示範建立交易，然後再呼叫 配接器使用通道層級程式設計的用戶端。</span><span class="sxs-lookup"><span data-stu-id="985f0-127">The following demonstrates a client creating a transaction, and then calling the adapter using channel level programming.</span></span>  
  
```csharp  
Message message;  
//Use a new TransactionScope  
using (System.Transactions.TransactionScope tx = new System.Transactions.TransactionScope())  
{  
    message = channel.Receive(TimeSpan.FromMinutes(2));  
    tx.Complete();  
}  
```  
  
### <a name="adapter-initiated-transactions"></a><span data-ttu-id="985f0-128">配接器起始的交易</span><span class="sxs-lookup"><span data-stu-id="985f0-128">Adapter-initiated Transactions</span></span>  
 <span data-ttu-id="985f0-129">當`SupportsTransactedInbound`屬性設定為**false**，必須藉由建立新的交易配接器程式碼中實作交易支援。</span><span class="sxs-lookup"><span data-stu-id="985f0-129">When hte `SupportsTransactedInbound` property is set to **false**, transaction support must be implemented within the adapter code by creating a new transaction.</span></span> <span data-ttu-id="985f0-130">傳回從訊息之前**TryReceive**，交易必須附加至訊息，藉由呼叫**設定**方法**TransactionMessageProperty**類別。</span><span class="sxs-lookup"><span data-stu-id="985f0-130">Before returning a message from **TryReceive**, the transaction must be attached to the message by calling the **Set** method of the **TransactionMessageProperty** class.</span></span> <span data-ttu-id="985f0-131">這個實作需要配接器程式碼中的外顯交易支援，並提供更好的控制，透過交易式配接器的行為。</span><span class="sxs-lookup"><span data-stu-id="985f0-131">This implementation requires explicit transaction support in the adapter code, and provides greater control over the transactional behavior of the adapter.</span></span>  
  
 <span data-ttu-id="985f0-132">下列示範如何建立相依的交易，並將此附加到訊息，再傳回給用戶端。</span><span class="sxs-lookup"><span data-stu-id="985f0-132">The following demonstrates creating a dependent transaction, and attaching this to the message before it is returned to the client.</span></span>  
  
```csharp  
  
Transaction transaction = inboundConnection.CurrentTransaction; //Existing transaction  
DependentTransaction dt = transaction.DependentClone(DependentCloneOption.BlockCommitUntilComplete);  
TransactionMessageProperty.Set(dt, message);  
inboundReply.DependentTransaction = dt; //this will later be closed during Reply processing  
```  
  
## <a name="see-also"></a><span data-ttu-id="985f0-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="985f0-133">See Also</span></span>  
 [<span data-ttu-id="985f0-134">開發活動</span><span class="sxs-lookup"><span data-stu-id="985f0-134">Development Activities</span></span>](../../esb-toolkit/development-activities.md)