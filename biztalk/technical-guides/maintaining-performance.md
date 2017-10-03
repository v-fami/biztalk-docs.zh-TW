---
title: "維護效能 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae7e63ed-4e28-45b1-ab00-be9f9488a2e6
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da10987a6532987ff7a2ed925e717a0a713cac6e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="maintaining-performance"></a>維護效能
本節旨在協助您解決例行維護檢查期間所發現的效能問題的資訊。 您也可以使用的工具和技術此處所述主動，嚴重的問題之前就識別潛在問題。  
  
 您通常必須先建立效能基準線的標準，據以評估目前的系統效能。  
  
 除了本節中的主題，這份文件中的其他主題會解決效能問題。 這些主題會列出相關的下列章節中。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [維護效能的最佳作法](../technical-guides/best-practices-for-maintaining-performance.md)  
  
-   [設定批次處理來改善配接器效能](../technical-guides/configuring-batching-to-improve-adapter-performance.md)  
  
-   [如何調整組態快取重新整理間隔](../technical-guides/how-to-adjust-the-configuration-cache-refresh-interval.md)  
  
-   [如何停用追蹤](../technical-guides/how-to-disable-tracking.md)  
  
-   [疑難排解效能 Issues3](../technical-guides/troubleshooting-performance-issues3.md)  
  
## <a name="related-sections"></a>相關章節  
  
-   如需有關效能的問題一般情況下，請參閱[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能最佳化指南 》，網址[http://go.microsoft.com/fwlink/?LinkID=150492](http://go.microsoft.com/fwlink/?LinkID=150492)。  
  
-   分析每週的效能監視器記錄檔基準和臨界值的相關資訊，請參閱[使用效能分析的記錄檔 (PAL) 工具](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md)，「 尋找並消除中的瓶頸"[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能最佳化指南[http://go.microsoft.com/fwlink/?LinkId=154675](http://go.microsoft.com/fwlink/?LinkId=154675)，和[疑難排解效能 Issues3](../technical-guides/troubleshooting-performance-issues3.md)。  
  
-   如需確保系統不會遇到經常自動成長[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，請參閱[定義資料庫的自動成長設定](../technical-guides/defining-auto-growth-settings-for-databases.md)，< 追蹤資料庫大小調整指導方針 > 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助在[http://go.microsoft.com/fwlink/?LinkId=154677](http://go.microsoft.com/fwlink/?LinkId=154677)、 和中的 「 識別資料庫層中的瓶頸"[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助在[http://go.microsoft.com/fwlink/?LinkId=154678](http://go.microsoft.com/fwlink/?LinkId=154678)。  
  
-   如需維護 SQL Server 資訊[執行的 SQL Server 維護程序](~/technical-guides/checklist-configuring-sql-server.md)。  
  
-   執行 SQL Server Profiler 來檢查長回應時間及高資源使用量的高負載期間的相關資訊，請參閱 「 使用 SQL Server Profiler"在 SQL Server 說明中在[http://go.microsoft.com/fwlink/?LinkID=106720](http://go.microsoft.com/fwlink/?LinkID=106720)。  
  
-   確保所有配接器的訊息批次處理適當的資源耗用量或延遲的相關資訊，請參閱[設定批次處理，以改善配接器效能](../technical-guides/configuring-batching-to-improve-adapter-performance.md)。  
  
-   如需增加 BizTalk Server 快取重新整理間隔的詳細資訊，請參閱[如何調整設定快取重新整理間隔](../technical-guides/how-to-adjust-the-configuration-cache-refresh-interval.md)。  
  
-   輸入和輸出主控件節流的相關資訊，請參閱 「 什麼是主控件節流？ 」 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助在[http://go.microsoft.com/fwlink/?LinkId=154694](http://go.microsoft.com/fwlink/?LinkId=154694)。 如需觸發程序、 動作，以及移轉策略輸入和輸出節流的資訊，請參閱"節流狀況觸發程序、 動作和緩和策略"中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助在[http://go.microsoft.com/fwlink/?LinkId = 154695](http://go.microsoft.com/fwlink/?LinkId=154695)。  
  
-   若要使用通過傳送管線，而不是預設的 XML 傳送管線，請參閱 「 管理傳送埠使用 BizTalk 總管 」 中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助在[http://go.microsoft.com/fwlink/?LinkID=154696](http://go.microsoft.com/fwlink/?LinkID=154696)。  
  
-   調整追蹤資料庫大小的相關資訊，請參閱 < 追蹤資料庫大小指導方針 >，在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助在[http://go.microsoft.com/fwlink/?LinkId=154677](http://go.microsoft.com/fwlink/?LinkId=154677)。  
  
-   調整大小的 MessageBox，BizTalkDTADb、 BAMPrimaryImport 資料庫的相關資訊，請參閱 「 識別瓶頸在資料庫層 」，在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助在[http://go.microsoft.com/fwlink/?LinkId=154678](http://go.microsoft.com/fwlink/?LinkId=154678)。  
  
-   如需避免競爭 MessageBox 資料庫中的資訊，請參閱[如何避免磁碟爭用](http://go.microsoft.com/fwlink/?LinkId=158809)([http://go.microsoft.com/fwlink/?LinkId=158809](http://go.microsoft.com/fwlink/?LinkId=158809)) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能最佳化指南。