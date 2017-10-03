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
# <a name="configure-dispatcher-initiated-or-adapter-initiated-transactions-with-the-wcf-lob-adapter-sdk"></a>使用 WCF LOB 配接器 SDK 設定發送器起始或配接器起始交易
## <a name="inbound-transactions"></a>輸入的交易  
 有兩種方法的實作與輸入操作的交易： 發送器起始或配接器起始。 配接器的需求會指定應該使用哪一種方法。 值`SupportsTransactedInbound`屬性會指出您的配接器將實作哪一種交易。  
  
 下表比較發送器起始與配接器起始的交易。  
  
|SupportsTransactedInbound|交易式行為|  
|-------------------------------|----------------------------|  
|True （發送器啟動）|-TryReceive 一律會在交易內容中呼叫。<br />的之後的訊息傳回至服務實作，將會認可交易。<br />-新的交易將會建立每個 IInputChannel.Receive 呼叫。 跨多個跨越交易接收依存於服務主機，而不是配接器開發。 **注意：**如果主機不使用 WCF 發送器 （服務主機），且會改為使用通道層級的程式設計，主應用程式應該接受**TransactedReceiveEnabled**屬性的 WCF 繫結，並應該讓所有在交易內 IInputChannel.Receive 呼叫。 **注意：**如果配接器使用發送器起始交易，並使用與 Biztalk Server，設定`SupportedInboundChannels`屬性`SupportedInboundChannels.IInputChannel`表示配接器只支援單向通道。 如果未設定，BizTalk Server 會嘗試使用雙向通道。|  
|False （配接器啟動）|-配接器開發人員必須實作配接器內的交易邏輯。<br />配接器-起始交易只能使用雙向的訊息 （回覆通道） 模型。<br />-一筆交易可以跨越多個訊息，因為每個訊息的發送器所建立相依的複製品。|  
  
### <a name="dispatcher-initiated-transactions"></a>發送器起始的交易  
 SupportsTransactedInbound 當設定為**true**，WCF 發送器會再自動建立的交易時呼叫**TryReceive**方法的配接器，並將認可交易之後的訊息傳回到服務實作。 這不需要任何特定交易的程式碼中的實作配接器而設定`SupportsTransactedInbound`屬性**true**。 不過，這取決於配接器內使用 WCF 發送器，服務主機所裝載，而且將不會發生，如果您要使用通道層級的程式設計。 當使用通道層級的程式設計時，主應用程式應該接受`TransactedReceiveEnabled`WCF 繫結，以及讓所有呼叫在交易中接收的屬性。  
  
 下列示範建立交易，然後再呼叫 配接器使用通道層級程式設計的用戶端。  
  
```csharp  
Message message;  
//Use a new TransactionScope  
using (System.Transactions.TransactionScope tx = new System.Transactions.TransactionScope())  
{  
    message = channel.Receive(TimeSpan.FromMinutes(2));  
    tx.Complete();  
}  
```  
  
### <a name="adapter-initiated-transactions"></a>配接器起始的交易  
 當`SupportsTransactedInbound`屬性設定為**false**，必須藉由建立新的交易配接器程式碼中實作交易支援。 傳回從訊息之前**TryReceive**，交易必須附加至訊息，藉由呼叫**設定**方法**TransactionMessageProperty**類別。 這個實作需要配接器程式碼中的外顯交易支援，並提供更好的控制，透過交易式配接器的行為。  
  
 下列示範如何建立相依的交易，並將此附加到訊息，再傳回給用戶端。  
  
```csharp  
  
Transaction transaction = inboundConnection.CurrentTransaction; //Existing transaction  
DependentTransaction dt = transaction.DependentClone(DependentCloneOption.BlockCommitUntilComplete);  
TransactionMessageProperty.Set(dt, message);  
inboundReply.DependentTransaction = dt; //this will later be closed during Reply processing  
```  
  
## <a name="see-also"></a>另請參閱  
 [開發活動](../../esb-toolkit/development-activities.md)