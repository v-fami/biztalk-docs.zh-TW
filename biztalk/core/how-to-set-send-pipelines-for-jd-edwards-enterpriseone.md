---
redirect_url: /biztalk/core/adding-biztalk-adapter-for-jd-edwards-enterpriseone/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: 263f1f5d9441a30687df3e1a7a1170b7bf35e2fc
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24015069"
---
# <a name="how-to-set-send-pipelines-for-jd-edwards-enterpriseone"></a>如何設定 JD Edwards EnterpriseOne 的傳送管線
Microsoft BizTalk Adapter for JD Edwards EnterpriseOne 需要您選取**XMLTransmit**和**XMLReceive**傳送和接收管線分別。  
  
### <a name="to-set-pipelines"></a>設定管線  
  
1.  在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 所需應用程式。  
  
2.  以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態請求-回應傳送埠**。  
  
3.  在**傳送埠屬性**對話方塊方塊中，執行下列動作：  
  
    1.  輸入傳送埠名稱，例如`SendToJDEEnterpriseOne`。  
  
    2.  從**類型**下拉式清單中，選取**JDE EnterpriseOne**。  
  
    3.  從**傳送處理常式**下拉式清單中，選取 URI。  
  
    4.  從 傳送管線 下拉式清單中，選取  **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**。  
  
    5.  從**接收管線**下拉式清單中，選取 **[microsoft.biztalk.defaultpiplelines.xmlreceive]**。  
  
4.  按一下 **[確定]**。  
  
