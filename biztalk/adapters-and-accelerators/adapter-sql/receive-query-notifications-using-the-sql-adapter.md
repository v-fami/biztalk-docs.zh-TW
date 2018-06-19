---
title: 接收查詢通知使用 SQL 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6b2ed0f0-d005-4eec-b1a6-97a0c94678dc
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37d333a2248c943d1d404aa086565ae4b1662226
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224502"
---
# <a name="receive-query-notifications-using-the-sql-adapter"></a>接收查詢通知使用 SQL 配接器
配接器用戶端可以接收 SQL Server 資料庫中的資料變更的查詢通知訂閱。 SQL SELECT 陳述式或預存程序指定的資料變更準則，用於觸發的查詢通知，資料表中和 SQL Server 會傳送做為查詢通知，當結果集的 SELECT 陳述式或預存程序變更。  
  
> [!IMPORTANT]
>  若要支援查詢通知，配接器用戶端和 SQL Server 資料庫必須符合特定需求。 有關這些需求的詳細資訊，請參閱 「 啟用查詢通知 」，網址[http://go.microsoft.com/fwlink/?LinkID=122323](http://go.microsoft.com/fwlink/?LinkID=122323)。  
  
 一般查詢通知涉及下列作業：  
  
-   配接器用戶端必須指定`Notification`為中的輸入作業**InboundOperationType**繫結屬性。 這個繫結屬性的預設值是`Polling`。  
  
-   配接器用戶端必須指定 SQL 陳述式中的查詢通知註冊**NotificationStatement**繫結屬性。 配接器用戶端會從 SQL Server 取得通知的結果集為指定的 SQL 陳述式變更為。  
  
    > [!IMPORTANT]
    >  若要接收通知，通知訂閱的 SQL 陳述式*必須*符合特定準則。 可用於查詢通知的 SQL 陳述式的相關資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=122160](http://go.microsoft.com/fwlink/?LinkId=122160)。  
  
-   配接器用戶端必須指定是否配接器傳送通知給配接器用戶端以啟動接聽程式之後儘速**NotifyOnListenerStart**繫結屬性。  
  
-   通知會傳送至配接器用戶端並時的結果集的 SQL 陳述式中指定**NotificationStatement**繫結屬性已變更。  
  
 如需有關這些繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
> [!NOTE]
>  通知訂閱一律是認可，不論陳述式已執行的交易已認可或回復。 因此，通知作業可能會保證針對通知訂閱查詢的結果已變更。 例如，假設資料插入資料表中的資料列 （通知訂閱） 交易，並立即傳送通知給變更 （插入） 相關的配接器通知。 由於某些原因，交易回復，並有效地任何資料插入資料表資料列。 不過，SQL Server 不會傳送通知給配接器有關交易回復。 SQL Server 中的查詢通知的相關資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=145367](http://go.microsoft.com/fwlink/?LinkId=145367)。  
  
## <a name="differences-between-query-notification-and-polling"></a>查詢通知和輪詢之間的差異  
 查詢通知輪詢都是這兩個輸入的作業，且 SQL Server 資料庫中的資料變更通知配接器用戶端，但下表列出這兩者之間的一些差異。 下列差異，可協助您決定在針對作業，視您的需求而定：  
  
|查詢通知|輪詢|  
|------------------------|-------------|  
|查詢通知是由 SQL Server 啟動。 只在配接器發出的通知陳述式會指示資料庫在陳述式的結果集變更的情況下起始通知。|輪詢配接器所起始。 執行陳述式，以驗證是否資料適用於輪詢，並以起始輪詢執行輪詢陳述式，如果某些資料可用於輪詢配接器。|  
|您可以使用查詢通知陳述式只讀取 SQL Server 資料庫資料表中的資料。|您可以使用輪詢陳述式來讀取或更新 SQL Server 資料庫資料表中的資料。|  
|查詢通知僅告知的類型變更的資料，例如 Insert、 Update 和 Delete。|輪詢會通知您有關已變更的實際資料。|  
|資料變更通知是在瞬間完成。|輪詢間隔，取決於資料變更通知，配接器用戶端就會接到通知有關的資料變更每個輪詢間隔的結尾。 **提示：** 輪詢可讓您更佳的輸送量持續發生資料變更並不想為每項變更，並發生時加以通知。 相反地，您可以指定您要在其後發生是因為最後一個變更通知的所有變更的通知輪詢間隔。|  
  
 如需有關在查詢通知[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]，請參閱[使用 BizTalk server 接收 SQL 查詢通知](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)