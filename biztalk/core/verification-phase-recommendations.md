---
title: "驗證階段建議 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00663354-ce5d-4391-b835-89940c92c1ce
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25344eafc37f492474b3f0bb36318afaf566829a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="verification-phase-recommendations"></a><span data-ttu-id="e2252-102">驗證階段建議</span><span class="sxs-lookup"><span data-stu-id="e2252-102">Verification Phase Recommendations</span></span>
<span data-ttu-id="e2252-103">在系統程式碼完成之後，即可開始全面加強其穩定性，並驗證其是否符合釋放準則。</span><span class="sxs-lookup"><span data-stu-id="e2252-103">After the system is code complete, it is ready to be fully stabilized and the release criteria can be verified.</span></span> <span data-ttu-id="e2252-104">這個階段通常稱為穩定化階段。</span><span class="sxs-lookup"><span data-stu-id="e2252-104">This phase is often referred to as the stabilization phase.</span></span> <span data-ttu-id="e2252-105">此階段的最終目標是要找出並修復錯誤，以及證實系統已準備好可以實際執行。</span><span class="sxs-lookup"><span data-stu-id="e2252-105">The ultimate goal of this phase is to identify and fix bugs and prove that the system is ready for production.</span></span> <span data-ttu-id="e2252-106">因此，在這個階段中，會對系統的發行候選版本進行終段測試。</span><span class="sxs-lookup"><span data-stu-id="e2252-106">This phase, therefore, involves a final round of testing on a release candidate of the system.</span></span>  
  
 <span data-ttu-id="e2252-107">發行候選版本是指在通過所有驗證測試的條件下，我們認為其完成度及穩定性夠得上發行水準的系統版本 (通常是最近完成的)。</span><span class="sxs-lookup"><span data-stu-id="e2252-107">A release candidate is a version of the system (usually the most recent) that is deemed complete and stable enough to become the released version should the verification test all pass.</span></span> <span data-ttu-id="e2252-108">要證實這點，就必須順利完成許多功能、效能及壓力測試，確認系統已準備就緒。</span><span class="sxs-lookup"><span data-stu-id="e2252-108">The way this is proven is by successful completion of a bank of functional, performance, and stress tests that verify it is indeed ready.</span></span>  
  
## <a name="test-to-verify-sustainable-throughput-and-latency"></a><span data-ttu-id="e2252-109">測試以確認持續性輸送量與潛在因素</span><span class="sxs-lookup"><span data-stu-id="e2252-109">Test to Verify Sustainable Throughput and Latency</span></span>  
 <span data-ttu-id="e2252-110">驗證效能的測試雖然和實作階段同時展開，但最後必須在證明成功通過整套釋放準則測試的發行候選版本上定案。</span><span class="sxs-lookup"><span data-stu-id="e2252-110">Verification testing for performance was started in parallel with the implementation phase, but needs to be finalized on a release candidate that has been shown to successfully withstand the full set of release criteria testing.</span></span> <span data-ttu-id="e2252-111">最理想的情況是，發行候選版本在終段測試期間，其測試結果未出現任何改變，讓人十分確信沒有帶進回復 (新功能對舊功能產生負面影響) 的因子。</span><span class="sxs-lookup"><span data-stu-id="e2252-111">Optimally, no changes to the release candidate are taken during the final test pass so that confidence is high that regressions have not been introduced.</span></span> <span data-ttu-id="e2252-112">這在實務上頗為困難，因為只要在組建內稍做變更，就必須對回復的風險進行評估。</span><span class="sxs-lookup"><span data-stu-id="e2252-112">In practice, this is quite difficult and, as changes are checked into the build, evaluations must be made as to the risk of regression.</span></span>  
  
 <span data-ttu-id="e2252-113">例如，如果系統成品 (如管線或協調流程) 中發生基本的變更，很可能就必須重新執行效能測試，以便驗證這個新的發行候選版本。</span><span class="sxs-lookup"><span data-stu-id="e2252-113">For example, if a fundamental change to a system artifact such as a pipeline or orchestration is introduced, performance tests will likely need to be re-run in order validate this new release candidate.</span></span>  
  
 <span data-ttu-id="e2252-114">為了確保系統已經準備好可以實際執行，您必須確認系統已在持續性方式下經過首尾連貫的測試。</span><span class="sxs-lookup"><span data-stu-id="e2252-114">To ensure that the system is ready for production, you must verify that it has been tested in a sustainable fashion end to end.</span></span> <span data-ttu-id="e2252-115">這表示所有的作業活動，例如資料庫維護，操作查詢與計劃和未規劃的中斷必須進行測試，如本主題中所定義[何謂持續性效能？](../core/what-is-sustainable-performance.md)</span><span class="sxs-lookup"><span data-stu-id="e2252-115">This means that all operations activities such as database maintenance, operations querying, and planned and unplanned outages must be tested, as defined in the topic [What Is Sustainable Performance?](../core/what-is-sustainable-performance.md)</span></span> <span data-ttu-id="e2252-116">這是證明系統整備所以結合一套完整的最終測試通過中的持續性效能測試的最後機會。</span><span class="sxs-lookup"><span data-stu-id="e2252-116">This is the last chance to certify readiness for the system, so it is important to combine the full suite of sustainable performance tests in the final test pass.</span></span>  
  
## <a name="identify-bottlenecks-and-adjust-hardware-or-solution-to-remove-goal-blockers"></a><span data-ttu-id="e2252-117">識別瓶頸與調整硬體，或者說，移除目標阻礙的解決方案</span><span class="sxs-lookup"><span data-stu-id="e2252-117">Identify Bottlenecks and Adjust Hardware or Solution to Remove Goal-Blockers</span></span>  
 <span data-ttu-id="e2252-118">在實務上，因此常會最終測試通過的測試平台會更接近硬體方面的生產環境與測試台的開發環境。</span><span class="sxs-lookup"><span data-stu-id="e2252-118">In practice, it is common that the test bed for the final test pass is closer to production with respect to hardware than the development of test beds.</span></span>  <span data-ttu-id="e2252-119">因此，最終測試通過期間利用這個機會，識別系統中的任何新的或現有的瓶頸，並決定它們是否足以需要調整硬體的相當重要。</span><span class="sxs-lookup"><span data-stu-id="e2252-119">It is important, therefore, to use the opportunity during the final test pass to identify any new or existing bottlenecks in the system and decide if they are of sufficient magnitude to require adjustments in hardware.</span></span> <span data-ttu-id="e2252-120">即使不需要立即調整硬體，發現最主要的系統瓶頸將可以提供寶貴的規劃和作業資訊。</span><span class="sxs-lookup"><span data-stu-id="e2252-120">Even if hardware doesn’t need to be adjusted immediately, identifying the most prevalent system bottlenecks will provide valuable planning and operations information.</span></span>  
  
 <span data-ttu-id="e2252-121">例如，如果系統可以支應實際執行時的一般負載情況，但發覺 MessageBox 伺服器上的實體磁碟閒置率很低 (例如，低於 20%)，那麼您就可以將實際執行期間對此磁碟的監控結果認定為一個關鍵狀況指標。</span><span class="sxs-lookup"><span data-stu-id="e2252-121">For example, if the system sustains the production load profile, but it is observed that the physical disk idle time on the MessageBox server is low (for example, below 20%), then monitoring this disk during production can be identified as a key health indicator.</span></span> <span data-ttu-id="e2252-122">此外，任何要增加系統負載能力的計劃，也可以將磁碟子系統需要改善的這項認知納入考量。</span><span class="sxs-lookup"><span data-stu-id="e2252-122">In addition, any plans for increasing the load capability of the system can now include knowledge that the disk subsystem will need to be improved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2252-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2252-123">See Also</span></span>  
 <span data-ttu-id="e2252-124">[依階段的專案規劃建議](../core/project-planning-recommendations-by-phase.md) </span><span class="sxs-lookup"><span data-stu-id="e2252-124">[Project Planning Recommendations by Phase](../core/project-planning-recommendations-by-phase.md) </span></span>  
 <span data-ttu-id="e2252-125">[需求階段建議](../core/requirements-phase-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="e2252-125">[Requirements Phase Recommendations](../core/requirements-phase-recommendations.md) </span></span>  
 <span data-ttu-id="e2252-126">[設計階段建議](../core/design-phase-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="e2252-126">[Design Phase Recommendations](../core/design-phase-recommendations.md) </span></span>  
 <span data-ttu-id="e2252-127">[實作階段建議](../core/implementation-phase-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="e2252-127">[Implementation Phase Recommendations](../core/implementation-phase-recommendations.md) </span></span>  
 [<span data-ttu-id="e2252-128">發行階段建議</span><span class="sxs-lookup"><span data-stu-id="e2252-128">Release Phase Recommendations</span></span>](../core/release-phase-recommendations.md)