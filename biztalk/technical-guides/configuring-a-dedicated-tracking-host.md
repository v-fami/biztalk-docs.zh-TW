---
title: "專用的追蹤主控件設定 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f997bcc2-08fd-4e9a-ba44-542ec8460d6d
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b91a4b65c6e9a9b293e967385b8f0ac4eece1aa4
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="configuring-a-dedicated-tracking-host"></a>專用的追蹤主控件設定
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]最佳化輸送量，因此主要協調流程和傳訊引擎不要實際上不會移動事件或訊息直接到 BizTalk 追蹤 (DTA) 或商務活動監控 (BAM) 資料庫，因為這會將這些引擎從其主要轉向至執行商務程序的工作。 相反地，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]離開事件和訊息在 MessageBox 資料庫，並將其標示為需要移至 BizTalk 追蹤 」 或 「 BAM 資料庫。 背景處理序 （追蹤主控件），然後到 BizTalk 追蹤和 BAM 資料庫，SQL Server Agent 作業複製追蹤的訊息到 BizTalk 追蹤資料庫時移動事件。  
  
## <a name="advantages-of-using-a-dedicated-tracking-host"></a>使用專用的追蹤主控件的優點  
 BizTalk 主控件裝載追蹤負責移動 DTA 和 BAM 追蹤資料從 MessageBox 資料庫，BizTalk 追蹤 (DTA) 」 及 「 BAM 主要匯入資料庫。 此移動的追蹤資料有其他正在執行中的相同的主控件裝載追蹤的 BizTalk 成品的效能影響。 因此，您應該使用不只一個主控件追蹤的專用的主機。  
  
 使用專用的追蹤主控件也可讓您停止其他 BizTalk 主控件，而不會干擾[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]追蹤。 追蹤資料從 MessageBox 資料庫的移動非常重要的狀況良好[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。 如果停止 BizTalk 主控件負責將追蹤資料移 BizTalk 群組中，將不會執行追蹤資料解碼服務。 這個影響是，如下所示：  
  
-   HAT 追蹤資料不會從 MessageBox 資料庫移動到 BizTalk 追蹤資料庫。  
  
-   BAM 追蹤資料會從 MessageBox 資料庫移至 BAM 主要匯入資料庫。  
  
-   不移動資料，因為它無法從 MessageBox 資料庫刪除。  
  
-   追蹤資料解碼服務停止時，追蹤攔截器仍執行，將追蹤資料寫入至 MessageBox 資料庫。 如果不移動資料，這將會導致 MessageBox 資料庫變得繁雜，這將會影響一段時間的效能。 即使自訂屬性不會受到追蹤，或是未設定 BAM 設定檔，根據預設某些會追蹤資料 （例如，管線接收 / 傳送事件和協調流程事件）。 如果您不想執行的追蹤資料解碼服務，請關閉所有的追蹤，以便任何攔截器會將資料儲存至資料庫。 若要停用全域追蹤，請參閱[如何關閉全域追蹤](http://go.microsoft.com/fwlink/?LinkId=154193)(http://go.microsoft.com/fwlink/?LinkId=154193) 使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台來選擇性地停用追蹤事件。  
  
## <a name="optimizing-performance-for-a-dedicated-tracking-host"></a>專用的追蹤主控件的效能最佳化  
 此主機應執行至少兩部電腦上執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]（重複性的情況下提供，其中失敗）。 為了達到最佳效能，您應該有至少一個追蹤主控件執行個體，每個 MessageBox 資料庫。 追蹤主控件執行個體的實際數目應為 N + 1，其中 N = MessageBox 資料庫數目。 "+ 1 」 是以獲得備援。 沒有任何好處，加入更多的因為只有一個追蹤主控件執行個體可以移動特定的 MessageBox 資料庫的資料。 如此一來，鎖定，應該不會發生問題。 其他的一個追蹤主控件執行個體加入具有容錯功能。如果其中一個追蹤主控執行個體失敗，其他執行個體就會假設失敗的執行個體的責任。  
  
 追蹤主控件執行個體移動特定的 MessageBox 資料庫的追蹤資料，但是會永遠不會有多個追蹤主控件執行個體特定的 MessageBox 資料庫移動資料。 例如，如果您有三個 MessageBox 資料庫，且只有兩個追蹤主控件執行個體，然後其中一個主控件執行個體需要移動兩個 MessageBox 資料庫的資料。 加入第三個追蹤主控件執行個體分散追蹤裝載另一部電腦執行的工作[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 在此案例中，加入第四個追蹤主控件執行個體不會散佈任何的多個追蹤主控件使用，但會提供額外的追蹤主控件執行個體的容錯功能。  
  
 如需有關 BAM 事件匯流排服務的詳細資訊，請參閱 BizTalk Server 說明中的下列主題：  
  
-   [管理 BAM 事件匯流排服務](http://go.microsoft.com/fwlink/?LinkId=154194)(http://go.microsoft.com/fwlink/?LinkId=154194)  
  
-   [建立的 BAM 事件匯流排服務執行個體](http://go.microsoft.com/fwlink/?LinkId=154195)(http://go.microsoft.com/fwlink/?LinkId=154195)  
  
## <a name="configuring-a-dedicated-tracking-host"></a>專用的追蹤主控件設定  
 若要執行本節中的程序，您必須使用下列使用者的權限來修改主控件屬性允許主控件追蹤：  
  
-   您必須是成員[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。  
  
-   在 SQL Server 中您必須具有以下權限：  
  
    -   您必須是 SQL Server 系統管理員或成員的*db_owner*或*db_securityadmin*中 BizTalk 追蹤資料庫 (BizTalk DTADb) MessageBox 資料庫 （SQL Server 資料庫角色BizTalkMsgBoxDb) 與 BAM 主要匯入資料庫 (BAMPrimaryImport)。  
  
    -   您必須是所有電腦上的 sysadmin SQL Server 角色的成員，其中的 MessageBox 資料庫，或成員*db_owner*或*db_ddladmin*所有 MessageBox 資料庫的 SQL Server 角色。  
  
#### <a name="to-enable-host-tracking"></a>若要啟用主控件追蹤  
  
1.  按一下**啟動**，按一下 **程式**，按一下  **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，展開 BizTalk 群組，按一下**平台設定**，然後按一下 **主機**。  
  
3.  在詳細資料窗格中，以滑鼠右鍵按一下您想要修改，然後按一下 主機**屬性**。  
  
4.  在**主控件屬性**對話方塊中，於**一般**索引標籤上，選取或清除**選項-允許主控件追蹤**，然後按一下 **確定**。  
  
     選取此核取方塊以指示主控件載入 BizTalk 追蹤元件，以處理狀況監控與商務資料。 若您選取此核取方塊，目前的主控件將會擁有 MessageBox 資料庫中追蹤資料表與追蹤資料庫的讀取/寫入存取權限。 因此，任何在此主控件中執行的物件也將擁有這些資料庫的讀/寫存取權限。  
  
     若您清除此核取方塊，主控件將只會擁有 MessageBox 資料庫中追蹤資料表的寫入存取權，而不會擁有追蹤資料庫的存取權。  
  
## <a name="see-also"></a>請參閱  
 [檢查清單：設定 BizTalk Server](../technical-guides/checklist-configuring-biztalk-server.md)