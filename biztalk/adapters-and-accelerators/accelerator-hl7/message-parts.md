---
title: 訊息部分 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, segments
- messages, fields
- messages, message parts
- segments, messages
ms.assetid: 2bb6557e-cd4a-42b7-8bc2-f8b53a59517e
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9b6b02096a0cc75460552a6cd1dd56ef9e6c4e9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22205078"
---
# <a name="message-parts"></a><span data-ttu-id="913de-102">訊息部分</span><span class="sxs-lookup"><span data-stu-id="913de-102">Message Parts</span></span>
<span data-ttu-id="913de-103">HL7 訊息包含下列部分： 區段、 資料欄位、 元件和選擇性子元件。</span><span class="sxs-lookup"><span data-stu-id="913de-103">An HL7 message contains the following parts: segments, data fields, components, and optionally subcomponents.</span></span> <span data-ttu-id="913de-104">HL7 訊息有下列的階層式結構：</span><span class="sxs-lookup"><span data-stu-id="913de-104">HL7 messages have the following hierarchical structure:</span></span>  
  
 <span data-ttu-id="913de-105">區段</span><span class="sxs-lookup"><span data-stu-id="913de-105">Segment</span></span>  
  
 <span data-ttu-id="913de-106">資料欄位</span><span class="sxs-lookup"><span data-stu-id="913de-106">Data Field</span></span>  
  
 <span data-ttu-id="913de-107">元件</span><span class="sxs-lookup"><span data-stu-id="913de-107">Component</span></span>  
  
 <span data-ttu-id="913de-108">子元件 （選擇性）</span><span class="sxs-lookup"><span data-stu-id="913de-108">Subcomponent (optional)</span></span>  
  
 <span data-ttu-id="913de-109">**區段**</span><span class="sxs-lookup"><span data-stu-id="913de-109">**Segments**</span></span>  
  
 <span data-ttu-id="913de-110">區段是資料欄位的邏輯群組。</span><span class="sxs-lookup"><span data-stu-id="913de-110">A segment is a logical grouping of data fields.</span></span> <span data-ttu-id="913de-111">區段位於最高的層級 （深度 1） 訊息階層。</span><span class="sxs-lookup"><span data-stu-id="913de-111">Segments are at the highest level (depth 1) of the message hierarchy.</span></span> <span data-ttu-id="913de-112">每個區段具有包含三個字元常值的名稱。</span><span class="sxs-lookup"><span data-stu-id="913de-112">Each segment has a name that includes a three-character literal value.</span></span> <span data-ttu-id="913de-113">下表顯示 ADT 訊息類型所包含的區段名稱的範例。</span><span class="sxs-lookup"><span data-stu-id="913de-113">The following table shows examples of segment names contained by ADT message types.</span></span>  
  
|<span data-ttu-id="913de-114">區段程式碼</span><span class="sxs-lookup"><span data-stu-id="913de-114">Segment code</span></span>|<span data-ttu-id="913de-115">Description</span><span class="sxs-lookup"><span data-stu-id="913de-115">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="913de-116">MSH</span><span class="sxs-lookup"><span data-stu-id="913de-116">MSH</span></span>|<span data-ttu-id="913de-117">訊息標頭</span><span class="sxs-lookup"><span data-stu-id="913de-117">Message Header</span></span>|  
|<span data-ttu-id="913de-118">EVN</span><span class="sxs-lookup"><span data-stu-id="913de-118">EVN</span></span>|<span data-ttu-id="913de-119">事件類型</span><span class="sxs-lookup"><span data-stu-id="913de-119">Event Type</span></span>|  
|<span data-ttu-id="913de-120">PID</span><span class="sxs-lookup"><span data-stu-id="913de-120">PID</span></span>|<span data-ttu-id="913de-121">病患資訊</span><span class="sxs-lookup"><span data-stu-id="913de-121">Patient Information</span></span>|  
  
 <span data-ttu-id="913de-122">HL7 訊息有*訊息標頭*和*主體*。</span><span class="sxs-lookup"><span data-stu-id="913de-122">HL7 messages have a *message header* and *body*.</span></span> <span data-ttu-id="913de-123">MSH 區段會定義訊息的標頭，且所有其他類型的區段構成訊息的本文。</span><span class="sxs-lookup"><span data-stu-id="913de-123">The MSH segments define the header of the message and all other types of segments form the body of the message.</span></span>  
  
 <span data-ttu-id="913de-124">**資料欄位**</span><span class="sxs-lookup"><span data-stu-id="913de-124">**Data Fields**</span></span>  
  
 <span data-ttu-id="913de-125">資料欄位是發生訊息階層的深度 2 個字元的字串。</span><span class="sxs-lookup"><span data-stu-id="913de-125">A data field is a string of characters that occur at depth 2 of the message hierarchy.</span></span> <span data-ttu-id="913de-126">資料型別定義資料欄位： 簡單與複雜。</span><span class="sxs-lookup"><span data-stu-id="913de-126">Data types define data fields: Simple and Complex.</span></span>  
  
 <span data-ttu-id="913de-127">下列範例示範的 MSH 和 EVN 區段包含 MSH.1 和 EVN.1 資料欄位的階層式的訊息結構：</span><span class="sxs-lookup"><span data-stu-id="913de-127">The following example shows the hierarchical message structure of the MSH and EVN segments containing the MSH.1 and EVN.1 data fields:</span></span>  
  
 <span data-ttu-id="913de-128">MSH</span><span class="sxs-lookup"><span data-stu-id="913de-128">MSH</span></span>  
  
 <span data-ttu-id="913de-129">MSH.1</span><span class="sxs-lookup"><span data-stu-id="913de-129">MSH.1</span></span>  
  
 <span data-ttu-id="913de-130">EVN</span><span class="sxs-lookup"><span data-stu-id="913de-130">EVN</span></span>  
  
 <span data-ttu-id="913de-131">EVN.1</span><span class="sxs-lookup"><span data-stu-id="913de-131">EVN.1</span></span>  
  
 <span data-ttu-id="913de-132">**元件和子元件**</span><span class="sxs-lookup"><span data-stu-id="913de-132">**Components and Subcomponents**</span></span>  
  
 <span data-ttu-id="913de-133">元件和子元件進一步包含資料欄位內的資料。</span><span class="sxs-lookup"><span data-stu-id="913de-133">Components and subcomponents further contain the data within data fields.</span></span> <span data-ttu-id="913de-134">元件和子元件可以重複相同的欄位中。</span><span class="sxs-lookup"><span data-stu-id="913de-134">Components and subcomponents can repeat within the same field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="913de-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="913de-135">See Also</span></span>  
 <span data-ttu-id="913de-136">[處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="913de-136">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 <span data-ttu-id="913de-137">[訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="913de-137">[Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span></span>  
 [<span data-ttu-id="913de-138">使用 HL7 2.X 結構描述</span><span class="sxs-lookup"><span data-stu-id="913de-138">Using HL7 2.X Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)