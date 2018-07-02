---
title: 登錄錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9a5bf2cd-f807-4083-8687-4416a2ee2908
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62522299866748d92abf91d36a01444c3175b070
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975111"
---
# <a name="registry-errors"></a><span data-ttu-id="4434e-102">登錄錯誤</span><span class="sxs-lookup"><span data-stu-id="4434e-102">Registry Errors</span></span>
<span data-ttu-id="4434e-103">診斷及解決 WCF 登錄錯誤的資訊。</span><span class="sxs-lookup"><span data-stu-id="4434e-103">Information for diagnosing and resolving WCF Registry errors.</span></span>  

## <a name="failed-to-access-the-registry"></a><span data-ttu-id="4434e-104">無法存取登錄</span><span class="sxs-lookup"><span data-stu-id="4434e-104">Failed to access the registry</span></span>
  
|                 |                                   <span data-ttu-id="4434e-105">錯誤詳細資料</span><span class="sxs-lookup"><span data-stu-id="4434e-105">Error details</span></span>                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="4434e-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="4434e-106">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="4434e-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="4434e-107">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="4434e-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="4434e-108">Event ID</span></span>     |                                         <span data-ttu-id="4434e-109">0</span><span class="sxs-lookup"><span data-stu-id="4434e-109">0</span></span>                                          |
|  <span data-ttu-id="4434e-110">事件來源</span><span class="sxs-lookup"><span data-stu-id="4434e-110">Event Source</span></span>   |                                         <span data-ttu-id="4434e-111">0</span><span class="sxs-lookup"><span data-stu-id="4434e-111">0</span></span>                                          |
|    <span data-ttu-id="4434e-112">元件</span><span class="sxs-lookup"><span data-stu-id="4434e-112">Component</span></span>    |                                         <span data-ttu-id="4434e-113">0</span><span class="sxs-lookup"><span data-stu-id="4434e-113">0</span></span>                                          |
|  <span data-ttu-id="4434e-114">符號名稱</span><span class="sxs-lookup"><span data-stu-id="4434e-114">Symbolic Name</span></span>  |                                         <span data-ttu-id="4434e-115">0</span><span class="sxs-lookup"><span data-stu-id="4434e-115">0</span></span>                                          |
|  <span data-ttu-id="4434e-116">訊息文字</span><span class="sxs-lookup"><span data-stu-id="4434e-116">Message Text</span></span>   |                             <span data-ttu-id="4434e-117">無法開啟 HKLM\\{0}。</span><span class="sxs-lookup"><span data-stu-id="4434e-117">Failed to open HKLM\\{0}.</span></span>                              |
  
### <a name="explanation"></a><span data-ttu-id="4434e-118">說明</span><span class="sxs-lookup"><span data-stu-id="4434e-118">Explanation</span></span>  
 <span data-ttu-id="4434e-119">此錯誤表示無法存取登錄。</span><span class="sxs-lookup"><span data-stu-id="4434e-119">This error indicates a failure to access the registry.</span></span>  
  
### <a name="user-action"></a><span data-ttu-id="4434e-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="4434e-120">User Action</span></span>  
 <span data-ttu-id="4434e-121">確定您已登錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="4434e-121">Ensure you have read access to the registry.</span></span> <span data-ttu-id="4434e-122">若要存取登錄，請確定您有系統管理員權限或連絡機器的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="4434e-122">To access the registry, ensure you have Administrator privileges or contact the administrator of the machine.</span></span>
 
## <a name="failed-to-obtain-biztalk-install-path"></a><span data-ttu-id="4434e-123">無法取得 BizTalk 安裝路徑</span><span class="sxs-lookup"><span data-stu-id="4434e-123">Failed to obtain BizTalk install path</span></span>
  
|                 |                                   <span data-ttu-id="4434e-124">錯誤詳細資料</span><span class="sxs-lookup"><span data-stu-id="4434e-124">Error Details</span></span>                                    |
|-----------------|------------------------------------------------------------------------------------|
|  <span data-ttu-id="4434e-125">產品名稱</span><span class="sxs-lookup"><span data-stu-id="4434e-125">Product Name</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| <span data-ttu-id="4434e-126">產品版本</span><span class="sxs-lookup"><span data-stu-id="4434e-126">Product Version</span></span> |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    <span data-ttu-id="4434e-127">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="4434e-127">Event ID</span></span>     |                                         <span data-ttu-id="4434e-128">0</span><span class="sxs-lookup"><span data-stu-id="4434e-128">0</span></span>                                          |
|  <span data-ttu-id="4434e-129">事件來源</span><span class="sxs-lookup"><span data-stu-id="4434e-129">Event Source</span></span>   |                                         <span data-ttu-id="4434e-130">0</span><span class="sxs-lookup"><span data-stu-id="4434e-130">0</span></span>                                          |
|    <span data-ttu-id="4434e-131">元件</span><span class="sxs-lookup"><span data-stu-id="4434e-131">Component</span></span>    |                                         <span data-ttu-id="4434e-132">0</span><span class="sxs-lookup"><span data-stu-id="4434e-132">0</span></span>                                          |
|  <span data-ttu-id="4434e-133">符號名稱</span><span class="sxs-lookup"><span data-stu-id="4434e-133">Symbolic Name</span></span>  |                                         <span data-ttu-id="4434e-134">0</span><span class="sxs-lookup"><span data-stu-id="4434e-134">0</span></span>                                          |
|  <span data-ttu-id="4434e-135">訊息文字</span><span class="sxs-lookup"><span data-stu-id="4434e-135">Message Text</span></span>   |             <span data-ttu-id="4434e-136">無法從 HKLM 取得 BizTalk 安裝路徑\\{0}\\{1}</span><span class="sxs-lookup"><span data-stu-id="4434e-136">Failed to obtain BizTalk install path from HKLM\\{0}\\{1}</span></span>              |
  
## <a name="explanation"></a><span data-ttu-id="4434e-137">說明</span><span class="sxs-lookup"><span data-stu-id="4434e-137">Explanation</span></span>  
 <span data-ttu-id="4434e-138">此錯誤表示無法存取登錄中，而且索引鍵有不正確的值。</span><span class="sxs-lookup"><span data-stu-id="4434e-138">This error indicates a failure to access the registry, and that the key has an incorrect value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4434e-139">使用者動作</span><span class="sxs-lookup"><span data-stu-id="4434e-139">User Action</span></span>  
 <span data-ttu-id="4434e-140">確定您已登錄的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="4434e-140">Ensure you have read access to the registry.</span></span> <span data-ttu-id="4434e-141">請確定索引鍵具有正確的值。</span><span class="sxs-lookup"><span data-stu-id="4434e-141">Ensure the key has the correct value.</span></span> <span data-ttu-id="4434e-142">若要存取登錄，請確定您有系統管理員權限或連絡機器的系統管理員。</span><span class="sxs-lookup"><span data-stu-id="4434e-142">To access the registry, ensure you have Administrator privileges or contact the administrator of the machine.</span></span> 