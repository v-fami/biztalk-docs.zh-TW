---
title: "在結構描述中建立自訂資料型別 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 2.X schemas, creating Z data types [Z objects]
- data types, creating [Z objects]
- Z objects, creating Z data types
ms.assetid: e545c849-d414-4d5d-bb56-d3f9d5238c70
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea38eb106b3554b72885355aaa9aef4928f4fda2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="creating-custom-data-types-in-schemas"></a><span data-ttu-id="434ce-102">在結構描述中建立自訂資料型別</span><span class="sxs-lookup"><span data-stu-id="434ce-102">Creating Custom Data Types in Schemas</span></span>
<span data-ttu-id="434ce-103">您可以建立自訂資料類型中 datatypes_\<*版本*\>.xsd 通用的結構描述。</span><span class="sxs-lookup"><span data-stu-id="434ce-103">You can create a custom data type in the datatypes_\<*version*\>.xsd common schema.</span></span> <span data-ttu-id="434ce-104">您可以根據自訂資料類型，現有的資料類型，基底資料型別或列舉型別資料表中定義。</span><span class="sxs-lookup"><span data-stu-id="434ce-104">You can base a custom data type on an existing data type, a base data type, or on an enumeration defined in a table.</span></span>  
  
### <a name="to-create-a-z-data-type"></a><span data-ttu-id="434ce-105">若要建立 Z 資料類型</span><span class="sxs-lookup"><span data-stu-id="434ce-105">To create a Z data type</span></span>  
  
1.  <span data-ttu-id="434ce-106">在 Visual Studio 的方案總管，開啟 常見的資料類型結構描述檔案 (**datatypes_\<*版本*\>.xsd * *)，然後按一下 **開啟**.</span><span class="sxs-lookup"><span data-stu-id="434ce-106">In Solution Explorer of Visual Studio, open the common data-type schema file (**datatypes_\<*version*\>.xsd**), and then click **Open**.</span></span>  
  
2.  <span data-ttu-id="434ce-107">在 BizTalk 編輯器 中，以滑鼠右鍵按一下**HL7DefinedDataTypes**，指向 **插入結構描述節點**，然後按一下 **子記錄**建立元件的資料類型，或按一下**子項目**建立簡單的資料類型。</span><span class="sxs-lookup"><span data-stu-id="434ce-107">In BizTalk Editor, right-click **HL7DefinedDataTypes**, point to **Insert Schema Node**, and then click **Child Record** to create a component data type, or click **Child Element** to create a simple data type.</span></span>  
  
3.  <span data-ttu-id="434ce-108">三個字元標記開頭為"Z"的已命名的資料類型。</span><span class="sxs-lookup"><span data-stu-id="434ce-108">Name the data type with a three-character tag starting with "Z".</span></span>  
  
4.  <span data-ttu-id="434ce-109">在 [屬性] 窗格中，鍵入您想要的數值**基底資料型別**，**資料型別**，和其他屬性，視需要。</span><span class="sxs-lookup"><span data-stu-id="434ce-109">In the Properties pane, type the values you want for **Base Data Type**, **Data Type**, and other properties, as needed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="434ce-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="434ce-110">See Also</span></span>  
 <span data-ttu-id="434ce-111">[擴充 HL7 2.X Z 物件結構描述](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span><span class="sxs-lookup"><span data-stu-id="434ce-111">[Extending HL7 2.X Schemas with Z Objects](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span></span>  
 <span data-ttu-id="434ce-112">[建立宣告的 Z 區段](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md) </span><span class="sxs-lookup"><span data-stu-id="434ce-112">[Creating Declared Z Segments](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md) </span></span>  
 <span data-ttu-id="434ce-113">[在結構描述中建立自訂的資料表](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="434ce-113">[Creating Custom Tables in Schemas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md) </span></span>  
 <span data-ttu-id="434ce-114">[擴充列舉型別](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="434ce-114">[Extending Enumerations](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md) </span></span>  
 [<span data-ttu-id="434ce-115">處理未宣告的 Z 區段</span><span class="sxs-lookup"><span data-stu-id="434ce-115">Handling Undeclared Z Segments</span></span>](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md)