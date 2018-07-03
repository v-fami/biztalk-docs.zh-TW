---
title: Oracle E-business Suite 使用接收資料庫變更通知 BizTalk Server |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e92520cf-c552-4225-abba-8e03f73ecf70
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6381e2c429763596e3aa5c1fd70619cae588b68d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991423"
---
# <a name="receive-oracle-e-business-suite-database-change-notifications-using-biztalk-server"></a>Oracle E-business Suite 使用接收資料庫變更通知 BizTalk Server
您可以設定[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]從 Oracle E-business Suite 接收資料庫變更通知訊息。 您可以指定配接器用來註冊通知 Oracle E-business Suite 的 SELECT 陳述式。 結果集的 SELECT 陳述式，註冊通知，請變更時，配接器會接收通知訊息。 如需配接器如何支援通知的詳細資訊，請參閱[接收資料庫變更通知使用 Oracle E-business Suite 配接器的考量](../../adapters-and-accelerators/adapter-oracle-ebs/before-you-receive-database-change-notifications-using-the-oracle-ebs-adapter.md)。  
  
 以下是一些您可以設定的案例[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]要從 Oracle E-business Suite 接收通知：  
  
- 配接器用戶端取得 「 增量 」 通知，比方說，只有這些上次告知以來對資料庫資料表所做的變更。  
  
- 如果大量的資料列插入資料庫資料表時，配接器用戶端可以設定多個接收位置，以進行負載平衡接收通知。  
  
  配接器用戶端會收到通知訊息之後，他們可以執行的收到的通知類型為基礎的特定工作。 例如，BizTalk 協調流程可以設計的方式收到更新通知時，它執行一組工作，如果收到插入通知和另一組工作。  
  
> [!CAUTION]
>  針對在網路中斷期間在 Oracle 資料庫上所做的變更，將通知 Oracle 資料庫與配接器用戶端之間的網路中斷時，將不傳送給配接器用戶端，之後。 因此，您必須使用輪詢作業，而非通知作業的重要案例。  
  
 在本節中的主題提供有關如何設定每個案例的配接器的資訊。 若要開始通知 Oracle E-business Suite 使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，您必須指定特定繫結屬性。 如需有關繫結屬性與通知相關的詳細資訊，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。 如需通知訊息的結構的詳細資訊，請參閱[通知作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-notification-operation2.md)。  
  
 從 Oracle E-business Suite 中接收通知，請確定：  
  
-   您可以使用配接器連線到支援的 Oracle 資料庫版本。 10.2 之前的 oracle 資料庫版本不支援通知。  
  
-   **變更通知**權限，才能接收資料庫變更通知。  若要設定此權限，連接到 Oracle 資料庫使用系統管理權限，然後輸入下列命令在 SQL 提示字元上。  
  
    ```  
    grant change notification to <user name>  
    ```  
  
-   決定您想要用來從 Oracle 資料庫接收資料庫變更通知 ODP.NET TCP 連接埠。 將該連接埠新增至 Windows 防火牆例外清單中。 如需如何將 Windows 防火牆例外清單中的連接埠的指示，請參閱 < [ http://go.microsoft.com/fwlink/?LinkID=196959 ](http://go.microsoft.com/fwlink/?LinkID=196959)。 您必須提供的相同連接埠號碼**NotificationPort**繫結屬性。 如需有關繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [接收資料庫變更通知使用 Oracle E-business Suite 配接器的考量](../../adapters-and-accelerators/adapter-oracle-ebs/before-you-receive-database-change-notifications-using-the-oracle-ebs-adapter.md)  
  
-   [若要完成 Oracle E-business Suite 中的特定工作的程序通知訊息](../../adapters-and-accelerators/adapter-oracle-ebs/process-notification-messages-to-complete-specific-tasks-in-oracle-ebs.md)  
  
-   [接收以累加方式使用 BizTalk Server 的 Oracle E-business Suite 變更通知](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-change-notifications-incrementally-using-biztalk-server.md)  
  
-   [接收 Oracle E-business Suite 資料庫變更通知上多個接收位置](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-on-multiple-receive-locations.md)  
  
-   [接收 Oracle E-business Suite 資料庫後的變更通知接收位置細目](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-after-a-receive-location-stops.md)  
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式使用 Oracle E-business Suite 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)