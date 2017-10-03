---
title: "資料庫可用性規劃 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6aa74257-4159-46f6-b538-f7e9083d74ad
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea5aa21ad9db78236d7b1e5335053b7c9ce28770
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-database-availability"></a>資料庫可用性規劃
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]傳訊引擎可確保商務程序的可靠性，方法是保存的永久性狀態和商務資料處理至[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]稱為 BizTalk Messagebox 資料庫的資料庫。 規劃高可用性的可靠性和保存資料持續性只會顯示為基礎的資料存放區，因為[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]是很重要的資料庫。  
  
## <a name="hardware-considerations"></a>硬體考量  
 若要確保高可用性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，請考慮下列規劃硬體時：  
  
1.  請考慮實作存放區域網路 (SAN) 來保存[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。 SAN 的磁碟應設定使用 RAID 1 + 0 （等量磁碟區鏡像組） 拓撲盡可能以最大效能和高可用性。 如需有關使用 SAN 來保存[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫看到[BizTalk Server 資料庫最佳化](http://go.microsoft.com/fwlink/?LinkID=101578)白皮書 ([http://go.microsoft.com/fwlink/?LinkID=101578](http://go.microsoft.com/fwlink/?LinkID=101578))。  
  
2.  安裝多部電腦執行計劃[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]來保存[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。 多部電腦執行[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]就會需要[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集 （建議選項） 和/或某些罩[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]個別的實體上的資料庫[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]（也建議使用） 的執行個體。  
  
3.  在上安裝一或多部執行的計劃[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]實作[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]記錄傳送，以利災害復原。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]實作資料庫使用的待命功能[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]記錄傳送。 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]記錄傳送會自動備份和還原的資料庫和交易記錄檔，允許繼續處理的實際執行伺服器失敗，資料庫的待命伺服器。 如需有關實作[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]記錄傳送的災害復原目的，請參閱[什麼是 BizTalk Server 記錄傳送嗎？](../technical-guides/what-is-biztalk-server-log-shipping.md)  
  
## <a name="software-considerations"></a>軟體考量  
 若要確保高可用性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，請考慮下列規劃軟體時： 計劃要安裝的版本和版別[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]支援容錯移轉叢集支援，及/或 BizTalk 記錄傳送支援。 如需完整的版本所支援的功能清單[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]，請參閱[支援的 SQL Server 2008 的版本功能](http://go.microsoft.com/fwlink/?LinkId=151940)([http://go.microsoft.com/fwlink/?LinkId = 151940](http://go.microsoft.com/fwlink/?LinkId=151940)) 中[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]文件。  
  
## <a name="high-availability-vs-disaster-recovery"></a>高可用性與災害復原  
 有兩個不同的方法，來增加可用性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境： 提供容錯和/或負載平衡，或提供可用性使用災害復原使用的高可用性。 由於每個方法會增加可用性，它們之間的主要差異是該容錯和/或負載平衡通常會提供更快速的復原時間比災害復原。 因此，容錯上建置方案或負載平衡會更常被認為是提供高可用性而非只提供可用性。 這兩種方法應該可以用在生產[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。  
  
 提供的高可用性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]配合 Windows Clustering 使用容錯的資料庫。 如需有關提供高可用性的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，請參閱[資料庫的高可用性](../technical-guides/high-availability-for-databases.md)。  
  
 提高可用性與災害復原使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送。 若要增加可用性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]災害復原的資料庫，請依照下列主題中的步驟[檢查清單： 提高可用性與災害復原](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)。