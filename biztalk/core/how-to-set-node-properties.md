---
title: "如何設定節點屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0c79eac-d9ba-45e2-a6e9-770b2bcb2067
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13dc0f13814808a69c4c4b9c3976e9047acde5b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-node-properties"></a><span data-ttu-id="e49e4-102">如何設定節點屬性</span><span class="sxs-lookup"><span data-stu-id="e49e4-102">How to Set Node Properties</span></span>
<span data-ttu-id="e49e4-103">將節點插入 BizTalk 結構描述後，您通常需要變更該節點屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="e49e4-103">After inserting a node into a BizTalk schema, you will often need to change the properties of that node from their default values.</span></span> <span data-ttu-id="e49e4-104">每種類型的節點都有不同的屬性集，在這些其中一個屬性集中，一個屬性的設定可影響其他屬性的可用性。</span><span class="sxs-lookup"><span data-stu-id="e49e4-104">Each type of node has a distinct set of properties, and within one of those sets, the settings of one property can affect the availability of other properties.</span></span> <span data-ttu-id="e49e4-105">例如，才能設定**預設換行字元**屬性**結構描述** 節點，您必須設定**Default Wrap Character Type**任一屬性**字元**或**十六進位**，藉此建立要代表先前屬性的格式。</span><span class="sxs-lookup"><span data-stu-id="e49e4-105">For example, before setting the **Default Wrap Character** property of the **Schema** node, you must set the **Default Wrap Character Type** property to either **Character** or **Hexadecimal**, thereby establishing the format in which you intend to represent the former property.</span></span> <span data-ttu-id="e49e4-106">此外，這些屬性可供使用，都是整個**剖析**屬性類別目錄所屬，除非**一般檔案延伸模組**啟用利用**結構描述編輯器擴充功能**屬性。</span><span class="sxs-lookup"><span data-stu-id="e49e4-106">Further, neither of these properties is available, nor is the entire **Parse** property category to which they belong, unless **Flat File Extension** is enabled by using the **Schema Editor Extensions** property.</span></span>  

 <span data-ttu-id="e49e4-107">節點屬性相當廣泛而且可以很複雜，就如同它們所支援的 XML 結構描述定義 (XSD) 語言一樣。</span><span class="sxs-lookup"><span data-stu-id="e49e4-107">Node properties are extensive and can be complex, as is the XML Schema definition (XSD) language that they support.</span></span> <span data-ttu-id="e49e4-108">本主題僅簡單描述與檢查和設定節點屬性相關的一般步驟。</span><span class="sxs-lookup"><span data-stu-id="e49e4-108">This topic only briefly describes the general steps involved in examining and setting node properties.</span></span> <span data-ttu-id="e49e4-109">如需這些屬性的詳細資訊，包括，比方說，其預設值的相關資訊以及允許的值，請參閱**結構描述屬性參考**。</span><span class="sxs-lookup"><span data-stu-id="e49e4-109">For detailed information about these properties, including, for example, information about their default and allowed values, see the **Schema Property Reference**.</span></span> <span data-ttu-id="e49e4-110">如更詳細的 XSD 概念和構成這些節點屬性的項目相關資訊，請直接參考資訊有關[在網站上的 XSD](../core/xsd-resources-on-the-web.md)。</span><span class="sxs-lookup"><span data-stu-id="e49e4-110">For even more detailed information about the XSD concepts and elements that underlie most of these node properties, refer directly to information about [XSD on the Web](../core/xsd-resources-on-the-web.md).</span></span>  

<span data-ttu-id="e49e4-111">這些屬性和結構描述屬性參考上的進一歩[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="e49e4-111">More info on these properties, and the schema property reference [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>

  
## <a name="examine-a-node-property-value"></a><span data-ttu-id="e49e4-112">檢查節點屬性值</span><span class="sxs-lookup"><span data-stu-id="e49e4-112">Examine a node property value</span></span>  
  
1.  <span data-ttu-id="e49e4-113">在 [BizTalk 編輯器] 中，開啟包含要檢查之屬性的結構描述，然後選取包含該屬性的節點。</span><span class="sxs-lookup"><span data-stu-id="e49e4-113">In BizTalk Editor, open the schema that contains the property you want to examine, and then select the node that contains that property.</span></span>  
  
2.  <span data-ttu-id="e49e4-114">如有需要，請按 F4，開啟 [[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 屬性] 視窗。</span><span class="sxs-lookup"><span data-stu-id="e49e4-114">If necessary, press F4 to open the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window.</span></span>  
  
3.  <span data-ttu-id="e49e4-115">如有需要，請捲動 [屬性] 視窗捲動，尋找您感興趣的屬性，並注意其值。</span><span class="sxs-lookup"><span data-stu-id="e49e4-115">If necessary, scroll the Properties window to find the property of interest, and note its value.</span></span>  
  
     <span data-ttu-id="e49e4-116">您可使用 [屬性] 視窗上方的按鈕變更屬性排序的方式，可依照字母順序在其類別中排序，或不考慮 (或不顯示) 其類別而依字母順序排序。</span><span class="sxs-lookup"><span data-stu-id="e49e4-116">You can use buttons at the top of the Properties window to change the way that the properties are sorted, either alphabetically within their categories, or alphabetically without regard for (or display of) their categories.</span></span>  
  
## <a name="set-a-node-property-value"></a><span data-ttu-id="e49e4-117">設定節點屬性值</span><span class="sxs-lookup"><span data-stu-id="e49e4-117">Set a node property value</span></span>  
  
1.  <span data-ttu-id="e49e4-118">在 [BizTalk 編輯器] 中，開啟包含要設定之屬性的結構描述，然後選取包含該屬性的節點。</span><span class="sxs-lookup"><span data-stu-id="e49e4-118">In BizTalk Editor, open the schema that contains the property you want to set, and then select the node that contains that property.</span></span>  
  
2.  <span data-ttu-id="e49e4-119">如有需要，請按 F4，開啟 [[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 屬性] 視窗。</span><span class="sxs-lookup"><span data-stu-id="e49e4-119">If necessary, press F4 to open the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window.</span></span>  
  
3.  <span data-ttu-id="e49e4-120">如有需要，請捲動 [屬性] 視窗，尋找您感興趣的屬性。</span><span class="sxs-lookup"><span data-stu-id="e49e4-120">If necessary, scroll the Properties window to find the property of interest.</span></span>  
  
     <span data-ttu-id="e49e4-121">您可使用 [屬性] 視窗上方的按鈕變更屬性排序的方式，可依照字母順序在其類別中排序，或不考慮 (或不顯示) 其類別而依字母順序排序。</span><span class="sxs-lookup"><span data-stu-id="e49e4-121">You can use buttons at the top of the Properties window to change the way that the properties are sorted, either alphabetically within their categories, or alphabetically without regard for (or display of) their categories.</span></span>  
  
4.  <span data-ttu-id="e49e4-122">在值欄位 (在屬性名稱的右邊) 中設定屬性值。</span><span class="sxs-lookup"><span data-stu-id="e49e4-122">Set the value of the property in the value field, which is to the right of the property name.</span></span> <span data-ttu-id="e49e4-123">根據屬性類型的不同，您可以輸入值，或從選取值欄位時所顯示的下拉式清單中選擇值。</span><span class="sxs-lookup"><span data-stu-id="e49e4-123">Depending on the type of the property, you might type a value or choose a value from the drop-down list that is displayed when the value field is selected.</span></span> <span data-ttu-id="e49e4-124">某些屬性同時允許這兩種方式。</span><span class="sxs-lookup"><span data-stu-id="e49e4-124">Some properties allow either operation.</span></span> <span data-ttu-id="e49e4-125">某些屬性會顯示省略符號 (**...**) 按鈕，按下後會開啟對話方塊，在其中更複雜的值，例如，集合、 可以設定。</span><span class="sxs-lookup"><span data-stu-id="e49e4-125">Some properties display an ellipsis (**...**) button that when clicked opens a dialog box in which more complicated values, such as collections, can be set.</span></span>  
  
5.  <span data-ttu-id="e49e4-126">輸入屬性的新值後，請按 ENTER 來完成。</span><span class="sxs-lookup"><span data-stu-id="e49e4-126">If you have typed a new value for the property, finish by pressing ENTER.</span></span>  
  
##  <a name="clear-a-node-property-value"></a><span data-ttu-id="e49e4-127">清除節點屬性值</span><span class="sxs-lookup"><span data-stu-id="e49e4-127">Clear a node property value</span></span>  
  
1.  <span data-ttu-id="e49e4-128">選取包含您感興趣之屬性的節點。</span><span class="sxs-lookup"><span data-stu-id="e49e4-128">Select the node that contains the property of interest.</span></span>  
  
2.  <span data-ttu-id="e49e4-129">在 [屬性] 視窗中，連按兩下您想要清除，屬性值，以滑鼠右鍵按一下，然後按一下屬性值**刪除**。</span><span class="sxs-lookup"><span data-stu-id="e49e4-129">In the Properties window, double-click the property value that you want to clear, right-click the property value, and then click **Delete**.</span></span>  
  
## <a name="restore-a-node-property-to-its-default-value"></a><span data-ttu-id="e49e4-130">節點屬性還原為其預設值</span><span class="sxs-lookup"><span data-stu-id="e49e4-130">Restore a node property to its default value</span></span>  
  
1.  <span data-ttu-id="e49e4-131">選取包含您感興趣之屬性的節點。</span><span class="sxs-lookup"><span data-stu-id="e49e4-131">Select the node that contains the property of interest.</span></span>  
  
2.  <span data-ttu-id="e49e4-132">在 [屬性] 視窗中，以滑鼠右鍵按一下您想要重設為其預設值，然後按一下屬性名稱**重設**。</span><span class="sxs-lookup"><span data-stu-id="e49e4-132">In the Properties window, right-click the property name that you want to reset to its default value, and then click **Reset**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e49e4-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e49e4-133">See Also</span></span>  
 [<span data-ttu-id="e49e4-134">使用現有的節點</span><span class="sxs-lookup"><span data-stu-id="e49e4-134">Working with Existing Nodes</span></span>](../core/working-with-existing-nodes.md)