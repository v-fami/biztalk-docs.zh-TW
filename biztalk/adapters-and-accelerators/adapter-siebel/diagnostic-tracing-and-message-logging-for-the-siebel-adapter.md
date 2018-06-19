---
title: 診斷追蹤和訊息記錄 Siebel 配接器的 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tracing, between the adapter client and the adapter
- logging, troubleshooting
- troubleshooting, tracing and message logging
- tracing, between the adapter and the LOB application
- message logging, troubleshooting
- tracing, troubleshooting
ms.assetid: fd2de692-45b7-45bc-b79c-381f3b1cf592
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f6b27dd6d169c9ea7e5012be3e03329e6888522
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26006527"
---
# <a name="diagnostic-tracing-and-message-logging-for-the-siebel-adapter"></a><span data-ttu-id="83728-102">診斷追蹤和 Siebel 配接器的訊息記錄</span><span class="sxs-lookup"><span data-stu-id="83728-102">Diagnostic Tracing and Message Logging for the Siebel adapter</span></span>
<span data-ttu-id="83728-103">配接器用戶端可以啟用診斷追蹤，才能有效地診斷使用配接器時所遇到的問題。</span><span class="sxs-lookup"><span data-stu-id="83728-103">Adapter clients can enable diagnostic tracing to effectively diagnose problems encountered while using the adapters.</span></span> <span data-ttu-id="83728-104">配接器用戶端可以啟動在三個不同的層級的追蹤：</span><span class="sxs-lookup"><span data-stu-id="83728-104">Adapter clients can activate tracing at three different levels:</span></span>  
  
-   <span data-ttu-id="83728-105">配接器用戶端之間的介面卡</span><span class="sxs-lookup"><span data-stu-id="83728-105">Between the adapter client and the adapter</span></span>  
  
-   <span data-ttu-id="83728-106">配接器內</span><span class="sxs-lookup"><span data-stu-id="83728-106">Within the adapter</span></span>  
  
-   <span data-ttu-id="83728-107">配接器之間的特定業務 (LOB) 應用程式</span><span class="sxs-lookup"><span data-stu-id="83728-107">Between the adapter and the line-of-business (LOB) application</span></span>  
  
 <span data-ttu-id="83728-108">本節提供啟動下列層級追蹤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="83728-108">This section provides information about activating tracing at these levels.</span></span>  
  
## <a name="tracing-between-the-adapter-client-and-the-adapter"></a><span data-ttu-id="83728-109">配接器用戶端與配接器之間的追蹤</span><span class="sxs-lookup"><span data-stu-id="83728-109">Tracing between the adapter client and the adapter</span></span>  
 <span data-ttu-id="83728-110">配接器用戶端可以啟用 WCF 追蹤，配接器用戶端與配接器之間的追蹤問題。</span><span class="sxs-lookup"><span data-stu-id="83728-110">Adapter clients can enable WCF tracing to trace issues between the adapter client and the adapter.</span></span> <span data-ttu-id="83728-111">WCF 追蹤用來追蹤來自配接器用戶端會使用 WCF 服務模型的輸入的 Xml，在診斷序列化問題很有用。</span><span class="sxs-lookup"><span data-stu-id="83728-111">WCF tracing is used to trace the input XMLs coming from the adapter client using the WCF service model and is useful in diagnosing serialization issues.</span></span> <span data-ttu-id="83728-112">WCF 追蹤不是適用於 WCF 通道模型或是從配接器至配接器用戶端的輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="83728-112">WCF tracing is not used for the WCF channel model or for output messages from the adapter to the adapter client.</span></span> <span data-ttu-id="83728-113">若要啟動 WCF 追蹤的 BizTalk 應用程式和 WCF 服務模型應用程式，您可以加入個別的組態檔中的摘錄。</span><span class="sxs-lookup"><span data-stu-id="83728-113">You can activate WCF tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files.</span></span> <span data-ttu-id="83728-114">此外，您可以啟用追蹤，在設計階段和執行階段。</span><span class="sxs-lookup"><span data-stu-id="83728-114">Also, you can enable tracing both at design-time and run-time.</span></span>  
  
-   <span data-ttu-id="83728-115">**在設計階段追蹤**。</span><span class="sxs-lookup"><span data-stu-id="83728-115">**Tracing at design-time**.</span></span> <span data-ttu-id="83728-116">為設計階段經驗，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="83728-116">For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span> <span data-ttu-id="83728-117">所有這些工具可以從使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="83728-117">All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="83728-118">因此，若要啟用的設計階段經驗的追蹤，您必須加入摘要內的 devenv.exe.config 檔案位於*\<安裝磁碟機\>*: \Program Files\Microsoft Visual Studio *\<版本\>* \Common7\IDE。</span><span class="sxs-lookup"><span data-stu-id="83728-118">So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive\>*:\Program Files\Microsoft Visual Studio *\<version\>* \Common7\IDE.</span></span>  
  
-   <span data-ttu-id="83728-119">**在執行階段追蹤**。</span><span class="sxs-lookup"><span data-stu-id="83728-119">**Tracing at run-time**.</span></span> <span data-ttu-id="83728-120">進行執行階段追蹤，您必須將根據您使用應用程式的摘要。</span><span class="sxs-lookup"><span data-stu-id="83728-120">For run-time tracing, you must add the excerpt depending on the application you are using.</span></span>  
  
    -   <span data-ttu-id="83728-121">如[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式，您必須加入至 BizTalk 組態檔，通常是 BTSNTSvc.exe.config 的摘錄。BizTalk Server 的這個檔案是通常在\<安裝磁碟機\>: \Program Files\Microsoft BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="83728-121">For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For BizTalk Server, this file is available typically under \<installation drive\>:\Program Files\Microsoft BizTalk Server.</span></span>  
  
    -   <span data-ttu-id="83728-122">WCF 服務模型.NET 應用程式，您必須將摘要加入您專案的 app.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="83728-122">For a WCF service model .NET application, you must add the excerpt to the app.config file of your project.</span></span>  
  
 <span data-ttu-id="83728-123">若要啟用 WCF 追蹤，您必須新增下列摘錄中的`<configuration>`標記：</span><span class="sxs-lookup"><span data-stu-id="83728-123">To enable WCF tracing, you must add the following excerpt within the `<configuration>` tag:</span></span>
  
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
  
 <span data-ttu-id="83728-124">這將 C:\log\WCFTrace.svclog WCF 追蹤。</span><span class="sxs-lookup"><span data-stu-id="83728-124">This saves the WCF traces to C:\log\WCFTrace.svclog.</span></span> <span data-ttu-id="83728-125">[WCF 追蹤](https://msdn.microsoft.com/library/ms730342.aspx)提供詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="83728-125">[WCF tracing](https://msdn.microsoft.com/library/ms730342.aspx) provides more info.</span></span>
  
> [!IMPORTANT]
>  <span data-ttu-id="83728-126">請確定您減輕潛在的安全性威脅的啟用追蹤來公開敏感的商業資料。</span><span class="sxs-lookup"><span data-stu-id="83728-126">Make sure you mitigate potential security threats of exposing sensitive business data by enabling tracing.</span></span> <span data-ttu-id="83728-127">請參閱[最佳作法來保護在 Siebel 介面卡](../../adapters-and-accelerators/adapter-siebel/best-practices-to-secure-the-siebel-adapter.md)</span><span class="sxs-lookup"><span data-stu-id="83728-127">See [Best practices to secure the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/best-practices-to-secure-the-siebel-adapter.md)</span></span> 
  
## <a name="tracing-within-the-adapter"></a><span data-ttu-id="83728-128">配接器內追蹤</span><span class="sxs-lookup"><span data-stu-id="83728-128">Tracing Within the Adapter</span></span>  
 <span data-ttu-id="83728-129">BizTalk Adapter Pack 中的介面卡登追蹤檔案，例如錯誤、 警告和資訊的有用資訊的不同類別。</span><span class="sxs-lookup"><span data-stu-id="83728-129">The adapters in the BizTalk Adapter Pack log different categories of useful information to the trace file such as errors, warnings, and information.</span></span> <span data-ttu-id="83728-130">這類資訊是用於了解配接器內的程序流程和診斷配接器的問題。</span><span class="sxs-lookup"><span data-stu-id="83728-130">Such information is useful in understanding the process flow within the adapter and diagnosing issues with the adapter.</span></span> <span data-ttu-id="83728-131">您可以啟動[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和配接器追蹤的 BizTalk 應用程式和 WCF 服務模型應用程式，方法是加入個別的組態檔的摘錄。</span><span class="sxs-lookup"><span data-stu-id="83728-131">You can activate [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files.</span></span> <span data-ttu-id="83728-132">此外，您可以啟用追蹤，在設計階段和執行階段。</span><span class="sxs-lookup"><span data-stu-id="83728-132">Also, you can enable tracing both at design-time and run-time.</span></span>  
  
-   <span data-ttu-id="83728-133">**在設計階段追蹤**。</span><span class="sxs-lookup"><span data-stu-id="83728-133">**Tracing at design-time**.</span></span> <span data-ttu-id="83728-134">為設計階段經驗，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="83728-134">For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span> <span data-ttu-id="83728-135">所有這些工具可以從使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="83728-135">All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="83728-136">因此，若要啟用的設計階段經驗的追蹤，您必須加入摘要內的 devenv.exe.config 檔案位於*\<安裝磁碟機\>*: \Program Files\Microsoft Visual Studio *\<版本\>* \Common7\IDE。</span><span class="sxs-lookup"><span data-stu-id="83728-136">So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive\>*:\Program Files\Microsoft Visual Studio *\<version\>* \Common7\IDE.</span></span>  
  
-   <span data-ttu-id="83728-137">**在執行階段追蹤**。</span><span class="sxs-lookup"><span data-stu-id="83728-137">**Tracing at run-time**.</span></span> <span data-ttu-id="83728-138">進行執行階段追蹤，您必須將根據您使用應用程式的摘要。</span><span class="sxs-lookup"><span data-stu-id="83728-138">For run-time tracing, you must add the excerpt depending on the application you are using.</span></span>  
  
    -   <span data-ttu-id="83728-139">如[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式，您必須加入至 BizTalk 組態檔，通常是 BTSNTSvc.exe.config 的摘錄。BizTalk Server 的這個檔案是通常在\<安裝磁碟機\>: \Program Files\Microsoft BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="83728-139">For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For BizTalk Server, this file is available typically under \<installation drive\>:\Program Files\Microsoft BizTalk Server.</span></span>  
  
    -   <span data-ttu-id="83728-140">WCF 服務模型.NET 應用程式，您必須將摘要加入您專案的 app.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="83728-140">For a WCF service model .NET application, you must add the excerpt to the app.config file of your project.</span></span>  
  
 <span data-ttu-id="83728-141">若要啟用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和配接器追蹤，您必須新增下列摘錄中的`<configuration>`標記：</span><span class="sxs-lookup"><span data-stu-id="83728-141">To enable [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing, you must add the following excerpt within the `<configuration>` tag:</span></span>  
  
```  
<system.diagnostics>  
    <sources>  
      <source name="Microsoft.ServiceModel.Channels" switchValue="Error">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="Microsoft.Adapters.Siebel" switchValue="Information">  
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
  
 <span data-ttu-id="83728-142">這樣會將 WCF 追蹤儲存至 C:\log\AdapterTrace.svclog。</span><span class="sxs-lookup"><span data-stu-id="83728-142">This would save the WCF traces to C:\log\AdapterTrace.svclog.</span></span>  
  
## <a name="tracing-between-the-adapter-and-the-lob-application"></a><span data-ttu-id="83728-143">配接器與 LOB 應用程式之間的追蹤</span><span class="sxs-lookup"><span data-stu-id="83728-143">Tracing Between the Adapter and the LOB Application</span></span>  
 <span data-ttu-id="83728-144">您必須啟用追蹤，配接器與 LOB 應用程式，以診斷的問題，您懷疑內 LOB 應用程式之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="83728-144">You must enable tracing for communication between the adapter and the LOB application to diagnose issues you suspect within the LOB application.</span></span> <span data-ttu-id="83728-145">配接器也會取決於 LOB 追蹤 （用戶端/伺服器端） 來存取這項資訊。</span><span class="sxs-lookup"><span data-stu-id="83728-145">Adapters also depend on LOB tracing (client/server side) to get access to this information.</span></span> <span data-ttu-id="83728-146">開啟 LOB 追蹤的細節會排除這份文件。</span><span class="sxs-lookup"><span data-stu-id="83728-146">The specifics of turning on LOB tracing are excluded from this document.</span></span>  
  
 <span data-ttu-id="83728-147">此外，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]提供的繫結屬性 (**LogData**)，在設定為**True**而追蹤層級設定為**Verbose**、 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]記錄介面卡與 Siebel 系統之間的資訊流程。</span><span class="sxs-lookup"><span data-stu-id="83728-147">Additionally, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] provides a binding property (**LogData**), which if set to **True** and if the trace level is set to **Verbose**, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] logs the information flow between the adapter and the Siebel system.</span></span> <span data-ttu-id="83728-148">這項資訊會記錄以及相同的追蹤檔案中的配接器追蹤。</span><span class="sxs-lookup"><span data-stu-id="83728-148">This information is logged along with the adapter traces in the same trace file.</span></span>  
  
 <span data-ttu-id="83728-149">如需此繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Siebel 繫結屬性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="83728-149">For more information about this binding property, see [Read about BizTalk Adapter for Siebel Binding Properties](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).</span></span>  
  
## <a name="viewing-the-traces"></a><span data-ttu-id="83728-150">檢視追蹤</span><span class="sxs-lookup"><span data-stu-id="83728-150">Viewing the Traces</span></span>  
 <span data-ttu-id="83728-151">您可以使用 Windows Communication Foundation (WCF) 服務追蹤檢視器工具來檢視追蹤。</span><span class="sxs-lookup"><span data-stu-id="83728-151">You can use the Windows Communication Foundation (WCF) Service Trace Viewer tool to view the traces.</span></span> <span data-ttu-id="83728-152">如需此工具的詳細資訊，請參閱[使用服務追蹤檢視器檢視相關追蹤和疑難排解](https://msdn.microsoft.com/library/aa751795.aspx)。</span><span class="sxs-lookup"><span data-stu-id="83728-152">For more information about the tool, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](https://msdn.microsoft.com/library/aa751795.aspx).</span></span>  
  
## <a name="configuring-tracking-for-biztalk-applications"></a><span data-ttu-id="83728-153">設定追蹤的 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="83728-153">Configuring Tracking for BizTalk Applications</span></span>  
 <span data-ttu-id="83728-154">BizTalk 管理主控台可讓您設定各種追蹤選項，針對像是傳送埠、 接收埠。</span><span class="sxs-lookup"><span data-stu-id="83728-154">The BizTalk Administration Console enables you to configure various tracking options for things such as send ports, receive ports.</span></span> <span data-ttu-id="83728-155">追蹤組態設定可讓您追蹤輸入/輸出事件資料、 訊息屬性、 訊息內文，以及協調流程。</span><span class="sxs-lookup"><span data-stu-id="83728-155">The tracking configuration settings enable you to track inbound/outbound event data, message properties, message bodies, and orchestrations.</span></span> <span data-ttu-id="83728-156">如需有關如何設定追蹤的 BizTalk 應用程式的詳細資訊，請參閱[管理成品](../../core/managing-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="83728-156">For more information about configuring tracking for BizTalk applications, see [Managing Artifacts](../../core/managing-artifacts.md).</span></span>
  
<span data-ttu-id="83728-157">您也可以使用 群組中樞[檢視追蹤的訊息和執行個體資料](../../core/viewing-tracked-message-and-instance-data.md)，包括追蹤檢查清單和最佳作法。</span><span class="sxs-lookup"><span data-stu-id="83728-157">You can also use Group Hub to [Viewing Tracked Message and Instance Data](../../core/viewing-tracked-message-and-instance-data.md), including a tracking checklist, and best practices.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="83728-158">請參閱</span><span class="sxs-lookup"><span data-stu-id="83728-158">See Also</span></span>  
[<span data-ttu-id="83728-159">Siebel 配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="83728-159">Troubleshoot the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)