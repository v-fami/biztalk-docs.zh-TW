---
title: 最佳化資料庫檔案群組 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7dbed4d-95d6-4a41-a69e-737a6f2f5a82
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e48e475d3f8daf36cb6860393a4c4ff031a10e5a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003655"
---
# <a name="optimizing-filegroups-for-the-databases"></a>最佳化檔案群組的資料庫
檔案輸入/輸出 (I/O) 爭用通常是限制因素或在生產環境 BizTalk Server 環境中的瓶頸。 BizTalk Server 是一個非常資料庫需要大量的應用程式和 BizTalk Server 所使用的 SQL Server 資料庫，是需要大量的非常檔案 I/O。  
  
 本主題描述如何更有效地使用的檔案和檔案群組的最小化的檔案 I/O 競爭的相符項目，並改善 BizTalk Server 解決方案的整體效能的 SQL Server 的功能。  
  
## <a name="overview"></a>概觀  
 每個 BizTalk Server 解決方案最後會發生檔案 I/O 競爭，因為會增加輸送量。 I/O 子系統或儲存引擎，為任何關聯式資料庫的重要元件。 成功的資料庫實作通常需要在專案早期就進行周密的規劃。 這項規劃應考量下列問題：  
  
- 應使用哪種磁碟硬體，如 RAID (磁碟陣列) 裝置。 
  
- 如何分配使用檔案和檔案群組在磁碟上的資料。 如需使用 SQL Server 中的檔案與檔案群組的詳細資訊，請參閱[Database Files and Filegroups](https://docs.microsoft.com/sql/relational-databases/databases/database-files-and-filegroups)。
  
- 實作存取資料時提升效能的最佳的索引設計。 如需更多關於設計索引的詳細資訊，請參閱[設計索引](https://docs.microsoft.com/sql/relational-databases/sql-server-index-design-guide)。
  
- 如何設定 SQL Server 組態參數，以獲得最佳效能。 適用於 SQL Server 設定最佳的組態參數的相關資訊，請參閱[伺服器組態選項](https://docs.microsoft.com/sql/database-engine/configure-windows/server-configuration-options-sql-server)。 
  
  其中一個 BizTalk Server 的主要設計目的是為了確保訊息**從未**遺失。 若要降低訊息遺失的可能性，訊息會經常寫入 MessageBox 資料庫在處理訊息。 當協調流程處理訊息時，會將訊息寫入至 MessageBox 資料庫，在協調流程中每個持續點。 這些持續點會導致 MessageBox 的訊息和相關的狀態寫入實體磁碟。 在更高的輸送量，此持續性可能會導致相當大的磁碟爭用情況，並可能成為瓶頸。  
  
  進行最佳使用的檔案和 SQL Server 中的檔案群組功能可能會有效地處理檔案 IO 瓶頸，並改善在 BizTalk Server 解決方案的整體效能。 此最佳化只應該由有經驗的 SQL Server 資料庫系統管理員，並只在所有 BizTalk Server 資料庫已正確地備份使用。 應該在 BizTalk Server 環境中的所有 SQL Server 電腦上執行此最佳化。  
  
  SQL Server 檔案和檔案群組可以用於改善資料庫效能，因為這項功能可讓資料庫可建立跨多個磁碟、 多個磁碟控制卡或 RAID （獨立磁碟備援陣列） 系統中執行。 例如，若電腦有 4 個磁碟，您可以建立由 3 個資料檔和 1 個記錄檔組成的資料庫，每一個檔案各在一個磁碟上。 存取資料時，四個讀寫頭可以同時存取以平行方式的資料。 大幅加快資料庫作業。 實作 SQL Server 磁碟的硬體解決方案的詳細資訊，請參閱 < 資料庫效能 >，SQL Server 線上叢書中在[ http://go.microsoft.com/fwlink/?LinkID=71419 ](http://go.microsoft.com/fwlink/?LinkID=71419)。  
  
  此外，檔案和檔案群組啟用資料位置選項，可以在特定的檔案群組中建立資料表。 這可改善效能，因為指定的資料表的所有檔案 I/O 可都導向特定的磁碟。 比方說，使用量大的資料表可放置在檔案群組，在一個磁碟，並在資料庫中其他較少存取的資料表可以位於不同的檔案，放在第二個磁碟上的另一個檔案群組中。  
  
  檔案 IO 瓶頸會相當詳細討論[資料庫層中的瓶頸](../technical-guides/bottlenecks-in-the-database-tier.md)。 最常見檔案 I/O (磁碟 I/O) 是一個瓶頸的指標是 「 實體磁碟： Average Disk Queue Length"計數器的值。 當 「 實體磁碟： Average Disk Queue Length"計數器的值大於約 3 個任何指定的磁碟上的任何 SQL 伺服器時，然後檔案 I/O 可能是瓶頸。  
  
  如果套用檔案群組的最佳化，無法解決檔案 I/O 瓶頸問題，則可能需要增加藉由新增額外的實體或 SAN 的磁碟機的磁碟子系統的輸送量。  
  
  本主題說明如何以手動方式套用檔案和檔案群組的最佳化，但這些最佳化可以也要編寫指令碼。 本主題的結尾會提供範例 SQL 指令碼。 請務必請注意，此指令碼會需要修改，以容納檔案、 檔案群組和任何指定的 BizTalk Server 解決方案使用的 SQL Server 資料庫的磁碟組態。  
  
 
## <a name="databases-created-with-a-default-biztalk-server-configuration"></a>使用預設的 BizTalk Server 組態建立的資料庫  
 依據設定 BizTalk Server 中，最多 13 個不同資料庫可能在 SQL Server 中建立，且所有這些資料庫會建立在預設檔案群組時，會啟用功能。 SQL Server 的預設檔案群組是主要檔案群組，除非使用 ALTER DATABASE 命令變更預設檔案群組。 下表列出如果設定 BizTalk Server 時，會啟用所有功能，SQL Server 中建立的資料庫。  
  
### <a name="biztalk-server-databases"></a>BizTalk Server 資料庫  
  
||||  
|-|-|-|  
|**[資料庫備份]**|**預設的資料庫名稱**|**說明**|  
|設定資料庫|BizTalkMgmtDb|中央中繼資訊存放區的所有 BizTalk Server 群組中的 BizTalk Server 執行個體。|  
|BizTalk MessageBox 資料庫|BizTalkMsgBoxDb|儲存訂閱述詞。 它是主應用程式平台，並保留每個 BizTalk Server 主控件佇列和狀態資料表。 MessageBox 資料庫也儲存訊息及訊息屬性。|  
|BizTalk 追蹤資料庫|BizTalkDTADb|儲存商務和狀況監控 BizTalk Server 追蹤引擎所追蹤的資料。|  
|BAM 分析資料庫|BAMAnalysis|保留商務活動彙總的歷程記錄資料的 SQL Server Analysis Services 資料庫。|  
|BAM 星狀結構描述資料庫|BAMStarSchema|轉換用於 OLAP 處理從商務活動監控收集的資料。 使用 BAM 分析資料庫時，需要此資料庫。|  
|BAM 主要匯入資料庫|BAMPrimaryImport|在活動執行個體之後，會儲存商務活動，然後查詢的進度與資料的事件。 此資料庫也會執行即時彙總。|  
|BAM 封存資料庫|BAMArchive|儲存訂閱述詞。 BAM 封存資料庫會將 BAM 主要匯入資料庫中的商務活動資料累積降到最低。|  
|SSO 資料庫|SSODB|安全地儲存組態資訊的接收位置。 將資訊儲存為 SSO 分支機構應用程式，以及所有分支機構應用程式的加密的使用者認證。|  
|規則引擎資料庫|BizTalkRuleEngineDb|存放庫：<br /><br /> -原則，也就是相關規則的集合。<br />-詞彙，規則中關於資料參考的使用者易記、 網域特定名稱的集合。|  
|追蹤 Analysis Server 管理資料庫|BizTalkAnalysisDb|儲存商務和狀況監控 OLAP cube。|  
  
## <a name="separation-of-data-files-and-log-files"></a>分隔資料檔和記錄檔  
 如先前所述，BizTalk Server 組態預設值會置於同一個檔案的預設檔案群組中的 MessageBox 資料庫。 根據預設，MessageBox 資料庫的資料和交易記錄檔會放在相同的磁碟機和路徑。 這是為了配合使用單一磁碟系統。 單一檔案/檔案群組/磁碟組態**並非最佳**在生產環境中。 為了達到最佳效能，資料檔案和記錄檔應置於不同的磁碟。  
  
> [!NOTE]  
>  記錄檔絕不能做為檔案群組的一部分。 記錄空間將與資料空間分別管理。  
  
## <a name="the-8020-rule-of-distributing-biztalk-server-databases"></a>BizTalk Server 資料庫的散發的 80/20 規則  
 在大部分的 BizTalk Server 解決方案，因為磁碟 I/O 競爭或資料庫爭用，競爭的主要來源是 BizTalk Server MessageBox 資料庫。 這是在單一和多個 MessageBox 的情況下，則為 true。 它是值的合理假設最高達 80%的發佈 BizTalk 資料庫，將會衍生自最佳化的 MessageBox 資料檔案和記錄檔。 在下面詳細的範例案例著重於最佳化 MessageBox 資料庫之資料檔案。 這些步驟可以再遵循其他資料庫如有需要比方說，如果解決方案需要大量追蹤，則也可以最佳化追蹤資料庫。  
  
## <a name="manually-adding-files-to-the-messagebox-database-step-by-step"></a>手動將檔案加入至 MessageBox 資料庫中，逐步  
 本節描述可供遵循以手動方式將檔案新增至 MessageBox 資料庫的步驟。 在此範例會新增三個檔案群組，然後檔案新增至每個檔案群組將檔案發佈的 MessageBox，跨多個磁碟。   
  
> [!NOTE]  
>  基於本指南中所進行的效能測試，已透過將 BizTalk Server 效能最佳化指南的一部分發行的指令碼使用進行最佳化檔案群組。 下列步驟會提供僅供參考。  
  
### <a name="manually-adding-files-to-the-messagebox-database-on-sql-server"></a>手動將檔案加入至 SQL Server 上的 MessageBox 資料庫
  
1. 開啟**SQL Server Management Studio**顯示**連接到伺服器** 對話方塊。  
  
     ![SQL Server 管理登入畫面](../technical-guides/media/641a03f4-362c-4dde-8c9d-ac313d8881e3.gif "641a03f4-362c-4dde-8c9d-ac313d8881e3")  
  
2.  在 **伺服器名稱**欄位**連接到伺服器** 對話方塊中，輸入裝載 BizTalk Server MessageBox 資料庫中，SQL Server 執行個體的名稱，然後按一下**Connect**  按鈕以顯示**Microsoft SQL Server Management Studio**  對話方塊。  
  
     在**物件總管**窗格中的 SQL Server Management Studio 中，展開**資料庫**，來檢視此 SQL Server 執行個體的資料庫。  
  
     ![SQL Server Management Studio，物件總管](../technical-guides/media/81f13912-fedc-48c3-9669-c18863e637b1.gif "81f13912-fedc-48c3-9669-c18863e637b1")  
  
3.  以滑鼠右鍵按一下要新增的檔案，然後按一下資料庫**屬性**顯示**資料庫屬性**資料庫 對話方塊。  
  
     ![SQL Server 資料庫屬性 對話方塊](../technical-guides/media/82ae7c11-5b3a-4312-876c-70876abdd65c.gif "82ae7c11-5b3a-4312-876c-70876abdd65c")  
  
4.  在 **資料庫屬性**對話方塊中，選取**檔案群組**頁面。 按一下 **新增**按鈕，以建立 BizTalkMsgBoxDb 資料庫的其他檔案群組。 在下列範例中，會加入三個額外的檔案群組。  
  
     ![SQL Server，將檔案群組加入資料庫中](../technical-guides/media/6be47c0e-06c3-45d9-bce2-a42453da7d19.gif "6be47c0e-06c3-45d9-bce2-a42453da7d19")  
  
5.  在 **[資料庫屬性]** 對話方塊中，選取 **[檔案]** 頁面。  
  
     按一下 **新增**按鈕來建立其他檔案加入檔案群組，然後按一下**確定**。 MessageBox 資料庫現在會分散到多個磁碟，這將會提供顯著的優勢，透過單一磁碟組態中。  
  
     在下列範例中，稍早建立的檔案群組的每個建立檔案時，每個檔案會放在不同的磁碟。  
  
     ![SQL Server，將檔案加入檔案群組](../technical-guides/media/d5d5c5df-d483-4f01-8128-f98228de51b9.gif "d5d5c5df-d483-4f01-8128-f98228de51b9")  
  
## <a name="sample-sql-script-for-adding-filegroups-and-files-to-the-biztalk-messagebox-database"></a>加入 BizTalk MessageBox 資料庫中的檔案群組和檔案的範例 SQL 指令碼  
 下列範例 SQL 指令碼執行以手動方式完成上一節中的相同工作。  
此範例指令碼會假設不同的邏輯磁碟機 G 透過 J.存在指令碼會建立檔案群組和每個檔案群組的檔案，並將放在 J 磁碟機上的記錄檔。  
  
> [!NOTE]  
>  SQL Server 循序寫入其記錄檔，因為沒有任何效能優勢，實現藉由建立多個 SQL Server 資料庫的記錄檔。  
  
```  
-- Filegroup changes are made using the master database  
USE [master]  
GO  
  
-- Script-wide declarations  
DECLARE @CommandBuffer nvarchar(2048)  
DECLARE @FG1_Path nvarchar(1024)  
DECLARE @FG2_Path nvarchar(1024)  
DECLARE @FG3_Path nvarchar(1024)  
DECLARE @Log_Path nvarchar(1024)  
  
-- Set the default path for all filegroups  
SET @FG1_Path = N'G:\BizTalkMsgBoxDATA\'  
SET @FG2_Path = N'H:\BizTalkMsgBoxDATA\'  
SET @FG3_Path = N'I:\BizTalkMsgBoxDATA\'  
SET @Log_Path = N'J:\BizTalkMsgBoxLog\'  
  
ALTER DATABASE [BizTalkMsgBoxDb] ADD FILEGROUP [BTS_MsgBox_FG1]  
SET @CommandBuffer = N'ALTER DATABASE [BizTalkMsgBoxDb] ADD FILE ( NAME = N''BizTalkMsgBoxDb_FG1'', FILENAME = N''' + @FG1_Path +   
N'BizTalkMsgBoxDb_FG1.ndf'' , SIZE = 102400KB , MAXSIZE = UNLIMITED, FILEGROWTH = 10240KB ) TO FILEGROUP [BTS_MsgBox_FG1]'  
EXECUTE (@CommandBuffer)  
  
ALTER DATABASE [BizTalkMsgBoxDb] ADD FILEGROUP [BTS_MsgBox_FG2]  
SET @CommandBuffer = N'ALTER DATABASE [BizTalkMsgBoxDb] ADD FILE ( NAME = N''BizTalkMsgBoxDb_FG1'', FILENAME = N''' + @FG2_Path +   
N'BizTalkMsgBoxDb_FG2.ndf'' , SIZE = 102400KB , MAXSIZE = UNLIMITED, FILEGROWTH = 10240KB ) TO FILEGROUP [BTS_MsgBox_FG2]'  
EXECUTE (@CommandBuffer)  
  
ALTER DATABASE [BizTalkMsgBoxDb] ADD FILEGROUP [BTS_MsgBox_FG3]  
SET @CommandBuffer = N'ALTER DATABASE [BizTalkMsgBoxDb] ADD FILE ( NAME = N''BizTalkMsgBoxDb_FG1'', FILENAME = N''' + @FG3_Path +   
N'BizTalkMsgBoxDb_FG3.ndf'' , SIZE = 102400KB , MAXSIZE = UNLIMITED, FILEGROWTH = 10240KB ) TO FILEGROUP [BTS_MsgBox_FG3]'  
EXECUTE (@CommandBuffer)  
  
ALTER DATABASE [BizTalkMsgBoxDb] MODIFY FILE ( NAME = N'BizTalkMsgBoxDb_log', SIZE = 10240KB , MAXSIZE = UNLIMITED, FILEGROWTH = 10240KB )  
  
GO -- Completes the previous batch, as necessary  
```  
  
 下列範例 SQL 指令碼可用來將特定的檔案群組設定為預設檔案群組：  
  
```  
USE [BizTalkMsgBoxDb]  
GO  
declare @isdefault bit  
SELECT @isdefault=convert(bit, (status & 0x10)) FROM sysfilegroups WHERE groupname=N'BTS_MsgBox_FG1'  
if(@isdefault=0)  
ALTER DATABASE [BizTalkMsgBoxDb] MODIFY FILEGROUP [BTS_MsgBox_FG1] DEFAULT  
GO  
```  
  
 指令碼的優點是，指令碼可以快速地執行多個工作、 精確地說，即可重現和降低人為錯誤的可能性。 指令碼的缺點是撰寫不正確的指令碼執行可能造成嚴重的問題，可能需要從頭重新設定 BizTalk Server 資料庫。 因此，它的 SQL 指令碼，如本主題中列出的指令碼範例會徹底的首要之前，先測試在生產環境中執行。