---
title: 維護效能 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ae7e63ed-4e28-45b1-ab00-be9f9488a2e6
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bdaa00ebb244db6d389393a0bbf32c0075c1f3d3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984423"
---
# <a name="maintaining-performance"></a>維護效能
本章節提供可協助您解決在例行維護檢查期間探索到的效能問題的資訊。 您也可以使用的工具和技術，此處所述主動，來識別潛在的問題之前就嚴重的問題。  

 您通常必須在建立效能基準為用來評估目前的系統效能標準。  

 在本節中的主題，除了這份文件中的其他主題會解決效能問題。 這些主題會列出以下相關章節。  

## <a name="in-this-section"></a>本節內容  

-   [維護效能的最佳做法](../technical-guides/best-practices-for-maintaining-performance.md)  

-   [設定批次處理來改善配接器效能](../technical-guides/configuring-batching-to-improve-adapter-performance.md)  

-   [如何調整設定快取重新整理間隔](../technical-guides/how-to-adjust-the-configuration-cache-refresh-interval.md)  

-   [如何停用追蹤](../technical-guides/how-to-disable-tracking.md)  

-   [疑難排解效能 Issues3](../technical-guides/troubleshooting-performance-issues3.md)  

## <a name="related-sections"></a>相關章節  

- 如需有關效能問題的請參閱[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能最佳化指南 》，網址[ http://go.microsoft.com/fwlink/?LinkID=150492 ](http://go.microsoft.com/fwlink/?LinkID=150492)。  

- 分析每週效能監視器記錄檔，針對 [基準] 和 [臨界值的相關資訊，請參閱[使用效能分析的記錄檔 (PAL) 工具](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md)、 「 尋找並消除中的瓶頸"[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能最佳化指南[ http://go.microsoft.com/fwlink/?LinkId=154675 ](http://go.microsoft.com/fwlink/?LinkId=154675)，以及[疑難排解效能 Issues3](../technical-guides/troubleshooting-performance-issues3.md)。  

- 如需確保系統不會遇到經常自動成長[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，請參閱[定義資料庫的自動成長設定](../technical-guides/defining-auto-growth-settings-for-databases.md)，「 追蹤資料庫大小調整指導方針 」 中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在協助[ http://go.microsoft.com/fwlink/?LinkId=154677 ](http://go.microsoft.com/fwlink/?LinkId=154677)，和中的 「 識別資料庫層中的瓶頸 」[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助在[ http://go.microsoft.com/fwlink/?LinkId=154678 ](http://go.microsoft.com/fwlink/?LinkId=154678)。  

- 如需維護 SQL Server[執行的 SQL Server 維護程序](~/technical-guides/checklist-configuring-sql-server.md)。  

- 若要檢查長回應時間和高資源使用量的高負載期間執行 SQL Server Profiler 的相關資訊，請參閱 「 使用 SQL Server Profiler"在 SQL Server 說明在[ http://go.microsoft.com/fwlink/?LinkID=106720 ](http://go.microsoft.com/fwlink/?LinkID=106720)。  

- 確保所有配接器的訊息批次處理適用於資源耗用量或延遲的相關資訊，請參閱[設定批次處理來改善配接器效能](../technical-guides/configuring-batching-to-improve-adapter-performance.md)。  

- 如需增加 BizTalk Server 快取重新整理間隔的詳細資訊，請參閱 <<c0> [ 如何調整設定快取重新整理間隔](../technical-guides/how-to-adjust-the-configuration-cache-refresh-interval.md)。  

- 輸入和輸出主控件節流的相關資訊，請參閱 「 主控件節流為何？ 」 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在幫助[ http://go.microsoft.com/fwlink/?LinkId=154694 ](http://go.microsoft.com/fwlink/?LinkId=154694)。 如需觸發程序、 動作和輸入和輸出節流的緩解策略，請參閱 「 節流狀況觸發程序、 動作和緩解策略 」 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在幫助[ http://go.microsoft.com/fwlink/?LinkId=154695 ](http://go.microsoft.com/fwlink/?LinkId=154695)。  

- 若要使用通過傳送管線，而不是預設值 XML 傳送管線，請參閱 「 管理傳送埠使用 BizTalk 總管 」 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在幫助[ http://go.microsoft.com/fwlink/?LinkID=154696 ](http://go.microsoft.com/fwlink/?LinkID=154696)。  

- 調整追蹤資料庫大小的相關資訊，請參閱"追蹤資料庫大小調整指導方針 」，在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在幫助[ http://go.microsoft.com/fwlink/?LinkId=154677 ](http://go.microsoft.com/fwlink/?LinkId=154677)。  

- 調整大小的 MessageBox，BizTalkDTADb、 BAMPrimaryImport 資料庫的相關資訊，請參閱 「 識別瓶頸在資料庫層 」，在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在幫助[ http://go.microsoft.com/fwlink/?LinkId=154678 ](http://go.microsoft.com/fwlink/?LinkId=154678)。  

- 如需避免爭用 MessageBox 資料庫中的資訊，請參閱[如何避免磁碟爭用](http://go.microsoft.com/fwlink/?LinkId=158809)([http://go.microsoft.com/fwlink/?LinkId=158809](http://go.microsoft.com/fwlink/?LinkId=158809)) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能最佳化指南。
