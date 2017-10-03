---
title: "使用 BizTalk 傳訊引擎 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, Messaging Engine
- adapters, TransportProxy object
- Messaging Engine, adapters
- Messaging Engine, architecture
- TransportProxy object
- Messaging Engine, how to
- architecture, Messaging Engine
- messages, Messaging Engine
ms.assetid: e6b6d1ec-38cd-4721-9673-ae40da003dec
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 701ed3e82eb75b98a948313a99bb4debc65a8cce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-biztalk-messaging-engine"></a>使用 BizTalk 傳訊引擎
下列圖表說明傳訊引擎的架構。 它顯示配接器收到訊息並將它提交至 BizTalk Server 的實例。  
  
 ![](../core/media/ebiz-prog-messaging1.gif "ebiz_prog_messaging1")  
傳訊引擎的架構  
  
 每個配接器都有自己的執行個體**TransportProxy**物件，它會使用與 「 傳訊引擎互動。 配接器會以批次方式在傳訊引擎上執行工作，並且以不可部分完成的方式處理。 批次是一個作業集合，其中包括 SubmitMessage、SuspendMessage 或 DeleteMessage。  
  
 下列是配接器提交訊息至傳訊引擎的實例之事件順序：  
  
1.  配接器建立新訊息並將資料流連接到訊息。  
  
2.  配接器從傳訊引擎取得新批次。  
  
3.  配接器會新增訊息至提交的批次。  
  
4.  該批次已認可且已經在傳訊引擎的執行緒集區中排入佇列。  
  
5.  傳訊引擎執行緒集區開始處理新批次。  
  
6.  在接收管線中處理訊息。  
  
7.  接收管線產生零或多個訊息。 若訊息未傳回任何錯誤，管線就可以取用訊息。 接收管線可以產生一個以上的訊息；這通常發生在解譯器元件將單一交換解譯為多個訊息的情況。 一般而言，接收管線會將提交到 XML 的訊息正規化。  
  
8.  若已設定對應，則會在對應工具中處理管線所產生的訊息。  
  
9. 訊息會發佈到訊息代理程式或發佈到 MessageBox 資料庫。  
  
10. 傳訊引擎會回呼配接器以通知它工作批次的結果。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [可復原交換處理](../core/recoverable-interchange-processing.md)  
  
-   [訊息的排序傳遞](../core/ordered-delivery-of-messages.md)  
  
-   [錯誤處理](../core/error-handling.md)  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 如何處理大型訊息](../core/how-biztalk-server-processes-large-messages.md)   
 [引擎效能特性](../core/engine-performance-characteristics.md)   
 [測量最大持續性引擎輸送量](../core/measuring-maximum-sustainable-engine-throughput.md)   
 [測量引擎 MST 的測試案例](../core/test-scenarios-for-measuring-mst-of-the-engine.md)   
 [使用 Microsoft BizTalk LoadGen 2007 工具](../core/using-the-microsoft-biztalk-loadgen-2007-tool.md)