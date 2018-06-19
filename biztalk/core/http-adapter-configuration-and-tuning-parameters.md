---
title: HTTP 配接器組態和調整參數 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- HTTP adapters, parameters
- configuring [HTTP adapters], parameters
- HTTP adapters, tuning
- RequestQueueSize key [HTTP adapters]
- HttpReceiveThreadsPerCpu key [HTTP adapters]
- HttpOutTimeoutInterval key [HTTP adapters]
- HttpOutInflightSize key [HTTP adapters]
- configuring [HTTP adapters], tuning
- DisableChunkEncoding key [HTTP adapters]
- HttpOutCompleteSize key [HTTP adapters]
ms.assetid: c8989a88-722a-40b5-94cf-4b6840add02e
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5db4f4dc4403ddfbf677ac2729c00e2b1976db61
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257782"
---
# <a name="http-adapter-configuration-and-tuning-parameters"></a><span data-ttu-id="c41c1-102">HTTP 配接器組態和調整參數</span><span class="sxs-lookup"><span data-stu-id="c41c1-102">HTTP Adapter Configuration and Tuning Parameters</span></span>
<span data-ttu-id="c41c1-103">HTTP 配接器可以透過登錄機碼項目和修改位於 BizTalk Server 安裝根目錄的 BTSNTSvc.exe.config 檔案，來存取組態和調整參數。</span><span class="sxs-lookup"><span data-stu-id="c41c1-103">Several configuration and tuning parameters are accessible for the HTTP adapter through registry key entries and through the modification of the BTSNTSvc.exe.config file that is located in the root BizTalk Server installation directory.</span></span>  
  
 <span data-ttu-id="c41c1-104">**影響 HTTP 配接器效能的登錄設定**</span><span class="sxs-lookup"><span data-stu-id="c41c1-104">**Registry Settings That Affect HTTP Adapter Performance**</span></span>  
  
 <span data-ttu-id="c41c1-105">下表描述會影響 HTTP 配接器效能的登錄設定。</span><span class="sxs-lookup"><span data-stu-id="c41c1-105">The following table describes the registry settings that affect the performance of the HTTP adapter.</span></span> <span data-ttu-id="c41c1-106">請注意，依照預設，在登錄中沒有 HTTP 配接器機碼，所以 HTTP 配接器會使用預設值。</span><span class="sxs-lookup"><span data-stu-id="c41c1-106">Note that by default there are no HTTP adapter keys in the registry, so the HTTP adapter uses the default settings.</span></span> <span data-ttu-id="c41c1-107">若有必要變更預設值，您必須在登錄的下列位置建立以下登錄機碼：</span><span class="sxs-lookup"><span data-stu-id="c41c1-107">If it is necessary to change the default settings, you need to create the following registry keys under the following locations in the registry:</span></span>  
  
-   <span data-ttu-id="c41c1-108">**DisableChunkEncoding**， **RequestQueueSize**，和**HttpReceiveThreadsPerCpu**必須定義在**碼BTSSvc.3.0\HttpReceive**。</span><span class="sxs-lookup"><span data-stu-id="c41c1-108">**DisableChunkEncoding**, **RequestQueueSize**, and **HttpReceiveThreadsPerCpu** must be defined in **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc.3.0\HttpReceive**.</span></span>  
  
-   <span data-ttu-id="c41c1-109">**HttpOutTimeoutInterval**， **HttpOutInflightSize**，和**HttpOutCompleteSize**必須定義在**碼BTSSvc {GUID}** 其中**GUID**是 HTTP 傳送處理常式主控件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c41c1-109">**HttpOutTimeoutInterval**, **HttpOutInflightSize**, and **HttpOutCompleteSize** must be defined in **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc{GUID}** where **GUID** is the ID of the host for the HTTP send handler.</span></span>  
  
|<span data-ttu-id="c41c1-110">機碼名稱</span><span class="sxs-lookup"><span data-stu-id="c41c1-110">Key name</span></span>|<span data-ttu-id="c41c1-111">類型</span><span class="sxs-lookup"><span data-stu-id="c41c1-111">Type</span></span>|<span data-ttu-id="c41c1-112">預設值</span><span class="sxs-lookup"><span data-stu-id="c41c1-112">Default</span></span>|<span data-ttu-id="c41c1-113">說明</span><span class="sxs-lookup"><span data-stu-id="c41c1-113">Explanation</span></span>|  
|--------------|----------|-------------|-----------------|  
|<span data-ttu-id="c41c1-114">**DisableChunkEncoding**</span><span class="sxs-lookup"><span data-stu-id="c41c1-114">**DisableChunkEncoding**</span></span>|<span data-ttu-id="c41c1-115">DWORD</span><span class="sxs-lookup"><span data-stu-id="c41c1-115">DWORD</span></span>|<span data-ttu-id="c41c1-116">0</span><span class="sxs-lookup"><span data-stu-id="c41c1-116">0</span></span>|<span data-ttu-id="c41c1-117">控制 HTTP 接收配接器在傳送回應給用戶端時是否使用區塊編碼。</span><span class="sxs-lookup"><span data-stu-id="c41c1-117">Regulates whether or not the HTTP receive adapter uses chunked encoding when sending responses back to the client.</span></span><br /><br /> <span data-ttu-id="c41c1-118">設成非零值以關閉 HTTP 接收配接器回應的區塊編碼。</span><span class="sxs-lookup"><span data-stu-id="c41c1-118">Set to a nonzero value to turn off chunked encoding for HTTP receive adapter responses.</span></span><br /><br /> <span data-ttu-id="c41c1-119">**最小值：** 0</span><span class="sxs-lookup"><span data-stu-id="c41c1-119">**Minimum value:** 0</span></span><br /><br /> <span data-ttu-id="c41c1-120">**最大值：** 任何非零值</span><span class="sxs-lookup"><span data-stu-id="c41c1-120">**Maximum value:** Any nonzero value</span></span>|  
|<span data-ttu-id="c41c1-121">**Requestqueuesize 機**</span><span class="sxs-lookup"><span data-stu-id="c41c1-121">**RequestQueueSize**</span></span>|<span data-ttu-id="c41c1-122">DWORD</span><span class="sxs-lookup"><span data-stu-id="c41c1-122">DWORD</span></span>|<span data-ttu-id="c41c1-123">256</span><span class="sxs-lookup"><span data-stu-id="c41c1-123">256</span></span>|<span data-ttu-id="c41c1-124">定義 HTTP 接收配接器一次處理的並行要求數目。</span><span class="sxs-lookup"><span data-stu-id="c41c1-124">Defines the number of concurrent requests that the HTTP receive adapter processes at one time.</span></span><br /><br /> <span data-ttu-id="c41c1-125">**最小值：** 10</span><span class="sxs-lookup"><span data-stu-id="c41c1-125">**Minimum value:**  10</span></span><br /><br /> <span data-ttu-id="c41c1-126">**最大值：** 2048年</span><span class="sxs-lookup"><span data-stu-id="c41c1-126">**Maximum value:** 2048</span></span>|  
|<span data-ttu-id="c41c1-127">**Httpreceivethreadspercpu 機**</span><span class="sxs-lookup"><span data-stu-id="c41c1-127">**HttpReceiveThreadsPerCpu**</span></span>|<span data-ttu-id="c41c1-128">DWORD</span><span class="sxs-lookup"><span data-stu-id="c41c1-128">DWORD</span></span>|<span data-ttu-id="c41c1-129">2</span><span class="sxs-lookup"><span data-stu-id="c41c1-129">2</span></span>|<span data-ttu-id="c41c1-130">定義配置給 HTTP 接收配接器的每個 CPU 的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="c41c1-130">Defines the number of threads per CPU that are allocated to the HTTP receive adapter.</span></span><br /><br /> <span data-ttu-id="c41c1-131">**最小值：** 1</span><span class="sxs-lookup"><span data-stu-id="c41c1-131">**Minimum value:** 1</span></span><br /><br /> <span data-ttu-id="c41c1-132">**最大值：** 10</span><span class="sxs-lookup"><span data-stu-id="c41c1-132">**Maximum value:** 10</span></span>|  
|<span data-ttu-id="c41c1-133">**HttpOutTimeoutInterval**</span><span class="sxs-lookup"><span data-stu-id="c41c1-133">**HttpOutTimeoutInterval**</span></span>|<span data-ttu-id="c41c1-134">DWORD</span><span class="sxs-lookup"><span data-stu-id="c41c1-134">DWORD</span></span>|<span data-ttu-id="c41c1-135">2000</span><span class="sxs-lookup"><span data-stu-id="c41c1-135">2000</span></span>|<span data-ttu-id="c41c1-136">定義 HTTP 傳送配接器在逾時前等候的間隔 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="c41c1-136">Defines the interval in seconds that the HTTP send adapter will wait before timing out.</span></span><br /><br /> <span data-ttu-id="c41c1-137">**最小值：** 500</span><span class="sxs-lookup"><span data-stu-id="c41c1-137">**Minimum value:** 500</span></span><br /><br /> <span data-ttu-id="c41c1-138">**最大值：** 10000000</span><span class="sxs-lookup"><span data-stu-id="c41c1-138">**Maximum value:** 10000000</span></span>|  
|<span data-ttu-id="c41c1-139">**HttpOutInflightSize**</span><span class="sxs-lookup"><span data-stu-id="c41c1-139">**HttpOutInflightSize**</span></span>|<span data-ttu-id="c41c1-140">DWORD</span><span class="sxs-lookup"><span data-stu-id="c41c1-140">DWORD</span></span>|<span data-ttu-id="c41c1-141">100</span><span class="sxs-lookup"><span data-stu-id="c41c1-141">100</span></span>|<span data-ttu-id="c41c1-142">這是 BizTalk Server HTTP 傳送配接器執行個體將處理的並行 HTTP 要求數目上限。</span><span class="sxs-lookup"><span data-stu-id="c41c1-142">This is the maximum number of concurrent HTTP requests that BizTalk Server HTTP send adapter instance will handle.</span></span><br /><br /> <span data-ttu-id="c41c1-143">建議的延遲值是介於 3 到 5 倍， **maxconnection**組態檔項目，如下所示。</span><span class="sxs-lookup"><span data-stu-id="c41c1-143">The recommended value for latency is between 3 to 5 times that of the **maxconnection** configuration file entry discussed below.</span></span><br /><br /> <span data-ttu-id="c41c1-144">**最小值：** 1</span><span class="sxs-lookup"><span data-stu-id="c41c1-144">**Minimum value:** 1</span></span><br /><br /> <span data-ttu-id="c41c1-145">**最大值：** 1024年</span><span class="sxs-lookup"><span data-stu-id="c41c1-145">**Maximum value:** 1024</span></span>|  
|<span data-ttu-id="c41c1-146">**HttpOutCompleteSize**</span><span class="sxs-lookup"><span data-stu-id="c41c1-146">**HttpOutCompleteSize**</span></span>|<span data-ttu-id="c41c1-147">DWORD</span><span class="sxs-lookup"><span data-stu-id="c41c1-147">DWORD</span></span>|<span data-ttu-id="c41c1-148">5</span><span class="sxs-lookup"><span data-stu-id="c41c1-148">5</span></span>|<span data-ttu-id="c41c1-149">控制 HTTP 傳送配接器傳回的訊息批次大小。</span><span class="sxs-lookup"><span data-stu-id="c41c1-149">Controls the size of the batch of messages that is returned from the HTTP send adapter.</span></span> <span data-ttu-id="c41c1-150">如果緩衝區未滿，而且有待處理的回應配接器將會等候 1 秒，直到它會認可批次。</span><span class="sxs-lookup"><span data-stu-id="c41c1-150">If the buffer is not full and there are outstanding responses then the adapter will wait for 1 second until it commits the batch.</span></span>  <span data-ttu-id="c41c1-151">低延遲案例這應該設定為 1，以允許配接器立即傳送回應訊息到 messagebox 進行處理。</span><span class="sxs-lookup"><span data-stu-id="c41c1-151">For low-latency scenarios this should be set to 1 which will allow the adapter to send response messages immediately to the message box for processing.</span></span><br /><br /> <span data-ttu-id="c41c1-152">**最小值：** 1</span><span class="sxs-lookup"><span data-stu-id="c41c1-152">**Minimum value:** 1</span></span><br /><br /> <span data-ttu-id="c41c1-153">**最大值：** 1024年</span><span class="sxs-lookup"><span data-stu-id="c41c1-153">**Maximum value:** 1024</span></span>|  
  
 <span data-ttu-id="c41c1-154">**組態檔項目來管理 HTTP 傳送配接器對特定目的地伺服器的同時連線數**</span><span class="sxs-lookup"><span data-stu-id="c41c1-154">**Configuration File Entry to Govern the Number of Concurrent Connections Made by the HTTP Send Adapter to a Particular Destination Server**</span></span>  
  
 <span data-ttu-id="c41c1-155">您可透過在根 BizTalk Server 安裝目錄的 BTSNTSvc.exe 組態檔建立一個項目，以設定 HTTP 配接器為特定目的地伺服器開啟的並行連線數目。</span><span class="sxs-lookup"><span data-stu-id="c41c1-155">The number of concurrent connections that the HTTP adapter opens for a particular destination server can be configured by making an entry in the BTSNTSvc.exe.config file that is located in the root BizTalk Server installation directory.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c41c1-156">若 HTTP 和 SOAP 配接器傳送訊息至相同的目的地 HTTP 伺服器，此屬性就會套用至 HTTP 和 SOAP 配接器。</span><span class="sxs-lookup"><span data-stu-id="c41c1-156">This property will be applied to both HTTP and SOAP adapters if they send messages to the same destination HTTP server.</span></span> <span data-ttu-id="c41c1-157">“maxconnnection”屬性的預設值為 2，可為所有 URI 的“maxconnection”屬性設定的最大值為 20。</span><span class="sxs-lookup"><span data-stu-id="c41c1-157">The default value for the “maxconnnection” property is 2, the maximum value that can be set for the “maxconnection” property for all URIs is 20.</span></span>  
  
 <span data-ttu-id="c41c1-158">下列是連線上限屬性的組態範例。</span><span class="sxs-lookup"><span data-stu-id="c41c1-158">The following is an example of the configuration for the maximum connections property:</span></span>  
  
```  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address = "http://www.contoso.com" maxconnection = "20" />  
      <add address = "http://www.northwind.com" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c41c1-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c41c1-159">See Also</span></span>  
 [<span data-ttu-id="c41c1-160">設定 HTTP 配接器</span><span class="sxs-lookup"><span data-stu-id="c41c1-160">Configuring the HTTP Adapter</span></span>](../core/configuring-the-http-adapter.md)