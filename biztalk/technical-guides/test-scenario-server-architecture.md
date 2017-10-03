---
title: "測試案例伺服器架構 |Microsoft 文件"
ms.custom: 
ms.date: 2015-12-09
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e3afb57-c3ff-4314-9605-cf9fe936e63f
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34a437cdc306a25d8f5e688880c55530ea9703f3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="test-scenario-server-architecture"></a>測試案例伺服器架構
本主題提供在負載測試期間的伺服器和執行負載測試的不同伺服器架構之間的訊息流程的概觀。  
  
## <a name="overview-of-message-flow-during-load-testing"></a>在負載測試期間的訊息流程的概觀  
 下圖提供用於所有的測試案例和負載測試期間的伺服器之間的訊息流程的伺服器架構的一般概觀。  
  
> [!NOTE]  
>  節將說明每個已測試的不同伺服器架構**基準伺服器架構**。  
  
 下圖提供的訊息流程的概觀。 此圖中的數字對應到如下圖所列的步驟。  
  
 ![訊息流程概觀](../technical-guides/media/archmsgflow.gif "ArchMsgFlow")  
訊息流程概觀  
  
1.  負載測試的負載代理程式控制器電腦起始**VSTS_TestController**:  
  
    -   上的 Visual Studio 2008 專案**VSTS_TestController**執行。 專案載入 BizUnit 類別的執行個體，載入指定的 BizUnit XML 組態檔，並開始執行 BizUnit 組態檔中定義的步驟。  
  
        > [!NOTE]  
        >  BizUnit 所使用的 XML 組態檔的詳細資訊，請參閱主題 < 定義測試使用的 XML 組態檔案 」，在[http://go.microsoft.com/fwlink/?LinkId=143432](http://go.microsoft.com/fwlink/?LinkId=143432)。  
  
    -   完成測試的安裝步驟之後，其中一個步驟 BizUnit 專案中執行命令，以顯示對話方塊，提示您啟動 「 忙於活絡"的測試回合來提交忙於活絡訊息至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。  
  
    -   從個別的 Visual Studio 2008 測試專案上提交忙於活絡訊息**VSTS_TestController**。 忙於活絡訊息會傳送 「 準備 」 的測試環境初始化系統快取。  
  
    -   處理所有忙於活絡訊息; 之後BizUnit 執行個體載入效能監視器計數器的所有主要的測試回合中測試的電腦，並執行命令，以顯示對話方塊，提示您將訊息提交以主要測試回合。  
  
    -   在 Visual Studio 2008 負載測試專案**VSTS_TestController**指示要將訊息提交以主要測試回合的負載測試代理程式電腦。  
  
2.  負載測試代理程式電腦送出測試訊息至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]負載測試控制器電腦上 Visual Studio 2008 的負載測試專案的 app.config 檔案中指定的電腦 (**VSTS_TestController**)。  
  
3.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦接收的負載測試代理程式電腦所提交的訊息，為這個負載測試，雙向接收的訊息是要求-回應接收位置。  
  
    -   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]將訊息發佈到 MessageBox 資料庫。  
  
    -   協調流程所使用的訊息。  
  
    -   協調流程繫結至雙向請求-回應傳送埠叫用下游計算機服務。  
  
    > [!NOTE]  
    >  下游計算機服務根據所述的 Windows Communication Foundation 範例[http://go.microsoft.com/fwlink/?LinkId=141762](http://go.microsoft.com/fwlink/?LinkId=141762)。 Windows Communication Foundation 範例可供下載[http://go.microsoft.com/fwlink/?LinkId=87352](http://go.microsoft.com/fwlink/?LinkId=87352)。  
  
4.  計算機服務會使用來自要求[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]並將回應傳回[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]請求-回應傳送埠。  
  
5.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]處理回應，並保存到 MessageBox 資料庫的回應訊息。 從 MessageBox 資料庫由 BizTalk 要求-回應連接埠，然後擷取來自計算機 web 服務的回應訊息和回應訊息傳遞到負載測試代理程式電腦。  
  
## <a name="baseline-server-architecture"></a>基準伺服器架構  
 對於基準的伺服器架構中，未安裝 HYPER-V 角色，兩者均[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]已安裝到主機作業系統。 這是要建立 「 數基準 」 效能度量的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在實體硬體環境中的方案。  
  
 下圖說明實體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]基準伺服器架構層。  
  
 ![實體 BizTalk &#47;實體 SQL](../technical-guides/media/archphysicalbts-physicalsql.gif "ArchPhysicalBTS_PhysicalSQL")  
實體 BizTalk 伺服器 / 實體 SQL Server （基準）  
  
-   **BizTalk Server** -2 BizTalk Server 電腦設定，如下所示：  
  
    -   一個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦**6** GB RAM 和**8**可用的處理器核心。  
  
    -   一個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦**3** GB RAM 和**4**可用的處理器核心。  
  
    -   總計的 6 + 3 = **9**可用 GB RAM 和 8 + 4 = **12**可用的處理器核心[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
-   **SQL Server** -1[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]電腦設定，如下所示：  
  
    -   **8**可用 GB RAM。  
  
    -   **4**可用的處理器核心。  
  
## <a name="virtual-biztalk-server--physical-sql-server"></a>虛擬 BizTalk Server / 實體 SQL Server  
 下圖說明虛擬[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和實體[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]層。  
  
 ![虛擬 BizTalk &#47;實體 SQL](../technical-guides/media/archvirtualbts-physicalsql.gif "ArchVirtualBTS_PhysicalSQL")  
虛擬 BizTalk Server / 實體 SQL Server  
  
 針對此案例中，執行負載測試[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]HYPER-V 虛擬機器上執行和[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]在實體硬體上執行。  
  
> [!NOTE]  
>  如下所述的 RAM 和處理器核心的配置是唯一的差異在於特定電腦在 HYPER-V 虛擬機器上，或實體硬體上執行的每個非基準的案例中，相同。  
  
-   **BizTalk Server** -3[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]的電腦設定，如下所示：  
  
    -   3 GB 的 RAM 配置給每個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦總數 3 x 3 = **9** GB RAM 可供[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
    -   4 顆處理器核心配置給每個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦 3 x 4 總數 = **12**可用的處理器核心[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
-   **SQL Server** -1[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]電腦設定，如下所示：  
  
    -   **8**可用 GB RAM。  
  
    -   **4**可用的處理器核心。  
  
## <a name="virtual-biztalk-server--virtual-sql-server"></a>虛擬 BizTalk Server / 虛擬 SQL Server  
 下圖說明虛擬[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦和虛擬機器[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]不同的 HYPER-V 主機電腦上的電腦。  
  
 ![虛擬 BizTalk &#47;虛擬 SQL](../technical-guides/media/archvirtualbts-virtualsql.gif "ArchVirtualBTS_VirtualSQL")  
虛擬 BizTalk Server / 虛擬 SQL Server  
  
 針對此案例中，執行負載測試[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]HYPER-V 虛擬機器上執行和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]HYPER-V 虛擬機器上執行。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HYPER-V 虛擬機器和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]HYPER-V 虛擬機器在不同的 HYPER-V 主機電腦上執行。  
  
> [!NOTE]  
>  在此案例的 RAM 和處理器核心的配置是等同的 RAM 和處理器核心的配置**虛擬的 BizTalk Server / 實體 SQL Server**情節、 唯一的差異在於，[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]已設定為在 HYPER-V 虛擬機器，而不是實體硬體上執行。  
  
## <a name="consolidated-environment"></a>合併的環境  
 下圖說明虛擬[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦和虛擬機器[!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]電腦整合在一部 HYPER-V 主機電腦上。  
  
 ![虛擬 BizTalk &#47;虛擬 SQL &#47;合併](../technical-guides/media/archvirtualbts-virtualsql-consolidated.gif "ArchVirtualBTS_VirtualSQL_Consolidated")  
合併的環境  
  
 針對此案例中，執行負載測試[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]HYPER-V 虛擬機器上執行和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]HYPER-V 虛擬機器上執行。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HYPER-V 虛擬機器和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]HYPER-V 虛擬機器所執行相同的 HYPER-V 主機電腦上。  
  
> [!NOTE]  
>  在此案例的 RAM 和處理器核心的配置是等同的 RAM 和處理器核心的配置**虛擬的 BizTalk Server / 虛擬 SQL Server**情節、 唯一的差異在於，這兩個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]HYPER-V 虛擬機器和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]HYPER-V 虛擬機器已設定為相同的 HYPER-V 主機電腦上執行。  
  
## <a name="see-also"></a>另請參閱  
 [測試案例概觀](../technical-guides/test-scenario-overview.md)