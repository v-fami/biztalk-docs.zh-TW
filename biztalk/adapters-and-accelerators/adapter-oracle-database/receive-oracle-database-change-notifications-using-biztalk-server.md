---
title: "接收使用 BizTalk Server 的 Oracle 資料庫變更通知 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 495a29bc-72f6-4140-8160-0b917d935503
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69d4b4b3a0b528109caac60ecec3c3614e5d7a5b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="receive-oracle-database-change-notifications-using-biztalk-server"></a>接收使用 BizTalk Server 的 Oracle 資料庫變更通知
您可以設定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]來接收從 Oracle 資料庫的資料庫變更通知訊息。 您可以指定配接器用來註冊通知與 Oracle 資料庫的 SELECT 陳述式。 結果集針對 SELECT 陳述式，註冊通知，請變更時，配接器會接收通知訊息。 如需配接器如何支援通知的詳細資訊，請參閱[接收資料庫變更通知使用 Oracle 資料庫配接器的考量](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md)。  
  
 以下是一些案例，您可以設定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]要從 Oracle 資料庫接收通知：  
  
-   配接器用戶端取得 「 增量 」 通知，例如，僅至資料庫資料表的最後一個通知之後進行這些變更。  
  
-   如果大量的資料列插入資料庫資料表時，配接器用戶端可以設定多個接收位置的負載平衡接收通知。  
  
 一旦配接器用戶端會收到通知訊息，他們可以執行特定工作，根據收到的通知類型。 例如，BizTalk 協調流程可以設計收到更新通知時，它執行一組工作，如果收到插入通知和另一組工作的方式。  
  
> [!CAUTION]
>  如果沒有 Oracle 資料庫與配接器用戶端之間的網路中斷，通知不會傳送到配接器用戶端網路中斷，這段期間完成的 Oracle 資料庫上的變更之後。 因此，您必須使用輪詢作業，而不是用在關鍵狀況通知操作。  
  
 此章節的主題提供如何設定配接器的每個案例的資訊。 若要開始從 Oracle 資料庫使用中取得通知[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，您必須指定特定繫結屬性。 如需通知相關的繫結屬性的詳細資訊，請參閱[使用繫結屬性](https://msdn.microsoft.com/library/dd788467.aspx)。 如需有關的通知訊息結構的詳細資訊，請參閱[通知作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-notification-operation1.md)。  
  
 從 Oracle 資料庫接收通知，請確定：  
  
-   您可以使用配接器連接到 Oracle 資料庫版本 10.2 或更新版本。 10.2 之前的 oracle 資料庫版本不支援通知。  
  
-   您用來連接到 Oracle 通知的認證具有`change notification`權限。 此權限，才能接收資料庫變更通知。 若要這樣做，連接到 Oracle 資料庫使用系統管理權限，然後在 SQL 提示字元處輸入下列命令。  
  
    ```  
    grant change notification to <user name>  
    ```  
  
-   決定您想要用於接收從 Oracle 資料庫的資料庫變更通知 ODP.NET TCP 連接埠。 Windows 防火牆例外清單中加入該通訊埠。 如需如何將連接埠新增至 Windows 防火牆例外清單的指示，請參閱[http://go.microsoft.com/fwlink/?LinkID=196959](http://go.microsoft.com/fwlink/?LinkID=196959)。 您必須提供的相同通訊埠編號**NotificationPort**繫結屬性。 如需繫結屬性的詳細資訊，請參閱[使用繫結屬性](https://msdn.microsoft.com/library/dd788467.aspx)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [接收使用 Oracle 資料庫配接器的資料庫變更通知的考量](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md)  
  
-   [處理 Oracle 資料庫使用 BizTalk Server 中完成特定工作的通知訊息](../../adapters-and-accelerators/adapter-oracle-database/process-notification-messages-to-run-specific-tasks-in-oracle-db-using-biztalk.md)  
  
-   [以累加方式使用 BizTalk Server 接收的 Oracle 資料庫變更通知](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-incrementally-using-biztalk-server.md)  
  
-   [接收 Oracle 資料庫變更通知，在多個接收位置](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-on-multiple-receive-locations.md)  
  
-   [接收之後的 Oracle 資料庫變更通知接收位置分解](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-after-a-receive-location-breakdown.md)  
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式與 Oracle 資料庫的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)