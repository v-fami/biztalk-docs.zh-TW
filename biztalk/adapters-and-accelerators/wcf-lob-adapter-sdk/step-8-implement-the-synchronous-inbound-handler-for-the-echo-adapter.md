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
# <a name="step-8-implement-the-synchronous-inbound-handler-for-the-echo-adapter"></a><span data-ttu-id="5ea93-102">步驟 8： 為回應配接器實作的同步輸入處理常式</span><span class="sxs-lookup"><span data-stu-id="5ea93-102">Step 8: Implement the Synchronous Inbound Handler for the Echo Adapter</span></span>
<span data-ttu-id="5ea93-103">![步驟 8 的 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-8of9.gif "Step_8of9")</span><span class="sxs-lookup"><span data-stu-id="5ea93-103">![Step 8 of 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-8of9.gif "Step_8of9")</span></span>  
  
 <span data-ttu-id="5ea93-104">**若要完成的時間：** 45 分鐘的時間</span><span class="sxs-lookup"><span data-stu-id="5ea93-104">**Time to complete:** 45 minutes</span></span>  
  
 <span data-ttu-id="5ea93-105">在此步驟中，您可以實作輸入的回應配接器的功能。</span><span class="sxs-lookup"><span data-stu-id="5ea93-105">In this step, you implement the inbound capability of the echo adapter.</span></span> <span data-ttu-id="5ea93-106">這項功能可讓配接器接聽的資料或從目標系統的事件。</span><span class="sxs-lookup"><span data-stu-id="5ea93-106">This capability allows the adapter to listen for data or events from the target system.</span></span> <span data-ttu-id="5ea93-107">根據[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，您只需要實作`Microsoft.ServiceModel.Channels.Common.IInboundHandler`時您的配接器是否支援傳入的功能的介面。</span><span class="sxs-lookup"><span data-stu-id="5ea93-107">According to the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], you only need to implement the `Microsoft.ServiceModel.Channels.Common.IInboundHandler` interface, when your adapter supports inbound capability.</span></span> <span data-ttu-id="5ea93-108">[!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]會自動產生為您呼叫 EchoAdpterInboundHandler 的衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="5ea93-108">The [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] automatically generates the derived class called EchoAdpterInboundHandler for you.</span></span>  
  
 <span data-ttu-id="5ea93-109">在下列區段中，您可以更新 EchoAdpterInboundHandler 類別，以取得更了解如何實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="5ea93-109">In the following section, you update the EchoAdpterInboundHandler class to get a better understanding on how to implement this interface.</span></span> <span data-ttu-id="5ea93-110">當您完成此步驟中時，您會有回應配接器的工作輸入處理常式。</span><span class="sxs-lookup"><span data-stu-id="5ea93-110">When you complete this step, you have a working inbound handler for the echo adapter.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5ea93-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="5ea93-111">Prerequisites</span></span>  
 <span data-ttu-id="5ea93-112">在開始此步驟之前，您必須已順利完成[步驟 7： 回應配接器實作同步輸出的處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-7-implement-the-synchronous-outbound-handler-for-the-echo-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="5ea93-112">Before you begin this step, you must have successfully completed [Step 7: Implement the Synchronous Outbound Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-7-implement-the-synchronous-outbound-handler-for-the-echo-adapter.md).</span></span> <span data-ttu-id="5ea93-113">基本的認識`Microsoft.ServiceModel.Channels.Common.IInboundHandler`也很有用。</span><span class="sxs-lookup"><span data-stu-id="5ea93-113">A basic familiarity with `Microsoft.ServiceModel.Channels.Common.IInboundHandler` is also helpful.</span></span>  
  
## <a name="the-iinboundhandler-interface"></a><span data-ttu-id="5ea93-114">IInboundHandler 介面</span><span class="sxs-lookup"><span data-stu-id="5ea93-114">The IInboundHandler Interface</span></span>  
 <span data-ttu-id="5ea93-115">`Microsoft.ServiceModel.Channels.Common.IInboundHandler`定義為：</span><span class="sxs-lookup"><span data-stu-id="5ea93-115">The `Microsoft.ServiceModel.Channels.Common.IInboundHandler` is defined as:</span></span>  
  
```  
public interface IInboundHandler : IConnectionHandler, IDisposable  
{  
          void StartListener(string[] actions, TimeSpan timeout);  
          void StopListener(TimeSpan timeout);  
          bool TryReceive(TimeSpan timeout, out Message message, out IInboundReply reply);  
          bool WaitForMessage(TimeSpan timeout);  
}  
```  
  
 <span data-ttu-id="5ea93-116">方法描述如下：</span><span class="sxs-lookup"><span data-stu-id="5ea93-116">The method descriptions are:</span></span>  
  
|<span data-ttu-id="5ea93-117">方法</span><span class="sxs-lookup"><span data-stu-id="5ea93-117">Method</span></span>|<span data-ttu-id="5ea93-118">Description</span><span class="sxs-lookup"><span data-stu-id="5ea93-118">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="5ea93-119">StartListener</span><span class="sxs-lookup"><span data-stu-id="5ea93-119">StartListener</span></span>|<span data-ttu-id="5ea93-120">開始接聽訊息與提供的 Ws-addressing 動作。</span><span class="sxs-lookup"><span data-stu-id="5ea93-120">Starts listening to messages with the provided WS-Addressing Actions.</span></span> <span data-ttu-id="5ea93-121">如果未指定，它會接聽所有或預設動作。</span><span class="sxs-lookup"><span data-stu-id="5ea93-121">If none is specified, it listens to all or the default actions.</span></span>|  
|<span data-ttu-id="5ea93-122">StopListener</span><span class="sxs-lookup"><span data-stu-id="5ea93-122">StopListener</span></span>|<span data-ttu-id="5ea93-123">停止接聽。</span><span class="sxs-lookup"><span data-stu-id="5ea93-123">Stops listening.</span></span>|  
|<span data-ttu-id="5ea93-124">TryReceive</span><span class="sxs-lookup"><span data-stu-id="5ea93-124">TryReceive</span></span>|<span data-ttu-id="5ea93-125">嘗試從目標系統接收傳入的訊息。</span><span class="sxs-lookup"><span data-stu-id="5ea93-125">Tries to receive an inbound message from the target system.</span></span>|  
|<span data-ttu-id="5ea93-126">WaitForMessage</span><span class="sxs-lookup"><span data-stu-id="5ea93-126">WaitForMessage</span></span>|<span data-ttu-id="5ea93-127">等候傳入 WCF 訊息從目標系統。</span><span class="sxs-lookup"><span data-stu-id="5ea93-127">Waits for an inbound WCF message from the target system.</span></span>|  
  
 <span data-ttu-id="5ea93-128">如需有關每個方法參數的描述的詳細資訊，請參閱說明文件`Microsoft.ServiceModel.Channels.Common.IInboundHandler`介面。</span><span class="sxs-lookup"><span data-stu-id="5ea93-128">For more details on the description for each method parameters, see the documentation on the `Microsoft.ServiceModel.Channels.Common.IInboundHandler` interface.</span></span>  
  
## <a name="implementing-the-echoadpterinboundhandler"></a><span data-ttu-id="5ea93-129">實作 EchoAdpterInboundHandler</span><span class="sxs-lookup"><span data-stu-id="5ea93-129">Implementing the EchoAdpterInboundHandler</span></span>  
 <span data-ttu-id="5ea93-130">回應配接器會使用`System.IO.FileSystemWatcher`模擬目標系統。</span><span class="sxs-lookup"><span data-stu-id="5ea93-130">The echo adapter uses the `System.IO.FileSystemWatcher` to simulate the target system.</span></span> <span data-ttu-id="5ea93-131">在下列程式碼，您會實作內的每個方法`Microsoft.ServiceModel.Channels.Common.IInboundHandler`StartListener、 StopListener、 TryReceive 和 WaitForMessage 介面。</span><span class="sxs-lookup"><span data-stu-id="5ea93-131">In the following, you implement each method within the `Microsoft.ServiceModel.Channels.Common.IInboundHandler` interface, StartListener, StopListener, TryReceive and WaitForMessage.</span></span>  
  
#### <a name="to-implement-iinboundhandler-interface-in-the-echoadpterinboundhandler-class"></a><span data-ttu-id="5ea93-132">若要在 EchoAdpterInboundHandler 類別中實作 IInboundHandler 介面</span><span class="sxs-lookup"><span data-stu-id="5ea93-132">To implement IInboundHandler interface in the EchoAdpterInboundHandler class</span></span>  
  
1.  <span data-ttu-id="5ea93-133">在 [方案總管] 中，按兩下**EchoAdapterInboundHandler.cs**檔案。</span><span class="sxs-lookup"><span data-stu-id="5ea93-133">In Solution Explorer, double-click the **EchoAdapterInboundHandler.cs** file.</span></span>  
  
2.  <span data-ttu-id="5ea93-134">在 Visual Studio 編輯器中，將下列幾行加入至現有的 using 指示詞集。</span><span class="sxs-lookup"><span data-stu-id="5ea93-134">In the Visual Studio editor, add the following lines to the existing set of using directives.</span></span>  
  
    ```csharp  
    using System.IO;  
    using System.ServiceModel.Channels;  
    using System.Xml;  
    using System.Diagnostics;  
    ```  
  
3.  <span data-ttu-id="5ea93-135">現在加入 EchoAdapterInboundHandler 類別的類別層級變數。</span><span class="sxs-lookup"><span data-stu-id="5ea93-135">Now add class level variables to the EchoAdapterInboundHandler class.</span></span> <span data-ttu-id="5ea93-136">這些變數可用來監視檔案 」 活動的檔案系統。</span><span class="sxs-lookup"><span data-stu-id="5ea93-136">These variables are used to monitor the file system for file activity.</span></span> <span data-ttu-id="5ea93-137">以下宣告複製建構函式之前的類別。</span><span class="sxs-lookup"><span data-stu-id="5ea93-137">Copy the declarations below into the class before the constructor.</span></span>  
  
    ```csharp  
    private Queue<Message> inboundQueue;  
    private FileSystemWatcher inboundWatcher;  
    private Object inboundQueueSynchronizationLock;  
    private string path;  
    private string filter;  
    ```  
  
4.  <span data-ttu-id="5ea93-138">EchoAdapterInboundHandler 建構函式在方法內，加入下列程式碼初始化監控基礎結構的檔案，以及擷取篩選條件與監視的路徑。</span><span class="sxs-lookup"><span data-stu-id="5ea93-138">Inside the EchoAdapterInboundHandler constructor method, add the following code to initialize the file watching infrastructure and to capture the monitoring path and filter.</span></span>  
  
    ```csharp  
    inboundWatcher = null;  
    inboundQueueSynchronizationLock = new Object();  
    path = connection.ConnectionFactory.Adapter.InboundFileSystemWatcherFolder;  
    filter = connection.ConnectionFactory.Adapter.InboundFileFilter;  
    ```  
  
5.  <span data-ttu-id="5ea93-139">現在，加入下列程式碼加入**StartListener**方法。</span><span class="sxs-lookup"><span data-stu-id="5ea93-139">Now add the following code to the **StartListener** method.</span></span> <span data-ttu-id="5ea93-140">程式碼會實作邏輯，以驗證參數，並開始監視檔案 」 活動。</span><span class="sxs-lookup"><span data-stu-id="5ea93-140">The code implements logic to verify parameters and start monitoring for file activity.</span></span>  
  
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
  
6.  <span data-ttu-id="5ea93-141">實作新增繼續**StopListener**方法。</span><span class="sxs-lookup"><span data-stu-id="5ea93-141">Continue by adding an implementation for the **StopListener** method.</span></span>  
  
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
  
7.  <span data-ttu-id="5ea93-142">現在提供實作**TryReveive**方法。</span><span class="sxs-lookup"><span data-stu-id="5ea93-142">Now provide an implementation for the **TryReveive** method.</span></span> <span data-ttu-id="5ea93-143">這個方法會擷取最新的檔案從內部的佇列接收訊息，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="5ea93-143">This method retrieves the most recent file receive message from the internal queue if one is available.</span></span>  
  
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
  
8.  <span data-ttu-id="5ea93-144">實作新增繼續**WaitForMessage**方法。</span><span class="sxs-lookup"><span data-stu-id="5ea93-144">Continue by adding an implementation for the **WaitForMessage** method.</span></span>  
  
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
  
9. <span data-ttu-id="5ea93-145">現在提供檔案監看員的回呼。</span><span class="sxs-lookup"><span data-stu-id="5ea93-145">Now supply the callback for the file watcher.</span></span> <span data-ttu-id="5ea93-146">若要這樣做，將新方法加入**FileMonitor_Created**至**EchoAdapterInboundAdapter**類別。</span><span class="sxs-lookup"><span data-stu-id="5ea93-146">To do so, add the new method **FileMonitor_Created** to the **EchoAdapterInboundAdapter** class.</span></span>  
  
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
  
10. <span data-ttu-id="5ea93-147">現在您必須移除**NotImplementedException**內部擲回例外狀況**EchoAdapterInboundReply**類別。</span><span class="sxs-lookup"><span data-stu-id="5ea93-147">Now you must remove the **NotImplementedException** exceptions thrown by the internal **EchoAdapterInboundReply** class.</span></span> <span data-ttu-id="5ea93-148">若要這樣做，請刪除下列陳述式從**中止**和**回覆**方法。</span><span class="sxs-lookup"><span data-stu-id="5ea93-148">To do this, delete the following statement from the **Abort** and **Reply** methods.</span></span>  
  
    ```csharp  
    throw new NotImplementedException("The method or operation is not implemented.");  
    ```  
  
     <span data-ttu-id="5ea93-149">您**中止**和**回覆**方法應該與下列類似。</span><span class="sxs-lookup"><span data-stu-id="5ea93-149">Your **Abort** and **Reply** methods should be similar to the following.</span></span>  
  
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
  
11. <span data-ttu-id="5ea93-150">若要完成之輸入的處理常式的實作，新增下列類別**EchoAdapterOutboundHandler.cs**。</span><span class="sxs-lookup"><span data-stu-id="5ea93-150">To complete the implementation for the inbound handler, add the following class to **EchoAdapterOutboundHandler.cs**.</span></span> <span data-ttu-id="5ea93-151">這個類別會提供逾時支援的輸入處理常式實作。</span><span class="sxs-lookup"><span data-stu-id="5ea93-151">This class provides timeout support for the inbound handler implementation.</span></span>  
  
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
  
12. <span data-ttu-id="5ea93-152">在 Visual Studio 中，在**檔案**功能表上，按一下 **全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="5ea93-152">In Visual Studio, on the **File** menu, click **Save All**.</span></span>  
  
13. <span data-ttu-id="5ea93-153">按一下 [ **建置** ] 功能表上的 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="5ea93-153">On the **Build** menu, click **Build Solution**.</span></span> <span data-ttu-id="5ea93-154">它應該編譯無誤。</span><span class="sxs-lookup"><span data-stu-id="5ea93-154">It should compile without errors.</span></span> <span data-ttu-id="5ea93-155">如果沒有，請確定您已依照上述每個步驟。</span><span class="sxs-lookup"><span data-stu-id="5ea93-155">If not, ensure that you have followed every step above.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5ea93-156">您應該已經儲存您的工作結果。</span><span class="sxs-lookup"><span data-stu-id="5ea93-156">You saved your work.</span></span> <span data-ttu-id="5ea93-157">您可以安全地關閉目前的 Visual Studio 或移至下一個步驟中，[步驟 9： 建立及部署回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-9-build-and-deploy-the-echo-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="5ea93-157">You can safely close Visual Studio at this time or go to the next step, [Step 9: Build and Deploy the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-9-build-and-deploy-the-echo-adapter.md).</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="5ea93-158">我剛剛做什麼？</span><span class="sxs-lookup"><span data-stu-id="5ea93-158">What Did I Just Do?</span></span>  
 <span data-ttu-id="5ea93-159">在此步驟回應配接器教學課程中，提供您實作輸入處理常式。</span><span class="sxs-lookup"><span data-stu-id="5ea93-159">In this step of the Echo Adapter tutorial, you provided an implementation for the Inbound Handler.</span></span> <span data-ttu-id="5ea93-160">此實作會提供檔案監看回應配接器使用的功能**FileSystemWatcher**的.NET Framework 類別。</span><span class="sxs-lookup"><span data-stu-id="5ea93-160">This implementation provides file watching capabilities for the Echo Adapter using the **FileSystemWatcher** class of the .NET Framework.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5ea93-161">後續步驟</span><span class="sxs-lookup"><span data-stu-id="5ea93-161">Next Steps</span></span>  
 <span data-ttu-id="5ea93-162">在下一個步驟中，您可以部署配接器。</span><span class="sxs-lookup"><span data-stu-id="5ea93-162">In the next step, you deploy the adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ea93-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ea93-163">See Also</span></span>  
 <span data-ttu-id="5ea93-164">[步驟 9： 建置並部署回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-9-build-and-deploy-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="5ea93-164">[Step 9: Build and Deploy the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-9-build-and-deploy-the-echo-adapter.md) </span></span>  
 [<span data-ttu-id="5ea93-165">步驟 7： 回應配接器實作同步輸出的處理常式</span><span class="sxs-lookup"><span data-stu-id="5ea93-165">Step 7: Implement the Synchronous Outbound Handler for the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-7-implement-the-synchronous-outbound-handler-for-the-echo-adapter.md)