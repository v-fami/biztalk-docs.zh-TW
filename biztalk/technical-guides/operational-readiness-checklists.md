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
ms.openlocfilehash: f9e9297e5539fd95f316ebbf6239a5d017ec4ecf
ms.sourcegitcommit: 6b6d905bbef7796c850178e99ac293578bb58317
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2017
---
# <a name="operational-readiness-checklists"></a>操作的整備檢查清單
操作的整備檢查清單包含您應該考慮的建議和部署 BizTalk 解決方案到實際執行環境之前，您應該執行的工作。 這些檢查清單包括資訊設定必要條件軟體，進而提高可用性，監視[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境，以及用於測試的程序。  
  
 因為[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]上維護相依性，因此許多其他 Microsoft 技術，您應該完成的每個相依的技術，可協助確保您的生產環境工作[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]順暢執行環境。  
  
## <a name="typical-prerequisite-software"></a>一般先決條件軟體  
 先決條件軟體的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式平台通常包括下列產品：  
  
-   Windows 作業系統  
  
-   SQL Server 
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
-   Visual Studio （適用於開發用途，不在執行階段）  
  
## <a name="additional-components"></a>其他元件  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式平台也可能需要數個下列軟體元件：  
  
-   Internet Information Services (IIS)  
  
-   SharePoint
  
-   Microsoft Office Excel 
  
    > [!NOTE]  
    >  BizTalk Server 支援只有 32 位元版本的 Microsoft Office。  
  
-   SQL Server
  
-   SQLXML 
  
-   .NET Framework 
  
-   若要啟用功能特定的非 Microsoft 元件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]配接器。  
  
 如需各種 Windows 作業系統版本的 BizTalk 應用程式平台的特定功能需要的相依性軟體的詳細資訊，請參閱[什麼是新增、 安裝、 設定及升級](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).
- 
  
## <a name="next-steps"></a>後續的步驟
  
-   [檢查清單：開始使用 BizTalk Server](http://msdn.microsoft.com/library/37d265cd-c393-46ac-ac21-129a1511359b)  
  
-   [檢查清單：設定 Windows Server](../technical-guides/checklist-configuring-windows-server.md)  
  
-   [檢查清單：設定 Internet Information Services](../technical-guides/checklist-configuring-internet-information-services.md)  
  
-   [檢查清單：設定 SQL Server](~/technical-guides/checklist-configuring-sql-server.md)  
  
-   [檢查清單：設定 BizTalk Server](../technical-guides/checklist-configuring-biztalk-server.md)  
  
-   [檢查清單：提供高可用性與容錯或負載平衡](../technical-guides/checklist-providing-high-availability-with-fault-tolerance-or-load-balancing.md)  
  
-   [檢查清單：利用災害復原功能提高可用性](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)  
  
-   [檢查清單：監視作業整備](../technical-guides/checklist-monitoring-operational-readiness.md)  
  
-   [檢查清單：維護和疑難排解 BizTalk Server 資料庫](~/technical-guides/checklist-maintaining-and-troubleshooting-biztalk-server-databases.md)  
  
-   [檢查清單：測試作業整備](../technical-guides/checklist-testing-operational-readiness.md)