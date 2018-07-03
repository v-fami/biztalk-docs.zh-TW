---
title: 使用 TIBCO Rendezvous 傳送埠從 BizTalk Server |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 34e3edf7-cfc5-4c89-8069-63e8784bc9f9
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 393006fdcb02f84b14e63646acec134a72c68cd6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011703"
---
# <a name="using-tibco-rendezvous-send-ports"></a>使用 TIBCO Rendezvous 傳送埠
傳輸埠可傳送任何種類的訊息。 當 BizTalk Server 透過 Microsoft BizTalk Adapter for TIBCO Rendezvous 傳送訊息時，配接器會依據訊息內容屬性值產生訊息，或是使用預設值並傳送到指定的主體。  
  
> [!NOTE]
>  依據 TIBCO Rendezvous 文件，不得在傳輸主體名稱中使用萬用字元。  
  
## <a name="message-handling"></a>訊息處理  
 配接器會維護狀態，並依據該狀態處理內送的 BizTalk Server 訊息。  
  
-   如果訊息因為傳輸失敗而無法傳送，會指示 BizTalk Server 稍後重新提交。  
  
-   如果訊息因為配接器仍在初始化而無法傳送，會將 BizTalk Server 訊息排入佇列。 如果初始化失敗，會指示 BizTalk Server 稍後重新提交。  
  
## <a name="message-generation"></a>訊息產生  
 使用傳輸配接器時，BizTalk Adapter for TIBCO Rendezvous 會忽略訊息目標命名空間與根元素。 如果配接器傳送訊息，會依原狀傳送內容。 如果配接器產生結構化的 TIBCO Rendezvous 訊息，則會忽略根元素的名稱 (訊息沒有名稱)。 在任何情況下，配接器在發佈訊息時均會使用內容屬性尋找要使用的主體。  
  
 如需詳細資訊，請參閱 < [BizTalk Server 訊息內容屬性 （傳送處理常式）](../core/biztalk-server-message-context-properties-send-handlers.md)並[Data Type Mapping for TIBCO Rendezvous 中的 接收處理常式](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md)。  

## <a name="using-biztalk-to-send-messages"></a>使用 BizTalk 傳送訊息
Microsoft BizTalk Adapter for TIBCO Rendezvous 使用非同步 API (Transport.Send)。 您可以使用訊息內容屬性指定配接器傳送的訊息種類：  
  
- **結構化**: 配接器會產生 TIBRVMSG_MSG 結構化的訊息，以從 BizTalk Server 接收的 XML 資料為依據。 (*)  
  
  如果 BizTalk Server 傳送的訊息中有欄位名稱超過 127 個字元，BizTalk Adapter for TIBCO Rendezvous 會將名稱截斷至 TIBCO Rendezvous 的欄位名稱大小上限 (即 127)。  
  
  如果提供 `reply subject name` 屬性，會用來設定 TIBCO Rendezvous 訊息的回覆主旨。 這是假設接收埠設為接聽回覆並將它轉寄至 BizTalk Server，或一些其他的 TIBCO Rendezvous 程式會處理回覆。  
  
  服務、精靈與網路這三者構成傳輸組態。 傳輸組態空白 (預設值) 時，則會透過預設的傳輸物件傳送訊息。  
  
  如果未指定字碼頁，配接器會使用 UTF-8 編碼 (字碼頁 65001)。 傳輸器端不支援認證訊息。  
  
## <a name="see-also"></a>另請參閱  
 [建立傳送埠](../core/creating-send-ports2.md)   
 [建立 TIBCO Rendezvous 傳送處理常式](../core/creating-tibco-rendezvous-send-handlers.md)