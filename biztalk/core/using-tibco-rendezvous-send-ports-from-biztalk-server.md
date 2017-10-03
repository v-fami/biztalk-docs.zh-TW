---
title: "使用 TIBCO Rendezvous 傳送埠從 BizTalk Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, handling
- message handling
- BizTalk Server, using send ports from
- send ports, using from BizTalk Server
- messages, generating
ms.assetid: 34e3edf7-cfc5-4c89-8069-63e8784bc9f9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04e11657e8e15ac0739124178e85f0c7c5c0a70e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-tibco-rendezvous-send-ports-from-biztalk-server"></a>從 BizTalk Server 使用 TIBCO Rendezvous 傳送埠
傳輸埠可傳送任何種類的訊息。 當 BizTalk Server 透過 Microsoft BizTalk Adapter for TIBCO Rendezvous 傳送訊息時，配接器會依據訊息內容屬性值產生訊息，或是使用預設值並傳送到指定的主體。  
  
> [!NOTE]
>  依據 TIBCO Rendezvous 文件，不得在傳輸主體名稱中使用萬用字元。  
  
## <a name="message-handling"></a>訊息處理  
 配接器會維護狀態，並依據該狀態處理內送的 BizTalk Server 訊息。  
  
-   如果訊息因為傳輸失敗而無法傳送，會指示 BizTalk Server 稍後重新提交。  
  
-   如果訊息因為配接器仍在初始化而無法傳送，會將 BizTalk Server 訊息排入佇列。 如果初始化失敗，會指示 BizTalk Server 稍後重新提交。  
  
## <a name="message-generation"></a>訊息產生  
 使用傳輸配接器時，BizTalk Adapter for TIBCO Rendezvous 會忽略訊息目標命名空間與根元素。 如果配接器傳送訊息，會依原狀傳送內容。 如果配接器產生結構化的 TIBCO Rendezvous 訊息，則會忽略根元素的名稱 (訊息沒有名稱)。 在任何情況下，配接器在發佈訊息時均會使用內容屬性尋找要使用的主體。  
  
 如需詳細資訊，請參閱[BizTalk Server 訊息內容屬性 （傳送處理常式）](../core/biztalk-server-message-context-properties-send-handlers.md)和[Data Type Mapping for TIBCO Rendezvous 中的 接收處理常式](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md)。  
  
## <a name="see-also"></a>另請參閱  
 [建立傳送埠](../core/creating-send-ports2.md)   
 [建立 TIBCO Rendezvous 傳送處理常式](../core/creating-tibco-rendezvous-send-handlers.md)