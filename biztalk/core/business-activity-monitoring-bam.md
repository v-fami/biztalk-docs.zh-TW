---
title: 商務活動監控 (BAM) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAM, tools
- utilities, Tracking Profile Deployment Utility
- BAM, deployment process
- BAM
- BAM, presentation layers
- BAM, Tracking Profile Deployment utility
- BAM, about BAM
- BAM, data storage
- BAM Management utility
- Tracking Profile Deployment utility
- BAM, runtime process
- BAM, design time
- BAM, data insertion
- BAM, data consumption
- BAM, BAM Management utility
- BAM, processing
ms.assetid: a8ad48b1-6891-4bbb-b125-27d224e49293
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 258294a8a51e6f8e80e360668123e522acf6ff15
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972303"
---
# <a name="business-activity-monitoring-bam"></a>商務活動監控 (BAM)
下圖說明商務活動監控 (BAM) 功能的架構。  
  
 ![](../core/media/architecture-bam-01.gif "architecture_bam_01")  
  
## <a name="tools"></a>工具  
 您可以使用下列工具來設計、開發及部署與 BAM 整合的 BizTalk 解決方案。  
  
-   **Microsoft Excel**。 Excel 的 BAM 增益集提供可在建立活動與檢視期間引導商務分析師的使用者介面。 Excel 可做為商務分析師的設計工具以及商務使用者的資料取用工具。 適用於 Excel 的相關的 BAM 增益集資訊，請參閱[使用適用於 Excel 的 BAM 增益集需求](../core/requirements-for-using-the-bam-add-in-for-excel.md)。  
  
-   **BAM 管理公用程式**。 BAM 管理公用程式是一種可將建立在 Excel 的 BAM 定義部署到企業中的部署工具。 BAM 管理公用程式會建立必要的 SQL Server 資料庫、Analysis Services Cube、SQL Notification Services 資料庫以及 DTS 或 SSIS 工作 (根據安裝的 SQL Server 不同版本而定)。 如需 BAM 管理員的詳細資訊，請參閱 < [BAM 管理公用程式](../core/bam-management-utility.md)。  
  
-   **追蹤設定檔編輯器**。 追蹤設定檔編輯器可以讓 BizTalk 開發人員將商務分析師定義的資料項目對應到包含協調流程及傳訊的 BizTalk 實作。 如需追蹤設定檔編輯器的詳細資訊，請參閱 < [Tracking Profile Editor](../core/tracking-profile-editor.md)。  
  
-   **追蹤設定檔部署公用程式**。 追蹤設定檔部署公用程式可以讓 IT 專業人員將新的及更新的追蹤設定檔部署到 BAM 架構。 如需追蹤設定檔部署工具的詳細資訊，請參閱[追蹤設定檔部署公用程式](../core/tracking-profile-deployment-utility.md)。  
  
## <a name="presentation"></a>呈現方式  
 展示層由下列項目組成：  
  
- **BAM 入口網站**。 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的 BAM 入口網站提供商務程序之即時、端對端的檢視。 這是由 ASP.NET 網頁組成的 Web 型功能。 您可以自訂 BAM 來增強效能及使用者經驗。 如需有關 BAM 入口網站的詳細資訊，請參閱 < [BAM 入口網站](../core/bam-portal.md)。  
  
- **Microsoft Excel**。 Excel 的 BAM 增益集提供可在建立活動與檢視期間引導商務分析師的使用者介面。 Excel 可做為商務分析師的設計工具以及商務使用者的資料取用工具。 適用於 Excel 的相關的 BAM 增益集資訊，請參閱[使用適用於 Excel 的 BAM 增益集需求](../core/requirements-for-using-the-bam-add-in-for-excel.md)。  
  
- **自訂使用者介面**。 ISV 與開發人員可以建立顯示 BAM 資料的自訂應用程式  
  
## <a name="processing"></a>Processing  
 處理層由下列項目組成：  
  
- **BAM 管理 Web 服務**。 BAM 入口網站應用程式會使用此 Web 服務通訊與 BAM 主要匯入資料表 (PIT)。 與資料庫的通訊會使用儲存在登錄中的模擬認證 (在組態期間建立) 來執行。 此 Web 服務所公開的方法可以自訂用戶端用來取得檢視其詳細資料、 相關的活動，以及樞紐分析表版面配置的任何使用者。 這些方法也可以用來管理資料庫中的警示。  
  
- **事件匯流排**。 BAM 事件匯流排服務會處理儲存在來源資料庫的追蹤資料 (資料流)，並以查詢表格格式將該資料保存在目的資料庫。  
  
- **SQL Notification Services**。 SQL Notification Services 會評估商務使用者定義的執行個體與彙總 BAM 警示。  
  
  下圖說明 BAM 架構的基礎實體程序。  
  
  ![](../core/media/architecture-bam-02.gif "architecture_bam_02")  
  
## <a name="design-time-experience"></a>設計階段經驗  
 下圖說明設計階段經驗。  
  
 ![](../core/media/architecture-bam-03.gif "architecture_bam_03")  
  
 下列步驟描述上圖說明的順序。  
  
1.  追蹤設定檔編輯器會假設 BizTalk Server 已經設定，即至少已部署一個 BAM 定義 (使用 BM.exe)，且已建立包含主要匯入資料庫的架構。 追蹤設定檔編輯器會使用在 BizTalk 組態期間設定的登錄機碼來決定管理資料庫的位置。  
  
    1.  一旦 BAM 探索到主要匯入資料庫時，就會列舉其中的活動。 BizTalk 開發人員會選取從 BAM 主要匯入資料庫提取的部署活動。  
  
    2.  BizTalk 開發人員藉由瀏覽從 BizTalk 管理資料庫擷取的已部署組件，將選取的活動對應到實體實作。  
  
    3.  一旦開發人員以視覺化方式將活動對應到 BizTalk 成品時，中繼資料就會提交至 BizTalk Server 執行階段以收集並儲存資料。 這是透過註解 (用來解碼收集的資料之傳訊資訊) 與追蹤設定檔 (用來擷取執行階段資料) 來完成。  
  
2.  Microsoft Excel 可用來做為設計階段工具以及資料使用或展示工具。 設計階段 Excel 經驗可以讓使用者藉由建立 BAM 活動與檢視來建構 BAM 定義。 它也可以讓您建立最後會顯示在 BAM 入口網站中的樞紐分析控制項與圖表。  
  
## <a name="deployment"></a>部署  
 部署有兩個類別  
  
- 建置動態架構  
  
- 檢測執行階段以收集資料。  
  
  下圖說明 BAM 部署。  
  
  ![](../core/media/architecture-bam-04.gif "architecture_bam_04")  
  
  下列步驟描述上圖說明的順序。  
  
1.  BAM 管理公用程式是用來建置動態架構。 使用 BAM 定義或設計階段 Excel 活頁簿以及 BAM 組態 XML 檔案，BAM 管理公用程式就可建置所有必要的資料庫以及系統運作所需的對應 DTS 或 SSIS 工作。  
  
    1.  會建構 BAM 主要匯入資料庫與所有支援的預存程序、觸發程序以及 DTS 或 SSIS 工作。  
  
    2.  在封存 DTS 或 SSIS 工作後，才會定義 BAM 封存資料庫，但不會建立該資料庫。  
  
    3.  若 BAM OLAP 彙總已定義，則會建立 BAM 星狀結構描述資料庫。 您可以判斷是否是否已定義彙總**即時彙總**Excel 試算表中的按鈕會停用或**CreateOlapCube**設定為**true**中BAM 定義與組態 XML 檔案都有部署單位**AnalysisDatabase**。  
  
    4.  BAM 定義與組態 XML 必須定義非 RTA 的彙總，以便建立 BAM OLAP Cube。  
  
    5.  BAM 管理員程序的分解式檢視顯示已呼叫 Notification Services 程序 (nscontrol.exe) 以建立 SQL NS 資料庫。  
  
2.  追蹤設定檔編輯器 UI 具有部署命令，可檢測執行階段以追蹤並解碼來自執行階段系統的資料。 在此情況下它會將推送**註解**到 BAM 主要匯入資料庫 （如果資料從傳訊系統提取）。 將追蹤設定檔插入 BizTalk 管理資料庫，BizTalk 執行階段會使用此資料庫來決定哪些資料要發佈到 BAM 系統。  
  
3.  BizTalk 追蹤部署命令列工具允許追蹤設定檔發佈到 BAM 主要匯入資料庫與管理資料庫，這和追蹤設定檔編輯器所執行的工作類似；不過，命令列工具並不允許對應功能。  
  
## <a name="data-consumption"></a>資料使用  
 資料使用指的是商務使用者使用 BAM 架構收集之資訊的程序。 此時會假定 BAM 定義已建立 (定義應該收集的資料與檢視方式)、BAM 定義已部署 (動態建立架構) 以及 BAM 定義已對應到實體實作中 (定義收集資料的位置，在某些案例中會撰寫程式碼以推入系統)。  
  
 下圖說明資料使用的程序。  
  
 ![](../core/media/architecture-bam-05.gif "architecture_bam_05")  
  
 下列步驟描述上圖說明的順序。  
  
1.  BAM 入口網站會分為兩個程序：Internet Explorer 以及裝載在 Internet Information Services 中的 BAM Web 入口網站程序。  
  
    1.  Internet Explorer 使用連接到 BAM 入口網站之商務使用者的安全性內容。 BAM 入口網站則是一種 ASPX 應用程式，使用 BAM 管理 Web 服務來收集資訊。  
  
    2.  BAM 入口網站會呼叫 BAM 管理 Web 服務，以擷取如特定商務使用者可看見之 BAM 活動/檢視等資訊。 BAM 管理 Web 服務必須能夠模擬商務使用者，因此，一般的部署是將 BAM 入口網站和 Web 服務裝載在同一部電腦上。  
  
        > [!NOTE]
        >  若您的企業支援 Kerberos 且已設定 Active Directory 來支援委派，就可以將入口網站與 Web 服務放置在不同電腦上。  
  
    3.  Web 服務會呼叫 BAM 主要匯入中的預存程序來執行安全性檢查、擷取中繼資料以及擷取 BAM 即時彙總的資訊。  
  
        > [!NOTE]
        >  目前 BAM 入口網站會使用未記載的 Web 服務，稱為**查詢 Web 服務**。 並未支援此服務，且在下一版本中可能會被取代。  
  
    4.  Internet Explorer 裝載 Office Web 控制項 (OWC)，它會直接連接到 BAM Analysis Services Cube。  
  
2.  [匯出]  
  
## <a name="runtime"></a>執行階段  
 定義 BAM 定義之後，也就已經建置架構，而開發人員也已檢測所需的系統，讓使用者可看見該系統，且資料可以開始在系統中流通。  
  
### <a name="data-insertion"></a>資料插入  
 資料流通至 BAM 系統的其中一個主要方式是透過 BizTalk 服務 (BTSNTSvc.exe)。 由於已架構 BizTalk 服務，因此它可包含邏輯子系統。  
  
 下圖說明此程序。  
  
 ![](../core/media/architecture-bam-06.gif "architecture_bam_06")  
  
 下列步驟描述上圖說明的順序。  
  
1.  一個子系統會裝載 BizTalk Server 引擎本身。 這個引擎負責執行協調流程及傳訊。  
  
2.  另一個子系統是事件匯流排服務。 事件匯流排服務負責將緩衝事件資料流資料寫入 BAM 主要匯入資料庫。  
  
### <a name="booting-the-runtime"></a>啟動執行階段  
 當 BizTalk 服務啟動時，每個子系統會載入可供子系統運作所需的中繼資料。  
  
 下圖說明此程序。  
  
 ![](../core/media/architecture-bam-07.gif "architecture_bam_07")  
  
 下列步驟描述上圖說明的順序。  
  
1.  當 BizTalk 引擎執行時 (協調流程或傳訊)，會呼叫攔截器，而該攔截器會調節從引擎進入 BAM 的資料流程。 當引擎呼叫攔截器時，攔截器會分析與執行協調流程或傳訊成品順序相關的引擎位置。 若有需要從引擎目前執行的位置擷取資料，攔截器就會收集適當的資料。 判定需擷取資料的位置以及需要擷取哪些資料的中繼資料儲存在追蹤設定檔中。 在啟動 BizTalk 服務期間，引擎的攔截器會連絡 BizTalk 管理資料庫，為正在執行的成品提取適當的追蹤設定檔。  
  
2.  事件匯流排服務的主要功能是將資料 BLOB (由 BizTalk 引擎寫入) 轉換為可使用的資料項目，並將資料插入 BAM 主要匯入資料庫。 傳訊攔截器會以壓縮格式來撰寫原始資料。 這是為了避免大量的記憶體工作集。 為了讓事件匯流排服務可將傳訊資料轉換為可使用的資料項目，事件匯流排服務必須先載入可解譯原始資料的中繼資料。 此中繼資料就所謂**註解**。 會透過追蹤設定檔編輯器或命令列追蹤設定檔部署工具來放置註解中繼資料。 若部署的解決方案未從傳訊中擷取資料，則不會有任何註解。 協調流程攔截器會以原始格式編碼足夠的資訊，讓事件匯流排服務能正確解碼，而不需擁有其他的註解。  
  
### <a name="storing-data"></a>儲存資料  
 本節討論從 BizTalk 服務擷取資料的方式。  
  
 下圖說明此程序。  
  
 ![](../core/media/architecture-bam-08.gif "architecture_bam_08")  
  
 下列步驟描述上圖說明的順序。  
  
1.  如前所述，BizTalk 引擎具有攔截器，而在執行協調流程及傳訊解決方案期間會呼叫此攔截器。 攔截器會根據追蹤設定檔資訊，判定應擷取哪些資料，然後以二進位格式將資料傳送到 BizTalk MessageBox。 在執行階段期間，會擷取一個保存序列 BLOB 資料的 TrackingData 表格。 在處理期間，引擎會有多次需要儲存在執行期間保存在記憶體中的資料。 這些時間稱為持續點，而引擎會決定這些點發生的時機。 當持續點發生時，從攔截器擷取的資料也會在同一個交易中排清及保存。 如此可確保引擎中的資料以及最後 BAM 中可看見的資料之一致性。 若發生失敗，則復原交易，且關聯的 BAM 資料也會復原。  
  
2.  事件匯流排服務儲存在與引擎相同的可執行程序中。 服務會送出由 BTS 引擎儲存的 TrackingData 表格中之資料 (或任何 BufferedEventStream 資料來源)。 此圖所示的組件 – Microsoft.BizTalk.Bam.EventObservation。 這個組件不會公開從 BufferedEventStream 擷取資料的方法。 此程式碼儲存在事件匯流排服務本身。 會擷取資料然後準備儲存在主要匯入資料庫中。 大部分的情況下，二進位資料是序列化的.NET 物件會解除凍結之後的屬性會從物件移至格式化的 SQL 陳述式。  
  
3.  儲存體的資料時，事件匯流排服務會嘗試大型批次。 批次包含呼叫由 BAM 管理部署工具產生的預存程序。 由於高度資料庫活動或其他缺少表格的狀況，批次儲存可能會失敗。 若發生失敗，會繼續嘗試進行批次數次。 若重試失敗，則會將批次分為較小的批次，然後再重試。 若還是失敗，就會將批次移到 FailedTracking 表格。  
  
### <a name="custom-data-insertion"></a>自訂資料插入  
 前一節示範了 BAM 如何從 BizTalk Server 主控件使用不同的方法擷取資料的詳細資料。 不直接使用追蹤設定檔編輯器來建立設定檔，但更直接地在程式碼中直接使用事件資料流方法。 不過，不是與 BAM 相關的所有資料都必須在 BizTalk 中。 因此，您可以使用一個組件來自訂所撰寫的應用程式。  
  
 下圖說明此程序。  
  
 ![](../core/media/architecture-bam-09.gif "architecture_bam_09")  
  
 下列步驟描述上圖說明的順序。  
  
1.  自訂的應用程式必須能夠載入[Microsoft.BizTalk.Bam.EventObservation](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.aspx)組件存取的資料插入 BAM 活動中的 BAM 方法。 其中公開兩個主要的類別，DirectEventStream 與 BufferedEventStream。 在上圖中，DirectEventStream 類別以反白顯示。 此類別會直接寫入主要匯入資料庫。 這是將資料寫入 BAM 活動最常用的方法。  
  
2.  與 BizTalk 儲存資料的方法類似，BufferedEventStream 類別會將二進位 BLOB 寫入非直接的資料庫中。 在此案例中，BizTalk MessageBox 用來做為中繼存放區。 您選擇的類別會根據不同的事項而定；但是效能仍然是主要的考量。 BufferedEventStream 類別會將資料分為批次並維持較高的輸送量。 缺點是不會立即寫入資料。  
  
3.  如同插入資料的 BizTalk 方法，事件匯流排服務會處理二進位資料、解碼資料並在最後將它儲存在 BAM 主要匯入資料庫中。 這只需要透過 BufferedEventStream 類別將資料寫入即可。  
  
## <a name="distributed-navigation"></a>分散式瀏覽  
 BAM 入口網站的分散式導覽功能，能讓使用者檢視跨越遠端界限的活動關係。  
  
## <a name="see-also"></a>另請參閱  
 [管理與追蹤架構](../core/management-and-tracking-architecture.md)