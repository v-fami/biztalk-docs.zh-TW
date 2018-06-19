---
title: 與 BizTalk Server 使用 SQL 配接器的輪詢 SQL Server |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eef9a4b4-552d-4552-b318-1deab506bad9
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31e631a966ffee632e6c866a962c4fe47b2f1025
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223086"
---
# <a name="poll-sql-server-using-the-sql-adapter-with-biztalk-server"></a>與 BizTalk Server 使用 SQL 配接器的輪詢 SQL Server
您可以設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]以接收來自 SQL Server 輪詢基礎資料變更的訊息。 您可以指定執行以輪詢資料庫配接器的輪詢陳述式。 輪詢陳述式可以是 SELECT 陳述式或預存程序會傳回結果集。 根據接收的輪詢訊息類型，則配接器會公開輪詢的三種不同的方式：  
  
-   **輪詢**。 此操作會傳回資料集當做輪詢訊息的一部分。 在設計階段，輪詢之資料庫物件的結構描述無法使用。 相反地，會提供結構描述做為執行階段期間，輪詢訊息的一部分。  
  
-   **TypedPolling**。 此操作會傳回強型別輪詢訊息。 在設計階段，也會提供資料庫物件的結構描述。 您必須使用這項作業輪詢，如果您想要將對應從輪詢訊息可能是針對另一項作業的另一個結構描述的特定項目。  
  
-   **XmlPolling**。 此操作會傳回做為 XML 訊息的輪詢訊息。 如果您想要使用 SELECT 陳述式或預存程序來傳回資料當做 XML 訊息中使用 FOR XML 子句，您必須使用這項作業。 如需 FOR XML 子句的詳細資訊，請參閱[FOR XML (SQL Server)](https://msdn.microsoft.com/library/ms178107.aspx)。 
  
 如需有關這些輪詢作業的詳細資訊，請參閱[支援輪詢](https://msdn.microsoft.com/library/dd788416.aspx)。  
  
> [!NOTE]
>  [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可讓配接器用戶端安裝相同的資料庫或資料表的多個輪詢或 TypedPolling 作業了單一 BizTalk 應用程式。 為了支援這類案例中，配接器包含唯一識別碼 — **InboundID**— 在 連線 URI。 當加入連接 URI，這個識別碼可唯一的藉此讓單一的 BizTalk 應用程式中的多個輪詢作業。  
  
 本節中的主題提供有關如何使用輪詢、 TypedPolling 和 XmlPolling BizTalk 應用程式中的指示。 本章節也提供有關如何使用資訊**InboundID**連接屬性。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用 BizTalk Server 從 SQL Server 接收輪詢基礎資料變更的訊息](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-biztalk.md)  
  
-   [從 SQL Server 使用 BizTalk Server 接收強型別輪詢基礎資料變更訊息](../../adapters-and-accelerators/adapter-sql/receive-strongly-typed-polling-based-data-changed-messages-from-sql-in-biztalk.md)  
  
-   [使用 BizTalk Server sql 接收輪詢訊息使用 SELECT 陳述式與 FOR XML 子句](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-using-select-with-for-xml-clause-with-the-sql-adapter.md)  
  
-   [使用 BizTalk Server sql 接收輪詢訊息跨多個接收埠](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-across-multiple-receive-ports-from-sql-using-biztalk.md)  
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)