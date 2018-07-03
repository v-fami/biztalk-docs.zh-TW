---
title: 專案位置不是空白 |Microsoft Docs
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
ms.openlocfilehash: 5fc106b534973f13544b9bafa85f190d8ed2c255
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994287"
---
# <a name="the-project-location-is-not-empty"></a><span data-ttu-id="96c9b-102">專案位置不是空白的</span><span class="sxs-lookup"><span data-stu-id="96c9b-102">The project location is not empty</span></span>
## <a name="details"></a><span data-ttu-id="96c9b-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="96c9b-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                                                    |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="96c9b-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="96c9b-104">Product Name</span></span>   |                                                                                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                                 |
| <span data-ttu-id="96c9b-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="96c9b-105">Product Version</span></span> |                                                                                             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                                                                             |
|    <span data-ttu-id="96c9b-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="96c9b-106">Event ID</span></span>     |                                                                                                                         <span data-ttu-id="96c9b-107">0</span><span class="sxs-lookup"><span data-stu-id="96c9b-107">0</span></span>                                                                                                                          |
|  <span data-ttu-id="96c9b-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="96c9b-108">Event Source</span></span>   |                                                                                                                         <span data-ttu-id="96c9b-109">0</span><span class="sxs-lookup"><span data-stu-id="96c9b-109">0</span></span>                                                                                                                          |
|    <span data-ttu-id="96c9b-110">元件</span><span class="sxs-lookup"><span data-stu-id="96c9b-110">Component</span></span>    |                                                                                                                         <span data-ttu-id="96c9b-111">0</span><span class="sxs-lookup"><span data-stu-id="96c9b-111">0</span></span>                                                                                                                          |
|  <span data-ttu-id="96c9b-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="96c9b-112">Symbolic Name</span></span>  |                                                                                                                         <span data-ttu-id="96c9b-113">0</span><span class="sxs-lookup"><span data-stu-id="96c9b-113">0</span></span>                                                                                                                          |
|  <span data-ttu-id="96c9b-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="96c9b-114">Message Text</span></span>   | <span data-ttu-id="96c9b-115">專案位置"{0}"不是空的。</span><span class="sxs-lookup"><span data-stu-id="96c9b-115">The project location "{0}" is not empty.</span></span> <span data-ttu-id="96c9b-116">您需要執行下列其中之一： 1。</span><span class="sxs-lookup"><span data-stu-id="96c9b-116">You need to do one of the following: 1.</span></span> <span data-ttu-id="96c9b-117">選擇新專案，也就是 2 的不同位置。</span><span class="sxs-lookup"><span data-stu-id="96c9b-117">Choose a different location for the new project, 2.</span></span> <span data-ttu-id="96c9b-118">指定覆寫重新使用現用位置或 3。</span><span class="sxs-lookup"><span data-stu-id="96c9b-118">Specify overwrite to reuse the existing location, or 3.</span></span> <span data-ttu-id="96c9b-119">手動刪除專案位置的內容。</span><span class="sxs-lookup"><span data-stu-id="96c9b-119">Manually delete the contents of the project location.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="96c9b-120">說明</span><span class="sxs-lookup"><span data-stu-id="96c9b-120">Explanation</span></span>  
 <span data-ttu-id="96c9b-121">此錯誤表示嘗試將服務發佈到的虛擬目錄不是空的。</span><span class="sxs-lookup"><span data-stu-id="96c9b-121">This error indicates the virtual directory where the service is trying to be published is not empty.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="96c9b-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="96c9b-122">User Action</span></span>  
 <span data-ttu-id="96c9b-123">選取覆寫位置重複使用相同的位置。</span><span class="sxs-lookup"><span data-stu-id="96c9b-123">Select the overwrite location to reuse the same location.</span></span> <span data-ttu-id="96c9b-124">或指定新的位置。</span><span class="sxs-lookup"><span data-stu-id="96c9b-124">Or specify a new location.</span></span>  <span data-ttu-id="96c9b-125">在 [WCF 服務發佈精靈，選取**覆寫現有的位置**然後按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="96c9b-125">In the WCF Service Publishing Wizard, select **Overwrite Existing Location** and click **Next**.</span></span> <span data-ttu-id="96c9b-126">此步驟會覆寫位置。</span><span class="sxs-lookup"><span data-stu-id="96c9b-126">This step overwrites the location.</span></span>