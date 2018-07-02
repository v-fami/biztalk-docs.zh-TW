---
title: 接收 Oracle E-business Suite 資料庫變更通知，在多個接收位置 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d25faa52-e0a4-4593-8449-3ec93d5887e9
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78e72333fa88a23b95d05eb75df8d132c4d0d77a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975431"
---
# <a name="receive-oracle-e-business-suite-database-change-notifications-on-multiple-receive-locations"></a>接收 Oracle E-business Suite 資料庫變更通知，在多個接收位置
假設您有多個接收位置設定為接收相同的資料表 (例如 ACCOUNTACTIVITY) 的查詢通知的不同 BizTalk 應用程式的過程中建立相同的資料庫中。 如果一百個記錄插入相同的資料表時，所有接收位置就會都收到通知訊息。 實際上會收到通知，跨多個接收位置，您可以從 BizTalk 應用程式一接收到通知時，如果接收位置的這種方式來呼叫作業，其他接收位置不會取得相同的通知。 因此，您可以有效地負載平衡多個位置上收到的通知。  

 若要設定負載平衡接收通知的協調流程所需的工作會與針對相同[接收 Oracle E-business Suite 變更通知以累加方式使用 BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-change-notifications-incrementally-using-biztalk-server.md)。 本主題列出的唯一兩種方法之間的差異。  

## <a name="load-balancing-query-notifications-across-multiple-receive-locations"></a>跨多個負載平衡查詢通知的接收位置  
 本主題所示[接收 Oracle E-business Suite 變更通知以累加方式使用 BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-change-notifications-incrementally-using-biztalk-server.md)，執行 PROCESS_RECORDS 程序設定累加通知。 若要設定負載平衡，您可以執行預存程序會刪除已通知的記錄。 例如，請考慮使用下列定義的預存程序 NOTIFY_LOAD_BALANCE:  

```  
PROCEDURE NOTIFY_LOAD_BALANCE (TABLE_DATA OUT SYS_REFCURSOR) IS  
  var int;  
BEGIN  
  SELECT TID INTO var FROM ACCOUNTACTIVITY WHERE ROWNUM = 1 FOR UPDATE;  
  OPEN TABLE_DATA FOR SELECT * FROM ACCOUNTACTIVITY WHERE TID = var;  
  DELETE FROM ACCOUNTACTIVITY WHERE TID = var;  
END NOTIFY_LOAD_BALANCE;  
```  

 當您執行這個預存程序的 BizTalk 應用程式的一部分時，刪除已收到通知的記錄。 因此，其他接收位置取得通知下, 一筆記錄。  

 以下是您必須執行才能設定負載平衡來接收通知的概要步驟。  

1. 建立結構描述**通知**（輸入作業） 和**NOTIFY_LOAD_BALANCE**程序 （輸出作業）。  

2. 新增協調流程以及接收通知、 執行程序，和取得回應的程序的三個訊息。  

3. 新增傳送和接收圖形、 建構訊息 」 圖形，以及連接埠，以建立協調流程。 您可以使用相同的範例程式碼建構的訊息，叫用 NOTIFY_LOAD_BALANCE 預存程序。 請注意，在執行中的作業時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台中，您必須在位置 C:\TestLocation\MessageIn NOTIFY_LOAD_BALANCE 程序的要求訊息。 您會執行，因為程式碼片段您叫用做為建立的協調流程的一部分[接收 Oracle E-business Suite 變更通知以累加方式使用 BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-change-notifications-incrementally-using-biztalk-server.md)建立要求存在 XML 為基礎的要求訊息在 C:\TestLocation\MessageIn。  

4. 建置及部署應用程式。 若要示範負載平衡，您必須部署此協調流程至少具有兩部不同電腦上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]安裝。  

5. 在  [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Wcf-oracleebs 的 Wcf-custom 接收位置，管理主控台，在這兩部電腦上的指定下列繫結屬性：  


   |     繫結屬性      |                                                                                                                                                                                                                                                                         ReplTest1                                                                                                                                                                                                                                                                         |
   |---------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **InboundOperationType**  |                                                                                                                                                                                                                                                             將此設為**通知**。                                                                                                                                                                                                                                                             |
   |   **NotificationPort**    | 指定 ODP.NET 必須開啟以接聽從 Oracle 資料庫的資料庫變更通知的連接埠號碼。 設定為相同的連接埠號碼，您必須已加入的 Windows 防火牆例外清單。 如需如何將 Windows 防火牆例外清單中的連接埠的指示，請參閱 < [ http://go.microsoft.com/fwlink/?LinkID=196959 ](http://go.microsoft.com/fwlink/?LinkID=196959)。 **重要事項：** 如果您設定為預設值-1，您必須完全停用 Windows 防火牆，以接收通知訊息。 |
   | **NotificationStatement** |                                                                                                                                                                 將此設為：<br /><br /> `SELECT TID,ACCOUNT,PROCESSED FROM SCOTT.ACCOUNTACTIVITY WHERE PROCESSED = ‘n’` **注意：** 您必須指定資料表名稱，以及結構描述名稱。 例如， `SCOTT.ACCOUNTACTIVITY`。                                                                                                                                                                 |
   | **NotifyOnListenerStart** |                                                                                                                                                                                                                                                                 將此設為 **，則為 True**。                                                                                                                                                                                                                                                                 |


6. 啟動 BizTalk 應用程式。  

7. 若要開始接收通知，數百筆記錄插入 ACCOUNTACTIVITY 資料表。 在這麼做，請確定叫用 NOTIFY_LOAD_BALANCE 程序的要求 XML 位於 C:\TestLocation\MessageIn。  

8. 監視 BizTalk 應用程式將會捨棄的通知訊息的位置 （在兩部電腦）。 您會發現，插入的數百個記錄，一個位置取得某些記錄的通知時其他位置取得剩餘的記錄的通知。 在一起，這兩個位置會收到數百個的所有記錄的通知。  

## <a name="see-also"></a>另請參閱  
 [Oracle E-business Suite 使用接收資料庫變更通知 BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-using-biztalk-server.md)