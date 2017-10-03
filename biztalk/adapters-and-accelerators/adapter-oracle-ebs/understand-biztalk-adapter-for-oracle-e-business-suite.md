---
title: "瞭解 BizTalk Adapter for Oracle E-business Suite |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77a3f0a8-fc64-42cd-bb7c-0a6f527622e4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1fa12862600cd1d1d5661e278b87c82cc45697b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="understand-biztalk-adapter-for-oracle-e-business-suite"></a>瞭解 BizTalk Adapter for Oracle E-business Suite
## <a name="biztalk-adapter-pack-features"></a>BizTalk Adapter Pack 功能
[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]啟用服務導向程式設計的存取，以便與外部系統互動。 配接器用戶端提供下列優點：  
  
-   **一致的設計階段經驗**。 配接器會提供一般和使用者易記的設計階段經驗，針對瀏覽、 搜尋和擷取的 LOB 成品的中繼資料。  
  
-   **各種程式設計選項**。 配接器提供選擇的程式設計模型包括 Windows Communication Foundation (WCF) 通道模型，WCF 服務模型中，ADO.NET 中，Web 服務，或 BizTalk Server 支援模型。  
  
-   **跨 Lob 統一經驗**。 標準化使用 WCF 配接器和[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，並因此提供一致的體驗的任何 LOB 系統的存取。  
  
 如所述，配接器會建立最上層的[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 此 SDK 提供通用的基礎建置各種 BizTalk Server 和 Microsoft Office 等用戶端應用程式可以取用的整合配接器。 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]對齊由公開為 WCF 通道整合配接器的 Microsoft 服務策略配接器的策略。 如需有關[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，請參閱[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]文件。 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]連同安裝文件[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]通常下\<*安裝磁碟機*>: \Program Files\\[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]\Documents。  

## <a name="overview-of-the-oracle-ebs-adapter"></a>Oracle EBS 配接器的概觀
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]公開為 WCF 服務的 Oracle E-business Suite。 配接器用戶端可以執行 Oracle E-business suite 作業交換 SOAP 訊息的配接器。 配接器會使用 SOAP 訊息，並會適當 ODP.NET 呼叫，以執行此作業。 配接器從 Oracle E-business Suite 傳回回應傳回給用戶端的 SOAP 訊息格式。  
  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]顯示 Oracle E-business Suite 成品 （PL/SQL 應用程式開發介面，介面資料表/檢視表、 並行程式和要求） 和基礎 Oracle 資料庫成品 （例如資料表、 函數和程序） 會描述中繼資料在表單的 Web 服務描述語言 (WSDL) 中的 SOAP 訊息的結構。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]讓配接器用戶端擷取作業的中繼資料。 配接器也會產生可使用的程式設計成品程式設計方案中。 如需有關[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，請參閱[連接到 Visual Studio 中的 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)。  
  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用.NET (ODP.NET) 11.1.0.7 Oracle 資料提供者與 Oracle E-business Suite 通訊。 ODP.NET 11.1.0.7 是其中一個元件的 Oracle 資料存取元件 (ODAC)。 您可以使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]與 Oracle E-business Suite 通訊以下列方式：  
  
-   開發 BizTalk 應用程式。 如需詳細資訊，請參閱[開發 BizTalk Server 應用程式](../../core/developing-biztalk-server-applications.md)。  
  
-   使用[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]服務模型。 如需詳細資訊，請參閱[開發 Oracle 資料庫應用程式所使用的 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)。  
  
-   使用 WCF 通道模型。 如需詳細資訊，請參閱[開發 SQL 應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)。  

## <a name="access-to-oracle-e-business-suite"></a>Oracle E-business Suite 存取
 若要執行 Oracle E-business Suite 作業，配接器用戶端必須存取相關的成品 Oracle E-business Suite 中。 外部應用程式可以新增或移除 Oracle E-business Suite 介面資料表和資料庫資料表中的資料，使用 SQL 陳述式。 應用程式也可以使用檢視、 函數和程序中存取介面資料表和資料庫資料表中的資料。 與[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]，配接器用戶端可以瀏覽 Oracle E-business Suite 中的成品，如基礎資料庫中一樣。 在 Oracle E-business Suite 中，配接器用戶端可以瀏覽介面資料表、 檢視介面、 並行程式，並要求基礎的 Oracle 資料庫中的設定時，配接器用戶端可以瀏覽資料表、 檢視、 預存程序、 函數、 PL/SQL 應用程式開發介面和封裝。 配接器用戶端可以選取他們為其方案所需，並擷取中繼資料，這些成品的成品。 這可讓使用者存取，並在 Oracle E-business Suite 和基礎的 Oracle 資料庫中執行之成品的作業。  
  
 此區段會列出的功能[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]。  
  
## <a name="more-good-stuff"></a>更多實用功能  
  
-    [連接到 Oracle E-business Suite 使用配接器](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-the-adapter.md)

- [瀏覽、 搜尋和取得 Oracle E-business Suite 中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-oracle-e-business-suite-metadata.md)

- [Oracle E-business Suite 配接器支援哪些作業](../../adapters-and-accelerators/adapter-oracle-ebs/what-operations-are-supported-by-the-oracle-e-business-suite-adapter.md)

- [處理與 Oracle 資料庫配接器的交易](../../adapters-and-accelerators/adapter-oracle-database/handle-transactions-with-the-oracle-database-adapter.md) 

- [Oracle EBS 配接器用戶端的功能](../../adapters-and-accelerators/adapter-oracle-ebs/features-for-oracle-ebs-adapter-clients.md) 

-   [BizTalk Adapter for Oracle E-business Suite 中的重要功能](../../adapters-and-accelerators/adapter-oracle-ebs/key-features-in-biztalk-adapter-for-oracle-e-business-suite.md)  
  
-   [BizTalk adapter for Oracle E-business Suite 的限制](../../adapters-and-accelerators/adapter-oracle-ebs/limitations-of-biztalk-adapter-for-oracle-e-business-suite.md)  
  
## <a name="see-also"></a>另請參閱  
[開始使用](../../adapters-and-accelerators/adapter-oracle-ebs/get-started-with-the-biztalk-adapter-for-oracle-e-business-suite.md)