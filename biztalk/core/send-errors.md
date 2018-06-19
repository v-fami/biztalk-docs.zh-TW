---
title: 將錯誤傳送 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3cf61c82-ad48-4555-af53-fb841fd0f503
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67741af0520d990be9a552685c8319aa6a5ae881
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269814"
---
# <a name="send-errors"></a><span data-ttu-id="48ffe-102">傳送錯誤</span><span class="sxs-lookup"><span data-stu-id="48ffe-102">Send Errors</span></span>
<span data-ttu-id="48ffe-103">診斷及解決 WCF 傳送錯誤的資訊。</span><span class="sxs-lookup"><span data-stu-id="48ffe-103">Information for diagnosing and resolving WCF Send errors.</span></span>  
  
## <a name="failed-to-generate-odx-file"></a><span data-ttu-id="48ffe-104">無法產生 ODX 檔案</span><span class="sxs-lookup"><span data-stu-id="48ffe-104">Failed to generate ODX file</span></span>

||<span data-ttu-id="48ffe-105">錯誤詳細資料</span><span class="sxs-lookup"><span data-stu-id="48ffe-105">Error details</span></span>|  
|-|-|  
|<span data-ttu-id="48ffe-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="48ffe-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="48ffe-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="48ffe-107">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="48ffe-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="48ffe-108">Event ID</span></span>|<span data-ttu-id="48ffe-109">0</span><span class="sxs-lookup"><span data-stu-id="48ffe-109">0</span></span>|  
|<span data-ttu-id="48ffe-110">事件來源</span><span class="sxs-lookup"><span data-stu-id="48ffe-110">Event Source</span></span>|<span data-ttu-id="48ffe-111">0</span><span class="sxs-lookup"><span data-stu-id="48ffe-111">0</span></span>|  
|<span data-ttu-id="48ffe-112">元件</span><span class="sxs-lookup"><span data-stu-id="48ffe-112">Component</span></span>|<span data-ttu-id="48ffe-113">0</span><span class="sxs-lookup"><span data-stu-id="48ffe-113">0</span></span>|  
|<span data-ttu-id="48ffe-114">符號名稱</span><span class="sxs-lookup"><span data-stu-id="48ffe-114">Symbolic Name</span></span>|<span data-ttu-id="48ffe-115">0</span><span class="sxs-lookup"><span data-stu-id="48ffe-115">0</span></span>|  
|<span data-ttu-id="48ffe-116">訊息文字</span><span class="sxs-lookup"><span data-stu-id="48ffe-116">Message Text</span></span>|<span data-ttu-id="48ffe-117">無法產生 ODX 檔案</span><span class="sxs-lookup"><span data-stu-id="48ffe-117">Failed to generate ODX file</span></span>|  
  
### <a name="explanation"></a><span data-ttu-id="48ffe-118">說明</span><span class="sxs-lookup"><span data-stu-id="48ffe-118">Explanation</span></span>  
 <span data-ttu-id="48ffe-119">此錯誤表示在使用服務時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="48ffe-119">This error indicates there was an error in consuming the service.</span></span>  
  
### <a name="user-action"></a><span data-ttu-id="48ffe-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="48ffe-120">User Action</span></span>  
 <span data-ttu-id="48ffe-121">請檢查服務具有有效的 Web 方法，以及 （如果您擁有的 WCF 服務） 裝載該中繼資料。</span><span class="sxs-lookup"><span data-stu-id="48ffe-121">Check that the service has valid Web Method and that metadata is hosted (if you own the WCF services).</span></span> <span data-ttu-id="48ffe-122">否則，請連絡服務提供者。</span><span class="sxs-lookup"><span data-stu-id="48ffe-122">Otherwise, contact the service provider.</span></span>  
  
 <span data-ttu-id="48ffe-123">如需有關如何使用 WCF 服務的詳細資訊，請參閱[考量取用 WCF 服務時使用 WCF 傳送配接器](../core/considerations-when-consuming-wcf-services-with-the-wcf-send-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="48ffe-123">For additional information on consuming WCF services, see [Considerations When Consuming WCF Services with the WCF Send Adapters](../core/considerations-when-consuming-wcf-services-with-the-wcf-send-adapters.md).</span></span>
 
## <a name="response-message-body-was-not-read"></a><span data-ttu-id="48ffe-124">未讀取回應訊息內文</span><span class="sxs-lookup"><span data-stu-id="48ffe-124">Response message body was not read</span></span>
  
||<span data-ttu-id="48ffe-125">錯誤詳細資料</span><span class="sxs-lookup"><span data-stu-id="48ffe-125">Error details</span></span>|  
|-|-|  
|<span data-ttu-id="48ffe-126">產品名稱</span><span class="sxs-lookup"><span data-stu-id="48ffe-126">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="48ffe-127">產品版本</span><span class="sxs-lookup"><span data-stu-id="48ffe-127">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="48ffe-128">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="48ffe-128">Event ID</span></span>|<span data-ttu-id="48ffe-129">0</span><span class="sxs-lookup"><span data-stu-id="48ffe-129">0</span></span>|  
|<span data-ttu-id="48ffe-130">事件來源</span><span class="sxs-lookup"><span data-stu-id="48ffe-130">Event Source</span></span>|<span data-ttu-id="48ffe-131">0</span><span class="sxs-lookup"><span data-stu-id="48ffe-131">0</span></span>|  
|<span data-ttu-id="48ffe-132">元件</span><span class="sxs-lookup"><span data-stu-id="48ffe-132">Component</span></span>|<span data-ttu-id="48ffe-133">0</span><span class="sxs-lookup"><span data-stu-id="48ffe-133">0</span></span>|  
|<span data-ttu-id="48ffe-134">符號名稱</span><span class="sxs-lookup"><span data-stu-id="48ffe-134">Symbolic Name</span></span>|<span data-ttu-id="48ffe-135">0</span><span class="sxs-lookup"><span data-stu-id="48ffe-135">0</span></span>|  
|<span data-ttu-id="48ffe-136">訊息文字</span><span class="sxs-lookup"><span data-stu-id="48ffe-136">Message Text</span></span>|<span data-ttu-id="48ffe-137">未讀取回應訊息內文 （這可能表示連接已經關閉。）</span><span class="sxs-lookup"><span data-stu-id="48ffe-137">The response message body was not read  (This may indicate the connection has been closed.)</span></span>|  
  
### <a name="explanation"></a><span data-ttu-id="48ffe-138">說明</span><span class="sxs-lookup"><span data-stu-id="48ffe-138">Explanation</span></span>  
 <span data-ttu-id="48ffe-139">回應訊息傳送回之前，用戶端可能會中斷。</span><span class="sxs-lookup"><span data-stu-id="48ffe-139">The client may be disconnected before the response message is sent back.</span></span>  
  
### <a name="user-action"></a><span data-ttu-id="48ffe-140">使用者動作</span><span class="sxs-lookup"><span data-stu-id="48ffe-140">User Action</span></span>  
 <span data-ttu-id="48ffe-141">請檢查用戶端連接性。</span><span class="sxs-lookup"><span data-stu-id="48ffe-141">Check the client connectivity.</span></span> <span data-ttu-id="48ffe-142">採取的步驟和動作的範圍取決於連接埠類型。</span><span class="sxs-lookup"><span data-stu-id="48ffe-142">The steps taken, and the extent of the action, will depend on the port type.</span></span>   
<span data-ttu-id="48ffe-143">如需詳細資訊，請參閱[工具和公用程式，以供疑難排解使用](../core/tools-and-utilities-to-use-for-troubleshooting.md)。</span><span class="sxs-lookup"><span data-stu-id="48ffe-143">For further information, see [Tools and Utilities to Use for Troubleshooting](../core/tools-and-utilities-to-use-for-troubleshooting.md).</span></span>