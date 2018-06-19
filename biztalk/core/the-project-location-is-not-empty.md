---
title: 專案位置不是空白 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db353050-3662-4ab6-8898-4e4d3bd78ac1
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2de1e1dd381a75f596b4980430ddcc5d6d8982b6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278782"
---
# <a name="the-project-location-is-not-empty"></a><span data-ttu-id="1d6d2-102">專案位置不是空白的</span><span class="sxs-lookup"><span data-stu-id="1d6d2-102">The project location is not empty</span></span>
## <a name="details"></a><span data-ttu-id="1d6d2-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1d6d2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1d6d2-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1d6d2-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="1d6d2-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="1d6d2-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="1d6d2-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1d6d2-106">Event ID</span></span>|<span data-ttu-id="1d6d2-107">0</span><span class="sxs-lookup"><span data-stu-id="1d6d2-107">0</span></span>|  
|<span data-ttu-id="1d6d2-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="1d6d2-108">Event Source</span></span>|<span data-ttu-id="1d6d2-109">0</span><span class="sxs-lookup"><span data-stu-id="1d6d2-109">0</span></span>|  
|<span data-ttu-id="1d6d2-110">元件</span><span class="sxs-lookup"><span data-stu-id="1d6d2-110">Component</span></span>|<span data-ttu-id="1d6d2-111">0</span><span class="sxs-lookup"><span data-stu-id="1d6d2-111">0</span></span>|  
|<span data-ttu-id="1d6d2-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1d6d2-112">Symbolic Name</span></span>|<span data-ttu-id="1d6d2-113">0</span><span class="sxs-lookup"><span data-stu-id="1d6d2-113">0</span></span>|  
|<span data-ttu-id="1d6d2-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1d6d2-114">Message Text</span></span>|<span data-ttu-id="1d6d2-115">專案位置 "{0}" 不是空白的。</span><span class="sxs-lookup"><span data-stu-id="1d6d2-115">The project location "{0}" is not empty.</span></span> <span data-ttu-id="1d6d2-116">您必須進行下列其中之一： 1。</span><span class="sxs-lookup"><span data-stu-id="1d6d2-116">You need to do one of the following: 1.</span></span> <span data-ttu-id="1d6d2-117">選擇新專案，也就是 2 的不同位置。</span><span class="sxs-lookup"><span data-stu-id="1d6d2-117">Choose a different location for the new project, 2.</span></span> <span data-ttu-id="1d6d2-118">指定要重複使用現有的位置或 3 覆寫。</span><span class="sxs-lookup"><span data-stu-id="1d6d2-118">Specify overwrite to reuse the existing location, or 3.</span></span> <span data-ttu-id="1d6d2-119">手動刪除專案位置的內容。</span><span class="sxs-lookup"><span data-stu-id="1d6d2-119">Manually delete the contents of the project location.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1d6d2-120">說明</span><span class="sxs-lookup"><span data-stu-id="1d6d2-120">Explanation</span></span>  
 <span data-ttu-id="1d6d2-121">此錯誤表示嘗試將服務發佈到的虛擬目錄不是空的。</span><span class="sxs-lookup"><span data-stu-id="1d6d2-121">This error indicates the virtual directory where the service is trying to be published is not empty.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1d6d2-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1d6d2-122">User Action</span></span>  
 <span data-ttu-id="1d6d2-123">選取覆寫位置重複使用相同的位置。</span><span class="sxs-lookup"><span data-stu-id="1d6d2-123">Select the overwrite location to reuse the same location.</span></span> <span data-ttu-id="1d6d2-124">或指定新位置。</span><span class="sxs-lookup"><span data-stu-id="1d6d2-124">Or specify a new location.</span></span>  <span data-ttu-id="1d6d2-125">在 WCF 服務發佈精靈，選取**覆寫現有位置**按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="1d6d2-125">In the WCF Service Publishing Wizard, select **Overwrite Existing Location** and click **Next**.</span></span> <span data-ttu-id="1d6d2-126">此步驟會覆寫位置。</span><span class="sxs-lookup"><span data-stu-id="1d6d2-126">This step overwrites the location.</span></span>