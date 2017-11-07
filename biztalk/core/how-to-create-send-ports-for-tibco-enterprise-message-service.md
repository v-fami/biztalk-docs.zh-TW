---
redirect_url: /biztalk/core/creating-tibco-enterprise-message-service-send-handlers/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 6b15d9d03ef967bcf7189ef756da8fc63a0eb3f6
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-create-send-ports-for-tibco-enterprise-message-service"></a>如何建立 TIBCO Enterprise Message Service 的傳送埠
依照下列步驟建立傳送埠。  
  
## <a name="creating-a-send-port"></a>建立傳送埠  
  
#### <a name="to-create-a-send-port"></a>建立傳送埠  
  
1.  在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 所需應用程式。  
  
2.  以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態請求-回應傳送埠**。  
  
3.  在**傳送埠屬性**對話方塊方塊中，執行下列動作：  
  
    1.  輸入傳送埠名稱，例如`SendToTIBCOEMS`。  
  
    2.  從**類型**下拉式清單中，選取**TIBCO EMS**。  
  
    3.  從**傳送處理常式**下拉式清單中，選取 URI。  
  
    4.  從 傳送管線 下拉式清單中，選取  **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**。  
  
    5.  從**接收管線**下拉式清單中，選取**[microsoft.biztalk.defaultpiplelines.xmlreceive]**。  
  
    6.  按一下**設定**以設定傳送埠。  
  
4.  在**TIBCO EMS 傳輸屬性**對話方塊方塊中，執行下列動作：  
  
    1.  輸入**訊息處理**，**伺服器連線定義**，**交易支援**， **Username**，而**密碼**。  
  
         您不需要設定登入資訊。  
  
    2.  在此清單中，選取您建立用來代表 TIBCO EMS 系統的分支機構應用程式。  
  
    3.  如**使用 SSO**，選取**是**。  
  
    4.  按一下 **[確定]**。  
  
5.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
  [建立 TIBCO Enterprise Message Service 傳送處理常式](../core/creating-tibco-enterprise-message-service-send-handlers.md)