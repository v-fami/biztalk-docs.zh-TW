---
title: "操作的整備檢查清單 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c308a876-9872-43b3-a1fb-76e81396612f
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87da295129a4cb90ecf643cd06eb18ac3e6aa18e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="operational-readiness-checklists"></a>操作的整備檢查清單
操作的整備檢查清單包含您應該考慮的建議和部署 BizTalk 解決方案到實際執行環境之前，您應該執行的工作。 這些檢查清單包括資訊設定必要條件軟體，進而提高可用性，監視[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境，以及用於測試的程序。  
  
 因為[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]上維護相依性，因此許多其他 Microsoft 技術，您應該完成的每個相依的技術，可協助確保您的生產環境工作[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]順暢執行環境。  
  
## <a name="typical-prerequisite-software"></a>一般先決條件軟體  
 先決條件軟體的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式平台通常包括下列產品：  
  
-   Windows 作業系統  
  
-   [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]SP1 或[!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
-   [!INCLUDE[vs2010](../includes/vs2010-md.md)]（適用於開發用途，不在執行階段）  
  
## <a name="additional-components"></a>其他元件  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式平台也可能需要數個下列軟體元件：  
  
-   Internet Information Services (IIS)  
  
-   Windows SharePoint® Services 2010  
  
-   SharePoint Foundation 2010  
  
-   Microsoft Office SharePoint Server 2007 Service Pack 1 (SP1) (MOSS)  
  
-   SP1 或 SP2 的 Windows SharePoint Services 3.0  
  
-   Microsoft Office Excel 2010 或 2007  
  
    > [!NOTE]  
    >  [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]支援僅 32 位元版本的 Microsoft Office 2010。  
  
-   SQL Server 2005 Notification Services  
  
-   SQLXML 4.0 搭配 Service Pack 1  
  
-   .NET framework 1.0  
  
-   .NET Framework 2.0  
  
-   .NET framework 3.0  
  
-   Microsoft.NET Framework 4 和.Net Framework 3.5 Service pack 1 (SP1)  
  
-   若要啟用功能特定的非 Microsoft 元件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]配接器。  
  
 如需各種 Windows 作業系統版本的 BizTalk 應用程式平台的特定功能需要的相依性軟體的詳細資訊，請參閱中的 「 功能相依性矩陣 」 一節[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]安裝和升級為特定的 Windows 作業系統版本的指南。 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]安裝與升級指南位於[http://go.microsoft.com/fwlink/?LinkID=152913](http://go.microsoft.com/fwlink/?LinkID=152913)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [檢查清單： 開始使用 BizTalk Server](http://msdn.microsoft.com/library/37d265cd-c393-46ac-ac21-129a1511359b)  
  
-   [檢查清單： 設定 Windows Server](../technical-guides/checklist-configuring-windows-server.md)  
  
-   [檢查清單： 設定 Internet Information Services](../technical-guides/checklist-configuring-internet-information-services.md)  
  
-   [檢查清單： 設定 SQL Server](~/technical-guides/checklist-configuring-sql-server.md)  
  
-   [檢查清單： 設定 BizTalk Server](../technical-guides/checklist-configuring-biztalk-server.md)  
  
-   [檢查清單： 提供高可用性與容錯或負載平衡](../technical-guides/checklist-providing-high-availability-with-fault-tolerance-or-load-balancing.md)  
  
-   [檢查清單： 提高可用性與災害復原](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)  
  
-   [檢查清單： 監視操作整備](../technical-guides/checklist-monitoring-operational-readiness.md)  
  
-   [檢查清單： 維護和疑難排解 BizTalk Server 資料庫](~/technical-guides/checklist-maintaining-and-troubleshooting-biztalk-server-databases.md)  
  
-   [檢查清單： 測試操作整備](../technical-guides/checklist-testing-operational-readiness.md)