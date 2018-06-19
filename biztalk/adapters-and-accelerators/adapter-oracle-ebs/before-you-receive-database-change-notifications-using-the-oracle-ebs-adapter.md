---
title: 變更通知使用 Oracle E-business Suite 配接器的接收資料庫的考量 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 95bbb19e-8d31-4b27-8cfe-6760e4bb0808
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3157b8ab7a706203d3b9475de890fb2a8f8dd3a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25963172"
---
# <a name="considerations-for-receiving-database-change-notifications-using-the-oracle-e-business-suite-adapter"></a>變更通知使用 Oracle E-business Suite 配接器的接收資料庫的考量
本主題提供一些考量和最佳作法，您必須使用時請記住[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]要從 Oracle 資料庫接收資料庫通知。  
  
## <a name="considerations-while-using-the-adapter-to-receive-notifications"></a>使用配接器接收通知時的考量  
 您必須考慮下列使用時[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]接收查詢通知。  
  
-   [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]只會傳遞通知，從 Oracle 資料庫時，它會接收配接器用戶端上。 配接器不會區分的通知不同的作業，也就是，配接器沒有任何資訊的特定通知適用於插入作業或更新作業。  
  
-   作業的通知訊息不會受到該作業所影響的記錄數目。 例如，Oracle 資料庫資料表中插入的記錄數目，不論配接器用戶端收到只有一個通知訊息。  
  
-   我們建議配接器用戶端應用程式包含的邏輯來解譯的從 Oracle 資料庫接收的通知類型。 配接器用戶端應用程式可以這樣做來擷取中的資訊**\<資訊\>** 接收的通知訊息的項目。 以下是 Insert 作業接收通知訊息的範例。  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <Notification xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Notification/">  
      <Details>  
        <NotificationDetails>  
          <ResourceName>SCOTT.ACCOUNTACTIVITY</ResourceName>   
          <Info>1</Info>   
          <QueryId>0</QueryId>   
        </NotificationDetails>  
      </Details>  
      <Info>Insert</Info>   
      <ResourceNames>  
        <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/Arrays">SCOTT.ACCOUNTACTIVITY</string>   
      </ResourceNames>  
      <Source>Data</Source>   
      <Type>Change</Type>   
    </Notification>  
    ```  
  
     請注意內的值**\<資訊\>** 項目。 此值會提供資訊在收到通知訊息的作業。 您的應用程式應該有的功能來擷取內的值**\<資訊\>** 項目，然後根據的值，執行後續的工作。 本主題[Oracle E-business Suite 中完成特定工作的程序通知訊息](../../adapters-and-accelerators/adapter-oracle-ebs/process-notification-messages-to-complete-specific-tasks-in-oracle-ebs.md)如何擷取內的值中的指示**\<資訊\>** 項目.  
  
-   在理想情況下，用戶端應用程式會收到通知之後，它應該更新其已收到通知，讓後續的通知沒有相同的記錄的記錄。 例如，請考慮**ACCOUNTACTIVITY**資料表具有**處理**資料行。 針對所有新記錄插入至**ACCOUNTACTIVITY**資料表中的值**處理**資料行一律是 ' n '。 例如，在插入作業中的記錄之後**ACCOUNTACTIVITY**資料表看起來如下所示：  
  
    |帳戶交易識別碼|已處理|  
    |----------------------------|---------------|  
    |10001|n|  
  
     若要取得之新插入的資料錄的通知，設定配接器用戶端將**NotificaitonStatement**繫結屬性：  
  
    ```  
    SELECT * FROM SCOTT.ACCOUNTACTIVITY WHERE PROCESSED = ‘n’  
    ```  
  
     之後，收到通知，用戶端應用程式必須設定的值**處理**'y' 資料行，以便在 notification 陳述式不能進行已收到的記錄。 因此，若要達成此目的，用戶端應用程式必須執行更新作業上**ACCOUNTACTIVITY**資料表。 更新作業之後，相同記錄**ACCOUNTACTIVITY**資料表看起來如下所示：  
  
    |帳戶交易識別碼|已處理|  
    |----------------------------|---------------|  
    |10001|y|  
  
     有趣的是，更新作業將會再次傳送通知給配接器用戶端，整個程序會重複一次。 因此，用戶端應用程式必須有必要的邏輯，以捨棄這類的不必要的通知。  
  
-   如果**NotifyOnListenerStart**繫結屬性為 true，配接器會傳送通知給配接器用戶端每次啟動接收位置。 如需有關如何使用繫結屬性和解譯的通知訊息的詳細資訊，請參閱[接收 Oracle E-business Suite 資料庫變更通知之後接收位置分解](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-after-a-receive-location-stops.md)。  
  
## <a name="typical-orchestration-for-receiving-notifications"></a>典型的協調流程接收通知  
 本節將概述接收通知使用一般的協調流程[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。  
  
1.  協調流程必須進行第一件事是通知的檢查的收到類型。 若要檢查的事項如下：  
  
    -   是否已收到通知，接收位置重新啟動。  
  
    -   是否已收到通知，作業會在資料庫資料表，例如 Insert、 Update 或 Delete。  
  
     協調流程必須包含**運算式**圖形，並在接收到 xpath 查詢，以決定何種訊息。  
  
2.  提供的通知類型之後，協調流程必須包含所要執行特定動作，根據收到的通知類型的決策區塊。 若要達成此目的，協調流程必須包含**決定**圖形。 **決定**圖形組成**規則**區塊和**Else**區塊。 內**規則**區塊中，您必須指定的條件，並再包含執行某些作業，如果符合條件的協調流程圖形。 內**Else**區塊中，您必須包含執行某些作業，如果條件為協調流程圖形*不*符合。  
  
 中的詳細說明上述建議[Oracle E-business Suite 中完成特定工作的程序通知訊息](../../adapters-and-accelerators/adapter-oracle-ebs/process-notification-messages-to-complete-specific-tasks-in-oracle-ebs.md)。  
  
## <a name="see-also"></a>請參閱  
 [接收 Oracle E-business Suite 資料庫變更通知使用 BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-using-biztalk-server.md)