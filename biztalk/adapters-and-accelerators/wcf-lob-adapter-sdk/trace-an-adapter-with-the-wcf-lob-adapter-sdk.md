---
title: 追蹤 WCF LOB Adapter SDK 的配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7a4f4758-3e3e-48c4-b4cf-414c2b05d539
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ca4b68f23f791de3ecd68bc69b85c2908b6d7a0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25965356"
---
# <a name="trace-an-adapter-with-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="c3d10-102">追蹤 WCF LOB Adapter SDK 的配接器</span><span class="sxs-lookup"><span data-stu-id="c3d10-102">Trace an adapter with the WCF LOB Adapter SDK</span></span>
[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]<span data-ttu-id="c3d10-103">追蹤是建立在 Systems.Diagnostics 之上。</span><span class="sxs-lookup"><span data-stu-id="c3d10-103"> tracing is built on top of Systems.Diagnostics.</span></span> <span data-ttu-id="c3d10-104">使用追蹤來源 Microsoft.ServiceModel.Channels[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]執行階段。</span><span class="sxs-lookup"><span data-stu-id="c3d10-104">You use Microsoft.ServiceModel.Channels trace source for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] runtime.</span></span>  <span data-ttu-id="c3d10-105">使用追蹤來源 Microsoft.ServiceModel.Channels.Tools.MetadataSearchBrowse[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]和[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c3d10-105">You use Microsoft.ServiceModel.Channels.Tools.MetadataSearchBrowse trace source for [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].</span></span> <span data-ttu-id="c3d10-106">WCF 追蹤會寫入名為 System.ServiceModel 的來源。</span><span class="sxs-lookup"><span data-stu-id="c3d10-106">WCF traces are written to the source named System.ServiceModel.</span></span>  
  
 <span data-ttu-id="c3d10-107">配接器開發人員可以提供使用 Microsoft.ServiceModel.Channels.Common.AdapterTrace 類別之配接器的追蹤來源名稱。</span><span class="sxs-lookup"><span data-stu-id="c3d10-107">The adapter developer can provide a trace source name for the adapter using Microsoft.ServiceModel.Channels.Common.AdapterTrace class.</span></span> <span data-ttu-id="c3d10-108">[!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]會產生可用於配接器開發人員所提供的配接器程式碼中的檢測追蹤包裝函式類別。</span><span class="sxs-lookup"><span data-stu-id="c3d10-108">The [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] generates a trace wrapper class that can be used by the adapter developer to provide instrumentation in the adapter code.</span></span>  
  
 <span data-ttu-id="c3d10-109">如需 WCF 追蹤資訊，請參閱[追蹤](https://msdn.microsoft.com/library/ms730342.aspx)。</span><span class="sxs-lookup"><span data-stu-id="c3d10-109">For information about WCF tracing, see [Tracing](https://msdn.microsoft.com/library/ms730342.aspx).</span></span>
  
 <span data-ttu-id="c3d10-110">如需分析 WCF 中的追蹤資訊，請參閱[服務追蹤檢視器工具 (SvcTraceViewer.exe)](https://msdn.microsoft.com/library/ms732023.aspx)。</span><span class="sxs-lookup"><span data-stu-id="c3d10-110">For information about analyzing traces in WCF, see [Service Trace Viewer Tool (SvcTraceViewer.exe)](https://msdn.microsoft.com/library/ms732023.aspx).</span></span> 
  
## <a name="sample-trace-wrapper-utility-class"></a><span data-ttu-id="c3d10-111">範例追蹤包裝函式的公用程式類別</span><span class="sxs-lookup"><span data-stu-id="c3d10-111">Sample Trace Wrapper Utility Class</span></span>  
  
```  
public class EchoAdapterUtilities  
{  
    static AdapterTrace trace = new AdapterTrace("Microsoft.Adapters.Samples.Echo.EchoAdapter");  
  
    /// <summary>  
    /// Gets the AdapterTrace  
    /// </summary>  
    public static AdapterTrace Trace  
    {  
        get  
        {  
            return trace;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="c3d10-112">然後由配接器開發人員在配接器程式碼提供檢測資料配接器取用者使用先前的公用程式類別。</span><span class="sxs-lookup"><span data-stu-id="c3d10-112">The previous utility class can then be used by the adapter developer throughout the adapter code to provide instrumentation data for the adapter consumers.</span></span>  
  
 <span data-ttu-id="c3d10-113">EchoAdapterUtilities.Trace.Trace (System.Diagnostics.TraceEventType.Information，"EchoAdapterConnection::Open 」、 「 已成功開啟連接 ！ 」);</span><span class="sxs-lookup"><span data-stu-id="c3d10-113">EchoAdapterUtilities.Trace.Trace(System.Diagnostics.TraceEventType.Information, "EchoAdapterConnection::Open", "Connection successfully opened!");</span></span>  
  
## <a name="enable-tracing-for-the-adapter-and-wcf-lob-adapter-sdk-runtime"></a><span data-ttu-id="c3d10-114">啟用配接器和 WCF LOB 配接器 SDK 執行階段的追蹤</span><span class="sxs-lookup"><span data-stu-id="c3d10-114">Enable Tracing for the Adapter and WCF LOB Adapter SDK Runtime</span></span>  
 <span data-ttu-id="c3d10-115">您可以啟用追蹤中所提供[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]藉由使用配接器的應用程式的 app.config 檔案中新增下一節。</span><span class="sxs-lookup"><span data-stu-id="c3d10-115">You can enable tracing provided in the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] by adding the following section in the app.config file of the application using the adapter.</span></span>  
  
```  
<system.diagnostics>  
  <sources>  
    <source name="Microsoft.Adapters.Samples.Echo.EchoAdapter" switchValue="Verbose">  
      <listeners>  
        <add name="xmlTrace" />  
      </listeners>  
    </source>  
    <source name="Microsoft.ServiceModel.Channels" switchValue="Verbose">  
      <listeners>  
        <add name="xmlTrace" />  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add initializeData="C:\logs\TestEchoAdapter_Browse.svclog" type="System.Diagnostics.XmlWriterTraceListener" name="xmlTrace">  
      <filter type="" />  
    </add>  
  </sharedListeners>  
  <trace autoflush="true" />  
</system.diagnostics>  
```  
  
 <span data-ttu-id="c3d10-116">您可以使用 新增項目，指定您想要使用的追蹤接聽項的類型與名稱。</span><span class="sxs-lookup"><span data-stu-id="c3d10-116">You can use the add element to specify the name and type of the trace listener you want to use.</span></span> <span data-ttu-id="c3d10-117">在範例組態中，我們將名為接聽程式 」 xmlTrace 」，我們想要使用的類型加入標準的.NET Framework 追蹤接聽項 (System.Diagnostics.XmlWriterTraceListener)。</span><span class="sxs-lookup"><span data-stu-id="c3d10-117">In our example configuration, we named the Listener "xmlTrace" and added the standard .NET Framework trace listener (System.Diagnostics.XmlWriterTraceListener) as the type we want to use.</span></span> <span data-ttu-id="c3d10-118">您可以加入任意數目的每個來源的追蹤接聽項。</span><span class="sxs-lookup"><span data-stu-id="c3d10-118">You can add any number of trace listeners for each source.</span></span> <span data-ttu-id="c3d10-119">例如，在下列範例中，我們也加入另一個名為"textTrace 」 使用.NET Framework 追蹤接聽項 System.Diagnostics.TextWriterTraceListener 的接聽程式。</span><span class="sxs-lookup"><span data-stu-id="c3d10-119">For example, in the following examples, we also added another listener named "textTrace" that uses the .NET Framework trace listener System.Diagnostics.TextWriterTraceListener.</span></span> <span data-ttu-id="c3d10-120">如果追蹤接聽項將追蹤發出到檔案，您必須在組態檔中指定的輸出檔案位置和名稱。</span><span class="sxs-lookup"><span data-stu-id="c3d10-120">If the trace listener emits the trace to a file, you must specify the output file location and name in the configuration file.</span></span> <span data-ttu-id="c3d10-121">這是設為 initializeData 檔案的名稱，該接聽項。</span><span class="sxs-lookup"><span data-stu-id="c3d10-121">This is done by setting initializeData to the name of the file for that listener.</span></span>  
  
## <a name="enabling-tracing-for-the-add-adapter-service-reference-plug-in"></a><span data-ttu-id="c3d10-122">啟用追蹤新增配接器服務參考外掛程式</span><span class="sxs-lookup"><span data-stu-id="c3d10-122">Enabling Tracing for the Add Adapter Service Reference Plug-in</span></span>  
 <span data-ttu-id="c3d10-123">您可以啟用追蹤，在此外掛程式的 devenv.exe.config 檔案中加入下一節位於`\Program Files (x86)\Microsoft Visual Studio\Common7\IDE`。</span><span class="sxs-lookup"><span data-stu-id="c3d10-123">You can enable tracing for this plug-in by adding the following section in the devenv.exe.config file located in `\Program Files (x86)\Microsoft Visual Studio\Common7\IDE`.</span></span>
  
```  
<system.diagnostics>  
   <sources>  
    <source name="Microsoft.ServiceModel.Channels.Tools.MetadataSearchBrowse" switchValue="Verbose, ActivityTracing">  
      <listeners>  
        <add name="textTrace"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add initializeData="C:\logs\aasr.svclog" type="System.Diagnostics.XmlWriterTraceListener" name="xmlTrace">  
      <filter type="" />  
    </add>  
    <add initializeData="C:\logs\aasr.log" type="System.Diagnostics.TextWriterTraceListener" name="textTrace">  
      <filter type="" />  
    </add>  
  </sharedListeners>  
  <trace autoflush="true" indentsize="4" />  
</system.diagnostics>  
```  
  
## <a name="enable-tracing-for-the-consume-adapter-service-add-in"></a><span data-ttu-id="c3d10-124">啟用追蹤功能使用配接器服務增益集</span><span class="sxs-lookup"><span data-stu-id="c3d10-124">Enable Tracing for the Consume Adapter Service Add-in</span></span>  
 <span data-ttu-id="c3d10-125">您可以啟用追蹤這個增益集在 BTSNTSVC.exe.config 檔案中加入下列區段`\Program Files (x86)\Microsoft BizTalk Server`。</span><span class="sxs-lookup"><span data-stu-id="c3d10-125">You can enable tracing for this add-in by adding the following section in the BTSNTSVC.exe.config file located in `\Program Files (x86)\Microsoft BizTalk Server`.</span></span>  
  
```  
<system.diagnostics>  
   <sources>  
    <source name="Microsoft.ServiceModel.Channels.Tools.MetadataSearchBrowse" switchValue="Verbose, ActivityTracing">  
      <listeners>  
        <add name="textTrace"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add initializeData="C:\logs\aasr.svclog" type="System.Diagnostics.XmlWriterTraceListener" name="xmlTrace">  
      <filter type="" />  
    </add>  
    <add initializeData="C:\logs\aasr.log" type="System.Diagnostics.TextWriterTraceListener" name="textTrace">  
      <filter type="" />  
    </add>  
  </sharedListeners>  
  <trace autoflush="true" indentsize="4" />  
</system.diagnostics>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3d10-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="c3d10-126">See Also</span></span>  
 [<span data-ttu-id="c3d10-127">使用 WCF LOB 配接器 SDK 所建立的配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="c3d10-127">Troubleshoot adapter created using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/troubleshoot-adapter-created-using-the-wcf-lob-adapter-sdk.md)