---
title: 從使用 BizTalk Server 的 SQL 接收查詢通知上的多個接收位置 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9afbe98e-8901-417c-a807-8db97fd7a24b
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 231d5f83e673a7af2594c3f6f49e4457fcd9573e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010463"
---
# <a name="receive-query-notifications-on-multiple-receive-locations-from-sql-using-biztalk-server"></a>從使用 BizTalk Server 的 SQL 接收查詢通知上的多個接收位置
假設您有多個接收位置設定為接收相同的資料表 （例如員工） 的查詢通知的不同 BizTalk 應用程式的過程中建立相同的資料庫中。 如果一百個記錄插入相同的資料表時，所有接收位置就會都收到通知訊息。 實際上會收到通知，跨多個接收位置，您可以從 BizTalk 應用程式一接收到通知時，如果接收位置的這種方式來呼叫作業，其他接收位置不會取得相同的通知。 因此，您可以有效地負載平衡多個位置上收到的通知。  

 若要設定負載平衡接收通知的協調流程所需的工作會與針對相同[接收查詢通知以累加方式從使用 BizTalk Server 的 SQL](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-incrementally-from-sql-using-biztalk-server.md)。 本主題列出的唯一兩種方法之間的差異。  

## <a name="load-balancing-query-notifications-across-multiple-receive-locations"></a>跨多個負載平衡查詢通知的接收位置  
 本主題所示[接收查詢通知以累加方式從使用 BizTalk Server 的 SQL](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-incrementally-from-sql-using-biztalk-server.md)，您會已收到的記錄上執行 UPDATE 陳述式來設定累加通知。 若要設定負載平衡，您可以執行預存程序會刪除已通知的記錄。 例如，請考慮使用下列定義的預存程序 PROCESS_EMPLOYEE:  

```  
DECLARE @var int  
SELECT TOP 1 @var = Employee_ID FROM Employee  
SELECT * FROM Employee WHERE Employee_ID=@var  
DELETE FROM Employee WHERE Employee_ID=@var  
```  

 當您執行這個預存程序的 BizTalk 應用程式的一部分時，刪除已收到通知的記錄。 因此，其他接收位置取得通知下, 一筆記錄。  

 以下是您必須執行才能設定負載平衡來接收通知的概要步驟。  

1. 建立結構描述**通知**（輸入作業） 和**PROCESS_EMPLOYEE**預存程序 （輸出作業）。  

2. 新增協調流程以及接收通知、 執行預存程序，和取得回應的預存程序的三個訊息。  

3. 新增傳送和接收圖形、 建構訊息 」 圖形，以及連接埠，以建立協調流程。 您可以使用相同的範例程式碼建構的訊息，叫用 PROCESS_EMPLOYEE 預存程序。 請注意，在執行中的作業時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您必須擁有 PROCESS_EMPLOYEE 的要求訊息中的位置 C:\TestLocation\MessageIn 預存程序。 您會執行，因為程式碼片段您叫用做為建立的協調流程的一部分[接收查詢通知以累加方式從使用 BizTalk Server 的 SQL](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-incrementally-from-sql-using-biztalk-server.md)建立要求訊息，根據要求的 XML 位於 C:\TestLocation\MessageIn。  

4. 建置及部署應用程式。 若要示範負載平衡，您必須部署此協調流程至少具有兩部不同電腦上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]安裝。  

5. 在 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]兩部電腦上的管理主控台可讓您指定下列的繫結屬性，Wcf-custom 或 WCF SQL 接收位置：  


   |     繫結屬性      |                                                                                                                  ReplTest1                                                                                                                  |
   |---------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **InboundOperationType**  |                                                                                                      將此設為**通知**。                                                                                                      |
   | **NotificationStatement** | 將此設為：<br /><br /> `SELECT Employee_ID, Name FROM dbo.Employee WHERE Status=0`<br /><br /> **注意：** 通知陳述式中，您一律必須指定資料表名稱，以及結構描述名稱。 例如， `dbo.Employee`。 |
   | **NotifyOnListenerStart** |                                                                                                          將此設為 **，則為 True**。                                                                                                          |


6. 啟動 BizTalk 應用程式。  

7. 若要開始接收通知，請將一百個記錄插入員工資料表。 同時這種方式，請確定要求 XML 叫用 PROCESS_EMPLOYEE 預存程序是用於 C:\TestLocation\MessageIn。  

8. 監視 BizTalk 應用程式將會捨棄的通知訊息的位置 （在兩部電腦）。 您會發現，插入的數百個記錄，一個位置取得某些記錄的通知時其他位置取得剩餘的記錄的通知。 在一起，這兩個位置會收到數百個的所有記錄的通知。  

## <a name="see-also"></a>另請參閱  
 [接收使用 BizTalk Server 的 SQL 查詢通知](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md)