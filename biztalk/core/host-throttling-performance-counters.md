---
title: 主控件節流效能計數器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- host throttling, performance counters
ms.assetid: b9090d1c-86be-40db-b814-cc116a426d95
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ca80f44b9f1244a340e9a9892593ae42ba4b4e9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25971868"
---
# <a name="host-throttling-performance-counters"></a>主控件節流效能計數器
本節描述測量影響主控件節流之系統參數的效能監控計數器。 下列效能計數器會在每個主控件執行個體可存取**biztalk： 訊息代理程式**效能物件類別：  
  
|計數器|Description|  
|-------------|-----------------|  
|作用中執行個體計數|記憶體中作用中的服務執行個體數目。 對於協調流程引擎來說，服務執行個體指的是每個執行中的協調流程排程執行個體。 對於結束點管理員來說，服務執行個體可能是對應至單一無狀態的訊息或有狀態的訊息集合。 **注意：** 可設定狀態的執行個體是保留的訊息執行個體相關聯的特定狀態資訊。 屬於有狀態執行個體的訊息會以某種形式相互關聯。 例如，會維護排序資訊的已排序傳送埠即算是有狀態的執行個體。 大部分的傳訊實例包含無狀態的執行個體，其中每個訊息都是完全獨立處理的。 每個這類的無狀態執行個體都會對應至 EPM 中的一個訊息。|  
|資料庫工作階段|使用的並行 MessageBox 資料庫連線數目。|  
|資料庫工作階段閾值|並行資料庫工作階段的目前閾值。 這一開始會設定為**資料庫連接**值**資源型節流**索引標籤中**設定儀表板**。 這個值會根據程序的資料庫工作階段使用量來自動調整。 若並行的資料庫工作階段數目超過此閾值，不論在任何時候，都會實作主控件節流。|  
|資料庫大小|此程序已發佈之資料庫佇列中的訊息數目。 這個值是由所有主控件的佇列表格中之項目數目以及多工緩衝處理與追蹤表格中的項目數目來測量。 若程序正發佈到多個佇列，則此計數器會反映所有佇列的加權平均值。 **注意：** 如果重新啟動主機時，保留在記憶體中的統計資料會遺失。 由於此作業會造成部分負擔，因此發佈數目至少必須有 100 個，而且至少佔重新啟動主控件程序中發佈總數的 5%，BizTalk Server 才會繼續收集統計資料。|  
|高資料庫工作階段|-0： 一般<br />-1： 資料庫工作階段計數超過閾值|  
|高資料庫大小|-0： 一般<br />-1： 資料庫大小已成長超出閾值<br /><br /> 此計數器將設定為其中一個值，如果任一個條件列出**訊息 DB 中的計數**臨界值，就會發生。 [如何修改資源基礎節流設定](../core/how-to-modify-resource-based-throttling-settings.md)提供此節流臨界值的相關資訊。|  
|高內含式訊息計數|-0： 一般<br />-1： 內含式訊息計數超過限制|  
|高訊息傳遞速率|-0： 一般<br />-1： 訊息傳遞速率超過訊息處理速率|  
|高訊息發佈速率|-0： 一般<br />-1： 發佈要求速率超過完成速率|  
|高程序記憶體|-0： 一般<br />-1： 處理序記憶體超過閾值|  
|高系統記憶體|-0： 一般<br />-1： 系統記憶體超過閾值|  
|高執行緒計數|-0： 一般<br />-1： 執行緒計數超過閾值|  
|內含式訊息計數|已傳遞到 XLANG 引擎或輸出傳訊引擎但尚未處理的記憶體中訊息數目。|  
|內含式訊息計數閾值|內含式訊息計數目前的閾值。|  
|訊息傳遞延遲 (ms)|每個訊息傳遞批次的目前延遲 (以毫秒為單位) (適用於訊息傳遞正在進行節流)。|  
|訊息傳遞內送速率|在指定的範例間隔中，每秒傳遞到協調流程引擎或傳訊引擎的訊息數目。|  
|訊息傳遞外寄速率|在指定的範例間隔中，協調流程引擎或傳訊引擎每秒處理的訊息數目。|  
|訊息傳遞節流狀態|指出系統是否正在進行訊息傳遞節流的一個旗標 (影響 XLANG 訊息處理及輸出傳輸)。<br /><br /> -0： 未進行節流<br />-1： 由於不平衡的訊息傳遞速率而進行節流 （輸入的速率超過輸出速率）<br />-3： 節流由於高內含式訊息計數<br />-4： 由於程序記憶體壓力而進行節流<br />-5： 由於系統記憶體不足的壓力而進行節流<br />-9： 由於高執行緒計數而進行節流<br />-10： 由於使用者而進行節流傳遞覆寫|  
|訊息傳遞節流狀態持續時間|系統進入此狀態後的秒數。 若主控件進行節流，指出進行節流的時間已有多久；若主控件未進行節流，則指出從上次進行節流到現在的時間已有多久。|  
|訊息傳遞節流使用者覆寫|此計數器會反映由引擎監控的使用者覆寫，解譯如下：<br /><br /> -0： 沒有覆寫<br />-1： 一律對訊息傳遞節流<br />-2： 不要節流訊息傳遞<br /><br /> 此覆寫是可設定在**根據速率的節流**索引標籤中**設定儀表板**。|  
|訊息發佈延遲 (ms)|每個訊息發佈批次的目前延遲 (以毫秒為單位) (適用於訊息發佈正在進行節流，且批次必須進行節流時)。|  
|訊息發佈內送速率|在指定的範例間隔中，每秒傳送到資料庫進行發佈的訊息數目。|  
|訊息發佈外寄速率|在指定的範例間隔中，資料庫中每秒實際發佈的訊息數目。|  
|訊息發佈節流狀態|指出系統是否正在進行訊息發佈節流的一個旗標 (影響 XLANG 訊息處理及輸入傳輸)。<br /><br /> -0： 未進行節流<br />-2： 由於不平衡的訊息發佈速率而進行節流 （輸入的速率超過輸出速率）<br />-4： 由於程序記憶體壓力而進行節流<br />-5： 由於系統記憶體不足的壓力而進行節流<br />-6： 由於資料庫成長而進行節流<br />-8： 由於高工作階段計數而進行節流<br />-9： 由於高執行緒計數而進行節流<br />-11： 由於使用者而進行節流覆寫發佈|  
|訊息發佈節流狀態持續時間|系統進入此狀態後的秒數。 若主控件進行節流，指出進行節流的時間已有多久；若主控件未進行節流，則指出從上次進行節流到現在的時間已有多久。|  
|訊息發佈節流使用者覆寫|此計數器會反映由引擎監控的使用者覆寫，解譯如下：<br /><br /> -0： 沒有覆寫<br />-1： 一律對訊息發佈進行節流<br />-2： 不要將訊息發佈節流<br /><br /> 此覆寫是可設定在**根據速率的節流**索引標籤中**設定儀表板**。|  
|實體記憶體使用量 (MB)|所有程序在電腦上使用的實體記憶體數量 (以 MB 為單位)。|  
|程序記憶體使用量 (MB)|程序記憶體的耗用量 (以 MB 為單位)。 這是程序工作組大小以及配置給程序分頁檔總空間的上限。|  
|程序記憶體使用量閾值 (MB)|程序記憶體耗用量的目前閾值 (以 MB 為單位)。 這一開始會設定為**程序虛擬**值**設定儀表板**。 若已指定百分比值，就會根據可進行認可的可用記憶體來計算該值|  
|服務類別識別碼|此效能計數器執行個體對應至的服務類別 GUID 開頭部分的十進位值。 程序可能會裝載一個以上的服務類別，且訊息代理程式效能計數器會顯示最活躍之服務類別的資料。|  
|執行緒計數|程序中正在使用的執行緒數目。|  
|執行緒計數閾值|程序中執行緒數目的目前閾值。 這一開始會設定為**執行緒**值**資源型節流**索引標籤中**設定儀表板**。 這個值會根據目前程序的執行緒需求來自動調整。 若程序中的執行緒數目超過此閾值，不論在任何時候，都會實作主控件節流。|  
|認可的總批次數|服務類別已認可的資料庫批次數目。|  
|傳遞的總訊息數|傳遞到協調流程引擎或結束點管理員 (EPM) 的輸出訊息數目。|  
|已發佈的總訊息數|已發佈的訊息數目。|  
  
> [!NOTE]
>  **Biztalk： 訊息代理程式**效能計數器可供分析主控件節流行為的明確目的，因此不會擷取的資料除非指定的主機目前正在處理的文件。 此行為是設計來防止在未發生節流活動時，耗用系統執行緒及效能監控器。  
  
## <a name="to-access-performance-counters"></a>存取效能計數器  
 使用下列步驟來存取效能計數器。  
  
#### <a name="if-you-are-using-windows-2008"></a>若是使用 Windows 2008  
  
1.  按一下**啟動**，指向 **系統管理工具**，然後按一下 **效能監視器**。  
  
2.  在**效能監視器**對話方塊方塊中，展開 **監視工具**，選取**效能監視器**，然後按一下 **新增**。  
  
3.  在**新增計數器**對話方塊中，從**可用的計數器**清單中，展開**biztalk： 訊息代理程式**效能計數器物件，然後選取要計數器監視。  
  
4.  在**選取執行個體的物件**清單中，選取要監視針對所選取計數器，然後按一下 特定的執行個體**新增**。  若要選取所有可用的計數器執行個體，請選取\<**所有執行個體**\>。  
  
5.  新增計數器後, 按一下**確定**。  
  
     選取的效能計數器隨即出現在**效能監視器**螢幕。  
  
## <a name="see-also"></a>請參閱  
 [節流設計建議](../core/throttling-design-recommendations.md)   
 [BizTalk Server 如何實作主控件節流](../core/how-biztalk-server-implements-host-throttling.md)   
 [針對 BizTalk Server 效能調整使用設定儀表板](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)