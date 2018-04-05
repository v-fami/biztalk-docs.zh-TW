---
title: 如何新增參數至協調流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, parameters
ms.assetid: 35c731ed-6327-4de7-8d2e-4d14024bda77
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8328a97631efb2b8454e0a2679b257d35402cf4c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-parameters-to-orchestrations"></a><span data-ttu-id="7dfdf-102">如何新增參數至協調流程</span><span class="sxs-lookup"><span data-stu-id="7dfdf-102">How to Add Parameters to Orchestrations</span></span>
<span data-ttu-id="7dfdf-103">您可以在 [協調流程檢視] 視窗中指定協調流程應該採用何種參數。</span><span class="sxs-lookup"><span data-stu-id="7dfdf-103">You can specify what parameters your orchestration should take in the Orchestration View window.</span></span> <span data-ttu-id="7dfdf-104">協調流程可以採用下列項目做為參數：</span><span class="sxs-lookup"><span data-stu-id="7dfdf-104">An orchestration can take the following items as parameters:</span></span>  
  
-   <span data-ttu-id="7dfdf-105">訊息</span><span class="sxs-lookup"><span data-stu-id="7dfdf-105">Messages</span></span>  
  
-   <span data-ttu-id="7dfdf-106">變數 (包括物件)</span><span class="sxs-lookup"><span data-stu-id="7dfdf-106">Variables (including objects)</span></span>  
  
-   <span data-ttu-id="7dfdf-107">相互關聯集合</span><span class="sxs-lookup"><span data-stu-id="7dfdf-107">Correlation sets</span></span>  
  
-   <span data-ttu-id="7dfdf-108">角色連結</span><span class="sxs-lookup"><span data-stu-id="7dfdf-108">Role links</span></span>  
  
-   <span data-ttu-id="7dfdf-109">連接埠</span><span class="sxs-lookup"><span data-stu-id="7dfdf-109">Ports</span></span>  
  
 <span data-ttu-id="7dfdf-110">參數可以在協調流程之間以 in 參數或 out 參數的形式傳遞。</span><span class="sxs-lookup"><span data-stu-id="7dfdf-110">Parameters can be passed between orchestrations as in parameters or out parameters.</span></span> <span data-ttu-id="7dfdf-111">In 參數可以用傳值或傳址方式來傳遞。</span><span class="sxs-lookup"><span data-stu-id="7dfdf-111">In parameters can be passed by value or by reference.</span></span> <span data-ttu-id="7dfdf-112">Out 參數則能只用傳址方式來傳遞。</span><span class="sxs-lookup"><span data-stu-id="7dfdf-112">Out parameters can only be passed by reference.</span></span> <span data-ttu-id="7dfdf-113">參數可以包含變數、訊息、相互關聯集合、角色連結和連接埠。</span><span class="sxs-lookup"><span data-stu-id="7dfdf-113">Parameters can include variables, messages, correlation sets, role links, and ports.</span></span>  
  
### <a name="to-set-orchestration-parameters"></a><span data-ttu-id="7dfdf-114">若要設定協調流程參數</span><span class="sxs-lookup"><span data-stu-id="7dfdf-114">To set orchestration parameters</span></span>  
  
1.  <span data-ttu-id="7dfdf-115">在 [協調流程檢視] 視窗中，使用**協調流程參數**来加入的變數、 訊息和連接埠資料夾。</span><span class="sxs-lookup"><span data-stu-id="7dfdf-115">In the Orchestration View window, use the **Orchestration Parameters** folder to add variables, messages, and ports.</span></span>  
  
2.  <span data-ttu-id="7dfdf-116">每個項目加入至**協調流程參數**資料夾中，使用 [屬性] 視窗來指定**方向**屬性：</span><span class="sxs-lookup"><span data-stu-id="7dfdf-116">For each item added to the **Orchestration Parameters** folder, use the Properties window to specify the **Direction** property:</span></span>  
  
    -   <span data-ttu-id="7dfdf-117">In，以傳值方式傳入的參數。</span><span class="sxs-lookup"><span data-stu-id="7dfdf-117">In—A parameter passed in by value.</span></span>  
  
    -   <span data-ttu-id="7dfdf-118">Ref，以傳址方式傳入的參數。</span><span class="sxs-lookup"><span data-stu-id="7dfdf-118">Ref—A parameter passed in by reference.</span></span>  
  
    -   <span data-ttu-id="7dfdf-119">Out，以傳址方式傳出的參數。</span><span class="sxs-lookup"><span data-stu-id="7dfdf-119">Out—A parameter passed out by reference.</span></span>  
  
### <a name="to-add-a-parameter-to-an-orchestration"></a><span data-ttu-id="7dfdf-120">若要將參數新增至協調流程</span><span class="sxs-lookup"><span data-stu-id="7dfdf-120">To add a parameter to an orchestration</span></span>  
  
1.  <span data-ttu-id="7dfdf-121">在協調流程檢視 視窗中，以滑鼠右鍵按一下**協調流程參數**資料夾，然後按一下您想要的參數類型。</span><span class="sxs-lookup"><span data-stu-id="7dfdf-121">In the Orchestration View window, right-click the **Orchestration Parameters** folder and then click the kind of parameter you want.</span></span>  
  
2.  <span data-ttu-id="7dfdf-122">對於已設定的連接埠和角色連結，請使用精靈設定參數。</span><span class="sxs-lookup"><span data-stu-id="7dfdf-122">For configured ports and role links, use the wizard to configure the parameter.</span></span>  
  
     <span data-ttu-id="7dfdf-123">-或者-</span><span class="sxs-lookup"><span data-stu-id="7dfdf-123">—Or—</span></span>  
  
     <span data-ttu-id="7dfdf-124">對於其他參數類型，請使用屬性頁設定參數。</span><span class="sxs-lookup"><span data-stu-id="7dfdf-124">For other parameter types, use the properties page to configure the parameter.</span></span>  
  
 <span data-ttu-id="7dfdf-125">**參數型別**</span><span class="sxs-lookup"><span data-stu-id="7dfdf-125">**Parameter types**</span></span>  
  
 <span data-ttu-id="7dfdf-126">參數可以依傳值、傳址方式或以 out 參數的形式傳遞。</span><span class="sxs-lookup"><span data-stu-id="7dfdf-126">Parameters can be passed by value, as reference parameters, and as out parameters.</span></span> <span data-ttu-id="7dfdf-127">當值傳遞至協調流程的參數時，資料的複本製作，並由協調流程使用。</span><span class="sxs-lookup"><span data-stu-id="7dfdf-127">When a parameter is passed by value to an orchestration, a copy of the data is made and used by the orchestration.</span></span>  
  
 <span data-ttu-id="7dfdf-128">當您使用參考參數時，則不會製作任何複本。</span><span class="sxs-lookup"><span data-stu-id="7dfdf-128">When you use a reference parameter, no copy is made.</span></span> <span data-ttu-id="7dfdf-129">包含資料的記憶體位置會在呼叫的程式與協調流程之間共用，此記憶體位置的內容可由協調流程修改。</span><span class="sxs-lookup"><span data-stu-id="7dfdf-129">The memory location that contains the data is shared between the calling program and the orchestration, and the contents of this memory location can be modified by the orchestration.</span></span> <span data-ttu-id="7dfdf-130">這類修改表示參數的值不僅在協調流程中變更，也會在呼叫的程式中變更。</span><span class="sxs-lookup"><span data-stu-id="7dfdf-130">Such a modification means that the value of the parameter is changed not only in the orchestration, but also in the calling program.</span></span>  
  
 <span data-ttu-id="7dfdf-131">Out 參數類似於參考參數，不過協調流程無法假設它在傳入時會包含有效資料，而是呼叫的程式可以預期協調流程會對此參數指派值。</span><span class="sxs-lookup"><span data-stu-id="7dfdf-131">An out parameter is similar to a reference parameter, but the orchestration cannot assume that it contains valid data when passed in; rather, the calling program expects the orchestration to assign a value to this parameter.</span></span>  
  
 <span data-ttu-id="7dfdf-132">**協調流程參數的規則**</span><span class="sxs-lookup"><span data-stu-id="7dfdf-132">**Rules for orchestration parameters**</span></span>  
  
-   <span data-ttu-id="7dfdf-133">您只能傳遞訊息和變數 (包括物件) 做為 out 參數或參考參數。</span><span class="sxs-lookup"><span data-stu-id="7dfdf-133">You can pass only messages and variables (including objects) as out or reference parameters.</span></span>  
  
-   <span data-ttu-id="7dfdf-134">您無法傳遞出或參考中的協調流程參數**啟動協調流程**圖形。</span><span class="sxs-lookup"><span data-stu-id="7dfdf-134">You cannot pass out or reference parameters to an orchestration in a **Start Orchestration** shape.</span></span>  
  
-   <span data-ttu-id="7dfdf-135">在參數中，包括任何角色連結和動態連接埠，都一定得在傳遞至協調流程之前獲得指派。</span><span class="sxs-lookup"><span data-stu-id="7dfdf-135">In parameters, including any role links and dynamic ports, must be definitely assigned before being passed to an orchestration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dfdf-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7dfdf-136">See Also</span></span>  
 <span data-ttu-id="7dfdf-137">[協調流程圖形](../core/orchestration-shapes.md) </span><span class="sxs-lookup"><span data-stu-id="7dfdf-137">[Orchestration Shapes](../core/orchestration-shapes.md) </span></span>  
 <span data-ttu-id="7dfdf-138">[如何新增圖形至協調流程](../core/how-to-add-shapes-to-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="7dfdf-138">[How to Add Shapes to Orchestrations](../core/how-to-add-shapes-to-orchestrations.md) </span></span>  
 [<span data-ttu-id="7dfdf-139">如何使用選取成品類型對話方塊</span><span class="sxs-lookup"><span data-stu-id="7dfdf-139">How to Use the Select Artifact Type Dialog Box</span></span>](../core/how-to-use-the-select-artifact-type-dialog-box.md)