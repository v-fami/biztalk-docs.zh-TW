---
title: 診斷追蹤和訊息記錄 Siebel 配接器 |Microsoft Docs
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
ms.openlocfilehash: 5ab369a74058f374ee229eb25d0697dc96f539ed
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994575"
---
# <a name="diagnostic-tracing-and-message-logging-for-the-siebel-adapter"></a><span data-ttu-id="91c70-102">診斷追蹤和 Siebel 配接器的訊息記錄</span><span class="sxs-lookup"><span data-stu-id="91c70-102">Diagnostic Tracing and Message Logging for the Siebel adapter</span></span>
<span data-ttu-id="91c70-103">配接器用戶端可以啟用診斷追蹤，才能有效地診斷使用的配接器時所遇到的問題。</span><span class="sxs-lookup"><span data-stu-id="91c70-103">Adapter clients can enable diagnostic tracing to effectively diagnose problems encountered while using the adapters.</span></span> <span data-ttu-id="91c70-104">配接器用戶端可以啟動三個不同層級的追蹤：</span><span class="sxs-lookup"><span data-stu-id="91c70-104">Adapter clients can activate tracing at three different levels:</span></span>  
  
- <span data-ttu-id="91c70-105">配接器用戶端與配接器</span><span class="sxs-lookup"><span data-stu-id="91c70-105">Between the adapter client and the adapter</span></span>  
  
- <span data-ttu-id="91c70-106">配接器內</span><span class="sxs-lookup"><span data-stu-id="91c70-106">Within the adapter</span></span>  
  
- <span data-ttu-id="91c70-107">配接器之間的營運 (LOB) 應用程式</span><span class="sxs-lookup"><span data-stu-id="91c70-107">Between the adapter and the line-of-business (LOB) application</span></span>  
  
  <span data-ttu-id="91c70-108">本節提供啟動下列層級追蹤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="91c70-108">This section provides information about activating tracing at these levels.</span></span>  
  
## <a name="tracing-between-the-adapter-client-and-the-adapter"></a><span data-ttu-id="91c70-109">配接器用戶端與配接器之間的追蹤</span><span class="sxs-lookup"><span data-stu-id="91c70-109">Tracing between the adapter client and the adapter</span></span>  
 <span data-ttu-id="91c70-110">配接器用戶端可以啟用 WCF 追蹤，到配接器用戶端和配接器之間的追蹤問題。</span><span class="sxs-lookup"><span data-stu-id="91c70-110">Adapter clients can enable WCF tracing to trace issues between the adapter client and the adapter.</span></span> <span data-ttu-id="91c70-111">WCF 追蹤用來追蹤來自配接器用戶端會使用 WCF 服務模型的輸入的 Xml，且有助於診斷序列化問題。</span><span class="sxs-lookup"><span data-stu-id="91c70-111">WCF tracing is used to trace the input XMLs coming from the adapter client using the WCF service model and is useful in diagnosing serialization issues.</span></span> <span data-ttu-id="91c70-112">WCF 通道模型或從配接器至配接器用戶端的輸出訊息，不會使用 WCF 追蹤。</span><span class="sxs-lookup"><span data-stu-id="91c70-112">WCF tracing is not used for the WCF channel model or for output messages from the adapter to the adapter client.</span></span> <span data-ttu-id="91c70-113">您可以藉由將個別的組態檔中的摘錄，來啟用 WCF 追蹤的 BizTalk 應用程式和 WCF 服務模型的應用程式。</span><span class="sxs-lookup"><span data-stu-id="91c70-113">You can activate WCF tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files.</span></span> <span data-ttu-id="91c70-114">此外，您可以啟用追蹤，在設計階段和執行階段。</span><span class="sxs-lookup"><span data-stu-id="91c70-114">Also, you can enable tracing both at design-time and run-time.</span></span>  
  
- <span data-ttu-id="91c70-115">**在設計階段追蹤**。</span><span class="sxs-lookup"><span data-stu-id="91c70-115">**Tracing at design-time**.</span></span> <span data-ttu-id="91c70-116">為設計階段體驗，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="91c70-116">For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span> <span data-ttu-id="91c70-117">所有這些工具可從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="91c70-117">All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="91c70-118">因此，若要啟用追蹤的設計階段經驗，您必須將摘要加入 devenv.exe.config 檔案位於*\<安裝磁碟機\>*: \Program Files\Microsoft Visual Studio *\<版本\>* \Common7\IDE。</span><span class="sxs-lookup"><span data-stu-id="91c70-118">So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive\>*:\Program Files\Microsoft Visual Studio *\<version\>* \Common7\IDE.</span></span>  
  
- <span data-ttu-id="91c70-119">**在執行階段追蹤**。</span><span class="sxs-lookup"><span data-stu-id="91c70-119">**Tracing at run-time**.</span></span> <span data-ttu-id="91c70-120">執行階段追蹤中，您必須將根據您使用應用程式的摘要。</span><span class="sxs-lookup"><span data-stu-id="91c70-120">For run-time tracing, you must add the excerpt depending on the application you are using.</span></span>  
  
  - <span data-ttu-id="91c70-121">針對[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式，您必須加入 BizTalk 組態檔，通常是 BTSNTSvc.exe.config 中的摘要。BizTalk Server 的這個檔案會位於通常\<安裝磁碟機\>: \Program Files\Microsoft BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="91c70-121">For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For BizTalk Server, this file is available typically under \<installation drive\>:\Program Files\Microsoft BizTalk Server.</span></span>  
  
  - <span data-ttu-id="91c70-122">WCF 服務模型.NET 應用程式，您必須將摘要加入您專案的 app.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="91c70-122">For a WCF service model .NET application, you must add the excerpt to the app.config file of your project.</span></span>  
  
  <span data-ttu-id="91c70-123">若要啟用 WCF 追蹤，您必須新增下列摘錄中的`<configuration>`標記：</span><span class="sxs-lookup"><span data-stu-id="91c70-123">To enable WCF tracing, you must add the following excerpt within the `<configuration>` tag:</span></span>
  
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
  
 <span data-ttu-id="91c70-124">這將 C:\log\WCFTrace.svclog 的 WCF 追蹤。</span><span class="sxs-lookup"><span data-stu-id="91c70-124">This saves the WCF traces to C:\log\WCFTrace.svclog.</span></span> <span data-ttu-id="91c70-125">[WCF 追蹤](https://msdn.microsoft.com/library/ms730342.aspx)提供詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="91c70-125">[WCF tracing](https://msdn.microsoft.com/library/ms730342.aspx) provides more info.</span></span>
  
> [!IMPORTANT]
>  <span data-ttu-id="91c70-126">請確定您緩解潛在的安全性威脅的啟用追蹤，以公開機密商務資料。</span><span class="sxs-lookup"><span data-stu-id="91c70-126">Make sure you mitigate potential security threats of exposing sensitive business data by enabling tracing.</span></span> <span data-ttu-id="91c70-127">請參閱[最佳作法來保護 Siebel 配接器](../../adapters-and-accelerators/adapter-siebel/best-practices-to-secure-the-siebel-adapter.md)</span><span class="sxs-lookup"><span data-stu-id="91c70-127">See [Best practices to secure the Siebel adapter](../../adapters-and-accelerators/adapter-siebel/best-practices-to-secure-the-siebel-adapter.md)</span></span> 
  
## <a name="tracing-within-the-adapter"></a><span data-ttu-id="91c70-128">追蹤配接器內</span><span class="sxs-lookup"><span data-stu-id="91c70-128">Tracing Within the Adapter</span></span>  
 <span data-ttu-id="91c70-129">BizTalk Adapter Pack 中的配接器追蹤檔，例如錯誤、 警告和資訊記錄有用資訊的不同的類別。</span><span class="sxs-lookup"><span data-stu-id="91c70-129">The adapters in the BizTalk Adapter Pack log different categories of useful information to the trace file such as errors, warnings, and information.</span></span> <span data-ttu-id="91c70-130">這類資訊很有用了解配接器內的程序流程和診斷配接器的問題。</span><span class="sxs-lookup"><span data-stu-id="91c70-130">Such information is useful in understanding the process flow within the adapter and diagnosing issues with the adapter.</span></span> <span data-ttu-id="91c70-131">您可以啟用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和配接器追蹤的 BizTalk 應用程式和 WCF 服務應用程式模型，藉由將個別的組態檔中的摘錄。</span><span class="sxs-lookup"><span data-stu-id="91c70-131">You can activate [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files.</span></span> <span data-ttu-id="91c70-132">此外，您可以啟用追蹤，在設計階段和執行階段。</span><span class="sxs-lookup"><span data-stu-id="91c70-132">Also, you can enable tracing both at design-time and run-time.</span></span>  
  
- <span data-ttu-id="91c70-133">**在設計階段追蹤**。</span><span class="sxs-lookup"><span data-stu-id="91c70-133">**Tracing at design-time**.</span></span> <span data-ttu-id="91c70-134">為設計階段體驗，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="91c70-134">For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span> <span data-ttu-id="91c70-135">所有這些工具可從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="91c70-135">All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="91c70-136">因此，若要啟用追蹤的設計階段經驗，您必須將摘要加入 devenv.exe.config 檔案位於*\<安裝磁碟機\>*: \Program Files\Microsoft Visual Studio *\<版本\>* \Common7\IDE。</span><span class="sxs-lookup"><span data-stu-id="91c70-136">So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive\>*:\Program Files\Microsoft Visual Studio *\<version\>* \Common7\IDE.</span></span>  
  
- <span data-ttu-id="91c70-137">**在執行階段追蹤**。</span><span class="sxs-lookup"><span data-stu-id="91c70-137">**Tracing at run-time**.</span></span> <span data-ttu-id="91c70-138">執行階段追蹤中，您必須將根據您使用應用程式的摘要。</span><span class="sxs-lookup"><span data-stu-id="91c70-138">For run-time tracing, you must add the excerpt depending on the application you are using.</span></span>  
  
  - <span data-ttu-id="91c70-139">針對[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式，您必須加入 BizTalk 組態檔，通常是 BTSNTSvc.exe.config 中的摘要。BizTalk Server 的這個檔案會位於通常\<安裝磁碟機\>: \Program Files\Microsoft BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="91c70-139">For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For BizTalk Server, this file is available typically under \<installation drive\>:\Program Files\Microsoft BizTalk Server.</span></span>  
  
  - <span data-ttu-id="91c70-140">WCF 服務模型.NET 應用程式，您必須將摘要加入您專案的 app.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="91c70-140">For a WCF service model .NET application, you must add the excerpt to the app.config file of your project.</span></span>  
  
  <span data-ttu-id="91c70-141">若要啟用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和配接器追蹤，您必須新增下列摘錄中的`<configuration>`標記：</span><span class="sxs-lookup"><span data-stu-id="91c70-141">To enable [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing, you must add the following excerpt within the `<configuration>` tag:</span></span>  
  
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
  
 <span data-ttu-id="91c70-142">這會將 WCF 追蹤儲存到 C:\log\AdapterTrace.svclog。</span><span class="sxs-lookup"><span data-stu-id="91c70-142">This would save the WCF traces to C:\log\AdapterTrace.svclog.</span></span>  
  
## <a name="tracing-between-the-adapter-and-the-lob-application"></a><span data-ttu-id="91c70-143">配接器與 LOB 應用程式之間的追蹤</span><span class="sxs-lookup"><span data-stu-id="91c70-143">Tracing Between the Adapter and the LOB Application</span></span>  
 <span data-ttu-id="91c70-144">您必須啟用追蹤配接器和診斷問題，您懷疑 LOB 應用程式中的 LOB 應用程式之間進行通訊。</span><span class="sxs-lookup"><span data-stu-id="91c70-144">You must enable tracing for communication between the adapter and the LOB application to diagnose issues you suspect within the LOB application.</span></span> <span data-ttu-id="91c70-145">配接器也相依於追蹤 （用戶端/伺服器端） 來存取這項資訊的 LOB。</span><span class="sxs-lookup"><span data-stu-id="91c70-145">Adapters also depend on LOB tracing (client/server side) to get access to this information.</span></span> <span data-ttu-id="91c70-146">開啟 LOB 追蹤的細節會排除這份文件。</span><span class="sxs-lookup"><span data-stu-id="91c70-146">The specifics of turning on LOB tracing are excluded from this document.</span></span>  
  
 <span data-ttu-id="91c70-147">此外，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]提供的繫結屬性 (**LogData**)，如果設定為**True**且的追蹤層級設定為**Verbose**， [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]記錄配接器與 Siebel 系統之間的資訊流程。</span><span class="sxs-lookup"><span data-stu-id="91c70-147">Additionally, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] provides a binding property (**LogData**), which if set to **True** and if the trace level is set to **Verbose**, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] logs the information flow between the adapter and the Siebel system.</span></span> <span data-ttu-id="91c70-148">這項資訊會記錄以及相同的追蹤檔案中的配接器追蹤。</span><span class="sxs-lookup"><span data-stu-id="91c70-148">This information is logged along with the adapter traces in the same trace file.</span></span>  
  
 <span data-ttu-id="91c70-149">如需有關這個繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for Siebel 繫結屬性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="91c70-149">For more information about this binding property, see [Read about BizTalk Adapter for Siebel Binding Properties](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md).</span></span>  
  
## <a name="viewing-the-traces"></a><span data-ttu-id="91c70-150">檢視追蹤</span><span class="sxs-lookup"><span data-stu-id="91c70-150">Viewing the Traces</span></span>  
 <span data-ttu-id="91c70-151">您可以使用 Windows Communication Foundation (WCF) 服務追蹤檢視器工具來檢視追蹤。</span><span class="sxs-lookup"><span data-stu-id="91c70-151">You can use the Windows Communication Foundation (WCF) Service Trace Viewer tool to view the traces.</span></span> <span data-ttu-id="91c70-152">如需有關此工具的詳細資訊，請參閱[使用服務追蹤檢視器檢視相互關聯的追蹤和疑難排解](https://msdn.microsoft.com/library/aa751795.aspx)。</span><span class="sxs-lookup"><span data-stu-id="91c70-152">For more information about the tool, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](https://msdn.microsoft.com/library/aa751795.aspx).</span></span>  
  
## <a name="configuring-tracking-for-biztalk-applications"></a><span data-ttu-id="91c70-153">設定 BizTalk 應用程式的追蹤</span><span class="sxs-lookup"><span data-stu-id="91c70-153">Configuring Tracking for BizTalk Applications</span></span>  
 <span data-ttu-id="91c70-154">BizTalk 管理主控台可讓您設定各種不同的追蹤選項，針對像是傳送埠、 接收埠。</span><span class="sxs-lookup"><span data-stu-id="91c70-154">The BizTalk Administration Console enables you to configure various tracking options for things such as send ports, receive ports.</span></span> <span data-ttu-id="91c70-155">追蹤組態設定可讓您追蹤輸入/輸出事件資料、 訊息屬性、 訊息內文，以及協調流程。</span><span class="sxs-lookup"><span data-stu-id="91c70-155">The tracking configuration settings enable you to track inbound/outbound event data, message properties, message bodies, and orchestrations.</span></span> <span data-ttu-id="91c70-156">如需有關如何設定追蹤的 BizTalk 應用程式的詳細資訊，請參閱[管理成品](../../core/managing-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="91c70-156">For more information about configuring tracking for BizTalk applications, see [Managing Artifacts](../../core/managing-artifacts.md).</span></span>
  
<span data-ttu-id="91c70-157">您也可以使用 群組中樞[檢視追蹤的訊息和執行個體資料](../../core/viewing-tracked-message-and-instance-data.md)，包括追蹤的檢查清單，以及最佳作法。</span><span class="sxs-lookup"><span data-stu-id="91c70-157">You can also use Group Hub to [Viewing Tracked Message and Instance Data](../../core/viewing-tracked-message-and-instance-data.md), including a tracking checklist, and best practices.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="91c70-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91c70-158">See Also</span></span>  
[<span data-ttu-id="91c70-159">Siebel 配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="91c70-159">Troubleshoot the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)