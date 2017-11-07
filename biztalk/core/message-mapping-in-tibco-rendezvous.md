---
title: "訊息 TIBCO Rendezvous 中的對應 |Microsoft 文件"
description: "訊息欄位和 XML 在 BizTalk Adapter for TIBCO Rendezvous 訊息對應"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62793bec-f076-425c-b25e-c4be5bd93cc8
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb80ea4f908aa50dc32755c333aa3ccf2ea4db91
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="message-mapping-in-tibco-rendezvous"></a><span data-ttu-id="56ba5-103">TIBCO Rendezvous 中的訊息對應</span><span class="sxs-lookup"><span data-stu-id="56ba5-103">Message Mapping in TIBCO Rendezvous</span></span>
<span data-ttu-id="56ba5-104">TIBCO Rendezvous 訊息是由標頭資訊與一系列訊息欄位所組成。</span><span class="sxs-lookup"><span data-stu-id="56ba5-104">TIBCO Rendezvous messages are composed of header information and a set of message fields.</span></span> <span data-ttu-id="56ba5-105">標頭資訊直接對應訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="56ba5-105">The header information is directly mapped to message context properties.</span></span>  
  
## <a name="message-field-elements"></a><span data-ttu-id="56ba5-106">訊息欄位元素</span><span class="sxs-lookup"><span data-stu-id="56ba5-106">Message Field Elements</span></span>  
 <span data-ttu-id="56ba5-107">訊息欄位由下列元素所組成：</span><span class="sxs-lookup"><span data-stu-id="56ba5-107">A message field is composed of the following elements:</span></span>  
  
|<span data-ttu-id="56ba5-108">元素</span><span class="sxs-lookup"><span data-stu-id="56ba5-108">Element</span></span>|<span data-ttu-id="56ba5-109">Description</span><span class="sxs-lookup"><span data-stu-id="56ba5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="56ba5-110">**名稱**</span><span class="sxs-lookup"><span data-stu-id="56ba5-110">**Name**</span></span>|<span data-ttu-id="56ba5-111">字元字串。</span><span class="sxs-lookup"><span data-stu-id="56ba5-111">Character string.</span></span> <span data-ttu-id="56ba5-112">在訊息中不需是唯一的。</span><span class="sxs-lookup"><span data-stu-id="56ba5-112">Does not have to be unique in a message.</span></span>|  
|<span data-ttu-id="56ba5-113">**識別碼**</span><span class="sxs-lookup"><span data-stu-id="56ba5-113">**Identifier**</span></span>|<span data-ttu-id="56ba5-114">短整數。</span><span class="sxs-lookup"><span data-stu-id="56ba5-114">Short integer.</span></span> <span data-ttu-id="56ba5-115">在訊息中是唯一的。</span><span class="sxs-lookup"><span data-stu-id="56ba5-115">Unique in a message.</span></span> <span data-ttu-id="56ba5-116">以隱含方式將訊息到 65535 之間的欄位數目的限制。</span><span class="sxs-lookup"><span data-stu-id="56ba5-116">Implicitly limits the number of message fields to 65535.</span></span> <span data-ttu-id="56ba5-117">識別項的範圍是訊息 （或子訊息）。</span><span class="sxs-lookup"><span data-stu-id="56ba5-117">The scope of the identifier is the message (or sub message).</span></span> <span data-ttu-id="56ba5-118">相同的識別碼可用於兩個子訊息 (包含的訊息中它們各自的部分) 中。</span><span class="sxs-lookup"><span data-stu-id="56ba5-118">The same identifier can be used in two sub-messages, which are themselves part of a containing message.</span></span>|  
|<span data-ttu-id="56ba5-119">**值**</span><span class="sxs-lookup"><span data-stu-id="56ba5-119">**Value**</span></span>|<span data-ttu-id="56ba5-120">訊息欄位資料。</span><span class="sxs-lookup"><span data-stu-id="56ba5-120">The message field data.</span></span>|  
|<span data-ttu-id="56ba5-121">**Count**</span><span class="sxs-lookup"><span data-stu-id="56ba5-121">**Count**</span></span>|<span data-ttu-id="56ba5-122">項目數 (在陣列的情況中)</span><span class="sxs-lookup"><span data-stu-id="56ba5-122">Number of items (in the case of an array)</span></span>|  
|<span data-ttu-id="56ba5-123">**型別**</span><span class="sxs-lookup"><span data-stu-id="56ba5-123">**Type**</span></span>|<span data-ttu-id="56ba5-124">訊息欄位的類型。</span><span class="sxs-lookup"><span data-stu-id="56ba5-124">The type of the message field.</span></span>|  
  
### <a name="mapping-process"></a><span data-ttu-id="56ba5-125">對應程序</span><span class="sxs-lookup"><span data-stu-id="56ba5-125">Mapping Process</span></span>  
 <span data-ttu-id="56ba5-126">TIBCO Rendezvous 結構化訊息會以下列方式對應至 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="56ba5-126">TIBCO Rendezvous structured messages are mapped to XML elements in the following way:</span></span>  
  
-   <span data-ttu-id="56ba5-127">**名稱**做為項目名稱。</span><span class="sxs-lookup"><span data-stu-id="56ba5-127">**Name** is used as the element name.</span></span> <span data-ttu-id="56ba5-128">TIBCO Rendezvous 欄位名稱可能會包含無法做為 XML 元素名稱的字元。</span><span class="sxs-lookup"><span data-stu-id="56ba5-128">The TIBCO Rendezvous field name may contain characters that are not valid for use in XML element names.</span></span> <span data-ttu-id="56ba5-129">配接器會在 XML 與 TIBCO Rendezvous 結構化訊息之間產生有效的字元對應。</span><span class="sxs-lookup"><span data-stu-id="56ba5-129">The adapter generates valid character mappings between XML and TIBCO Rendezvous structured messages.</span></span>  
  
-   <span data-ttu-id="56ba5-130">**識別項**會放入 'id' 屬性。</span><span class="sxs-lookup"><span data-stu-id="56ba5-130">**Identifier** is put into an ‘id’ attribute.</span></span>  
  
-   <span data-ttu-id="56ba5-131">**值**包含項目主體的字串表示法。</span><span class="sxs-lookup"><span data-stu-id="56ba5-131">**Value** contains a string representation that is the body of the element.</span></span>  
  
-   <span data-ttu-id="56ba5-132">**計數**會被忽略。</span><span class="sxs-lookup"><span data-stu-id="56ba5-132">**Count** is ignored.</span></span>  
  
-   <span data-ttu-id="56ba5-133">**型別**資訊放入產生的元素的 xsi: type 屬性。</span><span class="sxs-lookup"><span data-stu-id="56ba5-133">**Type** information is put into an xsi:type attribute for the generated element.</span></span>  
  
     <span data-ttu-id="56ba5-134">如需詳細資訊，請參閱[Data Type Mapping for TIBCO Rendezvous 中的 接收處理常式](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md)。</span><span class="sxs-lookup"><span data-stu-id="56ba5-134">For more information, see [Data Type Mapping for Receive Handlers in TIBCO Rendezvous](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56ba5-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56ba5-135">See Also</span></span>  
 <span data-ttu-id="56ba5-136">[TIBCO Rendezvous 概念](../core/tibco-rendezvous-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="56ba5-136">[TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md) </span></span>  
 [<span data-ttu-id="56ba5-137">建立 TIBCO Rendezvous 接收處理常式</span><span class="sxs-lookup"><span data-stu-id="56ba5-137">Creating TIBCO Rendezvous Receive Handlers</span></span>](../core/creating-tibco-rendezvous-receive-handlers.md)