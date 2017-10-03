---
title: "交易式批次支援接收配接器介面 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5289e8b8-4447-4196-9f7c-5e60c6598d8d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27b51a67f63f3088ce64c9db35c368289ce156d2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="interfaces-for-a-transactional-batch-supported-receive-adapter"></a>支援交易式批次的接收配接器介面
接收配接器可以在需要交易式的訊息提交時建立及控制交易。  
  
 交易式接收配接器建立，並將指標傳遞至 Microsoft Distributed Transaction Coordinator (MSDTC) 交易，**完成**方法**IBTTransportBatch**介面。 這樣可確保所有的批次作業都在特定交易物件的範圍中執行。 當批次提交完成時，配接器回呼方法便會認可或復原交易。 配接器所採取的動作取決於從傳輸 Proxy 傳回的狀態，並可能由配接器所進行的其他交易相關工作 (傳輸 Proxy 看不到) 決定。 配接器會決定交易為失敗或成功。 配接器報告交易 （commit 或 rollback） 的結果傳回給傳輸 proxy 使用**DTCCommitConfirm**方法**IBTDTCCommitConfirm**介面。 配接器會對成功的交易傳入 `true`，或是對失敗傳入 `false`。  
  
 下圖顯示在建立支援交易式批次的接收配接器時所牽涉的物件互動。  
  
 ![](../core/media/ebiz-sdk-devadapter2.gif "ebiz_sdk_devadapter2")  
使用 DCT 交易之接收配接器提交訊息批次的工作流程  
  
## <a name="see-also"></a>另請參閱  
 [配接器變數](../core/adapter-variables.md)   
 [開發接收配接器](../core/developing-a-receive-adapter.md)   
 [具現化，並初始化接收配接器](../core/instantiating-and-initializing-a-receive-adapter.md)   
 [介面的內含式接收配接器](../core/interfaces-for-an-in-process-receive-adapter.md)   
 [介面的外掛式接收配接器](../core/interfaces-for-an-isolated-receive-adapter.md)   
 [接收配接器批次支援的介面](../core/interfaces-for-a-batch-supported-receive-adapter.md)   
 [接收配接器同步要求-回應的介面](../core/interfaces-for-a-synchronous-request-response-receive-adapter.md)