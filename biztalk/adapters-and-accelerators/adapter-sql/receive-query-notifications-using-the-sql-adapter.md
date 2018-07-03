---
title: 接收查詢通知使用 SQL 配接器 |Microsoft Docs
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
ms.openlocfilehash: 786bbf556acb3a30e652a7ecb29723f40566cb06
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999743"
---
# <a name="receive-query-notifications-using-the-sql-adapter"></a>接收查詢通知使用 SQL 配接器
配接器用戶端可以訂閱以接收 SQL Server 資料庫中的資料變更的查詢通知。 SQL SELECT 陳述式或預存程序指定的資料變更準則的查詢通知中，觸發表格中和 SQL Server 會傳送做為查詢通知，當結果集的 SELECT 陳述式或預存程序變更。  
  
> [!IMPORTANT]
>  若要支援查詢通知，配接器用戶端和 SQL Server 資料庫必須符合特定需求。 有關這些需求的詳細資訊，請參閱 < 啟用查詢通知 >，網址[ http://go.microsoft.com/fwlink/?LinkID=122323 ](http://go.microsoft.com/fwlink/?LinkID=122323)。  
  
 典型的查詢通知涉及下列工作：  
  
- 配接器用戶端必須指定`Notification`中輸入作業**InboundOperationType**繫結屬性。 這個繫結屬性的預設值是`Polling`。  
  
- 配接器用戶端必須指定 SQL 陳述式中的查詢通知註冊**NotificationStatement**繫結屬性。 配接器用戶端從 SQL Server 取得通知，因為結果為指定的 SQL 陳述式變更。  
  
  > [!IMPORTANT]
  >  若要接收通知，通知訂用帳戶的 SQL 陳述式*必須*符合特定準則。 如需可用於查詢通知的 SQL 陳述式的資訊，請參閱[ http://go.microsoft.com/fwlink/?LinkId=122160 ](http://go.microsoft.com/fwlink/?LinkId=122160)。  
  
- 配接器用戶端必須指定是否配接器傳送通知給配接器用戶端，以啟動接聽程式**NotifyOnListenerStart**繫結屬性。  
  
- 通知會傳送至配接器用戶端，做為並結果集的 SQL 陳述式中指定**NotificationStatement**繫結屬性變更。  
  
  如需有關這些繫結屬性的詳細資訊，請參閱 <<c0> [ 了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。  
  
> [!NOTE]
>  通知訂閱總是被認可，不論陳述式已執行的交易已認可或回復。 因此，通知作業可能會保證已變更的通知訂閱查詢的結果。 例如，假設資料插入資料表中的資料列 （通知訂閱） 交易，並立即傳送通知給通知變更 （插入） 相關的配接器。 由於某些原因，交易會回復，且有效地沒有資料會插入至資料表資料列。 不過，SQL Server 不會傳送通知給配接器相關的交易回復。 SQL Server 中的查詢通知的相關資訊，請參閱[ http://go.microsoft.com/fwlink/?LinkId=145367 ](http://go.microsoft.com/fwlink/?LinkId=145367)。  
  
## <a name="differences-between-query-notification-and-polling"></a>查詢通知和輪詢之間的差異  
 查詢通知和輪詢是這兩個輸入的作業，而且有關 SQL Server 資料庫中的資料變更通知配接器用戶端，但下表列出兩者之間的一些差異。 下列差異將協助您決定的作業，視您的需求而定：  
  
|查詢通知|輪詢|  
|------------------------|-------------|  
|查詢通知是由 SQL Server 起始。 只在配接器發出的通知陳述式會指示要起始通知，萬一沒有陳述式的結果集變更的資料庫。|輪詢配接器所起始。 若要驗證是否可供輪詢，資料，並藉由執行輪詢陳述式，如果某些資料已可供輪詢起始輪詢陳述式執行配接器。|  
|您可以使用查詢通知的陳述式只讀取 SQL Server 資料庫資料表中的資料。|您可以使用輪詢陳述式來讀取或更新 SQL Server 資料庫資料表中的資料。|  
|查詢通知只會通知的類型變更的資料，例如 Insert、 Update 和 Delete。|輪詢會告知您已變更的實際資料。|  
|資料變更通知是在瞬間完成。|資料變更通知取決於輪詢間隔，以及配接器用戶端會通知有關的資料變更，每個輪詢間隔的結尾。 **提示：** 輪詢可讓您更佳的輸送量的資料變更會持續發生，並不想為每項變更並發生時收到通知。 相反地，您可以指定之後，您想要的上次變更通知，因為發生錯誤的所有變更的通知的輪詢間隔。|  
  
 如需詳細資訊中的查詢通知的相關[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]，請參閱 <<c2> [ 使用 BizTalk server 接收 SQL 查詢通知](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)