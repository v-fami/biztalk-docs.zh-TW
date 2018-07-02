---
title: 將錯誤傳送 |Microsoft Docs
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
ms.openlocfilehash: 76aa238227877ab70328e585d5d12b8c428e9061
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983320"
---
# <a name="send-errors"></a><span data-ttu-id="c37ef-102">傳送錯誤</span><span class="sxs-lookup"><span data-stu-id="c37ef-102">Send Errors</span></span>
<span data-ttu-id="c37ef-103">診斷及解決 WCF 傳送錯誤的資訊。</span><span class="sxs-lookup"><span data-stu-id="c37ef-103">Information for diagnosing and resolving WCF Send errors.</span></span>  
  
## <a name="failed-to-generate-odx-file"></a><span data-ttu-id="c37ef-104">無法產生 ODX 檔案</span><span class="sxs-lookup"><span data-stu-id="c37ef-104">Failed to generate ODX file</span></span>

|                 |                                   <span data-ttu-id="c37ef-105">錯誤詳細資料</span><span class="sxs-lookup"><span data-stu-id="c37ef-105">Error details</span></span>                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="c37ef-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c37ef-106">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="c37ef-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="c37ef-107">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="c37ef-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c37ef-108">Event ID</span></span>     |                                         <span data-ttu-id="c37ef-109">0</span><span class="sxs-lookup"><span data-stu-id="c37ef-109">0</span></span>                                          |
|  <span data-ttu-id="c37ef-110">事件來源</span><span class="sxs-lookup"><span data-stu-id="c37ef-110">Event Source</span></span>   |                                         <span data-ttu-id="c37ef-111">0</span><span class="sxs-lookup"><span data-stu-id="c37ef-111">0</span></span>                                          |
|    <span data-ttu-id="c37ef-112">元件</span><span class="sxs-lookup"><span data-stu-id="c37ef-112">Component</span></span>    |                                         <span data-ttu-id="c37ef-113">0</span><span class="sxs-lookup"><span data-stu-id="c37ef-113">0</span></span>                                          |
|  <span data-ttu-id="c37ef-114">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c37ef-114">Symbolic Name</span></span>  |                                         <span data-ttu-id="c37ef-115">0</span><span class="sxs-lookup"><span data-stu-id="c37ef-115">0</span></span>                                          |
|  <span data-ttu-id="c37ef-116">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c37ef-116">Message Text</span></span>   |                            <span data-ttu-id="c37ef-117">無法產生 ODX 檔案</span><span class="sxs-lookup"><span data-stu-id="c37ef-117">Failed to generate ODX file</span></span>                             |
  
### <a name="explanation"></a><span data-ttu-id="c37ef-118">說明</span><span class="sxs-lookup"><span data-stu-id="c37ef-118">Explanation</span></span>  
 <span data-ttu-id="c37ef-119">此錯誤表示在使用服務時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c37ef-119">This error indicates there was an error in consuming the service.</span></span>  
  
### <a name="user-action"></a><span data-ttu-id="c37ef-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c37ef-120">User Action</span></span>  
 <span data-ttu-id="c37ef-121">請檢查服務有沒有有效的 Web 方法，該中繼資料裝載 （如果您擁有的 WCF 服務時）。</span><span class="sxs-lookup"><span data-stu-id="c37ef-121">Check that the service has valid Web Method and that metadata is hosted (if you own the WCF services).</span></span> <span data-ttu-id="c37ef-122">否則，請連絡服務提供者。</span><span class="sxs-lookup"><span data-stu-id="c37ef-122">Otherwise, contact the service provider.</span></span>  
  
 <span data-ttu-id="c37ef-123">如需有關如何使用 WCF 服務的詳細資訊，請參閱[考量時使用 WCF 服務使用 WCF 傳送配接器](../core/considerations-when-consuming-wcf-services-with-the-wcf-send-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="c37ef-123">For additional information on consuming WCF services, see [Considerations When Consuming WCF Services with the WCF Send Adapters](../core/considerations-when-consuming-wcf-services-with-the-wcf-send-adapters.md).</span></span>
 
## <a name="response-message-body-was-not-read"></a><span data-ttu-id="c37ef-124">未讀取回應訊息內文</span><span class="sxs-lookup"><span data-stu-id="c37ef-124">Response message body was not read</span></span>
  
|                 |                                        <span data-ttu-id="c37ef-125">錯誤詳細資料</span><span class="sxs-lookup"><span data-stu-id="c37ef-125">Error details</span></span>                                        |
|-----------------|---------------------------------------------------------------------------------------------|
|  <span data-ttu-id="c37ef-126">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c37ef-126">Product Name</span></span>   |     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]      |
| <span data-ttu-id="c37ef-127">產品版本</span><span class="sxs-lookup"><span data-stu-id="c37ef-127">Product Version</span></span> |                 [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                  |
|    <span data-ttu-id="c37ef-128">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c37ef-128">Event ID</span></span>     |                                              <span data-ttu-id="c37ef-129">0</span><span class="sxs-lookup"><span data-stu-id="c37ef-129">0</span></span>                                              |
|  <span data-ttu-id="c37ef-130">事件來源</span><span class="sxs-lookup"><span data-stu-id="c37ef-130">Event Source</span></span>   |                                              <span data-ttu-id="c37ef-131">0</span><span class="sxs-lookup"><span data-stu-id="c37ef-131">0</span></span>                                              |
|    <span data-ttu-id="c37ef-132">元件</span><span class="sxs-lookup"><span data-stu-id="c37ef-132">Component</span></span>    |                                              <span data-ttu-id="c37ef-133">0</span><span class="sxs-lookup"><span data-stu-id="c37ef-133">0</span></span>                                              |
|  <span data-ttu-id="c37ef-134">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c37ef-134">Symbolic Name</span></span>  |                                              <span data-ttu-id="c37ef-135">0</span><span class="sxs-lookup"><span data-stu-id="c37ef-135">0</span></span>                                              |
|  <span data-ttu-id="c37ef-136">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c37ef-136">Message Text</span></span>   | <span data-ttu-id="c37ef-137">未讀取回應訊息內文 （這可能表示連接已經關閉。）</span><span class="sxs-lookup"><span data-stu-id="c37ef-137">The response message body was not read  (This may indicate the connection has been closed.)</span></span> |
  
### <a name="explanation"></a><span data-ttu-id="c37ef-138">說明</span><span class="sxs-lookup"><span data-stu-id="c37ef-138">Explanation</span></span>  
 <span data-ttu-id="c37ef-139">回應訊息傳送回之前，可能會中斷用戶端的連線。</span><span class="sxs-lookup"><span data-stu-id="c37ef-139">The client may be disconnected before the response message is sent back.</span></span>  
  
### <a name="user-action"></a><span data-ttu-id="c37ef-140">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c37ef-140">User Action</span></span>  
 <span data-ttu-id="c37ef-141">請檢查用戶端連接性。</span><span class="sxs-lookup"><span data-stu-id="c37ef-141">Check the client connectivity.</span></span> <span data-ttu-id="c37ef-142">採取的步驟和動作的範圍取決於連接埠類型。</span><span class="sxs-lookup"><span data-stu-id="c37ef-142">The steps taken, and the extent of the action, will depend on the port type.</span></span>   
<span data-ttu-id="c37ef-143">如需詳細資訊，請參閱 <<c0> [ 工具和公用程式來使用，以進行疑難排解](../core/tools-and-utilities-to-use-for-troubleshooting.md)。</span><span class="sxs-lookup"><span data-stu-id="c37ef-143">For further information, see [Tools and Utilities to Use for Troubleshooting](../core/tools-and-utilities-to-use-for-troubleshooting.md).</span></span>