---
title: 執行解析程式服務範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4bf0b21-6aa0-4524-9e63-93a172845d4a
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21c569f0be544292b4a70d49f4c75a038e2fed65
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006671"
---
# <a name="running-the-resolver-service-sample"></a><span data-ttu-id="a1ceb-102">執行解析程式服務範例</span><span class="sxs-lookup"><span data-stu-id="a1ceb-102">Running the Resolver Service Sample</span></span>
<span data-ttu-id="a1ceb-103">解析程式服務範例會示範下列案例：</span><span class="sxs-lookup"><span data-stu-id="a1ceb-103">The Resolver Service sample demonstrates the following scenarios:</span></span>  

- <span data-ttu-id="a1ceb-104">解決服務端點 URI UDDI3 使用繫結索引鍵</span><span class="sxs-lookup"><span data-stu-id="a1ceb-104">Resolve a service endpoint URI from UDDI3 using a binding key</span></span>  

- <span data-ttu-id="a1ceb-105">解決服務端點 URI UDDI3 使用分類搜尋</span><span class="sxs-lookup"><span data-stu-id="a1ceb-105">Resolve a service endpoint URI from UDDI3 using a categorization search</span></span>  

- <span data-ttu-id="a1ceb-106">解決使用靜態的解析程式的轉換 （BizTalk 對應型別）</span><span class="sxs-lookup"><span data-stu-id="a1ceb-106">Resolve a transformation (BizTalk Map type) using a STATIC resolver</span></span>  

- <span data-ttu-id="a1ceb-107">解決服務端點使用靜態的解析程式的 URI</span><span class="sxs-lookup"><span data-stu-id="a1ceb-107">Resolve a service endpoint URI using a STATIC resolver</span></span>  

- <span data-ttu-id="a1ceb-108">解決服務端點 URI 使用 XPath 運算式</span><span class="sxs-lookup"><span data-stu-id="a1ceb-108">Resolve a service endpoint URI using an XPath expression</span></span>  

- <span data-ttu-id="a1ceb-109">解決使用靜態的路線解析程式路線</span><span class="sxs-lookup"><span data-stu-id="a1ceb-109">Resolve an itinerary using a static ITINERARY resolver</span></span>  

- <span data-ttu-id="a1ceb-110">解決使用路線靜態 (Unity) 解析程式路線</span><span class="sxs-lookup"><span data-stu-id="a1ceb-110">Resolve an itinerary using an ITINERARY-STATIC (Unity) resolver</span></span>  

- <span data-ttu-id="a1ceb-111">解決路線使用 BRE （BRI 解析程式）</span><span class="sxs-lookup"><span data-stu-id="a1ceb-111">Resolve an itinerary using BRE (BRI Resolver)</span></span>  

- <span data-ttu-id="a1ceb-112">解決使用 BRE （BRI 解析程式） 與訊息路線</span><span class="sxs-lookup"><span data-stu-id="a1ceb-112">Resolve an Itinerary using BRE (BRI Resolver) with the Message</span></span>  

- <span data-ttu-id="a1ceb-113">解決服務端點 URI 使用 BRE</span><span class="sxs-lookup"><span data-stu-id="a1ceb-113">Resolve a service endpoint URI using BRE</span></span>  

- <span data-ttu-id="a1ceb-114">解決使用 BRE 的轉換</span><span class="sxs-lookup"><span data-stu-id="a1ceb-114">Resolve a transformation using BRE</span></span>  

  <span data-ttu-id="a1ceb-115">**若要執行使用解析程式服務的 ASMX 實作的所有解析案例**</span><span class="sxs-lookup"><span data-stu-id="a1ceb-115">**To run all the resolution scenarios using the ASMX implementation of the Resolver service**</span></span>  

1. <span data-ttu-id="a1ceb-116">如果尚未執行 GlobalBank.ESB 應用程式，使用 Microsoft BizTalk 管理主控台來啟動它。</span><span class="sxs-lookup"><span data-stu-id="a1ceb-116">If the GlobalBank.ESB application is not already running, use the Microsoft BizTalk Administration Console to start it.</span></span>  

2. <span data-ttu-id="a1ceb-117">在 Windows 檔案總管中，開啟 \Source\Samples\ResolverService 資料夾中，，然後按兩下檔案 RunTestClient_ASMX.cmd。</span><span class="sxs-lookup"><span data-stu-id="a1ceb-117">In Windows Explorer, open the \Source\Samples\ResolverService folder, and then double-click the file RunTestClient_ASMX.cmd.</span></span>  

3. <span data-ttu-id="a1ceb-118">開啟 \Source\Samples\ResolverService\Output] 資料夾中，然後再開啟 [結果檔案，這會對應到稍早所列的解析要求。</span><span class="sxs-lookup"><span data-stu-id="a1ceb-118">Open the \Source\Samples\ResolverService\Output folder, and then open the result files, which correspond to the resolution requests listed earlier.</span></span>  

   <span data-ttu-id="a1ceb-119">**若要執行使用 WCF 實作的解析程式服務的所有解析案例**</span><span class="sxs-lookup"><span data-stu-id="a1ceb-119">**To run all the resolution scenarios using the WCF implementation of the Resolver service**</span></span>  

4. <span data-ttu-id="a1ceb-120">如果尚未執行 GlobalBank.ESB 應用程式，使用 BizTalk 管理主控台來啟動它。</span><span class="sxs-lookup"><span data-stu-id="a1ceb-120">If the GlobalBank.ESB application is not already running, use the BizTalk Administration Console to start it.</span></span>  

5. <span data-ttu-id="a1ceb-121">在 Windows 檔案總管中，開啟 \Source\Samples\ResolverService 資料夾中，，然後按兩下檔案 RunTestClient_WCF.cmd。</span><span class="sxs-lookup"><span data-stu-id="a1ceb-121">In Windows Explorer, open the \Source\Samples\ResolverService folder, and then double-click the file RunTestClient_WCF.cmd.</span></span>  

6. <span data-ttu-id="a1ceb-122">開啟 \Source\Samples\ResolverService\Output] 資料夾中，然後再開啟 [結果檔案，這會對應到稍早所列的解析要求。</span><span class="sxs-lookup"><span data-stu-id="a1ceb-122">Open the \Source\Samples\ResolverService\Output folder, and then open the result files, which correspond to the resolution requests listed earlier.</span></span>
