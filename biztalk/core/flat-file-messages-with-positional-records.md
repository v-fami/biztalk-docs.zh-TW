---
title: "具有位置記錄的一般檔案訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72c17c25-3847-458e-a43e-0dbdc42db749
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26c9e4551abcbd0fba32b21fb8e4205bece6e82f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="flat-file-messages-with-positional-records"></a><span data-ttu-id="7f084-102">具有位置記錄的一般檔案訊息</span><span class="sxs-lookup"><span data-stu-id="7f084-102">Flat File Messages with Positional Records</span></span>
<span data-ttu-id="7f084-103">在一般檔案執行個體訊息中的位置記錄包含每個均有預先定義長度的個別欄位 (資料項目)。</span><span class="sxs-lookup"><span data-stu-id="7f084-103">Positional records within a flat file instance message contain individual fields (items of data) that are each of a predefined length.</span></span> <span data-ttu-id="7f084-104">會根據這些長度來剖析欄位。</span><span class="sxs-lookup"><span data-stu-id="7f084-104">The fields are parsed according to these lengths.</span></span> <span data-ttu-id="7f084-105">例如，請考慮下列一般檔案執行個體訊息的位置記錄，其中包含送貨地址 (第一行顯示為每個欄位保留的字元數目)。</span><span class="sxs-lookup"><span data-stu-id="7f084-105">For example, consider the following positional record from a flat file instance message, which contains a ship to address (the first line shows the number of characters reserved for each field).</span></span>  
  
```  
123456789012345678901234567890123456789012345678901234567890123456789012345  
US        Alice Smith         123 Maple Street    Mill Valley    CA 90952  
```  
  
 <span data-ttu-id="7f084-106">在一般檔案結構描述中對此記錄的合理定義可描述為位置記錄 (稱之為 shipTo)，其中包含下列欄位：</span><span class="sxs-lookup"><span data-stu-id="7f084-106">A reasonable definition for this record in a flat file schema can be described as a positional record named shipTo that contains the following fields:</span></span>  
  
-   <span data-ttu-id="7f084-107">名稱為 [國家/地區] 的屬性，該屬性靠左對齊，長度為 10 個字元，包含零個字元位移。</span><span class="sxs-lookup"><span data-stu-id="7f084-107">An attribute named country/region that is left-aligned, 10 characters in length, with a zero character offset.</span></span>  
  
-   <span data-ttu-id="7f084-108">名稱為 [名稱] 的項目，該項目靠左對齊，長度為 20 個字元，包含零個字元位移。</span><span class="sxs-lookup"><span data-stu-id="7f084-108">An element named name that is left-aligned, 20 characters in length, with a zero character offset.</span></span>  
  
-   <span data-ttu-id="7f084-109">名稱為 [街道] 的項目，該項目靠左對齊，長度為 20 個字元，包含零個字元位移。</span><span class="sxs-lookup"><span data-stu-id="7f084-109">An element named street that is left-aligned, 20 characters in length, with a zero character offset.</span></span>  
  
-   <span data-ttu-id="7f084-110">名稱為 [縣市] 的項目，該項目靠左對齊，長度為 15 個字元，包含零個字元位移。</span><span class="sxs-lookup"><span data-stu-id="7f084-110">An element named city that is left-aligned, 15 characters in length, with a zero character offset.</span></span>  
  
-   <span data-ttu-id="7f084-111">名稱為 [省市] 的項目，該項目靠左對齊，長度為 2 個字元，包含零個字元位移。</span><span class="sxs-lookup"><span data-stu-id="7f084-111">An element named state that is left-aligned, 2 characters in length, with a zero character offset.</span></span>  
  
-   <span data-ttu-id="7f084-112">名稱為 [郵遞區號] 的項目，該項目靠左對齊，長度為 5 個字元，包含一個字元位移。</span><span class="sxs-lookup"><span data-stu-id="7f084-112">An element named zip that is left-aligned, 5 characters in length, with a one character offset.</span></span>  
  
 <span data-ttu-id="7f084-113">指定這些記錄和欄位定義之後，一般檔案解譯器會產生等同於此記錄的下列 XML。</span><span class="sxs-lookup"><span data-stu-id="7f084-113">Given these record and field definitions, the flat file disassembler will produce the following XML equivalent of this record.</span></span>  
  
```  
<shipTo country/region="US">  
    <name>Alice Smith</name>  
    <street>123 Maple Street</street>  
    <city>Mill Valley</city>  
    <state>CA</state>  
    <zip>90952</zip>  
</shipTo>  
  
```  
  
 <span data-ttu-id="7f084-114">有一些與位置記錄相關的考量，會影響接收記錄後剖析記錄的方式，以及傳送記錄後建構記錄的方式，這些考量包括：</span><span class="sxs-lookup"><span data-stu-id="7f084-114">There are a number of considerations related to positional records that will affect how the record is parsed when received and constructed when sent, including:</span></span>  
  
-   <span data-ttu-id="7f084-115">用來填入每個欄位未使用部分的字元，稱為填補字元。</span><span class="sxs-lookup"><span data-stu-id="7f084-115">The character used to fill the unused portion of each field, known as the pad character.</span></span> <span data-ttu-id="7f084-116">如需詳細資訊，請參閱[欄位填補](../core/field-padding.md)。</span><span class="sxs-lookup"><span data-stu-id="7f084-116">For more information, see [Field Padding](../core/field-padding.md).</span></span>  
  
-   <span data-ttu-id="7f084-117">記錄中的一個選擇性標記，用來區別記錄與其他相似的記錄。</span><span class="sxs-lookup"><span data-stu-id="7f084-117">An optional tag within the record, used to distinguish the record from other similar records.</span></span> <span data-ttu-id="7f084-118">標記通常出現在記錄的開頭，不過，它可以出現在記錄中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="7f084-118">Tags usually occur at the beginning of the record but allowable anywhere within it.</span></span> <span data-ttu-id="7f084-119">如需詳細資訊，請參閱[在位置記錄中處理標記](../core/tag-handling-in-positional-records.md)。</span><span class="sxs-lookup"><span data-stu-id="7f084-119">For more information, see [Tag Handling in Positional Records](../core/tag-handling-in-positional-records.md).</span></span> <span data-ttu-id="7f084-120">位置記錄可以定義為有標記或沒有標記，但是，一旦定義之後，會根據定義決定標記是否必須存在。</span><span class="sxs-lookup"><span data-stu-id="7f084-120">Positional records can be defined to have a tag or not have a tag, but once defined, the tag must be present or not, based on the definition.</span></span>  
  
-   <span data-ttu-id="7f084-121">在固定長度的欄位中資料的對齊方式與其填補字元有關。</span><span class="sxs-lookup"><span data-stu-id="7f084-121">How data is justified within a fixed length field, relative to the accompanying pad characters.</span></span> <span data-ttu-id="7f084-122">如需詳細資訊，請參閱[欄位左右對齊](../core/field-justification.md)。</span><span class="sxs-lookup"><span data-stu-id="7f084-122">For more information, see [Field Justification](../core/field-justification.md).</span></span>  
  
-   <span data-ttu-id="7f084-123">在其他位置或分隔記錄中的巢狀位置記錄。</span><span class="sxs-lookup"><span data-stu-id="7f084-123">Positional records nested within other positional or delimited records.</span></span> <span data-ttu-id="7f084-124">如需詳細資訊，請參閱[巢狀位置記錄](../core/nested-positional-records.md)。</span><span class="sxs-lookup"><span data-stu-id="7f084-124">For more information, see [Nested Positional Records](../core/nested-positional-records.md).</span></span>  
  
-   <span data-ttu-id="7f084-125">位置記錄中指定的欄位長度為特定的位元組數目，而不是特定的字元數目。</span><span class="sxs-lookup"><span data-stu-id="7f084-125">Positional records with field lengths specified as a specific number of bytes rather than a specific number of characters.</span></span> <span data-ttu-id="7f084-126">如需詳細資訊，請參閱[以位元組為單位計算位置](../core/position-counting-in-bytes.md)。</span><span class="sxs-lookup"><span data-stu-id="7f084-126">For more information, see [Position Counting in Bytes](../core/position-counting-in-bytes.md).</span></span>  
  
 <span data-ttu-id="7f084-127">若要協助您深入了解如何使用位置一般檔案，請參閱位於 \Program Files\Microsoft 的 FlatFileReceive 和 FlatFileSend 資料夾中的範例[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]\SDK\Samples\Pipelines\AssemblerDisassembler\\。</span><span class="sxs-lookup"><span data-stu-id="7f084-127">To help you better understand how to work with positional flat files, see the samples in the FlatFileReceive and FlatFileSend folders located at \Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]\SDK\Samples\Pipelines\AssemblerDisassembler\\.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f084-128">如果您的一般檔案包含分隔和位置記錄，您必須設定**結構**根節點屬性**分隔**和**結構**屬性附屬記錄節點設為 **分隔**或**Positional**依適當情況。</span><span class="sxs-lookup"><span data-stu-id="7f084-128">If your flat file contains both delimited and positional records, you must set the **Structure** property of the root node to **Delimited** and the **Structure** property of subordinate record nodes to either **Delimited** or **Positional** as appropriate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f084-129">位置記錄中的欄位長度限制為 50000000 個字元。</span><span class="sxs-lookup"><span data-stu-id="7f084-129">Fields in positional records have a limit of 50000000 characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f084-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f084-130">See Also</span></span>  
 <span data-ttu-id="7f084-131">[一般檔案訊息的結構](../core/structure-of-a-flat-file-message.md) </span><span class="sxs-lookup"><span data-stu-id="7f084-131">[Structure of a Flat File Message](../core/structure-of-a-flat-file-message.md) </span></span>  
 [<span data-ttu-id="7f084-132">如何建立一般檔案訊息的結構描述</span><span class="sxs-lookup"><span data-stu-id="7f084-132">How to Create Schemas for Flat File Messages</span></span>](../core/how-to-create-schemas-for-flat-file-messages.md)