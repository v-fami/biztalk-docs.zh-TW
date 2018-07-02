---
title: 如何處理配接器失敗 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bdceb364-38d6-4aab-a176-bf751da1be25
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac87b905d7eb68bdb37a900840f7bd747c92ed77
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971919"
---
# <a name="how-to-handle-adapter-failures"></a>如何處理配接器失敗
一般而言，配接器應該會擱置無法處理的訊息。 舉例來說，雖然是否擱置訊息是依配接器的用途而定，但是發生提交失敗時，接收配接器通常會擱置訊息。 此外，在處理這類失敗時，還必須注意一些安全性考量。 例如，如果配接器自動擱置所有失敗的訊息，表示配接器可能容易受到拒絕服務攻擊，導致 BizTalk Server 擱置佇列被填滿。  某些配接器 (例如 HTTP) 會傳回失敗碼給用戶端，指出要求已遭到拒絕。 就這些配接器類型而言，傳回失敗碼通常會比擱置訊息來得有意義。 一般來說，在用盡主要和次要傳輸的所有重試次數之後，傳送配接器只會擱置訊息。  
  
## <a name="associate-error-processing-with-an-individual-operation-and-not-with-the-batch-that-contains-the-operation"></a>將錯誤處理與個別作業產生關聯，而不與包含作業的批次產生關聯  
 配接器的使用者應該看不到配接器內訊息的批次處理。 這表示，批次中一個作業的失敗不會在任何方面影響到任何其他作業。 然而，批次是不可部分完成的，因此一個訊息的失敗會造成批次的錯誤，並且無法處理任何作業。  
  
 您撰寫負責處理錯誤、重新提交成功訊息並擱置失敗訊息的程式碼。 幸而 BizTalk Server 會提供詳細的錯誤結構，讓您的配接器可以判斷失敗的特定作業， 並且允許建構其他批次以重新提交成功作業並擱置失敗作業。  
  
 作業的最後狀態應該不會受到配接器內批次處理的影響。  
  
## <a name="use-seterrorinfo-to-report-failure-to-biztalk-server"></a>使用 SetErrorInfo 回報失敗給 BizTalk Server  
 如果您要擱置訊息，必須將先前訊息內容中的失敗資訊提供給 BizTalk Server。 BizTalk Server 提供的錯誤報告功能採用**SetErrorInfo**方法兩者**IBaseMessage**並**Seterrorinfo**介面。 您可以使用下列方式報告錯誤：  
  
- 發生失敗時處理訊息時，設定例外狀況**SetErrorInfo (Exception e)** 訊息 (**IBaseMessage**) 暫停。 這可讓引擎保存錯誤和訊息，以便日後進行診斷，並且將錯誤記錄到事件記錄檔中，以警告系統管理員。  
  
- 如果您在初始化或內部簿記期間遇到錯誤 （不是在訊息處理） 應該呼叫**SetErrorInfo (Exception e)** 上**Seterrorinfo**指標傳遞給您在初始化期間。 如果您的配接器以 BaseAdapter 實作為基礎，那麼您應該永遠擁有這個指標的存取權限。 否則，您應該可以快取這個指標。  
  
  使用上述方法報告錯誤會導致錯誤訊息被寫入事件記錄檔。 請務必您將相關的訊息與錯誤您是否能夠執行這項操作。  
  
## <a name="handle-a-database-offline-condition"></a>處理資料庫離線的情況  
 如果其中一個 BizTalk Server 資料庫離線，BizTalk 服務便會自行回收。 傳訊引擎會盡力在回收服務之前，關閉所有接收位置。 如果此關閉程序花費 60 秒以上的時間，服務便會終止。 由於引擎已交易，因此，這不會導致資料遺失。  
  
 使用下列機碼，即可在登錄中調整這個逾時值：  
  
```  
DWORD   
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc{Host Guid}\MessagingDBFailoverShutdownTimeLimit  
```  
  
 如果是外掛式配接器，由於 BizTalk Server 沒有這種程序，因此當其中一個 BizTalk Server 資料庫離線時，會停用接收位置。 當資料庫再次上線後，那些接收位置也將重新啟用。  
  
## <a name="write-to-the-event-log"></a>寫入事件記錄檔  
 配接器可以寫入事件記錄檔項目，使用**IBTTransportProxy**傳入例外狀況的介面。 原生程式碼開發的配接器必須傳入**IErrorInfo**介面**IBTTransportProxy.SetErrorInfo (例外狀況** `e` **)**。  
  
 傳訊引擎會代表配接器，將有關配接器在傳輸失敗後重試訊息、將訊息移到備份傳輸或擱置訊息等事件寫入事件記錄檔。 對於這些作業，配接器只需要在呼叫 API 之前，先在訊息上設定好例外狀況即可。 下列程式碼片段示範如何進行：  
  
```  
IBaseMessage msg;  
...  
// Set exception on msg to indicate why transmission failed...  
msg.SetErrorInfo(  
 new ApplicationException(  
 "The TCP connection was closed by the destination"));  
```  
  
## <a name="handle-receive-specific-batch-errors"></a>處理接收特定批次錯誤  
  
### <a name="handle-receive-failures"></a>處理接收失敗  
 當配接器提交作業 (或作業批次) 給 BizTalk Server 時，可能會因各種不同的原因而造成失敗， 其中最重要的兩個原因為：  
  
- 接收管線失敗。  
  
- 發佈訊息時，發生路由失敗。  
  
  在收到接收管線失敗時，傳訊引擎會自動嘗試擱置訊息， 但是擱置作業不一定每次都會成功。 例如，如果傳訊引擎發佈訊息時，發生路由失敗，然後，引擎不會甚至嘗試擱置訊息。  
  
  訊息隨時可能發生失敗。 在這種情況下，配接器應該明確地呼叫**MoveToSuspendQ** API 並嘗試擱置訊息。 當配接器嘗試擱置訊息時，下列其中一個情形應該會成立：  
  
- 配接器所提交 (建議) 的相同訊息物件應該會遭到擱置。  
  
- 如果配接器必須建立新的訊息，則應該使用原先所提交之訊息內容的指標來設定新訊息的內容。 這是因為訊息的內容會包含許多有關訊息和失敗的有用資訊。 在偵錯失敗的訊息時，必須使用這項資訊。  
  
> [!NOTE]
>  如果配接器建立新的訊息物件並加以擱置，則必須從舊訊息物件將錯誤資訊複製到新訊息物件。  
  
 有些配接器 (例如與 BizTalk Server 一起提供的 HTTP 配接器) 並不需要將訊息擱置。 這些配接器會將錯誤傳回用戶端。  
  
#### <a name="causes-of-failure"></a>造成失敗的原因  
 簡單失敗的原因是隨著建構批次或時，可能會發生的錯誤**ibttransportbatch:: Done**呼叫。  
  
-   **提交失敗。** **送出**呼叫失敗的原因，數量有限，而且所有這些都嚴重。 其中包括：  
  
-   BizTalk Server 程序空間發生記憶體不足錯誤。  
  
-   結構描述組件已從部署中捨棄。 在此情況下，**送出**隱密錯誤而失敗。 在 MQSeries 配接器中，從 BizTalk Server 攔截到一般失敗例外狀況，並且在系統事件記錄檔中寫入擴充錯誤訊息。 這個訊息指示造成此錯誤的其中一個可能原因是，部署已捨棄結構描述組件。  
  
     一般而言，如果**送出**失敗，您應該嘗試擱置訊息使用相同的交易。  
  
-   **Ibttransportbatch:: Done 失敗。** **Ibttransportbatch:: Done**呼叫可能會失敗有數個原因。 一般而言，您應該隨時嘗試執行一個擱置作業，並且只在交易失敗時，結束交易。 其中一個您可能會從失敗的收到的錯誤碼**ibttransportbatch:: Done**是 BizTalk Server 會嘗試關閉。 在此情況下，您應該只是結束交易並將它保留，因為**Terminate**呼叫可能也會同時發生。 當您成功建構批次並順利執行，會發生其他實例**ibttransportbatch:: Done**。 在這些情況下，在傳回的錯誤**BatchComplete**和配接器必須判斷該如何處理它們。 本章節後面的部分將說明如何處理這個情況。  
  
#### <a name="processing-batchcomplete-errors"></a>處理 BatchComplete 錯誤  
 **BatchComplete**是由表示批次作業的完成狀態的 BizTalk Server 叫用配接器所提供的回呼。  
  
 最重要的參數傳遞給**BatchComplete**是批次狀態`hResult`。 這表示批次成功或失敗。 如果批次失敗，即表示批次中的作業不成功。 配接器會通過批次狀態結構，並判斷哪個訊息發生失敗 (這就所謂*篩選批次*)。  
  
#### <a name="nontransactional-batchcomplete-errors"></a>非交易式 BatchComplete 錯誤  
 對於非交易式配接器，您必須選擇您的回應為發生失敗時**SubmitMessage**/**SubmitRequestMessage**或**SubmitResponseMessage**作業。 通常配接器會擱置訊息藉由呼叫**MoveToSuspendQ**。  
  
 下列作業是預期一定會傳遞： **DeleteMessage**， **MoveToSuspendQ**， **ResubmitMessage**。 如果這些作業發生失敗，通常代表配接器存在錯誤。 您不需要以撰寫程式碼方式處理這些情況中的失敗。 不過，如果批次因為其他作業失敗而發生失敗，則必須在全新的批次中重新執行這些作業。  
  
 如果配接器會呼叫**MovetoBackupTransport**卻失敗 （因為沒有備份傳輸），那麼配接器應該呼叫**MoveToSuspendQ**來擱置訊息。  
  
#### <a name="transactional-batchcomplete-errors"></a>交易式 BatchComplete 錯誤  
 當您使用配接器所建立的交易提交批次給 BizTalk Server 時，必須遵守下列其中一個實例：  
  
-   **使用單一訊息批次。** 傳送單一訊息的批次給 BizTalk Server。 如果該單一訊息失敗，您就可以合法地在相同交易下傳送第二個批次給 BizTalk Server，但是您必須將違反的訊息移到擱置佇列，而不是重新提交該訊息。 移除失敗的訊息後，提交第二個批次應該會成功。 之後，您就可以在 BizTalk Server 確認第二個批次提交成功時認可交易。 如果第二個批次失敗，則配接器必須中止交易，或者將該訊息放置在其他位置。 在這個實例中，您很快就會發現交易回呼處理對效能造成很明顯的影響。  
  
     您可以利用一些技術來改善配接器的效能。 例如，MQSeries 配接器會在執行階段動態調整它的方式。 此配接器能夠執行 100 個訊息的批次。 如果發生錯誤，配接器必定會結束批次，但是當它取得以前的錯誤訊息時，便會切換成執行單一訊息批次，並以這樣的方式執行一段時間， 之後再還原成執行 100 個訊息的批次。 如果配接器再次發生錯誤，執行速度也會再次變慢。  
  
-   **使用先佔式擱置。** 建構事先擱置錯誤訊息的多訊息批次。 批次包含混合**提交**並**MoveToSuspendQ**作業，並為第一個和下交易的批次。 由於已事先擱置錯誤的資料，因此批次應該會成功，而交易也能獲得認可 (等候接收 BizTalk Server 的確認訊息之後)。  
  
     未來可能需要再進行深入研究，不過，此技術已經運用到 MSMQ 配接器。 這取決於是否具有確實唯一的訊息識別碼。 此配接器會建構訊息的批次。 如果發生任何失敗，配接器會回復交易 (以及批次)，並且會在暫存資料結構中記住訊息識別碼 (為了避免這個結構無限地擴大，在經過一段固定時間延遲之後，其中的項目就會遭到移除)。每個批次提交出去之前，配接器都會先查看錯誤訊息識別碼的清單。 如果配接器在清單中查到錯誤的訊息識別碼，即得知該訊息將會失敗 (因為以前曾經失敗過)，並且會事先將訊息擱置，而不會嘗試提交批次。  
  
     並非所有配接器都具有確實唯一的訊息識別碼，而交易式儲存區也不太可能會有這樣的訊息識別碼。 基於這個原因，許多交易式配接器都已限制成無法傳送單一訊息的批次。  
  
#### <a name="processing-other-errors"></a>處理其他錯誤  
 在所有其他情況下 (例如擱置訊息的失敗)，配接器都必須結束交易。 任何其他結果可能會產生重複或捨棄的訊息。  
  
 只要在可能的情況下，一旦批次發生失敗，配接器都應該中止交易。 然而，還是有配接器無法中止交易的實例。 在這樣的實例中，配接器應該利用相同的交易來擱置訊息。  
  
#### <a name="processing-errors-on-transactional-receive"></a>處理交易式接收上的錯誤  
 常見的交易式處理模式，是在發生錯誤時結束交易。 在這個情況中，所有事物都會回復到先前的狀態，並且不會遺失任何資料。 然而，如果您要使用交易式摘要中的資料 (例如一次從資料庫中的臨時資料表提取一列，或者一次從 MQSeries 或 MSMQ 之類的佇列產品提取一個訊息)，這對您來說可能不太夠。 如果您只是結束交易，返回後再收取相同的資料，那麼可能會發生相同的錯誤，並且系統會變成困在重複迴圈中。  
  
 舊版 BizTalk Server 中的 SQL 配接器有這個行為。 不過，在隨後發行的版本中，配接器的行為已變更成嘗試擱置失敗的訊息並認可交易。 如果將訊息移到相同交易下的擱置佇列，然後再認可交易，即可將資料儲存起來，免於遺失，同時，還能讓配接器取得以前的錯誤資料。  
  
 配接器的接收部分傳遞時的錯誤訊息以回應**送出**訊息作業時，配接器應該處理該錯誤，並將訊息移到擱置佇列。  
  
 就配接器已經在交易下建立交易物件並提交訊息的交易式批次而言，當發生失敗時，配接器應該以邏輯方式將訊息移到相同交易下的擱置佇列中。 此交易可確保資料不會被捨棄，甚至是造成錯誤的資料也不會遭到捨棄。  
  
### <a name="handle-messages-without-subscriptions"></a>在沒有訂閱的情況下處理訊息  
 BizTalk Server 在沒有定義接受訊息的訂閱時，不接受將訊息發佈到它的 MessageBox 資料庫中。 註冊訂閱的方式為協調流程或傳送埠。 多數訂閱都可以經過定義，而且訊息會傳送到多個目的地。 如果沒有訂閱，BizTalk Server 便會拒絕訊息，而且不會嘗試擱置該訊息。 如果配接器未處理這個錯誤並明確地擱置訊息，那麼訊息便會遭到捨棄，部分的資料可能也會遺失。 當然，交易式配接器可能會結束交易，並將訊息傳回它的目的地。  
  
### <a name="support-seek-with-your-receive-stream"></a>利用您的接收資料流支援 Seek  
 接收端資料流必須支援**搜尋**方法，BizTalk Server 才能擱置管線失敗上的訊息。 如果訊息資料流不是可搜尋，則 BizTalk Server 會嘗試執行時，會產生錯誤**搜尋**。  
  
 在許多情況下，支援**搜尋**並不容易。 舉例來說，資料流處理網路中的資料時，可能難以返回網路資源並再次要求資料。  
  
 數個隨附於 BizTalk Server 的配接器會在 BizTalk Server 讀取訊息資料的同時，將該資料多工緩衝處理到磁碟上的檔案。 這可讓配接器使用**搜尋**對該檔案，如果遇到錯誤 （在管線處理的訊息資料，例如）。 配接器會在內部使用**ReadOnlySeekableStream**類別會包裝內送的非可搜尋資料流，並達到可設定的大小臨界值時，溢位到磁碟。 對於小於閾值大小的訊息，則不會達到磁碟。  
  
### <a name="consider-user-configurable-error-handling-options"></a>考慮使用者可設定的錯誤處理選項  
 有時候可能沒有一個適當的回應能夠回應錯誤。 在這個情形中，您應該考慮採用使用者可設定的選項來選擇行為。 MQSeries 配接器即是如此。  
  
 一旦發生錯誤則配接器就會擱置訊息，其原因在於 BizTalk Server 中的擱置佇列在某種方面而言就如同「黑洞」一般。 將訊息移入佇列比再次收取出來容易。  
  
 某些配接器使用者可能不希望擱置佇列中有任何東西。 舉例來說，MQSeries 配接器所提供的設定選項可讓使用者執行下列其中一個操作：  
  
-   設定配接器在看到錯誤時結束當時的交易，並且自行停用。  
  
-   擱置失敗的訊息並認可交易。 配接器甚至會在 BizTalk Server 已經成功擱置訊息的情況下執行此操作。 即使會造成事件記錄並非完全正確，這個動作還是符合客戶的需求。  
  
### <a name="implement-receive-ordering-by-using-a-single-thread-and-waiting-on-batchcomplete"></a>使用單一執行緒並等候 BatchComplete 以實作接收排序  
 BizTalk Server 的介面是用來支援並行存取所擴充的效能和功能。 然而，如果您希望完全依序接收訊息 (有時必須從 MQSeries 或 MSMQ 之類的訊息佇列產品接收訊息時)，則必須在配接器中執行一些額外的作業，以停用該並行存取。 執行兩個步驟即可完成這個作業：  
  
1. 您必須針對配接器中的所有資料處理使用單一執行緒。  
  
2. 您必須等候 BizTalk Server 徹底地處理完每個批次。 這項需求非常重要，可以利用 .NET 執行緒同步基本來達成。 例如，使用**AutoResetEvent**，您會：  
  
   -   其中兩個主要的背景工作執行緒所存取的事件物件宣告並**BatchComplete**回呼物件。  
  
   -   主工作者執行緒，將訊息提交到批次像往常一樣，但接著呼叫**Ibttransportbatch**之前的批次呼叫在事件物件上**ibttransportbatch:: Done**。  
  
   -   呼叫**AutoResetEvent.WaitOne**從這個相同的執行緒在事件物件上。 這會導致封鎖主工作者執行緒。 在  **BatchComplete**回呼，從 BizTalk Server 接著呼叫**AutoResetEvent.Set**解除封鎖的背景工作執行緒，讓它已準備好處理另一則訊息在相同事件物件上。  
  
   強烈建議所*接收排序*像這可因為這會導致效能大幅降低。 許多使用者實例 (並非大多數) 不需要排序訊息。 此外，擱置訊息可能會破壞排序順序。 在這個情形中要做的就是應用程式相依，對配接器而言最好的做法是提供使用者設定點。  
  
   在排序的實例中，有些客戶已經表明他們偏好停止處理 (亦即停用配接器)，而不是破壞排序。 支援排序接收的 MQSeries 配接器提供使用者這個選項。  
  
## <a name="handle-send-specific-batch-errors"></a>處理傳送特定的批次錯誤  
  
### <a name="handle-send-retry-and-batching"></a>處理傳送重試和批次處理  
 以下是傳送端批次處理的常見範例：  
  
- BizTalk Server 提供訊息的批次給配接器。  
  
- 當配接器判斷它已經正確地將訊息傳送到目的地時，就會在 BizTalk Server 上執行向後刪除，表示操作已完成 (通常可以任意批次處理數個刪除訊息，以改善效能)。  
  
  如果傳送端配接器無法處理訊息，那麼配接器可以利用該訊息執行下列其中一個步驟：  
  
- 配接器應該告知 BizTalk Server 它需要重試訊息。 BizTalk Server 不會自動重試訊息。 BizTalk Server 會保留重試計數，而這個計數會顯示在訊息內容中。  
  
- 配接器可能會判斷出它無法處理訊息。 在這個情形中，配接器可能會將訊息移到下一個傳輸。 配接器會運用**MoveToNextTransport**上呼叫**批次**物件。  
  
- 配接器可以將訊息移到擱置佇列。  
  
  配接器會判斷訊息發生哪些狀況。 不過，它會建議您將配接器會以一致的方式運作，因為這樣會讓 BizTalk Server 安裝支援的工作變得更容易。  
  
  強烈建議配接器最好依照下列所述的方式執行。 隨附於 BizTalk Server 的配接器便具有這樣的行為。  
  
### <a name="recommended-behavior-for-handling-send-errors-in-a-batch"></a>處理批次中傳送錯誤的建議行為  
 傳送配接器會接收到一些訊息，並將那些訊息提交到 BizTalk Server。  
  
 配接器應該在 BizTalk Server 上刪除每個成功的訊息。 所有返回 BizTalk Server 的通訊是透過批次完成的，並且可以批次處理刪除。 它們不一定要是 BizTalk Server 在配接器上建立的相同批次。 如果還有任何回應訊息 (就像 SolicitResponse 實例)，便應該與相關的刪除一起提交回 BizTalk Server (使用 SubmitResponse)。  
  
- 如果配接器中的訊息處理不成功，請檢查重試計數。  
  
  -   如果未超過重試計數，請重新將訊息提交到 BizTalk Server，請記得在訊息上設定重試次數。 訊息內容會提供配接器可以使用的重試計數和重試間隔。  
  
  -   如果已超過重試計數，則配接器應該嘗試將訊息移利用**MoveToNextTransport**。 重新提交並**MoveToNextTransport**訊息可以混合使用相同的批次傳回給 BizTalk Server 中的刪除。 雖然這不是必要操作，但卻是有用的步驟。  
  
- 重新提交並**MoveToNextTransport**配接器處理失敗的方式。 不過失敗的處理中可能存在失敗。 在此情況下，在處理來自 BizTalk Server 的回應 (在**BatchComplete**方法) 的配接器必須建立另一個批次對 BizTalk Server，以指出如何處理該失敗。  
  
   在處理其他失敗的處理內所發生的失敗時，請依照下列步驟執行：  
  
  -   如果重新提交失敗，使用**MoveToNextTransport**。  
  
  -   如果**MoveToNextTransport**失敗，使用**MoveToSuspendQ**。  
  
  您必須持續在 BizTalk Server 上建立批次，直到從 BizTalk Server 接收成功動作為止。  
  
### <a name="serialization-of-message-context-property"></a>訊息內容屬性的序列化  
 所有指派給訊息內容屬性的物件必須是可序列化的， 否則，傳訊引擎會擲回例外狀況型別的**E_NOINTERFACE**。 這個傳回值模糊代表試圖要指派訊息內容的非可序列化物件。