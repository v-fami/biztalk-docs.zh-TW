---
title: 訊息分隔符號 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, events
- messages, XML messages
- events
- delimiters
- messages, delimiters
- flat files
- XML messages
- messages, flat files
ms.assetid: d25bf6db-5512-4c82-be0e-00da024c55d1
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3339ded8edf46f7c5b96317cdf7a3ec822ec808b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001495"
---
# <a name="message-delimiters"></a><span data-ttu-id="bd30e-102">訊息分隔符號</span><span class="sxs-lookup"><span data-stu-id="bd30e-102">Message Delimiters</span></span>
<span data-ttu-id="bd30e-103">HL7 標準所定義的訊息事件的形式如下：</span><span class="sxs-lookup"><span data-stu-id="bd30e-103">Message events defined by HL7 standards take the following form:</span></span>  
  
- <span data-ttu-id="bd30e-104">**一般檔案**。</span><span class="sxs-lookup"><span data-stu-id="bd30e-104">**Flat files**.</span></span> <span data-ttu-id="bd30e-105">HL7 2.4 及更早版本的版本所定義的訊息事件的一般檔案形式。</span><span class="sxs-lookup"><span data-stu-id="bd30e-105">Message events defined by HL7 versions 2.4 and earlier take the form of flat files.</span></span>  
  
- <span data-ttu-id="bd30e-106">**XML**。</span><span class="sxs-lookup"><span data-stu-id="bd30e-106">**XML**.</span></span> <span data-ttu-id="bd30e-107">HL7 版本 2.XML 和第 3 版所定義的訊息事件的 XML 檔案形式。</span><span class="sxs-lookup"><span data-stu-id="bd30e-107">Message events defined by HL7 versions 2.XML and version 3 take the form of XML files.</span></span>  
  
  <span data-ttu-id="bd30e-108">標準 HL7 未遵循位置的格式，因為它會使用分隔符號來定義區段、 欄位、 元件和子元件層級的一般檔案。</span><span class="sxs-lookup"><span data-stu-id="bd30e-108">Since the HL7 standard does not follow positional format, it uses delimiters to define the segment, field, component, and subcomponent levels of flat files.</span></span> <span data-ttu-id="bd30e-109">下表列出由 HL7 一般檔案的預設分隔符號。</span><span class="sxs-lookup"><span data-stu-id="bd30e-109">The following table lists the default delimiters used by HL7 flat files.</span></span>  
  
|<span data-ttu-id="bd30e-110">分隔符號</span><span class="sxs-lookup"><span data-stu-id="bd30e-110">Delimiter</span></span>|<span data-ttu-id="bd30e-111">ReplTest1</span><span class="sxs-lookup"><span data-stu-id="bd30e-111">Value</span></span>|<span data-ttu-id="bd30e-112">使用方式</span><span class="sxs-lookup"><span data-stu-id="bd30e-112">Usage</span></span>|  
|---------------|-----------|-----------|  
|<span data-ttu-id="bd30e-113">區段結束字元</span><span class="sxs-lookup"><span data-stu-id="bd30e-113">Segment terminator</span></span>|<span data-ttu-id="bd30e-114">\<cr\></span><span class="sxs-lookup"><span data-stu-id="bd30e-114">\<cr\></span></span>|<span data-ttu-id="bd30e-115">歸位字元結束區段的記錄。</span><span class="sxs-lookup"><span data-stu-id="bd30e-115">A carriage return terminates a segment record.</span></span> <span data-ttu-id="bd30e-116">您無法變更此值。</span><span class="sxs-lookup"><span data-stu-id="bd30e-116">You cannot change this value.</span></span>|  
|<span data-ttu-id="bd30e-117">欄位分隔符號</span><span class="sxs-lookup"><span data-stu-id="bd30e-117">Field separator</span></span>|<span data-ttu-id="bd30e-118">&#124;</span><span class="sxs-lookup"><span data-stu-id="bd30e-118">&#124;</span></span>|<span data-ttu-id="bd30e-119">縱線字元分隔的區段中的兩個相鄰的資料欄位。</span><span class="sxs-lookup"><span data-stu-id="bd30e-119">A pipe character separates two adjacent data fields within a segment.</span></span> <span data-ttu-id="bd30e-120">此字元，也會將每個區段的第一個資料欄位的區段識別碼。</span><span class="sxs-lookup"><span data-stu-id="bd30e-120">This character also separates the segment ID from the first data field in each segment.</span></span>|  
|<span data-ttu-id="bd30e-121">元件分隔符號</span><span class="sxs-lookup"><span data-stu-id="bd30e-121">Component separator</span></span>|^|<span data-ttu-id="bd30e-122">Hat 字元會分隔相鄰的元件的資料欄位允許的 HL7 標準位置。</span><span class="sxs-lookup"><span data-stu-id="bd30e-122">A hat character separates adjacent components of data fields where allowed by the HL7 standard.</span></span>|  
|<span data-ttu-id="bd30e-123">子元件分隔符號</span><span class="sxs-lookup"><span data-stu-id="bd30e-123">Subcomponent separator</span></span>|&|<span data-ttu-id="bd30e-124">連字號字元會分隔相鄰的子元件的資料欄位允許的 HL7 標準位置。</span><span class="sxs-lookup"><span data-stu-id="bd30e-124">An ampersand character separates adjacent subcomponents of data fields where allowed by the HL7 standard.</span></span> <span data-ttu-id="bd30e-125">如果不有任何子元件，您就可以省略此字元。</span><span class="sxs-lookup"><span data-stu-id="bd30e-125">If there are no subcomponents, then you can omit this character.</span></span>|  
|<span data-ttu-id="bd30e-126">重複分隔符號</span><span class="sxs-lookup"><span data-stu-id="bd30e-126">Repetition separator</span></span>|~|<span data-ttu-id="bd30e-127">波狀符號字元分隔的欄位中的子元件或元件的多個項目允許 HL7 標準的位置。</span><span class="sxs-lookup"><span data-stu-id="bd30e-127">A tilde character separates multiple occurrences of components or subcomponents in a field where allowed by the HL7 standard.</span></span>|  
|<span data-ttu-id="bd30e-128">逸出字元</span><span class="sxs-lookup"><span data-stu-id="bd30e-128">Escape character</span></span>|<span data-ttu-id="bd30e-129">\|使用符合 ST、 TX 或 全文檢索資料類型的任何欄位或 ED 資料類型的資料 （第四個） 元件，您可以使用逸出字元。</span><span class="sxs-lookup"><span data-stu-id="bd30e-129">\|You use an escape character with any field that conforms to an ST, TX, or FT data type, or with the data (fourth) component of the ED data type.</span></span> <span data-ttu-id="bd30e-130">如果沒有逸出字元存在訊息中，您可以省略此字元。</span><span class="sxs-lookup"><span data-stu-id="bd30e-130">If no escape characters exist in a message, you can omit this character.</span></span> <span data-ttu-id="bd30e-131">不過，您必須將它包含如果您使用訊息中的子元件。</span><span class="sxs-lookup"><span data-stu-id="bd30e-131">However, you must include it if you use subcomponents in the message.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bd30e-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd30e-132">See Also</span></span>  
 <span data-ttu-id="bd30e-133">[處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="bd30e-133">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 <span data-ttu-id="bd30e-134">[訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="bd30e-134">[Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span></span>  
 [<span data-ttu-id="bd30e-135">使用 HL7 2.X 結構描述</span><span class="sxs-lookup"><span data-stu-id="bd30e-135">Using HL7 2.X Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)