---
title: 針對 TIBCO Rendezvous 進行疑難排解 |Microsoft Docs
description: 使用 Windows 事件追蹤至 troubl = esdhoot Microsoft BizTalk Adapter for TIBCO Rendezvous 的 BizTalk Server
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5b7bc3ab-16fa-4e91-8730-9431473b2fb4
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ccbf7efb3d61f35c1fb54eb709471f0913314ea7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977882"
---
# <a name="troubleshoot-tibco-rendezvous"></a><span data-ttu-id="1bd3c-103">針對 TIBCO Rendezvous 進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="1bd3c-103">Troubleshoot TIBCO Rendezvous</span></span>
  
## <a name="use-event-tracing-for-windows"></a><span data-ttu-id="1bd3c-104">使用 Windows 事件追蹤</span><span class="sxs-lookup"><span data-stu-id="1bd3c-104">Use Event Tracing for Windows</span></span>
<span data-ttu-id="1bd3c-105">Microsoft BizTalk Adapter for TIBCO Rendezvous 會將錯誤、警告和資訊訊息記錄至 Windows 事件檢視器。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-105">Microsoft BizTalk Adapter for TIBCO Rendezvous logs error, warning, and information messages to the Windows Event Viewer.</span></span> <span data-ttu-id="1bd3c-106">您可以使用「Windows 事件追蹤」工具來查看其他追蹤訊息。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-106">You can see additional tracing messages by using the Event Tracing for Windows (ETW) tool.</span></span> <span data-ttu-id="1bd3c-107">啟動 ETW 時，它會建立一個 \*.etl 檔案來接收訊息。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-107">When ETW is activated, it creates an \*.etl file to receive the messages.</span></span> <span data-ttu-id="1bd3c-108">這個檔案是二進位格式，必須經過轉換才能讀取。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-108">This file is in binary format and must be converted to be read.</span></span> <span data-ttu-id="1bd3c-109">若要這樣做，您必須取用者應用程式可供解譯\*.etl 檔案，例如，tracerpt.exe 或 tracedmp.exe。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-109">To do this, you must have a consumer application available to interpret the \*.etl file, for example, tracerpt.exe or tracedmp.exe.</span></span> <span data-ttu-id="1bd3c-110">例如，tracerpt.exe 應用程式會將轉換\*成兩個文字檔的.etl 檔案： summary.txt 與 dumpfile.csv。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-110">For example, the tracerpt.exe application will convert the \*.etl file into two text files: summary.txt and dumpfile.csv.</span></span>  
  
## <a name="etw-components"></a><span data-ttu-id="1bd3c-111">ETW 元件</span><span class="sxs-lookup"><span data-stu-id="1bd3c-111">ETW Components</span></span>  
 <span data-ttu-id="1bd3c-112">「Windows 事件追蹤」有三個元件：</span><span class="sxs-lookup"><span data-stu-id="1bd3c-112">Event Tracing for Windows has three components:</span></span>  
  
-   <span data-ttu-id="1bd3c-113">**控制器應用程式**： 啟用和停用提供者 （例如，tracelog.exe 或 logman.exe）。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-113">**Controller application**: Activates and deactivates a provider (for example, tracelog.exe or logman.exe).</span></span>  
  
     <span data-ttu-id="1bd3c-114">您會將 PATH 環境變數設定成指向 tracelog.exe 的位置。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-114">You set your PATH environment variable to point to the location of tracelog.exe.</span></span> <span data-ttu-id="1bd3c-115">這可確保 BTATIBCO RendezvousTrace 呼叫可在系統中找出 tracelog.exe。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-115">This makes sure that BTATIBCO RendezvousTrace calls can locate tracelog.exe in the system.</span></span> <span data-ttu-id="1bd3c-116">BTATIBCO RendezvousTrace 預設會搜尋目前的路徑。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-116">By default, BTATIBCO RendezvousTrace searches the current path.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1bd3c-117">tracelog.exe 可從 Microsoft SDK 取得，而且與 Microsoft BizTalk Adapter for TIBCO Rendezvous 提供的命令相容。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-117">tracelog.exe is available from the Microsoft SDK and is compatible with the commands provided by Microsoft BizTalk Adapter for TIBCO Rendezvous.</span></span> <span data-ttu-id="1bd3c-118">如果要使用 logman.exe，請參閱 logman 文件。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-118">To use logman.exe, see the logman documentation.</span></span>  
  
- <span data-ttu-id="1bd3c-119">**取用者應用程式**： 讀取記錄的事件。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-119">**Consumer application**: Reads logged events.</span></span>  
  
   <span data-ttu-id="1bd3c-120">為了讓消費者應用程式能夠讀取 etl 檔案中的事件，Windows 事件追蹤必須將事件傾印到該檔案中。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-120">For the consumer application to be able to read the event in the etl file, Event Tracing for Windows must dump them into that file.</span></span> <span data-ttu-id="1bd3c-121">此動作通常是在控制器停用追蹤後完成的。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-121">Typically this is done when the controller deactivates the tracing.</span></span>  
  
   <span data-ttu-id="1bd3c-122">若要使用的取用者應用程式，而不需要停用追蹤，控制器必須啟用使用即時選項時，追蹤\<即時\>=-rt。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-122">To use the consumer application without deactivating the trace, the controller must activate the trace with the real time option, \<Real time\> = -rt.</span></span>  
  
- <span data-ttu-id="1bd3c-123">**提供者**： 提供事件。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-123">**Provider**: Provides the event.</span></span>  
  
   <span data-ttu-id="1bd3c-124">BizTalk Adapter for TIBCO Rendezvous 包含三個不同的提供者。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-124">BizTalk Adapter for TIBCO Rendezvous includes three different providers.</span></span> <span data-ttu-id="1bd3c-125">它們是在 Windows Management Instrumentation (WMI) 中註冊的。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-125">They are registered in Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="1bd3c-126">若要在 root\WMI\EventTrace 路經中尋找已登錄的提供者，您可以使用諸如 WMI CIM Studio 這類的工具。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-126">To find the registered providers in the root\WMI\EventTrace path, you can use tools such as WMI CIM Studio.</span></span>  
  
  <span data-ttu-id="1bd3c-127">BizTalk Adapter for TIBCO Rendezvous 有三個提供者。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-127">BizTalk Adapter for TIBCO Rendezvous has three providers.</span></span> <span data-ttu-id="1bd3c-128">這可讓您記錄不同種類的訊息：</span><span class="sxs-lookup"><span data-stu-id="1bd3c-128">This lets you log different kinds of messages:</span></span>  
  
- <span data-ttu-id="1bd3c-129">**接收器記錄提供者**:\<追蹤項目\>交換器 **-接收者**。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-129">**Receiver Logging Provider**: The \<Trace element\> switch is **-receiver**.</span></span>  
  
- <span data-ttu-id="1bd3c-130">使用 **-接收者**可從接收配接器在執行階段記錄中取得任何訊息。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-130">Use **-receiver** to get any messages from the log that were received by the adapter at runtime.</span></span>  
  
- <span data-ttu-id="1bd3c-131">**傳輸器記錄提供者**:\<追蹤項目\>交換器 **-傳輸器**。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-131">**Transmitter Logging Provider**: the \<Trace element\> switch is **-transmitter**.</span></span>  
  
   <span data-ttu-id="1bd3c-132">使用 **-傳輸器**從傳輸配接器在執行階段記錄中取得任何訊息。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-132">Use **-transmitter** to get any messages from the log that were transmitted by the adapter at run time.</span></span>  
  
- <span data-ttu-id="1bd3c-133"><strong>管理記錄提供者 —</strong>\<追蹤項目\>交換器 **-管理**。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-133"><strong>Management Logging Provider—</strong>the \<Trace element\> switch is **-management**.</span></span>  
  
   <span data-ttu-id="1bd3c-134">使用 **-管理**可從瀏覽伺服器系統期間所產生的記錄檔中取得任何訊息。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-134">Use **-management**to get any messages from the log that were generated during browsing of the server system.</span></span>  
  
## <a name="btatibcorvtrace-command"></a><span data-ttu-id="1bd3c-135">BTATIBCORVTrace 命令</span><span class="sxs-lookup"><span data-stu-id="1bd3c-135">BTATIBCORVTrace Command</span></span>  
 <span data-ttu-id="1bd3c-136">若要使用 ETW，請執行 BizTalk Adapter for TIBCO Rendezvous 命令，BTATIBCORVTrace.cmd。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-136">To use ETW, run the BizTalk Adapter for TIBCO Rendezvous command, BTATIBCORVTrace.cmd.</span></span> <span data-ttu-id="1bd3c-137">您可以下列方式使用此命令：</span><span class="sxs-lookup"><span data-stu-id="1bd3c-137">You use this command as follows:</span></span>  
  
```  
BTATIBCORVTrace <Trace element> -start [-cir <MB>|   
-seq <MB>] [-rt] logfile  
BTATIBCORVTrace <Trace element> -stop  
```  
  
 <span data-ttu-id="1bd3c-138">位置： **\<追蹤項目\>** （必要） 是一種提供者。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-138">Where: **\<Trace element\>** (required) is the kind of provider.</span></span>  
  
 <span data-ttu-id="1bd3c-139">可用選項如下：</span><span class="sxs-lookup"><span data-stu-id="1bd3c-139">Its options are as follows:</span></span>  
  
- <span data-ttu-id="1bd3c-140">**-傳輸器**</span><span class="sxs-lookup"><span data-stu-id="1bd3c-140">**-transmitter**</span></span>  
  
- <span data-ttu-id="1bd3c-141">**-接收者**</span><span class="sxs-lookup"><span data-stu-id="1bd3c-141">**-receiver**</span></span>  
  
- <span data-ttu-id="1bd3c-142">**-管理**</span><span class="sxs-lookup"><span data-stu-id="1bd3c-142">**-management**</span></span>  
  
- <span data-ttu-id="1bd3c-143">**-啟動、-停止**： 啟用或停用提供者。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-143">**-start, -stop**: Activate or deactivate the provider.</span></span>  
  
- <span data-ttu-id="1bd3c-144">**-cir \<MB\>**： 檔案的大小與種類。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-144">**-cir \<MB\>**: Size and kind of file.</span></span> <span data-ttu-id="1bd3c-145">**-cir**是循環檔案。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-145">**-cir** is a circular file.</span></span> <span data-ttu-id="1bd3c-146">**\<MB\>**： 以 mb 為單位的大小。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-146">**\<MB\>**: Size in megabytes.</span></span>  
  
- <span data-ttu-id="1bd3c-147">**-seq \<MB\>**： 檔案的大小與種類。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-147">**-seq \<MB\>**: Size and kind of file.</span></span> <span data-ttu-id="1bd3c-148">**-seq**是循序檔案。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-148">**-seq** is a sequential file.</span></span> <span data-ttu-id="1bd3c-149">**\<MB\>**： 以 mb 為單位的大小。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-149">**\<MB\>**: Size in megabytes.</span></span>  
  
- <span data-ttu-id="1bd3c-150">**-rt**： 上設定的即時模式。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-150">**-rt**: Set the real time mode on.</span></span>  
  
- <span data-ttu-id="1bd3c-151">**Logfile**： 記錄檔的名稱 （c:\rtlog.etl 是預設值）。</span><span class="sxs-lookup"><span data-stu-id="1bd3c-151">**Logfile**: Name of the log file (c:\rtlog.etl is the default).</span></span>  
  
  <span data-ttu-id="1bd3c-152">例如：</span><span class="sxs-lookup"><span data-stu-id="1bd3c-152">For example:</span></span>  
  
```  
BTATIBCORVTrace -transmitter -start -cir 10 -rt c:\log\mylog.etl  
BTATIBCORVTrace -transmitter -stop  
```  
## <a name="see-more"></a><span data-ttu-id="1bd3c-153">查看更多</span><span class="sxs-lookup"><span data-stu-id="1bd3c-153">See more</span></span>
[<span data-ttu-id="1bd3c-154">處理例外狀況</span><span class="sxs-lookup"><span data-stu-id="1bd3c-154">Handle exceptions</span></span>](../core/using-biztalk-server-exception-handling4.md)  
[<span data-ttu-id="1bd3c-155">Security</span><span class="sxs-lookup"><span data-stu-id="1bd3c-155">Security</span></span>](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md)  
[<span data-ttu-id="1bd3c-156">架構</span><span class="sxs-lookup"><span data-stu-id="1bd3c-156">Architecture</span></span>](../core/architecture-of-biztalk-adapter-for-tibco-rendezvous.md)