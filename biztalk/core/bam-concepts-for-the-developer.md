---
title: BAM 開發人員概念 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c26d0aed-821c-4e1f-9cc9-9375a2ba28de
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e407121e9f71707b45f95e77a8520ed30df3b33
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230806"
---
# <a name="bam-concepts-for-the-developer"></a><span data-ttu-id="e7ac6-102">開發人員適用的 BAM 概念</span><span class="sxs-lookup"><span data-stu-id="e7ac6-102">BAM Concepts for the Developer</span></span>
<span data-ttu-id="e7ac6-103">身為 BAM 開發人員，您必須熟悉重要的 BAM 概念，例如活動、接續和參考等。</span><span class="sxs-lookup"><span data-stu-id="e7ac6-103">As a BAM developer, you need to be familiar with important BAM concepts, such as activities, continuations, and references.</span></span> <span data-ttu-id="e7ac6-104">您也應該瞭解追蹤和交易式處理兩者之間的差異。</span><span class="sxs-lookup"><span data-stu-id="e7ac6-104">You should also understand the differences between tracking and transactional processing.</span></span>  
  
## <a name="what-is-a-bam-activity"></a><span data-ttu-id="e7ac6-105">何謂 BAM 活動？</span><span class="sxs-lookup"><span data-stu-id="e7ac6-105">What Is a BAM Activity?</span></span>  
 <span data-ttu-id="e7ac6-106">BAM 活動是商務程序 (例如單一 PO) 中對某個項目而言有意義之資料內容的定義；</span><span class="sxs-lookup"><span data-stu-id="e7ac6-106">A BAM activity is the definition of what data is interesting for an item in the business process (such as a single PO).</span></span> <span data-ttu-id="e7ac6-107">它定義了 BAM 資料庫中的資料行。</span><span class="sxs-lookup"><span data-stu-id="e7ac6-107">It defines what columns are in the BAM database.</span></span>  
  
 <span data-ttu-id="e7ac6-108">活動執行個體代表商務中的工作單位，例如訂單或貸款申請。</span><span class="sxs-lookup"><span data-stu-id="e7ac6-108">An instance of an activity represents a unit of work in the business, such as a purchase order or a loan application.</span></span> <span data-ttu-id="e7ac6-109">活動則指定一份里程碑清單 (活動的歷程記錄) 和有意義的資料。</span><span class="sxs-lookup"><span data-stu-id="e7ac6-109">An activity specifies a list of milestones (the history of the activity) and data of interest.</span></span> <span data-ttu-id="e7ac6-110">活動執行個體在 BAM 主要匯入資料庫中是以單一資料列來表示。</span><span class="sxs-lookup"><span data-stu-id="e7ac6-110">An instance of an activity is manifested as a single row in the BAM Primary Import database.</span></span> <span data-ttu-id="e7ac6-111">該活動執行個體的任何資料項目都只有一個值。</span><span class="sxs-lookup"><span data-stu-id="e7ac6-111">There is one and only one value for any data item for that instance of the activity.</span></span>  
  
 <span data-ttu-id="e7ac6-112">活動可用來對商務使用者或資訊工作者顯示有關此工作單位的歷程記錄 (里程碑) 和資料。</span><span class="sxs-lookup"><span data-stu-id="e7ac6-112">An activity is used to show the milestones and data about this unit of work to the business end user, or information worker.</span></span> <span data-ttu-id="e7ac6-113">例如，BAM SDK 範例中定義的活動包含諸如「已付」及「傳送」等里程碑，以及如「總金額」等有意義的資料。</span><span class="sxs-lookup"><span data-stu-id="e7ac6-113">For example, the activity defined in the BAM SDK sample contains milestones such as “Paid” and "Send," as well data of interest such as “Total Amount.”</span></span>  
  
 <span data-ttu-id="e7ac6-114">BAM 活動通常會直接對應到商務程序，但是在高階抽象概念中，活動與您 IT 基礎結構的實際實作無關。</span><span class="sxs-lookup"><span data-stu-id="e7ac6-114">BAM activities often map directly to a business process, although as a high-level abstraction an activity is independent of the actual implementation of your IT infrastructure.</span></span>  
  
 <span data-ttu-id="e7ac6-115">身為開發人員的工作，就是只從特定活動內容中的實作公開相關的里程碑和資料。</span><span class="sxs-lookup"><span data-stu-id="e7ac6-115">Your job as a developer is to maintain this abstraction by exposing only the relevant milestones and data from the implementation in the context of a specific activity.</span></span>  
  
## <a name="what-is-a-continuation"></a><span data-ttu-id="e7ac6-116">何謂接續？</span><span class="sxs-lookup"><span data-stu-id="e7ac6-116">What Is a Continuation?</span></span>  
 <span data-ttu-id="e7ac6-117">接續提供有關下列資訊的 BAM 基礎結構指導：</span><span class="sxs-lookup"><span data-stu-id="e7ac6-117">Continuations provide guidance to the BAM infrastructure about the following information:</span></span>  
  
-   <span data-ttu-id="e7ac6-118">預期的事件發生順序</span><span class="sxs-lookup"><span data-stu-id="e7ac6-118">The order in which events are expected to occur</span></span>  
  
-   <span data-ttu-id="e7ac6-119">處理唯一識別碼任何變更的方法，此識別碼與事件項目相互關聯</span><span class="sxs-lookup"><span data-stu-id="e7ac6-119">A way to handle any change in the unique ID to which event items are correlated</span></span>  
  
 <span data-ttu-id="e7ac6-120">如需接續及其使用方式的詳細資訊，請參閱[Continuation 和 ContinuationID 節點](../core/continuation-and-continuationid-nodes.md)。</span><span class="sxs-lookup"><span data-stu-id="e7ac6-120">For more information about Continuations and how they are used, see [Continuation and ContinuationID Nodes](../core/continuation-and-continuationid-nodes.md).</span></span>  
  
## <a name="what-is-a-reference"></a><span data-ttu-id="e7ac6-121">何謂參考？</span><span class="sxs-lookup"><span data-stu-id="e7ac6-121">What Is a Reference?</span></span>  
 <span data-ttu-id="e7ac6-122">參考 (也稱為相關活動) 會指定活動與其他項目之間的關係。</span><span class="sxs-lookup"><span data-stu-id="e7ac6-122">A reference (also known as a related activity) specifies a relationship between an activity and some other item.</span></span> <span data-ttu-id="e7ac6-123">相關項目的範例包括其他項目或文件位置。</span><span class="sxs-lookup"><span data-stu-id="e7ac6-123">Examples of items that can be related are another activity or a document location.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7ac6-124">當您將某個活動指定為相關活動時，如果相關活動尚未完成，並不會妨礙系統完成目前的活動；這一點與接續活動不同。</span><span class="sxs-lookup"><span data-stu-id="e7ac6-124">When you specify an activity as a related activity, the current activity is not, unlike a continuation activity, precluded from completing if the related activity has not completed.</span></span>  
  
## <a name="tracking-and-transactional-processing"></a><span data-ttu-id="e7ac6-125">追蹤和交易式處理</span><span class="sxs-lookup"><span data-stu-id="e7ac6-125">Tracking and Transactional Processing</span></span>  
 <span data-ttu-id="e7ac6-126">撰寫 BAM 程式碼可以讓您控制追蹤資料的方式，也就是透過追蹤或交易式處理來進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="e7ac6-126">Writing code for BAM gives you control of the way data is tracked, that is, through tracking or transactional processing.</span></span> <span data-ttu-id="e7ac6-127">根據預設，BAM 會為追蹤和處理指定同等的重要性。</span><span class="sxs-lookup"><span data-stu-id="e7ac6-127">By default, BAM assigns equal importance to tracking and processing.</span></span> <span data-ttu-id="e7ac6-128">這表示如果追蹤功能或交易程序失敗，兩者都將無法繼續執行。</span><span class="sxs-lookup"><span data-stu-id="e7ac6-128">This means that if either the tracking function or the transaction process fails, neither is allowed to proceed.</span></span> <span data-ttu-id="e7ac6-129">追蹤資料庫中不會記錄任何內容，而交易也會回復。</span><span class="sxs-lookup"><span data-stu-id="e7ac6-129">Nothing is recorded in the tracking database and the transaction is rolled back.</span></span> <span data-ttu-id="e7ac6-130">這可能不是您的解決方案慣用的追蹤方法。</span><span class="sxs-lookup"><span data-stu-id="e7ac6-130">This may not be the preferred method of tracking for your solution.</span></span> <span data-ttu-id="e7ac6-131">透過開發 BAM，您可以決定追蹤或交易式處理何者優先順序較高。</span><span class="sxs-lookup"><span data-stu-id="e7ac6-131">By developing for BAM you can determine whether tracking or transactional processing takes precedence.</span></span>  
  
 <span data-ttu-id="e7ac6-132">下表說明在 BAM 中追蹤資料的模式。</span><span class="sxs-lookup"><span data-stu-id="e7ac6-132">The following table describes the modes of tracking data in BAM.</span></span>  
  
|<span data-ttu-id="e7ac6-133">狀況</span><span class="sxs-lookup"><span data-stu-id="e7ac6-133">Scenario</span></span>|<span data-ttu-id="e7ac6-134">[描述]</span><span class="sxs-lookup"><span data-stu-id="e7ac6-134">Descriptions</span></span>|  
|--------------|------------------|  
|<span data-ttu-id="e7ac6-135">追蹤優先於處理</span><span class="sxs-lookup"><span data-stu-id="e7ac6-135">Tracking Over Processing</span></span>|<span data-ttu-id="e7ac6-136">如果處理程序成功，則寫入追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="e7ac6-136">If the process succeeds, write tracking information.</span></span><br /><br /> <span data-ttu-id="e7ac6-137">如果處理程序失敗，則寫入有關失敗的資訊。</span><span class="sxs-lookup"><span data-stu-id="e7ac6-137">If the process fails, write information about the failure.</span></span>|  
|<span data-ttu-id="e7ac6-138">處理等同於追蹤</span><span class="sxs-lookup"><span data-stu-id="e7ac6-138">Processing Equal to Tracking</span></span>|<span data-ttu-id="e7ac6-139">如果追蹤或處理失敗，則回復所有動作。</span><span class="sxs-lookup"><span data-stu-id="e7ac6-139">If either tracking or processing fails, roll back everything.</span></span>|  
|<span data-ttu-id="e7ac6-140">處理優先於追蹤</span><span class="sxs-lookup"><span data-stu-id="e7ac6-140">Processing Over Tracking</span></span>|<span data-ttu-id="e7ac6-141">如果處理程序成功但追蹤功能失敗，則繼續處理。</span><span class="sxs-lookup"><span data-stu-id="e7ac6-141">If the process succeeds and the tracking function fails, continue processing.</span></span>|