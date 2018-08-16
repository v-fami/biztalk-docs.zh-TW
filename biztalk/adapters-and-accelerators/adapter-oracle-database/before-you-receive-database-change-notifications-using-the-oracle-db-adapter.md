---
title: 接收資料庫變更通知使用 Oracle 資料庫配接器的考量 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 206439b9-0408-4fbb-80e3-cfda2f5a89a5
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d7237037794168ffb136c95734582b3df95db48
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015191"
---
# <a name="considerations-for-receiving-database-change-notifications-using-the-oracle-database-adapter"></a>接收資料庫變更通知使用 Oracle 資料庫配接器的考量
本主題提供一些考量和最佳作法，您必須謹記在心，同時使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]從 Oracle 資料庫接收資料庫通知。  
  
## <a name="considerations-while-using-the-adapter-to-receive-notifications"></a>使用配接器接收通知時的考量  
 您必須考慮使用下列[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]接收查詢通知。  
  
- [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]只會將傳遞通知，從 Oracle 資料庫時，它會接收配接器用戶端。 配接器不會區分的通知不同的作業，也就是，配接器不提供任何資訊的特定通知是要用於插入作業或更新作業。  
  
- 作業的通知訊息不會受到該作業所影響的記錄數目。 比方說，無論在 Oracle 資料庫資料表中插入的記錄數目，配接器用戶端會收到只有一個通知訊息。  
  
- 建議配接器用戶端應用程式，包含要解譯的從 Oracle 資料庫接收的通知類型的邏輯。 配接器用戶端應用程式可以達到此目的擷取中的資訊**\<Info\>** 接收的通知訊息的項目。 以下是範例插入作業所接收的通知訊息。  
  
  ```  
  <?xml version="1.0" encoding="utf-8" ?>   
  <Notification xmlns="http://Microsoft.LobServices.OracleDB/2007/03/Notification/">  
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
  
   請注意內的值**\<Info\>** 項目。 這個值會提供收到通知訊息的作業的資訊。 您的應用程式應該有的功能內的值中擷取**\<Info\>** 項目，然後根據的值，執行後續的工作。 本主題[處理通知訊息來完成 Oracle 資料庫中的特定工作](../../adapters-and-accelerators/adapter-oracle-database/process-notification-messages-to-run-specific-tasks-in-oracle-db-using-biztalk.md)有關如何擷取內的值中的指示**\<資訊\>** 項目。  
  
- 在理想情況下，用戶端應用程式會收到通知之後，它應該更新為其已收到通知，讓後續的通知不會針對同一筆記錄的記錄。 例如，請考慮**ACCOUNTACTIVITY**具有資料表**處理**資料行。 針對所有新記錄插入至**ACCOUNTACTIVITY**資料表中的值**處理**資料行一律是 ' n '。 例如，在插入作業後中的記錄**ACCOUNTACTIVITY**資料表看起來如下所示：  
  
  |帳戶的交易識別碼|已處理|  
  |----------------------------|---------------|  
  |10001|n|  
  
   若要取得之新插入的資料錄的通知，將配接器用戶端**NotificationStatement**繫結屬性設為：  
  
  ```  
  SELECT * FROM SCOTT.ACCOUNTACTIVITY WHERE PROCESSED = ‘n’  
  ```  
  
   之後，接收通知，用戶端應用程式必須設定的值**處理**為 'y' 的資料行，讓 notification 陳述式前已收到通知的記錄上無法運作。 因此，若要達到此目的，用戶端應用程式必須在更新作業上執行**ACCOUNTACTIVITY**資料表。 更新作業之後，相同記錄**ACCOUNTACTIVITY**資料表看起來如下所示：  
  
  |帳戶的交易識別碼|已處理|  
  |----------------------------|---------------|  
  |10001|y|  
  
   有趣的是，更新作業將會再次傳送通知給配接器用戶端，並且會再次重複整個程序。 因此，用戶端應用程式必須具有必要的邏輯，以捨棄這類不必要的通知。  
  
- 如果**NotifyOnListenerStart**繫結屬性為 true 時，配接器會傳送通知給配接器用戶端每次接收位置開始。 如需有關如何使用繫結屬性和解譯的通知訊息的詳細資訊，請參閱 <<c0> [ 接收 Oracle 資料庫變更通知之後接收位置解析](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-after-a-receive-location-breakdown.md)。  
  
## <a name="typical-orchestration-for-receiving-notifications"></a>典型的協調流程接收通知  
 本節將概述在一般的協調流程，接收通知使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
1. 協調流程必須進行第一件事是通知的要檢查的收到類型。 若要檢查的事項如下：  
  
   - 是否收到通知的接收位置重新啟動。  
  
   - 是否已收到通知，作業會在資料庫資料表，例如 Insert、 Update 或 Delete。  
  
     協調流程必須包含**運算式**圖形，並在其中接收 xpath 查詢，以決定何種訊息。  
  
2. 可用的通知類型之後，協調流程必須包含所要執行特定動作，根據收到的通知類型的決策區塊。 若要達到此目的，協調流程必須包含**決定**圖形。 **決定**圖形組成**規則**區塊並**Else**區塊。 內**規則**區塊中，您必須指定條件，然後包含 如果符合條件時執行特定作業的協調流程圖形。 內**Else**區塊中，您必須包含如果條件為執行特定作業的協調流程圖形*不*符合。  
  
   在將詳細說明上述的建議[處理通知訊息，以完成使用 BizTalk Server 的 Oracle 資料庫中的特定工作](../../adapters-and-accelerators/adapter-oracle-database/process-notification-messages-to-run-specific-tasks-in-oracle-db-using-biztalk.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk Server 接收的 Oracle 資料庫變更通知](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-using-biztalk-server.md)