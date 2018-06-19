---
title: 效能評定階段 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 120706f9-9fa1-4f41-bd89-3b9eada940ad
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32d3c32158bc5a334aa614f03aa1a86afd6fffd9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22301886"
---
# <a name="phases-of-a-performance-assessment"></a><span data-ttu-id="e1377-102">效能評定階段</span><span class="sxs-lookup"><span data-stu-id="e1377-102">Phases of a Performance Assessment</span></span>
<span data-ttu-id="e1377-103">其中一個主要目標[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]是容納最多處理的案例中，盡可能提供最大的彈性。</span><span class="sxs-lookup"><span data-stu-id="e1377-103">One of the primary goals of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is to provide maximum flexibility for accommodating as many processing scenarios as possible.</span></span> <span data-ttu-id="e1377-104">此絕佳的彈性，因為主要的 BizTalk 解決方案的開發人員所面臨的挑戰之一就是要判斷如何在中提供的功能的最佳使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]為了滿足其商業需求。</span><span class="sxs-lookup"><span data-stu-id="e1377-104">Because of this great flexibility, one of the primary challenges facing developers of a BizTalk solution is to determine how to make best use of the features available in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to meet their business needs.</span></span> <span data-ttu-id="e1377-105">BizTalk Server 解決方案的效能最佳化時，這種彈性也會造成一項挑戰。</span><span class="sxs-lookup"><span data-stu-id="e1377-105">This flexibility also poses a challenge when optimizing the performance of a BizTalk Server solution.</span></span>  
  
 <span data-ttu-id="e1377-106">本章節描述的方法，應該用來將 BizTalk Server 解決方案的效能最佳化參與 BizTalk Server 效能評估。</span><span class="sxs-lookup"><span data-stu-id="e1377-106">This section describes the methodology that should be used to optimize the performance of a BizTalk Server solution by engaging in a BizTalk Server performance assessment.</span></span> <span data-ttu-id="e1377-107">BizTalk Server 效能評估用來將特定的 BizTalk Server 解決方案的效能最大化。</span><span class="sxs-lookup"><span data-stu-id="e1377-107">A BizTalk Server performance assessment is used to maximize the performance of a particular BizTalk Server solution.</span></span> <span data-ttu-id="e1377-108">若要取得最大的好處，從 BizTalk Server 效能評定，效能評估應該分成下列五個主要步驟/階段：</span><span class="sxs-lookup"><span data-stu-id="e1377-108">In order to gain the maximum benefit from a BizTalk Server performance assessment, the performance assessment should be divided into the following five distinct steps/phases:</span></span>  
  
1.  <span data-ttu-id="e1377-109">範圍。</span><span class="sxs-lookup"><span data-stu-id="e1377-109">Scope</span></span>  
  
2.  <span data-ttu-id="e1377-110">計畫</span><span class="sxs-lookup"><span data-stu-id="e1377-110">Plan</span></span>  
  
3.  <span data-ttu-id="e1377-111">準備</span><span class="sxs-lookup"><span data-stu-id="e1377-111">Prepare</span></span>  
  
4.  <span data-ttu-id="e1377-112">建置實驗室</span><span class="sxs-lookup"><span data-stu-id="e1377-112">Build lab</span></span>  
  
5.  <span data-ttu-id="e1377-113">Execute</span><span class="sxs-lookup"><span data-stu-id="e1377-113">Execute</span></span>  
  
 <span data-ttu-id="e1377-114">本主題描述每一個階段中有更詳細。</span><span class="sxs-lookup"><span data-stu-id="e1377-114">This topic describes each of these phases in greater detail.</span></span>  
  
 <span data-ttu-id="e1377-115">![效能評定程序的階段](../technical-guides/media/assessmentprocess.gif "AssessmentProcess")</span><span class="sxs-lookup"><span data-stu-id="e1377-115">![Phases of a performance assessment process](../technical-guides/media/assessmentprocess.gif "AssessmentProcess")</span></span>  
<span data-ttu-id="e1377-116">BizTalk Server 效能評定的階段</span><span class="sxs-lookup"><span data-stu-id="e1377-116">Phases of a BizTalk Server performance assessment</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e1377-117">本節內容</span><span class="sxs-lookup"><span data-stu-id="e1377-117">In This Section</span></span>  
  
-   <span data-ttu-id="e1377-118">[階段 1： 設定範圍評估](../technical-guides/phase-1-scoping-the-assessment.md)-描述建立效能評定的範圍時，應遵循的步驟。</span><span class="sxs-lookup"><span data-stu-id="e1377-118">[Phase 1: Scoping the Assessment](../technical-guides/phase-1-scoping-the-assessment.md) - Describes the steps that should be followed when establishing the scope of the performance assessment.</span></span>  
  
-   <span data-ttu-id="e1377-119">[階段 2： 規劃評估](../technical-guides/phase-2-planning-the-assessment.md)– 說明如何建立方案的里程碑時間軸。</span><span class="sxs-lookup"><span data-stu-id="e1377-119">[Phase 2: Planning the Assessment](../technical-guides/phase-2-planning-the-assessment.md) – Describes how to create a solution milestones timeline.</span></span> <span data-ttu-id="e1377-120">這用做為主要計劃來清楚文件時應符合預期的目標方案的測試。</span><span class="sxs-lookup"><span data-stu-id="e1377-120">This is used as a master plan to clearly document when expected goals for the testing of the solution should be met.</span></span>  
  
-   <span data-ttu-id="e1377-121">[階段 3： 準備評估](../technical-guides/phase-3-preparing-for-the-assessment.md)– 說明如何提供解決方案的詳細的架構圖和方案所使用的硬體組態的特定層面。</span><span class="sxs-lookup"><span data-stu-id="e1377-121">[Phase 3: Preparing for the Assessment](../technical-guides/phase-3-preparing-for-the-assessment.md) – Describes how to provide a detailed architectural diagram of the solution and specific aspects of the hardware configuration used by the solution.</span></span>  
  
-   <span data-ttu-id="e1377-122">[第 4 個階段： 建立評估環境](../technical-guides/phase-4-building-the-assessment-environment.md)– 描述硬體和根據詳細的設計，先前已建立的方案平台的應用程式的安裝。</span><span class="sxs-lookup"><span data-stu-id="e1377-122">[Phase 4: Building the Assessment Environment](../technical-guides/phase-4-building-the-assessment-environment.md) – Describes installation of hardware and applications according to the detailed design of the solution platform that was established previously.</span></span>  
  
-   <span data-ttu-id="e1377-123">[第 5 個階段： 執行評估](../technical-guides/phase-5-executing-the-assessment.md)– 提供產生透過自動化的負載測試，以及如何偵測並排除在方案中的找出任何瓶頸的效能資料的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e1377-123">[Phase 5: Executing the Assessment](../technical-guides/phase-5-executing-the-assessment.md) – Provides information about generating performance data via automated load testing and how to detect and eliminate any bottlenecks in the solution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1377-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1377-124">See Also</span></span>  
 [<span data-ttu-id="e1377-125">BizTalk Server 效能測試方法</span><span class="sxs-lookup"><span data-stu-id="e1377-125">BizTalk Server Performance Testing Methodology</span></span>](../technical-guides/biztalk-server-performance-testing-methodology.md)