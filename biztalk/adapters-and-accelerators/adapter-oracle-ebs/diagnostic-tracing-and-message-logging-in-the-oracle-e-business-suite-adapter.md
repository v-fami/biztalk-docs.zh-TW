---
title: "診斷追蹤和訊息記錄在 Oracle E-business Suite 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0d6be2a-cbd0-4c9c-be6f-9631063346e2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8de2444cecbd661e9af4457f5f19c7e929d1c9c5
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="diagnostic-tracing-and-message-logging-in-the-oracle-e-business-suite-adapter"></a><span data-ttu-id="5d81d-102">診斷追蹤和訊息記錄在 Oracle E-business Suite 配接器</span><span class="sxs-lookup"><span data-stu-id="5d81d-102">Diagnostic Tracing and Message Logging in the Oracle E-Business Suite adapter</span></span>
<span data-ttu-id="5d81d-103">診斷追蹤可讓您有效地診斷使用配接器時，可能會遇到的問題。</span><span class="sxs-lookup"><span data-stu-id="5d81d-103">Diagnostic tracing helps to effectively diagnose problems that you might encounter when using the adapters.</span></span> <span data-ttu-id="5d81d-104">本主題提供下列三種支援的追蹤資訊[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="5d81d-104">This topic provides information about the following three types of tracing supported with [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]:</span></span>  
  
-   <span data-ttu-id="5d81d-105">使用用戶端識別元的 oracle 伺服器端追蹤</span><span class="sxs-lookup"><span data-stu-id="5d81d-105">Oracle server-side tracing using a client identifier</span></span>
  
-   <span data-ttu-id="5d81d-106">WCF 配接器用戶端與配接器之間的追蹤</span><span class="sxs-lookup"><span data-stu-id="5d81d-106">WCF tracing between the adapter client and the adapter</span></span>
  
-   <span data-ttu-id="5d81d-107">WCF 配接器內的追蹤</span><span class="sxs-lookup"><span data-stu-id="5d81d-107">WCF tracing within the adapter</span></span>
 
## <a name="oracle-server-side-tracing-using-a-client-identifier"></a><span data-ttu-id="5d81d-108">使用用戶端識別元的 oracle 伺服器端追蹤</span><span class="sxs-lookup"><span data-stu-id="5d81d-108">Oracle server side tracing using a client identifier</span></span>  
 <span data-ttu-id="5d81d-109">Oracle 可讓您執行伺服器端追蹤用戶端應用程式的 Oracle 資料庫上執行的作業。</span><span class="sxs-lookup"><span data-stu-id="5d81d-109">Oracle allows you to perform server-side tracing for the operations performed by client applications on the Oracle database.</span></span> <span data-ttu-id="5d81d-110">因為來自用戶端應用程式的要求會路由至不同的資料庫工作階段中，但是很難追蹤來源的要求。</span><span class="sxs-lookup"><span data-stu-id="5d81d-110">Because requests from client applications can be routed to different database sessions, it becomes difficult to trace the origin of the request.</span></span> <span data-ttu-id="5d81d-111">不過，Oracle 有助於使用用戶端識別元的端對端應用程式追蹤。</span><span class="sxs-lookup"><span data-stu-id="5d81d-111">However, Oracle facilitates end-to-end application tracing using client identifiers.</span></span> 
 
 <span data-ttu-id="5d81d-112">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]公開`OracleConnectionClientId`繫結可讓您指定用戶端識別元設計階段配接器用來連接到 Oracle 連接的屬性。</span><span class="sxs-lookup"><span data-stu-id="5d81d-112">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exposes the `OracleConnectionClientId` binding property that allows you to specify the client identifier at the design time for the connection used by the adapter to connect to Oracle.</span></span> <span data-ttu-id="5d81d-113">配接器用戶端識別碼可協助您在選擇性追蹤中的介面卡上的用戶端 Oracle 中，所執行的作業，也可讓您篩選並檢視 Oracle 伺服器追蹤為基礎的用戶端識別碼。</span><span class="sxs-lookup"><span data-stu-id="5d81d-113">The adapter client identifier helps you in selective tracing of the operations performed by the adapter client on Oracle, and also allows you to filter and view the Oracle server traces based on the client identifier.</span></span> <span data-ttu-id="5d81d-114">如需有關如何啟用用戶端識別元在 Oracle 中的追蹤資訊，請參閱[http://go.microsoft.com/fwlink/p/?LinkId=135746](http://go.microsoft.com/fwlink/p/?LinkId=135746)。</span><span class="sxs-lookup"><span data-stu-id="5d81d-114">For information about how you can enable tracing for client identifiers in Oracle, see [http://go.microsoft.com/fwlink/p/?LinkId=135746](http://go.microsoft.com/fwlink/p/?LinkId=135746).</span></span>  
  
## <a name="wcf-tracing-between-the-adapter-client-and-the-adapter"></a><span data-ttu-id="5d81d-115">WCF 配接器用戶端與配接器之間的追蹤</span><span class="sxs-lookup"><span data-stu-id="5d81d-115">WCF tracing between the adapter client and the adapter</span></span>  
 <span data-ttu-id="5d81d-116">配接器用戶端可以啟用 WCF 追蹤，配接器用戶端與配接器之間的追蹤問題。</span><span class="sxs-lookup"><span data-stu-id="5d81d-116">Adapter clients can enable WCF tracing to trace issues between the adapter client and the adapter.</span></span> <span data-ttu-id="5d81d-117">WCF 追蹤用來追蹤來自配接器用戶端使用 WCF 服務模型，且有助於診斷問題序列化輸入的 XML。</span><span class="sxs-lookup"><span data-stu-id="5d81d-117">WCF tracing is used to trace the input XML that comes from the adapter client by using the WCF service model and is useful in diagnosing serialization issues.</span></span> <span data-ttu-id="5d81d-118">WCF 追蹤不是適用於 WCF 通道模型或是從配接器至配接器用戶端的輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="5d81d-118">WCF tracing is not used for the WCF channel model or for output messages from the adapter to the adapter client.</span></span> <span data-ttu-id="5d81d-119">若要啟動 WCF 追蹤的 BizTalk 應用程式和 WCF 服務模型應用程式，您可以加入個別的組態檔中的摘錄。</span><span class="sxs-lookup"><span data-stu-id="5d81d-119">You can activate WCF tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files.</span></span> <span data-ttu-id="5d81d-120">此外，您可以啟用追蹤，在設計階段和執行階段。</span><span class="sxs-lookup"><span data-stu-id="5d81d-120">Also, you can enable tracing both at design-time and run-time.</span></span>  
  
-   <span data-ttu-id="5d81d-121">**在設計階段追蹤**。</span><span class="sxs-lookup"><span data-stu-id="5d81d-121">**Tracing at design-time**.</span></span> <span data-ttu-id="5d81d-122">為設計階段經驗，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5d81d-122">For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span> <span data-ttu-id="5d81d-123">所有這些工具可以從使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5d81d-123">All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="5d81d-124">因此，若要啟用的設計階段經驗的追蹤，您必須加入摘要內的 devenv.exe.config 檔案位於*\<安裝磁碟機\>*: \Program Files\Microsoft Visual Studio *\<版本\>*\Common7\IDE。</span><span class="sxs-lookup"><span data-stu-id="5d81d-124">So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive\>*:\Program Files\Microsoft Visual Studio *\<version\>*\Common7\IDE.</span></span>  
  
-   <span data-ttu-id="5d81d-125">**在執行階段追蹤**。</span><span class="sxs-lookup"><span data-stu-id="5d81d-125">**Tracing at run-time**.</span></span> <span data-ttu-id="5d81d-126">進行執行階段追蹤，您必須將根據您使用應用程式的摘要。</span><span class="sxs-lookup"><span data-stu-id="5d81d-126">For run-time tracing, you must add the excerpt depending on the application you are using.</span></span>  
  
    -   <span data-ttu-id="5d81d-127">如[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式，您必須加入至 BizTalk 組態檔，通常是 BTSNTSvc.exe.config 的摘錄。BizTalk Server 的這個檔案是通常在\<安裝磁碟機\>: \Program Files\Microsoft BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="5d81d-127">For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For BizTalk Server, this file is available typically under \<installation drive\>:\Program Files\Microsoft BizTalk Server.</span></span>  
  
    -   <span data-ttu-id="5d81d-128">WCF 服務模型.NET 應用程式，您必須將摘要加入您專案的 app.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="5d81d-128">For a WCF service model .NET application, you must add the excerpt to the app.config file of your project.</span></span>  
  
 <span data-ttu-id="5d81d-129">若要啟用 WCF 追蹤，加入下列摘錄中的`<configuration>`標記：</span><span class="sxs-lookup"><span data-stu-id="5d81d-129">To enable WCF tracing, add the following excerpt within the `<configuration>` tag:</span></span>  
  
```  
<system.diagnostics>  
    <sources>  
      <source name ="System.ServiceModel" switchValue="Verbose">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name ="System.ServiceModel.MessageLogging"   
              switchValue="Verbose, ActivityTracing">          
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name ="System.Runtime.Serialization" switchValue="Verbose">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
   </sources>  
   <sharedListeners>  
      <add name="xml" type="System.Diagnostics.XmlWriterTraceListener"                
           traceOutputOptions="LogicalOperationStack"   
           initializeData="C:\log\WCFTrace.svclog" />  
   </sharedListeners>  
   <trace autoflush="true" />  
  </system.diagnostics>  
  <system.serviceModel>  
    <diagnostics>  
      <messageLogging   
           logEntireMessage="true"   
           logMalformedMessages="false"  
           logMessagesAtServiceLevel="true"   
           logMessagesAtTransportLevel="false"/>  
    </diagnostics>      
  </system.serviceModel>  
```  
  
 <span data-ttu-id="5d81d-130">這將 C:\log\WCFTrace.svclog WCF 追蹤。</span><span class="sxs-lookup"><span data-stu-id="5d81d-130">This saves the WCF traces to C:\log\WCFTrace.svclog.</span></span> <span data-ttu-id="5d81d-131">[WCF 追蹤](https://msdn.microsoft.com/library/ms730342.aspx)提供詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="5d81d-131">[WCF tracing](https://msdn.microsoft.com/library/ms730342.aspx) provides more information.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5d81d-132">請確定您降低曝露敏感性商務資料，啟用追蹤時，可能導致潛在的安全性威脅。</span><span class="sxs-lookup"><span data-stu-id="5d81d-132">Make sure you mitigate potential security threats of exposing sensitive business data that can be caused when enabling tracing.</span></span> <span data-ttu-id="5d81d-133">如需建議，請參閱[訊息和執行個體資料追蹤的最佳作法](../../core/best-practices-for-message-and-instance-data-tracking.md)。</span><span class="sxs-lookup"><span data-stu-id="5d81d-133">For recommendations, see the [Best Practices for Message and Instance Data Tracking](../../core/best-practices-for-message-and-instance-data-tracking.md).</span></span>  
  
## <a name="wcf-tracing-within-the-adapter"></a><span data-ttu-id="5d81d-134">WCF 配接器內的追蹤</span><span class="sxs-lookup"><span data-stu-id="5d81d-134">WCF tracing within the adapter</span></span>  
 <span data-ttu-id="5d81d-135">配接器追蹤檔，例如錯誤、 警告和資訊訊息記錄有用資訊的不同的類別。</span><span class="sxs-lookup"><span data-stu-id="5d81d-135">The adapters log different categories of useful information to the trace file such as errors, warnings, and information messages.</span></span> <span data-ttu-id="5d81d-136">這類資訊是用於了解配接器內的程序流程和診斷配接器的問題。</span><span class="sxs-lookup"><span data-stu-id="5d81d-136">Such information is useful in understanding the process flow within the adapter and diagnosing issues with the adapter.</span></span> <span data-ttu-id="5d81d-137">您可以啟動[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和配接器追蹤的 BizTalk 應用程式和 WCF 服務模型應用程式，方法是加入個別的組態檔的摘錄。</span><span class="sxs-lookup"><span data-stu-id="5d81d-137">You can activate the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files.</span></span> <span data-ttu-id="5d81d-138">此外，您可以啟用追蹤，在設計階段和執行階段。</span><span class="sxs-lookup"><span data-stu-id="5d81d-138">Also, you can enable tracing both at design-time and run-time.</span></span>  
  
-   <span data-ttu-id="5d81d-139">**在設計階段追蹤**。</span><span class="sxs-lookup"><span data-stu-id="5d81d-139">**Tracing at design-time**.</span></span> <span data-ttu-id="5d81d-140">為設計階段經驗，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5d81d-140">For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span> <span data-ttu-id="5d81d-141">所有這些工具可以從使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5d81d-141">All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="5d81d-142">因此，若要啟用的設計階段經驗的追蹤，您必須加入摘要內的 devenv.exe.config 檔案位於*\<安裝磁碟機\>*: \Program Files\Microsoft Visual Studio *\<版本\>*\Common7\IDE。</span><span class="sxs-lookup"><span data-stu-id="5d81d-142">So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive\>*:\Program Files\Microsoft Visual Studio *\<version\>*\Common7\IDE.</span></span>  
  
-   <span data-ttu-id="5d81d-143">**在執行階段追蹤**。</span><span class="sxs-lookup"><span data-stu-id="5d81d-143">**Tracing at run-time**.</span></span> <span data-ttu-id="5d81d-144">進行執行階段追蹤，您必須將根據您使用應用程式的摘要。</span><span class="sxs-lookup"><span data-stu-id="5d81d-144">For run-time tracing, you must add the excerpt depending on the application you are using.</span></span>  
  
    -   <span data-ttu-id="5d81d-145">如[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式，您必須加入至 BizTalk 組態檔，通常是 BTSNTSvc.exe.config 的摘錄。如[!INCLUDE[btsbiztalkserver2006r2](../../includes/btsbiztalkserver2006r2-md.md)]，這個檔案位在通常\<安裝磁碟機\>: \Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006](../../includes/btsbiztalkserver2006-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5d81d-145">For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For [!INCLUDE[btsbiztalkserver2006r2](../../includes/btsbiztalkserver2006r2-md.md)], this file is available typically under \<installation drive\>:\Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006](../../includes/btsbiztalkserver2006-md.md)].</span></span> <span data-ttu-id="5d81d-146">BizTalk Server 的這個檔案是通常在\<安裝磁碟機\>: \Program Files\Microsoft BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="5d81d-146">For BizTalk Server, this file is available typically under \<installation drive\>:\Program Files\Microsoft BizTalk Server.</span></span>  
  
    -   <span data-ttu-id="5d81d-147">WCF 服務模型.NET 應用程式，您必須將摘要加入您專案的 app.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="5d81d-147">For a WCF service model .NET application, you must add the excerpt to the app.config file of your project.</span></span>  
  
 <span data-ttu-id="5d81d-148">若要啟用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和配接器追蹤，加入下列摘錄中的`<configuration>`標記：</span><span class="sxs-lookup"><span data-stu-id="5d81d-148">To enable [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing, add the following excerpt within the `<configuration>` tag:</span></span>  
  
```  
<system.diagnostics>  
    <sources>  
      <source name="Microsoft.ServiceModel.Channels" switchValue="Error">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="Microsoft.Adapters.OracleEBS" switchValue="Information">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="xml" type="System.Diagnostics.XmlWriterTraceListener"   
   traceOutputOptions="LogicalOperationStack"   
          initializeData="C:\log\AdapterTrace.svclog" />  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
```  
  
 <span data-ttu-id="5d81d-149">這將 C:\log\AdapterTrace.svclog WCF 追蹤。</span><span class="sxs-lookup"><span data-stu-id="5d81d-149">This saves the WCF traces to C:\log\AdapterTrace.svclog.</span></span>  
  
## <a name="viewing-the-traces"></a><span data-ttu-id="5d81d-150">檢視追蹤</span><span class="sxs-lookup"><span data-stu-id="5d81d-150">Viewing the traces</span></span>  
 <span data-ttu-id="5d81d-151">您可以使用 Windows Communication Foundation (WCF) 服務追蹤檢視器工具來檢視追蹤。</span><span class="sxs-lookup"><span data-stu-id="5d81d-151">You can use the Windows Communication Foundation (WCF) Service Trace Viewer tool to view the traces.</span></span> <span data-ttu-id="5d81d-152">[使用服務追蹤檢視器檢視相關追蹤和疑難排解](https://msdn.microsoft.com/library/aa751795.aspx)這項工具提供更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="5d81d-152">[Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](https://msdn.microsoft.com/library/aa751795.aspx) provides more details on this tool.</span></span>  
  
## <a name="configuring-tracking-for-biztalk-applications"></a><span data-ttu-id="5d81d-153">設定追蹤的 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="5d81d-153">Configuring tracking for BizTalk applications</span></span>  
 <span data-ttu-id="5d81d-154">BizTalk Server 管理主控台可讓您設定不同的追蹤選項項目，例如傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="5d81d-154">The BizTalk Server Administration console lets you configure various tracking options for items such as send ports and receive ports.</span></span> <span data-ttu-id="5d81d-155">追蹤組態設定可讓您追蹤輸入和輸出事件資料、 訊息屬性、 訊息內文，以及協調流程。</span><span class="sxs-lookup"><span data-stu-id="5d81d-155">The tracking configuration settings enable you to track inbound and outbound event data, message properties, message bodies, and orchestrations.</span></span> <span data-ttu-id="5d81d-156">如需有關如何設定追蹤的 BizTalk 應用程式的詳細資訊，請參閱[管理及追蹤您的成品](../../core/managing-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="5d81d-156">For more information about configuring tracking for BizTalk applications, see [Managing and tracking your artifacts](../../core/managing-artifacts.md).</span></span>  
  
 <span data-ttu-id="5d81d-157">您也可以使用 群組中樞[檢視追蹤的訊息和執行個體資料](../../core/viewing-tracked-message-and-instance-data.md)，包括最佳作法，儲存追蹤查詢等等。</span><span class="sxs-lookup"><span data-stu-id="5d81d-157">You can also use Group Hub to [view tracked message and instance data](../../core/viewing-tracked-message-and-instance-data.md), including best practices, saving tracking queries, and more.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5d81d-158">請參閱</span><span class="sxs-lookup"><span data-stu-id="5d81d-158">See Also</span></span>  
[<span data-ttu-id="5d81d-159">配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="5d81d-159">Troubleshooting the adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/troubleshooting-the-oracle-ebs-adapter.md)