---
title: HL7 版本 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- HL7, standards
- HL7, versions
ms.assetid: 47299c6f-55c3-4434-8170-5ad73fe9a84c
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3806ed8db2272068ff60c6656b73cdf4a726bd9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005895"
---
# <a name="hl7-versions"></a><span data-ttu-id="68c98-102">HL7 版本</span><span class="sxs-lookup"><span data-stu-id="68c98-102">HL7 Versions</span></span>
<span data-ttu-id="68c98-103">HL7 第 2 版是一系列的密切相關的標準，而不是以單一標準。</span><span class="sxs-lookup"><span data-stu-id="68c98-103">HL7 Version 2 is a family of closely related standards rather than a single standard.</span></span> <span data-ttu-id="68c98-104">HL7 組織已設計為向上相容 HL7 間的版本相容性規則的應用程式透過這些標準。</span><span class="sxs-lookup"><span data-stu-id="68c98-104">The HL7 organization has designed these standards to be upwards compatible through the application of the HL7 inter-version compatibility rules.</span></span> <span data-ttu-id="68c98-105">這些規則會保證，第 2 版的範圍，內 HL7 版本的規則下定義的介面將仍可運作的後續版本定義中。</span><span class="sxs-lookup"><span data-stu-id="68c98-105">These rules guarantee that, within the confines of Version 2, an interface defined under the rules of an HL7 version will still function within the definition of successor versions.</span></span> <span data-ttu-id="68c98-106">以便接收系統將能夠接受來自較新版本的訊息，而不會破壞它的實作，並傳送系統將能夠繼續將訊息傳送給支援最新版本的接收者。</span><span class="sxs-lookup"><span data-stu-id="68c98-106">So that a receiving system will be able to accept messages from later versions without breaking its implementation and a sending system will be able to continue to send messages to receivers who support later versions.</span></span>  
  
 <span data-ttu-id="68c98-107">請務必請注意，Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]):</span><span class="sxs-lookup"><span data-stu-id="68c98-107">It is important to note that Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]):</span></span>  
  
- <span data-ttu-id="68c98-108">支援所有的即時 HL7 版本，透過 2.5 版的版本 2.1</span><span class="sxs-lookup"><span data-stu-id="68c98-108">Supports all live HL7 versions from Version 2.1 through Version 2.5</span></span>  
  
- <span data-ttu-id="68c98-109">提供對應 HL7 版本之間所需的功能，可讓多個版本，在單一站台的互通性</span><span class="sxs-lookup"><span data-stu-id="68c98-109">Provides the functionality needed to map between HL7 versions, and enables the interoperability of multiple versions at a single site</span></span>  
  
- <span data-ttu-id="68c98-110">支援的 Z 區段支援當地語系化和啟用替代的解讀方式之間的對應或使用標準的訊息</span><span class="sxs-lookup"><span data-stu-id="68c98-110">Supports localization by supporting Z segments, and enables mapping between alternate interpretations or uses of the standard messages</span></span>  
  
  <span data-ttu-id="68c98-111">請務必注意的傳訊標準版本之間的差異：</span><span class="sxs-lookup"><span data-stu-id="68c98-111">It is important to note the difference between the versions of the messaging standard:</span></span>  
  
- <span data-ttu-id="68c98-112">第 1 版檔可作為概念證明</span><span class="sxs-lookup"><span data-stu-id="68c98-112">Version 1 functioned as a proof of concept</span></span>  
  
- <span data-ttu-id="68c98-113">第 2 版提供來支援應用程式之間的訊息交換的訊息規格的集合</span><span class="sxs-lookup"><span data-stu-id="68c98-113">Version 2 provides a collection of message specifications to support message exchange between applications</span></span>  
  
- <span data-ttu-id="68c98-114">第 3 版將提供規格，以支援一系列的互通性需求，以模型為基礎的整合式的的集合</span><span class="sxs-lookup"><span data-stu-id="68c98-114">Version 3 will provide a model-based integrated set of specifications to support a range of interoperability needs</span></span>  
  
  <span data-ttu-id="68c98-115">基本上，第 2 版著重務實的方式，為使用者提供他們需要執行指定的工作，而第 3 版著重於以確保一致性及長期的擴充性主體做為訊息規格的規格整體。</span><span class="sxs-lookup"><span data-stu-id="68c98-115">In essence, Version 2 focuses on a pragmatic approach to providing users with the specifications they need to carry out specified tasks, while Version 3 focuses on assuring consistency and long-term extensibility for the body of message specifications taken as a whole.</span></span>  
  
  <span data-ttu-id="68c98-116">臨床文件架構會提供重要的延伸模組，HL7 標準，藉由引進的臨床文件使用的 XML 表示法的標準。</span><span class="sxs-lookup"><span data-stu-id="68c98-116">The Clinical Document Architecture provides a significant extension to the HL7 standard by introducing standards for the representation of clinical documents using XML.</span></span>  
  
  <span data-ttu-id="68c98-117">下表顯示 HL7 標準開發進程。</span><span class="sxs-lookup"><span data-stu-id="68c98-117">The following table shows the HL7 standard development progression.</span></span>  
  
|<span data-ttu-id="68c98-118">事件</span><span class="sxs-lookup"><span data-stu-id="68c98-118">Event</span></span>|<span data-ttu-id="68c98-119">Year</span><span class="sxs-lookup"><span data-stu-id="68c98-119">Year</span></span>|<span data-ttu-id="68c98-120">詳細資料</span><span class="sxs-lookup"><span data-stu-id="68c98-120">Details</span></span>|  
|-----------|----------|-------------|  
|<span data-ttu-id="68c98-121">HL7 成立</span><span class="sxs-lookup"><span data-stu-id="68c98-121">HL7 Founded</span></span>|<span data-ttu-id="68c98-122">1987</span><span class="sxs-lookup"><span data-stu-id="68c98-122">1987</span></span>|<span data-ttu-id="68c98-123">第一個會議中，在史丹佛，CA 中，包含 12 出席者。</span><span class="sxs-lookup"><span data-stu-id="68c98-123">The first meeting, in Stanford, CA, included 12 attendees.</span></span>|  
|<span data-ttu-id="68c98-124">V1.0</span><span class="sxs-lookup"><span data-stu-id="68c98-124">V1.0</span></span>|<span data-ttu-id="68c98-125">1987</span><span class="sxs-lookup"><span data-stu-id="68c98-125">1987</span></span>|<span data-ttu-id="68c98-126">向 HL7 plenary 會議的草稿。</span><span class="sxs-lookup"><span data-stu-id="68c98-126">Draft presented to HL7 plenary meeting.</span></span>|  
|<span data-ttu-id="68c98-127">V2.0</span><span class="sxs-lookup"><span data-stu-id="68c98-127">V2.0</span></span>|<span data-ttu-id="68c98-128">1988</span><span class="sxs-lookup"><span data-stu-id="68c98-128">1988</span></span>|<span data-ttu-id="68c98-129">向 HL7 plenary 會議的草稿。</span><span class="sxs-lookup"><span data-stu-id="68c98-129">Draft presented to HL7 plenary meeting.</span></span>|  
|<span data-ttu-id="68c98-130">發行的 V2.1</span><span class="sxs-lookup"><span data-stu-id="68c98-130">V2.1 published</span></span>|<span data-ttu-id="68c98-131">1990</span><span class="sxs-lookup"><span data-stu-id="68c98-131">1990</span></span>|<span data-ttu-id="68c98-132">第一個廣為實作的版本</span><span class="sxs-lookup"><span data-stu-id="68c98-132">The first widely implemented version</span></span>|  
|<span data-ttu-id="68c98-133">發行的 V2.2</span><span class="sxs-lookup"><span data-stu-id="68c98-133">V2.2 published</span></span>|<span data-ttu-id="68c98-134">1994</span><span class="sxs-lookup"><span data-stu-id="68c98-134">1994</span></span>||  
|<span data-ttu-id="68c98-135">2.3 版發行</span><span class="sxs-lookup"><span data-stu-id="68c98-135">V.2.3 published</span></span>|<span data-ttu-id="68c98-136">1997</span><span class="sxs-lookup"><span data-stu-id="68c98-136">1997</span></span>|<span data-ttu-id="68c98-137">ANSI 核准</span><span class="sxs-lookup"><span data-stu-id="68c98-137">ANSI approved</span></span>|  
|<span data-ttu-id="68c98-138">V2.3.1 發行</span><span class="sxs-lookup"><span data-stu-id="68c98-138">V2.3.1 published</span></span>|<span data-ttu-id="68c98-139">1999</span><span class="sxs-lookup"><span data-stu-id="68c98-139">1999</span></span>|<span data-ttu-id="68c98-140">ANSI 核准</span><span class="sxs-lookup"><span data-stu-id="68c98-140">ANSI approved</span></span>|  
|<span data-ttu-id="68c98-141">V2.4 發行</span><span class="sxs-lookup"><span data-stu-id="68c98-141">V2.4 published</span></span>|<span data-ttu-id="68c98-142">2000</span><span class="sxs-lookup"><span data-stu-id="68c98-142">2000</span></span>|<span data-ttu-id="68c98-143">ANSI 核准</span><span class="sxs-lookup"><span data-stu-id="68c98-143">ANSI approved</span></span>|  
|<span data-ttu-id="68c98-144">臨床文件架構</span><span class="sxs-lookup"><span data-stu-id="68c98-144">Clinical Document Architecture</span></span>|<span data-ttu-id="68c98-145">2000</span><span class="sxs-lookup"><span data-stu-id="68c98-145">2000</span></span>|<span data-ttu-id="68c98-146">ANSI 核准</span><span class="sxs-lookup"><span data-stu-id="68c98-146">ANSI approved</span></span>|  
|<span data-ttu-id="68c98-147">V2.5 發行</span><span class="sxs-lookup"><span data-stu-id="68c98-147">V2.5 published</span></span>|<span data-ttu-id="68c98-148">2003</span><span class="sxs-lookup"><span data-stu-id="68c98-148">2003</span></span>|<span data-ttu-id="68c98-149">完成內 HL7，ansi 提交進行核准的核准。</span><span class="sxs-lookup"><span data-stu-id="68c98-149">Completed approval within HL7, submitted to ANSI for approval.</span></span>|  
|<span data-ttu-id="68c98-150">進行中的 3.0 版</span><span class="sxs-lookup"><span data-stu-id="68c98-150">V3.0 in progress</span></span>|<span data-ttu-id="68c98-151">2003</span><span class="sxs-lookup"><span data-stu-id="68c98-151">2003</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="68c98-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68c98-152">See Also</span></span>  
 <span data-ttu-id="68c98-153">[處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="68c98-153">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 <span data-ttu-id="68c98-154">[使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="68c98-154">[Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md) </span></span>  
 <span data-ttu-id="68c98-155">[使用 HL7 2.xml 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="68c98-155">[Using HL7 2.XML Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md) </span></span>  
 <span data-ttu-id="68c98-156">[訊息模式](../../adapters-and-accelerators/accelerator-hl7/message-modes.md) </span><span class="sxs-lookup"><span data-stu-id="68c98-156">[Message Modes](../../adapters-and-accelerators/accelerator-hl7/message-modes.md) </span></span>  
 [<span data-ttu-id="68c98-157">HL7 傳訊</span><span class="sxs-lookup"><span data-stu-id="68c98-157">HL7 Messaging</span></span>](../../adapters-and-accelerators/accelerator-hl7/hl7-messaging.md)