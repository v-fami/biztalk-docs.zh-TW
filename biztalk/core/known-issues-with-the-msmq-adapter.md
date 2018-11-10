---
title: MSMQ 配接器的已知問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ce77cdac-79c1-4529-8f09-0fb1f87ca037
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4accec1f9bed8ade9270e0c33e868e55c6a21942
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50752558"
---
# <a name="known-issues-with-the-msmq-adapter"></a><span data-ttu-id="c88c3-102">MSMQ 配接器的已知問題</span><span class="sxs-lookup"><span data-stu-id="c88c3-102">Known Issues with the MSMQ Adapter</span></span>
<span data-ttu-id="c88c3-103">本節包含可幫助您避免錯誤的資訊。</span><span class="sxs-lookup"><span data-stu-id="c88c3-103">This section contains information that may help you avoid errors.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="c88c3-104">已知問題</span><span class="sxs-lookup"><span data-stu-id="c88c3-104">Known Issues</span></span>  
  
#### <a name="msmq-adapter-receive-locations-do-not-process-documents"></a><span data-ttu-id="c88c3-105">MSMQ 配接器接收位置無法處理文件</span><span class="sxs-lookup"><span data-stu-id="c88c3-105">MSMQ Adapter receive locations do not process documents</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="c88c3-106">問題</span><span class="sxs-lookup"><span data-stu-id="c88c3-106">Problem</span></span>  
 <span data-ttu-id="c88c3-107">MSMQ 配接器接收位置無法處理文件。</span><span class="sxs-lookup"><span data-stu-id="c88c3-107">MSMQ Adapter receive locations will not process documents.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="c88c3-108">原因</span><span class="sxs-lookup"><span data-stu-id="c88c3-108">Cause</span></span>  
 <span data-ttu-id="c88c3-109">如果與執行 MSMQ 配接器接收處理常式之 BizTalk 主控件執行個體關聯的 .NET 執行緒集區中沒有足夠的可用執行緒，MSMQ 配接器接收位置就會因為執行緒嚴重短缺而無法處理文件。</span><span class="sxs-lookup"><span data-stu-id="c88c3-109">If there are insufficient threads available in the .NET thread pool associated with the BizTalk host instance that the MSMQ adapter receive handler is running in then MSMQ Adapter receive locations are unable to process documents due to thread starvation.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="c88c3-110">解決方案</span><span class="sxs-lookup"><span data-stu-id="c88c3-110">Resolution</span></span>  
 <span data-ttu-id="c88c3-111">若要增加主控件執行個體的.NET 執行緒集區中可用執行緒數目，請遵循**主控件的 CLR 裝載執行緒值**主題的章節[組態參數會影響配接器效能](../core/configuration-parameters-that-affect-adapter-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="c88c3-111">To increase the number of available threads in the .NET thread pool for the host instance, follow the steps in the **CLR Hosting thread values for the host** section of the topic [Configuration Parameters that Affect Adapter Performance](../core/configuration-parameters-that-affect-adapter-performance.md).</span></span>  
  
 <span data-ttu-id="c88c3-112">因為每個 MSMQ 接收位置繫結至 MSMQ 接收處理常式需要來自.NET 執行緒集區，設定**MinIOThreads**並**MinWorkerThreads**的值大於或等於MSMQ 接收位置數目繫結至的接收處理常式。</span><span class="sxs-lookup"><span data-stu-id="c88c3-112">Because each MSMQ receive location that is bound to an MSMQ receive handler requires a thread from the .NET thread pool, set **MinIOThreads** and **MinWorkerThreads** to a value that is greater than or equal to the number of MSMQ receive locations bound to the receive handler.</span></span> <span data-ttu-id="c88c3-113">因此，設定的值**MaxIOThreads**和**MaxWorkerThreads**等於 MSMQ 的數字的值繫結接收位置的接收處理常式\*2 的空餘空間：</span><span class="sxs-lookup"><span data-stu-id="c88c3-113">Accordingly, set the value for **MaxIOThreads** and **MaxWorkerThreads** to a value equal to the number of MSMQ receive locations bound to the receive handler \* 2 to allow for headroom:</span></span>  
  
|<span data-ttu-id="c88c3-114">DWORD 項目</span><span class="sxs-lookup"><span data-stu-id="c88c3-114">DWORD Entry</span></span>|<span data-ttu-id="c88c3-115">建議值</span><span class="sxs-lookup"><span data-stu-id="c88c3-115">Recommended value</span></span>|  
|-----------------|-----------------------|  
|<span data-ttu-id="c88c3-116">MaxIOThreads</span><span class="sxs-lookup"><span data-stu-id="c88c3-116">MaxIOThreads</span></span>|<span data-ttu-id="c88c3-117">數目 MSMQ 接收位置繫結至 MSMQ 配接器接收處理常式\*2。</span><span class="sxs-lookup"><span data-stu-id="c88c3-117">Number of MSMQ receive locations bound to the MSMQ adapter receive handler \* 2.</span></span>|  
|<span data-ttu-id="c88c3-118">MaxWorkerThreads</span><span class="sxs-lookup"><span data-stu-id="c88c3-118">MaxWorkerThreads</span></span>|<span data-ttu-id="c88c3-119">數目 MSMQ 接收位置繫結至 MSMQ 配接器接收處理常式\*2。</span><span class="sxs-lookup"><span data-stu-id="c88c3-119">Number of MSMQ receive locations bound to the MSMQ adapter receive handler \* 2.</span></span>|  
|<span data-ttu-id="c88c3-120">MinIOThreads</span><span class="sxs-lookup"><span data-stu-id="c88c3-120">MinIOThreads</span></span>|<span data-ttu-id="c88c3-121">MSMQ 配接器接收處理常式所繫結之 MSMQ 接收位置的數目。</span><span class="sxs-lookup"><span data-stu-id="c88c3-121">Number of MSMQ receive locations bound to the MSMQ adapter receive handler.</span></span>|  
|<span data-ttu-id="c88c3-122">MinWorkerThreads</span><span class="sxs-lookup"><span data-stu-id="c88c3-122">MinWorkerThreads</span></span>|<span data-ttu-id="c88c3-123">MSMQ 配接器接收處理常式所繫結之 MSMQ 接收位置的數目。</span><span class="sxs-lookup"><span data-stu-id="c88c3-123">Number of MSMQ receive locations bound to the MSMQ adapter receive handler.</span></span>|  
  
 <span data-ttu-id="c88c3-124">這些建議值不會將其他配接器處理常式或主控件執行個體中執行的協調流程所使用的執行緒當做因子，因此，值應該隨之增加。</span><span class="sxs-lookup"><span data-stu-id="c88c3-124">These recommended values do not factor in the threads used by other adapter handlers or orchestrations running in the host instance so the values should be increased accordingly.</span></span>  
  
#### <a name="msmq-adapter-receive-locations-shut-down-shortly-after-they-are-enabled"></a><span data-ttu-id="c88c3-125">MSMQ 配接器接收位置在啟用後很快就關閉</span><span class="sxs-lookup"><span data-stu-id="c88c3-125">MSMQ Adapter receive locations shut down shortly after they are enabled</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="c88c3-126">問題</span><span class="sxs-lookup"><span data-stu-id="c88c3-126">Problem</span></span>  
 <span data-ttu-id="c88c3-127">MSMQ 接收位置在啟用後很快就關閉。</span><span class="sxs-lookup"><span data-stu-id="c88c3-127">MSMQ receive locations shut down shortly after they are enabled.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="c88c3-128">原因</span><span class="sxs-lookup"><span data-stu-id="c88c3-128">Cause</span></span>  
 <span data-ttu-id="c88c3-129">如果 MSMQ 接收處理常式的主控件執行個體執行所在的相同電腦上，未執行訊息佇列服務的本機非叢集執行個體，就可能會發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="c88c3-129">This problem can occur if a local non-clustered instance of the Message Queuing service is not running on the same computer that the host instance for the MSMQ receive handler is running on.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="c88c3-130">解決方案</span><span class="sxs-lookup"><span data-stu-id="c88c3-130">Resolution</span></span>  
 <span data-ttu-id="c88c3-131">在 MSMQ 接收處理常式的主控件執行個體執行所在的電腦上，啟動訊息佇列服務。</span><span class="sxs-lookup"><span data-stu-id="c88c3-131">Start the Message Queuing service on the computer that the host instance for the MSMQ receive handler is running on.</span></span> <span data-ttu-id="c88c3-132">使用 MSMQ 配接器接收處理常式時，電腦上必須已在執行訊息佇列服務的本機執行個體，即使該電腦上已有該服務的叢集執行個體在執行中。</span><span class="sxs-lookup"><span data-stu-id="c88c3-132">The MSMQ adapter receive handler requires that a local instance of the Message Queuing service is running even if a clustered instance of the Message Queuing service is running on the same computer.</span></span>  
  
#### <a name="sc-tool-causes-error-when-attempting-to-stop-service-for-host-instance"></a><span data-ttu-id="c88c3-133">SC 工具在嘗試停止主控件執行個體的服務時導致錯誤</span><span class="sxs-lookup"><span data-stu-id="c88c3-133">SC tool causes error when attempting to stop service for host instance</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="c88c3-134">問題</span><span class="sxs-lookup"><span data-stu-id="c88c3-134">Problem</span></span>  
 <span data-ttu-id="c88c3-135">當您嘗試使用 SC 工具 (Sc.exe) 關閉 BizTalk 主控件執行個體的服務時，可能會收到如下錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="c88c3-135">When you try to use the SC tool (Sc.exe) to shut down the service for the BizTalk host instance, you may receive an error message that resembles the following:</span></span>  
  
 <span data-ttu-id="c88c3-136">**ControlService FAILED 1053:**</span><span class="sxs-lookup"><span data-stu-id="c88c3-136">**ControlService FAILED 1053:**</span></span>  
  
 <span data-ttu-id="c88c3-137">**服務未啟動或控制要求及時回應。**</span><span class="sxs-lookup"><span data-stu-id="c88c3-137">**The service did not respond to the start or control request in a timely fashion.**</span></span>  
  
 <span data-ttu-id="c88c3-138">當您收到此錯誤訊息後，BizTalk 主控件執行個體的服務即會停止。</span><span class="sxs-lookup"><span data-stu-id="c88c3-138">After you receive this error message, the service for the BizTalk host instance is stopped.</span></span> <span data-ttu-id="c88c3-139">但 SC 工具可能需要兩分鐘或更久的時間來關閉服務。</span><span class="sxs-lookup"><span data-stu-id="c88c3-139">However, the SC tool may need two minutes or more to shut down the service.</span></span>  
  
 <span data-ttu-id="c88c3-140">當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中已啟用 Microsoft Message Queuing 接收位置時，就會發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="c88c3-140">This problem occurs when a Microsoft Message Queuing receive location is enabled in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="c88c3-141">此外，系統記錄檔中也可能會記錄如下的錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="c88c3-141">Additionally, an error message that resembles the following may be logged in the System log:</span></span>  
  
 <span data-ttu-id="c88c3-142">**事件類型： 錯誤**</span><span class="sxs-lookup"><span data-stu-id="c88c3-142">**Event Type: Error**</span></span>  
  
 <span data-ttu-id="c88c3-143">**事件來源： 服務控制管理員**</span><span class="sxs-lookup"><span data-stu-id="c88c3-143">**Event Source: Service Control Manager**</span></span>  
  
 <span data-ttu-id="c88c3-144">**事件類別目錄： 無**</span><span class="sxs-lookup"><span data-stu-id="c88c3-144">**Event Category: None**</span></span>  
  
 <span data-ttu-id="c88c3-145">**事件識別碼： 7011**</span><span class="sxs-lookup"><span data-stu-id="c88c3-145">**Event ID: 7011**</span></span>  
  
 <span data-ttu-id="c88c3-146">**描述：**</span><span class="sxs-lookup"><span data-stu-id="c88c3-146">**Description:**</span></span>  
  
 <span data-ttu-id="c88c3-147">**逾時 （30000 毫秒） 等候來自 BTSSvc$ BizTalkServerApplication 服務的交易回應。**</span><span class="sxs-lookup"><span data-stu-id="c88c3-147">**Timeout (30000 milliseconds) waiting for a transaction response from the BTSSvc$BizTalkServerApplication service.**</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="c88c3-148">解決方案</span><span class="sxs-lookup"><span data-stu-id="c88c3-148">Resolution</span></span>  
 <span data-ttu-id="c88c3-149">Microsoft 已提供支援的 Hotfix。</span><span class="sxs-lookup"><span data-stu-id="c88c3-149">A supported hotfix is now available from Microsoft.</span></span> <span data-ttu-id="c88c3-150">但此 Hotfix 僅適用於更正本文所說明的問題。</span><span class="sxs-lookup"><span data-stu-id="c88c3-150">However, this hotfix is intended to correct only the problem that is described in this article.</span></span> <span data-ttu-id="c88c3-151">只將此 Hotfix 套用在發生此特定問題的系統。</span><span class="sxs-lookup"><span data-stu-id="c88c3-151">Apply this hotfix only to systems that are experiencing this specific problem.</span></span> <span data-ttu-id="c88c3-152">此 Hotfix 可能還會接受其他測試。</span><span class="sxs-lookup"><span data-stu-id="c88c3-152">This hotfix might receive additional testing.</span></span> <span data-ttu-id="c88c3-153">因此，如果此問題對您的影響不大，建議您靜待內含此 Hotfix 的下一個 Service Pack 推出。</span><span class="sxs-lookup"><span data-stu-id="c88c3-153">Therefore, if you are not severely affected by this problem, we recommend that you wait for the next service pack that contains this hotfix.</span></span>  
  
 <span data-ttu-id="c88c3-154">若要解決此問題，請提交要求至 Microsoft Online Customer Services 以取得此 Hotfix。</span><span class="sxs-lookup"><span data-stu-id="c88c3-154">To resolve this problem, submit a request to Microsoft Online Customer Services to obtain the hotfix.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c88c3-155">若有其他問題發生，或需要其他方面的疑難排解，您可以建立個別的服務要求。</span><span class="sxs-lookup"><span data-stu-id="c88c3-155">If additional issues occur or any troubleshooting is required, you might have to create a separate service request.</span></span> <span data-ttu-id="c88c3-156">其他不是此 Hotfix 要解決的支援問題，將酌收適當的支援費用。</span><span class="sxs-lookup"><span data-stu-id="c88c3-156">The usual support costs will apply to additional support questions and issues that do not qualify for this specific hotfix.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c88c3-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c88c3-157">See Also</span></span>  
 [<span data-ttu-id="c88c3-158">MSMQ 配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="c88c3-158">Troubleshooting the MSMQ Adapter</span></span>](../core/troubleshooting-the-msmq-adapter.md)