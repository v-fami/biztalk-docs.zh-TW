---
title: "規劃開發、 測試、 預備及生產環境 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c83a42d-117f-4a24-a669-b3e4e1c9a056
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5572ab96215d07570a39f53009eae3038792db8
ms.sourcegitcommit: 6b6d905bbef7796c850178e99ac293578bb58317
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2017
---
# <a name="planning-the-development-testing-staging-and-production-environments"></a>規劃開發、 測試、 預備及實際執行環境
本主題討論用於 BizTalk 解決方案的發行管理程序的環境。 如同任何企業軟體解決方案，您應該遵循已建立的軟體版本管理的指導方針，當您開發並發行 BizTalk 解決方案。 此程序應該包括下列相異的階段：  
  
-   部署  
  
-   測試  
  
-   臨時區域  
  
-   Production  
  
 在理想情況下，您應該先完成每個階段中發行管理程序，在獨立環境中，不同於其他環境。 實際上，您可能要結合以上一或多個環境中，由於硬體、 時間或其他資源條件約束。 至少，您應該將來自其他環境的實際執行環境。  
  
> [!NOTE]  
>  BizTalk Server 的最新安裝和升級指示會列在[BizTalk Server 功能的新增、 安裝、 設定及升級](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md)。 
>  
##  <a name="BKMK_VirtualServ"></a>發行管理程序期間使用虛擬伺服器  
 請考慮完成開發、 單元測試和 「 虛擬 」 環境中執行。 執行的開發工作，單元測試和預備環境，在虛擬環境中的提供很大的彈性，並使用遠少於硬體資源，否則需要比。 如果使用虛擬環境時，配置至少 512 MB 的記憶體，每個虛擬機器主機電腦和額外的 512 MB 的記憶體供主機作業系統上執行。  
  
 例如，對於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用五個虛擬機器的環境 (兩部執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]、 兩個 Microsoft[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集節點，有一個網域控制站)，您應該規劃將 3 GB 的主機電腦上安裝的記憶體。 如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境需要超過 2 GB 的記憶體，請考慮在主機電腦，以確保已安裝記憶體的最大數量是可存取主機作業系統上安裝 64 位元版本的 Windows。  
  
> [!NOTE]  
>  如需有關使用建議[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在虛擬環境中，請參閱[BizTalk Server 2009 HYPER-V 指南](http://go.microsoft.com/fwlink/?LinkId=151834)(http://go.microsoft.com/fwlink/?LinkId=151834)。  
  
> [!NOTE]  
>  [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]執行於任何 Microsoft 知識庫文章 842301 中所列的虛擬化軟體支援的作業系統上完全支援[虛擬機器上的 Microsoft BizTalk Server 可支援性](https://support.microsoft.com/kb/842301)。 不過，[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]可能無法如預期般如果安裝在執行中虛擬化軟體不屬於此知識庫文件中所述的支援作業系統上執行。  
  
## <a name="development-environment"></a>開發環境  
 在開發環境中建立 BizTalk 專案所使用的 BizTalk 方案。 您應該使用的電腦上安裝下列軟體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]開發環境：  
  
-   Internet Information Services (IIS)  
  
-   Visual Studio  
  
-   SQL Server 用戶端工具  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]（包括下列元件）  
  
    -   文件集  
  
    -   系統管理工具  
  
    -   開發者工具與 SDK  
  
    -   其他軟體  
  
-   [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫要在開發期間裝載在本機。  
  
-   通常開發人員也應該有自己的開發電腦上 （實體或虛擬），和安裝的必要軟體。  
  
> [!NOTE]  
>  我們建議您購買和非實際執行環境中使用 Visual Studio 訂用帳戶。 Visual Studio 訂閱會從相同的軟體的零售授權的成本提供折扣。 請參閱[Visual Studio 訂閱](https://visualstudio.com/subscriptions)。  
  
## <a name="testing-environment"></a>測試環境  
 單元測試可以在虛擬環境中完成。 您應該不過，會執行您的實體環境使用的硬體和軟體，等同於生產環境中測試的效能。  
  
 測試環境可用來測量效能特性，例如最大持續輸送量 (MST) 和 BizTalk 解決方案的最大持續性追蹤輸送量。 它應該儘可能密集地因此比對實體的實際執行環境。 如需有關測量效能特性的 BizTalk 解決方案查看[引擎效能特性](../core/engine-performance-characteristics.md)，或[BizTalk Server 效能最佳化指南](../technical-guides/biztalk-server-2010-performance-optimization-guide.md)。
  
## <a name="staging-environment"></a>預備環境  
 您通常會使用預備環境進行 「 單元測試 」 的 BizTalk 方案的實際部署。 預備環境中安裝的軟體應該相當符合實際執行環境中安裝的軟體。 它，不過，可以接受在預備環境中使用虛擬電腦，因為此環境並不是要用來測量效能。 如需部署到預備環境的 BizTalk 應用程式的詳細資訊，請參閱[BizTalk 應用程式部署的暫存工作](../core/staging-tasks-for-biztalk-application-deployment.md)。
  
## <a name="production-environment"></a>實際執行環境  
 在實際執行環境是 「 即時 」 的環境，將裝載執行 BizTalk 解決方案。 實際執行環境中發行管理程序的最後一個端點並應該只裝載 BizTalk 應用程式先前已經歷開發、 單元測試、 負載測試和在其他環境中的臨時區域。 完整的單元測試、 負載測試和預備此預先將協助您確保最大效能和 BizTalk 應用程式在生產環境中的執行時間。  
  
## <a name="guidelines-for-allocating-servers"></a>配置伺服器的指導方針  
 BizTalk server 與 SQL server，您應配置給發行管理程序，讓特定數目的實體電腦的每個階段的數目預計會在生產環境中使用下列指導方針提供根據經驗法則： 它們是粗略這可能會根據您的架構變更估計值。  
  
> [!NOTE]  
>  虛擬伺服器可能在開發和預備環境中使用，也可以用於單元測試。 所有的效能測試應該符合在實際執行環境中的實體硬體的實體硬體上執行。  
  
|執行 BizTalk Server 用於實際執行 （建議的實體硬體） 的電腦|開發伺服器 （虛擬或實體硬體）|測試伺服器 （建議的實體硬體）|臨時伺服器 （虛擬或實體硬體）|總計 [否]。 執行 BizTalk Server 的電腦|  
|---|---|---|---|---|  
|1|2|1|1|5|  
|2|2|2|1|7|  
|3|2|3|1|9|  
|4|2|4|1|11|  
  
|估計 [否]。 執行 SQL Server 用於實際執行 （建議的實體硬體） 的電腦|開發伺服器 （虛擬或實體硬體）|測試伺服器 （建議的實體硬體）|臨時伺服器 （虛擬或實體硬體）|總計 [否]。 執行 SQL Server 的電腦|  
|---|---|---|---|---|  
|1|1|1|1|4|  
|2|1|2|1|6|  
|3|2|3|1|9|  
|4|2|4|1|11|  
  
## <a name="see-also"></a>另請參閱  
 [規劃 BizTalk Server 的環境](../technical-guides/planning-the-environment-for-biztalk-server.md)