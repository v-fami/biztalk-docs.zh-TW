---
title: "需求階段建議 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b510313-c3a7-42bc-9c9b-336c927a5d4a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d945e50d9c7b8f0a9feae5e0f93a4766d108c695
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="requirements-phase-recommendations"></a><span data-ttu-id="5cae8-102">需求階段建議</span><span class="sxs-lookup"><span data-stu-id="5cae8-102">Requirements Phase Recommendations</span></span>
<span data-ttu-id="5cae8-103">與需求階段有關的主要工作事項是制定需求規格，或者說，制定一份包含附帶效能目標之需求的功能規格。</span><span class="sxs-lookup"><span data-stu-id="5cae8-103">The primary deliverable associated with the requirements phase is a requirements specification, or a functional specification that includes requirements including performance goals.</span></span> <span data-ttu-id="5cae8-104">在決定這些目標時，必須將系統的使用者和企業主一併列入考慮，才能取得精確的效能分析資料。</span><span class="sxs-lookup"><span data-stu-id="5cae8-104">It is very important to involve the end-users and business owners of the system when determining these goals to assure that an accurate profile for performance is derived.</span></span>  
  
## <a name="establish-performance-criteria"></a><span data-ttu-id="5cae8-105">建立效能準則</span><span class="sxs-lookup"><span data-stu-id="5cae8-105">Establish Performance Criteria</span></span>  
 <span data-ttu-id="5cae8-106">從效能觀點來看，在此階段建立的功能規格中，最重要的部分是為專案定義詳細的效能目標，以及建立效能釋放準則。</span><span class="sxs-lookup"><span data-stu-id="5cae8-106">From a performance perspective, the most important part of the functional specification that is created during this phase is the definition of detailed performance goals for the project and the establishment of performance release criteria.</span></span> <span data-ttu-id="5cae8-107">定義效能準則時，有三個關鍵要素：</span><span class="sxs-lookup"><span data-stu-id="5cae8-107">There are three critical components to defining performance criteria:</span></span>  
  
-   <span data-ttu-id="5cae8-108">以時間函式來定義效能的曲線。</span><span class="sxs-lookup"><span data-stu-id="5cae8-108">A curve that defines performance as a function of time.</span></span>  
  
-   <span data-ttu-id="5cae8-109">與效能函式關聯的效能需求。</span><span class="sxs-lookup"><span data-stu-id="5cae8-109">A performance requirement associated with the performance function.</span></span>  
  
-   <span data-ttu-id="5cae8-110">檔案大小與類型的散佈。</span><span class="sxs-lookup"><span data-stu-id="5cae8-110">A distribution of file sizes and types.</span></span>  
  
 <span data-ttu-id="5cae8-111">這些準則會討論[何謂持續性效能？](../core/what-is-sustainable-performance.md)</span><span class="sxs-lookup"><span data-stu-id="5cae8-111">These criteria are discussed in [What Is Sustainable Performance?](../core/what-is-sustainable-performance.md)</span></span>  
  
 <span data-ttu-id="5cae8-112">您可以從效能目標中推導出應用程式的效能釋放準則。</span><span class="sxs-lookup"><span data-stu-id="5cae8-112">You derive the performance release criteria for an application from the performance goals.</span></span> <span data-ttu-id="5cae8-113">這些準則具體描述一個可達成且可評量的行為模式，您可以經由測試來證實。</span><span class="sxs-lookup"><span data-stu-id="5cae8-113">These criteria embody an achievable and measurable behavior that you can prove via testing.</span></span> <span data-ttu-id="5cae8-114">除非已經符合所有的釋放準則，或者在無法達成時，認定發生了釋放準則的例外情況，否則不會將應用程式推出發行。</span><span class="sxs-lookup"><span data-stu-id="5cae8-114">The application will not move into release unless and until all release criteria have been met or, if not achievable, identified as exceptions to the release criteria.</span></span>  
  
 <span data-ttu-id="5cae8-115">在產品週期的先期階段中設定釋放準則，是非常重要的。</span><span class="sxs-lookup"><span data-stu-id="5cae8-115">It is very important to set the release criteria during the early phases of the product cycle.</span></span> <span data-ttu-id="5cae8-116">這麼做，意味著所有相關人員在正式同意設計與實作前，都知道目標是什麼，以及未達成準則的後果。</span><span class="sxs-lookup"><span data-stu-id="5cae8-116">Doing so means everyone involved knows what the goals are and the consequences of not reaching them before design and implementation are signed off.</span></span>  
  
 <span data-ttu-id="5cae8-117">此外，效能測試案例也將以釋放準則的評量方式為依歸，所以這個準則必須夠詳細，才能避免產生混淆。</span><span class="sxs-lookup"><span data-stu-id="5cae8-117">In addition, performance test cases will be based on how the release criteria are to be measured, so the criteria must be detailed enough to avoid confusion.</span></span> <span data-ttu-id="5cae8-118">例如，在陳述要達成的特定輸送量時，就應該包括：</span><span class="sxs-lookup"><span data-stu-id="5cae8-118">For example, when stating a specific throughput is to be achieved, it should include:</span></span>  
  
-   <span data-ttu-id="5cae8-119">執行時必須使用的硬體，例如，伺服器的數量及類型、磁碟速度/類型等</span><span class="sxs-lookup"><span data-stu-id="5cae8-119">The hardware on which it must run, for example, the number and type of servers, disk speed/type, etc.</span></span>  
  
-   <span data-ttu-id="5cae8-120">要測試什麼實例，例如，應用程式會採用何種路徑訊息</span><span class="sxs-lookup"><span data-stu-id="5cae8-120">What scenario is to be tested, for example, what path messages will take through the application</span></span>  
  
-   <span data-ttu-id="5cae8-121">評量的方法，例如，使用效能計數器、自訂程式碼、測試訊息抵達某部分的次數等</span><span class="sxs-lookup"><span data-stu-id="5cae8-121">How it is to be measured, for example, performance counters, custom code, measuring times messages arrive in a share, etc.</span></span>  
  
 <span data-ttu-id="5cae8-122">格式完整的釋放準則必須讓任何人都能夠檢視做成文件的釋放準則，並瞭解如何建立測試案例來驗證準則。</span><span class="sxs-lookup"><span data-stu-id="5cae8-122">To judge how well formed a release criteria is, anyone should be able look at the release criteria as documented and understand how to build a test case to prove the criteria.</span></span>  
  
## <a name="identify-performance-risks"></a><span data-ttu-id="5cae8-123">識別效能風險</span><span class="sxs-lookup"><span data-stu-id="5cae8-123">Identify Performance Risks</span></span>  
 <span data-ttu-id="5cae8-124">在充分制定效能目標及釋放準則的細節之後，可以進行初步的效能風險範圍評估。</span><span class="sxs-lookup"><span data-stu-id="5cae8-124">After the performance release goals and criteria have been sufficiently detailed, an initial assessment of performance risk areas can be performed.</span></span> <span data-ttu-id="5cae8-125">這項分析的目的是找出應用程式中可能需要在設計上多加注意、另行解決或刪減的部分，以利達成期望的準則。</span><span class="sxs-lookup"><span data-stu-id="5cae8-125">The purpose of this analysis is to identify parts of the application that may need special design attention, work-around alternatives or elimination in order to reach the desired criteria.</span></span>  
  
 <span data-ttu-id="5cae8-126">例如，每個傳輸配接器類型都有本身的效能及容量縮放特性。</span><span class="sxs-lookup"><span data-stu-id="5cae8-126">For example, each transport adapter type has its own performance and scale characteristics.</span></span> <span data-ttu-id="5cae8-127">如果所需的輸送量超過其中一或多個 (接收或傳送) 配接器類型的能力，則可能有必要研究調查擴充配接器的替代方法。</span><span class="sxs-lookup"><span data-stu-id="5cae8-127">If the desired throughput exceeds the ability of one or more of the adapter types (either receive or send), then alternatives for scaling the adapter may need to be investigated.</span></span>  
  
## <a name="estimate-sizing"></a><span data-ttu-id="5cae8-128">預估規模大小</span><span class="sxs-lookup"><span data-stu-id="5cae8-128">Estimate Sizing</span></span>  
 <span data-ttu-id="5cae8-129">確立目標和準則而知所遵循之後，最好盡早開始預估達到目標所需的硬體規模。</span><span class="sxs-lookup"><span data-stu-id="5cae8-129">Based on the established goals and criteria, it is never too early to begin the process of estimating the hardware sizing that will be required to meet the goals.</span></span> <span data-ttu-id="5cae8-130">如同使用任何大小估計的投入時間，一個必須依據估計實際的測試結果。</span><span class="sxs-lookup"><span data-stu-id="5cae8-130">As with any sizing estimation efforts, one must base the estimates on actual test results.</span></span> <span data-ttu-id="5cae8-131">在專案的先期階段中，這些結果可能得仰賴外部來源。</span><span class="sxs-lookup"><span data-stu-id="5cae8-131">During the early phases of a project, those results must come from external sources.</span></span> <span data-ttu-id="5cae8-132">您可以在閱讀案例研究位於 BizTalk Server 開發人員中心， [http://go.microsoft.com/fwlink/?LinkId=49339](http://go.microsoft.com/fwlink/?LinkId=49339)。</span><span class="sxs-lookup"><span data-stu-id="5cae8-132">You can read case studies at BizTalk Server Developer Center, at [http://go.microsoft.com/fwlink/?LinkId=49339](http://go.microsoft.com/fwlink/?LinkId=49339).</span></span> <span data-ttu-id="5cae8-133">這些案例研究會提供有關已測試實例、執行測試的硬體及測試組態的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="5cae8-133">The case studies provide details about the scenarios tested, the hardware on which testing was done, and the configuration for the tests.</span></span> <span data-ttu-id="5cae8-134">您可以從這些測試案例達成的效能進行推斷，來取得系統的初步規模預估。</span><span class="sxs-lookup"><span data-stu-id="5cae8-134">You can extrapolate from the performance achieved for these test cases to get an initial sizing estimate for your system.</span></span>  
  
 <span data-ttu-id="5cae8-135">請記住，沒有預測模型或模擬，準確預測的任何應用程式上執行的系統大小[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5cae8-135">Keep in mind that there is no predictive model or simulation that accurately predicts system size for any arbitrary application running on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="5cae8-136">是一個平台可供部署繁多的應用程式方案，每個都有它自己的效能行為。</span><span class="sxs-lookup"><span data-stu-id="5cae8-136"> is a platform on which a large variety of application solutions can be deployed, each with its own performance behavior.</span></span> <span data-ttu-id="5cae8-137">因此，雖然使用現有案例研究結果推得的預估資料，在規劃工作上提供了良好的起點，但即使是最簡單的應用程式架構，其系統的最終規模也必定需要加以調整。</span><span class="sxs-lookup"><span data-stu-id="5cae8-137">So, while an estimate derived using existing case study results will provide a good starting point for planning purposes, the final size of the system will most certainly need to be adjusted for all but the simplest application architectures.</span></span>  
  
## <a name="plan-for-sufficient-testing"></a><span data-ttu-id="5cae8-138">規劃充分的測試</span><span class="sxs-lookup"><span data-stu-id="5cae8-138">Plan for Sufficient Testing</span></span>  
 <span data-ttu-id="5cae8-139">如上所述，目前沒有模型或模擬方法可以準確預測滿足效能目標所需的硬體。</span><span class="sxs-lookup"><span data-stu-id="5cae8-139">As stated above, there is currently no model or simulation that will accurately predict the hardware required to meet performance goals.</span></span> <span data-ttu-id="5cae8-140">這代表實際驗證系統是否能夠達成目標的唯一辦法，就是在實際執行等級的硬體上測試它。</span><span class="sxs-lookup"><span data-stu-id="5cae8-140">This means that the only way to actually prove a system is capable of reaching goals is to test it on production-level hardware.</span></span> <span data-ttu-id="5cae8-141">也就是說，要在盡可能接近實際執行環境的硬體上執行測試案例。</span><span class="sxs-lookup"><span data-stu-id="5cae8-141">That is, to conduct test cases on hardware that is as close to the production setup as possible.</span></span>  
  
 <span data-ttu-id="5cae8-142">這個部分的規劃工作是關鍵所在，您必須綜覽持續性效能的原則，並詳細瞭解輸送量分析資料和效能釋放準則。</span><span class="sxs-lookup"><span data-stu-id="5cae8-142">This part of the planning is critical and pulls together the principles of sustainable performance, understanding throughput profiles in detail, and the performance release criteria.</span></span> <span data-ttu-id="5cae8-143">使用現有資料推估而得的輸送量分析資料時，必須導出能夠一致地評量釋放準則的測試案例。</span><span class="sxs-lookup"><span data-stu-id="5cae8-143">Using the throughput profiles obtained by extrapolating from existing data, test cases must be derived that will consistently measure the release criteria.</span></span> <span data-ttu-id="5cae8-144">執行測試案例時，也必須考慮到持續性的問題。</span><span class="sxs-lookup"><span data-stu-id="5cae8-144">The test cases must be run with sustainability in mind.</span></span> <span data-ttu-id="5cae8-145">如需持續性測試的範例，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="5cae8-145">For examples of sustainable testing, see the following topics:</span></span>  
  
-   [<span data-ttu-id="5cae8-146">測量最大持續性引擎輸送量</span><span class="sxs-lookup"><span data-stu-id="5cae8-146">Measuring Maximum Sustainable Engine Throughput</span></span>](../core/measuring-maximum-sustainable-engine-throughput.md)  
  
-   [<span data-ttu-id="5cae8-147">測量最大持續性追蹤輸送量</span><span class="sxs-lookup"><span data-stu-id="5cae8-147">Measuring Maximum Sustainable Tracking Throughput</span></span>](../core/measuring-maximum-sustainable-tracking-throughput.md)  
  
## <a name="see-also"></a><span data-ttu-id="5cae8-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5cae8-148">See Also</span></span>  
 <span data-ttu-id="5cae8-149">[依階段的專案規劃建議](../core/project-planning-recommendations-by-phase.md) </span><span class="sxs-lookup"><span data-stu-id="5cae8-149">[Project Planning Recommendations by Phase](../core/project-planning-recommendations-by-phase.md) </span></span>  
 <span data-ttu-id="5cae8-150">[設計階段建議](../core/design-phase-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="5cae8-150">[Design Phase Recommendations](../core/design-phase-recommendations.md) </span></span>  
 <span data-ttu-id="5cae8-151">[實作階段建議](../core/implementation-phase-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="5cae8-151">[Implementation Phase Recommendations](../core/implementation-phase-recommendations.md) </span></span>  
 <span data-ttu-id="5cae8-152">[驗證階段建議](../core/verification-phase-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="5cae8-152">[Verification Phase Recommendations](../core/verification-phase-recommendations.md) </span></span>  
 [<span data-ttu-id="5cae8-153">發行階段建議</span><span class="sxs-lookup"><span data-stu-id="5cae8-153">Release Phase Recommendations</span></span>](../core/release-phase-recommendations.md)