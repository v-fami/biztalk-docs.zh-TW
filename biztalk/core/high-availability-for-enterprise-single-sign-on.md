---
title: 企業單一登入的高可用性 |Microsoft Docs
ms.custom: ''
ms.date: 2016-02-29
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Master Secret server, availability
- high availability, SSO
- Master Secret server, high availability
- SSO, high availability
ms.assetid: 6c631b5c-7147-4cc0-b58a-6749e83df9d3
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9acc933df7b958ea6ae0f0651fd66ba14daad913
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37019242"
---
# <a name="high-availability-for-enterprise-single-sign-on"></a><span data-ttu-id="2d563-102">企業單一登入的高可用性</span><span class="sxs-lookup"><span data-stu-id="2d563-102">High Availability for Enterprise Single Sign-On</span></span>
<span data-ttu-id="2d563-103">即使您未使用「企業單一登入」(SSO) 功能來對應認證和單一登入，SSO 仍然是整個 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 基礎結構的重要部分，因為 BizTalk Server 會使用 SSO 協助保護接收位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="2d563-103">Even if you do not use the Enterprise Single-Sign-On (SSO) functionality for mapping credentials and single sign-on, SSO is a critical part of the overall Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] infrastructure, because BizTalk Server uses SSO to help secure information for the receive locations.</span></span>  
  
 <span data-ttu-id="2d563-104">您必須將安裝 SSO 服務的第一部電腦設定為主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="2d563-104">You must configure the first computer where you install the SSO service as the master secret server.</span></span> <span data-ttu-id="2d563-105">主要密碼伺服器是儲存主要密碼 (加密金鑰) 的 SSO 伺服器。</span><span class="sxs-lookup"><span data-stu-id="2d563-105">The master secret server is the SSO server that stores the master secret (encryption key).</span></span> <span data-ttu-id="2d563-106">主要密碼是一種加密金鑰，供 SSO 系統用來加密和解密儲存在 SSO 資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="2d563-106">The master secret is the encryption key that the SSO system uses to encrypt and decrypt the data it stores in the SSO database.</span></span>  
  
 <span data-ttu-id="2d563-107">若 SSO 伺服器失敗，且在其他 BizTalk Server 電腦 (也就是 SSO 伺服器) 執行相同的主控件執行個體，則其他 SSO 伺服器會繼續進行其工作。</span><span class="sxs-lookup"><span data-stu-id="2d563-107">If an SSO server fails, and if you have other BizTalk Server computers (and therefore SSO servers) running the same host instance, the other SSO servers continue doing their work.</span></span> <span data-ttu-id="2d563-108">這表示主要密碼伺服器仍可正確運作，因此 BizTalk Server 處理會繼續。</span><span class="sxs-lookup"><span data-stu-id="2d563-108">This means that the master secret server still functions correctly, and therefore the BizTalk Server processing continues.</span></span>  
  
 <span data-ttu-id="2d563-109">若主要密碼伺服器失敗，則所有在它失敗之前正在執行的執行階段作業 (包括認證的解密) 可成功地繼續進行。</span><span class="sxs-lookup"><span data-stu-id="2d563-109">If the master secret server fails, all run-time operations that were running before it failed, including decryption of credentials, continue successfully.</span></span> <span data-ttu-id="2d563-110">不過，您無法加密新的認證。</span><span class="sxs-lookup"><span data-stu-id="2d563-110">However, you cannot encrypt new credentials.</span></span> <span data-ttu-id="2d563-111">因此，BizTalk Server 環境與主要密碼伺服器的可用性相依，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="2d563-111">Therefore, the BizTalk Server environment has a dependency on the availability of the master secret server, as shown in the following figure.</span></span>  
  
 <span data-ttu-id="2d563-112">![失敗點](../core/media/tdi-highava-pointsfailure-mss.gif "TDI_HighAva_PointsFailure_MSS")</span><span class="sxs-lookup"><span data-stu-id="2d563-112">![Points of Failure](../core/media/tdi-highava-pointsfailure-mss.gif "TDI_HighAva_PointsFailure_MSS")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2d563-113">如果主要密碼伺服器無法使用，在下列情況發生前，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 主控件執行個體仍可使用主要密碼的記憶體中快取複本進行執行階段作業：</span><span class="sxs-lookup"><span data-stu-id="2d563-113">If the master secret server becomes unavailable, then [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] host instances can still perform run-time operations by using the in-memory cached copy of the master secret until:</span></span>  
> 
> - <span data-ttu-id="2d563-114">主控件執行個體重新啟動。</span><span class="sxs-lookup"><span data-stu-id="2d563-114">The host instances are restarted.</span></span>  
>   -   <span data-ttu-id="2d563-115">執行 BizTalk 主控件執行個體之電腦上的 SSO 服務重新啟動。</span><span class="sxs-lookup"><span data-stu-id="2d563-115">The SSO service on the computer running the BizTalk host instances is restarted.</span></span>  
>   -   <span data-ttu-id="2d563-116">SSO 主要密碼變更。</span><span class="sxs-lookup"><span data-stu-id="2d563-116">The SSO master secret is changed.</span></span>  
> 
>   <span data-ttu-id="2d563-117">如果重新啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上的 SSO 服務或變更 SSO 主要密碼，則會從記憶體中釋出主要密碼的快取複本，且 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 必須能夠連線主要密碼伺服器才能取得主要密碼的另一個複本。</span><span class="sxs-lookup"><span data-stu-id="2d563-117">If the SSO service is restarted on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers or if the SSO master secret is changed, then the cached copy of the master secret is released from memory and the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] must be able to contact the master secret server to obtain another copy of the master secret.</span></span> <span data-ttu-id="2d563-118">如果主要密碼伺服器無法使用，則需要存取主要密碼伺服器以進行加密的任何管理作業將會失敗。</span><span class="sxs-lookup"><span data-stu-id="2d563-118">If the master secret server is unavailable then any administrative operations that require access to the master secret server for purposes of encryption will fail.</span></span>  
  
## <a name="making-the-master-secret-server-available"></a><span data-ttu-id="2d563-119">讓主要密碼伺服器可用</span><span class="sxs-lookup"><span data-stu-id="2d563-119">Making the Master Secret Server Available</span></span>  
 <span data-ttu-id="2d563-120">為了讓 SSO 系統可用 (也就是讓 BizTalk Server 環境可用)，請務必在主要密碼產生之後立即將它備份。</span><span class="sxs-lookup"><span data-stu-id="2d563-120">For availability of the SSO system, and therefore of the BizTalk Server environment, it is critical that you back up the master secret as soon as it is generated.</span></span> <span data-ttu-id="2d563-121">若遺失該主要密碼，您將遺失使用它來加密的 SSO 系統資料。</span><span class="sxs-lookup"><span data-stu-id="2d563-121">If you lose it, you lose the data that the SSO system encrypted by using that master secret.</span></span> <span data-ttu-id="2d563-122">如需備份主要祕密的詳細資訊，請參閱[如何重新設定主要密碼](../core/how-to-back-up-the-master-secret.md)。</span><span class="sxs-lookup"><span data-stu-id="2d563-122">For more information about backing up the master secret, see [How to Back Up the Master Secret](../core/how-to-back-up-the-master-secret.md).</span></span>  
  
 <span data-ttu-id="2d563-123">可使用兩種方法讓主要密碼伺服器可用：</span><span class="sxs-lookup"><span data-stu-id="2d563-123">You can make the master secret server available in two ways:</span></span>  
  
-   <span data-ttu-id="2d563-124">**可供使用，但不是高度可用。**</span><span class="sxs-lookup"><span data-stu-id="2d563-124">**Available, but not highly available.**</span></span> <span data-ttu-id="2d563-125">所有 SSO 伺服器都會將主要密碼快取在記憶體中，且即使主要密碼伺服器失敗，執行階段作業仍然會繼續。</span><span class="sxs-lookup"><span data-stu-id="2d563-125">All the SSO servers have the master secret cached in memory, and run-time operations will continue even if the master secret server fails.</span></span> <span data-ttu-id="2d563-126">不過，您將無法變更連接埠組態或 SSO 組態。</span><span class="sxs-lookup"><span data-stu-id="2d563-126">However, you will not be able to change the configuration of ports or the SSO configuration.</span></span> <span data-ttu-id="2d563-127">BizTalk Server 執行階段將會順利繼續進行，但是您無法做任何設計變更。</span><span class="sxs-lookup"><span data-stu-id="2d563-127">The BizTalk Server runtime will continue working without problems, but you cannot make any design changes.</span></span>  
  
     <span data-ttu-id="2d563-128">即使此組態不是高度可用，但它仍可滿足大部分的實例，且它與向外擴充接收、傳送和處理主控件一致。</span><span class="sxs-lookup"><span data-stu-id="2d563-128">Even if this configuration is not highly available, it can be satisfactory for most scenarios and it is consistent with scaling out the receiving, sending, and processing hosts.</span></span>  
  
-   <span data-ttu-id="2d563-129">**高可用性。**</span><span class="sxs-lookup"><span data-stu-id="2d563-129">**Highly available.**</span></span> <span data-ttu-id="2d563-130">若要提供主要密碼伺服器的備援，請在不同的主要密碼伺服器叢集上使用 Windows 叢集，或在現有的資料庫叢集上設定主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="2d563-130">To provide redundancy for the master secret server, use Windows Clustering on a separate master secret server cluster, or configure the master secret server on an existing database cluster.</span></span> <span data-ttu-id="2d563-131">主要密碼伺服器所提供的服務不會耗用太多資源，且在資料庫叢集上安裝時，通常不會影響資料庫的功能或效能。</span><span class="sxs-lookup"><span data-stu-id="2d563-131">The services provided by the master secret server do not consume many resources, and typically do not affect database functionality or performance when installed on a database cluster.</span></span> <span data-ttu-id="2d563-132">下圖顯示如何讓主要密碼伺服器高度可用。</span><span class="sxs-lookup"><span data-stu-id="2d563-132">The following figure shows how you can make the master secret server highly available.</span></span>  
  
     <span data-ttu-id="2d563-133">![高可用性的主要密碼伺服器](../core/media/tdi-highava-msscluster.gif "TDI_HighAva_MSSCluster")</span><span class="sxs-lookup"><span data-stu-id="2d563-133">![Highly Available Master Secret Server](../core/media/tdi-highava-msscluster.gif "TDI_HighAva_MSSCluster")</span></span>  
  
     <span data-ttu-id="2d563-134">雖然此組態高度可用，它仍然需要額外的硬體資源。</span><span class="sxs-lookup"><span data-stu-id="2d563-134">While this configuration is highly available, it requires additional hardware resources.</span></span> <span data-ttu-id="2d563-135">如需高可用性 SSO 安裝選項的詳細資訊，請參閱[高可用性 SSO 安裝選項](../core/high-availability-sso-installation-options.md)。</span><span class="sxs-lookup"><span data-stu-id="2d563-135">For more information about high availability installation options for SSO, see [High-Availability SSO Installation Options](../core/high-availability-sso-installation-options.md).</span></span> <span data-ttu-id="2d563-136">本節包含設定為高可用性的叢集資源的 Windows Server 叢集上的 SSO 主要祕密伺服器的詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="2d563-136">This section includes detailed information about configuring the SSO master secret server as a highly available cluster resource on a Windows Server cluster.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2d563-137">若要減少高度可用方案的硬體資源，您可以在 SQL Server 叢集中新增主要密碼伺服器做為叢集資源。</span><span class="sxs-lookup"><span data-stu-id="2d563-137">To reduce the hardware resources for a highly available solution, you can add the master secret server as a cluster resource in your SQL Server cluster.</span></span> <span data-ttu-id="2d563-138">您不需要購買額外的 BizTalk Server 授權，另一部電腦上安裝 SSO 服務。</span><span class="sxs-lookup"><span data-stu-id="2d563-138">You do not need to purchase additional BizTalk Server licenses to install the SSO service on another computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d563-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d563-139">See Also</span></span>  
 <span data-ttu-id="2d563-140">[叢集 BizTalk Server 資料庫](../core/clustering-the-biztalk-server-databases1.md) </span><span class="sxs-lookup"><span data-stu-id="2d563-140">[Clustering the BizTalk Server Databases](../core/clustering-the-biztalk-server-databases1.md) </span></span>  
 <span data-ttu-id="2d563-141">[建立高可用性的 BizTalk Server 環境](../core/creating-a-highly-available-biztalk-server-environment.md) </span><span class="sxs-lookup"><span data-stu-id="2d563-141">[Creating a Highly Available BizTalk Server Environment](../core/creating-a-highly-available-biztalk-server-environment.md) </span></span>  
 [<span data-ttu-id="2d563-142">如何叢集化主要密碼伺服器</span><span class="sxs-lookup"><span data-stu-id="2d563-142">How to Cluster the Master Secret Server</span></span>](../core/how-to-cluster-the-master-secret-server1.md)