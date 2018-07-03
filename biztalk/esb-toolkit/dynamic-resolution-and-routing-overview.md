---
title: 動態解析和路由概觀 |Microsoft Docs
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
ms.openlocfilehash: ab7ea6f4ddd37be8d8c2c6629d2449c2d9df5f81
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018764"
---
# <a name="dynamic-resolution-and-routing-overview"></a><span data-ttu-id="480c2-102">動態解析和路由概觀</span><span class="sxs-lookup"><span data-stu-id="480c2-102">Dynamic Resolution and Routing Overview</span></span>
<span data-ttu-id="480c2-103">ESB 解析程式類別會支援下列執行階段解析：</span><span class="sxs-lookup"><span data-stu-id="480c2-103">The ESB Resolver classes support run-time resolution of the following:</span></span>  

- <span data-ttu-id="480c2-104">訊息傳遞端點</span><span class="sxs-lookup"><span data-stu-id="480c2-104">Message delivery endpoints</span></span>  

- <span data-ttu-id="480c2-105">轉換的對應</span><span class="sxs-lookup"><span data-stu-id="480c2-105">Maps for transformation</span></span>  

- <span data-ttu-id="480c2-106">端點組態</span><span class="sxs-lookup"><span data-stu-id="480c2-106">Endpoint configuration</span></span>  

- <span data-ttu-id="480c2-107">自訂的服務中繼資料</span><span class="sxs-lookup"><span data-stu-id="480c2-107">Custom service metadata</span></span>  

- <span data-ttu-id="480c2-108">伺服器端路線</span><span class="sxs-lookup"><span data-stu-id="480c2-108">Server-side itineraries</span></span>  

  <span data-ttu-id="480c2-109">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]郵件送達時，嘗試解析對應和端點時，用以解析程式的連接字串。</span><span class="sxs-lookup"><span data-stu-id="480c2-109">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] uses resolver connection strings to attempt resolution of maps and endpoints when messages arrive.</span></span> <span data-ttu-id="480c2-110">這些連接字串可能存在路線的 SOAP 標頭的訊息中，當到達，或它們可能會設定在自訂管線中使用下列管線元件的其中一個： ESB 路線選取器、 ESB 發送器或 ESB 發送器解譯。</span><span class="sxs-lookup"><span data-stu-id="480c2-110">These connections strings may exist in the itinerary SOAP header of messages when they arrive, or they may be set in a custom pipeline using one of the following pipeline components: ESB Itinerary Selector, ESB Dispatcher, or ESB Dispatcher Disassemble.</span></span> <span data-ttu-id="480c2-111">稍後在處理生命週期使用 ESB 解析程式和配接器提供者架構元件的 「 只是時間 」 (JIT) 解析功能，就會發生解析。</span><span class="sxs-lookup"><span data-stu-id="480c2-111">Resolution occurs later in the processing life cycle using the "just-in-time" (JIT) resolution capabilities of the ESB Resolver and Adapter Provider Framework components.</span></span>  

  <span data-ttu-id="480c2-112">例如，如果動態轉換代理程式收到的訊息，它必須對應，但尚未決定對應名稱，它會嘗試使用相關聯的解析程式執行解析。</span><span class="sxs-lookup"><span data-stu-id="480c2-112">For example, if the dynamic transformation agent receives a message that it must map, but the map name has not yet been determined, it will attempt to use the associated resolver to perform the resolution.</span></span> <span data-ttu-id="480c2-113">如果 JIT 解析失敗，這被歸類為錯誤，系統會產生例外狀況訊息。</span><span class="sxs-lookup"><span data-stu-id="480c2-113">If JIT resolution fails, which is classed as an error, the system generates an exception message.</span></span>  

  <span data-ttu-id="480c2-114">下列資料存放區或解析機制，可以查詢解析程式和配接器提供者架構：</span><span class="sxs-lookup"><span data-stu-id="480c2-114">The Resolver and Adapter Provider Framework can query the following data stores or resolution mechanisms:</span></span>  

- <span data-ttu-id="480c2-115">硬式編碼的對應或端點，不會發生案例的動態解析不會</span><span class="sxs-lookup"><span data-stu-id="480c2-115">Hard-coded maps or endpoints, in which case dynamic resolution does not occur</span></span>  

- <span data-ttu-id="480c2-116">商務規則引擎 (BRE) 原則</span><span class="sxs-lookup"><span data-stu-id="480c2-116">A Business Rules Engine (BRE) policy</span></span>  

- <span data-ttu-id="480c2-117">實作自訂組件**IResolveProvider**介面</span><span class="sxs-lookup"><span data-stu-id="480c2-117">A custom assembly implementing the **IResolveProvider** interface</span></span>  

- <span data-ttu-id="480c2-118">XPath 查詢放在訊息</span><span class="sxs-lookup"><span data-stu-id="480c2-118">An XPath query over the message</span></span>  

- <span data-ttu-id="480c2-119">通用描述、 探索與整合 (UDDI) 查閱</span><span class="sxs-lookup"><span data-stu-id="480c2-119">A Universal Description, Discovery, and Integration (UDDI) lookup</span></span>
