---
title: "批次處理接收訊息處理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 32bf0b70-e9d1-4fab-9c74-160e51390700
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef14179c1af460afc516b7fa331ee30a758219c3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="batching-messages-for-receive-processing"></a>批次處理接收訊息
## <a name="batch-callbacks"></a>批次回呼  
 由接收配接器提交至傳訊引擎的批次是以非同步方式處理。 因此，配接器需要某種機制，將回呼繫結至配接器中的某個狀態，這樣才能夠收到成功或失敗的通知，並執行任何必要的清理動作。 回呼語意相當有彈性，因此配接器可以使用三個方法中的其中一種或任意組合。 它們是：  
  
-   所有的回呼都對物件執行個體實作**IBTBatchCallBack**。  
  
-   使用要求新批次時傳遞到引擎中的 Cookie，使回呼與配接器中的狀態產生相互關聯。  
  
-   沒有實作每個批次的不同的回呼物件**IBTBatchCallBack**。 這裡的每個物件都具有本身的私用狀態。  
  
 當處理批次之後時，配接器回呼的實作**IBTBatchCallBack.BatchComplete**。 批次的整體狀態由第一個參數 HRESULT 狀態顯示出來。 如果這個值大於或等於零，即表示批次已成功，因為引擎具有資料的擁有權，而配接器可以自由地從連線上刪除該項資料。 負數的狀態表示批次失敗：批次中沒有任何作業成功，而配接器將負責處理失敗。  
  
 如果批次失敗，配接器就必須知道是哪一項作業的哪一個項目失敗。 例如，假設配接器從磁碟讀取了 20 個檔案，並使用單一批次將它們提交到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中。 如果第十個檔案已損毀，配接器需要擱置這一個檔案，然後重新提交剩下的 19。 這項資訊可供第二個和第三個參數中的配接器 —`opCount` （作業計數） 的 short 類型和`operationStatus`，BTBatchOperationStatus [] 類型。  
  
> [!NOTE]
>  對於單一批次物件，您絕對不要提交訊息一次以上。 在同一批次上多次提交相同訊息物件會導致引擎錯誤。  
  
 作業計數會指出批次中的多少作業型別是 (大小**BTBatchOperationStatus**陣列)。 作業狀態陣列中的每個元素會對應至指定的作業類型。 使用**BTBatchOperationStatus**陣列，配接器可以判斷哪一個項目中指定的作業無法藉由查看**BTBatchOperationStatus.MessageStatus**負數 HRESULT 的陣列值表示失敗。 在上面的實例中，配接器會建立一個新批次，其中包含 19 個訊息提交和 1 個訊息擱置。  
  
 下列程式碼片段顯示配接器如何透過傳輸 Proxy 向引擎要求新批次，並使用 Cookie 的方式提交單一訊息到引擎中。 傳訊引擎會呼叫**BatchComplete**它已完成處理整個批次的批次回呼方法提交訊息。  
  
```  
using Microsoft.BizTalk.TransportProxy.Interop;  
using Microsoft.BizTalk.Message.Interop;  
  
public class MyAdapter :   
                  IBTTransport,   
                  IBTTransportConfig,   
                  IBTTransportControl,  
                  IPersistPropertyBag,   
                  IBaseComponent,  
                  IBTBatchCallBack  
{  
      private IBTTransportProxy _tp;  
  
      public void BatchComplete(      
            Int32                         status,   
            Int16                         opCount,   
            BTBatchOperationStatus[]      operationStatus,   
            System.Object                 callbackCookie)  
      {  
            // Use cookie to correlate callback with work done,  
            // in this example the batch is to submit a single  
            // file the name of which will be in the  
            // callbackCookie  
            string fileName = (string)callbackCookie;  
            if ( status >= 0 )  
                  // DeleteFile from disc  
                  File.Delete(fileName);          
            else  
                  // Rename file to fileName.bad  
                  File.Move(fileName, fileName + ".bad");  
      }  
  
      private void SubmitMessage(  
            IBaseMessage                  msg,   
            string                        fileName)  
      {  
            // Note: Pass in the filename as the cookie  
            IBTTransportBatch batch =   
                  _tp.GetBatch(this, (object)fileName);  
  
            // Add msg to batch for submitting   
            batch.SubmitMessage(msg);   
  
            // Process this batch  
            batch.Done(null);  
      }  
}  
```  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SDK 包含下列配接器的範例：FILE、HTTP、MSMQ 和交易式配接器。 這些配接器全都是建立一個通用建置組塊上，稱為 BaseAdapter。 BaseAdapter 的 1.0.1 版包含所有相關的程式碼，可用來剖析作業狀態和重建新批次以進行提交。  
  
## <a name="race-condition"></a>競爭情形  
 解決錯誤以及決定提交批次最後結果的這兩項工作，似乎相當簡單，但事實上它們需要依賴來自不同執行緒的資訊：  
  
-   配接器處理所傳遞的資訊為基礎的錯誤[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]至配接器的**BatchComplete**回呼方法。 這個回呼會在配接器的執行緒上執行。  
  
-   **DTCCommitConfirm**上是一種方法**IBTDTCCommitConfirm**物件。 執行個體**IBTDTCCommitConfirm**批次所傳回物件**ibttransportbatch:: Done**呼叫。 這個執行個體位於相同的執行緒**ibttransportbatch:: Done**呼叫，這是配接器的回呼執行緒不同。  
  
 配接器對每次呼叫**ibttransportbatch:: Done**傳訊引擎會回呼方法的對應呼叫**BatchComplete**中個別的執行緒，報告的結果批次提交。 在**BatchComplete**批次的配接器必須認可或回復交易根據是否成功或失敗。 在任一情況下，配接器應該都會接著呼叫**DTCCommitConfirm**報告交易的狀態。  
  
 可能的競爭情形存在是因為配接器的實作**BatchComplete**可能會假設**IBTDTCCommitConfirm**所傳回物件**ibttransportbatch:: Done**時一律可以使用**BatchComplete**執行。 不過， **BatchComplete**時，才能呼叫個別的傳訊引擎執行緒，即使之前**ibttransportbatch:: Done**傳回。 可能的配接器嘗試存取**IBTDTCCommitConfirm**物件的一部分**BatchComplete**實作中，會發生存取違規，因為該呼叫執行緒不再存在。 請使用下列解決方法來避免這個情形。  
  
 在下列範例中，將使用事件來解決問題。 這裡會使用事件的屬性來存取介面指標。 Get 方法永遠會等到 Set 方法完成後才繼續。  
  
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
  
## <a name="batch-status-codes"></a>批次狀態碼  
 整體批次狀態碼會指出批次處理的結果。 作業狀態會提供提交狀態碼給個別訊息項目。 批次失敗的原因有很多種。 可能是發生有關安全性的失敗，或是當提交訊息時，引擎正在關閉 (引擎關閉時通常不會接受任何新工作，但是會允許正在進行中的工作完成)。下表顯示批次狀態或作業狀態傳回的一些常見 HRESULT 值。 同時也會指出這些值是成功碼，還是失敗碼。 這些代碼的正確處理於更完整的說明[如何處理配接器失敗](../core/how-to-handle-adapter-failures.md)。  
  
|代碼 (在類別 BTTransportProxy 中定義)|成功/失敗碼|Description|  
|----------------------------------------------------|---------------------------|-----------------|  
|BTS_S_EPM_SECURITY_CHECK_FAILED|成功|連接埠已設定為執行安全性檢查，並捨棄驗證失敗的訊息。 配接器不會擱置傳回這個狀態碼的批次。|  
|BTS_S_EPM_MESSAGE_SUSPENDED|成功|表示有一則或多則訊息被擱置，而引擎具有資料的擁有權。 這是成功碼，因為傳訊引擎已經接受訊息提交。|  
|E_BTS_URL_DISALLOWED|失敗|無效的送出訊息**InboundTransportLocation**。|  
  
## <a name="batch-operations"></a>批次作業  
 下表詳細說明的成員方法和操作的**IBTTransportBatch**配接器使用將工作新增至指定的批次的物件。  
  
|方法名稱|作業類型|Description|  
|-----------------|--------------------|-----------------|  
|**SubmitMessage**|提交|將訊息提交到引擎中。|  
|**SubmitResponseMessage**|提交|將回應訊息提交到引擎中。 這是成對的「請求-回應」中的回應訊息。|  
|**DeleteMessage**|DELETE|刪除因為配接器使用非封鎖傳送方式透過連線成功傳輸而產生的訊息。 使用封鎖傳送配接器不需要呼叫這個方法，因為 「 傳訊引擎會執行刪除代替配接器的配接器傳回`true`從**TransmitMesssage**。|  
|**MoveToSuspendQ**|MoveToSuspendQ|將訊息移到訊息擱置佇列中。|  
|**重新提交**|Resubmit|要求稍後重新嘗試傳送訊息。 這通常會在傳輸嘗試失敗之後被呼叫。|  
|**MoveToNextTransport**|MoveToNextTransport|要求使用其備份傳輸來傳送訊息。 這通常會在用盡所有嘗試次數而仍失敗之後被呼叫。 如果沒有備份傳輸，這個方法將會失敗|  
|**SubmitRequestMessage**|SubmitRequest|提交要求訊息。 這是成對的「要求-回應」中的要求訊息。|  
|**CancelRequestForResponse**|CancelRequestForResponse|通知引擎：配接器已經不再等待成對的「要求-回應」中的回應訊息。|  
|**Clear**|NA|從批次清除所有工作。|  
|**完成**|NA|將訊息批次提交給引擎進行處理。|  
  
## <a name="batch-management"></a>批次管理  
 批次是在傳訊引擎中以原生程式碼來實作的。 因此，以 Managed 程式碼撰寫的配接器應該在完成批次後，為批次發佈執行階段可呼叫包裝函式 (RCW)。 這是由 managed 程式碼中使用**Marshal.ReleaseComObject**應用程式開發介面。 請務必記得要在 while 迴圈中呼叫這個 API，直到傳回的參考計數到達零為止。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會在同步處理同一批次中的訊息。 您可以並行處理許多批次，如此可以藉由調整應用程式定義域中的批次大小，在配接器中進行一些最佳化工作。 例如，您可以處理 FTP 網站上的所有檔案 (直到達到某個限制為止)。 在 SAP 的情況下，您可以將單一資料流處理成一些接下來會以批次方式提交的訊息。  
  
 配接器使用來將作業傳遞回 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的批次，並不需要完全對應 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供給配接器的訊息清單。 也就是說，執行交易傳送時您必須將分割重新提交作業**MoveToNextTransport**和**MoveToSuspendQ**成個別的批次。 許多配接器會將已經提交給多個結束點的訊息批次區分為不同的訊息清單，以作進一步處理。  
  
 要注意的是，在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，並沒有與訊息批次處理相關的規則 (除了與交易關聯的規則之外)。 批次處理只是配接器用來將訊息劃分成進出 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 之區塊的特定實作方式。  
  
 配接器可以將 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供的多個較小批次中的訊息，批次處理成較大批次以回應 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 這在處理大量小型訊息的交易式配接器中，可能是一項重大的最佳化成果。 它會將「每則訊息的交易總數」比率降至最低。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 一般會產生介於 5 和 10 則訊息的傳送端批次。 如果這些是非常小的訊息，配接器可能會批次最多 100 個訊息或多個之前它會將之刪除交易式批次提交回[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 像這樣的最佳化並不容易實作；您必須確定訊息不會滯留於配接器記憶體中，無止境地等待達到某個閾值。  
  
 像是 MQSeries 這類具有高處理能力的配接器，會在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的批次處理上展現可觀的效能。 這些配接器是以至少為傳送頻率兩倍的頻率來接收訊息。 根據預設，接收配接器會使用含有 100 則訊息的批次；傳送配接器會使用指定的預設 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 批次。  
  
## <a name="transactional-batches"></a>交易批次  
 當您撰寫建立交易物件的配接器，並將它交付至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時，您就有責任要撰寫執行以下工作的程式碼：  
  
-   決定批次作業的最後結果：認可或結束交易。 此結果可能取決於這個並非依存於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 之交易範圍內的其他交易分支，例如寫入訊息佇列 (MSMQ) 佇列或交易式資料庫作業。  
  
-   通知[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]藉由呼叫的最後結果的**IBTDTCCommitConfirm.DTCCommitConfirm**方法。 傳回 `true` 即表示成功認可交易；傳回 `false` 則代表交易失敗和回復。  
  
 配接器必須通知 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 關於交易的最後結果，以維護其內部追蹤資料。 配接器會[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]藉由呼叫結果的**DTCCommitConfirm**。 如果配接器不這麼做，就會發生嚴重的記憶體遺漏，而且即使作業成功完成，MSDTC 交易還是會逾時並失敗。