---
title: 擴充列舉 |Microsoft 文件
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
ms.openlocfilehash: 2abb040d79f0c9312a8761289c0bf6252fef2f3a
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26006239"
---
# <a name="extending-enumerations"></a><span data-ttu-id="ffc5d-102">擴充列舉型別</span><span class="sxs-lookup"><span data-stu-id="ffc5d-102">Extending Enumerations</span></span>
<span data-ttu-id="ffc5d-103">您可以將值加入至 HL7 訊息本文、 通知和訊息內文結構描述中建立可接受的許多欄位、 區段，以及資料類型值的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="ffc5d-103">You can add values to the enumerations that establish accepted values for many fields, segments, and data types in HL7 message body, acknowledgment, and message body schemas.</span></span> <span data-ttu-id="ffc5d-104">這項作業包括變更一組通用 HL7 版本，您使用資料表值結構描述檔中特定資料表中的值 ( **Tablevalues_\<***版本* **\>.xsd**結構描述檔案)。</span><span class="sxs-lookup"><span data-stu-id="ffc5d-104">This involves changing the set of values in a specific table in the common table values schema file for the HL7 version in which you are working (the **Tablevalues_\<***version***\>.xsd** schema file).</span></span>  
  
 <span data-ttu-id="ffc5d-105">您在列舉中加入訊息標頭結構描述的不同方式不同於其他結構描述，例如訊息內文結構描述。</span><span class="sxs-lookup"><span data-stu-id="ffc5d-105">You add to the enumeration in a different way for the message header schema than you do in other schemas, such as the message body schema.</span></span> <span data-ttu-id="ffc5d-106">訊息標頭結構描述中，您必須變更 MSH_25_GLO_DEF.xsd 檔案內的資料表。</span><span class="sxs-lookup"><span data-stu-id="ffc5d-106">For the message header schema, you must change the table within the MSH_25_GLO_DEF.xsd file.</span></span> <span data-ttu-id="ffc5d-107">其他結構描述中，您可以變更資料表值的結構描述檔案中的資料表 (tablevalues_\<版本\>.xsd)。</span><span class="sxs-lookup"><span data-stu-id="ffc5d-107">For other schemas, you change the table in the table values schema file (tablevalues_\<version\>.xsd).</span></span>  
  
### <a name="to-add-an-enumeration-value-to-the-table-values-common-schema-file"></a><span data-ttu-id="ffc5d-108">若要加入的資料表值 common 結構描述檔案列舉值</span><span class="sxs-lookup"><span data-stu-id="ffc5d-108">To add an enumeration value to the table values common schema file</span></span>  
  
1.  <span data-ttu-id="ffc5d-109">您必須先判斷資料表，其中包含您想要加入至列舉。</span><span class="sxs-lookup"><span data-stu-id="ffc5d-109">You first need to determine the table that contains the enumeration that you want to add to.</span></span> <span data-ttu-id="ffc5d-110">在 Visual Studio 的方案總管，開啟包含您想要變更之項目的結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="ffc5d-110">In Solution Explorer of Visual Studio, open the schema file that contains the element that you want to change.</span></span> <span data-ttu-id="ffc5d-111">在 BizTalk 總管 中，按一下您想要加入的值欄位項目。</span><span class="sxs-lookup"><span data-stu-id="ffc5d-111">In BizTalk Explorer, click the field element that you want to add a value for.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ffc5d-112">當您變更資料表值 common 結構描述檔案中的列舉型別時，受影響的所有物件，參考該列舉型別。</span><span class="sxs-lookup"><span data-stu-id="ffc5d-112">When you change an enumeration in the table values common schema file, all objects that reference that enumeration are affected.</span></span>  
  
2.  <span data-ttu-id="ffc5d-113">在**屬性** 窗格中，記下中的資料表名稱**基底資料型別**欄位。</span><span class="sxs-lookup"><span data-stu-id="ffc5d-113">In the **Properties** pane, note the name of the table in the **Base Data Type** field.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ffc5d-114">如果沒有任何資料表中列出**基底資料型別** 欄位中，和**Derived By**屬性未設定為**restricted**，欄位沒有與其相關聯的列舉.</span><span class="sxs-lookup"><span data-stu-id="ffc5d-114">If there is no table listed in **Base Data Type** field, and the **Derived By** property is not set to **Restricted**, then the field does not have an enumeration associated with it.</span></span>  
  
3.  <span data-ttu-id="ffc5d-115">在 方案總管 中，開啟**Tablevalues_\<***版本***\>.xsd**，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="ffc5d-115">In Solution Explorer, open the **Tablevalues_\<***version***\>.xsd**, and then click **Open**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ffc5d-116">您必須為每個您想要變更 HL7 結構描述版本的個別執行此程序。</span><span class="sxs-lookup"><span data-stu-id="ffc5d-116">You must perform this procedure separately for each version of the HL7 schema that you want to change.</span></span>  
  
4.  <span data-ttu-id="ffc5d-117">在 [BizTalk 編輯器] 中，瀏覽至您想要變更，然後再按一下該資料表節點的資料表。</span><span class="sxs-lookup"><span data-stu-id="ffc5d-117">In BizTalk Editor, browse to the table you want to change, and then click that table node.</span></span>  
  
5.  <span data-ttu-id="ffc5d-118">在 屬性 視窗中**限制**區段中，按一下**列舉**，然後按一下省略符號 （...） 按鈕開啟 列舉編輯器。</span><span class="sxs-lookup"><span data-stu-id="ffc5d-118">In the Properties window, in the **Restriction** section, click **Enumeration**, and then click the ellipsis (…) button to open the Enumeration Editor.</span></span>  
  
6.  <span data-ttu-id="ffc5d-119">在 列舉編輯器 中，將新的值加入至現有的值清單，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="ffc5d-119">In the Enumeration Editor, add the new value to the list of existing values, and then click **OK**.</span></span>  
  
### <a name="to-add-an-enumeration-value-to-a-message-header-schema"></a><span data-ttu-id="ffc5d-120">將列舉值新增至訊息標頭結構描述</span><span class="sxs-lookup"><span data-stu-id="ffc5d-120">To add an enumeration value to a message header schema</span></span>  
  
1.  <span data-ttu-id="ffc5d-121">在 方案總管開啟 MSH_25_GLO_DEF 結構描述，然後按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="ffc5d-121">In Solution Explorer, open the MSH_25_GLO_DEF schema, and then click **Open**.</span></span>  
  
2.  <span data-ttu-id="ffc5d-122">以滑鼠右鍵按一下**MSH**節點，指向**插入結構描述節點**，然後按一下 **子欄位項目**。</span><span class="sxs-lookup"><span data-stu-id="ffc5d-122">Right-click the **MSH** node, point to **Insert Schema Node**, and then click **Child Field Element**.</span></span> [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="ffc5d-123">將欄位的節點加入 MSH，稱為**欄位**。</span><span class="sxs-lookup"><span data-stu-id="ffc5d-123"> adds a field node to MSH, called **Field**.</span></span> <span data-ttu-id="ffc5d-124">按一下**ENTER**。</span><span class="sxs-lookup"><span data-stu-id="ffc5d-124">Click **ENTER**.</span></span>  
  
3.  <span data-ttu-id="ffc5d-125">在**屬性**視窗中，按一下 [**資料型別**] 節點，然後從下拉式清單中，選取您要新增的列舉值的資料表。</span><span class="sxs-lookup"><span data-stu-id="ffc5d-125">In the **Properties** window, click the **Data Type** node, then from the drop-down list, select the table to which you want to add the enumeration value.</span></span>  
  
4.  <span data-ttu-id="ffc5d-126">在**屬性**視窗，請在**限制**區段中，按一下**列舉**，然後按一下省略符號 （...） 按鈕開啟 列舉編輯器。</span><span class="sxs-lookup"><span data-stu-id="ffc5d-126">In the **Properties** window, in the **Restriction** section, click **Enumeration**, and then click the ellipsis (…) button to open the Enumeration Editor.</span></span>  
  
5.  <span data-ttu-id="ffc5d-127">在 列舉編輯器 中，將新的值加入至現有的值清單，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="ffc5d-127">In the Enumeration Editor, add the new value to the list of existing values, and then click **OK**.</span></span>  
  
     <span data-ttu-id="ffc5d-128">當您將值加入至列舉型別之任何節點，例如**欄位**節點中，新增全域使用該資料表的所有物件的值。</span><span class="sxs-lookup"><span data-stu-id="ffc5d-128">When you add a value to the enumeration for any node, such as the **Field** node, you add that value globally for all objects that use that table.</span></span> <span data-ttu-id="ffc5d-129">如此一來，您現在可以刪除**欄位**節點，然後此值仍然會出現資料表。</span><span class="sxs-lookup"><span data-stu-id="ffc5d-129">As a result, you can now delete the **Field** node, and the value will still be present for the table.</span></span> <span data-ttu-id="ffc5d-130">您可以驗證，捲動到資料表，右窗格 BizTalk 編輯器中，確認您所加入的值存在。</span><span class="sxs-lookup"><span data-stu-id="ffc5d-130">You can verify this by scrolling in the right pane of BizTalk Editor to the table, and verifying that the value that you added is present.</span></span>  
  
6.  <span data-ttu-id="ffc5d-131">以滑鼠右鍵按一下**欄位**節點在 BizTalk 編輯器 中，按一下**刪除**，然後按一下 **是**。</span><span class="sxs-lookup"><span data-stu-id="ffc5d-131">Right-click the **Field** node in BizTalk Editor, click **Delete**, and then click **Yes**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffc5d-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="ffc5d-132">See Also</span></span>  
 <span data-ttu-id="ffc5d-133">[資料表值的通用結構描述](../../adapters-and-accelerators/accelerator-hl7/table-values-common-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="ffc5d-133">[Table Values Common Schemas](../../adapters-and-accelerators/accelerator-hl7/table-values-common-schemas.md) </span></span>  
 <span data-ttu-id="ffc5d-134">[擴充 HL7 2.X Z 物件結構描述](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span><span class="sxs-lookup"><span data-stu-id="ffc5d-134">[Extending HL7 2.X Schemas with Z Objects](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span></span>  
 <span data-ttu-id="ffc5d-135">[建立宣告的 Z 區段](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md) </span><span class="sxs-lookup"><span data-stu-id="ffc5d-135">[Creating Declared Z Segments](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md) </span></span>  
 <span data-ttu-id="ffc5d-136">[在結構描述中建立自訂資料型別](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="ffc5d-136">[Creating Custom Data Types in Schemas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md) </span></span>  
 <span data-ttu-id="ffc5d-137">[在結構描述中建立自訂的資料表](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="ffc5d-137">[Creating Custom Tables in Schemas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md) </span></span>  
 [<span data-ttu-id="ffc5d-138">處理未宣告的 Z 區段</span><span class="sxs-lookup"><span data-stu-id="ffc5d-138">Handling Undeclared Z Segments</span></span>](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md)