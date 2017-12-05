---
title: "WCF 配接器 FAQ： 開發程式庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d05b635a-d46d-4f7d-896b-8ed7a799e80f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0676403e4fa13df5547bc518666a2e648b181fcb
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="wcf-adapter-faq-development-libraries"></a>WCF 配接器 FAQ：開發程式庫
## <a name="when-does-it-make-more-sense-to-use-the-wcf-adapters-vs-a-wcf-custom-binding-to-communicate-with-an-external-application-or-system"></a>何時它會做更多的意義上，使用與外部應用程式或系統進行通訊的 WCF 配接器與 WCF 自訂繫結？  
 BizTalk Server WCF 配接器促進使用 WCF 的 BizTalk Server 外部系統整合的兩種新方式：  
  
-   您可以撰寫 WCF 用戶端/服務程式碼，並使用標準的 BizTalk Server WCF 配接器處理之間的通訊。  
  
-   或者您可以使用.NET WCF framework 來開發新的自訂 WCF 繫結，並使用它來取代 WCF 配接器來處理之間的通訊。  
  
 使用 WCF 配接器與 BizTalk Server，您可以開發 WCF 用戶端程式碼，並呼叫 BizTalk Server 做為遠端的 WCF 服務，或您可以撰寫 WCF 服務和設定 BizTalk Server 將它公開為 WCF 服務。 替代方案是，您實際上無法撰寫的全新自訂 WCF 繫結處理之間的通訊。  
  
 寫入標準 WCF 用戶端或服務程式碼和撰寫 WCF 自訂繫結項目使用標準的 BizTalk Server 配接器的優點是更難開發自訂的繫結。 產生 WCF 用戶端或服務存在於之外，BizTalk Server 管理 （監視、 設定及部署） universe。 撰寫您自己的新自訂繫結和裝載使用 BizTalk WCF 自訂配接器的優點是，它可以緊密整合至這些 BizTalk Server 管理函式。 與開發方面的基礎結構支援的繫結相關聯的成本相當多的成本會比與開發服務。  
  
 請務必了解這兩種方法提供您一個機會以交易方式整合內部的 BizTalk MessageBox 資料庫，並提供類似的效能。 它是更決定您想讓解決方案更多複雜。  
  
 使用 WCF 時您應該先嘗試撰寫自訂的服務和用戶端，並使用標準的 BizTalk WCF 配接器連接兩個。 .NET Framework 和 WCF 程式庫特別針對進行這項工作更容易。 若要建立 WCF 服務時，只要開發您的自訂介面、 設定適當的屬性，並實作合約背後的程式碼。 WCF 會負責從中繼資料物件序列化的所有項目。 不必撰寫您的 WCF 服務您接著可以設定 WCF 配接器透過傳送埠與幾個簡單步驟中的服務。 您甚至可以設定交易，讓新的服務可以參與交易的訊息交換，與內部 BizTalk MessageBox 資料庫。  
  
 在接收端，以便在網路上的接收位置看起來就像 WCF 服務一樣，可以設定 BizTalk Server。 可讓您撰寫正常的 WCF 用戶端程式碼，您甚至可以使用交易，當您呼叫該服務。 直接從 WCF 用戶端可設定橋接器，WCF 服務程式碼為使用標準的 BizTalk WCF 配接器的優點是非常簡單開發劇本。 WCF 配接器至 BizTalk Server 提供高效能、 可交易橋接器，從 WCF 服務環境，以簡單的方式。  
  
 在 [摘要] 與外部系統，通訊可以撰寫 WCF 服務與外部系統互動，，然後撰寫程式碼來直接與 WCF 服務溝通，做為更簡單的解決方案，您的問題。 您可以使用更複雜的方式，撰寫新的自訂繫結並整合 BizTalk Server 使用其中一個 WCF 自訂配接器使用 WCF 服務以比更嚴格的方式。 撰寫新的自訂繫結是較低層級和複雜開發工作。 這個方法的優點是，您會抵達緊密整合的解決方案，BizTalk Server 管理、 設定及開發劇本正在使用一致的方式跨整個方案。 如果為外部的 WCF 用戶端和服務開發配接器功能時，組態必須是 BizTalk Server 環境之外，並因此沒有相關聯的基礎結構支援。  
  
## <a name="what-are-the-differences-between-the-wcf-adapters-and-the-adapters-in-the-biztalk-adapter-pack"></a>BizTalk Adapter Pack 中的 WCF 配接器和配接器之間的差異為何？  
 WCF 配接器是 BizTalk Server 版本標準的七個配接器：  
  
-   WCF-Custom  
  
-   WCF-CustomIsolated  
  
-   WCF-NetTcp  
  
-   WCF-BasicHttp  
  
-   Wcf-wshttp  
  
-   WCF-NetNamedPipe  
  
-   WCF-NetMsmq  
  
 [BizTalk Adapter Pack](http://www.microsoft.com/biztalk/en/us/adapter-pack.aspx)是提供單一輕鬆安全地連接到的特定業務 (LOB) 資料從任何自訂開發.NET 應用程式，SQL Server 為基礎的商務方案的 post BizTalk Server 版本智慧方案或 Office 商務應用程式 (OBA)。 此版本中提供三個介面卡是 Siebel、 SAP、 和 Oracle 資料庫。 配接器組件授權隨附於 BizTalk Server Developer、 Standard 和 Enterprise 版本，但不含 Branch edition。 已購買的軟體保證的 BizTalk Server 的客戶也會有存取 BizTalk 配接器封包，透過該計畫。  
  
## <a name="what-is-the-recommended-order-for-deciding-to-use-the-biztalk-server-adapter-framework-the-wcf-lob-adapter-sdk-or-the-net-framework"></a>決定要使用 BizTalk Server 配接器架構、 WCF LOB 配接器 SDK 或.NET Framework 的建議的順序為何？  
 BizTalk 配接器架構會是最慣用的選項，因為它不以標準.NET WCF 為基礎。 因為策略性方案應該包括 WCF 最有可能，若要這樣做的最佳方式為何？ 最簡單的選項，就是撰寫 WCF 用戶端和服務，然後將它們結合在一起使用的 WCF 配接器。 如果 BizTalk Server 外部程式，然後您可以撰寫以.NET Framework 的 WCF 自訂繫結。  
  
 唯一的時間會因為選項是如果您嘗試解決大量中繼資料為中心的 LOB 整合問題選擇 WCF LOB 配接器 SDK。 WCF LOB 配接器 SDK 建立的 WCF 繫結，只是另一個方式，而其特製化的中繼資料支援。 此中繼資料要求的範例時，您通訊的系統並沒有固定的一種文件。 BizTalk Server 傳送或接收的 XML 文件和中繼資料描述的文件中的資料配置，因此在目標系統可以使用它。  
  
## <a name="what-are-the-differences-between-the-biztalk-adapter-framework-and-the-wcf-lob-adapter-sdk"></a>BizTalk 配接器架構和 WCF LOB 配接器 SDK 之間的差異為何？  
 BizTalk 配接器架構用來建置自訂的 WCF 配接器時的七個標準 WCF 配接器都不符合通訊需求。 配接器架構提供了豐富的支援，以支援 LOB 應用程式，並共用的標準化的組態和標準 WCF 配接器所使用的管理方法的中繼資料。  
  
 WCF LOB 配接器 SDK 可讓您撰寫大量的中繼資料需求的目標系統的自訂繫結。 WCF LOB Adapter SDK 的目標是加速統一開發的可重複使用的中繼資料導向 WCF 配接器可讓企業應用程式和資料庫彼此整合。 包括自訂.NET 應用程式、 BizTalk Server、 Microsoft Office SharePoint （) Server、 Microsoft SQL Server 整合的多個.NET 應用程式中使用 WCF LOB 配接器 SDK 會產生 WCF 繫結，因為可重複使用相同開發的方案服務。 此外，WCF LOB 配接器 SDK 提供通用的中繼資料物件模型公開目標系統中繼資料，以瀏覽、 搜尋及擷取 WCF 配接器取用者合約從配接器。 您可以下載從 SDK [http://go.microsoft.com/fwlink/?LinkID=96184](http://go.microsoft.com/fwlink/?LinkID=96184)。  
  
 雖然 BizTalk 配接器架構和 WCF LOB 配接器 SDK 有相似之處，在於它們可協助進行開發的自訂配接器，有一些值得注意的差異：  
  
-   WCF LOB 配接器 SDK 是較新版本，並根據.NET Framework 3.0 類別。 如同舊版的 BizTalk 配接器架構它可提供豐富的功能，對中繼資料處理和管理連線;不過，產生的配接器是未繫結至 BizTalk Server 架構中。  
  
-   使用 WCF LOB 配接器 SDK 所撰寫的配接器會公開為自訂繫結，因此可由任何 WCF 用戶端應用程式呼叫。 它也可以擴充成為 WCF 通道。 使用 BizTalk 配接器架構所撰寫的配接器可以呼叫只能由 BizTalk Server。  
  
 BizTalk 配接器架構沒有明確的開發工具支援。 WCF LOB 配接器 sdk，配接器程式碼產生精靈會引導您透過一系列的步驟來收集各種資訊的自訂配接器必須使用，然後產生讓您使用自訂配接器專案中的檔案。