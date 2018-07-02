---
title: 移動資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6a0d09a1-90a5-4a5d-a783-b979724e101b
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15562fc1fb642a4766190dabe912e81b38bb1ea8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972415"
---
# <a name="moving-databases"></a>移動資料庫
建議的方法，移動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]（除了商務活動監控 (BAM) 資料庫中） 的資料庫是設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]一節中所述，記錄傳送[嚴重損壞修復](../technical-guides/disaster-recovery.md)。 使用 BAM，所有的資料庫除外[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以備份資料庫使用**備份 BizTalk Server** [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]代理程式作業。 如需有關這項作業的詳細資訊，請參閱 <<c0> [ 如何排程 「 備份 BizTalk Server 」 工作](http://go.microsoft.com/fwlink/?LinkId=154674)(<http://go.microsoft.com/fwlink/?LinkId=154674>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
 本章節描述如何移動 BAM 相關的資料庫以及如何移動其餘[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，而不先設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送。 升級時，這種方法可能會很有用[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫或在其他情況下，不會與災害復原。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [移動 BAM 資料庫](../technical-guides/moving-bam-databases.md)  
  
-   [移動非 BAM 資料庫](../technical-guides/moving-non-bam-databases.md)  
  
## <a name="see-also"></a>另請參閱  
 [管理 BizTalk Server2](../technical-guides/managing-biztalk-server2.md)