---
title: 傳送配接器的交換模式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ad65fb5-640d-4bd2-aabe-946210f58a22
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 997aaa9a92f90f30bdaaeb59cc9cecb0c454496f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248350"
---
# <a name="exchange-patterns-for-send-adapters"></a>傳送配接器的交換模式
BizTalk 傳訊引擎是透過網路傳輸，將訊息傳遞給傳送配接器。 這些訊息可能採用單向或雙向的訊息交換模式來傳送。 處理這類雙向訊息交換模式的配接器稱為「請求-回應」配接器。  
  
## <a name="blocking-vs-non-blocking-transmissions"></a>封鎖 vs。非封鎖式傳輸  
 「 傳訊引擎將訊息傳遞至傳送配接器使用**IBTTransmitter.TransmitMessage**方法或**IBTTransmitterBatch.TransmitMessage**方法，取決於是否配接器是批次感知的。 這兩種方法的傳回值都是布林值，指出配接器傳輸訊息的情形。 如果配接器傳回 `true`，表示配接器是在完整送出訊息後才傳回。 在此情況下，傳訊引擎會替配接器代為從 MessageBox 資料庫刪除訊息。 如果配接器傳回 `false`，表示配接器已開始進行訊息傳輸，且於傳輸完成前即傳回。 在此情況下，配接器不僅要負責從應用程式佇列刪除訊息，還得處理傳輸失敗而必須重試傳輸或擱置訊息的狀況。  
  
 配接器傳回`false`是未封鎖的呼叫，表示**TransmitMessage**實作程式碼不會封鎖呼叫執行緒，「 傳訊引擎。 配接器只是將訊息放入記憶體中的佇列以準備傳輸，然後再傳回。 配接器本身應有自己的執行緒集區，用於維護記憶體中的佇列、傳輸訊息，然後將傳輸結果通知引擎。  
  
 傳訊引擎的執行緒通常比用來透過網路傳送資料的執行緒更受限於 CPU 處理能力。 混用這兩種執行緒會對效能造成負面影響。 非封鎖式傳送能分離這兩種執行緒，相較於封鎖式呼叫而言可獲得顯著的效能改善。  
  
 下圖顯示配接器的執行緒集區，其受限的因素偏向於 I/O 作業。 BizTalk Server 傳訊引擎的執行緒集區則大多受限於 CPU 處理能力。 若是保持兩種不同的執行緒集區且不混用相同類型的執行緒，系統運作就會更有效率。  
  
 ![](../core/media/io-cpu-bound-threadpools.gif "Io_cpu_bound_threadpools")  
  
 **效能提示：** 為了達到最佳效能，傳送配接器應封鎖可識別批次。 BizTalk 傳送配接器若從不能識別批次的封鎖式變更為可識別批次的非封鎖式，效能將顯著提升三倍。  
  
 **疑難排解秘訣：** 封鎖傳輸可能會導致整個主控件執行個體的效能降低。 如果配接器過度封鎖了**TransmitMessage**它將使得引擎執行緒無法傳遞訊息給其他配接器。  
  
## <a name="non-batched-sends"></a>非批次傳送  
 不是批次的配接器應該實作**IBTTransmitter**中所詳述[非同步傳送配接器的介面](../core/interfaces-for-an-asynchronous-send-adapter.md)。 針對每個訊息，配接器需要傳輸，傳訊引擎會呼叫**IBTTransmitter.TransmitMessage**。 底下的物件互動示意圖詳盡說明慣常的訊息傳輸方式，其中包含下列步驟：  
  
1.  引擎傳遞訊息給配接器。  
  
2.  配接器將訊息放入記憶體中的佇列以準備傳輸。  
  
3.  配接器的執行緒集區中某個執行緒從佇列取出訊息、讀取訊息的組態，然後透過網路傳輸訊息。  
  
4.  配接器從引擎取得新批次。  
  
5.  配接器呼叫**DeleteMessage**批次，傳入剛才傳輸出去的訊息。  
  
6.  配接器呼叫**完成**批次。  
  
7.  引擎處理該批次並從應用程式佇列刪除訊息。  
  
8.  引擎回呼配接器以通知它的結果**DeleteMessage**作業。  
  
 ![](../core/media/deleting-from-message-queue.gif "Deleting_from_message_queue")  
  
 上面的物件互動示意圖顯示配接器從應用程式佇列刪除單一訊息的情形。 理想情況下，配接器會批次執行多項訊息作業，而不是一次只對一個訊息進行作業。  
  
## <a name="batched-sends"></a>批次傳送  
 批次的配接器應該實作**IBTBatchTransmitter**和**IBTTransmitterBatch**中所詳述[傳送配接器的介面](../core/interfaces-for-send-adapters.md)。 當引擎有訊息傳輸的配接器時，引擎取得新批次從配接器藉由呼叫**IBTBatchTransmitter.GetBatch**。 配接器會傳回新的批次物件實作**IBTTransmitterBatch**。 然後藉由呼叫啟動批次的引擎**IBTTransmitterBatch.BeginBatch**。 此 API 具有輸出參數，讓配接器能夠指定批次中可接受的訊息數目上限。 配接器亦可能選擇性地傳回 DTC 交易。 則引擎會呼叫**IBTTransmitterBatch.TransmitMessage**批次中加入每個外寄訊息一次。 其呼叫次數大於零，但小於或等於配接器所指定的批次大小上限。 當所有訊息都已加入至批次時，配接器會呼叫**IBTTransmitterBatch.Done**。 這時，配接器通常會將批次中的訊息全部放入記憶體中的佇列。 配接器透過本身執行緒集區內一或多個執行緒來傳輸訊息，就像不能識別批次的配接器一樣。 最後，配接器會向引擎通知其傳輸結果。  
  
 底下的物件互動示意圖說明批次傳送配接器如何傳輸兩個訊息。  
  
 ![](../core/media/batchedsends.gif "BatchedSends")  
  
## <a name="handling-transmission-failures"></a>處理傳輸失敗  
 傳輸失敗時的建議做法如下圖所示。 這些只是建議事項，並非傳訊引擎強制限定的做法。 只要理由合理，您可以跳脫這些指導方針自行開發配接器，但屆時務必留意若干常規。 例如，一般來說，當重試次數已達上限之後，配接器都應該將訊息移至備份傳輸。  
  
 通常，傳輸的重試次數可能必須高於設定值。 兩者雖稍有差距卻仍屬合理，因為傳輸層的回復性已有增進。 傳訊引擎所公開的 API 通常設計成盡量賦予配接器最多的控制權。 這種控制方式提供了更完善的責任制度。  
  
 ![](../core/media/handlingerrors.gif "HandlingErrors")  
  
 配接器藉由檢查系統內容屬性決定訊息可重試次數**RetryCount**。 配接器呼叫**重新提交**API 一次針對每個重試嘗試並傳入要重新提交訊息。 隨訊息一併傳入的還有時間戳記，指示引擎應於何時將訊息傳回配接器。 這個值通常是目前的時間加上值**RetryInterval**。 **RetryInterval**是系統的內容屬性的單位是分鐘。 這兩個**RetryCount**和**RetryInterval**訊息內容中是 傳送埠所設定的值。 以向外擴充部署為例，假設有一個 BizTalk 主控件將各執行個體部署至多部電腦。 如果訊息是在重試間隔過後傳遞，則訊息可能會傳遞給設定要在其中執行之任何一部電腦上的任一主控件執行個體。 所以配接器不應保留任何與試圖重試之訊息關聯的狀態，因為無法保證稍後仍會由配接器的相同執行個體負責傳輸。  
  
 一旦重試計數小於或等於零，配接器就只能嘗試將訊息移至備份傳輸。 如果連接埠沒有設定備份傳輸，嘗試將訊息移至備份傳輸便會失敗。 在此情況下應當擱置訊息。  
  
 下列程式碼片段示範如何從訊息內容判斷重試計數和重試間隔，並決定隨後應重新提交或是移至備份傳輸。  
  
```  
using Microsoft.XLANGs.BaseTypes;  
using Microsoft.BizTalk.Message.Interop;  
using Microsoft.BizTalk.TransportProxy.Interop;  
 …  
// RetryCount and RetyInterval are system context properties...  
private static readonly PropertyBase RetryCountProperty =   
 new BTS.RetryCount();  
private static readonly PropertyBase RetryIntervalProperty =   
 new BTS.RetryInterval();  
  
public void HandleRetry(IBaseMessage msg, IBTTransportBatch batch)  
{  
int retryCount = 0;  
int retryInterval = 0;  
  
// Get the RetryCount and RetryInterval off the msg ctx...  
 GetMessageRetryState(msg, out retryCount, out retryInterval);  
  
// If we have retries available resubmit, else move to   
 // backup transport...  
 if ( retryCount > 0 )  
batch.Resubmit(  
 msg, DateTime.Now.AddMinutes(retryInterval));  
else  
batch.MoveToNextTransport(msg);  
}  
  
public void GetMessageRetryState(  
 IBaseMessage msg,   
 out int retryCount,   
 out int retryInterval )  
{  
retryCount = 0;  
retryInterval = 0;  
  
object obj =  msg.Context.Read(  
RetryCountProperty.Name.Name,    
RetryCountProperty.Name.Namespace);   
  
if ( null != obj )  
retryCount = (int)obj;  
  
obj =  msg.Context.Read(  
RetryIntervalProperty.Name.Name,    
RetryIntervalProperty.Name.Namespace);   
  
if ( null != obj )  
retryInterval = (int)obj;  
}  
```  
  
## <a name="throwing-an-exception-from-transmitmessage"></a>從 TransmitMessage 擲回例外狀況  
 如果配接器會擲回例外狀況上任何 Api **IBTTransmitter.TransmitMessage**， **IBTTransmitterBatch.TransmitMessage**， **IBTTransmitterBatch.Done**，引擎相關的訊息傳輸視為傳輸失敗，並採取適當的動作訊息中所述[如何處理配接器失敗](../core/how-to-handle-adapter-failures.md)。  
  
 可識別批次的傳送配接器若在 TransmitMessage API 執行期間擲回例外狀況，就會清除整個批次，並對該批次中的所有訊息執行傳輸失敗時的預設動作。  
  
## <a name="solicit-response"></a>請求-回應  
 雙向傳送配接器通常同時支援單向和雙向傳輸。 傳送配接器會決定是否將訊息應該傳送為單向或雙向傳送藉由檢查**IsSolicitResponse**訊息內容中的系統內容屬性。  
  
 下列程式碼片段示範如何進行：  
  
```  
private bool portIsTwoWay = false;  
private static readonly PropertyBase IsSolicitResponseProperty= new BTS.IsSolicitResponse();  
  
...  
  
 // Port is one way or two way...  
 object obj =  this.message.Context.Read(  
 IsSolicitResponseProperty.Name.Name,    
 IsSolicitResponseProperty.Name.Namespace);   
  
if ( null != obj )  
 this.portIsTwoWay = (bool)obj;  
```  
  
 在請求-回應傳輸期間，配接器會傳輸請求訊息。 完成此步驟後，配接器會提交關聯的回應，並指示傳訊引擎從 MessageBox 資料庫刪除原始請求訊息。 從應用程式佇列刪除訊息與提交回應訊息的動作應該在同一批次的傳輸 Proxy 中執行。 這可確保回應的刪除與提交為不可部分完成的作業。 為達到完全不可部分完成性，配接器應使用 DTC 交易，以一致在相同的 DTC 交易環境下將請求訊息傳輸至可識別交易的資源、提交回應訊息及刪除請求訊息。 一如既往地建議您，傳遞請求訊息請採用非封鎖式傳送。  
  
 下列程式碼片段示範雙向傳送的主要概念。 當引擎呼叫**IBTTransmitter.TransmitMessage**配接器將訊息傳送給記憶體中的佇列。 配接器傳回 `false` 以表示會執行非封鎖式傳送。 配接器的執行緒集區 (**WorkerThreadThunk**) 記憶體中的佇列，並從佇列取出訊息遞交給 helper 方法。 該方法負責傳送請求訊息及接收回應訊息 (此協助程式方法的實作已超出本主題的討論範圍)。回應訊息將提交至引擎，請求訊息則會從應用程式佇列刪除。  
  
```  
using System.Collections;  
using Microsoft.XLANGs.BaseTypes;  
using Microsoft.BizTalk.Message.Interop;  
using Microsoft.BizTalk.TransportProxy.Interop;  
  
     static private Queue _transmitQueue = new Queue();  
  static private IBTTransportProxy _transportProxy = null;   
// IBTTransmitter...  
 public bool TransmitMessage(IBaseMessage msg)  
{  
// Add message to the transmit queue...  
lock(_transmitQueue.SyncRoot)  
 {  
_transmitQueue.Enqueue(msg);  
 }  
  
 return false;  
}  
  
 // Threadpool worker thread...   
private void WorkerThreadThunk()  
{  
try  
{  
 IBaseMessage solicitMsg = null;  
  
 lock(_transmitQueue.SyncRoot)  
 {  
 solicitMsg =   
 (IBaseMessage)_transmitQueue.Dequeue();  
}  
  
 IBaseMessage responseMsg = SendSolicitResponse(   
 solicitMsg );  
Callback cb = new Callback();  
  
IBTTransportBatch batch = _transportProxy.GetBatch(  
 cb, null);  
batch.SubmitResponseMessage( solicitMsg, responseMsg );  
batch.DeleteMessage( solicitMsg );  
batch.Done(null);  
}  
catch(Exception)  
{  
// Handle failure....  
}  
}  
  
static private IBaseMessage SendSolicitResponse(  
 IBaseMessage solicitMsg )  
{  
// Helper method to send solicit message and receive   
 // response message...  
IBaseMessage responseMsg = null;  
return responseMsg;  
}  
```  
  
## <a name="dynamic-sends"></a>動態傳送  
 動態傳送埠沒有配接器組態與其相關聯。 反之，這類傳送埠使用處理常式組態，為配接器提供在動態連接埠上傳輸訊息所需的任何預設屬性。 例如，HTTP 配接器可能需要使用 Proxy 且必須提供憑證。 使用者名稱、密碼和連接埠可指定於處理常式組態中，而由配接器在執行階段予以快取。  
  
 引擎來判斷是，透過傳送動態訊息的傳輸**OutboundTransportLocation**加上配接器的別名。 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝期間，配接器可註冊一或多個別名。 剖析引擎**OutboundTransportLocation**在執行階段尋找相符項目。 配接器會負責處理**OutboundTransportLocation** ，不論前面會加上別名。 下表所示為現成的 BizTalk 配接器註冊的若干別名範例。  
  
|配接器別名|配接器|OutboundTransportLocation 範例|  
|-------------------|-------------|---------------------------------------|  
|HTTP://|HTTP|http://www. MyCompany.com/bar|  
|HTTPS://|HTTP|https://www. MyCompany.com/bar|  
|mailto:|SMTP|mailto:A.User@MyCompany.com|  
|FILE://|FILE|FILE://C:\MyCompany \\%MessageID%.xml|