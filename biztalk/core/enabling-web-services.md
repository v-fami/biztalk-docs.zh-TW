---
title: "啟用 Web 服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web services, publishing
- hosts, isolated
- Web services, planning
- Web services, enabling
ms.assetid: 2a4681f6-9ded-423d-baa5-5831e6a85c61
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b7cd0b1694422caf04285206f0bd7411ff5de20
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="enabling-web-services"></a><span data-ttu-id="88ac6-102">啟用 Web 服務</span><span class="sxs-lookup"><span data-stu-id="88ac6-102">Enabling Web Services</span></span>
<span data-ttu-id="88ac6-103">若要發佈 Web 服務，您必須設定 Internet Information Services (IIS)、BizTalk 外掛式主控件，以及 Windows 使用者和群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="88ac6-103">To publish Web services, you must configure Internet Information Services (IIS), BizTalk Isolated Hosts, and Windows user and group accounts.</span></span> <span data-ttu-id="88ac6-104">本節討論如何啟用 IIS 中的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="88ac6-104">This section discusses how to enable Web services in IIS.</span></span> <span data-ttu-id="88ac6-105">如需有關啟用 Web 服務的詳細資訊，請參閱 IIS 文件。</span><span class="sxs-lookup"><span data-stu-id="88ac6-105">For more information about enabling Web services, see the IIS documentation.</span></span>  
  
 <span data-ttu-id="88ac6-106">**Internet Information Services**</span><span class="sxs-lookup"><span data-stu-id="88ac6-106">**Internet Information Services**</span></span>  
  
 <span data-ttu-id="88ac6-107">您可以發佈 Web 服務，Windows 系統上有 IIS 與 ASP.NET 設定。</span><span class="sxs-lookup"><span data-stu-id="88ac6-107">You can publish Web services to Windows systems that have IIS configured with ASP.NET.</span></span> <span data-ttu-id="88ac6-108">每部伺服器的所有 Web 服務都會在 ASP.NET 背景工作處理序內執行。</span><span class="sxs-lookup"><span data-stu-id="88ac6-108">For each server, all Web services run within the ASP.NET worker process.</span></span>  
  
 <span data-ttu-id="88ac6-109">根據預設，ASP.NET 背景工作處理序會使用本機 ASPNET 帳戶。</span><span class="sxs-lookup"><span data-stu-id="88ac6-109">The ASP.NET worker process uses the local ASPNET account by default.</span></span> <span data-ttu-id="88ac6-110">IIS 用來處理 Web 服務要求的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="88ac6-110">IIS uses application pools for processing Web service requests.</span></span>  
  
 <span data-ttu-id="88ac6-111">**BizTalk 外掛式主控件**</span><span class="sxs-lookup"><span data-stu-id="88ac6-111">**BizTalk Isolated Hosts**</span></span>  
  
 <span data-ttu-id="88ac6-112">若要啟用 Web 服務，您必須至少在 BizTalk Server 中建立一個外掛式主控件。</span><span class="sxs-lookup"><span data-stu-id="88ac6-112">To enable Web services, you must create at least one Isolated Host in BizTalk Server.</span></span> <span data-ttu-id="88ac6-113">外掛式主控的件代表外部處理序，例如 ISAPI 擴充程式及 BizTalk Server 不會建立或控制 ASP.NET 處理序。</span><span class="sxs-lookup"><span data-stu-id="88ac6-113">Isolated Hosts represent external processes, such as ISAPI extensions and ASP.NET processes that BizTalk Server does not create or control.</span></span> <span data-ttu-id="88ac6-114">這些類型的外部處理序必須裝載特定配接器，例如 HTTP/S 和 SOAP。</span><span class="sxs-lookup"><span data-stu-id="88ac6-114">These types of external processes must host certain adapters, such as HTTP/S and SOAP.</span></span>  
  
 <span data-ttu-id="88ac6-115">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態管理員會建立 BizTalk 用來做為預設外掛式主控件的 BizTalkServerIsolatedHost。</span><span class="sxs-lookup"><span data-stu-id="88ac6-115">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration Manager creates the BizTalkServerIsolatedHost that BizTalk uses as the default Isolated Host.</span></span> <span data-ttu-id="88ac6-116">BizTalk 外掛式主控件使用者群組是與這個主控件相關的 Windows 群組預設名稱。</span><span class="sxs-lookup"><span data-stu-id="88ac6-116">The BizTalk Isolated Host Users group is the name of the Windows group associated with this host by default.</span></span> <span data-ttu-id="88ac6-117">如需主控件和主控件執行個體的詳細資訊，請參閱[管理 BizTalk 主控件和主控件執行個體](../core/managing-biztalk-hosts-and-host-instances.md)。</span><span class="sxs-lookup"><span data-stu-id="88ac6-117">For more information about Hosts and Host Instances, see [Managing BizTalk Hosts and Host Instances](../core/managing-biztalk-hosts-and-host-instances.md).</span></span>  
  
 <span data-ttu-id="88ac6-118">外掛式主控件執行個體只能執行一個配接器。</span><span class="sxs-lookup"><span data-stu-id="88ac6-118">An isolated host instance can run only one adapter.</span></span> <span data-ttu-id="88ac6-119">如果您使用單一外掛式主控件設定 HTTP 和 SOAP 配接器的接收處理常式，則必須建立兩個應用程式集區，讓每個配接器使用一個應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="88ac6-119">If you configure the receive handlers of HTTP and SOAP adapters with the one isolated host, you must create two application pools, one application pool for each adapter.</span></span>  
  
 <span data-ttu-id="88ac6-120">例如，如果您計劃設定兩個外掛式主控件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="88ac6-120">For example, if you plan to configure two isolated hosts as following:</span></span>  
  
|<span data-ttu-id="88ac6-121">外掛式主控件名稱</span><span class="sxs-lookup"><span data-stu-id="88ac6-121">Isolated host name</span></span>|<span data-ttu-id="88ac6-122">接收位置</span><span class="sxs-lookup"><span data-stu-id="88ac6-122">Receive locations</span></span>|  
|------------------------|-----------------------|  
|<span data-ttu-id="88ac6-123">外掛式主控的件 1</span><span class="sxs-lookup"><span data-stu-id="88ac6-123">Isolated Host 1</span></span>|<span data-ttu-id="88ac6-124">HTTP_ReceiveLocation1A</span><span class="sxs-lookup"><span data-stu-id="88ac6-124">HTTP_ReceiveLocation1A</span></span><br /><br /> <span data-ttu-id="88ac6-125">HTTP_ReceiveLocation1B</span><span class="sxs-lookup"><span data-stu-id="88ac6-125">HTTP_ReceiveLocation1B</span></span><br /><br /> <span data-ttu-id="88ac6-126">SOAP_ReceiveLocation1**附註：** **外掛式主控件 1**用於接收 SOAP 和 HTTP 配接器處理常式。</span><span class="sxs-lookup"><span data-stu-id="88ac6-126">SOAP_ReceiveLocation1 **Note:**  The **Isolated Host 1** is used for receive handlers of both SOAP and HTTP adapters.</span></span>|  
|<span data-ttu-id="88ac6-127">外掛式主控件 2</span><span class="sxs-lookup"><span data-stu-id="88ac6-127">Isolated Host 2</span></span>|<span data-ttu-id="88ac6-128">HTTP_ReceiveLocation2</span><span class="sxs-lookup"><span data-stu-id="88ac6-128">HTTP_ReceiveLocation2</span></span>|  
  
 <span data-ttu-id="88ac6-129">您可以建立四個虛擬目錄，讓每一個接收位置使用一個目錄，如下所示：</span><span class="sxs-lookup"><span data-stu-id="88ac6-129">You may create four virtual directories, one for each receive location as follows:</span></span>  
  
|<span data-ttu-id="88ac6-130">接收位置</span><span class="sxs-lookup"><span data-stu-id="88ac6-130">Receive location</span></span>|<span data-ttu-id="88ac6-131">虛擬目錄</span><span class="sxs-lookup"><span data-stu-id="88ac6-131">Virtual directory</span></span>|  
|----------------------|-----------------------|  
|<span data-ttu-id="88ac6-132">HTTP_ReceiveLocation1A</span><span class="sxs-lookup"><span data-stu-id="88ac6-132">HTTP_ReceiveLocation1A</span></span>|<span data-ttu-id="88ac6-133">IIS_Virtual_Directory1A</span><span class="sxs-lookup"><span data-stu-id="88ac6-133">IIS_Virtual_Directory1A</span></span>|  
|<span data-ttu-id="88ac6-134">HTTP_ReceiveLocation1B</span><span class="sxs-lookup"><span data-stu-id="88ac6-134">HTTP_ReceiveLocation1B</span></span>|<span data-ttu-id="88ac6-135">IIS_Virtual_Directory1B</span><span class="sxs-lookup"><span data-stu-id="88ac6-135">IIS_Virtual_Directory1B</span></span>|  
|<span data-ttu-id="88ac6-136">SOAP_ReceiveLocation1</span><span class="sxs-lookup"><span data-stu-id="88ac6-136">SOAP_ReceiveLocation1</span></span>|<span data-ttu-id="88ac6-137">IIS_Virtual_Directory1C</span><span class="sxs-lookup"><span data-stu-id="88ac6-137">IIS_Virtual_Directory1C</span></span>|  
|<span data-ttu-id="88ac6-138">HTTP_ReceiveLocation2</span><span class="sxs-lookup"><span data-stu-id="88ac6-138">HTTP_ReceiveLocation2</span></span>|<span data-ttu-id="88ac6-139">IIS_Virtual_Directory2</span><span class="sxs-lookup"><span data-stu-id="88ac6-139">IIS_Virtual_Directory2</span></span>|  
  
 <span data-ttu-id="88ac6-140">然後，您必須，如下所示建立至少三個應用程式集區的虛擬目錄：</span><span class="sxs-lookup"><span data-stu-id="88ac6-140">Then, you must create at least three application pools for the virtual directories as follows:</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88ac6-141">您必須至少為每一個外掛式主控件建立一個應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="88ac6-141">You must create at least one application pool for each isolated host.</span></span>  
  
|<span data-ttu-id="88ac6-142">虛擬目錄</span><span class="sxs-lookup"><span data-stu-id="88ac6-142">Virtual directories</span></span>|<span data-ttu-id="88ac6-143">應用程式集區</span><span class="sxs-lookup"><span data-stu-id="88ac6-143">Application pool</span></span>|<span data-ttu-id="88ac6-144">Description</span><span class="sxs-lookup"><span data-stu-id="88ac6-144">Description</span></span>|  
|-------------------------|----------------------|-----------------|  
|<span data-ttu-id="88ac6-145">IIS_Virtual_Directory1A</span><span class="sxs-lookup"><span data-stu-id="88ac6-145">IIS_Virtual_Directory1A</span></span><br /><br /> <span data-ttu-id="88ac6-146">IIS_Virtual_Directory1B</span><span class="sxs-lookup"><span data-stu-id="88ac6-146">IIS_Virtual_Directory1B</span></span>|<span data-ttu-id="88ac6-147">AppPool_Host1_HTTP</span><span class="sxs-lookup"><span data-stu-id="88ac6-147">AppPool_Host1_HTTP</span></span>|<span data-ttu-id="88ac6-148">您不需要其他應用程式集區，因為所有接收位置都有相同的外掛式主控件 (外掛式主控件 1)，和相同的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="88ac6-148">A separate application pool is not required because all of the receive locations have the same isolated host (Isolated Host 1), and the same protocol.</span></span>|  
|<span data-ttu-id="88ac6-149">IIS_Virtual_Directory1C</span><span class="sxs-lookup"><span data-stu-id="88ac6-149">IIS_Virtual_Directory1C</span></span>|<span data-ttu-id="88ac6-150">AppPool_Host1_SOAP</span><span class="sxs-lookup"><span data-stu-id="88ac6-150">AppPool_Host1_SOAP</span></span>|<span data-ttu-id="88ac6-151">您不需要其他應用程式集區，因為接收位置使用的通訊協定 (SOAP) 與同一主控件 (外掛式主控件 1) 中其他接收位置不同。</span><span class="sxs-lookup"><span data-stu-id="88ac6-151">A separate application pool is required because the receive location uses the different protocol (SOAP) from the other receive locations in the same host (Isolated Host 1).</span></span>|  
|<span data-ttu-id="88ac6-152">IIS_Virtual_Directory2</span><span class="sxs-lookup"><span data-stu-id="88ac6-152">IIS_Virtual_Directory2</span></span>|<span data-ttu-id="88ac6-153">AppPool_Host2_HTTP</span><span class="sxs-lookup"><span data-stu-id="88ac6-153">AppPool_Host2_HTTP</span></span>|<span data-ttu-id="88ac6-154">您需要另一個應用程式集區，因為接收位置不是在外掛式主控件 1 下執行。</span><span class="sxs-lookup"><span data-stu-id="88ac6-154">A separate application pool is required because the receive location runs under the different host from Isolated Host 1.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="88ac6-155">您必須將應用程式集區的使用者帳戶加入適當的本機或網域群組的外掛式主控件。</span><span class="sxs-lookup"><span data-stu-id="88ac6-155">You must add the user account for the application pools to the appropriate local or domain groups of the isolated hosts.</span></span> <span data-ttu-id="88ac6-156">如需詳細資訊，請參閱[Windows 群組和 BizTalk Server 中的使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="88ac6-156">For more information, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88ac6-157">您必須根據上表，在外掛式主控件執行個體與對應的應用程式集區之間對應使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="88ac6-157">You need to match the user account between an isolated host instance and the corresponding application pool according to the previous tables.</span></span> <span data-ttu-id="88ac6-158">如需外掛式主控的件執行個體和應用程式集區的使用者帳戶之間的關聯性的詳細資訊，請參閱[如何變更服務帳戶和密碼](../core/how-to-change-service-accounts-and-passwords.md)。</span><span class="sxs-lookup"><span data-stu-id="88ac6-158">For more information about the relationship between user accounts of isolated host instance and application pools, see [How to Change Service Accounts and Passwords](../core/how-to-change-service-accounts-and-passwords.md).</span></span>  
  
 <span data-ttu-id="88ac6-159">**單一伺服器安裝的資料庫存取**</span><span class="sxs-lookup"><span data-stu-id="88ac6-159">**Database access for single server installations**</span></span>  
  
 <span data-ttu-id="88ac6-160">如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 BizTalk 管理資料庫位於同一部伺服器上，則應該將 ASP.NET 背景工作處理序或 IIS 應用程式集區的使用者內容設定為本機 ASPNET 使用者帳戶，或是具備最低權限的本機或網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="88ac6-160">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and the BizTalk Management database reside on the same server, you should set the user context of the ASP.NET worker process or the IIS Application Pool to the local ASPNET user account, or a local or domain user account that has minimal privileges.</span></span>  
  
 <span data-ttu-id="88ac6-161">**多個伺服器安裝的資料庫存取**</span><span class="sxs-lookup"><span data-stu-id="88ac6-161">**Database access for multiple server installations**</span></span>  
  
 <span data-ttu-id="88ac6-162">如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 BizTalk 管理資料庫位於不同的伺服器上，則應該將 ASP.NET 背景工作處理序或 IIS 應用程式集區的使用者內容變更為網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="88ac6-162">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and the BizTalk Management database reside on different servers, you should change the user context of the ASP.NET worker process or the IIS Application Pool to a domain user account.</span></span>  
  
 <span data-ttu-id="88ac6-163">實作多重伺服器部署時，BizTalk 資料庫伺服器所屬的網域上必須有外掛式主控件 Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="88ac6-163">When implementing a multi-server deployment, the Isolated Host Windows groups must exist on the domain which the BizTalk database servers belong to.</span></span>  
  
 <span data-ttu-id="88ac6-164">**最小化帳戶權限和使用者權限**</span><span class="sxs-lookup"><span data-stu-id="88ac6-164">**Minimizing account privileges and user rights**</span></span>  
  
 <span data-ttu-id="88ac6-165">請使用外掛式主控件，將與 BizTalk Server 互動時所需最低限度資源的存取權限，賦予給在外部處理序中執行的配接器。</span><span class="sxs-lookup"><span data-stu-id="88ac6-165">You use Isolated Hosts to give adapters that run in external processes access to the minimal amount of required resources to interact with BizTalk Server.</span></span> <span data-ttu-id="88ac6-166">為了部署安全起見，您應該給予外部處理序的使用者內容最低權限。</span><span class="sxs-lookup"><span data-stu-id="88ac6-166">For a secure deployment, you should give the user context for the external processes minimal privileges.</span></span>  
  
 <span data-ttu-id="88ac6-167">**BizTalk Web 服務發佈精靈的安全性建議**</span><span class="sxs-lookup"><span data-stu-id="88ac6-167">**Security recommendations for BizTalk Web Services Publishing Wizard**</span></span>  
  
 <span data-ttu-id="88ac6-168">BizTalk Web 服務發佈精靈建立的虛擬目錄將繼承父系虛擬目錄或網站的存取控制清單 (ACL) 和驗證需求。</span><span class="sxs-lookup"><span data-stu-id="88ac6-168">The virtual directory created by the BizTalk Web Services Publishing Wizard will inherit the access control lists (ACL) and authentication requirements from the parent virtual directory or Web site.</span></span> <span data-ttu-id="88ac6-169">如果父系虛擬目錄或網站允許匿名存取，則 BizTalk Web 服務發佈精靈將在建立虛擬目錄時移除該功能。</span><span class="sxs-lookup"><span data-stu-id="88ac6-169">If the parent virtual directory or Web site allows anonymous access, the BizTalk Web Services Publishing Wizard will remove that capability when creating the virtual directory.</span></span>  
  
 <span data-ttu-id="88ac6-170">下列包含 [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)] 的安全性注意事項與建議。</span><span class="sxs-lookup"><span data-stu-id="88ac6-170">The following contains security notes and recommendations for [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)].</span></span>  
  
## <a name="next"></a><span data-ttu-id="88ac6-171">下一個</span><span class="sxs-lookup"><span data-stu-id="88ac6-171">Next</span></span>
  
[<span data-ttu-id="88ac6-172">如何啟用 ASP.NET 的已發佈的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="88ac6-172">How to Enable ASP.NET for Published Web Services</span></span>](../core/how-to-enable-asp-net-4-0-for-published-web-services.md)