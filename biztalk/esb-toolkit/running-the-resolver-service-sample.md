---
title: "執行 「 解析程式服務 」 範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4bf0b21-6aa0-4524-9e63-93a172845d4a
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb9d7e3e4d4bce4e46653f7b650004928368eced
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-resolver-service-sample"></a><span data-ttu-id="e8b90-102">執行解析程式服務範例</span><span class="sxs-lookup"><span data-stu-id="e8b90-102">Running the Resolver Service Sample</span></span>
<span data-ttu-id="e8b90-103">此解析程式服務範例會示範下列情況：</span><span class="sxs-lookup"><span data-stu-id="e8b90-103">The Resolver Service sample demonstrates the following scenarios:</span></span>  
  
-   <span data-ttu-id="e8b90-104">解決服務端點 URI 從 UDDI3 使用繫結索引鍵</span><span class="sxs-lookup"><span data-stu-id="e8b90-104">Resolve a service endpoint URI from UDDI3 using a binding key</span></span>  
  
-   <span data-ttu-id="e8b90-105">解決服務端點 URI 從 UDDI3 使用分類搜尋</span><span class="sxs-lookup"><span data-stu-id="e8b90-105">Resolve a service endpoint URI from UDDI3 using a categorization search</span></span>  
  
-   <span data-ttu-id="e8b90-106">解決使用靜態的解析程式的轉換 （BizTalk 對應型別）</span><span class="sxs-lookup"><span data-stu-id="e8b90-106">Resolve a transformation (BizTalk Map type) using a STATIC resolver</span></span>  
  
-   <span data-ttu-id="e8b90-107">解決服務端點 URI 使用靜態的解析程式</span><span class="sxs-lookup"><span data-stu-id="e8b90-107">Resolve a service endpoint URI using a STATIC resolver</span></span>  
  
-   <span data-ttu-id="e8b90-108">解決服務端點 URI 使用 XPath 運算式</span><span class="sxs-lookup"><span data-stu-id="e8b90-108">Resolve a service endpoint URI using an XPath expression</span></span>  
  
-   <span data-ttu-id="e8b90-109">解決使用靜態的行程解析程式路線</span><span class="sxs-lookup"><span data-stu-id="e8b90-109">Resolve an itinerary using a static ITINERARY resolver</span></span>  
  
-   <span data-ttu-id="e8b90-110">解決使用路線靜態 (Unity) 解析程式路線</span><span class="sxs-lookup"><span data-stu-id="e8b90-110">Resolve an itinerary using an ITINERARY-STATIC (Unity) resolver</span></span>  
  
-   <span data-ttu-id="e8b90-111">解決使用 BRE （BRI 解析程式） 路線</span><span class="sxs-lookup"><span data-stu-id="e8b90-111">Resolve an itinerary using BRE (BRI Resolver)</span></span>  
  
-   <span data-ttu-id="e8b90-112">解決使用 BRE （BRI 解析程式） 與訊息路線</span><span class="sxs-lookup"><span data-stu-id="e8b90-112">Resolve an Itinerary using BRE (BRI Resolver) with the Message</span></span>  
  
-   <span data-ttu-id="e8b90-113">解決服務端點 URI 使用 BRE</span><span class="sxs-lookup"><span data-stu-id="e8b90-113">Resolve a service endpoint URI using BRE</span></span>  
  
-   <span data-ttu-id="e8b90-114">解決使用 BRE 的轉換</span><span class="sxs-lookup"><span data-stu-id="e8b90-114">Resolve a transformation using BRE</span></span>  
  
 <span data-ttu-id="e8b90-115">**若要執行所有使用解析程式服務的 ASMX 實作的解決方案案例**</span><span class="sxs-lookup"><span data-stu-id="e8b90-115">**To run all the resolution scenarios using the ASMX implementation of the Resolver service**</span></span>  
  
1.  <span data-ttu-id="e8b90-116">如果尚未執行 GlobalBank.ESB 應用程式，使用 Microsoft BizTalk 管理主控台來啟動它。</span><span class="sxs-lookup"><span data-stu-id="e8b90-116">If the GlobalBank.ESB application is not already running, use the Microsoft BizTalk Administration Console to start it.</span></span>  
  
2.  <span data-ttu-id="e8b90-117">在 Windows 檔案總管 中開啟 \Source\Samples\ResolverService 資料夾，然後按兩下檔案 RunTestClient_ASMX.cmd。</span><span class="sxs-lookup"><span data-stu-id="e8b90-117">In Windows Explorer, open the \Source\Samples\ResolverService folder, and then double-click the file RunTestClient_ASMX.cmd.</span></span>  
  
3.  <span data-ttu-id="e8b90-118">開啟 \Source\Samples\ResolverService\Output 資料夾，然後開啟 結果檔案，其對應至稍早所列的解析要求。</span><span class="sxs-lookup"><span data-stu-id="e8b90-118">Open the \Source\Samples\ResolverService\Output folder, and then open the result files, which correspond to the resolution requests listed earlier.</span></span>  
  
 <span data-ttu-id="e8b90-119">**若要執行所有使用解析程式服務的 WCF 實作的解決方案案例**</span><span class="sxs-lookup"><span data-stu-id="e8b90-119">**To run all the resolution scenarios using the WCF implementation of the Resolver service**</span></span>  
  
1.  <span data-ttu-id="e8b90-120">如果尚未執行 GlobalBank.ESB 應用程式，使用 BizTalk 管理主控台來啟動它。</span><span class="sxs-lookup"><span data-stu-id="e8b90-120">If the GlobalBank.ESB application is not already running, use the BizTalk Administration Console to start it.</span></span>  
  
2.  <span data-ttu-id="e8b90-121">在 Windows 檔案總管 中開啟 \Source\Samples\ResolverService 資料夾，然後按兩下檔案 RunTestClient_WCF.cmd。</span><span class="sxs-lookup"><span data-stu-id="e8b90-121">In Windows Explorer, open the \Source\Samples\ResolverService folder, and then double-click the file RunTestClient_WCF.cmd.</span></span>  
  
3.  <span data-ttu-id="e8b90-122">開啟 \Source\Samples\ResolverService\Output 資料夾，然後開啟 結果檔案，其對應至稍早所列的解析要求。</span><span class="sxs-lookup"><span data-stu-id="e8b90-122">Open the \Source\Samples\ResolverService\Output folder, and then open the result files, which correspond to the resolution requests listed earlier.</span></span>