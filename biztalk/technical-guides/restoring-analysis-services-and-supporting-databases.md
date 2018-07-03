---
title: 還原 Analysis Services 和支援資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 490ad0fb-7805-4ebc-9bc5-117d52d7c3a8
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9cf50a7ef1903d3839aaa9b810e145432b62b552
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37020459"
---
# <a name="restoring-analysis-services-and-supporting-databases"></a>還原 Analysis Services 和支援的資料庫
有兩個[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]必須還原的災害復原案例中的 Analysis Services 資料庫：  
  
- BAM 分析 (BAMAnalysis)  
  
- 追蹤 Analysis Server (BizTalkAnalysisdb)  
  
  BAM[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]可能備份資料庫的 「 備份 BizTalk Server 」 工作一部分如果已啟用但未設定 BAM。  
  
> [!NOTE]  
>  BAM 主要匯入一律備份資料庫的 「 備份 BizTalk Server 」 工作一部分因為它所參與 DTC 交易。  
  
 如果已啟用但未設定 BAM，下列 BAM 資料庫將成為 「 備份 BizTalk Server 」 工作的一部分：  
  
- BAMStarSchema  
  
- BAMArchive  
  
  請依照下列中的步驟[如何在 「 備份 BizTalk Server 」 工作中的 還原資料庫](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md)還原這些資料庫。  
  
  **否則，**  
  **如果 BAM 已啟用，而且也已使用 BM.exe，一組正確的 BAM 資料庫必須還原在一起以一組。** 若要確保會復原一組完整的封存資料，BAM 封存資料庫備份的磁碟分割會複製到 BAM 封存後，但從 BAM 主要匯入資料庫刪除資料分割。 這是由插入最後一個步驟 「 結束封存 」 之前，備份 BAM 封存資料庫的步驟修改每個活動的資料維護 SSIS 封裝執行  
  
  BAM 資料庫的還原程序是： x 的最後備份日期還原 「 BAM 主要匯入資料庫時，請將 BAM 封存和 BAM 星狀結構描述資料庫對應的複本還原最新的資料維護 SSIS 封裝時的日期x 的日期之前執行。  
  
  識別一組正確的 BAM 資料庫之後，還原[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]並[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Analysis Services 資料庫中所述，使用標準程序[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》 的還原[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Analysis Services 資料庫。  
  
## <a name="see-also"></a>另請參閱  
 [備份 BAM 分析和追蹤 Analysis Server 資料庫](../technical-guides/backing-up-the-bam-analysis-and-tracking-analysis-server-databases.md)