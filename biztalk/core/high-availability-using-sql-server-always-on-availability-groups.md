---
title: 使用 SQL Server Alwayson 可用性群組的高可用性 |Microsoft 文件
description: 群組的 BizTalk Server 資料庫，以取得高可用性 (HA) 解決方案，使用 SQL Server Alwayson 上可用群組 (AG)，包括系統需求和限制的不同節點上。 一律在 AG 需要 Windows Server 容錯移轉叢集 (WSFC)。
ms.custom: ''
ms.date: 04/10/2018
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4511a578-77d2-49ee-99bd-f0406ad625d0
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4bc7a1d1864b4e31bc20d170e2f2dd2602646188
ms.sourcegitcommit: 770523695b34cc54db81f7ab7eba46f2bc19baec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="high-availability-using-sql-server-always-on-availability-groups"></a>使用 SQL Server Alwayson 可用性群組的高可用性
設定使用 SQL Server AlwaysOn 可用性群組的高可用性。

> [!TIP] 
[設定 BizTalk Server 2016 使用可用性群組實驗室](https://skastberg.wordpress.com/2017/02/22/setting-up-my-biztalk-server-2016-using-availability-groups-lab/)提供 Microsoft 欄位工程師撰寫的逐步指引。 它根據實驗室環境，並包含某些觀察。 簽出。  

> [!IMPORTANT]
> * 使用從 SQL Server 2016 alwayson 可用性群組。 如果您使用舊版 SQL Server，本主題不適用於您。 
> * BizTalk Server 2016 支援同步認可模式，不支援非同步認可模式。 災害復原，建議設定 「 備份 BizTalk Server 」 工作，並使用記錄傳送。 請參閱[備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-biztalk-server-databases.md)的特定詳細資料。
> 
>    [可用性模式](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/availability-modes-always-on-availability-groups)詳細說明與 Alwayson 可用性群組的認可選項。 


## <a name="background-and-history"></a>背景和歷程記錄

BizTalk Server 高度依賴 SQL Server 以保存資料。 整合不同的商業應用程式，例如，接收、 處理，或將訊息路由時，其他元件和 BizTalk Server 中的主機都有特定的角色。 資料庫電腦會擷取此工作，並將它保存到磁碟。 

BizTalk 會使用 SQL Server 容錯移轉叢集和記錄傳送至其內部資料庫提供高可用性、 備份和還原和災害復原。 在 Azure IaaS （Azure 虛擬機器），舊版的 SQL Server 不支援容錯移轉叢集執行個體 （不支援 MSDTC）。 如此一來，BizTalk 沒有高可用性解決方案時使用 Azure Vm。

從 SQL Server 2016 開始，SQL Server AlwaysOn 可用性群組可以支援 MSDTC 內部部署和使用 Azure Vm。 如此一來，BizTalk 資料庫內部部署或 Azure IaaS 案例可以支援 SQL Server 2016 AlwaysOn 功能。 

## <a name="sql-server-2016-alwayson-availability-groups"></a>SQL Server 2016 AlwaysOn 可用性群組 
部署 AlwaysOn 可用性群組需要 Windows Server 容錯移轉叢集 (WSFC) 叢集。 給定可用性群組的每個可用性複本都必須位在相同 WSFC 叢集的不同節點上。 對於您建立的每個可用性群組，系統會建立一個 WSFC 資源群組。 WSFC 叢集會監視此資源群組，以評估主要複本的健康情況。  

下圖顯示可用性群組，其中包含一個主要複本和四個次要複本。  
 
 ![SQLAG_PrimaryReplica](../core/media/sqlag-primaryreplica.png)

用戶端可以連線到使用可用性群組接聽程式之給定的可用性群組的主要複本。 可用性群組接聽程式提供一組會附加至給定的可用性群組的直接用戶端連接至適當的可用性複本的資源。 

>[!IMPORTANT]
> SQL Server 2016 支援 Windows Server 2016 和 Windows Server 2012 R2 上的 MSDTC 與 AlwaysOn 可用性群組 (AG)。 **Windows Server 2012 R2**需要[3090973](https://support.microsoft.com/kb/3090973)来安裝的 Windows hotfix。 
> **Windows Server 2016**要求[RemoteAccessEnabled 登錄機碼](https://support.microsoft.com/kb/3182294)啟用。

SQL Server 2016 之前的任何版本不支援使用 AlwaysOn AG 的 MSDTC。  

使用 SQL Server AlwaysOn 可用性群組不支援相同的 SQL Server 執行個體上的資料庫之間的 MSDTC。 這表示在分散式交易中的任何兩個 BizTalk 資料庫可以位於相同的 SQL server 執行個體。 交易一致性，應該在不同的 SQL server 執行個體上裝載參與分散式交易的 BizTalk 資料庫。 請注意，並不重要 SQL 執行個體是在同一部電腦或不同的電腦。  


## <a name="providing-high-availability-for-biztalk-databases-using-alwayson-availability-groups"></a>為使用 AlwaysOn 可用性群組的 BizTalk 資料庫提供高可用性 
在 BizTalk Server 的基本組態，9 資料庫至少會建立包含規則和 BAM 資料庫。 因為 MSDTC 可用性群組限制先前所述，如下列組態不能確保交易一致性。 

![SQLAG_NoTrans](../core/media/sqlag-notrans.gif)
 
我們建議您在 BizTalk Server 資料庫分為下列四個 SQL Server 執行個體︰
 
| 執行個體 |角色 |該群組中的 BizTalk 資料庫  |
|--- | --- | ---|
|1 |驗證 |SSODB|
|2 |管理 |BizTalkMgmtDb| 
|3 |執行階段 |BizTalkMsgBoxDb<br/> BizTalkRulesEngineDb<br/> BAMPrimaryImport<br/>BAMStarSchema <br/>BAMAlertsApplication |
|4 |追蹤 |BizTalkDTADb<br/>EsbItineraryDb<br/>EsbExceptionDb | 
 
在向外擴充 MessageBox 案例 （具有一個以上的 MessageBox 的組態） 中，沒有一個以上的 MessageBox 資料庫，且每個 MessageBox 資料庫必須在自己的 SQL Server 執行個體。 

BizTalk Server 也取決於 SQL Server Analysis Services 與 BAM 分析和封存的 SQL Server 整合服務。 SQL Server Integration Services 或 Azure IaaS 中的 Analysis Services 不提供高可用性解決方案。 因此建議使用 BAMArchive 和 BAMAnalysis Analysis Services 資料庫的另一個獨立 SQL Server 執行個體。 內部部署上安裝 SQL 容錯移轉叢集執行個體可以用於建立高可用性設定。 

此設定下, 圖說明並建議您在可用性群組的 BizTalk 資料庫︰  

![SQLAG_Recommended](../core/media/sqlag-recommended.png)
 
SQL Server 資料庫，以及 BizTalk Server 組態也會建立 SQL Server 安全性登入和 SQL 代理程式作業。 AlwaysOn 可用性群組只會提供管理資料庫可用性群組內的能力。 登入和 BizTalk 的 SQL 代理程式作業需要建立及更新/管理，以手動方式在所有可用性複本上。  

下列清單中的 SQL Server 安全性登入是 BizTalk Server 相關聯。 您可能必須建立的 BizTalk Server 應用程式的其他登入。 如果是的話，您必須複寫在每個裝載 BizTalk 資料庫複本的 SQL Server 執行個體上。 

1. BizTalk 應用程式使用者 （一或多個對應到每個內含式主控件） 
2. BizTalk 外掛式主控件的使用者 （一或多個對應到每個外掛式主控件） 
3. BizTalk Server 系統管理員 
4. BizTalk Server B2B 操作員 
5. BizTalk Server 操作員 
6. SSO 系統管理員 
7. BAM 警示使用者 
8. BAM 管理 Web 服務使用者 
9. 規則引擎更新服務帳戶 

如果您已建立其他主機，或稍後再建立其他主機，則會在此程序建立新的 SQL 登入。 您必須確定在對應的複本上手動建立這些 SQL 登入。

下列的 SQL Server Agent 作業會關聯到 BizTalk Server 項目。 安裝在每一部伺服器上的作業會安裝及設定的功能而有所不同。 大部分的這些作業會在 BizTalk Server 組態期間建立的。 設定記錄傳送時，會建立數個項目。 這些工作需要複寫到其對應的 BizTalk 資料庫的 SQL Server 主控複本的每個執行個體。 這必須手動執行。 

- BizTalkMgmtDb 的工作︰ 
    - 備份 BizTalk Server (BizTalkMgmtDb) 
    - CleanupBTFExpiredEntriesJob_BizTalkMgmtDb 
    - 監控 BizTalk Server (BizTalkMgmtDb) 
- BizTalkMsgBoxDb 工作︰ 
    - MessageBox_DeadProcesses_Cleanup_BizTalkMsgBoxDb 
    - MessageBox_Message_Cleanup_BizTalkMsgBoxDb
    - MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb
    - MessageBox_Parts_Cleanup_BizTalkMsgBoxDb 
    - MessageBox_UpdateStats_BizTalkMsgBoxDb 
    - Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb 
    - PurgeSubscriptionsJob_BizTalkMsgBoxDb 
    - TrackedMessages_Copy_BizTalkMsgBoxDb 
- 其他 msgboxes 的工作
- BizTalkDTADb 工作︰ 
    - DTA 清除與封存 (BizTalkDTADb) 
- BizTalkRulesEngineDb 工作︰ 
    - Rules_Database_Cleanup_BizTalkRuleEngineDb 
- BAMAlertsApplication 工作︰ 
    - 0 或更多 DelAlertHistJob 

不同於 SQL 容錯移轉叢集執行個體，在可用性群組中所有複本都是作用中、 正在執行且可用。 SQL 代理程式作業會重複進行容錯移轉的每個複本上，它們對執行對應的複本，無論它是否是目前在主要角色或次要角色。 為了確保目前主要複本上才會執行這些工作，每一個步驟中的每個工作必須括在 IF 區塊中所示︰ 

    IF (sys.fn_hadr_is_primary_replica(‘dbname’) = 1)  
    BEGIN  
    …  
    END
  
取代 `‘dbname’` 依據工作設定為執行之對應的資料庫名稱。 下列範例會示範這項變更的 TrackedMessages_Copy_BizTalkMsgBoxDb BizTalkMsgBoxDb 上︰ 
 
 ![SQLAG_AgentJob](../core/media/sqlag-agentjob.gif)

### <a name="configure-biztalk-server-when-availability-groups-are-already-set-up"></a>設定 BizTalk Server 時已經設定可用性群組

1. 請檢查您的作業系統需求： 
* 所有**Windows Server 2012 R2**電腦，安裝[3090973 MSDTC hotfix](https://support.microsoft.com/kb/3090973) （開啟的知識庫文件）
* 所有**Windows Server 2016**電腦，可以讓[RemoteAccessEnabled 登錄機碼](https://support.microsoft.com/kb/3182294)（開啟的知識庫文件）
2. 請確定有至少四個不同 SQL 執行個體將主控各種 BizTalk 資料庫。 也應該在不同的 SQL 執行個體設定次要複本。 這會導致最少 8 個 SQL 執行個體 （1 主要和 1 次要複本的每個 4 的執行個體），以及至少 4 個可用性群組。 請參閱上面的圖例中這個可用性群組組態。 請確定可用性群組會使用建立 **每個資料庫的 DTC 支援** 選項，這樣您之後無法變更。 
3. 當設定 BizTalk Server，並指定 SQL 伺服器名稱，而不是實際的電腦名稱使用可用性群組接聽程式名稱。 這會在目前的主要複本上建立 BizTalk 資料庫、 登入，以及 SQL 代理程式作業。 
4. 停止 BizTalk 處理 （主控件執行個體，SSO 服務、 IIS、 規則引擎更新服務、 BAMAlerts 服務等等），並停止 SQL 代理程式作業。 
5. 現在加入個別的可用性群組的 BIzTalk 資料庫。 
6. 括住主體內的 SQL 代理程式作業步驟 `IF` （先前所述），確定它們執行只有當目標是主要複本的區塊。 
7. 編寫登入和 SQL Agent 作業，才能將它們對應的複本上的複寫。 
8. 複寫的 SQL DBMail 設定檔和對應的 SQL 執行個體裝載次要複本上 BAM 警示的帳戶。 
9. 如果您要加入其他的 messagebox 資料庫，或部署新 BAM 活動/檢視更新版本，然後新 SQL 作業會建立新的訊息方塊資料庫或目前的主要複本上的 BAM 警示資料庫。 請確定主要複本上進行編輯，然後在對應的次要複本上手動建立關聯。 

這項設定還可以使用裝載主要複本 SQL 執行個體。 在此情況下，BizTalk 設定之後，執行 `UpdateDatabase.vbs` 和 `UpdateRegistry.vbs` 完成上述步驟之後的 BizTalk 電腦上的指令碼。 這是下一節中詳細討論。  
 
### <a name="move-biztalk-server-databases-of-an-existing-biztalk-system-to-availability-groups"></a>將現有的 BizTalk 系統的 BizTalk Server 資料庫移至可用性群組

1. 請檢查您的作業系統需求： 
* 所有**Windows Server 2012 R2**電腦，安裝[3090973 MSDTC hotfix](https://support.microsoft.com/kb/3090973) （開啟的知識庫文件）
* 所有**Windows Server 2016**電腦，可以讓[RemoteAccessEnabled 登錄機碼](https://support.microsoft.com/kb/3182294)（開啟的知識庫文件）
2. 請確定有至少四個不同 SQL 執行個體將主控各種 BizTalk 資料庫。 也應該在不同的 SQL 執行個體設定次要複本。 這會導致最少 8 個 SQL 執行個體 （1 主要和 1 次要複本的每個 4 的執行個體），以及至少 4 個可用性群組。 請參閱上面的圖例中這個可用性群組組態。 請確定可用性群組會使用建立 **每個資料庫的 DTC 支援** 選項，這樣您之後無法變更。  
3. 停止 BizTalk 處理程序和 SQL 代理程式作業。 
4. 執行完整備份所有的 BizTalk 資料庫。 
5. 還原目前位於主要角色，可用性群組中的 SQL 執行個體上的 BizTalk 資料庫。 
6. 編寫登入和 SQL 代理程式上對應的 SQL 執行個體目前在可用性群組中的主要角色中的工作。  
7. 執行 `UpdateDatabase.vbs` 和 `UpdateRegistry.vbs` BizTalk 在機器上使用下列步驟的指令碼。 輸入可用性群組接聽程式做為輸入的更新資訊的 xml 中新的伺服器名稱。  
    1. 停止 BizTalk Server 上的所有 BizTalk 服務和企業單一登入服務。 SQL Server 上停止 SQL Agent 服務。 
    2. 在 BizTalk Server 中，編輯 SampleUpdateInfo.xml 下列資料夾中︰ 
 
        32 位元電腦︰ `%SystemRoot%\Program Files\Microsoft BizTalk Server 20xx\Schema\Restore`
 
        64 位元電腦︰ `%SystemRoot%\Program Files (x86)\Microsoft BizTalk Server 20xx\Bins32\Schema\Restore`
 
            1. Replace "SourceServer" with the source server name (old SQL Server hosting old databases).  
            2. Replace "DestinationServer" with the name of the destination server, which should be the availability group listener name.  
            3. If you have the BAMAnalysis, BAM databases or RuleEngineDB, uncomment the appropriate sections. 

    3. 開啟命令提示字元，然後移至︰ 
 
        32 位元電腦︰ `%SystemRoot%\Program Files\Microsoft BizTalk Server 20xx\Schema\Restore` 
 
        64 位元電腦︰ `%SystemRoot%\Program Files (x86)\Microsoft BizTalk Server 20xx\Bins32\Schema\Restore` 
 
        在命令提示字元執行︰  
    `cscript UpdateDatabase.vbs SampleUpdateInfo.xml`  
 
        在 BizTalk 群組中只有一部伺服器上執行 UpdateDatabase.vbs。 

    4. 將編輯的 SampleUpdateInfo.xml 檔案複製到此 BizTalk 群組中每一部 BizTalk Server 電腦的下列資料夾︰ 
 
        32 位元電腦︰ `%SystemRoot%\Program Files\Microsoft BizTalk Server 20xx\Schema\Restore` 
 
        64 位元電腦︰ `%SystemRoot%\Program Files (x86)\Microsoft BizTalk Server 20xx\Bins32\Schema\Restore` 
 
    5. 每一部 BizTalk Server 群組中，開啟命令提示字元，然後移至︰ 
 
        32 位元電腦︰ `%SystemRoot%\Program Files\Microsoft BizTalk Server 20xx\Schema\Restore`
 
        64 位元電腦︰ `%SystemRoot%\Program Files (x86)\Microsoft BizTalk Server 20xx\Bins32\Schema\Restore` 
 
        在命令提示字元執行︰  
    `cscript UpdateRegistry.vbs SampleUpdateInfo.xml` 
 
        在 BizTalk 群組中的每一部伺服器上執行 UpdateRegistry.vbs。 
 
8. 現在將資料庫移到個別的可用性群組。 
9. SQL DBMail 設定檔和帳戶 BAM 警示的 sql 執行個體裝載 BAMAlerts 資料庫複本的複寫。 
10. 將 SQL Agent 作業步驟，以確保它們執行只有當目標是主要 IF 區塊中的主體。 
11. 編寫登入和 SQL Agent 作業，才能將它們對應的複本上的複寫。 UpdateDatabase 指令碼也會更新為 Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb 與 TrackedMessages_Copy_BizTalkMsgBoxDb 作業中的伺服器名稱。 因此編寫 SQL 代理程式作業指令碼後才執行 UpdateDatabase 指令碼。 

## <a name="requirements"></a>需求 
* BizTalk Server 2016 Enterprise
* SQL Server 2016 Enterprise
* Windows Server 2012 R2
* Windows Server 2016 

### <a name="availability-group-listener-configured-with-non-default-port-1433"></a>使用非預設設定的可用性群組接聽程式通訊埠 (1433) 
使用 SQL 別名在 BizTalk Server 的電腦上。 

### <a name="supporting-availability-group-multi-subnet-failovers"></a>支援可用性群組多重子網路容錯移轉 
BizTalk Server 會使用 Microsoft OLE DB 資料庫連接，不支援**MultiSubnetFailover**連接選項。 BizTalk Server 不支援 `MultiSubnetFailover (=TRUE)` 連線 選項，而這可能會造成多重子網路容錯移轉期間更高的復原時間。 

### <a name="read-only-routing"></a>唯讀路由 
唯讀路由是指 SQL Server 可用性群組接聽程式的內送連接路由至次要複本設定為允許唯讀工作負載的能力。 

BizTalk 不使用唯讀路由的任何資料庫的連接。 這表示可用性複本上可用性群組中的 「 可讀取次要 」 選項 BizTalk 資料庫連接上沒有任何影響。 

### <a name="behavior-of-biztalk-server-host-instances-during-sql-server-failover"></a>SQL Server 容錯移轉期間的 BizTalk Server 主控件執行個體行為 
如果 SQL Server 可用性群組發生容錯移轉，可用性群組上的 BizTalk Server 資料庫會暫時無法使用。 

#### <a name="behavior-of-in-process-host-instances-during-sql-server-failover"></a>SQL Server 容錯移轉期間的內含式主控件執行個體行為 
如果無法使用 BizTalk Server 資料庫，然後同處理序的 BizTalk Server 主控件執行個體就會回收直到還原 SQL 伺服器的連線。 一旦還原 SQL Server 資料庫的連接之後，繼續正常處理文件。
 
#### <a name="behavior-of-isolated-host-instances-during-sql-server-failover"></a>SQL Server 容錯移轉期間的外掛式主控件執行個體行為 
如果 BizTalk Server 資料庫無法使用，便會暫停，隔離的 BizTalk Server 主控件執行個體，並在 BizTalk Server 應用程式記錄檔中會產生類似下面的錯誤︰ 

    All receive locations are being temporarily disabled because either the MessageBox or Configuration database is not available. When these databases become available, the receive locations will be automatically enabled.
 
一旦還原 SQL Server 資料庫的連接之後，類似於下列參考用訊息寫入至 BizTalk Server 應用程式記錄檔中，並處理文件然後繼續正常︰ 

    All receive locations are being enabled because both the MessageBox and Configuration databases are back online.

#### <a name="biztalk-server-log-shipping-for-disaster-recovery"></a>BizTalk Server 記錄傳送的嚴重損壞修復 
BizTalk Server 實作資料庫待命功能，透過使用資料庫記錄傳送。 BizTalk Server 記錄傳送自動化備份與還原的資料庫和其交易記錄檔，可讓待命伺服器，在繼續處理資料庫的實際執行資料庫伺服器的事件中，就會失敗。 

**可用性群組中的次要資料庫不是備份。** 繼續備份 BizTalk 資料庫，並使用 BizTalk Server 記錄傳送作業及其交易記錄檔。 BizTalk 記錄傳送實作的方式可確保一律會針對每個資料庫的目前主要複本執行備份。 BizTalk Server 記錄傳送作業不會接受可用性群組備份喜好設定。 

如果您要新增其他 BizTalk 資料庫至 BizTalk 資料庫備份作業，請務必使用可用性群組接聽程式名稱做為資料庫伺服器，這些設定在備份時。  
 
## <a name="references"></a>參考 
 
* [為 BizTalk Server 資料庫提供高可用性](../core/providing-high-availability-for-biztalk-server-databases.md)  
* [Microsoft Azure 虛擬機器的 Microsoft server software 支援](https://support.microsoft.com/kb/2721672)  
* [SQL Server 資料庫鏡像、磁碟區陰影複製服務和 AlwaysOn](../core/sql-server-database-mirroring-volume-shadow-copy-service-and-alwayson.md)  
* [AlwaysOn 可用性群組 (SQL Server) 概觀](https://msdn.microsoft.com/library/ff877884.aspx)  
* [跨資料庫交易支援資料庫鏡像或 AlwaysOn 可用性群組 (SQL Server)](https://msdn.microsoft.com/library/ms366279.aspx)  
* [SQL Server 的 Windows Server 2012 R2 中接收交易結果時，無法呼叫 reenlist](https://support.microsoft.com/kb/3090973)  
* [備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-biztalk-server-databases.md)  
* [如何移動 BizTalk Server 資料庫](../core/how-to-move-the-biztalk-server-databases.md)  
* [如何還原資料庫](../core/how-to-restore-your-databases.md)   
* [在多重子網路可用性群組的連線逾時](https://blogs.msdn.microsoft.com/alwaysonpro/2014/06/03/connection-timeouts-in-multi-subnet-availability-group/)  
 
## <a name="known-limitations"></a>已知的限制 

這些限制適用於 BizTalk Server，SQL Server AlwaysOn 可用性群組，以及 Azure 虛擬機器。 這些限制可能會也在未來可能無法取得解決。 

* 登入、 SQL Agent 作業，SQL DB 郵件設定檔和帳戶，無法管理可用性群組內。 這需要手動修改，以確定它們執行的主要複本的工作。 
* SQL Server Analysis Services 和 SQL Server Integration Services 不參與可用性群組。 如果不使用這項支援從 SQL Server，就沒有高可用性解決方案，這些 Azure 虛擬機器中。 BizTalk Server BAM 功能都依賴這些服務。 
* 可用性群組不支援在相同的 SQL 執行個體上的資料庫之間的 MSDTC。 因此，最小 8 SQL 執行個體，需要將 BizTalk 設定。 
* 若要解決 MSDTC 可用性群組，BizTalk 資料庫的限制可以使用至少兩部伺服器裝載四個 SQL 執行個體每個設定。 您也可以使用[與 Azure 負載平衡器的多個 IP 位址](https://docs.microsoft.com/azure/load-balancer/load-balancer-multivip-overview)。 因此，如果您想要使用單一伺服器上的通訊埠 1433年上的四個預設 SQL 執行個體，您需要四個 IP 位址。 如果您受限為一個 IP 位址，而且您想要裝載在相同伺服器上的多個 SQL 執行個體，請務必要自訂連接埠用於每個 SQL 執行個體。 
* BizTalk Server 無法使用唯讀路由。 
* BizTalk Server 不會設定 `MultiSubnetFailover` 連接屬性。 
* BizTalk 使用記錄傳送的備份工作將會永遠目標無論設定可用性群組的備份喜好設定的主要複本。 
 
