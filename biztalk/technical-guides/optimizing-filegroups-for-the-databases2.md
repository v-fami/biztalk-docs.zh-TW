---
title: "最佳化檔案群組 Databases2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d7fa4c9-e504-4f43-a308-517a4a574c26
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f2f3ffab64795f8000af37cdc07c3754bb1fb5bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-filegroups-for-the-databases"></a>最佳化檔案群組的資料庫
檔案輸入/輸出 (I/O) 競爭的情況通常是限制因素或在生產環境 BizTalk Server 環境中的瓶頸。 BizTalk Server 資料庫非常密集的應用程式，而接著，BizTalk Server 所使用的 SQL Server 資料庫檔案最需要大量 I/O。 本主題描述如何最有效地利用檔案及檔案群組功能的 SQL Server 檔案 I/O 競爭次數降到最低，並改善 BizTalk Server 解決方案的整體效能。  
  
## <a name="overview"></a>概觀  
 每個 BizTalk Server 解決方案最終將會遇到檔案 I/O 競爭，提升輸送量。 I/O 子系統或儲存引擎是任何關聯式資料庫的重要元件。 成功的資料庫實作通常需要在專案早期就進行周密的規劃。 這項規劃應考量下列問題：  
  
-   應使用哪種磁碟硬體，如 RAID (磁碟陣列) 裝置。 如需使用 RAID 硬體解決方案的詳細資訊，請參閱[有關硬體為基礎的解決方案](http://go.microsoft.com/fwlink/?LinkID=113944)(http://go.microsoft.com/fwlink/?LinkID=113944) 中 SQL Server 線上叢書 》。  
  
-   如何分配使用檔案和檔案群組的磁碟上的資料。 如需有關如何使用 SQL Server 2008 R2 中的檔案和檔案群組的詳細資訊，請參閱[Files and Filegroups](http://go.microsoft.com/fwlink/?LinkID=69369) (http://go.microsoft.com/fwlink/?LinkID = 69369) 和[了解檔案與檔案群組](http://go.microsoft.com/fwlink/?LinkID=96447)(http://go.microsoft.com/fwlink/?LinkID = 96447) 中 SQL Server 線上叢書 》。  
  
-   實作最佳的索引設計來存取資料時改善效能。 如需設計索引的詳細資訊，請參閱[設計索引](http://go.microsoft.com/fwlink/?LinkID=96457)(http://go.microsoft.com/fwlink/?LinkID=96457) 中 SQL Server 線上叢書 》。  
  
-   如何設定 SQL Server 組態參數，以獲得最佳效能。 適用於 SQL Server 設定最佳的設定參數的相關資訊，請參閱[最佳化伺服器效能](http://go.microsoft.com/fwlink/?LinkID=71418)(http://go.microsoft.com/fwlink/?LinkID=71418) 中 SQL Server 線上叢書 》。  
  
 BizTalk server 的主要設計目標之一是確保訊息是**從未**遺失。 若要降低訊息遺失的可能性，訊息會經常寫入至 MessageBox 資料庫在處理訊息。 當協調流程處理訊息時，訊息會寫入協調流程中每個持續點的 MessageBox 資料庫中。 這些持續點會導致 MessageBox 實體磁碟寫入的訊息和相關的狀態。 在更高的輸送量，此持續性會造成相當大的磁碟爭用情況，而可能成為瓶頸。  
  
 進行最佳使用的檔案，並有效地解決檔案 IO 瓶頸，改善在 BizTalk Server 解決方案的整體效能可能會在 SQL Server 中的檔案群組功能。  
  
> [!NOTE]  
>  此最佳化只應該由有經驗的 SQL Server 資料庫系統管理員和只有之後所有 BizTalk Server 資料庫已正確地備份。 應該在 BizTalk Server 環境中的所有 SQL Server 電腦上執行此最佳化。  
  
 SQL Server 的檔案和檔案群組可用來改善資料庫效能，因為這項功能可讓資料庫來建立跨多個磁碟、 多個磁碟控制卡或 RAID （獨立磁碟備援陣列） 系統。 例如，若電腦有 4 個磁碟，您可以建立由 3 個資料檔和 1 個記錄檔組成的資料庫，每一個檔案各在一個磁碟上。 存取資料時，四個讀寫頭可以同時存取平行的資料。 大幅加快資料庫作業。 如需有關實作 SQL Server 磁碟的硬體解決方案的詳細資訊，請參閱[資料庫效能](http://go.microsoft.com/fwlink/?LinkID=71419)(http://go.microsoft.com/fwlink/?LinkID=71419) 中 SQL Server 線上叢書 》。  
  
 此外，檔案和檔案群組啟用資料位置選項，可以在特定的檔案群組中建立資料表。 這可改善效能，因為指定資料表的所有檔案 I/O 都可都導向特定的磁碟。 比方說，經常使用的資料表可以放在檔案群組，在某個磁碟，並在資料庫中其他較少存取的資料表可以位於不同的檔案放在第二個磁碟上的另一個檔案群組中。  
  
 檔案 I/O 瓶頸中相當大的詳細資料 > 主題中討論[資料庫層中的瓶頸](../technical-guides/bottlenecks-in-the-database-tier.md)。 最常見檔案 I/O （磁碟 I/O） 是一個瓶頸的指標是 「 實體磁碟： 平均磁碟佇列長度 」 計數器的值。 「 實體磁碟： 平均磁碟佇列長度 」 計數器的值大於約 3 的任何執行 SQL Server 的電腦上任何指定的磁碟，然後檔案 I/O 時，可能是效能瓶頸。  
  
 如果套用檔案群組的最佳化，不會解決檔案 I/O 瓶頸問題，可能必須加入額外的實體或 SAN 磁碟機來增加磁碟子系統的輸送量。  
  
 本主題描述如何將手動套用 file 和 filegroup 最佳化，但也可撰寫這些最佳化。 中提供的範例 SQL 指令碼[BizTalk Server MessageBox 資料庫檔案群組 SQL 指令碼](../technical-guides/biztalk-server-messagebox-database-filegroups-sql-script.md)。  
  
> [!NOTE]  
>  請務必注意，此指令碼會需要修改，以配合檔案、 檔案群組，以及任何指定的 BizTalk Server 解決方案的 SQL Server 資料庫所使用的磁碟組態。  
  
> [!NOTE]  
>  本主題也描述如何建立多個檔案和檔案群組的 BizTalk MessageBox 資料庫。 建議的檔案和檔案群組的所有 BizTalk Server 資料庫的完整清單，請參閱 「 附錄 B 「 [BizTalk Server 資料庫最佳化](http://go.microsoft.com/fwlink/?LinkID=101578)白皮書 (http://go.microsoft.com/fwlink/?LinkID=101578)。  
  
> [!NOTE]  
>  即使[BizTalk Server 資料庫最佳化](http://go.microsoft.com/fwlink/?LinkID=101578)白皮書 (http://go.microsoft.com/fwlink/?LinkID=101578) 以寫入[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]納入考量，相同的原則套用至[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]。  
  
## <a name="databases-created-with-a-default-biztalk-server-configuration"></a>使用預設的 BizTalk Server 組態建立的資料庫  
 依據 13 不同資料庫中設定 BizTalk Server 中，可能會建立在 SQL Server 及所有的這些資料庫會建立預設檔案群組中時，會啟用功能。 SQL Server 的預設檔案群組是主要檔案群組，除非使用 ALTER DATABASE 命令來變更預設檔案群組。 下表列出的資料庫所建立的 SQL Server 中，如果設定 BizTalk Server 時，會啟用所有功能。  
  
### <a name="biztalk-server-databases"></a>BizTalk Server 資料庫  
  
||||  
|-|-|-|  
|**資料庫**|**預設的資料庫名稱**|**說明**|  
|設定資料庫|BizTalkMgmtDb|中央中繼資訊存放區的所有 BizTalk Server 群組中的 BizTalk Server 執行個體。|  
|BizTalk MessageBox 資料庫|BizTalkMsgBoxDb|儲存訂閱述詞。 它是主機平台，並會保留每個 BizTalk Server 主控件佇列和狀態資料表。 MessageBox 資料庫也儲存訊息及訊息屬性。|  
|BizTalk 追蹤資料庫|BizTalkDTADb|儲存商務和狀況監控 BizTalk Server 追蹤引擎所追蹤的資料。|  
|BAM 分析資料庫|BAMAnalysis|SQL Server Analysis Services 資料庫的彙總的歷程記錄資料會保留商務活動。|  
|BAM 星狀結構描述資料庫|BAMStarSchema|轉換的 OLAP 處理從商務活動監控所收集的資料。 使用 BAM 分析資料庫時，此資料庫是必要的。|  
|BAM 主要匯入資料庫|BAMPrimaryImport|活動執行個體之後，會儲存商務活動，然後查詢的進度和資料的事件。 此資料庫也會執行即時彙總。|  
|BAM 封存資料庫|BAMArchive|儲存訂閱述詞。 BAM 封存資料庫可將 BAM 主要匯入資料庫中的商務活動資料累積降到最低。|  
|SSO 資料庫|SSODB|安全地儲存組態資訊的接收位置。 儲存資訊的 SSO 分支機構應用程式，以及所有分支機構應用程式已加密的使用者認證。|  
|規則引擎資料庫|BizTalkRuleEngineDb|儲存機制：<br /><br /> -原則，也就是相關規則的集合。<br />-詞彙，規則中關於資料參考的使用者易記、 網域特定名稱的集合。|  
|BizTalk 基底 EDI 資料庫|BizTalkEDIDb|儲存追蹤及處理資料的 EDI 文件。|  
|人力工作流程服務管理資料庫|BizTalkHwsDb|會儲存 BizTalk 「 人力工作流程服務所需的系統管理資訊。|  
|交易夥伴管理資料庫|TPM|商務活動服務 (BAS) 交易夥伴資料存放區。|  
|追蹤 Analysis Server 管理資料庫|BizTalkAnalysisDb|儲存商務和狀況監控 OLAP cube。|  
  
## <a name="separation-of-data-files-and-log-files"></a>分隔資料檔和記錄檔  
 如前文所述，預設的 BizTalk Server 組態會將 MessageBox 資料庫置於單一檔案中的預設檔案群組。 根據預設，MessageBox 資料庫的資料和交易記錄檔會放在相同的磁碟機和路徑。 這是為了配合單一磁碟系統。 單一檔案/檔案群組磁碟組態是**並非最佳**實際執行環境中。 為了達到最佳效能，資料檔案和記錄檔應放在不同磁碟上。  
  
> [!NOTE]  
>  記錄檔絕不能做為檔案群組的一部分。 記錄空間將與資料空間分別管理。  
  
## <a name="the-8020-rule-of-distributing-biztalk-server-databases"></a>BizTalk Server 資料庫的散發的 80/20 規則  
 在大部分的 BizTalk Server 解決方案，因為磁碟 I/O 競爭或資料庫競爭競爭的主要來源是 BizTalk Server MessageBox 資料庫。 這是在單一和多重 MessageBox 的案例中，則為 true。 它是值的合理假設在最多可達 80%的散發 BizTalk 資料庫會值的衍生自最佳化的 MessageBox 資料檔案和記錄檔。 下列所述的範例案例會著重於最佳化 MessageBox 資料庫的資料檔案。 這些步驟然後是其他資料庫，視需要。 例如，如果解決方案需要大量的追蹤，追蹤資料庫，也可以最佳化。  
  
## <a name="manually-adding-files-to-the-messagebox-database-step-by-step"></a>手動將檔案加入至 MessageBox 資料庫中，逐步  
 本節的主題描述可供遵循以手動將檔案加入至 MessageBox 資料庫的步驟。 在這個範例會加入三個檔案群組，然後將檔案加入至每個檔案群組，以便將檔案發佈的 MessageBox 中，跨多個磁碟。 在此範例中，在上執行的步驟[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]。  
  
### <a name="manually-adding-files-to-the-messagebox-database-on-sql-server-2008-r2"></a>手動將檔案加入至 MessageBox 資料庫的 SQL Server 2008 R2  
 **請遵循下列步驟來手動將檔案加入至 MessageBox 資料庫的 SQL Server 2008 R2:**  
  
1.  按一下**啟動**，指向 **程式**，指向   **[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]** ，然後按一下 [ **SQL Server Management Studio**顯示**連接到伺服器**] 對話方塊。  
  
     ![SQL Server 2008 R2 &#45;登入畫面](../technical-guides/media/sqlserver2008r2-loginscreen.gif "Sqlserver2008r2-kbxxxxxx Loginscreen")  
  
2.  在**伺服器名稱**編輯方塊**連接到伺服器**對話方塊方塊中，輸入裝載 BizTalk Server MessageBox 資料庫的 SQL Server 執行個體的名稱，然後按一下**連接**顯示 SQL Server Management Studio。 在**物件總管 中**窗格中的 SQL Server Management Studio，展開**資料庫**以檢視資料庫的 SQL Server 的這個執行個體。  
  
     ![SQL Server 2005 Management Studio，物件總管 中](../technical-guides/media/81f13912-fedc-48c3-9669-c18863e637b1.gif "81f13912-fedc-48c3-9669-c18863e637b1")  
  
3.  以滑鼠右鍵按一下要新增檔案，然後再按資料庫**屬性**顯示**資料庫屬性**資料庫 對話方塊。  
  
     ![SQL Server 2005 資料庫屬性 對話方塊](../technical-guides/media/82ae7c11-5b3a-4312-876c-70876abdd65c.gif "82ae7c11-5b3a-4312-876c-70876abdd65c")  
  
4.  在**資料庫屬性**對話方塊中，選取**檔案群組**頁面。 若要建立 BizTalkMsgBoxDb 資料庫的其他檔案群組，請按一下**新增**。 在下列範例中，會加入三個額外的檔案群組。  
  
     ![將檔案群組加入資料庫中的 SQL Server 2005](../technical-guides/media/6be47c0e-06c3-45d9-bce2-a42453da7d19.gif "6be47c0e-06c3-45d9-bce2-a42453da7d19")  
  
5.  在 **[資料庫屬性]** 對話方塊中，選取 **[檔案]** 頁面。  
  
     若要建立其他檔案加入檔案群組，請按一下**新增**，然後按一下 **確定**。 MessageBox 資料庫現在都會分散到多個磁碟、 將提供顯著的效能優勢，透過單一磁碟組態中。  
  
     在下列範例中，針對每個稍早建立的檔案群組建立一個檔案，每個檔案放在不同磁碟上。  
  
     ![SQL Server 2005，新增檔案至檔案群組](../technical-guides/media/d5d5c5df-d483-4f01-8128-f98228de51b9.gif "d5d5c5df-d483-4f01-8128-f98228de51b9")  
  
## <a name="sample-sql-script-for-adding-filegroups-and-files-to-the-biztalk-messagebox-database"></a>BizTalk MessageBox 資料庫中加入檔案群組和檔案的範例 SQL 指令碼  
 本指南包含將檔案群組和檔案加入至 BizTalk Server MessageBox 資料庫的 SQL 指令碼。  
  
> [!NOTE]  
>  SQL Server 循序寫入其記錄檔，因為沒有任何效能優勢，藉由建立多個 SQL Server 資料庫的記錄檔，才能實現。  
  
 若要執行此指令碼，請遵循下列步驟：  
  
1.  按一下**啟動**，指向 **程式**，指向   **[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]** ，然後按一下 [ **SQL Server Management Studio**顯示**連接到伺服器**] 對話方塊。  
  
2.  在**伺服器名稱**編輯方塊**連接到伺服器**對話方塊方塊中，輸入裝載 BizTalk Server MessageBox 資料庫的 SQL Server 執行個體的名稱，然後按一下**連接**以顯示 [SQL Server Management Studio] 對話方塊。  
  
3.  在 SQL Server Management Studio 中，按一下 **檔案**功能表上，指向**新增**，然後按一下 **使用目前的連接查詢**SQL 查詢編輯器啟動。  
  
4.  複製的範例指令碼，從[BizTalk Server MessageBox 資料庫檔案群組 SQL 指令碼](../technical-guides/biztalk-server-messagebox-database-filegroups-sql-script.md)到 查詢編輯器。  
  
5.  編輯指令碼以符合您的 BizTalk Server 環境中的參數，然後執行指令碼。  
  
 指令碼的優點是指令碼可以快速地執行多個工作，可以明確地說，重現和減少人為錯誤的可能性。 指令碼的缺點是，撰寫不正確的指令碼的執行都可能會造成嚴重的問題，可能需要從頭重新設定 BizTalk Server 資料庫。  
  
> [!IMPORTANT]  
>  它是責 SQL 指令碼，例如本指南中的範例指令碼會徹底測試，才能在生產環境中執行。  
  
## <a name="see-also"></a>另請參閱  
 [最佳化資料庫效能](../technical-guides/optimizing-database-performance.md)