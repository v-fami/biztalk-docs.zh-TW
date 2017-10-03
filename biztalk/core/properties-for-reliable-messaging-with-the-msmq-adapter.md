---
title: "使用 MSMQ 配接器的可信賴傳訊屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, properties
- queues, MSMQ adapters
- MSMQ adapters, dead letters
- queues, failures [MSMQ adapters]
- MSMQ adapters, impersonation
- MSMQ adapters, remote queues
- queues
- reliability, MSMQ adapters
- impersonation, MSMQ adapters
- MSMQ adapters, queue failures
- clustering, MSMQ adapters
- queues, remote
- MSMQ adapters, reliability
- MSMQ adapters, clustering
ms.assetid: 34bfe028-b2aa-4816-a437-3679d19dffb2
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49aebf12c86ae72d5dcb224d078c62afefcb8f46
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="properties-for-reliable-messaging-with-the-msmq-adapter"></a>使用 MSMQ 配接器的可信賴傳訊屬性
您可以藉由設定 MSMQ 配接器的方式來改善以 MSMQ 配接器傳送和接收訊息的可靠性。 本主題討論使用幾個組態屬性以進行可靠傳訊。  
  
## <a name="running-msmq-adapter-handlers-within-a-clustered-biztalk-host"></a>在叢集 BizTalk 主控件中執行 MSMQ 配接器處理常式  
 達成高可用性的一個方法是在不同的 BizTalk Server 之多個主控件執行個體中，同時執行配接器處理常式。 不建議將此方法用於 MSMQ 配接器處理常式，因為 MSMQ 不支援遠端交易讀取，且因為 MSMQ 傳送處理常式會在本機執行的 MSMQ 服務執行個體上維持相依性。 若要提供 MSMQ 傳送和接收處理常式的高可用性，建議您在 BizTalk 主控件的叢集執行個體中執行 MSMQ 配接器。 如需詳細資訊，請參閱[叢集主控件中執行配接器處理常式的考量](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)。  
  
## <a name="queue-failure-and-the-dead-letter-queue"></a>佇列失敗與無法寄出的信件佇列  
 在成功傳送訊息之後，若停用或刪除接收佇列，則不會為後續訊息提示錯誤。 此狀況可能造成訊息遺失。  
  
 設定**使用寄不出信件佇列**組態屬性**True**可避免您遺失訊息。 當這個屬性為 `True` (預設) 時，佇列未接收的訊息會進入無法寄出的信件佇列中。  
  
## <a name="impersonation-and-remote-queues"></a>模擬與遠端佇列  
 您也必須設定**使用寄不出信件佇列**組態屬性**True**當您使用遠端佇列。 若 MSMQ 配接器模擬沒有使用遠端佇列的權限之使用者，則訊息可能會遺失。  
  
 若屬性是**True**模擬的使用者沒有使用遠端佇列的權限，本機或遠端電腦上的訊息會移至寄不出信件佇列。 在交易式傳送中，訊息會進入本機電腦之無法寄出的信件佇列。 在非交易式傳送中，訊息會進入遠端電腦之無法寄出的信件佇列。  
  
## <a name="recoverable-and-use-journal-queue-properties"></a>[可復原] 和 [使用日誌佇列] 屬性  
 這兩個**可修復**和**使用日誌佇列**屬性都會儲存傳送訊息的複本。 如需有關這些屬性的詳細資訊，請參閱[如何設定 MSMQ 接收位置](../core/how-to-configure-an-msmq-receive-location.md)和[如何設定 MSMQ 傳送埠](../core/how-to-configure-an-msmq-send-port.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 MSMQ 配接器的可信賴傳訊](../core/reliable-messaging-with-the-msmq-adapter.md)   
 [執行叢集主控件中的配接器處理常式的考量](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)