---
title: "在 SQL Server 中使用 SQL 配接器輪詢 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c31b3cda-c05e-46db-827b-6c47a53d1a3a
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d01bc3d004da60b98e0132aa3c8e04442a45426
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="polling-in-sql-server-using-the-sql-adapter"></a>在 SQL Server 中使用 SQL 配接器輪詢
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]可讓配接器用戶端接收 SQL Server 資料庫中的資料變更訊息。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]支援接收 「 輪詢基礎 」 的訊息執行指定的 SQL 陳述式 （SELECT 陳述式或預存程序），其中配接器會擷取或更新資料，並提供結果的固定間隔配接器用戶端時間。  
  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]公開輪詢的下列作業：  
  
-   **輪詢**： 可讓您接收的 SQL Server 資料表或檢視表的週期性的資料變更訊息。 訊息是不強型別。  
  
-   **TypedPolling**： 可讓您接收來自 SQL Server 資料庫的強型別的訊息。 如果您想要將輪詢訊息中的項目對應至任何其他結構描述，您必須使用這項作業。  
  
-   **XmlPolling**。 可讓您使用 SELECT 陳述式或預存程序，使用 FOR XML 子句，並傳回資料當做 XML 訊息。 此操作會傳回做為 XML 訊息的輪詢訊息。  
  
     如需有關 FOR XML 子句的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=131402](http://go.microsoft.com/fwlink/?LinkId=131402)。  
  
 如需有關在輪詢[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，請參閱[從 SQL Server 所使用的 BizTalk Server 收到輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-biztalk.md)。  
  
## <a name="polling"></a>輪詢  
 使用一般輪詢作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]牽涉到下列：  
  
1.  配接器用戶端必須指定`Polling`為中的輸入作業**InboundOperationType**繫結屬性。 這個繫結屬性的預設值是`Polling`。  
  
2.  配接器用戶端必須指定 SQL 陳述式**PolledDataAvailableStatement**繫結屬性，可判斷是否有資料可用來輪詢。 第一個傳回的結果集上執行此陳述式的第一個資料列的第一個資料行包含整數值。 如果不沒有可用於輪詢的任何資料，傳回值是 0 （零）。 如果沒有可用的資料，傳回值是小於或等於零。  
  
3.  配接器用戶端必須指定輪詢間隔**PollingIntervalInSeconds**內容繫結至定義的間隔中的陳述式**PolledDataAvailableStatement**繫結執行屬性。 在每個輪詢間隔結束時，輪詢的資料可用陳述式會執行，而且會傳回結果集。  
  
4.  配接器用戶端必須指定輪詢 SQL 陳述式 （SELECT 陳述式或預存程序） **PollingStatement**繫結屬性。 如果沒有資料可用於輪詢 (取決於**PolledDataAvailableStatement**繫結屬性)，配接器執行輪詢陳述式可以取得和更新 （如果適用） 的 SQL Server 資料庫中的資料。 當[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]搭配[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，相同的交易也會用來提交訊息至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  
  
5.  配接器用戶端可以使用**PollWhileDataFound**內容繫結至忽略的輪詢間隔，並持續輪詢資料，以及可用時。  
  
6.  由於執行輪詢陳述式會傳回結果集做為輸入的訊息傳送至配接器用戶端。  
  
> [!NOTE]
>  XmlPolling 作業牽涉到相同的步驟，以輪詢作業。  
  
## <a name="strongly-typed-polling"></a>強型別輪詢  
 使用一般的強型別輪詢作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]牽涉到下列：  
  
1.  配接器用戶端必須指定`TypedPolling`為中的輸入作業**InboundOperationType**繫結屬性。 這個繫結屬性的預設值是`Polling`。  
  
2.  配接器用戶端必須指定輸入的識別碼做為連線 URI 的一部分。 輸入的識別碼可能是任何字串，並附加至 TypedPolling 作業來避免命名空間發生衝突的標準的命名空間。  
  
3.  其餘的步驟會與步驟 2-6 列在上一節中說明的輪詢作業相同。  
  
 如需相關輪詢和強型別輪詢的繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
> [!NOTE]
>  執行輪詢陳述式的結果可以傳回多個結果集。 如果結果集未包含任何資料列，會不傳送任何訊息給配接器用戶端。  
  
 下圖提供資訊中的輪詢工作流程[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 輪詢工作流程的兩個案例說明：  
  
1.  當值**PollWhileDataFound**設為"False"（預設值）。  
  
2.  當值**PollWhileDataFound**設為"True"。  
  
 ![輪詢工作流程 &#40;PollWhileDataFound &#61;False &#41;] (../../adapters-and-accelerators/adapter-sql/media/15598c14-3a62-4b8d-90bf-84e004a386db.gif "15598c14-3a62-4b8d-90bf-84e004a386db") ![輪詢工作流程 &#40;PollWhileDataFound &#61;True &#41;] (../../adapters-and-accelerators/adapter-sql/media/c20535be-ea45-4456-8b62-4d4585cb1d8c.gif "c20535be-ea45-4456-8b62-4d4585cb1d8c")  
  
## <a name="differences-between-polling-and-query-notification"></a>查詢通知輪詢之間的差異  
 雖然輪詢和查詢通知是這兩個輸入的作業，而且配接器用戶端通知的 SQL Server 資料庫中的資料變更下, 表列出這兩者之間的一些差異。 下列差異，可協助您決定在針對作業，視您的需求而定：  
  
|輪詢|查詢通知|  
|-------------|------------------------|  
|輪詢配接器所起始。 執行陳述式，以驗證是否資料適用於輪詢，並以起始輪詢執行輪詢陳述式，如果某些資料可用於輪詢配接器。|查詢通知是由 SQL Server 啟動。 只在配接器發出的通知陳述式會指示資料庫在陳述式的結果集變更的情況下起始通知。|  
|您可以使用輪詢陳述式來讀取或更新 SQL Server 資料庫資料表中的資料。|您可以使用查詢通知陳述式只讀取 SQL Server 資料庫資料表中的資料。|  
|輪詢會通知您有關已變更的實際資料。|查詢通知只會告知的類型變更的資料，例如 Insert、 Update 和 Delete。|  
|輪詢間隔，取決於資料變更通知，配接器用戶端就會接到通知有關的資料變更每個輪詢間隔的結尾。 **提示：**輪詢可讓您更佳的輸送量持續發生資料變更並不想為每項變更，並發生時加以通知。 相反地，您可以指定的輪詢之後, 您想要發生的問題後的最後一個資料變更通知的所有變更的通知。|資料變更通知是在瞬間完成。|  
  
 如需有關在查詢通知[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]，請參閱[使用 BizTalk server 接收 SQL 查詢通知](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)