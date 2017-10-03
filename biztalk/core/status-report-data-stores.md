---
title: "狀態報告資料存放區 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6cd40ce8-1ac6-43b4-9cef-7cd045e8893c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da876f1151b641216cf9613f6830ed84049da83d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="status-report-data-stores"></a>狀態報告資料存放區
狀態報告追蹤資料會儲存在 BAM 主要匯入資料庫中。 這個資料庫中的許多資料表會用於 EDI 和 AS2 訊息資料，包括開頭為 dbo.bam_AS2、dbo.bam.batching、dbo.bam.InterchangeStatusActivity 和其他開頭的資料表。 即使 EDI 報告功能已停用，狀態資料仍會儲存在主要匯入資料庫中。 若已啟動狀態報告，您就只能使用狀態報告 UI 來檢視和查詢這項資料。  
  
 如果您為了符合不可否認性而啟用訊息資料儲存區，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會將 EDI 和/或 AS2 資料儲存於 BizTalk 追蹤資料庫 (BizTalkDTADb) 的 EDI Message Content 資料表中。 如果您啟用訊息內容來檢視詳細資料裝載的儲存 (藉由選取**儲存報告的訊息內容**協議屬性中的**一般屬性**頁面**一般**索引標籤中**協議屬性**對話方塊)，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]也會儲存在此資料表中的交易集。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會封存和清除 BAM 主要匯入資料庫和 BizTalkDTADb 資料庫中的資料。 這些資料庫中的資料表會定期清除。  
  
> [!NOTE]
>  如果 BAM 主要匯入資料庫和 DTA DB 資料庫使用不同的封存間隔，這兩個資料庫可能就不會同步。  
  
 EDI 和 AS2 狀態報告功能可能會影響效能。 如需詳細資訊，請參閱 [效能考量的 EDI 和 AS2 狀態報告][已知問題與 EDI 和 AS2 效能](../core/known-issues-with-edi-and-as2-performance.md)。  
  
## <a name="see-also"></a>另請參閱  
 [資料如何儲存 EDI 和 AS2 狀態報告](../core/how-data-is-stored-for-edi-and-as2-status-reports.md)