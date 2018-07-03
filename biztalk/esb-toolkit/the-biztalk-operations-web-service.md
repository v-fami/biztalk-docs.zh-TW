---
title: BizTalk 作業 Web 服務 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af38815f-f643-4598-9148-6499071d12e4
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b9a78dddbbd76566c5c97b1e571e5ad80073d4a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997967"
---
# <a name="the-biztalk-operations-web-service"></a>BizTalk 作業 Web 服務
Microsoft BizTalk 作業 Web 服務會公開有關物件和 BizTalk Server 中的訊息資訊。 服務名稱是**ESB.BizTalkOperationsService**，和服務會公開各種不同的方法會傳回清單等主機、 協調流程、 應用程式和 BizTalk 應用程式狀態的項目。  
  
 下列方法可用：  
  
-   **應用程式**。 這個方法會採用任何參數，並傳回的名稱和描述的所有已安裝的 BizTalk 應用程式的集合**BTApplication**物件。  
  
-   **ApplicationStatus**。 這個方法會將參數當成應用程式名稱，並傳回為指定的 BizTalk 應用程式的相關資訊**BTSysStatus**執行個體。 這項資訊包括協調流程、 傳送埠、 接收位置，以及主機詳細資料。  
  
-   **GetLiveMessageBody**。 這個方法會採用做為參數，一個訊息識別碼，而且執行個體識別碼，並從即時環境，做為傳回該訊息的本文**BTMsgBody**執行個體。  
  
-   **GetMessageInstances**。 這個方法會做為參數的訊息類型，並為集合傳回所有相符的訊息**BTMsgInstance**物件。  
  
-   **GetOrchestrationInstances**。 這個方法會採用做為參數名稱的協調流程，並傳回的集合**BTOrchestrationInstance**包含相符的協調流程的詳細資料的物件。  
  
-   **GetTrackedMessageBody**。 這個方法會採用做為參數的訊息的 GUID，並傳回該訊息本文**BTMsgBody**處理 BizTalk 中之後，執行個體。  
  
-   **主機**。 這個方法會採用做為參數的主機名稱，並傳回指定的主控件執行個體的相關資訊的集合**BTHost**執行個體。 您可以使用主機名稱參數為空字串，傳回所有主控件執行個體的相關資訊。  
  
-   **MessageFlowTree**。 這個方法會採用做為參數執行個體識別碼，並傳回該訊息的訊息流程的詳細資料**RouteTreeNode**執行個體。  
  
-   **協調流程**。 這個方法會採用做為參數的協調流程，名稱，並傳回做為協調流程的所有資訊**BTSysStatus**執行個體。 您可以使用協調流程名稱參數為空字串，傳回所有的協調流程的相關資訊。  
  
-   **ReceiveLocations**。 這個方法會採用做為參數名稱的接收位置，並傳回進行比對為位置的所有資訊**BTSysStatus**執行個體。 您可以使用接收位置名稱參數為空字串，傳回所有位置的相關資訊。  
  
-   **ReceiveLocationsByDescription**。 這個方法會採用做為參數描述的接收位置，並傳回的比對為位置的所有資訊**BTSysStatus**執行個體。 您可以使用 description 參數為空字串，傳回所有位置的相關資訊。  
  
-   **SendPorts**。 這個方法會採用做為參數傳送埠的名稱，並傳回用於比對為連接埠的所有資訊**BTSysStatus**執行個體。 您可以使用傳送連接埠名稱參數為空字串，傳回所有連接埠的相關資訊。  
  
-   **SendPortsByDescription**。 這個方法會採用做為參數描述的傳送埠，並傳回用於比對為連接埠的所有資訊**BTSysStatus**執行個體。 您可以使用 description 參數為空字串，傳回所有連接埠的相關資訊。  
  
-   **StatusChanged**。 這個方法會採用做為參數的時間戳記，則會傳回的詳細資料 （例如連接埠、 主機和協調流程） 的 BizTalk 物件修改為指定的時間戳記**BTSysStatus**執行個體。  
  
-   **SystemStatus**。 這個方法不採用任何參數，則會傳回做為 BizTalk 系統狀態的完整詳細資料**BTSysStatus**執行個體。  
  
-   **UpdateReceiveLocationDescription**。 這個方法會更新指定的接收位置使用應用程式名稱、 接收埠名稱、 接收位置名稱，以及接收位置描述所包含的參數值的描述。 它會傳回字串，表示作業的結果。 請注意，測試用戶端應用程式會從其 App.config 檔案讀取這項資訊。  
  
-   **UpdateSendPortDescription**。 這個方法會更新指定的傳送埠使用的傳送埠名稱和傳送埠描述所包含的參數值的描述。 它會傳回字串，表示作業的結果。 請注意，測試用戶端應用程式會從其 App.config 檔案讀取這項資訊。  
  
## <a name="configuring-the-biztalk-operations-web-service"></a>設定 BizTalk 作業 Web 服務  
 BizTalk 作業 Web 服務可能會直接與 BizTalk Server 管理資料庫，使用 Windows Management Instrumentation (WMI) 通訊，或使用 BizTalk 作業和 Explorer API 來取得它所需要的資訊。 因此，您必須確定您的系統符合下列條件，和您設定下列安全性權限設定：  
  
- 設定**allowOverride**屬性，在電腦層級的 Web.config 檔，以便**false**藉此確定開發人員不能變更他們的應用程式的信任層級。  
  
- 根據預設，BizTalk 作業 Web 服務未設定為需要 Secure Sockets Layer (SSL) 用戶端存取時。 您應該設定服務，因此它需要 SSL 用戶端存取，並保護 Internet Information Services (IIS) Web 服務主機電腦與執行裝載 BizTalkMgmtDb 資料庫使用 SQL Server 的電腦之間的連線網路層級 IPSec 和適當的檔案層級存取控制清單 (ACL) 權限。  
  
- 存取 BizTalk 作業 Web 服務的使用者必須是某些方法的預設 BizTalk Server 系統管理員群組的成員和其他方法的預設 BizTalk 應用程式使用者群組的成員。  
  
- 您必須確定 BizTalk 作業 Web 服務都位於名為 已停用匿名存取的 ESB.BizTalkOperationsService 的 IIS 虛擬目錄。  
  
- 使用者必須擁有**選取**BizTalkMgmtDb 資料庫和 BizTalkMsgBoxDb 資料庫位於 SQL Server 中的多個資料表的權限。 您可以使用 SQL Server Management Studio 來設定下列權限：  
  
  -   在 BizTalkMgmtDb 資料庫中，設定 BTS_ADMIN_USERS 資料庫角色**選取**權限的下列資料表：  
  
      -   adm_Server2HostMapping  
  
      -   adm_Server  
  
      -   adm_hostInstance  
  
  -   在 BizTalkMsgBoxDb 資料庫中，設定 BTS_ADMIN_USER 資料庫角色**選取**ProcessHeartbeats 資料表的權限。  
  
  在 SQL Server Management Studio，您可以設定的必要權限。 若要這樣做，請展開**安全性**在樹狀檢視左的窗格的 物件總管 中，展開**角色**，展開**適**選取 BTS_ADMIN_USERS 角色，然後編輯此角色，如 圖 1 所示的屬性。  
  
  ![SQL Server 管理 Studio](../esb-toolkit/media/ch4-sqlservermgmtstudio.gif "第 4 章第 SQLServerMgmtStudio")  
  
  **圖 1**  
  
  **編輯 Microsoft SQL Server Management Studio 中的 BTS_ADMIN_USERS 資料庫角色的權限**  
  
> [!NOTE]
>  您必須設定此服務使用 Windows 整合式安全性，並內建的網路服務帳戶下執行。 您也必須啟用 Kerberos 驗證您的 IIS 網頁伺服器上，因此它會傳送標頭**Negotiate、 NTLM**給用戶端。 如需詳細資訊，請參閱 <<c0> [ 如何設定 IIS 以支援用於網路驗證的 Kerberos 通訊協定與 NTLM 通訊協定](http://go.microsoft.com/fwlink/?LinkId=186430)([http://go.microsoft.com/fwlink/?LinkId=186430](http://go.microsoft.com/fwlink/?LinkId=186430))。  
>   
>  根據預設，BizTalk 作業 Web 服務未設定為需要 SSL 用戶端存取時。 您應該設定服務，因此它需要 SSL 用戶端存取和保護 IIS Web 服務主機電腦和伺服器主控 「 UDDI 服務使用網路層級 IPSec 和適當的檔案層級 ACL 權限之間的連線。