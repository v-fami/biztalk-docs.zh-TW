---
title: 最佳化 MSMQ 配接器的效能 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, performance
- performance, MSMQ adapters
- configuring [MSMQ adapters], performance
ms.assetid: f8537ea8-a96e-4874-bcaf-cd1442a50bd4
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 729aaddba023d854d7ecfeb5644357f2383bc6b1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011583"
---
# <a name="optimizing-performance-of-the-msmq-adapter"></a>最佳化 MSMQ 配接器效能
MSMQ 配接器的最佳化在傳送端與接收端之間各有不同。 您可以藉由設定接收位置上的屬性，來控制接收端上的最佳化。 在傳送端上，您可以使用協調流程來控制最佳化。  
  
## <a name="receive-optimization"></a>接收最佳化  
 在接收端上，您可以讓配接器使用單一執行緒。 配接器是使用單一執行緒或多個執行緒的設定而定**排序的處理**上接收位置，如下所示的屬性：  
  
- 將屬性何時 **，則為 True**，配接器會在單一執行緒上運作。 這將限制配接器一次只能處理一個訊息並節省記憶體。 請注意，這實際上是設定**批次大小**為一 (1)，不論屬性表中指派給它的值。  
  
- 當**排序的處理**是**False**，配接器會執行多個執行緒，並可以處理多個訊息一次，因此可提升效能。  
  
  您必須設定**排序的處理**要 **，則為 True**如果您將在管理伺服器資源的費用，或訊息大小的數目可能會耗盡可用的記憶體。  
  
  您也可以藉由減少的值來控制記憶體使用量**批次大小**接收位置上。 批次大小越小，會在記憶體中保留的訊息就越少，因此會用到的記憶體也會比較少。  
  
  將傳送埠和接收位置放置在不同的電腦上，也可以減少記憶體的使用。  
  
## <a name="send-optimization"></a>傳送最佳化  
 在傳送端上，您可以使用範例協調流程來達成相等的單一訊息處理。 此範例會傳送單一訊息，然後等待傳送下一個訊息，直到它收到通知為止。 如需詳細資訊，請參閱 <<c0> [ 如何從程式碼建立 MSMQ 接收位置和傳送埠](../core/how-to-create-msmq-receive-locations-and-send-ports-from-code.md)。  
  
## <a name="remote-transactional-read-operations"></a>遠端交易讀取作業  
 與 BizTalk Server MSMQ 配接器都能讓從交易式 MSMQ 佇列的遠端讀取的作業。  這是因為 MSMQ 4.0 和更新版本支援遠端交易讀取的作業。  不過，交易式讀取的作業都是通常很慢的作業。 若要最佳化效能，則應該只在沒有其他選擇的情況下使用這類作業。  
  
## <a name="see-also"></a>另請參閱  
 [如何設定 MSMQ 接收位置](../core/how-to-configure-an-msmq-receive-location.md)   
 [如何設定 MSMQ 傳送埠](../core/how-to-configure-an-msmq-send-port.md)   
 [設定 MSMQ 配接器](../core/configuring-the-msmq-adapter.md)