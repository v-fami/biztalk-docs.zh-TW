---
title: 依階段的專案計劃建議 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- planning, performance
- performance, planning
ms.assetid: 422f05e3-5ad4-4f47-9be3-c229a20a6ef3
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb8886f3e52d347651630a4cafb716049fdf19fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22264950"
---
# <a name="project-planning-recommendations-by-phase"></a><span data-ttu-id="b8371-102">依階段的專案規劃建議</span><span class="sxs-lookup"><span data-stu-id="b8371-102">Project Planning Recommendations by Phase</span></span>
<span data-ttu-id="b8371-103">現今有許多軟體開發生命週期模型，皆有其各自的方法、優點及限制。</span><span class="sxs-lookup"><span data-stu-id="b8371-103">There are a number of software development lifecycle models in existence today, each with their own approaches, benefits, and limitations.</span></span> <span data-ttu-id="b8371-104">本節的目標是提供一組建議，協助您適當地規劃成功的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 開發專案。</span><span class="sxs-lookup"><span data-stu-id="b8371-104">The goal of this section is to provide a set of recommendations that will help you plan appropriately for a successful [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] development project.</span></span>  
  
 <span data-ttu-id="b8371-105">在此節中，我們會使用 Microsoft 廣泛採用的生命週期模型。</span><span class="sxs-lookup"><span data-stu-id="b8371-105">In this section, we use the lifecycle model employed broadly at Microsoft.</span></span> <span data-ttu-id="b8371-106">此模型為反覆與瀑布生命週期模型的組合。</span><span class="sxs-lookup"><span data-stu-id="b8371-106">This model is a combination of iterative and waterfall lifecycle models.</span></span>  
  
 <span data-ttu-id="b8371-107">在此模型中，共有五個階段，其界限會定義專案的一系列里程碑。</span><span class="sxs-lookup"><span data-stu-id="b8371-107">In this model, there are five phases whose boundaries define a sequential set of milestones for the project.</span></span> <span data-ttu-id="b8371-108">以下為各個階段 (依序執行)：</span><span class="sxs-lookup"><span data-stu-id="b8371-108">The phases, in order of execution, are as follows:</span></span>  
  
-   <span data-ttu-id="b8371-109">**需求**。</span><span class="sxs-lookup"><span data-stu-id="b8371-109">**Requirements**.</span></span> <span data-ttu-id="b8371-110">使用者需求是從定義建置標的之功能規格中擷取出來。</span><span class="sxs-lookup"><span data-stu-id="b8371-110">User requirements are captured in functional specifications that define what is to be built.</span></span>  
  
-   <span data-ttu-id="b8371-111">**設計**。</span><span class="sxs-lookup"><span data-stu-id="b8371-111">**Design**.</span></span> <span data-ttu-id="b8371-112">以功能需求為基礎，可以建立實體設計規格，進而實作原型，來確認設計概念和調查平台功能。</span><span class="sxs-lookup"><span data-stu-id="b8371-112">Based on the functional requirements, physical design specifications are created and prototyping is conducted to verify design ideas and investigate platform capabilities.</span></span>  
  
-   <span data-ttu-id="b8371-113">**實作**。</span><span class="sxs-lookup"><span data-stu-id="b8371-113">**Implementation**.</span></span> <span data-ttu-id="b8371-114">使用設計與功能規格，即可完成軟體程式編碼。</span><span class="sxs-lookup"><span data-stu-id="b8371-114">Using the design and functional specifications, the software coding is done.</span></span>  
  
-   <span data-ttu-id="b8371-115">**驗證**。</span><span class="sxs-lookup"><span data-stu-id="b8371-115">**Verification**.</span></span> <span data-ttu-id="b8371-116">這是測試軟體以確認它會依照規格來執行的程序。</span><span class="sxs-lookup"><span data-stu-id="b8371-116">This is the process of testing the software to verify that it performs according to the specifications.</span></span>  
  
-   <span data-ttu-id="b8371-117">**發行**。</span><span class="sxs-lookup"><span data-stu-id="b8371-117">**Release**.</span></span> <span data-ttu-id="b8371-118">軟體在經過完全確認之後，就會進行封裝，並準備向使用者發行。</span><span class="sxs-lookup"><span data-stu-id="b8371-118">After the software has been fully verified, it is packed and prepared for release to users.</span></span>  
  
 <span data-ttu-id="b8371-119">下圖顯示此專案計劃週期。</span><span class="sxs-lookup"><span data-stu-id="b8371-119">The following figure shows this project planning cycle.</span></span>  
  
 <span data-ttu-id="b8371-120">![依階段的專案計劃建議](../core/media/planningbyphase.gif "PlanningByPhase")</span><span class="sxs-lookup"><span data-stu-id="b8371-120">![Project Planning Recommendations by Phase](../core/media/planningbyphase.gif "PlanningByPhase")</span></span>  
  
 <span data-ttu-id="b8371-121">其中大多數 (若非全部) 階段的時間會有重疊，一般都是反覆的子階段。</span><span class="sxs-lookup"><span data-stu-id="b8371-121">Most, if not all, of these phases overlap in time and there are typically iterative sub-phases.</span></span> <span data-ttu-id="b8371-122">例如，通常完成產品功能子集的實作並開始驗證該子集時，已經在實作下一個功能子集。</span><span class="sxs-lookup"><span data-stu-id="b8371-122">For example, it is common to complete implementation of a sub-set of the product features and for verification to begin on that subset while implementation of the next sub set of features is under way.</span></span> <span data-ttu-id="b8371-123">因此，雖然本節中的建議與特定階段有關，但其意圖並非暗示它們不會同時發生，而是提供相關順序的一些概念，也就是應該在計劃時將這些建議納入考慮，並將之當成因素。</span><span class="sxs-lookup"><span data-stu-id="b8371-123">Therefore, while the recommendations in this section are associated with certain phases, the intention is not to imply that they cannot happen in parallel, but rather to give some idea of the relative order that the recommendations should be considered and factored into planning.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b8371-124">本節內容</span><span class="sxs-lookup"><span data-stu-id="b8371-124">In This Section</span></span>  
  
-   [<span data-ttu-id="b8371-125">需求階段建議</span><span class="sxs-lookup"><span data-stu-id="b8371-125">Requirements Phase Recommendations</span></span>](../core/requirements-phase-recommendations.md)  
  
-   [<span data-ttu-id="b8371-126">設計階段建議</span><span class="sxs-lookup"><span data-stu-id="b8371-126">Design Phase Recommendations</span></span>](../core/design-phase-recommendations.md)  
  
-   [<span data-ttu-id="b8371-127">實作階段建議</span><span class="sxs-lookup"><span data-stu-id="b8371-127">Implementation Phase Recommendations</span></span>](../core/implementation-phase-recommendations.md)  
  
-   [<span data-ttu-id="b8371-128">驗證階段建議</span><span class="sxs-lookup"><span data-stu-id="b8371-128">Verification Phase Recommendations</span></span>](../core/verification-phase-recommendations.md)  
  
-   [<span data-ttu-id="b8371-129">發行階段建議</span><span class="sxs-lookup"><span data-stu-id="b8371-129">Release Phase Recommendations</span></span>](../core/release-phase-recommendations.md)