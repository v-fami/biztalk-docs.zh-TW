---
title: "與接收訊息 」 圖形使用篩選器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filters, receive messages
- messages, filters
ms.assetid: 5310039b-6719-4971-933a-2da0573fb5e7
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1434e9704e073cfef1503ef550409e6d6414bb7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-filters-with-the-receive-message-shape"></a>使用篩選器與接收訊息 」 圖形
篩選條件運算式是選擇性的參數，可以套用至將 [啟動] 屬性指定為 True 值的協調流程接收圖形。. 如果有指定篩選條件運算式，協調流程便只會在內送訊息符合篩選條件運算式中指定的條件時啟動。 如果沒有指定篩選條件運算式，協調流程所訂閱的任何內送訊息都會啟動該協調流程。  
  
 若要建立篩選條件運算式，您可以比較運算式左邊的內送訊息屬性和運算式右邊的常數。 您也可以將 AND 和 OR 運算子套用至兩個或多個運算式，以便建立複合運算式。 您也可以將篩選條件運算式留白，在此情況下，便會接受所有的訊息。  
  
 篩選條件運算式可能會與下列相似：  
  
```  
InvoiceSchema.Quantity >= 1000  
```  
  
 在此範例中，會對協調流程展示內送訊息。 協調流程具有啟動**接收**圖形 (**啟用**屬性設定為**True**以便接收特定訊息會導致執行協調流程) 與先前套用的篩選條件運算式。 內送的訊息都應該要有命名空間中稱為 Quantity 的屬性**InvoiceSchema**。 協調流程只接受 1000 個以上項目的發票，因此執行階段引擎會在執行之前檢查內送訊息。  
  
 下表顯示您可以在篩選條件運算式中使用的運算子。  
  
|運算子|Description|範例|  
|--------------|-----------------|-------------|  
|==|等於|ReqMsg(Total) == 100|  
|!=|不等於|ReqMsg(Total) != 100|  
|<|小於|ReqMsg(Total) \< 100|  
|>|大於|ReqMsg(Total) > 100|  
|<=|小於或等於|ReqMsg(Total) \<= 100|  
|>=|大於或等於|ReqMsg(Total) > = 100|  
|exists|exists|ReqMsg(Description) exists|  
  
> [!NOTE]
>  在篩選條件運算式的字串值會以引號括住，例如： ReqMsg(Description) ="訂單狀態 」。 您無法在篩選條件運算式中使用字元值。  
  
> [!NOTE]
>  如果您的啟動接收與某個直接繫結連接埠關聯，而且後來針對篩選條件所測試的屬性，傳送具有相同值之相同類型的訊息，就會建立無限的迴圈。 該訊息會移至 MessageBox，並會因為符合篩選準則，而被再度收取。 若要避免這個問題，您應該針對不同的屬性篩選、傳送不同類型的訊息，或是確定在將相同類型的訊息傳送出去之前變更屬性的值。  
  
## <a name="see-also"></a>另請參閱  
 [如何設定 「 接收 」 圖形](../core/how-to-configure-the-receive-shape.md)   
 [協調流程中使用的相互關聯](../core/using-correlations-in-orchestrations.md)   
 [使用辨別的欄位和屬性欄位](../core/using-distinguished-fields-and-property-fields.md)   
 [協調流程中使用訊息](../core/using-messages-in-orchestrations.md)