---
title: "BizTalk Adapter for Oracle 資料庫的概觀 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapter, overview
- ODP.NET
- Oracle Data Provider for .NET 2.0
ms.assetid: 852b8f82-ab34-45b8-ad7f-263d719a87f9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b874b5523256342a4e8ae14b2c475ede11fe279
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="overview-of-biztalk-adapter-for-oracle-database"></a>BizTalk Adapter for Oracle 資料庫的概觀
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]公開為 WCF 服務的 Oracle 資料庫。 配接器用戶端可以交換 SOAP 訊息的配接器所執行的 Oracle 資料庫上的作業。 配接器取用 WCF 訊息，並會適當 ODP.NET 呼叫，以執行此作業。 配接器會傳回回應從 Oracle 資料庫中的 SOAP 訊息形式的用戶端。  
  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]表面的中繼資料的 Oracle 資料庫成品 （資料表、 函數、 程序等） 描述結構的 SOAP 訊息中 WSDL 的形式。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]， [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，和[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]讓配接器用戶端擷取作業的中繼資料，並產生可使用的程式設計成品程式設計方案中。  
  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用 Oracle Data Provider for.NET (ODP.NET) 來與 Oracle 資料庫通訊。 您可以使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]以下列方式與 Oracle 資料庫通訊：  
  
-   開發 BizTalk 應用程式。 請參閱[開發 BizTalk 應用程式](../../core/develop-your-biztalk-applications.md)如需詳細資訊。  
  
-   使用[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]服務模型。 請參閱[開發 Oracle 資料庫應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)如需詳細資訊。  
  
-   使用 WCF 通道模型。 請參閱[開發 Oracle 資料庫應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)如需詳細資訊。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [配接器如何連接到 Oracle 資料庫？](https://msdn.microsoft.com/library/cc185360(v=bts.10).aspx)  
  
-   [配接器介面 Oracle 中繼資料的運作方式](https://msdn.microsoft.com/library/cc185310(v=bts.10).aspx)  
  
-   [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185259(v=bts.10).aspx)  
  
-   [配接器處理交易的運作方式](https://msdn.microsoft.com/library/dd788428.aspx)  
  
-   [Oracle 資料庫中的 LOB 資料類型的串流支援](../../adapters-and-accelerators/adapter-oracle-database/streaming-support-for-lob-data-types-in-oracle-database.md)  
  
-   [Oracle 資料庫配接器支援哪些作業](../../adapters-and-accelerators/adapter-oracle-database/what-operations-are-supported-by-the-oracle-database-adapter.md)  
  
## <a name="see-also"></a>另請參閱  
 [瞭解 Biztalk Adapter for Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/understand-the-biztalk-adapter-for-oracle-database.md)