---
title: 如何檢視資訊提示和工具提示 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5621bd0a-7028-43fc-b6e8-74a528129285
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06aba645f94b87e0a7951d9c8264056262a12a13
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257278"
---
# <a name="how-to-view-infotip-and-tooltip"></a><span data-ttu-id="fd395-102">如何檢視資訊提示與工具提示</span><span class="sxs-lookup"><span data-stu-id="fd395-102">How to View Infotip and Tooltip</span></span>
<span data-ttu-id="fd395-103">當您將游標移至對應項目上方而不選取它時，會顯示含有該項目之實用資訊的工具提示。</span><span class="sxs-lookup"><span data-stu-id="fd395-103">When you move the cursor over a map item without clicking it, a screen tip appears with useful information about that item.</span></span>  
  
 <span data-ttu-id="fd395-104">BizTalk 對應工具使用兩種類型的工具提示 – 資訊提示和工具提示。</span><span class="sxs-lookup"><span data-stu-id="fd395-104">The BizTalk Mapper uses two types of screen tips – infotip and tooltip.</span></span>  
  
-   <span data-ttu-id="fd395-105">**資訊提示**會顯示運算質或連結。</span><span class="sxs-lookup"><span data-stu-id="fd395-105">**Infotips** are displayed for functoids or links.</span></span> <span data-ttu-id="fd395-106">當您為運算質或連結設定標籤或註解時，會在格線頁上以資訊提示的形式看見它們。</span><span class="sxs-lookup"><span data-stu-id="fd395-106">When you configure labels or comments for functoids or links, you see them as infotip on the grid page.</span></span> <span data-ttu-id="fd395-107">此外，當屬性的文字值超過顯示**屬性方格**，資訊提示會顯示。</span><span class="sxs-lookup"><span data-stu-id="fd395-107">Also, when the text value for properties exceeds the display of the **Properties Grid**, the infotip is displayed.</span></span>  
  
-   <span data-ttu-id="fd395-108">**工具提示**部分/整個隱藏的資料格檢視中目前的對齊方式的結構描述節點會顯示。</span><span class="sxs-lookup"><span data-stu-id="fd395-108">**Tooltips** are displayed for those schema nodes that are hidden partially/completely from the current alignment in the grid view.</span></span>  
  
 <span data-ttu-id="fd395-109">對於連結標籤，只會保留前 256 個字元，而工具提示會顯示完整的標籤。</span><span class="sxs-lookup"><span data-stu-id="fd395-109">For link labels, only the first 256 characters are retained, and the tooltip displays the complete label.</span></span> <span data-ttu-id="fd395-110">對於運算質，標籤最多可包含 256 個字元，而註解則有 1024 個字元的限制。</span><span class="sxs-lookup"><span data-stu-id="fd395-110">For functoids, the label can contain a maximum of 256 characters and comments have a limit of 1024 characters.</span></span> <span data-ttu-id="fd395-111">註解的文字會因此而截斷，以便只顯示註解的前 256 個字元。</span><span class="sxs-lookup"><span data-stu-id="fd395-111">Text of comment gets truncated accordingly to display only first 256 characters of comment.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fd395-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="fd395-112">Prerequisites</span></span>  
 <span data-ttu-id="fd395-113">如果要檢視工具提示，請確定 BizTalk 對應工具正在執行。</span><span class="sxs-lookup"><span data-stu-id="fd395-113">To view the tooltips, ensure BizTalk Mapper is running.</span></span>  
  
## <a name="to-view-the-infotip"></a><span data-ttu-id="fd395-114">檢視資訊提示</span><span class="sxs-lookup"><span data-stu-id="fd395-114">To view the infotip</span></span>  
 <span data-ttu-id="fd395-115">當您將滑鼠游標移至運算質上方時，資訊提示會顯示關於運算質名稱、運算質標籤、運算質註解與輸入參數 (如果有的話) 的資訊。</span><span class="sxs-lookup"><span data-stu-id="fd395-115">When you move the mouse on a functoid, the infotip displays information about the functoid name, the functoid label, the functoid comment, and the input parameters (if existing).</span></span> <span data-ttu-id="fd395-116">如**指令碼處理**運算質，資訊提示會顯示第一個幾行程式碼。</span><span class="sxs-lookup"><span data-stu-id="fd395-116">For a **Scripting** functoid, the infotip displays the first few lines of code.</span></span>  
  
 <span data-ttu-id="fd395-117">連結的資訊提示會顯示下列資訊：</span><span class="sxs-lookup"><span data-stu-id="fd395-117">The infotip to a link displays the following information:</span></span>  
  
-   <span data-ttu-id="fd395-118">連結標籤 (如果已設定的話)。</span><span class="sxs-lookup"><span data-stu-id="fd395-118">Link label, if set.</span></span>  
  
-   <span data-ttu-id="fd395-119">**： 從來源連接**。</span><span class="sxs-lookup"><span data-stu-id="fd395-119">**From: source connection**.</span></span> <span data-ttu-id="fd395-120">如果來源連接是結構描述項目，會顯示項目名稱。</span><span class="sxs-lookup"><span data-stu-id="fd395-120">If the source connection is a schema element, it shows the element name.</span></span> <span data-ttu-id="fd395-121">如果來源連接是運算質，會顯示運算質名稱。</span><span class="sxs-lookup"><span data-stu-id="fd395-121">If the source connection is a functoid, it shows the functoid name.</span></span>  
  
-   <span data-ttu-id="fd395-122">**至： 目的地連接**。</span><span class="sxs-lookup"><span data-stu-id="fd395-122">**To: destination connection**.</span></span> <span data-ttu-id="fd395-123">如果目的地連接是結構描述項目，會顯示項目名稱。</span><span class="sxs-lookup"><span data-stu-id="fd395-123">If the destination connection is a schema element, it shows the element name.</span></span> <span data-ttu-id="fd395-124">如果目的地連接是運算質，會顯示運算質名稱。</span><span class="sxs-lookup"><span data-stu-id="fd395-124">If the destination connection is a functoid, it shows the functoid name.</span></span>  
  
 <span data-ttu-id="fd395-125">如果中的欄位**屬性方格**文字超過顯示，將滑鼠游標移欄位。</span><span class="sxs-lookup"><span data-stu-id="fd395-125">If the fields in the **Properties Grid** have text that exceeds the display, move the mouse on the field.</span></span> <span data-ttu-id="fd395-126">資訊提示就會顯示完整文字。</span><span class="sxs-lookup"><span data-stu-id="fd395-126">The infotip will show the full text.</span></span>  
  
 <span data-ttu-id="fd395-127">下圖說明與運算質，資訊提示的連結，而**屬性方格**。</span><span class="sxs-lookup"><span data-stu-id="fd395-127">The following figure illustrates infotips to a functoid, link, and the **Properties Grid**.</span></span>  
  
 <span data-ttu-id="fd395-128">![運算質、 連結及標籤的資訊提示](../core/media/viewing-infotips.gif "Viewing_infotips")</span><span class="sxs-lookup"><span data-stu-id="fd395-128">![Infotips for functoid, link, and label](../core/media/viewing-infotips.gif "Viewing_infotips")</span></span>  
  
## <a name="to-view-the-tooltip"></a><span data-ttu-id="fd395-129">檢視工具提示</span><span class="sxs-lookup"><span data-stu-id="fd395-129">To view the tooltip</span></span>  
 <span data-ttu-id="fd395-130">當您的來源和/或目的地結構描述過大時，您的對應可能會過長，因此可能只看得到部分結構描述節點。</span><span class="sxs-lookup"><span data-stu-id="fd395-130">When your source and/or destination schemas are big, your map can span vertically; hence the schema nodes may be partially visible.</span></span> <span data-ttu-id="fd395-131">在此狀況下，當您將滑鼠游標移至那些來源節點上方時，就可以看到工具提示。</span><span class="sxs-lookup"><span data-stu-id="fd395-131">In such a scenario, you can see tooltips when you move the mouse on those source nodes.</span></span>  
  
 <span data-ttu-id="fd395-132">下圖顯示某個部分隱藏之目標結構描述節點的工具提示。</span><span class="sxs-lookup"><span data-stu-id="fd395-132">The following figure shows a tooltip to a partially hidden target schema node.</span></span>  
  
 <span data-ttu-id="fd395-133">![結構描述節點的工具提示](../core/media/viewing-tooltips.gif "Viewing_tooltips")</span><span class="sxs-lookup"><span data-stu-id="fd395-133">![Tooltip to a schema node](../core/media/viewing-tooltips.gif "Viewing_tooltips")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd395-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd395-134">See Also</span></span>  
 [<span data-ttu-id="fd395-135">使用 BizTalk 對應工具</span><span class="sxs-lookup"><span data-stu-id="fd395-135">Using BizTalk Mapper</span></span>](../core/using-biztalk-mapper.md)