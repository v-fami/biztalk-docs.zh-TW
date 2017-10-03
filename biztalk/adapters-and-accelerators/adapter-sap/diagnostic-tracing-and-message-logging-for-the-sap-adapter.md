---
title: "診斷追蹤和訊息記錄 SAP 配接器的 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracing, between the adapter client and adapter
- tracing, within the adapter
- tracing, between the adapter and the LOB application
- troubleshooting, tracing and logging
ms.assetid: 5c60af54-896d-4873-acbf-32fbcd051ee2
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6aab9debbc619d2524063c1228c63745c6481d42
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="diagnostic-tracing-and-message-logging-for-the-sap-adapter"></a><span data-ttu-id="b50d3-102">診斷追蹤和 SAP 配接器的訊息記錄</span><span class="sxs-lookup"><span data-stu-id="b50d3-102">Diagnostic Tracing and Message Logging for the SAP adapter</span></span>
<span data-ttu-id="b50d3-103">診斷追蹤可讓您有效地診斷使用配接器時，可能會遇到的問題。</span><span class="sxs-lookup"><span data-stu-id="b50d3-103">Diagnostic tracing helps to effectively diagnose problems that you might encounter when using the adapters.</span></span> <span data-ttu-id="b50d3-104">配接器用戶端可以啟動三個層級的診斷追蹤：</span><span class="sxs-lookup"><span data-stu-id="b50d3-104">Adapter clients can activate diagnostic tracing at three levels:</span></span>  
  
-   <span data-ttu-id="b50d3-105">配接器用戶端之間的介面卡</span><span class="sxs-lookup"><span data-stu-id="b50d3-105">Between the adapter client and the adapter</span></span>  
  
-   <span data-ttu-id="b50d3-106">配接器內</span><span class="sxs-lookup"><span data-stu-id="b50d3-106">Within the adapter</span></span>  
  
-   <span data-ttu-id="b50d3-107">配接器之間的特定業務 (LOB) 應用程式</span><span class="sxs-lookup"><span data-stu-id="b50d3-107">Between the adapter and the line-of-business (LOB) application</span></span>  
  
 <span data-ttu-id="b50d3-108">本節提供啟動下列層級追蹤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b50d3-108">This section provides information about activating tracing at these levels.</span></span>  
  
## <a name="tracing-between-the-adapter-client-and-the-adapter"></a><span data-ttu-id="b50d3-109">配接器用戶端與配接器之間的追蹤</span><span class="sxs-lookup"><span data-stu-id="b50d3-109">Tracing Between the Adapter Client and the Adapter</span></span>  
 <span data-ttu-id="b50d3-110">配接器用戶端可以啟用 WCF 追蹤，配接器用戶端與配接器之間的追蹤問題。</span><span class="sxs-lookup"><span data-stu-id="b50d3-110">Adapter clients can enable WCF tracing to trace issues between the adapter client and the adapter.</span></span> <span data-ttu-id="b50d3-111">WCF 追蹤用來追蹤來自配接器用戶端使用 WCF 服務模型，且有助於診斷問題序列化輸入的 XML。</span><span class="sxs-lookup"><span data-stu-id="b50d3-111">WCF tracing is used to trace the input XML that comes from the adapter client by using the WCF service model and is useful in diagnosing serialization issues.</span></span> <span data-ttu-id="b50d3-112">WCF 追蹤不是適用於 WCF 通道模型或是從配接器至配接器用戶端的輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="b50d3-112">WCF tracing is not used for the WCF channel model or for output messages from the adapter to the adapter client.</span></span> <span data-ttu-id="b50d3-113">若要啟動 WCF 追蹤的 BizTalk 應用程式和 WCF 服務模型應用程式，您可以加入個別的組態檔中的摘錄。</span><span class="sxs-lookup"><span data-stu-id="b50d3-113">You can activate WCF tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files.</span></span> <span data-ttu-id="b50d3-114">此外，您可以啟用追蹤，在設計階段和執行階段。</span><span class="sxs-lookup"><span data-stu-id="b50d3-114">Also, you can enable tracing both at design-time and run-time.</span></span>  
  
-   <span data-ttu-id="b50d3-115">**在設計階段追蹤**。</span><span class="sxs-lookup"><span data-stu-id="b50d3-115">**Tracing at design-time**.</span></span> <span data-ttu-id="b50d3-116">為設計階段經驗，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b50d3-116">For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span> <span data-ttu-id="b50d3-117">所有這些工具可以從使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b50d3-117">All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="b50d3-118">因此，若要啟用的設計階段經驗的追蹤，您必須加入摘要內的 devenv.exe.config 檔案位於*\<安裝磁碟機 >*: \Program Files\Microsoft Visual Studio  *\<版本 >*\Common7\IDE。</span><span class="sxs-lookup"><span data-stu-id="b50d3-118">So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive>*:\Program Files\Microsoft Visual Studio *\<version>*\Common7\IDE.</span></span>  
  
-   <span data-ttu-id="b50d3-119">**在執行階段追蹤**。</span><span class="sxs-lookup"><span data-stu-id="b50d3-119">**Tracing at run-time**.</span></span> <span data-ttu-id="b50d3-120">進行執行階段追蹤，您必須將根據您使用應用程式的摘要。</span><span class="sxs-lookup"><span data-stu-id="b50d3-120">For run-time tracing, you must add the excerpt depending on the application you are using.</span></span>  
  
    -   <span data-ttu-id="b50d3-121">如[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式，您必須加入至 BizTalk 組態檔，通常是 BTSNTSvc.exe.config 的摘錄。如[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]，這個檔案位在通常\<安裝磁碟機 >: \Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b50d3-121">For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)], this file is available typically under \<installation drive>:\Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].</span></span>  
  
    -   <span data-ttu-id="b50d3-122">WCF 服務模型.NET 應用程式，您必須將摘要加入您專案的 app.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="b50d3-122">For a WCF service model .NET application, you must add the excerpt to the app.config file of your project.</span></span>  
  
 <span data-ttu-id="b50d3-123">若要啟用 WCF 追蹤，加入下列摘錄中的`<configuration>`標記。</span><span class="sxs-lookup"><span data-stu-id="b50d3-123">To enable WCF tracing, add the following excerpt within the `<configuration>` tag.</span></span>  
  
```  
\<system.diagnostics>  
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
  \</system.diagnostics>  
  \<system.serviceModel>  
    <diagnostics>  
      <messageLogging   
           logEntireMessage="true"   
           logMalformedMessages="false"  
           logMessagesAtServiceLevel="true"   
           logMessagesAtTransportLevel="false"/>  
    </diagnostics>      
  \</system.serviceModel>  
```  
  
 <span data-ttu-id="b50d3-124">這將 C:\log\WCFTrace.svclog WCF 追蹤。</span><span class="sxs-lookup"><span data-stu-id="b50d3-124">This saves the WCF traces to C:\log\WCFTrace.svclog.</span></span> <span data-ttu-id="b50d3-125">如需 WCF 追蹤的詳細資訊，請參閱[追蹤](https://msdn.microsoft.com/library/ms730342.aspx)。</span><span class="sxs-lookup"><span data-stu-id="b50d3-125">For more information about WCF tracing, see [Tracing](https://msdn.microsoft.com/library/ms730342.aspx).</span></span> 
  
> [!IMPORTANT]
>  <span data-ttu-id="b50d3-126">請確定您減輕潛在的安全性威脅的啟用追蹤來公開敏感的商業資料。</span><span class="sxs-lookup"><span data-stu-id="b50d3-126">Make sure you mitigate potential security threats of exposing sensitive business data by enabling tracing.</span></span> <span data-ttu-id="b50d3-127">如建議，請參閱[最佳作法來保護 SAP 配接器](../../adapters-and-accelerators/adapter-sap/best-practices-to-secure-the-sap-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="b50d3-127">For recommendations see [Best practices to secure the SAP adapter](../../adapters-and-accelerators/adapter-sap/best-practices-to-secure-the-sap-adapter.md).</span></span>  
  
## <a name="tracing-within-the-adapter"></a><span data-ttu-id="b50d3-128">配接器內追蹤</span><span class="sxs-lookup"><span data-stu-id="b50d3-128">Tracing Within the Adapter</span></span>  
 <span data-ttu-id="b50d3-129">配接器追蹤檔，例如錯誤、 警告和資訊訊息記錄有用資訊的不同的類別。</span><span class="sxs-lookup"><span data-stu-id="b50d3-129">The adapters log different categories of useful information to the trace file such as errors, warnings, and information messages.</span></span> <span data-ttu-id="b50d3-130">這類資訊是用於了解配接器內的程序流程和診斷配接器的問題。</span><span class="sxs-lookup"><span data-stu-id="b50d3-130">Such information is useful in understanding the process flow within the adapter and diagnosing issues with the adapter.</span></span> <span data-ttu-id="b50d3-131">您可以啟動[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和配接器追蹤的 BizTalk 應用程式和 WCF 服務模型應用程式，方法是加入個別的組態檔的摘錄。</span><span class="sxs-lookup"><span data-stu-id="b50d3-131">You can activate the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files.</span></span> <span data-ttu-id="b50d3-132">此外，您可以啟用追蹤，在設計階段和執行階段。</span><span class="sxs-lookup"><span data-stu-id="b50d3-132">Also, you can enable tracing both at design-time and run-time.</span></span>  
  
-   <span data-ttu-id="b50d3-133">**在設計階段追蹤**。</span><span class="sxs-lookup"><span data-stu-id="b50d3-133">**Tracing at design-time**.</span></span> <span data-ttu-id="b50d3-134">為設計階段經驗，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b50d3-134">For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span> <span data-ttu-id="b50d3-135">所有這些工具可以從使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b50d3-135">All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="b50d3-136">因此，若要啟用的設計階段經驗的追蹤，您必須加入摘要內的 devenv.exe.config 檔案位於*\<安裝磁碟機 >*: \Program Files\Microsoft Visual Studio  *\<版本 >*\Common7\IDE。</span><span class="sxs-lookup"><span data-stu-id="b50d3-136">So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive>*:\Program Files\Microsoft Visual Studio *\<version>*\Common7\IDE.</span></span>  
  
-   <span data-ttu-id="b50d3-137">**在執行階段追蹤**。</span><span class="sxs-lookup"><span data-stu-id="b50d3-137">**Tracing at run-time**.</span></span> <span data-ttu-id="b50d3-138">進行執行階段追蹤，您必須將根據您使用應用程式的摘要。</span><span class="sxs-lookup"><span data-stu-id="b50d3-138">For run-time tracing, you must add the excerpt depending on the application you are using.</span></span>  
  
    -   <span data-ttu-id="b50d3-139">如[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式，您必須加入至 BizTalk 組態檔，通常是 BTSNTSvc.exe.config 的摘錄。如[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]，這個檔案位在通常\<安裝磁碟機 >: \Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b50d3-139">For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)], this file is available typically under \<installation drive>:\Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].</span></span>  
  
    -   <span data-ttu-id="b50d3-140">WCF 服務模型.NET 應用程式，您必須將摘要加入您專案的 app.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="b50d3-140">For a WCF service model .NET application, you must add the excerpt to the app.config file of your project.</span></span>  
  
 <span data-ttu-id="b50d3-141">若要啟用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和配接器追蹤，加入下列摘錄中的`<configuration>`標記。</span><span class="sxs-lookup"><span data-stu-id="b50d3-141">To enable [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing, add the following excerpt within the `<configuration>` tag.</span></span>  
  
```  
\<system.diagnostics>  
    <sources>  
      <source name="Microsoft.ServiceModel.Channels" switchValue="Error">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="Microsoft.Adapters.SAP" switchValue="Information">  
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
  \</system.diagnostics>  
```  
  
 <span data-ttu-id="b50d3-142">這將 C:\log\AdapterTrace.svclog WCF 追蹤。</span><span class="sxs-lookup"><span data-stu-id="b50d3-142">This saves the WCF traces to C:\log\AdapterTrace.svclog.</span></span>  
  
## <a name="tracing-between-the-adapter-and-the-lob-application"></a><span data-ttu-id="b50d3-143">配接器與 LOB 應用程式之間的追蹤</span><span class="sxs-lookup"><span data-stu-id="b50d3-143">Tracing Between the Adapter and the LOB Application</span></span>  
 <span data-ttu-id="b50d3-144">診斷問題，您懷疑有關 LOB 應用程式中，您必須啟用追蹤，配接器與 LOB 應用程式之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="b50d3-144">To diagnose issues that you suspect are related to the LOB application, you must enable tracing for communication between the adapter and the LOB application.</span></span> <span data-ttu-id="b50d3-145">配接器也會取決於 LOB 追蹤 （用戶端/伺服器端） 來存取這項資訊。</span><span class="sxs-lookup"><span data-stu-id="b50d3-145">Adapters also depend on LOB tracing (client/server side) to access this information.</span></span> <span data-ttu-id="b50d3-146">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]可讓配接器用戶端連線 URI 中指定"RfcSdkTrace"參數開啟 SAP 系統內的追蹤。</span><span class="sxs-lookup"><span data-stu-id="b50d3-146">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] enables adapter clients to turn on tracing within the SAP system by specifying the "RfcSdkTrace" parameter in the connection URI.</span></span> <span data-ttu-id="b50d3-147">您必須指定這個參數，以啟用 RFC SDK 追蹤 SAP 系統內的資訊流程。</span><span class="sxs-lookup"><span data-stu-id="b50d3-147">You must specify this parameter to enable the RFC SDK to trace information flow within the SAP system.</span></span> <span data-ttu-id="b50d3-148">如需連線 URI 的詳細資訊，請參閱[建立 SAP 系統連接 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="b50d3-148">For more information about the connection URI, see [Create the SAP system connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span></span>  
  
 <span data-ttu-id="b50d3-149">此外，您也可以建立的追蹤層級設定 RFC sdk RFC_TRACE 環境變數。</span><span class="sxs-lookup"><span data-stu-id="b50d3-149">Additionally, you can also create an RFC_TRACE environment variable that sets the level of tracing for the RFC SDK.</span></span> <span data-ttu-id="b50d3-150">RFC_TRACE 是 SAP 所定義的環境變數，而且是由 RFC SDK。</span><span class="sxs-lookup"><span data-stu-id="b50d3-150">RFC_TRACE is an environment variable defined by SAP and is used by the RFC SDK.</span></span> <span data-ttu-id="b50d3-151">如果這個變數未定義，或設為 0，RFC SDK 追蹤層級是最低限度。</span><span class="sxs-lookup"><span data-stu-id="b50d3-151">If this variable is not defined or is set to 0, the RFC SDK tracing level is bare minimum.</span></span> <span data-ttu-id="b50d3-152">如果變數設定為 1 或 2，會更詳細的追蹤層級。</span><span class="sxs-lookup"><span data-stu-id="b50d3-152">If the variable is set to 1 or 2, the tracing level is more detailed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b50d3-153">無論是否設定 RFC_TRACE 環境變數，RFC SDK 追蹤已啟用*只*如果"RfcSdkTrace 」 參數設定為在 連線 URI，則為 true。</span><span class="sxs-lookup"><span data-stu-id="b50d3-153">Irrespective of whether the RFC_TRACE environment variable is set, the RFC SDK tracing is enabled *only* if the "RfcSdkTrace" parameter is set to true in the connection URI.</span></span> <span data-ttu-id="b50d3-154">這個環境變數的值只會管理 RFC SDK 追蹤層的級。</span><span class="sxs-lookup"><span data-stu-id="b50d3-154">The value of this environment variable solely governs the level of RFC SDK tracing.</span></span> <span data-ttu-id="b50d3-155">如果 RfcSdkTrace 設為 true，則配接器與 SAP 系統之間的追蹤會複製到您的電腦上的"system32"資料夾。</span><span class="sxs-lookup"><span data-stu-id="b50d3-155">If RfcSdkTrace is set to true, the message traces between the adapter and the SAP system are copied to the “system32” folder on your computer.</span></span> <span data-ttu-id="b50d3-156">若要將 RFC SDK 追蹤儲存到其他位置，您可以設定 RFC_TRACE_DIR 環境變數。</span><span class="sxs-lookup"><span data-stu-id="b50d3-156">To save the RFC SDK traces to some other location, you can set the RFC_TRACE_DIR environment variable.</span></span> <span data-ttu-id="b50d3-157">如需這些環境變數詳細資訊，請參閱 SAP 文件集。</span><span class="sxs-lookup"><span data-stu-id="b50d3-157">For more information about these environment variables refer to the SAP documentation.</span></span>  
  
## <a name="viewing-the-traces"></a><span data-ttu-id="b50d3-158">檢視追蹤</span><span class="sxs-lookup"><span data-stu-id="b50d3-158">Viewing the Traces</span></span>  
 <span data-ttu-id="b50d3-159">您可以使用 Windows Communication Foundation (WCF) 服務追蹤檢視器工具來檢視追蹤。</span><span class="sxs-lookup"><span data-stu-id="b50d3-159">You can use the Windows Communication Foundation (WCF) Service Trace Viewer tool to view the traces.</span></span> <span data-ttu-id="b50d3-160">如需此工具的詳細資訊，請參閱[使用服務追蹤檢視器檢視相關追蹤和麻煩](https://msdn.microsoft.com/library/aa751795.aspx)。</span><span class="sxs-lookup"><span data-stu-id="b50d3-160">For more information about the tool, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubles](https://msdn.microsoft.com/library/aa751795.aspx).</span></span>
  
## <a name="configuring-tracking-for-biztalk-applications"></a><span data-ttu-id="b50d3-161">設定追蹤的 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="b50d3-161">Configuring Tracking for BizTalk Applications</span></span>  
 <span data-ttu-id="b50d3-162">BizTalk Server 管理主控台可讓您設定不同的追蹤選項項目，例如傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="b50d3-162">The BizTalk Server Administration console lets you configure various tracking options for items such as send ports and receive ports.</span></span> <span data-ttu-id="b50d3-163">追蹤組態設定可讓您追蹤輸入和輸出事件資料、 訊息屬性、 訊息內文，以及協調流程。</span><span class="sxs-lookup"><span data-stu-id="b50d3-163">The tracking configuration settings enable you to track inbound and outbound event data, message properties, message bodies, and orchestrations.</span></span> <span data-ttu-id="b50d3-164">如需有關如何設定追蹤的 BizTalk 應用程式的詳細資訊，請參閱[管理成品](../../core/managing-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="b50d3-164">For more information about configuring tracking for BizTalk applications, see the [Managing Artifacts](../../core/managing-artifacts.md).</span></span>
  
 <span data-ttu-id="b50d3-165">您也可以使用健全狀況與活動追蹤 (HAT) 來檢視歷史或追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="b50d3-165">You can also use Health and Activity Tracking (HAT) to view historical or tracked data.</span></span> <span data-ttu-id="b50d3-166">如需詳細資訊，請參閱[檢視歷程記錄和追蹤資料](../../core/viewing-historical-and-tracked-data.md)。</span><span class="sxs-lookup"><span data-stu-id="b50d3-166">For more information, see [Viewing Historical and Tracked Data](../../core/viewing-historical-and-tracked-data.md).</span></span>
 
## <a name="see-also"></a><span data-ttu-id="b50d3-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b50d3-167">See Also</span></span>  
[<span data-ttu-id="b50d3-168">SAP 配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="b50d3-168">Troubleshoot the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)