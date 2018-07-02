---
title: 接收使用 BizTalk Server 的 Oracle 資料庫變更通知 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495a29bc-72f6-4140-8160-0b917d935503
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8bd67791e56d941d58cb0b221bf7ad63bb3778f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985039"
---
# <a name="receive-oracle-database-change-notifications-using-biztalk-server"></a>接收使用 BizTalk Server 的 Oracle 資料庫變更通知
您可以設定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]從 Oracle 資料庫接收資料庫變更通知訊息。 您可以指定配接器用來註冊通知與 Oracle 資料庫的 SELECT 陳述式。 結果集的 SELECT 陳述式，註冊通知，請變更時，配接器會接收通知訊息。 如需配接器如何支援通知的詳細資訊，請參閱[接收資料庫變更通知使用 Oracle 資料庫配接器的考量](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md)。  
  
 以下是一些您可以設定的案例[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]從 Oracle 資料庫接收通知：  
  
- 配接器用戶端取得 「 增量 」 通知，比方說，只有這些上次告知以來對資料庫資料表所做的變更。  
  
- 如果大量的資料列插入資料庫資料表時，配接器用戶端可以設定多個接收位置，以進行負載平衡接收通知。  
  
  一旦配接器用戶端會收到通知訊息，他們可以執行特定工作，根據接收到通知的類型。 例如，BizTalk 協調流程可以設計的方式收到更新通知時，它執行一組工作，如果收到插入通知和另一組工作。  
  
> [!CAUTION]
>  針對在網路中斷期間在 Oracle 資料庫上所做的變更，將通知 Oracle 資料庫與配接器用戶端之間的網路中斷時，將不傳送給配接器用戶端，之後。 因此，您必須使用輪詢作業，而非通知作業的重要案例。  
  
 在本節中的主題提供有關如何設定每個案例的配接器的資訊。 若要開始從 Oracle 資料庫使用中取得通知[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，您必須指定特定繫結屬性。 如需有關繫結屬性與通知相關的詳細資訊，請參閱[使用繫結屬性](https://msdn.microsoft.com/library/dd788467.aspx)。 如需通知訊息的結構的詳細資訊，請參閱[通知作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-notification-operation1.md)。  
  
 從 Oracle 資料庫中接收通知，請確定：  
  
-   您可以使用配接器連線到 Oracle 資料庫版本 10.2 或更新版本。 10.2 之前的 oracle 資料庫版本不支援通知。  
  
-   您用來連接到 Oracle，通知的認證具有`change notification`權限。 此權限，才能接收資料庫變更通知。 若要這樣做，請連接到 Oracle 資料庫使用系統管理權限，然後在 SQL 提示字元上輸入下列命令。  
  
    ```  
    grant change notification to <user name>  
    ```  
  
-   決定您想要用來從 Oracle 資料庫接收資料庫變更通知 ODP.NET TCP 連接埠。 將該連接埠新增至 Windows 防火牆例外清單中。 如需如何將 Windows 防火牆例外清單中的連接埠的指示，請參閱 < [ http://go.microsoft.com/fwlink/?LinkID=196959 ](http://go.microsoft.com/fwlink/?LinkID=196959)。 您必須提供的相同連接埠號碼**NotificationPort**繫結屬性。 如需有關繫結屬性的詳細資訊，請參閱[使用繫結屬性](https://msdn.microsoft.com/library/dd788467.aspx)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [接收資料庫變更通知使用 Oracle 資料庫配接器的考量](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md)  
  
-   [處理通知訊息，以使用 BizTalk Server 的 Oracle 資料庫中完成特定工作](../../adapters-and-accelerators/adapter-oracle-database/process-notification-messages-to-run-specific-tasks-in-oracle-db-using-biztalk.md)  
  
-   [以累加方式使用 BizTalk Server 接收的 Oracle 資料庫變更通知](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-incrementally-using-biztalk-server.md)  
  
-   [接收 Oracle 資料庫變更通知，在多個接收位置](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-on-multiple-receive-locations.md)  
  
-   [接收之後的 Oracle 資料庫變更通知接收位置細目](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-after-a-receive-location-breakdown.md)  
  
## <a name="see-also"></a>另請參閱  
[若要開發與 Oracle 資料庫的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)