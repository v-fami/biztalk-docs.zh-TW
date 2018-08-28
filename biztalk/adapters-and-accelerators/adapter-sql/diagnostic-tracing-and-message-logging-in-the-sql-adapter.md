---
title: 診斷追蹤和訊息記錄中的 SQL 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d6599b4d-5650-4592-96af-ee43fb36357d
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fbcdac66c40a4b1d9c2b35d2f8268a63c8bd0e5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968151"
---
# <a name="diagnostic-tracing-and-message-logging-in-the-sql-adapter"></a><span data-ttu-id="29443-102">診斷追蹤和訊息記錄中的 SQL 配接器</span><span class="sxs-lookup"><span data-stu-id="29443-102">Diagnostic Tracing and Message Logging in the SQL adapter</span></span>
<span data-ttu-id="29443-103">診斷追蹤，可協助有效地診斷中使用配接器時可能遇到的問題。</span><span class="sxs-lookup"><span data-stu-id="29443-103">Diagnostic tracing helps to effectively diagnose problems that you might encounter when using the adapters.</span></span> <span data-ttu-id="29443-104">配接器用戶端可以啟動兩個層級的診斷追蹤：</span><span class="sxs-lookup"><span data-stu-id="29443-104">Adapter clients can activate diagnostic tracing at two levels:</span></span>  
  
- <span data-ttu-id="29443-105">配接器用戶端與配接器</span><span class="sxs-lookup"><span data-stu-id="29443-105">Between the adapter client and the adapter</span></span>  
  
- <span data-ttu-id="29443-106">配接器內</span><span class="sxs-lookup"><span data-stu-id="29443-106">Within the adapter</span></span>  
  
  <span data-ttu-id="29443-107">本節提供啟動下列層級追蹤的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="29443-107">This section provides information about activating tracing at these levels.</span></span>  
  
## <a name="tracing-between-the-adapter-client-and-the-adapter"></a><span data-ttu-id="29443-108">配接器用戶端與配接器之間的追蹤</span><span class="sxs-lookup"><span data-stu-id="29443-108">Tracing Between the Adapter Client and the Adapter</span></span>  
 <span data-ttu-id="29443-109">配接器用戶端可以啟用 WCF 追蹤，到配接器用戶端和配接器之間的追蹤問題。</span><span class="sxs-lookup"><span data-stu-id="29443-109">Adapter clients can enable WCF tracing to trace issues between the adapter client and the adapter.</span></span> <span data-ttu-id="29443-110">WCF 追蹤用來追蹤輸入的 XML 來源配接器用戶端使用 WCF 服務模型，且有助於診斷序列化問題。</span><span class="sxs-lookup"><span data-stu-id="29443-110">WCF tracing is used to trace the input XML that comes from the adapter client by using the WCF service model and is useful in diagnosing serialization issues.</span></span> <span data-ttu-id="29443-111">WCF 通道模型或從配接器至配接器用戶端的輸出訊息，不會使用 WCF 追蹤。</span><span class="sxs-lookup"><span data-stu-id="29443-111">WCF tracing is not used for the WCF channel model or for output messages from the adapter to the adapter client.</span></span> <span data-ttu-id="29443-112">您可以藉由將個別的組態檔中的摘錄，來啟用 WCF 追蹤的 BizTalk 應用程式和 WCF 服務模型的應用程式。</span><span class="sxs-lookup"><span data-stu-id="29443-112">You can activate WCF tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files.</span></span> <span data-ttu-id="29443-113">此外，您可以啟用追蹤兩者都在設計階段和執行階段。</span><span class="sxs-lookup"><span data-stu-id="29443-113">Also, you can enable tracing both at design time and run time.</span></span>  
  
- <span data-ttu-id="29443-114">**在設計階段追蹤**。</span><span class="sxs-lookup"><span data-stu-id="29443-114">**Tracing at design time**.</span></span> <span data-ttu-id="29443-115">為設計階段體驗，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="29443-115">For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span> <span data-ttu-id="29443-116">所有這些工具可從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="29443-116">All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="29443-117">因此，若要啟用追蹤的設計階段經驗，您必須將摘要加入 devenv.exe.config 檔案位於*\<安裝磁碟機\>*: \Program Files\Microsoft Visual Studio *\<版本\>* \Common7\IDE。</span><span class="sxs-lookup"><span data-stu-id="29443-117">So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive\>*:\Program Files\Microsoft Visual Studio *\<version\>* \Common7\IDE.</span></span>  
  
- <span data-ttu-id="29443-118">**在執行階段追蹤**。</span><span class="sxs-lookup"><span data-stu-id="29443-118">**Tracing at run time**.</span></span> <span data-ttu-id="29443-119">執行階段追蹤中，您必須將根據您使用應用程式的摘要。</span><span class="sxs-lookup"><span data-stu-id="29443-119">For run-time tracing, you must add the excerpt depending on the application you are using.</span></span>  
  
  - <span data-ttu-id="29443-120">針對[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式中，您必須加入 BizTalk 組態檔，通常是 BTSNTSvc.exe.config 中的摘要。BizTalk Server 的這個檔案會位於通常\<安裝磁碟機\>: \Program Files\Microsoft BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="29443-120">For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For BizTalk Server, this file is available typically under \<installation drive\>:\Program Files\Microsoft BizTalk Server.</span></span>  
  
  - <span data-ttu-id="29443-121">WCF 服務模型.NET 應用程式，您必須將摘要加入您專案的 app.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="29443-121">For a WCF service model .NET application, you must add the excerpt to the app.config file of your project.</span></span>  
  
  <span data-ttu-id="29443-122">若要啟用 WCF 追蹤，加入下列摘錄中的`<configuration>`標記。</span><span class="sxs-lookup"><span data-stu-id="29443-122">To enable WCF tracing, add the following excerpt within the `<configuration>` tag.</span></span>  
  
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
  
 <span data-ttu-id="29443-123">這將 C:\log\WCFTrace.svclog 的 WCF 追蹤。</span><span class="sxs-lookup"><span data-stu-id="29443-123">This saves the WCF traces to C:\log\WCFTrace.svclog.</span></span> <span data-ttu-id="29443-124">如需有關 WCF 追蹤的詳細資訊，請參閱 <<c0> [ 追蹤](https://msdn.microsoft.com/library/ms730342.aspx)。</span><span class="sxs-lookup"><span data-stu-id="29443-124">For more information about WCF tracing, see [Tracing](https://msdn.microsoft.com/library/ms730342.aspx).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="29443-125">請確定您緩解潛在的安全性威脅的啟用追蹤，以公開機密商務資料。</span><span class="sxs-lookup"><span data-stu-id="29443-125">Make sure you mitigate potential security threats of exposing sensitive business data by enabling tracing.</span></span> <span data-ttu-id="29443-126">如需建議請參閱[最佳做法來保護 SQL 配接器](../../adapters-and-accelerators/adapter-sql/best-practices-to-secure-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="29443-126">For recommendations see [Best practices to secure the SQL adapter](../../adapters-and-accelerators/adapter-sql/best-practices-to-secure-the-sql-adapter.md).</span></span>
  
## <a name="tracing-within-the-adapter"></a><span data-ttu-id="29443-127">追蹤配接器內</span><span class="sxs-lookup"><span data-stu-id="29443-127">Tracing Within the Adapter</span></span>  
 <span data-ttu-id="29443-128">配接器追蹤檔，例如錯誤、 警告和資訊訊息記錄有用資訊的不同的類別。</span><span class="sxs-lookup"><span data-stu-id="29443-128">The adapters log different categories of useful information to the trace file such as errors, warnings, and information messages.</span></span> <span data-ttu-id="29443-129">這類資訊很有用了解配接器內的程序流程和診斷配接器的問題。</span><span class="sxs-lookup"><span data-stu-id="29443-129">Such information is useful in understanding the process flow within the adapter and diagnosing issues with the adapter.</span></span> <span data-ttu-id="29443-130">您可以啟用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和配接器追蹤的 BizTalk 應用程式和 WCF 服務應用程式模型，藉由將個別的組態檔中的摘錄。</span><span class="sxs-lookup"><span data-stu-id="29443-130">You can activate the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files.</span></span> <span data-ttu-id="29443-131">此外，您可以啟用追蹤兩者都在設計階段和執行階段。</span><span class="sxs-lookup"><span data-stu-id="29443-131">Also, you can enable tracing both at design time and run time.</span></span>  
  
- <span data-ttu-id="29443-132">**在設計階段追蹤**。</span><span class="sxs-lookup"><span data-stu-id="29443-132">**Tracing at design time**.</span></span> <span data-ttu-id="29443-133">為設計階段體驗，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="29443-133">For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span> <span data-ttu-id="29443-134">所有這些工具可從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="29443-134">All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="29443-135">因此，若要啟用追蹤的設計階段經驗，您必須將摘要加入 devenv.exe.config 檔案位於*\<安裝磁碟機\>*: \Program Files\Microsoft Visual Studio *\<版本\>* \Common7\IDE。</span><span class="sxs-lookup"><span data-stu-id="29443-135">So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive\>*:\Program Files\Microsoft Visual Studio *\<version\>* \Common7\IDE.</span></span>  
  
- <span data-ttu-id="29443-136">**在執行階段追蹤**。</span><span class="sxs-lookup"><span data-stu-id="29443-136">**Tracing at run time**.</span></span> <span data-ttu-id="29443-137">執行階段追蹤中，您必須將根據您使用應用程式的摘要。</span><span class="sxs-lookup"><span data-stu-id="29443-137">For run-time tracing, you must add the excerpt depending on the application you are using.</span></span>  
  
  - <span data-ttu-id="29443-138">針對[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式中，您必須加入 BizTalk 組態檔，通常是 BTSNTSvc.exe.config 中的摘要。BizTalk Server 的這個檔案會位於通常\<安裝磁碟機\>: \Program Files\Microsoft BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="29443-138">For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For BizTalk Server, this file is available typically under \<installation drive\>:\Program Files\Microsoft BizTalk Server.</span></span>  
  
  - <span data-ttu-id="29443-139">WCF 服務模型.NET 應用程式，您必須將摘要加入您專案的 app.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="29443-139">For a WCF service model .NET application, you must add the excerpt to the app.config file of your project.</span></span>  
  
  <span data-ttu-id="29443-140">若要啟用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和 配接器追蹤，加入下列摘錄中的`<configuration>`標記。</span><span class="sxs-lookup"><span data-stu-id="29443-140">To enable [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing, add the following excerpt within the `<configuration>` tag.</span></span>  
  
```  
<system.diagnostics>  
    <sources>  
      <source name="Microsoft.ServiceModel.Channels" switchValue="Error">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="Microsoft.Adapters.Sql" switchValue="Information">  
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
  
 <span data-ttu-id="29443-141">這將 C:\log\AdapterTrace.svclog 的 WCF 追蹤。</span><span class="sxs-lookup"><span data-stu-id="29443-141">This saves the WCF traces to C:\log\AdapterTrace.svclog.</span></span>  
  
## <a name="viewing-the-traces"></a><span data-ttu-id="29443-142">檢視追蹤</span><span class="sxs-lookup"><span data-stu-id="29443-142">Viewing the Traces</span></span>  
 <span data-ttu-id="29443-143">您可以使用 Windows Communication Foundation (WCF) 服務追蹤檢視器工具來檢視追蹤。</span><span class="sxs-lookup"><span data-stu-id="29443-143">You can use the Windows Communication Foundation (WCF) Service Trace Viewer tool to view the traces.</span></span> <span data-ttu-id="29443-144">如需有關此工具的詳細資訊，請參閱[使用服務追蹤檢視器檢視相互關聯的追蹤和麻煩](https://msdn.microsoft.com/library/aa751795.aspx)。</span><span class="sxs-lookup"><span data-stu-id="29443-144">For more information about the tool, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubles](https://msdn.microsoft.com/library/aa751795.aspx).</span></span>
  
## <a name="configuring-tracking-for-biztalk-applications"></a><span data-ttu-id="29443-145">設定 BizTalk 應用程式的追蹤</span><span class="sxs-lookup"><span data-stu-id="29443-145">Configuring Tracking for BizTalk Applications</span></span>  
 <span data-ttu-id="29443-146">BizTalk Server 管理主控台可讓您設定不同的追蹤選項項目，例如傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="29443-146">The BizTalk Server Administration console lets you configure various tracking options for items such as send ports and receive ports.</span></span> <span data-ttu-id="29443-147">追蹤組態設定可讓您追蹤輸入和輸出事件資料、 訊息屬性、 訊息內文，以及協調流程。</span><span class="sxs-lookup"><span data-stu-id="29443-147">The tracking configuration settings enable you to track inbound and outbound event data, message properties, message bodies, and orchestrations.</span></span> <span data-ttu-id="29443-148">如需有關如何設定追蹤的 BizTalk 應用程式的詳細資訊，請參閱[管理成品](../../core/managing-artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="29443-148">For more information about configuring tracking for BizTalk applications, see the [Managing Artifacts](../../core/managing-artifacts.md).</span></span>
  
 <span data-ttu-id="29443-149">您也可以使用健全狀況與活動追蹤 (HAT) 來檢視歷史或追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="29443-149">You can also use Health and Activity Tracking (HAT) to view historical or tracked data.</span></span> <span data-ttu-id="29443-150">如需詳細資訊，請參閱 <<c0> [ 檢視歷程記錄和追蹤資料](../../core/viewing-historical-and-tracked-data.md)。</span><span class="sxs-lookup"><span data-stu-id="29443-150">For more information, see [Viewing Historical and Tracked Data](../../core/viewing-historical-and-tracked-data.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="29443-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29443-151">See Also</span></span>  
 [<span data-ttu-id="29443-152">SQL 配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="29443-152">Troubleshoot the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/troubleshoot-the-sql-adapter.md)