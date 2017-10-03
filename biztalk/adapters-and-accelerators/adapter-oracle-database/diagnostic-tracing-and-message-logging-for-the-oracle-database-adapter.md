---
title: "診斷追蹤和訊息記錄的 Oracle 資料庫配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracing
- message logging
- tracing, within the adapter
- tracing, between the adapter client and the adapter
ms.assetid: 971d34e4-5609-42c6-85b9-d9b1989fc47d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 126ab9336d90fa85f03e310eca0a9bdebb442792
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="diagnostic-tracing-and-message-logging-for-the-oracle-database-adapter"></a><span data-ttu-id="692e8-102">診斷追蹤和 Oracle 資料庫配接器的訊息記錄</span><span class="sxs-lookup"><span data-stu-id="692e8-102">Diagnostic tracing and message logging for the Oracle Database adapter</span></span>
<span data-ttu-id="692e8-103">診斷追蹤可讓您有效地診斷使用配接器時，可能會遇到的問題。</span><span class="sxs-lookup"><span data-stu-id="692e8-103">Diagnostic tracing helps to effectively diagnose problems that you might encounter when using the adapters.</span></span> <span data-ttu-id="692e8-104">本主題提供下列兩種支援的追蹤資訊[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="692e8-104">This topic provides information about the following two types of tracing supported with [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]:</span></span>  
  
-   <span data-ttu-id="692e8-105">WCF 配接器用戶端與配接器之間的追蹤</span><span class="sxs-lookup"><span data-stu-id="692e8-105">WCF tracing between the adapter client and the adapter</span></span>  
  
-   <span data-ttu-id="692e8-106">WCF 配接器內的追蹤</span><span class="sxs-lookup"><span data-stu-id="692e8-106">WCF tracing within the adapter</span></span>  
  
## <a name="wcf-tracing-between-the-adapter-client-and-the-adapter"></a><span data-ttu-id="692e8-107">WCF 配接器用戶端與配接器之間的追蹤</span><span class="sxs-lookup"><span data-stu-id="692e8-107">WCF Tracing Between the Adapter Client and the Adapter</span></span>  
 <span data-ttu-id="692e8-108">配接器用戶端可以啟用 WCF 追蹤，配接器用戶端與配接器之間的追蹤問題。</span><span class="sxs-lookup"><span data-stu-id="692e8-108">Adapter clients can enable WCF tracing to trace issues between the adapter client and the adapter.</span></span> <span data-ttu-id="692e8-109">WCF 追蹤用來追蹤輸入的 XML，來自配接器用戶端使用 WCF 服務模型，有助於診斷序列化的問題。</span><span class="sxs-lookup"><span data-stu-id="692e8-109">WCF tracing is used to trace the input XML that comes from the adapter client by using the WCF service model, and is useful in diagnosing serialization issues.</span></span> <span data-ttu-id="692e8-110">WCF 追蹤不是適用於 WCF 通道模型或是從配接器至配接器用戶端的輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="692e8-110">WCF tracing is not used for the WCF channel model or for output messages from the adapter to the adapter client.</span></span> <span data-ttu-id="692e8-111">若要啟動 WCF 追蹤的 BizTalk 應用程式和 WCF 服務模型應用程式，您可以加入個別的組態檔中的摘錄。</span><span class="sxs-lookup"><span data-stu-id="692e8-111">You can activate WCF tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files.</span></span> <span data-ttu-id="692e8-112">此外，您可以啟用追蹤，在設計階段和執行階段。</span><span class="sxs-lookup"><span data-stu-id="692e8-112">Also, you can enable tracing both at design-time and run-time.</span></span>  
  
-   <span data-ttu-id="692e8-113">**在設計階段追蹤**。</span><span class="sxs-lookup"><span data-stu-id="692e8-113">**Tracing at design-time**.</span></span> <span data-ttu-id="692e8-114">為設計階段經驗，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="692e8-114">For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span> <span data-ttu-id="692e8-115">所有這些工具可以從使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="692e8-115">All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="692e8-116">因此，若要啟用的設計階段經驗的追蹤，您必須加入摘要內的 devenv.exe.config 檔案位於*\<安裝磁碟機 >*: \Program Files\Microsoft Visual Studio  *\<版本 >*\Common7\IDE。</span><span class="sxs-lookup"><span data-stu-id="692e8-116">So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive>*:\Program Files\Microsoft Visual Studio *\<version>*\Common7\IDE.</span></span>  
  
-   <span data-ttu-id="692e8-117">**在執行階段追蹤**。</span><span class="sxs-lookup"><span data-stu-id="692e8-117">**Tracing at run-time**.</span></span> <span data-ttu-id="692e8-118">進行執行階段追蹤，您必須將根據您使用應用程式的摘要。</span><span class="sxs-lookup"><span data-stu-id="692e8-118">For run-time tracing, you must add the excerpt depending on the application you are using.</span></span>  
  
    -   <span data-ttu-id="692e8-119">如[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式，您必須加入至 BizTalk 組態檔，通常是 BTSNTSvc.exe.config 的摘錄。如[!INCLUDE[prague](../../includes/prague-md.md)]，這個檔案位在通常\<安裝磁碟機 >: \Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="692e8-119">For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For [!INCLUDE[prague](../../includes/prague-md.md)], this file is available typically under \<installation drive>:\Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].</span></span>  
  
    -   <span data-ttu-id="692e8-120">WCF 服務模型.NET 應用程式，您必須將摘要加入您專案的 app.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="692e8-120">For a WCF service model .NET application, you must add the excerpt to the app.config file of your project.</span></span>  
  
 <span data-ttu-id="692e8-121">若要啟用 WCF 追蹤，加入下列摘錄中的`<configuration>`標記。</span><span class="sxs-lookup"><span data-stu-id="692e8-121">To enable WCF tracing, add the following excerpt within the `<configuration>` tag.</span></span>  
  
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
  
 <span data-ttu-id="692e8-122">這將 C:\log\WCFTrace.svclog WCF 追蹤。</span><span class="sxs-lookup"><span data-stu-id="692e8-122">This saves the WCF traces to C:\log\WCFTrace.svclog.</span></span> <span data-ttu-id="692e8-123">[WCF 追蹤](https://msdn.microsoft.com/library/ms730342.aspx)提供良好的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="692e8-123">[WCF Tracing](https://msdn.microsoft.com/library/ms730342.aspx) provides more good information.</span></span>
  
> [!IMPORTANT]
>  <span data-ttu-id="692e8-124">請確定您減輕潛在的安全性威脅的啟用追蹤來公開敏感的商業資料。</span><span class="sxs-lookup"><span data-stu-id="692e8-124">Make sure you mitigate potential security threats of exposing sensitive business data by enabling tracing.</span></span> <span data-ttu-id="692e8-125">如需建議，請參閱[最佳作法來保護 Oracle 資料庫配接器](../../adapters-and-accelerators/adapter-oracle-database/best-practices-to-secure-the-oracle-database-adapter.md)</span><span class="sxs-lookup"><span data-stu-id="692e8-125">For recommendations, see [Best practices to secure the Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/best-practices-to-secure-the-oracle-database-adapter.md)</span></span>
  
## <a name="wcf-tracing-within-the-adapter"></a><span data-ttu-id="692e8-126">WCF 配接器內的追蹤</span><span class="sxs-lookup"><span data-stu-id="692e8-126">WCF tracing within the adapter</span></span>  
 <span data-ttu-id="692e8-127">配接器追蹤檔，例如錯誤、 警告和資訊訊息記錄有用資訊的不同的類別。</span><span class="sxs-lookup"><span data-stu-id="692e8-127">The adapters log different categories of useful information to the trace file such as errors, warnings, and information messages.</span></span> <span data-ttu-id="692e8-128">這類資訊是用於了解配接器內的程序流程和診斷配接器的問題。</span><span class="sxs-lookup"><span data-stu-id="692e8-128">Such information is useful in understanding the process flow within the adapter and diagnosing issues with the adapter.</span></span> <span data-ttu-id="692e8-129">您可以啟動[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和配接器追蹤的 BizTalk 應用程式和 WCF 服務模型應用程式，方法是加入個別的組態檔的摘錄。</span><span class="sxs-lookup"><span data-stu-id="692e8-129">You can activate the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing for BizTalk applications and WCF service model applications by adding an excerpt to the respective configuration files.</span></span> <span data-ttu-id="692e8-130">此外，您可以啟用追蹤，在設計階段和執行階段。</span><span class="sxs-lookup"><span data-stu-id="692e8-130">Also, you can enable tracing both at design-time and run-time.</span></span>  
  
-   <span data-ttu-id="692e8-131">**在設計階段追蹤**。</span><span class="sxs-lookup"><span data-stu-id="692e8-131">**Tracing at design-time**.</span></span> <span data-ttu-id="692e8-132">為設計階段經驗，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="692e8-132">For the design-time experience, you may use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], or the [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)].</span></span> <span data-ttu-id="692e8-133">所有這些工具可以從使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="692e8-133">All these tools can be used from [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="692e8-134">因此，若要啟用的設計階段經驗的追蹤，您必須加入摘要內的 devenv.exe.config 檔案位於*\<安裝磁碟機 >*: \Program Files\Microsoft Visual Studio  *\<版本 >*\Common7\IDE。</span><span class="sxs-lookup"><span data-stu-id="692e8-134">So, to enable tracing for the design-time experience, you must add the excerpt to the devenv.exe.config file located in *\<installation drive>*:\Program Files\Microsoft Visual Studio *\<version>*\Common7\IDE.</span></span>  
  
-   <span data-ttu-id="692e8-135">**在執行階段追蹤**。</span><span class="sxs-lookup"><span data-stu-id="692e8-135">**Tracing at run-time**.</span></span> <span data-ttu-id="692e8-136">進行執行階段追蹤，您必須將根據您使用應用程式的摘要。</span><span class="sxs-lookup"><span data-stu-id="692e8-136">For run-time tracing, you must add the excerpt depending on the application you are using.</span></span>  
  
    -   <span data-ttu-id="692e8-137">如[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式，您必須加入至 BizTalk 組態檔，通常是 BTSNTSvc.exe.config 的摘錄。如[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]，這個檔案位在通常\<安裝磁碟機 >: \Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="692e8-137">For a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, you must add the excerpt to the BizTalk configuration file, typically BTSNTSvc.exe.config. For [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)], this file is available typically under \<installation drive>:\Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].</span></span>  
  
    -   <span data-ttu-id="692e8-138">WCF 服務模型.NET 應用程式，您必須將摘要加入您專案的 app.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="692e8-138">For a WCF service model .NET application, you must add the excerpt to the app.config file of your project.</span></span>  
  
 <span data-ttu-id="692e8-139">若要啟用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和配接器追蹤，加入下列摘錄中的`<configuration>`標記：</span><span class="sxs-lookup"><span data-stu-id="692e8-139">To enable [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] and adapter tracing, add the following excerpt within the `<configuration>` tag:</span></span>  
  
```  
\<system.diagnostics>  
    <sources>  
      <source name="Microsoft.ServiceModel.Channels" switchValue="Error">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name=" Microsoft.Adapters.OracleDB" switchValue="Information">  
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
  
 <span data-ttu-id="692e8-140">這將 C:\log\AdapterTrace.svclog WCF 追蹤。</span><span class="sxs-lookup"><span data-stu-id="692e8-140">This saves the WCF traces to C:\log\AdapterTrace.svclog.</span></span>  
  
## <a name="viewing-the-traces"></a><span data-ttu-id="692e8-141">檢視追蹤</span><span class="sxs-lookup"><span data-stu-id="692e8-141">Viewing the traces</span></span>  
 <span data-ttu-id="692e8-142">您可以使用 Windows Communication Foundation (WCF) 服務追蹤檢視器工具來檢視追蹤。</span><span class="sxs-lookup"><span data-stu-id="692e8-142">You can use the Windows Communication Foundation (WCF) Service Trace Viewer tool to view the traces.</span></span> <span data-ttu-id="692e8-143">請參閱[使用服務追蹤檢視器檢視相關追蹤並進行疑難排解](https://msdn.microsoft.com/library/aa751795.aspx)。</span><span class="sxs-lookup"><span data-stu-id="692e8-143">See [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](https://msdn.microsoft.com/library/aa751795.aspx).</span></span>
  
## <a name="configuring-tracking-for-biztalk-applications"></a><span data-ttu-id="692e8-144">設定追蹤的 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="692e8-144">Configuring Tracking for BizTalk Applications</span></span>  
 <span data-ttu-id="692e8-145">BizTalk Server 管理主控台可讓您設定不同的追蹤選項項目，例如傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="692e8-145">The BizTalk Server Administration console lets you configure various tracking options for items such as send ports and receive ports.</span></span> <span data-ttu-id="692e8-146">追蹤組態設定可讓您追蹤輸入和輸出事件資料、 訊息屬性、 訊息內文，以及協調流程。</span><span class="sxs-lookup"><span data-stu-id="692e8-146">The tracking configuration settings enable you to track inbound and outbound event data, message properties, message bodies, and orchestrations.</span></span> <span data-ttu-id="692e8-147">[管理成品](../../core/managing-artifacts.md)包含詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="692e8-147">[Managing Artifacts](../../core/managing-artifacts.md) includes more info.</span></span> 

  
## <a name="see-also"></a><span data-ttu-id="692e8-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="692e8-148">See Also</span></span>  
[<span data-ttu-id="692e8-149">Oracle 資料庫配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="692e8-149">Troubleshoot the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)