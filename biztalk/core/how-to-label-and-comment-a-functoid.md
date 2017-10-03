---
title: "如何加上標籤與註解的運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.mapper.functiod.general
ms.assetid: 58ff3a07-cbb6-4817-b301-d2b434ed2ad9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fccdeefa35f9abb5a0c3158dba518d524811c611
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-label-and-comment-a-functoid"></a><span data-ttu-id="88ad8-102">如何為運算質加上標籤與註解</span><span class="sxs-lookup"><span data-stu-id="88ad8-102">How to Label and Comment a Functoid</span></span>
<span data-ttu-id="88ad8-103">標籤與註解有助於記錄對應中的運算質或連結用途。</span><span class="sxs-lookup"><span data-stu-id="88ad8-103">Labels and comments are helpful to document the purpose of a functoid or a link in a map.</span></span> <span data-ttu-id="88ad8-104">您可以使用**標籤**屬性提供運算質的名稱。</span><span class="sxs-lookup"><span data-stu-id="88ad8-104">You can use the **Label** property to provide a name for a functoid.</span></span> <span data-ttu-id="88ad8-105">**註解**屬性可讓您提供的運算質，它正在執行之作業的相關的一般相關資訊的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="88ad8-105">The **Comments** property enables you to provide additional information about the functoid, typically relevant information about the operation being performed by it.</span></span>  
  
 <span data-ttu-id="88ad8-106">下圖顯示的標籤和註解的運算質。</span><span class="sxs-lookup"><span data-stu-id="88ad8-106">The following figure shows the label and comments for a functoid.</span></span> <span data-ttu-id="88ad8-107">運算質從來源結構描述新增兩個輸入 (Field1 與 Field3)，並將結果輸出到目標結構描述中的 Field4。</span><span class="sxs-lookup"><span data-stu-id="88ad8-107">The functoid adds two inputs (Field1 and Field3) from the source schema and outputs the result to Field4 in the target schema.</span></span> <span data-ttu-id="88ad8-108">在此範例中，運算質標籤為「新增 Field1 與 Field3」，註解為「新增是 Field4 的輸出」。</span><span class="sxs-lookup"><span data-stu-id="88ad8-108">In this example, the functoid label is “Add Field1 and Field3” and the comment is “The addition is an output to Field4”.</span></span>  
  
 <span data-ttu-id="88ad8-109">![插入運算質標籤及註解](../core/media/label.gif "Label_")</span><span class="sxs-lookup"><span data-stu-id="88ad8-109">![Inserting functoid labels and comments](../core/media/label.gif "Label_")</span></span>  
  
 <span data-ttu-id="88ad8-110">因為運算質可能是極複雜之對應的一部分，適當地加上標籤並提供相關註解是很重要的。</span><span class="sxs-lookup"><span data-stu-id="88ad8-110">Because a functoid can be a part of very complex mapping, it is important to label it properly and also to provide relevant comments.</span></span> <span data-ttu-id="88ad8-111">您可以為運算質和連結加上標籤。</span><span class="sxs-lookup"><span data-stu-id="88ad8-111">You can label both functoids and links.</span></span> <span data-ttu-id="88ad8-112">如需如何標示連結資訊，請參閱[如何標示連結](../core/how-to-label-a-link.md)。</span><span class="sxs-lookup"><span data-stu-id="88ad8-112">For information on how to label a link, see [How to Label a Link](../core/how-to-label-a-link.md).</span></span>  
  
 <span data-ttu-id="88ad8-113">您可以下列方式為運算質加上標籤與註解：</span><span class="sxs-lookup"><span data-stu-id="88ad8-113">You can label and comment a functoid in the following ways:</span></span>  
  
-   <span data-ttu-id="88ad8-114">使用**設定\<運算質 > 運算質** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="88ad8-114">By using the **Configure \<Functoid> Functoid** dialog box.</span></span>  
  
-   <span data-ttu-id="88ad8-115">使用**屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="88ad8-115">By using the **Properties** window.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="88ad8-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="88ad8-116">Prerequisites</span></span>  
 <span data-ttu-id="88ad8-117">這些指示需要執行中的 BizTalk 對應工具。</span><span class="sxs-lookup"><span data-stu-id="88ad8-117">These instructions require that BizTalk Mapper is running.</span></span>  
  
### <a name="to-label-and-comment-a-functoid-from-configure-dialog-box"></a><span data-ttu-id="88ad8-118">從 [設定] 對話方塊為運算質加上標籤與註解</span><span class="sxs-lookup"><span data-stu-id="88ad8-118">To label and comment a functoid from Configure dialog box</span></span>  
  
1.  <span data-ttu-id="88ad8-119">以滑鼠右鍵按一下您想要標籤和註解，然後再按一下運算質**設定運算質輸入**。</span><span class="sxs-lookup"><span data-stu-id="88ad8-119">Right-click the functoid you want to label and comment, and then click **Configure Functoid Inputs**.</span></span>  
  
2.  <span data-ttu-id="88ad8-120">在**設定\<運算質 > 運算質**對話方塊中，按一下 [**標籤與註解**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="88ad8-120">In the **Configure \<Functoid> Functoid** dialog box, click the **Label and Comments** tab.</span></span>  
  
3.  <span data-ttu-id="88ad8-121">輸入下列資訊，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="88ad8-121">Enter the following information, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="88ad8-122">**標籤 –**輸入新名稱。</span><span class="sxs-lookup"><span data-stu-id="88ad8-122">**Label –** Enter the new name.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="88ad8-123">允許的字元數目上限是 256。</span><span class="sxs-lookup"><span data-stu-id="88ad8-123">The maximum number of characters allowed is 256.</span></span> <span data-ttu-id="88ad8-124">如果指定超過 256 個字元的字串，則接受前 256 個字元，其餘部分會被捨棄。</span><span class="sxs-lookup"><span data-stu-id="88ad8-124">If a string with more than 256 characters is specified, the first 256 characters are accepted and the rest are discarded.</span></span>  
  
    -   <span data-ttu-id="88ad8-125">**註解 –**運算質輸入的註解。</span><span class="sxs-lookup"><span data-stu-id="88ad8-125">**Comments –** Enter the comments for the functoid.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="88ad8-126">允許的字元數目上限為 1024年。</span><span class="sxs-lookup"><span data-stu-id="88ad8-126">The maximum number of characters allowed is 1024.</span></span> <span data-ttu-id="88ad8-127">如果指定超過 1024 個字元的字串，則先 1024年個字元會接受，而且會捨棄其餘部分。</span><span class="sxs-lookup"><span data-stu-id="88ad8-127">If a string with more than 1024 characters is specified, the first 1024 characters are accepted and the rest are discarded.</span></span>  
  
### <a name="to-label-and-comment-a-functoid-from-properties-window"></a><span data-ttu-id="88ad8-128">從 [屬性] 視窗為運算質加上標籤與註解</span><span class="sxs-lookup"><span data-stu-id="88ad8-128">To label and comment a functoid from Properties window</span></span>  
  
1.  <span data-ttu-id="88ad8-129">選取您要加上標籤與註解的運算質。</span><span class="sxs-lookup"><span data-stu-id="88ad8-129">Select the functoid you want to label and comment.</span></span>  
  
2.  <span data-ttu-id="88ad8-130">在**屬性**視窗中，輸入下列資訊，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="88ad8-130">In the **Properties** window, enter the following information, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="88ad8-131">**標籤 –**輸入新名稱。</span><span class="sxs-lookup"><span data-stu-id="88ad8-131">**Label –** Enter the new name.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="88ad8-132">允許的字元數目上限是 256。</span><span class="sxs-lookup"><span data-stu-id="88ad8-132">The maximum number of characters allowed is 256.</span></span> <span data-ttu-id="88ad8-133">如果指定超過 256 個字元的字串，則接受前 256 個字元，其餘部分會被捨棄。</span><span class="sxs-lookup"><span data-stu-id="88ad8-133">If a string with more than 256 characters is specified, the first 256 characters are accepted and the rest are discarded.</span></span>  
  
    -   <span data-ttu-id="88ad8-134">**註解 –**運算質輸入的註解。</span><span class="sxs-lookup"><span data-stu-id="88ad8-134">**Comments –** Enter the comments for the functoid.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="88ad8-135">允許的字元數目上限為 1024年。</span><span class="sxs-lookup"><span data-stu-id="88ad8-135">The maximum number of characters allowed is 1024.</span></span> <span data-ttu-id="88ad8-136">如果指定超過 1024 個字元的字串，則先 1024年個字元會接受，而且會捨棄其餘部分。</span><span class="sxs-lookup"><span data-stu-id="88ad8-136">If a string with more than 1024 characters is specified, the first 1024 characters are accepted and the rest are discarded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88ad8-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88ad8-137">See Also</span></span>  
 [<span data-ttu-id="88ad8-138">編輯運算質屬性和輸入的參數</span><span class="sxs-lookup"><span data-stu-id="88ad8-138">Editing Functoid Properties and Input Parameters</span></span>](../core/editing-functoid-properties-and-input-parameters.md)