---
title: 監視和減少資料庫 I/O 競爭 |Microsoft Docs
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
ms.openlocfilehash: e4a58b0733f44ca2d85c96a9b4a91045bb3947be
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001097"
---
# <a name="monitoring-and-reducing-database-io-contention"></a>監視和減少資料庫 I/O 競爭
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 效能通常預測時有[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]依次通常預測有磁碟 I/O 效能時的效能。 因此，您應該監視和效能調整執行的電腦上的磁碟 I/O[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。  
  
## <a name="monitoring-disk-io"></a>監視磁碟 I/O  
 由於這樣的資料庫需要大量[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]、 磁碟 I/O 很容易變得 MessageBox 的瓶頸和 BizTalk 追蹤資料庫; 這是 true 即使磁碟 I/O 先前已有資料庫檔案中的瓶頸您[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]環境。 因此，我們建議您主動測量存放的資料和交易記錄檔之磁碟的磁碟 I/O 效能。 如需有關如何監視磁碟 I/O 效能，使用 「 系統監視器的詳細資訊，請參閱 <<c0> [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 一文[「 前置部署 I/O 最佳作法 」](http://go.microsoft.com/fwlink/?LinkId=104829) (<http://go.microsoft.com/fwlink/?LinkId=104829>)。 如果您使用 SAN，您可能也需要從 SAN 硬體製造商，以測量磁碟 I/O 效能的特定工具。  
  
## <a name="separating-the-messagebox-and-biztalk-tracking-dta-databases-and-log-files"></a>用來分隔 MessageBox 和 BizTalk 追蹤 (DTA) 資料庫和記錄檔  
 由於 MessageBox 和 「 BizTalk 追蹤資料庫是最常使用，我們建議針對每一種可降低磁碟 I/O 競爭問題的可能性的專用磁碟機上放置資料檔和交易記錄檔。 例如，您需要四個磁碟機的 MessageBox 和 「 BizTalk 追蹤資料庫檔案中;一個磁碟機，如下列各項：  
  
- MessageBox 資料檔案  
  
- MessageBox 交易記錄檔  
  
- BizTalk 追蹤資料檔案  
  
- BizTalk 追蹤 」 的交易記錄檔  
  
  分隔 MessageBox 和 「 BizTalk 追蹤資料庫，並將資料庫檔案和交易記錄檔，在不同的實體磁碟上會被視為減少磁碟 I/O 競爭的最佳作法。 請試著盡可能分散多個實體磁針的磁碟 I/O。 如需有關如何避免磁碟爭用情況的詳細資訊，請參閱 <<c0> [ 如何避免磁碟爭用](http://go.microsoft.com/fwlink/?LinkId=158809)(<http://go.microsoft.com/fwlink/?LinkId=158809>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能最佳化指南。  
  
  您應該在設定之後，手動個別檔案[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 如需詳細資訊，請參閱 < [BizTalk Server 資料庫最佳化白皮書](http://go.microsoft.com/fwlink/?LinkId=101578)(<http://go.microsoft.com/fwlink/?LinkId=101578>)。  
  
## <a name="see-also"></a>另請參閱  
 [使用記錄檔效能分析 (PAL) 工具](../technical-guides/using-the-performance-analysis-of-logs-pal-tool.md)