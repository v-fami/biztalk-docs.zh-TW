---
title: 處理未宣告的 Z 區段 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Z segments, 2.X schemas
- 2.X schemas, undeclared Z segments
- segments, undeclared [Z objects]
- Z objects, undeclared segments
ms.assetid: 8878bc93-1833-4bfc-b80e-305e4144739e
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 633c1d338a87bef7c0fe53ff5df7f53438eac843
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990015"
---
# <a name="handling-undeclared-z-segments"></a><span data-ttu-id="b7464-102">處理未宣告的 Z 區段</span><span class="sxs-lookup"><span data-stu-id="b7464-102">Handling Undeclared Z Segments</span></span>
<span data-ttu-id="b7464-103">有兩種類型的 Z 區段： 宣告的 Z 區段和未宣告的 Z 區段。</span><span class="sxs-lookup"><span data-stu-id="b7464-103">There are two types of Z segments: declared Z segments and undeclared Z segments.</span></span> <span data-ttu-id="b7464-104">雖然它們的相似處，在於您用於本機的用途，它們是在您使用的方式非常不同。</span><span class="sxs-lookup"><span data-stu-id="b7464-104">While they are similar in that you use them for local purposes, they are very different in how you use them.</span></span>  
  
 <span data-ttu-id="b7464-105">您納入宣告的 Z 區段的定義訊息結構描述] 和 [Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 會使用它來處理訊息時，就像 HL7 標準所定義的結構描述。</span><span class="sxs-lookup"><span data-stu-id="b7464-105">You include the definition of a declared Z segment in a message schema, and Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) uses it to process a message, just like a schema defined by the HL7 standard.</span></span> <span data-ttu-id="b7464-106">沒有結構描述定義的未宣告的 Z 區段。</span><span class="sxs-lookup"><span data-stu-id="b7464-106">No schema defines an undeclared Z segment.</span></span> <span data-ttu-id="b7464-107">您包含結尾的訊息時，未宣告的 Z 區段和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]通過，而不需處理針對結構描述。</span><span class="sxs-lookup"><span data-stu-id="b7464-107">You include an undeclared Z segment at the end of a message, and [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] passes through without processing it against a schema.</span></span> <span data-ttu-id="b7464-108">剖析器和序列化程式不會驗證它。</span><span class="sxs-lookup"><span data-stu-id="b7464-108">The parser and serializer do not validate it.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="b7464-109"> 會將其視為二進位大型物件 (BLOB)。</span><span class="sxs-lookup"><span data-stu-id="b7464-109"> treats it as a binary large object (BLOB).</span></span> <span data-ttu-id="b7464-110">只檢查[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]未上未宣告的 Z 區段會驗證 BLOB 不包含任何現有的三個字元的結構描述標記。</span><span class="sxs-lookup"><span data-stu-id="b7464-110">The only check that [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] does on an undeclared Z segment is verifying that the BLOB does not include any existing three-character schema tag.</span></span>  
  
 <span data-ttu-id="b7464-111">您包含未宣告的 Z 區段，為第三個部分或 Z 部分的多部分訊息。</span><span class="sxs-lookup"><span data-stu-id="b7464-111">You include the undeclared Z segment as the third part, or Z part, of a multi-part message.</span></span> <span data-ttu-id="b7464-112">此訊息包含標頭、 內文和 Z 組件。</span><span class="sxs-lookup"><span data-stu-id="b7464-112">The message includes the header, the body, and the Z part.</span></span> <span data-ttu-id="b7464-113">Z 組件會有開頭為字母"Z"的區段識別碼。</span><span class="sxs-lookup"><span data-stu-id="b7464-113">The Z part has a segment ID starting with the letter "Z".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7464-114">Zpart 一律必須包含資料。</span><span class="sxs-lookup"><span data-stu-id="b7464-114">The Zpart must always contain data.</span></span> <span data-ttu-id="b7464-115">指定在錯誤狀況的資料流結果為 null。</span><span class="sxs-lookup"><span data-stu-id="b7464-115">Specifying null for the stream results in an error condition.</span></span> <span data-ttu-id="b7464-116">如果沒有資料包含在 Zpart， [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Zpart 中插入 「 空白 」 這個字。</span><span class="sxs-lookup"><span data-stu-id="b7464-116">If no data is included in the Zpart, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] inserts the word "Empty" in the Zpart.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="b7464-117"> 使用內容屬性**ZPartPresent**來判斷是否要序列化的 Z 部分。</span><span class="sxs-lookup"><span data-stu-id="b7464-117"> uses the context property **ZPartPresent** to determine whether to serialize the Z part.</span></span>  
> 
> [!CAUTION]
>  <span data-ttu-id="b7464-118">Microsoft 已經測試 Zsegments ANSI 字元集，以 ANSI 字元的 Zsegment 行為是可預測的結果。</span><span class="sxs-lookup"><span data-stu-id="b7464-118">Microsoft has tested Zsegments with ANSI character sets, with the result that Zsegment behavior with ANSI characters is predictable.</span></span> <span data-ttu-id="b7464-119">不過，使用其他字元集 Zsegments 中可能會導致無法預期的行為。</span><span class="sxs-lookup"><span data-stu-id="b7464-119">However, using other character sets in Zsegments may result in unpredictable behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7464-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7464-120">See Also</span></span>  
 <span data-ttu-id="b7464-121">[使用 Z 物件擴充 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span><span class="sxs-lookup"><span data-stu-id="b7464-121">[Extending HL7 2.X Schemas with Z Objects](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md) </span></span>  
 <span data-ttu-id="b7464-122">[建立宣告的 Z 區段](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md) </span><span class="sxs-lookup"><span data-stu-id="b7464-122">[Creating Declared Z Segments](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md) </span></span>  
 <span data-ttu-id="b7464-123">[結構描述中建立自訂資料類型](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="b7464-123">[Creating Custom Data Types in Schemas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md) </span></span>  
 [<span data-ttu-id="b7464-124">在結構描述中建立自訂資料表</span><span class="sxs-lookup"><span data-stu-id="b7464-124">Creating Custom Tables in Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md)