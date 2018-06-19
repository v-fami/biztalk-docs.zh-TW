---
title: 處理交易 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d360742-e969-4651-b364-9edc6a93b8d4
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 954d0e91e078c7f973bddc22961c760aa4080941
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248150"
---
# <a name="handling-transactions"></a>處理交易
## <a name="transacted-receivers"></a>交易接收方  
 交易接收方與非交易接收方之間主要的差異，在於交易接收方會建立和使用明確的 MSDTC 交易，來確保其資料來源與 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MessageBox 資料庫之間的不可部分完成性。 就配接器的其他部分而言，通常都是相同的。  
  
 應注意的是，要求-回應接收配接器只有在提交原始要求訊息至傳訊引擎時才會使用交易。 從傳訊引擎傳送至配接器的回應傳輸必須使用不同的交易。 這是因為第一個交易的範圍是介於配接器與 MessageBox 資料庫之間。 後續的要求訊息要等到原始要求訊息的交易認可後，才會從傳訊引擎傳送至配接器。  
  
 底下的物件互動示意圖說明交易式提交內送訊息期間，配接器與傳訊引擎之間的互動。 在此範例中，會依序發生下列互動：  
  
1.  配接器從引擎取得新批次。  
  
2.  配接器建立新的 MSDTC 交易。  
  
3.  配接器對已經登錄於交易中的資料來源進行破壞性讀取。  
  
4.  配接器提交訊息。  
  
5.  配接器呼叫**完成**批次，並傳入其 MSDTC 交易並將其**BatchComplete**回呼指標。 引擎傳回**IBTDTCCommitConfirm**介面。  
  
6.  引擎會處理批次、 回呼配接器在其**BatchComplete**實作中，並傳達其訊息給配接器處理狀態。  
  
7.  如果批次成功的配接器會認同交易並呼叫**IBTDTCCommitConfirm.DTCCommitConfirm** API`true`認可的值。  
  
 ![](../core/media/transactedreceiver.gif "TransactedReceiver")  
  
## <a name="transacted-transmitters"></a>交易傳輸器  
 交易配接器絕大部分都和非交易配接器非常相似。 主要的差異，在於交易配接器會將訊息中的資料傳送至已經登錄於 MSDTC 交易中的資源。  
  
 **實作秘訣：** 對於交易傳送，配接器應該使用相同的 MSDTC 交易將資料寫入目的地，以及刪除它透過**IBTTransportBatch.DeleteMessage**方法呼叫。 只需要交易這兩項作業即可。 任何其他作業，例如**IBTTransportBatch.Resubmit**， **IBTTransportBatch.MoveToNextTransport**，和**IBTTransportBatch.MoveToSuspendQ**不需要是交易。 這是因為引擎會隱含地使用交易，而這些作業類型對目的地而言，不必是不可部分完成的。  
  
 底下的物件互動示意圖說明配接器與引擎之間的互動。 事件的順序如下：  
  
1.  引擎從配接器取得新的批次。  
  
2.  引擎將兩個訊息加入至新批次。  
  
3.  引擎會呼叫**完成**批次，促使配接器服務的內部傳輸佇列的批次張貼其執行緒集區。  
  
4.  配接器建立新的 MSDTC 交易。  
  
5.  配接器傳輸訊息，將目的地登錄在 MSDTC 交易中。 例如，可能會是寫入 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 資料庫。  
  
6.  在傳輸之後，配接器從引擎取得新的批次。  
  
7.  配接器呼叫**DeleteMessage**已經成功傳輸的訊息。  
  
8.  配接器呼叫**完成**傳入其 DTC 交易批次。 引擎傳回**IBTDTCCommitConfirm**介面。  
  
9. 引擎處理該批次並從應用程式佇列刪除訊息。  
  
10. 引擎回呼配接器的**IBTBatchCallback**成功刪除作業的相關資訊的介面。  
  
11. 如果批次成功，配接器隨即認可交易。  
  
12. 配接器呼叫**IBTDTCCommitConfirm.DTCCommitConfirm** ，告知引擎已成功認可交易。  
  
 ![](../core/media/transactedtransmitter.gif "Transactedtransmitter")  
  
### <a name="transacted-solicit-response-adapters"></a>交易請求-回應配接器  
 與雙向接收不同，雙向傳送可以使用同一筆 DTC 交易來執行。 交易請求-回應配接器應該使用相同**IBTTransportBatch**如**SubmitResponseMessage**和**DeleteMessage**作業。 這個批次應該使用與用於傳送和接收請求-回應訊息組相同的 MSDTC 交易。 這樣可以確保「請求-回應訊息交換」的不可部份完成性。  
  
## <a name="service-components-and-byot"></a>服務元件和 BYOT  
 使用傳訊引擎 API 時，必須提供 MSDTC 交易。 但有些 .NET 元件是設計用來當做服務元件，不允許透過程式設計方式認可或中止交易， 而是由該平台上的 COM+ 執行階段自動認可交易。  
  
 在這些實例中，配接器應該使用 Bring Your Own Transaction (BYOT)。 這可以讓配接器建立 MSDTC 交易、產生使用交易的 .NET 元件，以及允許該元件繼承已建立的交易而不要建立它自己的交易。 .NET Framework 提供**System.EnterpriseServices.BYOT**針對此目的。 SDK BaseAdapter 提供 helper 類別， **BYOTTransaction**，針對此目的。  
  
## <a name="avoiding-race-conditions"></a>避免競爭條件  
 當您撰寫建立交易物件的配接器，並將它交付至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時，您就有責任要撰寫執行以下工作的程式碼：  
  
-   在與批次關聯的訊息中解決錯誤。  
  
-   決定與批次作業關聯之交易的最後結果。  
  
 配接器必須通知 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 關於交易的最後結果，以維護其內部追蹤資料。 配接器會[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]藉由呼叫結果的**DTCConfirmCommit**。 如果配接器不這麼做，就會發生嚴重的記憶體遺漏。  
  
 以上所列的兩個工作 （解決錯誤，並決定最終的結果） 似乎相當簡單，但事實上它們依賴從不同執行緒的資訊：  
  
-   配接器處理所傳遞的資訊為基礎的錯誤[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]至**BatchComplete**配接器中的回呼。 這個回呼位於配接器的執行緒上。  
  
-   **DTCConfirmCommit**上是一種方法**IBTDTCCommitConfirm**物件。 執行個體**IBTDTCCommitConfirm**批次所傳回物件**ibttransportbatch:: Done**呼叫。 這個執行個體位於相同的執行緒**ibttransportbatch:: Done**呼叫，這是配接器的執行緒不同。  
  
-   配接器對每次呼叫**ibttransportbatch:: Done**沒有對應的回呼**BatchComplete**，也就是呼叫，傳訊引擎不同的執行緒中報告的結果批次提交。 在**BatchComplete**批次的配接器必須認可或回復交易根據是否成功或失敗。 在任一情況下，配接器應該都會接著呼叫**DTCConfirmCommit**回報給傳訊引擎交易的狀態。  
  
 可能的競爭情形存在是因為配接器的實作**BatchComplete**可能會假設**IBTDTCCommitConfirm**所傳回物件**ibttransportbatch:: Done**時一律可以使用**BatchComplete**執行。 不過， **BatchComplete**時，才能呼叫個別的傳訊引擎執行緒，即使之前**ibttransportbatch:: Done**傳回。 可能的配接器嘗試存取**IBTDTCCommitConfirm**物件的一部分**BatchComplete**實作中，沒有發生存取違規。  
  
 在下列範例中，將使用事件來解決問題。 這裡會使用事件的屬性來存取介面指標。 Get 方法永遠會等候 Set 方法完成。  
  
```  
protected IBTDTCCommitConfirm CommitConfirm  
{  
   set  
   {  
       this.commitConfirm = value;  
       this.commitConfirmEvent.Set();  
   }  
   get  
   {  
       this.commitConfirmEvent.WaitOne();  
       return this.commitConfirm;  
   }  
}  
protected IBTDTCCommitConfirm commitConfirm = null;  
private ManualResetEvent commitConfirmEvent = new ManualResetEvent(false);  
```  
  
 現在將指派的傳回值**ibttransportbatch:: Done**給這個屬性，並使用它在**BatchComplete**呼叫。  
  
## <a name="see-also"></a>另請參閱  
 [交易式訊息批次](../core/transactional-message-batches.md)