---
title: 載入組件時發生錯誤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 600973e0-3142-455f-9afa-74430af31e38
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13be3acf6974565c86cc87b14ed58929553d5220
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241734"
---
# <a name="error-loading-assembly"></a><span data-ttu-id="607d6-102">載入組件時發生錯誤</span><span class="sxs-lookup"><span data-stu-id="607d6-102">Error loading assembly</span></span>
## <a name="details"></a><span data-ttu-id="607d6-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="607d6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="607d6-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="607d6-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="607d6-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="607d6-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="607d6-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="607d6-106">Event ID</span></span>|<span data-ttu-id="607d6-107">0</span><span class="sxs-lookup"><span data-stu-id="607d6-107">0</span></span>|  
|<span data-ttu-id="607d6-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="607d6-108">Event Source</span></span>|<span data-ttu-id="607d6-109">0</span><span class="sxs-lookup"><span data-stu-id="607d6-109">0</span></span>|  
|<span data-ttu-id="607d6-110">元件</span><span class="sxs-lookup"><span data-stu-id="607d6-110">Component</span></span>|<span data-ttu-id="607d6-111">0</span><span class="sxs-lookup"><span data-stu-id="607d6-111">0</span></span>|  
|<span data-ttu-id="607d6-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="607d6-112">Symbolic Name</span></span>|<span data-ttu-id="607d6-113">0</span><span class="sxs-lookup"><span data-stu-id="607d6-113">0</span></span>|  
|<span data-ttu-id="607d6-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="607d6-114">Message Text</span></span>|<span data-ttu-id="607d6-115">此錯誤表示位置可能不完全受信任的網路共用上。</span><span class="sxs-lookup"><span data-stu-id="607d6-115">This error indicates the location may not be fully trusted if it is on a network share.</span></span> <span data-ttu-id="607d6-116">檢查該區域的程式碼存取安全性原則。</span><span class="sxs-lookup"><span data-stu-id="607d6-116">Check the Code Access Security policy for the Zone.</span></span> <span data-ttu-id="607d6-117">或檔案可能不是 BizTalk.NET 組件。</span><span class="sxs-lookup"><span data-stu-id="607d6-117">Or the file may not be a BizTalk .NET assembly.</span></span> <span data-ttu-id="607d6-118">核取的組件 [組件： BizTalkAssembly] 自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="607d6-118">Check the assembly for the [assembly: BizTalkAssembly] custom attribute.</span></span> <span data-ttu-id="607d6-119">或檔案可能不是.NET 組件。</span><span class="sxs-lookup"><span data-stu-id="607d6-119">Or the file may not be a .NET assembly.</span></span> <span data-ttu-id="607d6-120">如果檔案是.dll 或 exe，可能是 unmanaged 程式碼</span><span class="sxs-lookup"><span data-stu-id="607d6-120">If the file is a .dll or  exe, it may be unmanaged code</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="607d6-121">說明</span><span class="sxs-lookup"><span data-stu-id="607d6-121">Explanation</span></span>  
 <span data-ttu-id="607d6-122">此錯誤表示位置可能不完全受信任的網路共用上。</span><span class="sxs-lookup"><span data-stu-id="607d6-122">This error indicates the location may not be fully trusted if it is on a network share.</span></span> <span data-ttu-id="607d6-123">檢查該區域的程式碼存取安全性原則。</span><span class="sxs-lookup"><span data-stu-id="607d6-123">Check the Code Access Security policy for the Zone.</span></span> <span data-ttu-id="607d6-124">或檔案可能不是 BizTalk.NET 組件。</span><span class="sxs-lookup"><span data-stu-id="607d6-124">Or the file may not be a BizTalk .NET assembly.</span></span> <span data-ttu-id="607d6-125">核取的組件 [*組件： BizTalkAssembly*] 自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="607d6-125">Check the assembly for the [*assembly: BizTalkAssembly*] custom attribute.</span></span> <span data-ttu-id="607d6-126">或檔案可能不是.NET 組件。</span><span class="sxs-lookup"><span data-stu-id="607d6-126">Or the file may not be a .NET assembly.</span></span> <span data-ttu-id="607d6-127">如果檔案是.dll 或 exe，它可能是 unmanaged 程式碼。</span><span class="sxs-lookup"><span data-stu-id="607d6-127">If the file is a .dll or  exe, it may be unmanaged code.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="607d6-128">使用者動作</span><span class="sxs-lookup"><span data-stu-id="607d6-128">User Action</span></span>  
 <span data-ttu-id="607d6-129">授與完整信任層級，如果它來自可靠來源的位置。</span><span class="sxs-lookup"><span data-stu-id="607d6-129">Grant Full trust level to the location if it’s from a reliable source.</span></span>  <span data-ttu-id="607d6-130">請確認該 dll 是有效的 BizTalk.net 組件。</span><span class="sxs-lookup"><span data-stu-id="607d6-130">Ensure the dll is a valid BizTalk .net assembly.</span></span>