---
title: 備份資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0524a8f0-15a3-4731-a7bd-c0c935fff6c8
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b3d3e488c1bae99e343f5ff6d5a15b826138459
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980063"
---
# <a name="backing-up-databases"></a>備份資料庫
因為[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用分散式交易跨越多個資料庫，則 「 備份 BizTalk Server 」 工作會建立所有的同步的備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。 這是透過標示的交易具有 「 完整 」 的資料庫復原模式來完成。 這是必要的跨資料庫處於交易一致狀態的備份。 如需詳細資訊，請參閱 < ["標示的交易、 完整備份和記錄備份 」](http://go.microsoft.com/fwlink/?LinkId=151565) (<http://go.microsoft.com/fwlink/?LinkId=151565>) 中的 BizTalk Server 文件。  
  
## <a name="advantages-of-the-backup-biztalk-server-job"></a>「 備份 BizTalk Server 」 工作的優點  
 「 備份 BizTalk Server 」 工作是唯一支援的方法，來備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。 利用[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]工作來備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]不支援在生產環境中的資料庫。  
  
 如果備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]不會執行作業，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫交易記錄檔將會無限制的成長。 備份作業會截斷交易記錄檔，這讓它們繼續無限制成長。 如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫交易記錄檔繼續成長，他們可以在某個時間點填滿它們裝載於該磁碟。  
  
> [!NOTE]
>  使用這兩個備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業和記錄傳送是目前唯一完整記錄和支援方法來執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]database 備份和還原。  
  
## <a name="guidelines-for-the-backup-biztalk-server-job"></a>「 備份 BizTalk Server 」 工作的指導方針  
 您應該還原整個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]定期執行的環境。 這包括不只是 SQL server 和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，但是也執行的電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 您應該記錄並實際發生故障前，練習這些程序。  
  
> [!NOTE]
>  備份[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業不會刪除舊的備份檔案。 您必須定義，並將程序放在封存舊的備份檔案，並將其從該備份作業使用的備份目錄移至的位置。  
  
## <a name="additional-resources"></a>其他資源  
 請參閱下列主題中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]文件：  
  
- 如需有關特定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]備份和還原工作，請參閱[「 檢查清單:: 備份和還原"](http://go.microsoft.com/fwlink/?LinkId=154070) (<http://go.microsoft.com/fwlink/?LinkId=154070>)。  
  
- 如需備份和還原的概觀[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱 < ["備份和還原 BizTalk Server 」](http://go.microsoft.com/fwlink/?LinkId=154071) (<http://go.microsoft.com/fwlink/?LinkId=154071>)。  
  
- 如需有關設定 「 備份 BizTalk Server 」 工作的詳細資訊，請參閱 < [」 方式來設定備份 BizTalk Server 作業 」](http://go.microsoft.com/fwlink/?LinkId=154072) (http://go.microsoft.com/fwlink/?LinkId=154072)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk Server 記錄傳送進行災害復原](../technical-guides/using-biztalk-server-log-shipping-for-disaster-recovery.md)