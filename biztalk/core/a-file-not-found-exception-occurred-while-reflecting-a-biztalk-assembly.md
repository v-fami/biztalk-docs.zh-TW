---
title: "找不到檔案反映 BizTalk 組件時發生例外狀況 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 223147eb-785f-4dfc-b2a6-7d50dfaf8092
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00000896eb4cb97e44ed51602675fc65495552be
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="a-file-not-found-exception-occurred-while-reflecting-a-biztalk-assembly"></a><span data-ttu-id="15c84-102">找不到檔案反映 BizTalk 組件時發生例外狀況</span><span class="sxs-lookup"><span data-stu-id="15c84-102">A file not found exception occurred while reflecting a BizTalk assembly</span></span>
## <a name="details"></a><span data-ttu-id="15c84-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="15c84-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="15c84-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="15c84-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="15c84-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="15c84-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="15c84-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="15c84-106">Event ID</span></span>|<span data-ttu-id="15c84-107">0</span><span class="sxs-lookup"><span data-stu-id="15c84-107">0</span></span>|  
|<span data-ttu-id="15c84-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="15c84-108">Event Source</span></span>|<span data-ttu-id="15c84-109">0</span><span class="sxs-lookup"><span data-stu-id="15c84-109">0</span></span>|  
|<span data-ttu-id="15c84-110">元件</span><span class="sxs-lookup"><span data-stu-id="15c84-110">Component</span></span>|<span data-ttu-id="15c84-111">0</span><span class="sxs-lookup"><span data-stu-id="15c84-111">0</span></span>|  
|<span data-ttu-id="15c84-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="15c84-112">Symbolic Name</span></span>|<span data-ttu-id="15c84-113">0</span><span class="sxs-lookup"><span data-stu-id="15c84-113">0</span></span>|  
|<span data-ttu-id="15c84-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="15c84-114">Message Text</span></span>|<span data-ttu-id="15c84-115">找不到檔案反映 BizTalk 組件"{0}"時發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="15c84-115">A file not found exception occurred while reflecting BizTalk assembly "{0}".</span></span> <span data-ttu-id="15c84-116">無法使用一或多個相依性時，可能會發生這個問題。</span><span class="sxs-lookup"><span data-stu-id="15c84-116">This problem may occur if one or more dependencies are not available.</span></span> <span data-ttu-id="15c84-117">若要修正這個問題，請嘗試下列其中一種： 1。</span><span class="sxs-lookup"><span data-stu-id="15c84-117">To correct this problem, try one of the following: 1.</span></span> <span data-ttu-id="15c84-118">將組件的相依性複製到相同的資料夾。</span><span class="sxs-lookup"><span data-stu-id="15c84-118">Copy the dependencies of the assembly to the same folder.</span></span> <span data-ttu-id="15c84-119">2.</span><span class="sxs-lookup"><span data-stu-id="15c84-119">2.</span></span> <span data-ttu-id="15c84-120">將遺失的相依性安裝到全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="15c84-120">Install the missing dependencies into the Global Assembly Cache.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="15c84-121">說明</span><span class="sxs-lookup"><span data-stu-id="15c84-121">Explanation</span></span>  
 <span data-ttu-id="15c84-122">此錯誤表示正在發行的參考 BizTalk 組件不在全域組件快取 (GAC) 或相同的目錄中的另一個組件。</span><span class="sxs-lookup"><span data-stu-id="15c84-122">This error indicates the BizTalk Assembly that is being published references another assembly that is not in the Global Assembly Cache (GAC) or in the same directory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="15c84-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="15c84-123">User Action</span></span>  
 <span data-ttu-id="15c84-124">除了錯誤訊息中指定的動作，將參考組件移到全域組件快取或將它複製到與 BizTalk 組件相同的位置</span><span class="sxs-lookup"><span data-stu-id="15c84-124">In addition to the actions specified in the error message, move the reference assembly to the Global Assembly Cache or copy it to the same location as the BizTalk assembly</span></span>  
  
1.  <span data-ttu-id="15c84-125">按一下**啟動**，指向 **所有程式**，指向  **Visual Studio**，然後按一下  **Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="15c84-125">Click **Start**, point to **All Programs**, point to **Visual Studio**, and then click **Visual Studio**.</span></span>  
  
2.  <span data-ttu-id="15c84-126">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="15c84-126">Open a command prompt.</span></span>  
  
3.  <span data-ttu-id="15c84-127">瀏覽組件的位置，然後輸入**gacutil /I /\<***組件名稱***\>.dll**</span><span class="sxs-lookup"><span data-stu-id="15c84-127">Browse to the location of the assembly, and enter **gacutil /I /\<***assembly name***\>.dll**</span></span>