---
title: "檢視的記錄備份還原 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- restoring, history
- backing up, history
ms.assetid: 8852befa-b8e7-469d-b014-75c881907442
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa5a7fbe2b0e731920880570b0555402ba162c7a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="viewing-the-history-of-restored-backups"></a>檢視所還原備份的歷程記錄
若要判斷上一個已還原的成功備份集，請檢視 Master.dbo.bts_LogShippingHistory 資料表的內容。 這個資料表是由「取得備份歷程記錄」工作填入，並且由「還原資料庫」工作更新。 成功還原備份時，會將 [已還原] 欄設定為 1，並將 RestoredDateTime 設定為目前的日期和時間。  
  
 成功還原所有由特定備份集還原到伺服器的資料庫之後，該備份集識別碼會寫入 Master.dbo.bts_LogShippingLastRestoreSet 資料表。  
  
## <a name="gaps-in-the-restore-process"></a>還原程序中的間斷  
 檢視 Master.dbo.bts_LogShippingHistory 資料表中的記錄時，您可能會在還原的備份集中發現一些間斷。 這可能有數種原因。 不過，即使在發生間斷時，您仍然可以回復目的地系統 (即備份電腦) 的穩定性。 間斷之後必須緊接著還原完整備份集，才能修復目的地系統。 如果間斷之後沒有接著還原完整備份集，則目的地環境就會不穩定。  
  
> [!NOTE]
>  還原完整備份的目的只是要初步建立資料庫，並修復記錄檔歷程記錄備份鏈結中的問題。 不過，多數情況下均無法還原完整備份集，因為這些備份集並非記錄備份鏈結中的一部分。  
  
## <a name="see-also"></a>另請參閱  
 [備份和還原的相關進階的資訊](../core/advanced-information-about-backup-and-restore1.md)