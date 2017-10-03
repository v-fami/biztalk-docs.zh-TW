---
title: "處理未宣告的 Z 區段 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Z segments, 2.X schemas
- 2.X schemas, undeclared Z segments
- segments, undeclared [Z objects]
- Z objects, undeclared segments
ms.assetid: 8878bc93-1833-4bfc-b80e-305e4144739e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ff982aedee39ed60820a9f03db11d7e4d051a34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="handling-undeclared-z-segments"></a><span data-ttu-id="9e2ff-102">處理未宣告的 Z 區段</span><span class="sxs-lookup"><span data-stu-id="9e2ff-102">Handling Undeclared Z Segments</span></span>
<span data-ttu-id="9e2ff-103">有兩種類型的 Z 區段： 宣告 Z 線段，而未宣告的 Z 線段。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-103">There are two types of Z segments: declared Z segments and undeclared Z segments.</span></span> <span data-ttu-id="9e2ff-104">時，您可以使用這些本機進行，它們很相似，它們是在您使用的方式大不相同。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-104">While they are similar in that you use them for local purposes, they are very different in how you use them.</span></span>  
  
 <span data-ttu-id="9e2ff-105">您在訊息結構描述中包含宣告 Z 線段的定義和[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 使用它來處理訊息，就像 HL7 標準所定義的結構描述。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-105">You include the definition of a declared Z segment in a message schema, and [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) uses it to process a message, just like a schema defined by the HL7 standard.</span></span> <span data-ttu-id="9e2ff-106">沒有結構描述定義了未宣告的 Z 區段。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-106">No schema defines an undeclared Z segment.</span></span> <span data-ttu-id="9e2ff-107">包含未宣告的 Z 區段結尾的訊息，和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]通過，而不需處理針對結構描述。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-107">You include an undeclared Z segment at the end of a message, and [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] passes through without processing it against a schema.</span></span> <span data-ttu-id="9e2ff-108">剖析器和序列化程式不會驗證它。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-108">The parser and serializer do not validate it.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="9e2ff-109">會將它視為二進位大型物件 (BLOB)。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-109"> treats it as a binary large object (BLOB).</span></span> <span data-ttu-id="9e2ff-110">僅檢查[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]沒有上未宣告的 Z 區段會驗證 BLOB 不包含任何現有的三個字元的結構描述標記。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-110">The only check that [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] does on an undeclared Z segment is verifying that the BLOB does not include any existing three-character schema tag.</span></span>  
  
 <span data-ttu-id="9e2ff-111">您包含未宣告的 Z 區段，做為第三個部分或 Z 部分多部分訊息。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-111">You include the undeclared Z segment as the third part, or Z part, of a multi-part message.</span></span> <span data-ttu-id="9e2ff-112">此訊息包含的標頭、 內文和 Z 組件。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-112">The message includes the header, the body, and the Z part.</span></span> <span data-ttu-id="9e2ff-113">Z 部分具有開頭為字母"Z"的區段識別碼。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-113">The Z part has a segment ID starting with the letter "Z".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e2ff-114">Zpart 必須永遠包含資料。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-114">The Zpart must always contain data.</span></span> <span data-ttu-id="9e2ff-115">指定在錯誤狀況的資料流結果為 null。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-115">Specifying null for the stream results in an error condition.</span></span> <span data-ttu-id="9e2ff-116">如果沒有資料包含在 Zpart [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Zpart 中插入 「 空白 」 這個字。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-116">If no data is included in the Zpart, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] inserts the word "Empty" in the Zpart.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="9e2ff-117">使用內容屬性**ZPartPresent**來判斷是否要序列化的 Z 部分。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-117"> uses the context property **ZPartPresent** to determine whether to serialize the Z part.</span></span>  
  
> [!CAUTION]
>  [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="9e2ff-118">過測試 Zsegments ANSI 字元集，ANSI 字元的 Zsegment 行為是可預測的結果。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-118"> has tested Zsegments with ANSI character sets, with the result that Zsegment behavior with ANSI characters is predictable.</span></span> <span data-ttu-id="9e2ff-119">不過，使用其他字元集 Zsegments 中可能會導致無法預期的行為。</span><span class="sxs-lookup"><span data-stu-id="9e2ff-119">However, using other character sets in Zsegments may result in unpredictable behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e2ff-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e2ff-120">See Also</span></span>  
 <span data-ttu-id="9e2ff-121">[擴充 HL7 2.X Z 物件結構描述](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span><span class="sxs-lookup"><span data-stu-id="9e2ff-121">[Extending HL7 2.X Schemas with Z Objects](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span></span>  
 <span data-ttu-id="9e2ff-122">[建立宣告的 Z 區段](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md) </span><span class="sxs-lookup"><span data-stu-id="9e2ff-122">[Creating Declared Z Segments](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md) </span></span>  
 <span data-ttu-id="9e2ff-123">[在結構描述中建立自訂資料型別](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="9e2ff-123">[Creating Custom Data Types in Schemas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md) </span></span>  
 [<span data-ttu-id="9e2ff-124">在結構描述中建立自訂的資料表</span><span class="sxs-lookup"><span data-stu-id="9e2ff-124">Creating Custom Tables in Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md)