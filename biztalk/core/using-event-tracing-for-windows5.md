---
title: 事件追蹤用於 Windows5 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ETW
- events, Event Tracing for Windows
- controller application
- ETW components
- consumer application
- Provider
- Event Tracing for Windows
- Event Tracing for Windows, components
- BTAPeopleSoftTrace command
ms.assetid: 330ef84b-5e2a-4b79-85a9-72271eb489d2
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60a317dabd31bc1a6f37645c6b3fb2ce25d6de43
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "25973548"
---
# <a name="using-event-tracing-for-windows"></a><span data-ttu-id="e5c42-102">使用 Windows 事件追蹤</span><span class="sxs-lookup"><span data-stu-id="e5c42-102">Using Event Tracing for Windows</span></span>
<span data-ttu-id="e5c42-103">Microsoft BizTalk Adapter for PeopleSoft Enterprise 會將錯誤、警告與資訊訊息記錄到 Windows 事件檢視器中。</span><span class="sxs-lookup"><span data-stu-id="e5c42-103">Microsoft BizTalk Adapter for PeopleSoft Enterprise logs error, warning, and information messages to the Windows Event Viewer.</span></span> <span data-ttu-id="e5c42-104">您可以使用「Windows 事件追蹤」工具來查看其他追蹤訊息。</span><span class="sxs-lookup"><span data-stu-id="e5c42-104">You can see additional tracing messages by using the Event Tracing for Windows (ETW) tool.</span></span> <span data-ttu-id="e5c42-105">當 ETW 啟用時，它會建立 \*.etl 檔案以接收訊息。</span><span class="sxs-lookup"><span data-stu-id="e5c42-105">When ETW is enabled, it creates an \*.etl file to receive the messages.</span></span> <span data-ttu-id="e5c42-106">檔案是二進位格式，必須經過轉換才能讀取。</span><span class="sxs-lookup"><span data-stu-id="e5c42-106">The file is in binary format and must be converted to be read.</span></span> <span data-ttu-id="e5c42-107">您必須擁有可解譯的消費者應用程式才能執行這項操作 \*.etl 檔案; 例如，tracerpt.exe 或 tracedmp.exe。</span><span class="sxs-lookup"><span data-stu-id="e5c42-107">To do this you must have a consumer application available to interpret the \*.etl file; for example, tracerpt.exe or tracedmp.exe.</span></span>  
  
## <a name="etw-components"></a><span data-ttu-id="e5c42-108">ETW 元件</span><span class="sxs-lookup"><span data-stu-id="e5c42-108">ETW Components</span></span>  
 <span data-ttu-id="e5c42-109">「Windows 事件追蹤」有三個元件：</span><span class="sxs-lookup"><span data-stu-id="e5c42-109">Event Tracing for Windows has three components:</span></span>  
  
-   <span data-ttu-id="e5c42-110">**控制器應用程式**︰ 啟用和停用提供者 （例如，tracelog.exe 或 logman.exe）。</span><span class="sxs-lookup"><span data-stu-id="e5c42-110">**Controller application**: Activates and deactivates a provider (for example, tracelog.exe or logman.exe).</span></span>  
  
     <span data-ttu-id="e5c42-111">您會將 PATH 環境變數設定成指向 tracelog.exe 的位置。</span><span class="sxs-lookup"><span data-stu-id="e5c42-111">You set your PATH environment variable to point to the location of tracelog.exe.</span></span> <span data-ttu-id="e5c42-112">這樣可確保 `BTAPeopleSoftTrace` 呼叫可在系統中找到 tracelog.exe。</span><span class="sxs-lookup"><span data-stu-id="e5c42-112">This makes sure that `BTAPeopleSoftTrace` calls can locate tracelog.exe in the system.</span></span> <span data-ttu-id="e5c42-113">根據預設，BTAPeopleSoftTrace 會搜尋目前的路徑。</span><span class="sxs-lookup"><span data-stu-id="e5c42-113">By default, BTAPeopleSoftTrace searches the current path.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e5c42-114">tracelog.exe 可以從 Microsoft SDK 取得，且和 BizTalk Adapter for PeopleSoft Enterprise 提供的命令相容。</span><span class="sxs-lookup"><span data-stu-id="e5c42-114">tracelog.exe is available from the Microsoft SDK and is compatible with the commands provided by BizTalk Adapter for PeopleSoft Enterprise.</span></span> <span data-ttu-id="e5c42-115">如果要使用 logman.exe，請參閱 logman 文件。</span><span class="sxs-lookup"><span data-stu-id="e5c42-115">To use logman.exe, see the logman documentation.</span></span>  
  
-   <span data-ttu-id="e5c42-116">**取用者應用程式**︰ 讀取記錄的事件。</span><span class="sxs-lookup"><span data-stu-id="e5c42-116">**Consumer application**: Reads logged events.</span></span>  
  
     <span data-ttu-id="e5c42-117">如果要讓取用者應用程式可讀取 .etl 檔案中的事件，「Windows 事件追蹤」必須將它們傾印到該檔案。</span><span class="sxs-lookup"><span data-stu-id="e5c42-117">For the consumer application to be able to read the event in the .etl file, Event Tracing for Windows must dump them into that file.</span></span> <span data-ttu-id="e5c42-118">此動作通常是在控制器停用追蹤後完成的。</span><span class="sxs-lookup"><span data-stu-id="e5c42-118">Typically this is done when the controller deactivates the tracing.</span></span>  
  
     <span data-ttu-id="e5c42-119">若要使用取用者，而不停用追蹤，控制器必須啟動使用即時選項時，追蹤\<即時\>=-rt。</span><span class="sxs-lookup"><span data-stu-id="e5c42-119">To use the consumer without deactivating the trace, the controller must activate the trace with the real time option, \<Real time\> = -rt.</span></span>  
  
-   <span data-ttu-id="e5c42-120">**提供者︰** 提供事件。</span><span class="sxs-lookup"><span data-stu-id="e5c42-120">**Provider:** Provides the event.</span></span>  
  
     <span data-ttu-id="e5c42-121">BizTalk Adapter for PeopleSoft Enterprise 有五個不同的提供者。</span><span class="sxs-lookup"><span data-stu-id="e5c42-121">BizTalk Adapter for PeopleSoft Enterprise has five different providers.</span></span> <span data-ttu-id="e5c42-122">它們是在 Windows Management Instrumentation (WMI) 中註冊的。</span><span class="sxs-lookup"><span data-stu-id="e5c42-122">They are registered in Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="e5c42-123">若要尋找已註冊的提供者在 **root\WMI\EventTrace** 路徑，您可以使用 WMI CIM Studio 之類的工具。</span><span class="sxs-lookup"><span data-stu-id="e5c42-123">To find the registered providers in the **root\WMI\EventTrace** path, you can use tools such as WMI CIM Studio.</span></span>  
  
 <span data-ttu-id="e5c42-124">BizTalk Adapter for PeopleSoft Enterprise 有五個提供者，可讓您記錄不同種類的訊息：</span><span class="sxs-lookup"><span data-stu-id="e5c42-124">BizTalk Adapter for PeopleSoft Enterprise has five providers, allowing you to log different kinds of messages:</span></span>  
  
-   <span data-ttu-id="e5c42-125">**接收器記錄提供者**:\<追蹤項目\>交換器 **-接收者**。</span><span class="sxs-lookup"><span data-stu-id="e5c42-125">**Receiver Logging Provider**: The \<Trace element\> switch is **-receiver**.</span></span>  
  
-   <span data-ttu-id="e5c42-126">**接收器 Castdetail 提供者**:\<追蹤項目\>交換器 **-castDetailsReceive**。</span><span class="sxs-lookup"><span data-stu-id="e5c42-126">**Receiver CastDetails Provider**: The \<Trace element\> switch is **-castDetailsReceive**.</span></span>  
  
-   <span data-ttu-id="e5c42-127">**傳輸器記錄提供者**:\<追蹤項目\>交換器 **-傳輸器**。</span><span class="sxs-lookup"><span data-stu-id="e5c42-127">**Transmitter Logging Provider**: The \<Trace element\> switch is **-transmitter**.</span></span>  
  
-   <span data-ttu-id="e5c42-128">**傳輸器 CastDetails 提供者**:\<追蹤項目\>交換器 **-castDetailsTransmit**。</span><span class="sxs-lookup"><span data-stu-id="e5c42-128">**Transmitter CastDetails Provider**: The \<Trace element\> switch is **-castDetailsTransmit**.</span></span>  
  
-   <span data-ttu-id="e5c42-129">**管理記錄提供者**:\<追蹤項目\>交換器 **-管理**。</span><span class="sxs-lookup"><span data-stu-id="e5c42-129">**Management Logging Provider**: The \<Trace element\> switch is **-management**.</span></span>  
  
## <a name="btapeoplesofttrace-command"></a><span data-ttu-id="e5c42-130">BTAPeopleSoftTrace 命令</span><span class="sxs-lookup"><span data-stu-id="e5c42-130">BTAPeopleSoftTrace Command</span></span>  
 <span data-ttu-id="e5c42-131">若要使用 ETW，請執行配接器命令 **BTAPeopleSoftTrace.cmd**。</span><span class="sxs-lookup"><span data-stu-id="e5c42-131">To use ETW, run the adapter command, **BTAPeopleSoftTrace.cmd**.</span></span> <span data-ttu-id="e5c42-132">您可以下列方式使用此命令：</span><span class="sxs-lookup"><span data-stu-id="e5c42-132">You use this command as follows:</span></span>  
  
```  
BTAPeopleSoftTrace <Trace element> -start [-cir <MB>|   
    -seq <MB>] [-rt] logfile  
BTAPeopleSoftTrace <Trace element> -stop  
```  
  
 <span data-ttu-id="e5c42-133">其中：</span><span class="sxs-lookup"><span data-stu-id="e5c42-133">Where:</span></span>  
  
-   <span data-ttu-id="e5c42-134">\<追蹤項目\>（必要） 是提供者的類型。</span><span class="sxs-lookup"><span data-stu-id="e5c42-134">\<Trace element\> (required) is the kind of provider.</span></span>  
  
     <span data-ttu-id="e5c42-135">選項如下：</span><span class="sxs-lookup"><span data-stu-id="e5c42-135">Options are as follows:</span></span>  
  
    -   <span data-ttu-id="e5c42-136">**-castDetailsTransmit**</span><span class="sxs-lookup"><span data-stu-id="e5c42-136">**-castDetailsTransmit**</span></span>  
  
    -   <span data-ttu-id="e5c42-137">**-傳輸器**</span><span class="sxs-lookup"><span data-stu-id="e5c42-137">**-transmitter**</span></span>  
  
    -   <span data-ttu-id="e5c42-138">**-castDetailsReceive**</span><span class="sxs-lookup"><span data-stu-id="e5c42-138">**-castDetailsReceive**</span></span>  
  
    -   <span data-ttu-id="e5c42-139">**-接收者**</span><span class="sxs-lookup"><span data-stu-id="e5c42-139">**-receiver**</span></span>  
  
    -   <span data-ttu-id="e5c42-140">**-管理**</span><span class="sxs-lookup"><span data-stu-id="e5c42-140">**-management**</span></span>  
  
    -   <span data-ttu-id="e5c42-141">**-start、-stop**︰ 啟用或停用提供者。</span><span class="sxs-lookup"><span data-stu-id="e5c42-141">**-start, -stop**: Activate or deactivate the provider.</span></span>  
  
-   <span data-ttu-id="e5c42-142">**-cir \<MB\>**： 檔案的大小與種類。</span><span class="sxs-lookup"><span data-stu-id="e5c42-142">**-cir \<MB\>**: Size and kind of file.</span></span> <span data-ttu-id="e5c42-143">-cir 是循環檔案。</span><span class="sxs-lookup"><span data-stu-id="e5c42-143">-cir is a circular file.</span></span> <span data-ttu-id="e5c42-144">\<MB\>： 以 mb 為單位的大小。</span><span class="sxs-lookup"><span data-stu-id="e5c42-144">\<MB\>: Size in megabytes.</span></span>  
  
-   <span data-ttu-id="e5c42-145">**-seq \<MB\>**： 檔案的大小與種類。</span><span class="sxs-lookup"><span data-stu-id="e5c42-145">**-seq \<MB\>**: Size and kind of file.</span></span> <span data-ttu-id="e5c42-146">-seq 是循序檔案。</span><span class="sxs-lookup"><span data-stu-id="e5c42-146">-seq is a sequential file.</span></span> <span data-ttu-id="e5c42-147">\<MB\>： 以 mb 為單位的大小。</span><span class="sxs-lookup"><span data-stu-id="e5c42-147">\<MB\>: Size in megabytes.</span></span>  
  
-   <span data-ttu-id="e5c42-148">**-rt**︰ 上設定的即時模式。</span><span class="sxs-lookup"><span data-stu-id="e5c42-148">**-rt**: Set the real time mode on.</span></span>  
  
-   <span data-ttu-id="e5c42-149">**記錄檔**: （C:\rtlog.etl 是預設值） 的記錄檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="e5c42-149">**Logfile**: Name of the log file (C:\rtlog.etl is the default).</span></span>  
  
 <span data-ttu-id="e5c42-150">例如：</span><span class="sxs-lookup"><span data-stu-id="e5c42-150">For example:</span></span>  
  
```  
BTAPeopleSoftTrace -transmitter -start -cir 10 -rt C:\log\mylog.etl  
BTAPeopleSoftTrace -transmitter -stop  
```  
  
## <a name="see-also"></a><span data-ttu-id="e5c42-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5c42-151">See Also</span></span>  
 [<span data-ttu-id="e5c42-152">疑難排解 peoplesoft 問題</span><span class="sxs-lookup"><span data-stu-id="e5c42-152">Troubleshooting PeopleSoft</span></span>](../core/troubleshooting-peoplesoft.md)