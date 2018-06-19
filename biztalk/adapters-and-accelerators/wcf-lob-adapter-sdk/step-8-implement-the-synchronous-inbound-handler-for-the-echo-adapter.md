---
title: 步驟 8： 為回應配接器實作的同步輸入處理常式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 723eac73-40c4-41b4-aca1-dd7451d25bfe
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da34bca28f073babac4907b7d408d0642a234e2a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22226630"
---
# <a name="step-8-implement-the-synchronous-inbound-handler-for-the-echo-adapter"></a>步驟 8： 為回應配接器實作的同步輸入處理常式
![步驟 8 的 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-8of9.gif "Step_8of9")  
  
 **若要完成的時間：** 45 分鐘的時間  
  
 在此步驟中，您可以實作輸入的回應配接器的功能。 這項功能可讓配接器接聽的資料或從目標系統的事件。 根據[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，您只需要實作`Microsoft.ServiceModel.Channels.Common.IInboundHandler`時您的配接器是否支援傳入的功能的介面。 [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]會自動產生為您呼叫 EchoAdpterInboundHandler 的衍生的類別。  
  
 在下列區段中，您可以更新 EchoAdpterInboundHandler 類別，以取得更了解如何實作這個介面。 當您完成此步驟中時，您會有回應配接器的工作輸入處理常式。  
  
## <a name="prerequisites"></a>必要條件  
 在開始此步驟之前，您必須已順利完成[步驟 7： 回應配接器實作同步輸出的處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-7-implement-the-synchronous-outbound-handler-for-the-echo-adapter.md)。 基本的認識`Microsoft.ServiceModel.Channels.Common.IInboundHandler`也很有用。  
  
## <a name="the-iinboundhandler-interface"></a>IInboundHandler 介面  
 `Microsoft.ServiceModel.Channels.Common.IInboundHandler`定義為：  
  
```  
public interface IInboundHandler : IConnectionHandler, IDisposable  
{  
          void StartListener(string[] actions, TimeSpan timeout);  
          void StopListener(TimeSpan timeout);  
          bool TryReceive(TimeSpan timeout, out Message message, out IInboundReply reply);  
          bool WaitForMessage(TimeSpan timeout);  
}  
```  
  
 方法描述如下：  
  
|方法|Description|  
|------------|-----------------|  
|StartListener|開始接聽訊息與提供的 Ws-addressing 動作。 如果未指定，它會接聽所有或預設動作。|  
|StopListener|停止接聽。|  
|TryReceive|嘗試從目標系統接收傳入的訊息。|  
|WaitForMessage|等候傳入 WCF 訊息從目標系統。|  
  
 如需有關每個方法參數的描述的詳細資訊，請參閱說明文件`Microsoft.ServiceModel.Channels.Common.IInboundHandler`介面。  
  
## <a name="implementing-the-echoadpterinboundhandler"></a>實作 EchoAdpterInboundHandler  
 回應配接器會使用`System.IO.FileSystemWatcher`模擬目標系統。 在下列程式碼，您會實作內的每個方法`Microsoft.ServiceModel.Channels.Common.IInboundHandler`StartListener、 StopListener、 TryReceive 和 WaitForMessage 介面。  
  
#### <a name="to-implement-iinboundhandler-interface-in-the-echoadpterinboundhandler-class"></a>若要在 EchoAdpterInboundHandler 類別中實作 IInboundHandler 介面  
  
1.  在 [方案總管] 中，按兩下**EchoAdapterInboundHandler.cs**檔案。  
  
2.  在 Visual Studio 編輯器中，將下列幾行加入至現有的 using 指示詞集。  
  
    ```csharp  
    using System.IO;  
    using System.ServiceModel.Channels;  
    using System.Xml;  
    using System.Diagnostics;  
    ```  
  
3.  現在加入 EchoAdapterInboundHandler 類別的類別層級變數。 這些變數可用來監視檔案 」 活動的檔案系統。 以下宣告複製建構函式之前的類別。  
  
    ```csharp  
    private Queue<Message> inboundQueue;  
    private FileSystemWatcher inboundWatcher;  
    private Object inboundQueueSynchronizationLock;  
    private string path;  
    private string filter;  
    ```  
  
4.  EchoAdapterInboundHandler 建構函式在方法內，加入下列程式碼初始化監控基礎結構的檔案，以及擷取篩選條件與監視的路徑。  
  
    ```csharp  
    inboundWatcher = null;  
    inboundQueueSynchronizationLock = new Object();  
    path = connection.ConnectionFactory.Adapter.InboundFileSystemWatcherFolder;  
    filter = connection.ConnectionFactory.Adapter.InboundFileFilter;  
    ```  
  
5.  現在，加入下列程式碼加入**StartListener**方法。 程式碼會實作邏輯，以驗證參數，並開始監視檔案 」 活動。  
  
    ```csharp  
    // if no actions are provided, log an error in the trace log  
    // and throw an exception  
    if (actions.Length == 0)  
    {  
        EchoAdapterUtilities.Trace.Trace(TraceEventType.Error, "http://echoadapterv2/startlistener/noactions", "No operation actions were received for listener to do specific processing.", this);  
        throw new AdapterException("Unable to receive any actions for inbound handler to start listening.");  
    }  
  
    inboundQueue = new Queue<Message>();  
    foreach (string action in actions)  
    {  
        // for the OnReceiveEcho action listen for a new file created event  
        if ("Echo/OnReceiveEcho".Equals(action))  
        {  
            if (inboundWatcher == null)  
            {  
                inboundWatcher = new FileSystemWatcher(path);  
                inboundWatcher.Filter = filter;  
                // Begin monitoring  
                inboundWatcher.EnableRaisingEvents = true;  
            }  
            inboundWatcher.Created += new FileSystemEventHandler(FileMonitor_Created);  
            EchoAdapterUtilities.Trace.Trace(TraceEventType.Information, "http://echoadapterv2/startlistener", "Listening for file created event for " + filter + " in path " + path, this);  
        }  
    }  
    ```  
  
6.  實作新增繼續**StopListener**方法。  
  
    ```csharp  
    if (inboundWatcher != null)  
    {  
        // End monitoring  
        inboundWatcher.EnableRaisingEvents = false;  
        inboundWatcher = null;  
    }  
    lock (inboundQueueSynchronizationLock)  
    {  
        inboundQueue.Clear();  
        inboundQueue = null;  
    }  
    ```  
  
7.  現在提供實作**TryReveive**方法。 這個方法會擷取最新的檔案從內部的佇列接收訊息，如果有的話。  
  
    ```csharp  
    reply = new EchoAdapterInboundReply();  
    message = null;  
    TimeoutHelper timeoutHelper = new TimeoutHelper(timeout);  
    while (true)  
    {  
        lock (inboundQueueSynchronizationLock)  
        {  
            if (inboundQueue == null)  
            {  
                //listener has been closed  
                return false;  
            }  
            if (inboundQueue.Count != 0)  
            {  
                message = inboundQueue.Dequeue();  
                if (message != null)  
                {  
                    return true;  
                }  
            }  
        }  
        if (timeoutHelper.IsExpired)  
        {  
            return false;  
        }  
        //wait for sometime, and check again  
        System.Threading.Thread.Sleep(500);  
    }  
    ```  
  
8.  實作新增繼續**WaitForMessage**方法。  
  
    ```csharp  
    while (inboundQueue.Count == 0) { };  
    Message msg = inboundQueue.Peek();  
    if (msg != null)  
    {  
        return true;  
    }  
    else  
    {  
        return false;  
    }  
    ```  
  
9. 現在提供檔案監看員的回呼。 若要這樣做，將新方法加入**FileMonitor_Created**至**EchoAdapterInboundAdapter**類別。  
  
    ```csharp  
    private void FileMonitor_Created(object sender, FileSystemEventArgs e)  
    {  
        lock (inboundQueueSynchronizationLock)  
        {  
            if (e.ChangeType == WatcherChangeTypes.Created)  
            {  
                // wait for file to close - should do this in a better manner  
                System.Threading.Thread.Sleep(500);  
                try  
                {  
                    EchoAdapterUtilities.Trace.Trace(TraceEventType.Information, "http://echoadapterv2/FileMonitorCreated", "File " + e.FullPath + " created.", this);  
                    FileInfo fileInfo = new FileInfo(e.FullPath);  
                    // Create WCF message to send to the inbound service  
                    // that is listening for messages from adapter  
                    String xmlData = String.Format(@"<OnReceiveEcho xmlns=""{0}""><path>{1}</path><length>{2}</length></OnReceiveEcho>", EchoAdapter.SERVICENAMESPACE, e.FullPath, fileInfo.Length);  
                    // set action string  
                    XmlReader reader = XmlReader.Create(new StringReader(xmlData));  
                    // create WCF message  
                    Message requestMessage = Message.CreateMessage(MessageVersion.Default  
                                , "Echo/OnReceiveEcho"  
                                , reader);  
                    requestMessage.Headers.To = new Uri(path);  
                    inboundQueue.Enqueue(requestMessage);  
                }  
                catch (Exception ex)  
                {  
                    String message = String.Format("An exception was thrown while trying to open file {1}.", e.FullPath);  
                    EchoAdapterUtilities.Trace.Trace(System.Diagnostics.TraceEventType.Error, "http://echoadapterv2/FileMonitorCreated", message, this, ex);  
                    throw new AdapterException(message, ex);  
                }  
            }  
        }  
    }  
    ```  
  
10. 現在您必須移除**NotImplementedException**內部擲回例外狀況**EchoAdapterInboundReply**類別。 若要這樣做，請刪除下列陳述式從**中止**和**回覆**方法。  
  
    ```csharp  
    throw new NotImplementedException("The method or operation is not implemented.");  
    ```  
  
     您**中止**和**回覆**方法應該與下列類似。  
  
    ```csharp  
    /// <summary>  
    /// Abort the inbound reply call  
    /// </summary>  
    public override void Abort()  
    {  
    }  
  
    /// <summary>  
    /// Reply message implemented  
    /// </summary>  
    public override void Reply(System.ServiceModel.Channels.Message message  
        , TimeSpan timeout)  
    {  
    }  
    ```  
  
11. 若要完成之輸入的處理常式的實作，新增下列類別**EchoAdapterOutboundHandler.cs**。 這個類別會提供逾時支援的輸入處理常式實作。  
  
    ```csharp  
    /// <summary>  
    /// Utility class containing helper functions for measuring timeout   
    /// </summary>  
    class TimeoutHelper  
    {  
        private TimeSpan timeout;  
        private DateTime creationTime;  
        private Boolean isInfinite;  
  
        /// <summary>  
        /// Constructor  
        /// </summary>  
        /// <param name="timeout"></param>  
        public TimeoutHelper(TimeSpan timeout)  
        {  
            this.creationTime = DateTime.Now;  
            this.timeout = timeout;  
            if (timeout.Equals(Infinite)) this.isInfinite = true;  
        }  
  
        /// <summary>  
        /// Value of infinite timespan  
        /// </summary>  
        public static TimeSpan Infinite  
        {  
            get { return TimeSpan.MaxValue; }  
        }  
  
        /// <summary>  
        /// Value indicating remaining timeout  
        /// </summary>  
        public TimeSpan RemainingTimeout  
        {  
            get  
            {  
                if (this.isInfinite) return Infinite;  
                return this.timeout.Subtract(DateTime.Now.Subtract(this.creationTime));  
            }  
        }  
  
        /// <summary>  
        /// Get remaining timeout value and throw an exception if the timeout  
        /// has expired.  
        /// </summary>  
        /// <param name="exceptionMessage"></param>  
        /// <returns></returns>  
        public TimeSpan GetRemainingTimeoutAndThrowIfExpired(String exceptionMessage)  
        {  
            if (this.isInfinite) return Infinite;  
            if (RemainingTimeout < TimeSpan.Zero)  
            {  
                throw new TimeoutException(exceptionMessage);  
            }  
            return RemainingTimeout;  
        }  
  
        /// <summary>  
        /// Throw an exception if the timeout has expired.  
        /// </summary>  
        /// <param name="exceptionMessage"></param>  
        public void ThrowIfTimeoutExpired(String exceptionMessage)  
        {  
            if (RemainingTimeout < TimeSpan.Zero)  
            {  
                throw new TimeoutException(exceptionMessage);  
            }  
  
        }  
  
        /// <summary>  
        /// Value indicating whether timeout has expired.  
        /// </summary>  
        public Boolean IsExpired  
        {  
            get  
            {  
                if (this.isInfinite) return false;  
                return RemainingTimeout < TimeSpan.Zero;  
            }  
        }  
    }  
    ```  
  
12. 在 Visual Studio 中，在**檔案**功能表上，按一下 **全部儲存**。  
  
13. 按一下 [ **建置** ] 功能表上的 [ **建置方案**]。 它應該編譯無誤。 如果沒有，請確定您已依照上述每個步驟。  
  
> [!NOTE]
>  您應該已經儲存您的工作結果。 您可以安全地關閉目前的 Visual Studio 或移至下一個步驟中，[步驟 9： 建立及部署回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-9-build-and-deploy-the-echo-adapter.md)。  
  
## <a name="what-did-i-just-do"></a>我剛剛做什麼？  
 在此步驟回應配接器教學課程中，提供您實作輸入處理常式。 此實作會提供檔案監看回應配接器使用的功能**FileSystemWatcher**的.NET Framework 類別。  
  
## <a name="next-steps"></a>後續步驟  
 在下一個步驟中，您可以部署配接器。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 9： 建置並部署回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-9-build-and-deploy-the-echo-adapter.md)   
 [步驟 7： 回應配接器實作同步輸出的處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-7-implement-the-synchronous-outbound-handler-for-the-echo-adapter.md)