---
title: 建立宣告的 Z 區段 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Z objects, creating segments
- segments, creating Z segments [Z objects]
- Z segments, creating
- creating, Z segments [Z objects]
ms.assetid: afd1b7b7-089e-4c6a-a063-e708431bb888
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dae9148547f527d29238b6080cd499be8da7b7e6
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
ms.locfileid: "22204742"
---
# <a name="creating-declared-z-segments"></a><span data-ttu-id="7683a-102">建立宣告的 Z 區段</span><span class="sxs-lookup"><span data-stu-id="7683a-102">Creating Declared Z Segments</span></span>
<span data-ttu-id="7683a-103">您可以建立宣告的 Z 區段 （不同於未宣告 Z 區段，其必須是多個合作對象的訊息，下列的內文部分的最後一個部分） 結構任何的描述層級。</span><span class="sxs-lookup"><span data-stu-id="7683a-103">You can create declared Z segments at any level of a schema (unlike undeclared Z segments, which must be the last part of a multi-party message, following the body part).</span></span>  
  
### <a name="to-create-a-z-segment-in-biztalk-editor"></a><span data-ttu-id="7683a-104">在 [BizTalk 編輯器] 中建立 Z 區段</span><span class="sxs-lookup"><span data-stu-id="7683a-104">To create a Z segment in BizTalk Editor</span></span>  
  
1.  <span data-ttu-id="7683a-105">在 方案總管的 Visual Studio 中，以滑鼠右鍵按一下您想要新增 Z 區段，然後按一下 結構的描述**開啟**。</span><span class="sxs-lookup"><span data-stu-id="7683a-105">In Solution Explorer of Visual Studio, right-click the schema to which you want to add a Z segment, and then click **Open**.</span></span>  
  
2.  <span data-ttu-id="7683a-106">在 BizTalk 編輯器 中，以滑鼠右鍵按一下結構描述名稱的節點，指向**插入結構描述節點**，然後按一下 **子記錄**。</span><span class="sxs-lookup"><span data-stu-id="7683a-106">In BizTalk Editor, right-click the node with the name of the schema, point to **Insert Schema Node**, and then click **Child Record**.</span></span>  
  
3.  <span data-ttu-id="7683a-107">名稱的名稱開頭為三個英數字元數字，以大寫，為正在"Z"的第一個數字的記錄。</span><span class="sxs-lookup"><span data-stu-id="7683a-107">Name the record starting the name with three alphanumeric digits, in capitals, with the first digit being "Z".</span></span> <span data-ttu-id="7683a-108">（Z 區段標記必須包含三個字元）。插入底線 (_)，然後再加入 區段的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="7683a-108">(The Z segment tag must include three characters.) Insert an underscore (_), and then add a short description of the segment.</span></span> <span data-ttu-id="7683a-109">描述應該有一個或一系列的字，不含空格，每個字大寫的第一個字母。</span><span class="sxs-lookup"><span data-stu-id="7683a-109">The description should be one or a series of words, without spaces, with the first letter of each word capitalized.</span></span> <span data-ttu-id="7683a-110">最後一個字應該是 「 區段 」。</span><span class="sxs-lookup"><span data-stu-id="7683a-110">The last word should be "Segment".</span></span> <span data-ttu-id="7683a-111">（範例為"ZPP_PatientPreferencesSegment。）按 **Enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="7683a-111">(An example is "ZPP_PatientPreferencesSegment.) Press **Enter**.</span></span>  
  
4.  <span data-ttu-id="7683a-112">在 屬性 窗格中，輸入 Z 區段中，您想要的屬性包括**資料結構型別**（結構描述名稱或具有 xsd: anytype） **Max Occurs**，和**Min Occurs**。</span><span class="sxs-lookup"><span data-stu-id="7683a-112">In the Properties pane, type the properties you want for the Z segment, including **Data Structure Type** (schema name or xsd:anyType), **Max Occurs**, and **Min Occurs**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7683a-113">如果您輸入的資料結構類型的記錄，您無法加入子欄位項目。</span><span class="sxs-lookup"><span data-stu-id="7683a-113">If you enter a data structure type for the record, you will not be able to add a child field element.</span></span>  
  
5.  <span data-ttu-id="7683a-114">在 BizTalk 編輯器 中，以滑鼠右鍵按一下 Z 區段的名稱，指向**插入結構描述節點**，然後按一下 **子欄位項目**。</span><span class="sxs-lookup"><span data-stu-id="7683a-114">In BizTalk Editor, right-click the name of the Z segment, point to **Insert Schema Node**, then click **Child Field Element**.</span></span>  
  
6.  <span data-ttu-id="7683a-115">輸入欄位，名稱開頭的區段名稱，後面接著句號和欄位中，後面接著底線，然後的簡短描述的欄位數目的前三個位數的名稱。</span><span class="sxs-lookup"><span data-stu-id="7683a-115">Type the name of the field, starting the name with the first three digits of the segment name, followed by a period and the number of the field, followed by an underscore and then a short description of the field.</span></span> <span data-ttu-id="7683a-116">描述應該有一個或一系列的字，不含空格，每個字大寫的第一個字母。</span><span class="sxs-lookup"><span data-stu-id="7683a-116">The description should be one or a series of words, without spaces, with the first letter of each word capitalized.</span></span> <span data-ttu-id="7683a-117">按 **Enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="7683a-117">Press **Enter**.</span></span>  
  
7.  <span data-ttu-id="7683a-118">在 屬性 窗格中，輸入 Z 區段中，您想要的屬性包括**資料型別**， **Nillable**，**固定**， **Max Occurs**，和**Min Occurs**。</span><span class="sxs-lookup"><span data-stu-id="7683a-118">In the Properties pane, type the properties you want for the Z segment, including **Data Type**, **Nillable**, **Fixed**, **Max Occurs**, and **Min Occurs**.</span></span>  
  
8.  <span data-ttu-id="7683a-119">若要建立欄位與元件，建立記錄、 欄位，然後建立該記錄每個元件的子項目。</span><span class="sxs-lookup"><span data-stu-id="7683a-119">To create a field with components, create the field as a record, and then create a child element of that record for each component.</span></span> <span data-ttu-id="7683a-120">若要建立欄位時的子元件，建立欄位和元件的記錄，並且為子系的子元件項目。</span><span class="sxs-lookup"><span data-stu-id="7683a-120">To create a field with subcomponents, create the field and components as records, and the subcomponents as child elements.</span></span> <span data-ttu-id="7683a-121">請注意，子元件不能是複合資料類型。</span><span class="sxs-lookup"><span data-stu-id="7683a-121">Note that subcomponents cannot be composite data types.</span></span> <span data-ttu-id="7683a-122">例如，對於名為 ZPP_PatientPreferencesSegment 區段，您可以建立 ZPP.1_Dietary 欄位和 PD.1 的過敏情況元件與 PD.1.1_FoodGroupAllergy 子元件。</span><span class="sxs-lookup"><span data-stu-id="7683a-122">For example, for the segment named ZPP_PatientPreferencesSegment, you might create a ZPP.1_Dietary field and a PD.1 Allergies component with a PD.1.1_FoodGroupAllergy subcomponent.</span></span> <span data-ttu-id="7683a-123">PD.1.1_FoodGroupAllergy 子元件必須是簡單的資料類型。</span><span class="sxs-lookup"><span data-stu-id="7683a-123">The PD.1.1_FoodGroupAllergy subcomponent would have to be a simple data type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7683a-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7683a-124">See Also</span></span>  
 <span data-ttu-id="7683a-125">[擴充 HL7 2.X Z 物件結構描述](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span><span class="sxs-lookup"><span data-stu-id="7683a-125">[Extending HL7 2.X Schemas with Z Objects](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span></span>  
 <span data-ttu-id="7683a-126">[在結構描述中建立自訂資料型別](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="7683a-126">[Creating Custom Data Types in Schemas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md) </span></span>  
 <span data-ttu-id="7683a-127">[在結構描述中建立自訂的資料表](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="7683a-127">[Creating Custom Tables in Schemas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md) </span></span>  
 <span data-ttu-id="7683a-128">[擴充列舉型別](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="7683a-128">[Extending Enumerations](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md) </span></span>  
 [<span data-ttu-id="7683a-129">處理未宣告的 Z 區段</span><span class="sxs-lookup"><span data-stu-id="7683a-129">Handling Undeclared Z Segments</span></span>](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md)