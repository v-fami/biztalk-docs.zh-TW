---
title: 規劃開發、 測試、 預備及生產環境 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6c83a42d-117f-4a24-a669-b3e4e1c9a056
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4d72440595adb34b822b70e934985f88f79c66d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996047"
---
# <a name="planning-the-development-testing-staging-and-production-environments"></a>規劃開發、 測試、 預備及生產環境
本主題討論使用發行管理程序中的 BizTalk 解決方案的環境。 如同任何企業軟體解決方案，您應該遵循已建立的軟體發行管理指導方針，當您開發和發行的 BizTalk 解決方案。 此程序應該包括下列的不同階段：  
  
- 部署  
  
- 測試  
  
- 預備環境  
  
- Production  
  
  在理想情況下，您應該先完成發行管理程序，在獨立環境中，不同於其他環境中的每個階段。 實際上，您可能要結合一或多個環境，因為硬體、 時間或其他資源條件約束。 最少，您應該分開從其他環境的實際執行環境。  
  
> [!NOTE]
>  最新的安裝和升級指示，以便讓 BizTalk Server 會列在[BizTalk Server 功能的新增、 安裝、 設定和升級](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md)。 
> 
> ##  <a name="BKMK_VirtualServ"></a> 在 發行管理程序期間使用 Virtual Server  
>  請考慮完成開發、 單元測試和預備中的 「 虛擬 」 的環境。 執行開發工作，單元測試，並在虛擬環境中的預備環境提供很大的彈性，並使用遠少於硬體資源，否則需要比。 如果使用虛擬環境時，配置至少 512 MB 的記憶體在主機電腦，並增加 512 MB 的記憶體供主機作業系統上執行每個虛擬機器。  
  
 例如，對於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用五部虛擬機器的環境 (兩部執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]、 兩個 Microsoft[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]叢集節點和一個網域控制站)，您應該規劃將 3 GB 的記憶體的主機電腦上安裝。 如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境需要超過 2 GB 的記憶體，請考慮在主機電腦，以確保已安裝的記憶體最大數量供主機作業系統上安裝 64 位元版本的 Windows。  
  
> [!NOTE]
>  如需有關使用建議[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在虛擬環境中，請參閱[BizTalk Server 2009 HYPER-V 指南](http://go.microsoft.com/fwlink/?LinkId=151834)(<http://go.microsoft.com/fwlink/?LinkId=151834>)。  
> 
> [!NOTE]
>  在任何 Microsoft 知識庫文章 842301 中列出的虛擬化軟體執行的受支援作業系統上完全支援 BizTalk Server [虛擬機器上的MicrosoftBizTalkServer可支援性](https://support.microsoft.com/kb/842301). 不過，BizTalk Server 可能無法如預期般運作，如果安裝在以外的知識庫文章中提到的那些虛擬化軟體中執行的受支援作業系統上執行。  
  
## <a name="development-environment"></a>開發環境  
 在開發環境中建立 BizTalk 專案所使用的 BizTalk 方案。 您應該在使用中的電腦上安裝下列軟體[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]開發環境：  
  
- Internet Information Services (IIS)  
  
- Visual Studio  
  
- SQL Server 用戶端工具  
  
- [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] （包括下列元件）  
  
  -   文件集  
  
  -   系統管理工具  
  
  -   開發人員工具和 SDK  
  
  -   其他軟體  
  
- [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫是在本機裝載在開發期間。  
  
- 通常開發人員也應該有自己的開發電腦 （實體或虛擬），安裝必要軟體。  
  
> [!NOTE]  
>  我們建議您購買，並針對非生產環境中使用 Visual Studio 訂用帳戶。 Visual Studio 訂用帳戶從相同的軟體的零售授權的成本提供可觀的折扣。 請參閱[Visual Studio 訂用帳戶](https://visualstudio.com/subscriptions)。  
  
## <a name="testing-environment"></a>測試環境  
 單元測試可以在虛擬環境中完成。 您應，不過，進行您在具有等同於生產環境的軟硬體的實體環境中測試的效能。  
  
 測試環境用以測量效能特性，例如最大持續輸送量 (MST) 」 和 「 BizTalk 解決方案的最大持續性追蹤輸送量。 它應該儘可能密集地因此比對實體的實際執行環境。 如需有關測量效能特性的 BizTalk 解決方案請參閱[引擎效能特性](../core/engine-performance-characteristics.md)，或有[BizTalk Server 效能最佳化指南](../technical-guides/biztalk-server-2010-performance-optimization-guide.md)。
  
## <a name="staging-environment"></a>預備環境  
 您通常會使用 「 單元測試 」 在預備環境的 BizTalk 方案的實際部署。 預備環境中安裝的軟體應該相當符合生產環境中安裝的軟體。 它，不過，可以接受在預備環境中使用虛擬電腦，因為此環境不是用來測量效能。 如需部署至預備環境的 BizTalk 應用程式的詳細資訊，請參閱[BizTalk 應用程式部署的預備工作](../core/staging-tasks-for-biztalk-application-deployment.md)。
  
## <a name="production-environment"></a>生產環境  
 生產環境是 「 即時 」 的環境，將裝載執行的 BizTalk 方案。 生產環境是在發行管理程序中的最後一個端點，且應該只裝載 BizTalk 應用程式先前已在開發、 單元測試、 負載測試和在其他環境中的預備環境所經歷。 完整的單元測試、 負載測試和預備事先將可協助您確保最大效能和 BizTalk 應用程式在生產環境中的執行時間。  
  
## <a name="guidelines-for-allocating-servers"></a>配置伺服器的指導方針  
 下列指導方針提供 BizTalk server 和 SQL server，您應該將配置給發行管理程序，提供特定數目的實體電腦的每個階段的數目預計會使用於生產環境中的經驗法則： 它們是概略這可能會有所變更，根據您的架構的估計值。  
  
> [!NOTE]  
>  虛擬伺服器可能會使用在開發和預備環境中，並也用於單元測試。 所有的效能測試應該符合在實際執行環境中的實體硬體的實體硬體上執行。  
  
|執行 BizTalk Server 用於生產環境 （建議的實體硬體） 中的電腦|開發伺服器 （虛擬或實體硬體）|測試伺服器 （建議的實體硬體）|預備伺服器 （虛擬或實體硬體）|總計 [否]。 執行 BizTalk Server 的電腦|  
|---|---|---|---|---|  
|@shouldalert|2|@shouldalert|@shouldalert|5|  
|2|2|2|@shouldalert|7|  
|3|2|3|@shouldalert|9|  
|4|2|4|@shouldalert|11|  
  
|預估 [否]。 執行生產環境 （建議的實體硬體） 中使用的 SQL Server 的電腦|開發伺服器 （虛擬或實體硬體）|測試伺服器 （建議的實體硬體）|預備伺服器 （虛擬或實體硬體）|總計 [否]。 執行 SQL Server 的電腦|  
|---|---|---|---|---|  
|@shouldalert|@shouldalert|@shouldalert|@shouldalert|4|  
|2|@shouldalert|2|@shouldalert|6|  
|3|2|3|@shouldalert|9|  
|4|2|4|@shouldalert|11|  
  
## <a name="see-also"></a>另請參閱  
 [規劃 BizTalk Server 的環境](../technical-guides/planning-the-environment-for-biztalk-server.md)