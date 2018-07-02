---
title: 專用的追蹤主控件設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f997bcc2-08fd-4e9a-ba44-542ec8460d6d
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: defed64020300ebe6843e8e06bb15a51af2c4ec3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986711"
---
# <a name="configuring-a-dedicated-tracking-host"></a>專用的追蹤主控件設定
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 針對輸送量最佳化讓主要的協調流程和傳訊引擎執行不實際事件或訊息直接移至 BizTalk 追蹤 (DTA) 」 或 「 商務活動監控 (BAM) 資料庫，因為這會將轉向與其主要這些引擎執行商務程序的工作。 相反地，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]離開事件和訊息在 MessageBox 資料庫，並將其標示為需要移至 BizTalk 追蹤 」 或 「 BAM 資料庫。 背景處理序 （追蹤主控件），然後到 BizTalk 追蹤 」 和 「 BAM 資料庫，同時 SQL Server Agent 作業複製追蹤的訊息到 BizTalk 追蹤資料庫的移動事件。  
  
## <a name="advantages-of-using-a-dedicated-tracking-host"></a>使用專用的追蹤主控件的優點  
 BizTalk 主控件裝載追蹤負責移動 DTA 和 BAM 追蹤資料從 MessageBox 資料庫，以 「 BizTalk 追蹤 (DTA) 」 及 「 BAM 主要匯入資料庫。 此移動的追蹤資料會影響效能的其他執行相同的主應用程式裝載追蹤中的 BizTalk 成品。 因此，您應該使用專用的主機，不只一個主控件追蹤。  
  
 使用專用的追蹤主控件也可讓您停止其他 BizTalk 主控件，而不會干擾[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]追蹤。 追蹤從 MessageBox 資料庫的資料移動最重要的是狀況良好[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。 如果停止 BizTalk 主控件，負責移動 BizTalk 群組中的追蹤資料，將不會執行追蹤資料解碼服務。 影響如下所示：  
  
- HAT 追蹤資料會從 MessageBox 資料庫移動到 BizTalk 追蹤資料庫。  
  
- BAM 追蹤資料會從 MessageBox 資料庫移動至 BAM 主要匯入資料庫。  
  
- 資料不會移動，因為它無法從 MessageBox 資料庫刪除。  
  
- 追蹤資料解碼服務停止時，追蹤攔截器將仍執行，並將追蹤資料寫入至 MessageBox 資料庫。 如果不移動資料，這會變得過大，MessageBox 資料庫將會影響一段時間的效能。 即使自訂屬性不會受到追蹤，或是未設定 BAM 設定檔，預設情況下一些會追蹤資料 （例如管線接收 / 傳送事件和協調流程事件）。 如果您不要執行追蹤資料解碼服務，請關閉所有的追蹤，以便任何攔截器會將資料儲存至資料庫。 若要停用全域追蹤，請參閱[如何關閉全域追蹤](http://go.microsoft.com/fwlink/?LinkId=154193)(<http://go.microsoft.com/fwlink/?LinkId=154193>) 使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台來選擇性地停用追蹤事件。  
  
## <a name="optimizing-performance-for-a-dedicated-tracking-host"></a>專用的追蹤主控件的效能最佳化  
 應執行至少兩部電腦上執行，此主控件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]（以提供備援，萬一其中一個失敗）。 為了達到最佳效能，您應該有至少一個追蹤主控件執行個體，每個 MessageBox 資料庫。 追蹤主控件執行個體的實際數目應該是 N + 1，其中 N = MessageBox 資料庫數目。 "+ 1"是冗餘的。 沒有任何好處，因為只有一個追蹤主控件執行個體，請新增更多的項目，可以移動特定的 MessageBox 資料庫的資料。 如此一來，鎖定，應該永遠不會是問題。 其他的一個追蹤主控件執行個體新增容錯功能;如果其中一個追蹤主控執行個體失敗，其他執行個體就會假設失敗的執行個體的責任。  
  
 追蹤主控件執行個體移動特定的 MessageBox 資料庫的追蹤資料，但是會永遠不會有一個以上的追蹤主控件執行個體特定的 MessageBox 資料庫移動資料。 例如，如果您有三個 MessageBox 資料庫，以及追蹤主控件執行個體的唯一兩個，然後其中一個主控件執行個體必須為兩個 MessageBox 資料庫移動資料。 新增第三個追蹤主控件執行個體分散追蹤裝載工作来執行的另一部電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 在此案例中，加入第四個追蹤主控件執行個體不會發佈任何詳細的追蹤主控件運作，但會提供額外的追蹤主控件執行個體的容錯功能。  
  
 如需有關 BAM 事件匯流排服務的詳細資訊，請參閱 BizTalk Server 說明中的下列主題：  
  
-   [管理 BAM 事件匯流排服務](http://go.microsoft.com/fwlink/?LinkId=154194)(http://go.microsoft.com/fwlink/?LinkId=154194)  
  
-   [建立 BAM 事件匯流排服務的執行個體](http://go.microsoft.com/fwlink/?LinkId=154195)(http://go.microsoft.com/fwlink/?LinkId=154195)  
  
## <a name="configuring-a-dedicated-tracking-host"></a>專用的追蹤主控件設定  
 在本節中，執行程序，您必須使用下列使用者的權限來修改主控件屬性允許主控件追蹤：  
  
- 您必須是成員[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。  
  
- 在 SQL Server 中您必須具有以下權限：  
  
  -   您必須是 SQL Server 系統管理員或成員*db_owner*或是*db_securityadmin*中 BizTalk 追蹤資料庫 (BizTalk DTADb)、 MessageBox 資料庫 （SQL Server 資料庫角色BizTalkMsgBoxDb)，以及 BAM 主要匯入資料庫 (BAMPrimaryImport)。  
  
  -   您必須是所有電腦上的 sysadmin SQL Server 角色的成員，有的 MessageBox 資料庫，或隸屬*db_owner*或是*db_ddladmin*所有 MessageBox 資料庫的 SQL Server 角色。  
  
#### <a name="to-enable-host-tracking"></a>若要啟用主控件追蹤  
  
1. 按一下 **開始**，按一下**程式**，按一下  **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**，展開 BizTalk 群組，按一下**平台設定**，然後按一下**主機**。  
  
3. 在 詳細資料 窗格中，以滑鼠右鍵按一下您要修改，然後按一下 主機**屬性**。  
  
4. 在 **主機內容**對話方塊的 **一般**索引標籤上，選取或清除**選項-允許主控件追蹤**，然後按一下**確定**。  
  
    選取此核取方塊以指示主控件載入 BizTalk 追蹤元件，以處理狀況監控與商務資料。 若您選取此核取方塊，目前的主控件將會擁有 MessageBox 資料庫中追蹤資料表與追蹤資料庫的讀取/寫入存取權限。 因此，任何在此主控件中執行的物件也將擁有這些資料庫的讀/寫存取權限。  
  
    若您清除此核取方塊，主控件將只會擁有 MessageBox 資料庫中追蹤資料表的寫入存取權，而不會擁有追蹤資料庫的存取權。  
  
## <a name="see-also"></a>另請參閱  
 [檢查清單：設定 BizTalk Server](../technical-guides/checklist-configuring-biztalk-server.md)