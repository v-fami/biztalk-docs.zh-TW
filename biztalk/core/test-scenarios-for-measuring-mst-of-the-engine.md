---
title: 測量引擎 MST 的測試案例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e54667b9-7262-43c8-a013-9242eb062daf
caps.latest.revision: 28
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4fe9fd977563553e62d10675ee35caa673cf0c8e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998919"
---
# <a name="test-scenarios-for-measuring-mst-of-the-engine"></a>測量引擎 MST 的測試實例
本節描述一個測試實例，實作此實例以測量在三個不同負載層級驅動 BizTalk 系統的效果：  
  
- [持續性負載測試](../core/sustainable-load-test.md)。 基於這些測試的詳細資訊，持續性負載主題所述[什麼是持續性效能？](../core/what-is-sustainable-performance.md)。  
  
- [加速負載測試](../core/overdrive-load-test.md)。 加速負載的定義一致的負載超過 MST。  
  
- [大量負載測試](../core/floodgate-load-test.md)。 大量負載的低負載間歇尖峰的負載超過 MST 之定義。  
  
  本主題描述測試硬體組態、測試實例，並討論這些測試的每一個發現。  
  
> [!IMPORTANT]
>  讀者必須注意，本節包含的資訊代表 Microsoft 在發行日當時對討論之問題的觀點。 由於我們必須回應不斷變化的市場狀況與技術，因此 Microsoft 無法保證發行日之後提出之任何資訊的正確性。  
  
## <a name="test-system-configuration"></a>測試系統組態  
 這個測試實例是使用下列硬體：  
  
- **六部 BizTalk Server**。 每部都配備了兩個 3GHz 處理器和 2GB 的 RAM。 每部伺服器都使用本機磁碟。 兩部 BizTalk Server 是使用接收主控件的執行個體來設定，另外兩部是使用傳送主控件的執行個體來設定，而剩下的兩部是以用於處理協調流程的主控件執行個體來設定。  
  
- **一個主要 MessageBox 資料庫和非 MessageBox 資料庫的 SQL Server**。 配備八個 2GHz 處理器和 4 GB 的 RAM。 此伺服器是透過光纖連線到快速 SAN 磁碟子系統。 已停用訊息發佈。  
  
- **要發佈到 Messagebox 資料庫的三部 SQL Server**。 配備四個 2GHz 處理器和 4GB 的 RAM。 這些伺服器均是透過光纖連線到快速 SAN 磁碟子系統。 MessageBox 資料庫的資料和交易記錄檔是位於個別的儲存區域網路 (SAN) 邏輯單位數 (LUN) 中。  
  
- **負載驅動程式用戶端電腦**。 配備兩個 3GHz 處理器和 2GB 的 RAM。 此伺服器是用來產生用於測試 BizTalk 系統的負載。  
  
  以下會說明用於負載測試的拓樸。  
  
  **用於負載測試的拓樸**  
  
  ![BizTalk Server 負載測試的硬體拓撲](../core/media/bts06-msttopology.gif "BTS06_MSTTopology")  
  
## <a name="the-test-scenario"></a>測試實例  
 測試實例非常簡單。 負載產生工具 LoadGen 2007 是安裝在負載驅動程式伺服器上，可用來將檔案複本傳送到檔案配接器所監控的共用。 負載生產工具會將輸入檔案執行個體的複本，平均分散到各個檔案共用。  
  
> [!NOTE]
>  下載[LoadGen](https://www.microsoft.com/download/details.aspx?id=14925)。 這項工具的上一個版本，BizTalk Server 2004 負載產生工具可供下載[ http://go.microsoft.com/fwlink/?linkid=108999 ](http://go.microsoft.com/fwlink/?linkid=108999)。 如需有關使用 LoadGen 搭配 MSMQ 配接器的資訊，請參閱[搭配 MSMQ 使用 LoadGen 2007](../core/using-loadgen-2007-with-msmq.md)。  
  
 BizTalk 檔案配接器是設定來監控檔案共用，並將訊息發佈至 MessageBox。 只包含接收圖形與傳送圖型的簡單型協調流程會訂閱已發佈的訊息。 由協調流程發佈回 MessageBox 的訊息會被檔案傳送埠所拾取，並傳送到 SAN 中所定義的一般共用。 抵達輸出 SAN 共用的檔案會立即刪除，以防止長期測試執行期間在該共用上建置檔案。  
  
 這個實例已定義四個主控件，各別用於接收位置、協調流程、傳送埠和追蹤。 為了觀察引擎積存的行為，在測試執行期間會完全關閉追蹤。 依照預設，只會針對管線和協調流程啟動追蹤，所以在 BizTalk 系統管理員中，會針對所使用的協調流程和管線明確地關閉追蹤。  
  
 關閉追蹤之後，就不會建立追蹤主控件的執行個體，以隔離這些測試的核心 MessageBox 行為。  
  
 會使用一個簡單的結構描述，且用於測試的所有執行個體檔案的大小總共為 10KB。 輸入文件會使用 XMLReceive 管線，而不會使用對應元件或輸出元件，這是為了讓測試實例維持簡單，並將觀察重心放在 MessageBox 的行為。  
  
## <a name="parameters-measured-in-the-test"></a>測試中所測量的參數  
 測試中所測量的參數如下：  
  
 **測量的主要測試參數**  
  
 下列參數是測量 MST 時所使用的主要指標：  
  
- 所測量的 MessageBox 積存**多工緩衝處理大小**所提供的計數器**biztalk: messagebox:** 效能物件。 Messagebox 積存是維持性的關鍵指標。 很顯然地，MessageBox 積存不可能無限地繼續成長而不會遭遇任何問題。 因此，一直以來所監控的 MessageBox 資料庫積存的深度，是用來評估維持性。  
  
   命名的 MessageBox 表格**多工緩衝處理**包含系統中的每個訊息的記錄 (作用中或等待被記憶體回收收集)。 監控此資料表中的資料列數目，以及每秒所接收的訊息數目，而不斷增加的系統負載提供了一個輕鬆的方法，來測量可維持的輸送量上限。 這個度量單位指**多工緩衝處理表深度**或是**多工緩衝處理深度**。  
  
- 每秒所測量接收的文件數目**文件數/秒**所提供的計數器**BizTalk： 傳訊**效能物件。  
  
  **測量的次要測試參數**  
  
  下列參數是測量 MST 時可以評估的次要指標。 這些參數可能會影響多工緩衝處理深度的主要指標，以及每秒鐘接收的文件數目。  
  
- 實體磁碟閒置時間的 MessageBox 資料與交易檔案磁碟所測量 **%閒置時間**計數器適用於**LogicalDisk**效能物件。  
  
- 所測量的 MessageBox 伺服器的 CPU 使用率 （%） **%Processor Time**計數器適用於**處理器**效能物件。  
  
- 鎖定逾時，每秒在 MessageBox 資料庫所測量**Lock Timeouts/sec**計數器適用於**sqlserver: Locks**效能物件。  
  
- 負責清除與已移除訊息相關聯之訊息方塊表的 SQL 代理程式，最近執行的時間 (秒)。 這由測量**MsgBox 訊息 Cleanup(Purge Jobs)** 計數器適用於**biztalk: messagebox:** 效能物件。  
  
- 負責清除與已移除訊息部分相關聯之訊息方塊表的 SQL 代理程式，最近執行的時間 (秒)。 這由測量**MsgBox 部分 Cleanup(Purge Jobs)** 計數器適用於**biztalk: messagebox:** 效能物件。  
  
  在測試以判斷最大持續輸送量時，輸入負載會增加到多工緩衝處理表格開始無限成長的點。  
  
> [!NOTE]
>  若您無法產生足夠的負載，讓多工緩衝處理表可以無限地成長，這只是表示系統最慢的部分是在接收端，而非處理/傳送端。  
  

## <a name="next"></a>下一個
  
-   [使用 Microsoft BizTalk LoadGen 2007 工具](../core/using-the-microsoft-biztalk-loadgen-2007-tool.md)  
  
-   [持續性負載測試](../core/sustainable-load-test.md)  
  
-   [加速負載測試](../core/overdrive-load-test.md)  
  
-   [大量負載測試](../core/floodgate-load-test.md)