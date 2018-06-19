---
redirect_url: /biztalk/core/installing-biztalk-adapter-for-tibco-rendezvous/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: bcccc92430a73685ced9ad7259d8ec57dfc450b8
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24013229"
---
# <a name="tibco-rendezvous-limitations"></a>TIBCO Rendezvous 限制
在 TIBCO Rendezvous 中，並不保證欄位名稱是唯一的。 如果 TIBCO Rendezvous 訊息包含兩個相同的欄位名稱，結果產生的 XML 會無效。  
  
 其他限制還包括：  
  
-   不會提供欄位排序。  
  
-   根據 TIBCO Rendezvous 文件，不可列印的字元不會使用在主體名稱中，但是，仍有使用這類字元的可能。 BizTalk Adapter for TIBCO Rendezvous 不支援含有這些字元的主體名稱。  
  
-   不支援對精靈的安全連線。  
  
-   不支援自訂資料型別。  
  
-   傳輸端不支援「認證傳訊」。  
  
## <a name="see-also"></a>另請參閱  
 [TIBCO Rendezvous 概念](../core/tibco-rendezvous-concepts.md)   
 [快速入門](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)