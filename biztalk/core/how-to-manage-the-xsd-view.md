---
title: 如何管理 XSD 檢視 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3245ebf0-6128-47b4-8e88-ea06ececbc15
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e38707d25355b8ee46a653971b459f1f799614b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004214"
---
# <a name="how-to-manage-the-xsd-view"></a><span data-ttu-id="2ebea-102">如何管理 XSD 檢視</span><span class="sxs-lookup"><span data-stu-id="2ebea-102">How to Manage the XSD View</span></span>
<span data-ttu-id="2ebea-103">與 XSD 檢視相關的管理工作可以分為三類：變更其大小、變更其背景色彩和字型以及變更其重新整理特性。</span><span class="sxs-lookup"><span data-stu-id="2ebea-103">Management tasks with respect to the XSD view can be divided into three categories: changing its size, changing its background color and font, and changing its refresh characteristics.</span></span>  
  
 <span data-ttu-id="2ebea-104">最後一個類別，即重新整理特性，在使用自動重新整理可能造成長時間延遲的大型結構描述時最有用。</span><span class="sxs-lookup"><span data-stu-id="2ebea-104">The latter category, concerning refresh characteristics, is most useful when working with large schemas, for which using automatic refresh might cause undesirable delays.</span></span> <span data-ttu-id="2ebea-105">在此情況下，您可以停用自動 (連續) 重新整理，以必要時手動重新整理 XSD 檢視取代。</span><span class="sxs-lookup"><span data-stu-id="2ebea-105">In such cases, you can disable automatic (continuous) refresh, and instead refresh the XSD view manually as needed.</span></span>  
  
 <span data-ttu-id="2ebea-106">本主題提供這些工作的逐步解說。</span><span class="sxs-lookup"><span data-stu-id="2ebea-106">This topic provides step-by-step instructions for these tasks.</span></span>  
  
### <a name="to-make-the-xsd-view-taller-or-shorter"></a><span data-ttu-id="2ebea-107">使 XSD 檢視較高或較矮</span><span class="sxs-lookup"><span data-stu-id="2ebea-107">To make the XSD view taller or shorter</span></span>  
  
1. <span data-ttu-id="2ebea-108">將滑鼠指標移至 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 主要編輯視窗的下邊緣 (在結構描述樹狀結構檢視旁會顯示 XSD 檢視)，直到指標變成標準的視窗垂直大小調整圖示。</span><span class="sxs-lookup"><span data-stu-id="2ebea-108">Move the mouse pointer to the bottom edge of the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] main editing window, which displays the XSD view side-by-side with the schema tree view, until the cursor changes to the standard window vertical resizing icon.</span></span>  
  
2. <span data-ttu-id="2ebea-109">按住滑鼠左鍵並上下拖曳視窗邊緣。</span><span class="sxs-lookup"><span data-stu-id="2ebea-109">Click and hold the left mouse button and drag the window edge either up or down.</span></span>  
  
    <span data-ttu-id="2ebea-110">藉由垂直調整整個主要編輯視窗的大小，您已垂直調整 XSD 檢視的大小。</span><span class="sxs-lookup"><span data-stu-id="2ebea-110">You have vertically resized the XSD view by vertically resizing the entire main editing window.</span></span>  
  
### <a name="to-make-the-xsd-view-wider-or-more-narrow"></a><span data-ttu-id="2ebea-111">使 XSD 檢視較寬或較窄</span><span class="sxs-lookup"><span data-stu-id="2ebea-111">To make the XSD view wider or more narrow</span></span>  
  
1. <span data-ttu-id="2ebea-112">移動滑鼠游標至 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 主要編輯視窗中的窗格分割線 (用來分割 XSD 檢視和結構描述樹狀結構檢視)，直到游標變成標準的視窗水平調整大小圖示。</span><span class="sxs-lookup"><span data-stu-id="2ebea-112">Move the mouse pointer to the pane divider in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] main editing window, which divides the XSD view from the schema tree view, until the cursor changes to the standard window horizontal resizing icon.</span></span>  
  
2. <span data-ttu-id="2ebea-113">按住滑鼠左鍵並左右拖曳 (調整寬窄) 窗格邊緣。</span><span class="sxs-lookup"><span data-stu-id="2ebea-113">Click and hold the left mouse button and drag the pane edge either left (wider) or right (narrower).</span></span>  
  
    <span data-ttu-id="2ebea-114">藉由變更 XSD 檢視所使用的主要編輯視窗的大小 (相對於結構描述樹狀結構檢視的大小)，您已水平調整 XSD 檢視的大小。</span><span class="sxs-lookup"><span data-stu-id="2ebea-114">You have horizontally resized the XSD view by changing the amount of the main editing window dedicated to the XSD view, relative to the schema tree view.</span></span>  
  
    <span data-ttu-id="2ebea-115">您也可以水平調整整個主要編輯視窗的大小，使 XSD 檢視較寬或較窄。</span><span class="sxs-lookup"><span data-stu-id="2ebea-115">You can also make the XSD view wider or narrower by horizontally resizing the entire main editing window.</span></span>  
  
### <a name="to-change-the-background-color-andor-font-used-by-the-xsd-view"></a><span data-ttu-id="2ebea-116">變更 XSD 檢視所使用的背景色彩和/或字型</span><span class="sxs-lookup"><span data-stu-id="2ebea-116">To change the background color and/or font used by the XSD view</span></span>  
  
1. <span data-ttu-id="2ebea-117">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]的 **[工具]** 功能表上，按一下 **[選項]**。</span><span class="sxs-lookup"><span data-stu-id="2ebea-117">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **Tools** menu, click **Options**.</span></span>  
  
2. <span data-ttu-id="2ebea-118">在 [**選項**] 對話方塊中，按一下 [BizTalk 編輯器] 資料夾中，並如有必要，展開**結構描述顯示**類別目錄，按一下加號 （+） 圖示。</span><span class="sxs-lookup"><span data-stu-id="2ebea-118">In the **Options** dialog box, click the BizTalk Editor folder, and if necessary, expand the **Schema Display** category by clicking the plus (+) icon.</span></span>  
  
3. <span data-ttu-id="2ebea-119">使用下拉式色彩選擇器來變更背景色彩和/或字型和/或**字型**相關聯的對話方塊**XSD 檢視背景色彩**並**XSD 檢視字型**屬性，分別。</span><span class="sxs-lookup"><span data-stu-id="2ebea-119">Change the background color and/or font by using the drop-down color picker and/or **Font** dialog box associated with the **XSD View Background Color** and **XSD View Font** properties, respectively.</span></span>  
  
    <span data-ttu-id="2ebea-120">存取權**字型**對話方塊中，使用省略符號 (**...**) 按鈕位於右邊**XSD 檢視字型**屬性值方塊。</span><span class="sxs-lookup"><span data-stu-id="2ebea-120">Access the **Font** dialog box by using the ellipsis (**…**) button located at the right end of the **XSD View Font** property value box.</span></span>  
  
### <a name="to-turn-automatic-refresh-of-the-xsd-view-on-and-off"></a><span data-ttu-id="2ebea-121">開啟和關閉 XSD 檢視的自動重新整理</span><span class="sxs-lookup"><span data-stu-id="2ebea-121">To turn automatic refresh of the XSD view on and off</span></span>  
  
-   <span data-ttu-id="2ebea-122">在 「 BizTalk 編輯器 」 中下, 面**XSD**索引標籤上，按一下**關閉自動重新整理**或是**開啟自動重新整理**。</span><span class="sxs-lookup"><span data-stu-id="2ebea-122">In BizTalk Editor, below the **XSD** tab, click **Turn off auto refresh** or **Turn on auto refresh**.</span></span>  
  
     <span data-ttu-id="2ebea-123">自動重新整理關閉時，XSD 檢視為空白。</span><span class="sxs-lookup"><span data-stu-id="2ebea-123">When auto-refresh is off, the XSD view is blank.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="2ebea-124">依照預設，自動重新整理為開啟。</span><span class="sxs-lookup"><span data-stu-id="2ebea-124">By default, auto-refresh is on.</span></span> <span data-ttu-id="2ebea-125">當您的結構描述變得越來越大，關閉自動重新整理功能，改為視需要手動重新整理結構描述也漸漸變得重要。</span><span class="sxs-lookup"><span data-stu-id="2ebea-125">As your schemas become bigger and bigger, it becomes increasingly important for you to turn off the automatic refresh feature and refresh your schema manually as needed.</span></span>  
  
### <a name="to-manually-refresh-the-xsd-view"></a><span data-ttu-id="2ebea-126">手動重新整理 XSD 檢視</span><span class="sxs-lookup"><span data-stu-id="2ebea-126">To manually refresh the XSD view</span></span>  
  
-   <span data-ttu-id="2ebea-127">在  **BizTalk**功能表上，按一下**重新整理 XSD**。</span><span class="sxs-lookup"><span data-stu-id="2ebea-127">On the **BizTalk** menu, click **Refresh XSD**.</span></span>  
  
     <span data-ttu-id="2ebea-128">會更新 XSD 檢視，以反映您對結構描述樹狀結構所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="2ebea-128">The XSD view updates to reflect any changes you have made to the schema tree.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2ebea-129">您可以也手動重新整理 XSD 檢視，即可**重新整理 XSD**相關聯的結構描述樹狀目錄中，或按一下每個節點的捷徑功能表上**重新整理**下面的連結**XSD** XSD 檢視中的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="2ebea-129">You can also manually refresh the XSD view by clicking **Refresh XSD** on the shortcut menu associated with every node in the schema tree, or by clicking the **Refresh** link below the **XSD** tab in the XSD view.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ebea-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ebea-130">See Also</span></span>  
 [<span data-ttu-id="2ebea-131">使用 BizTalk 編輯器</span><span class="sxs-lookup"><span data-stu-id="2ebea-131">Using BizTalk Editor</span></span>](../core/using-biztalk-editor.md)