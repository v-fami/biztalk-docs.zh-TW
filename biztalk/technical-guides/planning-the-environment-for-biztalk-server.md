---
title: "規劃 BizTalk Server 環境 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e9ef0b4-eccb-47e2-bbb5-e859ffa0468c
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66cd358f3d8a4fbda2c4ed43432f1ad8b2f6979e
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="planning-the-environment-for-biztalk-server"></a>規劃 BizTalk Server 環境
操作指南中的規劃 > 一節說明角色和責任聯[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。 它包含規劃建議的應用程式和資料層[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境中，並可提供發行計劃建議的 BizTalk 解決方案的管理階段。  
  
 此一說進入 」 您無法在計劃，如果您計劃失敗。 」 當然有這個安全的建議的例外狀況，成功實作生產環境的 BizTalk 解決方案不是其中一個。 本簡介主題，以規劃 > 一節提供規劃 BizTalk 解決方案時，您應該做的決策的高階概觀。  
  
## <a name="deciding-whether-biztalk-server-is-the-right-tool-for-the-job"></a>決定 BizTalk Server 是否正在正確的工具來執行工作  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可以視為 「 商務整合引擎。 」 基本上，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]設計成可整合不同的商務營運系統、 處理序和訊息。 例如，交換符合 EDI 標準之訊息的商務系統可能需要整合與商務系統交換符合 RosettaNet 標準的訊息。 或者，使用 SAP 的內部商務系統可能需要與另一個將資料儲存在 Microsoft SQL Server 資料庫的內部商務系統進行通訊。 或可能必須只能傳送或接收訊息使用 FTP 通訊協定的商務系統與只能使用 HTTP 通訊協定的商務系統交換訊息。  
  
 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]藉由當做系統之間的訊息傳遞 middleman 配合這種不同的系統的整合。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]支援廣泛的業界標準傳輸通訊協定、 文件交換格式和企業營運應用程式。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]也提供功能強大的商業程序自動化功能，BizTalk 協調流程引擎中。 您可以使用 BizTalk 協調流程設計師來建立商務程序，這可以內建在 BizTalk 協調流程引擎中執行的可執行程式碼的視覺化表示。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]也包含數個其他功能，幫助資訊工作者例如商務活動監控 (BAM)，包括訊息的工作流程引擎、 商務規則引擎 (BRE) 和技術的企業整合。  
  
 如需有關使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]商務程序的管理功能，請參閱[技術白皮書： Microsoft 和 BPM-技術概觀](http://go.microsoft.com/fwlink/?LinkId=106015)(http://go.microsoft.com/fwlink/?LinkId=106015)。 若要深入了解不同的整合技術，提供由 Microsoft 和一個具有其他優點，請參閱[了解 Microsoft 整合技術](http://go.microsoft.com/fwlink/?LinkId=158452)(http://go.microsoft.com/fwlink/?LinkId=158452)。  
  
 特定的整合案例是較適用於其他 Microsoft 產品。 如果您的主要焦點是在下列任何案例時，請考慮使用這些 Microsoft 產品，而不是[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]:  
  
|**狀況**|**若要使用的產品**|  
|------------------|------------------------|  
|使用者佈建|**Microsoft Identity Lifecycle Manager 2010**<br /><br /> 如需 Microsoft Identity Lifecycle Manager 2010 的詳細資訊，請參閱[Microsoft Identity Lifecycle Manager 2010 FP1](http://go.microsoft.com/fwlink/?LinkId=204577) (http://go.microsoft.com/fwlink/?LinkId=204577)。|  
|系統之間的資料複寫|**SQL Server 複寫**<br /><br /> 如需有關 SQL Server 複寫的詳細資訊，請參閱[SQL Server 2008 R2 複寫](http://go.microsoft.com/fwlink/?LinkID=69978)(http://go.microsoft.com/fwlink/?LinkID=69978)。|  
|資料擷取、 轉換及載入 (ETL)|**SQL Server Integration Services (SSIS)**<br /><br /> 如需有關 SQL Server Integration Services 的詳細資訊，請參閱[SQL Server 2008 R2 Integration Services](http://go.microsoft.com/fwlink/?LinkId=152044) (http://go.microsoft.com/fwlink/?LinkId=152044)。|  
  
## <a name="deciding-which-edition-of-biztalk-server-is-right-for-the-job"></a>決定哪個版本的 BizTalk Server 作業的權限  
 有四個不同的版本的 BizTalk Server 中，其中每個為目標的特定案例。 BizTalk Server 的四個版本包括：  
  
-   **企業**-與企業層級需求的高容量、 可靠性和可用性設計的客戶。  
  
-   **標準**-中等的磁碟區與小數位數的部署需求的企業而設計。  
  
-   **分支**-特殊版本的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]設計中樞和支點部署案例包括 RFID。  
  
-   **開發人員**-提供的所有企業版功能開發和測試用途，並可做為 BizTalk Server 評估版，不花一毛錢供評估之用。 安裝成評估版，BizTalk Server 將運作 120 天。  
  
-   **RFID 企業**-設計用來開發、 部署和管理豐富的 RFID 和感應器解決方案，包含 BizTalk RFID Server 與 BizTalk RFID Mobile 提供可擴充、 可延伸的平台。  
  
 如需 BizTalk Server 的不同版本的詳細資訊，請參閱[Microsoft BizTalk Server 版本](http://go.microsoft.com/fwlink/?LinkId=108051)(http://go.microsoft.com/fwlink/?LinkId=108051)。  
  
## <a name="planning-for-message-load"></a>規劃訊息負載  
 一旦您判斷出[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]符合您企業的整合需要您應該先判斷訊息負載的 BizTalk 方案將會預期要處理的下一個項目。 這是一個重要的決策，因為不同版本的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]具有不同的向上延展及向外延展功能。  
  
 是執行負載測試以判斷最大持續輸送量 (MST)，以及最大持續性追蹤輸送量 (MSTT) 的 BizTalk 方案來判斷訊息載入的索引鍵。 如需有關如何測量最大持續輸送量和在一般的效能最佳做法的詳細資訊，請參閱[BizTalk Server 2009 效能指南](http://go.microsoft.com/fwlink/?LinkID=150492)(http://go.microsoft.com/fwlink/?LinkID=150492)。  
  
## <a name="planning-for-expansion"></a>規劃擴充  
 請考慮實作 BizTalk 方案使用 Enterprise edition 的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]如果您將新增大量的交易夥伴，將需要使用主機叢集，或將需要向外延展至多部電腦執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中BizTalk 群組。 Standard 和分支版本的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]無法調整多部電腦執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中群組或主機叢集。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [BizTalk Server 角色和責任](../technical-guides/biztalk-server-roles-and-responsibilities.md)  
  
-   [規劃 BizTalk Server 層](../technical-guides/planning-the-biztalk-server-tier.md)  
  
-   [規劃資料庫層](../technical-guides/planning-the-database-tier.md)  
  
-   [規劃開發、測試、臨時和生產環境](../technical-guides/planning-the-development-testing-staging-and-production-environments.md)