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
ms.openlocfilehash: 3172759541f46ec6c3c8c2b3e684086747036f37
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="ops-adapter-implementation-details"></a>Ops 配接器實作詳細資料
您會發現以程式設計方式修改或設定配接器時，瞭解 Ops 配接器的下列層面是非常有用的。  
  
> [!NOTE]
>  Ops 配接器是使用配接器架構所建置的。 建置配接器架構的相關資訊，請參閱[開發自訂配接器](../core/developing-custom-adapters.md)。  
  
## <a name="batch-processing"></a>批次處理  
 配接器一次處理一個訊息，因此每個訊息都是分開處理，而回復作業一次只針對一個訂單進行處理。 雖然配接器一次只處理一個訊息，但它會使用批次處理，以訊息的一個批次大小來處理訊息。 這可讓您更輕鬆地修改配接器處理批次中的訊息。  
  
## <a name="transaction-handling"></a>交易處理  
 配接器會使用由 Microsoft 提供的交易設施[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] **System.Transactions**設備。 配接器建立新**CommittableTransaction** ，並使用它與**TransactionScope**。 配接器呼叫**初始化**和**Execute**此交易內容中的方法。 呼叫的組件中的程式碼可以參與交易中使用**Transaction.Current**靜態方法來取得交易內容。 範例錯誤處理常式不會利用此功能。 如需有關**System.Transactions**，請參閱.NET Framework 類別庫版本中的 < System.Transactions 命名空間 >。  
  
## <a name="handling-data-other-than-error-reports"></a>處理錯誤報告以外的資料  
 在解決方案中，配接器會從新的錯誤報告功能來處理錯誤報告訊息。 不過，因為**Execute**方法採用位元組陣列做為其唯一的引數，所以不會特別限制可以傳遞至**Execute**方法。  
  
## <a name="using-the-adapter-when-creating-ports-programmatically"></a>以程式設計方式建立連接埠時使用配接器  
 您可以在從程式碼建立連接埠時指定配接器。 下表顯示自訂屬性名稱以及它們如何對應到顯示名稱。  
  
|傳送自訂屬性名稱|顯示名稱|  
|-------------------------------|------------------|  
|**DotNetAssemblyStrongName**|**DotNetAssemblyStrongName**|  
|**DotNetClassName**|**DotNetClassName**|  
|**InitializationData**|**InitializationData**|  
|**TransportLocationUri**|不適用。|  
  
 所有屬性均為字串值。 您可以從組件名稱和類別名稱建構 TransportLocationUri 屬性的值。 URI 具有 OPS 的值: / /\<DotNetAssemblyStrongName\>/\<DotNetClassName\>其中預留位置會取代對應的自訂屬性的值。  
  
 從程式碼建立連接埠的詳細資訊，請參閱[如何建立 MSMQ 接收位置和傳送埠的程式碼](../core/how-to-create-msmq-receive-locations-and-send-ports-from-code.md)。  
  
## <a name="see-also"></a>請參閱  
 [Ops 配接器](../core/the-ops-adapter.md)