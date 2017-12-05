---
title: "交易處理與 MSMQ 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, transaction handling
- transactions, MSMQ adapters
ms.assetid: 2e5dd0da-3852-48bf-9372-b019ecab23be
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1bea79413042ec99cfd1cbc5bc6dee500aef4ac4
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="transaction-handling-with-the-msmq-adapter"></a>交易處理與 MSMQ 配接器
本節將討論交易如何接收和傳送。  
  
> [!NOTE]
>  若是 MSMQ 配接器，即使您使用的是遠端佇列，交易還是會從 BizTalk MessageBox 資料庫擴充到本機「訊息佇列」佇列。  
  
 您可以透過 MSMQ 配接器，在傳送和接收中使用交易。 在交易傳送上，配接器會累計訊息，直到有完整批次為止。 然後配接器會將批次提交給本機「訊息佇列」服務，以做為單一交易。 若提交失敗，則配接器會嘗試重新提交批次。 若重新提交失敗，配接器會移動到次要傳輸。  
  
> [!NOTE]
>  配接器支援與訊息佇列 4.0 或更新版本的遠端佇列的交易式讀取。 在此案例中 BizTalk Server 和遠端的訊息佇列伺服器必須執行訊息佇列 4.0 或更新版本。  
  
 在交易接收上，配接器會擱置失敗的訊息，因此它不會遺失任何訊息。 在交易接收期間，配接器會將訊息新增到批次，直到批次完成。 然後提交批次：  
  
-   若沒有問題，且伺服器接收到訊息，則配接器會認同交易。  
  
-   若有問題，配接器會建立新的批次，以做為目前交易的一部分。 然後將任何有問題的訊息移動到新的批次。 接著重新提交第一個批次，並將新的批次以擱置的訊息提交。 若在此重新提交期間沒有任何問題，則配接器會認同交易。  
  
 若您在叢集式 BizTalk 主控件執行個體中執行 MSMQ 配接器傳送處理常式，應該要將相同叢集群組中的 MSMQ 服務叢集起來，以確保交易一致性。  
  
 「 網路 DTC 存取 」 已停用 DCOMCNFG 公用程式中，MSMQ 交易式遠端接收作業會失敗並語意不明的錯誤訊息。  若要執行交易式遠端接收與 MSMQ 配接器，必須啟用 「 網路 DTC 存取 」。 詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=124623](http://go.microsoft.com/fwlink/?LinkId=124623)。  
  
 若您在叢集式 BizTalk 主控件執行個體中執行 MSMQ 配接器接收處理常式，則應該將相同叢集群組中的 MSMQ 服務叢集起來，以支援本機交易讀取，因為 MSMQ 不支援遠端交易讀取。 如需有關如何在叢集 BizTalk 主控件執行個體中執行 MSMQ 配接器處理常式的詳細資訊，請參閱[叢集主控件中執行配接器處理常式的考量](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)。  
  
## <a name="see-also"></a>請參閱  
 [使用 MSMQ 配接器的可靠傳訊](../core/reliable-messaging-with-the-msmq-adapter.md)