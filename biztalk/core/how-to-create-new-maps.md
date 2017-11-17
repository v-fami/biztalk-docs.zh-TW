---
title: "如何建立新對應 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43b36cd8-f28e-4349-87d5-c94b7d8761bf
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 910d79782f4332ae1d706e12a8c5dda8c399a41b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-new-maps"></a><span data-ttu-id="47d7e-102">如何建立新的對應</span><span class="sxs-lookup"><span data-stu-id="47d7e-102">How to Create New Maps</span></span>

## <a name="overview"></a><span data-ttu-id="47d7e-103">概觀</span><span class="sxs-lookup"><span data-stu-id="47d7e-103">Overview</span></span>
<span data-ttu-id="47d7e-104">若要建置新的 BizTalk 對應，請執行三個高階步驟：</span><span class="sxs-lookup"><span data-stu-id="47d7e-104">To build a new BizTalk map, there are three high-level steps to perform:</span></span>  
  
1.  <span data-ttu-id="47d7e-105">在 BizTalk 專案內建立新對應。</span><span class="sxs-lookup"><span data-stu-id="47d7e-105">Create the new map within a BizTalk project.</span></span>  
  
2.  <span data-ttu-id="47d7e-106">將來源與目的結構描述加入至對應。</span><span class="sxs-lookup"><span data-stu-id="47d7e-106">Add the source and destination schemas to the map.</span></span>  
  
3.  <span data-ttu-id="47d7e-107">建置連結集或可能需要建置中繼運算質以指定來源結構描述對應到目的結構描述的方式。</span><span class="sxs-lookup"><span data-stu-id="47d7e-107">Build the set of links and, perhaps, intermediate functoids specifying how the source schema maps to the destination schema.</span></span>  
  
 <span data-ttu-id="47d7e-108">在目前的內容中，這三個步驟中的前兩個被視為「建立」對應。</span><span class="sxs-lookup"><span data-stu-id="47d7e-108">In the current context, the first two of these three steps is considered "creating" the map.</span></span> <span data-ttu-id="47d7e-109">第三步驟則被視為「建置」對應。</span><span class="sxs-lookup"><span data-stu-id="47d7e-109">The third step is considered "building" the map.</span></span> <span data-ttu-id="47d7e-110">如需的許多建置對應程序的相關工作的逐步指示，請參閱[更加建立複雜的對應使用運算質](../core/using-functoids-to-create-more-complex-mappings.md)。</span><span class="sxs-lookup"><span data-stu-id="47d7e-110">For step-by-step instructions on many of the tasks related to the process of building the map, see [Using Functoids to Create More Complex Mappings](../core/using-functoids-to-create-more-complex-mappings.md).</span></span>  
  
## <a name="create-a-new-map"></a><span data-ttu-id="47d7e-111">建立新的對應</span><span class="sxs-lookup"><span data-stu-id="47d7e-111">Create a new map</span></span> 
  
1.  <span data-ttu-id="47d7e-112">以滑鼠右鍵按一下 BizTalk 專案，在 [方案總管] 中，選取**新增**，然後選取**新項目**。</span><span class="sxs-lookup"><span data-stu-id="47d7e-112">Right-click a BizTalk project in Solution Explorer, select **Add**, and then select **New Item**.</span></span>  
  
2.  <span data-ttu-id="47d7e-113">在**加入新項目**對話方塊中，於**範本**區域中，選取**對應**。</span><span class="sxs-lookup"><span data-stu-id="47d7e-113">In the **Add New Item** dialog box, in the **Templates** area, select **Map**.</span></span>  
  
3.  <span data-ttu-id="47d7e-114">選取的文字中**名稱**方塊，輸入對應的名稱，然後選取**新增**。</span><span class="sxs-lookup"><span data-stu-id="47d7e-114">Select the text in the **Name** box, type a name for the map, and then select **Add**.</span></span>  
  
     <span data-ttu-id="47d7e-115">BizTalk 對應工具會開啟在 Microsoft[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]編輯視窗中，顯示三個不同的窗格，來並行。</span><span class="sxs-lookup"><span data-stu-id="47d7e-115">BizTalk Mapper opens in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] editing window, showing three distinct panes, side-by-side.</span></span> <span data-ttu-id="47d7e-116">由左至右，三個窗格依次顯示來源結構描述、格線 (可能有多頁) 和目的結構描述。</span><span class="sxs-lookup"><span data-stu-id="47d7e-116">From left to right, these panes show the source schema, the grid (which may have multiple pages), and the destination schema.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="47d7e-117">以下名稱不能作為對應："XmlContent"、"SourceSchemas"、"TargetSchemas" 或 "XsltArgumentListContent"。</span><span class="sxs-lookup"><span data-stu-id="47d7e-117">You cannot use the following names for maps: "XmlContent", "SourceSchemas", "TargetSchemas", or "XsltArgumentListContent".</span></span> <span data-ttu-id="47d7e-118">不能使用這些名稱的原因是編譯到 .NET 組件時會因為產生 C# 碼而發生命名限制。</span><span class="sxs-lookup"><span data-stu-id="47d7e-118">These names cannot be used because compilation into a .NET assembly produces naming restrictions as the result of generated C# code.</span></span>  
  
4.  <span data-ttu-id="47d7e-119">在 BizTalk 對應工具的左窗格中，選取**開啟來源結構描述**。</span><span class="sxs-lookup"><span data-stu-id="47d7e-119">In BizTalk Mapper, in the left pane, select **Open Source Schema**.</span></span>  
  
5.  <span data-ttu-id="47d7e-120">在**BizTalk 型別選擇器**對話方塊方塊中，展開 [**結構描述**] 節點，選取適當的來源結構描述，然後選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="47d7e-120">In the **BizTalk Type Picker** dialog box, expand the **Schemas** node, select the appropriate source schema, and then select **OK**.</span></span>  

    > [!TIP] 
    > <span data-ttu-id="47d7e-121">**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** ，您可以調整 [型別選擇器] 視窗，請參閱您的結構描述的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="47d7e-121">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]**, you can resize the Type Picker window to see the full name of your schema.</span></span>
  
     <span data-ttu-id="47d7e-122">如果只存在來源結構描述中的單一根節點或根節點，已建立的結構描述使用**根參考**屬性**結構描述** 節點，在左的窗格中，而且您開啟來源結構描述可以繼續進行步驟 7。</span><span class="sxs-lookup"><span data-stu-id="47d7e-122">If only a single root exists in the source schema, or a root node has been established for the schema using the **Root Reference** property of the **Schema** node, the source schema opens in the left pane, and you can proceed to step 7.</span></span>  
  
6.  <span data-ttu-id="47d7e-123">如果來源結構描述有多個根節點，並沒有根節點，已建立的來源結構描述使用**結構描述**節點的**根參考**屬性，請在**來源根節點結構描述**對話方塊中，選取適當的根節點，然後選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="47d7e-123">If the source schema has multiple root nodes, and no root node has been established for the source schema using the **Schema** node's **Root Reference** property, in the **Root Node for Source Schema** dialog box, select the appropriate root node, and select **OK**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="47d7e-124">如果您在 BizTalk 對應工具中選擇的根節點的結構描述，然後稍後變更**根參考**屬性結構描述，下次您在 BizTalk 對應工具中開啟結構描述中的根節點不會更新來設定新的根參考在 [BizTalk 編輯器]。</span><span class="sxs-lookup"><span data-stu-id="47d7e-124">If you choose a root node for a schema in BizTalk Mapper and then later change the **Root Reference** property in the schema, the next time you open the schema in BizTalk Mapper, the root node will not update to the new root reference configured in BizTalk Editor.</span></span>  
  
7.  <span data-ttu-id="47d7e-125">在 BizTalk 對應工具中，在右窗格中，選取**開啟目的結構描述**。</span><span class="sxs-lookup"><span data-stu-id="47d7e-125">In BizTalk Mapper, in the right pane, select **Open Destination Schema**.</span></span>  
  
8.  <span data-ttu-id="47d7e-126">在**BizTalk 型別選擇器**對話方塊方塊中，展開 **結構描述**節點在樹狀目錄中，如果有必要，選取適當的目的地結構描述，然後選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="47d7e-126">In the **BizTalk Type Picker** dialog box, expand the **Schema** node in the tree, if necessary, select the appropriate destination schema, and then select **OK**.</span></span>  
  
     <span data-ttu-id="47d7e-127">如果只有單一根節點存在於目的結構描述，或根節點，已建立的目的地結構描述使用**根參考**屬性**結構描述**] 節點，開啟 [目的結構描述在右窗格中，且您不需要執行步驟 9。</span><span class="sxs-lookup"><span data-stu-id="47d7e-127">If only a single root exists in the destination schema, or a root node has been established for the destination schema using the **Root Reference** property of the **Schema** node, the destination schema opens in the right pane, and you will not need to perform step 9.</span></span>  
  
9. <span data-ttu-id="47d7e-128">如果目的地結構描述有多個根節點，並沒有根節點，已建立的目的地結構描述使用**根參考**屬性**結構描述**節點，請在**根節點目標結構描述的**對話方塊中，選取適當的根節點，然後選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="47d7e-128">If the destination schema has multiple root nodes, and no root node has been established for the destination schema using the **Root Reference** property of the **Schema** node, in the **Root Node for Target Schema** dialog box, select the appropriate root node, and select **OK**.</span></span>  
  
     <span data-ttu-id="47d7e-129">目的結構描述在右窗格中開啟。</span><span class="sxs-lookup"><span data-stu-id="47d7e-129">The destination schema opens in the right pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47d7e-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47d7e-130">See Also</span></span>  
 [<span data-ttu-id="47d7e-131">管理專案中的對應</span><span class="sxs-lookup"><span data-stu-id="47d7e-131">Managing Maps Within Projects</span></span>](../core/managing-maps-within-projects.md)