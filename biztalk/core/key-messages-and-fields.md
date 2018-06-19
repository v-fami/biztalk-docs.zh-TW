---
title: 關鍵訊息和欄位 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- process management solution tutorial, processing
- processing, processing logic
ms.assetid: 77db0706-dfdc-48b0-8ca4-bae7ab2d7641
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 524b5f361495d9509809a9229362d28a18712239
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263926"
---
# <a name="key-messages-and-fields"></a>關鍵訊息和欄位
本節將簡短描述關鍵訊息和欄位由**OrderBroker**和**OrderManager**協調流程。 如需應用程式中的訊息的完整清單，請參閱[商務程序管理解決方案的訊息參考](../core/message-reference-for-the-business-process-management-solution.md)。  
  
## <a name="order-messages"></a>訂單訊息  
 訂單訊息**OrderBroker**為多部分訊息。 一部分包含路由資訊；另一部分則為訂單資訊。 定義路由訊息部分的 .NET 類別可讓它的所有欄位成為辨別欄位，如此協調流程便可存取做為訊息屬性的所有類別成員。 類別也包括路由類別中的升級欄位在內，因而能夠路由訊息。 所有升級欄位也是辨別欄位，因此能以較不複雜的註解進行設計程式和參考。  
  
 如需有關使用.NET 類別來定義訊息的詳細資訊，請參閱[使用者程式碼中的 建構訊息](../core/constructing-messages-in-user-code.md)。  
  
## <a name="identifying-orders"></a>識別訂單  
 解決方案使用路由資訊中的三個欄位來識別訂單。 這三個欄位中，兩個欄位會識別訂單： 訂單識別項 (**OrderID**) 和客戶識別碼 (**CustomerID**)。 雖然這兩個欄位可識別訂單，但是訂單可有一個以上的執行個體。 例如，客戶可能訂購新的標準網路安裝，而稍後又來電將訂單變更為訂購新的豪華網路安裝。 原始的訂單不大可能在更新訂單送達之前完成。 這便會使訂單產生兩個執行個體。  
  
 為了區分順序的執行個體之間，解決方案會使用唯一的訂單序號 (**SeqNum**)。 三個欄位**OrderID**， **CustomerID**，和**SeqNum**唯一識別某個訂單的執行個體。  
  
 最後，因為解決方案會使用遞增的數字**SeqNum**，方案可以區別原始訂單的更新，具有較高的更新**SeqNum**。  
  
> [!NOTE]
>  解決方案依賴系統建立訂單要求，以遞增將值指派給**SeqNum**。 請參閱輸入的 web 服務的 ASP 頁面背後的程式碼**CSRMainForm.aspx.cs**，並將要求轉換成訂單對應**CSR_OrderRequest_To_Order.btm**欄位的名稱牽涉到。  
  
## <a name="status"></a>狀態  
 **OrderBroker**， **OrderManager**，和其附屬協調流程會使用訂單訊息路由部分中的兩個欄位來追蹤狀態：**狀態**，和**階段**。 **狀態**欄位可追蹤訂單狀態。 下表描述的值**狀態**欄位。  
  
|值|設定之處|Description|  
|-----------|---------------|-----------------|  
|ACCEPTED|OrderBroker|訂單可繼續送往 OrderManager。|  
|COMPLETED|OrderManager|整份訂單處理完成，沒有發生錯誤。|  
|ERROR|OrderManager|偵測到訂單中有錯誤。|  
|ORDERMANAGER-EXCEPTION|OrderManager|處理訂單時，OrderManager 中發生例外狀況。|  
|STAGE_n_COMPLETED|OrderManager|指示已完成階段 n (其中 n 為數字)，沒有發生錯誤。|  
|STARTED|OrderManager|已開始處理訂單。|  
|TERMINATED|OrderManager|由於取消而停止處理訂單。|  
  
## <a name="stage"></a>階段  
 **OrderManager**使用**階段**欄位來表示訊息的處理階段的路由部分中。 此欄位在篩選條件中用來判定處理訊息的附屬協調流程。 **OrderManager**一開始設定**階段**為一 (1)。 當終止或完成，訂單**OrderManager**設定**階段**的協調流程變數，值**停止**。  
  
## <a name="requesttype"></a>RequestType  
 **OrderManager**也會使用**RequestType**訂單訊息的欄位。 若欄位值為 TERMINATE，便會終止該訂單。 協調流程會忽略所有其他的值**RequestType**欄位，並依賴訂單序號來辨識訂單更新和重複項目。 否則， **OrderBroker**設定**RequestType**欄位的值**狀態**從廠商或客戶服務系統訊息中的欄位。  
  
## <a name="ordertypecode-ordertype-and-serviceclass"></a>OrderTypeCode、OrderType 和 ServiceClass  
 順序的類型是在**OrderTypeCode**訂單訊息的欄位。 **OrderBroker**設定其值中的值為**OrdTypeCode**來自客戶服務系統或廠商系統的訊息中的欄位。 下表顯示可能的值為**OrderTypeCode**:  
  
|值|Description|  
|-----------|-----------------|  
|NS|新的標準網路安裝。|  
|ND|新的豪華網路安裝。|  
|XS|取消標準網路安裝。|  
|XD|取消豪華網路安裝。|  
|CS|變更標準網路安裝。|  
|CD|變更豪華網路安裝。|  
|UNKNOWN|未知。|  
  
 稍後，**驗證**協調流程會將這些值轉譯為兩個欄位，使用 「 商務規則引擎**OrderType**和**ServiceClass**。 **驗證**協調流程會呼叫第一個訂單處理階段**CableOrder1**。  
  
 下表提供的值**OrderType**:  
  
|OrderTypeCode 值|OrderType 值|  
|--------------------------|---------------------|  
|NS、ND|ACTIVATE|  
|XS、XD|CANCEL|  
|CS、CD|CHANGE|  
|組合無效。|INVALID|  
  
 值**ServiceClass**是對應的單一字母， **S**標準，或**D**的豪華 （deluxe)。  
  
## <a name="additional-identifiers"></a>其他識別碼  
 解決方案也使用識別碼以供每份訂單使用。 這個識別碼， **RequestId**，必須是唯一的所有訂單。 輸入 Web 服務會自動指派 GUID 給它。 透過批次輸入提交的訊息必須包含欄位的值。 此欄位是**RequestID**順序結構描述中。 **OrderBroker**，不過，會使用**CSR_OrderRequest**處理訂單的結構描述。 欄位會顯示為**ReqId**這個結構描述中而且是辨別的屬性。  
  
 解決方案會使用**RequestId**來形成用於 BAM 追蹤系統的活動識別項。  
  
## <a name="see-also"></a>另請參閱  
 [程序管理員邏輯](../core/process-manager-logic.md)   
 [透過處理序管理員的訂單流程](../core/order-flow-through-the-process-manager.md)   
 [使用者程式碼中建構的訊息](../core/constructing-messages-in-user-code.md)   
 [商務程序管理解決方案的訊息參考](../core/message-reference-for-the-business-process-management-solution.md)