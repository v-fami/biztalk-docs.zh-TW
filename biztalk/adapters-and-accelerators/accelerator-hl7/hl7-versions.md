---
title: "HL7 版本 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HL7, standards
- HL7, versions
ms.assetid: 47299c6f-55c3-4434-8170-5ad73fe9a84c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c7edcfa6c44467c0660efd8a9b4b02df7010de6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="hl7-versions"></a><span data-ttu-id="175cf-102">HL7 版本</span><span class="sxs-lookup"><span data-stu-id="175cf-102">HL7 Versions</span></span>
<span data-ttu-id="175cf-103">HL7 版本 2 是系列密切相關的標準，而不是單一標準。</span><span class="sxs-lookup"><span data-stu-id="175cf-103">HL7 Version 2 is a family of closely related standards rather than a single standard.</span></span> <span data-ttu-id="175cf-104">HL7 組織已設計為透過 HL7 間的版本相容性規則的應用程式向上相容這些標準。</span><span class="sxs-lookup"><span data-stu-id="175cf-104">The HL7 organization has designed these standards to be upwards compatible through the application of the HL7 inter-version compatibility rules.</span></span> <span data-ttu-id="175cf-105">這些規則可保證，在第 2 版的範圍內，定義 HL7 版本的規則 下的介面仍舊會執行後續版本的定義內。</span><span class="sxs-lookup"><span data-stu-id="175cf-105">These rules guarantee that, within the confines of Version 2, an interface defined under the rules of an HL7 version will still function within the definition of successor versions.</span></span> <span data-ttu-id="175cf-106">如此將無法接受來自較新版本的訊息，而不會中斷它的實作，並傳送接收端系統系統可以繼續將訊息傳送給接收者者支援更新版本。</span><span class="sxs-lookup"><span data-stu-id="175cf-106">So that a receiving system will be able to accept messages from later versions without breaking its implementation and a sending system will be able to continue to send messages to receivers who support later versions.</span></span>  
  
 <span data-ttu-id="175cf-107">請務必注意[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]):</span><span class="sxs-lookup"><span data-stu-id="175cf-107">It is important to note that [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]):</span></span>  
  
-   <span data-ttu-id="175cf-108">支援所有的即時 HL7 版本從版本 2.1 透過 2.5 版</span><span class="sxs-lookup"><span data-stu-id="175cf-108">Supports all live HL7 versions from Version 2.1 through Version 2.5</span></span>  
  
-   <span data-ttu-id="175cf-109">提供對應 HL7 版本之間所需的功能，並可在一個站台的多個版本的互通性</span><span class="sxs-lookup"><span data-stu-id="175cf-109">Provides the functionality needed to map between HL7 versions, and enables the interoperability of multiple versions at a single site</span></span>  
  
-   <span data-ttu-id="175cf-110">支援當地語系化支援 Z 區段並啟用替代的解讀方式之間的對應或使用標準的訊息</span><span class="sxs-lookup"><span data-stu-id="175cf-110">Supports localization by supporting Z segments, and enables mapping between alternate interpretations or uses of the standard messages</span></span>  
  
 <span data-ttu-id="175cf-111">請務必注意的傳訊標準版本之間的差異：</span><span class="sxs-lookup"><span data-stu-id="175cf-111">It is important to note the difference between the versions of the messaging standard:</span></span>  
  
-   <span data-ttu-id="175cf-112">第 1 版的作用為概念證明</span><span class="sxs-lookup"><span data-stu-id="175cf-112">Version 1 functioned as a proof of concept</span></span>  
  
-   <span data-ttu-id="175cf-113">第 2 版提供集合，以支援應用程式之間的訊息交換的訊息規格</span><span class="sxs-lookup"><span data-stu-id="175cf-113">Version 2 provides a collection of message specifications to support message exchange between applications</span></span>  
  
-   <span data-ttu-id="175cf-114">第 3 版會提供以模型為基礎組整合的規格，以支援較大範圍的互通性需求</span><span class="sxs-lookup"><span data-stu-id="175cf-114">Version 3 will provide a model-based integrated set of specifications to support a range of interoperability needs</span></span>  
  
 <span data-ttu-id="175cf-115">第 2 版本質上而言，著重於實用的方法，以提供使用者執行指定工作，而第 3 版著重於以確保一致性和長期的擴充性的訊息規格來做為主體所需的規格整數。</span><span class="sxs-lookup"><span data-stu-id="175cf-115">In essence, Version 2 focuses on a pragmatic approach to providing users with the specifications they need to carry out specified tasks, while Version 3 focuses on assuring consistency and long-term extensibility for the body of message specifications taken as a whole.</span></span>  
  
 <span data-ttu-id="175cf-116">臨床文件架構會提供藉由引進臨床文件使用的 XML 表示的標準 HL7 標準的大幅擴充功能。</span><span class="sxs-lookup"><span data-stu-id="175cf-116">The Clinical Document Architecture provides a significant extension to the HL7 standard by introducing standards for the representation of clinical documents using XML.</span></span>  
  
 <span data-ttu-id="175cf-117">下表顯示 HL7 標準開發進程。</span><span class="sxs-lookup"><span data-stu-id="175cf-117">The following table shows the HL7 standard development progression.</span></span>  
  
|<span data-ttu-id="175cf-118">事件</span><span class="sxs-lookup"><span data-stu-id="175cf-118">Event</span></span>|<span data-ttu-id="175cf-119">Year</span><span class="sxs-lookup"><span data-stu-id="175cf-119">Year</span></span>|<span data-ttu-id="175cf-120">詳細資料</span><span class="sxs-lookup"><span data-stu-id="175cf-120">Details</span></span>|  
|-----------|----------|-------------|  
|<span data-ttu-id="175cf-121">HL7 所建構</span><span class="sxs-lookup"><span data-stu-id="175cf-121">HL7 Founded</span></span>|<span data-ttu-id="175cf-122">1987</span><span class="sxs-lookup"><span data-stu-id="175cf-122">1987</span></span>|<span data-ttu-id="175cf-123">在第一個會議 Stanford，CA，包含 12 出席者。</span><span class="sxs-lookup"><span data-stu-id="175cf-123">The first meeting, in Stanford, CA, included 12 attendees.</span></span>|  
|<span data-ttu-id="175cf-124">V1.0</span><span class="sxs-lookup"><span data-stu-id="175cf-124">V1.0</span></span>|<span data-ttu-id="175cf-125">1987</span><span class="sxs-lookup"><span data-stu-id="175cf-125">1987</span></span>|<span data-ttu-id="175cf-126">提供給 HL7 plenary 會議的草稿。</span><span class="sxs-lookup"><span data-stu-id="175cf-126">Draft presented to HL7 plenary meeting.</span></span>|  
|<span data-ttu-id="175cf-127">V2.0</span><span class="sxs-lookup"><span data-stu-id="175cf-127">V2.0</span></span>|<span data-ttu-id="175cf-128">1988</span><span class="sxs-lookup"><span data-stu-id="175cf-128">1988</span></span>|<span data-ttu-id="175cf-129">提供給 HL7 plenary 會議的草稿。</span><span class="sxs-lookup"><span data-stu-id="175cf-129">Draft presented to HL7 plenary meeting.</span></span>|  
|<span data-ttu-id="175cf-130">V2.1 發行</span><span class="sxs-lookup"><span data-stu-id="175cf-130">V2.1 published</span></span>|<span data-ttu-id="175cf-131">1990</span><span class="sxs-lookup"><span data-stu-id="175cf-131">1990</span></span>|<span data-ttu-id="175cf-132">第一個廣泛版本</span><span class="sxs-lookup"><span data-stu-id="175cf-132">The first widely implemented version</span></span>|  
|<span data-ttu-id="175cf-133">V2.2 發行</span><span class="sxs-lookup"><span data-stu-id="175cf-133">V2.2 published</span></span>|<span data-ttu-id="175cf-134">1994</span><span class="sxs-lookup"><span data-stu-id="175cf-134">1994</span></span>||  
|<span data-ttu-id="175cf-135">V.2.3 發行</span><span class="sxs-lookup"><span data-stu-id="175cf-135">V.2.3 published</span></span>|<span data-ttu-id="175cf-136">1997</span><span class="sxs-lookup"><span data-stu-id="175cf-136">1997</span></span>|<span data-ttu-id="175cf-137">ANSI 核准</span><span class="sxs-lookup"><span data-stu-id="175cf-137">ANSI approved</span></span>|  
|<span data-ttu-id="175cf-138">V2.3.1 發行</span><span class="sxs-lookup"><span data-stu-id="175cf-138">V2.3.1 published</span></span>|<span data-ttu-id="175cf-139">1999</span><span class="sxs-lookup"><span data-stu-id="175cf-139">1999</span></span>|<span data-ttu-id="175cf-140">ANSI 核准</span><span class="sxs-lookup"><span data-stu-id="175cf-140">ANSI approved</span></span>|  
|<span data-ttu-id="175cf-141">V2.4 發行</span><span class="sxs-lookup"><span data-stu-id="175cf-141">V2.4 published</span></span>|<span data-ttu-id="175cf-142">2000</span><span class="sxs-lookup"><span data-stu-id="175cf-142">2000</span></span>|<span data-ttu-id="175cf-143">ANSI 核准</span><span class="sxs-lookup"><span data-stu-id="175cf-143">ANSI approved</span></span>|  
|<span data-ttu-id="175cf-144">臨床文件架構</span><span class="sxs-lookup"><span data-stu-id="175cf-144">Clinical Document Architecture</span></span>|<span data-ttu-id="175cf-145">2000</span><span class="sxs-lookup"><span data-stu-id="175cf-145">2000</span></span>|<span data-ttu-id="175cf-146">ANSI 核准</span><span class="sxs-lookup"><span data-stu-id="175cf-146">ANSI approved</span></span>|  
|<span data-ttu-id="175cf-147">2.5 版發行</span><span class="sxs-lookup"><span data-stu-id="175cf-147">V2.5 published</span></span>|<span data-ttu-id="175cf-148">2003</span><span class="sxs-lookup"><span data-stu-id="175cf-148">2003</span></span>|<span data-ttu-id="175cf-149">完成內 HL7，為 ANSI 所提交核准的核准。</span><span class="sxs-lookup"><span data-stu-id="175cf-149">Completed approval within HL7, submitted to ANSI for approval.</span></span>|  
|<span data-ttu-id="175cf-150">V3.0 正在進行中</span><span class="sxs-lookup"><span data-stu-id="175cf-150">V3.0 in progress</span></span>|<span data-ttu-id="175cf-151">2003</span><span class="sxs-lookup"><span data-stu-id="175cf-151">2003</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="175cf-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="175cf-152">See Also</span></span>  
 <span data-ttu-id="175cf-153">[處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="175cf-153">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 <span data-ttu-id="175cf-154">[使用 HL7 2.X 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="175cf-154">[Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md) </span></span>  
 <span data-ttu-id="175cf-155">[使用 HL7 2.XML 結構描述](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="175cf-155">[Using HL7 2.XML Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md) </span></span>  
 <span data-ttu-id="175cf-156">[訊息模式](../../adapters-and-accelerators/accelerator-hl7/message-modes.md) </span><span class="sxs-lookup"><span data-stu-id="175cf-156">[Message Modes](../../adapters-and-accelerators/accelerator-hl7/message-modes.md) </span></span>  
 [<span data-ttu-id="175cf-157">HL7 訊息</span><span class="sxs-lookup"><span data-stu-id="175cf-157">HL7 Messaging</span></span>](../../adapters-and-accelerators/accelerator-hl7/hl7-messaging.md)