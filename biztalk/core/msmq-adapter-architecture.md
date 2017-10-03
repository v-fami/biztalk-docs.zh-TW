---
title: "MSMQ 配接器架構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, MSMQ adapters
- MSMQ adapters, architecture
ms.assetid: acecc2a4-0670-487e-be39-28a24c8c3f16
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd314b6f835568b6336121478268b84381a288ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="msmq-adapter-architecture"></a>MSMQ 配接器架構
MSMQ 配接器讓您可以利用 Microsoft Message Queuing (也稱為 MSMQ) 功能，該功能在 BizTalk Server 中是無法使用的。  
  
## <a name="adapter-structure"></a>配接器結構  
 MSMQ 配接器和其他 BizTalk 配接器的結構相同，並且使用「配接器架構」。 它是由設計階段元件與執行階段元件所組成。 執行階段元件依序包含實作訊息傳輸的項目。  
  
 設計階段元件讓您設定傳送和接收的配接器屬性。  
  
 執行階段元件可以將訊息傳送到設計階段定義的佇列，或從指定的佇列接收訊息。 配接器執行階段與 BizTalk Server 應用程式在相同的程序中執行，而且不會在外掛式主控件中執行。  
  
 所有訊息處理都依靠本機「訊息佇列」服務，即使遠端佇列也一樣。 對於遠端佇列，配接器會將訊息送交本機「訊息佇列」服務。 接著，它會將訊息傳送到遠端佇列。  
  
 如需完整清單的傳送和接收組態屬性，請參閱[如何設定 MSMQ 傳送埠](../core/how-to-configure-an-msmq-send-port.md)和[如何設定 MSMQ 接收位置](../core/how-to-configure-an-msmq-receive-location.md)。  
  
 如需有關訊息佇列的詳細資訊，請參閱 Microsoft TechNet 文件庫中可用的下列主題：  
  
-   **訊息佇列設計指南**在[http://go.microsoft.com/fwlink/?LinkId=137080](http://go.microsoft.com/fwlink/?LinkId=137080)。  
  
-   **訊息佇列操作指南**在[http://go.microsoft.com/fwlink/?LinkId=137079](http://go.microsoft.com/fwlink/?LinkId=137079)。  
  
-   **訊息佇列疑難排解指南**在[http://go.microsoft.com/fwlink/?LinkId=137081](http://go.microsoft.com/fwlink/?LinkId=137081)。  
  
-   **訊息佇列技術參考**在[http://go.microsoft.com/fwlink/?LinkId=137082](http://go.microsoft.com/fwlink/?LinkId=137082)。  
  
## <a name="see-also"></a>另請參閱  
 [什麼是 MSMQ 配接器？](../core/what-is-the-msmq-adapter.md)