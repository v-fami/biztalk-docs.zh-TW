---
title: "建立自訂的資料表結構描述中 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, Z tables [Z objects]
- Z objects, creating Z tables
- 2.X schemas, creating Z tables
ms.assetid: d6ab8ac9-a835-4ec0-9ddd-76ff267a3cbd
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7c3ce69e60517f90af4031bf76691a551afcbe2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-custom-tables-in-schemas"></a><span data-ttu-id="a9abc-102">在結構描述中建立自訂的資料表</span><span class="sxs-lookup"><span data-stu-id="a9abc-102">Creating Custom Tables in Schemas</span></span>
<span data-ttu-id="a9abc-103">您可以建立自訂的資料表中 tablevalues_\<*版本*>.xsd 通用的結構描述。</span><span class="sxs-lookup"><span data-stu-id="a9abc-103">You can create a custom table in the tablevalues_\<*version*>.xsd common schema.</span></span> <span data-ttu-id="a9abc-104">您可以根據自訂資料表或資料表中定義的列舉型別上現有的資料類型，基底資料型別。</span><span class="sxs-lookup"><span data-stu-id="a9abc-104">You can base a custom table on an existing data type, a base data type, or on an enumeration defined in a table.</span></span>  
  
### <a name="to-create-a-z-table"></a><span data-ttu-id="a9abc-105">若要建立 Z 資料表</span><span class="sxs-lookup"><span data-stu-id="a9abc-105">To create a Z table</span></span>  
  
1.  <span data-ttu-id="a9abc-106">在 [方案總管] 中，開啟通用的資料類型結構描述檔案 **tablevalues_\<*版本*>.xsd * *，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="a9abc-106">In Solution Explorer, open the common data-type schema file **tablevalues_\<*version*>.xsd**, and then click **Open**.</span></span>  
  
2.  <span data-ttu-id="a9abc-107">在 BizTalk 編輯器 中，以滑鼠右鍵按一下**HL7DefinedTables**，指向 **插入結構描述節點**，然後按一下 **子欄位項目**。</span><span class="sxs-lookup"><span data-stu-id="a9abc-107">In BizTalk Editor, right-click **HL7DefinedTables**, point to **Insert Schema Node**, and then click **Child Field Element**.</span></span>  
  
3.  <span data-ttu-id="a9abc-108">開頭為字母"Z"標記的已命名資料表。</span><span class="sxs-lookup"><span data-stu-id="a9abc-108">Name the table with a tag starting with the letter "Z".</span></span>  
  
4.  <span data-ttu-id="a9abc-109">視需要請在 [屬性] 窗格中，輸入您想要用於特定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="a9abc-109">In the Properties pane, type the values you want for specific properties, as needed.</span></span>  
  
5.  <span data-ttu-id="a9abc-110">列舉型別與表格中的 屬性 窗格中，設定**Derived By**至**限制**，按一下 **列舉**，按一下省略符號 （...） 按鈕，如**列舉型別**，然後輸入您想要包含在 列舉編輯器 中列舉的值。</span><span class="sxs-lookup"><span data-stu-id="a9abc-110">To associate an enumeration with the table, in the Properties pane, set **Derived By** to **Restriction**, click **Enumeration**, click the ellipsis (…) button for **Enumeration**, and then type the values that you want the enumeration to contain in the Enumeration Editor.</span></span> <span data-ttu-id="a9abc-111">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="a9abc-111">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9abc-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9abc-112">See Also</span></span>  
 <span data-ttu-id="a9abc-113">[擴充 HL7 2.X Z 物件結構描述](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span><span class="sxs-lookup"><span data-stu-id="a9abc-113">[Extending HL7 2.X Schemas with Z Objects](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span></span>  
 <span data-ttu-id="a9abc-114">[建立宣告的 Z 區段](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md) </span><span class="sxs-lookup"><span data-stu-id="a9abc-114">[Creating Declared Z Segments](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md) </span></span>  
 <span data-ttu-id="a9abc-115">[在結構描述中建立自訂資料型別](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="a9abc-115">[Creating Custom Data Types in Schemas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md) </span></span>  
 <span data-ttu-id="a9abc-116">[擴充列舉型別](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="a9abc-116">[Extending Enumerations](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md) </span></span>  
 [<span data-ttu-id="a9abc-117">處理未宣告的 Z 區段</span><span class="sxs-lookup"><span data-stu-id="a9abc-117">Handling Undeclared Z Segments</span></span>](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md)