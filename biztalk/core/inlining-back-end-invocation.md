---
title: "內嵌後端引動過程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MessageBox database, performance
- service solution tutorial, performance
- performance, in-line invocation
- Inline Invocation of Back-End Processes [service solutions], performance
- performance, MessageBox database
ms.assetid: 991d080f-a4cc-4f14-bab3-3b8b74636daf
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7300429e9f74abc7bc10569c653bdaa0a4c13b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="inlining-back-end-invocation"></a>內嵌後端叫用
完整解決方案的內嵌呼叫版本可提供最快速的處理次數。 內嵌版本消除了對 MessageBox 資料庫中後端系統持續傳送要求及取得回應的負擔。 在配接器版本中，訊息會從傳送協調流程到 MessageBox。 執行配接器的主控件會取出訊息，並透過訊息再次發佈到 MessageBox 的方式，將訊息傳送到後端程序。  
  
 內嵌的效率會犧牲協調流程直接與後端系統傳輸通訊協定的繫結。 在內嵌版本中，協調流程不是透過邏輯連接埠進行通訊，而是透過三個自訂組件呼叫後端系統。 若後端系統傳輸變更，則必須重新撰寫並重新編譯組件。 下表描述組件及其功能：  
  
|組件名稱|後端連接|  
|-------------------|--------------------------|  
|Microsoft.Samples.BizTalk.WoodgroveBank.PaymentTrackerCall|使用 MQSeries**取得**和**放**訊息功能。|  
|Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactionsCall|叫用交易系統的 Web 服務。|  
|Microsoft.Samples.BizTalk.WoodgroveBank.SAPCall|呼叫模擬 SAP 的 Web 服務。|  
  
## <a name="see-also"></a>另請參閱  
 [實作會反白顯示的服務導向解決方案](../core/implementation-highlights-of-the-service-oriented-solution.md)   
 [開發服務導向解決方案](../core/developing-a-service-oriented-solution.md)   
 [轉譯模式的服務導向解決方案](../core/translating-the-patterns-of-the-service-oriented-solution.md)   
 [監控服務導向 BAM 解決方案](../core/monitoring-the-service-oriented-solution-with-bam.md)