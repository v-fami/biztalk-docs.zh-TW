---
title: "測試規劃 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca2f5f29-9eea-4f4d-9781-75c231db4605
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12bdf5f35d5d612ec077ebdac83339c5a6838109
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-testing"></a><span data-ttu-id="d1b6b-102">測試規劃</span><span class="sxs-lookup"><span data-stu-id="d1b6b-102">Planning for Testing</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d1b6b-103">測試可以分成數種類別，包括單元測試、 功能測試、 負載測試，以及可用性測試。</span><span class="sxs-lookup"><span data-stu-id="d1b6b-103"> testing can be divided into several categories including unit testing, functional testing, load testing, and availability testing.</span></span> <span data-ttu-id="d1b6b-104">本主題描述單位和負載測試，以及如何針對每個計劃。</span><span class="sxs-lookup"><span data-stu-id="d1b6b-104">This topic describes unit and load testing and how to plan for each.</span></span>  
  
## <a name="planning-for-unit-testing"></a><span data-ttu-id="d1b6b-105">單元測試計劃</span><span class="sxs-lookup"><span data-stu-id="d1b6b-105">Planning for Unit Testing</span></span>  
 <span data-ttu-id="d1b6b-106">單元測試是用來驗證該程式碼個別單位的程序依照設計運作。</span><span class="sxs-lookup"><span data-stu-id="d1b6b-106">Unit testing is a procedure used to validate that individual units of code are working as designed.</span></span> <span data-ttu-id="d1b6b-107">單元測試可以視為 「 中斷/修正 「 測試： 軟體不會執行所需的功能在不同情況下，可以在這些情況下會發生軟體處理錯誤？</span><span class="sxs-lookup"><span data-stu-id="d1b6b-107">Unit testing can be thought of as "break/fix" testing: Does the software perform the desired functionality under different conditions and can the software handle errors that occur under these conditions?</span></span>  
  
 <span data-ttu-id="d1b6b-108">因為個別的元件通常會執行單元測試，關聯的測試平台不需要實際執行環境的處理功能。</span><span class="sxs-lookup"><span data-stu-id="d1b6b-108">Since unit testing is typically performed on individual components, the associated test bed does not need the processing capabilities of an actual production environment.</span></span> <span data-ttu-id="d1b6b-109">基於這個理由，您應該考慮執行單元測試中的虛擬伺服器環境，可大幅較少的硬體資源。</span><span class="sxs-lookup"><span data-stu-id="d1b6b-109">For this reason, you should consider performing unit testing in a Virtual Server environment, which requires considerably fewer hardware resources.</span></span>  
  
 <span data-ttu-id="d1b6b-110">單元測試的虛擬化環境中執行的另一個層面暫存。</span><span class="sxs-lookup"><span data-stu-id="d1b6b-110">Another aspect of unit testing that may be performed in a virtualized environment is staging.</span></span> <span data-ttu-id="d1b6b-111">臨時區域是單元測試實際部署 BizTalk 解決方案的程序。</span><span class="sxs-lookup"><span data-stu-id="d1b6b-111">Staging is the process of unit testing the actual deployment of a BizTalk solution.</span></span> <span data-ttu-id="d1b6b-112">若要充分利用可用的硬體資源，請考慮使用 Virtual Server 的執行環境。</span><span class="sxs-lookup"><span data-stu-id="d1b6b-112">To maximize available hardware resources, consider using Virtual Server for your staging environment.</span></span>  
  
 <span data-ttu-id="d1b6b-113">如需有關使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在虛擬環境中，請參閱[使用虛擬伺服器期間發行管理程序](../technical-guides/planning-the-development-testing-staging-and-production-environments.md#BKMK_VirtualServ)。</span><span class="sxs-lookup"><span data-stu-id="d1b6b-113">For more information about using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a virtual environment, see [Using Virtual Server During the Release Management Process](../technical-guides/planning-the-development-testing-staging-and-production-environments.md#BKMK_VirtualServ).</span></span> <span data-ttu-id="d1b6b-114">工具可能適用於單元測試 BizTalk 解決方案的相關資訊，請參閱[工具測試](~/technical-guides/tools-for-testing.md)。</span><span class="sxs-lookup"><span data-stu-id="d1b6b-114">For information about tools that may be useful for unit testing a BizTalk solution, see [Tools for Testing](~/technical-guides/tools-for-testing.md).</span></span> <span data-ttu-id="d1b6b-115">如需執行單元測試的考量的檢查清單，請參閱[執行單元測試](../technical-guides/performing-unit-testing.md)。</span><span class="sxs-lookup"><span data-stu-id="d1b6b-115">For a checklist of considerations for performing unit testing see [Performing Unit Testing](../technical-guides/performing-unit-testing.md).</span></span>  
  
## <a name="planning-for-load-testing"></a><span data-ttu-id="d1b6b-116">負載測試的計劃</span><span class="sxs-lookup"><span data-stu-id="d1b6b-116">Planning for Load Testing</span></span>  
 <span data-ttu-id="d1b6b-117">負載測試是測量最大持續性效能和最大持續性追蹤的 BizTalk 解決方案的效能，然後再移除禁止解決方案的輸送量瓶頸的程序。</span><span class="sxs-lookup"><span data-stu-id="d1b6b-117">Load testing is the process of measuring maximum sustainable performance and maximum sustainable tracking performance of a BizTalk solution and then removing bottlenecks that inhibit the throughput of the solution.</span></span> <span data-ttu-id="d1b6b-118">如需有關負載測試，且會移除從瓶頸[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]方案，請參閱[BizTalk Server 2009 效能指南](http://go.microsoft.com/fwlink/?LinkID=150492)(http://go.microsoft.com/fwlink/?LinkID=150492)。</span><span class="sxs-lookup"><span data-stu-id="d1b6b-118">For more information about load testing and removing bottlenecks from a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution, see the [BizTalk Server 2009 Performance Guide](http://go.microsoft.com/fwlink/?LinkID=150492) (http://go.microsoft.com/fwlink/?LinkID=150492).</span></span>  
  
 <span data-ttu-id="d1b6b-119">工具可用於負載測試 BizTalk 解決方案的相關資訊，請參閱[工具測試](~/technical-guides/tools-for-testing.md)。</span><span class="sxs-lookup"><span data-stu-id="d1b6b-119">For information about tools that may be useful for load testing a BizTalk solution, see [Tools for Testing](~/technical-guides/tools-for-testing.md).</span></span> <span data-ttu-id="d1b6b-120">如需負載測試的考量的檢查清單，請參閱[執行載入及輸送量測試](../technical-guides/performing-load-and-throughput-testing.md)。</span><span class="sxs-lookup"><span data-stu-id="d1b6b-120">For a checklist of considerations for load testing see [Performing Load and Throughput Testing](../technical-guides/performing-load-and-throughput-testing.md).</span></span>  
  
## <a name="plan-to-test-for-the-lifetime-of-the-solution"></a><span data-ttu-id="d1b6b-121">測試計劃的存留期方案</span><span class="sxs-lookup"><span data-stu-id="d1b6b-121">Plan to Test for the Lifetime of the Solution</span></span>  
 <span data-ttu-id="d1b6b-122">而單元測試和負載測試是特別重要之方案的早期階段存留期中的方案以找出潛在的問題，可能會發生負載增加時，或是做為新功能或元件的一般測試計劃會加入至方案。</span><span class="sxs-lookup"><span data-stu-id="d1b6b-122">While unit testing and load testing are particularly important during the early stages of the solution, plan regular testing throughout the lifetime of the solution to uncover potential problems that may occur as load increases or as new functionality or components are added to the solution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1b6b-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1b6b-123">See Also</span></span>  
 <span data-ttu-id="d1b6b-124">[規劃 BizTalk Server 層](../technical-guides/planning-the-biztalk-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="d1b6b-124">[Planning the BizTalk Server Tier](../technical-guides/planning-the-biztalk-server-tier.md) </span></span>  
 [<span data-ttu-id="d1b6b-125">檢查清單： 測試操作整備</span><span class="sxs-lookup"><span data-stu-id="d1b6b-125">Checklist: Testing Operational Readiness</span></span>](../technical-guides/checklist-testing-operational-readiness.md)