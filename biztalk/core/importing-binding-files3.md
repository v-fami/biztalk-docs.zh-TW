---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-jd-edwards-oneworld/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: 5c5cce40f3fbeb580ec7ba854d02cb243e1742b4
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24013461"
---
# <a name="importing-binding-files"></a>匯入繫結檔案

## <a name="overview"></a>概觀
使用 BizTalk Server 匯入繫結檔案之前，請確認下列項目：  
  
-   CLASSPATH 指向 JD Edwards 專屬檔案的特定位置。 確認這些檔案的位置在新電腦上是相同的，否則請編輯繫結檔案。  
  
-   在新電腦上用於存放回應的資料夾存在且相同，否則請編輯繫結檔案。  
  
-   JD Edwards 系統密碼 (如果出現在組態中) 會以 ***** 格式儲存在繫結檔案中。 
  
> [!NOTE]
>  部署會覆寫接收位置組態。 在目標電腦上部署繫結檔案 (和組件) 時，傳送埠和接收位置會在匯入時被取代為 XML 繫結檔案中的傳送埠和接收位置。  
  
## <a name="import-the-binding-files"></a>匯入繫結檔案  
  
1.  上**啟動**功能表上，指向**Program Files**，指向  **Microsoft BizTalk Server**，然後按一下  **BizTalk Server 管理**啟動 BizTalk Server 管理主控台。  
  
2.  依序展開 BizTalk Server 管理**BizTalk 群組**，然後展開**應用程式**。  
  
3.  以滑鼠右鍵按一下所需的應用程式，指向**匯入**，然後按一下 **繫結**。  
  
4.  在**匯入繫結**對話方塊中，瀏覽並選取繫結檔案，然後按一下**開啟**。  
  
## <a name="cleaning-the-target-computer"></a>清除目標電腦  
移除傳送埠和接收位置繫結至協調流程。  
  
## <a name="see-also"></a>另請參閱  
 [將成品新增至 BizTalk 管理](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md)   
 [匯入 JD Edwards OneWorld 應用程式](deploying-biztalk-adapter-for-jd-edwards-oneworld.md)