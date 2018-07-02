---
title: 使用 SQL 配接器與 BizTalk Server 輪詢 SQL Server |Microsoft Docs
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
ms.openlocfilehash: 971de39bff2149b1b6bdb5d20d6e8b721821a8ea
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996439"
---
# <a name="poll-sql-server-using-the-sql-adapter-with-biztalk-server"></a>使用 SQL 配接器與 BizTalk Server 輪詢 SQL Server
您可以設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]從 SQL Server 接收以輪詢為基礎的資料變更訊息。 您可以指定要輪詢的資料庫執行的配接器的輪詢陳述式。 輪詢陳述式可以是 SELECT 陳述式或預存程序會傳回結果集。 根據接收的輪詢訊息類型，則配接器會公開三種不同方式用於輪詢：  
  
- **輪詢**。 此操作會傳回資料集當做輪詢訊息的一部分。 在設計階段，您可能不提供要輪詢的資料庫物件的結構描述。 相反地，會提供結構描述執行階段期間，輪詢訊息的一部分。  
  
- **TypedPolling**。 這項作業會傳回強型別輪詢訊息。 在設計階段，也會提供資料庫物件的結構描述。 您必須使用這項作業輪詢，如果您想要將對應從輪詢訊息可能是另一項作業的另一個結構描述的特定項目。  
  
- **XmlPolling**。 這項作業會傳回做為 XML 訊息的輪詢訊息。 如果您想要使用 SELECT 陳述式或使用 FOR XML 子句來傳回資料做為 XML 訊息的預存程序，您必須使用這項作業。 如需有關 FOR XML 子句的詳細資訊，請參閱 < [FOR XML (SQL Server)](https://msdn.microsoft.com/library/ms178107.aspx)。 
  
  如需有關這些輪詢作業的詳細資訊，請參閱 <<c0> [ 輪詢支援](https://msdn.microsoft.com/library/dd788416.aspx)。  
  
> [!NOTE]
>  [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可讓配接器用戶端有相同的資料庫或資料表的一個以上的輪詢或 TypedPolling 作業的單一 BizTalk 應用程式。 若要支援此情況下，配接器包含唯一識別碼 — **InboundID**— 在 連線 URI。 當加入至 連線 URI，此識別碼可唯一的藉此讓多個在單一的 BizTalk 應用程式中的輪詢作業。  
  
 在本節中的主題提供有關如何使用 BizTalk 應用程式中的 輪詢、 TypedPolling 和 XmlPolling 的指示。 本章節也提供有關如何使用資訊**InboundID**連接屬性。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用 BizTalk Server 從 SQL Server 接收以輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-biztalk.md)  
  
-   [使用 BizTalk Server 從 SQL Server 接收強型別輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-sql/receive-strongly-typed-polling-based-data-changed-messages-from-sql-in-biztalk.md)  
  
-   [從使用 BizTalk Server 的 SQL 接收輪詢訊息使用 SELECT 陳述式與 FOR XML 子句](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-using-select-with-for-xml-clause-with-the-sql-adapter.md)  
  
-   [從使用 BizTalk Server 的 SQL 接收輪詢訊息跨多個接收埠](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-across-multiple-receive-ports-from-sql-using-biztalk.md)  
  
## <a name="see-also"></a>另請參閱  
[使用 SQL 配接器開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)