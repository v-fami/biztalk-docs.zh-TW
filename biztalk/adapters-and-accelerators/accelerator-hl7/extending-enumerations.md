---
title: 擴充列舉 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- enumeration values
- 2.X schemas, enumeration values
ms.assetid: 043def35-b644-4502-a2e2-cc1a5fc0328a
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc5b91513833b76ba7dc3697f9eee409bf9752bf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987847"
---
# <a name="extending-enumerations"></a><span data-ttu-id="7f993-102">擴充列舉</span><span class="sxs-lookup"><span data-stu-id="7f993-102">Extending Enumerations</span></span>
<span data-ttu-id="7f993-103">您可以加入 HL7 訊息內文、 通知和訊息內文結構描述中建立可接受的許多欄位，區段和資料類型值的列舉值。</span><span class="sxs-lookup"><span data-stu-id="7f993-103">You can add values to the enumerations that establish accepted values for many fields, segments, and data types in HL7 message body, acknowledgment, and message body schemas.</span></span> <span data-ttu-id="7f993-104">這包括變更一組常見 HL7 版本，您使用資料表值結構描述檔案中的特定資料表的值 ( **Tablevalues_\<**<em>版本</em> **\>.xsd**結構描述檔案)。</span><span class="sxs-lookup"><span data-stu-id="7f993-104">This involves changing the set of values in a specific table in the common table values schema file for the HL7 version in which you are working (the **Tablevalues_\<**<em>version</em>**\>.xsd** schema file).</span></span>  
  
 <span data-ttu-id="7f993-105">您加入至列舉的訊息標頭結構描述不同的方式不同於其他結構描述，例如訊息內文結構描述。</span><span class="sxs-lookup"><span data-stu-id="7f993-105">You add to the enumeration in a different way for the message header schema than you do in other schemas, such as the message body schema.</span></span> <span data-ttu-id="7f993-106">針對訊息標頭結構描述中，您必須變更 MSH_25_GLO_DEF.xsd 檔案內的資料表。</span><span class="sxs-lookup"><span data-stu-id="7f993-106">For the message header schema, you must change the table within the MSH_25_GLO_DEF.xsd file.</span></span> <span data-ttu-id="7f993-107">對於其他結構描述中，您可以變更資料表值的結構描述檔案中的資料表 (tablevalues_\<版本\>.xsd)。</span><span class="sxs-lookup"><span data-stu-id="7f993-107">For other schemas, you change the table in the table values schema file (tablevalues_\<version\>.xsd).</span></span>  
  
### <a name="to-add-an-enumeration-value-to-the-table-values-common-schema-file"></a><span data-ttu-id="7f993-108">將列舉值新增至資料表值 common 結構描述檔案</span><span class="sxs-lookup"><span data-stu-id="7f993-108">To add an enumeration value to the table values common schema file</span></span>  
  
1. <span data-ttu-id="7f993-109">您首先要決定資料表，其中包含您想要加入的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="7f993-109">You first need to determine the table that contains the enumeration that you want to add to.</span></span> <span data-ttu-id="7f993-110">在 Visual Studio 的方案總管中開啟結構描述檔案，其中包含您想要變更的項目。</span><span class="sxs-lookup"><span data-stu-id="7f993-110">In Solution Explorer of Visual Studio, open the schema file that contains the element that you want to change.</span></span> <span data-ttu-id="7f993-111">在 [BizTalk 總管] 中，按一下您想要新增的值欄位項目。</span><span class="sxs-lookup"><span data-stu-id="7f993-111">In BizTalk Explorer, click the field element that you want to add a value for.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="7f993-112">當您變更資料表值 common 結構描述檔案中的列舉型別時，會影響所有參考該列舉的物件。</span><span class="sxs-lookup"><span data-stu-id="7f993-112">When you change an enumeration in the table values common schema file, all objects that reference that enumeration are affected.</span></span>  
  
2. <span data-ttu-id="7f993-113">在 **屬性**窗格中，記下的資料表中的名稱**Base Data Type**欄位。</span><span class="sxs-lookup"><span data-stu-id="7f993-113">In the **Properties** pane, note the name of the table in the **Base Data Type** field.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="7f993-114">中如果沒有列出任何資料表**基底資料型別** 欄位中，而**Derived By**屬性未設定為**Restricted**，沒有與其相關聯的列舉型別欄位.</span><span class="sxs-lookup"><span data-stu-id="7f993-114">If there is no table listed in **Base Data Type** field, and the **Derived By** property is not set to **Restricted**, then the field does not have an enumeration associated with it.</span></span>  
  
3. <span data-ttu-id="7f993-115">在 [方案總管] 中，開啟**Tablevalues_\<**<em>版本</em>**\>.xsd**，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="7f993-115">In Solution Explorer, open the **Tablevalues_\<**<em>version</em>**\>.xsd**, and then click **Open**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="7f993-116">您必須為每個您想要變更的 HL7 結構描述版本，個別執行此程序。</span><span class="sxs-lookup"><span data-stu-id="7f993-116">You must perform this procedure separately for each version of the HL7 schema that you want to change.</span></span>  
  
4. <span data-ttu-id="7f993-117">在 「 BizTalk 編輯器 」 中，瀏覽至您想要變更此項目，然後再按一下該資料表節點的資料表。</span><span class="sxs-lookup"><span data-stu-id="7f993-117">In BizTalk Editor, browse to the table you want to change, and then click that table node.</span></span>  
  
5. <span data-ttu-id="7f993-118">在 屬性 視窗中，在**限制**區段中，按一下**列舉**，然後按一下省略符號 （...） 按鈕，以開啟 列舉編輯器。</span><span class="sxs-lookup"><span data-stu-id="7f993-118">In the Properties window, in the **Restriction** section, click **Enumeration**, and then click the ellipsis (…) button to open the Enumeration Editor.</span></span>  
  
6. <span data-ttu-id="7f993-119">在 列舉編輯器 中，將新的值新增到現有的值清單，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="7f993-119">In the Enumeration Editor, add the new value to the list of existing values, and then click **OK**.</span></span>  
  
### <a name="to-add-an-enumeration-value-to-a-message-header-schema"></a><span data-ttu-id="7f993-120">將列舉值新增至訊息標頭結構描述</span><span class="sxs-lookup"><span data-stu-id="7f993-120">To add an enumeration value to a message header schema</span></span>  
  
1. <span data-ttu-id="7f993-121">在 [方案總管] 中，開啟 MSH_25_GLO_DEF 結構描述，然後**開啟**。</span><span class="sxs-lookup"><span data-stu-id="7f993-121">In Solution Explorer, open the MSH_25_GLO_DEF schema, and then click **Open**.</span></span>  
  
2. <span data-ttu-id="7f993-122">以滑鼠右鍵按一下**MSH**節點，指向**插入結構描述節點**，然後按一下**子欄位項目**。</span><span class="sxs-lookup"><span data-stu-id="7f993-122">Right-click the **MSH** node, point to **Insert Schema Node**, and then click **Child Field Element**.</span></span> [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="7f993-123"> 將 [欄位] 節點新增至 MSH，稱為**欄位**。</span><span class="sxs-lookup"><span data-stu-id="7f993-123"> adds a field node to MSH, called **Field**.</span></span> <span data-ttu-id="7f993-124">按一下  **ENTER**。</span><span class="sxs-lookup"><span data-stu-id="7f993-124">Click **ENTER**.</span></span>  
  
3. <span data-ttu-id="7f993-125">在 **屬性** 視窗中，按一下**資料型別** 節點，然後從下拉式清單中，選取您要加入的列舉值的資料表。</span><span class="sxs-lookup"><span data-stu-id="7f993-125">In the **Properties** window, click the **Data Type** node, then from the drop-down list, select the table to which you want to add the enumeration value.</span></span>  
  
4. <span data-ttu-id="7f993-126">在**屬性**] 視窗，請在**限制**區段中，按一下**列舉型別**，然後按一下省略符號 （...） 按鈕，以開啟 [列舉編輯器。</span><span class="sxs-lookup"><span data-stu-id="7f993-126">In the **Properties** window, in the **Restriction** section, click **Enumeration**, and then click the ellipsis (…) button to open the Enumeration Editor.</span></span>  
  
5. <span data-ttu-id="7f993-127">在 列舉編輯器 中，將新的值新增到現有的值清單，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="7f993-127">In the Enumeration Editor, add the new value to the list of existing values, and then click **OK**.</span></span>  
  
    <span data-ttu-id="7f993-128">當您將值加入對於任何節點中，列舉這類**欄位**節點中，新增使用該資料表的所有物件的全域值。</span><span class="sxs-lookup"><span data-stu-id="7f993-128">When you add a value to the enumeration for any node, such as the **Field** node, you add that value globally for all objects that use that table.</span></span> <span data-ttu-id="7f993-129">如此一來，您現在可以刪除**欄位** 節點和值仍然會出現資料表。</span><span class="sxs-lookup"><span data-stu-id="7f993-129">As a result, you can now delete the **Field** node, and the value will still be present for the table.</span></span> <span data-ttu-id="7f993-130">您可以驗證，請捲動在右窗格在 「 BizTalk 編輯器 」 的資料表，並驗證您所加入的值存在。</span><span class="sxs-lookup"><span data-stu-id="7f993-130">You can verify this by scrolling in the right pane of BizTalk Editor to the table, and verifying that the value that you added is present.</span></span>  
  
6. <span data-ttu-id="7f993-131">以滑鼠右鍵按一下**欄位**節點在 「 BizTalk 編輯器 」 中，按一下**刪除**，然後按一下**是**。</span><span class="sxs-lookup"><span data-stu-id="7f993-131">Right-click the **Field** node in BizTalk Editor, click **Delete**, and then click **Yes**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f993-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f993-132">See Also</span></span>  
 <span data-ttu-id="7f993-133">[資料表值的通用結構描述](../../adapters-and-accelerators/accelerator-hl7/table-values-common-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="7f993-133">[Table Values Common Schemas](../../adapters-and-accelerators/accelerator-hl7/table-values-common-schemas.md) </span></span>  
 <span data-ttu-id="7f993-134">[使用 Z 物件擴充 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span><span class="sxs-lookup"><span data-stu-id="7f993-134">[Extending HL7 2.X Schemas with Z Objects](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span></span>  
 <span data-ttu-id="7f993-135">[建立宣告的 Z 區段](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md) </span><span class="sxs-lookup"><span data-stu-id="7f993-135">[Creating Declared Z Segments](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md) </span></span>  
 <span data-ttu-id="7f993-136">[結構描述中建立自訂資料類型](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="7f993-136">[Creating Custom Data Types in Schemas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md) </span></span>  
 <span data-ttu-id="7f993-137">[結構描述中建立自訂的資料表](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="7f993-137">[Creating Custom Tables in Schemas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md) </span></span>  
 [<span data-ttu-id="7f993-138">處理未宣告的 Z 區段</span><span class="sxs-lookup"><span data-stu-id="7f993-138">Handling Undeclared Z Segments</span></span>](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md)