---
title: "還原 Analysis Services 和支援的資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 490ad0fb-7805-4ebc-9bc5-117d52d7c3a8
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da16bde7b69071b71b794c4c46407feab3ef4512
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="restoring-analysis-services-and-supporting-databases"></a>還原 Analysis Services 和支援的資料庫
有兩個[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Analysis Services 資料庫必須還原在嚴重損壞修復案例：  
  
-   BAM 分析 (BAMAnalysis)  
  
-   追蹤 Analysis Server (BizTalkAnalysisdb)  
  
 BAM[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫可能會備份為 「 備份 BizTalk Server 」 工作一部分如果 BAM 已啟用但尚未設定。  
  
> [!NOTE]  
>  BAM 主要匯入永遠備份資料庫的 「 備份 BizTalk Server 」 工作一部分因為參與 DTC 交易。  
  
 下列 BAM 資料庫將會是 「 備份 BizTalk Server 」 工作的一部分，如果 BAM 已啟用但尚未設定：  
  
-   BAMStarSchema  
  
-   BAMArchive  
  
 請依照[如何還原資料庫中 「 備份 BizTalk Server 」 工作](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md)来還原這些資料庫。  
  
 **否則，**  
 **如果 BAM 已啟用，也會搭配 BM.exe 設定一組正確的 BAM 資料庫必須先為一組一起還原。** 若要確定會復原一組完整的封存資料，BAM 封存資料庫被備份資料分割會複製到 BAM 封存後，但從 BAM 主要匯入資料庫刪除資料分割。 這是由所插入的最後一個步驟 「 結束封存 」 之前，備份 BAM 封存資料庫的步驟，藉以修改每個活動的資料維護 SSIS 封裝執行  
  
 BAM 資料庫的還原程序： 如果 x 的最後備份日期還原 BAM 主要匯入資料庫，還原 BAM 封存和 BAM 星狀結構描述資料庫對應的複本至最新的資料維護 SSIS 封裝時的日期x 的日期之前執行。  
  
 識別一組正確的 BAM 資料庫之後，還原[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Analysis Services 資料庫中所述，使用標準程序[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]線上叢書 》 還原[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Analysis Services 資料庫。  
  
## <a name="see-also"></a>另請參閱  
 [備份 BAM 分析和追蹤 Analysis Server 資料庫](../technical-guides/backing-up-the-bam-analysis-and-tracking-analysis-server-databases.md)