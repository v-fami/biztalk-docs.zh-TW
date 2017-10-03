---
title: "中繼資料錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ccb60c91-5905-4852-813b-586b82de4825
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4dce5fc9eb944eccbeed57073c2546f81825ec6f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="metadata-errors"></a><span data-ttu-id="81b92-102">中繼資料錯誤</span><span class="sxs-lookup"><span data-stu-id="81b92-102">Metadata Errors</span></span>
<span data-ttu-id="81b92-103">診斷及解決 WCF 中繼資料錯誤的資訊。</span><span class="sxs-lookup"><span data-stu-id="81b92-103">Information for diagnosing and resolving WCF Metadata errors.</span></span>  
  
## <a name="error-consuming-wcf-service-metadata"></a><span data-ttu-id="81b92-104">取用 WCF 服務中繼資料時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="81b92-104">Error consuming WCF service metadata</span></span>

||<span data-ttu-id="81b92-105">錯誤詳細資料</span><span class="sxs-lookup"><span data-stu-id="81b92-105">Error details</span></span>|  
|-|-|  
|<span data-ttu-id="81b92-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="81b92-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="81b92-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="81b92-107">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="81b92-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="81b92-108">Event ID</span></span>|<span data-ttu-id="81b92-109">0</span><span class="sxs-lookup"><span data-stu-id="81b92-109">0</span></span>|  
|<span data-ttu-id="81b92-110">事件來源</span><span class="sxs-lookup"><span data-stu-id="81b92-110">Event Source</span></span>|<span data-ttu-id="81b92-111">0</span><span class="sxs-lookup"><span data-stu-id="81b92-111">0</span></span>|  
|<span data-ttu-id="81b92-112">元件</span><span class="sxs-lookup"><span data-stu-id="81b92-112">Component</span></span>|<span data-ttu-id="81b92-113">0</span><span class="sxs-lookup"><span data-stu-id="81b92-113">0</span></span>|  
|<span data-ttu-id="81b92-114">符號名稱</span><span class="sxs-lookup"><span data-stu-id="81b92-114">Symbolic Name</span></span>|<span data-ttu-id="81b92-115">0</span><span class="sxs-lookup"><span data-stu-id="81b92-115">0</span></span>|  
|<span data-ttu-id="81b92-116">訊息文字</span><span class="sxs-lookup"><span data-stu-id="81b92-116">Message Text</span></span>|<span data-ttu-id="81b92-117">取用 WCF 服務中繼資料時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="81b92-117">Error consuming WCF service metadata</span></span>|  
  
### <a name="explanation"></a><span data-ttu-id="81b92-118">說明</span><span class="sxs-lookup"><span data-stu-id="81b92-118">Explanation</span></span>  
 <span data-ttu-id="81b92-119">此錯誤表示中繼資料可供服務未使用或不正確。</span><span class="sxs-lookup"><span data-stu-id="81b92-119">This error indicates the metadata for the service is either not available or is not valid.</span></span>  
  
### <a name="user-action"></a><span data-ttu-id="81b92-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="81b92-120">User Action</span></span>  
 <span data-ttu-id="81b92-121">更正服務中繼資料，並嘗試使用 （如果您擁有想要使用的 WCF 服務）。</span><span class="sxs-lookup"><span data-stu-id="81b92-121">Correct the service metadata and try to consume (if you own the WCF service you are trying to consume).</span></span> <span data-ttu-id="81b92-122">移至服務組態編輯器 (**svcConfigEditor.exe**) 並對組態檔進行變更。</span><span class="sxs-lookup"><span data-stu-id="81b92-122">Go to the Service Configuration Editor (**svcConfigEditor.exe**) and make changes to the configuration file.</span></span>  <span data-ttu-id="81b92-123">否則，請連絡服務提供者</span><span class="sxs-lookup"><span data-stu-id="81b92-123">Otherwise, contact the service provider</span></span>

## <a name="failed-to-get-metadata"></a><span data-ttu-id="81b92-124">無法取得中繼資料</span><span class="sxs-lookup"><span data-stu-id="81b92-124">Failed to get metadata</span></span>

||<span data-ttu-id="81b92-125">錯誤詳細資料</span><span class="sxs-lookup"><span data-stu-id="81b92-125">Error details</span></span>|  
|-|-|  
|<span data-ttu-id="81b92-126">產品名稱</span><span class="sxs-lookup"><span data-stu-id="81b92-126">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="81b92-127">產品版本</span><span class="sxs-lookup"><span data-stu-id="81b92-127">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="81b92-128">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="81b92-128">Event ID</span></span>|<span data-ttu-id="81b92-129">0</span><span class="sxs-lookup"><span data-stu-id="81b92-129">0</span></span>|  
|<span data-ttu-id="81b92-130">事件來源</span><span class="sxs-lookup"><span data-stu-id="81b92-130">Event Source</span></span>|<span data-ttu-id="81b92-131">0</span><span class="sxs-lookup"><span data-stu-id="81b92-131">0</span></span>|  
|<span data-ttu-id="81b92-132">元件</span><span class="sxs-lookup"><span data-stu-id="81b92-132">Component</span></span>|<span data-ttu-id="81b92-133">0</span><span class="sxs-lookup"><span data-stu-id="81b92-133">0</span></span>|  
|<span data-ttu-id="81b92-134">符號名稱</span><span class="sxs-lookup"><span data-stu-id="81b92-134">Symbolic Name</span></span>|<span data-ttu-id="81b92-135">0</span><span class="sxs-lookup"><span data-stu-id="81b92-135">0</span></span>|  
|<span data-ttu-id="81b92-136">訊息文字</span><span class="sxs-lookup"><span data-stu-id="81b92-136">Message Text</span></span>|<span data-ttu-id="81b92-137">無法從 "{0}" 取得中繼資料</span><span class="sxs-lookup"><span data-stu-id="81b92-137">Failed to get metadata from "{0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="81b92-138">說明</span><span class="sxs-lookup"><span data-stu-id="81b92-138">Explanation</span></span>  
 <span data-ttu-id="81b92-139">此錯誤表示沒有可供該服務的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="81b92-139">This error indicates the metadata is not available for that service.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="81b92-140">使用者動作</span><span class="sxs-lookup"><span data-stu-id="81b92-140">User Action</span></span>  
 <span data-ttu-id="81b92-141">啟用服務的中繼資料，然後再次執行使用精靈，（如果您擁有想要使用的 WCF 服務）。</span><span class="sxs-lookup"><span data-stu-id="81b92-141">Enable metadata for the service and run the consuming wizard again (if you own the WCF service you are trying to consume).</span></span> <span data-ttu-id="81b92-142">否則，請連絡服務提供者。</span><span class="sxs-lookup"><span data-stu-id="81b92-142">Otherwise, contact the service provider.</span></span>