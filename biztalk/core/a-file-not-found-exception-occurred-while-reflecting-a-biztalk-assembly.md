---
title: 找不到檔案反映 BizTalk 組件時發生例外狀況 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 223147eb-785f-4dfc-b2a6-7d50dfaf8092
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee0cffc331765924b4fe7d29d95f7094b14aecb3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000839"
---
# <a name="a-file-not-found-exception-occurred-while-reflecting-a-biztalk-assembly"></a><span data-ttu-id="fe619-102">找不到檔案反映 BizTalk 組件時發生例外狀況</span><span class="sxs-lookup"><span data-stu-id="fe619-102">A file not found exception occurred while reflecting a BizTalk assembly</span></span>
## <a name="details"></a><span data-ttu-id="fe619-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fe619-103">Details</span></span>  

|                 |                                                                                                                                                                                                                                                                                                                                        |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="fe619-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="fe619-104">Product Name</span></span>   |                                                                                                                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                                                                           |
| <span data-ttu-id="fe619-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="fe619-105">Product Version</span></span> |                                                                                                                                       [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                                                                                                                       |
|    <span data-ttu-id="fe619-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="fe619-106">Event ID</span></span>     |                                                                                                                                                                   <span data-ttu-id="fe619-107">0</span><span class="sxs-lookup"><span data-stu-id="fe619-107">0</span></span>                                                                                                                                                                    |
|  <span data-ttu-id="fe619-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="fe619-108">Event Source</span></span>   |                                                                                                                                                                   <span data-ttu-id="fe619-109">0</span><span class="sxs-lookup"><span data-stu-id="fe619-109">0</span></span>                                                                                                                                                                    |
|    <span data-ttu-id="fe619-110">元件</span><span class="sxs-lookup"><span data-stu-id="fe619-110">Component</span></span>    |                                                                                                                                                                   <span data-ttu-id="fe619-111">0</span><span class="sxs-lookup"><span data-stu-id="fe619-111">0</span></span>                                                                                                                                                                    |
|  <span data-ttu-id="fe619-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="fe619-112">Symbolic Name</span></span>  |                                                                                                                                                                   <span data-ttu-id="fe619-113">0</span><span class="sxs-lookup"><span data-stu-id="fe619-113">0</span></span>                                                                                                                                                                    |
|  <span data-ttu-id="fe619-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="fe619-114">Message Text</span></span>   | <span data-ttu-id="fe619-115">找不到檔案反映 BizTalk 組件時發生例外狀況 」{0}"。</span><span class="sxs-lookup"><span data-stu-id="fe619-115">A file not found exception occurred while reflecting BizTalk assembly "{0}".</span></span> <span data-ttu-id="fe619-116">無法使用一或多個相依性時，可能會發生此問題。</span><span class="sxs-lookup"><span data-stu-id="fe619-116">This problem may occur if one or more dependencies are not available.</span></span> <span data-ttu-id="fe619-117">若要更正這個問題，請嘗試下列其中之一： 1。</span><span class="sxs-lookup"><span data-stu-id="fe619-117">To correct this problem, try one of the following: 1.</span></span> <span data-ttu-id="fe619-118">將組件的相依性複製到相同的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="fe619-118">Copy the dependencies of the assembly to the same folder.</span></span> <span data-ttu-id="fe619-119">2.</span><span class="sxs-lookup"><span data-stu-id="fe619-119">2.</span></span> <span data-ttu-id="fe619-120">全域組件快取中安裝缺少的相依性。</span><span class="sxs-lookup"><span data-stu-id="fe619-120">Install the missing dependencies into the Global Assembly Cache.</span></span> |

## <a name="explanation"></a><span data-ttu-id="fe619-121">說明</span><span class="sxs-lookup"><span data-stu-id="fe619-121">Explanation</span></span>  
 <span data-ttu-id="fe619-122">此錯誤表示 BizTalk 組件已發行的參考不在全域組件快取 (GAC) 或相同的目錄中的另一個組件。</span><span class="sxs-lookup"><span data-stu-id="fe619-122">This error indicates the BizTalk Assembly that is being published references another assembly that is not in the Global Assembly Cache (GAC) or in the same directory.</span></span>  

## <a name="user-action"></a><span data-ttu-id="fe619-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="fe619-123">User Action</span></span>  
 <span data-ttu-id="fe619-124">除了錯誤訊息中指定的動作，將參考組件移到全域組件快取，或將它複製到與 BizTalk 組件相同的位置</span><span class="sxs-lookup"><span data-stu-id="fe619-124">In addition to the actions specified in the error message, move the reference assembly to the Global Assembly Cache or copy it to the same location as the BizTalk assembly</span></span>  

1. <span data-ttu-id="fe619-125">按一下 **開始**，指向**所有程式**，指向**Visual Studio**，然後按一下**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="fe619-125">Click **Start**, point to **All Programs**, point to **Visual Studio**, and then click **Visual Studio**.</span></span>  

2. <span data-ttu-id="fe619-126">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="fe619-126">Open a command prompt.</span></span>  

3. <span data-ttu-id="fe619-127">瀏覽至組件的位置，然後輸入**gacutil /I /\<**<em>組件名稱</em>**\>.dll**</span><span class="sxs-lookup"><span data-stu-id="fe619-127">Browse to the location of the assembly, and enter **gacutil /I /\<**<em>assembly name</em>**\>.dll**</span></span>
