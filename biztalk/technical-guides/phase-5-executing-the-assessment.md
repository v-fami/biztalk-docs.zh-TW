---
title: "第 5 個階段： 執行評定 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d40fc64-b6cb-448b-8ea1-a6ad7302ab8b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fba6d49d8d69276af4282ad0a941ee1fc4d8068
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="phase-5-executing-the-assessment"></a><span data-ttu-id="473f6-102">第 5 個階段： 執行評估</span><span class="sxs-lookup"><span data-stu-id="473f6-102">Phase 5: Executing the Assessment</span></span>
<span data-ttu-id="473f6-103">執行階段是透過自動化的負載測試和其中的效能瓶頸會探索及定址，產生的效能資料的位置。</span><span class="sxs-lookup"><span data-stu-id="473f6-103">The Execute phase is where the performance data is generated through automated load testing and where performance bottlenecks are discovered and addressed.</span></span> <span data-ttu-id="473f6-104">這個階段中具有反覆的程序效能瓶頸是減少或消除藉由測試，藉此評估效能、 最佳化及測試一次。</span><span class="sxs-lookup"><span data-stu-id="473f6-104">This phase has an iterative process whereby performance bottlenecks are reduced or eliminated by testing, evaluating performance, optimizing, and testing again.</span></span>  
  
 <span data-ttu-id="473f6-105">本主題說明通常會遵循 BizTalk Server 效能評估的執行階段的步驟：</span><span class="sxs-lookup"><span data-stu-id="473f6-105">This topic describes the steps that are typically followed during the Execute phase of a BizTalk Server performance assessment:</span></span>  
  
## <a name="step-1-run-automated-tests"></a><span data-ttu-id="473f6-106">步驟 1： 執行自動化的測試</span><span class="sxs-lookup"><span data-stu-id="473f6-106">Step 1: Run automated tests</span></span>  
 <span data-ttu-id="473f6-107">開始執行階段執行自動化的測試。</span><span class="sxs-lookup"><span data-stu-id="473f6-107">Begin the Execute phase by running automated tests.</span></span> <span data-ttu-id="473f6-108">BizTalk Server 效能評估通常著重於輸送量和/或延遲的測試，但可能會包含組建驗證和功能測試。</span><span class="sxs-lookup"><span data-stu-id="473f6-108">A BizTalk Server performance assessment typically focuses on throughput and/or latency testing but may include build verification and functional tests.</span></span> <span data-ttu-id="473f6-109">完整執行自動化測試的詳細資訊，請參閱[實作自動化的測試](../technical-guides/implementing-automated-testing.md)。</span><span class="sxs-lookup"><span data-stu-id="473f6-109">For comprehensive information about running automated testing, see [Implementing Automated Testing](../technical-guides/implementing-automated-testing.md).</span></span>  
  
## <a name="step-2-document-and-evaluate-test-results"></a><span data-ttu-id="473f6-110">步驟 2： 文件，並評估測試結果</span><span class="sxs-lookup"><span data-stu-id="473f6-110">Step 2: Document and evaluate test results</span></span>  
 <span data-ttu-id="473f6-111">在每個測試結束時，請徹底測試結果的文件，並評估是否已符合規定的效能目標。</span><span class="sxs-lookup"><span data-stu-id="473f6-111">At the conclusion of each test, thoroughly document the test results and evaluate whether the stated performance goals have been met.</span></span>  
  
## <a name="step-3-modify-the-configuration-of-biztalk-server-third-party-systems-or-solution-artifacts-to-tune-for-performance-based-on-the-test-results"></a><span data-ttu-id="473f6-112">步驟 3： 修改 BizTalk Server、 第三方系統或方案成品，若要根據測試結果的效能微調的組態</span><span class="sxs-lookup"><span data-stu-id="473f6-112">Step 3: Modify the configuration of BizTalk Server, third-party systems, or solution artifacts to tune for performance based on the test results</span></span>  
 <span data-ttu-id="473f6-113">使用測試結果來決定如何將環境最佳化到達所述的輸送量或延遲的目標。</span><span class="sxs-lookup"><span data-stu-id="473f6-113">Use the test results to make decisions about how to optimize the environment to reach stated throughput or latency goals.</span></span>  
  
## <a name="step-4-record-all-changes-made-to-the-environment"></a><span data-ttu-id="473f6-114">步驟 4： 對環境的所有變更的都記錄</span><span class="sxs-lookup"><span data-stu-id="473f6-114">Step 4: Record all changes made to the environment</span></span>  
 <span data-ttu-id="473f6-115">請確定對環境進行任何變更都完整記錄。</span><span class="sxs-lookup"><span data-stu-id="473f6-115">Ensure that any changes made to the environment are thoroughly documented.</span></span> <span data-ttu-id="473f6-116">變更的記錄可讓您輕鬆地套用實際執行環境中的變更，並將納變更的復原，如果需要。</span><span class="sxs-lookup"><span data-stu-id="473f6-116">A record of the changes will allow you to easily apply the changes in the production environment and will accommodate the undoing of changes if need be.</span></span>  
  
## <a name="step-5-repeat-this-cycle-until-goals-are-achieved"></a><span data-ttu-id="473f6-117">步驟 5： 重複這個循環，直到達到目標是</span><span class="sxs-lookup"><span data-stu-id="473f6-117">Step 5: Repeat this cycle until goals are achieved</span></span>  
 <span data-ttu-id="473f6-118">繼續測試、 評估和記錄結果、 最佳化環境，以及撰寫環境的變更，直到到達所要的效能目標的週期。</span><span class="sxs-lookup"><span data-stu-id="473f6-118">Continue the cycle of testing, evaluating and documenting results, optimizing the environment, and documenting changes to the environment until the desired performance goals are reached.</span></span>  
  
## <a name="step-6-summarize-test-results-at-the-end-of-each-day"></a><span data-ttu-id="473f6-119">步驟 6： 彙總的每一天結束測試結果</span><span class="sxs-lookup"><span data-stu-id="473f6-119">Step 6: Summarize test results at the end of each day</span></span>  
 <span data-ttu-id="473f6-120">完成測試結果和結尾的每一天的進度 」 執行的摘要 」。</span><span class="sxs-lookup"><span data-stu-id="473f6-120">Complete an “executive summary” of the test results and progress made at the end of each day.</span></span> <span data-ttu-id="473f6-121">編譯包含摘要的電子郵件，並讓每個人所針對的進度的通知傳送給所有專案關係人的效能評估中。</span><span class="sxs-lookup"><span data-stu-id="473f6-121">Compile an e-mail that contains the summary, and send to all stakeholders in the performance assessment to keep everyone informed of progress that is being made.</span></span>  
  
## <a name="step-7-update-the-project-plan-as-timeline-goals-are-met"></a><span data-ttu-id="473f6-122">步驟 7： 更新專案計劃符合目標的時間軸</span><span class="sxs-lookup"><span data-stu-id="473f6-122">Step 7: Update the project plan as timeline goals are met</span></span>  
 <span data-ttu-id="473f6-123">在計劃階段開發時間表是效能評定的整體進度的良好參考。</span><span class="sxs-lookup"><span data-stu-id="473f6-123">The timeline developed in the Plan phase is a good reference for the overall progress of the performance assessment.</span></span> <span data-ttu-id="473f6-124">更新這個時間軸在必要時，所有專案關係人溝通進度。</span><span class="sxs-lookup"><span data-stu-id="473f6-124">Update this timeline as necessary to communicate the progress to all stakeholders.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="473f6-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="473f6-125">See Also</span></span>  
 [<span data-ttu-id="473f6-126">效能評定階段</span><span class="sxs-lookup"><span data-stu-id="473f6-126">Phases of a Performance Assessment</span></span>](../technical-guides/phases-of-a-performance-assessment.md)