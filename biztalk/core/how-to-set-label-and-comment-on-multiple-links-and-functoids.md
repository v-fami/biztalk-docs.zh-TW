---
title: "如何設定標籤和註解多個連結與運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b554a19-2bd4-4dbc-b5cb-567b98c07024
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 65bcb25fae52da46bbea1679e3b4e215720782d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-label-and-comment-on-multiple-links-and-functoids"></a><span data-ttu-id="ba739-102">如何在多個連結與運算質設定標籤和註解</span><span class="sxs-lookup"><span data-stu-id="ba739-102">How to Set Label and Comment on Multiple Links and Functoids</span></span>
<span data-ttu-id="ba739-103">您可以設定多個運算質和 (或) 連結的通用標籤和 (或) 註解。</span><span class="sxs-lookup"><span data-stu-id="ba739-103">You can set a common label and/or a comment for multiple functoids and/or links.</span></span> <span data-ttu-id="ba739-104">本主題提供如何執行此作業的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ba739-104">This topic provides details about how to perform this operation.</span></span>  
  
 <span data-ttu-id="ba739-105">如需如何選取多個運算質和/或連結的資訊，請參閱[如何選取多個連結和運算質](../core/how-to-select-multiple-links-and-functoids.md)。</span><span class="sxs-lookup"><span data-stu-id="ba739-105">For information about how to select multiple functoid(s) and/or link(s), see [How to Select Multiple Links and Functoids](../core/how-to-select-multiple-links-and-functoids.md).</span></span>  
  
 <span data-ttu-id="ba739-106">選取多個運算質和 (或) 連結之後，您可以執行下列任一作業：</span><span class="sxs-lookup"><span data-stu-id="ba739-106">After selecting multiple functoid(s) and/or link(s), you can do any of the following:</span></span>  
  
-   <span data-ttu-id="ba739-107">設定所選取連結的通用標籤。</span><span class="sxs-lookup"><span data-stu-id="ba739-107">Set a common label for selected links.</span></span>  
  
-   <span data-ttu-id="ba739-108">設定所選取運算質的通用標籤和 (或) 註解。</span><span class="sxs-lookup"><span data-stu-id="ba739-108">Set a common label and/or comment for the selected functoids.</span></span>  
  
-   <span data-ttu-id="ba739-109">設定所選取運算質和連結的通用標籤。</span><span class="sxs-lookup"><span data-stu-id="ba739-109">Set a common label for the selected functoids and links.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ba739-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="ba739-110">Prerequisites</span></span>  
 <span data-ttu-id="ba739-111">這些指示需要執行中的 BizTalk 對應工具。</span><span class="sxs-lookup"><span data-stu-id="ba739-111">These instructions require that BizTalk Mapper is running.</span></span>  
  
## <a name="to-set-a-common-label-for-selected-links"></a><span data-ttu-id="ba739-112">若要設定所選取連結的通用標籤</span><span class="sxs-lookup"><span data-stu-id="ba739-112">To set a common label for selected links</span></span>  
 <span data-ttu-id="ba739-113">在多個連結上設定通用標籤是一個不可部分完成的作業。</span><span class="sxs-lookup"><span data-stu-id="ba739-113">Setting a common label on multiple links is one atomic operation.</span></span> <span data-ttu-id="ba739-114">您可以復原或重做此作業。</span><span class="sxs-lookup"><span data-stu-id="ba739-114">You can undo or redo this operation.</span></span>  
  
 <span data-ttu-id="ba739-115">若要設定所選取連結的通用標籤：</span><span class="sxs-lookup"><span data-stu-id="ba739-115">To set a common label for the selected links:</span></span>  
  
1.  <span data-ttu-id="ba739-116">在對應工具方格頁上，選取想要的連結。</span><span class="sxs-lookup"><span data-stu-id="ba739-116">On the Mapper grid page, select the desired links.</span></span>  
  
2.  <span data-ttu-id="ba739-117">在**屬性**視窗中，輸入適用的標籤在**標籤**屬性。</span><span class="sxs-lookup"><span data-stu-id="ba739-117">In the **Properties** window, enter a suitable label in the **Label** property.</span></span>  
  
## <a name="to-set-a-common-label-andor-comment-for-selected-functoids"></a><span data-ttu-id="ba739-118">若要設定所選取運算質的通用標籤和 (或) 註解</span><span class="sxs-lookup"><span data-stu-id="ba739-118">To set a common label and/or comment for selected functoids</span></span>  
 <span data-ttu-id="ba739-119">為所選取的運算質設定通用標籤和通用註解，是兩項不同的不可部分完成作業。</span><span class="sxs-lookup"><span data-stu-id="ba739-119">Setting a common label and setting a common comment for the selected functoids are two different atomic operations.</span></span> <span data-ttu-id="ba739-120">您可以復原或重做這些作業。</span><span class="sxs-lookup"><span data-stu-id="ba739-120">You can undo or redo these operations.</span></span>  
  
 <span data-ttu-id="ba739-121">若要設定所選取運算質的通用標籤/註解：</span><span class="sxs-lookup"><span data-stu-id="ba739-121">To set a common label/comment for the selected functoids:</span></span>  
  
1.  <span data-ttu-id="ba739-122">在對應工具方格頁上，選取想要的運算質。</span><span class="sxs-lookup"><span data-stu-id="ba739-122">On the Mapper grid page, select the desired functoids.</span></span>  
  
2.  <span data-ttu-id="ba739-123">在**屬性**視窗中，輸入適用的標籤及/或註解中**標籤**和**註解**屬性。</span><span class="sxs-lookup"><span data-stu-id="ba739-123">In the **Properties** window, enter a suitable label and/or comment in the **Label** and **Comments** properties.</span></span>  
  
## <a name="to-set-a-common-label-for-selected-functoids-and-links"></a><span data-ttu-id="ba739-124">若要設定所選取運算質和連結的通用標籤</span><span class="sxs-lookup"><span data-stu-id="ba739-124">To set a common label for selected functoids and links</span></span>  
 <span data-ttu-id="ba739-125">您可以設定所選取運算質和連結的通用標籤。</span><span class="sxs-lookup"><span data-stu-id="ba739-125">You can set a common label for the selected functoids and links.</span></span> <span data-ttu-id="ba739-126">**標籤**是唯一運算質和連結的通用的屬性。</span><span class="sxs-lookup"><span data-stu-id="ba739-126">**Label** is the only property which is common to both functoids and links.</span></span> <span data-ttu-id="ba739-127">您可以復原或重做此作業。</span><span class="sxs-lookup"><span data-stu-id="ba739-127">You can undo or redo this operation.</span></span>  
  
 <span data-ttu-id="ba739-128">若要設定所選取運算質和連結的通用標籤：</span><span class="sxs-lookup"><span data-stu-id="ba739-128">To set a common label for the selected functoids and links:</span></span>  
  
1.  <span data-ttu-id="ba739-129">在對應工具方格頁上，選取想要的運算質和連結。</span><span class="sxs-lookup"><span data-stu-id="ba739-129">On the Mapper grid page, select the desired functoids and links.</span></span>  
  
2.  <span data-ttu-id="ba739-130">在**屬性**視窗中，輸入適用的標籤在**標籤**屬性。</span><span class="sxs-lookup"><span data-stu-id="ba739-130">In the **Properties** window, enter a suitable label in the **Label** property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba739-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba739-131">See Also</span></span>  
 [<span data-ttu-id="ba739-132">使用連結指定記錄和欄位對應</span><span class="sxs-lookup"><span data-stu-id="ba739-132">Using Links to Specify Record and Field Mappings</span></span>](../core/using-links-to-specify-record-and-field-mappings.md)