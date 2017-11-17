---
title: "使用效能計數器，與 WCF LOB 配接器 SDK |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b928eaf-2ab6-40a6-a1dd-804d4e89541e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ead07059cac11f251d35fae18f0e228c4488c07a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="use-performance-counters-with-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="77173-102">使用效能計數器，與 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="77173-102">Use performance counters with the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="77173-103">您可以使用 [效能] 工具會自動收集效能資料，從本機或遠端電腦執行[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="77173-103">You can use the performance tool to automatically collect performance data from local or remote computers that are running the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="77173-104">您可以定義開始和停止時間，來自動產生記錄檔，從單一主控台視窗中，管理多個記錄工作階段，然後設定可讓要傳送訊息的電腦上的記錄檔，以符合您的準則時啟動的警示。</span><span class="sxs-lookup"><span data-stu-id="77173-104">You can define start and stop times for automatic log generation, manage multiple logging sessions from a single console window, and set an alert on a computer that enables a message to be sent or a log to be started when your criteria are met.</span></span> <span data-ttu-id="77173-105">本主題討論的效能計數器[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="77173-105">This topic discusses the performance counters for the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span>  
  
## <a name="performance-objects-and-counters"></a><span data-ttu-id="77173-106">效能物件和計數器</span><span class="sxs-lookup"><span data-stu-id="77173-106">Performance Objects and Counters</span></span>  
 <span data-ttu-id="77173-107">當您安裝[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，已安裝名為"ServiceModel 配接器 」 的單一效能物件。</span><span class="sxs-lookup"><span data-stu-id="77173-107">When you install the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], a single performance object named "ServiceModel Adapters" is installed.</span></span> <span data-ttu-id="77173-108">效能物件包含許多不同的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="77173-108">The performance object contains a number of different performance counters.</span></span> <span data-ttu-id="77173-109">效能物件會測量特定的資源、 應用程式或服務的活動。</span><span class="sxs-lookup"><span data-stu-id="77173-109">A performance object measures the activity for a given resource, application, or service.</span></span> <span data-ttu-id="77173-110">效能物件和計數器取得計數器的效能資料[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]、 功能、 和服務電腦上相同的方式。</span><span class="sxs-lookup"><span data-stu-id="77173-110">Performance objects and counters obtain performance data from the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], features, and services on your computer as they are used.</span></span> <span data-ttu-id="77173-111">此效能資料通常會命名為元件所產生的資料。</span><span class="sxs-lookup"><span data-stu-id="77173-111">This performance data is typically named for the component that generates the data.</span></span> <span data-ttu-id="77173-112">效能計數器可用來收集特定資訊或指定的效能物件的資料。</span><span class="sxs-lookup"><span data-stu-id="77173-112">Performance counters are used for gathering specific information or data for a given performance object.</span></span>  
  
 <span data-ttu-id="77173-113">當選取計數器的 ServiceModel 配接器效能物件中，您可以選擇只從選取的執行個體清單中選取執行個體來監視資訊的特定配接器執行個體。</span><span class="sxs-lookup"><span data-stu-id="77173-113">When selecting counters from the ServiceModel Adapters performance object, you can choose to only monitor information specific adapter instances by selecting the instance from the Select Instances list.</span></span> <span data-ttu-id="77173-114">每個配接器執行個體將會列在格式\<ProcessId > @\<ConnectionString >。</span><span class="sxs-lookup"><span data-stu-id="77173-114">Each adapter instance will be listed in the format of \<ProcessId>@\<ConnectionString>.</span></span> <span data-ttu-id="77173-115">比方說， 115@echo:&#124; &#124; 主機 &#124; temp？ echoprefix = 前表示回應配接器執行個體處理序 115 中執行。</span><span class="sxs-lookup"><span data-stu-id="77173-115">For example, 115@echo:&#124;&#124;host&#124;temp?echoprefix=pre indicates the echo adapter instance running in process 115.</span></span>  
  
 <span data-ttu-id="77173-116">在 WCF 中的效能計數器的相關資訊，請參閱[WCF 效能計數器](https://msdn.microsoft.com/library/ms735098.aspx)。</span><span class="sxs-lookup"><span data-stu-id="77173-116">For information about performance counters in WCF, see [WCF Performance Counters](https://msdn.microsoft.com/library/ms735098.aspx).</span></span>
  
### <a name="servicemodel-adapters-metadata-cache-performance-counters"></a><span data-ttu-id="77173-117">ServiceModel 配接器中繼資料快取效能計數器</span><span class="sxs-lookup"><span data-stu-id="77173-117">ServiceModel Adapters Metadata Cache Performance Counters</span></span>  
 <span data-ttu-id="77173-118">下表摘要說明可用來監視快取效能計數器[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="77173-118">The following table summarizes the cache performance counters that can be used to monitor the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span>  
  
|<span data-ttu-id="77173-119">計數器</span><span class="sxs-lookup"><span data-stu-id="77173-119">Counter</span></span>|<span data-ttu-id="77173-120">Description</span><span class="sxs-lookup"><span data-stu-id="77173-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="77173-121">%快取讀取的叫用</span><span class="sxs-lookup"><span data-stu-id="77173-121">% Cache read hits</span></span>|<span data-ttu-id="77173-122">讀取配接器快取點擊的中繼資料的百分比。</span><span class="sxs-lookup"><span data-stu-id="77173-122">Percentage of metadata read hits in the adapter cache.</span></span>|  
|<span data-ttu-id="77173-123">判斷已解決的中繼資料</span><span class="sxs-lookup"><span data-stu-id="77173-123">Metadata Resolved</span></span>|<span data-ttu-id="77173-124">配接器所解析的中繼資料項目的數目。</span><span class="sxs-lookup"><span data-stu-id="77173-124">Number of metadata items resolved by the adapter.</span></span>|  
|<span data-ttu-id="77173-125">%完整快取</span><span class="sxs-lookup"><span data-stu-id="77173-125">% Cache full</span></span>|<span data-ttu-id="77173-126">使用中的快取大小限制的百分比。</span><span class="sxs-lookup"><span data-stu-id="77173-126">Percentage of the cache size limit in use.</span></span>|  
  
### <a name="servicemodel-adapters-connection-performance-counters"></a><span data-ttu-id="77173-127">ServiceModel 介面卡連線效能計數器</span><span class="sxs-lookup"><span data-stu-id="77173-127">ServiceModel Adapters Connection Performance Counters</span></span>  
 <span data-ttu-id="77173-128">下表摘要說明用於監視的連線效能計數器[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="77173-128">The following table summarizes the connection performance counters that can be used to monitor the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span>  
  
|<span data-ttu-id="77173-129">計數器</span><span class="sxs-lookup"><span data-stu-id="77173-129">Counter</span></span>|<span data-ttu-id="77173-130">Description</span><span class="sxs-lookup"><span data-stu-id="77173-130">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="77173-131">已中止的連線</span><span class="sxs-lookup"><span data-stu-id="77173-131">Aborted Connections</span></span>|<span data-ttu-id="77173-132">已中止的目標系統的連線數目。</span><span class="sxs-lookup"><span data-stu-id="77173-132">Number of aborted target system connections.</span></span>|  
|<span data-ttu-id="77173-133">使用中連接</span><span class="sxs-lookup"><span data-stu-id="77173-133">In-use Connections</span></span>|<span data-ttu-id="77173-134">目前使用中的目標系統的連線數目。</span><span class="sxs-lookup"><span data-stu-id="77173-134">Number of currently in-use target system connections.</span></span>|  
|<span data-ttu-id="77173-135">開啟的連接</span><span class="sxs-lookup"><span data-stu-id="77173-135">Opened Connections</span></span>|<span data-ttu-id="77173-136">目前開啟的目標系統的連線數目。</span><span class="sxs-lookup"><span data-stu-id="77173-136">Number of currently open target system connections.</span></span>|  
|<span data-ttu-id="77173-137">準備好的連線</span><span class="sxs-lookup"><span data-stu-id="77173-137">Ready Connections</span></span>|<span data-ttu-id="77173-138">可用的目標系統的連線數目。</span><span class="sxs-lookup"><span data-stu-id="77173-138">Number of available target system connections.</span></span>|  
|<span data-ttu-id="77173-139">暫止的連接要求</span><span class="sxs-lookup"><span data-stu-id="77173-139">Pending Connection Requests</span></span>|<span data-ttu-id="77173-140">數字的暫止的目標系統的連線要求。</span><span class="sxs-lookup"><span data-stu-id="77173-140">Number of pending target system connection requests.</span></span>|  
  
### <a name="servicemodel-adapters-message-exchange-performance-counters"></a><span data-ttu-id="77173-141">ServiceModel 配接器訊息交換的效能計數器</span><span class="sxs-lookup"><span data-stu-id="77173-141">ServiceModel Adapters Message Exchange Performance Counters</span></span>  
 <span data-ttu-id="77173-142">下表摘要說明用於監視的訊息交換效能計數器[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="77173-142">The following table summarizes the message exchange performance counters that can be used to monitor the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span>  
  
|<span data-ttu-id="77173-143">計數器</span><span class="sxs-lookup"><span data-stu-id="77173-143">Counter</span></span>|<span data-ttu-id="77173-144">Description</span><span class="sxs-lookup"><span data-stu-id="77173-144">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="77173-145">傳出呼叫</span><span class="sxs-lookup"><span data-stu-id="77173-145">Outbound Calls</span></span>|<span data-ttu-id="77173-146">從配接器到目標系統進行傳出呼叫的數目。</span><span class="sxs-lookup"><span data-stu-id="77173-146">Number of outbound calls from the adapter to the target system.</span></span>|  
|<span data-ttu-id="77173-147">輸出 Calls/sec</span><span class="sxs-lookup"><span data-stu-id="77173-147">Outbound Calls/sec</span></span>|<span data-ttu-id="77173-148">傳出呼叫每秒從配接器到目標系統的數目。</span><span class="sxs-lookup"><span data-stu-id="77173-148">Number of outbound calls per second from the adapter to the target system.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="77173-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77173-149">See Also</span></span>  
 [<span data-ttu-id="77173-150">使用 WCF LOB 配接器 SDK 所建立的配接器進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="77173-150">Troubleshoot adapter created using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/troubleshoot-adapter-created-using-the-wcf-lob-adapter-sdk.md)