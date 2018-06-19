---
title: 使用 WCF LOB 配接器 SDK 時，選取 使用 URI 配置和定址的格式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3bb4feee-3d39-43ca-82ac-aba38c13bc69
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9990facf6a23f4abea37ee9ce9758a7333eaca61
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25965308"
---
# <a name="select-a-uri-scheme-and-addressing-format-when-using-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="aaa82-102">使用 WCF LOB 配接器 SDK 時，選取 使用 URI 配置和定址的格式</span><span class="sxs-lookup"><span data-stu-id="aaa82-102">Select a URI scheme and addressing format when using the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="aaa82-103">統一資源識別元 (URI) 可唯一識別資源，像是 Web 服務，或在使用開發配接器的情況下[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，連接到系統，以及要執行的動作。</span><span class="sxs-lookup"><span data-stu-id="aaa82-103">A Uniform Resource Identifier (URI) uniquely identifies resources like a Web service or, in the case of an adapter developed with the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], the system to connect to as well as the action to perform.</span></span> <span data-ttu-id="aaa82-104">本節提供的建議如何建構 URI 來唯一描述的端點位址以及您的配接器的動作。</span><span class="sxs-lookup"><span data-stu-id="aaa82-104">This section provides a recommendation on how to construct a URI to uniquely describe the endpoint address and the action for your adapter.</span></span>  
  
## <a name="anatomy-of-a-uri"></a><span data-ttu-id="aaa82-105">URI 的剖析</span><span class="sxs-lookup"><span data-stu-id="aaa82-105">Anatomy of a URI</span></span>  
 <span data-ttu-id="aaa82-106">URI 是由下列三個元件所組成：</span><span class="sxs-lookup"><span data-stu-id="aaa82-106">A URI consists of the following three components:</span></span>  
  
-   <span data-ttu-id="aaa82-107">**配置名稱**URI 字串的前置部分，而命名的結構; 第一個層級範例包括 http、 urn 和 contoso。</span><span class="sxs-lookup"><span data-stu-id="aaa82-107">**Scheme name** is the lead part of the URI string and is the first level of the naming structure; examples include http, urn, and contoso.</span></span>  
  
-   <span data-ttu-id="aaa82-108">**階層式部分**包含通常階層，而且可以包含選擇性的授權單位、 主機名稱和連接埠資訊的資訊。</span><span class="sxs-lookup"><span data-stu-id="aaa82-108">**Hierarchical part** consists of information that is usually hierarchical and can contain optional authority, hostname, and port information.</span></span> <span data-ttu-id="aaa82-109">範例包括 www.microsoft.com 和使用者名稱 =User@microsoft.com:4099。</span><span class="sxs-lookup"><span data-stu-id="aaa82-109">Examples include www.microsoft.com and UserName=User@microsoft.com:4099.</span></span>  
  
-   <span data-ttu-id="aaa82-110">**查詢**包含以問號 （？） 標示，而且通常會分組為索引鍵/值組，以連字號分隔的選擇性資訊 (&)。</span><span class="sxs-lookup"><span data-stu-id="aaa82-110">**Query** contains optional information marked with a question mark (?) and typically grouped as key/value pairs separated by an ampersand (&).</span></span> <span data-ttu-id="aaa82-111">例如，contoso://microsoft.com/functions?name=Find。</span><span class="sxs-lookup"><span data-stu-id="aaa82-111">For example, contoso://microsoft.com/functions?name=Find.</span></span>  
  
-   <span data-ttu-id="aaa82-112">**片段**用來儲存配接器可能需要的額外識別資訊。</span><span class="sxs-lookup"><span data-stu-id="aaa82-112">**Fragment** is used to store extra identifying information that may be needed by the adapter.</span></span> <span data-ttu-id="aaa82-113">片段隔開雜湊 （#）。例如，contoso://microsoft.com/functions?name=Find#public。</span><span class="sxs-lookup"><span data-stu-id="aaa82-113">The fragment is separated by a hash (#); for example, contoso://microsoft.com/functions?name=Find#public.</span></span>  
  
 <span data-ttu-id="aaa82-114">您可能不會使用所有的 URI 語法所提供的功能。</span><span class="sxs-lookup"><span data-stu-id="aaa82-114">You might not use all of the features provided by the URI syntax.</span></span>  
  
## <a name="designing-the-uri"></a><span data-ttu-id="aaa82-115">設計 URI</span><span class="sxs-lookup"><span data-stu-id="aaa82-115">Designing the URI</span></span>  
 <span data-ttu-id="aaa82-116">身為配接器開發人員，您必須設定適當的 URI 為目標的特定業務系統。</span><span class="sxs-lookup"><span data-stu-id="aaa82-116">As an adapter developer, you will have to devise an appropriate URI for your target line-of-business system.</span></span> <span data-ttu-id="aaa82-117">在設計您的 URI 時，務必要唯一且具有意義。</span><span class="sxs-lookup"><span data-stu-id="aaa82-117">When designing your URI, it is important to make it unique and meaningful.</span></span>  
  
 <span data-ttu-id="aaa82-118">唯一的 URI 是未與現有的 Uri，在組織內外的其他企業網路和網際網路衝突。</span><span class="sxs-lookup"><span data-stu-id="aaa82-118">A unique URI is one that does not conflict with existing URIs within an organization and across other businesses and the Internet.</span></span> <span data-ttu-id="aaa82-119">例如，選擇的配置名稱，例如"http"或"afs 」 可能目前辨識，或已廣為使用可能會導致連接或操作問題因為要求可能會被路由至不同系統而非您的配接器。</span><span class="sxs-lookup"><span data-stu-id="aaa82-119">For example, choosing a scheme name like "http" or "afs" that may be currently recognized or already in wide use could cause connection or operational problems because requests might be routed to a different system and not to your adapter.</span></span>  
  
 <span data-ttu-id="aaa82-120">URI 設計的另一個重要層面對它有意義的人員將會使用您的配接器的開發人員對象。</span><span class="sxs-lookup"><span data-stu-id="aaa82-120">Another important aspect of URI design is making it meaningful to the developer audience who will be consuming your adapter.</span></span> <span data-ttu-id="aaa82-121">例如，如果您要撰寫配接器的醫療理賠處理系統，您可以設計包含公司名稱、 處理系統名稱和作業系統版本的目標宣告的 URI 配置： northwind.contoso.cps.v1.0://。</span><span class="sxs-lookup"><span data-stu-id="aaa82-121">For example, if you are writing an adapter for a medical claims processing system, you could design a URI scheme that includes your company name, the target claims processing system name, and system version: northwind.contoso.cps.v1.0://.</span></span>  
  
## <a name="connecting-to-the-target-system"></a><span data-ttu-id="aaa82-122">連接到目標系統</span><span class="sxs-lookup"><span data-stu-id="aaa82-122">Connecting to the Target System</span></span>  
 <span data-ttu-id="aaa82-123">連接字串具有下列語法：</span><span class="sxs-lookup"><span data-stu-id="aaa82-123">Connection strings have the following syntax:</span></span>  
  
 <span data-ttu-id="aaa82-124">**\<配置\>: //[userinfo"@"]\<LOB 連線字串\>**</span><span class="sxs-lookup"><span data-stu-id="aaa82-124">**\<scheme\>://[userinfo "@"]\<LOB Connection String\>**</span></span>  
  
 <span data-ttu-id="aaa82-125">比方說，您無法連接到 contoso 目錄排序 system （企業營運應用程式的範例行） 使用下列：</span><span class="sxs-lookup"><span data-stu-id="aaa82-125">For example, you could connect to the contoso catalog ordering system (a sample line of business application) using the following:</span></span>  
  
 <span data-ttu-id="aaa82-126">**northwind.contoso.v1.0://\<servername\>嗎？目錄 Contoso 與整合式的安全性 = = True**</span><span class="sxs-lookup"><span data-stu-id="aaa82-126">**northwind.contoso.v1.0://\<servername\>?Catalog=Contoso&Integrated Security=True**</span></span>  
  
 <span data-ttu-id="aaa82-127">您也可以提供選擇性的授權單位 URI，包括使用者名稱和密碼以及其他重要的認證資訊。</span><span class="sxs-lookup"><span data-stu-id="aaa82-127">You can also provide optional authority information in the URI including user name and password and other important credentials.</span></span> <span data-ttu-id="aaa82-128">不過，這可能會造成安全性風險。</span><span class="sxs-lookup"><span data-stu-id="aaa82-128">However, this can present a security risk.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="aaa82-129">請勿在 URI 中傳遞使用者認證和其他機密資訊。</span><span class="sxs-lookup"><span data-stu-id="aaa82-129">Do not pass user credentials and other sensitive information in the URI.</span></span> <span data-ttu-id="aaa82-130">無法攔截與未經授權的使用者檢視這項資訊。</span><span class="sxs-lookup"><span data-stu-id="aaa82-130">This information could be intercepted and viewed by unauthorized users.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaa82-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="aaa82-131">See Also</span></span>  
 [<span data-ttu-id="aaa82-132">計劃和設計配接器使用 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="aaa82-132">Plan and design an adapter using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-an-adapter-using-the-wcf-lob-adapter-sdk.md)