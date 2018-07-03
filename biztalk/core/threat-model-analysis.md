---
title: 威脅模型分析 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TMA, about TMA
- TMA
- TMA, procedure steps
ms.assetid: dfbf46aa-0a35-4925-8718-df8591efc279
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7fa52a2d256bace363c3453f19cabefca81cb73
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37016845"
---
# <a name="threat-model-analysis"></a><span data-ttu-id="b6527-102">威脅模型分析</span><span class="sxs-lookup"><span data-stu-id="b6527-102">Threat Model Analysis</span></span>
<span data-ttu-id="b6527-103">威脅模型分析 (TMA) 是一種分析，可協助判斷對產品、應用程式或環境造成的安全性風險，以及攻擊會如何出現。</span><span class="sxs-lookup"><span data-stu-id="b6527-103">A threat model analysis (TMA) is an analysis that helps determine the security risks posed to a product, application, network, or environment, and how attacks can show up.</span></span> <span data-ttu-id="b6527-104">其目標是用以判斷哪些威脅需要防護以及如何減輕這些威脅。</span><span class="sxs-lookup"><span data-stu-id="b6527-104">The goal is to determine which threats require mitigation and how to mitigate them.</span></span>  
  
 <span data-ttu-id="b6527-105">本節提供 TMA 程序的概要資訊。</span><span class="sxs-lookup"><span data-stu-id="b6527-105">This section provides high-level information about the TMA process.</span></span> <span data-ttu-id="b6527-106">如需詳細資訊，請參閱之第 4 章*Writing Secure Code，第二版*、 Michael Howard 與 David LeBlanc。</span><span class="sxs-lookup"><span data-stu-id="b6527-106">For more information, see Chapter 4 of *Writing Secure Code, Second edition*, by Michael Howard and David LeBlanc.</span></span>  
  
 <span data-ttu-id="b6527-107">TMA 的一些優點為：</span><span class="sxs-lookup"><span data-stu-id="b6527-107">Some of the benefits of a TMA are:</span></span>  
  
- <span data-ttu-id="b6527-108">讓您對應用程式更加瞭解</span><span class="sxs-lookup"><span data-stu-id="b6527-108">Provides a better understanding of your application</span></span>  
  
- <span data-ttu-id="b6527-109">協助您尋找錯誤</span><span class="sxs-lookup"><span data-stu-id="b6527-109">Helps you find bugs</span></span>  
  
- <span data-ttu-id="b6527-110">可協助新的小組成員詳細瞭解應用程式</span><span class="sxs-lookup"><span data-stu-id="b6527-110">Can help new team members understand the application in detail</span></span>  
  
- <span data-ttu-id="b6527-111">包含應用程式上建置的其他小組之重要資訊</span><span class="sxs-lookup"><span data-stu-id="b6527-111">Contains important information for other teams that build on your application</span></span>  
  
- <span data-ttu-id="b6527-112">對測試人員相當有用</span><span class="sxs-lookup"><span data-stu-id="b6527-112">Useful for testers</span></span>  
  
  <span data-ttu-id="b6527-113">執行 TMA 的概要步驟：</span><span class="sxs-lookup"><span data-stu-id="b6527-113">The high-level steps to perform a TMA are:</span></span>  
  
- <span data-ttu-id="b6527-114">步驟 1：</span><span class="sxs-lookup"><span data-stu-id="b6527-114">Step 1.</span></span> <span data-ttu-id="b6527-115">收集背景資訊</span><span class="sxs-lookup"><span data-stu-id="b6527-115">Collect Background Information</span></span>  
  
- <span data-ttu-id="b6527-116">步驟 2：</span><span class="sxs-lookup"><span data-stu-id="b6527-116">Step 2.</span></span> <span data-ttu-id="b6527-117">建立和分析威脅模型</span><span class="sxs-lookup"><span data-stu-id="b6527-117">Create and Analyze the Threat Model</span></span>  
  
- <span data-ttu-id="b6527-118">步驟 3：</span><span class="sxs-lookup"><span data-stu-id="b6527-118">Step 3.</span></span> <span data-ttu-id="b6527-119">檢視威脅</span><span class="sxs-lookup"><span data-stu-id="b6527-119">Review Threats</span></span>  
  
- <span data-ttu-id="b6527-120">步驟 4：</span><span class="sxs-lookup"><span data-stu-id="b6527-120">Step 4.</span></span> <span data-ttu-id="b6527-121">識別防護技術</span><span class="sxs-lookup"><span data-stu-id="b6527-121">Identify Mitigation Techniques and Technologies</span></span>  
  
- <span data-ttu-id="b6527-122">步驟 5：</span><span class="sxs-lookup"><span data-stu-id="b6527-122">Step 5.</span></span> <span data-ttu-id="b6527-123">文件的安全性模型和部署考量</span><span class="sxs-lookup"><span data-stu-id="b6527-123">Document Security Model and Deployment Considerations</span></span>  
  
- <span data-ttu-id="b6527-124">步驟 6：</span><span class="sxs-lookup"><span data-stu-id="b6527-124">Step 6.</span></span> <span data-ttu-id="b6527-125">實作和測試防護</span><span class="sxs-lookup"><span data-stu-id="b6527-125">Implement and Test Mitigations</span></span>  
  
- <span data-ttu-id="b6527-126">步驟 7：</span><span class="sxs-lookup"><span data-stu-id="b6527-126">Step 7.</span></span> <span data-ttu-id="b6527-127">保持威脅模型與設計同步</span><span class="sxs-lookup"><span data-stu-id="b6527-127">Keep the Threat Model in Sync with Design</span></span>  
  
## <a name="step-1-collect-background-information"></a><span data-ttu-id="b6527-128">步驟 1：</span><span class="sxs-lookup"><span data-stu-id="b6527-128">Step 1.</span></span> <span data-ttu-id="b6527-129">收集背景資訊</span><span class="sxs-lookup"><span data-stu-id="b6527-129">Collect Background Information</span></span>  
 <span data-ttu-id="b6527-130">為準備一個成功的 TMA，您必須收集一些背景資訊。</span><span class="sxs-lookup"><span data-stu-id="b6527-130">To prepare for a successful TMA, you have to collect some background information.</span></span> <span data-ttu-id="b6527-131">依照下列方式分析目標環境 (應用程式、程式或整個基礎結構) 是相當有用的：</span><span class="sxs-lookup"><span data-stu-id="b6527-131">It is useful to analyze your target environment (an application, program, or the whole infrastructure) as follows:</span></span>  
  
-   <span data-ttu-id="b6527-132">識別使用實例。</span><span class="sxs-lookup"><span data-stu-id="b6527-132">Identify use-case scenarios.</span></span> <span data-ttu-id="b6527-133">針對目標環境的每個使用實例，識別您預期公司如何使用目標環境，以及對目標環境的限制。</span><span class="sxs-lookup"><span data-stu-id="b6527-133">For each use-case scenario for your target environment, identify how you expect your company to use the target environment, and any limitations or restrictions on the target environment.</span></span> <span data-ttu-id="b6527-134">此資訊可協助定義威脅模型討論的範圍，並提供資產 (對您公司有價值的任何事物，例如資料與電腦) 與進入點的指標。</span><span class="sxs-lookup"><span data-stu-id="b6527-134">This information helps define the scope of the threat model discussion, and provides pointers to assets (anything of value to your company, such as data and computers) and entry points.</span></span>  
  
-   <span data-ttu-id="b6527-135">為每個實例建立資料流程圖 (DFD)。</span><span class="sxs-lookup"><span data-stu-id="b6527-135">Create a data flow diagram (DFD) for each scenario.</span></span> <span data-ttu-id="b6527-136">請確定您對威脅的瞭解夠深入。</span><span class="sxs-lookup"><span data-stu-id="b6527-136">Make sure that you go deep enough to understand your threats.</span></span>  
  
-   <span data-ttu-id="b6527-137">決定目標環境的界限與範圍。</span><span class="sxs-lookup"><span data-stu-id="b6527-137">Determine the boundaries and scope of the target environment.</span></span>  
  
-   <span data-ttu-id="b6527-138">瞭解信任與不信任元件之間的界限。</span><span class="sxs-lookup"><span data-stu-id="b6527-138">Understand the boundaries between trusted and untrusted components.</span></span>  
  
-   <span data-ttu-id="b6527-139">瞭解每個元件的組態與管理模型。</span><span class="sxs-lookup"><span data-stu-id="b6527-139">Understand the configuration and administration model for each component.</span></span>  
  
-   <span data-ttu-id="b6527-140">建立外部相依性的清單。</span><span class="sxs-lookup"><span data-stu-id="b6527-140">Create a list of external dependencies.</span></span>  
  
-   <span data-ttu-id="b6527-141">建立每個元件相依的其他元件之假設清單。</span><span class="sxs-lookup"><span data-stu-id="b6527-141">Create a list of assumptions about other components on which each component depends.</span></span> <span data-ttu-id="b6527-142">這可以協助與其他小組一起驗證跨元件假設、動作項目以及後續項目。</span><span class="sxs-lookup"><span data-stu-id="b6527-142">This helps validate cross-component assumptions, action items, and follow-up items with other teams.</span></span>  
  
## <a name="step-2-create-and-analyze-the-threat-model"></a><span data-ttu-id="b6527-143">步驟 2：</span><span class="sxs-lookup"><span data-stu-id="b6527-143">Step 2.</span></span> <span data-ttu-id="b6527-144">建立和分析威脅模型</span><span class="sxs-lookup"><span data-stu-id="b6527-144">Create and Analyze the Threat Model</span></span>  
 <span data-ttu-id="b6527-145">在您收集背景資訊之後，應該召開威脅模型會議。</span><span class="sxs-lookup"><span data-stu-id="b6527-145">After you collect the background information, you should have a threat model meeting or meetings.</span></span> <span data-ttu-id="b6527-146">請確定每個開發領域 (例如，程式管理人員、開發人員以及測試人員) 至少有一位成員出席會議。</span><span class="sxs-lookup"><span data-stu-id="b6527-146">Make sure that at least one member of each development discipline (for example, program managers, developers, and testers) is at the meeting.</span></span> <span data-ttu-id="b6527-147">請務必提醒與會人員，會議目的是要找出威脅，而不是修正威脅。</span><span class="sxs-lookup"><span data-stu-id="b6527-147">Make sure that you remind the attendees that the goal of the meeting is to find threats, not to fix them.</span></span> <span data-ttu-id="b6527-148">在威脅模型會議期間，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="b6527-148">During the threat model meeting, do the following:</span></span>  
  
-   <span data-ttu-id="b6527-149">檢查每個使用實例的 DFD。</span><span class="sxs-lookup"><span data-stu-id="b6527-149">Examine the DFD for each use case.</span></span> <span data-ttu-id="b6527-150">在每個使用實例識別下列項目：</span><span class="sxs-lookup"><span data-stu-id="b6527-150">For each use case identify:</span></span>  
  
    -   <span data-ttu-id="b6527-151">進入點</span><span class="sxs-lookup"><span data-stu-id="b6527-151">Entry points</span></span>  
  
    -   <span data-ttu-id="b6527-152">信任界限</span><span class="sxs-lookup"><span data-stu-id="b6527-152">Trust boundaries</span></span>  
  
    -   <span data-ttu-id="b6527-153">從輸入點到最後靜止位置的資料流 (然後返回)</span><span class="sxs-lookup"><span data-stu-id="b6527-153">Flow of data from entry point to final resting location (and back)</span></span>  
  
-   <span data-ttu-id="b6527-154">請注意相關的資產。</span><span class="sxs-lookup"><span data-stu-id="b6527-154">Note the assets involved.</span></span>  
  
-   <span data-ttu-id="b6527-155">討論每個 DFD，並尋找下列類別的 dfd 的所有項目中的威脅： **S**假冒識別，請**T**的資料，ampering **R**否認， **我**nformation 洩漏**D**拒絕服務，和**E**權限的身分。</span><span class="sxs-lookup"><span data-stu-id="b6527-155">Discuss each DFD, and look for threats in the following categories for all entries in the DFD: **S**poofing identify, **T**ampering with data, **R**epudiation, **I**nformation disclosure, **D**enial of service, and **E**levation of privileges.</span></span>  
  
-   <span data-ttu-id="b6527-156">建立已識別威脅的清單。</span><span class="sxs-lookup"><span data-stu-id="b6527-156">Create a list of the identified threats.</span></span> <span data-ttu-id="b6527-157">我們建議此清單包含下列： 標題、 簡短描述 （包括威脅樹狀結構）、 資產、 影響、 風險、 防護技術、 防護狀態以及錯誤數目。</span><span class="sxs-lookup"><span data-stu-id="b6527-157">We recommend that this list include the following: title, brief description (including threat trees), asset (asset), impact(s), risk, mitigation techniques, mitigation status, and a bug number.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b6527-158">您可以在檢視威脅時新增風險、防護技術以及防護狀態。</span><span class="sxs-lookup"><span data-stu-id="b6527-158">You can add risk, mitigation techniques, and mitigation status as you review the threats.</span></span> <span data-ttu-id="b6527-159">在威脅模型會議期間，請勿花費太多時間在這些領域。</span><span class="sxs-lookup"><span data-stu-id="b6527-159">Do not spend too much time in these areas during the threat model meeting.</span></span>  
  
## <a name="step-3-review-threats"></a><span data-ttu-id="b6527-160">步驟 3：</span><span class="sxs-lookup"><span data-stu-id="b6527-160">Step 3.</span></span> <span data-ttu-id="b6527-161">檢視威脅</span><span class="sxs-lookup"><span data-stu-id="b6527-161">Review Threats</span></span>  
 <span data-ttu-id="b6527-162">在您識別對環境的威脅之後，必須將每個威脅的風險排名，並決定如何回應每個威脅。</span><span class="sxs-lookup"><span data-stu-id="b6527-162">After you have identified the threats to your environment, you must rank the risk of each threat and determine how you want to respond to each threat.</span></span> <span data-ttu-id="b6527-163">您可以在其他小組會議或是透過電子郵件來執行此動作。</span><span class="sxs-lookup"><span data-stu-id="b6527-163">You can do this with additional team meetings or through e-mail.</span></span> <span data-ttu-id="b6527-164">您可以使用下列影響類別來計算風險洩露： **D**損害， **R**eproducibility， **E**xploitability， 受使用者，並**D**iscoverability。</span><span class="sxs-lookup"><span data-stu-id="b6527-164">You can use the following effect categories to calculate risk exposure: **D**amage potential, **R**eproducibility, **E**xploitability, **A**ffected users, and **D**iscoverability.</span></span>  
  
 <span data-ttu-id="b6527-165">在您擁有依照風險優先順序排列的目標環境之威脅清單後，必須決定將如何回應每個威脅。</span><span class="sxs-lookup"><span data-stu-id="b6527-165">After you have a list of the threats to your target environment prioritized by risk, you must determine how you will respond to each threat.</span></span> <span data-ttu-id="b6527-166">您的回應可以是不做任何動作 (通常不是好選擇)、警告使用者可能的問題、移除問題或是修正問題。</span><span class="sxs-lookup"><span data-stu-id="b6527-166">Your response can be to do nothing (rarely a good choice), warn users about the potential problem, remove the problem, or fix the problem.</span></span>  
  
## <a name="step-4-identify-mitigation-techniques-and-technologies"></a><span data-ttu-id="b6527-167">步驟 4：</span><span class="sxs-lookup"><span data-stu-id="b6527-167">Step 4.</span></span> <span data-ttu-id="b6527-168">識別防護技術</span><span class="sxs-lookup"><span data-stu-id="b6527-168">Identify Mitigation Techniques and Technologies</span></span>  
 <span data-ttu-id="b6527-169">在您識別要修正的威脅之後，必須決定每個威脅的可用防護技術，以及最適當的技術以降低每個威脅的影響。</span><span class="sxs-lookup"><span data-stu-id="b6527-169">After you identify which threats you will fix, you must determine the available mitigation techniques for each threat, and the most appropriate technology to reduce the effect of each threat.</span></span>  
  
 <span data-ttu-id="b6527-170">例如，視目標環境的詳細情況而定，您可以使用授權技術來降低資料竄改威脅的影響。</span><span class="sxs-lookup"><span data-stu-id="b6527-170">For example, depending on the details of your target environment, you can reduce the effect of data-tamper threats by using authorization techniques.</span></span> <span data-ttu-id="b6527-171">接著您必須決定要使用的適當授權技術 (例如，判別存取控制清單 (DACL)、權限或 IP 限制)。</span><span class="sxs-lookup"><span data-stu-id="b6527-171">You then have to determine the appropriate authorization technology to use (for example, discretionary access control lists (DACLs), permissions, or IP restrictions).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b6527-172">當您評估要使用的防護技術時，必須考量是否符合您公司的商務考量，以及是否有任何公司政策會影響要選擇的防護技術。</span><span class="sxs-lookup"><span data-stu-id="b6527-172">When you evaluate mitigation techniques and technologies to use, you must consider what makes business sense for your company, and any policies your company has that might affect the mitigation technique to choose.</span></span>  
  
 <span data-ttu-id="b6527-173">在完成 TMA 之後，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="b6527-173">After you complete the TMA, do the following:</span></span>  
  
-   <span data-ttu-id="b6527-174">記錄安全性模型與部署考量</span><span class="sxs-lookup"><span data-stu-id="b6527-174">Document the security model and deployment considerations</span></span>  
  
-   <span data-ttu-id="b6527-175">實作和測試防護</span><span class="sxs-lookup"><span data-stu-id="b6527-175">Implement and test mitigations</span></span>  
  
-   <span data-ttu-id="b6527-176">保持威脅模型與設計同步</span><span class="sxs-lookup"><span data-stu-id="b6527-176">Keep the threat model synchronized with design</span></span>  
  
## <a name="step-5-document-security-model-and-deployment-considerations"></a><span data-ttu-id="b6527-177">步驟 5：</span><span class="sxs-lookup"><span data-stu-id="b6527-177">Step 5.</span></span> <span data-ttu-id="b6527-178">文件的安全性模型和部署考量</span><span class="sxs-lookup"><span data-stu-id="b6527-178">Document Security Model and Deployment Considerations</span></span>  
 <span data-ttu-id="b6527-179">在 TMA 期間記錄所發現的狀況，並決定如何降低對目標環境威脅的影響，是非常有用的。</span><span class="sxs-lookup"><span data-stu-id="b6527-179">It is valuable to document what you discover during the TMA and how you decide to reduce the effect of the threats to your target environment.</span></span> <span data-ttu-id="b6527-180">本文件對於品質保證 (QA)、測試、支援以及作業人員是非常有用的。</span><span class="sxs-lookup"><span data-stu-id="b6527-180">This documentation can be useful to quality assurance (QA), test, support, and operations personnel.</span></span> <span data-ttu-id="b6527-181">包含與目標環境互動和介入目標環境的其他應用程式之資訊，以及防火牆與拓樸建議和需求之資訊。</span><span class="sxs-lookup"><span data-stu-id="b6527-181">Include information about other applications that interact or interface with your target environment, and the firewall and topology recommendations and requirements.</span></span>  
  
## <a name="step-6-implement-and-test-mitigations"></a><span data-ttu-id="b6527-182">步驟 6：</span><span class="sxs-lookup"><span data-stu-id="b6527-182">Step 6.</span></span> <span data-ttu-id="b6527-183">實作和測試防護</span><span class="sxs-lookup"><span data-stu-id="b6527-183">Implement and Test Mitigations</span></span>  
 <span data-ttu-id="b6527-184">當您的小組準備修正在 TMA 期間識別的威脅時，請務必使用開發和部署檢查清單，以遵循安全準則和部署標準，協助將新威脅的產生降到最低。</span><span class="sxs-lookup"><span data-stu-id="b6527-184">When your team is ready to fix threats identified during the TMA, make sure you use development and deployment checklists to follow secure code and deployment standards that will help minimize the introduction of new threats.</span></span>  
  
 <span data-ttu-id="b6527-185">在您實作防護之後，請務必測試防護，以確定它可提供針對威脅所需的防護層級。</span><span class="sxs-lookup"><span data-stu-id="b6527-185">After you implement a mitigation, make sure you test it to make sure it provides the level of protection that you want for the threat.</span></span>  
  
## <a name="step-7-keep-the-threat-model-in-sync-with-design"></a><span data-ttu-id="b6527-186">步驟 7：</span><span class="sxs-lookup"><span data-stu-id="b6527-186">Step 7.</span></span> <span data-ttu-id="b6527-187">保持威脅模型與設計同步</span><span class="sxs-lookup"><span data-stu-id="b6527-187">Keep the Threat Model in Sync with Design</span></span>  
 <span data-ttu-id="b6527-188">當您新增應用程式、伺服器以及其他項目至環境中時，請務必重新瀏覽威脅模型分析的發現，並針對任何新功能執行 TMA。</span><span class="sxs-lookup"><span data-stu-id="b6527-188">As you add new applications, servers, and other elements to your environment, make sure that you revisit the findings of the threat model analysis and do TMAs for any new functionality.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6527-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6527-189">See Also</span></span>  
<span data-ttu-id="b6527-190">[小型至中型公司的安全性案例研究](../core/security-case-studies-for-small-to-medium-sized-companies.md) </span><span class="sxs-lookup"><span data-stu-id="b6527-190">[Security Case Studies for Small to Medium-Sized Companies](../core/security-case-studies-for-small-to-medium-sized-companies.md) </span></span>  
 [<span data-ttu-id="b6527-191">威脅模型分析的案例範例</span><span class="sxs-lookup"><span data-stu-id="b6527-191">Sample Scenarios for Threat Model Analysis</span></span>](../core/sample-scenarios-for-threat-model-analysis.md)