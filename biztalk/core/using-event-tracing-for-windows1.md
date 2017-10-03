---
title: "事件追蹤用於 Windows1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW
- provider
- Receiver Logging Provider
- Transmitter Logging Provider
- controller application
- Management Logging Provider
- consumer application
- Event Tracing for Windows
- BTATIBCORVTrace command
ms.assetid: 9e0418e2-7938-4202-83b7-555a90348904
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b51ca273e63ce93ee1ce94a66d0d14a97f807767
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-event-tracing-for-windows"></a><span data-ttu-id="4bb7b-102">使用 Windows 事件追蹤</span><span class="sxs-lookup"><span data-stu-id="4bb7b-102">Using Event Tracing for Windows</span></span>
<span data-ttu-id="4bb7b-103">Microsoft BizTalk Adapter for TIBCO Rendezvous 會將錯誤、警告和資訊訊息記錄至 Windows 事件檢視器。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-103">Microsoft BizTalk Adapter for TIBCO Rendezvous logs error, warning, and information messages to the Windows Event Viewer.</span></span> <span data-ttu-id="4bb7b-104">您可以使用「Windows 事件追蹤」工具來查看其他追蹤訊息。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-104">You can see additional tracing messages by using the Event Tracing for Windows (ETW) tool.</span></span> <span data-ttu-id="4bb7b-105">啟動 ETW 時，它會建立一個 *.etl 檔案來接收訊息。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-105">When ETW is activated, it creates an *.etl file to receive the messages.</span></span> <span data-ttu-id="4bb7b-106">這個檔案是二進位格式，必須經過轉換才能讀取。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-106">This file is in binary format and must be converted to be read.</span></span> <span data-ttu-id="4bb7b-107">若要這樣做，您必須取用者應用程式可供解譯\*.etl 檔案，例如，tracerpt.exe 或 tracedmp.exe。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-107">To do this, you must have a consumer application available to interpret the \*.etl file, for example, tracerpt.exe or tracedmp.exe.</span></span> <span data-ttu-id="4bb7b-108">例如，tracerpt.exe 應用程式會將轉換\*成兩個文字檔的.etl 檔案： summary.txt 與 dumpfile.csv。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-108">For example, the tracerpt.exe application will convert the \*.etl file into two text files: summary.txt and dumpfile.csv.</span></span>  
  
## <a name="etw-components"></a><span data-ttu-id="4bb7b-109">ETW 元件</span><span class="sxs-lookup"><span data-stu-id="4bb7b-109">ETW Components</span></span>  
 <span data-ttu-id="4bb7b-110">「Windows 事件追蹤」有三個元件：</span><span class="sxs-lookup"><span data-stu-id="4bb7b-110">Event Tracing for Windows has three components:</span></span>  
  
-   <span data-ttu-id="4bb7b-111">**控制器應用程式**： 啟用和停用提供者 （例如，tracelog.exe 或 logman.exe）。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-111">**Controller application**: Activates and deactivates a provider (for example, tracelog.exe or logman.exe).</span></span>  
  
     <span data-ttu-id="4bb7b-112">您會將 PATH 環境變數設定成指向 tracelog.exe 的位置。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-112">You set your PATH environment variable to point to the location of tracelog.exe.</span></span> <span data-ttu-id="4bb7b-113">這可確保 BTATIBCO RendezvousTrace 呼叫可在系統中找出 tracelog.exe。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-113">This makes sure that BTATIBCO RendezvousTrace calls can locate tracelog.exe in the system.</span></span> <span data-ttu-id="4bb7b-114">BTATIBCO RendezvousTrace 預設會搜尋目前的路徑。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-114">By default, BTATIBCO RendezvousTrace searches the current path.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4bb7b-115">tracelog.exe 可從 Microsoft SDK 取得，而且與 Microsoft BizTalk Adapter for TIBCO Rendezvous 提供的命令相容。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-115">tracelog.exe is available from the Microsoft SDK and is compatible with the commands provided by Microsoft BizTalk Adapter for TIBCO Rendezvous.</span></span> <span data-ttu-id="4bb7b-116">如果要使用 logman.exe，請參閱 logman 文件。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-116">To use logman.exe, see the logman documentation.</span></span>  
  
-   <span data-ttu-id="4bb7b-117">**取用者應用程式**： 讀取記錄的事件。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-117">**Consumer application**: Reads logged events.</span></span>  
  
     <span data-ttu-id="4bb7b-118">為了讓消費者應用程式能夠讀取 etl 檔案中的事件，Windows 事件追蹤必須將事件傾印到該檔案中。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-118">For the consumer application to be able to read the event in the etl file, Event Tracing for Windows must dump them into that file.</span></span> <span data-ttu-id="4bb7b-119">此動作通常是在控制器停用追蹤後完成的。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-119">Typically this is done when the controller deactivates the tracing.</span></span>  
  
     <span data-ttu-id="4bb7b-120">若要使用取用者應用程式，而不停用追蹤，控制器必須啟動使用即時選項時，追蹤\<即時 > =-rt。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-120">To use the consumer application without deactivating the trace, the controller must activate the trace with the real time option, \<Real time> = -rt.</span></span>  
  
-   <span data-ttu-id="4bb7b-121">**提供者**： 提供的事件。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-121">**Provider**: Provides the event.</span></span>  
  
     <span data-ttu-id="4bb7b-122">BizTalk Adapter for TIBCO Rendezvous 包含三個不同的提供者。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-122">BizTalk Adapter for TIBCO Rendezvous includes three different providers.</span></span> <span data-ttu-id="4bb7b-123">它們是在 Windows Management Instrumentation (WMI) 中註冊的。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-123">They are registered in Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="4bb7b-124">若要在 root\WMI\EventTrace 路經中尋找已登錄的提供者，您可以使用諸如 WMI CIM Studio 這類的工具。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-124">To find the registered providers in the root\WMI\EventTrace path, you can use tools such as WMI CIM Studio.</span></span>  
  
 <span data-ttu-id="4bb7b-125">BizTalk Adapter for TIBCO Rendezvous 有三個提供者。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-125">BizTalk Adapter for TIBCO Rendezvous has three providers.</span></span> <span data-ttu-id="4bb7b-126">這可讓您記錄不同種類的訊息：</span><span class="sxs-lookup"><span data-stu-id="4bb7b-126">This lets you log different kinds of messages:</span></span>  
  
-   <span data-ttu-id="4bb7b-127">**接收器記錄提供者**:\<追蹤項目 > 參數是**-接收者**。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-127">**Receiver Logging Provider**: The \<Trace element> switch is **-receiver**.</span></span>  
  
-   <span data-ttu-id="4bb7b-128">使用**-接收者**可從已在執行階段的配接器收到的記錄檔中取得任何訊息。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-128">Use **-receiver** to get any messages from the log that were received by the adapter at runtime.</span></span>  
  
-   <span data-ttu-id="4bb7b-129">**傳輸器記錄提供者**:\<追蹤項目 > 參數是**-傳輸器**。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-129">**Transmitter Logging Provider**: the \<Trace element> switch is **-transmitter**.</span></span>  
  
     <span data-ttu-id="4bb7b-130">使用**-傳輸器**可傳輸的配接器在執行階段的記錄檔中取得任何訊息。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-130">Use **-transmitter** to get any messages from the log that were transmitted by the adapter at run time.</span></span>  
  
-   <span data-ttu-id="4bb7b-131">**管理記錄提供者 —**\<追蹤項目 > 參數是**-管理**。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-131">**Management Logging Provider—**the \<Trace element> switch is **-management**.</span></span>  
  
     <span data-ttu-id="4bb7b-132">使用**-管理**可瀏覽伺服器系統期間所產生的記錄檔中取得任何訊息。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-132">Use **-management**to get any messages from the log that were generated during browsing of the server system.</span></span>  
  
## <a name="btatibcorvtrace-command"></a><span data-ttu-id="4bb7b-133">BTATIBCORVTrace 命令</span><span class="sxs-lookup"><span data-stu-id="4bb7b-133">BTATIBCORVTrace Command</span></span>  
 <span data-ttu-id="4bb7b-134">若要使用 ETW，請執行 BizTalk Adapter for TIBCO Rendezvous 命令，BTATIBCORVTrace.cmd。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-134">To use ETW, run the BizTalk Adapter for TIBCO Rendezvous command, BTATIBCORVTrace.cmd.</span></span> <span data-ttu-id="4bb7b-135">您可以下列方式使用此命令：</span><span class="sxs-lookup"><span data-stu-id="4bb7b-135">You use this command as follows:</span></span>  
  
```  
BTATIBCORVTrace <Trace element> -start [-cir <MB>|   
-seq <MB>] [-rt] logfile  
BTATIBCORVTrace <Trace element> -stop  
```  
  
 <span data-ttu-id="4bb7b-136">位置： **\<追蹤項目 >** （必要） 是提供者的類型。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-136">Where: **\<Trace element>** (required) is the kind of provider.</span></span>  
  
 <span data-ttu-id="4bb7b-137">可用選項如下：</span><span class="sxs-lookup"><span data-stu-id="4bb7b-137">Its options are as follows:</span></span>  
  
-   <span data-ttu-id="4bb7b-138">**-傳輸器**</span><span class="sxs-lookup"><span data-stu-id="4bb7b-138">**-transmitter**</span></span>  
  
-   <span data-ttu-id="4bb7b-139">**-接收者**</span><span class="sxs-lookup"><span data-stu-id="4bb7b-139">**-receiver**</span></span>  
  
-   <span data-ttu-id="4bb7b-140">**-管理**</span><span class="sxs-lookup"><span data-stu-id="4bb7b-140">**-management**</span></span>  
  
-   <span data-ttu-id="4bb7b-141">**-開始、-停止**： 啟用或停用提供者。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-141">**-start, -stop**: Activate or deactivate the provider.</span></span>  
  
-   <span data-ttu-id="4bb7b-142">**-cir \<MB >**： 檔案的大小與種類。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-142">**-cir \<MB>**: Size and kind of file.</span></span> <span data-ttu-id="4bb7b-143">**-cir**是循環檔案。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-143">**-cir** is a circular file.</span></span> <span data-ttu-id="4bb7b-144">**\<MB >**： 以 mb 為單位的大小。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-144">**\<MB>**: Size in megabytes.</span></span>  
  
-   <span data-ttu-id="4bb7b-145">**-seq \<MB >**： 檔案的大小與種類。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-145">**-seq \<MB>**: Size and kind of file.</span></span> <span data-ttu-id="4bb7b-146">**-seq**是循序檔案。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-146">**-seq** is a sequential file.</span></span> <span data-ttu-id="4bb7b-147">**\<MB >**： 以 mb 為單位的大小。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-147">**\<MB>**: Size in megabytes.</span></span>  
  
-   <span data-ttu-id="4bb7b-148">**-rt**： 設定即時模式。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-148">**-rt**: Set the real time mode on.</span></span>  
  
-   <span data-ttu-id="4bb7b-149">**記錄檔**： 記錄檔的名稱 （c:\rtlog.etl 是預設值）。</span><span class="sxs-lookup"><span data-stu-id="4bb7b-149">**Logfile**: Name of the log file (c:\rtlog.etl is the default).</span></span>  
  
 <span data-ttu-id="4bb7b-150">例如：</span><span class="sxs-lookup"><span data-stu-id="4bb7b-150">For example:</span></span>  
  
```  
BTATIBCORVTrace -transmitter -start -cir 10 -rt c:\log\mylog.etl  
BTATIBCORVTrace -transmitter -stop  
```  
  
## <a name="see-also"></a><span data-ttu-id="4bb7b-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bb7b-151">See Also</span></span>  
 [<span data-ttu-id="4bb7b-152">對 TIBCO Rendezvous 進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="4bb7b-152">Troubleshooting TIBCO Rendezvous</span></span>](../core/troubleshooting-tibco-rendezvous.md)