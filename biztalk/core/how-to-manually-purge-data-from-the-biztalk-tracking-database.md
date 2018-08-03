---
title: 如何從 BizTalk 追蹤資料庫手動清除資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tracking database, purging
- purging, manually
- purging, warnings
ms.assetid: f350d850-5034-4166-940c-8d10b7b445fb
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ffb7b0eb838295e4abdc059a1437b6cf338d0a99
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993079"
---
# <a name="how-to-manually-purge-data-from-the-biztalk-tracking-database"></a>如何手動清除 BizTalk 追蹤資料庫的資料
「DTA 封存和清除 SQL Server Agent 作業」工作可減少由於持續清除資料庫和壓縮儲存的追蹤資料，而必須從 BizTalk 追蹤 (BizTalkDTADb) 資料庫手動清除資料的需要。 若 BizTalk 追蹤 (BizTalkDTADb) 資料庫已大量成長，導致效能持續降低，且「DTA 封存和清除」工作無法跟上資料庫的成長時，就可能需要手動清除資料。  
  
> [!CAUTION]
>  不論其完成時間為何，執行此程序會從 BizTalk 追蹤 (BizTalkDTADb) 資料庫刪除已完成執行個體的所有追蹤資料。 在執行此程序之前，您應該將 BizTalk 追蹤 (BizTalkDTADb) 資料庫與其他 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 資料庫分開封存。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以 SQL Server 系統管理員 (sysadmin) 固定伺服器角色成員的帳戶登入來執行這個程序。  
  
### <a name="to-manually-purge-data-from-the-biztalk-tracking-database"></a>若要從 BizTalk 追蹤資料庫手動清除資料  
  
1. 備份 BizTalk Server 資料庫。  
  
2. 封存 BizTalk 追蹤 (BizTalkDTADb) 資料庫。  
  
3. 開啟 [服務] 主控台。 按一下 **開始**，按一下**執行**，然後輸入**services.msc**。 如果**使用者帳戶控制** 對話方塊隨即出現，請按一下**繼續**。  
  
4. 當 [服務] 主控台出現時，請找出並停止下列每個服務。 若要停止服務，以滑鼠右鍵按一下中的服務資料列**Services**窗格中，然後再按一下**停止**。  
  
   -   BizTalkServiceBizTalkGroup: BizTalkServerApplication  
  
   -   企業單一登入服務  
  
        如果，BizTalkServiceBizTalkGroup: BizTalkServerApplication 服務正在執行，當您嘗試將 「 企業單一登入服務，關閉**停止其他服務**就會顯示對話方塊。 按一下 **[是]**。  
  
   -   規則引擎更新服務  
  
5. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。 如果**使用者帳戶控制** 對話方塊隨即出現，請確認描述的動作是什麼您想要，然後按一下**繼續**。  
  
6. 在  **BizTalk Server 管理主控台**在左邊視窗的 總管 窗格中，按兩下**BizTalk 群組**展開其下的清單，然後按兩下**平台設定**，然後按一下**主控件執行個體**。 這會顯示主控件執行個體的清單 (**主控件執行個體**窗格) 和相關屬性，在畫面右邊。  
  
7. 在 **主控件執行個體**窗格中，每個執行的主控件執行個體，以滑鼠右鍵按一下，然後按一下**停止**。  
  
8. 按一下 **開始**，請移至**執行**，型別**cmd**，然後按一下 **確定**。  
  
9. 在命令提示字元中，輸入：  
  
     **net stop iisadmin /y**  
  
     這將會逐一停止「IIS 管理服務」以及所有相依的服務，並在清除資料時，避免新的資料寫入 BizTalkDTADb。 請在每個服務停止時記下服務清單。 在稍後重新啟動 IIS 時，您將需要使用此服務清單。  
  
     以下是在發出此命令之後您將看到的輸出範例 (列在電腦中的相依服務可能不同)：  
  
    ```  
    The following services are dependent on the IIS Admin Service service. Stopping the IIS Admin Service service will also stop these services.  
    World Wide Web Publishing Service  
    HTTP SSL  
    ```  
  
10. 按一下 **開始**，按一下**所有程式**，按一下  **Microsoft SQL Server 2008 SP2**，然後按一下**SQL Server Management Studio**。  
  
11. 在 [**連接到伺服器**] 對話方塊中，指定 BizTalk 追蹤 (BizTalkDTADb) 資料庫所在 SQL Server 和適當的驗證類型的名稱，然後按一下**Connect**至連接到適當的 SQL Server。  
  
12. 在  **Microsoft SQL Server Management Studio**，按兩下**資料庫**，連按兩下**BizTalkDTADb**資料庫中，按兩下**可程式性**，然後按一下**預存程序**。  
  
13. 在 **物件總管詳細資料**窗格中，以滑鼠右鍵按一下**dtasp_purgeallcompletedtrackingdata**，然後按一下**執行預存程序**。  
  
14. 在 [**執行程序**] 對話方塊中，按一下**確定**。  
  
     不論其完成時間為何，此預存程序會刪除和已完成的執行個體關聯的所有追蹤資料。  
  
15. 開啟 [服務]。 按一下 **開始**，按一下**執行**，然後輸入**services.msc**。 如果**使用者帳戶控制** 對話方塊隨即出現，請確認描述的動作是什麼您想要，然後按一下**繼續**。  
  
16. 每個以下的服務，以滑鼠右鍵按一下，然後按一下**啟動**:  
  
    -   BizTalkServiceBizTalkGroup: BizTalkServerApplication  
  
    -   企業單一登入服務  
  
    -   規則引擎更新服務  
  
17. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
18. 在  **BizTalk Server 管理主控台**，按兩下**BizTalk 群組**，按兩下**平台設定**，然後按一下 **主機執行個體**。  
  
19. 在 **物件總管詳細資料**窗格中，每個停止的主控件執行個體，以滑鼠右鍵按一下，然後按一下**開始**。  
  
20. 啟動 [命令提示字元]，如上面的步驟 8 所述。  
  
21. 在命令提示字元中，以重新啟動每個您停止 IIS 服務步驟 4。 類型：  
  
     **net start**  *\<IISserviceName\>*  
  
     何處*\<IISserviceName\>* 是您想要重新啟動 IIS 服務的名稱。 您必須為每個 IIS 服務重複此命令。  
  
## <a name="see-also"></a>另請參閱  
 [封存和清除 BizTalk 追蹤資料庫](../core/archiving-and-purging-the-biztalk-tracking-database.md)   
 [備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-biztalk-server-databases.md)   
 [如何啟動、 停止、 暫停、 繼續或重新啟動 BizTalk Server 服務](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md)