---
title: "相互關聯的內送交易集與外寄批次 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fbe40f8-7379-42be-b8a7-070ce8a7ce26
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ddd5a1ec83db1177050711d82bfb465c2bcb7637
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="correlating-an-incoming-transaction-set-with-an-outgoing-batch"></a>使內送交易集與外寄批次相互關聯
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可讓您將提交至「批次處理協調流程」的 EDI 交易集與外寄批次相互關聯。 您可以透過讓提交至「批次處理協調流程」(BTSInterchangeID) 的狀態報告項目與協調流程 (ActivityID) 的狀態報告項目相互關聯，藉此完成這項操作。 此相互關聯是使用 BusinessMessageJournal BAM 活動中的項目執行。 這些項目是由「批次處理協調流程」在接收批次元素時建立。  
  
> [!IMPORTANT]
>  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI 狀態報告和交易集 」 追蹤已啟用協議時，才會建立在 BusinessMessageJournal 活動中的項目。  
  
 下列章節會說明下列內容：  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 如何儲存追蹤資料  
  
-   如何建立自訂管線元件來啟用相互關聯  
  
-   如何使內送交易集與外寄批次相互關聯  
  
-   如何在已知批次中所包含交易集的 BTSInterchangeID 時查詢 BusinessMessageJournal 活動以判斷批次的 BTSInterchangeID。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
## <a name="changes-to-the-activities"></a>活動的變更  
 「批次處理協調流程」會在 BatchingActivity、TransactionSetActivity 和 BusinessMessageJournal BAM 活動中建立項目。 為交易集通過[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會在交易集合與包含它的批次這些活動資料表中進行下列項目：  
  
1.  當 EDI 解譯器處理內送 EDI 交換時，會在 InterchangeStatusActivity 和 TransactionSetActivity 資料表中建立項目。  
  
    > [!NOTE]
    >  如需 BAM 活動的詳細資訊，請參閱[追蹤 EDI AS2 訊息的 BAM 活動建立](../core/bam-activities-created-to-track-edi-as2-messages.md)。  
  
2.  當「批次處理協調流程」產生時，協調流程就會在 BatchingActivity 中建立一個項目。 BAM 子系統會為 ActivityID 建立一個值。  
  
3.  批次處理協調流程挑選了交易集之後，就會在 TransactionSetActivity 資料表中建立交易集的項目。  
  
4.  協調流程會在 BusinessMessageJournal 活動中建立一個項目。 它會將此活動的 MessageTrackingID 欄位設定為協調流程在 TransactionSetActivity 資料表中所建立項目的 ActivityID 欄位值。 此外還會將 BTSInterchangeID 欄位設為交易集的 BTS.InterchangeID 內容屬性，以及將 BTSMessageID 欄位設為交易集的 BTS.MessageID 內容屬性。  
  
5.  協調流程會在 BusinessMessageJournal 活動中建立第二個項目。 它會將 MessageTrackingID 欄位設定為協調流程在 TransactionSetActivity 資料表中所建立項目的 ActivityID 欄位， 以及將 BTSInterchangeID 欄位設為批次的 BTS.InterchangeID 內容屬性。 不過不會設定 BTSMessageID。 另外還會將 ContainerActivityID 設為 BatchingActivity 中 ActivityID 的值。  
  
## <a name="creating-a-custom-pipeline-component-for-enabling-correlation"></a>建立自訂管線元件來啟用相互關聯  
 若要建立內送交易集與包含交易集的外寄批次之間的相互關聯，您必須建立自訂管線元件。 此管線元件應在 EDI 解譯器之後，並且在 EDIReceive 管線的 BatchMarker 元件之前。 此管線元件必須在 BusinessMessageJournal 活動中建立一個項目。 在此項目中，BTSInterchangeID 欄位應設為 BTS.InterchangeID 內容屬性，而 BTSMessageID 欄位應設為 BTS.MessageID 內容屬性。  
  
## <a name="looking-up-the-interchangeid-for-a-transaction-set-in-a-batch"></a>查閱批次中交易集的 InterchangeID  
 您可以透過使用 BatchingActivity 資料表和 BusinessMessageJournal 活動中的項目，使收到的交換與包含交換中交易集的批次相互關聯，如下所述。  
  
### <a name="to-correlate-an-incoming-transaction-set-with-an-outgoing-batch-that-contains-that-transaction-set"></a>使內送交易集與包含該交易集的外寄批次相互關聯  
  
1.  判斷 BatchingActivity 資料表中批次的 ActivityID 值。  
  
2.  在 BusinessMessageJournal 活動資料表的 ContainerActivityID 欄位中搜尋 ActivityID 值。  
  
3.  在 ContainerActivityID 識別的記錄中，查閱與批次相關聯的 MessageTrackingID 欄位值。  
  
4.  使用與 BusinessMessageJournal 活動資料表中批次相關聯的 MessageTrackingID 欄位值，在 BusinessMessageJournal 活動資料表中其他記錄的 MessageTrackingID 欄位中搜尋相同的值。 找到的所有記錄都會與批次中的交易集相關，如同「批次處理協調流程」所記錄。  
  
5.  在與 BusinessMessageJournal 活動資料表中交易集相關的記錄中，查閱 BTSInterchangeID 欄位的值。  
  
6.  您可以使用 BTSInterchangeID 的值，查閱之前在 BusinessMessageJournal 活動資料表中建立的交易集記錄，如自訂管線元件所記錄。 您也可以查閱 TransactionSetActivity 資料表中的交易集記錄。  
  
## <a name="querying-businessmessagejournal"></a>查詢 BusinessMessageJournal  
 如果交易集報告已啟用，而且您知道所收到交換的 BTSInterchangeID，則可以使用下列 [SQL 查詢] 找出包含提交至「批次處理協調流程」之交易集的批次 BTSInterchangeID。 您可以使用此程式碼建立自訂應用程式，以檢視批次中的訊息。  
  
> [!IMPORTANT]
>  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI 狀態報告和交易集 」 追蹤已啟用協議時，才會建立在 BusinessMessageJournal 活動中的項目。  
  
```  
Select MessageTrackingID  
From BusinessMessageJournal  
Where BTSInterchangeID = <given InterchangeID of the receive interchange>  
  
Select BTSInterchangeID  
From BusinessMessageJournal  
Where MessageTrackingID = <MessageTrackingID from the previous query> and BTSInterchangeID = <given InterchangeID>  
```  
  
## <a name="see-also"></a>另請參閱  
 [建立追蹤 EDI AS2 訊息的 BAM 活動](../core/bam-activities-created-to-track-edi-as2-messages.md)   
 [啟用 EDI 和 AS2 狀態報告](../core/enabling-edi-and-as2-status-reports.md)