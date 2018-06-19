---
redirect_url: /biztalk/core/using-tibco-rendezvous-send-ports-from-biztalk-server/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: d4a4f4fce200089db0e29d09b3ea49af00f3792f
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24014493"
---
# <a name="using-biztalk-server-from-tibco-rendezvous-to-send-messages"></a>從 TIBCO Rendezvous 使用 BizTalk Server 傳送訊息
Microsoft BizTalk Adapter for TIBCO Rendezvous 使用非同步 API (Transport.Send)。 您可以使用訊息內容屬性指定配接器傳送的訊息種類：  
  
-   **結構化**: 配接器會產生 TIBRVMSG_MSG 結構化的訊息時，根據從 BizTalk Server 接收的 XML 資料。 (*)  
  
 如果 BizTalk Server 傳送的訊息中有欄位名稱超過 127 個字元，BizTalk Adapter for TIBCO Rendezvous 會將名稱截斷至 TIBCO Rendezvous 的欄位名稱大小上限 (即 127)。  
  
 如果提供 `reply subject name` 屬性，會用來設定 TIBCO Rendezvous 訊息的回覆主旨。 這是假設接收埠設為接聽回覆並將它轉寄至 BizTalk Server，或一些其他的 TIBCO Rendezvous 程式會處理回覆。  
  
 服務、精靈與網路這三者構成傳輸組態。 傳輸組態空白 (預設值) 時，則會透過預設的傳輸物件傳送訊息。  
  
 如果未指定字碼頁，配接器會使用 UTF-8 編碼 (字碼頁 65001)。 傳輸器端不支援認證訊息。  
  
## <a name="see-also"></a>另請參閱  
 [TIBCO Rendezvous 概念](../core/tibco-rendezvous-concepts.md)   
 [建立 TIBCO Rendezvous 傳送處理常式](../core/creating-tibco-rendezvous-send-handlers.md)