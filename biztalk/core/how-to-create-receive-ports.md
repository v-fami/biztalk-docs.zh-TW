---
redirect_url: /biztalk/core/creating-tibco-rendezvous-receive-handlers/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: 0cd93bcd2d1855f137600214b6a07d52b6f52e4f
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24013317"
---
# <a name="how-to-create-receive-ports"></a>如何建立接收埠
請遵循下列步驟，使用 Visual Studio 建立接收埠。  
  
### <a name="to-create-a-receive-port"></a>建立接收埠  
  
1.  在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開 所需應用程式。  
  
2.  以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下 **單向接收埠**。  
  
3.  在**接收埠屬性**視窗，請在**一般**頁面上，執行下列動作：  
  
    1.  在**名稱**欄位中，輸入`ReceiveFromTIBCORV`。  
  
    2.  在**驗證**群組方塊中，指定使用驗證時，如何處理的訊息。  
  
    3.  選取**啟用的路由失敗訊息**核取方塊。  
  
4.  在**接收位置**頁面上，執行下列動作：  
  
    1.  按一下 **[新增]**。  
  
    2.  在**接收位置**視窗，請在**一般**頁面上，輸入**名稱**接收位置。  
  
    3.  從**類型**下拉式清單中，選取傳輸類型，以及從**接收處理常式**下拉式清單中，選取傳輸位址。  
  
    4.  從**接收管線**下拉式清單中，選取接收管線。  
  
    5.  在**排程**頁面上，選取**開始日期**和**結束日期**限制接收文件。  
  
    6.  選取**啟用服務窗口**核取方塊。  
  
    7.  按一下 **[確定]**。  
  
5.  在**輸入對應**頁面上，選取輸入的對應轉換文件上選取的連接埠。  
  
6.  在**追蹤**頁面上，選取所需的追蹤訊息內文和追蹤訊息屬性。  
  
7.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [建立 TIBCO Rendezvous 接收處理常式](../core/creating-tibco-rendezvous-receive-handlers.md)