---
title: 主要功能在 Siebel 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- features, performance-related
- adapter features, new
- features, technology-related
- features, metadata-related
- adapter features, operations-related
- adapter features, performance-related
- features, new
- features, operations-related
- adapter features, metadata-related
ms.assetid: 4612c9ab-810e-4c69-9168-a25c58682e71
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 295ff8b13358109a5d4737fb5f9325b3c9caa0f8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222126"
---
# <a name="key-features-in-the-siebel-adapter"></a><span data-ttu-id="a29d1-102">Siebel 配接器中的主要功能</span><span class="sxs-lookup"><span data-stu-id="a29d1-102">Key features in the Siebel Adapter</span></span>
<span data-ttu-id="a29d1-103">此區段會列出中的新功能[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a29d1-103">This section lists the new features in [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a29d1-104">本主題已經使用舊版的[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="a29d1-104">This topic has been used from the previous version of [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] Help.</span></span>  
  
## <a name="new-features-in-the-siebel-adapter"></a><span data-ttu-id="a29d1-105">Siebel 配接器的新功能</span><span class="sxs-lookup"><span data-stu-id="a29d1-105">New Features in the Siebel Adapter</span></span>  
 <span data-ttu-id="a29d1-106">以下是在此版本中引進的新功能[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a29d1-106">The following are the new features introduced in this release of the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
### <a name="technology-related-features"></a><span data-ttu-id="a29d1-107">技術相關功能</span><span class="sxs-lookup"><span data-stu-id="a29d1-107">Technology-Related Features</span></span>  
  
|<span data-ttu-id="a29d1-108">功能</span><span class="sxs-lookup"><span data-stu-id="a29d1-108">Feature</span></span>|<span data-ttu-id="a29d1-109">註解</span><span class="sxs-lookup"><span data-stu-id="a29d1-109">Comment</span></span>|  
|-------------|-------------|  
|<span data-ttu-id="a29d1-110">支援使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]與 Microsoft Office SharePoint Server (MOSS)</span><span class="sxs-lookup"><span data-stu-id="a29d1-110">Support for using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] with Microsoft Office SharePoint Server (MOSS)</span></span>|<span data-ttu-id="a29d1-111">您可以使用配接器呈現來自 Siebel 系統到 MOSS 入口網站上的資料。</span><span class="sxs-lookup"><span data-stu-id="a29d1-111">You can use the adapters to present data from the Siebel system onto a MOSS portal.</span></span> <span data-ttu-id="a29d1-112">如需詳細資訊，請參閱[Siebel 配接器使用 Microsoft Office SharePoint Server](https://msdn.microsoft.com/library/dd788017.aspx)。</span><span class="sxs-lookup"><span data-stu-id="a29d1-112">For more information, see [Using the Siebel Adapter with Microsoft Office SharePoint Server](https://msdn.microsoft.com/library/dd788017.aspx).</span></span>|  
  
### <a name="operations-related-features"></a><span data-ttu-id="a29d1-113">與作業相關的功能</span><span class="sxs-lookup"><span data-stu-id="a29d1-113">Operations-Related Features</span></span>  
  
|<span data-ttu-id="a29d1-114">功能</span><span class="sxs-lookup"><span data-stu-id="a29d1-114">Feature</span></span>|<span data-ttu-id="a29d1-115">註解</span><span class="sxs-lookup"><span data-stu-id="a29d1-115">Comment</span></span>|  
|-------------|-------------|  
|<span data-ttu-id="a29d1-116">支援商務元件上的相關作業</span><span class="sxs-lookup"><span data-stu-id="a29d1-116">Support for ASSOCIATE operation on business components</span></span>|<span data-ttu-id="a29d1-117">配接器用戶端可以建立關聯，藉由指定搜尋運算式的父記錄和子記錄。</span><span class="sxs-lookup"><span data-stu-id="a29d1-117">Adapter clients can associate records by specifying search expressions for parent and child records.</span></span> <span data-ttu-id="a29d1-118">這只適用於多重值的群組 (MVG) 欄位的商務元件。</span><span class="sxs-lookup"><span data-stu-id="a29d1-118">This is applicable only for business components with multivalued group (MVG) fields.</span></span> <span data-ttu-id="a29d1-119">請注意，搜尋運算式應該篩選父和下層業務元件的完全一筆記錄。</span><span class="sxs-lookup"><span data-stu-id="a29d1-119">Note that the search expressions should filter exactly one record for both the parent and child business components.</span></span>|  
|<span data-ttu-id="a29d1-120">商務元件上的 DISASSOCIATE 作業的支援</span><span class="sxs-lookup"><span data-stu-id="a29d1-120">Support for DISASSOCIATE operation on business components</span></span>|<span data-ttu-id="a29d1-121">藉由指定搜尋運算式的父記錄和子記錄，可以中斷關聯配接器用戶端。</span><span class="sxs-lookup"><span data-stu-id="a29d1-121">Adapter clients can dissociate records by specifying search expressions for parent and child records.</span></span> <span data-ttu-id="a29d1-122">這只適用於多重值的群組 (MVG) 欄位的商務元件。</span><span class="sxs-lookup"><span data-stu-id="a29d1-122">This is applicable only for business components with multivalued group (MVG) fields.</span></span> <span data-ttu-id="a29d1-123">請注意，搜尋運算式必須篩選父和下層業務元件的完全一筆記錄。</span><span class="sxs-lookup"><span data-stu-id="a29d1-123">Note that the search expressions must filter exactly one record for both the parent and child business components.</span></span>|  
|<span data-ttu-id="a29d1-124">支援多重值連結查詢</span><span class="sxs-lookup"><span data-stu-id="a29d1-124">Support for multivalue link queries</span></span>|<span data-ttu-id="a29d1-125">配接器用戶端可以查詢藉由指定的父記錄和多重值的欄位名稱與父記錄相關聯之子記錄。</span><span class="sxs-lookup"><span data-stu-id="a29d1-125">Adapter clients can query the child records associated with a parent record by specifying the parent record and the multivalued field name.</span></span> <span data-ttu-id="a29d1-126">這只適用於多重值的群組 (MVG) 欄位的商務元件。</span><span class="sxs-lookup"><span data-stu-id="a29d1-126">This is applicable only for business components with multivalued group (MVG) fields.</span></span>|  
  
### <a name="other-features"></a><span data-ttu-id="a29d1-127">其他功能</span><span class="sxs-lookup"><span data-stu-id="a29d1-127">Other Features</span></span>  
  
|<span data-ttu-id="a29d1-128">功能</span><span class="sxs-lookup"><span data-stu-id="a29d1-128">Feature</span></span>|<span data-ttu-id="a29d1-129">註解</span><span class="sxs-lookup"><span data-stu-id="a29d1-129">Comment</span></span>|  
|-------------|-------------|  
|<span data-ttu-id="a29d1-130">使用中的配接器的新方法[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a29d1-130">New way of using the adapter in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]</span></span>|<span data-ttu-id="a29d1-131">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]可用於 BizTalk 作為 WCF 自訂連接埠或 Wcf-siebel 連接埠。</span><span class="sxs-lookup"><span data-stu-id="a29d1-131">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] can be used in BizTalk either as a WCF-Custom port or a WCF-Siebel port.</span></span> <span data-ttu-id="a29d1-132">如果您想要使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]透過 WCF 自訂連接埠，您不需要新增 WCF 自訂連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台，因為 WCF 自訂連接埠新增到[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]預設的管理主控台。</span><span class="sxs-lookup"><span data-stu-id="a29d1-132">If you want to use the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] through a WCF-Custom port, you do not need to add the WCF-Custom port to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console because the WCF-Custom port is added to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console by default.</span></span> <span data-ttu-id="a29d1-133">不過，如果您想要使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]透過 Wcf-siebel 連接埠，您必須先新增 Wcf-siebel 配接器[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="a29d1-133">However, if you want to use the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] through a WCF-Siebel port, you must first add the WCF-Siebel adapter to the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="a29d1-134">如需詳細資訊，請參閱[新增 Siebel 配接器至 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="a29d1-134">For more information, see [Add the Siebel Adapter to BizTalk Server Administration Console](../../adapters-and-accelerators/adapter-siebel/add-the-siebel-adapter-to-biztalk-server-administration-console.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a29d1-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a29d1-135">See Also</span></span>  
 [<span data-ttu-id="a29d1-136">瞭解 BizTalk Adapter for Siebel eBusiness 應用程式</span><span class="sxs-lookup"><span data-stu-id="a29d1-136">Understand BizTalk Adapter for Siebel eBusiness Applications</span></span>](../../adapters-and-accelerators/adapter-siebel/understand-biztalk-adapter-for-siebel-ebusiness-applications.md)