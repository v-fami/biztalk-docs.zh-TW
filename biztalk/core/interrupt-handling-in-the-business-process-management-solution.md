---
title: 中斷商務程序管理解決方案中的處理 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- processing, pausing
- process management solution tutorial, pausing processing
ms.assetid: 23ce7617-f705-4b7d-8447-221dec9fb196
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78b98eae8ee9cbb43354c1cfc48710c70969a929
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257774"
---
# <a name="interrupt-handling-in-the-business-process-management-solution"></a>中斷商務程序管理解決方案中的處理
本節描述商務程序管理解決方案中的中斷處理機制。 使用中斷機制，可讓您在訂單更新或取消時，終止訂單處理。  
  
## <a name="interrupt-handling"></a>中斷處理  
 實作處理階段協調流程呼叫的協調流程， **CheckInterrupt**，以測試的程序的某些其他部分的中斷要求。 **CheckInterrupt**協調流程組成**接聽**圖形。 其中一個分支**接聽**圖形會檢查目前的順序相同的相互關聯識別碼的訊息。 如果沒有這類訊息**CheckInterrupt**協調流程傳送通知訊息，並執行**擲回**圖形。 因為在分支**接聽**圖形會執行從左到右，在右邊的分支會出現延遲。 請注意延遲是零 (0)。  
  
 組合**接聽**圖形、 接收分支及延遲分支讓協調流程能檢查訊息。 若有任何的中斷訊息，左邊的分支便會執行。 若沒有任何訊息，則右邊的分支會執行，並返回呼叫的協調流程。 中斷訊息是隨時都可傳送的。 因為**CheckInterrupt**只有有時候，可能會等候中斷訊息，協調流程會執行。  
  
 **OrderManager**藉由呼叫設定中斷**Interrupter**協調流程。 **Interrupter**協調流程傳送中斷訊息至**InterruptPort**並等待回覆。 協調流程使用**逾時**封入屬性**範圍**圖形，如果未接收到回覆，請重新啟動迴圈。 在未接收到回覆之前，只要超過了範圍時間，協調流程便會繼續傳送中斷訊息。 逾時表示要求已符合訂閱，但已無時間可等待回覆。 若有回覆，或如果沒有任何訂閱，迴圈結束**InterruptPort**。  
  
 要求-回應-完成模式**OrderManager**以處理階段是中斷處理很重要的一部分。 因為**OrderManager**等候回應-通知-從階段，即得知該階段已開始執行後再繼續。 這可確保階段不會在其開始之前便接收到中斷。 這也讓**OrderManager**知道，是否沒有任何中斷的訂閱，已完成階段。  
  
## <a name="see-also"></a>另請參閱  
 [商務程序管理解決方案中的處理](../core/processing-in-the-business-process-management-solution.md)   
 [程序管理員邏輯](../core/process-manager-logic.md)   
 [ExceptionHandler 協調流程](../core/the-exceptionhandler-orchestration.md)