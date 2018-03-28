---
title: 使用的記錄檔 (PAL) 工具的效能分析 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d563aa7d-102d-4fe6-a892-66794feaf83b
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f289cdf157100dc69feb468f789a9ebb76764a1
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="using-the-performance-analysis-of-logs-pal-tool"></a>使用記錄檔 (PAL) 工具的效能的分析
PAL （效能分析的記錄檔） 工具讀入效能監視器計數器記錄檔 （任何已知的格式），並且會使用複雜，但已知臨界值 （提供） 加以分析。 此工具會產生 HTML 基礎報表，以圖形方式圖表重要的效能計數器，並擲回警示時已超過閾值。 臨界值最初根據 Microsoft 產品團隊，包括所定義的臨界值[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，而且屬於 Microsoft 支援。 此工具不是傳統的效能分析的取代，但它會自動分析的效能計數器記錄足以協助節省時間。 PAL 工具：  
  
-   分析臨界值的效能計數器記錄  
  
-   很大的效能記錄檔  
  
-   識別[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和作業系統效能計數器瓶頸，藉由分析臨界值  
  
-   擴充，以進行分析上的任何效能計數器  
  
-   可用來協助撰寫您自己的計數器  
  
 PAL 是在免費下載[ http://go.microsoft.com/fwlink/?linkid=98098 ](http://go.microsoft.com/fwlink/?linkid=98098)。 它需要 Microsoft 的記錄檔剖析器。 記錄檔剖析器是功能強大、 靈活的工具，提供通用的查詢文字為基礎的資料，例如記錄檔、 XML 檔案和 CSV 檔案，以及索引鍵的資料來源來存取 Windows 作業系統，例如事件記錄檔、 登錄、 檔案系統和作用中Directory® 目錄服務。 若要使用此工具來查詢大量的記錄資訊。 您可以下載記錄檔剖析器工具在[ http://go.microsoft.com/fwlink/?linkid=85574 ](http://go.microsoft.com/fwlink/?linkid=85574)。  
  
## <a name="using-pal-with-performance-counter-logs-in-different-languages"></a>在不同的語言使用 PAL 與效能計數器記錄  
 PAL 工具會分析僅以英文語言的效能計數器記錄檔。 若要使用其他語言中的效能計數器記錄檔 [PAL] 工具，您必須先轉換記錄檔，以英文語言。 您可以使用**Perfmon 記錄轉譯程式**工具位於[ http://go.microsoft.com/fwlink/?LinkId=158802 ](http://go.microsoft.com/fwlink/?LinkId=158802)翻譯成英文原始的效能計數器記錄檔。  
  
## <a name="understanding-the-pal-tool-report-for-microsoft-biztalk-server-2010"></a>了解 Microsoft BizTalk Server 2010 的 PAL 工具報告  
 PAL 工具提供 Windows 作業系統，Microsoft SQL Server，效能監視器記錄分析臨界值和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 本章節描述大部分的 BizTalk Server 閾值報表 PAL 工具中分析。  
  
> [!NOTE]  
>  本主題很長，以便可以在一個地方，以方便參考包含有關 PAL 工具的完整資訊。  
  
 PAL 工具會報告下列分析和臨界值。  
  
|分析的類型和名稱|分析描述|  
|----------------------------|--------------------------|  
|： 磁碟的磁碟可用空間的核心傾印|這項分析會檢查以確定有足夠的磁碟空間，用於作業系統磁碟的所有記憶體傾都印。 如果可用磁碟空間不足，作業系統將無法建立 memory.dmp 時，這是要分析根本原因的核心傾印檔案。|  
|磁碟： 邏輯/實體磁碟介面分析|這項分析會查看每個實體磁碟的閒置時間。 多閒置磁碟，使用磁碟越低。 此計數器適合在使用一個磁碟的邏輯磁碟中。 "%閒置時間 」 報告的範例間隔期間磁碟閒置時間百分比。<br /><br /> 參考： 統治出磁碟繫結的問題 [http://go.microsoft.com/fwlink/?linkid=50669](http://go.microsoft.com/fwlink/?linkid=50669)|  
|磁碟： 邏輯/實體磁碟讀取/寫入延遲分析|Windows 偵測到磁碟的效能瓶頸最可靠的方式是藉由測量其回應時間。 如果回應時間大於.025 （25 毫秒為單位），也就是保守的臨界值，然後值得注意的速度並影響使用者的效能問題可能會發生。 如需詳細資訊，請參閱邏輯/實體磁碟讀取/寫入延遲分析本主題中。|  
|磁碟： Logical Disk Transfers/sec|「 磁碟 Transfers/sec"是讀取的速率和寫入磁碟上的作業。 這項分析檢查以查看是否有任何的邏輯磁碟的臨界值會顯示不佳的回應時間 （大於 25 毫秒 I/O 作業的回應時間）。 如果為 true，則每秒磁碟轉移操作應該等於或高於 80。 如果沒有，則需要調查磁碟架構。 不佳的磁碟 I/O 的最常見原因是多載 SAN 上的 LUN。 如需詳細資訊，請參閱 Logical Disk Transfers/sec 本主題中。|  
|磁碟： LogicalDisk %可用空間|「 %可用空間 」 是已在所選邏輯磁碟機上可用的總可用空間百分比。 少於 30%的可用磁碟空間之前，應該不會影響效能。 使用磁碟機的 70%時，剩餘的可用空間是磁碟的位於更接近中間，都是磁碟的在較低的效能層級運作的磁碟磁針。 可用磁碟空間不足可能會造成嚴重的磁碟效能。<br /><br /> 參考： NT 伺服器和磁碟子系統效能 [http://go.microsoft.com/fwlink/?linkid=106783](http://go.microsoft.com/fwlink/?linkid=106783)|  
|磁碟： 處理 IO Data Operations/sec 和處理 IO 其他作業數/秒分析|這些計數器計算所有的 I/O 活動，包括檔案、 網路及裝置 I/o 處理序所產生。 當處理序正在執行超過 1,000 個我 / O 的每秒，並且將它標示為警告，請檢查這些分析。 這些分析最適合用於與其他分析，例如磁碟分析相互關聯來判斷哪些處理程序可能會陷入 I/O 活動。|  
|可用記憶體的記憶體：|這項分析會檢查是否總可用記憶體偏低 – 可用的 10%的警告和重大在可用的 5%。 警告也會收到警示，每小時 10 MB 的遞減趨勢偵測到時，可指出潛在的即將進行的記憶體不足。 實體記憶體不足可能會造成更高特殊權限的模式 CPU 和系統的延遲。 如需詳細資訊，請參閱可用 MemoryAnalysis 本主題中。|  
|記憶體： 可用系統分頁表項目|Free System Page Table Entries (PTE) 是由系統目前未使用的分頁表項目數目。 這項分析會判斷系統是否已執行超出 PTE 的方式是檢查是否有少於 5000 可用 PTE 的警告是否少於 10,000 可用 PTE 的。 缺乏足夠 PTE 可能會導致整個系統停止回應。 也請注意，/3GB 參數將會大幅降低可用 PTE 數量。 如需詳細資訊，請參閱可用系統分頁資料表項目分析本主題中。|  
|記憶體： 記憶體流失偵測|這項分析會判斷是否的任何程序正在耗用大量系統的記憶體和處理程序是否在經過一段時間的記憶體耗用量增加。 處理序耗用是記憶體的正常的只要在處理序傳回回系統的記憶體。 尋找增加圖表中的趨勢。 遞增趨勢上很長一段時間可能表示記憶體流失。 「 私用位元組 」 是目前的大小，以位元組為單位，此處理序已配置的記憶體不能與其他處理序共用。 這項分析會檢查 10 MB 的每小時和 5 MB 的每小時增加的趨勢。 您可以使用這項分析中與 PAL 中的可用記憶體分析相互關聯。 如需詳細資訊，請參閱記憶體流失偵測分析本主題中。|  
|記憶體： 控制代碼遺漏偵測|這項分析會檢查所有來判斷多少處理每個處理序已開啟，並懷疑來判斷是否控制代碼遺漏。 包含大量的控制代碼和/或積極增加的趨勢的程序可能表示有控制代碼流失，通常會導致記憶體流失。 此程序目前開啟的控制代碼總數會等於這個處理序中的每個執行緒目前開啟的控制代碼總和。<br /><br /> 參考： 偵錯診斷工具 v1.1，在 [http://go.microsoft.com/fwlink/?linkid=106784](http://go.microsoft.com/fwlink/?linkid=106784)|  
|記憶體： 記憶體 Pages Input/sec|「 Pages Input/sec"是從磁碟為解決硬體分頁錯誤而讀取分頁的速率。 處理程序是指不在其工作集或其他位置中的實體記憶體，因而必須從磁碟擷取的虛擬記憶體分頁時，就會發生硬體分頁錯誤。 這項分析會檢查是否有 10 個以上每秒的分頁檔案讀取。|  
|Memory: Memory Pages/sec|這項分析會檢查是否"Pages/sec"很高 （超過 1,000 個）。 如果高，然後系統可能記憶體不足嘗試將頁面上的記憶體到磁碟。 「 頁/sec"是在讀取或寫入為解決硬體分頁錯誤而對磁碟頁面的速率。 這個計數器是導致整個系統延遲的錯誤種類的主要指示器。  您可以使用這項分析中可用的記憶體分析與 PAL 中的記憶體流失偵測分析相互關聯。 如果所有這些分析會擲回警示，在相同的時間，然後這可能表示系統用完記憶體，並根據推測的處理程序牽涉到 PAL 中的記憶體流失偵測分析中所述步驟分析。<br /><br /> 如需詳細資訊，請參閱本主題中的記憶體 Pages/sec 分析。|  
|記憶體： 記憶體系統快取常駐位元組|「 系統快取常駐位元組 」 是大小，以位元組為單位的檔案系統快取中的可分頁作業系統程式碼。 此值只包含目前實體頁面，而且不包含任何非目前駐留的虛擬記憶體分頁。 這個值是元件的 「 記憶體\\\System 程式碼常駐位元組 」 代表所有目前正在實體記憶體的可分頁作業系統程式碼。 這個計數器會顯示最後觀察到的值它不是平均值。 這項分析會檢查每小時 10 MB 的遞增趨勢。 在負載下，伺服器可能會以快取的 I/O 活動，例如磁碟使用的系統快取。 用於相互關聯處理序 IO Data Operations/sec 與其他處理序 IO 作業數/秒 PAL 中的分析。<br /><br /> 參考： 檔案快取效能和調整在 [http://go.microsoft.com/fwlink/?linkid=106786](http://go.microsoft.com/fwlink/?linkid=106786)|  
|記憶體： 集區未分頁位元組|"Pool Nonpaged 的 Bytes 」 是以位元組為單位的非分頁集區，不能寫入的物件系統記憶體區域的大小，磁碟、 但只要已配置就必須保留在實體記憶體中。 這項分析會檢查以查看系統即將推出，接近 最大的集區未分頁記憶體大小。 它會透過評估下列因素納入考量的集區大小/3 GB、 實體記憶體大小，以及 32 位元/64 位元，然後判斷值是否大於估計的集區大小的 60%。 如果系統變成接近最大大小，系統可能會導致系統寬的停止回應。<br /><br /> Boot.ini 檔案中的 3 GB 交換器選項會大幅降低此記憶體集區的大小。<br /><br /> 如需詳細資訊，請參閱 Pool Non-Paged 位元組分析本主題中。|  
|記憶體： 集區分頁位元組|這項分析會檢查以查看系統即將推出，接近 最大的集區的分頁記憶體大小。 它會透過評估下列因素納入考量的集區大小/3 GB、 實體記憶體大小，以及 32 位元/64 位元，然後判斷值是否大於估計的集區大小的 60%。 如果系統變成接近最大大小，系統可能會導致系統寬的停止回應。<br /><br /> Boot.ini 檔案中的 3 GB 交換器選項會大幅降低此記憶體集區的大小。<br /><br /> 如需詳細資訊，請參閱集區的分頁位元組分析本主題中。|  
|記憶體： 處理序執行緒計數|這項分析會檢查所有的處理序，來決定處理程序是否有超過 500 個執行緒，以及如果 50 執行緒每小時增加的執行緒數目。 大量執行緒和/或積極增加的趨勢的處理序可能表示執行緒遺漏通常會導致記憶體遺漏或高內容切換。 高內容切換，會導致高特殊權限模式 CPU。|  
|記憶體： 處理程序工作組|「 工作集 」 是目前的大小，以位元組為單位的工作集，此程序。 工作集是由程序中執行緒最近觸及的記憶體分頁的集合。 如果電腦中的可用記憶體超過閾值，頁面會留在程序的工作集，即使他們沒有使用中。 當可用記憶體低於臨界值時，會從工作集修剪頁面。 若您需要這些然後再將其寫回工作集退出主記憶體。 這項分析會檢查遞增趨勢的 10 MB 以上每個處理程序中。 在相互關聯使用 PAL 中的可用記憶體分析。<br /><br /> 參考： 偵測在記憶體瓶頸 [http://go.microsoft.com/fwlink/?linkid=106787](http://go.microsoft.com/fwlink/?linkid=106787)|  
|網路： 網路輸出佇列長度分析|這項分析會檢查網路介面卡上等候多少執行緒。 如果有很多執行緒正在等待網路介面卡，然後系統會可能讓網路飽和 I/O 由於網路延遲或網路頻寬。 「 輸出佇列長度 」 （以封包） 的輸出封包佇列長度。 延遲會指出如果這是長度大於二，並且應該找到並盡快解決瓶頸。 網路輸出佇列的一般原因包括大量的小型網路要求和網路延遲。|  
|網路： 網路使用率分析|「 Bytes Total/sec"是在傳送及接收每個網路介面卡，包括框架字元位元組的速率。 "Network Interface\Bytes Received/sec"是"Network Interface\Bytes Received/sec"和"Network Interface\Bytes Sent/sec"的總和。 此計數器可協助您了解在您的網路介面卡的流量是否已飽和，以及您是否需要新增另一個網路介面卡。 您可以識別問題的速度取決於類型有以及您是否與其他應用程式共用頻寬的網路。 這項分析會將"Bytes Total/sec"轉換成位元，並比較計算網路使用率的網路介面卡的目前頻寬。 接下來，它會檢查使用量超過 50%。<br /><br /> 參考： 測量在.NET 應用程式效能 [http://go.microsoft.com/fwlink/?linkid=106788](http://go.microsoft.com/fwlink/?linkid=106788)|  
|分頁檔： 分頁檔案使用量百分比和 %使用率正達尖峰|以百分比表示的使用中的頁面檔案執行個體數量。 另請參閱 「 處理程序\\\Page File Bytes"。 這項分析會檢查是否使用的百分比大於 70%。|  
|處理器： 處理器使用率分析和處理序過度佔用處理器使用|此計數器是處理器活動的主要指示器，並顯示在取樣間隔期間觀察到的忙碌時間平均百分比。 其計算方式是監視該服務處於非使用中的時間，並從 100%減去該值。 這項分析會檢查使用量大於每個處理器上的 60%。 如果是的話，判斷它是否高使用者模式 CPU 或高特殊權限的模式。 如果懷疑 CPU 高特殊權限的模式，則會看到在 PAL 中的特殊權限模式 CPU 分析。 如果懷疑有使用者模式處理器瓶頸，請考慮使用處理程序的程式碼剖析工具分析造成高 CPU 耗用率的函式。|  
|處理器： 處理器佇列長度|這項分析會判斷是否平均處理器佇列長度會超過處理器的數目。 如果是的話，這可能表示發生處理器瓶頸。 使用這項分析中使用特殊權限模式 CPU 分析和過多的處理器使用 PAL 中的程序分析的相互關聯。 如需詳細資訊，請參閱處理器佇列長度分析本主題中。|  
|處理器： 特殊權限的模式 CPU 分析|此計數器表示執行緒在特權模式下執行的時間的百分比。 當您的應用程式呼叫作業系統函式 （例如來執行檔案或網路 I/O，或配置記憶體） 時，這些作業系統函式會執行特殊權限模式。 這項分析會檢查是否有權限的模式 CPU 耗用超過 30%的總 CPU。 如果，則 CPU 耗用量可能是另一個以外的處理器，例如網路、 記憶體或磁碟 I/O 瓶頸所造成。 用於相互關聯的處理器: %Interrupt Time 及處理器： 高內容切換在 PAL 中的分析。 如需詳細資訊，請參閱特殊權限模式 CPU 分析本主題中。|  
|處理器： 中斷時間|"%Interrupt Time 是處理器花費在接收與處理硬體插斷取樣間隔期間的時間。 這個值是產生插斷，例如系統時鐘、 滑鼠、 磁碟驅動程式、 資料通訊線路、 網路介面卡及其他週邊裝置的裝置活動的間接指示器。 在已完成工作，或需要注意時，這些裝置通常插斷處理器。 在插斷期間會暫停執行一般執行緒。 大多數的系統時鐘會插斷處理器每隔 10 毫秒，建立中斷活動的背景。 在此計數器指出可能硬體問題。 這項分析會檢查 「 插斷時間百分比 」 大於百分之 30。 如果發生這種情況，請考慮更新此警示的相互關聯的硬體的裝置驅動程式。<br /><br /> 參考： 測量在.NET 應用程式效能 [http://go.microsoft.com/fwlink/?linkid=106788](http://go.microsoft.com/fwlink/?linkid=106788)|  
|處理器： 高內容切換|當高優先順序的執行緒優先執行較低優先順序的執行緒目前正在執行或高優先權執行緒會封鎖，就會發生內容切換。 多執行緒共用相同的優先權層級，就會發生內容切換的高層級。 這通常表示太多執行緒會在系統上處理器的競爭。 一般而言，內容切換率小於每個處理器每秒 5000 就不值得耽心。 如果內容切換率超過 15,000 每個處理器每秒，就將條件約束。 如需詳細資訊，請參閱高內容切換分析本主題中。|  
|Microsof BizTalk Server: BizTalk 凍結協調流程|當許多長時間執行商務程序在相同的時間執行時，記憶體和效能問題可能會進行。 協調流程引擎透過「凍結」和「解除凍結」協調流程執行個體來解決這些問題。 凍結是將協調流程狀態序列化到 SQL Server 資料庫中的程序。 解除凍結是此程序的反向︰ 還原序列化的協調流程從資料庫上次執行狀態。 凍結是藉由減少必須一次在記憶體中產生的協調流程數目，來將系統資源的使用降至最低。 因此，dehyrations 儲存記憶體耗用量，但可執行相當耗費資源的作業。 這項分析會檢查 dehydrations 10 倍或更多。 如果是這樣，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可能記憶體不足 （虛擬或實體），請執行高效能的協調流程數等待在訊息上或凍結設定不正確。<br /><br /> 參考： 協調流程凍結和解除凍結在  [http://go.microsoft.com/fwlink/?LinkId=155284](http://go.microsoft.com/fwlink/?LinkId=155284)|  
|Microsoft BizTalk Server: BizTalk 高資料庫工作階段|此計數器有兩個可能的值： normal (0) 或超過閾值 (1)。 這項分析會檢查值為 1。 如果是這樣，BizTalk 已超過允許的資料庫工作階段數目的臨界值。 這個值是由 「 每一 CPU 的資料庫連線 」 中的值的 BizTalk 主控件節流設定所控制的。 「 資料庫每一 CPU 的連線 」 為並行資料庫工作階段數目上限 （每一 CPU) 節流開始前允許。 您可以使用 biztalk： 訊息代理程式的效能物件類別下的資料庫工作階段效能計數器來監視作用中資料庫連線數目。 此參數只會影響輸出訊息節流。 如需詳細資訊，請參閱 BizTalk 高資料庫工作階段分析本主題中。|  
|Microsoft BizTalk Server: BizTalk 高資料庫大小|此計數器將設定為值 1，如果其中一個列出的資料庫臨界值中的訊息計數的條件發生。 根據預設主機訊息資料庫節流閾值中的計數是設定為 50000，將會觸發節流狀況，在下列情況下的值：<br /><br /> 訊息發佈的工作、 狀態和擱置的佇列訂閱的主控件的主控件執行個體-總數超過 50,000。<br />-多工緩衝處理表格或追蹤資料表中的訊息數目超過 500,000 訊息。<br /><br /> 如果發生這種情況，請考慮採取的動作，將會減少在資料庫中的訊息數目。 例如，請在 SQL Server 工作[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]正在執行不會發生錯誤，而且使用中的 [群組中樞] 頁面[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台來判斷訊息增多是否因大量擱置的訊息。 如需詳細資訊，請參閱 BizTalk 高資料庫大小分析本主題中。|  
|Microsoft BizTalk Server: BizTalk 高內含式訊息計數|這項分析會檢查以判斷是否發生這種節流高內含式訊息計數計數器。 如果是的話，請考慮調整"訊息每一 CPU 的內含式 」 設定。 此參數只會影響輸出訊息節流。 在停用以每一 CPU 的內含式訊息數目為基礎的節流"訊息每一 CPU 的內含式 」 設定中輸入值為 0。 「 內含式訊息每一 CPU 」 設定的預設值是 1000。 請注意，此值也可能會影響低度延遲的訊息和 （或） BizTalk 資源的效率。 如需詳細資訊，請參閱 BizTalk 高內含式訊息計數分析本主題中。|  
|Microsoft BizTalk Server: BizTalk 高訊息傳遞速率|這項分析會檢查 1 高訊息傳遞速率計數器中的值。 高訊息傳遞速率可能因高處理複雜性、 慢速輸出配接器或瞬間的系統資源不足。 如需詳細資訊，請參閱 BizTalk 高訊息傳遞速率分析本主題中。|  
|Microsoft BizTalk Server: BizTalk 高訊息發佈速率|輸入主控件節流，也稱為 「 訊息發佈節流中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，套用至主控件執行個體包含接收配接器或協調流程發佈訊息至 MessageBox 資料庫。 這項分析會檢查 1 高訊息發佈速率計數器中的值。 如果發生這種情況，然後資料庫無法跟上發佈速率的訊息到 BizTalk MessageBox 資料庫。<br /><br /> 參考：<br /><br /> -裝載在節流效能計數器 [http://go.microsoft.com/fwlink/?LinkId=155285](http://go.microsoft.com/fwlink/?LinkId=155285)<br />-如何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]實作主控件節流在 [http://go.microsoft.com/fwlink/?LinkId=155286](http://go.microsoft.com/fwlink/?LinkId=155286)<br />訊息發佈節流設定 對話方塊 [http://go.microsoft.com/fwlink/?LinkId=155287](http://go.microsoft.com/fwlink/?LinkId=155287)<br />-什麼是主控件節流？在 [http://go.microsoft.com/fwlink/?LinkID=154694](http://go.microsoft.com/fwlink/?LinkID=154694)|  
|Microsoft BizTalk Server: BizTalk 高程序記憶體|節流臨界值 設定的 BizTalk 處理序記憶體使用量會是記憶體的與工作集大小和處理序的總可用虛擬記憶體的總和，如果輸入從 1 到 100 的值使用百分比。 當指定某個百分比值時，則會以定期間隔重新計算程序記憶體閾值。 這項分析會檢查 1 高的處理序記憶體計數器的值。 如需詳細資訊，請參閱 BizTalk 高的處理序記憶體分析本主題中。|  
|Microsoft BizTalk Server: BizTalk 高系統記憶體|BizTalk 的實體記憶體使用量節流臨界值設定為輸入則是從 1 到 100 相較於可用的實體記憶體的值如果總數量的記憶體耗用量的百分比。 如果輸入大於 100 的值，此設定也可以是以 mb 為單位的可用實體記憶體總數。 輸入值為 0 時可停用以實體記憶體使用量為基礎的節流。 預設值是 0。 如需詳細資訊，請參閱 BizTalk 高系統記憶體分析本主題中。|  
|Microsoft BizTalk Server: BizTalk 高執行緒計數|[每一 CPU 的執行緒] 是在主機處理程序包括使用配接器之執行緒的執行緒總數。 如果超過此閾值，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會嘗試減少 EPM 執行緒集區和訊息代理程式 」 執行緒集區的大小。 在高負載可能導致建立大量執行緒的情況時，應啟用以執行緒為基礎的節流。 此參數會同時影響輸入和輸出節流。 執行緒為基礎的節流預設為停用。 如需詳細資訊，請參閱 BizTalk 高執行緒計數分析本主題中。|  
|Microsoft BizTalk Server: BizTalk 主控件佇列長度|BizTalk 主控件佇列長度會追蹤特定主控件佇列中的訊息總數。 您可以使用長度的大小 （也就是 ' BizTalk:MessageBox:HostCounters:Host 佇列 – 長度 '） 來提供深度的正在排在內部，以顯示為個別主機的佇列深度的訊息數目的更詳細的檢視。 此計數器可以用來判斷特定主機的瓶頸。 假設唯一主機使用的是每個傳輸，這可以是很有幫助判斷潛在傳輸瓶頸。 這項分析會檢查平均佇列長度大於 1。 主控件佇列長度是在目標主機的彙總所有佇列的 (工作 Q，狀態 Q 暫停 Q) 的記錄計數加權的佇列長度。<br /><br /> 參考： BizTalk Server 2006： 管理在成功的效能實驗室[ http://go.microsoft.com/fwlink/?linkid=104152 ](http://go.microsoft.com/fwlink/?linkid=104152) **附註：**這份技術白皮書也會套用到 BizTalk 伺服器。|  
|Microsoft BizTalk Server: BizTalk 主控件擱置郵件佇列長度|此計數器會追蹤特定主控件的擱置的訊息總數。 擱置的訊息是訊息或協調流程的執行個體，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]已停止處理因錯誤而在系統或訊息。 一般來說，因系統錯誤而擱置的執行個體會在系統問題獲得解決後繼續。 通常，因訊息有問題而擱置的執行個體不會繼續執行，而且必須修正訊息本身，並重新提交至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。<br /><br /> 擱置的訊息佇列是包含的錯誤或失敗期間發生未處理的工作項目。 訊息擱置佇列會儲存訊息直到修正和重新處理或是刪除後為止。 這項分析會檢查擱置的任何的訊息項目。 增加的趨勢可能表示嚴重處理錯誤。<br /><br /> 參考： BizTalk Server 2004： 監視和疑難排解於 [http://go.microsoft.com/fwlink/?linkid=108771](http://go.microsoft.com/fwlink/?linkid=108771)|  
|BizTalk Server: BizTalk 閒置協調流程|目前由主控件執行個體裝載而閒置的協調流程執行個體數。 此計數器是指不進行進度，但不是可凍結的協調流程。 可能會發生這種情況下，協調流程遭到封鎖時，等待接收，接聽或不可部分完成的交易的延遲時間。 如果大量的非可凍結的協調流程會累積，BizTalk 可能用盡記憶體。<br /><br /> 凍結是將協調流程狀態序列化到 SQL Server 資料庫中的程序。 解除凍結是此程序的反向︰ 還原序列化的協調流程從資料庫上次執行狀態。 凍結是藉由減少必須一次在記憶體中產生的協調流程數目，來將系統資源的使用降至最低。 引擎會儲存狀態以凍結執行個體，並釋出執行個體所需的記憶體。 透過凍結休眠的協調流程執行個體，引擎就可以讓大量的長時間執行之商務程序在相同電腦上同時執行。 這項分析會檢查遞增趨勢的一個每小時的閒置協調流程。<br /><br /> 參考： 協調流程凍結和解除凍結在  [http://go.microsoft.com/fwlink/?LinkId=155284](http://go.microsoft.com/fwlink/?LinkId=155284)|  
|BizTalk Server: BizTalk 輸入延遲|平均延遲 （毫秒），傳訊引擎收到文件從配接器之前發佈到 MessageBox 的時間。 降低延遲很重要的 BizTalk 中，某些使用者因此追蹤時間文件花費輸入配接器中很重要。 如需詳細資訊，請參閱 BizTalk 輸入延遲分析本主題中。|  
|BizTalk Server: BizTalk 訊息傳遞延遲|這是加諸於 （適用於訊息傳遞進行節流處理） 每個訊息傳遞批次的目前延遲 （毫秒） （毫秒）。 節流就而言，在發行或處理訊息，根據訊息是傳入或傳出時套用延遲。 延遲期間為節流狀況的嚴重性成正比。 較高的嚴重性節流狀況將會起始與較低的嚴重性節流狀況更長的節流期間。 透過狀況變更時的節流機制，這個延遲期間可在特定範圍內上下調整。 目前的延遲期間會公開透過訊息傳遞延遲 （毫秒） 」 和 「 訊息發佈延遲 （毫秒） 效能計數器與 biztalk： 訊息代理程式的效能物件類別相關聯。 這項分析會檢查訊息傳遞延遲大於 5 秒。 由於高負載過重節流，可能表示長訊息傳遞延遲。<br /><br /> 參考： 如何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]實作主控件節流在 [http://go.microsoft.com/fwlink/?LinkId=155286](http://go.microsoft.com/fwlink/?LinkId=155286)|  
|BizTalk Server: BizTalk 訊息傳遞節流狀態|BizTalk 訊息傳遞節流狀態是節流的主要指標。 它是旗標，指出系統是否正在進行節流訊息傳遞 （影響 XLANG 訊息處理及輸出傳輸）。 節流狀況會指示計數器的數值。 如需詳細資訊，請參閱本主題中的 BizTalk 訊息傳遞節流狀態分析。|  
|BizTalk Server: BizTalk 訊息發佈延遲|導致節流的訊息發佈的每個符合批次中的延遲。 節流就而言，在發行或處理訊息，根據訊息是傳入或傳出時套用延遲。 延遲期間為節流狀況的嚴重性成正比。 較高的嚴重性節流狀況將會起始與較低的嚴重性節流狀況更長的節流期間。 透過狀況變更時的節流機制，這個延遲期間可在特定範圍內上下調整。 目前的延遲期間會公開透過訊息傳遞延遲 （毫秒） 」 和 「 訊息發佈延遲 （毫秒） 效能計數器與 biztalk： 訊息代理程式的效能物件類別相關聯。 這項分析會檢查訊息發佈延遲大於 5 秒。 由於高負載過重節流，可能表示長訊息傳遞延遲。<br /><br /> 參考： 如何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]實作主控件節流在 [http://go.microsoft.com/fwlink/?LinkId=155286](http://go.microsoft.com/fwlink/?LinkId=155286)|  
|BizTalk Server: BizTalk MessageBox 資料庫連線失敗|此效能計數器是資料庫連線嘗試的主控件執行個體啟動後失敗的數目。 如果裝載 BizTalk 資料庫的 SQL Server 服務因故無法使用，資料庫叢集資源從作用中的電腦傳輸到被動電腦。 在容錯移轉過程中，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]服務執行個體發生資料庫連線失敗，並自動重新啟動以重新連接到資料庫。 正在運作的資料庫電腦 (先前為被動電腦) 會在容錯移轉期間獲得資源後，開始處理資料庫連接。 如需詳細資訊，請參閱 BizTalk MessageBox 資料庫連線失敗分析本主題中。|  
|BizTalk Server: BizTalk 傳訊延遲： 要求的回應延遲|傳訊引擎從配接器收到要求文件，到回應文件傳回該配接器之間的平均延遲 (毫秒)。 請參閱顯示 BizTalk 輸入延遲分析中測量延遲是方式，本主題中的圖表。 假設在低延遲的環境，這項分析會檢查要求-回應延遲大於 5 秒。 這可能表示輸入配接器和輸出配接器之間處理延遲。<br /><br /> 參考：<br /><br /> -要求/回應訊息在 [http://go.microsoft.com/fwlink/?LinkId=155288](http://go.microsoft.com/fwlink/?LinkId=155288)<br />BizTalk Server 2006： 使用 SOAP 配接器在 BizTalk Server 2006 中的擴充性案例研究 [http://go.microsoft.com/fwlink/?linkid=108774](http://go.microsoft.com/fwlink/?linkid=108774)|  
|BizTalk Server: BizTalk 訊息發佈節流狀態|BizTalk 訊息發佈節流狀態是節流的主要指標。 旗標，指出系統是否正在進行節流 （影響 XLANG 訊息處理及輸入的傳輸） 的訊息發佈它。 如需詳細資訊，請參閱 BizTalk 訊息發佈節流狀態分析本主題中。|  
|BizTalk Server: BizTalk 協調流程已暫停/秒|擱置的訊息是訊息或協調流程的執行個體，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]已停止處理因錯誤而在系統或訊息。 一般來說，因系統錯誤而擱置的執行個體會在系統問題獲得解決後繼續。 通常，因訊息有問題而擱置的執行個體不會繼續執行，而且必須修正訊息本身，並重新提交至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統。 這項分析會檢查任何擱置的訊息/協調流程。<br /><br /> 參考： BizTalk Server 2004： 監視和疑難排解於 [http://go.microsoft.com/fwlink/?linkid=108771](http://go.microsoft.com/fwlink/?linkid=108771)|  
|BizTalk Server: BizTalk 協調流程已完成/秒|這是已完成的 BizTalk 協調流程數秒。 這是很好的指標，指出正在處理 BizTalk 多少輸送量。 這項分析會提供僅限統計資料。<br /><br /> 參考： BizTalk Server 2006： 使用 SOAP 配接器在 BizTalk Server 2006 中的擴充性案例研究 <br />[http://go.microsoft.com/fwlink/?linkid=108774](http://go.microsoft.com/fwlink/?linkid=108774)|  
|BizTalk Server: BizTalk 協調流程捨棄|自從主控件執行個體啟動之後，已從記憶體捨棄的協調流程執行個體數。 如果引擎無法保存協調流程的狀態，即可予以捨棄。 這項分析會檢查有任何已捨棄的訊息。<br /><br /> 參考： BizTalk 核心引擎的部落格<br />[http://go.microsoft.com/fwlink/?linkid=108775](http://go.microsoft.com/fwlink/?linkid=108775)|  
|BizTalk Server: BizTalk 協調流程常駐在記憶體中|目前由主控件執行個體裝載的協調流程執行個體數。 這項分析會檢查遞增趨勢常駐記憶體，且是否超過 50%的記憶體中駐留的協調流程不是可凍結的協調流程中。 如需詳細資訊，請參閱 BizTalk 協調流程常駐在記憶體分析。|  
|BizTalk Server: BizTalk 配接器輸出延遲|這是平均延遲的秒數從當配接器取得傳訊引擎從配接器傳送的時間之前的文件。 請參閱顯示 BizTalk 輸入延遲分析中測量延遲是方式，本主題中的圖表。 假設在低延遲的環境，這項分析會檢查延遲大於 5 秒的輸出配接器中的平均。 這可能表示之傳輸的輸出配接器在此主控件執行個體中的訊息處理延遲。 如果多個輸出配接器存在於此主控件執行個體，請考慮將它們分割到他們自己的主機，來判斷哪些輸出配接器都有高延遲。<br /><br /> 參考：<br /><br /> -要求/回應訊息在 [http://go.microsoft.com/fwlink/?LinkId=155288](http://go.microsoft.com/fwlink/?LinkId=155288)<br />BizTalk Server 2006： 使用 SOAP 配接器在 BizTalk Server 2006 中的擴充性案例研究 [http://go.microsoft.com/fwlink/?linkid=108774](http://go.microsoft.com/fwlink/?linkid=108774)<br />識別在 BizTalk 層中的瓶頸 [http://go.microsoft.com/fwlink/?LinkId=155289](http://go.microsoft.com/fwlink/?LinkId=155289)<br />BizTalk Server 2004： 針對在傳訊低度延遲的效能微調 [http://go.microsoft.com/fwlink/?linkid=108777](http://go.microsoft.com/fwlink/?linkid=108777)|  
|BizTalk Server: BizTalk 暫止訊息數目|接收到 MessageBox 收到尚未認可的訊息數目。 暫止訊息數目會有已提取到記憶體，並傳遞至 XLANG 協調流程中，但尚未已處理訊息。 這種情況下沒有遺失資料。  將訊息傳遞到協調流程是多步驟程序，只是位在資料庫中的多工緩衝處理資料表中的訊息執行個體。 這些暫止訊息計數為內含式訊息。因此，需要大量的記憶體中可能會導致記憶體節流系統上。 調整 [內部訊息佇列大小] 設定可以協助控制的暫止訊息數目。 每個 CPU 的內含式訊息設定將會影響當節流會叫用時就會發生大量的暫止訊息數目。 在 BizTalk 管理主控台的主機內容中找到這些設定。 這項分析會檢查只有此計數器會顯示統計資料。<br /><br /> 參考： 在協調流程引擎效能計數器 [http://go.microsoft.com/fwlink/?LinkId=155290](http://go.microsoft.com/fwlink/?LinkId=155290)|  
|BizTalk Server: BizTalk 持續點/秒|平均每秒保存的協調流程執行個體數。 協調流程引擎會在不同點儲存執行中協調流程執行個體的狀態。 如果需要解除凍結協調流程執行個體、 從控制的關閉、 啟動或從非預期的關機復原，它會從上次保存點執行協調流程執行個體。 以保存協調流程執行個體，所有物件直接或間接參考至您的協調流程的執行個體 （像是透過其他物件） 必須是可序列化。 為訊息保存頻率 （資料需要保存的時間的數字） 增加，整體效能會降低。 作用中，每個持續點是來回存取資料庫，因此盡可能減少持續點的頻率避免或合併持續點。 請參閱下方有關持續點發生時的參考。 這項分析會檢查有 10 個以上的持續點，每秒平均。 這是一般的起始點。<br /><br /> 參考：<br /><br /> -在協調流程中的持續性 [http://go.microsoft.com/fwlink/?LinkId=155291](http://go.microsoft.com/fwlink/?LinkId=155291)<br />持續性和在協調流程引擎 [http://go.microsoft.com/fwlink/?LinkId=155292](http://go.microsoft.com/fwlink/?LinkId=155292)|  
|BizTalk Server: BizTalk 私用位元組|這是主控件執行個體，其相當於"\Process （*） \Private 位元組 」 效能計數器的配置私用記憶體 mb。 這項分析會判斷是否任何主控件執行個體正在耗用龐大的系統記憶體和主控件執行個體是否持續一段時間的記憶體耗用量增加。 本主題，如需詳細資訊，請參閱 BizTalk 私用位元組分析。|  
|BizTalk Server: BizTalk 多工緩衝處理表格大小|MessageBox 多工緩衝處理表格包含系統中的每個訊息的記錄 (作用中或等候 「 記憶體回收 」)。 監視此資料表中的資料列數目和增加系統負載提供簡單的方法來尋找最大持續輸送量時，每秒接收的訊息數目。 只要增加輸入的負載可能是 1） 多工緩衝處理資料表會無止盡成長或 2） 的每個第二個富饒、 何者較早，和也就是您的最大持續輸送量收到的訊息數目。 總而言之，不論其他指標，此量值可讓您快速輕鬆的方式，來評估您的系統正在既是否。 當 BizTalk 多工緩衝處理表格大小增加的趨勢時，然後節流因為不平衡的訊息傳遞速率 （輸入的速率超過輸出速率） 或可能是由於資料庫大小而進行節流。 這項分析會檢查在 BizTalk 多工緩衝處理表格大小增加的趨勢。<br /><br /> 參考：<br /><br /> -了解 BizTalk Server 2004 SP1 輸送量和在容量 [http://go.microsoft.com/fwlink/?linkid=108781](http://go.microsoft.com/fwlink/?linkid=108781)<br />-在持續性負載測試 [http://go.microsoft.com/fwlink/?LinkId=155293](http://go.microsoft.com/fwlink/?LinkId=155293)<br />-建議測試引擎效能時 [http://go.microsoft.com/fwlink/?LinkID=155294](http://go.microsoft.com/fwlink/?LinkID=155294)|  
|BizTalk Server: BizTalk 追蹤資料大小|當 BizTalk Server 處理您系統上的多資料時，BizTalk 追蹤資料庫 (BizTalkDTADb) 會繼續成長的大小。 若未發現此成長現象將會降低系統效能，並且可能會在 Tracking Data Delivery Service (TDDS) 中產生錯誤。 除了一般追蹤資料以外，追蹤的訊息也會累積在 MessageBox 資料庫，導致磁碟效能變差。 這項分析會檢查遞增趨勢的多個 5 MB 的每小時追蹤中的資料大小。<br /><br /> 參考：<br /><br /> 封存和清除 BizTalk 追蹤資料庫  [http://go.microsoft.com/fwlink/?LinkID=153816](http://go.microsoft.com/fwlink/?LinkID=153816)|  
|BizTalk Server： 交易式範圍數 BizTalk 中止|這是長時間執行或不可部分完成範圍自從主控件執行個體啟動之後已中止的數目。 交易式範圍中止，則協調流程內的交易範圍內發生的失敗。 請務必了解的範圍已順利完成，但是然後才可以復原，因為周圍的範圍決定 （因為在處理時稍後可能會發生的失敗） 而中止時，才叫用範圍的補償處理常式。 此外，「 自動 」 復原的狀態就會發生交易中止時。 您可以達到這個結果，以程式設計方式透過例外狀況和補償處理常式。 交易式範圍中止不應該通常發生在實際執行環境。因此，這項分析會檢查有任何已中止的交易式範圍的項目。<br /><br /> 參考：<br /><br /> 在 BizTalk Server 2004 整個交易 [http://go.microsoft.com/fwlink/?linkid=108784](http://go.microsoft.com/fwlink/?linkid=108784)|  
|BizTalk Server: BizTalk 交易式範圍補償|補償可以視為邏輯工作，已成功提交回應某個錯誤狀況中復原。 請務必了解的範圍已順利完成，但是然後才可以復原，因為周圍的範圍決定 （因為在處理時稍後可能會發生的失敗） 而中止時，才叫用範圍的補償處理常式。 此外，「 自動 」 復原的狀態就會發生交易中止時。 您可以透過例外狀況和補償處理常式，以程式設計方式來達成這點。 交易式範圍的補償不應該通常發生在實際執行環境。因此，這項分析會檢查有任何已中止的交易式範圍的項目。<br /><br /> 在 BizTalk Server 2004 整個的參考： 交易 [http://go.microsoft.com/fwlink/?linkid=108784](http://go.microsoft.com/fwlink/?linkid=108784)|  
|BizTalk Server: BizTalk Virtual Bytes|這是保留給主控件執行個體的虛擬記憶體 （mb）。 這項分析會決定是否任何主控件執行個體正在耗用大量系統的記憶體，以及是否在經過一段時間的記憶體耗用量增加主控件執行個體。 如需詳細資訊，請參閱 BizTalk 虛擬位元組分析本主題中。|  
|BizTalk Server: BizTalk 訊息代理程式工作階段節流的資料庫|這是到 MessageBox，相較於其各自的 BizTalk 節流設定的開放式資料庫連接的數目。 「 資料庫每一 CPU 的連線 」 為並行資料庫工作階段數目上限 （每一 CPU) 節流開始前允許。 如需詳細資訊，請參閱 BizTalk 訊息代理程式資料庫工作階段節流分析本主題中。|  
|BizTalk Server: BizTalk 訊息代理程式資料庫工作階段節流處理臨界值|這是到 MessageBox 的開放式資料庫連接數目的目前閾值。 「 資料庫每一 CPU 的連線 」 為並行資料庫工作階段數目上限 （每一 CPU) 節流開始前允許。 如需詳細資訊，請參閱 BizTalk 訊息代理程式資料庫工作階段節流閾值分析本主題中。|  
|BizTalk Server: BizTalk 訊息代理程式內含式訊息計數節流|這是並行服務類別正在處理的訊息數目。 「 內含式訊息每一 CPU 」 中的設定主控件節流設定是傳遞至 「 結束點管理員 」 (EPM) 或 XLANG 尚未處理的訊息的數目上限。 如需詳細資訊，請參閱本主題中 BizTalk 訊息代理程式內含式訊息計數節流分析。|  
|BizTalk Server: BizTalk 訊息代理程式內含式訊息計數節流處理臨界值|這是目前的服務類別正在處理的並行訊息數目的閾值。 「 內含式訊息每一 CPU 」 中的設定主控件節流設定是傳遞至 「 結束點管理員 」 (EPM) 或 XLANG 尚未處理的訊息的數目上限。 如需詳細資訊，請參閱 BizTalk 訊息代理程式內含式訊息計數節流閾值分析本主題中。|  
|BizTalk Server: BizTalk 訊息代理程式處理序記憶體使用量 (MB) 節流設定|這是目前的處理序 (MB) 的記憶體使用量。 BizTalk 處理序記憶體節流設定可能要發行批次具有並不容易學習的記憶體需求，或是太多的執行緒正在處理訊息。 如需詳細資訊，請參閱本主題中的 BizTalk 訊息代理程式處理序記憶體使用量 (MB) 節流分析。|  
|BizTalk Server: BizTalk 訊息代理程式處理序記憶體使用量 (MB) 節流處理臨界值|這是目前的處理序 (MB) 的記憶體使用量的目前閾值。 實際至這個處理序記憶體耗用量模式，其可用的記憶體數量而定，可能會以動態方式調整臨界值。 BizTalk 處理序記憶體節流設定可能要發行批次具有並不容易學習的記憶體需求，或是太多的執行緒正在處理訊息。 如需詳細資訊，請參閱 BizTalk 訊息代理程式處理序記憶體使用量 (MB) 本主題中的節流閾值分析。|  
|BizTalk Server: BizTalk 訊息代理程式執行緒計數節流|BizTalk 處理序中執行緒的總數。 [每一 CPU 的執行緒] 是在主機處理程序包括使用配接器之執行緒的執行緒總數。 若超過此閾值，BizTalk Server 會嘗試減少 EPM 執行緒集區和訊息代理程式執行緒集區的大小。 在高負載可能導致建立大量執行緒的情況時，應啟用以執行緒為基礎的節流。 此參數會同時影響輸入和輸出節流。 執行緒為基礎的節流預設為停用。 這項分析會檢查 BizTalk 執行緒計數是否大於 80%的指出節流狀況有可能節流臨界值。<br /><br /> 參考：<br /><br /> -裝載在節流效能計數器 [http://go.microsoft.com/fwlink/?LinkId=155285](http://go.microsoft.com/fwlink/?LinkId=155285)<br />-如何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]實作主控件節流在 [http://go.microsoft.com/fwlink/?LinkId=155286](http://go.microsoft.com/fwlink/?LinkId=155286)<br />-如何修改預設主控件節流設定 [http://go.microsoft.com/fwlink/?LinkId=155296](http://go.microsoft.com/fwlink/?LinkId=155296)<br />-影響配接器的效能設定參數 [http://go.microsoft.com/fwlink/?LinkID=154200](http://go.microsoft.com/fwlink/?LinkID=154200)<br />執行緒，資料庫工作階段，並在節流 [http://go.microsoft.com/fwlink/?linkid=106793](http://go.microsoft.com/fwlink/?linkid=106793)|  
|BizTalk Server: BizTalk 訊息代理程式執行緒計數節流處理臨界值|這是目前的處理序中的執行緒總數閾值。 [每一 CPU 的執行緒] 是在主機處理程序包括使用配接器之執行緒的執行緒總數。 若超過此閾值，BizTalk Server 會嘗試減少 EPM 執行緒集區和訊息代理程式執行緒集區的大小。 在高負載可能會導致建立大量執行緒的案例中應該啟用執行緒為基礎的節流設定。 此參數會同時影響輸入和輸出節流。<br /><br /> 這項分析會檢查此節流的設定是否已設為非預設值。 執行緒為基礎的節流預設為停用。<br /><br /> 參考：<br /><br /> -裝載在節流效能計數器 [http://go.microsoft.com/fwlink/?LinkId=155285](http://go.microsoft.com/fwlink/?LinkId=155285)<br />-如何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]實作主控件節流在 [http://go.microsoft.com/fwlink/?LinkId=155286](http://go.microsoft.com/fwlink/?LinkId=155286)<br />-如何修改預設主控件節流設定 [http://go.microsoft.com/fwlink/?LinkId=155296](http://go.microsoft.com/fwlink/?LinkId=155296)<br />-影響配接器的效能設定參數 [http://go.microsoft.com/fwlink/?LinkID=154200](http://go.microsoft.com/fwlink/?LinkID=154200)<br />執行緒，資料庫工作階段，並在節流 [http://go.microsoft.com/fwlink/?linkid=106793](http://go.microsoft.com/fwlink/?linkid=106793)|  
  
## <a name="logicalphysical-disk-readwrite-latency-analysis"></a>邏輯/實體磁碟讀取/寫入延遲分析  
 Windows 偵測到磁碟的效能瓶頸最可靠的方式是藉由測量其回應時間。 如果回應時間大於.025 （25 毫秒為單位），也就是保守的臨界值，然後值得注意的速度並影響使用者的效能問題可能會發生。  
  
 不佳的磁碟延遲的常見原因是磁碟分散程度，能快取、 使用量飽和 SAN，並在磁碟上的負載過大。 使用 SPA 工具，找出的最上層檔案和使用磁碟的程序。 同時檢查 」 程序 IO Data Operations/sec"和"處理序 IO 其他 Operations/sec"，了解哪些處理程序會使用最大磁碟我 / O 的 請注意，效能監視器計數器無法指定哪些檔案相關。  
  
### <a name="references"></a>參考  
  
-   統治出磁碟繫結的問題 [http://go.microsoft.com/fwlink/?linkid=50669](http://go.microsoft.com/fwlink/?linkid=50669)  
  
-   如何識別使用 Microsoft 伺服器效能警告器 (SPA) 工具，在磁碟效能瓶頸 [http://go.microsoft.com/fwlink/?linkid=98096](http://go.microsoft.com/fwlink/?linkid=98096)  
  
-   在 Microsoft 服務效能建議程式 (SPA) 的下載詳細資料： [http://go.microsoft.com/fwlink/?linkid=57769](http://go.microsoft.com/fwlink/?linkid=57769)  
  
## <a name="logical-disk-transferssec"></a>Logical Disk Transfers/sec  
 「 磁碟 Transfers/sec"是讀取的速率和寫入磁碟上的作業。 由於磁碟轉移操作並不直接的相互關聯的磁碟我 / O 的它們告訴我們多少磁碟作業正在進行。 如果您平均循序我 / O 的隨機和我 / O 的則您最後產生約 80 我 / O 的每秒做為一般的經驗法則。 因此，我們應該預期 SAN 磁碟機執行我超過 80/O 的每個底下的第二個 when 載入。 這項分析檢查以查看是否有任何的邏輯磁碟的臨界值會顯示不佳的回應時間 （大於 25 毫秒 I/O 作業的回應時間）。 如果為 true，我們應該預期會等於或高於 80 每秒磁碟轉移操作。 如果沒有，則需要調查磁碟架構。 不佳的磁碟 I/O 的最常見原因是多載 SAN – 這表示的條件的多個 LUN 使用小型的實體磁碟陣列上的邏輯單元編號 (LUN)。  
  
### <a name="reference"></a>참조  
 NT 伺服器和磁碟子系統效能 [http://go.microsoft.com/fwlink/?linkid=106783](http://go.microsoft.com/fwlink/?linkid=106783)  
  
## <a name="available-memory-analysis"></a>可用記憶體分析  
 "Available Mbytes 」 是以 mb 為單位的電腦上執行的處理序可用的實體記憶體數量。 虛擬記憶體管理員持續調整用於維護最小作業系統和處理序的可用位元組數目的實體記憶體中和磁碟上的空間。 當可用的位元組是充足，虛擬記憶體管理員可讓處理程序的工作集成長時，或將它們置於穩定藉由移除舊的頁面加入每一個新頁面。 可用的位元組數時，虛擬記憶體管理員必須修剪處理程序來維護所需的最小工作的集。  
  
 這項分析會檢查，看看是否低 – 警告位於可用的 10%的總可用記憶體和 5%的可用的重大。 遞減趨勢 10 MB 的每小時偵測到，指出潛在的即將進行的記憶體不足時，也會提出警示警告。 實體記憶體不足可能會造成更高特殊權限的模式 CPU 和系統的延遲。  
  
### <a name="references"></a>參考  
  
-   在偵測記憶體瓶頸 [http://go.microsoft.com/fwlink/?linkid=106787](http://go.microsoft.com/fwlink/?linkid=106787)  
  
-   統治出記憶體繫結的問題 [http://go.microsoft.com/fwlink/?linkid=62575](http://go.microsoft.com/fwlink/?linkid=62575)  
  
## <a name="memory-leak-detection-analysis"></a>記憶體流失偵測分析  
 這項分析會判斷是否的任何程序正在耗用大量系統的記憶體和處理程序是否在經過一段時間的記憶體耗用量增加。 處理序耗用的記憶體也沒關係，只要在處理序傳回回系統的記憶體。 尋找增加圖表中的趨勢。 遞增趨勢上很長一段時間可能表示記憶體流失。 私用位元組是目前的大小，以位元組為單位，此處理序已配置的記憶體不能與其他處理序共用。 這項分析會檢查 10 MB 的每小時和 5 MB 的每小時增加的趨勢。 您可以使用這項分析中可用的記憶體分析相互關聯。  
  
 此外，請記住，啟動新的程序一開始會顯示為記憶體流失時，它只是正常的啟動行為。 處理序耗用的記憶體會繼續與一段很長一段時間不釋放記憶體時發生記憶體流失。  
  
 如果您懷疑記憶體流失的狀況，再安裝，並使用偵錯診斷工具。 如需有關偵錯診斷工具的詳細資訊，請參閱 < 參考一節。  
  
### <a name="reference"></a>참조  
 偵錯診斷工具 v1.1，在 [http://go.microsoft.com/fwlink/?linkid=106784](http://go.microsoft.com/fwlink/?linkid=106784)  
  
## <a name="memory-pagessec-analysis"></a>記憶體每秒頁面分析  
 這項分析會檢查，看看是否高"Pages/sec"。 如果高，然後系統可能記憶體不足嘗試將頁面上的記憶體到磁碟。 「 頁/sec"是在讀取或寫入為解決硬體分頁錯誤而對磁碟頁面的速率。 這個計數器是導致整個系統延遲的錯誤種類的主要指示器。  它是 「 Memory\Pages Input/sec"和"Memory\Pages Output/sec"的總和。 它被計算頁數，因此可以與其他分頁數，例如"Memory\Page Faults/sec"。  
  
 此計數器一律應少於 1000。 這項分析會檢查超過 1,000 個的值。 使用這項分析中可用的記憶體分析和記憶體流失偵測分析與相互關聯。 如果所有的分析在同一時間中擲回警示，這可能表示系統用完記憶體。 請遵循本主題中的其他資訊有關記憶體流失偵測分析中所述的分析步驟。  
  
### <a name="reference"></a>참조  
 統治出記憶體繫結的問題 [http://go.microsoft.com/fwlink/?linkid=62575](http://go.microsoft.com/fwlink/?linkid=62575)  
  
## <a name="memory-system-cache-resident-bytes-analysis"></a>記憶體系統快取常駐位元組分析  
 「 系統快取常駐位元組 」 是大小，以位元組為單位的檔案系統快取中的可分頁作業系統程式碼。 此值只包含目前實體頁面，而且不包含任何非目前駐留的虛擬記憶體分頁。 它等於顯示 [工作管理員] 中的系統快取值。 如此一來，這個值可能小於的實際使用中的檔案系統快取的虛擬記憶體數量。 這個值是元件的 「 記憶體\\\System 常駐位元組的程式碼 」，代表所有目前正在實體記憶體的可分頁作業系統程式碼。 這個計數器會顯示最後觀察到的值它不是平均值。  
  
 這項分析會檢查每小時 10 MB 的遞增趨勢。 在負載下，伺服器可能會以快取的 I/O 活動，例如磁碟使用的系統快取。 用於相互關聯處理序 IO Data Operations/sec 與其他處理序 IO 作業數/秒的分析。  
  
## <a name="processor-utilization-analysis-and-excessive-processor-use-by-processes"></a>處理器使用率分析和處理序過度佔用處理器使用  
 「 處理器時間百分比 」 是處理器花費在執行非閒置執行緒所經過時間的百分比。 其計算方式是測量閒置執行緒處於使用中的範例間隔的持續時間，然後再從減去該時間間隔的持續時間。 （每顆處理器具有閒置執行緒會佔用循環當其他執行緒尚未準備好要執行的）。此計數器是處理器活動的主要指示器，並顯示在取樣間隔期間觀察到的忙碌時間平均百分比。 其計算方式是監視該服務處於非使用中的時間，並從 100%減去該值。  
  
 這項分析會檢查使用量大於每個個別的處理器上的 60%。 如果是的話，判斷它是否高使用者模式 CPU 或高特殊權限的模式。 如果懷疑 CPU 高特殊權限的模式，則會看到 「 特殊權限模式 CPU 分析 」。 如果懷疑有使用者模式處理器瓶頸，請考慮使用處理程序的程式碼剖析工具分析造成高 CPU 耗用率的函式。 請參閱 「 如何以： 識別造成高的使用者模式 CPU 瓶頸的伺服器應用程式在生產環境中的函式 」 參考一節，如需詳細資訊的發行項。  
  
## <a name="processor-queue-length-analysis"></a>處理器佇列長度分析  
 「 處理器佇列長度 」 是處理器佇列中的執行緒數目。 不同於磁碟計數器，此計數器會顯示準備就緒的執行緒，無法執行的執行緒。  即使在有多個處理器的電腦上，有處理器時間是單一佇列。 因此，如果電腦有多個處理器，您需要此值除以工作負載的處理器數目。 處理器佇列持續少於 10 個執行緒，每個處理器的是可以接受的依存工作負載。  
  
 這項分析會判斷是否平均處理器佇列長度會超過處理器的數目。 如果是的話，這可能表示發生處理器瓶頸。 使用這項分析中使用特殊權限模式 CPU 分析和處理程序過多處理器使用相互關聯。 處理器佇列已準備好，但您不能因為另一個使用中執行緒目前正在執行的處理器來執行執行緒的集合。 持續性或重複執行的多個執行緒的處理器數目超過佇列可清楚指出是處理器瓶頸。  
  
 您可以使用這個計數器配合"處理器\\%Processor Time"計數器以判斷您的應用程式是否可以發揮更多的 Cpu。 沒有單一佇列的處理器時間，即使在多處理器電腦上。 因此，在多處理器電腦上，「 處理器佇列長度 」 (PQL) 值除以工作負載的處理器數目  
  
 如果 CPU 是非常忙碌 （90%和更高的使用率），而且 PQL 平均值高於一致處理器數目，則您可能無法受益於額外的 Cpu 處理器瓶頸。 或者，您無法減少的執行緒和應用程式層級的佇列。 這會導致較少的內容切換，這是適合用來降低 CPU 負載。 處理器時間的要求到達隨機，而執行緒要求異常大量的處理器時間高 PQL 低 CPU 使用率的常見原因。 這表示處理器不是瓶頸。 相反地，將執行緒的邏輯，需要改善。  
  
 如果懷疑有使用者模式處理器瓶頸，請考慮使用處理程序的程式碼剖析工具分析造成高 CPU 耗用率的函式。 請參閱 「 如何以： 識別造成高的使用者模式 CPU 瓶頸的伺服器應用程式在生產環境中的函式 」 參考一節，如需詳細資訊的發行項。  
  
## <a name="privileged-mode-cpu-analysis"></a>特殊權限的模式 CPU 分析  
 此計數器表示執行緒在特權模式下執行的時間的百分比。 當您的應用程式呼叫作業系統函式 （例如來執行檔案或網路 I/O，或配置記憶體） 時，這些作業系統函式會執行特殊權限模式。  
  
 高特殊權限的模式 CPU 指出電腦花太多時間在系統 I/O 與真實 （使用者模式） 的工作。 "%特殊權限時間 」 的處理序執行緒花在特權模式下執行的程式碼的時間百分比。  呼叫 Windows 系統服務時，服務通常會在特殊權限模式來取得系統私用資料的存取權執行。 這類資料會受到在使用者模式中執行的執行緒存取。 呼叫系統可以是明確或隱含方式，例如分頁錯誤或中斷。 與某些早期作業系統不同 Windows 會使用處理序界限來保護子系統的傳統保護除了使用者和特殊權限的模式。 代表應用程式由 Windows 完成某些工作可能會出現在其他子系統處理序，除了處理序中的特殊權限時間。  
  
 這項分析會檢查是否有權限的模式 CPU 耗用超過 30%的總 CPU。 如果，則 CPU 耗用量可能是另一個以外的處理器，例如網路、 記憶體或磁碟 I/O 瓶頸所造成。 用於相互關聯與 %Interrupt Time 及高內容切換的分析。  
  
## <a name="high-context-switching-analysis"></a>高內容切換分析  
 當高優先順序的執行緒優先執行較低優先順序的執行緒目前正在執行或高優先權執行緒會封鎖，就會發生內容切換。 多執行緒共用相同的優先權層級，就會發生內容切換的高層級。 這通常表示太多執行緒會在系統上處理器的競爭。 如果您看不太多的處理器使用率，而且您看到的內容切換的層級非常低，則可能表示執行緒會被封鎖。  
  
 高內容切換只應該加以調查，高 CPU 和整體 CPU 的特殊權限的模式時。 一般而言，內容切換率小於每個處理器每秒 5000 就不值得耽心。 如果內容切換率超過 15,000 每個處理器每秒，就將條件約束。  
  
 這項分析會檢查是否有高的 CPU、 高特殊權限的模式 CPU 和高 （超過 5000，每個處理器） 系統秒內容切換次數所有發生在相同的時間。 如果發生高內容切換時，接著減少執行緒和處理序在系統上執行的數目。  
  
## <a name="biztalk-high-database-sessions-analysis"></a>BizTalk 高資料庫工作階段分析  
 此計數器會有兩個可能的值也就是正常 (0)，或超過 (1)。 這項分析會檢查值為 1。 如果是這樣，BizTalk 已超過允許的資料庫工作階段數目的臨界值。 這個值是由 「 每一 CPU 的資料庫連線 」 中的值的 BizTalk 主控件節流設定所控制的。  
  
 「 資料庫每一 CPU 的連線 」 為並行資料庫工作階段數目上限 （每一 CPU) 節流開始前允許。 一般個別主控件工作階段集區中的閒置資料庫工作階段不會加到此計數，而是對主控件執行個體實際正在使用的工作階段數目嚴格執行這項檢查。 此選項會停用的預設值;一般而言，這項設定，才應該啟用如果資料庫伺服器是瓶頸或低階的資料庫伺服器的 BizTalk Server 系統中。 您可以使用 biztalk： 訊息代理程式的效能物件類別下的資料庫工作階段效能計數器監視使用中的資料庫連線數目。 此參數只會影響輸出訊息節流。 輸入值為 0 時可停用以資料庫工作階段數目為基礎的節流。 預設值是 0。  
  
> [!NOTE]  
>  「 MaxWorkerThreads"登錄機碼會影響數字的執行緒可用來 BizTalk 和有助於如果大部分的 BizTalk 執行緒忙著處理資料庫連接。  
  
### <a name="references"></a>參考  
  
-   主控件節流效能計數器在 [http://go.microsoft.com/fwlink/?LinkID=155285](http://go.microsoft.com/fwlink/?LinkID=155285)  
  
-   執行緒、 DB 工作階段，以及在節流 [http://go.microsoft.com/fwlink/?linkid=106793](http://go.microsoft.com/fwlink/?linkid=106793)  
  
-   影響配接器的效能設定參數 [http://go.microsoft.com/fwlink/?LinkID=154200](http://go.microsoft.com/fwlink/?LinkID=154200)  
  
-   如何修改預設主控件節流設定 [http://go.microsoft.com/fwlink/?LinkID=155296](http://go.microsoft.com/fwlink/?LinkID=155296)  
  
## <a name="biztalk-high-database-size-analysis"></a>BizTalk 高資料庫大小分析  
 此計數器是指在此程序已發佈的資料庫佇列中的訊息數目。 這個值是由所有主控件的佇列表格中之項目數目以及多工緩衝處理與追蹤表格中的項目數目來測量。 佇列包含在工作佇列、 狀態佇列和擱置的佇列。 若程序正發佈到多個佇列，則此計數器會反映所有佇列的加權平均值。  
  
 若重新啟動主控件，則會遺失保留在記憶體中的統計值。 涉及一些額外負荷，因為 BizTalk Server 將會繼續收集統計資料，只有當有至少 100 發行時，具有 5%的總計會發佈在重新啟動主控件程序中。  
  
 此計數器將設定為值 1，如果其中一個列出的資料庫臨界值中的訊息計數的條件發生。 此閾值記錄主題中的 < 如何修改預設主控件節流設定下面所參照。 根據預設主機訊息資料庫節流閾值中的計數是設定為 50000，將會觸發節流狀況，在下列情況下的值：  
  
-   主控件執行個體發佈到訂閱之主控件的工作、狀態和擱置佇列的訊息總數超過 50,000。  
  
-   多工緩衝處理表格或追蹤表格中的訊息數目超過 50,000 個訊息。  
  
 即使低或完全無負載發生 BizTalk server 擱置的訊息包含在計算資料庫中的訊息計數，因為是的訊息發佈節流可能發生的。  
  
 這項分析會檢查值為 1。 如果發生這種情況，請考慮採取的動作，將會減少在資料庫中的訊息數目。 比方說，確保 BizTalk SQL Server 正在執行工作不會發生錯誤，並在 BizTalk 管理主控台中使用 群組中樞，以判斷是否要將訊息增多造成的大量擱置的訊息。  
  
### <a name="references"></a>參考  
  
-   擱置的訊息會包含在資料庫節流閾值中郵件計數 [http://go.microsoft.com/fwlink/?LinkId=155304](http://go.microsoft.com/fwlink/?LinkId=155304)  
  
-   如何修改預設主控件節流設定 [http://go.microsoft.com/fwlink/?LinkID=155296](http://go.microsoft.com/fwlink/?LinkID=155296)  
  
-   主控件節流效能計數器在 [http://go.microsoft.com/fwlink/?LinkID=155285](http://go.microsoft.com/fwlink/?LinkID=155285)  
  
## <a name="biztalk-high-in-process-message-count-analysis"></a>BizTalk 高內含式訊息計數分析  
 「 內含式訊息每一 CPU 」 中的設定主控件節流設定是傳遞至 「 結束點管理員 」 (EPM) 或 XLANG 尚未處理的訊息的數目上限。 這個數字不包含擷取自資料庫，但仍然等候中記憶體中的佇列傳遞的訊息。 您可以使用 biztalk： 訊息代理程式的效能物件類別下的 內含式訊息計數 效能計數器來監視內含式訊息的數目。 當您考慮節流狀況時，這個參數會提供提示給節流機制。 實際閾值會受自我調整影響而不同。 您可以監視內含式訊息計數 」 效能計數器，以確認實際閾值。  
  
 這個參數可以將大型訊息實例，其中平均訊息大小很高，或訊息的處理可能需要大量的訊息較小的值。 如果案例中遇到記憶體為根據的節流太過頻繁，與記憶體臨界值可讓您取得自動調整為相當低的值，這會是明顯。 此類行為發生時表示輸出傳輸應減少同時處理的訊息數，以避免過度使用記憶體。 此外，對於一次處理少量訊息可讓配接器較有效率的實例 (例如，傳送至限制並行連線的伺服器時)，此參數可調整為低於預設的值。  
  
 這項分析會檢查以判斷是否發生這種節流高內含式訊息計數計數器。 如果是的話，請考慮調整"訊息每一 CPU 的內含式 」 設定。 此參數只會影響輸出訊息節流。 在停用以每一 CPU 的內含式訊息數目為基礎的節流"訊息每一 CPU 的內含式 」 設定中輸入值為 0。 「 內含式訊息每一 CPU 」 設定的預設值是 1000。 請注意，此值也可能會影響低度延遲的訊息和 （或） BizTalk 資源的效率。  
  
### <a name="references"></a>參考  
  
-   如何修改預設主控件節流設定 [http://go.microsoft.com/fwlink/?LinkID=155296](http://go.microsoft.com/fwlink/?LinkID=155296)  
  
-   主控件節流效能計數器在 [http://go.microsoft.com/fwlink/?LinkID=155285](http://go.microsoft.com/fwlink/?LinkID=155285)  
  
## <a name="biztalk-high-message-delivery-rate-analysis"></a>BizTalk 高訊息傳遞速率分析  
 對於輸出 （已傳遞） 訊息，BizTalk Server 會調整訊息的傳遞如果主控件執行個體的訊息傳遞內送速率超過訊息傳遞外寄速率 * 指定的速率增加因數 （百分比） 值。 訊息處理節流設定 對話方塊上的速率增加因數 （百分比） 參數是可設定的。 主要是藉由引發從記憶體中佇列移除訊息，並將訊息傳遞到結束點管理員 」 (EPM) 或協調流程引擎以進行處理之前的延遲來完成輸出訊息之根據速率的節流。 不採取其他任何動作的目的就能完成輸出訊息之根據速率的節流。  
  
 輸出節流會造成訊息延遲傳遞，而且訊息可能建立在記憶體中佇列內，並造成清除佇列執行緒遭到封鎖，直到移轉了節流狀況為止。 當清除佇列執行緒處於封鎖狀態、 任何其他的訊息會從 MessageBox 提取到記憶體中佇列中等待傳送外寄。  
  
 這項分析會檢查 1 高訊息傳遞速率計數器中的值。 高訊息傳遞速率可能因高處理複雜性、 慢速輸出配接器或瞬間的系統資源不足。  
  
### <a name="references"></a>參考  
  
-   主控件節流效能計數器在 [http://go.microsoft.com/fwlink/?LinkID=155285](http://go.microsoft.com/fwlink/?LinkID=155285)  
  
-   BizTalk Server 如何實作主控件節流在 [http://go.microsoft.com/fwlink/?LinkID=155286](http://go.microsoft.com/fwlink/?LinkID=155286)  
  
-   如何修改預設主控件節流設定 [http://go.microsoft.com/fwlink/?LinkID=155296](http://go.microsoft.com/fwlink/?LinkID=155296)  
  
## <a name="biztalk-high-process-memory-analysis"></a>BizTalk 高程序記憶體分析  
 節流臨界值 設定的 BizTalk 處理序記憶體使用量會是記憶體的與工作集大小和處理序的總可用虛擬記憶體的總和，如果輸入從 1 到 100 的值使用百分比。 根據預設，節流設定的 BizTalk 程序記憶體使用量會是 25。 當指定某個百分比值時，則會以定期間隔重新計算程序記憶體閾值。 如果使用者指定的百分比值，它將會以根據可用的記憶體為認可和目前的處理序記憶體使用量計算。  
  
 這項分析會檢查 1 高的處理序記憶體計數器的值。 如果發生這種情況，然後再次嘗試使用偵錯 Diag 判斷記憶體增加的原因 （請參閱記憶體流失偵測分析中的參考）。 請注意，為它的一般程序進行期間啟動，而這會耗用大量記憶體可能一開始會顯示為記憶體流失，但是當處理程序無法釋放不再需要藉此減少可用的我的記憶體時，就會發生真正的記憶體流失mory 經過一段時間。 有關如何以一般方式分析程序記憶體遺漏，biztalk，請參閱下面的 「 如何要擷取記憶體傾印的處理程序，是流失記憶體 」 參考及/或 PAL 中的 「 記憶體流失偵測 」 分析，如需詳細資訊。  
  
 如果要發行批次有遽記憶體需求，高程序記憶體節流設定可能會發生或太多的執行緒正在處理訊息。  若系統出現過度節流，請考慮增加主控件相關聯處理序記憶體使用量閾值的值，並確認主控件執行個體不會產生 「 記憶體不足 」 錯誤。 如果藉由增加程序記憶體使用量閾值，會引發 「 記憶體不足 」 錯誤，請考慮縮減內部訊息佇列大小的值，內含式訊息，每個 CPU 臨界值。 此策略特別會與大型訊息處理實例有關。 此外，這個值應設為需要大量記憶體需求，每個訊息的案例較低的值。 設定較低的值會在初期節流開始作用，並導致程序中的記憶體擴張。  
  
 如果您的 BizTalk server 定期執行虛擬記憶體不足，請考慮 BizTalk Server 64 位元。 在 64 位元伺服器上的每個處理序可以處理最多 4 TB 的虛擬記憶體與 2 GB 的 32 位元。 一般情況下，強烈建議 BizTalk 64 位元和 64 位元 SQL Server。 請參閱 < BizTalk Server 64 位元支援 > 參考，如需詳細資訊。  
  
### <a name="references"></a>參考  
  
-   BizTalk Server 如何實作主控件節流在 [http://go.microsoft.com/fwlink/?LinkID=155286](http://go.microsoft.com/fwlink/?LinkID=155286)  
  
-   如何修改預設主控件節流設定 [http://go.microsoft.com/fwlink/?LinkID=155296](http://go.microsoft.com/fwlink/?LinkID=155296)  
  
-   如何擷取發生記憶體溢位在的處理程序的記憶體傾印 [http://go.microsoft.com/fwlink/?LinkId=155305](http://go.microsoft.com/fwlink/?LinkId=155305)  
  
-   在 BizTalk Server 64 位元支援 [http://go.microsoft.com/fwlink/?LinkId=155306](http://go.microsoft.com/fwlink/?LinkId=155306)  
  
## <a name="biztalk-high-system-memory-analysis"></a>BizTalk 高系統記憶體分析  
 BizTalk 的實體記憶體使用量節流臨界值設定為輸入則是從 1 到 100 相較於可用的實體記憶體的值如果總數量的記憶體耗用量的百分比。 如果輸入大於 100 的值，此設定也可以是以 mb 為單位的可用實體記憶體總數。 輸入值為 0 時可停用以實體記憶體使用量為基礎的節流。 預設值是 0。  
  
 這項分析會檢查 1 高系統記憶體計數器的值。 因為這會測量系統記憶體總量，若非 BizTalk Server 程序正耗用過量的系統記憶體，則可能觸發節流狀況。 因此如果發生這種情況，最好的方法是找出哪些處理程序正在耗用的最實體記憶體及/或將額外的實體記憶體新增至伺服器。 此外，請考慮減少負載，藉由減少 EPM 執行緒集區的預設大小和 （或） 配接器批次的大小。 如需詳細資訊，請參閱 < 在 PAL 中的記憶體流失偵測分析。  
  
### <a name="references"></a>參考  
  
-   主控件節流效能計數器在 [http://go.microsoft.com/fwlink/?LinkID=155285](http://go.microsoft.com/fwlink/?LinkID=155285)  
  
-   如何修改預設主控件節流設定 [http://go.microsoft.com/fwlink/?LinkID=155296](http://go.microsoft.com/fwlink/?LinkID=155296)  
  
-   BizTalk Server 如何實作主控件節流在 [http://go.microsoft.com/fwlink/?LinkID=155286](http://go.microsoft.com/fwlink/?LinkID=155286)  
  
## <a name="biztalk-high-thread-count-analysis"></a>BizTalk 高執行緒計數分析  
 [每一 CPU 的執行緒] 是在主機處理程序包括使用配接器之執行緒的執行緒總數。 如果超過此臨界值時，BizTalk Server 會嘗試減少 EPM 執行緒集區和訊息代理程式 」 執行緒集區的大小。 在高負載可能導致建立大量執行緒的情況時，應啟用以執行緒為基礎的節流。 此參數會同時影響輸入和輸出節流。 執行緒為基礎的節流預設為停用。  
  
> [!NOTE]  
>  使用者指定的值做為指導方針，而且主應用程式可能會以動態方式自我調整為基礎的記憶體使用量模式和處理序執行緒需求此臨界值。  
  
 這項分析會檢查 1 高執行緒計數計數器中的值。 考慮調整不同的執行緒集區大小，以確定系統不會建立大量的執行緒。 這項分析可與內容切換相互關聯每個第二個分析，以判斷是否作業系統已飽和，太多執行緒，但在大部分情況下高執行緒計數原因後端資料庫比在 BizTalk server 上的多個競爭。 如需修改執行緒集區大小的詳細資訊請參閱 < 如何修改預設主控件節流設定在參考中。  
  
### <a name="references"></a>參考  
  
-   主控件節流效能計數器在 [http://go.microsoft.com/fwlink/?LinkID=155285](http://go.microsoft.com/fwlink/?LinkID=155285)  
  
-   BizTalk Server 如何實作主控件節流在 [http://go.microsoft.com/fwlink/?LinkID=155286](http://go.microsoft.com/fwlink/?LinkID=155286)  
  
-   如何修改預設主控件節流設定 [http://go.microsoft.com/fwlink/?LinkID=155296](http://go.microsoft.com/fwlink/?LinkID=155296)  
  
-   影響配接器的效能設定參數 [http://go.microsoft.com/fwlink/?LinkID=154200](http://go.microsoft.com/fwlink/?LinkID=154200)  
  
-   執行緒、 DB 工作階段，以及在節流 [http://go.microsoft.com/fwlink/?linkid=106793](http://go.microsoft.com/fwlink/?linkid=106793)  
  
 BizTalk 輸入延遲 AnalysisAverage 延遲 （毫秒），傳訊引擎收到文件從配接器發佈至 messagebox 之前。 降低延遲很重要的 BizTalk 中，某些使用者因此追蹤時間文件花費輸入配接器中很重要。  
  
 以下是顯示的方式測量延遲圖表。  
  
|1|2|3|4|5|6|  
|-------|-------|-------|-------|-------|-------|  
|配接器接收訊息並提交到引擎，才能將訊息提供給引擎不在配接器完成的工作擷取這些效能計數器|引擎從配接器接收訊息、 執行接收管線、 對應、 訂閱評估，保存在資料庫中的訊息。|協調流程或請求-回應連接埠執行，並產生回應訊息。|回應訊息在傳訊引擎從佇列中清除、 執行傳送管線、 對應。|傳訊引擎會提供回應訊息給配接器。|配接器會通知引擎訊息作業都是。|  
||I|||||  
||RR|RR|RR|||  
||||O|O|O|  
|||||OA|OA|  
  
 I = 輸入的延遲  
  
 RR = 要求的回應延遲  
  
 O = 輸出延遲  
  
 OA = 配接器輸出延遲  
  
 假設在低延遲的環境，這項分析會檢查是否在文件所花費的時間超過 5 秒的輸入配接器中。 這可能表示之傳輸的訊息，透過此主控件執行個體的輸入配接器處理延遲。 如果多個輸入配接器存在於此主控件執行個體，請考慮將它們分割到他們自己的主機，以判斷哪一個輸入的介面卡有高延遲。  
  
### <a name="references"></a>參考  
  
-   BizTalk Server 資料庫最佳化  
    [http://go.microsoft.com/fwlink/?linkid=104427](http://go.microsoft.com/fwlink/?linkid=104427)  
  
-   要求/回應傳訊  
    [http://go.microsoft.com/fwlink/?LinkID=155288](http://go.microsoft.com/fwlink/?LinkID=155288)  
  
-   識別 BizTalk 層中的瓶頸  
    [http://go.microsoft.com/fwlink/?LinkID=155289](http://go.microsoft.com/fwlink/?LinkID=155289)  
  
## <a name="biztalk-message-delivery-throttling-state-analysis"></a>BizTalk 訊息傳遞節流狀態分析  
 BizTalk 訊息傳遞節流狀態是節流的主要指標。 它是旗標，指出系統是否正在進行節流訊息傳遞 （影響 XLANG 訊息處理及輸出傳輸）。 節流狀況會指示計數器的數值。 以下是一份值和其各自的意義：  
  
|||  
|-|-|  
|0|未進行節流|  
|1|由於不平衡的訊息傳遞速率 (輸入速率超過輸出速率) 而進行節流|  
|3|由於高內含式訊息計數而進行節流|  
|4|由於處理程序記憶體壓力而進行節流|  
|5|由於系統記憶體壓力而進行節流|  
|9|由於高執行緒計數而進行節流|  
|10|由於傳遞時使用者覆寫而進行節流|  
  
 這項分析會檢查每個這些值，並為每個有特定的警示。  
  
### <a name="references"></a>參考  
  
-   主控件節流效能計數器在 [http://go.microsoft.com/fwlink/?LinkID=155285](http://go.microsoft.com/fwlink/?LinkID=155285)  
  
-   BizTalk Server 如何實作主控件節流在 [http://go.microsoft.com/fwlink/?LinkID=155286](http://go.microsoft.com/fwlink/?LinkID=155286)  
  
## <a name="biztalk-messagebox-database-connection-failures-analysis"></a>BizTalk MessageBox 資料庫連線失敗分析  
 此效能計數器是資料庫連線嘗試的主控件執行個體啟動後失敗的數目。 如果裝載 BizTalk 資料庫的 SQL Server 服務因故無法使用，資料庫叢集資源從作用中的電腦傳輸到被動電腦。 在此容錯移轉程序期間，BizTalk Server 服務執行個體發生資料庫連接失敗並自動重新啟動以重新連接到資料庫。 正在運作的資料庫電腦 (先前為被動電腦) 會在容錯移轉期間獲得資源後，開始處理資料庫連接。  
  
 當 BizTalk Server 執行階段無法與 MessageBox 或管理資料庫通訊時，會發生 DBNetLib （資料庫網路程式庫） 錯誤。 當發生這種情況時，攔截例外狀況的 BizTalk Server 執行階段執行個體就會關閉，並再每分鐘循環查看資料庫是否可用。 這個主題，請參閱 [參考] 區段，如需詳細資訊。  
  
 當用戶端起始 TCP/IP 通訊端連線聯繫伺服器時，用戶端通常會連接到伺服器上特定的連接埠，並要求伺服器透過短期有效的臨時 TCP 或 UDP 連接埠回應用戶端。 在 Windows Server 2003 和 Windows XP 中，用戶端應用程式所使用的臨時連接埠的預設範圍是從 1025 到 5000。 在某些情況下很可能就會耗盡可用的連接埠中的預設範圍。 這個主題，請參閱 [參考] 區段，如需詳細資訊。  
  
 這項分析會檢查資料庫連線失敗的任何項目。 資料庫連線失敗非常重要的因為 BizTalk 資料庫沒有就無法作用。 如果資料庫連線失敗的原因不明，然後考慮下面所列的參考和/或連絡 Microsoft 支援服務以判斷連線失敗的性質。  
  
### <a name="references"></a>參考  
  
-   向外擴充的資料庫  
    [http://go.microsoft.com/fwlink/?LinkId=155307](http://go.microsoft.com/fwlink/?LinkId=155307)  
  
-   避免 DBNETLIB 例外狀況  
    [http://go.microsoft.com/fwlink/?LinkId=155308](http://go.microsoft.com/fwlink/?LinkId=155308)  
  
-   避免 TCP/IP 連接埠耗盡  
    [http://go.microsoft.com/fwlink/?LinkId=155309](http://go.microsoft.com/fwlink/?LinkId=155309)  
  
## <a name="biztalk-messaging-publishing-throttling-state-analysis"></a>BizTalk 訊息發佈節流狀態分析  
 BizTalk 訊息發佈節流狀態是節流的主要指標。 旗標，指出系統是否正在進行節流 （影響 XLANG 訊息處理及輸入的傳輸） 的訊息發佈它。節流狀況會指示計數器的數值。 以下是一份值和其各自的意義：  
  
|||  
|-|-|  
|0|未進行節流|  
|2|由於不平衡的訊息發佈速率 (輸入速率超過輸出速率) 而進行節流|  
|4|由於處理程序記憶體壓力而進行節流|  
|5|由於系統記憶體壓力而進行節流|  
|6|由於資料庫成長而進行節流|  
|8|由於高工作階段計數而進行節流|  
|9|由於高執行緒計數而進行節流|  
|11|由於發佈時使用者覆寫而進行節流|  
  
 這項分析會檢查每個這些值，並為每個有特定的警示。  
  
### <a name="references"></a>參考  
  
-   主控件節流效能計數器在 [http://go.microsoft.com/fwlink/?LinkID=155285](http://go.microsoft.com/fwlink/?LinkID=155285)  
  
-   BizTalk Server 如何實作主控件節流在 [http://go.microsoft.com/fwlink/?LinkID=155286](http://go.microsoft.com/fwlink/?LinkID=155286)  
  
## <a name="biztalk-orchestrations-resident-in-memory"></a>在記憶體中的 BizTalk 協調流程內建  
 目前由主控件執行個體裝載的協調流程執行個體數。 如果看到爆增情形或暴增的記憶體中駐留的協調流程可能遭視為正常，而遞增趨勢可能表示"以免 」 的協調流程在記憶體中。 當 BizTalk 無法凍結訊息/協調流程執行個體時，可能會發生一段時間遞增趨勢。 嘗試將此計數器與"XLANG/s Orchestrations(?) 相互關聯\Dehydratable 協調流程 」 其中問號 （？） 是相同計數器執行個體，以做為此計數器。  
  
 如果大量的協調流程是常駐在記憶體中的，如果協調流程數目最少可凍結，則您的協調流程可能會在記憶體中的閒置，而且可能會造成記憶體流失的狀況。 如果有的話，請使用這項分析與 「 \XLANG/s 協調流程 （*） \Idle 協調流程 」 產生關聯。 遞增趨勢 BizTalk 閒置協調流程中的是更好的指標，記憶體流失，因為無法凍結協調流程執行個體。  
  
 這項分析會檢查遞增趨勢常駐記憶體，且如果超過 50%的記憶體中駐留的協調流程未凍結的協調流程中。  
  
### <a name="references"></a>參考  
  
-   協調流程引擎效能計數器  
    [http://go.microsoft.com/fwlink/?LinkID=155290](http://go.microsoft.com/fwlink/?LinkID=155290)  
  
-   協調流程凍結和解除凍結  
    [http://go.microsoft.com/fwlink/?LinkID=155284](http://go.microsoft.com/fwlink/?LinkID=155284)  
  
## <a name="biztalk-private-bytes-analysis"></a>BizTalk 私用位元組分析  
 這是主控件執行個體，其相當於"\Process （*） \Private 位元組 」 效能計數器的配置私用記憶體 mb。 私用位元組是記憶體的目前的大小，以位元組為單位的處理序已配置，不能與其他處理序共用。 這項分析會判斷是否任何主控件執行個體正在耗用龐大的系統記憶體和主控件執行個體是否持續一段時間的記憶體耗用量增加。 耗用記憶體的主控件執行個體是正常的只要它傳回至系統的記憶體。 尋找增加圖表中的趨勢。 遞增趨勢上很長一段時間可能表示記憶體流失。  
  
 這項分析會檢查每小時 10 MB-遞增的趨勢。 您可以使用這項分析中可用的記憶體分析與記憶體流失分析相互關聯。 此外，請記住，新啟動主控件執行個體一開始會顯示為記憶體流失時，它只是一般啟動行為。 記憶體遺漏時，處理程序會繼續耗用記憶體和沒有釋出一段很長一段時間的記憶體。 如果您懷疑記憶體流失的情況，請閱讀以下參照"記憶體成長中 BizTalk 傳訊 」 文章。 否則，安裝並使用偵錯診斷工具。 如需有關偵錯診斷工具的詳細資訊，請參閱 < 參考一節。  
  
### <a name="references"></a>參考  
  
-   偵錯診斷工具 v1.1  
    [http://go.microsoft.com/fwlink/?linkid=106784](http://go.microsoft.com/fwlink/?linkid=106784)  
  
-   在 「 BizTalk 訊息的記憶體成長  
    [http://go.microsoft.com/fwlink/?linkid=108788](http://go.microsoft.com/fwlink/?linkid=108788)  
  
## <a name="biztalk-virtual-bytes-analysis"></a>BizTalk 虛擬位元組分析  
 這是保留給主控件執行個體的虛擬記憶體 （mb）。 這項分析會決定是否任何主控件執行個體正在耗用大量系統的記憶體，以及是否在經過一段時間的記憶體耗用量增加主控件執行個體。 耗用記憶體的主控件執行個體是正常的只要它會傳回至系統記憶體。 尋找增加圖表中的趨勢。 遞增趨勢上很長一段時間可能表示記憶體流失。  
  
 這項分析會檢查每小時 10 MB-遞增的趨勢，以虛擬位元組為單位。 您可以使用這項分析中可用的記憶體分析與記憶體流失分析相互關聯。 此外，請記住，新啟動主控件執行個體一開始會顯示為記憶體流失時，它只是一般啟動行為。 記憶體遺漏時，處理程序會繼續耗用記憶體和沒有釋出一段很長一段時間的記憶體。 如果您懷疑記憶體流失的狀況，然後讀取 「 記憶體成長中 BizTalk 傳訊 」 下列文件。 否則，安裝並使用偵錯診斷工具。 如需有關偵錯診斷工具的詳細資訊，請參閱 < 參考一節。  
  
### <a name="references"></a>參考  
  
-   偵錯診斷工具 v1.1  
    [http://go.microsoft.com/fwlink/?linkid=106784](http://go.microsoft.com/fwlink/?linkid=106784)  
  
-   在 「 BizTalk 訊息的記憶體成長  
    [http://go.microsoft.com/fwlink/?linkid=108788](http://go.microsoft.com/fwlink/?linkid=108788)  
  
## <a name="biztalk-message-agent-database-session-throttling-analysis"></a>BizTalk 訊息代理程式的資料庫工作階段節流分析  
 這是到 MessageBox，相較於其各自的 BizTalk 節流設定的開放式資料庫連接的數目。 「 資料庫每一 CPU 的連線 」 為並行資料庫工作階段數目上限 （每一 CPU) 節流開始前允許。 一般個別主控件工作階段集區中的閒置資料庫工作階段不會加到此計數，而是對主控件執行個體實際正在使用的工作階段數目嚴格執行這項檢查。 此選項預設為停用；通常只有在資料庫伺服器是 BizTalk Server 系統中的瓶頸時，才應啟用此設定。 您可以使用 biztalk： 訊息代理程式的效能物件類別下的資料庫工作階段效能計數器監視使用中的資料庫連線數目。 此參數只會影響輸出訊息節流。 輸入值為 0 時可停用以資料庫工作階段數目為基礎的節流。 預設值是 0。  
  
 MaxWorkerThreads 登錄機碼具有數字的執行緒可用來 BizTalk 的影響力，並有助於在其中大部分的 BizTalk 的執行緒都是使用資料庫連接忙碌的情況下。 這項分析會檢查到 MessageBox 的開放式資料庫連接的數目是否大於 80%的資料庫工作階段，節流設定，表示可能節流狀況。  
  
### <a name="references"></a>參考  
  
-   主控件節流效能計數器在 [http://go.microsoft.com/fwlink/?LinkID=155285](http://go.microsoft.com/fwlink/?LinkID=155285)  
  
-   影響配接器的效能設定參數 [http://go.microsoft.com/fwlink/?LinkID=154200](http://go.microsoft.com/fwlink/?LinkID=154200)  
  
-   執行緒、 DB 工作階段，以及在節流 [http://go.microsoft.com/fwlink/?linkid=106793](http://go.microsoft.com/fwlink/?linkid=106793)  
  
## <a name="biztalk-message-agent-database-session-throttling-threshold-analysis"></a>BizTalk 訊息代理程式的資料庫工作階段節流閾值分析  
 這是到 MessageBox 的開放式資料庫連接數目的目前閾值。 「 資料庫每一 CPU 的連線 」 為並行資料庫工作階段數目上限 （每一 CPU) 節流開始前允許。 一般個別主控件工作階段集區中的閒置資料庫工作階段不會加到此計數，而是對主控件執行個體實際正在使用的工作階段數目嚴格執行這項檢查。 此選項預設為停用；通常只有在資料庫伺服器是 BizTalk Server 系統中的瓶頸時，才應啟用此設定。 您可以使用 biztalk： 訊息代理程式的效能物件類別下的資料庫工作階段效能計數器監視使用中的資料庫連線數目。 此參數只會影響輸出訊息節流。 輸入值為 0 時可停用以資料庫工作階段數目為基礎的節流。 預設值是 0。  
  
 MaxWorkerThreads 登錄機碼具有數字的執行緒可用來 BizTalk 的影響力，並有助於在其中大部分的 BizTalk 的執行緒都是使用資料庫連接忙碌的情況下。 這項分析會檢查此值來查看是否有已修改的預設設定。 根據預設，此設定會是 0，表示節流的資料庫工作階段上已停用。  
  
### <a name="references"></a>參考  
  
-   主控件節流效能計數器在 [http://go.microsoft.com/fwlink/?LinkID=155285](http://go.microsoft.com/fwlink/?LinkID=155285)  
  
-   影響配接器的效能設定參數 [http://go.microsoft.com/fwlink/?LinkID=154200](http://go.microsoft.com/fwlink/?LinkID=154200)  
  
-   執行緒、 DB 工作階段，以及在節流 [http://go.microsoft.com/fwlink/?linkid=106793](http://go.microsoft.com/fwlink/?linkid=106793)  
  
## <a name="biztalk-message-agent-in-process-message-count-throttling-analysis"></a>BizTalk 訊息代理程式內含式訊息計數節流分析  
 這是並行服務類別正在處理的訊息數目。 「 內含式訊息每一 CPU 」 中的設定主控件節流設定是傳遞至 「 結束點管理員 」 (EPM) 或 XLANG 尚未處理的訊息的數目上限。 這不包括從資料庫擷取但仍在等候記憶體中的佇列中傳遞的訊息。 您可以使用 biztalk： 訊息代理程式的效能物件類別下的 內含式訊息計數 效能計數器來監視內含式訊息的數目。 此參數提供提示給節流機制，做為節流狀況的考量。 實際閾值會受自我調整影響而不同。 您可以監視內含式訊息計數效能計數器，以確認實際閾值。  
  
 對於大型訊息實例 （其中平均訊息大小很高，或訊息的處理可能需要大量的訊息），這個參數可以設定為較小的值。 大型訊息實例被表示如果記憶體為根據的節流太過頻繁發生且臨界值時，取得自動調整為相當低的值。 此類行為發生時表示輸出傳輸應減少同時處理的訊息數，以避免過度使用記憶體。 此外，對於一次處理少量訊息可讓配接器較有效率的實例 (例如，傳送至限制並行連線的伺服器時)，此參數可調整為低於預設的值。 這項分析會檢查高內含式訊息計數計數器來判斷其是否超過其節流設定相同的名稱下的 80%，表示節流狀況有可能。  
  
### <a name="references"></a>參考  
  
-   主控件節流效能計數器在 [http://go.microsoft.com/fwlink/?LinkID=155285](http://go.microsoft.com/fwlink/?LinkID=155285)  
  
-   如何修改預設主控件節流設定 [http://go.microsoft.com/fwlink/?LinkID=155296](http://go.microsoft.com/fwlink/?LinkID=155296)  
  
## <a name="biztalkmessage-agent-in-process-message-count-throttling-threshold-analysis"></a>Biztalk： 訊息代理程式內含式訊息計數節流閾值分析  
 這是目前的服務類別正在處理的並行訊息數目的閾值。 「 內含式訊息每一 CPU 」 中的設定主控件節流設定是傳遞至 「 結束點管理員 」 (EPM) 或 XLANG 尚未處理的訊息的數目上限。 這不包括從資料庫擷取但仍在等候記憶體中的佇列中傳遞的訊息。 您可以使用 biztalk： 訊息代理程式的效能物件類別下的 內含式訊息計數 效能計數器來監視內含式訊息的數目。 此參數提供提示給節流機制，做為節流狀況的考量。 實際閾值會受自我調整影響而不同。 您可以監視內含式訊息計數效能計數器，以確認實際閾值。  
  
 對於大型訊息實例 （其中平均訊息大小很高，或訊息的處理可能需要大量的訊息），這個參數可以設定為較小的值。 大型訊息實例被表示如果記憶體為根據的節流太過頻繁發生且臨界值時，取得自動調整為相當低的值。 此類行為發生時表示輸出傳輸應減少同時處理的訊息數，以避免過度使用記憶體。 此外，對於一次處理少量訊息可讓配接器較有效率的實例 (例如，傳送至限制並行連線的伺服器時)，此參數可調整為低於預設的值。 這項分析會檢查節流處理臨界值的非預設值高內含式訊息計數。  
  
### <a name="references"></a>參考  
  
-   主控件節流效能計數器在 [http://go.microsoft.com/fwlink/?LinkID=155285](http://go.microsoft.com/fwlink/?LinkID=155285)  
  
-   如何修改預設主控件節流設定 [http://go.microsoft.com/fwlink/?LinkID=155296](http://go.microsoft.com/fwlink/?LinkID=155296)  
  
## <a name="biztalk-message-agent-process-memory-usage-mb-throttling-analysis"></a>BizTalk 訊息代理程式處理序記憶體使用量 (MB) 節流分析  
 這是目前的處理序 (MB) 的記憶體使用量。 BizTalk 處理序記憶體節流設定可能要發行批次具有並不容易學習的記憶體需求，或是太多的執行緒正在處理訊息。  若系統出現過度節流，請考慮增加主控件相關聯處理序記憶體使用量閾值的值，並確認主控件執行個體不會產生 「 記憶體不足 」 錯誤。 如果藉由增加程序記憶體使用量閾值，會引發 「 記憶體不足 」 錯誤，請考慮縮減內部訊息佇列大小的值，內含式訊息，每個 CPU 臨界值。 此策略特別會與大型訊息處理實例有關。  
  
 如果您的 BizTalk server 定期執行虛擬記憶體不足，請考慮 BizTalk Server 64 位元。 在 64 位元伺服器上的每個處理序可以處理最多 4 TB 的虛擬記憶體與 2 GB 的 32 位元。 一般情況下，強烈建議 BizTalk 64 位元和 64 位元 SQL Server。 請參閱 < BizTalk Server 64 位元支援 > 參考，如需詳細資訊。 這項分析會檢查是否大於 80%的其各自的節流臨界值具有相同名稱的程序記憶體使用量。 根據預設，節流設定的 BizTalk 程序記憶體使用量會是 25%之處理序可用的虛擬記憶體。 /3GB 參數這項設定沒有作用。  
  
### <a name="references"></a>參考  
  
-   BizTalk Server 如何實作主控件節流在 [http://go.microsoft.com/fwlink/?LinkID=155286](http://go.microsoft.com/fwlink/?LinkID=155286)  
  
-   如何修改預設主控件節流設定 [http://go.microsoft.com/fwlink/?LinkID=155296](http://go.microsoft.com/fwlink/?LinkID=155296)  
  
-   如何擷取發生記憶體溢位在的處理程序的記憶體傾印 [http://go.microsoft.com/fwlink/?LinkId=155305](http://go.microsoft.com/fwlink/?LinkId=155305)  
  
-   在 BizTalk Server 64 位元支援 [http://go.microsoft.com/fwlink/?LinkId=155306](http://go.microsoft.com/fwlink/?LinkId=155306)  
  
## <a name="biztalkmessage-agent-process-memory-usage-mb-throttling-threshold-analysis"></a>Biztalk： 訊息代理程式處理序記憶體使用量 (MB) 節流閾值分析  
 這是目前的處理序 (MB) 的記憶體使用量的目前閾值。 實際至這個處理序記憶體耗用量模式，其可用的記憶體數量而定，可能會以動態方式調整臨界值。 BizTalk 處理序記憶體節流設定可能要發行批次具有並不容易學習的記憶體需求，或是太多的執行緒正在處理訊息。 若系統出現過度節流，請考慮增加主控件相關聯處理序記憶體使用量閾值的值，並確認主控件執行個體不會產生 「 記憶體不足 」 錯誤。 如果藉由增加程序記憶體使用量閾值，會引發 「 記憶體不足 」 錯誤，請考慮縮減內部訊息佇列大小的值，內含式訊息，每個 CPU 臨界值。 此策略特別會與大型訊息處理實例有關。  
  
 如果您的 BizTalk server 定期執行虛擬記憶體不足，請考慮 BizTalk Server 64 位元。 在 64 位元伺服器上的每個處理序可以處理最多 4 TB 的虛擬記憶體與 2 GB 的 32 位元。 一般情況下，強烈建議 BizTalk 64 位元和 64 位元 SQL Server。 請參閱 < BizTalk Server 64 位元支援 > 參考，如需詳細資訊。 這項分析會檢查是否程序記憶體節流設定為非預設值。  
  
### <a name="references"></a>參考  
  
-   BizTalk Server 如何實作主控件節流在 [http://go.microsoft.com/fwlink/?LinkID=155286](http://go.microsoft.com/fwlink/?LinkID=155286)  
  
-   如何修改預設主控件節流設定 [http://go.microsoft.com/fwlink/?LinkID=155296](http://go.microsoft.com/fwlink/?LinkID=155296)  
  
-   如何擷取發生記憶體溢位在的處理程序的記憶體傾印 [http://go.microsoft.com/fwlink/?LinkId=155305](http://go.microsoft.com/fwlink/?LinkId=155305)  
  
-   在 BizTalk Server 64 位元支援 [http://go.microsoft.com/fwlink/?LinkId=155306](http://go.microsoft.com/fwlink/?LinkId=155306)