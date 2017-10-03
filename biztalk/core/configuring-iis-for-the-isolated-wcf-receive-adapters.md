---
title: "設定 IIS 的外掛式 WCF 接收配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive adapters, WCF services
- WCF services, receive adapters
- IIS, configuring [WCF receive adapters]
ms.assetid: 1c6f1561-a7ba-4eb0-8878-bf213ebcd6a6
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1515a69ab6a9150668db4f3415f0483dd1ce4e7a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-iis-for-the-isolated-wcf-receive-adapters"></a><span data-ttu-id="fc5d8-102">針對外掛式 WCF 接收配接器設定 IIS</span><span class="sxs-lookup"><span data-stu-id="fc5d8-102">Configuring IIS for the Isolated WCF Receive Adapters</span></span>
<span data-ttu-id="fc5d8-103">若要使用 BizTalk WCF 服務發佈精靈來發佈 WCF 服務，您必須設定 Internet Information Services (IIS)、BizTalk 外掛式主控件和 Windows 使用者群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="fc5d8-103">To publish WCF services by using the BizTalk WCF Service Publishing Wizard, you must configure Internet Information Services (IIS), BizTalk isolated hosts, and Windows user group accounts.</span></span> <span data-ttu-id="fc5d8-104">本節討論的問題與設定 IIS 以外掛式 WCF 接收配接器 (例如 WCF-BasicHttp 接收配接器、WCF-WSHttp 接收配接器和 WCF-CustomIsolated 配接器) 發佈 WCF 服務有關。</span><span class="sxs-lookup"><span data-stu-id="fc5d8-104">This section discusses issues related to configuring IIS for publishing WCF services with isolated WCF receive adapters such as the WCF-BasicHttp receive adapter, WCF-WSHttp receive adapter, and WCF-CustomIsolated adapter.</span></span> <span data-ttu-id="fc5d8-105">一般 WCF 服務裝載在 IIS 的詳細資訊，請參閱 < 裝載於 IIS >，網址[http://go.microsoft.com/fwlink/?LinkId=75700](http://go.microsoft.com/fwlink/?LinkId=75700)。</span><span class="sxs-lookup"><span data-stu-id="fc5d8-105">For general information about hosting WCF services in IIS, see "Hosting in IIS" at [http://go.microsoft.com/fwlink/?LinkId=75700](http://go.microsoft.com/fwlink/?LinkId=75700).</span></span>  
  
## <a name="considerations-when-configuring-iis"></a><span data-ttu-id="fc5d8-106">設定 IIS 的考量</span><span class="sxs-lookup"><span data-stu-id="fc5d8-106">Considerations When Configuring IIS</span></span>  
 <span data-ttu-id="fc5d8-107">**Internet Information Services 7.0 和 7.5**</span><span class="sxs-lookup"><span data-stu-id="fc5d8-107">**Internet Information Services 7.0 and 7.5**</span></span>  
  
 <span data-ttu-id="fc5d8-108">您可以使用以 ASP.NET 4.0 設定的 IIS 7.0 和 7.5，利用外掛式 WCF 接收配接器來發佈 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="fc5d8-108">You can use IIS 7.0 and 7.5 configured with ASP.NET 4.0 to publish WCF services with isolated WCF receive adapters.</span></span>  
  
 <span data-ttu-id="fc5d8-109">IIS 7.0 (適用於 Windows Server 2008 SP2) 和 IIS 7.5 (適用於 Windows Server 2008 R2) 會使用 IIS 應用程式集區來處理 Web 服務要求。</span><span class="sxs-lookup"><span data-stu-id="fc5d8-109">IIS 7.0 (for Windows Server 2008 SP2) and IIS 7.5 (for Windows Server 2008 R2) use the IIS application pools for processing Web service requests.</span></span> <span data-ttu-id="fc5d8-110">IIS 7.0 支援多個應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="fc5d8-110">IIS 7.0 supports multiple application pools.</span></span> <span data-ttu-id="fc5d8-111">每個應用程式集區處理序都可以在不同的使用者環境下執行。</span><span class="sxs-lookup"><span data-stu-id="fc5d8-111">Each application pool process can run under a different user context.</span></span>  
  
 <span data-ttu-id="fc5d8-112">**BizTalk 外掛式主控件**</span><span class="sxs-lookup"><span data-stu-id="fc5d8-112">**BizTalk isolated hosts**</span></span>  
  
 <span data-ttu-id="fc5d8-113">若要以外掛式 WCF 接收配接器裝載 WCF 服務，您必須在 BizTalk Server 中建立至少一個外掛式主控件。</span><span class="sxs-lookup"><span data-stu-id="fc5d8-113">To host the WCF services with isolated WCF receive adapters, you must create at least one isolated host in BizTalk Server.</span></span> <span data-ttu-id="fc5d8-114">如需如何設定 BizTalk 外掛式主控件的詳細資訊，請參閱 「 BizTalk 外掛式主控件 」 中[啟用 Web 服務](../core/enabling-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="fc5d8-114">For more information about how to configure BizTalk isolated hosts, see "BizTalk Isolated Hosts" in [Enabling Web Services](../core/enabling-web-services.md).</span></span>  
  
 <span data-ttu-id="fc5d8-115">**多個伺服器安裝的資料庫存取**</span><span class="sxs-lookup"><span data-stu-id="fc5d8-115">**Database access for multiple server installations**</span></span>  
  
 <span data-ttu-id="fc5d8-116">如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 BizTalk 管理資料庫位於不同的伺服器上，則應該將 IIS 應用程式集區的使用者內容變更為網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="fc5d8-116">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and the BizTalk Management database reside on different servers, you should change the user context of the IIS Application Pool to a domain user account.</span></span>  
  
 <span data-ttu-id="fc5d8-117">實作多重伺服器部署時，BizTalk 資料庫伺服器所屬的網域上必須有外掛式主控件 Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="fc5d8-117">When implementing a multi-server deployment, the Isolated Host Windows groups must exist on the domain to which the BizTalk database servers belong.</span></span>  
  
 <span data-ttu-id="fc5d8-118">**最小化帳戶權限和使用者權限**</span><span class="sxs-lookup"><span data-stu-id="fc5d8-118">**Minimizing account privileges and user rights**</span></span>  
  
 <span data-ttu-id="fc5d8-119">請使用外掛式主控件，將與 BizTalk Server 互動時所需最低限度資源的存取權限，賦予給在外部處理序中執行的配接器。</span><span class="sxs-lookup"><span data-stu-id="fc5d8-119">You use isolated hosts to give adapters that run in external processes access to the minimal amount of required resources to interact with BizTalk Server.</span></span> <span data-ttu-id="fc5d8-120">為了部署安全起見，您應該給予外部處理序的使用者內容最低權限。</span><span class="sxs-lookup"><span data-stu-id="fc5d8-120">For a secure deployment, you should give the user context for the external processes minimal privileges.</span></span>  
  
 <span data-ttu-id="fc5d8-121">**BizTalk Web 服務發佈精靈的安全性建議**</span><span class="sxs-lookup"><span data-stu-id="fc5d8-121">**Security recommendations for the BizTalk Web Services Publishing Wizard**</span></span>  
  
 <span data-ttu-id="fc5d8-122">BizTalk WCF 服務發佈精靈建立的虛擬目錄繼承了父系虛擬目錄或網站的存取控制清單 (ACL)。</span><span class="sxs-lookup"><span data-stu-id="fc5d8-122">The virtual directory created by the BizTalk WCF Service Publishing Wizard inherits the access control lists (ACL) from the parent virtual directory or Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc5d8-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc5d8-123">See Also</span></span>  
 [<span data-ttu-id="fc5d8-124">發佈 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="fc5d8-124">Publishing WCF Services</span></span>](../core/publishing-wcf-services.md)