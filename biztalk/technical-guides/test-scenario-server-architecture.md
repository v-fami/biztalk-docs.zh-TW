---
title: 測試案例伺服器架構 |Microsoft Docs
ms.custom: ''
ms.date: 2015-12-09
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1e3afb57-c3ff-4314-9605-cf9fe936e63f
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 369286ea2c5c42a53a8e22a7e0b03ac5701db0d5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981263"
---
# <a name="test-scenario-server-architecture"></a>測試案例伺服器架構
本主題提供在負載測試期間的伺服器和執行負載測試在不同的伺服器架構之間的訊息流程概觀。  
  
## <a name="overview-of-message-flow-during-load-testing"></a>在負載測試期間的訊息流程概觀  
 下圖提供用於所有的測試案例和負載測試期間的伺服器之間的訊息流程的伺服器架構的一般概觀。  
  
> [!NOTE]  
>  已進行過測試每個不同的伺服器架構一節所述**基準伺服器架構**。  
  
 下圖提供的訊息流程的概觀。 此圖中的數字會對應至圖如下所列的步驟。  
  
 ![訊息流程概觀](../technical-guides/media/archmsgflow.gif "ArchMsgFlow")  
訊息流程概觀  
  
1. 負載測試的負載代理程式的控制器電腦起始**VSTS_TestController**:  
  
   - 上的 Visual Studio 2008 專案**VSTS_TestController**執行。 專案載入 BizUnit 類別的執行個體，載入指定的 BizUnit XML 組態檔，並開始執行 BizUnit 組態檔中定義的步驟。  
  
     > [!NOTE]  
     >  BizUnit 所使用的 XML 組態檔的詳細資訊，請參閱 「 定義測試使用 XML 組態檔 」 的主題，網址[ http://go.microsoft.com/fwlink/?LinkId=143432 ](http://go.microsoft.com/fwlink/?LinkId=143432)。  
  
   - 完成測試的設定步驟之後，其中一個 BizUnit 專案中的步驟執行命令，以顯示對話方塊，它會提示您啟動 「 忙於活絡"的測試回合來提交忙於活絡訊息至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。  
  
   - 從個別的 Visual Studio 2008 測試專案上提交忙於活絡訊息**VSTS_TestController**。 忙於活絡訊息會傳送 「 暖 」 測試環境初始化系統快取。  
  
   - 處理完所有忙於活絡訊息; 之後BizUnit 執行個體載入效能監視器計數器中主要的測試回合正在測試的所有電腦，並執行命令，以顯示對話方塊，它會提示您將訊息提交以主要的測試回合。  
  
   - 在 Visual Studio 2008 的負載測試專案**VSTS_TestController**指示來提交訊息之主要的測試回合的負載測試代理程式電腦。  
  
2. 負載測試代理程式電腦提交測試訊息至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]負載測試控制器電腦上 Visual Studio 2008 的負載測試專案的 app.config 檔案中指定的電腦 (**VSTS_TestController**)。  
  
3. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦接收的負載測試代理程式電腦所提交的訊息，這兩種方式接收訊息的負載測試要求-回應接收位置。  
  
   - [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將訊息發佈到 MessageBox 資料庫。  
  
   - 協調流程所取用的訊息。  
  
   - 協調流程繫結至雙向請求-回應傳送埠會叫用下游計算機服務。  
  
   > [!NOTE]  
   >  下游計算機服務為基礎所述的 Windows Communication Foundation 範例[ http://go.microsoft.com/fwlink/?LinkId=141762 ](http://go.microsoft.com/fwlink/?LinkId=141762)。 Windows Communication Foundation 範例可供下載： [ http://go.microsoft.com/fwlink/?LinkId=87352 ](http://go.microsoft.com/fwlink/?LinkId=87352)。  
  
4. 計算機服務將取用的要求[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]並將回應傳回給[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]請求-回應傳送埠。  
  
5. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 處理回應，並保存到 MessageBox 資料庫的回應訊息。 從 MessageBox 資料庫由 BizTalk 的要求-回應連接埠，然後擷取來自計算機 web 服務的回應訊息和回應訊息會傳遞回負載測試代理程式電腦。  
  
## <a name="baseline-server-architecture"></a>基準伺服器架構  
 針對基準伺服器架構中，未安裝 HYPER-V 角色，同時兩者皆[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和 SQL Server 安裝到主機作業系統。 這是要建立的 「 基準 」 效能度量[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在實體硬體環境的解決方案。  
  
 下圖將說明實體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和基準伺服器架構的 SQL Server 層。  
  
 ![實體 BizTalk&#47;實體的 SQL](../technical-guides/media/archphysicalbts-physicalsql.gif "ArchPhysicalBTS_PhysicalSQL")  
實體 BizTalk 伺服器 / 實體 SQL Server （基準）  
  
- **BizTalk Server** -2 個 BizTalk Server 電腦設定，如下所示：  
  
  - 一[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦**6** GB 的 RAM 並**8**可用的處理器核心。  
  
  - 一[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦**3** GB 的 RAM 並**4**可用的處理器核心。  
  
  - 總共 6 + 3 = **9**可用 GB RAM 和 8 + 4 = **12**處理器核心可供[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
- **SQL Server** -1 的 SQL Server 電腦設定，如下所示：  
  
  -   **8**可用 GB RAM。  
  
  -   **4**可用的處理器核心。  
  
## <a name="virtual-biztalk-server--physical-sql-server"></a>虛擬 BizTalk 伺服器 / 實體 SQL Server  
 下圖說明虛擬[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和實體[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]層。  
  
 ![虛擬 BizTalk&#47;實體的 SQL](../technical-guides/media/archvirtualbts-physicalsql.gif "ArchVirtualBTS_PhysicalSQL")  
虛擬 BizTalk 伺服器 / 實體 SQL Server  
  
 針對此案例中，執行負載測試[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]HYPER-V 虛擬機器和實體硬體上執行的 SQL Server 上執行。  
  
> [!NOTE]  
>  如下所述的 RAM 以及處理器核心的配置是唯一的差別在於特定電腦是否正在執行的 HYPER-V 虛擬機器上或在實體硬體上每個非基準的情況下，完全相同。  
  
- **BizTalk Server** -3[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]的電腦設定，如下所示：  
  
  - 3 GB 的 RAM 配置給每個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]共有 3 x 3 個電腦 = **9** GB 的 RAM 供[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
  - 4 顆處理器核心配置給每個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]共有 3 x 4 個電腦 = **12**處理器核心可供[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
- **SQL Server** -1 的 SQL Server 電腦設定，如下所示：  
  
  -   **8**可用 GB RAM。  
  
  -   **4**可用的處理器核心。  
  
## <a name="virtual-biztalk-server--virtual-sql-server"></a>虛擬 BizTalk 伺服器 / 虛擬 SQL Server  
 下圖說明虛擬[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦和虛擬的 SQL Server 電腦上不同的 HYPER-V 主機電腦。  
  
 ![虛擬 BizTalk&#47;虛擬 SQL](../technical-guides/media/archvirtualbts-virtualsql.gif "ArchVirtualBTS_VirtualSQL")  
虛擬 BizTalk 伺服器 / 虛擬 SQL Server  
  
 針對此案例中，執行負載測試[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]HYPER-V 虛擬機器上執行和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]HYPER-V 虛擬機器上執行。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HYPER-V 虛擬機器和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]不同的 HYPER-V 主機電腦上執行 HYPER-V 虛擬機器。  
  
> [!NOTE]
>  此案例中的 RAM 和處理器核心的配置等同於配置的 RAM 和處理器核心**虛擬的 BizTalk Server / 實體 SQL Server**案例，唯一的差別在於，[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]已設定為在 HYPER-V 虛擬機器，而不是實體硬體上執行。  
  
## <a name="consolidated-environment"></a>合併的環境  
 下圖說明虛擬[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦和虛擬的 SQL Server 電腦彙總一部 HYPER-V 主機電腦上。  
  
 ![虛擬 BizTalk&#47;虛擬 SQL&#47;合併](../technical-guides/media/archvirtualbts-virtualsql-consolidated.gif "ArchVirtualBTS_VirtualSQL_Consolidated")  
合併的環境  
  
 針對此案例中，執行負載測試[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]HYPER-V 虛擬機器上執行和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]HYPER-V 虛擬機器上執行。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HYPER-V 虛擬機器和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]HYPER-V 虛擬機器所執行相同的 HYPER-V 主機電腦上。  
  
> [!NOTE]
>  在此案例的 RAM 以及處理器核心的配置等同於配置的 RAM 和處理器核心**虛擬的 BizTalk Server / 虛擬 SQL Server**案例，唯一的差別在於，這兩個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]HYPER-V 虛擬機器和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]HYPER-V 虛擬機器已設定為相同的 HYPER-V 主機電腦上執行。  
  
## <a name="see-also"></a>另請參閱  
 [測試案例概觀](../technical-guides/test-scenario-overview.md)