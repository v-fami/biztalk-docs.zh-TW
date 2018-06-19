---
title: 升級和版本的應用程式的策略 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e881def2-c407-4205-a6b3-5c1fa5144bb4
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf239b00d45d62a0ee3587baaea40482bfe50667
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24015349"
---
# <a name="upgrading-and-versioning-strategies-for-applications"></a><span data-ttu-id="e7fd8-102">升級和應用程式的版本控制方法</span><span class="sxs-lookup"><span data-stu-id="e7fd8-102">Upgrading and Versioning Strategies for Applications</span></span>
<span data-ttu-id="e7fd8-103">當您需要執行兩個版本的 BizTalk 方案的並存，或如果您無法使用 BizTalk 應用程式停機時間，來部署新的版本，BizTalk 應用程式版本可能會造成問題。</span><span class="sxs-lookup"><span data-stu-id="e7fd8-103">BizTalk application versioning can become an issue when you need to run two versions of a BizTalk solution side-by-side, or if you cannot use BizTalk application downtime to deploy a new version.</span></span> <span data-ttu-id="e7fd8-104">如果您不需要執行兩個版本的方案同時 （例如，您有任何長時間執行的協調流程），而服務維護視窗可用，然後是完全可接受的解除部署舊的版本，並部署新的版本做為版本控制策略 （沒有組件版本控制）。</span><span class="sxs-lookup"><span data-stu-id="e7fd8-104">If you do not need to run two versions of the solution simultaneously (for example, where you have no long-running orchestrations), and service maintenance windows are available, then it is perfectly acceptable to undeploy the old version, and deploy the new version as a versioning strategy (no assembly versioning).</span></span> <span data-ttu-id="e7fd8-105">這是可能的版本控制策略，不過我們還是建議遞增檔案版本號碼 (讓您知道哪一個版本執行的電腦上部署[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="e7fd8-105">This is a possible versioning strategy, although we still recommend incrementing the file version number (to let you know what version is deployed on the computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]).</span></span>  
  
## <a name="when-to-use-versioning"></a><span data-ttu-id="e7fd8-106">使用版本控制的時機</span><span class="sxs-lookup"><span data-stu-id="e7fd8-106">When to Use Versioning</span></span>  
 <span data-ttu-id="e7fd8-107">如果您需要支援長時間執行的協調流程，和/或您需要執行 BizTalk 應用程式部署包含無 BizTalk 應用程式停機時間，則您必須實作並練習實線、 端對端[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]版本控制策略不同的版本控制案例。</span><span class="sxs-lookup"><span data-stu-id="e7fd8-107">If you need to support long-running orchestrations, and/or you need to perform BizTalk application deployments with no BizTalk application downtime, then you need to implement and practice a solid, end-to-end [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] versioning strategy for the different versioning scenarios.</span></span> <span data-ttu-id="e7fd8-108">這包括.NET 組件版本控制和版本控制的所有的 BizTalk 成品，其中包含結構描述、 對應、 管線、 管線元件、 協調流程、 自訂配接器、 自訂類別中呼叫的協調流程、 對應、 商務規則與 BAM。</span><span class="sxs-lookup"><span data-stu-id="e7fd8-108">This includes .NET assembly versioning and versioning of all BizTalk artifacts, which includes schemas, maps, pipelines, pipeline components, orchestrations, custom adapters, custom classes called in orchestrations and maps, business rules, and BAM.</span></span>  
  
 <span data-ttu-id="e7fd8-109">結構描述版本控制中是唯一的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管線會判斷目標命名空間加上的根節點為基礎的訊息的訊息類型的結構描述中定義的名稱。</span><span class="sxs-lookup"><span data-stu-id="e7fd8-109">Schema versioning is unique in that the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pipelines determine the message type of a message based on the target namespace plus root node name defined in the schema.</span></span> <span data-ttu-id="e7fd8-110">如需詳細資訊，請參閱[管線元件中的結構描述解析](../core/schema-resolution-in-pipeline-components.md)。</span><span class="sxs-lookup"><span data-stu-id="e7fd8-110">For more information, see [Schema Resolution in Pipeline Components](../core/schema-resolution-in-pipeline-components.md).</span></span> <span data-ttu-id="e7fd8-111">如果您需要版本您的結構描述，版本指標必須是目標命名空間的一部分。</span><span class="sxs-lookup"><span data-stu-id="e7fd8-111">If you need to version your schemas, a version indicator must be part of the target namespace.</span></span> <span data-ttu-id="e7fd8-112">變更結構描述版本連帶影響整個方案，並因此應該事先規劃。</span><span class="sxs-lookup"><span data-stu-id="e7fd8-112">Changing the schema version has a ripple effect throughout your solution, and therefore should be planned in advance.</span></span> <span data-ttu-id="e7fd8-113">在建立協調流程訊息時，搜尋**BizTalk Server: 8 的秘訣和訣竅更好的 BizTalk 程式設計**(提示 1： 一律使用多部分訊息類型)。</span><span class="sxs-lookup"><span data-stu-id="e7fd8-113">When creating orchestration messages, search for **BizTalk Server: 8 Tips And Tricks For Better BizTalk Programming** (tip 1: Always Use Multi-Part Message Types).</span></span> <span data-ttu-id="e7fd8-114">使用這個方法提供更大的彈性時結構描述版本。</span><span class="sxs-lookup"><span data-stu-id="e7fd8-114">Use of this method provides greater flexibility when versioning schemas.</span></span>  
  
## <a name="using-factoring-for-assembly-versioning"></a><span data-ttu-id="e7fd8-115">使用組件版本控制的建構</span><span class="sxs-lookup"><span data-stu-id="e7fd8-115">Using Factoring for Assembly Versioning</span></span>  
 <span data-ttu-id="e7fd8-116">如果您需要支援長時間執行的協調流程、-並存部署或無停機時間升級，您應該實作的組件版本控制和封裝策略。</span><span class="sxs-lookup"><span data-stu-id="e7fd8-116">If you need to support long-running orchestrations, side-by-side deployments, or no-downtime upgrades, then you should implement an assembly versioning and packaging strategy.</span></span> <span data-ttu-id="e7fd8-117">若要執行的 BizTalk 成品的組件版本控制，您的 BizTalk 方案組件需要中分解出來 （封裝） 的方式以允許[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]版本控制。</span><span class="sxs-lookup"><span data-stu-id="e7fd8-117">In order to perform assembly versioning of BizTalk artifacts, your BizTalk solution assemblies need to be factored (packaged) in such a way to allow for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] versioning.</span></span>  <span data-ttu-id="e7fd8-118">有三種類型的建構：</span><span class="sxs-lookup"><span data-stu-id="e7fd8-118">There are three types of factoring:</span></span>  
  
-   <span data-ttu-id="e7fd8-119">**沒有建構**</span><span class="sxs-lookup"><span data-stu-id="e7fd8-119">**No factoring**</span></span>  
  
     <span data-ttu-id="e7fd8-120">所有的 BizTalk 成品是在一個組件。</span><span class="sxs-lookup"><span data-stu-id="e7fd8-120">All BizTalk artifacts are in one assembly.</span></span> <span data-ttu-id="e7fd8-121">這是容易了解和部署，但可提供最大的彈性。</span><span class="sxs-lookup"><span data-stu-id="e7fd8-121">This is the easiest to understand and deploy, but provides the least amount of flexibility.</span></span>  
  
-   <span data-ttu-id="e7fd8-122">**完整的建構**</span><span class="sxs-lookup"><span data-stu-id="e7fd8-122">**Full factoring**</span></span>  
  
     <span data-ttu-id="e7fd8-123">每個 BizTalk 成品是在它自己組件中。</span><span class="sxs-lookup"><span data-stu-id="e7fd8-123">Each BizTalk artifact is in its own assembly.</span></span> <span data-ttu-id="e7fd8-124">這會提供最大的彈性，但最為複雜部署並了解。</span><span class="sxs-lookup"><span data-stu-id="e7fd8-124">This provides the most flexibility, but is the most complex to deploy and understand.</span></span>  
  
-   <span data-ttu-id="e7fd8-125">**最佳建構**</span><span class="sxs-lookup"><span data-stu-id="e7fd8-125">**Optimal factoring**</span></span>  
  
     <span data-ttu-id="e7fd8-126">某處介於 「 沒有分解 」 及 「 完整分解 」 為基礎的 BizTalk 應用程式的深入分析。</span><span class="sxs-lookup"><span data-stu-id="e7fd8-126">Somewhere in-between “no factoring” and “full factoring” based on in-depth analysis of your BizTalk applications.</span></span> <span data-ttu-id="e7fd8-127">除了版本控制，這可讓您輕鬆地實作您的 BizTalk 主控件設計。</span><span class="sxs-lookup"><span data-stu-id="e7fd8-127">In addition to versioning, this allows you to easily implement your BizTalk Host design.</span></span> <span data-ttu-id="e7fd8-128">藉由尋找 BizTalk 成品之間的關聯性來達到此目的。</span><span class="sxs-lookup"><span data-stu-id="e7fd8-128">This is achieved by looking for relationships among BizTalk artifacts.</span></span> <span data-ttu-id="e7fd8-129">成品一律版本一起通常可以放在相同的組件中。</span><span class="sxs-lookup"><span data-stu-id="e7fd8-129">Artifacts that are always versioned together can typically be put in the same assembly.</span></span> <span data-ttu-id="e7fd8-130">如果需要之成品的獨立版本設定，然後將它們必須放在不同的組件中。</span><span class="sxs-lookup"><span data-stu-id="e7fd8-130">If independent versioning of the artifacts is required, then they must be put in different assemblies.</span></span> <span data-ttu-id="e7fd8-131">這是層級想要達到的建構。</span><span class="sxs-lookup"><span data-stu-id="e7fd8-131">This is the level of factoring you want to achieve.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="e7fd8-132">其他資源</span><span class="sxs-lookup"><span data-stu-id="e7fd8-132">Additional Resources</span></span>  
  
 <span data-ttu-id="e7fd8-133">定義和練習以確保它會提供任何並存的部署策略，您可能需要的實心版本控制策略。</span><span class="sxs-lookup"><span data-stu-id="e7fd8-133">Define and practice a solid versioning strategy to ensure it provides any side-by-side deployment strategies you might need.</span></span> <span data-ttu-id="e7fd8-134">BizTalk Server 應用程式的升級和版本控制策略的資源包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="e7fd8-134">Resources for BizTalk Server application upgrade and versioning strategies include the following:</span></span>  
  
-   [<span data-ttu-id="e7fd8-135">更新應用程式</span><span class="sxs-lookup"><span data-stu-id="e7fd8-135">Updating an Application</span></span>](../technical-guides/updating-an-application.md)  
  
-   [<span data-ttu-id="e7fd8-136">更新 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="e7fd8-136">Updating BizTalk Applications</span></span>](../core/updating-biztalk-applications.md)
  
-   [<span data-ttu-id="e7fd8-137">BizTalk Server 專案版本管理</span><span class="sxs-lookup"><span data-stu-id="e7fd8-137">BizTalk Server Project Versioning</span></span>](../core/biztalk-server-project-versioning.md)  
  
-   [<span data-ttu-id="e7fd8-138">了解 BizTalk Server 應用程式部署</span><span class="sxs-lookup"><span data-stu-id="e7fd8-138">Understanding BizTalk Server Application Deployment</span></span>](../core/understanding-biztalk-application-deployment-and-management.md)


  
## <a name="see-also"></a><span data-ttu-id="e7fd8-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7fd8-139">See Also</span></span>  
 [<span data-ttu-id="e7fd8-140">檢查清單：設定 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="e7fd8-140">Checklist: Configuring BizTalk Server</span></span>](../technical-guides/checklist-configuring-biztalk-server.md)
