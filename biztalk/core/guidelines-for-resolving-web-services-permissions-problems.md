---
title: 解決 Web 服務的權限問題的指導方針 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e29543e9-9b87-437b-ac91-8f1cce01fab4
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd4420cb7c651ae1ad1bbe4bcb318b86b59c9ac4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005311"
---
# <a name="guidelines-for-resolving-web-services-permissions-problems"></a>解決 Web 服務權限問題的指導方針
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在使用 SOAP 配接器以及將協調流程發佈為 Web 服務時，均大量使用 Web 服務。 本主題包含一些一般指導方針，可用來儘可能減少 Web 服務的權限問題，另外也包含疑難排解步驟，可用於解決對 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 造成影響的 Web 服務權限的問題。  
  
## <a name="general-guidelines"></a>一般指導方針  
  
- **設定使用者帳戶**： 確保與裝載 Web 服務的虛擬目錄相關聯的 IIS 應用程式主機處理序識別設為特定使用者帳戶，並確保此使用者帳戶會新增到下列群組：  
  
  - BizTalk 外掛式主控件使用者 (網域或本機群組)  
  
  - IIS_WPG (本機群組)  
  
    必須具有這 2 個群組中的成員資格，才能對 BizTalk Web 服務發佈精靈所建立的 Web 服務授與適當的權限，使其可以將 SOAP 要求訊息發佈到 BizTalk MessageBox 資料庫 (此資料庫會啟動定閱協調流程)。 如需決定或設定 IIS 應用程式主機處理序識別的詳細資訊，請參閱**設定 IIS 應用程式主機處理序身分識別**一節[解決 IIS 權限問題指導方針](../core/guidelines-for-resolving-iis-permissions-problems.md).  
  
- **在 TEMP 環境變數所指定的資料夾上設定權限**： 請確定裝載 Web 服務的虛擬目錄的 IIS 應用程式主機處理序識別具有讀取和寫入權限所指定的資料夾TEMP 環境變數。 若要決定開啟 TEMP 環境變數所指定的資料夾的命令提示字元，在 BizTalk 伺服器上，輸入下列命令，，，然後按 ENTER:  
  
  ```  
  echo %TEMP%  
  ```  
  
   TEMP 環境變數所指定的資料夾，即為 Web 服務以 Just In Time (JIT) 方式編繹成動態連結程式庫 (dll) 檔案的位置，因此必須可以藉此使用者帳戶的讀寫權限來存取。  
  
- **以 SOAP 方法呼叫傳送認證**： 確保 Web 服務用戶端以 SOAP 方法呼叫傳送認證。 依預設在 IIS 7.0[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]需要 windows 驗證。 使用 Internet Explorer 測試 Web 服務時，會自動傳送目前已登入之使用者的認證，這就是為什麼 Web 服務可以從 Internet Explorer 使用，卻不能從其他用戶端使用的原因。 如果 Web 服務用戶端沒有將認證加入 SOAP 方法呼叫，則會由於驗證失敗而產生 SOAP 例外狀況。 多個如需詳細資訊傳送認證，以 SOAP 方法呼叫中提供的範例程式碼[如何使用新 System.Net 類別建立 HTTP 用戶端](http://support.microsoft.com/kb/303436)。  
  
- **針對呼叫 Web 服務的錯誤進行疑難排解**： 如果呼叫 Web 服務時，就會發生錯誤，請檢查應用程式記錄檔，或訊息透過 BizTalk Server 管理 的事件和服務執行個體追蹤**群組中樞**頁面。 錯誤的可能原因相關資訊，請參閱[監控 BizTalk Server](../core/monitoring-biztalk-server.md)並[使用 [群組中樞] 頁面](../core/using-the-group-hub-page.md)。  
  
- **收集偵錯資訊**： 若要取得偵錯的詳細的資訊，請依照下列主題中所述的步驟[偵錯已發佈的 Web 服務](../core/debugging-published-web-services.md)如果遵循上述步驟無法解決問題。  
  
## <a name="known-issues"></a>已知問題  
 如需其他有關的已知問題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]相關的 Web 服務權限，請參閱 < You cannot call 協調流程公開為 Web 服務正在執行 BizTalk Server 的伺服器上的 「 網址[ http://go.microsoft.com/fwlink/?LinkId=196379 ](http://go.microsoft.com/fwlink/?LinkId=196379).  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解 BizTalk Server 權限](../core/troubleshooting-biztalk-server-permissions.md)   
 [解決 IIS 權限問題的指導方針](../core/guidelines-for-resolving-iis-permissions-problems.md)