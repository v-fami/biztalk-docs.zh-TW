---
title: "BizTalk 作業 Web 服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af38815f-f643-4598-9148-6499071d12e4
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d09fb2cdcca83e8a9f2e4e7704178d40a915065
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-biztalk-operations-web-service"></a>BizTalk 作業 Web 服務
Microsoft BizTalk 作業 Web 服務公開的物件和 BizTalk Server 訊息相關資訊。 服務名稱是**ESB.BizTalkOperationsService**，與此服務會公開各種不同的方法會傳回項目，例如清單主機、 協調流程、 應用程式和 BizTalk 應用程式狀態。  
  
 可用的方法如下：  
  
-   **應用程式**。 這個方法會採用任何參數，並傳回的名稱和描述的所有已安裝的 BizTalk 應用程式做為集合**BTApplication**物件。  
  
-   **ApplicationStatus**。 這個方法會將參數當成應用程式名稱，並傳回為指定的 BizTalk 應用程式的相關資訊**BTSysStatus**執行個體。 這項資訊包括協調流程、 傳送埠、 接收位置和主機詳細資料。  
  
-   **GetLiveMessageBody**。 訊息識別碼和執行個體識別碼，這個方法會採用做為參數，並從即時環境做為傳回該訊息的本文**BTMsgBody**執行個體。  
  
-   **GetMessageInstances**。 這個方法會做為參數的訊息類型，並做為集合傳回所有比對訊息**BTMsgInstance**物件。  
  
-   **GetOrchestrationInstances**。 這個方法會採用做為參數名稱的協調流程，並傳回的集合**BTOrchestrationInstance**包含相符的協調流程的詳細資料的物件。  
  
-   **GetTrackedMessageBody**。 這個方法會將參數當成訊息的 GUID，並傳回做為該訊息的本文**BTMsgBody** biztalk 處理後的執行個體。  
  
-   **主機**。 這個方法會將參數當成主機的名稱，並傳回指定的主機執行個體的相關資訊，做為集合**BTHost**執行個體。 您可以使用主機名稱參數為空字串，傳回所有主控件執行個體的相關資訊。  
  
-   **MessageFlowTree**。 這個方法會採用做為參數執行個體識別碼，並傳回該訊息的訊息流程的詳細資料**RouteTreeNode**執行個體。  
  
-   **協調流程**。 這個方法會採用做為參數名稱的協調流程，並傳回該協調流程的所有資訊**BTSysStatus**執行個體。 傳回有關所有協調流程中使用協調流程名稱參數為空字串。  
  
-   **ReceiveLocations**。 這個方法會採用做為參數名稱的接收位置，並傳回所有資訊比對的位置中的，如**BTSysStatus**執行個體。 您可以使用接收位置名稱參數為空字串，傳回所有位置的相關資訊。  
  
-   **ReceiveLocationsByDescription**。 這個方法會採用做為參數的描述接收位置，並傳回所有資訊比對的位置中的，如**BTSysStatus**執行個體。 您可以使用描述參數為空字串，傳回所有位置的相關資訊。  
  
-   **SendPorts**。 這個方法會採用做為參數傳送埠的名稱，並傳回符合為連接埠的所有資訊**BTSysStatus**執行個體。 您可以使用傳送連接埠名稱參數為空字串，傳回所有連接埠的相關資訊。  
  
-   **SendPortsByDescription**。 這個方法會採用做為參數的描述傳送埠，並傳回符合為連接埠的所有資訊**BTSysStatus**執行個體。 傳回有關所有連接埠使用 description 參數為空字串。  
  
-   **StatusChanged**。 這個方法會將參數當成時間戳記，並傳回詳細資料 （例如連接埠、 主機和協調流程） 的 BizTalk 物件的修改，因為指定的時間戳記，當做**BTSysStatus**執行個體。  
  
-   **SystemStatus**。 這個方法會採用任何參數，並傳回完整詳細資料，做為 BizTalk 系統狀態的**BTSysStatus**執行個體。  
  
-   **UpdateReceiveLocationDescription**。 這個方法會更新指定的接收位置使用的參數值包含應用程式名稱、 接收埠名稱、 接收位置名稱和接收位置描述的描述。 它會傳回字串，表示作業的結果。 請注意測試用戶端應用程式會從其 App.config 檔案讀取這項資訊。  
  
-   **UpdateSendPortDescription**。 這個方法會更新指定的傳送埠使用的參數值包含傳送埠名稱和描述傳送連接埠的描述。 它會傳回字串，表示作業的結果。 請注意測試用戶端應用程式會從其 App.config 檔案讀取這項資訊。  
  
## <a name="configuring-the-biztalk-operations-web-service"></a>設定 BizTalk 作業 Web 服務  
 BizTalk 作業 Web 服務可能會直接與 BizTalk Server 管理資料庫使用 Windows Management Instrumentation (WMI) 通訊，或使用 BizTalk 作業和戲嚽庢 API 來取得它所需要的資訊。 因此，您必須確定您的系統符合下列條件，並將下列安全性權限設定：  
  
-   設定**allowOverride**電腦層級 Web.config 檔案中的屬性**false**以確定開發人員無法變更其應用程式的信任層級。  
  
-   根據預設，BizTalk 作業 Web 服務未設定為需要安全通訊端層 (SSL) 用戶端存取時。 您應該設定服務，讓它需要 SSL 用戶端存取，並保護網際網路資訊服務 (IIS) Web 服務主機電腦與執行裝載 BizTalkMgmtDb 資料庫使用 SQL Server 的電腦之間的連線網路層級 IPSec 與適當的檔案層級存取控制清單 (ACL) 權限。  
  
-   存取 BizTalk 作業 Web 服務的使用者必須是一些方法的預設 BizTalk Server 系統管理員群組的成員以及其他方法的預設 BizTalk 應用程式使用者群組的成員。  
  
-   您必須確定 BizTalk 作業 Web 服務位於名為 已停用匿名存取的 ESB.BizTalkOperationsService 的 IIS 虛擬目錄。  
  
-   使用者必須擁有**選取**BizTalkMgmtDb 資料庫和 BizTalkMsgBoxDb 資料庫位於 SQL Server 中之數個資料表的權限。 您可以使用 SQL Server Management Studio 來設定下列權限：  
  
    -   在 BizTalkMgmtDb 資料庫中，設定 BTS_ADMIN_USERS 資料庫角色與**選取**權限的下列資料表：  
  
        -   adm_Server2HostMapping  
  
        -   adm_Server  
  
        -   adm_hostInstance  
  
    -   在 BizTalkMsgBoxDb 資料庫中，設定 BTS_ADMIN_USER 資料庫角色與**選取**ProcessHeartbeats 資料表的權限。  
  
 在 SQL Server Management Studio，您可以設定的必要權限。 若要這樣做，請展開**安全性**在左的窗格的樹狀檢視的 [物件總管] 中，依序展開**角色**，依序展開**適**選取 BTS_ADMIN_USERS 角色，然後編輯此角色，如圖 1 所示的屬性。  
  
 ![SQL Server Mgmt Studio](../esb-toolkit/media/ch4-sqlservermgmtstudio.gif "第 4 章第 SQLServerMgmtStudio")  
  
 **圖 1**  
  
 **編輯 Microsoft SQL Server Management Studio 中的 BTS_ADMIN_USERS 資料庫角色的權限**  
  
> [!NOTE]
>  您必須設定使用 Windows 整合式安全性，並內建網路服務帳戶下執行此服務。 您也必須啟用 Kerberos 驗證您的 IIS 網頁伺服器上，讓它將此標頭**Negotiate、 NTLM**給用戶端。 如需詳細資訊，請參閱[如何設定 IIS 以支援用於網路驗證的 Kerberos 通訊協定與 NTLM 通訊協定](http://go.microsoft.com/fwlink/?LinkId=186430)([http://go.microsoft.com/fwlink/?LinkId=186430](http://go.microsoft.com/fwlink/?LinkId=186430))。  
>   
>  根據預設，BizTalk 作業 Web 服務未設定為需要 SSL 用戶端存取時。 您應該設定服務，讓需要 SSL 用戶端存取和保護 IIS Web 服務主機電腦和伺服器主控 「 UDDI 服務使用網路層級 IPSec 和適當的檔案層級 ACL 權限之間的連線。