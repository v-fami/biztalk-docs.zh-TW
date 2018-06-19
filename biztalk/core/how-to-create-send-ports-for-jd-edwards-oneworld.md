---
redirect_url: /biztalk/core/adding-biztalk-adapter-for-jd-edwards-oneworld/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: d65b87fbcbdaf89289406ae6850b70c605123451
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24015566"
---
# <a name="how-to-create-send-ports-for-jd-edwards-oneworld"></a>如何建立 JD Edwards OneWorld 的傳送埠
使用下列程序來建立傳送埠。  
  
### <a name="to-create-a-send-port"></a>建立傳送埠  
  
1.  在 BizTalk Server 管理主控台中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後瀏覽至必要的應用程式。  
  
2.  以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態請求-回應傳送埠**。  
  
    > [!NOTE]
    >  您也可以使用**靜態單向連接埠**。  
  
3.  在**傳送埠屬性**對話方塊中，於**名稱**欄位中，輸入傳送埠名稱 (例如，輸入**SendToJDE**。)  
  
4.  在**類型**下拉式清單中，選取 **[jdeoneworld]**。  
  
5.  在**URI**下拉式清單中，選取傳送處理常式。  
  
6.  按一下 **[確定]**。  
  
