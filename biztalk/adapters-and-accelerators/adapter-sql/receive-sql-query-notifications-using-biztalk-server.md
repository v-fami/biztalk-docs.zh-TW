---
title: 接收 SQL 查詢通知使用 BizTalk Server |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 69444df7-f2ae-4d1a-9b49-817b437517d8
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1cc8174db5193702e512f5f8b01c2a8ecfbeeee5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988887"
---
# <a name="receive-sql-query-notifications-using-biztalk-server"></a>接收使用 BizTalk Server 的 SQL 查詢通知
您可以設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]接收通知訊息的 SQL Server 資料表或檢視表。 您可以指定配接器用來註冊通知與 SQL Server 的 SQL 陳述式。 Notification 陳述式可以是 SELECT 陳述式或預存程序會傳回結果集。 查詢通知的詳細資訊，請參閱 「 使用查詢通知 」，網址[ http://go.microsoft.com/fwlink/?LinkId=122159 ](http://go.microsoft.com/fwlink/?LinkId=122159)。 查詢可用於查詢通知的相關資訊，請參閱 「 建立查詢的通知 」，網址[ http://go.microsoft.com/fwlink/?LinkId=122160 ](http://go.microsoft.com/fwlink/?LinkId=122160)。  
  
 從 SQL Server 接收查詢通知是類似輪詢 SQL Server，但有一些重要的差異。 如需差異的清單，請參閱[考量接收查詢通知使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/considerations-for-receiving-query-notifications-using-the-sql-adapter.md)。  
  
 以下是一些您可以設定的案例[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]以接收來自 SQL Server 通知：  
  
- 配接器用戶端取得 「 增量 」 通知，比方說，只有這些上次告知以來對資料庫資料表所做的變更。  
  
- 如果多個資料列插入資料庫資料表時，配接器用戶端可以設定多個接收位置，以進行負載平衡接收通知。  
  
- 如果配接器用戶端會在其接收通知的接收位置關閉時，配接器用戶端可以設定配接器收到通知，因為接收位置已啟動一次。 用戶端也必須實作邏輯來處理，可能會有已插入、 更新或刪除接收位置已關閉時記錄其應用程式中。  
  
  一旦配接器用戶端會收到通知訊息，他們可以執行特定工作，根據接收到通知的類型。 例如，BizTalk 協調流程可以設計的方式收到更新通知時，它執行一組工作，如果收到插入通知和另一組工作。  
  
  在本節中的主題提供有關如何設定每個案例的配接器的資訊。 若要開始使用 SQL Server 將通知[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，您必須指定特定繫結屬性。 如需配接器支援接收訊息的詳細資訊，請參閱[考量接收查詢通知使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/considerations-for-receiving-query-notifications-using-the-sql-adapter.md)。 如需有關繫結屬性與通知相關的詳細資訊，請參閱[了解 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。 如需通知訊息的結構的詳細資訊，請參閱[查詢通知的訊息結構描述](../../adapters-and-accelerators/adapter-sql/message-schemas-for-query-notification.md)。  
  
  您也必須啟用查詢通知的 SQL Server 上執行下列工作。  
  
- SQL Server 資料庫，您必須啟用 Service Broker。  
  
- 您必須確定配接器用戶端具有必要的權限來執行命令要求通知。  
  
  這些工作的詳細資訊，請參閱 「 啟用查詢通知 」，網址[ http://go.microsoft.com/fwlink/?LinkID=122323 ](http://go.microsoft.com/fwlink/?LinkID=122323)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [考量接收查詢通知使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/considerations-for-receiving-query-notifications-using-the-sql-adapter.md)  
  
-   [處理通知訊息，以便完成特定工作中使用 BizTalk Server 的 SQL](../../adapters-and-accelerators/adapter-sql/process-notification-messages-to-complete-specific-tasks-in-sql-using-biztalk.md)  
  
-   [以累加方式查詢通知接收使用 BizTalk Server 的 SQL](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-incrementally-from-sql-using-biztalk-server.md)  
  
-   [從使用 BizTalk Server 的 SQL 接收查詢通知上的多個接收位置](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-on-receive-locations-from-sql-server-using-biztalk.md)  
  
-   [查詢通知之後會收到在細分接收位置中使用 BizTalk Server 的 SQL](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-after-a-sql-receive-location-stops-in-biztalk.md)  
  
## <a name="see-also"></a>另請參閱  
[使用 SQL 配接器開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)