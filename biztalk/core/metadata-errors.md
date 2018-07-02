---
title: 中繼資料錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ccb60c91-5905-4852-813b-586b82de4825
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07167c2c0189c36f7b1a321d81bd0070398953e8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975119"
---
# <a name="metadata-errors"></a><span data-ttu-id="5baaa-102">中繼資料錯誤</span><span class="sxs-lookup"><span data-stu-id="5baaa-102">Metadata Errors</span></span>
<span data-ttu-id="5baaa-103">診斷及解決 WCF 中繼資料錯誤的資訊。</span><span class="sxs-lookup"><span data-stu-id="5baaa-103">Information for diagnosing and resolving WCF Metadata errors.</span></span>  
  
## <a name="error-consuming-wcf-service-metadata"></a><span data-ttu-id="5baaa-104">取用 WCF 服務中繼資料時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="5baaa-104">Error consuming WCF service metadata</span></span>

|                 |                                   <span data-ttu-id="5baaa-105">錯誤詳細資料</span><span class="sxs-lookup"><span data-stu-id="5baaa-105">Error details</span></span>                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="5baaa-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="5baaa-106">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="5baaa-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="5baaa-107">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="5baaa-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="5baaa-108">Event ID</span></span>     |                                         <span data-ttu-id="5baaa-109">0</span><span class="sxs-lookup"><span data-stu-id="5baaa-109">0</span></span>                                          |
|  <span data-ttu-id="5baaa-110">事件來源</span><span class="sxs-lookup"><span data-stu-id="5baaa-110">Event Source</span></span>   |                                         <span data-ttu-id="5baaa-111">0</span><span class="sxs-lookup"><span data-stu-id="5baaa-111">0</span></span>                                          |
|    <span data-ttu-id="5baaa-112">元件</span><span class="sxs-lookup"><span data-stu-id="5baaa-112">Component</span></span>    |                                         <span data-ttu-id="5baaa-113">0</span><span class="sxs-lookup"><span data-stu-id="5baaa-113">0</span></span>                                          |
|  <span data-ttu-id="5baaa-114">符號名稱</span><span class="sxs-lookup"><span data-stu-id="5baaa-114">Symbolic Name</span></span>  |                                         <span data-ttu-id="5baaa-115">0</span><span class="sxs-lookup"><span data-stu-id="5baaa-115">0</span></span>                                          |
|  <span data-ttu-id="5baaa-116">訊息文字</span><span class="sxs-lookup"><span data-stu-id="5baaa-116">Message Text</span></span>   |                        <span data-ttu-id="5baaa-117">取用 WCF 服務中繼資料時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="5baaa-117">Error consuming WCF service metadata</span></span>                        |
  
### <a name="explanation"></a><span data-ttu-id="5baaa-118">說明</span><span class="sxs-lookup"><span data-stu-id="5baaa-118">Explanation</span></span>  
 <span data-ttu-id="5baaa-119">此錯誤表示中繼資料可供服務可能未提供或無效。</span><span class="sxs-lookup"><span data-stu-id="5baaa-119">This error indicates the metadata for the service is either not available or is not valid.</span></span>  
  
### <a name="user-action"></a><span data-ttu-id="5baaa-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="5baaa-120">User Action</span></span>  
 <span data-ttu-id="5baaa-121">更正的服務中繼資料，然後再次嘗試使用 （如果您擁有想要使用的 WCF 服務時）。</span><span class="sxs-lookup"><span data-stu-id="5baaa-121">Correct the service metadata and try to consume (if you own the WCF service you are trying to consume).</span></span> <span data-ttu-id="5baaa-122">移至 服務組態編輯器 (**svcConfigEditor.exe**) 並對組態檔進行變更。</span><span class="sxs-lookup"><span data-stu-id="5baaa-122">Go to the Service Configuration Editor (**svcConfigEditor.exe**) and make changes to the configuration file.</span></span>  <span data-ttu-id="5baaa-123">否則，請連絡服務提供者</span><span class="sxs-lookup"><span data-stu-id="5baaa-123">Otherwise, contact the service provider</span></span>

## <a name="failed-to-get-metadata"></a><span data-ttu-id="5baaa-124">無法取得中繼資料</span><span class="sxs-lookup"><span data-stu-id="5baaa-124">Failed to get metadata</span></span>

|                 |                                   <span data-ttu-id="5baaa-125">錯誤詳細資料</span><span class="sxs-lookup"><span data-stu-id="5baaa-125">Error details</span></span>                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="5baaa-126">產品名稱</span><span class="sxs-lookup"><span data-stu-id="5baaa-126">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="5baaa-127">產品版本</span><span class="sxs-lookup"><span data-stu-id="5baaa-127">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="5baaa-128">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="5baaa-128">Event ID</span></span>     |                                         <span data-ttu-id="5baaa-129">0</span><span class="sxs-lookup"><span data-stu-id="5baaa-129">0</span></span>                                          |
|  <span data-ttu-id="5baaa-130">事件來源</span><span class="sxs-lookup"><span data-stu-id="5baaa-130">Event Source</span></span>   |                                         <span data-ttu-id="5baaa-131">0</span><span class="sxs-lookup"><span data-stu-id="5baaa-131">0</span></span>                                          |
|    <span data-ttu-id="5baaa-132">元件</span><span class="sxs-lookup"><span data-stu-id="5baaa-132">Component</span></span>    |                                         <span data-ttu-id="5baaa-133">0</span><span class="sxs-lookup"><span data-stu-id="5baaa-133">0</span></span>                                          |
|  <span data-ttu-id="5baaa-134">符號名稱</span><span class="sxs-lookup"><span data-stu-id="5baaa-134">Symbolic Name</span></span>  |                                         <span data-ttu-id="5baaa-135">0</span><span class="sxs-lookup"><span data-stu-id="5baaa-135">0</span></span>                                          |
|  <span data-ttu-id="5baaa-136">訊息文字</span><span class="sxs-lookup"><span data-stu-id="5baaa-136">Message Text</span></span>   |                          <span data-ttu-id="5baaa-137">無法取得中繼資料 」{0}</span><span class="sxs-lookup"><span data-stu-id="5baaa-137">Failed to get metadata from "{0}</span></span>                          |
  
## <a name="explanation"></a><span data-ttu-id="5baaa-138">說明</span><span class="sxs-lookup"><span data-stu-id="5baaa-138">Explanation</span></span>  
 <span data-ttu-id="5baaa-139">此錯誤表示中繼資料不是適用於該服務。</span><span class="sxs-lookup"><span data-stu-id="5baaa-139">This error indicates the metadata is not available for that service.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5baaa-140">使用者動作</span><span class="sxs-lookup"><span data-stu-id="5baaa-140">User Action</span></span>  
 <span data-ttu-id="5baaa-141">啟用服務中繼資料並執行使用精靈一次 （如果您擁有想要使用的 WCF 服務時）。</span><span class="sxs-lookup"><span data-stu-id="5baaa-141">Enable metadata for the service and run the consuming wizard again (if you own the WCF service you are trying to consume).</span></span> <span data-ttu-id="5baaa-142">否則，請連絡服務提供者。</span><span class="sxs-lookup"><span data-stu-id="5baaa-142">Otherwise, contact the service provider.</span></span>