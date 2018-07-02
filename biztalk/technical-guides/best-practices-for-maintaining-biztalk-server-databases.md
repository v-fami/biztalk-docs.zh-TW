---
title: 維護 BizTalk Server 資料庫的最佳作法 |Microsoft Docs
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
ms.openlocfilehash: 6b1d8f03201b04a3be1f7908eaf7e763a4ade226
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981247"
---
# <a name="best-practices-for-maintaining-biztalk-server-databases"></a>維護 BizTalk Server 資料庫的最佳做法
本主題列出維護的一些最佳做法[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。  
  
- 請確定 SQL Server Agent 正在執行的 SQL Server 上。 SQL Server Agent 停止時，無法執行負責維護資料庫的內建 BizTalk SQL Server Agent 作業。 這個行為會導致資料庫成長，這種成長，可能會造成效能問題。 如需監視 SQL Server Agent 作業的詳細資訊，請參閱[監視 SQL Server Agent 作業](../technical-guides/monitoring-sql-server-agent-jobs.md)。  
  
- 請確定 SQL Server LDF 和 MDF 檔案是位在不同的磁碟機。 具有相同的磁碟機上 BizTalkMsgBoxDb 和 BizTalkDTADb 資料庫的 LDF 和 MDF 檔案，可能會導致磁碟爭用情況。  
  
- 請勿啟用訊息內文追蹤，如果不需要。 通常，您可能要啟用訊息內文追蹤，而您會開發和疑難排解解決方案。 如果是的話，請確定您停用訊息內文追蹤完成時。 如果您保留訊息內文追蹤，啟用 BizTalk Server 資料庫成長。 如果您有要求您啟用訊息內文追蹤的商務需求，請確認**TrackedMessages_Copy_BizTalkMsgBoxDb**並**DTA 清除與封存**執行 SQL Server Agent 作業已成功。  
  
- 一般而言，較小的交易記錄檔會導致更好的效能。 若要保持較小的交易記錄檔，設定**備份 BizTalk Server**更常執行的 SQL Server Agent 作業。 如需詳細資訊，請參閱 < [BizTalk Server 資料庫最佳化白皮書](http://go.microsoft.com/fwlink/?LinkId=153594)(http://go.microsoft.com/fwlink/?LinkId=153594)。  
  
- 使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]要評估現有的 Best Practices Analyzer (BPA)[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署。 BPA 會執行許多資料庫相關的檢查。 您可以下載從 BizTalk Server Best Practices Analyzer 工具[BizTalk Server Best Practices Analyzer 工具](http://go.microsoft.com/fwlink/?LinkId=83317)(<http://go.microsoft.com/fwlink/?LinkId=83317>)。  
  
## <a name="see-also"></a>另請參閱  
 [檢查清單： 維護和疑難排解 BizTalk Server 資料庫](~/technical-guides/checklist-maintaining-and-troubleshooting-biztalk-server-databases.md)   
 [日益成長的 BizTalk Server 資料庫資料表](../technical-guides/large-growing-biztalk-server-database-tables.md)