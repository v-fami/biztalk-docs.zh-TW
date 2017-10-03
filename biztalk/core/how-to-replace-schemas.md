---
title: "如何取代結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 104e60d3-1303-4e56-b13a-c10ab14ba383
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e8d4e3be39d27d30ca8fa6062bb452a8ce32a12
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-replace-schemas"></a><span data-ttu-id="7e259-102">如何取代結構描述</span><span class="sxs-lookup"><span data-stu-id="7e259-102">How to Replace Schemas</span></span>
<span data-ttu-id="7e259-103">您有時候可能想要取代現有對應中的來源或目的結構描述，例如當您收到來自交易夥伴的已更新結構描述時。</span><span class="sxs-lookup"><span data-stu-id="7e259-103">There may be times when you want to replace either the source or destination schema in an existing map, such as when you receive an updated schema from a trading partner.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e259-104">「BizTalk 對應工具」會嘗試維護已保留結構描述和已取代結構描述之間的所有現有連結。</span><span class="sxs-lookup"><span data-stu-id="7e259-104">The BizTalk Mapper attempts to maintain all existing links between the retained schema and the replaced schema.</span></span>  
  
## <a name="replace-a-source-or-destination-schema"></a><span data-ttu-id="7e259-105">取代來源或目的結構描述</span><span class="sxs-lookup"><span data-stu-id="7e259-105">Replace a source or destination schema</span></span>  
  
1.  <span data-ttu-id="7e259-106">來源或目的結構描述樹狀檢視中，以滑鼠右鍵按一下，然後選取**取代結構描述**。</span><span class="sxs-lookup"><span data-stu-id="7e259-106">Right-click either the source or destination schema tree view, and then select **Replace Schema**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7e259-107">或者，您也可以按下鍵盤的 CTRL+M、CTRL+S。</span><span class="sxs-lookup"><span data-stu-id="7e259-107">Alternatively, you can also press CTRL+M, CTRL+S from the keyboard.</span></span> <span data-ttu-id="7e259-108">如需對應工具鍵盤快速鍵的完整清單，請參閱[BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。</span><span class="sxs-lookup"><span data-stu-id="7e259-108">For a complete list of Mapper keyboard shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
2.  <span data-ttu-id="7e259-109">在**BizTalk 型別選擇器**對話方塊方塊中，展開 **結構描述**節點在樹狀目錄中，選取適當的結構描述，然後選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="7e259-109">In the **BizTalk Type Picker** dialog box, expand the **Schemas** node in the tree, select the appropriate schema, and then select **OK**.</span></span>  
  
     <span data-ttu-id="7e259-110">![選取的結構描述](../core/media/biztalk-typepicker.gif "BizTalk_TypePicker")</span><span class="sxs-lookup"><span data-stu-id="7e259-110">![Select the Schema](../core/media/biztalk-typepicker.gif "BizTalk_TypePicker")</span></span>  

    > [!TIP] 
    > <span data-ttu-id="7e259-111">**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** ，您可以調整 [型別選擇器] 視窗，請參閱您的結構描述的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="7e259-111">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]**, you can resize the Type Picker window to see the full name of your schema.</span></span>
      
     <span data-ttu-id="7e259-112">如果只存在取代結構描述中的單一根節點或根節點，已建立的取代結構描述使用**根參考**屬性**結構描述**] 節點，開啟 [取代結構描述在相關窗格中，且您不需要執行步驟 3。</span><span class="sxs-lookup"><span data-stu-id="7e259-112">If only a single root exists in the replacement schema, or a root node has been established for the replacement schema using the **Root Reference** property of the **Schema** node, the replacement schema opens in the relevant pane, and you will not need to perform step 3.</span></span>  
  
3.  <span data-ttu-id="7e259-113">如果多個根節點存在於目的地結構描述，而且沒有根節點，已建立的目的地結構描述使用**根參考**屬性**結構描述**節點，請在**的根節點\<*來源/目標*> 結構描述 * * 對話方塊中，選取適當的根節點，然後選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="7e259-113">If multiple root nodes exist in the destination schema, and no root node has been established for the destination schema using the **Root Reference** property of the **Schema** node, in the **Root Node for \<*Source/Target*> Schema** dialog box, select the appropriate root node, and then select **OK**.</span></span>  
  
     <span data-ttu-id="7e259-114">取代結構描述會在相關窗格中開啟。</span><span class="sxs-lookup"><span data-stu-id="7e259-114">The replacement schema opens in the relevant pane.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7e259-115">如果取代結構描述時找不到相關的記錄/欄位，某些連結可能會遺失。</span><span class="sxs-lookup"><span data-stu-id="7e259-115">While replacing schema, if relevant records/fields are not found, some links may get lost.</span></span> <span data-ttu-id="7e259-116">只有當您選取時，會取代結構描述**是**上**確認** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7e259-116">The schema is replaced only when you select **Yes** on the **Confirmation**  dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e259-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e259-117">See Also</span></span>  
 [<span data-ttu-id="7e259-118">管理專案中的對應</span><span class="sxs-lookup"><span data-stu-id="7e259-118">Managing Maps Within Projects</span></span>](../core/managing-maps-within-projects.md)