---
title: "訊息佇列的佇列 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [MSMQ adapters], queue paths
- naming conventions, MSMQ adapters
- configuring [MSMQ adapters], naming conventions
- messages, queuing
- MSMQ adapters, troubleshooting
- MSMQ adapters, message queues
- configuring [MSMQ adapters], troubleshooting
- troubleshooting, queue paths [MSMQ adapters]
- naming conventions, queue paths [MSMQ adapters]
- configuring [MSMQ adapters], message queues
ms.assetid: b802348e-8543-4b06-a6e4-149b86139fb1
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa8d2521a8cf434c7a0ea56f749f9df3f032551e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="message-queuing-queues"></a>訊息佇列的佇列
本節描述使用 MSMQ 配接器時如何指定 Microsoft Message Queuing (也稱為 MSMQ) 佇列。 內容不但描述指定路徑的慣例，同時也說明格式名稱在轉譯路徑成為佇列目的地時所扮演的角色。  
  
## <a name="queue-path-naming-conventions"></a>佇列路徑命名慣例  
 若佇列名稱是指路徑，請使用下表中的命名慣例。  
  
|**佇列類型**|**路徑的語法**|  
|--------------------|-------------------------|  
|公用佇列|*Computername*\QueueName|  
|私用佇列|*Computername*\Private$\QueueName|  
|記錄檔佇列|*Computername*\QueueName\Journal$|  
|電腦日誌佇列**附註：**用於只接收佇列。|*Computername*\Journal$|  
|電腦寄不出的信件佇列**附註：**用於只接收佇列。|*Computername*\Deadletter$|  
|電腦交易無法寄不出信件佇列**附註：**用於只接收佇列。|*Computername*\XactDeadletter$|  
  
> [!NOTE]
>  佇列的路徑必須是唯一的。  
  
 若佇列名稱是指格式名稱，會採用字串的形式，指示佇列是公用還是私用，並視需要接著為佇列和其他識別項所產生的 GUID。 使用下表中的命名慣例。  
  
|**格式類型**|**格式名稱語法**|  
|---------------------|--------------------------------|  
|公用|*使用 FormatName*： 公用 = QueueGUID|  
|直接|*使用 FormatName*: DIRECT = SPX:NetworkNumber:HostNumber\QueueName<br /><br /> *使用 FormatName*: DIRECT = TCP:IPAddress\QueueName<br /><br /> *使用 FormatName*: DIRECT = OS:ComputerName\QueueName|  
  
 若傳送埠佇列是通訊群組清單，那麼佇列路徑語法是：  
  
 DL=DistributionListGUID  
  
 若傳送或接收佇列路徑是 HTTP 或 HTTPS URL，那麼語法是：  
  
 FormatName:DIRECT = http: / /\<用戶端名稱\>/msmq/\<佇列名稱\>  
  
 FormatName:DIRECT = https: / /\<用戶端名稱\>/msmq/\<佇列名稱\>  
  
> [!NOTE]
>  "msmq" 是訊息佇列在 Internet Information Services (IIS) 中建立的虛擬資料夾。  
  
> [!NOTE]
>  您只能使用 HTTP 傳送訊息。 若佇列是使用 HTTP 直接格式名稱所開啟的，您就無法在遠端電腦上的佇列中讀取訊息。 不過，您仍然可以使用沒有 HTTP 的私用或公用佇列路徑，從遠端佇列接收 SOAP (格式化) 訊息。  
  
 若佇列名稱指的是系統管理員為佇列所指定的說明性文字標籤，那麼表示這個標籤的佇列路徑語法是：  
  
 LABEL:MyQueue  
  
> [!NOTE]
>  標籤不一定是唯一的。 因此，當您嘗試使用其標籤連接到特定佇列時，若發生名稱衝突，您就會收到錯誤。  
  
> [!NOTE]
>  標籤是配接器的必要傳輸欄位。  
  
## <a name="role-of-the-format-name"></a>格式名稱的角色  
 訊息佇列使用格式名稱來識別佇列以及決定存取方式。 訊息佇列會指派格式名稱到佇列。  
  
 當您使用路徑名稱語法指定佇列時，例如 myMachine\myQueue，訊息佇列會查詢路徑以尋找相關的格式名稱。 接著，訊息佇列會使用該格式名稱來存取佇列。 當您指定格式名稱時，訊息佇列會使用您所使用的格式名稱。  
  
 如需有關格式名稱的詳細資訊，請參閱＜.NET Framework 類別庫說明＞中的＜MessageQueue.FormatName 屬性＞。  
  
## <a name="troubleshooting-queue-paths"></a>疑難排解佇列路徑  
  
-   若提供的佇列路徑的語法不符合之前在＜佇列路徑命名慣例＞中所描述的其中一種格式，會發生例外狀況。  
  
-   下列字元在佇列路徑中的電腦名稱無效：  
  
     \ ; , + "  
  
     若電腦名稱是數字，會發生例外狀況。 例如： 234\private$ \queue。  
  
-   對於電腦無法寄出的信件佇列、電腦記錄檔佇列以及電腦交易無法寄出的信件佇列，若使用者指定任何一個系統佇列做為傳送的目的地佇列，會發生例外狀況。  
  
-   **System.Messaging.MessageQueue.Exists**不適用於遠端佇列。 如需詳細資訊，請參閱＜.NET Framework 類別庫說明＞中的＜MessageQueue.Exists 方法＞。  
  
## <a name="see-also"></a>請參閱  
 [設定 MSMQ 配接器](../core/configuring-the-msmq-adapter.md)