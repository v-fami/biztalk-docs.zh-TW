---
title: SQL Server 資料庫鏡像磁碟區陰影複製服務和 AlwaysOn |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b965cafc-cd34-4657-975d-0dedffd27333
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bea9d6063330e7af15ecb202513deb4def6571fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277990"
---
# <a name="sql-server-database-mirroring-volume-shadow-copy-service-and-alwayson"></a>SQL Server 資料庫鏡像磁碟區陰影複製服務和 AlwaysOn
Microsoft 提供軟體解決方案，稱為 SQL Server*資料庫鏡像*和 Windows 磁碟區陰影複製服務 (VSS) 來增加特定案例的高可用性。 SQL Server*資料庫鏡像*增加資料庫的可用磁碟區陰影複製服務 (VSS) 提供災害復原的備份和還原功能的機率。 使用 SQL Server*資料庫鏡像*或 Windows 磁碟區陰影複製服務不支援的解決方案，可確保高可用性的 Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。  
  
## <a name="using-sql-server-database-mirroring-to-provide-high-availability-for-biztalk-server-databases"></a>使用 BizTalk Server 資料庫提供高可用性 SQL Server 資料庫鏡像  
 使用 SQL Server*資料庫鏡像*目前不支援的解決方案，可確保高可用性的 Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]因為維護交易一致性的潛在問題的資料庫BizTalk Server 資料庫。 如需有關資料庫鏡像和 SQL Server 中的跨資料庫交易，請參閱[http://go.microsoft.com/fwlink/?LinkId=87977](http://go.microsoft.com/fwlink/?LinkId=87977)。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫應該安裝在 SQL Server 叢集，以確保高可用性和 BizTalk 記錄傳送應該利用災害復原用途。 如需 BizTalk 記錄傳送的詳細資訊，請參閱[記錄傳送](../core/log-shipping.md)。  
  
## <a name="using-the-volume-shadow-copy-service-to-provide-high-availability-for-biztalk-server-databases"></a>使用磁碟區陰影複製服務來為 BizTalk Server 資料庫提供高可用性  
 「磁碟區陰影複製服務」提供進行災害復原所需的備份與還原功能。 Microsoft 分散式交易協調器 (MS DTC) 支援 VSS 的因此很有限，本機部署和交易的協調案例 （也受限於其他限制）、 使用 VSS 服務目前不支援的方案確保高可用性的 Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。 如需磁碟區陰影複製服務支援分散式交易的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=139505](http://go.microsoft.com/fwlink/?LinkId=139505)。  
  
## <a name="using-sql-server-alwayson"></a>使用 SQL Server AlwaysOn 
 當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 安裝在不同的電腦時，分散式交易協調器 (MS DTC) 會處理電腦間的交易。 
 
從 SQL Server 2016 開始，AlwaysOn 支援 MSDTC 交易。 如此一來，[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]時使用此 SQL Server 版本支援 AlwaysOn 功能。 與舊版 SQL Server， [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] AlwaysOn 功能不支援 MSDTC 交易，因此不支援 AlwaysOn。 

請參閱[使用 SQL Server Alwayson 可用性群組的高可用性](../core/high-availability-using-sql-server-always-on-availability-groups.md)。
  
## <a name="see-also"></a>另請參閱  
 [叢集 BizTalk Server 資料庫](../core/clustering-the-biztalk-server-databases1.md)   
 [備份和還原的相關進階的資訊](../core/advanced-information-about-backup-and-restore1.md)