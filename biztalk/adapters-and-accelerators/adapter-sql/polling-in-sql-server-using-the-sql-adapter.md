---
title: 在使用 SQL 配接器的 SQL Server 中輪詢 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c31b3cda-c05e-46db-827b-6c47a53d1a3a
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73bb47bfd631576fe992ef072eee8ff3ff5ba5bf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967127"
---
# <a name="polling-in-sql-server-using-the-sql-adapter"></a>在使用 SQL 配接器的 SQL Server 中輪詢
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] 可讓配接器用戶端接收的 SQL Server 資料庫中的資料變更訊息。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]支援接收 「 以輪詢為基礎 」 的訊息執行指定的 SQL 陳述式 （SELECT 陳述式或預存程序），其中配接器擷取或更新資料，並提供給配接器用戶端的結果的固定間隔時間。  
  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]公開 （expose) 輪詢執行下列作業：  
  
- **輪詢**： 可讓您接收的 SQL Server 資料表或檢視表的定期的資料變更訊息。 訊息會不強型別。  
  
- **TypedPolling**： 可讓您接收的 SQL Server 資料庫中的強型別訊息。 如果您想要將輪詢訊息中的項目對應至任何其他的結構描述，您必須使用這項作業。  
  
- **XmlPolling**。 可讓您使用 SELECT 陳述式或預存程序，使用 FOR XML 子句，並傳回資料做為 XML 訊息。 這項作業會傳回做為 XML 訊息的輪詢訊息。  
  
   如需有關 FOR XML 子句的詳細資訊，請參閱 < [ http://go.microsoft.com/fwlink/?LinkId=131402 ](http://go.microsoft.com/fwlink/?LinkId=131402)。  
  
  如需有關在輪詢[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱 <<c2> [ 從 SQL Server 所使用的 BizTalk Server 接收輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-biztalk.md)。  
  
## <a name="polling"></a>輪詢  
 典型的輪詢作業使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]牽涉到下列：  
  
1. 配接器用戶端必須指定`Polling`中輸入作業**InboundOperationType**繫結屬性。 這個繫結屬性的預設值是`Polling`。  
  
2. 配接器用戶端必須指定的 SQL 陳述式**PolledDataAvailableStatement**繫結屬性，可決定是否有資料可供輪詢。 第一個傳回的結果集上執行此陳述式的第一個資料列的第一個資料行包含整數值。 如果沒有資料可供輪詢，則傳回值是 0 （零）。 如果沒有可用的資料，則傳回的值會是小於或等於零。  
  
3. 配接器用戶端必須指定輪詢間隔**PollingIntervalInSeconds**繫結屬性來定義的間隔時間中的陳述式**PolledDataAvailableStatement**繫結屬性會執行。 在每個輪詢間隔結束時，輪詢的資料提供陳述式會執行，而且會傳回結果集。  
  
4. 配接器用戶端必須指定輪詢 SQL 陳述式 （SELECT 陳述式或預存程序），如**PollingStatement**繫結屬性。 如果沒有資料可供輪詢 (取決於**PolledDataAvailableStatement**屬性繫結)，配接器執行輪詢陳述式來取得和更新 （如果適用） SQL Server 資料庫中的資料。 當[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]搭配[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，在同一個交易也會用來提交訊息至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
5. 配接器用戶端可以使用**PollWhileDataFound**忽略輪詢間隔，並持續輪詢資料，當有可用的屬性繫結。  
  
6. 結果集所傳回的結果執行輪詢陳述式會傳送至配接器用戶端，做為輸入的訊息。  
  
> [!NOTE]
>  XmlPolling 作業牽涉到相同的步驟，以輪詢作業。  
  
## <a name="strongly-typed-polling"></a>強型別輪詢  
 典型的強型別輪詢作業使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]牽涉到下列：  
  
1. 配接器用戶端必須指定`TypedPolling`中輸入作業**InboundOperationType**繫結屬性。 這個繫結屬性的預設值是`Polling`。  
  
2. 配接器用戶端必須指定輸入的識別碼，做為連線 URI 的一部分。 輸入的識別碼可能是任何字串，並附加至以避免命名空間衝突 TypedPolling 作業的標準命名空間。  
  
3. 其餘的步驟是相同的步驟 2 – 6 在上一節中所述的輪詢作業中所列。  
  
   如需與輪詢和強型別輪詢的繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
> [!NOTE]
>  由於執行輪詢陳述式可傳回多個結果集。 如果結果集未包含任何資料列，會不傳送任何訊息給配接器用戶端。  
  
 下圖提供資訊中的輪詢工作流程[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 說明的輪詢工作流程的兩個案例：  
  
1. 當 windows 7 **PollWhileDataFound**設為"False"（預設值）。  
  
2. 當 windows 7 **PollWhileDataFound**設為"True"。  
  
   ![輪詢工作流程&#40;PollWhileDataFound &#61; False&#41;](../../adapters-and-accelerators/adapter-sql/media/15598c14-3a62-4b8d-90bf-84e004a386db.gif "15598c14-3a62-4b8d-90bf-84e004a386db") ![輪詢工作流程&#40;PollWhileDataFound &#61; True&#41; ] (../../adapters-and-accelerators/adapter-sql/media/c20535be-ea45-4456-8b62-4d4585cb1d8c.gif "c20535be-ea45-4456-8b62-4d4585cb1d8c")  
  
## <a name="differences-between-polling-and-query-notification"></a>輪詢和查詢通知之間的差異  
 輪詢和查詢通知是兩個輸入的作業，而且有關 SQL Server 資料庫中的資料變更通知配接器用戶端，但下表列出兩者之間的一些差異。 下列差異將協助您決定的作業，視您的需求而定：  
  
|輪詢|查詢通知|  
|-------------|------------------------|  
|輪詢配接器所起始。 若要驗證是否可供輪詢，資料，並藉由執行輪詢陳述式，如果某些資料已可供輪詢起始輪詢陳述式執行配接器。|查詢通知是由 SQL Server 起始。 只在配接器發出的通知陳述式會指示要起始通知，萬一沒有陳述式的結果集變更的資料庫。|  
|您可以使用輪詢陳述式來讀取或更新 SQL Server 資料庫資料表中的資料。|您可以使用查詢通知的陳述式只讀取 SQL Server 資料庫資料表中的資料。|  
|輪詢會告知您已變更的實際資料。|查詢通知只會告知的類型變更的資料，例如 Insert、 Update 和 Delete。|  
|資料變更通知取決於輪詢間隔，以及配接器用戶端會通知有關的資料變更，每個輪詢間隔的結尾。 **提示：** 輪詢可讓您更佳的輸送量的資料變更會持續發生，並不想為每項變更並發生時收到通知。 相反地，您可以指定之後，您想要收到的最後一個資料變更通知之後發生的所有變更通知的輪詢間隔。|資料變更通知是在瞬間完成。|  
  
 如需詳細資訊中的查詢通知的相關[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]，請參閱 <<c2> [ 使用 BizTalk server 接收 SQL 查詢通知](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)