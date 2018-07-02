---
title: 規劃 BizTalk Server 環境 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e9ef0b4-eccb-47e2-bbb5-e859ffa0468c
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d92039b397053d24909d6ade75797c9f68d06172
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977735"
---
# <a name="planning-the-environment-for-biztalk-server"></a>規劃 BizTalk Server 環境
操作指南的規劃一節說明角色和相關聯的責任[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。 它包含規劃的應用程式和資料層的建議[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境中，它也提供計劃的建議版本 BizTalk 解決方案的管理階段。  
  
 跟您說： 進入時，「 如果您無法在計劃，您計劃失敗。 」 雖然一定有這個安全的建議的例外狀況，成功的生產環境的 BizTalk 解決方案的實作不是其中一個。 這個簡介主題規劃一節提供規劃您的 BizTalk 解決方案時，您應該做的決策的高階概觀。  
  
## <a name="deciding-whether-biztalk-server-is-the-right-tool-for-the-job"></a>決定 BizTalk Server 是否正在工作的正確工具  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可以視為 「 業務整合引擎。 」 基本上，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]旨在整合不同的商務系統、 處理序和訊息。 例如，商務系統交換訊息符合 EDI 標準可能需要整合商務系統交換符合 RosettaNet 標準的訊息。 或者，使用 SAP 的內部商務系統可能需要將資料儲存在 Microsoft SQL Server 資料庫的另一個內部商務系統與通訊。 或商務系統，可以只傳送或接收訊息使用 FTP 通訊協定可能需要與只能使用 HTTP 通訊協定的商務系統交換訊息。  
  
 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 配合這種不同的系統整合所做為訊息傳遞系統之間的中間人。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 支援各種不同的業界標準的傳輸通訊協定、 文件交換格式，以及企業營運應用程式。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 也提供功能強大的商務程序自動化功能，在 BizTalk 協調流程引擎。 您可以使用 BizTalk 協調流程設計師來建立商務程序，這可以內建在 BizTalk 協調流程引擎中執行的可執行程式碼的視覺表示法。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 也包含數個其他功能，幫助資訊工作者等商務活動監控 (BAM)，包括訊息的工作流程引擎、 商務規則引擎 」 (BRE) 和技術的企業整合。  
  
 如需使用詳細資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]商務程序管理功能，請參閱 <<c2> [ 技術白皮書： Microsoft 和 BPM-技術概觀](http://go.microsoft.com/fwlink/?LinkId=106015)(<http://go.microsoft.com/fwlink/?LinkId=106015>)。 若要深入了解 Microsoft 和優點而不是另一個已提供不同的整合技術，請參閱[了解 Microsoft 的整合技術](http://go.microsoft.com/fwlink/?LinkId=158452)(<http://go.microsoft.com/fwlink/?LinkId=158452>)。  
  
 特定的整合案例較適合於其他 Microsoft 產品。 如果您的主要焦點是在任何下列的案例時，請考慮使用這些 Microsoft 產品，而不是[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]:  
  
|**狀況**|**若要使用的產品**|  
|------------------|------------------------|  
|使用者佈建|**Microsoft Identity Lifecycle Manager 2010**<br /><br /> 如需有關 Microsoft Identity Lifecycle Manager 2010 的詳細資訊，請參閱 < [Microsoft Identity Lifecycle Manager 2010 FP1](http://go.microsoft.com/fwlink/?LinkId=204577) (http://go.microsoft.com/fwlink/?LinkId=204577)。|  
|系統之間的資料複寫|**SQL Server 複寫**<br /><br /> 如需有關 SQL Server 複寫的詳細資訊，請參閱 < [SQL Server 2008 R2 複寫](http://go.microsoft.com/fwlink/?LinkID=69978)(http://go.microsoft.com/fwlink/?LinkID=69978)。|  
|資料擷取、 轉換和載入 (ETL)|**SQL Server Integration Services (SSIS)**<br /><br /> 如需有關 SQL Server Integration Services 的詳細資訊，請參閱 < [SQL Server 2008 R2 Integration Services](http://go.microsoft.com/fwlink/?LinkId=152044) (http://go.microsoft.com/fwlink/?LinkId=152044)。|  
  
## <a name="deciding-which-edition-of-biztalk-server-is-right-for-the-job"></a>決定哪一個版本的 BizTalk Server 作業的權限  
 有四個不同版本 BizTalk Server 中，其中每個為目標的特定案例。 四個 BizTalk Server 版本包括：  
  
- **企業**-高容量、 可靠性和可用性的企業層級需求設計的客戶。  
  
- **標準**-專為一般磁碟區與部署規模需求的企業而設計。  
  
- **分支**-特殊版本[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專為中樞和支點部署案例包括 RFID。  
  
- **開發人員**-提供所有企業版的功能進行開發和測試用途，並可從 BizTalk Server 評估版，免費供評估之用。 安裝成評估版，BizTalk Server 將會運作 120 天。  
  
- **RFID 企業**-設計來提供可擴充、 可延伸的平台開發、 部署和管理各種 RFID 和感應器解決方案，包括 BizTalk RFID Server 與 BizTalk RFID Mobile。  
  
  如需有關 BizTalk Server 的不同版本的詳細資訊，請參閱[Microsoft BizTalk Server Edition](http://go.microsoft.com/fwlink/?LinkId=108051) (http://go.microsoft.com/fwlink/?LinkId=108051)。  
  
## <a name="planning-for-message-load"></a>規劃訊息負載  
 一旦您判斷出[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]符合您業務的整合需求，接下來，您應該判斷 BizTalk 解決方案的訊息負載預期處理。 這是一項重要決策，因為不同版本的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]有不同的相應增加和相應放大功能。  
  
 判斷訊息負載的關鍵在於來執行負載測試來判斷最大持續輸送量 (MST) 和最大持續性追蹤輸送量 (MSTT) 的 BizTalk 方案。 如需有關如何測量最大持續輸送量和一般的效能最佳做法的詳細資訊，請參閱 < [BizTalk Server 2009 效能指南](http://go.microsoft.com/fwlink/?LinkID=150492)(http://go.microsoft.com/fwlink/?LinkID=150492)。  
  
## <a name="planning-for-expansion"></a>規劃擴充  
 請考慮實作 BizTalk 方案，使用 Enterprise edition[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]如果您將新增大量的交易夥伴，將需要使用主機叢集，或將需要向外延展至多部電腦執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中BizTalk 群組。 標準版與 Branch 版的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]並不會滿足多部電腦執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中群組或主機叢集。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [BizTalk Server 角色和責任](../technical-guides/biztalk-server-roles-and-responsibilities.md)  
  
-   [規劃 BizTalk Server 層](../technical-guides/planning-the-biztalk-server-tier.md)  
  
-   [規劃資料庫層](../technical-guides/planning-the-database-tier.md)  
  
-   [規劃開發、測試、臨時和生產環境](../technical-guides/planning-the-development-testing-staging-and-production-environments.md)