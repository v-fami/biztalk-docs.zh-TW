---
title: "連接埠組態錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 92eae0d8-a0c4-4f8c-b91a-fd98b9f6931a
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f0e51c06fab9dadb60fc43a003108e50bbb0fab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="port-configuration-errors"></a><span data-ttu-id="f2241-102">連接埠組態錯誤</span><span class="sxs-lookup"><span data-stu-id="f2241-102">Port Configuration Errors</span></span>
<span data-ttu-id="f2241-103">診斷及解決 WCF 通訊埠組態錯誤的資訊。</span><span class="sxs-lookup"><span data-stu-id="f2241-103">Information for diagnosing and resolving WCF Port Configuration errors.</span></span>  

## <a name="cannot-merge-operation-due-to-communication-pattern-conflict"></a><span data-ttu-id="f2241-104">無法合併操作，因為通訊模式衝突</span><span class="sxs-lookup"><span data-stu-id="f2241-104">Cannot merge operation due to communication pattern conflict</span></span>
  
||<span data-ttu-id="f2241-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f2241-105">Details</span></span>|  
|-|-|  
|<span data-ttu-id="f2241-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f2241-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f2241-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="f2241-107">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="f2241-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f2241-108">Event ID</span></span>|<span data-ttu-id="f2241-109">0</span><span class="sxs-lookup"><span data-stu-id="f2241-109">0</span></span>|  
|<span data-ttu-id="f2241-110">事件來源</span><span class="sxs-lookup"><span data-stu-id="f2241-110">Event Source</span></span>|<span data-ttu-id="f2241-111">0</span><span class="sxs-lookup"><span data-stu-id="f2241-111">0</span></span>|  
|<span data-ttu-id="f2241-112">元件</span><span class="sxs-lookup"><span data-stu-id="f2241-112">Component</span></span>|<span data-ttu-id="f2241-113">0</span><span class="sxs-lookup"><span data-stu-id="f2241-113">0</span></span>|  
|<span data-ttu-id="f2241-114">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f2241-114">Symbolic Name</span></span>|<span data-ttu-id="f2241-115">0</span><span class="sxs-lookup"><span data-stu-id="f2241-115">0</span></span>|  
|<span data-ttu-id="f2241-116">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f2241-116">Message Text</span></span>|<span data-ttu-id="f2241-117">無法合併操作"{0}"，因為通訊模式衝突。</span><span class="sxs-lookup"><span data-stu-id="f2241-117">Cannot merge operation "{0}" due to communication pattern conflict.</span></span>  <span data-ttu-id="f2241-118">所有作業必須都為單向或要求-回應</span><span class="sxs-lookup"><span data-stu-id="f2241-118">All operations must be one-way or request-response</span></span>|  
  
### <a name="explanation"></a><span data-ttu-id="f2241-119">說明</span><span class="sxs-lookup"><span data-stu-id="f2241-119">Explanation</span></span>  
 <span data-ttu-id="f2241-120">此錯誤表示[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]嘗試合併具有不同的通訊模式的連接埠類型的連接埠。</span><span class="sxs-lookup"><span data-stu-id="f2241-120">This error indicates [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is attempting to merge ports with port types that have different communication patterns.</span></span>  
  
### <a name="user-action"></a><span data-ttu-id="f2241-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f2241-121">User Action</span></span>  
 <span data-ttu-id="f2241-122">使用連接埠組態精靈中，請確定正在進行合併的所有連接埠具有相同的通訊方向可能是單向或要求-回應。</span><span class="sxs-lookup"><span data-stu-id="f2241-122">Using the Port Configuration Wizard, ensure that all the ports that are being merged have the same communication direction, either one-way or request-response.</span></span>  
  
 <span data-ttu-id="f2241-123">如需有關通訊埠組態的詳細資訊，請參閱[如何執行連接埠組態精靈](../core/how-to-run-the-port-configuration-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="f2241-123">For additional information on port configuration, see [How to Run the Port Configuration Wizard](../core/how-to-run-the-port-configuration-wizard.md).</span></span>
 
## <a name="port-types-that-have-a-combination-of-one-way-and-request-response-operations-are-not-allowed"></a><span data-ttu-id="f2241-124">連接埠類型具有多種單向和要求-回應作業不允許</span><span class="sxs-lookup"><span data-stu-id="f2241-124">Port types that have a combination of one-way and request-response operations are not allowed</span></span> 
  
||<span data-ttu-id="f2241-125">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f2241-125">Details</span></span>|  
|-|-|  
|<span data-ttu-id="f2241-126">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f2241-126">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f2241-127">產品版本</span><span class="sxs-lookup"><span data-stu-id="f2241-127">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="f2241-128">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f2241-128">Event ID</span></span>|<span data-ttu-id="f2241-129">0</span><span class="sxs-lookup"><span data-stu-id="f2241-129">0</span></span>|  
|<span data-ttu-id="f2241-130">事件來源</span><span class="sxs-lookup"><span data-stu-id="f2241-130">Event Source</span></span>|<span data-ttu-id="f2241-131">0</span><span class="sxs-lookup"><span data-stu-id="f2241-131">0</span></span>|  
|<span data-ttu-id="f2241-132">元件</span><span class="sxs-lookup"><span data-stu-id="f2241-132">Component</span></span>|<span data-ttu-id="f2241-133">0</span><span class="sxs-lookup"><span data-stu-id="f2241-133">0</span></span>|  
|<span data-ttu-id="f2241-134">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f2241-134">Symbolic Name</span></span>|<span data-ttu-id="f2241-135">0</span><span class="sxs-lookup"><span data-stu-id="f2241-135">0</span></span>|  
|<span data-ttu-id="f2241-136">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f2241-136">Message Text</span></span>|<span data-ttu-id="f2241-137">連接埠類型具有單向的組合，而且不允許要求-回應作業。</span><span class="sxs-lookup"><span data-stu-id="f2241-137">Port types that have a combination of one-way and request-response operations are not allowed.</span></span> <span data-ttu-id="f2241-138">更正服務描述"{0}"連接埠類型 」 {1}"，然後再重新執行精靈</span><span class="sxs-lookup"><span data-stu-id="f2241-138">Correct service description "{0}" port type "{1}" and rerun the wizard</span></span>|  
  
### <a name="explanation"></a><span data-ttu-id="f2241-139">說明</span><span class="sxs-lookup"><span data-stu-id="f2241-139">Explanation</span></span>  
 <span data-ttu-id="f2241-140">此錯誤表示嘗試從中使用此服務有單向和雙向作業 （或要求-回應）。</span><span class="sxs-lookup"><span data-stu-id="f2241-140">This error indicates the service trying to be consumed has operations that are both one-way and two-way (or request-response).</span></span>  
  
### <a name="user-action"></a><span data-ttu-id="f2241-141">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f2241-141">User Action</span></span>  
 <span data-ttu-id="f2241-142">更正的適當作業的服務 (可能是單向或要求-回應，但非兩者)，然後再次嘗試使用 （如果您擁有想要使用的 WCF 服務）。</span><span class="sxs-lookup"><span data-stu-id="f2241-142">Correct the service with the appropriate operations (either one-way or request-response but not both) and try to consume (if you own the WCF services that you are trying to consume).</span></span> <span data-ttu-id="f2241-143">否則，請連絡服務提供者。</span><span class="sxs-lookup"><span data-stu-id="f2241-143">Otherwise, contact the service provider.</span></span>
