---
title: 監視與降低資料庫的 I/O 競爭 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bd6d3343-3fa3-469a-9772-e94f22fdf558
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 446a4b512b4f38869637cb3968305fad1e869dae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22298774"
---
# <a name="monitoring-and-reducing-database-io-contention"></a>監視和減少資料庫 I/O 競爭
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能通常取決於[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]依次通常預測有磁碟 I/O 效能時的效能。 因此，您應該監視和效能調整執行的電腦上的磁碟 I/O[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]該馬上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。  
  
## <a name="monitoring-disk-io"></a>監視磁碟 I/O  
 由於大量資料庫的本質之故[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]、 磁碟 I/O 會變成 messagebox 是效能瓶頸和 BizTalk 追蹤資料庫; 這是 true 即使磁碟 I/O 先前尚未中的資料庫檔案是效能瓶頸您[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]環境。 因此，我們建議您主動測量存放的資料和交易記錄檔磁碟的磁碟 I/O 效能。 如需有關如何監視磁碟 I/O 效能，使用 「 系統監視器的詳細資訊，請參閱[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]文章[「 前置部署 I/O 最佳作法 」](http://go.microsoft.com/fwlink/?LinkId=104829) (http://go.microsoft.com/fwlink/?LinkId=104829)。 如果您使用 SAN，您可能也需要 SAN 硬體製造商，來測量磁碟 I/O 效能的特定工具。  
  
## <a name="separating-the-messagebox-and-biztalk-tracking-dta-databases-and-log-files"></a>分隔 MessageBox 和 BizTalk 追蹤 (DTA) 資料庫和記錄檔  
 由於 MessageBox 和 「 BizTalk 追蹤資料庫是最常使用，我們建議您針對每一種可降低發生問題的磁碟 I/O 競爭的可能性的專用磁碟機上放置資料檔和交易記錄檔。 例如，您需要四個磁碟機 MessageBox 和 「 BizTalk 追蹤資料庫檔案。一個磁碟機，如下列各項：  
  
-   MessageBox 資料檔案  
  
-   MessageBox 交易記錄檔  
  
-   BizTalk 追蹤資料檔案  
  
-   BizTalk 追蹤交易記錄檔  
  
 區隔 MessageBox 和 「 BizTalk 追蹤資料庫，以及將資料庫檔案和交易記錄檔不同實體磁碟上的會被視為降低磁碟 I/O 競爭的最佳作法。 請試著儘可能將磁碟 I/O 分散數量的實體磁針。 如需有關如何避免磁碟爭用情況的詳細資訊，請參閱[如何避免磁碟爭用](http://go.microsoft.com/fwlink/?LinkId=158809)(http://go.microsoft.com/fwlink/?LinkId=158809) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能最佳化指南。  
  
 您應該設定之後，手動將檔案[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱[BizTalk Server 資料庫最佳化白皮書](http://go.microsoft.com/fwlink/?LinkId=101578)(http://go.microsoft.com/fwlink/?LinkId=101578)。  
  
## <a name="see-also"></a>另請參閱  
 [使用記錄檔 (PAL) 工具的效能的分析](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md)