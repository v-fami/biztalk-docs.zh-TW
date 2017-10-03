---
title: "搭配 WCF 服務模型中使用 SQL 配接器的輪詢 SQL Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eef2e868-bd51-4393-b091-f67299b4759d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20d0ab576e5feddb0b5f3e867ca549a45bb2af97
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="poll-sql-server-using-the-sql-adapter-with-wcf-service-model"></a>搭配 WCF 服務模型中使用 SQL 配接器的輪詢 SQL Server
您可以設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]以接收來自 SQL Server 輪詢基礎資料變更的訊息。 您可以指定執行以輪詢資料庫配接器的輪詢陳述式。 輪詢陳述式可以是 SELECT 陳述式或預存程序會傳回結果集。 根據接收的輪詢訊息類型，則配接器會公開不同的輪詢作業：  
  
-   **輪詢**。 此操作會傳回資料集當做輪詢訊息的一部分。  
  
-   **TypedPolling**。 此操作會傳回強型別輪詢訊息。  
  
-   **XmlPolling**。 此操作會傳回做為 XML 訊息的輪詢訊息。 如果您想要使用 SELECT 陳述式或預存程序來傳回資料當做 XML 訊息中使用 FOR XML 子句，您必須使用這項作業。 [FOR XML 子句](https://docs.microsoft.com/sql/relational-databases/xml/for-xml-sql-server)提供詳細的資訊。 
  
 如需有關這些輪詢作業的詳細資訊，請參閱[在 SQL Server 中使用 SQL 配接器輪詢](../../adapters-and-accelerators/adapter-sql/polling-in-sql-server-using-the-sql-adapter.md)。  
  
> [!NOTE]
>  [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可讓配接器用戶端有具有相同的資料庫或資料表的多個輪詢或 TypedPolling 作業的單一應用程式。 為了支援這類案例中，配接器包含唯一識別碼 — **InboundID**— 在 連線 URI。 當加入連接 URI，這個識別碼可唯一的藉此讓單一應用程式中的多個輪詢作業。  
  
 此章節的主題提供有關如何在.NET 應用程式中使用輪詢和 TypedPolling 作業的指示。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [從 SQL Server 使用 WCF 服務模型收到輪詢基礎資料變更的訊息](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-a-wcf-service.md)  
  
-   [使用 WCF 服務模型的 SQL Server 從接收強型別輪詢基礎資料變更訊息](../../adapters-and-accelerators/adapter-sql/receive-strongly-typed-polling-based-data-changed-sql-messages-with-wcf-service.md)  
  
## <a name="see-also"></a>另請參閱  
[開發 SQL 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)