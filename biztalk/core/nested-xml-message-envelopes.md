---
title: "巢狀 XML 訊息信封 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e880cef1-4e73-4bce-a06e-8c4d23bc5a8c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46b0f505dd9ba7da71df1cb460f9c9a6610763d3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="nested-xml-message-envelopes"></a><span data-ttu-id="b3476-102">巢狀 XML 訊息信封</span><span class="sxs-lookup"><span data-stu-id="b3476-102">Nested XML Message Envelopes</span></span>
<span data-ttu-id="b3476-103">您可以巢狀處理 XML 信封以建立複雜文件結構。</span><span class="sxs-lookup"><span data-stu-id="b3476-103">XML envelopes can be nested to create complex document structures.</span></span> <span data-ttu-id="b3476-104">巢狀 XML 信封有兩種格式，稱為彈性格式與標準格式。</span><span class="sxs-lookup"><span data-stu-id="b3476-104">Nested XML envelopes can occur in two forms, known as flexible and canonical.</span></span> <span data-ttu-id="b3476-105">下列範例顯示信封文件的彈性格式，其中文件和信封 (以粗體顯示) 可出現在封入信封中的相同層級。</span><span class="sxs-lookup"><span data-stu-id="b3476-105">The following example shows the flexible form of enveloped documents, in which documents and envelopes (shown in bold type) can appear at the same level within an enclosing envelope.</span></span>  
  
```  
<envelope1>  
    <document1/>    <envelope2>  
        <document2/>  
        <document3/>  
    </envelope2>    <document4/>  
</envelope1>  
```  
  
 <span data-ttu-id="b3476-106">下列範例類似的執行個體訊息信封文件，所有文件出現在最內層的信封中相同層級中的標準格式符合。</span><span class="sxs-lookup"><span data-stu-id="b3476-106">The following example shows a similar instance message that conforms to the canonical form of enveloped documents, in which all documents appear at the same level within the innermost envelope.</span></span>  
  
```  
<envelope1>  
    <envelope2>  
        <document1/>  
        <document2/>  
        <document3/>  
        <document4/>  
    </envelope2>  
</envelope1>  
  
```  
  
 <span data-ttu-id="b3476-107">假定執行個體訊息為上述的其中一種格式，XML 解譯器將會產生 document1、document2、document3 及 document4。</span><span class="sxs-lookup"><span data-stu-id="b3476-107">Given an instance message in either of the forms described, the XML disassembler will produce document1, document2, document3, and document4.</span></span> <span data-ttu-id="b3476-108">這些文件中的每一個之訊息內容會包含從對應的文件升級之屬性，以及每個封入信封中升級的屬性。</span><span class="sxs-lookup"><span data-stu-id="b3476-108">The message context of each of these documents includes the properties promoted from the corresponding document as well as the properties promoted within each of the enclosing envelopes.</span></span> <span data-ttu-id="b3476-109">下表顯示在每個彈性與標準格式範例之未包裝文件的訊息內容中將包含的升級屬性，這是假定在各個信封與文件的第一欄中已指定屬性升級。</span><span class="sxs-lookup"><span data-stu-id="b3476-109">The following table shows the promoted properties that will be include in the message context of each unwrapped documents for both the flexible and canonical examples, given the property promotions specified in the first column for the various envelopes and documents.</span></span>  
  
|<span data-ttu-id="b3476-110">指定屬性升級</span><span class="sxs-lookup"><span data-stu-id="b3476-110">Specified property promotions</span></span>|<span data-ttu-id="b3476-111">彈性格式範例的結果訊息內容屬性</span><span class="sxs-lookup"><span data-stu-id="b3476-111">Resulting message context properties for flexible example</span></span>|<span data-ttu-id="b3476-112">標準格式範例的結果訊息內容屬性</span><span class="sxs-lookup"><span data-stu-id="b3476-112">Resulting message context properties for canonical example</span></span>|  
|-----------------------------------|---------------------------------------------------------------|----------------------------------------------------------------|  
|<span data-ttu-id="b3476-113">envelope1: p1</span><span class="sxs-lookup"><span data-stu-id="b3476-113">envelope1: p1</span></span><br /><br /> <span data-ttu-id="b3476-114">envelope2: p3</span><span class="sxs-lookup"><span data-stu-id="b3476-114">envelope2: p3</span></span><br /><br /> <span data-ttu-id="b3476-115">document1: p2</span><span class="sxs-lookup"><span data-stu-id="b3476-115">document1: p2</span></span><br /><br /> <span data-ttu-id="b3476-116">document2: p4 and p5</span><span class="sxs-lookup"><span data-stu-id="b3476-116">document2: p4 and p5</span></span><br /><br /> <span data-ttu-id="b3476-117">document3: no promotions</span><span class="sxs-lookup"><span data-stu-id="b3476-117">document3: no promotions</span></span><br /><br /> <span data-ttu-id="b3476-118">document4: no promotions</span><span class="sxs-lookup"><span data-stu-id="b3476-118">document4: no promotions</span></span>|<span data-ttu-id="b3476-119">document1: p1, p2</span><span class="sxs-lookup"><span data-stu-id="b3476-119">document1: p1, p2</span></span><br /><br /> <span data-ttu-id="b3476-120">document2: p1, p3, p4, p5</span><span class="sxs-lookup"><span data-stu-id="b3476-120">document2: p1, p3, p4, p5</span></span><br /><br /> <span data-ttu-id="b3476-121">document3: p1, p3</span><span class="sxs-lookup"><span data-stu-id="b3476-121">document3: p1, p3</span></span><br /><br /> <span data-ttu-id="b3476-122">document4: p1</span><span class="sxs-lookup"><span data-stu-id="b3476-122">document4: p1</span></span>|<span data-ttu-id="b3476-123">document1: p1, p2, p3</span><span class="sxs-lookup"><span data-stu-id="b3476-123">document1: p1, p2, p3</span></span><br /><br /> <span data-ttu-id="b3476-124">document2: p1, p3, p4, p5</span><span class="sxs-lookup"><span data-stu-id="b3476-124">document2: p1, p3, p4, p5</span></span><br /><br /> <span data-ttu-id="b3476-125">document3: p1, p3</span><span class="sxs-lookup"><span data-stu-id="b3476-125">document3: p1, p3</span></span><br /><br /> <span data-ttu-id="b3476-126">document4: p1, p3</span><span class="sxs-lookup"><span data-stu-id="b3476-126">document4: p1, p3</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b3476-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3476-127">See Also</span></span>  
 <span data-ttu-id="b3476-128">[XML 訊息信封](../core/xml-message-envelopes.md) </span><span class="sxs-lookup"><span data-stu-id="b3476-128">[XML Message Envelopes](../core/xml-message-envelopes.md) </span></span>  
 <span data-ttu-id="b3476-129">[XML 訊息的結構](../core/structure-of-an-xml-message.md) </span><span class="sxs-lookup"><span data-stu-id="b3476-129">[Structure of an XML Message](../core/structure-of-an-xml-message.md) </span></span>  
 [<span data-ttu-id="b3476-130">如何建立信封的結構描述</span><span class="sxs-lookup"><span data-stu-id="b3476-130">How to Create Schemas for Envelopes</span></span>](../core/how-to-create-schemas-for-envelopes.md)