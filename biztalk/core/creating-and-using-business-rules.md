---
title: 建立和使用商務規則 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- business rules, Business Rules Editor
- Business Rules Editor
ms.assetid: a15fd09b-ff4e-4c26-8cb6-5ffd258a2182
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31925296de1e9c6f017e2447e0dccfd699ac177c
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50752550"
---
# <a name="creating-and-using-business-rules"></a><span data-ttu-id="5ecf5-102">建立和使用商務規則</span><span class="sxs-lookup"><span data-stu-id="5ecf5-102">Creating and Using Business Rules</span></span>
<span data-ttu-id="5ecf5-103">商務規則 (或商務原則) 會定義及控制組織的結構、作業和策略。</span><span class="sxs-lookup"><span data-stu-id="5ecf5-103">Business rules (or business policies) define and control the structure, operation, and strategy of an organization.</span></span> <span data-ttu-id="5ecf5-104">商務規則可能會正式定義在程序手冊、合約或協定中，也可能以知識或專業技術的形式來由員工呈現。</span><span class="sxs-lookup"><span data-stu-id="5ecf5-104">Business rules may be formally defined in procedure manuals, contracts, or agreements, or may exist as knowledge or expertise embodied in employees.</span></span> <span data-ttu-id="5ecf5-105">商務規則是動態的，會隨著時間而改變，而且可以在所有類型的應用程式中找到。</span><span class="sxs-lookup"><span data-stu-id="5ecf5-105">Business rules are dynamic and subject to change over time, and can be found in all types of applications.</span></span> <span data-ttu-id="5ecf5-106">在商務規則所控管的許多商務領域中，金融保險、電子商務、運輸、電信、Web 服務和個人化只是其中的幾項。</span><span class="sxs-lookup"><span data-stu-id="5ecf5-106">Finance and insurance, e-business, transportation, telecommunications, Web-based services, and personalization are just a few of the many business domains that are governed by business rules.</span></span> <span data-ttu-id="5ecf5-107">每一個商務領域都需要傳達商業策略、原則和規章給資訊技術 (IT) 人員，將這些資訊加入到軟體應用程式中。</span><span class="sxs-lookup"><span data-stu-id="5ecf5-107">Each of these business domains shares the need to convey business strategies, policies, and regulations to information technology (IT) personnel for inclusion into software applications.</span></span>  
  
 <span data-ttu-id="5ecf5-108">傳統的程序和物件導向程式語言 (如 C、C++ 和 Microsoft Visual Basic) 都是程式設計人員導向。</span><span class="sxs-lookup"><span data-stu-id="5ecf5-108">Traditional procedural and object-oriented programming languages, such as C, C++, and Microsoft Visual Basic, are oriented towards programmers.</span></span> <span data-ttu-id="5ecf5-109">更進階的物件導向語言 (如 Java 和 C#) 仍然是程式設計人員主要使用的語言。</span><span class="sxs-lookup"><span data-stu-id="5ecf5-109">Even advanced object-oriented languages, such as Java and C#, are still primarily programmers' languages.</span></span> <span data-ttu-id="5ecf5-110">傳統的軟體開發週期 (包括設計、開發、編譯和測試) 需要大量的時間和協調工作，而且無法讓非程式設計人員參與自動化商務原則的維護工作。</span><span class="sxs-lookup"><span data-stu-id="5ecf5-110">The traditional software development cycle of design, develop, compile, and test requires substantial time and coordination, and does not enable nonprogrammers to participate in the maintenance of automated business policies.</span></span> <span data-ttu-id="5ecf5-111">為了對付這個問題，商務規則架構提供了一個開發環境，可讓您快速建立應用程式，而不需要傳統應用程式設計所需的冗長週期。</span><span class="sxs-lookup"><span data-stu-id="5ecf5-111">The Business Rules Framework addresses this problem by providing a development environment that allows rapid application creation without the lengthy cycle of traditional application programming.</span></span> <span data-ttu-id="5ecf5-112">例如，當更新使用這個架構所建構的商務規則時，可以不需要重新編譯及重新部署關聯的協調流程。</span><span class="sxs-lookup"><span data-stu-id="5ecf5-112">For example, business policies constructed by using this framework can be updated without recompiling and redeploying the associated orchestrations.</span></span>  
  
 <span data-ttu-id="5ecf5-113">商務規則架構與 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 緊密整合在一起，而且開發人員可以使用下列功能來建置及管理商務規則：</span><span class="sxs-lookup"><span data-stu-id="5ecf5-113">The Business Rules Framework is tightly integrated with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and developers can use the following features to build and manage business rules:</span></span>  
  
- <span data-ttu-id="5ecf5-114">高效能的規則引擎，可實作推斷機制來評估商務規則。</span><span class="sxs-lookup"><span data-stu-id="5ecf5-114">A high-performance rule engine that implements an inference mechanism to evaluate the business rules.</span></span>  
  
- <span data-ttu-id="5ecf5-115">一組豐富的應用程式發展介面 (API)，可用來開發以規則為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5ecf5-115">A rich set of application programming interfaces (APIs) for developing rule-based applications.</span></span>  
  
- <span data-ttu-id="5ecf5-116">一個圖形化使用者介面 (商務規則編輯器)，開發人員、商務分析師及系統管理員可透過各種方式來使用此介面，以便有效率地開發及套用規則與原則。</span><span class="sxs-lookup"><span data-stu-id="5ecf5-116">A graphical user interface, the Business Rule Composer, which developers, business analysts, and administrators can use in various ways to efficiently develop and apply rules and policies.</span></span>  
  
- <span data-ttu-id="5ecf5-117">與 BizTalk 協調流程緊密整合，可讓您從 BizTalk 協調流程叫用商務原則或一組商務規則。</span><span class="sxs-lookup"><span data-stu-id="5ecf5-117">A seamless integration with BizTalk orchestrations, which enables you to invoke a business policy or a set of business rules from a BizTalk orchestration.</span></span>  
  
- <span data-ttu-id="5ecf5-118">「規則引擎部署精靈」，可讓您快速地匯入或匯出商務規則或規則所使用的詞彙，以及部署或解除部署這些規則。</span><span class="sxs-lookup"><span data-stu-id="5ecf5-118">The Rule Engine Deployment Wizard, which enables you to rapidly import or export business rules or the vocabularies used by the rules, as well as to deploy or undeploy these rules.</span></span>  
  
  <span data-ttu-id="5ecf5-119">您透過商務規則架構所建立的商務規則 (原則) 可用於協調的商務程序中，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="5ecf5-119">The business rules (policy) you create by using the Business Rules Framework can be used in an orchestrated business process, as shown in the following figure.</span></span>  
  
  <span data-ttu-id="5ecf5-120">![此圖表顯示在程序中的商務原則。](../core/media/ebiz-dev-busprcsi.gif "ebiz_dev_busprcsi")</span><span class="sxs-lookup"><span data-stu-id="5ecf5-120">![Diagram showing business policy in process.](../core/media/ebiz-dev-busprcsi.gif "ebiz_dev_busprcsi")</span></span>  
  <span data-ttu-id="5ecf5-121">商務原則</span><span class="sxs-lookup"><span data-stu-id="5ecf5-121">Business Policy</span></span>  
  
  <span data-ttu-id="5ecf5-122">本章節提供一些概念性資訊，讓您瞭解如何利用商務規則架構及使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供的工具來開發商務規則。</span><span class="sxs-lookup"><span data-stu-id="5ecf5-122">This section provides conceptual information about how you can leverage the Business Rules Framework and use the tools that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides to develop business rules.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5ecf5-123">本節內容</span><span class="sxs-lookup"><span data-stu-id="5ecf5-123">In This Section</span></span>  
  
-   [<span data-ttu-id="5ecf5-124">建立商務規則</span><span class="sxs-lookup"><span data-stu-id="5ecf5-124">Creating Business Rules</span></span>](../core/creating-business-rules-using-the-business-rule-composer.md)  
  
-   [<span data-ttu-id="5ecf5-125">商務規則架構安全性</span><span class="sxs-lookup"><span data-stu-id="5ecf5-125">Business Rules Framework Security</span></span>](../core/business-rules-framework-security.md)  
  
-   [<span data-ttu-id="5ecf5-126">使用商務規則架構設計程式</span><span class="sxs-lookup"><span data-stu-id="5ecf5-126">Programming with Business Rules Framework</span></span>](../core/programming-with-business-rules-framework.md)  
  
-   [<span data-ttu-id="5ecf5-127">規則引擎設定和調整參數</span><span class="sxs-lookup"><span data-stu-id="5ecf5-127">Rule Engine Configuration and Tuning Parameters</span></span>](../core/rule-engine-configuration-and-tuning-parameters.md)
