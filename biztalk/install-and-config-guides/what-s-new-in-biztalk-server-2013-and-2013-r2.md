---
title: "什麼是 BizTalk Server 2013 和 2013 R2 的新功能 |Microsoft 文件"
description: "新功能和變更 BizTalk Server 2013 R2 和 2013年中的完整清單"
caps.latest.revision: "67"
author: MandiOhlinger
manager: anneta
ms.custom: 
ms.date: 2017-08-10
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bdb841f7-4aa9-45c9-a6f1-d527089fcc09
ms.author: mandia
ms.openlocfilehash: 49a4e668f1c5e23169464fdbc4b4f0464a062628
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="whats-new-in-biztalk-server-2013-and-2013-r2"></a>BizTalk Server 2013 和 2013 R2 有哪些新功能？
請參閱 [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)] 和 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013 的新功能及取代的項目。
  
##  <a name="BKMK_NewR2"></a> BizTalk Server 2013 R2 有哪些新功能？  
  
|功能|描述|  
|-------------|-----------------|  
|支援新版的 Windows 作業系統、SQL Server 和 Visual Studio|請參閱 [BizTalk Server 2013 和 2013 R2 的硬體和軟體需求](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md)。|  
|支援 JSON|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 現在支援傳送及接收 JSON 訊息。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 包含從 JSON 執行個體產生 XSD 結構描述的精靈，以及搭配自訂管線使用的編碼器和解碼器元件。 如需詳細資訊，請參閱[使用 BizTalk Server 處理 JSON 訊息](../core/processing-json-messages-using-biztalk-server.md)。|  
|更新為 SB-Messaging 配接器|在 ACS 之外，已增強 SB Messaging 配接器以支援 SAS (共用存取簽章) 型驗證。  使用這項新改進，BizTalk Server 現在也可以與內部部署版本的服務匯流排互動。 如需詳細資訊，請參閱 [SB-Messaging 配接器](../core/sb-messaging-adapter.md)。|  
|更新為 SFTP 配接器|SFTP 配接器現在支援雙因素驗證，提供在上傳/下載大型檔案時指定暫時資料夾的選項。 您也可以選取指定至您目標伺服器的加密編碼器值。 如需詳細資訊，請參閱 [SFTP 配接器](../core/sftp-adapter.md)。|  
|更新為 HL7 加速器|HL7 加速器現在支援以下功能：<br /><br /> - 可納入任意文字料為訊息的一部分，並由 HL7 管線進行處理。<br /><br /> - 主控 Hl7 配接器 64 位元支援。<br /><br /> 請參閱 [BizTalk Accelerator for HL7 的新功能](http://msdn.microsoft.com/library/ee409458\(v=bts.80\).aspx)。|  
|BHM 狀況監控|BHM 狀況監控是新的 BizTalk 嵌入式管理單元，可協助您監視 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境的健全狀況。 此嵌入式管理單元可以加入現有的 BizTalk 管理主控台，或個別執行。 以下是 BHM 狀況監控的功能︰<br /><br /> - 產生與檢視健全狀況報表<br /><br /> - BizTalk 環境的整體健全狀況儀表板檢視<br /><br /> - 傳送電子郵件通知<br /><br /> - 排程報表集合<br /><br /> - 整合效能監視器能與預先載入的案例型效能計數器<br /><br /> - 監視多個 BizTalk 環境<br /><br /> - 報表管理<br /><br /> 如需 BHM 狀況監控的詳細資訊，請參閱 [Getting Started with BizTalk Health Monitor](http://go.microsoft.com/fwlink/?LinkId=403315) (從 BHM 狀況監控開始) 及 [Overview of BizTalk Health Monitor](http://go.microsoft.com/fwlink/?LinkId=403316) (BHM 狀況監控概觀)。|  
  
### <a name="deprecated-list"></a>已被取代的清單  
  
|計畫|狀態|取代|  
|-------------|------------|-----------------|  
|RFID Mobile|已移除|無|  
|RFID 伺服器|已被取代|無|  
|SharePoint SSOM/Web 服務配接器|已被取代|使用 CSOM (用戶端物件模型) 選項。<br /><br /> [Windows SharePoint Services 配接器](../core/windows-sharepoint-services-adapter.md)<br /><br /> [附錄 B：安裝 Microsoft SharePoint 配接器](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)|  
|SOAP adapter (SOAP 配接器)|已被取代|[WCF-BasicHttp 配接器](../core/wcf-basichttp-adapter.md)|  
|舊的 SQL 配接器|已被取代|[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] 中的 WCF-SQL 配接器|  
|UDDI|已被取代|無|  
  
> [!IMPORTANT]
>  較新版本的 BizTalk 中可能還存有這些已被取代的部分功能。 在這種情況下，請注意下列事項：  
>   
>  -   BizTalk 內部可以使用的功能，不表示可供客戶解決方案使用。 客戶解決方案不支援這類功能。  
> -   Microsoft 可能已修改介面且不公開使用。  
  
##  <a name="BKMK_New"></a> BizTalk Server 2013 的新功能  
 BizTalk Server 2013 中納入了下列功能。  
  
 **Azure IaaS 上的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**  
  
|功能|說明|  
|-------------|-----------------|  
|在 [!INCLUDE[winazure](../includes/winazure-md.md)][!INCLUDE[vm](../includes/vm-md.md)] 上設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|請參閱[在 Windows Azure 中建立 BizTalk 虛擬機器](http://msdn.microsoft.com/library/jj572843.aspx)。|  
|在 [!INCLUDE[winazure](../includes/winazure-md.md)][!INCLUDE[vm](../includes/vm-md.md)] 建立 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 群組|請參閱[建立 BizTalk 群組必要條件](http://msdn.microsoft.com/library/jj248711.aspx)及[設定 BizTalk 群組](http://msdn.microsoft.com/library/jj572845.aspx)。|  
  
 **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]內部部署**  
  
|功能|描述|  
|-------------|-----------------|  
|依核心授權模型|SQL Server 2013 也是依核心。 SQL Server 2012 也是依核心。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2010 和舊版是依處理器。<br /><br /> 在四核心或較少核心的處理器上執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時，授權成本保持與 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2010 一致。 核心授權按處理器授權成本每季計價。 以較高容量的處理器執行伺服器時，授權成本會因為硬體耗能增加而增加。<br /><br /> 如需協助判斷您所需要的授權數目，可以使用 *C:\Program Files (x86)\Microsoft BizTalk Server 20xx\SDK\Utilities\LicenseUsageTracking* 中的 PowerShell Cmdlet。<br /><br /> 有用的連結︰<br /><br /> [BizTalk Server 2013 價格與版本](http://www.microsoft.com/biztalk/pricing.aspx)<br /><br /> [瞭解 BizTalk Server 2013 授權](http://blogs.biztalk360.com/understand-biztalk-server-2013-licensing/)|  
|支援新的配接器|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供新的配接器擴充 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式連接到 [!INCLUDE[winazure](../includes/winazure-md.md)] 的能力。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 也提供 SharePoint 配接器的更新，讓使用者可以選擇使用用戶端或伺服器端物件模型連接到 SharePoint 伺服器。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 包含新的配接器，從 SFTP 伺服器傳送和接收訊息。|  
|追蹤成品之間的相依性|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 更新 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台，提供 UI 驅動體驗以查看不同的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 成品，例如協調流程、傳送埠、接收位置等等如何彼此相依。 如需詳細資訊，請參閱[追蹤 BizTalk Server 應用程式中成品之間的依存性](../core/tracking-dependencies-between-artifacts-in-a-biztalk-server-application.md)。|  
|整合式 ESB Toolkit|ESB Toolkit 現在整合為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝程式的一部分。 此外，也簡化 ESB Toolkit 設定體驗以方便使用者快速啟動。 如需詳細資訊，請參閱[安裝和設定 Microsoft BizTalk ESB Toolkit](../esb-toolkit/install-and-configure-the-microsoft-biztalk-esb-toolkit.md)。|  
|支援新版的 Windows 作業系統、SQL Server 和 Visual Studio|請參閱 [BizTalk Server 2013 和 2013 R2 的硬體和軟體需求](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md)。|  
|受支援 EDI 結構描述的更新|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 推出下列 EDI 結構描述的支援︰<br /><br /> -                     **X12** – 5040、5050、6020、6030<br /><br /> - **EDIFACT** – D06A、D06B、D07A、D07B、D08A、D08B、D09A、D09B、D10A、D10B<br /><br /> -                     **HL7** – 已加入 2.51 訊息支援<br /><br /> -                     **SWIFT** – 2012年訊息組件<br /><br /> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝套件包含結構描述。 您可以從 [http://go.microsoft.com/fwlink/p/?LinkId=258228](http://go.microsoft.com/fwlink/p/?LinkId=258228) 下載安裝套件。|  
|對應程式使用 XSLCompiledTransform|對應程式使用 XSLCompiledTransform 類別。 舊版的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 使用 XslTransform 類別，此作法已淘汰。 XSLCompiledTransform 類別提供效能增強功能，包括︰<br /><br /> - 一旦 Load 方法順利完成，就可以從多個執行緒同時呼叫 Transform 方法。<br /><br /> - 新的 XSLT 處理器會將 XSLT 樣式表編譯成常見的中繼格式。 樣式表編譯完成後，即可予以快取和重複使用。<br /><br /> 詳細資訊請參閱 [What the BizTalk Server 2013 Mapper Updates Mean for You](http://www.quicklearn.com/blog/2013/05/24/what-the-biztalk-server-2013-mapper-updates-mean-for-you/) 和 [XslCompiledTransform Class](https://msdn.microsoft.com/library/system.xml.xsl.xslcompiledtransform.aspx) (XslCompiledTransform 類別)。|  
|可設定的動態傳送埠處理常式|建立動態傳送埠時，可針對「每一個」安裝的配接器設定配接器傳送處理常式。 同時包含單向以及請求-回應動態通訊埠。 在舊版的 BizTalk 中，動態傳送埠會使用配接器的預設主控件。<br /><br /> [可設定的動態傳送埠處理常式](../core/dynamic-send-port-handler-is-configurable.md)會提供詳細資訊。|  
|排序的傳遞|在舊版 BizTalk 的排序傳遞使用多個端點的案例中，最慢的配接器類型速度最快。 這種行為會直接影響 HL7 解決方案。 使用 MLLP 配接器時需有通知 (ACK)。 因為必須在傳送下一個訊息之前收到 ACK，所以會發生延遲。<br /><br /> 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，不用等待先前訊息的 ACK 就可以傳送下一個訊息。 當 ACK 抵達時，會在內部與其訊息相互關聯/連接。|  
|Support Tools|Support Tools 會隨 Biztalk 自動安裝︰*C:\Program Files (x86)\Microsoft BizTalk Server 20xx\SDK\Utilities\Support Tools*。<br /><br /> 這些工具包括：<br /><br /> - BizTalk 組件檢查程式<br /><br /> - MsgBox 檢視器<br /><br /> - PSSDiagForBizTalk<br /><br /> - BizTalk 結束字元下載的網際網路捷徑|  
|PowerShell 提供者|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] PowerShell 提供者位於 *C:\Program Files (x86)\Microsoft BizTalk Server 2013\SDK\Utilities\PowerShell*。<br /><br /> 舊版的 BizTalk 有 CodePlex PowerShell 提供者，位於 [http://psbiztalk.codeplex.com/](http://psbiztalk.codeplex.com/)。|  
|BAM 警示|若 BizTalk Server 2013 使用 [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)]，需要 Database Mail 才能使用 BAM 警示。 若 BizTalk Server 使用 SQL Server 2008 R2，需要 SQL Server Notification Services 才能使用 BAM 警示。<br /><br /> [BAM 警示](../install-and-config-guides/prepare-your-computer-for-installation.md#BKMK_BAMAlerts)提供詳細資訊。|  
  
> [!IMPORTANT]
>  當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 安裝在不同的電腦時，分散式交易協調器 (MS DTC) 會處理電腦間的交易。 因此，[!INCLUDE[bts2013r2](../includes/bts2013r2-md.md)] 和 2013 不支援 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] AlwaysOn 功能。 自 [!INCLUDE[bts2016](../includes/bts2016-md.md)] 開始，**支援** AlwaysOn 功能。 如需詳細資訊，請參閱 [BizTalk Server 2016 的新功能](../install-and-config-guides/what-s-new-in-biztalk-server-2016.md)。  
  
### <a name="known-issues"></a>已知問題  
 [Known issues in BizTalk Server 2013](http://support.microsoft.com/kb/2954101) (BizTalk Server 2013 的已知問題)