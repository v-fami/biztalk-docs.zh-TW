---
title: "設計階段工具 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Adapter Framework
- BTAHL7, tools
- Starter Project
- Pipeline Designer
- BizTalk Editor
- Visual Studio Starter Project
- BizTalk Mapper
- design-time tools
- Orchestration Designer
ms.assetid: 709bd782-d2ad-49be-ba33-e957eba2a0cc
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e22272fd04dd3bf2461e4b9fef104657cf007fbb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="design-time-tools"></a><span data-ttu-id="12ec9-102">設計階段工具</span><span class="sxs-lookup"><span data-stu-id="12ec9-102">Design Time Tools</span></span>
<span data-ttu-id="12ec9-103">開發人員在[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 有一組內建的設計階段工具的使用[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="12ec9-103">Developers working on [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) have the use of a set of design time tools built into [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].</span></span> <span data-ttu-id="12ec9-104">這些工具已整合至[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="12ec9-104">These tools are integrated into [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="12ec9-105">如需有關[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]工具，請參閱[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="12ec9-105">For more information about [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] tools, see [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
## <a name="biztalk-editor"></a><span data-ttu-id="12ec9-106">BizTalk Editor (BizTalk 編輯器)</span><span class="sxs-lookup"><span data-stu-id="12ec9-106">BizTalk Editor</span></span>  
 <span data-ttu-id="12ec9-107">您可以使用 [BizTalk 編輯器] 來管理 HL7 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="12ec9-107">You use BizTalk Editor to manage HL7 XSD schemas.</span></span> <span data-ttu-id="12ec9-108">方案開發的您可以使用下列支援的結構描述範本 （為 XSD 檔案）：</span><span class="sxs-lookup"><span data-stu-id="12ec9-108">You can use the following supported schema templates (as XSD files) for your solution development:</span></span>  
  
-   <span data-ttu-id="12ec9-109">HL7: 2.1 （包括 37 事件）</span><span class="sxs-lookup"><span data-stu-id="12ec9-109">HL7: 2.1 (includes 37 events)</span></span>  
  
-   <span data-ttu-id="12ec9-110">HL7: 2.2 （包括 56 事件）</span><span class="sxs-lookup"><span data-stu-id="12ec9-110">HL7: 2.2 (includes 56 events)</span></span>  
  
-   <span data-ttu-id="12ec9-111">HL7: 2.3 （包括 182 事件）</span><span class="sxs-lookup"><span data-stu-id="12ec9-111">HL7: 2.3 (includes 182 events)</span></span>  
  
-   <span data-ttu-id="12ec9-112">HL7: 2.3.1 （包括 189 事件）</span><span class="sxs-lookup"><span data-stu-id="12ec9-112">HL7: 2.3.1 (includes 189 events)</span></span>  
  
-   <span data-ttu-id="12ec9-113">HL7: 2.4 （包括 288 事件）</span><span class="sxs-lookup"><span data-stu-id="12ec9-113">HL7: 2.4 (includes 288 events)</span></span>  
  
-   <span data-ttu-id="12ec9-114">HL7: 2.5 （包括大約 390 結構描述）</span><span class="sxs-lookup"><span data-stu-id="12ec9-114">HL7: 2.5 (includes approximately 390 schemas)</span></span>  
  
-   <span data-ttu-id="12ec9-115">HL7: 2.（V2.3.1 和 2.4 包括大約需要 450 的結構描述） 的 XML</span><span class="sxs-lookup"><span data-stu-id="12ec9-115">HL7: 2.XML (includes approximately 450 schemas for V2.3.1 and 2.4)</span></span>  
  
## <a name="biztalk-mapper"></a><span data-ttu-id="12ec9-116">BizTalk Mapper (BizTalk 對應工具)</span><span class="sxs-lookup"><span data-stu-id="12ec9-116">BizTalk Mapper</span></span>  
 <span data-ttu-id="12ec9-117">使用「BizTalk 對應工具」可以建立和自訂定義資料轉換的對應。</span><span class="sxs-lookup"><span data-stu-id="12ec9-117">You use BizTalk Mapper to create and customize maps that define data transformations.</span></span> <span data-ttu-id="12ec9-118">您可以使用 BizTalk 對應工具來對應的輸入和輸出的轉換[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]訊息類型。</span><span class="sxs-lookup"><span data-stu-id="12ec9-118">You use BizTalk Mapper to map transformations for both inbound and outbound [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] message types.</span></span>  
  
## <a name="biztalk-orchestration-designer"></a><span data-ttu-id="12ec9-119">BizTalk 協調流程設計師</span><span class="sxs-lookup"><span data-stu-id="12ec9-119">BizTalk Orchestration Designer</span></span>  
 <span data-ttu-id="12ec9-120">「BizTalk 協調流程設計師」可以設計和實作商務程序。</span><span class="sxs-lookup"><span data-stu-id="12ec9-120">You use BizTalk Orchestration Designer to design and implement business processes.</span></span>  
  
## <a name="biztalk-pipeline-designer"></a><span data-ttu-id="12ec9-121">BizTalk 管線設計師</span><span class="sxs-lookup"><span data-stu-id="12ec9-121">BizTalk Pipeline Designer</span></span>  
 <span data-ttu-id="12ec9-122">您可以使用 BizTalk 管線設計師 」 來建立及設定定義管線和處理步驟的連結。</span><span class="sxs-lookup"><span data-stu-id="12ec9-122">You use BizTalk Pipeline Designer to create and configure the pipelines that define and link processing steps.</span></span> <span data-ttu-id="12ec9-123">管線會將處理分成各個階段，並決定執行每個工作類別的順序。</span><span class="sxs-lookup"><span data-stu-id="12ec9-123">Pipelines divide processing into stages, and determine the sequence in which you perform each category of work.</span></span>  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="12ec9-124">接收和傳輸管線對於所有支援的 HL7 版本都提供。</span><span class="sxs-lookup"><span data-stu-id="12ec9-124"> provides both receive and transmit pipelines for all supported HL7 versions.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="12ec9-125">提供自訂 HL7 剖析器和解譯器/組合器元件的管線範本。</span><span class="sxs-lookup"><span data-stu-id="12ec9-125"> provides a pipeline template that has a custom HL7 parser and disassembler/assembler component.</span></span>  
  
## <a name="biztalk-adapter-framework"></a><span data-ttu-id="12ec9-126">BizTalk 配接器架構</span><span class="sxs-lookup"><span data-stu-id="12ec9-126">BizTalk Adapter Framework</span></span>  
 <span data-ttu-id="12ec9-127">「BizTalk 配接器架構」可以搭配端點配接器一起使用，以便與交易夥伴及應用程式進行整合。</span><span class="sxs-lookup"><span data-stu-id="12ec9-127">You use the BizTalk Adapter Framework with end-point adapters to integrate with partners and applications.</span></span>  
  
## <a name="visual-studio-starter-project"></a><span data-ttu-id="12ec9-128">Visual Studio 入門專案</span><span class="sxs-lookup"><span data-stu-id="12ec9-128">Visual Studio Starter Project</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="12ec9-129">包含[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]入門專案，您可以使用快速入門您 HL7 解決方案的實作。</span><span class="sxs-lookup"><span data-stu-id="12ec9-129"> includes the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Starter Project, which you can use to quick-start your HL7 solution implementation.</span></span> <span data-ttu-id="12ec9-130">入門專案都包含下列專案：</span><span class="sxs-lookup"><span data-stu-id="12ec9-130">The Starter Project includes the following projects:</span></span>  
  
-   <span data-ttu-id="12ec9-131">**空白**[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]**專案**。    </span><span class="sxs-lookup"><span data-stu-id="12ec9-131">**Empty**  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]  **Project**.</span></span> <span data-ttu-id="12ec9-132">不包含任何結構描述。</span><span class="sxs-lookup"><span data-stu-id="12ec9-132">Does not include any schemas.</span></span>  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="12ec9-133">**V2XCommon 專案**。</span><span class="sxs-lookup"><span data-stu-id="12ec9-133"> **V2XCommon Project**.</span></span> <span data-ttu-id="12ec9-134">包含標頭和通知結構描述。</span><span class="sxs-lookup"><span data-stu-id="12ec9-134">Includes header and acknowledgment schemas.</span></span>  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="12ec9-135">**V21Common 專案**。</span><span class="sxs-lookup"><span data-stu-id="12ec9-135"> **V21Common Project**.</span></span> <span data-ttu-id="12ec9-136">包含 HL7 2.1 版通用結構描述。</span><span class="sxs-lookup"><span data-stu-id="12ec9-136">Includes common schemas for HL7 version 2.1.</span></span>  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="12ec9-137">**V22Common 專案**。</span><span class="sxs-lookup"><span data-stu-id="12ec9-137"> **V22Common Project**.</span></span> <span data-ttu-id="12ec9-138">包含 HL7 2.2 版通用結構描述。</span><span class="sxs-lookup"><span data-stu-id="12ec9-138">Includes common schemas for HL7 version 2.2.</span></span>  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="12ec9-139">**V23Common 專案**。</span><span class="sxs-lookup"><span data-stu-id="12ec9-139"> **V23Common Project**.</span></span> <span data-ttu-id="12ec9-140">包含 HL7 版本 2.3 常見的結構描述。</span><span class="sxs-lookup"><span data-stu-id="12ec9-140">Includes common schemas for HL7 version 2.3.</span></span>  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="12ec9-141">**V231Common 專案**。</span><span class="sxs-lookup"><span data-stu-id="12ec9-141"> **V231Common Project**.</span></span> <span data-ttu-id="12ec9-142">包含 HL7 版本 2.3.1 常見的結構描述。</span><span class="sxs-lookup"><span data-stu-id="12ec9-142">Includes common schemas for HL7 version 2.3.1.</span></span>  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="12ec9-143">**V24Common 專案**。</span><span class="sxs-lookup"><span data-stu-id="12ec9-143"> **V24Common Project**.</span></span> <span data-ttu-id="12ec9-144">包含為 HL7 2.4 版通用結構描述。</span><span class="sxs-lookup"><span data-stu-id="12ec9-144">Includes common schemas for HL7 version 2.4.</span></span>  
  
-   <span data-ttu-id="12ec9-145">BTAHL7**V25Common 專案**。</span><span class="sxs-lookup"><span data-stu-id="12ec9-145">BTAHL7**V25Common Project**.</span></span> <span data-ttu-id="12ec9-146">包含 HL7 2.5 版通用結構描述。</span><span class="sxs-lookup"><span data-stu-id="12ec9-146">Includes common schemas for HL7 version 2.5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12ec9-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12ec9-147">See Also</span></span>  
 <span data-ttu-id="12ec9-148">[工具和功能](../../adapters-and-accelerators/accelerator-hl7/tools-and-features.md) </span><span class="sxs-lookup"><span data-stu-id="12ec9-148">[Tools and Features](../../adapters-and-accelerators/accelerator-hl7/tools-and-features.md) </span></span>  
 [<span data-ttu-id="12ec9-149">分析工具</span><span class="sxs-lookup"><span data-stu-id="12ec9-149">Analysis Tools</span></span>](../../adapters-and-accelerators/accelerator-hl7/analysis-tools2.md)