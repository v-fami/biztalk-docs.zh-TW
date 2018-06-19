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
# <a name="custom-exceptions"></a>自訂例外狀況
出現無法復原的錯誤時，「商務程序管理」解決方案會使用例外狀況處理常式搭配自訂例外狀況。  
  
## <a name="handling-exceptions"></a>處理例外狀況  
 而不是使用**Terminate**呼叫的協調流程中的圖形，您可以使用擲回例外狀況由根協調流程處理模式。 如此可讓具有最廣內容範圍的協調流程做出處理例外狀況的決定。 讓附屬協調流程擲回自訂例外狀況可讓您與根協調流程交流更明確的資訊。  
  
 商務程序管理解決方案遵循此模式。 有四個根，或在方案中的使用未呼叫，協調流程： **OrderBroker**， **OrderManager**， **CableOrder1**，和**CableOrder2**. 三個根協調流程接收和處理自訂例外狀況： **OrderManager**， **CableOrder1**，和**CableOrder2**。  
  
 請注意，某些根協調流程使用**Terminate**圖形，且該**Terminate** 」 圖形會顯示一般結束點的協調流程之前。 協調流程仍會使用**Terminate**圖形發生錯誤時，讓協調流程會記錄為已終止，而不是已完成但有錯誤訊息。 這種方式可讓解決方案除了記錄錯誤外，也能輕鬆地追蹤失敗的執行個體。  
  
 如需有關**Terminate**圖形，請參閱[如何設定終止圖形](../core/how-to-configure-the-terminate-shape.md)。 如需有關**ThrowException**圖形，請參閱[如何設定擲回例外狀況圖形](../core/how-to-configure-the-throw-exception-shape.md)。  
  
## <a name="the-custom-exceptions"></a>自訂例外狀況  
 下列三種自訂例外狀況都是遵循相同的模式。 擁有不同的類型可讓程式碼分辨不同的例外狀況。  
  
|Exception|擲回 (協調流程)|  
|---------------|---------------------------------|  
|**ActivateException**|**變更**|  
|**CableOrderException**|**啟動**， **CableOrder1**|  
|**InterruptException**|**CableOrder1**， **CheckInterrupt**， **ErrorHandlerOrch**|  
  
 所有的自訂例外狀況都定義在**公用程式**組件。 自訂例外狀況都是 .NET 類別。 所有的自訂例外狀況類別繼承自.NET **ApplicationException**類別繼承自該類別**System.Exception**類別。 由於例外狀況可以凍結 (序列化並儲存於資料庫)，因此例外狀況必須實作還原序列化建構函式。 還原序列化建構函式會採用兩個引數的建構函式： SerializationInfo 物件和一個 StreamingContext 物件。 此還原序列化建構函式將用於例外狀況的解除凍結期間。 因為**ApplicationException**類別已經實作還原序列化建構函式、 自訂例外狀況的建構函式只會叫用的基底 (ApplicationException) 還原序列化建構函式。 例如， **InterruptException**包含下列建構函式：  
  
```  
// "info" is the object holding the serialized object data.  
// "context" is the contextual information about the source  
// or destination.  
public InterruptException(SerializationInfo info,  
                  StreamingContext context) : base(info, context) { }  
```  
  
 如需有關自訂序列化的詳細資訊，請參閱《[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] 開發人員手冊》中的＜自訂序列化＞。  
  
## <a name="nested-exception-handlers-and-compensation-blocks"></a>巢狀例外狀況處理常式和補償區塊  
 自訂例外狀況除了可以做為特製化例外狀況之外，在某些地方也做為排序旗標。 在**變更**協調流程中，取消作業必須復原的兩個地方。  
  
> [!NOTE]
>  您可能想要閱讀本節**變更**Visual Studio 中開啟協調流程。  
  
 頂端的協調流程中，如果呼叫**取消**協調流程失敗， **CancelCompensation**區塊會執行並回復**取消**交易。 如果一切順利，協調流程接著會呼叫**Activate**協調流程。  
  
 如果**Activate**作業將會失敗，**取消**必須也會回復交易。 不過，若要呼叫的例外狀況處理常式**Activate**不會知道**取消**交易。 若要處理這種情形，有適用整個協調流程的例外狀況處理常式。 這個處理常式，因為它包含**取消**範圍，知道**取消**交易。 處理常式會攔截擲回的例外狀況**Activate**範圍 ( **ActivateException**)，回復**取消**交易，然後擲回的例外狀況如此一來協調流程呼叫**變更**協調流程可以執行任何額外的處理。  
  
 請注意，此設計只補償**取消**如果**Activate**失敗。 如果**取消**失敗並擲回例外狀況，**取消**不會發生，所以不需要補償。  
  
 如需有關補償區塊和**補償**圖形，請參閱[如何設定補償圖形](../core/how-to-configure-the-compensate-shape.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在商務程序管理解決方案中處理的例外狀況](../core/exception-handling-in-the-business-process-management-solution.md)   
 [ExceptionHandler 協調流程](../core/the-exceptionhandler-orchestration.md)