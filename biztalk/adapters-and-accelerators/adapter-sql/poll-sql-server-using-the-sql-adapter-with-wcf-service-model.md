---
title: 使用 WCF 服務模型中的 SQL 配接器的輪詢 SQL Server |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eef2e868-bd51-4393-b091-f67299b4759d
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb3bbd42c732f3377c5823831b9507bbeb0c83bf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022308"
---
# <a name="poll-sql-server-using-the-sql-adapter-with-wcf-service-model"></a>使用 WCF 服務模型中的 SQL 配接器的輪詢 SQL Server
您可以設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]從 SQL Server 接收以輪詢為基礎的資料變更訊息。 您可以指定要輪詢的資料庫執行的配接器的輪詢陳述式。 輪詢陳述式可以是 SELECT 陳述式或預存程序會傳回結果集。 根據接收的輪詢訊息類型，則配接器會公開不同的輪詢作業：  
  
- **輪詢**。 此操作會傳回資料集當做輪詢訊息的一部分。  
  
- **TypedPolling**。 這項作業會傳回強型別輪詢訊息。  
  
- **XmlPolling**。 這項作業會傳回做為 XML 訊息的輪詢訊息。 如果您想要使用 SELECT 陳述式或使用 FOR XML 子句來傳回資料做為 XML 訊息的預存程序，您必須使用這項作業。 [FOR XML 子句](https://docs.microsoft.com/sql/relational-databases/xml/for-xml-sql-server)提供詳細的資訊。 
  
  如需有關這些輪詢作業的詳細資訊，請參閱 <<c0> [ 在使用 SQL 配接器的 SQL Server 中輪詢](../../adapters-and-accelerators/adapter-sql/polling-in-sql-server-using-the-sql-adapter.md)。  
  
> [!NOTE]
>  [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可讓配接器用戶端有一個以上的輪詢或 TypedPolling 作業的同一個資料庫或資料表的單一應用程式。 若要支援此情況下，配接器包含唯一識別碼 — **InboundID**— 在 連線 URI。 當加入至 連線 URI，此識別碼可唯一的藉此讓單一應用程式中的多個輪詢作業。  
  
 在本節中的主題提供有關如何使用.NET 應用程式中輪詢和 TypedPolling 作業的指示。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用 WCF 服務模型的 SQL Server 從接收以輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-a-wcf-service.md)  
  
-   [接收從 SQL Server 使用 WCF 服務模型的強型別輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-sql/receive-strongly-typed-polling-based-data-changed-sql-messages-with-wcf-service.md)  
  
## <a name="see-also"></a>另請參閱  
[開發 SQL 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)