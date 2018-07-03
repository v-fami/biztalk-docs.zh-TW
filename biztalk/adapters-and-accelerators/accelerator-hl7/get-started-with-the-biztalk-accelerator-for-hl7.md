---
title: 開始使用 BizTalk Accelerator for HL7 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- btahl7.configurationexplorer.gettingstarted
helpviewer_keywords:
- BizTalk Accelerator for HL7
- BizTalk Accelerator for HL7, getting started
- getting started
ms.assetid: e842d501-2037-4fd6-a518-d29b25877250
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 14559d888bc020a5772fbbc6eddf3ba4fdb4beb0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989599"
---
# <a name="get-started-with-the-biztalk-accelerator-for-hl7"></a><span data-ttu-id="3b7eb-102">開始使用 BizTalk Accelerator for HL7</span><span class="sxs-lookup"><span data-stu-id="3b7eb-102">Get started with the BizTalk Accelerator for HL7</span></span>
<span data-ttu-id="3b7eb-103">使用 Microsoft [!INCLUDE[HL7_CurrentVersion_FirstRef_md](../../includes/hl7-currentversion-firstref-md.md)]，您可以開發醫療保健電腦系統之間的商務程序。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-103">Using the Microsoft [!INCLUDE[HL7_CurrentVersion_FirstRef_md](../../includes/hl7-currentversion-firstref-md.md)], you can develop business processes between your health care computer systems.</span></span> <span data-ttu-id="3b7eb-104">使用[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]，開發人員、 IT 專業人員和介面分析師可在通用的環境來開發跨醫療保健應用程式的端對端整合的 BTAHL7 架構解決方案。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-104">By using [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)], developers, IT professionals, and interface analysts can work in a common environment to develop end-to-end integrated BTAHL7-based solutions across health care applications.</span></span>  
  
 <span data-ttu-id="3b7eb-105">更具體來說，與[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]您可以：</span><span class="sxs-lookup"><span data-stu-id="3b7eb-105">More specifically, with [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] you can:</span></span>  
  
- <span data-ttu-id="3b7eb-106">**簡化醫療保健應用程式整合**。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-106">**Simplify health care application integration**.</span></span> <span data-ttu-id="3b7eb-107">建置、 管理及追蹤分散式的商務程序使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]開發環境。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-107">Build, manage, and track distributed business processes using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] development environment.</span></span>  
  
- <span data-ttu-id="3b7eb-108">**標準化醫療應用程式之間的臨床資料交換**。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-108">**Standardize clinical data interchange between medical applications**.</span></span> <span data-ttu-id="3b7eb-109">轉換現有的資料傳輸至應用程式之間[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]標準。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-109">Transform existing data transmission between applications to the [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] standard.</span></span>  
  
- <span data-ttu-id="3b7eb-110">**提高效率**。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-110">**Increase efficiency**.</span></span> <span data-ttu-id="3b7eb-111">使用最少的手動介入的醫療應用程式之間的所有通訊程序都自動化。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-111">Automate all communication processes between medical applications with minimal manual intervention.</span></span>  

<span data-ttu-id="3b7eb-112">本節提供有關您可以使用的角色專屬資訊[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]和[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]以便在醫院和醫護競技場，自動化企業對企業的醫療保健解決方案的企業應用程式整合 (EAI).</span><span class="sxs-lookup"><span data-stu-id="3b7eb-112">This section provides role-specific information about how you can use [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] and [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] to facilitate Enterprise Application Integration (EAI) within hospitals and the healthcare arena to automate business-to-business healthcare solutions.</span></span>  
  
[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]<span data-ttu-id="3b7eb-113"> 提供每種方案中的四個不同的案例教學課程的格式。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-113"> provides four separate scenarios in tutorial format for each type of solution.</span></span> <span data-ttu-id="3b7eb-114">這些教學課程之前，您應該了解中的基本概念[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]，以及工具和程序，才能開始建置解決方案[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-114">Before you begin these tutorials, you should understand the fundamental concepts in [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)], and the tools and processes that are required to start building solutions with [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)].</span></span>  

> [!TIP] 
> <span data-ttu-id="3b7eb-115">這些課程中，開始之前[深入了解 HL7 加速器以及可用的 BizTalk 工具](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md)。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-115">Before you begin these lessons, [learn about the HL7 accelerator and the BizTalk tools available](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md).</span></span>  
  
 <span data-ttu-id="3b7eb-116">以下描述提供大致的了解每個[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]教學課程。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-116">The following descriptions provide a general understanding of each [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] tutorial.</span></span>  
  
## <a name="end-to-end-tutorial"></a><span data-ttu-id="3b7eb-117">端對端教學課程</span><span class="sxs-lookup"><span data-stu-id="3b7eb-117">End-to-End tutorial</span></span>  
 <span data-ttu-id="3b7eb-118">[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]端對端教學課程會將您提供詳細的步驟，以便在 「 訂閱者 」 和 「 發行者 」 的案例中的商務程序。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-118">The [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] End-to-End tutorial provides you with detailed steps to facilitate business processes in a subscriber and publisher scenario.</span></span> <span data-ttu-id="3b7eb-119">此案例中是以 「 發行者 」，例如許可出院和傳輸系統會傳送訊息至特定的訂閱者的情況。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-119">This scenario is a situation in which a publisher, for example, an Admissions Discharge and Transfer system sends a message to specific subscribers.</span></span>  
  
 <span data-ttu-id="3b7eb-120">訊息將路由傳送至[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]介面引擎，進而接收程序，驗證、 重新格式化，並接著會將訊息路由至訂閱者。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-120">The message routes to the [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] Interface Engine, which in turn receives, processes, validates, reformats, and then routes the message to the subscribers.</span></span> <span data-ttu-id="3b7eb-121">在此案例中的 「 訂閱者 」 是醫院資訊系統和 Pharmacy 系統。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-121">The subscribers in this scenario are a Hospital Information System and a Pharmacy System.</span></span>  
  
 <span data-ttu-id="3b7eb-122">此案例使用檔案和最小的較低層通訊協定 (MLLP) 配接器類型。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-122">This scenario uses both File and Minimal Lower Layer Protocol (MLLP) adapter types.</span></span> <span data-ttu-id="3b7eb-123">不需要留意的 「 訂閱者 」，「 發行者 」 和[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]介面引擎處理訊息之後將適當的通知傳送到 「 發行者 」。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-123">The publisher does not need to be aware of the subscribers, and the [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] Interface Engine sends an appropriate acknowledgement to the publisher after processing the message.</span></span>  
  
## <a name="interrogative-tutorial"></a><span data-ttu-id="3b7eb-124">詢問式教學課程</span><span class="sxs-lookup"><span data-stu-id="3b7eb-124">Interrogative tutorial</span></span>  
 <span data-ttu-id="3b7eb-125">[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]詢問式教學課程為您提供詳細的步驟來實作組織內的子系統之間的查詢回應系統。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-125">The [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] Interrogative tutorial provides you with detailed steps for implementing a query-response system between sub-systems within an organization.</span></span> <span data-ttu-id="3b7eb-126">在此案例中，的營運 (LOB) 應用程式中的許可，出院，，和傳輸系統會將查詢傳送至醫院資訊系統，以取得病患的實驗室結果。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-126">In this scenario, a line-of-business (LOB) application in the Admissions, Discharge, and Transfer system sends a query to the Hospital Information System to obtain patient lab results.</span></span> <span data-ttu-id="3b7eb-127">醫院資訊系統收到查詢之後，它會傳送回系統發出查詢要求的資料。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-127">After the Hospital Information System receives the query, it sends the requested data back to the system that issued the query.</span></span>  
  
 <span data-ttu-id="3b7eb-128">此案例會使用 MLLP 做為傳輸通訊協定的所有訊息，包括通知。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-128">This scenario uses MLLP as the transport protocol for all messages, including acknowledgments.</span></span>  
  
## <a name="message-enrichment-tutorial"></a><span data-ttu-id="3b7eb-129">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="3b7eb-129">Message enrichment tutorial</span></span>  
 <span data-ttu-id="3b7eb-130">[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]擴充教學課程會將您提供詳細的步驟來解決特定商務問題： 訊息豐富 」 案例。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-130">The [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] Enrichment tutorial provides you with detailed steps to solve a particular business problem: the message-enrichment scenario.</span></span> <span data-ttu-id="3b7eb-131">訊息豐富 」 案例是您不必加入或擴充的情況下，不符合規範 HL7 和/或不完整的訊息。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-131">The message-enrichment scenario is a situation in which you have to add to, or enrich, a message that is not HL7-compliant and/or is incomplete.</span></span> <span data-ttu-id="3b7eb-132">應用程式，例如病患註冊應用程式，或會填入來自 XML 資料的訊息可能會發生這種情況下[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-132">This situation can occur with an application, such as a patient-registration application, or when you are populating a message with XML data from [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="3b7eb-133">您可以在訊息豐富 」 案例中，擷取的訊息[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]，並提供任何遺漏的資料，例如從病患記錄資料庫。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-133">In the message enrichment scenario, you capture the messages with [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)], and provide any missing data, for example, from a patient-records database.</span></span> <span data-ttu-id="3b7eb-134">然後將訊息轉換，並將它傳送至一個實驗室、 保險或使用 MLLP 配接器任何舊版的特定業務 (LOB) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-134">You then convert the message and send it to a laboratory, insurance, or any legacy line-of-business (LOB) application using the MLLP adapter.</span></span>  
  
## <a name="batching-tutorial"></a><span data-ttu-id="3b7eb-135">批次處理教學課程</span><span class="sxs-lookup"><span data-stu-id="3b7eb-135">Batching tutorial</span></span>  
 <span data-ttu-id="3b7eb-136">[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]批次處理教學課程會將您提供詳細的步驟，以接收和傳送批次的訊息。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-136">The [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] Batching tutorial provides you with detailed steps to receive and send batched messages.</span></span> <span data-ttu-id="3b7eb-137">批次處理為單一複合訊息包含接收和/或傳送一組個別的訊息 （或通知）。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-137">Batching involves receiving and/or sending a group of individual messages (or acknowledgments) as a single composite message.</span></span>  
  
[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]<span data-ttu-id="3b7eb-138"> 支援下列三個訊息批次處理案例：</span><span class="sxs-lookup"><span data-stu-id="3b7eb-138"> supports the following three message batching scenarios:</span></span>  
  
- <span data-ttu-id="3b7eb-139">**片段化的輸入批次**。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-139">**Fragmented inbound batch**.</span></span> <span data-ttu-id="3b7eb-140">在此案例中，[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]接收 HL7 訊息批次中，並再將個別的訊息路由至目的系統。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-140">In this scenario, [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] receives an HL7 message batch, and then routes the individual messages to the destination system.</span></span>  
  
- <span data-ttu-id="3b7eb-141">**在批次 / 批次出**。[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]接收 HL7 訊息批次驗證個別訊息的批次內，然後將批次訊息路由傳送至目的地系統。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-141">**Batch in/batch out**. [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] receives an HL7 message batch, verifies the individual messages within the batch, and then routes the message batch to the destination system.</span></span>  
  
- <span data-ttu-id="3b7eb-142">**建立批次 （或輸出批次處理）**。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-142">**Create batch (or outbound batching)**.</span></span> [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]<span data-ttu-id="3b7eb-143"> 接收個別的訊息，批次處理它們之前先路由傳送至目的地系統。</span><span class="sxs-lookup"><span data-stu-id="3b7eb-143"> receives individual messages and batches them before routing them to the destination system.</span></span>  
  
## <a name="tutorial-links"></a><span data-ttu-id="3b7eb-144">教學課程的連結</span><span class="sxs-lookup"><span data-stu-id="3b7eb-144">Tutorial links</span></span>  
  
-   [<span data-ttu-id="3b7eb-145">端對端教學課程</span><span class="sxs-lookup"><span data-stu-id="3b7eb-145">End-to-End Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md)  
  
-   [<span data-ttu-id="3b7eb-146">詢問式教學課程</span><span class="sxs-lookup"><span data-stu-id="3b7eb-146">Interrogative Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md)  
  
-   [<span data-ttu-id="3b7eb-147">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="3b7eb-147">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)  
  
-   [<span data-ttu-id="3b7eb-148">批次處理教學課程</span><span class="sxs-lookup"><span data-stu-id="3b7eb-148">Batching Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md)
  
## <a name="see-also"></a><span data-ttu-id="3b7eb-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b7eb-149">See also</span></span>
  
[<span data-ttu-id="3b7eb-150">行動不便人士的協助工具</span><span class="sxs-lookup"><span data-stu-id="3b7eb-150">Accessibility for People with Disabilities</span></span>](../../adapters-and-accelerators/accelerator-hl7/accessibility-for-people-with-disabilities5.md)