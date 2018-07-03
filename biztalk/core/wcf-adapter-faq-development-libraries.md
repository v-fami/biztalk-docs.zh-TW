---
title: WCF 配接器 FAQ： 開發程式庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d05b635a-d46d-4f7d-896b-8ed7a799e80f
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45280a2cba918e68d0d27ab17c48dab5c2ffc7b2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011687"
---
# <a name="wcf-adapter-faq-development-libraries"></a>WCF 配接器 FAQ：開發程式庫
## <a name="when-does-it-make-more-sense-to-use-the-wcf-adapters-vs-a-wcf-custom-binding-to-communicate-with-an-external-application-or-system"></a>何時未比較合理使用 WCF 配接器與 WCF 自訂繫結與外部應用程式或系統進行通訊？  
 BizTalk Server WCF 配接器可促進使用 WCF 的 BizTalk Server 與整合外部系統的兩種新方式：  
  
- 您可以撰寫 WCF 用戶端/服務程式碼，並使用標準的 BizTalk Server WCF 配接器處理之間的通訊。  
  
- 或者，您可以使用.NET WCF framework 來開發新的自訂 WCF 繫結，並使用它來取代 WCF 配接器來處理之間的通訊。  
  
  使用 WCF 配接器與 BizTalk Server，您可以開發 WCF 用戶端程式碼，並呼叫 BizTalk Server 做為遠端的 WCF 服務，或您可以撰寫的 WCF 服務，並設定 BizTalk Server 將它公開為 WCF 服務。 替代方法是，您實際上可以撰寫全新自訂 WCF 繫結至處理之間的通訊。  
  
  寫入標準 WCF 用戶端或服務程式碼和撰寫的 WCF 自訂繫結項目時，透過標準的 BizTalk Server 配接器的優點是很難開發自訂的繫結。 產生 WCF 用戶端或服務存在於之外的 BizTalk Server 管理 （監視、 設定及部署） universe。 撰寫您自己的新自訂繫結和其使用 BizTalk WCF 自訂配接器裝載的優點是，它可以緊密整合至這些 BizTalk Server 管理函式。 與開發相關的基礎結構支援的繫結相關聯的成本是相當耗用更多資源比開發服務。  
  
  請務必了解這兩種方法可讓您整合內部的 BizTalk MessageBox 資料庫，以交易方式，以及可以提供類似的效能。 它是一個您想讓解決方案更複雜的決策。  
  
  使用 WCF 時您應該先嘗試撰寫的自訂服務和用戶端，並使用標準的 BizTalk WCF 配接器連接兩個。 .NET Framework 和 WCF 程式庫特別專如此可輕鬆使用這項工作。 若要建立 WCF 服務時，只要開發您的自訂介面、 設定適當的屬性，然後實作合約背後的程式碼。 WCF 會負責從中繼資料物件序列化的所有項目。 不必撰寫您的 WCF 服務您接著可以設定 WCF 配接器傳送埠透過一些簡單的步驟中的服務與服務通訊。 您甚至可以設定交易，讓新的服務可以參與異動的訊息交換，與內部 BizTalk MessageBox 資料庫。  
  
  在接收端，以便在網路上的接收位置看起來就像 WCF 服務一樣，可以設定 BizTalk Server。 可讓您撰寫規則的 WCF 用戶端程式碼，您甚至可以使用交易，當您呼叫該服務。 使用標準的 BizTalk WCF 配接器，因為 WCF 服務程式碼直接從 WCF 用戶端可設定橋接器是一種開發案例，是非常簡單的優點。 WCF 配接器至 BizTalk Server 提供高效能、 可交易橋接器，從 WCF 服務環境，以簡單的方式。  
  
  在 [摘要] 與外部系統，通訊可以撰寫 WCF 服務與外部系統互動，並再撰寫程式碼來直接與 WCF 服務交談，為您的問題較簡單的解決方案。 使用較複雜的方法，可以撰寫新的自訂繫結，並使用其中一個 WCF 自訂配接器更緊密的方式，比使用 WCF 服務的 BizTalk Server 與整合。 撰寫新的自訂繫結是較低層級和複雜的開發練習。 此方法的優點是，您會抵達緊密整合的解決方案的 BizTalk Server 管理、 設定及開發案例使用的地方一致地跨整個方案。 如果配接器的功能開發為外部的 WCF 用戶端和服務，設定必須是 BizTalk Server 環境之外，並因此沒有相關聯的基礎結構支援。  
  
## <a name="what-are-the-differences-between-the-wcf-adapters-and-the-adapters-in-the-biztalk-adapter-pack"></a>BizTalk Adapter Pack WCF 配接器和配接器之間的差異為何？  
 WCF 配接器是 BizTalk Server 版本標準的七個配接器：  
  
- WCF-Custom  
  
- WCF-CustomIsolated  
  
- WCF-NetTcp  
  
- WCF-BasicHttp  
  
- Wcf-wshttp  
  
- WCF-NetNamedPipe  
  
- WCF-NetMsmq  
  
  [BizTalk Adapter Pack](http://www.microsoft.com/biztalk/en/us/adapter-pack.aspx)是 post BizTalk Server 版本，提供單一的解決方案，可以輕鬆且安全地連接到的營運 (LOB) 資料從任何自訂開發.NET 應用程式，SQL Server 為基礎的商務智慧解決方案或 Office Business Application (OBA)。 此版本中提供的三個介面卡是 Siebel、 SAP 和 Oracle DB。 配接器組件授權是隨附於 BizTalk Server Developer、 Standard 和 Enterprise 版本，但不是隨附的新分支版本。 已購買 BizTalk Server 具有軟體保證的客戶也會有透過該計畫的 BizTalk 配接器套件的存取權。  
  
## <a name="what-is-the-recommended-order-for-deciding-to-use-the-biztalk-server-adapter-framework-the-wcf-lob-adapter-sdk-or-the-net-framework"></a>決定要使用 BizTalk Server 配接器架構、 WCF LOB 配接器 SDK 或.NET Framework 的建議的順序為何？  
 BizTalk 配接器架構是最慣用的選項，因為它不以標準.NET WCF 為基礎。 因為策略性解決方案應該包括 WCF 最有可能，執行這項操作的最佳方式為何？ 最簡單的選項，就是撰寫 WCF 用戶端和服務，並使用 WCF 配接器將其繫結在一起。 如果 BizTalk Server 外部程式，然後您可以撰寫以.NET Framework 的 WCF 自訂繫結。  
  
 唯一的時間會因為選項是如果您嘗試解決的大量中繼資料為中心的 LOB 整合問題選擇 WCF LOB 配接器 SDK。 WCF LOB 配接器 SDK 是只是另一個辦法建立 WCF 繫結，而其特製化的中繼資料支援。 此中繼資料需求的範例是當您正在與通訊的系統並沒有固定的一種文件。 BizTalk Server 傳送或接收的 XML 文件和中繼資料描述的文件中的資料版面配置，因此在目標系統可以使用它。  
  
## <a name="what-are-the-differences-between-the-biztalk-adapter-framework-and-the-wcf-lob-adapter-sdk"></a>BizTalk 配接器架構和 WCF LOB 配接器 SDK 之間的差異為何？  
 BizTalk 配接器架構用來建置自訂的 WCF 配接器，當標準的七個 WCF 配接器都不符合通訊需求。 配接器架構提供豐富的支援，以支援 LOB 應用程式，並共用的標準化的組態和標準 WCF 配接器所使用的管理方法的中繼資料。  
  
 WCF LOB 配接器 SDK 可讓您撰寫大量的中繼資料需求的目標系統的自訂繫結。 WCF LOB 配接器 SDK 的目標是為了方便統一開發可重複使用的中繼資料導向 WCF 架構配接器可讓企業應用程式和資料庫彼此整合。 包括自訂.NET 應用程式、 BizTalk Server、 Microsoft Office SharePoint® Server、 Microsoft SQL Server 整合的多個.NET 應用程式中使用 WCF LOB 配接器 SDK 產生的 WCF 繫結，因為可重複使用相同的開發的解決方案服務。 此外，WCF LOB 配接器 SDK 提供通用的中繼資料物件模型公開目標系統中繼資料，以瀏覽、 搜尋及擷取 WCF 配接器取用者合約從配接器。 您可以下載從 SDK [ http://go.microsoft.com/fwlink/?LinkID=96184 ](http://go.microsoft.com/fwlink/?LinkID=96184)。  
  
 雖然 BizTalk 配接器架構和 WCF LOB 配接器 SDK 有相似之處在於，它們可協助進行開發的自訂配接器，但有一些值得注意的差異：  
  
- WCF LOB 配接器 SDK 是較新版本，而且以.NET Framework 3.0 類別為依據。 像先前的 BizTalk 配接器架構中，它提供豐富的功能，對中繼資料處理和管理連線;不過，產生的配接器是未繫結至 BizTalk Server 架構中。  
  
- 使用 WCF LOB 配接器 SDK 來撰寫配接器會公開為自訂繫結，因此可供呼叫任何 WCF 用戶端應用程式。 它也可以擴充為 WCF 通道。 使用 BizTalk 配接器架構所撰寫的配接器可以呼叫只能由 BizTalk Server。  
  
  BizTalk 配接器架構沒有明確的開發工具支援。 WCF LOB 配接器 sdk，配接器的程式碼產生精靈會引導您完成一連串的步驟來收集各種不同的資訊需要自訂配接器使用，然後產生供您使用自訂配接器專案中的檔案。