---
title: 維護 BizTalk Server 資料庫的最佳作法 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93333f41-ee83-4b64-b381-66584a7d5551
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b5f6cf1fadf5c039c53e6cca46792c4660353d0c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22299998"
---
# <a name="best-practices-for-maintaining-biztalk-server-databases"></a>維護 BizTalk Server 資料庫的最佳作法
本主題列出維護的一些最佳作法[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。  
  
-   請確定 SQL Server Agent 正在執行 SQL Server 上。 SQL Server Agent 停止時，負責維護資料庫的內建 BizTalk SQL Server Agent 工作無法執行。 這個行為會導致資料庫成長，而且這股成長可能造成效能問題。 如需監視 SQL Server Agent 作業的相關資訊，請參閱[監視 SQL Server Agent 作業](../technical-guides/monitoring-sql-server-agent-jobs.md)。  
  
-   請確定 SQL Server LDF 和 MDF 檔案是位在不同的磁碟機。 具有相同的磁碟機上 BizTalkMsgBoxDb 和 BizTalkDTADb 資料庫的 LDF 和 MDF 檔案可能會導致磁碟爭用情況。  
  
-   請勿啟用訊息內文追蹤，如果不需要。 通常，您可以啟用訊息內文追蹤，在您開發並疑難排解方案。 如果是的話，請確定您停用訊息內文追蹤完成時。 如果您保留訊息內文追蹤，啟用 BizTalk Server 資料庫成長。 如果您有要求您啟用訊息內文追蹤的商務需求，請確認**TrackedMessages_Copy_BizTalkMsgBoxDb**和**DTA 清除與封存**執行 SQL Server Agent 作業已成功。  
  
-   一般而言，較小的交易記錄檔會產生較佳的效能。 若要保持較小的交易記錄檔，設定**備份 BizTalk Server**更常執行的 SQL Server Agent 作業。 如需詳細資訊，請參閱[BizTalk Server 資料庫最佳化白皮書](http://go.microsoft.com/fwlink/?LinkId=153594)(http://go.microsoft.com/fwlink/?LinkId=153594)。  
  
-   使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]要評估現有的 Best Practices Analyzer (BPA)[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署。 BPA 會執行多個資料庫相關的檢查。 您可以下載從 BizTalk Server Best Practices Analyzer 工具[BizTalk Server Best Practices Analyzer 工具](http://go.microsoft.com/fwlink/?LinkId=83317)(http://go.microsoft.com/fwlink/?LinkId=83317)。  
  
## <a name="see-also"></a>另請參閱  
 [檢查清單： 維護和疑難排解 BizTalk Server 資料庫](~/technical-guides/checklist-maintaining-and-troubleshooting-biztalk-server-databases.md)   
 [大型成長的情況的 BizTalk Server 資料庫資料表](../technical-guides/large-growing-biztalk-server-database-tables.md)