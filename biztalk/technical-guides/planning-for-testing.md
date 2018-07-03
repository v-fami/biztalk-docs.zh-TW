---
title: 規劃測試 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ca2f5f29-9eea-4f4d-9781-75c231db4605
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b386ee074538af7960ca39bfb50c25ac59df1dbb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010279"
---
# <a name="planning-for-testing"></a><span data-ttu-id="9bc3d-102">規劃測試</span><span class="sxs-lookup"><span data-stu-id="9bc3d-102">Planning for Testing</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9bc3d-103"> 測試可以分成幾個類別，包括單元測試、 功能性測試、 負載測試，及可用性測試。</span><span class="sxs-lookup"><span data-stu-id="9bc3d-103"> testing can be divided into several categories including unit testing, functional testing, load testing, and availability testing.</span></span> <span data-ttu-id="9bc3d-104">本主題描述單位與負載測試，以及如何針對每個計劃。</span><span class="sxs-lookup"><span data-stu-id="9bc3d-104">This topic describes unit and load testing and how to plan for each.</span></span>  
  
## <a name="planning-for-unit-testing"></a><span data-ttu-id="9bc3d-105">單元測試計劃</span><span class="sxs-lookup"><span data-stu-id="9bc3d-105">Planning for Unit Testing</span></span>  
 <span data-ttu-id="9bc3d-106">單元測試是用來驗證該個別程式碼單位的程序依照設計運作。</span><span class="sxs-lookup"><span data-stu-id="9bc3d-106">Unit testing is a procedure used to validate that individual units of code are working as designed.</span></span> <span data-ttu-id="9bc3d-107">單元測試可以視為 「 協助修正 」 測試： 軟體不會執行所需的功能，在不同情況下，可以在這些情況下會發生軟體處理錯誤？</span><span class="sxs-lookup"><span data-stu-id="9bc3d-107">Unit testing can be thought of as "break/fix" testing: Does the software perform the desired functionality under different conditions and can the software handle errors that occur under these conditions?</span></span>  
  
 <span data-ttu-id="9bc3d-108">單元測試通常在個別的元件上執行，因為相關聯的測試平台不需要實際的生產環境的處理能力。</span><span class="sxs-lookup"><span data-stu-id="9bc3d-108">Since unit testing is typically performed on individual components, the associated test bed does not need the processing capabilities of an actual production environment.</span></span> <span data-ttu-id="9bc3d-109">基於這個理由，您應該考慮執行單元測試在虛擬伺服器環境中，這需要大幅較少的硬體資源。</span><span class="sxs-lookup"><span data-stu-id="9bc3d-109">For this reason, you should consider performing unit testing in a Virtual Server environment, which requires considerably fewer hardware resources.</span></span>  
  
 <span data-ttu-id="9bc3d-110">單元測試的可能執行虛擬化環境中的另一個層面預備環境。</span><span class="sxs-lookup"><span data-stu-id="9bc3d-110">Another aspect of unit testing that may be performed in a virtualized environment is staging.</span></span> <span data-ttu-id="9bc3d-111">預備環境是單元測試實際部署 BizTalk 解決方案的程序。</span><span class="sxs-lookup"><span data-stu-id="9bc3d-111">Staging is the process of unit testing the actual deployment of a BizTalk solution.</span></span> <span data-ttu-id="9bc3d-112">若要充分利用可用的硬體資源，請考慮使用 Virtual Server 進行您的預備環境。</span><span class="sxs-lookup"><span data-stu-id="9bc3d-112">To maximize available hardware resources, consider using Virtual Server for your staging environment.</span></span>  
  
 <span data-ttu-id="9bc3d-113">如需使用詳細資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在虛擬環境中，請參閱[使用虛擬伺服器期間發行管理程序](../technical-guides/planning-the-development-testing-staging-and-production-environments.md#BKMK_VirtualServ)。</span><span class="sxs-lookup"><span data-stu-id="9bc3d-113">For more information about using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a virtual environment, see [Using Virtual Server During the Release Management Process](../technical-guides/planning-the-development-testing-staging-and-production-environments.md#BKMK_VirtualServ).</span></span> <span data-ttu-id="9bc3d-114">可能是適用於單元測試 BizTalk 解決方案的工具的相關資訊，請參閱[工具測試](~/technical-guides/tools-for-testing.md)。</span><span class="sxs-lookup"><span data-stu-id="9bc3d-114">For information about tools that may be useful for unit testing a BizTalk solution, see [Tools for Testing](~/technical-guides/tools-for-testing.md).</span></span> <span data-ttu-id="9bc3d-115">如需執行單元測試的考量事項的檢查清單，請參閱[執行單元測試](../technical-guides/performing-unit-testing.md)。</span><span class="sxs-lookup"><span data-stu-id="9bc3d-115">For a checklist of considerations for performing unit testing see [Performing Unit Testing](../technical-guides/performing-unit-testing.md).</span></span>  
  
## <a name="planning-for-load-testing"></a><span data-ttu-id="9bc3d-116">規劃負載測試</span><span class="sxs-lookup"><span data-stu-id="9bc3d-116">Planning for Load Testing</span></span>  
 <span data-ttu-id="9bc3d-117">負載測試是測量的最大持續性效能和最大持續性追蹤的 BizTalk 解決方案的效能，然後再移除禁止解決方案的輸送量的瓶頸的程序。</span><span class="sxs-lookup"><span data-stu-id="9bc3d-117">Load testing is the process of measuring maximum sustainable performance and maximum sustainable tracking performance of a BizTalk solution and then removing bottlenecks that inhibit the throughput of the solution.</span></span> <span data-ttu-id="9bc3d-118">如需有關負載測試，並移除從瓶頸[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]解決方案，請參閱 < [BizTalk Server 2009 效能指南](http://go.microsoft.com/fwlink/?LinkID=150492)(<http://go.microsoft.com/fwlink/?LinkID=150492>)。</span><span class="sxs-lookup"><span data-stu-id="9bc3d-118">For more information about load testing and removing bottlenecks from a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution, see the [BizTalk Server 2009 Performance Guide](http://go.microsoft.com/fwlink/?LinkID=150492) (<http://go.microsoft.com/fwlink/?LinkID=150492>).</span></span>  
  
 <span data-ttu-id="9bc3d-119">可能是適用於負載測試 BizTalk 解決方案的工具的相關資訊，請參閱[工具測試](~/technical-guides/tools-for-testing.md)。</span><span class="sxs-lookup"><span data-stu-id="9bc3d-119">For information about tools that may be useful for load testing a BizTalk solution, see [Tools for Testing](~/technical-guides/tools-for-testing.md).</span></span> <span data-ttu-id="9bc3d-120">如需負載測試的考量的檢查清單[執行載入和輸送量測試](../technical-guides/performing-load-and-throughput-testing.md)。</span><span class="sxs-lookup"><span data-stu-id="9bc3d-120">For a checklist of considerations for load testing see [Performing Load and Throughput Testing](../technical-guides/performing-load-and-throughput-testing.md).</span></span>  
  
## <a name="plan-to-test-for-the-lifetime-of-the-solution"></a><span data-ttu-id="9bc3d-121">規劃測試解決方案的存留期</span><span class="sxs-lookup"><span data-stu-id="9bc3d-121">Plan to Test for the Lifetime of the Solution</span></span>  
 <span data-ttu-id="9bc3d-122">雖然單元測試和負載測試是特別重要之方案的早期階段存留期的方案，以找出潛在的問題，可能會發生負載增加時，或為新功能或元件的一般測試計劃會加入至方案。</span><span class="sxs-lookup"><span data-stu-id="9bc3d-122">While unit testing and load testing are particularly important during the early stages of the solution, plan regular testing throughout the lifetime of the solution to uncover potential problems that may occur as load increases or as new functionality or components are added to the solution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bc3d-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bc3d-123">See Also</span></span>  
 <span data-ttu-id="9bc3d-124">[規劃 BizTalk Server 層](../technical-guides/planning-the-biztalk-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="9bc3d-124">[Planning the BizTalk Server Tier](../technical-guides/planning-the-biztalk-server-tier.md) </span></span>  
 [<span data-ttu-id="9bc3d-125">檢查清單：測試作業整備</span><span class="sxs-lookup"><span data-stu-id="9bc3d-125">Checklist: Testing Operational Readiness</span></span>](../technical-guides/checklist-testing-operational-readiness.md)