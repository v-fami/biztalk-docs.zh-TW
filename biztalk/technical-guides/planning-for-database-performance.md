---
title: "規劃資料庫效能 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7212fa37-88e0-4b5f-af97-c72063357645
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1338088acc91a45572ae1b49131d99f6c58cb739
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-database-performance"></a>規劃資料庫效能
Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]是極資料庫密集的應用程式，可能需要多達 13 個不同的資料庫中 Microsoft 建立[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]。 由於資料庫大量本質之故[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，為您選擇的適當版本和版別重要[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，將裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。 若要執行的電腦的效能最佳化[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]該馬上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫，請遵循本主題中以及在建議[BizTalk Server 資料庫最佳化](http://go.microsoft.com/fwlink/?LinkID=101578)白皮書 ([http://go.microsoft.com/fwlink/?LinkID=101578](http://go.microsoft.com/fwlink/?LinkID=101578))。  
  
 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]資料庫必須安裝在[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]或[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]。  
  
> [!NOTE]  
>  雖然這份技術白皮書為其他版本的撰寫[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]，您可以使用的相同建議[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]和[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]  /  [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]。  
  
## <a name="considerations-for-sql-server-editions"></a>SQL Server 版本的考量  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫應該設定為在專用 SQL Server 執行個體盡可能上執行。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫大量應用程式，因此，明確劃分[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦和裝載 SQL Server 電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫將可改善效能，並且應該視為最佳作法是在生產環境中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境.  
  
 各版[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]提供不同的功能，這可能會影響效能的程式[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。 例如，在高負載情況下可用的數目資料庫可用於 32 位元版本的鎖定[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]可能超出即不利的 BizTalk 方案的效能。 請考慮罩上的 SQL Server 64 位元版本的 MessageBox 資料庫，如果您在測試環境中發生 「 鎖定不足 」 錯誤。 在 64 位元版本的 SQL Server 上，可用的鎖定數目大幅提高。  
  
 請考慮下的表決定 database engine 功能時，您必須針對您的 BizTalk 環境。 小規模的解決方案，例如，當執行[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]Branch Edition [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]  /  [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] Workgroup Edition 可能已滿足外罩[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。 針對大規模的企業層級方案需要叢集的支援，BizTalk 記錄傳送支援，或 Analysis Services 支援，則需要[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]  /  [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] Enterprise Edition 來保存[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]資料庫。  
  
|SQL Server 的版本|64 位元支援|多重執行個體的支援|叢集支援|Analysis Services|  
|---------------------------------------|---------------------|-----------------------------|------------------------|-----------------------|  
|SQL Server 2008 SP1 / SQL Server 2008 R2 Enterprise Edition|是|是|是|是|  
|[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] / [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]Standard Edition|是|是|是 （節點 2）|是|  
|[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] / [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]Workgroup Edition|是|是|否|否|  
  
> [!NOTE]  
>  BAM RTA 需要[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]  /  [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] Enterprise Edition。  
  
 如需完整的版本所支援的功能清單[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]，請參閱[支援版本的 SQL Server 2008 R2 的功能](http://go.microsoft.com/fwlink/?LinkId=151940)([http://go.microsoft.com/fwlink/?LinkId = 151940](http://go.microsoft.com/fwlink/?LinkId=151940)) 中[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]文件。