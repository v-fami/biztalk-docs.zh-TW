---
title: 保留和隱藏分隔符號 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30985b94-625e-411a-8137-1c129bc197bf
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9bb92d9784fb9e12494757407898388d6f52725e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975471"
---
# <a name="delimiter-preservation-and-suppression"></a><span data-ttu-id="b1795-102">保留和隱藏分隔符號</span><span class="sxs-lookup"><span data-stu-id="b1795-102">Delimiter Preservation and Suppression</span></span>

## <a name="overview"></a><span data-ttu-id="b1795-103">概觀</span><span class="sxs-lookup"><span data-stu-id="b1795-103">Overview</span></span>
<span data-ttu-id="b1795-104">有兩個適用於分隔記錄的屬性：**保留空白資料的分隔符號**並**隱藏尾端分隔符號**。</span><span class="sxs-lookup"><span data-stu-id="b1795-104">There are two properties that apply to delimited records: **Preserve Delimiter For Empty Data** and **Suppress Trailing Delimiters**.</span></span> <span data-ttu-id="b1795-105">使用這些屬性來控制一般檔案組合器如何處理不存在的資料和尾端分隔符號與相關聯的分隔符號。</span><span class="sxs-lookup"><span data-stu-id="b1795-105">Use these properties to control how the flat file assembler handles delimiters associated with nonexistent data and trailing delimiters.</span></span> <span data-ttu-id="b1795-106">當您設定**保留空白資料的分隔符號**屬性設**是**（此為預設設定，） 分隔符號會包含在轉譯的一般檔案訊息：</span><span class="sxs-lookup"><span data-stu-id="b1795-106">When you set the **Preserve Delimiter For Empty Data** property to **Yes** (which is the default setting), delimiters are included in the translated flat file message for:</span></span>  
  
- <span data-ttu-id="b1795-107">沒有資料的欄位。</span><span class="sxs-lookup"><span data-stu-id="b1795-107">Fields without data.</span></span>  
  
- <span data-ttu-id="b1795-108">沒有資料也沒有關聯標記的直接附屬記錄。</span><span class="sxs-lookup"><span data-stu-id="b1795-108">Immediately subordinate records without data that do not have a tag associated with them.</span></span>  
  
  <span data-ttu-id="b1795-109">當您設定**保留空白資料的分隔符號**屬性設**No**，分隔符號不會包含在轉譯的一般檔案的記錄和欄位，但不含資料。</span><span class="sxs-lookup"><span data-stu-id="b1795-109">When you set the **Preserve Delimiter For Empty Data** property to **No**, delimiters are not included in the translated flat file for records and fields without data.</span></span> <span data-ttu-id="b1795-110">此外，不論設定為何**保留空白資料的分隔符號**屬性，分隔符號不會納入的直接附屬記錄，但不含定義標記資料轉譯的一般檔案訊息。</span><span class="sxs-lookup"><span data-stu-id="b1795-110">Further, regardless of the setting of the **Preserve Delimiter For Empty Data** property, delimiters will not be included in the translated flat file message for immediately subordinate records without data for which a tag is defined.</span></span>  
  
  <span data-ttu-id="b1795-111">當您設定**隱藏尾端分隔符號**屬性設**No** （這是預設值），轉譯的一般檔案訊息中可能包含一或多個尾端分隔符號。</span><span class="sxs-lookup"><span data-stu-id="b1795-111">When you set the **Suppress Trailing Delimiters** property to **No** (which is the default setting), one or more trailing delimiters may be included in the translated flat file message.</span></span> <span data-ttu-id="b1795-112">當您設定**隱藏尾端分隔符號**屬性設**是**、 尾端分隔符號不會包含在轉譯的一般檔案訊息中。</span><span class="sxs-lookup"><span data-stu-id="b1795-112">When you set the **Suppress Trailing Delimiters** property to **Yes**, trailing delimiters are not included in the translated flat file message.</span></span>  

## <a name="special-scenarios"></a><span data-ttu-id="b1795-113">特殊案例</span><span class="sxs-lookup"><span data-stu-id="b1795-113">Special scenarios</span></span>  
 <span data-ttu-id="b1795-114">有一些特殊的情況下，設定所造成的行為**保留空白資料的分隔符號**並**隱藏尾端分隔符號**屬性可能會發生衝突。</span><span class="sxs-lookup"><span data-stu-id="b1795-114">There are some special cases where the behaviors caused by the settings of the **Preserve Delimiter For Empty Data** and **Suppress Trailing Delimiters** properties can conflict.</span></span> <span data-ttu-id="b1795-115">在此情況下，後者的屬性，與關聯的行為**隱藏尾端分隔符號**，將會優先。</span><span class="sxs-lookup"><span data-stu-id="b1795-115">In such cases, the behaviors associated with the latter property, **Suppress Trailing Delimiters**, will take precedence.</span></span> <span data-ttu-id="b1795-116">此外，在某些特殊情況下，若您為這兩個屬性所選擇的設定可能互相衝突時，則會提出警告。</span><span class="sxs-lookup"><span data-stu-id="b1795-116">Further, there are some special cases where you will be warned about potential conflicts between the settings you have chosen for these two properties.</span></span>  
  
 <span data-ttu-id="b1795-117">例如，請考慮**記錄**節點定義下列屬性值：</span><span class="sxs-lookup"><span data-stu-id="b1795-117">For example, consider a **Record** node defined with the following property values:</span></span>  
  
- <span data-ttu-id="b1795-118">節點名稱為 MyRec</span><span class="sxs-lookup"><span data-stu-id="b1795-118">Node Name is MyRec</span></span>  
  
- <span data-ttu-id="b1795-119">標記識別項為 Rec</span><span class="sxs-lookup"><span data-stu-id="b1795-119">Tag Identifier is Rec</span></span>  
  
- <span data-ttu-id="b1795-120">子分隔符號為 ,</span><span class="sxs-lookup"><span data-stu-id="b1795-120">Child Delimiter is ,</span></span>  
  
- <span data-ttu-id="b1795-121">子系順序為 Infix</span><span class="sxs-lookup"><span data-stu-id="b1795-121">Child Order is Infix</span></span>  
  
  <span data-ttu-id="b1795-122">並定義包含五個**欄位項目**具有下列名稱的節點 (也可以是**Field 屬性**節點或附屬**記錄**節點):</span><span class="sxs-lookup"><span data-stu-id="b1795-122">And defined to contain five **Field Element** nodes with the following names (they could also be **Field Attribute** nodes or subordinate **Record** nodes):</span></span>  
  
- <span data-ttu-id="b1795-123">FieldElem1</span><span class="sxs-lookup"><span data-stu-id="b1795-123">FieldElem1</span></span>  
  
- <span data-ttu-id="b1795-124">FieldElem2</span><span class="sxs-lookup"><span data-stu-id="b1795-124">FieldElem2</span></span>  
  
- <span data-ttu-id="b1795-125">FieldElem3</span><span class="sxs-lookup"><span data-stu-id="b1795-125">FieldElem3</span></span>  
  
- <span data-ttu-id="b1795-126">FieldElem4</span><span class="sxs-lookup"><span data-stu-id="b1795-126">FieldElem4</span></span>  
  
- <span data-ttu-id="b1795-127">FieldElem5</span><span class="sxs-lookup"><span data-stu-id="b1795-127">FieldElem5</span></span>  
  
  <span data-ttu-id="b1795-128">接下來，假設，下列主要的空 XML 片段，表示這個**記錄** 節點，會傳遞至一般檔案組合器。</span><span class="sxs-lookup"><span data-stu-id="b1795-128">Next, assume that the following mainly empty XML fragment, representing this **Record** node, is passed to the flat file assembler.</span></span>  
  
```  
<MyRec>  
    <FieldElem1 />  
    <FieldElem2 />  
    <FieldElem3>Val</FieldElem3>  
    <FieldElem4 />  
    <FieldElem5 />  
</MyRec>  
  
```  
  
 <span data-ttu-id="b1795-129">下表顯示所產生的輸出和相關聯的其他屬性，設定相關的結構描述節點，根據不同的設定需求**保留空白資料的分隔符號**(PDFED) 和**隱藏尾端分隔符號**(STD) 屬性。</span><span class="sxs-lookup"><span data-stu-id="b1795-129">The following table shows the output produced, and the associated additional property setting requirements for the relevant schema nodes, based on different settings for the **Preserve Delimiter For Empty Data** (PDFED) and **Suppress Trailing Delimiters** (STD) properties.</span></span>  
  
|<span data-ttu-id="b1795-130">PDFED 設定</span><span class="sxs-lookup"><span data-stu-id="b1795-130">PDFED setting</span></span>|<span data-ttu-id="b1795-131">STD 設定</span><span class="sxs-lookup"><span data-stu-id="b1795-131">STD setting</span></span>|<span data-ttu-id="b1795-132">輸出</span><span class="sxs-lookup"><span data-stu-id="b1795-132">Output</span></span>|<span data-ttu-id="b1795-133">其他節點需求</span><span class="sxs-lookup"><span data-stu-id="b1795-133">Additional node requirements</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="b1795-134">是</span><span class="sxs-lookup"><span data-stu-id="b1795-134">Yes</span></span>|<span data-ttu-id="b1795-135">否</span><span class="sxs-lookup"><span data-stu-id="b1795-135">No</span></span>|<span data-ttu-id="b1795-136">Rec,,,Val,,</span><span class="sxs-lookup"><span data-stu-id="b1795-136">Rec,,,Val,,</span></span>|<span data-ttu-id="b1795-137">無。</span><span class="sxs-lookup"><span data-stu-id="b1795-137">None.</span></span>|  
|<span data-ttu-id="b1795-138">否</span><span class="sxs-lookup"><span data-stu-id="b1795-138">No</span></span>|<span data-ttu-id="b1795-139">是</span><span class="sxs-lookup"><span data-stu-id="b1795-139">Yes</span></span>|<span data-ttu-id="b1795-140">Rec,Val</span><span class="sxs-lookup"><span data-stu-id="b1795-140">Rec,Val</span></span>|<span data-ttu-id="b1795-141">所有**欄位項目**節點必須設定為選擇性。</span><span class="sxs-lookup"><span data-stu-id="b1795-141">All **Field Element** nodes must be configured as optional.</span></span>|  
|<span data-ttu-id="b1795-142">是</span><span class="sxs-lookup"><span data-stu-id="b1795-142">Yes</span></span>|<span data-ttu-id="b1795-143">是</span><span class="sxs-lookup"><span data-stu-id="b1795-143">Yes</span></span>|<span data-ttu-id="b1795-144">Rec,,,Val</span><span class="sxs-lookup"><span data-stu-id="b1795-144">Rec,,,Val</span></span>|<span data-ttu-id="b1795-145">名為的節點**FieldElem4**並 **[fieldelem5]** 必須設定為選擇性。</span><span class="sxs-lookup"><span data-stu-id="b1795-145">Nodes named **FieldElem4** and **FieldElem5** must be configured as optional.</span></span>|  
|<span data-ttu-id="b1795-146">否</span><span class="sxs-lookup"><span data-stu-id="b1795-146">No</span></span>|<span data-ttu-id="b1795-147">否</span><span class="sxs-lookup"><span data-stu-id="b1795-147">No</span></span>|<span data-ttu-id="b1795-148">Rec,Val,,</span><span class="sxs-lookup"><span data-stu-id="b1795-148">Rec,Val,,</span></span>|<span data-ttu-id="b1795-149">所有**欄位項目**節點必須設定為選擇性。</span><span class="sxs-lookup"><span data-stu-id="b1795-149">All **Field Element** nodes must be configured as optional.</span></span>|  
  
 <span data-ttu-id="b1795-150">當這些屬性設定指定分隔符號不能保留或應該隱藏時，會在下列兩種情況下發出訊息，警告可能無法使用相同的結構描述剖析序列化的一般檔案資料：</span><span class="sxs-lookup"><span data-stu-id="b1795-150">When these property settings specify that delimiters should either not be preserved or should be suppressed, a message warning that it might not be possible to parse the serialized flat file data using the same schema will be issued in the following two cases:</span></span>  
  
-   <span data-ttu-id="b1795-151">當**記錄**節點**保留空白資料的分隔符號**屬性設定為**No**和/或**隱藏尾端分隔符號**屬性設定為 **[是]** 分別包含附屬於**欄位項目**節點**欄位屬性**節點，或**記錄**不指定任何標記的節點。</span><span class="sxs-lookup"><span data-stu-id="b1795-151">When the **Record** node for which the **Preserve Delimiter For Empty Data** property is set to **No** and/or the **Suppress Trailing Delimiters** property is set to **Yes**, respectively, contains subordinate **Field Element** nodes, **Field Attribute** nodes, or **Record** nodes for which no tag is specified.</span></span>  
  
-   <span data-ttu-id="b1795-152">當下層**欄位項目**節點，**欄位屬性**節點，和**記錄**不指定任何標記的節點未設定為 optional (藉由設定**Min Occurs**屬性設定為零) 結構描述中。</span><span class="sxs-lookup"><span data-stu-id="b1795-152">When the subordinate **Field Element** nodes, **Field Attribute** nodes, and **Record** nodes for which no tag is specified are not configured to be optional (by setting the **Min Occurs** property set to zero) in the schema.</span></span> <span data-ttu-id="b1795-153">當**隱藏尾端分隔符號**屬性設定為**是**，只有最後一個這類附屬節點都必須設定為選擇性。</span><span class="sxs-lookup"><span data-stu-id="b1795-153">When the **Suppress Trailing Delimiters** property is set to **Yes**, only the last such subordinate nodes need to be configured as optional.</span></span> <span data-ttu-id="b1795-154">當**保留空白資料的分隔符號**屬性設定為**No**，所有尾端附屬節點都必須設定為選擇性。</span><span class="sxs-lookup"><span data-stu-id="b1795-154">When the **Preserve Delimiter For Empty Data** property is set to **No**, all trailing subordinate nodes need to be configured as optional.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1795-155">XML 項目相關聯 （大概是選擇項） 時，一律會保留分隔符號**記錄**，**欄位項目**，或**欄位屬性**節點會完全遺失從商務文件，除了當後面接著 「 記錄遺失的選擇性欄位的 XML 表示法。</span><span class="sxs-lookup"><span data-stu-id="b1795-155">Delimiters are always preserved when the XML element associated with a (presumably optional) **Record**, **Field Element**, or **Field Attribute** node are entirely missing from the XML representation of the business document except when a Record follows a missing optional Field.</span></span> <span data-ttu-id="b1795-156">也就是說，當資料和括住它的 XML 標記都遺失時，對應的分隔符號永遠都會包含在商務文件的一般檔案表示法中。</span><span class="sxs-lookup"><span data-stu-id="b1795-156">In other words, when the data and its surrounding XML tags are both missing, the corresponding delimiter is always included in the flat file representation of the business document.</span></span>  
  
 <span data-ttu-id="b1795-157">現在請變更結構描述，以兩個欄位項目 (緊接在遺失的欄位項目之後) 包含子記錄。</span><span class="sxs-lookup"><span data-stu-id="b1795-157">Now change the schema to include a child record with two Field Element immediately following a missing Field Element.</span></span> <span data-ttu-id="b1795-158">子記錄項目設定為使用&#124;（管線） 字元做為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="b1795-158">The child record elements are configured to use the &#124; (pipe) character as a delimiter.</span></span>  
  
```  
<MyRec>  
    <FieldElem1 />  
    <FieldElem2 />  
    <FieldElem3>Val</FieldElem3>  
    <!-- <FieldElem4 /> -->  
    <ChildRec>  
        <InnerFieldElement1>Inner1</InnerFieldElement1>   
        <InnerFieldElement2>Inner2</InnerFieldElement1>  
    </ChildRec>  
    <FieldElem5 />  
</MyRec>  
  
```  
  
 <span data-ttu-id="b1795-159">如果此記錄被傳遞給一般檔案解譯器，將不會保留 FieldElem4 的分隔符號，但是會如預期地分隔後續的記錄。</span><span class="sxs-lookup"><span data-stu-id="b1795-159">If this is passed to the flat file disassembler, the delimiters for FieldElem4 will not be preserved but subsequent records will be delimited as expected.</span></span>  
  
```  
,,Val,,Inner1,Inner2,,  
```  
  
## <a name="see-also"></a><span data-ttu-id="b1795-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1795-160">See Also</span></span>  
- [<span data-ttu-id="b1795-161">分隔記錄考量</span><span class="sxs-lookup"><span data-stu-id="b1795-161">Delimited Record Considerations</span></span>](../core/delimited-record-considerations.md)   
- <span data-ttu-id="b1795-162">**保留空白資料 （一般檔案結構描述中的節點屬性） 的分隔符號**和**隱藏尾端分隔符號 （一般檔案結構描述中的節點屬性）** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="b1795-162">**Preserve Delimiter For Empty Data (Node Property of Flat File Schemas)** and **Suppress Trailing Delimiters (Node Property of Flat File Schemas)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
