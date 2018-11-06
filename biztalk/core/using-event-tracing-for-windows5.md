---
title: 使用事件追蹤 Windows5 |Microsoft Docs
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
ms.openlocfilehash: ff69c0740b772070551697152c49be8c89a16610
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50752862"
---
# <a name="using-event-tracing-for-windows"></a><span data-ttu-id="ac5cd-102">使用 Windows 追蹤的事件</span><span class="sxs-lookup"><span data-stu-id="ac5cd-102">Using Event Tracing for Windows</span></span>
<span data-ttu-id="ac5cd-103">Microsoft BizTalk Adapter for PeopleSoft Enterprise 會將錯誤、警告與資訊訊息記錄到 Windows 事件檢視器中。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-103">Microsoft BizTalk Adapter for PeopleSoft Enterprise logs error, warning, and information messages to the Windows Event Viewer.</span></span> <span data-ttu-id="ac5cd-104">您可以使用「Windows 事件追蹤」工具來查看其他追蹤訊息。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-104">You can see additional tracing messages by using the Event Tracing for Windows (ETW) tool.</span></span> <span data-ttu-id="ac5cd-105">當 ETW 啟用時，它會建立\*.etl 檔案以接收的訊息。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-105">When ETW is enabled, it creates an \*.etl file to receive the messages.</span></span> <span data-ttu-id="ac5cd-106">檔案是二進位格式，必須經過轉換才能讀取。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-106">The file is in binary format and must be converted to be read.</span></span> <span data-ttu-id="ac5cd-107">若要這樣做，您必須具有可解譯的消費者應用程式\*.etl 檔案; 例如，tracerpt.exe 或 tracedmp.exe。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-107">To do this you must have a consumer application available to interpret the \*.etl file; for example, tracerpt.exe or tracedmp.exe.</span></span>  
  
## <a name="etw-components"></a><span data-ttu-id="ac5cd-108">ETW 元件</span><span class="sxs-lookup"><span data-stu-id="ac5cd-108">ETW Components</span></span>  
 <span data-ttu-id="ac5cd-109">「Windows 事件追蹤」有三個元件：</span><span class="sxs-lookup"><span data-stu-id="ac5cd-109">Event Tracing for Windows has three components:</span></span>  
  
- <span data-ttu-id="ac5cd-110">**控制器應用程式**： 啟用和停用提供者 （例如，tracelog.exe 或 logman.exe）。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-110">**Controller application**: Activates and deactivates a provider (for example, tracelog.exe or logman.exe).</span></span>  
  
   <span data-ttu-id="ac5cd-111">您會將 PATH 環境變數設定成指向 tracelog.exe 的位置。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-111">You set your PATH environment variable to point to the location of tracelog.exe.</span></span> <span data-ttu-id="ac5cd-112">這樣可確保`BTAPeopleSoftTrace`呼叫可在系統中找到 tracelog.exe。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-112">This makes sure that `BTAPeopleSoftTrace` calls can locate tracelog.exe in the system.</span></span> <span data-ttu-id="ac5cd-113">根據預設，BTAPeopleSoftTrace 會搜尋目前的路徑。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-113">By default, BTAPeopleSoftTrace searches the current path.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="ac5cd-114">tracelog.exe 可以從 Microsoft SDK 取得，且和 BizTalk Adapter for PeopleSoft Enterprise 提供的命令相容。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-114">tracelog.exe is available from the Microsoft SDK and is compatible with the commands provided by BizTalk Adapter for PeopleSoft Enterprise.</span></span> <span data-ttu-id="ac5cd-115">如果要使用 logman.exe，請參閱 logman 文件。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-115">To use logman.exe, see the logman documentation.</span></span>  
  
- <span data-ttu-id="ac5cd-116">**取用者應用程式**： 讀取記錄的事件。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-116">**Consumer application**: Reads logged events.</span></span>  
  
   <span data-ttu-id="ac5cd-117">如果要讓取用者應用程式可讀取 .etl 檔案中的事件，「Windows 事件追蹤」必須將它們傾印到該檔案。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-117">For the consumer application to be able to read the event in the .etl file, Event Tracing for Windows must dump them into that file.</span></span> <span data-ttu-id="ac5cd-118">此動作通常是在控制器停用追蹤後完成的。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-118">Typically this is done when the controller deactivates the tracing.</span></span>  
  
   <span data-ttu-id="ac5cd-119">若要使用的取用者，而不需要停用追蹤，控制器必須啟用使用即時選項時，追蹤\<即時\>=-rt。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-119">To use the consumer without deactivating the trace, the controller must activate the trace with the real time option, \<Real time\> = -rt.</span></span>  
  
- <span data-ttu-id="ac5cd-120">**提供者：** 提供事件。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-120">**Provider:** Provides the event.</span></span>  
  
   <span data-ttu-id="ac5cd-121">BizTalk Adapter for PeopleSoft Enterprise 有五個不同的提供者。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-121">BizTalk Adapter for PeopleSoft Enterprise has five different providers.</span></span> <span data-ttu-id="ac5cd-122">它們是在 Windows Management Instrumentation (WMI) 中註冊的。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-122">They are registered in Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="ac5cd-123">若要尋找中已註冊的提供者**root\WMI\EventTrace**路徑，您可以使用 WMI CIM Studio 這類的工具。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-123">To find the registered providers in the **root\WMI\EventTrace** path, you can use tools such as WMI CIM Studio.</span></span>  
  
  <span data-ttu-id="ac5cd-124">BizTalk Adapter for PeopleSoft Enterprise 有五個提供者，可讓您記錄不同種類的訊息：</span><span class="sxs-lookup"><span data-stu-id="ac5cd-124">BizTalk Adapter for PeopleSoft Enterprise has five providers, allowing you to log different kinds of messages:</span></span>  
  
- <span data-ttu-id="ac5cd-125">**接收器記錄提供者**:\<追蹤項目\>交換器 **-接收者**。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-125">**Receiver Logging Provider**: The \<Trace element\> switch is **-receiver**.</span></span>  
  
- <span data-ttu-id="ac5cd-126">**接收器 Castdetail 提供者**:\<追蹤項目\>交換器 **-castDetailsReceive**。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-126">**Receiver CastDetails Provider**: The \<Trace element\> switch is **-castDetailsReceive**.</span></span>  
  
- <span data-ttu-id="ac5cd-127">**傳輸器記錄提供者**:\<追蹤項目\>交換器 **-傳輸器**。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-127">**Transmitter Logging Provider**: The \<Trace element\> switch is **-transmitter**.</span></span>  
  
- <span data-ttu-id="ac5cd-128">**傳輸器 CastDetails 提供者**:\<追蹤項目\>交換器 **-castDetailsTransmit**。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-128">**Transmitter CastDetails Provider**: The \<Trace element\> switch is **-castDetailsTransmit**.</span></span>  
  
- <span data-ttu-id="ac5cd-129">**管理記錄提供者**:\<追蹤項目\>交換器 **-管理**。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-129">**Management Logging Provider**: The \<Trace element\> switch is **-management**.</span></span>  
  
## <a name="btapeoplesofttrace-command"></a><span data-ttu-id="ac5cd-130">BTAPeopleSoftTrace 命令</span><span class="sxs-lookup"><span data-stu-id="ac5cd-130">BTAPeopleSoftTrace Command</span></span>  
 <span data-ttu-id="ac5cd-131">若要使用 ETW，請執行 [配接器] 命令中， **BTAPeopleSoftTrace.cmd**。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-131">To use ETW, run the adapter command, **BTAPeopleSoftTrace.cmd**.</span></span> <span data-ttu-id="ac5cd-132">您可以下列方式使用此命令：</span><span class="sxs-lookup"><span data-stu-id="ac5cd-132">You use this command as follows:</span></span>  
  
```  
BTAPeopleSoftTrace <Trace element> -start [-cir <MB>|   
    -seq <MB>] [-rt] logfile  
BTAPeopleSoftTrace <Trace element> -stop  
```  
  
 <span data-ttu-id="ac5cd-133">其中：</span><span class="sxs-lookup"><span data-stu-id="ac5cd-133">Where:</span></span>  
  
- <span data-ttu-id="ac5cd-134">\<追蹤項目\>（必要） 是一種提供者。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-134">\<Trace element\> (required) is the kind of provider.</span></span>  
  
   <span data-ttu-id="ac5cd-135">選項如下：</span><span class="sxs-lookup"><span data-stu-id="ac5cd-135">Options are as follows:</span></span>  
  
  -   <span data-ttu-id="ac5cd-136">**-castDetailsTransmit**</span><span class="sxs-lookup"><span data-stu-id="ac5cd-136">**-castDetailsTransmit**</span></span>  
  
  -   <span data-ttu-id="ac5cd-137">**-傳輸器**</span><span class="sxs-lookup"><span data-stu-id="ac5cd-137">**-transmitter**</span></span>  
  
  -   <span data-ttu-id="ac5cd-138">**-castDetailsReceive**</span><span class="sxs-lookup"><span data-stu-id="ac5cd-138">**-castDetailsReceive**</span></span>  
  
  -   <span data-ttu-id="ac5cd-139">**-接收者**</span><span class="sxs-lookup"><span data-stu-id="ac5cd-139">**-receiver**</span></span>  
  
  -   <span data-ttu-id="ac5cd-140">**-管理**</span><span class="sxs-lookup"><span data-stu-id="ac5cd-140">**-management**</span></span>  
  
  -   <span data-ttu-id="ac5cd-141">**-啟動、-停止**： 啟用或停用提供者。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-141">**-start, -stop**: Activate or deactivate the provider.</span></span>  
  
- <span data-ttu-id="ac5cd-142">**-cir \<MB\>**： 檔案的大小與種類。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-142">**-cir \<MB\>**: Size and kind of file.</span></span> <span data-ttu-id="ac5cd-143">-cir 是循環檔案。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-143">-cir is a circular file.</span></span> <span data-ttu-id="ac5cd-144">\<MB\>： 以 mb 為單位的大小。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-144">\<MB\>: Size in megabytes.</span></span>  
  
- <span data-ttu-id="ac5cd-145">**-seq \<MB\>**： 檔案的大小與種類。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-145">**-seq \<MB\>**: Size and kind of file.</span></span> <span data-ttu-id="ac5cd-146">-seq 是循序檔案。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-146">-seq is a sequential file.</span></span> <span data-ttu-id="ac5cd-147">\<MB\>： 以 mb 為單位的大小。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-147">\<MB\>: Size in megabytes.</span></span>  
  
- <span data-ttu-id="ac5cd-148">**-rt**： 上設定的即時模式。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-148">**-rt**: Set the real time mode on.</span></span>  
  
- <span data-ttu-id="ac5cd-149">**Logfile**: （C:\rtlog.etl 是預設值） 的記錄檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="ac5cd-149">**Logfile**: Name of the log file (C:\rtlog.etl is the default).</span></span>  
  
  <span data-ttu-id="ac5cd-150">例如：</span><span class="sxs-lookup"><span data-stu-id="ac5cd-150">For example:</span></span>  
  
```  
BTAPeopleSoftTrace -transmitter -start -cir 10 -rt C:\log\mylog.etl  
BTAPeopleSoftTrace -transmitter -stop  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac5cd-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac5cd-151">See Also</span></span>  
 [<span data-ttu-id="ac5cd-152">疑難排解 PeopleSoft 問題</span><span class="sxs-lookup"><span data-stu-id="ac5cd-152">Troubleshooting PeopleSoft</span></span>](../core/troubleshooting-peoplesoft.md)