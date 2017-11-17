---
title: "計劃和設計您的配接器使用 WCF LOB 配接器 SDK |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dfbfa6c-2f87-40bb-93d4-6fbb37a235c5
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ae4ff4e0263c5b652d9422324ea176496bc555aa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="plan-and-design-your-adapter-using-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="f1be5-102">計劃和設計您的配接器使用 WCF LOB 配接器 SDK</span><span class="sxs-lookup"><span data-stu-id="f1be5-102">Plan and design your adapter using the WCF LOB Adapter SDK</span></span>

## <a name="overview"></a><span data-ttu-id="f1be5-103">概觀</span><span class="sxs-lookup"><span data-stu-id="f1be5-103">Overview</span></span>
<span data-ttu-id="f1be5-104">規劃是所有開發工作，包括以開發配接器的重要部分[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f1be5-104">Planning is an important part of any development effort, including adapters developed with the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> <span data-ttu-id="f1be5-105">無法做充裕的計畫時開發配接器可能會導致您的配接器如預期般運作，而缺少某些重要的功能 API 所提供的業務系統，並涉及不同的實作詳細資料與互動的策略和預期的使用者，或需要頻繁更新和修復。</span><span class="sxs-lookup"><span data-stu-id="f1be5-105">Failure to adequately plan strategies for interacting with the line-of-business system and the different implementation details involved when developing an adapter could cause your adapter to behave unexpectedly, to lack certain key features provided by the API and expected by the user, or to require frequent update and repair.</span></span>  
  
 <span data-ttu-id="f1be5-106">本節包含設計您的配接器所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="f1be5-106">This section contains the information needed to design your adapter.</span></span> <span data-ttu-id="f1be5-107">您可以使用這項資訊，規劃符合使用者需求的設計。</span><span class="sxs-lookup"><span data-stu-id="f1be5-107">Using this information, you can plan a design that meets the needs of your users.</span></span>  
  
## <a name="get-started"></a><span data-ttu-id="f1be5-108">快速入門</span><span class="sxs-lookup"><span data-stu-id="f1be5-108">Get started</span></span>
  
-   [<span data-ttu-id="f1be5-109">知道並了解您的 LOB 系統</span><span class="sxs-lookup"><span data-stu-id="f1be5-109">Know and understand your LOB system</span></span>](understand-the-lob-system-with-the-wcf-lob-adapter-sdk.md) 
  
-   [<span data-ttu-id="f1be5-110">檢視 WCF LOB 配接器 SDK 中的 支援的訊息交換模式</span><span class="sxs-lookup"><span data-stu-id="f1be5-110">View the supported message exchange patterns in the WCF LOB Adapter SDK</span></span>](view-the-supported-message-exchange-patterns-in-the-wcf-lob-adapter-sdk.md)  
  
-   [<span data-ttu-id="f1be5-111">使用 WCF LOB 配接器 SDK 時，選取 使用 URI 配置和定址的格式</span><span class="sxs-lookup"><span data-stu-id="f1be5-111">Select a URI scheme and addressing format when using the WCF LOB Adapter SDK</span></span>](select-a-uri-scheme-and-addressing-format-when-using-the-wcf-lob-adapter-sdk.md)  
  
-   [<span data-ttu-id="f1be5-112">了解 WCF LOB 配接器 SDK 所建立的配接器的 WCF 安全性</span><span class="sxs-lookup"><span data-stu-id="f1be5-112">Understand WCF security on the adapter created with the WCF LOB Adapter SDK</span></span>](understand-wcf-security-on-the-adapter-created-with-the-wcf-lob-adapter-sdk.md)  
  
-   [<span data-ttu-id="f1be5-113">了解 WCF 的異動</span><span class="sxs-lookup"><span data-stu-id="f1be5-113">Understand transactions in WCF</span></span>](atomic-consistent-isolated-durable-transactions-with-the-wcf-lob-adapter-sdk.md)  
  
-   [<span data-ttu-id="f1be5-114">關於中繼資料搜尋和瀏覽您的 WCF LOB 配接器 SDK 配接器</span><span class="sxs-lookup"><span data-stu-id="f1be5-114">About metadata search and browse with your WCF LOB Adapter SDK adapter</span></span>](about-metadata-search-and-browse-with-your-wcf-lob-adapter-sdk-adapter.md)
  
## <a name="see-also"></a><span data-ttu-id="f1be5-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1be5-115">See Also</span></span>  
[<span data-ttu-id="f1be5-116">規劃和設計您的配接器架構</span><span class="sxs-lookup"><span data-stu-id="f1be5-116">Plan and architect your adapter</span></span>](plan-and-design-an-adapter-using-the-wcf-lob-adapter-sdk.md)