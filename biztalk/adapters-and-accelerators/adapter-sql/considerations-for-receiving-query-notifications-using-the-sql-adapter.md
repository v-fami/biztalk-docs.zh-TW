---
title: "使用 SQL 配接器接收查詢通知的考量 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0142f385-3d55-41a7-a50e-dda94b96d0a4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20bb7019a993e47137ec2e4f71334c5b6b3f663c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-for-receiving-query-notifications-using-the-sql-adapter"></a>使用 SQL 配接器接收查詢通知的考量
本主題提供一些考量和最佳作法，以使用時請記住[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]要從 SQL Server 資料庫接收查詢通知。  
  
## <a name="considerations-while-using-the-adapter-to-receive-notifications"></a>使用配接器接收通知時的考量  
 您必須考慮下列使用時[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]接收查詢通知：  
  
-   [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]收到來自 SQL Server 查詢通知，然後只是要傳送通知到配接器用戶端。 配接器不會區分不同的作業的通知 （亦即，配接器沒有任何資訊是否為插入作業或更新作業的特定通知）。  
  
-   作業的通知訊息不會受到該作業所影響的記錄數目。 例如，插入、 更新或刪除 SQL Server 資料庫資料表中的記錄數目，不論配接器用戶端收到只有一個通知訊息。  
  
-   我們建議配接器用戶端應用程式包含的邏輯來解譯收到來自 SQL Server 通知的類型。 通知類型可以決定所擷取的資訊，從**\<資訊 >**接收的通知訊息的項目。 插入作業接收通知訊息的範例如下：  
  
    ```  
    <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification/">  
      <Info>Insert</Info>  
      <Source>Data</Source>  
      <Type>Change</Type>  
    </Notification>  
    ```  
  
     請注意內的值**\<資訊 >**項目。 此值會提供資訊在收到通知訊息的作業。 您的應用程式應該有的功能來擷取內的值**\<資訊 >**項目，然後根據的值，執行後續的工作。 本主題[處理通知訊息，以便完成特定工作中使用 BizTalk Server 的 SQL](../../adapters-and-accelerators/adapter-sql/process-notification-messages-to-complete-specific-tasks-in-sql-using-biztalk.md)如何擷取內的值中的指示**\<資訊 >**項目。 詳細的教學課程，執行類似的工作也會提供在[教學課程 2： 員工-訂單程序使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/tutorial-2-employee-purchase-order-process-using-the-sql-adapter.md)。  
  
-   在理想情況下，用戶端應用程式會收到通知的特定記錄後，該記錄應該會更新，讓沒有收到其他通知。 例如，請考慮**員工**資料表具有**狀態**資料行。 針對所有新記錄插入至**員工**資料表中的值**狀態**資料行一律是"0"，資料表看起來像下面：  
  
    |員工名稱|狀態|  
    |-------------------|------------|  
    |John|0|  
  
     若要接收通知之新插入的記錄，設定配接器用戶端將**NotificatonStatement**繫結屬性：  
  
    ```  
    SELECT Employee_ID, Name FROM dbo.Employee WHERE Status=0  
    ```  
  
    > [!NOTE]
    >  具體來說，您必須指定資料行名稱中的陳述式中所示 SELECT 陳述式。 此外，您永遠必須指定資料表名稱，以及結構描述名稱。 例如，dbo。員工。  
  
     在收到通知，用戶端應用程式必須重設的值**狀態**為"1"的資料行，以便通知陳述式不能進行資料錄一次。 若要達成此目的，用戶端應用程式必須在執行更新作業**員工**資料表。 更新作業之後，相同記錄**員工**資料表看起來如下所示：  
  
    |員工名稱|狀態|  
    |-------------------|------------|  
    |John|1|  
  
     有趣的是，更新作業將會再次傳送通知給配接器用戶端和整個程序會重複一次，因此，用戶端應用程式必須具備所需的邏輯，以捨棄這類的不必要的通知。  
  
-   如果**NotifyOnListenerStart**繫結屬性為 true，每次啟動接收位置配接器用戶端會收到通知訊息。 如需有關如何使用繫結屬性和解譯的通知訊息的詳細資訊，請參閱[接收查詢通知之後接收位置分解在使用 BizTalk Server 的 SQL](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-after-a-sql-receive-location-stops-in-biztalk.md)。  
  
## <a name="typical-orchestration-for-receiving-notifications"></a>典型的協調流程接收通知  
 本節將概述接收通知使用一般的協調流程[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
1.  協調流程必須進行第一件事是要判斷接收通知的類型包括：  
  
    -   接收位置重新啟動之後，是否已收到通知。  
  
    -   是否已收到通知，作業會在資料庫資料表，例如 Insert、 Update 或 Delete。  
  
     協調流程必須包含**運算式**圖形，並在其中，xpath 查詢來決定接收的訊息種類。  
  
2.  在通知之後類型決定，協調流程必須包含所要執行特定動作，根據收到的通知類型的決策區塊。 若要達成此目的，協調流程必須包含**決定**圖形，其中包括**規則**區塊和**Else**區塊：  
  
    -   內**規則**區塊中，您必須指定的條件，並再包含執行某些作業，如果符合條件的協調流程圖形。  
  
    -   內**Else**區塊中，您必須包含執行某些作業，如果條件為協調流程圖形*不*符合。  
  
 中所述的上述需求的詳細資料[處理通知訊息，以便完成特定工作中使用 BizTalk Server 的 SQL](../../adapters-and-accelerators/adapter-sql/process-notification-messages-to-complete-specific-tasks-in-sql-using-biztalk.md)。 詳細的教學課程也會提供[教學課程 2： 員工-訂單程序使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/tutorial-2-employee-purchase-order-process-using-the-sql-adapter.md)。