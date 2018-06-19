---
title: 動態解析和路由概觀 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a9a32491-132b-4b25-ac8c-4a927052f0be
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 341b8389530ac85fdc459816f5691f3b814fbd56
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22293990"
---
# <a name="dynamic-resolution-and-routing-overview"></a><span data-ttu-id="7c0b8-102">動態解析和路由概觀</span><span class="sxs-lookup"><span data-stu-id="7c0b8-102">Dynamic Resolution and Routing Overview</span></span>
<span data-ttu-id="7c0b8-103">ESB 解析程式類別支援下列執行階段解析：</span><span class="sxs-lookup"><span data-stu-id="7c0b8-103">The ESB Resolver classes support run-time resolution of the following:</span></span>  
  
-   <span data-ttu-id="7c0b8-104">訊息傳遞端點</span><span class="sxs-lookup"><span data-stu-id="7c0b8-104">Message delivery endpoints</span></span>  
  
-   <span data-ttu-id="7c0b8-105">轉換的對應</span><span class="sxs-lookup"><span data-stu-id="7c0b8-105">Maps for transformation</span></span>  
  
-   <span data-ttu-id="7c0b8-106">端點組態</span><span class="sxs-lookup"><span data-stu-id="7c0b8-106">Endpoint configuration</span></span>  
  
-   <span data-ttu-id="7c0b8-107">自訂的服務中繼資料</span><span class="sxs-lookup"><span data-stu-id="7c0b8-107">Custom service metadata</span></span>  
  
-   <span data-ttu-id="7c0b8-108">伺服器端行程</span><span class="sxs-lookup"><span data-stu-id="7c0b8-108">Server-side itineraries</span></span>  
  
 <span data-ttu-id="7c0b8-109">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]嘗試解析對應和端點的訊息到達時使用解析程式的連接字串。</span><span class="sxs-lookup"><span data-stu-id="7c0b8-109">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] uses resolver connection strings to attempt resolution of maps and endpoints when messages arrive.</span></span> <span data-ttu-id="7c0b8-110">這些連接字串可能存在於路線的 SOAP 標頭的訊息到達時，或它們可能會在自訂管線中使用下列管線元件的其中一個設定時： ESB 行程選取器中，ESB 發送器或 ESB 發送器反組譯。</span><span class="sxs-lookup"><span data-stu-id="7c0b8-110">These connections strings may exist in the itinerary SOAP header of messages when they arrive, or they may be set in a custom pipeline using one of the following pipeline components: ESB Itinerary Selector, ESB Dispatcher, or ESB Dispatcher Disassemble.</span></span> <span data-ttu-id="7c0b8-111">使用 ESB 解析器和配接器提供者架構元件的 「 在 just-in-time 」 (JIT) 解析功能在處理生命週期的更新版本中進行解析。</span><span class="sxs-lookup"><span data-stu-id="7c0b8-111">Resolution occurs later in the processing life cycle using the "just-in-time" (JIT) resolution capabilities of the ESB Resolver and Adapter Provider Framework components.</span></span>  
  
 <span data-ttu-id="7c0b8-112">比方說，如果動態轉換代理程式收到的訊息，必須將對應，但尚未決定對應名稱，它會嘗試使用相關聯的解析程式執行的解決方式。</span><span class="sxs-lookup"><span data-stu-id="7c0b8-112">For example, if the dynamic transformation agent receives a message that it must map, but the map name has not yet been determined, it will attempt to use the associated resolver to perform the resolution.</span></span> <span data-ttu-id="7c0b8-113">如果 JIT 解析失敗，這會歸類為錯誤，系統會產生例外狀況訊息。</span><span class="sxs-lookup"><span data-stu-id="7c0b8-113">If JIT resolution fails, which is classed as an error, the system generates an exception message.</span></span>  
  
 <span data-ttu-id="7c0b8-114">下列資料存放區或解析機制，可以查詢解析器和配接器提供者架構：</span><span class="sxs-lookup"><span data-stu-id="7c0b8-114">The Resolver and Adapter Provider Framework can query the following data stores or resolution mechanisms:</span></span>  
  
-   <span data-ttu-id="7c0b8-115">硬式編碼對應或端點都不會發生動態結案不</span><span class="sxs-lookup"><span data-stu-id="7c0b8-115">Hard-coded maps or endpoints, in which case dynamic resolution does not occur</span></span>  
  
-   <span data-ttu-id="7c0b8-116">商務規則引擎 (BRE) 原則</span><span class="sxs-lookup"><span data-stu-id="7c0b8-116">A Business Rules Engine (BRE) policy</span></span>  
  
-   <span data-ttu-id="7c0b8-117">實作自訂組件**IResolveProvider**介面</span><span class="sxs-lookup"><span data-stu-id="7c0b8-117">A custom assembly implementing the **IResolveProvider** interface</span></span>  
  
-   <span data-ttu-id="7c0b8-118">在訊息上的 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="7c0b8-118">An XPath query over the message</span></span>  
  
-   <span data-ttu-id="7c0b8-119">通用描述、 探索與整合 (UDDI) 查閱</span><span class="sxs-lookup"><span data-stu-id="7c0b8-119">A Universal Description, Discovery, and Integration (UDDI) lookup</span></span>