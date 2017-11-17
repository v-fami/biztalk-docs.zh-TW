---
title: "具有分隔記錄的一般檔案訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7ad7119b-4e39-43df-9dba-a04382eb6db2
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5dc9eb0253e2bfe8824f6395e1c619c23f0e551
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="flat-file-messages-with-delimited-records"></a><span data-ttu-id="b9bc5-102">具有分隔記錄的一般檔案訊息</span><span class="sxs-lookup"><span data-stu-id="b9bc5-102">Flat File Messages with Delimited Records</span></span>
<span data-ttu-id="b9bc5-103">在一般檔案執行個體訊息中的分隔記錄包含由預先定義的字元或字元集分隔的巢狀記錄和/或個別欄位 (資料項目)。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-103">Delimited records within a flat file instance message contain nested records and/or individual fields (items of data) that are separated by a predefined character or set of characters.</span></span> <span data-ttu-id="b9bc5-104">系統根據這些個別的分隔符號來剖析欄位。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-104">The fields are parsed according to these separating delimiters.</span></span> <span data-ttu-id="b9bc5-105">例如，請考慮一般檔案執行個體訊息中的下列分隔記錄，其中包含一個假設性的訂單中的兩個產品項目：</span><span class="sxs-lookup"><span data-stu-id="b9bc5-105">For example, consider the following delimited records from a flat file instance message, which contain two line items from a hypothetical purchase order:</span></span>  
  
```  
  
ITEMS,ITEM872-AA|Lawnmower|1|148.95|Electric-120vac,ITEM926-AA|Baby Monitor|1|39.98|Electric-4AA|2004-01-21  
  
```  
  
 <span data-ttu-id="b9bc5-106">此記錄的一般檔案結構描述中的合理定義可如下所述：</span><span class="sxs-lookup"><span data-stu-id="b9bc5-106">A reasonable definition for this record in a flat file schema can be described as follows:</span></span>  
  
-   <span data-ttu-id="b9bc5-107">具有子分隔符號 (,)、子順序前置詞以及標記 ITEMS 之分隔記錄命名的項目。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-107">A delimited record named items with child delimiter (,), child order prefix, and the tag ITEMS.</span></span>  
  
    -   <span data-ttu-id="b9bc5-108">之分隔，重複記錄命名項目具有子分隔符號 &#124;、 子順序中置以及標記項目。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-108">A delimited, repeating record named item with child delimiter &#124;, child order infix, and the tag ITEM.</span></span>  
  
    -   <span data-ttu-id="b9bc5-109">名為 "partNum" 的屬性。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-109">An attribute named "partNum".</span></span>  
  
    -   <span data-ttu-id="b9bc5-110">名為 "productName" 的項目。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-110">An element named "productName".</span></span>  
  
    -   <span data-ttu-id="b9bc5-111">名為 "quantity" 的項目。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-111">An element named "quantity".</span></span>  
  
    -   <span data-ttu-id="b9bc5-112">名為 "USPrice" 的項目。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-112">An element named "USPrice".</span></span>  
  
    -   <span data-ttu-id="b9bc5-113">名為 "powerSource" 的項目。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-113">An element named "powerSource".</span></span>  
  
-   <span data-ttu-id="b9bc5-114">名為 "shipDate" 的選擇性項目。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-114">An optional element named "shipDate".</span></span>  
  
 <span data-ttu-id="b9bc5-115">指定這些記錄和欄位定義之後，一般檔案解譯器會產生等同於這些記錄的下列 XML。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-115">Given these record and field definitions, the flat file disassembler produces the following XML equivalent of these records.</span></span>  
  
```  
  
<items>  
    <item partNum="872-AA">  
        <productName>Lawnmower</productName>  
        <quantity>1</quantity>  
        <USPrice>148.95</USPrice>  
        <powerSource>Electric-120vac</powerSource>  
    </item>  
    <item partNum="926-AA">  
        <productName>Baby Monitor</productName>  
        <quantity>1</quantity>  
        <USPrice>39.98</USPrice>  
        <powerSource>Electric-4AA</powerSource>  
        <shipDate>2004-01-21</shipDate>  
    </item>  
</items>  
  
```  
  
 <span data-ttu-id="b9bc5-116">有一些與分隔記錄相關的考量，會影響接收記錄後剖析記錄的方式，以及傳送記錄後建構記錄的方式，這些考量包括：</span><span class="sxs-lookup"><span data-stu-id="b9bc5-116">There are a number of considerations related to delimited records that will affect how the record is parsed when received and constructed when sent, including:</span></span>  
  
-   <span data-ttu-id="b9bc5-117">用來覆寫分隔符號解譯以便將它們做為資料之一部分的一或多個字元。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-117">The character or characters used to override the interpretation of delimiters so that they are treated as part of the data.</span></span> <span data-ttu-id="b9bc5-118">如需詳細資訊，請參閱[方式解譯特殊字元做為欄位值的一部分](../core/ways-to-interpret-special-characters-as-part-of-a-field-value.md)。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-118">For more information, see [Ways to Interpret Special Characters as Part of a Field Value](../core/ways-to-interpret-special-characters-as-part-of-a-field-value.md).</span></span>  
  
-   <span data-ttu-id="b9bc5-119">在記錄開頭的一個選擇性標記，用來區別記錄與其他相似的記錄。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-119">An optional tag at the beginning of the record, used to distinguish the record from other similar records.</span></span> <span data-ttu-id="b9bc5-120">如需詳細資訊，請參閱[在分隔記錄中處理標記](../core/tag-handling-in-delimited-records.md)。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-120">For more information, see [Tag Handling in Delimited Records](../core/tag-handling-in-delimited-records.md).</span></span>  
  
-   <span data-ttu-id="b9bc5-121">在有最小長度限制的欄位中資料的對齊方式與其填補字元有關。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-121">How data is justified within fields with minimum lengths, relative to the accompanying pad characters.</span></span> <span data-ttu-id="b9bc5-122">如需詳細資訊，請參閱[欄位填補](../core/field-padding.md)，[欄位左右對齊](../core/field-justification.md)，和[最小欄位長度內分隔記錄](../core/minimum-field-lengths-within-delimited-records.md)。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-122">For more information, see [Field Padding](../core/field-padding.md), [Field Justification](../core/field-justification.md), and [Minimum Field Lengths Within Delimited Records](../core/minimum-field-lengths-within-delimited-records.md).</span></span>  
  
-   <span data-ttu-id="b9bc5-123">在其他分隔記錄中的巢狀位置記錄。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-123">Positional records nested within other delimited records.</span></span> <span data-ttu-id="b9bc5-124">如需詳細資訊，請參閱[巢狀位置記錄與分隔記錄](../core/nested-positional-and-delimited-records.md)。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-124">For more information, see [Nested Positional and Delimited Records](../core/nested-positional-and-delimited-records.md).</span></span>  
  
-   <span data-ttu-id="b9bc5-125">在固定長度的欄位中資料的對齊方式與其填補字元有關。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-125">How data is justified within a fixed length field, relative to its accompanying pad characters.</span></span> <span data-ttu-id="b9bc5-126">如需詳細資訊，請參閱[欄位左右對齊](../core/field-justification.md)。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-126">For more information, see [Field Justification](../core/field-justification.md).</span></span>  
  
-   <span data-ttu-id="b9bc5-127">與分隔符號所分隔之資料相關的位置考量。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-127">Considerations concerning the positioning of delimiters relate to the data that they delimit.</span></span> <span data-ttu-id="b9bc5-128">如需詳細資訊，請參閱[子順序考量](../core/child-order-considerations.md)。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-128">For more information, see [Child Order Considerations](../core/child-order-considerations.md).</span></span>  
  
-   <span data-ttu-id="b9bc5-129">在接收或傳送一般檔案訊息時保留和隱藏分隔符號。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-129">Preservation and suppression of delimiters when flat file messages are received and sent.</span></span> <span data-ttu-id="b9bc5-130">如需詳細資訊，請參閱[保留和隱藏分隔符號](../core/delimiter-preservation-and-suppression.md)。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-130">For more information, see [Delimiter Preservation and Suppression](../core/delimiter-preservation-and-suppression.md).</span></span>  
  
 <span data-ttu-id="b9bc5-131">若要協助您深入了解如何使用分隔的一般檔案，請參閱位於的 FlatFileReceive 和 FlatFileSend 資料夾中的範例[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Pipelines\AssemblerDisassembler\\。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-131">To help you better understand how to work with delimited flat files, see the samples in the FlatFileReceive and FlatFileSend folders located at [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Pipelines\AssemblerDisassembler\\.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9bc5-132">如果您的一般檔案包含分隔和位置記錄，您必須設定**結構**根節點屬性**分隔**和**結構**屬性附屬記錄節點設為 **分隔**或**Positional**依適當情況。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-132">If your flat file contains both delimited and positional records, you must set the **Structure** property of the root node to **Delimited** and the **Structure** property of subordinate record nodes to either **Delimited** or **Positional** as appropriate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9bc5-133">一般檔案中的分隔欄位長度限制為 50000000 個字元。</span><span class="sxs-lookup"><span data-stu-id="b9bc5-133">Delimited fields in flat files have a limit of 50000000 characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9bc5-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9bc5-134">See Also</span></span>  
 <span data-ttu-id="b9bc5-135">[一般檔案訊息的結構](../core/structure-of-a-flat-file-message.md) </span><span class="sxs-lookup"><span data-stu-id="b9bc5-135">[Structure of a Flat File Message](../core/structure-of-a-flat-file-message.md) </span></span>  
 <span data-ttu-id="b9bc5-136">[如何建立一般檔案訊息的結構描述](../core/how-to-create-schemas-for-flat-file-messages.md) </span><span class="sxs-lookup"><span data-stu-id="b9bc5-136">[How to Create Schemas for Flat File Messages](../core/how-to-create-schemas-for-flat-file-messages.md) </span></span>  
 [<span data-ttu-id="b9bc5-137">移轉一般檔案記錄</span><span class="sxs-lookup"><span data-stu-id="b9bc5-137">Migrating Flat File Records</span></span>](../core/migrating-flat-file-records.md)