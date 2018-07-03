---
title: SOAP 配接器的已知問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a3229d73-170d-42b7-bab9-12ae5f2d0fa7
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 273ebf62251050f6cb4aa8de9582aec9f475cbee
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018692"
---
# <a name="known-issues-with-the-soap-adapter"></a><span data-ttu-id="b5813-102">SOAP 配接器的已知問題</span><span class="sxs-lookup"><span data-stu-id="b5813-102">Known Issues with the SOAP Adapter</span></span>
<span data-ttu-id="b5813-103">本節包含可幫助您避免錯誤的資訊。</span><span class="sxs-lookup"><span data-stu-id="b5813-103">This section contains information that may help you avoid errors.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="b5813-104">已知問題</span><span class="sxs-lookup"><span data-stu-id="b5813-104">Known Issues</span></span>  
  
#### <a name="the-soap-adapter-experiences-poor-performance-or-generates-errors-under-load"></a><span data-ttu-id="b5813-105">SOAP 配接器在負載下遭遇效能不佳的情況，或產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="b5813-105">The SOAP Adapter experiences poor performance or generates errors under load</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="b5813-106">問題</span><span class="sxs-lookup"><span data-stu-id="b5813-106">Problem</span></span>  
 <span data-ttu-id="b5813-107">SOAP 配接器在負載下遭遇效能不佳的情況，或產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="b5813-107">The SOAP Adapter experiences poor performance or generates errors under load</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="b5813-108">原因</span><span class="sxs-lookup"><span data-stu-id="b5813-108">Cause</span></span>  
 <span data-ttu-id="b5813-109">這個問題發生的原因，是因為 SOAP 配接器或影響 SOAP 配接器之相依性元件的預設組態選項未針對負載下的效能進行微調。</span><span class="sxs-lookup"><span data-stu-id="b5813-109">This problem occurs because the default configuration options for the SOAP adapter or for dependency components that affect the SOAP adapter are not tuned for performance under load.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="b5813-110">解決方案</span><span class="sxs-lookup"><span data-stu-id="b5813-110">Resolution</span></span>  
 <span data-ttu-id="b5813-111">若要解決此問題，請修改 SOAP 配接器或相依性元件 > 主題所述的組態選項[組態參數會影響配接器效能的](../core/configuration-parameters-that-affect-adapter-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="b5813-111">To resolve this problem modify the configuration options for the SOAP adapter or for the dependency components described in the topic [Configuration Parameters that Affect Adapter Performance](../core/configuration-parameters-that-affect-adapter-performance.md).</span></span>  
  
#### <a name="the-mimesmime-encoder-and-decoder-pipeline-components-cannot-encode-and-decode-data-processed-by-the-soap-adapter"></a><span data-ttu-id="b5813-112">MIME/SMIME 編碼器和解碼器管線元件無法編碼和解碼 SOAP 配接器所處理的資料</span><span class="sxs-lookup"><span data-stu-id="b5813-112">The MIME/SMIME encoder and decoder pipeline components cannot encode and decode data processed by the SOAP adapter</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="b5813-113">問題</span><span class="sxs-lookup"><span data-stu-id="b5813-113">Problem</span></span>  
 <span data-ttu-id="b5813-114">MIME/SMIME 編碼器和解碼器管線元件無法編碼和解碼 SOAP 配接器所處理的資料</span><span class="sxs-lookup"><span data-stu-id="b5813-114">The MIME/SMIME encoder and decoder pipeline components cannot encode and decode data processed by the SOAP adapter</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="b5813-115">原因</span><span class="sxs-lookup"><span data-stu-id="b5813-115">Cause</span></span>  
 <span data-ttu-id="b5813-116">這個問題發生的原因，是因為 SOAP 配接器在程序的配接器階段組合和解譯了 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="b5813-116">This problem occurs because the SOAP adapter assembles and disassembles the SOAP messages in the adapter stage of the process.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="b5813-117">解決方案</span><span class="sxs-lookup"><span data-stu-id="b5813-117">Resolution</span></span>  
 <span data-ttu-id="b5813-118">若要解決這個問題，請使用安全通訊端層 (SSL) 確保通訊安全，以編碼 SOAP 配接器處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="b5813-118">To resolve this problem, Use Secure Sockets Layer (SSL) to secure communications to encode messages processed by the SOAP adapter.</span></span> <span data-ttu-id="b5813-119">在傳送端，使用**用戶端憑證指紋**來達到此目的 SOAP 配接器屬性頁中的屬性。</span><span class="sxs-lookup"><span data-stu-id="b5813-119">On the send side, use the **Client Certificate Thumbprint** property in the SOAP adapter properties page to achieve this.</span></span> <span data-ttu-id="b5813-120">在接收端，您必須設定裝載 BizTalk Web 服務的虛擬目錄，以取得安全的 SSL 通訊。</span><span class="sxs-lookup"><span data-stu-id="b5813-120">On the receive side, you must configure the virtual directory that hosts the BizTalk Web Service for SSL secure communications.</span></span>  
  
#### <a name="the-default-appdomain-hosting-the-soap-adapter-gets-unloaded-causing-the-host-process-to-hang"></a><span data-ttu-id="b5813-121">裝載 SOAP 配接器的預設 AppDomain 卸載，造成主控件處理序沒有反應</span><span class="sxs-lookup"><span data-stu-id="b5813-121">The default AppDomain hosting the SOAP adapter gets unloaded causing the host process to hang</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="b5813-122">問題</span><span class="sxs-lookup"><span data-stu-id="b5813-122">Problem</span></span>  
 <span data-ttu-id="b5813-123">裝載 SOAP 配接器的處理序沒有反應，造成此處理序中的所有其他 Web 服務也沒有反應。</span><span class="sxs-lookup"><span data-stu-id="b5813-123">The process hosting the SOAP adapter hangs, causing all other Web services in the process to hang.</span></span> <span data-ttu-id="b5813-124">這可能產生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="b5813-124">This may result in the following error:</span></span>  
  
 <span data-ttu-id="b5813-125">執行回應 （傳送） 管線失敗:"未知"來源:"未知"接收埠:: TwoWayLatencyLoopBack_RxPort"URI:"/ /twowaylatencyrxsoap/twowaylatencyws.asmx"原因： 嘗試存取已卸載的 AppDomain。</span><span class="sxs-lookup"><span data-stu-id="b5813-125">There was a failure executing the response(send) pipeline: "Unknown " Source: "Unknown " Receive Port: TwoWayLatencyLoopBack_RxPort" URI: "/TwoWayLatencyRxSOAP/TwoWayLatencyWS.asmx" Reason: Attempted to access an unloaded AppDomain.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="b5813-126">原因</span><span class="sxs-lookup"><span data-stu-id="b5813-126">Cause</span></span>  
 <span data-ttu-id="b5813-127">SOAP 配接器在 IIS 處理序空間中執行。</span><span class="sxs-lookup"><span data-stu-id="b5813-127">The SOAP adapter runs in the IIS process space.</span></span> <span data-ttu-id="b5813-128">如果 IIS AppPool 中有一個以上的 Web 服務存在，則每一個 Web 服務最後都會有它自己的 AppDomain。</span><span class="sxs-lookup"><span data-stu-id="b5813-128">If more than one Web service exists in the IIS AppPool, then every Web service ends up having its own AppDomain.</span></span>  
  
 <span data-ttu-id="b5813-129">根據預設，所有傳訊引擎物件會建立第一個 AppDomain 中 （亦即。</span><span class="sxs-lookup"><span data-stu-id="b5813-129">By default all messaging engine objects are created in the first AppDomain (that is,.</span></span> <span data-ttu-id="b5813-130">AppDomain 對應到第一個 Web 服務)。</span><span class="sxs-lookup"><span data-stu-id="b5813-130">the AppDomain corresponding to the first Web service).</span></span> <span data-ttu-id="b5813-131">如果第一個 Web 服務因為任何原因而停止作用一段時間，則 IIS 會卸載第一個 AppDomain。</span><span class="sxs-lookup"><span data-stu-id="b5813-131">If the first Web service is inactive for an extended period of time for any reason, IIS unloads the first AppDomain.</span></span> <span data-ttu-id="b5813-132">當發生這個情況時，裝載處理序中的所有服務都會無法使用。</span><span class="sxs-lookup"><span data-stu-id="b5813-132">When this happens, all services in the hosting process become unusable.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="b5813-133">解決方案</span><span class="sxs-lookup"><span data-stu-id="b5813-133">Resolution</span></span>  
 <span data-ttu-id="b5813-134">若要避免卸載 AppDomain，請遵循下列程序：</span><span class="sxs-lookup"><span data-stu-id="b5813-134">To prevent the AppDomain from being unloaded, follow the procedure below:</span></span>  
  
1. <span data-ttu-id="b5813-135">按一下 **開始**，指向**所有程式**，指向**Microsoft BizTalk Server**然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="b5813-135">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk Server** and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="b5813-136">在  **BizTalk Server 管理主控台**，展開**BizTalk Server 管理**，展開**BizTalk 群組**，展開 **平台設定**，然後按一下**主機**。</span><span class="sxs-lookup"><span data-stu-id="b5813-136">In **BizTalk Server Administration Console**, Expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then click **Hosts**.</span></span>  
  
3. <span data-ttu-id="b5813-137">從清單中的主機，以滑鼠右鍵按一下 必要的主機，然後**設定**。</span><span class="sxs-lookup"><span data-stu-id="b5813-137">From the list of Hosts, right-click the required host, and then click **Settings**.</span></span>  
  
4. <span data-ttu-id="b5813-138">在 [ **BizTalk 設定儀表板**，檢查**外掛式配接器的預設應用程式定義域**之下**一般**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b5813-138">In the **BizTalk Settings Dashboard**, check **Default application domain for isolated adapter** under **General** tab.</span></span>  
  
   <span data-ttu-id="b5813-139">當您這樣做時，會在預設 AppDomain 中建立 BizTalk 傳訊引擎物件，而不是在其自己的 AppDomain 中建立。</span><span class="sxs-lookup"><span data-stu-id="b5813-139">When you do this, the BizTalk Messaging Engine objects are created in the default AppDomain instead of in their own AppDomains.</span></span> <span data-ttu-id="b5813-140">因為預設 AppDomain 絕對不會卸載，所以此問題將不再發生。</span><span class="sxs-lookup"><span data-stu-id="b5813-140">Because the default AppDomain is never unloaded, the problem no longer occurs.</span></span>  
  
#### <a name="the-soap-adapter-fails-to-register"></a><span data-ttu-id="b5813-141">SOAP 配接器無法註冊</span><span class="sxs-lookup"><span data-stu-id="b5813-141">The SOAP Adapter fails to register</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="b5813-142">問題</span><span class="sxs-lookup"><span data-stu-id="b5813-142">Problem</span></span>  
 <span data-ttu-id="b5813-143">當 BizTalk Server 嘗試註冊 SOAP (或 HTTP) 配接器時，可能發生下列錯誤。</span><span class="sxs-lookup"><span data-stu-id="b5813-143">The following error may occur when BizTalk Server attempts to register the SOAP (or HTTP) adapter.</span></span>  
  
 <span data-ttu-id="b5813-144">"傳訊引擎無法註冊配接器 "SOAP"。</span><span class="sxs-lookup"><span data-stu-id="b5813-144">"The Messaging Engine failed to register an adapter "SOAP".</span></span> <span data-ttu-id="b5813-145">詳細資料: 「 註冊相同的程序中的多個配接器類型不支援的案例。</span><span class="sxs-lookup"><span data-stu-id="b5813-145">Details: "Registering multiple adapter types within the same process is not a supported scenario.</span></span> <span data-ttu-id="b5813-146">例如，HTTP 與 SOAP 接收配接器不能共存於相同的程序中"。</span><span class="sxs-lookup"><span data-stu-id="b5813-146">For e.g. HTTP and SOAP receive adapters cannot co-exist in the same process".</span></span>  
  
 <span data-ttu-id="b5813-147">或</span><span class="sxs-lookup"><span data-stu-id="b5813-147">Or</span></span>  
  
 <span data-ttu-id="b5813-148">"傳訊引擎無法註冊配接器 "HTTP"。</span><span class="sxs-lookup"><span data-stu-id="b5813-148">"The Messaging Engine failed to register an adapter "HTTP".</span></span> <span data-ttu-id="b5813-149">詳細資料: 「 註冊相同的程序中的多個配接器類型不支援的案例。</span><span class="sxs-lookup"><span data-stu-id="b5813-149">Details: "Registering multiple adapter types within the same process is not a supported scenario.</span></span>  <span data-ttu-id="b5813-150">例如，HTTP 與 SOAP 接收配接器不能共存於相同的程序中"。</span><span class="sxs-lookup"><span data-stu-id="b5813-150">For e.g. HTTP and SOAP receive adapters cannot co-exist in the same process".</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="b5813-151">原因</span><span class="sxs-lookup"><span data-stu-id="b5813-151">Cause</span></span>  
 <span data-ttu-id="b5813-152">當您在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] / IIS 6.x 上執行 [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] 時，SOAP 和 HTTP 配接器無法在相同的處理序空間或應用程式集區中執行。</span><span class="sxs-lookup"><span data-stu-id="b5813-152">When running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] / IIS 6.x, the SOAP and HTTP adapters cannot execute in the same process space or application pool.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="b5813-153">解決方案</span><span class="sxs-lookup"><span data-stu-id="b5813-153">Resolution</span></span>  
 <span data-ttu-id="b5813-154">如果安裝需要在相同的 Web 伺服器上使用 SOAP 和 HTTP 配接器，則必須針對每一個配接器建立個別的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="b5813-154">If an installation requires using both the SOAP and HTTP adapters on the same Web server then separate application pools must be created for each adapter.</span></span>  <span data-ttu-id="b5813-155">一旦建立之後，就會將每一個配接器的虛擬目錄指派給不同的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="b5813-155">Once created, the virtual directories for each adapter are each assigned to a different application pool.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5813-156">這個問題不會發生在 Windows XP 上，因為在這些作業系統上，SOAP 和 HTTP 配接器是在 IIS 5.x 之下的不同處理序空間中執行。</span><span class="sxs-lookup"><span data-stu-id="b5813-156">This problem does not occur under Windows XP since under these operating systems, the SOAP and HTTP adapter run in different process spaces under IIS 5.x.</span></span>  <span data-ttu-id="b5813-157">SOAP 配接器在 aspnet_wp.exe 處理序中會當做 ASP.Net 應用程式來執行；</span><span class="sxs-lookup"><span data-stu-id="b5813-157">The SOAP adapter runs as an ASP.Net application in the aspnet_wp.exe process.</span></span>  <span data-ttu-id="b5813-158">HTTP 配接器則是在 dllhost.exe 的專用處理序空間中執行。</span><span class="sxs-lookup"><span data-stu-id="b5813-158">The HTTP adapter runs in the dedicated process space of dllhost.exe.</span></span>  <span data-ttu-id="b5813-159">因此，將這兩個配接器隔離，就可讓它們並行於相同的 Web 伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="b5813-159">Therefore both adapters are isolated from each other allowing them to run on the same Web server concurrently.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5813-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5813-160">See Also</span></span>  
 [<span data-ttu-id="b5813-161">SOAP 配接器疑難排解</span><span class="sxs-lookup"><span data-stu-id="b5813-161">Troubleshooting the SOAP Adapter</span></span>](../core/troubleshooting-the-soap-adapter.md)