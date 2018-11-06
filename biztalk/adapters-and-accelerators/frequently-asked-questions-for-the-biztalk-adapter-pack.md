---
title: BizTalk Adapter Pack 的常見問題集 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0cdaf09a-50fe-4f30-bd9d-60e316351846
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b62675f0f2f4d798ef93ead8e8e9281d28917795
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50752463"
---
# <a name="frequently-asked-questions"></a>常見問題集
常見問題集 (Faq) 的相關[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。  


## <a name="general-questions"></a>一般問題

### <a name="what-are-the-supported-biztalk-versions-for-the-biztalk-adapter-pack"></a>BizTalk Adapter Pack 支援的 BizTalk 版本有哪些？  
 [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]隨附於 Microsoft [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。 安裝版本隨附於您[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]版本。 安裝[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]從另一個[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]不支援的版本。 

### <a name="in-which-user-context-should-the-setup-be-run"></a>在哪一個使用者內容中應該安裝程式要執行？  
執行[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]安裝程式使用的是本機 administrators 群組成員的帳戶和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。 

相關的連結：[最低安全性權限](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx)

### <a name="how-do-i-get-started-using-the-adapter"></a>如何開始使用配接器？  
如果您熟悉[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]而[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，然後安裝[BAP 2016](../adapters-and-accelerators/install-the-biztalk-adapter-pack-2016.md)或[BAP 2013 R2 和 2013年](../adapters-and-accelerators/install-biztalk-adapter-pack-2013-r2-and-2013.md)，然後立刻開始使用[不同配接器](../adapters-and-accelerators/biztalk-adapter-pack.md).

如果您是全新[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]或[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，看看 get 啟動主題，並逐步進行教學課程： 

[開始使用 BizTalk Adapter for Oracle 資料庫](../adapters-and-accelerators/adapter-oracle-database/get-started-with-the-oracle-database-adapter.md)  
[開始使用 BizTalk Adapter for Oracle E-business Suite](../adapters-and-accelerators/adapter-oracle-ebs/get-started-with-the-biztalk-adapter-for-oracle-e-business-suite.md)  
[開始使用 BizTalk Adapter for mySAP Business Suite](../adapters-and-accelerators/adapter-sap/get-started-with-the-biztalk-adapter-for-mysap-business-suite.md)  
[開始使用 BizTalk Adapter for Siebel eBusiness 應用程式](../adapters-and-accelerators/adapter-siebel/get-started-with-the-biztalk-adapter-for-siebel-ebusiness-applications.md)  
[開始使用 BizTalk adapter for SQL](../adapters-and-accelerators/adapter-sql/get-started-with-the-biztalk-adapter-for-sql.md)

### <a name="does-the-microsoft-biztalk-adapter-pack-support-tracing"></a>Microsoft BizTalk Adapter Pack 支援追蹤？  
[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]可讓配接器用戶端啟用 Windows Communication Foundation (WCF) 追蹤和配接器特定的追蹤。 當您啟用追蹤時，您也可以選擇的資料夾路徑和檔案名稱。 因此，追蹤會儲存您希望的位置。 若要檢視追蹤，請使用 WCF 服務追蹤檢視器工具。 請參閱[使用服務追蹤檢視器檢視相關追蹤並進行疑難排解](https://msdn.microsoft.com/library/aa751795.aspx)。

如需有關追蹤與其他疑難排解的相關說明的詳細資訊，請參閱： 

[Oracle 資料庫配接器進行疑難排解](../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)  
[Oracle EBS 配接器進行疑難排解](../adapters-and-accelerators/adapter-oracle-ebs/troubleshooting-the-oracle-ebs-adapter.md)  
[SAP 配接器進行疑難排解](../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)  
[Siebel 配接器進行疑難排解](../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)  
[SQL 配接器進行疑難排解](../adapters-and-accelerators/adapter-sql/troubleshoot-the-sql-adapter.md)  

### <a name="are-performance-counters-available-for-the-adapters"></a>是適用於配接器效能計數器嗎？  
是的。 [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]提供**LOB 的時間 （累計）** 效能計數器來測量時間 （毫秒），以完成某個動作，起始配接器所採用的 LOB 用戶端程式庫。  您可以設定來啟用效能計數器`EnablePerformanceCounters`屬性來繫結 **，則為 True**。 若要停用效能計數器，請設定`EnablePerformanceCounters`要**False** （預設值）。   

## <a name="biztalk-server-questions"></a>BizTalk Server 相關問題

### <a name="which-biztalk-server-tools-are-used-while-working-with-adapters-where-can-i-find-more-information-about-these-tools"></a>使用配接器時，會使用哪些 BizTalk Server 工具？ 哪裡可以找到這些工具的詳細資訊？  
有數個工具，可協助使用這些介面卡的成品： 


|                                  工具                                  |                                                                                                                                                                                           中的主題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]核心文件集                                                                                                                                                                                            |
|------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] | -   [使用 Visual Studio](../core/using-visual-studio.md) <br />-   [使用 BizTalk 專案](../core/working-with-biztalk-projects.md)<br />-   [部署 BizTalk 組件從 Visual Studio 到 BizTalk 應用程式](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)<br /><br /> 深入了解 Visual Studio 方案、 專案和項目會在[Visual Studio 中方案和專案](https://msdn.microsoft.com/library/b142f8e7.aspx)。 |
|                         協調流程設計師                         |                                                                                                                                                                                       [使用協調流程設計師建立協調流程](../core/creating-orchestrations-using-orchestration-designer.md)                                                                                                                                                                                        |
|                           管線設計師                            |                                                                                                                                                                                                 [使用管線設計師建立管線](../core/creating-pipelines-using-pipeline-designer.md)                                                                                                                                                                                                  |
|                             BizTalk Mapper (BizTalk 對應工具)                             |                                                                                                                                                                                                         [使用 BizTalk 對應工具建立對應](../core/creating-maps-using-biztalk-mapper.md)                                                                                                                                                                                                          |
|                 BizTalk Server 管理主控台                  |                                                                                                                                                                                            [使用 BizTalk Server 管理主控台](../core/using-the-biztalk-server-administration-console.md)                                                                                                                                                                                             |

### <a name="can-i-reuse-bindings-of-a-biztalk-application-how"></a>可以重複使用 BizTalk 應用程式的繫的結嗎？ 如何？  
是的。 繫結會建立對應，以單一邏輯端點，例如協調流程連接埠或角色連結，與實體端點，例如傳送和接收埠。 這讓通訊能在不同的 BizTalk 商務方案元件之間進行。 繫結資訊會儲存在包含 BizTalk 組件、 應用程式或群組的範圍中每個 BizTalk 協調流程的繫結資訊的 XML 檔案中。 您可以匯出 BizTalk 組件、 應用程式或群組的繫結，並重複使用將它匯入至 BizTalk 應用程式或群組。 如需相關資訊，請參閱 

[重複使用 Oracle DB 配接器繫結](../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md)  
[重複使用 Oracle EBS 配接器繫結](../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md)  
[重複使用 SAP 配接器繫結](../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md)  
[重複使用 Siebel 配接器繫結](../adapters-and-accelerators/adapter-siebel/reuse-adapter-bindings-in-the-siebel-adapter.md)  
[重複使用 SQL 配接器繫結](../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md)

### <a name="what-is-the-transaction-isolation-level-how-can-i-configure-it"></a>什麼是 「 交易隔離層級 」？ 如何設定它？  
 交易隔離等級會決定交易是由其他交易所做的資料變更與隔離的程度。 它會定義連接至的營運 (LOB) 系統所發出的 TRANSACT-SQL 命令的鎖定行為。 

這是可設定某些配接器。 請參閱： 

[Oracle 資料庫： 設定交易隔離等級和交易等待時間](../adapters-and-accelerators/adapter-oracle-database/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-db.md)  
[Oracle E-business Suite： 設定交易隔離等級和交易等待時間](../adapters-and-accelerators/adapter-oracle-ebs/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-ebs.md)  
[SQL： 設定交易隔離等級和交易等待時間](../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md)

[SQL 資料庫引擎中的隔離等級](https://technet.microsoft.com/library/ms189122.aspx)說明在 SQL 中的不同層級。 

## <a name="wcf-based-adapter-faqs"></a>WCF 架構的配接器常見問題集

### <a name="what-is-wcf"></a>WCF 是什麼？
 WCF 代表 Windows Communication Foundation。 WCF 是建置服務導向應用程式由 Microsoft 所開發的程式設計架構。 WCF 是.NET framework 的一部分，並可讓開發人員建置安全、 可靠和交易性的解決方案，跨平台整合，並與現有投資交互操作。  

相關的連結：[何謂 Windows Communication Foundation](https://msdn.microsoft.com/library/ms731082.aspx)  

### <a name="what-is-wcf-lob-adapter-sdk"></a>WCF LOB 配接器 SDK 是什麼？  
 WCF LOB 配接器 SDK 是工具和元件，提供一致的架構開發可重複使用、 豐富的中繼資料的特定業務系統的配接器的集合。 配接器使用 WCF LOB 配接器 SDK 撰寫會呈現為自訂 WCF 繫結，並可供 WCF 支援的用戶端。 

相關的連結： [WCF 線條的營運配接器 SDK 文件](../adapters-and-accelerators/wcf-lob-adapter-sdk/microsoft-wcf-line-of-business-adapter-sdk-documentation.md) 

### <a name="what-is-the-wcf-service-model"></a>WCF 服務模型是什麼？  
 WCF 服務模型是 LOB 系統 （例如 Oracle 或 SAP） 公開為 WCF 服務的 WCF 所提供的程式設計模型。 為.NET 介面，表示用戶端與服務之間存在的服務合約和作業會表示成此介面上的方法。 WCF 服務模型會產生 proxy 類別，WCF 用戶端類別，透過此程式碼可以叫用作業，並接收使用配接器的資料。 

 中的所有介面卡[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]支援 WCF 服務模型。

 ### <a name="what-is-the-wcf-channel-model"></a>WCF 通道模型是什麼？  
 WCF 通道模型是低層級的抽象概念的用戶端與服務之間的 SOAP 訊息交換。 它提供介面和類型，可讓您傳送和接收訊息所使用的是稱為通道堆疊的多層式通訊協定堆疊。 堆疊的每個圖層由通道所組成，每一個色頻建立從 WCF 繫結。 每個配接器是 WCF 自訂傳輸繫結會公開為 WCF 服務的 LOB 系統。 

  中的所有介面卡[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]支援 WCF 通道模型。

### <a name="when-should-i-use-the-wcf-service-model-or-the-wcf-channel-model"></a>何時應該使用 WCF 服務模型或 WCF 通道模型？  
 WCF 服務模型提供的模型很熟悉.NET 程式設計人員，並透過通道會隱藏基礎 SOAP 訊息交換的複雜性。 此外，新增的配接器服務參考外掛程式會與 Visual Studio 的設計體驗，整合，並提供標準的 Microsoft Windows 介面提供強大的瀏覽和搜尋功能，對配接器所公開的作業。 因此，WCF 服務模型通常是開發任何 WCF 架構配接器程式設計解決方案的最佳選擇。  

 您想要使用透過 WCF 服務的 WCF 通道模型建立模型時：  

-   WCF 通道模型提供更細微的控制，透過在 WCF 通道模型中，您直接控制您透過通道傳送訊息的內容，因為部署 LOB 系統執行的作業。  

-   WCF 通道模型提供更完整的支援，以端對端串流大型物件 (LOB) 資料類型，與 WCF 服務模型。 這是因為在 WCF 通道模型中，您直接控制如何於外寄訊息提供訊息內文和訊息本文，對傳入訊息的處理方式。 

### <a name="how-do-i-get-started-with-the-wcf-service-model"></a>如何開始使用 WCF 服務模型？  
 提供 WCF 服務模型來產生 WCF 用戶端類別或 WCF 服務合約和相關聯的協助程式程式碼，從服務中繼資料會由每張介面卡，您可以使用下列工具：  

- ServiceModel Metadata Utility Tool (svcutil.exe)，隨附於 WCF。  

- 新增配接器服務參考 Visual Studio 外掛程式，隨附於[!INCLUDE[adapterpacknoversion_md](../includes/adapterpacknoversion-md.md)]。  

### <a name="how-do-i-get-started-with-the-wcf-channel-model"></a>如何開始使用 WCF 通道模型？  
 使用 WCF 通道模型時，可以叫用作業，並使用配接器的 SOAP 訊息交換透過 WCF 通道來接收輪詢查詢的結果。 若要開始，您需要建立輸出 （用戶端） 和輸入 （服務） 通道。

## <a name="see-also"></a>另請參閱  
[BizTalk Adapter Pack](../adapters-and-accelerators/biztalk-adapter-pack.md)