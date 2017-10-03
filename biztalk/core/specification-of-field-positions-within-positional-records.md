---
title: "在位置記錄中欄位位置的規格 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33c2eee3-ec30-46c5-a143-a3d2e2f265a6
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91a253c76e8f3394897514716978e1902cf2e3d8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="specification-of-field-positions-within-positional-records"></a><span data-ttu-id="cf87b-102">在位置記錄中欄位位置的規格</span><span class="sxs-lookup"><span data-stu-id="cf87b-102">Specification of Field Positions within Positional Records</span></span>
<span data-ttu-id="cf87b-103">若要定義序數記錄，您必須提供該記錄中欄位的位置和長度之相關資訊。</span><span class="sxs-lookup"><span data-stu-id="cf87b-103">To define a positional record, you must provide information about the positions and lengths of the fields within that record.</span></span> <span data-ttu-id="cf87b-104">若記錄包含子記錄，則子記錄中欄位的位置和長度會納入包含記錄之相關資訊。</span><span class="sxs-lookup"><span data-stu-id="cf87b-104">If the record contains subrecords, the positions and lengths of the fields in the subrecord are rolled up to contribute to the information about the containing record.</span></span>  
  
 <span data-ttu-id="cf87b-105">您為指定的值的總和**Positional Offset**和**Positional Length**特定屬性**欄位項目**或**欄位屬性**節點決定對應欄位專屬的字元數目。</span><span class="sxs-lookup"><span data-stu-id="cf87b-105">The sum of the values you specify for the **Positional Offset** and **Positional Length** properties for a particular **Field Element** or **Field Attribute** node determines the number of characters dedicated to the corresponding field.</span></span> <span data-ttu-id="cf87b-106">在記錄及其任何子記錄中所有欄位的這些總和決定記錄中欄位的界限。</span><span class="sxs-lookup"><span data-stu-id="cf87b-106">The series of these sums across all of the fields in the record and any of its subrecords determine the boundaries of the fields in the records.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf87b-107">當**Count Positions In Bytes**屬性**結構描述**節點設定為**是**、 **Positional Length**和**位置位移**屬性指定的位元組，而不是字元。</span><span class="sxs-lookup"><span data-stu-id="cf87b-107">When the **Count Positions In Bytes** property of the **Schema** node is set to **Yes**, the **Positional Length** and **Position Offset** properties specify bytes rather than characters.</span></span>  

<span data-ttu-id="cf87b-108">這些屬性查看詳細[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="cf87b-108">See more details on these properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="positional-offset-property"></a><span data-ttu-id="cf87b-109">Positional Offset 屬性</span><span class="sxs-lookup"><span data-stu-id="cf87b-109">Positional Offset property</span></span>  
 <span data-ttu-id="cf87b-110">當一般檔案解譯器將一般檔案執行個體訊息轉換為相等的 XML 執行個體訊息時，您指定值的**Positional Offset**屬性定義所忽略的幾個字元 （或位元組）並透過該位置執行個體訊息中略過。</span><span class="sxs-lookup"><span data-stu-id="cf87b-110">When the flat file disassembler is converting a flat file instance message into an equivalent XML instance message, the value you specify for the **Positional Offset** property defines a number of characters (or bytes) that are ignored and skipped over at that position in the instance message.</span></span> <span data-ttu-id="cf87b-111">換句話說，在該開始位置和長度發生的任何資訊 (所指定的第二個**Positional Offset**屬性) 在 一般檔案執行個體訊息將不會複製到訊息的 XML 版本。</span><span class="sxs-lookup"><span data-stu-id="cf87b-111">In other words, any information occurring at that starting position and length (the latter as specified by the **Positional Offset** property) in the flat file instance message will not be copied into the XML version of the message.</span></span>  
  
 <span data-ttu-id="cf87b-112">當一般檔案組合器將 XML 執行個體訊息轉換為相等的一般檔案執行個體訊息時，您指定值的**Positional Offset**屬性會定義填滿的數字字元 （或位元組）正在建立一般檔案執行個體訊息中該開始位置的空格字元。</span><span class="sxs-lookup"><span data-stu-id="cf87b-112">When the flat file assembler is converting an XML instance message into an equivalent flat file instance message, the value you specify for the **Positional Offset** property defines a number of characters (or bytes) that are filled with space characters at that starting position within the flat file instance message being created.</span></span> <span data-ttu-id="cf87b-113">空白字元永遠用來填滿位移位置，使用的字元無法設定。</span><span class="sxs-lookup"><span data-stu-id="cf87b-113">The space character is always used to fill offset positions; the character used is not configurable.</span></span>  
  
 <span data-ttu-id="cf87b-114">**Positional Offset**屬性提供彈性為解譯序數記錄的內容。</span><span class="sxs-lookup"><span data-stu-id="cf87b-114">The **Positional Offset** property provides flexibility for interpreting the contents of positional records.</span></span> <span data-ttu-id="cf87b-115">本質上，這個屬性可讓您忽略在設為非零值欄位前的任何固定長度資料。</span><span class="sxs-lookup"><span data-stu-id="cf87b-115">Essentially, this property allows you to ignore any fixed length data that precedes the field for which it is set to a nonzero value.</span></span> <span data-ttu-id="cf87b-116">該固定長度資料可能是一或多個整個欄位資料或某個類型的常數資料，像是與欄位關聯的標記，不需要包含在一般檔案執行個體訊息對等的 XML 中。</span><span class="sxs-lookup"><span data-stu-id="cf87b-116">That fixed length data might be one or more entire fields of data or some type of constant data, such as a tag associated with the field, that does not need to be included in the XML equivalent of the flat file instance message.</span></span> <span data-ttu-id="cf87b-117">如需詳細資訊，請參閱下列範例。</span><span class="sxs-lookup"><span data-stu-id="cf87b-117">For more information, see the example that follows.</span></span>  
  
## <a name="positional-length-property"></a><span data-ttu-id="cf87b-118">Positional Length 屬性</span><span class="sxs-lookup"><span data-stu-id="cf87b-118">Positional Length property</span></span>  
 <span data-ttu-id="cf87b-119">當一般檔案解譯器將一般檔案執行個體訊息轉換為相等的 XML 執行個體訊息時，您指定值的**Positional Length**屬性定義的字元 （或位元組） 的數目執行個體訊息中該位置欄位相關聯。</span><span class="sxs-lookup"><span data-stu-id="cf87b-119">When the flat file disassembler is converting a flat file instance message into an equivalent XML instance message, the value you specify for the **Positional Length** property defines the number of characters (or bytes) that are associated with the field at that position in the instance message.</span></span> <span data-ttu-id="cf87b-120">發生的開始位置和長度，一般檔案執行個體訊息中構成在欄位中，受限於提供由相關聯的其他資訊的資料的資訊**理由**和**填補字元**屬性。</span><span class="sxs-lookup"><span data-stu-id="cf87b-120">The information occurring at that starting position and length in the flat file instance message constitutes the data in the field, subject to the additional information provided by the associated **Justification** and **Pad Character** properties.</span></span> <span data-ttu-id="cf87b-121">如需有關左右對齊和欄位填補的概念性資訊，請參閱[欄位左右對齊](../core/field-justification.md)和[欄位填補](../core/field-padding.md)。</span><span class="sxs-lookup"><span data-stu-id="cf87b-121">For more conceptual information about justification and field padding, see [Field Justification](../core/field-justification.md) and [Field Padding](../core/field-padding.md).</span></span>  
  
 <span data-ttu-id="cf87b-122">當一般檔案組合器將 XML 執行個體訊息轉換為相等的一般檔案執行個體訊息時，您指定值的**Positional Length**屬性定義幾個字元 （或位元組） 適用於撰寫與該欄位相關聯的資料。</span><span class="sxs-lookup"><span data-stu-id="cf87b-122">When the flat file assembler is converting an XML instance message into an equivalent flat file instance message, the value you specify for the **Positional Length** property defines a number of characters (or bytes) available for writing the data associated with that field.</span></span> <span data-ttu-id="cf87b-123">若資料字元少於指定的欄位長度，則使用相關的填補字元填滿差距。</span><span class="sxs-lookup"><span data-stu-id="cf87b-123">If there are fewer data characters than the specified length of the field, the relevant pad character is used to fill up the difference.</span></span> <span data-ttu-id="cf87b-124">如果有資料字元多於指定欄位長度，開頭或結尾的資料會截斷為基礎的設定**理由**屬性，不包含在一般檔案執行個體訊息正在建構。</span><span class="sxs-lookup"><span data-stu-id="cf87b-124">If there are more data characters than the specified length of the field, the beginning or end of the data is truncated based on the setting of the **Justification** property and not included in the flat file instance message being constructed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf87b-125">靠左對齊資料的尾端部分會被截斷並捨棄。</span><span class="sxs-lookup"><span data-stu-id="cf87b-125">The trailing portion of left-aligned data is truncated and discarded.</span></span> <span data-ttu-id="cf87b-126">靠右對齊資料的開頭部分會被截斷並捨棄。</span><span class="sxs-lookup"><span data-stu-id="cf87b-126">The leading portion of right-aligned data is truncated and discarded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf87b-127">範例</span><span class="sxs-lookup"><span data-stu-id="cf87b-127">Example</span></span>  
 <span data-ttu-id="cf87b-128">考量下列的記錄欄位定義。</span><span class="sxs-lookup"><span data-stu-id="cf87b-128">Consider the following field definitions for a record.</span></span>  
  
|<span data-ttu-id="cf87b-129">欄位節點名稱</span><span class="sxs-lookup"><span data-stu-id="cf87b-129">Field node name</span></span>|<span data-ttu-id="cf87b-130">Offset</span><span class="sxs-lookup"><span data-stu-id="cf87b-130">Offset</span></span>|<span data-ttu-id="cf87b-131">長度</span><span class="sxs-lookup"><span data-stu-id="cf87b-131">Length</span></span>|<span data-ttu-id="cf87b-132">填補字元</span><span class="sxs-lookup"><span data-stu-id="cf87b-132">Pad Character</span></span>|<span data-ttu-id="cf87b-133">理由</span><span class="sxs-lookup"><span data-stu-id="cf87b-133">Justification</span></span>|  
|---------------------|------------|------------|-------------------|-------------------|  
|<span data-ttu-id="cf87b-134">Field1</span><span class="sxs-lookup"><span data-stu-id="cf87b-134">Field1</span></span>|<span data-ttu-id="cf87b-135">0</span><span class="sxs-lookup"><span data-stu-id="cf87b-135">0</span></span>|<span data-ttu-id="cf87b-136">6</span><span class="sxs-lookup"><span data-stu-id="cf87b-136">6</span></span>|<span data-ttu-id="cf87b-137">預設 (空格)</span><span class="sxs-lookup"><span data-stu-id="cf87b-137">Default (space)</span></span>|<span data-ttu-id="cf87b-138">Left</span><span class="sxs-lookup"><span data-stu-id="cf87b-138">Left</span></span>|  
|<span data-ttu-id="cf87b-139">Field2</span><span class="sxs-lookup"><span data-stu-id="cf87b-139">Field2</span></span>|<span data-ttu-id="cf87b-140">0</span><span class="sxs-lookup"><span data-stu-id="cf87b-140">0</span></span>|<span data-ttu-id="cf87b-141">4</span><span class="sxs-lookup"><span data-stu-id="cf87b-141">4</span></span>|*|<span data-ttu-id="cf87b-142">Right</span><span class="sxs-lookup"><span data-stu-id="cf87b-142">Right</span></span>|  
|<span data-ttu-id="cf87b-143">Field3</span><span class="sxs-lookup"><span data-stu-id="cf87b-143">Field3</span></span>|<span data-ttu-id="cf87b-144">2</span><span class="sxs-lookup"><span data-stu-id="cf87b-144">2</span></span>|<span data-ttu-id="cf87b-145">6</span><span class="sxs-lookup"><span data-stu-id="cf87b-145">6</span></span>|*|<span data-ttu-id="cf87b-146">Left</span><span class="sxs-lookup"><span data-stu-id="cf87b-146">Left</span></span>|  
|<span data-ttu-id="cf87b-147">Field4</span><span class="sxs-lookup"><span data-stu-id="cf87b-147">Field4</span></span>|<span data-ttu-id="cf87b-148">4</span><span class="sxs-lookup"><span data-stu-id="cf87b-148">4</span></span>|<span data-ttu-id="cf87b-149">6</span><span class="sxs-lookup"><span data-stu-id="cf87b-149">6</span></span>|<span data-ttu-id="cf87b-150">預設 (空格)</span><span class="sxs-lookup"><span data-stu-id="cf87b-150">Default (space)</span></span>|<span data-ttu-id="cf87b-151">Right</span><span class="sxs-lookup"><span data-stu-id="cf87b-151">Right</span></span>|  
  
 <span data-ttu-id="cf87b-152">具備這些欄位定義之記錄的開始點發生下列字元資料流 (第一行用於計算字元位置)。</span><span class="sxs-lookup"><span data-stu-id="cf87b-152">And the following stream of characters is encountered at the starting point of a record with these field definitions (the first line is for counting character positions).</span></span>  
  
```  
123456789012345678901234567890123456789012345678901234567890  
abc   **12345678**skip  here  
```  
  
 <span data-ttu-id="cf87b-153">當這些欄位定義套用到此範例記錄資料時，一般檔案解譯器會產生以下對等 XML (其資料以粗體字顯示)。</span><span class="sxs-lookup"><span data-stu-id="cf87b-153">When these field definitions are applied to this sample record data, the flat file disassembler produces the following XML equivalent (with the data shown in bold type).</span></span>  
  
```  
<Field1>abc</Field1>  
<Field2>12</Field2>  
<Field3>5678</Field3>  
<Field4>here</Field4>  
```  
  
 <span data-ttu-id="cf87b-154">下列觀察與此資料的剖析方式有關：</span><span class="sxs-lookup"><span data-stu-id="cf87b-154">The following observations are relevant to how this data is parsed:</span></span>  
  
-   <span data-ttu-id="cf87b-155">Field1 與相關聯的字元 （長度為 6，沒有位移） 是 「`abc` "，但不包含空格 XML 中因為空白字元是 Field1 的 （預設） 填補字元，而 Field1 定義為靠左對齊。</span><span class="sxs-lookup"><span data-stu-id="cf87b-155">The characters associated with Field1 (length 6 with no offset) are "`abc` ", but the spaces are not included in the XML because the space character is the (default) pad character for Field1 and Field1 is defined as left-aligned.</span></span>  
  
-   <span data-ttu-id="cf87b-156">與 Field2 (長度為 4，沒有位移) 關聯的字元為 "`**12`"，但 XML 中不包含星號，因為星號字元已定義為 Field2 的填補字元，而 Field2 定義為靠右對齊。</span><span class="sxs-lookup"><span data-stu-id="cf87b-156">The characters associated with Field2 (length 4 with no offset) are "`**12`", but the asterisks are not included in the XML because the asterisk character is the pad character defined for Field2 and Field2 is defined as right-aligned.</span></span>  
  
-   <span data-ttu-id="cf87b-157">與 Field3 (長度為 6，位移為 2) 關聯的字元為 "`345678**`"，但由於位移的緣故，所以 XML 中不包含 3 和 4。</span><span class="sxs-lookup"><span data-stu-id="cf87b-157">The characters associated with Field3 (length 6 plus an offset of 2) are "`345678**`", but the 3 and 4 are not included in the XML because of the offset.</span></span> <span data-ttu-id="cf87b-158">XML 中也不包含星號，因為星號字元已定義為 Field2 的填補字元，而 Field2 定義為靠左對齊。</span><span class="sxs-lookup"><span data-stu-id="cf87b-158">The asterisks are also not included in the XML because the asterisk character is the pad character defined for Field2 and Field2 is defined as left-aligned.</span></span>  
  
-   <span data-ttu-id="cf87b-159">與 Field4 (長度為 6，位移為 4) 關聯的字元為 "`skip  here`"，但由於位移的緣故，所以 XML 中不包含字元順序 "`skip`"。</span><span class="sxs-lookup"><span data-stu-id="cf87b-159">The characters associated with Field4 (length 6 plus an offset of 4) are "`skip  here`", but the character sequence "`skip`" is not included in the XML because of the offset.</span></span> <span data-ttu-id="cf87b-160">XML 中也不包含兩個空白字元，因為空白字元是 Field4 的 (預設) 填補字元，而 Field4 定義為靠右對齊。</span><span class="sxs-lookup"><span data-stu-id="cf87b-160">The two space characters are also not included in the XML because the space character is the (default) pad character for Field4 and Field4 is defined as right-aligned.</span></span>  
  
 <span data-ttu-id="cf87b-161">若此範例中由一般檔案解譯器產生的 XML 使用相同的欄位定義傳遞給一般檔案組合器，則會產生相同的一般檔案資料，但有兩個例外：捨棄的位移順序 34 和跳過會以空白字元填滿 (在緊接著資料的行中以 `^` 字元表示)。</span><span class="sxs-lookup"><span data-stu-id="cf87b-161">If the XML produced by the flat file disassembler in this example is passed to the flat file assembler using the same field definitions, the same flat file data is produced, with two exceptions: the discarded offset sequences 34 and skip are filled with space characters (indicated with the `^` character in the line following the data).</span></span>  
  
```  
123456789012345678901234567890123456789012345678901234567890  
abc   **12  5678**      here  
          ^^      ^^^^  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="cf87b-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf87b-162">See Also</span></span>  
-  [<span data-ttu-id="cf87b-163">欄位考量</span><span class="sxs-lookup"><span data-stu-id="cf87b-163">Field Considerations</span></span>](../core/field-considerations.md)    
-  [<span data-ttu-id="cf87b-164">欄位左右對齊</span><span class="sxs-lookup"><span data-stu-id="cf87b-164">Field Justification</span></span>](../core/field-justification.md)   
-  [<span data-ttu-id="cf87b-165">欄位填補</span><span class="sxs-lookup"><span data-stu-id="cf87b-165">Field Padding</span></span>](../core/field-padding.md)   
- <span data-ttu-id="cf87b-166">下列屬性的詳細資訊[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]:</span><span class="sxs-lookup"><span data-stu-id="cf87b-166">More info on the following properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]:</span></span>  
    - <span data-ttu-id="cf87b-167">計算位置，以位元組為單位 （一般檔案結構描述中的節點屬性）</span><span class="sxs-lookup"><span data-stu-id="cf87b-167">Count Positions In Bytes (Node Property of Flat File Schemas)</span></span>  
    - <span data-ttu-id="cf87b-168">對齊方式 （一般檔案結構描述中的節點屬性）</span><span class="sxs-lookup"><span data-stu-id="cf87b-168">Justification (Node Property of Flat File Schemas)</span></span>  
    - <span data-ttu-id="cf87b-169">Pad Character （一般檔案結構描述中的節點屬性）</span><span class="sxs-lookup"><span data-stu-id="cf87b-169">Pad Character (Node Property of Flat File Schemas)</span></span> 
    - <span data-ttu-id="cf87b-170">Positional Offset （一般檔案結構描述中的節點屬性）</span><span class="sxs-lookup"><span data-stu-id="cf87b-170">Positional Offset (Node Property of Flat File Schemas)</span></span>
    - <span data-ttu-id="cf87b-171">Positional Length （一般檔案結構描述中的節點屬性）</span><span class="sxs-lookup"><span data-stu-id="cf87b-171">Positional Length (Node Property of Flat File Schemas)</span></span>