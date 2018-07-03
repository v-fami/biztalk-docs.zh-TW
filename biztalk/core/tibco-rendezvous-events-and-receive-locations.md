---
redirect_url: /biztalk/core/creating-tibco-rendezvous-receive-handlers/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: 8fc76fb212d343bcafa67c5ea76f62899847b40e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984263"
---
# <a name="tibco-rendezvous-events-and-receive-locations"></a>TIBCO Rendezvous 事件與接收位置
所有 TIBCO Rendezvous 系統均可傳送訊息給它們選擇的主體名稱。 概念*事件*是新一代的其他 TIBCO Rendezvous 程式的訊息。  
  
 下列步驟說明接收位置的生命週期：  
  
1.  接收位置已建立。  
  
2.  接收位置已和主控件建立關聯。  
  
3.  接收位置已繫結到協調流程。  
  
4.  接收位置已啟用。  
  
5.  接收位置收到訊息。  
  
> [!IMPORTANT]
>  每個接收位置都必須有一個唯一的名稱。 在同一個 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 部署中，不能有兩個相同名稱的接收位置。  
> 
> [!IMPORTANT]
>  建議您在接收位置的放置位置中設定強式存取控制清單 (ACL)。 例如，您必須在檔案接收位置拾取訊息的目錄中設定強式 ACL，讓只有經過授權的使用者可以在此位置放置訊息。  
  
## <a name="see-also"></a>另請參閱  
 [建立 TIBCO Rendezvous 接收處理常式](../core/creating-tibco-rendezvous-receive-handlers.md)