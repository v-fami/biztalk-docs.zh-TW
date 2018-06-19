---
title: 如何建立另一個節點或類型參考 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c60be9ad-01a9-40e7-b43b-8c3d09bbb32f
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 643f39b9a42e2566f77371096d7305f56e11a328
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22250350"
---
# <a name="create-references-to-another-node-or-type"></a><span data-ttu-id="202d5-102">建立另一個節點或類型的參考</span><span class="sxs-lookup"><span data-stu-id="202d5-102">Create References to Another Node or Type</span></span>
<span data-ttu-id="202d5-103">您可以使用全域節點建立可重複使用的資料型別 (結構片段)，以在適合該結構的結構描述中使用。</span><span class="sxs-lookup"><span data-stu-id="202d5-103">You can use global nodes to create reusable data types—fragments of structure—that you can use throughout the schema wherever that structure is appropriate.</span></span> <span data-ttu-id="202d5-104">您只能使用節點的直接子系**結構描述**節點建立全域型別。</span><span class="sxs-lookup"><span data-stu-id="202d5-104">You can only use nodes that are direct children of the **Schema** node to create global types.</span></span>  
  
 <span data-ttu-id="202d5-105">您也可以建立使用資料類型的節點不是直接子系的循環參考**結構描述**節點。</span><span class="sxs-lookup"><span data-stu-id="202d5-105">You can also create cyclical references using the data types of nodes that are not direct descendants of the **Schema** node.</span></span> <span data-ttu-id="202d5-106">這在結構描述中代表遞迴結構時很有用。</span><span class="sxs-lookup"><span data-stu-id="202d5-106">This is useful for representing recursive structures in schemas.</span></span>  
  
 <span data-ttu-id="202d5-107">本主題提供各種全域節點類型及如何參照它們來加以使用的逐步說明。</span><span class="sxs-lookup"><span data-stu-id="202d5-107">This topic provides step-by-step instructions for various types of global nodes and how to refer to them to use them.</span></span>  
  
 <span data-ttu-id="202d5-108">**建立全域宣告**</span><span class="sxs-lookup"><span data-stu-id="202d5-108">**Creating Global Declarations**</span></span>  
  
 <span data-ttu-id="202d5-109">您可以使用記錄、欄位或屬性，建立全域類型。</span><span class="sxs-lookup"><span data-stu-id="202d5-109">You can create global types using records, fields or attributes.</span></span> <span data-ttu-id="202d5-110">從記錄建立的全域類型只能用在記錄，從欄位建立的類型只能用在欄位，而從屬性建立的類型只能用在屬性。</span><span class="sxs-lookup"><span data-stu-id="202d5-110">Global types created from records may only be used in records, types created from fields only in fields, attribute types only in attributes.</span></span> <span data-ttu-id="202d5-111">下列程序說明如何定義和使用全域宣告。</span><span class="sxs-lookup"><span data-stu-id="202d5-111">The following procedures describe how to define and use global declarations.</span></span>  
  
## <a name="create-a-global-declaration-from-a-node"></a><span data-ttu-id="202d5-112">從節點建立全域宣告</span><span class="sxs-lookup"><span data-stu-id="202d5-112">Create a global declaration from a node</span></span>  
  
1.  <span data-ttu-id="202d5-113">選取**記錄**，**欄位屬性**，或**欄位項目**節點您想要變更為全域的型別。</span><span class="sxs-lookup"><span data-stu-id="202d5-113">Select the **Record** , **Field Attribute**,or **Field Element** node whose type you want to make globally available.</span></span>  
  
2.  <span data-ttu-id="202d5-114">在**屬性** 視窗中，輸入的名稱在**資料結構型別**清單，將使用做為複雜類型的全域名稱，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="202d5-114">In the **Properties** window, type a name in the **Data Structure Type** list that will be used as the global name for the complex type, and then press ENTER.</span></span>  
  
## <a name="create-a-globally-defined-sequence-group-node-choice-group-node-or-all-group-node"></a><span data-ttu-id="202d5-115">建立全域定義的 Sequence 群組節點、 Choice 群組 節點或 All 群組 節點</span><span class="sxs-lookup"><span data-stu-id="202d5-115">Create a globally defined Sequence Group node, Choice Group node, or All Group node</span></span>  
  
1.  <span data-ttu-id="202d5-116">選取**記錄**要插入全域定義的群組節點的節點。</span><span class="sxs-lookup"><span data-stu-id="202d5-116">Select the **Record** node into which you want to insert the globally defined group node.</span></span>  
  
2.  <span data-ttu-id="202d5-117">在**BizTalk**功能表上，指向**插入結構描述節點**，然後按一下  **Sequence 群組**， **Choice 群組**，或**所有群組**視情況。</span><span class="sxs-lookup"><span data-stu-id="202d5-117">On the **BizTalk** menu, point to **Insert Schema Node**, and then click **Sequence Group**, **Choice Group**, or **All Group**, as appropriate.</span></span>  
  
3.  <span data-ttu-id="202d5-118">在新插入的群組中建立結構。</span><span class="sxs-lookup"><span data-stu-id="202d5-118">Create a structure in the newly inserted group.</span></span> <span data-ttu-id="202d5-119">例如，插入**記錄**或**欄位項目**節點，以表示群組節點內的資料結構。</span><span class="sxs-lookup"><span data-stu-id="202d5-119">For example, insert **Record** or **Field Element** nodes to express the structure of the data within the group node.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="202d5-120">Sequence 群組**Choice 群組**，和**All 群組**節點只能包含節點對應至 XML 項目，因此不能包含**欄位屬性**節點。</span><span class="sxs-lookup"><span data-stu-id="202d5-120">Sequence Group, **Choice Group**, and **All Group** nodes can only contain nodes that correspond to XML elements and therefore cannot contain **Field Attribute** nodes.</span></span>  
  
4.  <span data-ttu-id="202d5-121">選取在步驟 2 插入的群組節點</span><span class="sxs-lookup"><span data-stu-id="202d5-121">Select the group node inserted in step 2.</span></span>  
  
5.  <span data-ttu-id="202d5-122">在 屬性 視窗中，按一下**群組參考**值 欄位中輸入名稱，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="202d5-122">In the Properties window, click **Group Reference**, type a name into the value field, and then press ENTER.</span></span>  
  
     <span data-ttu-id="202d5-123">中提供的名稱**群組參考**屬性，就能全域定義群組節點之後, 您可以將其他群組節點與此全域定義類型 （結構）。</span><span class="sxs-lookup"><span data-stu-id="202d5-123">By providing a name in the **Group Reference** property, you have globally defined group node, after which you can associate other group nodes with this globally defined type (structure).</span></span>  
  
## <a name="create-a-globally-defined-attribute-group-node"></a><span data-ttu-id="202d5-124">建立全域定義的屬性群組節點</span><span class="sxs-lookup"><span data-stu-id="202d5-124">Create a globally defined Attribute Group node</span></span>  
  
1.  <span data-ttu-id="202d5-125">選取**記錄**節點要插入全域定義**屬性群組**節點。</span><span class="sxs-lookup"><span data-stu-id="202d5-125">Select the **Record** node into which you want to insert the globally defined **Attribute Group** node.</span></span>  
  
2.  <span data-ttu-id="202d5-126">在**BizTalk**功能表上，指向**插入結構描述節點**，然後按一下 **屬性群組**。</span><span class="sxs-lookup"><span data-stu-id="202d5-126">On the **BizTalk** menu, point to **Insert Schema Node**, and then click **Attribute Group**.</span></span>  
  
     <span data-ttu-id="202d5-127">這樣會加入**屬性群組**在所選節點之子節點結尾處的節點**記錄**節點。</span><span class="sxs-lookup"><span data-stu-id="202d5-127">This adds an **Attribute Group** node to the end of the child nodes in the selected **Record** node.</span></span>  
  
3.  <span data-ttu-id="202d5-128">新增適當**欄位屬性**或**屬性群組**節點，以您**屬性群組**。</span><span class="sxs-lookup"><span data-stu-id="202d5-128">Add the appropriate **Field Attribute** or **Attribute Group** nodes to your **Attribute Group**.</span></span>  
  
4.  <span data-ttu-id="202d5-129">（選擇性） 如果您想要重新命名**屬性群組**節點中，選取**屬性群組**節點，然後變更其**群組參考**您所選擇的新名稱的屬性。</span><span class="sxs-lookup"><span data-stu-id="202d5-129">Optionally, if you want to rename the **Attribute Group** node, select the **Attribute Group** node and change its **Group Reference** property to a new name of your choosing.</span></span>  
  
     <span data-ttu-id="202d5-130">屬性群組一律為全域性，且在使用時會從其位置參照。</span><span class="sxs-lookup"><span data-stu-id="202d5-130">Attribute groups are always global and referenced from their point of use.</span></span>  
  
## <a name="use-a-type-or-group-that-has-been-globally-defined"></a><span data-ttu-id="202d5-131">使用類型或已全域定義的群組</span><span class="sxs-lookup"><span data-stu-id="202d5-131">Use a type or group that has been globally defined</span></span>  
  
1.  <span data-ttu-id="202d5-132">選取要使用全域定義類型的節點。</span><span class="sxs-lookup"><span data-stu-id="202d5-132">Select the node for which you want to use a globally defined type.</span></span>  
  
2.  <span data-ttu-id="202d5-133">在 [屬性] 視窗中選取的全域定義的類型從下拉式清單中，為**資料結構型別**屬性 (**記錄**節點)，**資料型別**屬性 (**欄位項目**和**欄位屬性**節點)，或**群組參考**(**Sequence 群組**， **Choice 群組**， **all 群組**，和**屬性群組**節點)。</span><span class="sxs-lookup"><span data-stu-id="202d5-133">In the Properties window, select the globally defined type from the drop-down list for the **Data Structure Type** property (**Record** nodes), **Data Type** property (**Field Element** and **Field Attribute** nodes), or **Group Reference** (**Sequence Group**, **Choice Group**, **All Group**, and **Attribute Group** nodes).</span></span> <span data-ttu-id="202d5-134">這些屬性的詳細[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="202d5-134">More details on these properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
    > [!NOTE]
    >  <span data-ttu-id="202d5-135">您可以在全域定義的類型或群組出現的任何結構描述位置，對其進行後續的變更。</span><span class="sxs-lookup"><span data-stu-id="202d5-135">Subsequent changes to the globally defined type or group can be made in any of the schema locations in which it appears.</span></span> <span data-ttu-id="202d5-136">在這些位置的單一任意位置中進行變更時，會在所有這類位置上套用變更。</span><span class="sxs-lookup"><span data-stu-id="202d5-136">These changes will be applied in all such locations as you make them in the single, arbitrary location.</span></span>  
  
 <span data-ttu-id="202d5-137">建立全域宣告之後，您無法在單一步驟中刪除它。</span><span class="sxs-lookup"><span data-stu-id="202d5-137">After you have created a global declaration, you cannot delete it in a single step.</span></span> <span data-ttu-id="202d5-138">不過，您可以藉由刪除它**清除全域資料型別**儲存結構描述時，使用下列程序 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="202d5-138">However, you can delete it by using the **Cleanup Global DataTypes** dialog box when the schema is saved, using the following procedure.</span></span>  
  
## <a name="delete-a-global-declaration"></a><span data-ttu-id="202d5-139">刪除全域宣告</span><span class="sxs-lookup"><span data-stu-id="202d5-139">Delete a global declaration</span></span>  
  
1.  <span data-ttu-id="202d5-140">刪除使用此全域類型或群組的所有節點，或指定不同的類型或群組供所有這些節點使用，或將兩種方法的組合使用。</span><span class="sxs-lookup"><span data-stu-id="202d5-140">Delete all of the nodes where this global type or group is used, or specify a different type or group to be used in all of those nodes, or some combination thereof.</span></span> <span data-ttu-id="202d5-141">如需刪除節點的逐步指示，請參閱[刪除節點](../core/how-to-delete-nodes.md)。</span><span class="sxs-lookup"><span data-stu-id="202d5-141">For step-by-step instructions for deleting a node, see [Deleting Nodes](../core/how-to-delete-nodes.md).</span></span>  
  
2.  <span data-ttu-id="202d5-142">在儲存您的規格時**清除全域資料型別** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="202d5-142">Upon saving your specification, the **Cleanup Global DataTypes** dialog box appears.</span></span> <span data-ttu-id="202d5-143">選取您想要完全刪除您的規格，然後按一下 全域宣告**確定**。</span><span class="sxs-lookup"><span data-stu-id="202d5-143">Select the global declaration you want to completely delete from your specification, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="202d5-144">**清除全域資料型別**每次您未使用的資料類型儲存結構描述 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="202d5-144">The **Cleanup Global DataTypes** dialog box appears every time you save a schema with unused data types.</span></span> <span data-ttu-id="202d5-145">若未出現此對話方塊，則表示結構描述中的其他位置已使用所有的資料型別，或是結構描述自開啟後未曾修改過 (在後者的情況中，它可能仍包含先前保留的未使用資料型別)。</span><span class="sxs-lookup"><span data-stu-id="202d5-145">If this dialog box does not appear, either all data types are used somewhere in the schema or the schema has not been modified since it was opened (in the latter case, it might still contain unused data types that were previously retained.</span></span>  
  
## <a name="create-cyclical-references-to-another-node"></a><span data-ttu-id="202d5-146">建立另一個節點的循環參考</span><span class="sxs-lookup"><span data-stu-id="202d5-146">Create Cyclical References to Another Node</span></span>  
 <span data-ttu-id="202d5-147">您可以建立節點的循環參考來代表遞迴的結構描述項目。</span><span class="sxs-lookup"><span data-stu-id="202d5-147">You can create cyclical references to a node to represent recursive schema elements.</span></span> <span data-ttu-id="202d5-148">若要這麼做，您可以建立一個類型由封閉式記錄所定義的節點。</span><span class="sxs-lookup"><span data-stu-id="202d5-148">You do this by creating a node whose type is defined by an enclosing record.</span></span> <span data-ttu-id="202d5-149">例如，假設有一個執行個體訊息是包裝在具有相同結構的任意數目信封中。</span><span class="sxs-lookup"><span data-stu-id="202d5-149">For example, consider an instance message that is wrapped in an arbitrary number of envelopes having the same structure.</span></span> <span data-ttu-id="202d5-150">使用循環參考時，您可以建立一個定義此種執行個體訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="202d5-150">Using cyclical references, you can create a schema that defines such instance messages.</span></span>  
  
### <a name="create-a-cyclical-reference"></a><span data-ttu-id="202d5-151">建立循環參考</span><span class="sxs-lookup"><span data-stu-id="202d5-151">Create a cyclical reference</span></span>  
  
1.  <span data-ttu-id="202d5-152">選取**記錄**您要建立遞迴參考節點。</span><span class="sxs-lookup"><span data-stu-id="202d5-152">Select a **Record** node for which you want to create a recursive reference.</span></span> <span data-ttu-id="202d5-153">這是代表遞迴結構頂端的節點。</span><span class="sxs-lookup"><span data-stu-id="202d5-153">This is the node representing the top of the recursive structure.</span></span>  
  
2.  <span data-ttu-id="202d5-154">在 [屬性] 視窗中，確認**資料結構型別**的值。</span><span class="sxs-lookup"><span data-stu-id="202d5-154">In the Properties window, verify that the **Data Structure Type** has a value.</span></span>  
  
     <span data-ttu-id="202d5-155">確認**記錄**具名節點都有與其相關聯的類型是必要的因為遞迴結構時會定義包含本身的類型。</span><span class="sxs-lookup"><span data-stu-id="202d5-155">Verifying that the **Record** node has a named type associated with it is necessary because recursive structures are defined when a type contains itself.</span></span> <span data-ttu-id="202d5-156">只有透過巢狀方式使用具名的全域類型，類型才能包含其本身。</span><span class="sxs-lookup"><span data-stu-id="202d5-156">Types can only contain themselves through nested use of named global types.</span></span>  
  
3.  <span data-ttu-id="202d5-157">選取子**記錄**節點或插入子**記錄**節點。</span><span class="sxs-lookup"><span data-stu-id="202d5-157">Select a child **Record** node or insert a child **Record** node.</span></span>  
  
4.  <span data-ttu-id="202d5-158">子系**記錄**節點，在 [屬性] 視窗中**資料結構型別**清單中，選取在步驟 2 中識別的資料結構。</span><span class="sxs-lookup"><span data-stu-id="202d5-158">For the child **Record** node, in the Properties window, in the **Data Structure Type** list, select the data structure identified in step 2.</span></span>  
  
> [!IMPORTANT]
>  - <span data-ttu-id="202d5-159">**Min Occurs**重複節點的屬性必須設定為零 (**0**)。</span><span class="sxs-lookup"><span data-stu-id="202d5-159">The **Min Occurs** property for the repeating node must be set to zero (**0**).</span></span> <span data-ttu-id="202d5-160">設為一 (**1**) 會造成無限迴圈。</span><span class="sxs-lookup"><span data-stu-id="202d5-160">Setting it to one (**1**) causes an infinite loop.</span></span>  
>
>  - <span data-ttu-id="202d5-161">匯入包含遞迴項目的結構描述時，「BizTalk 編輯器」並不會自動檢查來確認遞迴項目是否有效。</span><span class="sxs-lookup"><span data-stu-id="202d5-161">If you import a schema that contains a recursive element, BizTalk Editor does not automatically check to ensure that the recursive element is valid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="202d5-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="202d5-162">See Also</span></span>  
 [<span data-ttu-id="202d5-163">管理結構描述中的節點</span><span class="sxs-lookup"><span data-stu-id="202d5-163">Managing the Nodes Within a Schema</span></span>](../core/managing-the-nodes-within-a-schema.md)