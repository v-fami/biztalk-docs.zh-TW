---
title: "登錄錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a5bf2cd-f807-4083-8687-4416a2ee2908
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c84ec2a1082f431fef8e06357f14cc9b621c6a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="registry-errors"></a><span data-ttu-id="d5bf1-102">登錄錯誤</span><span class="sxs-lookup"><span data-stu-id="d5bf1-102">Registry Errors</span></span>
<span data-ttu-id="d5bf1-103">診斷及解決 WCF 登錄錯誤的資訊。</span><span class="sxs-lookup"><span data-stu-id="d5bf1-103">Information for diagnosing and resolving WCF Registry errors.</span></span>  

## <a name="failed-to-access-the-registry"></a><span data-ttu-id="d5bf1-104">無法存取登錄</span><span class="sxs-lookup"><span data-stu-id="d5bf1-104">Failed to access the registry</span></span>
  
||<span data-ttu-id="d5bf1-105">錯誤詳細資料</span><span class="sxs-lookup"><span data-stu-id="d5bf1-105">Error details</span></span>|  
|-|-|  
|<span data-ttu-id="d5bf1-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d5bf1-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d5bf1-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="d5bf1-107">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="d5bf1-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d5bf1-108">Event ID</span></span>|<span data-ttu-id="d5bf1-109">0</span><span class="sxs-lookup"><span data-stu-id="d5bf1-109">0</span></span>|  
|<span data-ttu-id="d5bf1-110">事件來源</span><span class="sxs-lookup"><span data-stu-id="d5bf1-110">Event Source</span></span>|<span data-ttu-id="d5bf1-111">0</span><span class="sxs-lookup"><span data-stu-id="d5bf1-111">0</span></span>|  
|<span data-ttu-id="d5bf1-112">元件</span><span class="sxs-lookup"><span data-stu-id="d5bf1-112">Component</span></span>|<span data-ttu-id="d5bf1-113">0</span><span class="sxs-lookup"><span data-stu-id="d5bf1-113">0</span></span>|  
|<span data-ttu-id="d5bf1-114">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d5bf1-114">Symbolic Name</span></span>|<span data-ttu-id="d5bf1-115">0</span><span class="sxs-lookup"><span data-stu-id="d5bf1-115">0</span></span>|  
|<span data-ttu-id="d5bf1-116">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d5bf1-116">Message Text</span></span>|<span data-ttu-id="d5bf1-117">無法開啟 HKLM\\{0}。</span><span class="sxs-lookup"><span data-stu-id="d5bf1-117">Failed to open HKLM\\{0}.</span></span>|  
  
### <a name="explanation"></a><span data-ttu-id="d5bf1-118">說明</span><span class="sxs-lookup"><span data-stu-id="d5bf1-118">Explanation</span></span>  
 <span data-ttu-id="d5bf1-119">此錯誤表示無法存取登錄。</span><span class="sxs-lookup"><span data-stu-id="d5bf1-119">This error indicates a failure to access the registry.</span></span>  
  
### <a name="user-action"></a><span data-ttu-id="d5bf1-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d5bf1-120">User Action</span></span>  
 <span data-ttu-id="d5bf1-121">請確定您具有讀取存取登錄。</span><span class="sxs-lookup"><span data-stu-id="d5bf1-121">Ensure you have read access to the registry.</span></span> <span data-ttu-id="d5bf1-122">若要存取登錄，請確定您有系統管理員權限或連絡電腦的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="d5bf1-122">To access the registry, ensure you have Administrator privileges or contact the administrator of the machine.</span></span>
 
## <a name="failed-to-obtain-biztalk-install-path"></a><span data-ttu-id="d5bf1-123">無法取得 BizTalk 安裝路徑</span><span class="sxs-lookup"><span data-stu-id="d5bf1-123">Failed to obtain BizTalk install path</span></span>
  
||<span data-ttu-id="d5bf1-124">錯誤詳細資料</span><span class="sxs-lookup"><span data-stu-id="d5bf1-124">Error Details</span></span>|  
|-|-|  
|<span data-ttu-id="d5bf1-125">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d5bf1-125">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d5bf1-126">產品版本</span><span class="sxs-lookup"><span data-stu-id="d5bf1-126">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="d5bf1-127">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d5bf1-127">Event ID</span></span>|<span data-ttu-id="d5bf1-128">0</span><span class="sxs-lookup"><span data-stu-id="d5bf1-128">0</span></span>|  
|<span data-ttu-id="d5bf1-129">事件來源</span><span class="sxs-lookup"><span data-stu-id="d5bf1-129">Event Source</span></span>|<span data-ttu-id="d5bf1-130">0</span><span class="sxs-lookup"><span data-stu-id="d5bf1-130">0</span></span>|  
|<span data-ttu-id="d5bf1-131">元件</span><span class="sxs-lookup"><span data-stu-id="d5bf1-131">Component</span></span>|<span data-ttu-id="d5bf1-132">0</span><span class="sxs-lookup"><span data-stu-id="d5bf1-132">0</span></span>|  
|<span data-ttu-id="d5bf1-133">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d5bf1-133">Symbolic Name</span></span>|<span data-ttu-id="d5bf1-134">0</span><span class="sxs-lookup"><span data-stu-id="d5bf1-134">0</span></span>|  
|<span data-ttu-id="d5bf1-135">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d5bf1-135">Message Text</span></span>|<span data-ttu-id="d5bf1-136">無法從 HKLM 取得 BizTalk 安裝路徑\\{0}\\{1}</span><span class="sxs-lookup"><span data-stu-id="d5bf1-136">Failed to obtain BizTalk install path from HKLM\\{0}\\{1}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d5bf1-137">說明</span><span class="sxs-lookup"><span data-stu-id="d5bf1-137">Explanation</span></span>  
 <span data-ttu-id="d5bf1-138">此錯誤表示無法存取登錄，以及索引鍵的值不正確。</span><span class="sxs-lookup"><span data-stu-id="d5bf1-138">This error indicates a failure to access the registry, and that the key has an incorrect value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d5bf1-139">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d5bf1-139">User Action</span></span>  
 <span data-ttu-id="d5bf1-140">請確定您具有讀取存取登錄。</span><span class="sxs-lookup"><span data-stu-id="d5bf1-140">Ensure you have read access to the registry.</span></span> <span data-ttu-id="d5bf1-141">請確定機碼具有正確的值。</span><span class="sxs-lookup"><span data-stu-id="d5bf1-141">Ensure the key has the correct value.</span></span> <span data-ttu-id="d5bf1-142">若要存取登錄，請確定您有系統管理員權限或連絡電腦的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="d5bf1-142">To access the registry, ensure you have Administrator privileges or contact the administrator of the machine.</span></span> 