---
title: 組合器管線元件中的屬性降級 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XML Assembler [pipeline component], properties
- pipeline components, properties
- BizTalk Framework Assembler [pipeline component], properties
- XML Assembler [pipeline component], about XML Assembler
- Flat File Assembler [pipeline component], properties
ms.assetid: c5275638-d594-4b0d-a818-b7a9460b41a6
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af634d302f01b18c91ebdbb7533673e8b9c545c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268830"
---
# <a name="property-demotion-in-assembler-pipeline-components"></a><span data-ttu-id="13862-102">組合器管線元件中的屬性降級</span><span class="sxs-lookup"><span data-stu-id="13862-102">Property Demotion in Assembler Pipeline Components</span></span>
<span data-ttu-id="13862-103">您可以使用屬性降級將訊息內容中的屬性值複製到訊息內容或其標頭或結尾。</span><span class="sxs-lookup"><span data-stu-id="13862-103">You can use property demotion to copy a property value from the message context into the message content or to its header or trailer.</span></span> <span data-ttu-id="13862-104">您可以使用在文件或標頭和結尾結構描述中指定的 XPath 運算式來完成屬性降級。</span><span class="sxs-lookup"><span data-stu-id="13862-104">You accomplish property demotion by using an XPath expression specified in the document or in the header and trailer schema.</span></span>  
  
 <span data-ttu-id="13862-105">將日期時間資料從內容屬性寫入產生的文件時，BizTalk Server 會假設所有資料時間資料都是 UTC 格式。</span><span class="sxs-lookup"><span data-stu-id="13862-105">When writing datetime data from the context property into the resulting document, BizTalk Server assumes that all datetime data is in UTC format.</span></span>  
  
 <span data-ttu-id="13862-106">用來將屬性寫入資料的格式，是由顯示在下表的 XSD 資料型別所決定。</span><span class="sxs-lookup"><span data-stu-id="13862-106">The format used to write properties into the data is determined by the XSD data type as shown in the following table.</span></span>  
  
|<span data-ttu-id="13862-107">資料類型</span><span class="sxs-lookup"><span data-stu-id="13862-107">Data type</span></span>|<span data-ttu-id="13862-108">格式</span><span class="sxs-lookup"><span data-stu-id="13862-108">Format</span></span>|  
|---------------|------------|  
|<span data-ttu-id="13862-109">xs:datetime</span><span class="sxs-lookup"><span data-stu-id="13862-109">xs:datetime</span></span>|<span data-ttu-id="13862-110">yyyy-MM-ddTHH:mm:ss.fffffffZ</span><span class="sxs-lookup"><span data-stu-id="13862-110">yyyy-MM-ddTHH:mm:ss.fffffffZ</span></span>|  
|<span data-ttu-id="13862-111">xs:date</span><span class="sxs-lookup"><span data-stu-id="13862-111">xs:date</span></span>|<span data-ttu-id="13862-112">yyyy-MM-ddZ</span><span class="sxs-lookup"><span data-stu-id="13862-112">yyyy-MM-ddZ</span></span>|  
|<span data-ttu-id="13862-113">xs:gDay</span><span class="sxs-lookup"><span data-stu-id="13862-113">xs:gDay</span></span>|<span data-ttu-id="13862-114">---ddZ</span><span class="sxs-lookup"><span data-stu-id="13862-114">---ddZ</span></span>|  
|<span data-ttu-id="13862-115">xs:gMonth</span><span class="sxs-lookup"><span data-stu-id="13862-115">xs:gMonth</span></span>|<span data-ttu-id="13862-116">--MM—Z</span><span class="sxs-lookup"><span data-stu-id="13862-116">--MM—Z</span></span>|  
|<span data-ttu-id="13862-117">xs:gMonthDay</span><span class="sxs-lookup"><span data-stu-id="13862-117">xs:gMonthDay</span></span>|<span data-ttu-id="13862-118">--MM-ddZ</span><span class="sxs-lookup"><span data-stu-id="13862-118">--MM-ddZ</span></span>|  
|<span data-ttu-id="13862-119">xs:gYear</span><span class="sxs-lookup"><span data-stu-id="13862-119">xs:gYear</span></span>|<span data-ttu-id="13862-120">yyyyZ</span><span class="sxs-lookup"><span data-stu-id="13862-120">yyyyZ</span></span>|  
|<span data-ttu-id="13862-121">xs:gYearMonth</span><span class="sxs-lookup"><span data-stu-id="13862-121">xs:gYearMonth</span></span>|<span data-ttu-id="13862-122">yyyy-MMZ</span><span class="sxs-lookup"><span data-stu-id="13862-122">yyyy-MMZ</span></span>|  
|<span data-ttu-id="13862-123">xs:time</span><span class="sxs-lookup"><span data-stu-id="13862-123">xs:time</span></span>|<span data-ttu-id="13862-124">HH:mm:ss.fffffffZ</span><span class="sxs-lookup"><span data-stu-id="13862-124">HH:mm:ss.fffffffZ</span></span>|  
  
## <a name="property-demotion-and-envelopes"></a><span data-ttu-id="13862-125">屬性降級和信封</span><span class="sxs-lookup"><span data-stu-id="13862-125">Property Demotion and Envelopes</span></span>  
 <span data-ttu-id="13862-126">在信封中組譯檔案時，將一或多個系統命名空間 — 或您自己的其中一個命名空間 — 中的值降級通常很有用。</span><span class="sxs-lookup"><span data-stu-id="13862-126">It is often useful to demote values from one or more of the system namespaces -- or one of your own namespaces -- when assembling files within an envelope.</span></span> <span data-ttu-id="13862-127">一些常見的案例包括：</span><span class="sxs-lookup"><span data-stu-id="13862-127">Some common scenarios include:</span></span>  
  
-   <span data-ttu-id="13862-128">您想要將提交至系統的原始檔案名稱包含在輸出訊息，以讓後端系統能夠追蹤資料的來源。</span><span class="sxs-lookup"><span data-stu-id="13862-128">You want to include the original file name submitted to the system in outbound messages so back-end systems can track the origin of data.</span></span>  
  
-   <span data-ttu-id="13862-129">您想將內文訊息中的資料寫入標頭中。</span><span class="sxs-lookup"><span data-stu-id="13862-129">You want to write data from the body message to the header.</span></span> <span data-ttu-id="13862-130">例如，將要命名的出貨寫入下游系統的信封中可能會對於訂單很有用。</span><span class="sxs-lookup"><span data-stu-id="13862-130">For example, for a purchase order it might be useful to write the ship to name to the envelope for down-stream systems.</span></span>  
  
-   <span data-ttu-id="13862-131">您想要將多個不同的欄位組合到標頭中，而不要撰寫自訂程式碼。</span><span class="sxs-lookup"><span data-stu-id="13862-131">You want to combine many different fields into the header without writing custom code.</span></span> <span data-ttu-id="13862-132">Xml 組合器或一般檔案組合器中的屬性降級可完成這項工作。</span><span class="sxs-lookup"><span data-stu-id="13862-132">Property demotion in the Xml assembler or flat file assembler can do the job.</span></span>  
  
 <span data-ttu-id="13862-133">必須記住，XML 和一般檔案組合器元件兩者都可讓您指定要對信封和文件內容使用的結構描述。</span><span class="sxs-lookup"><span data-stu-id="13862-133">It is important to remember that the XML and flat file assembler components both allow you to specify which schema to use for the envelope and document body.</span></span> <span data-ttu-id="13862-134">您在選擇用於解譯的相同結構描述，或建立包含不同欄位的新信封結構描述。</span><span class="sxs-lookup"><span data-stu-id="13862-134">You can choose the same schemas used in disassembly or create a new envelope schema with different fields.</span></span>  
  
 <span data-ttu-id="13862-135">如需這些概念的範例，請參閱[EnvelopeProcessing （BizTalk Server 範例）](../core/envelopeprocessing-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="13862-135">For an example of these concepts, see [EnvelopeProcessing (BizTalk Server Sample)](../core/envelopeprocessing-biztalk-server-sample.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13862-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13862-136">See Also</span></span>  
 <span data-ttu-id="13862-137">[一般檔案組合器管線元件](../core/flat-file-assembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="13862-137">[Flat File Assembler Pipeline Component](../core/flat-file-assembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="13862-138">如何設定一般檔案組合器管線元件</span><span class="sxs-lookup"><span data-stu-id="13862-138">How to Configure the Flat File Assembler Pipeline Component</span></span>](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md)