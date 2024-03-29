---
title: 第 1 階段： 設定評量的範圍 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 667c3669-7314-4562-84bc-fbb1be1f0314
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 377abbb4ae14e3c3e1c13f7caf45ac998e9f5e9b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986975"
---
# <a name="phase-1-scoping-the-assessment"></a>第 1 階段： 設定評量的範圍
本主題說明 BizTalk Server 效能評定的 「 範圍 」 階段的層面。  
  
 常見的錯誤時更吸引人的效能評定中於低估效能評估的範圍。 如果未事先配置足夠的資源和時間，然後負責效能評定的小組將無法完成所有建置和測試複雜的類似生產的環境所需的工作。 使用效能評定小組應該仔細選擇其重點。 大部分的效能評定會執行非常有限的時間範圍內，且因此小組應該識別，並專注在最多的關鍵效能目標的一或兩個，或許是三個。 要測試應用程式應該特別開發來專注於所識別之的效能目標，並應該排除所有其他技術變數盡量。 本主題說明 BizTalk Server 效能評定的 「 範圍 」 階段的層面。  
  
## <a name="considerations-before-beginning-the-performance-assessment"></a>開始效能評定之前的考量  
 任何其他工作為了效能評定之前，應該考慮下列因素。 這些因素有助於決定 「 範圍 」 階段的一般方向，並會很好的效能評定的起點。  
  
### <a name="message-load"></a>訊息負載  
 請務必考慮直接從一開始要如何複寫實際上經過生產系統的訊息負載。 比方說，如果在生產環境中有 20%的訊息將會 < 20 KB 的大小會是百分之 50 < 100 KB 的大小和剩餘的 30%可能最多 1 MB 的大小，很重要，這會複寫在實驗室中。  
  
### <a name="develop-a-brief-detail-of-the-scenarios-to-be-tested"></a>開發簡短的詳細資料，要測試的案例  
 識別將會測試的測試案例之後，務必找出有關它們的主要元件。 這包括 BizTalk Server 元件 （例如傳訊與協調流程） 和其他元件，包括協力廠商技術，例如 MQSeries 或 SAP。 它是非常重要的是您要注意的所有這些一開始就因為這將協助您量測計的實驗室複雜度，而且可讓您規劃在 engagement 期間所需的技術技能。  
  
### <a name="identify-which-adapters-will-be-used"></a>識別哪些介面卡將用於  
 它是重要性的重要的效能評定實驗室使用實際的配接器將用於生產環境中。 使用實際的介面卡用於生產環境中的失敗會造成問題，因為不同的配接器的效能大幅變化。 比方說，File 配接器是其中一個最快的 BizTalk Server 配接器，但是它缺乏一些的某些系統; 所需的功能特別是在 File 配接器不提供交易支援。 交易支援可讀取訊息，並將它們寫入至 MessageBox 資料庫，全部都在 MSDTC 交易的環境內。 交易支援會產生額外負荷。 因此，以模擬實際執行案例需要的交易支援使用 File 配接器不會是可行的比較。 在此案例中，效能結果是本質上無效，因為它們是很難反映生產系統的實際效能。  
  
### <a name="estimate-time-required-for-the-performance-assessment"></a>效能評定所需的預估時間  
 您可以使用下列指導方針來估計效能評定所需的時間：  
  
- 設定測試環境中配置兩週的準備時間。 一週會用來建置所需的基礎結構軟體元件，並套用軟體更新。 第二週專用於設定 複製 BizTalk Server 生產環境的特定環境。  
  
- 每個測試案例，就會分析效能評定期間配置其他的週。  
  
- 配置的實際效能評定結果的效能評定的文件結尾的一週。  
  
  因此的兩個測試案例一般效能評定，預估完成評估的時間會是：  
  
  （兩週的準備時間） + （兩週，實際的效能評定） + （1 週到文件所發現的錯誤） = 總計五週。  
  
## <a name="documenting-the-performance-assessment"></a>記錄效能評定  
 範圍效能評定的一部分，應該在 engagement 摘要中記錄評量的詳細資料。 目的與目標，專案關係人和效能評定的里程碑，應該清楚地定義這份文件。 本文件將做為效能評定的藍圖，協助確保所有共同工作人員同意 engagement 詳細資料，並提供以確保效能評定持續追蹤。這份文件更新整個效能評定，以及包含在結束時的效能評定結果的摘要。  
  
### <a name="goals-and-objectives"></a>長期與短期目標  
 **請小心地定義的輸送量和延遲目標**-效能準則為何您想要最大化嗎？ 一或多個下列的效能量值通常 BizTalk Server 效能評定的焦點。  
  
- **輸送量**– 通常是測量每個可以處理一段指定的時間間隔的時間單位的訊息數目。 比方說，輸送量目標可能會定義為能夠處理的一段 3 小時內每秒 100 個訊息。  
  
- **延遲**– 通常是已定義的所有訊息，可以是百分比處理端對端在指定的時間間隔內，例如：  
  
  -   95%的所有訊息 2 秒鐘內應該處理的端對端。  
  
  -   100%的所有訊息應該處理的端對端四秒。  
  
- **尖峰負載**  
  
- **若要完成的批次的時間***X*   
  
- **大量復原案例**  
  
- **包括硬體和軟體的高階架構**  
  
  效能目標應該要測量的"達到最高可能*X*硬體和軟體的條件約束。 」 決定如何目標事先來測量。 比方說，「 最大持續性輸送量*X*端對端所測量計數器 'XLang/s\orchestrations 完成 / 秒' 」。  
  
> [!NOTE]  
>  在上述範例*X*是預留位置的焦點所在的效能評定的單位。 *X*可能代表協調流程、 訊息或其他相關的 BizTalk 方案的效能計量。  
  
### <a name="is-the-desired-performance-attainable"></a>是所需的效能如今？  
 評估時的效能考量，您應該先判斷是否可用硬體資源足以符合您的效能目標。 在某些情況下，所需的效能不只是一定要有額外的硬體投資。 沒有任何可用來判斷何種效能或不能指定特定硬體組態，因為許多因素會影響效能的解決方案，包括複雜的協調流程，可使用時，自訂程式碼的魔術公式訊息的次數會保存到 MessageBox 資料庫和外部系統的限制。 下表提供用來達成特定的效能目標，適用於特定案例的硬體摘要。  
  
> [!NOTE]  
>  下列資訊是僅提供作為指引。 不同的 BizTalk Server 解決方案之需求的差異很大，所以此資料表中的值應該當作 」 的經驗法則 」 大致估計所需的硬體資源時。  
  
### <a name="sample-hardware-scenarios"></a>範例硬體案例  
  
|處理類型|BizTalk Server 電腦|SQL Server 電腦|取得的輸送量|注意|  
|------------------------|------------------------------|--------------------------|-------------------------|-----------|  
|協調流程公開為 Web 服務，MQSeries 配接器|-6 BizTalk Server 2010 的電腦<br />-每個執行兩個 3 GHZ 雙核心處理器的伺服器<br />Windows Server 2008 r2、windows 8 GB 記憶體|-3 的 SQL Server 2008 R2 電腦<br />-每一部執行四個 3 GHZ 雙核心處理器<br />-64 位元，16 GB 記憶體<br />-單一 MessageBox 資料庫|每秒的 95 協調流程|-平均延遲 1.11s<br />-99%的訊息處理 < 2 秒的延遲|  
|Messaging (傳訊)|6 個 BizTalk Server 2010 的電腦|3 個 SQL Server 2008 R2 電腦|達到 2 小時期間內產生的尖峰輸送量為 277 的訊息，每秒|之前最佳化解決方案，尖峰輸送量為每秒 125 訊息|  
|使用協調流程和 Web 服務的低延遲案例|一部 BizTalk Server 2010 的雙處理器的電腦|一個四處理器的 SQL Server 2008 R2 電腦|每秒 60 的協調流程|達成 < 350 毫秒延遲|  
|使用協調流程的低延遲案例|23 四處理器 BizTalk Server 2010 的電腦|-3 的 SQL Server 2008 R2 電腦<br />-一個 16 個 CPU 的主要 MessageBox 資料庫<br />-兩通 8-CPU 次要 MessageBox 資料庫電腦|每秒的 1156年協調流程|自 2010 年 1 月起已執行記錄的協調流程的 BizTalk Server 的最高的持續性效能|  
  
 可用的硬體基礎結構會被視為足以達到所需的效能之後，請考量下列範圍的 BizTalk Server 效能評估：  
  
-   哪些配接器和/或加速器需要？  
  
-   在方案中實作協調流程的需求有哪些？  
  
-   文件的輸送量需求： 解決方案的最大持續輸送量需求為何？  
  
-   延遲需求： 如何回應方案必須請求-回應 」 和 「 要求回應的案例？  
  
-   解決方案程度的尖峰文件載入期間從復原？  
  
-   方案的高可用性需求有哪些？  
  
-   文件追蹤需求的解決方案有哪些？  
  
-   任何相依的應用程式，例如遠端 Web 服務或其他系統的效能特性有哪些？ 如果相依的應用程式執行無法跟上必要的負載，會隨之降低整體系統效能。  
  
### <a name="hardware-information-to-consider-during-scope-phase"></a>範圍階段納入考量的硬體資訊  
 範圍的解決方案時，建立包含下列的高階硬體圖表：  
  
-   電腦架構 （例如 x86、 x64 和 IA64）  
  
-   CPU 需求 （例如類型、 速度、 數目、 核心，以及使用超執行緒）  
  
-   每一部電腦的 RAM 需求  
  
-   本機磁碟儲存體 （類型、 大小、 速度）  
  
-   SAN (存放裝置需求： 數字的 LUN。SAN 卡片類型）  
  
-   網路卡 （在每一部電腦，100 mb / 秒 (Mbps) （1 gigabit / 秒 (1 Gbps) 與數字。）  
  
-   防火牆會部署方案中的方式？  
  
-   會使用網路負載平衡硬體嗎？  
  
-   要叢集化是特定的電腦？  
  
### <a name="software-information-to-consider-during-the-scope-phase"></a>軟體資訊給 「 範圍 」 階段，考慮  
 同樣的硬體資訊和重要是軟體堆疊，將會用於效能評定。  您應該確定文件的下列資訊：  
  
-   每一部電腦 （32 或 64 位元，叢集或非叢集） 的作業系統。  
  
-   在每一部電腦上安裝伺服器軟體。  
  
-   使用虛擬化軟體。  
  
-   通常不會安裝 COM + 彙總套件修正或 SQL Server 主機外修正程式，例如特定的軟體功能所需。  
  
### <a name="determine-if-code-changes-are-within-the-scope-of-the-performance-assessment"></a>決定是否效能評定的範圍內的程式碼變更  
 這是其中一個最重要的工作，來判斷範圍的程序期間。  最佳化 BizTalk Server，以及它會使用 （SQL Server、 Windows、 IIS 和更多） 的基礎元件，可以使用本指南所述的設定變更與微調技術。 不過，如果應用程式尚未開發以獲得最佳效能，它可能會拖累這些效能提升。 因此，變更程式碼應該只會從範圍有完整的程式碼檢閱已完成，應用程式進入實驗室之前的信心。 如有必要，您可能會同意，只有特定變更被允許，比方說，在協調流程中的持續點移除。  
  
## <a name="roles-and-responsibilities"></a>角色和責任  
 其中一個最重要的部分的執行效能評定是為了確保角色和責任清楚地指派。 下列重要的角色應指派的效能評定開始：  
  
- **Engagement 潛在客戶**-engagement 潛在客戶會負責主控整體 engagement 端對端。  這個角色通常會執行由資深的顧問或架構設計師。  在理想情況下這位人員應具有微調架構的 BizTalk Server 系統的經驗。  SQL Server 和任何其他技術，包括協力廠商的知識是合理的。  請注意，並非潛在客戶是所有方面的專家，但是它們必須具有至少有技術的實用知識，他們可以與這些領域專家一起合作，並了解它們所套用的最佳化。  
  
- **測試設計工具**-就必須有專門用來設計和實作將在實驗室中執行測試的任何人。  這會牽涉到決定將用於建立測試，測試每個測試，以確保它會滿足需求的實驗室，並確保那些負責執行測試已了解如何使用用戶端的測試架構。  
  
- **環境擁有者**-具代表性的環境內精確地反映實際執行 BizTalk Server 的實驗室環境非常重要。  執行此角色的人員會負責檢查使用的軟體和硬體堆疊的每個項目，因此驗證有沒有顯著的差異。 例如 SQL Server 2008 R2 32 位元平台上執行時只可以處理 4 GB 的實體記憶體而不需使用實體位址擴充 (PAE) 或 Address Windowing Extensions (AWE)。 SQL Server 2008 r2 的 64 位元到 1 tb 的記憶體可以解決 （這是目前的最大實體記憶體支援的 Windows Server 2008 R2）。 因此重大的差異客戶和實驗室環境會是 BizTalk Server 和 SQL Server 所使用的 CPU 架構。 除了這些明顯的因素，其他較不明顯的因素，例如 service pack 層級和 hotfix 安裝，可能會影響環境的效能。  
  
- **建置環境的潛在客戶**-已繪製詳細的規格後進行效能評定中，有人應指派的建置環境的責任。 這包括硬體和軟體堆疊。 在許多情況下一個人會負責此 （通常是環境擁有者）。 不過在大型企業環境擁有者可能需要為不同的團隊，他們可能負責解決方案的各種元件之間的連絡窗口。 例如，一個小組可能會負責 Windows 組建，另一個用於 SQL Server，和另一個小組以取得 BizTalk Server。  
  
- **部署的潛在客戶**-就必須讓其他人負責確保應用程式已正確部署至 BizTalk Server、 設定的正確的繫結，會套用任何自訂設定。 此角色會需要解決方案的全面的瞭解和會需要了解將應用程式封裝及部署應用程式並驗證它是在實驗室環境內正常運作的狀態。  
  
- **產品專家**– 請務必識別哪些產品專家所需的效能評定。 所需的確切技能，取決於設計和 BizTalk Server 應用程式的目的。  
  
   其中一個所需的最常見產品專家技能是效能微調 SQL Server 的廣泛知識。 這些技術所需的兩個目的： 首先，它通常是執行 SQL Server 最佳化，以最佳化效能的第二個與 BizTalk 資料庫所需，許多 BizTalk 解決方案讓使用自訂的資料庫。 使用自訂的資料庫可能成為瓶頸，以在方案中的，如果正確的最佳化不會套用至 SQL Server 環境。 若要識別並套用適當的資料庫最佳化，下列的 SQL Server 技能則通常需要：  
  
  - 徹底了解 SQL Server 預存程序程式碼，包括能夠最佳化現有的預存程序。  
  
  - 找出並建立資料庫的遺漏索引的能力。  
  
  - 撰寫指令碼來將資料庫分割成多個檔案的能力。  
  
    > [!NOTE]  
    >  如需有關如何套用此最佳化的詳細資訊，請參閱[最佳化檔案群組的資料庫 2](../technical-guides/optimizing-filegroups-for-the-databases2.md)。  
  
  - 若要找出使用 SQL Server 2008 R2 績效儀表板報告的效能問題的能力。  
  
    > [!NOTE]  
    >  SQL Server 2008 R2 績效儀表板報告可供下載： [ http://go.microsoft.com/fwlink/?LinkId=118673 ](http://go.microsoft.com/fwlink/?LinkId=118673)。  
  
    每個效能評定所涉及的專家技術，如同上述 SQL Server 應定義一份需求。 這可確保取得的資源有清楚的期望的功能將會需要它們。 經常效能評定期間需要特殊的知識的另一個技術是 IBM Websphere MQ。 下列清單說明 IBM WebSphere MQ 產品專家的需求規格：  
  
  - 監視、 維護和 MQSeries 的自訂體驗。  
  
  - 安裝和移轉的新版本的 MQSeries 的體驗。  
  
  - 分析及調整 MQSeries 效能的能力。  
  
  - 執行 MQSeries 問題分析。  
  
  - 處理序和 MQSeries 安全性、 管理、 復原和自動化的相關程序的知識。  
  
- **文件的潛在客戶**-持續更新實驗室文件端對端整個效能評定是非常重要。 最佳化已成功套用在生產環境中，並取得所需的層級的效能，但系統之前，應該不判斷 lab engagement 整體 successfulness。 若要這樣做，請務必詳細的記錄下列資訊會保留：  
  
  -   實驗室的高層級的結果摘要  
  
  -   未解決的問題  
  
  -   已解決的問題  
  
  -   實驗室的時間軸  
  
  -   實驗室進度  
  
  -   依類別的實作的最佳化  
  
  -   依時間先後順序 （以確保它們可以套用相同的順序在生產系統中） 的實作的最佳化  
  
  -   高階架構圖  
  
  -   要測試案例的詳細資料  
  
  -   其中涉及的協力廠商技術  
  
  -   實驗室硬體圖形  
  
  -   連絡人清單  
  
  -   詳細的硬體清查  
  
  -   使用完整的詳細結果的附錄  
  
- **開發人員**-開發人員是否需要大部分取決於 engagement 的範圍。 如果程式碼基底已經鎖定，而且實驗室的目的是要測試基礎結構與平台最佳化則只是開發人員的服務不應該需要。 當執行效能測試實際執行伺服器的"go live"日期之前，會發生這種情況。 此時，程式碼應該已遭鎖定，而且完整的迴歸測試應該是完整的或進行中。 在實驗室中導入的程式碼的任何變更，可以導入迴歸，因此，在生產系統中產生的風險。 如果允許程式碼變更，則開發人員通常會需要。 下列清單代表通常由開發人員參與 BizTalk Server 效能評定所需的技能：  
  
  -   若要找出並修正效能問題與協調流程的能力  
  
  -   找出並修正效能問題與管線的能力  
  
  -   熟悉.NET 包括：  
  
      -   企業程式庫  
  
      -   Visual Studio 的 F1 profiler 專業知識  
  
      -   Microsoft Visual Studio 2010 Ultimate 或 Visual Studio 測試 Professional 2010  
  
- **測試組長**-確保取得精確、 完整且透徹一組結果，是很重要。 測試潛在客戶會負責確保擷取、 適當地分析和適當地散發之後每個測試回合, 所需的資訊。 請務必考慮如何將資料擷取、 測試資料通常是適用於 Excel 試算表的簡報。 下列清單說明應該針對每個實驗室期間執行的測試中擷取的資料：  
  
  - 測試回合的數目  
  
  - date  
  
  - 處理的訊息總數  
  
  - 每秒處理的訊息  
  
  - 開始時間  
  
  - 已停止的時間  
  
  - 測試持續時間，以分鐘為單位  
  
  - 擱置的訊息已處理的訊息總數 / 這可以擷取從 BizTalk 管理主控台，或是藉由測量使用效能監視器的 BizTalk Server 效能計數器。  
  
  - \# 無法處理訊息的  
  
  - \# 或已成功處理的訊息  
  
  - 測試用戶端回應  
  
  - 用戶端處理序持續時間的平均值，以秒為單位通常實作同步的訊息方案，與 BizTalk Server 時，這個值會測量，在此情況下就一定要知道值的平均用戶端持續時間，因為這通常是代表多久畷樾簅正在等候回應從解決方案。  
  
  - 用戶端處理序持續時間上限值，以秒為單位  
  
  - 用戶端處理序持續時間最小值，以秒為單位  
  
  - BizTalk Server 的要求/回應延遲，以秒為單位  
  
  - 每秒完成的協調流程  
  
  - %的時間處理的訊息  
  
  - 值**TestResultsLocation** Visual Studio Team System 測試工具所使用的變數。  
  
  - 值**TestResultsLocation** BizUnit 所使用的變數。  
  
  - 任何意見或建議  
  
    收集結果，以及測試潛在客戶應該確保他們會監視每個測試回合來查看是否有任何的趨勢。 提升的效能應該傳送到小組的其餘部分，以及應該會指出多少效能已改善，以及哪一個最佳化已套用到改善。 在一天結束務必測試負責人提供已在實驗室中執行的測試摘要。 這可讓專案關係人保持持續實驗室的進度通知。 下表說明如何這項資訊可能會放在一起範例更新電子郵件中：  
  
  ### <a name="test-results-summary"></a>測試結果摘要  
  
  |[狀態]|輸送量|平均延遲|%< 2 秒|測試回合的數目|# 個 BizTalk Server 電腦|# 個訊息|平均訊息大小|Duration|  
  |------------|----------------|---------------------|-------------------|---------------------|------------------------------------|--------------------|--------------------------|--------------|  
  |相應放大|140 訊息/秒|0.777 秒|99.3%|2|6|270,000|609 位元組|30 分鐘|  
  |最佳|50 的訊息/秒|1.12 秒|99.12%|17|2|360,000|609 位元組|2 小時|  
  |基準|30 訊息/秒|1.52 秒|92.9 %|4|2|36,000|609 位元組|20 分鐘|  
  |目標|5 訊息/秒|< 2 秒|90%|-|2|-|-|-|  
  
## <a name="define-all-deliverables-that-are-required-at-the-onset-of-the-performance-assessment"></a>定義所有交付項目所需的效能評定開始  
 請務必同意必須要備妥，再開始 BizTalk Server 效能評定的交付項目。 下一節描述應該位於效能評估的開始位置的交付項目。  
  
- **要測試的應用程式**– 效能評定期間，會使用完整的應用程式必須可用。 很重要，在應用程式開始效能評定之前進行完整的狀態，否則沒有遺失重要的實驗室測試時的風險。  
  
- **自動化的建置與部署規劃**-再進行效能評定中，自動化的組建和部署程序應該開發 BizTalk Server 解決方案的測試。 自動化應用程式的建置程序，可讓您執行連續每日組建流程，然後伴隨著一組可用來測試整個系統的功能性流程的組建驗證測試 (Bvt)。 這可讓您偵測編譯與運作的問題，更快速且輕鬆在整個開發生命週期。 在實驗室中，這表示如果需要變更任何程式碼可以快速確認更新的方案就不會出現問題。 以手動方式建置、 部署和設定應用程式的效能實驗室可以是既繁瑣又錯誤很容易出錯的工作。 因此建議您使用自動化技術，用來完成下列建置和部署活動：  
  
  -   從原始檔控制中取得最新的程式碼。  
  
  -   建置完整的解決方案。  
  
  -   將方案部署到環境。  
  
  -   建立 BizTalk 應用程式。  
  
  -   將 BizTalk Server 資源，例如.dll 檔案和繫結新增至 BizTalk 應用程式中。  
  
  -   若要建立的連接埠和繫結至協調流程的繫結檔案匯入。  
  
  -   匯出 BizTalk 應用程式為 Microsoft® Windows® Installer 套件，以便它可以在測試或生產環境中部署。  
  
  > [!NOTE]  
  >  如需有關如何實作自動化的建置程序的詳細資訊，請參閱[自動化建置程序](../technical-guides/automating-the-build-process.md)  
  
   .NET framework 2.0 可讓開發人員自動化工作，例如前文所述稍早被引進 MSBuild。 數個 BizTalk Server 特有的 MSBuild 工作所含的 SDC 工作程式庫，也就是可從下載[ http://go.microsoft.com/fwlink/?LinkId=119288 ](http://go.microsoft.com/fwlink/?LinkId=119288)。  
  
- **測試資料用於效能評定期間**– 使用測試資料具有相當大的影響，整體的效率和效能評定的成功。  假設訊息、 協調流程和規則引擎的 BizTalk Server 應用程式會利用。 規則引擎會從內呼叫管線元件在接收端，以判斷哪一個協調流程將會用來處理訊息，而它也會從呼叫來判斷流程的各個點上的協調流程中。 規則引擎會實作快取，以便最佳化執行規則原則。 因此，如果單一訊息當做測試資料中，效能評定期間，測試結果可能會扭曲 （因為快取），而且可能會取得無法在生產環境中複寫的結果。  
  
   在理想情況下效能評估期間所使用的測試資料應該實際生產資料或實際執行資料的子集。 負載和流量會流經生產系統的模式，也應該模擬的測試資料。 當定義需求的測試資料，請考慮下列因素：  
  
  - **在指定時間將會流經整個系統的訊息數目**-這通常表示為每秒的訊息或每小時的訊息。  
  
  - **類型的訊息**– 是訊息的一般檔案、 XML 或二進位檔？  
  
  - **訊息散佈**– 百分比會將使用多少百分比的每個 XML 訊息類型的一般檔案？  
  
  - **處理需求的尖峰負載**-在許多情況下，大型的交換可能會處理在非尖峰時段。 例如付款的大型批次可能會在午夜張貼到銀行的系統。 如果發生這種情況，確保您能夠複寫這在測試期間。  
  
  - **用來接收/傳送訊息的端點**-在許多環境的個別接收位置會設定為接收不同類型的訊息。 比方說可能使用 File 配接器接收一般檔案訊息或 MQSeries 配接器可能會用來接收 XML 訊息。 雖然訊息可能所有由處理相同的協調流程就可以進入系統的不同進入點。 每個這些不同的接收位置可以裝載於個別的主控件;事實上執行此動作通常會改善系統的整體效能。  
  
    下表提供應該決定測試資料的規格時擷取之資訊的範例：  
  
  ### <a name="sample-test-data-specification"></a>範例測試資料的規格  
  
  |                                             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
  |---------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  |           **每秒的訊息**           |                                                                                                                                                                                                                                                                                   -最大輸送量是在此案例中的索引鍵<br />-目標為每秒 50 則訊息<br />-低度延遲並不是目標                                                                                                                                                                                                                                                                                    |
  |            **訊息類型**             |                                                                                                                                                                                                                                                                  -小型的 XML 訊息，符合 XML 結構描述大約 25 的 KB *X*<br />-中度的 XML 訊息，大約 512KB 符合 XML 結構描述*Y*                                                                                                                                                                                                                                                                  |
  |        **訊息散佈**         |                                                                                                                                                                                                          -58 %25 KB （小型的 XML 訊息）<br />-25 %512 KB （中型 XML 訊息）<br />-11 %3 MB （中型二進位資料 – PDF）-非可壓縮<br />-4 %7.5 MB （大型二進位資料 – PDF）-非可壓縮)<br />-2 %20 MB （大型二進位資料 – PDF）-非可壓縮                                                                                                                                                                                                          |
  |    **尖峰負載的處理需求**    |                                                                                                                                                                                                                                  大型二進位資料 (20 MB) 會代表大約 2%的資料 （如上述所指定） 的這處理的時間為非可預測。 系統必須能夠容納這些大型訊息在任何指定時間。                                                                                                                                                                                                                                  |
  | **用來接收/傳送訊息的端點** | **小型的 XML 訊息 (25 KB)**<br /><br /> -接收位置： PaymentXMLDocIn<br />-裝載： ReceiveHost<br />-使用的管線： XMLReceive<br /><br /> **中的 XML 訊息 (512 KB)**<br /><br /> -接收位置： PaymentXMLDocIn<br />-裝載： ReceiveHost<br />-使用的管線： XMLReceive<br /><br /> **中度的二進位資料 (3 MB) 的 – PDF – 非可壓縮**<br /><br /> -接收位置： BinaryDataIn<br />-裝載： ReceiveHost<br />-使用的管線： PassThruReceive<br /><br /> **大型二進位資料 (7.5 MB – 20 MB) – PDF – 非可壓縮**<br /><br /> -接收位置： BinaryDataIn<br />-裝載： ReceiveHost<br />-使用的管線： PassThruReceive |
  |          **測試資料的位置**          |                                                                                                                                                                                                                                                                                                    在本機存取的測試資料檔案共用，例如： \\\PerformanceLabs\July\Test Data\                                                                                                                                                                                                                                                                                                    |
  
   將資訊放入資料表時，會完成幾件事。 第一次，讓它更為容易專案關係人同意做測試資料的相關假設。 第二，它提供您可用來決定可能的最佳化，效能評定的資訊。 比方說在您的資料表可以看到用來處理所有的不同資料類型的所有接收位置都都裝載在 ReceiveHost BizTalk 主控件。 這表示此主控件的每個執行個體將會負責處理不同類型和大小的資料 （例如 XML 和二進位的非可壓縮 PDF 資料）。 假設每個主控件執行個體是單一執行個體的 BizTalk Server 程序 (BTSNTSVC。EXE)，這可能會變成處理瓶頸。 因此在此案例中顯而易見的最佳化，環境就是測試改進後的效能各自分隔的其中一個會接收到它自己個別的主控件的位置。 具有摘要的表格式格式 」 的測試資料的資訊的存取權，讓這類簡單的最佳化量測計的工作變得更容易。  
  
- **規劃進行自動化負載測試，並且載入產生**-建立效能評定測試資料設定檔之後，務必考慮如何執行負載測試的環境中。 BizTalk Server 2010 負載測試，我們會使用 Visual Studio 2010 負載測試。 如需如何加速負載測試使用 Visual Studio 2010 的詳細資訊，請參閱[使用 Visual Studio 促進自動化測試](../technical-guides/using-visual-studio-to-facilitate-automated-testing.md)。  
  
## <a name="see-also"></a>另請參閱  
 [效能評定的階段](../technical-guides/phases-of-a-performance-assessment.md)