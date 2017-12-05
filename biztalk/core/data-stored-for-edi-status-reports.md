---
title: "EDI 狀態報告的儲存資料 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec66e4d7-2694-499f-a60c-2f80fe643e12
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9395cb3895675e586576088f3d257dbf4115948f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="data-stored-for-edi-status-reports"></a>EDI 狀態報告的儲存資料
EDI 狀態報告中有兩個層級的報告： 第一個 if**開啟報告**協議，和第二個如果選取屬性**儲存交易集/內容報告**選取協議屬性。 這些屬性可用於**一般屬性**頁面**一般**索引標籤中**協議屬性** 對話方塊。  
  
## <a name="data-stored-if-edi-reporting-is-activated"></a>啟動 EDI 報告時的儲存資料  
 如果**開啟報告**協議中，選取屬性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會保留所有已傳送或接收之交換、 技術通知以及功能通知的記錄。  
  
 對於已接收的交換，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會儲存下列資訊：  
  
-   所有已接收交換的記錄。 這是 EDI 狀態報告 UI 中顯示的第一筆資訊。  
  
-   包含於交換中之所有交易集的記錄。 這並不包括啟用交易集儲存區時所儲存的所有詳細資料。  
  
-   出現在已接收交換中之所有技術通知的記錄。  
  
-   出現在已接收交換中之所有功能通知的記錄。  
  
    > [!NOTE]
    >  如果交換具有多個功能群組，狀態報告 UI 中就會儲存多個功能通知。 然而，如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 收到某個群組的重複功能通知，則 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 只會將最近一個功能通知儲存到狀態報告 UI 中。  
  
-   是否需要為已接收的交換產生技術通知。  
  
-   是否需要為已接收的交易集產生功能通知。  
  
 對於已傳送的交換，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會儲存下列資訊：  
  
-   已傳送交換的記錄。  
  
-   包含於交換中之所有交易集的記錄。  
  
-   出現在已傳送交換中之所有技術通知的記錄。  
  
-   出現在已傳送交換中之所有功能通知的記錄。  
  
 EDI 狀態報告 UI 會將這些記錄相互關聯以顯示完整的資訊。 例如，如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 收到某個交換，而且需要向原始訊息的傳送者發送技術通知和功能通知，您便可以在狀態報告 UI 中輕易找到這項資訊。  
  
## <a name="data-stored-if-transaction-set-storage-is-enabled"></a>啟用交易集儲存區時的儲存資料  
 如果**儲存報告的訊息內容**協議中，選取屬性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會儲存已傳送或接收交換中找到的所有交易集的詳細資料。 如果有啟動 EDI 報告，這個層級的狀態報告便會實作所有執行的第一層級報告，並會加上交易集的專屬資訊。 EDI 接收管線和傳送管線產生項目在 BAM 資料庫的每個內送和外寄群組或交易集 (雖然"**報告的儲存訊息內容**選取屬性)。 如果該交換遭到拒絕，就不會產生任何項目。  
  
 對於傳送或接收的交換，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]儲存下列資訊：  
  
-   交易集內容。 在狀態報告 UI 中，您可以查看交換所包含的交易集，然後再檢視實際的交易集內容。  
  
-   有關交易集的其他詳細資訊包括如下：  
  
|||  
|-|-|  
|資訊|欄位或值|  
|ApplicationSender|(GS02 或\<UNG2.1(UNG2.2)\>|  
|ApplicationReceiver|GS03 或\<UNG3.1(UNG3.2)\>|  
|GroupDate|GS04 或 UNG2.4|  
|GroupTime|GS05 或 UNG2.5|  
|TransactionSetId|ST01 或 UNH2.1 （AN 字串）|  
|InterchangeControlNo|ISA13|  
|GroupControlNo|GS06|  
|BtsDocType|NameSpace + Root 節點名稱|  
|TransactionSetControlID|ST02 或 UNH1|  
|TransactionSetStatus|Accepted、AcceptedWithError 或 Rejected|  
|方向|傳送或接收|  
|BtsProcessingTime|在接收端：做為管線中戳記的 BTSReceiveTime (本地時間)<br /><br /> 在傳送端：由 ASM 元件加上做為信封上戳記的 BTSSendTime (本地時間)|  
|BTS.MessageId|在接收端：來自訊息屬性的 BTSMessageId<br /><br /> 在傳送端：<br /><br /> 對於單一交易集：BTSMessageId<br /><br /> 對於輸出批次： 批次 (不是批次訊息的 BTSMessageId) 中的每個個別訊息的 TransactionSet BTSMessageId**附註：**儲存體只 – 將不會顯示在 UI 中。|  
  
## <a name="see-also"></a>請參閱  
 [EDI 和 AS2 狀態報告的儲存資料](../core/data-stored-for-edi-and-as2-status-reports.md)   
 [針對批次狀態報告儲存的資料](../core/data-stored-for-batching-status-reports.md)   
 [AS2 狀態報告的儲存資料](../core/data-stored-for-as2-status-reports.md)