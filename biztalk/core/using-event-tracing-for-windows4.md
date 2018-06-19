---
title: 事件追蹤用於 Windows4 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ETW
- BTAJDEEnterpriseOneTrace command
- Event Tracing for Windows
ms.assetid: 5f07d317-5ae2-4d1e-a343-941f3079dc4b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e98340654df792b8ec58014d4804394b5a6c6099
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "25973676"
---
# <a name="using-event-tracing-for-windows"></a><span data-ttu-id="0fd8f-102">使用 Windows 事件追蹤</span><span class="sxs-lookup"><span data-stu-id="0fd8f-102">Using Event Tracing for Windows</span></span>
<span data-ttu-id="0fd8f-103">Microsoft BizTalk Adapter for JD Edwards EnterpriseOne 會將錯誤、警告與資訊訊息記錄到 Windows 事件檢視器中。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-103">Microsoft BizTalk Adapter for JD Edwards EnterpriseOne logs error, warning, and information messages to the Windows Event Viewer.</span></span> <span data-ttu-id="0fd8f-104">您可以使用 Windows 事件追蹤 (ETW) 工具來檢視其他追蹤訊息。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-104">You can view additional tracing messages by using the Event Tracing for Windows (ETW) tool.</span></span> <span data-ttu-id="0fd8f-105">啟動 ETW 時，它會建立一個 \*.etl 檔案來接收訊息。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-105">When ETW is activated, it creates an \*.etl file to receive the messages.</span></span> <span data-ttu-id="0fd8f-106">這個檔案是二進位格式，必須經過轉換才能讀取。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-106">This file is in binary format and must be converted to be read.</span></span> <span data-ttu-id="0fd8f-107">若要這樣做，您必須取用者應用程式可供解譯 \*.etl 檔案; 例如，tracerpt.exe 或 tracedmp.ex。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-107">To do this, you must have a consumer application available to interpret the \*.etl file; for example, tracerpt.exe or tracedmp.ex.</span></span> <span data-ttu-id="0fd8f-108">Tracept.exe 應用程式將轉換 \*.etl 成兩個文字檔︰ summary.txt 與 dumpfile.csv。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-108">The tracept.exe application converts the \*.etl into two text files: summary.txt and dumpfile.csv.</span></span>  
  
## <a name="etw-components"></a><span data-ttu-id="0fd8f-109">ETW 元件</span><span class="sxs-lookup"><span data-stu-id="0fd8f-109">ETW Components</span></span>  
 <span data-ttu-id="0fd8f-110">「Windows 事件追蹤」有三個元件：</span><span class="sxs-lookup"><span data-stu-id="0fd8f-110">Event Tracing for Windows has three components:</span></span>  
  
-   <span data-ttu-id="0fd8f-111">**控制器應用程式**。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-111">**Controller application**.</span></span> <span data-ttu-id="0fd8f-112">啟用與停用提供者 (例如，tracelog.exe 或 logman.exe)。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-112">Activates and deactivates a provider (for example, tracelog.exe or logman.exe).</span></span>  
  
     <span data-ttu-id="0fd8f-113">您會將 PATH 環境變數設定成指向 tracelog.exe 的位置。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-113">You set your PATH environment variable to point to the location of tracelog.exe.</span></span> <span data-ttu-id="0fd8f-114">這可確保 BTAJDEEnterpriseOneTrace 呼叫，可在系統中找到 tracelog.exe。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-114">This ensures that BTAJDEEnterpriseOneTrace calls can locate tracelog.exe in your system.</span></span> <span data-ttu-id="0fd8f-115">依照預設，BTAJDEEnterpriseOneTrace 會搜尋目前的路徑。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-115">By default, BTAJDEEnterpriseOneTrace searches the current path.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0fd8f-116">tracelog.exe 可以從 Microsoft SDK 取得，且和 BizTalk Adapter  for JD Edwards EnterpriseOne 提供的命令相容。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-116">tracelog.exe is available from the Microsoft SDK and is compatible with the commands provided by  BizTalk Adapter  for JD Edwards EnterpriseOne.</span></span> <span data-ttu-id="0fd8f-117">如果要使用 logman.exe，請參閱 logman 文件。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-117">To use logman.exe, refer to the logman documentation.</span></span>  
  
-   <span data-ttu-id="0fd8f-118">**取用者應用程式**。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-118">**Consumer application**.</span></span> <span data-ttu-id="0fd8f-119">讀取記錄的事件。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-119">Reads logged events.</span></span> <span data-ttu-id="0fd8f-120">為了讓消費者應用程式能夠讀取 etl 檔案中的事件，Windows 事件追蹤必須將事件傾印到該檔案中。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-120">For the consumer application to be able to read the event in the etl file, Event Tracing for Windows must dump them into that file.</span></span> <span data-ttu-id="0fd8f-121">通常這是在控制器停用追蹤時完成。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-121">Normally this is done when the controller deactivates the tracing.</span></span>  
  
     <span data-ttu-id="0fd8f-122">若要使用取用者應用程式，而不停用追蹤，控制器必須啟動使用即時選項時，追蹤**\<即時\>=-rt**。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-122">To use the consumer application without deactivating the trace, the controller must activate the trace with the real-time option, **\<Real time\> = -rt**.</span></span>  
  
-   <span data-ttu-id="0fd8f-123">**提供者**。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-123">**Provider**.</span></span> <span data-ttu-id="0fd8f-124">用來提供事件。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-124">Used to provide the event.</span></span> <span data-ttu-id="0fd8f-125">BizTalk Adapter for JD Edwards EnterpriseOne 包含三種不同的提供者。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-125">BizTalk Adapter for JD Edwards EnterpriseOne includes three different providers.</span></span> <span data-ttu-id="0fd8f-126">它們是在 Windows Management Instrumentation (WMI) 中註冊的。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-126">They are registered in Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="0fd8f-127">若要在 root\WMI\EventTrace 路經中尋找已登錄的提供者，您可以使用諸如 WMI CIM Studio 這類的工具。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-127">To find the registered providers in the root\WMI\EventTrace path, you can use tools such as WMI CIM Studio.</span></span>  
  
 <span data-ttu-id="0fd8f-128">BizTalk Adapter  for JD Edwards EnterpriseOne 有三個提供者，可讓您記錄不同種類的訊息：</span><span class="sxs-lookup"><span data-stu-id="0fd8f-128">BizTalk Adapter  for JD Edwards EnterpriseOne contains three providers, allowing you to log different kinds of messages:</span></span>  
  
-   <span data-ttu-id="0fd8f-129">**接收器記錄提供者**:\<追蹤項目\>交換器 **-接收者**。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-129">**Receiver Logging Provider**: The \<Trace element\> switch is **-receiver**.</span></span> <span data-ttu-id="0fd8f-130">使用 **-接收者** 可在執行階段接收配接器的記錄檔中取得任何訊息。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-130">Use **-receiver** to get any messages from the log that were received by the adapter at run time.</span></span>  
  
-   <span data-ttu-id="0fd8f-131">**傳輸器記錄提供者**:\<追蹤項目\>交換器 **-傳輸器**。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-131">**Transmitter Logging Provider**: The \<Trace element\> switch is **-transmitter**.</span></span> <span data-ttu-id="0fd8f-132">使用 **-transmitter** 從傳輸配接器在執行階段的記錄檔中取得任何訊息。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-132">Use **-transmitter** to get any messages from the log that were transmitted by the adapter at run time.</span></span>  
  
-   <span data-ttu-id="0fd8f-133">**管理記錄提供者**:\<追蹤項目\>交換器 **-管理**使用 **-管理**從產生的記錄檔中取得任何訊息在瀏覽伺服器系統。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-133">**Management Logging Provider**: The \<Trace element\> switch is **-management** Use **-management** to get any messages from the log that were generated during browsing of the server system.</span></span>  
  
### <a name="btajdeenterpriseonetrace-command"></a><span data-ttu-id="0fd8f-134">BTAJDEEnterpriseOneTrace 命令</span><span class="sxs-lookup"><span data-stu-id="0fd8f-134">BTAJDEEnterpriseOneTrace Command</span></span>  
 <span data-ttu-id="0fd8f-135">若要使用 ETW，請執行 BizTalk Adapter for JD Edwards EnterpriseOne 命令 **BTAJDEEnterpriseOneTrace.cmd**。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-135">To use ETW, run the BizTalk Adapter for JD Edwards EnterpriseOne command, **BTAJDEEnterpriseOneTrace.cmd**.</span></span> <span data-ttu-id="0fd8f-136">您可以下列方式使用此命令：</span><span class="sxs-lookup"><span data-stu-id="0fd8f-136">You use this command as follows:</span></span>  
  
```  
BTAJDEEnterpriseOneTrace <Trace element> -start [-cir <MB>|   
-seq <MB>] [-rt] logfile  
BTAJDEEnterpriseOneTrace <Trace element> -stop  
  
```  
  
 <span data-ttu-id="0fd8f-137">位置： **\<追蹤項目\>** （必要） 是提供者的類型。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-137">Where: **\<Trace element\>** (required) is the kind of provider.</span></span>  
  
 <span data-ttu-id="0fd8f-138">可用選項包括：</span><span class="sxs-lookup"><span data-stu-id="0fd8f-138">Its options are:</span></span>  
  
-   <span data-ttu-id="0fd8f-139">**-傳輸器**</span><span class="sxs-lookup"><span data-stu-id="0fd8f-139">**-transmitter**</span></span>  
  
-   <span data-ttu-id="0fd8f-140">**-接收者**</span><span class="sxs-lookup"><span data-stu-id="0fd8f-140">**-receiver**</span></span>  
  
-   <span data-ttu-id="0fd8f-141">**-管理**</span><span class="sxs-lookup"><span data-stu-id="0fd8f-141">**-management**</span></span>  
  
-   <span data-ttu-id="0fd8f-142">**-start、-stop**︰ 啟用或停用提供者。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-142">**-start, -stop**: Activate or deactivate the provider.</span></span>  
  
-   <span data-ttu-id="0fd8f-143">**-cir \<MB\>**： 檔案的大小與種類。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-143">**-cir \<MB\>**: Size and kind of file.</span></span> <span data-ttu-id="0fd8f-144">-cir 是循環檔案。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-144">-cir is a circular file.</span></span> <span data-ttu-id="0fd8f-145">\<MB\>： 大小以 mb 表示。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-145">\<MB\>: Size in meg.</span></span>  
  
-   <span data-ttu-id="0fd8f-146">**-seq \<MB\>**： 檔案的大小與種類。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-146">**-seq \<MB\>**: Size and kind of file.</span></span> <span data-ttu-id="0fd8f-147">-seq 是循序檔案。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-147">-seq is a sequential file.</span></span> <span data-ttu-id="0fd8f-148">\<MB\>： 大小以 mb 表示。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-148">\<MB\>: Size in meg.</span></span>  
  
-   <span data-ttu-id="0fd8f-149">**-rt**︰ 上設定的即時模式。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-149">**-rt**: Set the real time mode on.</span></span>  
  
-   <span data-ttu-id="0fd8f-150">**記錄檔**︰ 記錄檔的名稱 （c:\rtlog.etl 是預設值）。</span><span class="sxs-lookup"><span data-stu-id="0fd8f-150">**Logfile**: Name of the log file (c:\rtlog.etl is the default).</span></span>  
  
 <span data-ttu-id="0fd8f-151">例如：</span><span class="sxs-lookup"><span data-stu-id="0fd8f-151">For example:</span></span>  
  
```  
BTAJDEEnterpriseOneTrace -transmitter -start -cir 10 -rt c:\log\mylog.etl  
BTAJDEEnterpriseOneTrace -transmitter -stop  
```  
  
## <a name="see-also"></a><span data-ttu-id="0fd8f-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0fd8f-152">See Also</span></span>  
 [<span data-ttu-id="0fd8f-153">疑難排解 JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="0fd8f-153">Troubleshooting JD Edwards EnterpriseOne</span></span>](../core/troubleshooting-jd-edwards-enterpriseone.md)