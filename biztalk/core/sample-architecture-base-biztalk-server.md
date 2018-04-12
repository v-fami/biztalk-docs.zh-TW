---
title: 範例架構： 基本 BizTalk Server |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture, examples
- IPSec
- BizTalk Server, examples
- security, examples
- security, architecture
- IPSec, about IPSec
- BizTalk Server, architecture
- architecture, security
ms.assetid: 7ccc1ef3-670f-423f-b6ca-3d56b9bbeabf
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea815c0165f58c28cea8ce7cae35fd6ed7437323
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sample-architecture-base-biztalk-server"></a><span data-ttu-id="8587a-102">範例架構： 基本 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="8587a-102">Sample Architecture: Base BizTalk Server</span></span>
<span data-ttu-id="8587a-103">本主題討論基本範例架構。</span><span class="sxs-lookup"><span data-stu-id="8587a-103">This topic discusses the base sample architecture.</span></span> <span data-ttu-id="8587a-104">其中描述與配接器無關的 BizTalk Server 部署中的元件。</span><span class="sxs-lookup"><span data-stu-id="8587a-104">It describes the components in a BizTalk Server deployment that are adapter-independent.</span></span> <span data-ttu-id="8587a-105">建議任何 BizTalk Server 部署至少都要有這些元件。</span><span class="sxs-lookup"><span data-stu-id="8587a-105">We recommend that any BizTalk Server deployment have at least these components.</span></span>  
  
 <span data-ttu-id="8587a-106">下圖顯示基本 BizTalk Server 範例架構的元件。</span><span class="sxs-lookup"><span data-stu-id="8587a-106">The following figure shows the components of the base BizTalk Server sample architecture.</span></span> <span data-ttu-id="8587a-107">這些元件會在後面章節所討論的各種配接器特定 BizTalk Server 架構中出現。</span><span class="sxs-lookup"><span data-stu-id="8587a-107">These components appear in all the adapter-specific BizTalk Server architectures that we discuss in later sections.</span></span>  
  
 <span data-ttu-id="8587a-108">**圖 1 基本架構元件**</span><span class="sxs-lookup"><span data-stu-id="8587a-108">**Figure 1 Base architecture components**</span></span>  
  
 <span data-ttu-id="8587a-109">![基底架構元件](../core/media/tdi-sec-refarch.gif "TDI_Sec_RefArch_")</span><span class="sxs-lookup"><span data-stu-id="8587a-109">![Base architecture components](../core/media/tdi-sec-refarch.gif "TDI_Sec_RefArch_")</span></span>  
  
 <span data-ttu-id="8587a-110">此範例架構包含下列章節中討論的項目。</span><span class="sxs-lookup"><span data-stu-id="8587a-110">This sample architecture contains the items discussed in the following sections.</span></span>  
  
## <a name="perimeter-networkinternet"></a><span data-ttu-id="8587a-111">周邊網路─網際網路</span><span class="sxs-lookup"><span data-stu-id="8587a-111">Perimeter network―internet</span></span>  
  
-   <span data-ttu-id="8587a-112">周邊網路 (也稱為 DMZ 以及過濾的子網路) 包含提供網際網路相關服務的伺服器。</span><span class="sxs-lookup"><span data-stu-id="8587a-112">This perimeter network (also known as DMZ, demilitarized zone, and screened subnet) contains servers that provide Internet-related services.</span></span> <span data-ttu-id="8587a-113">在此網域中沒有 BizTalk Server、BizTalk 接收位置或企業單一登入伺服器。</span><span class="sxs-lookup"><span data-stu-id="8587a-113">There are no BizTalk Servers, BizTalk receive locations, or Enterprise Single Sign-On servers in this domain.</span></span>  
  
## <a name="perimeter-networkintranet"></a><span data-ttu-id="8587a-114">周邊網路─內部網路</span><span class="sxs-lookup"><span data-stu-id="8587a-114">Perimeter network―intranet</span></span>  
 <span data-ttu-id="8587a-115">周邊網路包含提供內部網路相關服務的伺服器。</span><span class="sxs-lookup"><span data-stu-id="8587a-115">This perimeter network contains servers that provide intranet-related services.</span></span> <span data-ttu-id="8587a-116">它會在內部網路 (例如企業網路) 和執行應用程式的伺服器之間，提供額外的安全性階層。</span><span class="sxs-lookup"><span data-stu-id="8587a-116">It provides an additional layer of security between your intranet (for example, a corporate network) and the servers that run the application.</span></span> <span data-ttu-id="8587a-117">類似於網際網路周邊網路，內部網路周邊網路不包含 BizTalk Server、BizTalk 接收位置或「企業單一登入」(SSO) 伺服器。</span><span class="sxs-lookup"><span data-stu-id="8587a-117">Like the Internet perimeter network, the intranet perimeter network does not contain BizTalk Servers, BizTalk receive locations, or Enterprise Single Sign-On servers.</span></span>  
  
## <a name="e-business-domain"></a><span data-ttu-id="8587a-118">電子商務網域</span><span class="sxs-lookup"><span data-stu-id="8587a-118">E-Business Domain</span></span>  
 <span data-ttu-id="8587a-119">此網域包含 BizTalk Server 實作所使用的所有基礎結構與應用程式。</span><span class="sxs-lookup"><span data-stu-id="8587a-119">This domain contains all the infrastructure and applications used by your BizTalk Server implementation.</span></span> <span data-ttu-id="8587a-120">此網域中的伺服器包括：</span><span class="sxs-lookup"><span data-stu-id="8587a-120">The servers in this domain are:</span></span>  
  
-   <span data-ttu-id="8587a-121">**BizTalk Server。**</span><span class="sxs-lookup"><span data-stu-id="8587a-121">**BizTalk Server.**</span></span> <span data-ttu-id="8587a-122">此伺服器擁有一個 BizTalk Server 執行階段安裝與許多「BizTalk 主控件」的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8587a-122">This server has an installation of the BizTalk Server runtime and instances of various BizTalk Hosts.</span></span> <span data-ttu-id="8587a-123">環境中 BizTalk Server 的數目依它們執行的主控件類型與效能需求而定。</span><span class="sxs-lookup"><span data-stu-id="8587a-123">The number of BizTalk Servers in the environment depends on the type of hosts they run and the performance needs.</span></span> <span data-ttu-id="8587a-124">當您的效能需求增加時，可以為處理主控件的主控件執行個體在環境中加入更多 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="8587a-124">As your performance needs increase, you can add more BizTalk Servers to your environment for host instances of your processing hosts.</span></span>  
  
-   <span data-ttu-id="8587a-125">**主要密碼伺服器。**</span><span class="sxs-lookup"><span data-stu-id="8587a-125">**Master secret server.**</span></span> <span data-ttu-id="8587a-126">此伺服器是「企業單一登入」(SSO) 主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="8587a-126">This server is the Enterprise Single Sign-On (SSO) master secret server.</span></span> <span data-ttu-id="8587a-127">其中保存 SSO 系統用來加密 SSO 資料庫中資料的主要密碼 (加密金鑰)。</span><span class="sxs-lookup"><span data-stu-id="8587a-127">It holds the master secret (encryption key) that the SSO system uses to encrypt the data in the SSO database.</span></span>  
  
-   <span data-ttu-id="8587a-128">**SQL Server。**</span><span class="sxs-lookup"><span data-stu-id="8587a-128">**SQL Server.**</span></span> <span data-ttu-id="8587a-129">此伺服器包含 BizTalk 資料庫。</span><span class="sxs-lookup"><span data-stu-id="8587a-129">This server contains the BizTalk databases.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="8587a-130">對於容錯移轉保護，建議您叢集每個 BizTalk 資料庫。</span><span class="sxs-lookup"><span data-stu-id="8587a-130">For failover protection, we recommend that you cluster each BizTalk database.</span></span> <span data-ttu-id="8587a-131">如需有關 Microsoft SQL Server 容錯移轉叢集的詳細資訊，請參閱 Microsoft MSDN 網站，網址[http://go.microsoft.com/fwlink/?LinkID=190216](http://go.microsoft.com/fwlink/?LinkID=190216)。</span><span class="sxs-lookup"><span data-stu-id="8587a-131">For more information about Microsoft SQL Server failover clustering, see the Microsoft MSDN Web site at [http://go.microsoft.com/fwlink/?LinkID=190216](http://go.microsoft.com/fwlink/?LinkID=190216).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8587a-132">依據您的效能需求，您可能必須將 BizTalk 資料庫分割至執行 SQL Server 的多部電腦上。</span><span class="sxs-lookup"><span data-stu-id="8587a-132">Depending on your performance needs, you might have to separate the BizTalk databases into multiple computers that run SQL Server.</span></span>  
  
-   <span data-ttu-id="8587a-133">**網域控制站。**</span><span class="sxs-lookup"><span data-stu-id="8587a-133">**Domain controller.**</span></span> <span data-ttu-id="8587a-134">此伺服器裝載電子商務 Active Directory 網域。</span><span class="sxs-lookup"><span data-stu-id="8587a-134">This server hosts the E-Business Active Directory domain.</span></span> <span data-ttu-id="8587a-135">其中包含需要存取 BizTalk Server 的所有群組與個別帳戶的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8587a-135">It contains information about all the groups and individual accounts that need access to BizTalk Server.</span></span>  
  
-   <span data-ttu-id="8587a-136">**系統管理工具。**</span><span class="sxs-lookup"><span data-stu-id="8587a-136">**Administration tools.**</span></span> <span data-ttu-id="8587a-137">此網域的其中一個伺服器會裝載下列管理工具：BizTalk 管理主控台和企業單一登入 (SSO) 管理公用程式。</span><span class="sxs-lookup"><span data-stu-id="8587a-137">One of the servers in this domain hosts the administration tools: BizTalk Administration console and Enterprise Single Sign-On (SSO) administration utility.</span></span>  
  
## <a name="firewalls-and-domains"></a><span data-ttu-id="8587a-138">防火牆與網域</span><span class="sxs-lookup"><span data-stu-id="8587a-138">Firewalls and Domains</span></span>  
 <span data-ttu-id="8587a-139">在圖 1 中，Forefront Threat Management Gateway (TMG) 2010 server 扮演軟體防火牆協助保護，並包含每個網域。</span><span class="sxs-lookup"><span data-stu-id="8587a-139">In Figure 1, Forefront Threat Management Gateway (TMG) 2010 server acts as a software firewall to help protect and contain each of these domains.</span></span> <span data-ttu-id="8587a-140">此外，電子商務網域有它自己的網域控制站，此網域不信任任何其他網域。</span><span class="sxs-lookup"><span data-stu-id="8587a-140">Additionally, the E-Business domain has its own domain controller, and this domain does not trust any other domain.</span></span> <span data-ttu-id="8587a-141">如需如何設定網域和信任的防火牆的詳細資訊，請參閱 「 Microsoft 說明及支援 」 網站，網址[http://go.microsoft.com/fwlink/?LinkId=25230](http://go.microsoft.com/fwlink/?LinkId=25230)。</span><span class="sxs-lookup"><span data-stu-id="8587a-141">For more information about how to configure a firewall for domains and trusts, see the Microsoft Help and Support Web site at [http://go.microsoft.com/fwlink/?LinkId=25230](http://go.microsoft.com/fwlink/?LinkId=25230).</span></span>  
  
 <span data-ttu-id="8587a-142">範例架構有兩個防火牆：</span><span class="sxs-lookup"><span data-stu-id="8587a-142">The sample architecture has two firewalls:</span></span>  
  
-   <span data-ttu-id="8587a-143">**防火牆 1。**</span><span class="sxs-lookup"><span data-stu-id="8587a-143">**Firewall 1.**</span></span> <span data-ttu-id="8587a-144">此防火牆有三個網路介面：它會路由傳送來自網際網路、內部網路以及周邊網路的流量。</span><span class="sxs-lookup"><span data-stu-id="8587a-144">This firewall has three network interfaces: It routes traffic from the Internet, the intranet, and the perimeter networks.</span></span>  
  
-   <span data-ttu-id="8587a-145">**防火牆 2。**</span><span class="sxs-lookup"><span data-stu-id="8587a-145">**Firewall 2.**</span></span> <span data-ttu-id="8587a-146">此防火牆是雙重主機：它會路由傳送來自周邊網路 (網際網路與內部網路) 與電子商務網域的流量。</span><span class="sxs-lookup"><span data-stu-id="8587a-146">This firewall is dual-homed: It routes traffic from the perimeter networks (both Internet and intranet) and the E-Business domain.</span></span>  
  
 <span data-ttu-id="8587a-147">周邊網路中的電腦不是任何網域的成員，而且它們不會相互通訊。</span><span class="sxs-lookup"><span data-stu-id="8587a-147">The computers in the perimeter networks are not members of any domain, and they do not communicate with each other.</span></span>  
  
## <a name="ipsec"></a><span data-ttu-id="8587a-148">IPsec</span><span class="sxs-lookup"><span data-stu-id="8587a-148">IPsec</span></span>  
 <span data-ttu-id="8587a-149">建議您使用網際網路通訊協定安全性 (IPSec) 來協助保護電子商務網域中所有伺服器之間的通訊安全。</span><span class="sxs-lookup"><span data-stu-id="8587a-149">We recommend that you use Internet Protocol security (IPSec) to help secure the communication between all the servers in the E-Business domain.</span></span> <span data-ttu-id="8587a-150">IPsec 規則如下：</span><span class="sxs-lookup"><span data-stu-id="8587a-150">The IPsec rules are as follows:</span></span>  
  
-   <span data-ttu-id="8587a-151">允許 BizTalk Server 與網域控制站之間已驗證的流量。</span><span class="sxs-lookup"><span data-stu-id="8587a-151">Allow authenticated traffic between BizTalk Server and the domain controller.</span></span>  
  
-   <span data-ttu-id="8587a-152">允許 BizTalk Server 與管理工具伺服器之間已驗證的流量。</span><span class="sxs-lookup"><span data-stu-id="8587a-152">Allow authenticated traffic between BizTalk Server and the administration tools server.</span></span>  
  
-   <span data-ttu-id="8587a-153">允許 BizTalk Server 與主要密碼伺服器之間已驗證的流量。</span><span class="sxs-lookup"><span data-stu-id="8587a-153">Allow authenticated traffic between BizTalk Server and the master secret server.</span></span>  
  
-   <span data-ttu-id="8587a-154">允許 BizTalk Server 與 SQL Server 之間已驗證的流量。</span><span class="sxs-lookup"><span data-stu-id="8587a-154">Allow authenticated traffic between BizTalk Server and the SQL Server.</span></span>  
  
-   <span data-ttu-id="8587a-155">允許主要密碼伺服器與網域控制站之間已驗證的流量。</span><span class="sxs-lookup"><span data-stu-id="8587a-155">Allow authenticated traffic between the master secret server and the domain controller.</span></span>  
  
-   <span data-ttu-id="8587a-156">允許主要密碼伺服器與 BizTalk Server (外掛式、處理、內含式以及追蹤主控件) 之間已驗證的流量。</span><span class="sxs-lookup"><span data-stu-id="8587a-156">Allow authenticated traffic between the master secret server and the BizTalk Server (isolated, processing, in-process, and tracking hosts.)</span></span>  
  
-   <span data-ttu-id="8587a-157">允許主要密碼伺服器與 SQL Server (SSO 資料庫) 之間已驗證的流量。</span><span class="sxs-lookup"><span data-stu-id="8587a-157">Allow authenticated traffic between the master secret server and the SQL Server (SSO databases).</span></span>  
  
-   <span data-ttu-id="8587a-158">允許網域控制站與網域中所有伺服器之間已驗證的流量。</span><span class="sxs-lookup"><span data-stu-id="8587a-158">Allow authenticated traffic between the domain controller and all the servers in the domain.</span></span>  
  
-   <span data-ttu-id="8587a-159">允許管理工具伺服器與網域中所有伺服器之間已驗證的流量。</span><span class="sxs-lookup"><span data-stu-id="8587a-159">Allow authenticated traffic between the administration tools server and all the servers in the domain.</span></span>  
  
 <span data-ttu-id="8587a-160">若您在網域中有其他應用程式不需要存取 BizTalk Server、SQL Server 以及主要密碼伺服器或管理工具伺服器，請封鎖那些應用程式與適當伺服器之間的流量。</span><span class="sxs-lookup"><span data-stu-id="8587a-160">If you have other applications in the domain that do not need access to the BizTalk Server, SQL Server, master secret server, or administration tools server, block traffic between those applications and the appropriate servers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8587a-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8587a-161">See Also</span></span>  
 <span data-ttu-id="8587a-162">[安全性規劃](../core/planning-for-security.md) </span><span class="sxs-lookup"><span data-stu-id="8587a-162">[Planning for Security](../core/planning-for-security.md) </span></span>  
 <span data-ttu-id="8587a-163">[小型與中型公司的範例架構](../core/sample-architectures-for-small-medium-sized-companies.md) </span><span class="sxs-lookup"><span data-stu-id="8587a-163">[Sample Architectures for Small & Medium-Sized Companies](../core/sample-architectures-for-small-medium-sized-companies.md) </span></span>  
 [<span data-ttu-id="8587a-164">威脅模型分析的範例案例</span><span class="sxs-lookup"><span data-stu-id="8587a-164">Sample Scenarios for Threat Model Analysis</span></span>](../core/sample-scenarios-for-threat-model-analysis.md)