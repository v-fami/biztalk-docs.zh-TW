---
title: 了解 BizTalk Adapter for Oracle E-business Suite |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77a3f0a8-fc64-42cd-bb7c-0a6f527622e4
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ebf84eef3d5e1ec4730926dd34b6533e1a7491f8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980543"
---
# <a name="understand-biztalk-adapter-for-oracle-e-business-suite"></a>了解 BizTalk Adapter for Oracle E-business Suite
## <a name="biztalk-adapter-pack-features"></a>BizTalk Adapter Pack 功能
[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]啟用服務導向程式設計的存取，以便與外部系統進行互動。 配接器用戶端提供下列優點：  
  
- **一致的設計階段經驗**。 配接器會提供一般和方便使用的設計階段經驗，針對瀏覽、 搜尋和擷取的 LOB 成品的中繼資料。  
  
- **各種程式設計選項**。 配接器會提供各種程式設計模型，包括 Windows Communication Foundation (WCF) 通道模型，WCF 服務模型中，ADO.NET 中，Web 服務，或 BizTalk Server 支援的模型。  
  
- **統一的體驗，跨 Lob**。 使用 WCF 配接器將標準化和[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，並因此提供一致的體驗的任何 LOB 系統的存取。  
  
  如前所述，配接器是以 WCF LOB 配接器 SDK 為基礎。 WCF LOB 配接器 SDK 建置可取用各種不同的用戶端應用程式，例如 BizTalk Server 和 Microsoft Office 的整合配接器提供的通用基礎。 WCF LOB 配接器 SDK 公開為 Windows Communication Foundation (WCF) 通道的整合配接器會將對齊配接器策略，Microsoft 服務策略。 如需有關 WCF LOB 配接器 SDK 的詳細資訊，請參閱 < [WCF LOB 配接器 SDK 文件](../../adapters-and-accelerators/wcf-lob-adapter-sdk/microsoft-wcf-line-of-business-adapter-sdk-documentation.md)。

## <a name="overview-of-the-oracle-ebs-adapter"></a>Oracle EBS 配接器的概觀
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]公開為 WCF 服務的 Oracle E-business Suite。 配接器用戶端可以執行 Oracle E-business Suite 作業交換 SOAP 訊息的配接器。 配接器會使用 SOAP 訊息並執行作業的適當 ODP.NET 呼叫。 配接器從 Oracle E-business Suite 傳回回應傳回給用戶端的 SOAP 訊息格式。  
  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會顯示 Oracle E-business Suite 成品 （PL/SQL Api、 介面資料表/檢視表、 同時執行的程式，並要求集） 和基礎 Oracle 資料庫成品 （例如資料表、 函數和程序） 描述的中繼資料在表單的 Web 服務描述語言 (WSDL) 中的 SOAP 訊息的結構。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]會使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，和[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]讓配接器用戶端擷取作業的中繼資料。 配接器也會產生程式設計方案程式設計可用的成品。 如需詳細資訊[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]， [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]，並[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，請參閱[連接到 Oracle E-business Suite，在 Visual Studio 中](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-the-oracle-e-business-suite-in-visual-studio.md)。  
  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]使用.NET (ODP.NET) 11.1.0.7 Oracle 資料提供者與 Oracle E-business Suite 通訊。 ODP.NET 11.1.0.7 是 Oracle 資料存取元件 (ODAC) 的元件之一。 您可以使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]與 Oracle E-business Suite 通訊，以下列方式：  
  
- 開發 BizTalk 應用程式。 如需詳細資訊，請參閱 <<c0> [ 開發的 BizTalk Server 應用程式](../../core/developing-biztalk-server-applications.md)。  
  
- 使用[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]服務模型。 如需詳細資訊，請參閱 <<c0> [ 開發 Oracle 資料庫應用程式所使用的 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)。  
  
- 使用 WCF 通道模型。 如需詳細資訊，請參閱 <<c0> [ 開發 SQL 應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)。  

## <a name="access-to-oracle-e-business-suite"></a>Oracle E-business Suite 的存取
 若要執行 Oracle E-business Suite 作業，配接器用戶端必須存取相關的成品 Oracle E-business Suite 中。 外部應用程式可以新增或移除 Oracle E-business Suite 介面資料表和資料庫資料表中的資料，使用 SQL 陳述式。 應用程式也可以使用檢視、 函數和程序中存取介面資料表和資料庫資料表中的資料。 使用[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]，配接器用戶端可以瀏覽 Oracle E-business Suite 中的成品與基礎資料庫。 在 Oracle E-business Suite 中，配接器用戶端可以瀏覽介面資料表、 介面檢視、 同時執行的程式，並要求集，但基礎的 Oracle 資料庫中，配接器用戶端可以瀏覽資料表、 檢視、 預存程序、 函式，PL/SQL Api與套件。 配接器用戶端可以選取的成品，它們需要解決方案，並擷取這些構件的中繼資料。 這可讓使用者存取和 Oracle E-business Suite 和基礎的 Oracle 資料庫中執行的構件上的作業。  
  
 本節列出的功能[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]。  
  
## <a name="more-good-stuff"></a>更多實用功能  
  
-    [使用配接器連接到 Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-the-adapter.md)

- [瀏覽、 搜尋及取得 Oracle E-business Suite 中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-oracle-e-business-suite-metadata.md)

- [Oracle E-business Suite 配接器支援哪些作業](../../adapters-and-accelerators/adapter-oracle-ebs/what-operations-are-supported-by-the-oracle-e-business-suite-adapter.md)

- [使用 Oracle 資料庫配接器處理交易](../../adapters-and-accelerators/adapter-oracle-database/handle-transactions-with-the-oracle-database-adapter.md) 

- [Oracle EBS 配接器用戶端的功能](../../adapters-and-accelerators/adapter-oracle-ebs/features-for-oracle-ebs-adapter-clients.md) 

-   [BizTalk Adapter for Oracle E-business Suite 中的主要功能](../../adapters-and-accelerators/adapter-oracle-ebs/key-features-in-biztalk-adapter-for-oracle-e-business-suite.md)  
  
-   [BizTalk Adapter for Oracle E-business Suite 的限制](../../adapters-and-accelerators/adapter-oracle-ebs/limitations-of-biztalk-adapter-for-oracle-e-business-suite.md)  
  
## <a name="see-also"></a>另請參閱  
[開始使用](../../adapters-and-accelerators/adapter-oracle-ebs/get-started-with-the-biztalk-adapter-for-oracle-e-business-suite.md)