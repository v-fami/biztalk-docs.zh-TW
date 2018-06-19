---
redirect_url: /biztalk/core/adding-biztalk-adapter-for-jd-edwards-enterpriseone/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: fe877aa8c7b76a638df93a073eed0cf26f71a609
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24013277"
---
# <a name="how-to-create-send-ports-for-jd-edwards-enterpriseone"></a>如何建立 JD Edwards EnterpriseOne 的傳送埠
使用 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 建立傳送埠。  
  
### <a name="to-create-a-send-port"></a>建立傳送埠  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft BizTalk Server**，然後按一下  **BizTalk Server 管理**。  
  
2.  在 BizTalk Server 管理主控台中，展開  **BizTalk Server 管理**，依序展開**BizTalk 群組**，並展開**應用程式**，然後展開您要建立傳送埠的應用程式。  
  
3.  以滑鼠右鍵按一下**傳送埠**按一下**新增**，然後按一下 **靜態請求-回應連接埠**。  
  
4.  在**傳送埠屬性**對話方塊方塊中，執行下列動作：  
  
    -   在**名稱**方塊中，輸入傳送埠名稱 (例如， `SendToJDE`)。  
  
    -   從**類型**下拉式清單中，選取**JDEdwards**。  
  
    -   從**傳送處理常式**下拉式清單中，選取傳送處理常式位址。  
  
5.  按一下 **[確定]**。  
  
