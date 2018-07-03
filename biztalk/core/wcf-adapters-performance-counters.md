---
title: WCF 配接器效能計數器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance, WCF adapters
- performance, performance counters
- WCF adapters, performance
ms.assetid: 9feb052f-5674-419f-84ab-9b5d312a04a5
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5b916b6212da18dcf4aa48d4ca941e23413513d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37016249"
---
# <a name="wcf-adapters-performance-counters"></a><span data-ttu-id="bed08-102">WCF 配接器效能計數器</span><span class="sxs-lookup"><span data-stu-id="bed08-102">WCF Adapters Performance Counters</span></span>
<span data-ttu-id="bed08-103">效能計數器可讓您針對服務在網站或系統上所執行的工作，監控其特定層面。</span><span class="sxs-lookup"><span data-stu-id="bed08-103">Performance counters enable you to monitor specific aspects of work performed on the site or system by a service.</span></span> <span data-ttu-id="bed08-104">效能計數器也可以幫助您識別和疑難排解伺服器的效能問題。</span><span class="sxs-lookup"><span data-stu-id="bed08-104">Performance counters can help you identify and troubleshoot server performance issues.</span></span> <span data-ttu-id="bed08-105">WCF 配接器本身並未提供效能計數器。</span><span class="sxs-lookup"><span data-stu-id="bed08-105">The WCF adapters do not provide their own performance counters.</span></span> <span data-ttu-id="bed08-106">然而，監控 Windows Communication Foundation (WCF) 的效能計數器，即可量測 WCF 接收位置的效能。</span><span class="sxs-lookup"><span data-stu-id="bed08-106">However, you can monitor the performance counters of Windows Communication Foundation (WCF) to gauge the performance of the WCF receive locations.</span></span> <span data-ttu-id="bed08-107">若要針對 WCF 接收位置使用 WCF 效能計數器，您必須為執行接收位置之主控件執行個體啟用效能計數器。</span><span class="sxs-lookup"><span data-stu-id="bed08-107">To use the WCF performance counters for the WCF receive locations, you have to enable the performance counters for the host instances running the receive locations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bed08-108">WCF 傳送埠無法使用 WCF 效能計數器。</span><span class="sxs-lookup"><span data-stu-id="bed08-108">The WCF performance counters are not available for WCF send ports.</span></span>  
  
 <span data-ttu-id="bed08-109">對於內含式 WCF 配接器，您可以透過 BTSNTSvc.exe.config 檔案啟用效能計數器。</span><span class="sxs-lookup"><span data-stu-id="bed08-109">For the in-process WCF adapters, you can enable the performance counters through the BTSNTSvc.exe.config file.</span></span> <span data-ttu-id="bed08-110">若為外掛式 WCF 配接器，則可以修改 Web.config 檔案來啟用效能計數器。</span><span class="sxs-lookup"><span data-stu-id="bed08-110">For the isolated WCF adapters, you can modify the Web.config file to enable the performance counters.</span></span> <span data-ttu-id="bed08-111">WCF 效能計數器的詳細資訊，請參閱 < WCF 效能計數器 」，網址[ http://go.microsoft.com/fwlink/?LinkID=87245 ](http://go.microsoft.com/fwlink/?LinkID=87245)。</span><span class="sxs-lookup"><span data-stu-id="bed08-111">For more information about the WCF performance counters, see "WCF Performance Counters" at [http://go.microsoft.com/fwlink/?LinkID=87245](http://go.microsoft.com/fwlink/?LinkID=87245).</span></span>  
  
## <a name="enabling-the-wcf-performance-counters-for-the-wcf-receive-locations"></a><span data-ttu-id="bed08-112">為 WCF 接收位置啟用 WCF 效能計數器</span><span class="sxs-lookup"><span data-stu-id="bed08-112">Enabling the WCF Performance Counters for the WCF Receive Locations</span></span>  
 <span data-ttu-id="bed08-113">對於內含式 WCF 配接器，您可以透過 BTSNTSvc.exe.config 檔案啟用效能計數器。</span><span class="sxs-lookup"><span data-stu-id="bed08-113">For the in-process WCF adapters, you can enable the performance counters through the BTSNTSvc.exe.config file.</span></span>  
  
 <span data-ttu-id="bed08-114">若為外掛式 WCF 配接器，您可以修改 Web.config 檔案 (「BizTalk WCF 服務發佈精靈」在 Web 應用程式資料夾中建立的檔案) 來啟用 WCF 追蹤</span><span class="sxs-lookup"><span data-stu-id="bed08-114">For the isolated WCF adapters, you can enable WCF tracing by modifying the Web.config file that the BizTalk WCF Service Publishing Wizard creates in the Web application folder</span></span>  
  
 <span data-ttu-id="bed08-115">若要修改 BTSNtSvc.exe.config 或 Web.config，請開啟組態檔並設定 WCF 追蹤，如以下組態範例所示：</span><span class="sxs-lookup"><span data-stu-id="bed08-115">To modify BTSNtSvc.exe.config or Web.config, open the configuration file, and then configure WCF tracing, as indicated in the following configuration example:</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bed08-116">BTSNTSvc.exe.config 永遠與 BTSNTSvc.exe 檔案位於相同的目錄中，此目錄通常是 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bed08-116">The BTSNTSvc.exe.config file is always located in the same directory as the BTSNTSvc.exe file, which is usually [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span></span>  
  
```  
<configuration>  
 <system.serviceModel>  
 <diagnostics performanceCounters="All" />  
 </system.serviceModel>  
 </configuration>  
```  
  
 <span data-ttu-id="bed08-117">**PerformanceCounters**屬性可以設定以啟用特定類型的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="bed08-117">The **performanceCounters** attribute can be set to enable a specific type of performance counters.</span></span> <span data-ttu-id="bed08-118">有效值如下：</span><span class="sxs-lookup"><span data-stu-id="bed08-118">Valid values are</span></span>  
  
- <span data-ttu-id="bed08-119">**所有**： 所有類別的計數器 (**ServiceModelService**， **ServiceModelEndpoint**，和**ServiceModelOperation**) 會啟用。</span><span class="sxs-lookup"><span data-stu-id="bed08-119">**All**: All category counters (**ServiceModelService**, **ServiceModelEndpoint**, and **ServiceModelOperation**) are enabled.</span></span>  
  
- <span data-ttu-id="bed08-120">**ServiceOnly**： 僅**ServiceModelService**類別的計數器會啟用。</span><span class="sxs-lookup"><span data-stu-id="bed08-120">**ServiceOnly**: Only **ServiceModelService** category counters are enabled.</span></span>  
  
- <span data-ttu-id="bed08-121">**關閉**: ServiceModel \* 效能計數器已停用。</span><span class="sxs-lookup"><span data-stu-id="bed08-121">**Off**: ServiceModel\* performance counters are disabled.</span></span> <span data-ttu-id="bed08-122">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="bed08-122">This is the default value.</span></span>  
  
  <span data-ttu-id="bed08-123">修改 BTSNTSvc.exe.config 檔案後，您必須重新啟動執行內含式 WCF 接收位置的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="bed08-123">After modifying the BTSNTSvc.exe.config file, you must restart the host instances running the in-process WCF receive locations.</span></span>  
  
## <a name="types-of-performance-counters"></a><span data-ttu-id="bed08-124">效能計數器型別</span><span class="sxs-lookup"><span data-stu-id="bed08-124">Types of Performance Counters</span></span>  
 <span data-ttu-id="bed08-125">WCF 效能計數器分為三種不同的層級： 服務、 端點和作業。</span><span class="sxs-lookup"><span data-stu-id="bed08-125">WCF performance counters are scoped to three different levels: service, endpoint, and operation.</span></span>  
  
 <span data-ttu-id="bed08-126">**服務效能計數器**</span><span class="sxs-lookup"><span data-stu-id="bed08-126">**Service performance counters**</span></span>  
  
 <span data-ttu-id="bed08-127">服務效能計數器會以整體的方式測量服務行為，而且可用來診斷整個服務的效能。</span><span class="sxs-lookup"><span data-stu-id="bed08-127">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="bed08-128">下找到它們**ServiceModelService 3.0.0.0**以效能監視器檢視時的效能物件。</span><span class="sxs-lookup"><span data-stu-id="bed08-128">They are found under the **ServiceModelService 3.0.0.0** performance object when viewing with Performance Monitor.</span></span> <span data-ttu-id="bed08-129">執行個體的命名模式如下：</span><span class="sxs-lookup"><span data-stu-id="bed08-129">The instances are named using the following pattern:</span></span>  
  
```  
biztalkserviceinstance@<URI of a receive location>  
```  
  
 <span data-ttu-id="bed08-130">由於 WCF 配接器會為各接收位置建立個別的服務，因此也會為每個接收位置建立效能計數器執行個體。</span><span class="sxs-lookup"><span data-stu-id="bed08-130">Because the WCF adapters create a separate service host for each receive location, a performance counter instance is created for each receive location.</span></span> <span data-ttu-id="bed08-131">如需有關服務類別實作 WCF 服務合約，請參閱 < **BizTalkServiceInstance 類別** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="bed08-131">For more information about the service class implementing the WCF service contracts, see the **BizTalkServiceInstance Class** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span> 
  
 <span data-ttu-id="bed08-132">**端點效能計數器**</span><span class="sxs-lookup"><span data-stu-id="bed08-132">**Endpoint performance counters**</span></span>  
  
 <span data-ttu-id="bed08-133">端點效能計數器可讓您檢視反映端點如何接收訊息的資料。</span><span class="sxs-lookup"><span data-stu-id="bed08-133">Endpoint performance counters enable you to look at data reflecting how an endpoint is accepting messages.</span></span> <span data-ttu-id="bed08-134">下找到它們**ServiceModelEndpoint 3.0.0.0**以效能監視器檢視時的效能物件。</span><span class="sxs-lookup"><span data-stu-id="bed08-134">They are found under the **ServiceModelEndpoint 3.0.0.0** performance object when viewing with Performance Monitor.</span></span> <span data-ttu-id="bed08-135">執行個體的命名模式如下：</span><span class="sxs-lookup"><span data-stu-id="bed08-135">The instances are named using the following pattern:</span></span>  
  
```  
biztalkserviceinstance.<WCF service contract>@<URI of a receive location>  
```  
  
 <span data-ttu-id="bed08-136">會為每個接收位置建立一個效能計數器執行個體。</span><span class="sxs-lookup"><span data-stu-id="bed08-136">A performance counter instance is created for each receive location.</span></span> <span data-ttu-id="bed08-137">在前述的模式中，WCF 服務合約的名稱，代表 WCF 配接器選擇透過接收位置接收訊息的服務合約。</span><span class="sxs-lookup"><span data-stu-id="bed08-137">In the preceding pattern, the name of the WCF service contract represents the service contract that the WCF adapters choose to receive messages through the receive location.</span></span> <span data-ttu-id="bed08-138">如需有關 WCF 配接器從可用的 WCF 所選擇的服務合約的服務合約，請參閱 < **WCF 配接器服務合約參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="bed08-138">For more information about how the WCF adapters choose a service contract from the available WCF service contracts, see **WCF Adapters Service Contract Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>  
  
 <span data-ttu-id="bed08-139">**作業效能計數器**</span><span class="sxs-lookup"><span data-stu-id="bed08-139">**Operation performance counters**</span></span>  
  
 <span data-ttu-id="bed08-140">找到作業效能計數器**ServiceModelOperation 3.0.0.0**以效能監視器檢視時的效能物件。</span><span class="sxs-lookup"><span data-stu-id="bed08-140">Operation performance counters are found under the **ServiceModelOperation 3.0.0.0** performance object when viewing with Performance Monitor.</span></span> <span data-ttu-id="bed08-141">會為每個接收位置建立兩個效能計數器執行個體。</span><span class="sxs-lookup"><span data-stu-id="bed08-141">Two performance counter instances are created for each receive location.</span></span> <span data-ttu-id="bed08-142">其中一個物件執行個體的命名模式如下：</span><span class="sxs-lookup"><span data-stu-id="bed08-142">One of the object instances is named using the following pattern:</span></span>  
  
```  
biztalkserviceinstance.<WCF service contract>biztalksubmit@<URI of a receive location>  
```  
  
 <span data-ttu-id="bed08-143">在前述的模式中，WCF 服務合約的名稱，代表 WCF 配接器選擇透過接收位置接收訊息的服務合約。</span><span class="sxs-lookup"><span data-stu-id="bed08-143">In the preceding pattern, the name of the WCF service contract represents the service contract that the WCF adapters choose to receive messages through the receive location.</span></span> <span data-ttu-id="bed08-144">**biztalksubmit**是服務合約中宣告的作業名稱，並造成執行階段在中繼資料建立 WSDL 作業。</span><span class="sxs-lookup"><span data-stu-id="bed08-144">**biztalksubmit** is an operation name declared in the service contract, and causes the runtime to create WSDL operations in the metadata.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bed08-145">如需有關 WCF 配接器從可用的 WCF 所選擇的服務合約的服務合約，請參閱 < **WCF 配接器服務合約參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="bed08-145">For more information about how the WCF adapters choose a service contract from the available WCF service contracts, see **WCF Adapters Service Contract Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
 <span data-ttu-id="bed08-146">另外一個物件執行個體的命名模式如下：</span><span class="sxs-lookup"><span data-stu-id="bed08-146">The other object instance is named using the following pattern:</span></span>  
  
```  
biztalkserviceinstance.<WCF service contract><twowaymethod|onewaymethod>@<URI of a receive location>  
```  
  
 <span data-ttu-id="bed08-147">此效能計數器執行個體代表以非同步的方式處理透過接收位置內送之訊息的作業。</span><span class="sxs-lookup"><span data-stu-id="bed08-147">This performance counter instance represents the operation that asynchronously processes messages incoming through the receive location.</span></span> <span data-ttu-id="bed08-148">這個執行個體的作業名稱部分可以是**twowaymethod**或是**onewaymethod**視接收位置中所使用的 WCF 配接器類型而定。</span><span class="sxs-lookup"><span data-stu-id="bed08-148">The operation name part of this instance can be **twowaymethod** or **onewaymethod** depending on the type of WCF adapter used in the receive location.</span></span> <span data-ttu-id="bed08-149">如果您使用 Wcf-netmsmq 配接器執行個體擁有**onewaymethod**建立作業名稱。</span><span class="sxs-lookup"><span data-stu-id="bed08-149">If you use the WCF-NetMsmq adapter, an instance having the **onewaymethod** operation name is created.</span></span> <span data-ttu-id="bed08-150">為其他配接器， **twowaymethod**用於作業名稱部分。</span><span class="sxs-lookup"><span data-stu-id="bed08-150">For the other adapters, **twowaymethod** is used for the operation name part.</span></span>