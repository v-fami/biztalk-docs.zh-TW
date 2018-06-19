---
title: EDI 和 AS2 效能的已知問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c47294f9-f728-4b6b-abe1-578434eb54df
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e034cf228ee92157c4b29c36660111bb1856c358
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22261758"
---
# <a name="known-issues-with-edi-and-as2-performance"></a>EDI 和 AS2 效能的已知問題
本主題說明 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI 和 AS2 方案在效能方面的已知問題。  
  
## <a name="performance-considerations-for-edi-and-as2-status-reporting"></a>EDI 和 AS2 狀態報告的效能考量  
 當您啟動 EDI 或 AS2 狀態報告時，系統效能可能會受到正在執行狀態報告之訊息的數目所影響。 當您選取 EDI 或 AS2 處理的 [儲存報告的交易集/內容] 屬性時，系統效能可能會受到正在執行狀態報告之訊息的大小所影響。  
  
 EDI 和 AS2 狀態報告之 BAMPrimaryImport 資料庫中使用的資料表已完成最佳化。 您不需要執行任何最佳化。 不過，您可以變更封存 BAMPrimaryImport 資料庫活動執行個體資料的時間間隔，提高封存 BAM 主要匯入資料庫資料的速率。 如需詳細資訊，請參閱 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 文件中的＜封存主要匯入資料庫資料＞。  
  
 交易集/內容資料是儲存在 BizTalkDTADb 資料庫中。 如需此資料庫效能的詳細資訊，請參閱 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 文件中的＜瞭解 DTA 追蹤效能行為＞。  
  
 系統效能也可能會受到系統組態中所啟用之狀態報告的程度所影響。 您可以停用特定類型的狀態報告來提高效能。  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解 EDI 和 AS2 解決方案](../core/troubleshooting-edi-and-as2-solutions.md)