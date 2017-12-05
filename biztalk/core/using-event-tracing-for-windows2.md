---
title: "事件追蹤用於 Windows2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW
- Event Tracing for Windows
ms.assetid: 88b91b74-2b2e-40e0-a3e9-1ebd6367abe8
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c5f610d75048b250fc90aba7f723cee39c4f2e1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="using-event-tracing-for-windows"></a><span data-ttu-id="d3c73-102">使用 Windows 事件追蹤</span><span class="sxs-lookup"><span data-stu-id="d3c73-102">Using Event Tracing for Windows</span></span>
<span data-ttu-id="d3c73-103">Microsoft BizTalk Adapter for JD Edwards OneWorld 會將錯誤、警告和資訊訊息記錄至 Windows 事件檢視器。</span><span class="sxs-lookup"><span data-stu-id="d3c73-103">Microsoft BizTalk Adapter for JD Edwards OneWorld logs error, warning, and information messages to the Windows Event Viewer.</span></span> <span data-ttu-id="d3c73-104">您可以使用 Windows 事件追蹤 (ETW) 工具來檢視其他追蹤訊息。</span><span class="sxs-lookup"><span data-stu-id="d3c73-104">You can view additional tracing messages by using the Event Tracing for Windows (ETW) tool.</span></span> <span data-ttu-id="d3c73-105">啟動 ETW 時，它會建立一個 *.etl 檔案來接收訊息。</span><span class="sxs-lookup"><span data-stu-id="d3c73-105">When ETW is activated, it creates an *.etl file to receive the messages.</span></span> <span data-ttu-id="d3c73-106">這個檔案是二進位格式，必須經過轉換才能讀取。</span><span class="sxs-lookup"><span data-stu-id="d3c73-106">This file is in binary format and must be converted to be read.</span></span> <span data-ttu-id="d3c73-107">若要這樣做，您必須取用者應用程式可供解譯\*.etl 檔案： 例如，tracerpt.exe 或 tracedmp.exe。</span><span class="sxs-lookup"><span data-stu-id="d3c73-107">To do this, you must have a consumer application available to interpret the \*.etl file: for example, tracerpt.exe or tracedmp.exe.</span></span>  
  
## <a name="etw-components"></a><span data-ttu-id="d3c73-108">ETW 元件</span><span class="sxs-lookup"><span data-stu-id="d3c73-108">ETW Components</span></span>  
 <span data-ttu-id="d3c73-109">「Windows 事件追蹤」有三個元件：</span><span class="sxs-lookup"><span data-stu-id="d3c73-109">Event Tracing for Windows has three components:</span></span>  
  
-   <span data-ttu-id="d3c73-110">**控制器應用程式。**</span><span class="sxs-lookup"><span data-stu-id="d3c73-110">**Controller application.**</span></span> <span data-ttu-id="d3c73-111">啟用與停用提供者 (例如，tracelog.exe 或 logman.exe)。</span><span class="sxs-lookup"><span data-stu-id="d3c73-111">Activates and deactivates a provider (for example, tracelog.exe or logman.exe).</span></span>  
  
     <span data-ttu-id="d3c73-112">您會將 PATH 環境變數設定成指向 tracelog.exe 的位置。</span><span class="sxs-lookup"><span data-stu-id="d3c73-112">You set your PATH environment variable to point to the location of tracelog.exe.</span></span> <span data-ttu-id="d3c73-113">這可確保 BTAJDEdwardsOneWorldTrace 呼叫可在您的系統中找出 tracelog.exe。</span><span class="sxs-lookup"><span data-stu-id="d3c73-113">This ensures that BTAJDEdwardsOneWorldTrace calls can locate tracelog.exe in your system.</span></span> <span data-ttu-id="d3c73-114">BTAJDEdwardsOneWorldTrace 預設會搜尋目前的路徑。</span><span class="sxs-lookup"><span data-stu-id="d3c73-114">By default, BTAJDEdwardsOneWorldTrace searches the current path.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d3c73-115">tracelog.exe 可從 Microsoft SDK 取得，而且與 BizTalk Adapter for JD Edwards OneWorld 提供的命令相容。</span><span class="sxs-lookup"><span data-stu-id="d3c73-115">tracelog.exe is available from the Microsoft SDK and is compatible with the commands provided by BizTalk Adapter for JD Edwards OneWorld.</span></span> <span data-ttu-id="d3c73-116">若要使用 logman.exe，請參閱 logman 文件。</span><span class="sxs-lookup"><span data-stu-id="d3c73-116">To use logman.exe refer to the logman documentation.</span></span>  
  
-   <span data-ttu-id="d3c73-117">**取用者應用程式。**</span><span class="sxs-lookup"><span data-stu-id="d3c73-117">**Consumer application.**</span></span> <span data-ttu-id="d3c73-118">讀取記錄的事件。</span><span class="sxs-lookup"><span data-stu-id="d3c73-118">Reads logged events.</span></span>  
  
     <span data-ttu-id="d3c73-119">如果要讓取用者應用程式可讀取 .etl 檔案中的事件，「Windows 事件追蹤」必須將它們傾印到該檔案。</span><span class="sxs-lookup"><span data-stu-id="d3c73-119">For the consumer application to be able to read the event in the .etl file, Event Tracing for Windows must dump them into that file.</span></span> <span data-ttu-id="d3c73-120">通常這是在控制器停用追蹤時完成。</span><span class="sxs-lookup"><span data-stu-id="d3c73-120">Normally this is done when the controller deactivates the tracing.</span></span>  
  
     <span data-ttu-id="d3c73-121">若要使用取用者應用程式，而不停用追蹤，控制器必須啟動使用即時選項時，追蹤**\<即時\>=-rt**。</span><span class="sxs-lookup"><span data-stu-id="d3c73-121">To use the consumer application without deactivating the trace, the controller must activate the trace with the real-time option, **\<Real time\> = -rt**.</span></span>  
  
-   <span data-ttu-id="d3c73-122">**提供者。**</span><span class="sxs-lookup"><span data-stu-id="d3c73-122">**Provider.**</span></span> <span data-ttu-id="d3c73-123">提供事件。</span><span class="sxs-lookup"><span data-stu-id="d3c73-123">Provides the event.</span></span>  
  
 <span data-ttu-id="d3c73-124">BizTalk Adapter for JD Edwards OneWorld 包含五個不同的提供者。</span><span class="sxs-lookup"><span data-stu-id="d3c73-124">BizTalk Adapter for JD Edwards OneWorld includes five different providers.</span></span> <span data-ttu-id="d3c73-125">它們是在 Windows Management Instrumentation (WMI) 中註冊的。</span><span class="sxs-lookup"><span data-stu-id="d3c73-125">They are registered in Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="d3c73-126">若要在 root\WMI\EventTrace 路經中尋找已登錄的提供者，您可以使用諸如 WMI CIM Studio 這類的工具。</span><span class="sxs-lookup"><span data-stu-id="d3c73-126">To find the registered providers in the root\WMI\EventTrace path, you can use tools such as WMI CIM Studio.</span></span>  
  
 <span data-ttu-id="d3c73-127">BizTalk Adapter for JD Edwards OneWorld 有五個提供者，可讓您記錄不同種類的訊息：</span><span class="sxs-lookup"><span data-stu-id="d3c73-127">BizTalk Adapter for JD Edwards OneWorld has five providers, allowing you to log different kinds of messages:</span></span>  
  
-   <span data-ttu-id="d3c73-128">**接收器記錄提供者。**</span><span class="sxs-lookup"><span data-stu-id="d3c73-128">**Receiver Logging Provider.**</span></span> <span data-ttu-id="d3c73-129">\<追蹤項目\>交換器**-接收者**。</span><span class="sxs-lookup"><span data-stu-id="d3c73-129">The \<Trace element\> switch is **-receiver**.</span></span>  
  
-   <span data-ttu-id="d3c73-130">**接收器 Castdetail 提供者。**</span><span class="sxs-lookup"><span data-stu-id="d3c73-130">**Receiver CastDetails Provider.**</span></span> <span data-ttu-id="d3c73-131">\<追蹤項目\>交換器**-castDetailsReceive**。</span><span class="sxs-lookup"><span data-stu-id="d3c73-131">The \<Trace element\> switch is **-castDetailsReceive**.</span></span>  
  
-   <span data-ttu-id="d3c73-132">**傳輸器記錄提供者。**</span><span class="sxs-lookup"><span data-stu-id="d3c73-132">**Transmitter Logging Provider.**</span></span> <span data-ttu-id="d3c73-133">\<追蹤項目\>交換器**-傳輸器**。</span><span class="sxs-lookup"><span data-stu-id="d3c73-133">The \<Trace element\> switch is **-transmitter**.</span></span>  
  
-   <span data-ttu-id="d3c73-134">**傳輸器 CastDetails 提供者。**</span><span class="sxs-lookup"><span data-stu-id="d3c73-134">**Transmitter CastDetails Provider.**</span></span> <span data-ttu-id="d3c73-135">\<追蹤項目\>交換器**-castDetailsTransmit**。</span><span class="sxs-lookup"><span data-stu-id="d3c73-135">The \<Trace element\> switch is **-castDetailsTransmit**.</span></span>  
  
-   <span data-ttu-id="d3c73-136">**管理記錄提供者。**</span><span class="sxs-lookup"><span data-stu-id="d3c73-136">**Management Logging Provider.**</span></span> <span data-ttu-id="d3c73-137">\<追蹤項目\>交換器**-管理**。</span><span class="sxs-lookup"><span data-stu-id="d3c73-137">The \<Trace element\> switch is **-management**.</span></span>  
  
 <span data-ttu-id="d3c73-138">BTAJDEOneWorldTrace 命令</span><span class="sxs-lookup"><span data-stu-id="d3c73-138">BTAJDEOneWorldTrace Command</span></span>  
  
 <span data-ttu-id="d3c73-139">若要使用 ETW，請執行 BizTalk Adapter for JD Edwards OneWorld 命令，BTAJDEOneWorldTrace.cmd。</span><span class="sxs-lookup"><span data-stu-id="d3c73-139">To use ETW, run the BizTalk Adapter for JD Edwards OneWorld command, BTAJDEOneWorldTrace.cmd.</span></span> <span data-ttu-id="d3c73-140">您可以下列方式使用此命令：</span><span class="sxs-lookup"><span data-stu-id="d3c73-140">You use this command as follows:</span></span>  
  
```  
BTAJDEOneWorldTrace <Trace element> -start [-cir <MB>|   
      -seq <MB>] [-rt] logfile  
BTAJDEOneWorldTrace <Trace element> -stop  
```  
  
 <span data-ttu-id="d3c73-141">其中：</span><span class="sxs-lookup"><span data-stu-id="d3c73-141">Where:</span></span>  
  
-   <span data-ttu-id="d3c73-142">**\<追蹤項目\>** （必要） 是提供者的類型。</span><span class="sxs-lookup"><span data-stu-id="d3c73-142">**\<Trace element\>** (required) is the kind of provider.</span></span>  
  
-   <span data-ttu-id="d3c73-143">可用選項包括：</span><span class="sxs-lookup"><span data-stu-id="d3c73-143">Its options are:</span></span>  
  
    -   <span data-ttu-id="d3c73-144">**-castDetailsTransmit**</span><span class="sxs-lookup"><span data-stu-id="d3c73-144">**-castDetailsTransmit**</span></span>  
  
    -   <span data-ttu-id="d3c73-145">**-傳輸器**</span><span class="sxs-lookup"><span data-stu-id="d3c73-145">**-transmitter**</span></span>  
  
    -   <span data-ttu-id="d3c73-146">**-castDetailsReceive**</span><span class="sxs-lookup"><span data-stu-id="d3c73-146">**-castDetailsReceive**</span></span>  
  
    -   <span data-ttu-id="d3c73-147">**-接收者**</span><span class="sxs-lookup"><span data-stu-id="d3c73-147">**-receiver**</span></span>  
  
    -   <span data-ttu-id="d3c73-148">**-管理**</span><span class="sxs-lookup"><span data-stu-id="d3c73-148">**-management**</span></span>  
  
    -   <span data-ttu-id="d3c73-149">**-開始、-停止**： 啟用或停用提供者。</span><span class="sxs-lookup"><span data-stu-id="d3c73-149">**-start, -stop**: Activate or deactivate the provider.</span></span>  
  
    -   <span data-ttu-id="d3c73-150">**-cir \<MB\>**： 檔案的大小與種類。</span><span class="sxs-lookup"><span data-stu-id="d3c73-150">**-cir \<MB\>**: Size and kind of file.</span></span> <span data-ttu-id="d3c73-151">-cir 是循環檔案。</span><span class="sxs-lookup"><span data-stu-id="d3c73-151">-cir is a circular file.</span></span> <span data-ttu-id="d3c73-152">\<MB\>： 大小以 mb 表示。</span><span class="sxs-lookup"><span data-stu-id="d3c73-152">\<MB\>: Size in meg.</span></span>  
  
    -   <span data-ttu-id="d3c73-153">**-seq \<MB\>**： 檔案的大小與種類。</span><span class="sxs-lookup"><span data-stu-id="d3c73-153">**-seq \<MB\>**: Size and kind of file.</span></span> <span data-ttu-id="d3c73-154">-seq 是循序檔案。</span><span class="sxs-lookup"><span data-stu-id="d3c73-154">-seq is a sequential file.</span></span> <span data-ttu-id="d3c73-155">\<MB\>： 大小以 mb 表示。</span><span class="sxs-lookup"><span data-stu-id="d3c73-155">\<MB\>: Size in meg.</span></span>  
  
    -   <span data-ttu-id="d3c73-156">**-rt**： 設定即時模式。</span><span class="sxs-lookup"><span data-stu-id="d3c73-156">**-rt**: Set the real time mode on.</span></span>  
  
    -   <span data-ttu-id="d3c73-157">**記錄檔**： 記錄檔的名稱 （c:\rtlog.etl 是預設值）。</span><span class="sxs-lookup"><span data-stu-id="d3c73-157">**Logfile**: Name of the log file (c:\rtlog.etl is the default).</span></span>  
  
 <span data-ttu-id="d3c73-158">例如：</span><span class="sxs-lookup"><span data-stu-id="d3c73-158">For example:</span></span>  
  
```  
BTAJDEOneWorldTrace -transmitter -start -cir 10 -rt c:\log\mylog.etl  
BTAJDEOneWorldTrace -transmitter -stop  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3c73-159">請參閱</span><span class="sxs-lookup"><span data-stu-id="d3c73-159">See Also</span></span>  
 [<span data-ttu-id="d3c73-160">疑難排解 JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="d3c73-160">Troubleshooting JD Edwards OneWorld</span></span>](../core/troubleshooting-jd-edwards-oneworld.md)