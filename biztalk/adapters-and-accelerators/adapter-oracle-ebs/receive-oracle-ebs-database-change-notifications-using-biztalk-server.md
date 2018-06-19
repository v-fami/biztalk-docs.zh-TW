---
title: 接收 Oracle E-business Suite 使用 BizTalk Server 資料庫的變更通知 |Microsoft 文件
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
ms.openlocfilehash: 24ac132f599256c2051763ed849e4e5329563201
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22215678"
---
# <a name="receive-oracle-e-business-suite-database-change-notifications-using-biztalk-server"></a>接收 Oracle E-business Suite 使用 BizTalk Server 資料庫的變更通知
您可以設定[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]從 Oracle E-business Suite 接收資料庫變更的通知訊息。 您可以指定配接器用來註冊通知與 Oracle E-business Suite 的 SELECT 陳述式。 結果集針對 SELECT 陳述式，註冊通知，請變更時，配接器會接收通知訊息。 如需配接器如何支援通知的詳細資訊，請參閱[接收資料庫變更通知使用 Oracle E-business Suite 介面卡的考量](../../adapters-and-accelerators/adapter-oracle-ebs/before-you-receive-database-change-notifications-using-the-oracle-ebs-adapter.md)。  
  
 以下是一些案例，您可以設定[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]與[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]要從 Oracle E-business Suite 接收通知：  
  
-   配接器用戶端取得 「 增量 」 通知，例如，僅至資料庫資料表的最後一個通知之後進行這些變更。  
  
-   如果大量的資料列插入資料庫資料表時，配接器用戶端可以設定多個接收位置的負載平衡接收通知。  
  
 配接器用戶端接收通知訊息之後，他們可以執行特定工作，根據收到的通知類型。 例如，BizTalk 協調流程可以設計收到更新通知時，它執行一組工作，如果收到插入通知和另一組工作的方式。  
  
> [!CAUTION]
>  如果沒有 Oracle 資料庫與配接器用戶端之間的網路中斷，通知不會傳送到配接器用戶端網路中斷，這段期間完成的 Oracle 資料庫上的變更之後。 因此，您必須使用輪詢作業，而不是用在關鍵狀況通知操作。  
  
 此章節的主題提供如何設定配接器的每個案例的資訊。 若要開始使用 Oracle E-business Suite 取得通知[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，您必須指定特定繫結屬性。 如需通知相關的繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。 如需有關的通知訊息結構的詳細資訊，請參閱[通知作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-notification-operation2.md)。  
  
 從 Oracle E-business Suite 接收通知，請確定：  
  
-   您可以使用介面卡連線到支援的 Oracle 資料庫版本。 10.2 之前的 oracle 資料庫版本不支援通知。  
  
-   **變更通知**權限，才能接收資料庫變更通知。  若要設定此權限，連接到 Oracle 資料庫使用系統管理權限，然後在 SQL 提示字元處輸入下列命令。  
  
    ```  
    grant change notification to <user name>  
    ```  
  
-   決定您想要用於接收從 Oracle 資料庫的資料庫變更通知 ODP.NET TCP 連接埠。 Windows 防火牆例外清單中加入該通訊埠。 如需如何將連接埠新增至 Windows 防火牆例外清單的指示，請參閱[http://go.microsoft.com/fwlink/?LinkID=196959](http://go.microsoft.com/fwlink/?LinkID=196959)。 您必須提供的相同通訊埠編號**NotificationPort**繫結屬性。 如需繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [接收資料庫變更通知使用 Oracle E-business Suite 介面卡的考量](../../adapters-and-accelerators/adapter-oracle-ebs/before-you-receive-database-change-notifications-using-the-oracle-ebs-adapter.md)  
  
-   [處理程序來完成 Oracle E-business Suite 中的特定工作的通知訊息](../../adapters-and-accelerators/adapter-oracle-ebs/process-notification-messages-to-complete-specific-tasks-in-oracle-ebs.md)  
  
-   [接收以累加方式使用 BizTalk Server 的 Oracle E-business Suite 變更通知](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-change-notifications-incrementally-using-biztalk-server.md)  
  
-   [接收 Oracle E-business Suite 資料庫變更通知上的多個接收位置](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-on-multiple-receive-locations.md)  
  
-   [接收 Oracle E-business Suite 資料庫後的變更通知接收位置分解](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-after-a-receive-location-stops.md)  
  
## <a name="see-also"></a>另請參閱  
[開發 BizTalk 應用程式使用 Oracle E-business Suite 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)