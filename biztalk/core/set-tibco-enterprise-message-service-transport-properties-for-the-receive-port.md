---
redirect_url: /biztalk/core/creating-tibco-enterprise-message-service-receive-handlers/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 1a32564f9e0e9e81624b39ab0ba156e76b109497
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="setting-tibco-enterprise-message-service-transport-properties-for-the-receive-port"></a>設定 TIBCO 企業訊息服務接收埠的傳輸屬性
如 TIBCO Enterprise Message System (EMS) 接收位置， **URL**和**目標命名空間**至 TIBCO EMS 系統是所需的組態值。  
  
### <a name="to-specify-tibco-ems-transport-properties"></a>指定 TIBCO EMS 傳輸屬性  
  
1.  展開**系統定義**並輸入 TIBCO EMS 伺服器連線的所有必要的資訊。  
  
2.  展開**訊息處理**並輸入所有必要的資訊。  
  
    |參數|Description|  
    |---------------|-----------------|  
    |**訊息選取器**|只有在對目的地中的訊息評估此字串得到 True 時，才會接收訊息。<br /><br /> 允許接收埠只接收內部標頭屬性與此欄位所述運算式相符的訊息。<br /><br /> 訊息選取器的語法是以 SQL92 條件運算式語法的子集為基礎。 TIBCO EMS 使用者指南含有此語法的完整說明。<br /><br /> 例如，如果訊息中包含名為 NewsType 的標頭屬性，則接收埠只能擷取屬於 Sports 或 Editorial 類型的訊息。|  
    |**重試計數**|傳輸的重試計數。 預設值為 0。|  
    |**重試間隔**|配接器進行重試之前所等候的時間。 預設值為五分鐘。|  
  
3.  展開**伺服器連線定義**並輸入所有必要的資訊。  
  
    |參數|Description|  
    |---------------|-----------------|  
    |**目的地**|必要設定。 定義目的地的名稱與類型。 使用下列格式定義佇列或主題：Queue[queue.name] 或 Topic[topic.name]。|  
    |**通訊埠編號**|TIBCO EMS 伺服器所收聽的連接埠。|  
    |**伺服器名稱**|必要設定。 裝載 TIBCO EMS 伺服器的系統名稱。|  
  
4.  提供使用單一登入 (SSO) 的認證。  
  
     有兩種方法可以用來存取 TIBCO EMS 系統。 您可以使用「認證」(使用者名稱與密碼參數) 或「單一登入」。  
  
    -   選取**是**中**使用 SSO**使用單一登入。  
  
    -   在清單中選取分支機構應用程式。  
  
         由企業單一登入工具所建立的分支機構應用程式代表如 TIBCO EMS 之類的應用程式。 Microsoft BizTalk Adapter for TIBCO EMS 會使用應用程式使用者的認證。 這些認證是針對所指定分支機構應用程式，從伺服器系統的 SSO 資料庫中擷取所得。  
  
         如需如何建立分支機構應用程式的詳細資訊，請參閱[建立分支機構應用程式](../core/creating-affiliate-applications5.md)。  
  
5.  展開**使用者認證**輸入**使用者名**和**密碼**來存取 TIBCO EMS 伺服器。  
  
    |參數|Description|  
    |---------------|-----------------|  
    |`Password`|用來與 TIBCO EMS 精靈通訊的使用者密碼。<br /><br /> 如果您未選取**使用 SSO**，您必須設定為 BizTalk Adapter for TIBCO EMS 才能與 TIBCO EMS 精靈通訊的認證參數。|  
    |`User Name`|用來與 TIBCO EMS 精靈通訊的使用者名稱。<br /><br /> 如果您未選取**使用 SSO**，您必須設定為 BizTalk Adapter for TIBCO EMS 才能與 TIBCO EMS 精靈通訊的認證參數。|  
  
6.  按一下**套用**，然後按一下 [**確定**。  
  
## <a name="see-also"></a>另請參閱  
  [建立 TIBCO Enterprise Message Service 接收處理常式](../core/creating-tibco-enterprise-message-service-receive-handlers.md)