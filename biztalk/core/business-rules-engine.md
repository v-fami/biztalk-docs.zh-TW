---
title: 商務規則引擎 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- business rules, Business Rules Engine
- Business Rules Engine
- Business Rules Engine, rules
- Business Rules Engine, about Business Rules Engine
ms.assetid: 87b38507-9f6d-4863-88a6-9c20f15a4e55
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d99cff10324f1cf1ba97d99431524474ed5f039b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232614"
---
# <a name="business-rules-engine"></a><span data-ttu-id="342b7-102">商務規則引擎</span><span class="sxs-lookup"><span data-stu-id="342b7-102">Business Rules Engine</span></span>
<span data-ttu-id="342b7-103">「商務規則架構」是一個 Microsoft .NET 相容的類別庫。</span><span class="sxs-lookup"><span data-stu-id="342b7-103">The Business Rules Framework is a Microsoft .NET-compliant class library.</span></span> <span data-ttu-id="342b7-104">它提供一個有效的推斷引擎，可將易讀、宣告式且語意豐富的規則連結到任何商務物件 (.NET 元件)、XML文件或資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="342b7-104">It provides an efficient inference engine that can link highly readable, declarative, semantically rich rules to any business objects (.NET components), XML documents, or database tables.</span></span> <span data-ttu-id="342b7-105">應用程式開發人員可從小型的商務邏輯建置區塊 (小型的規則集) 開始建構規則，以執行 .NET 物件、資料庫資料表和 XML 文件中包含的資訊 (事實)，以建立商務規則。</span><span class="sxs-lookup"><span data-stu-id="342b7-105">Application developers can build business rules by constructing rules from small building blocks of business logic (small rule sets) that operate on information (facts) contained in .NET objects, database tables, and XML documents.</span></span> <span data-ttu-id="342b7-106">此設計模式可提升程式碼重複使用率、簡化設計和商務邏輯的模組化程序。</span><span class="sxs-lookup"><span data-stu-id="342b7-106">This design pattern promotes code reuse, design simplicity, and modularity of business logic.</span></span> <span data-ttu-id="342b7-107">此外，規則引擎並非利用商務應用程式的架構或設計。</span><span class="sxs-lookup"><span data-stu-id="342b7-107">In addition, the rule engine does not impose on the architecture or design of business applications.</span></span> <span data-ttu-id="342b7-108">事實上，您可以直接叫用規則引擎將規則技術加入商務應用程式，或是取得叫用您的商務物件的外部邏輯，無需修改。</span><span class="sxs-lookup"><span data-stu-id="342b7-108">In fact, you can add rule technology to a business application by directly invoking the rule engine, or you can have external logic that invokes your business objects without modifying them.</span></span> <span data-ttu-id="342b7-109">總之，開發人員若採用該技術，只需耗費最少的精力便能建立和維護應用程式。</span><span class="sxs-lookup"><span data-stu-id="342b7-109">In short, the technology enables developers to create and maintain applications with minimal effort.</span></span>  
  
 <span data-ttu-id="342b7-110">在規劃開發規則應用程式方面，首先必須決定規則與商務程序要如何配合。</span><span class="sxs-lookup"><span data-stu-id="342b7-110">In planning development of a rule-based application, you first need to determine how rules will fit into your business processes.</span></span> <span data-ttu-id="342b7-111">應用程式將會建立原則的執行個體，並提供所要執行的資料或事實。</span><span class="sxs-lookup"><span data-stu-id="342b7-111">Your application will create an instance of a policy and supply it with data, or facts, on which to operate.</span></span> <span data-ttu-id="342b7-112">原則物件可封裝規則引擎，並提供透過其執行的單一進入點。</span><span class="sxs-lookup"><span data-stu-id="342b7-112">The policy object encapsulates the rule engine and provides a single point of entry through which to run it.</span></span>  
  
 <span data-ttu-id="342b7-113">您也必須規劃開發工作和測試所設計的規則。</span><span class="sxs-lookup"><span data-stu-id="342b7-113">You also will need to plan for the development and testing of your rules design.</span></span> <span data-ttu-id="342b7-114">還必須考慮如何部署和更新您的原則。</span><span class="sxs-lookup"><span data-stu-id="342b7-114">You must consider how you are going to deploy and update your policies.</span></span> <span data-ttu-id="342b7-115">您很可能想要追蹤規則引擎的執行進度和監控目前的狀態。</span><span class="sxs-lookup"><span data-stu-id="342b7-115">You will likely want to track the progress of your rule engine's execution and monitor its current state.</span></span>  
  
 <span data-ttu-id="342b7-116">規劃您的規則開發工作時，請說明下列步驟：</span><span class="sxs-lookup"><span data-stu-id="342b7-116">Account for the following steps as you plan your rules development:</span></span>  
  
1.  <span data-ttu-id="342b7-117">規劃如何將規則併入應用程式。</span><span class="sxs-lookup"><span data-stu-id="342b7-117">Plan how to incorporate your rules into your application.</span></span>  
  
2.  <span data-ttu-id="342b7-118">識別想要在應用程式中以規則表示的商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="342b7-118">Identify the business logic that you want to represent with rules in your application.</span></span> <span data-ttu-id="342b7-119">「商務邏輯」一詞可指許多事情；「超過五百美元的訂單均必須由經理核准」即為商務邏輯的一個範例。</span><span class="sxs-lookup"><span data-stu-id="342b7-119">The term "business logic" can refer to many things; an example of business logic is "Purchase orders for more than five hundred dollars must be approved by a manager."</span></span>  
  
3.  <span data-ttu-id="342b7-120">識別規則項目的資料來源。</span><span class="sxs-lookup"><span data-stu-id="342b7-120">Identify data sources for your rule elements.</span></span> <span data-ttu-id="342b7-121">您可以選擇性地定義和發佈詞彙 (表示基礎繫結的網域特有術語表)。</span><span class="sxs-lookup"><span data-stu-id="342b7-121">You can optionally define and publish vocabularies (domain-specific nomenclature that represents underlying bindings).</span></span>  
  
4.  <span data-ttu-id="342b7-122">從詞彙定義或直接從資料繫結來定義規則，然後再由規則來編輯代表商務邏輯的原則。</span><span class="sxs-lookup"><span data-stu-id="342b7-122">Define rules from vocabulary definitions or directly from data bindings, and from them compose a policy that represents your business logic.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="342b7-123">必須先發佈詞彙，才能在規則中套用詞彙。</span><span class="sxs-lookup"><span data-stu-id="342b7-123">Vocabularies must be published before they can be applied in rules.</span></span>  
  
5.  <span data-ttu-id="342b7-124">以事實範例測試原則並進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="342b7-124">Test and debug the policy with sample facts.</span></span> <span data-ttu-id="342b7-125">您可以使用 「 商務規則編輯器 」 測試原則功能，或使用**原則**或**PolicyTester**從應用程式、 命令列程式或協調流程執行的類別。</span><span class="sxs-lookup"><span data-stu-id="342b7-125">You can either use the Test Policy functionality in the Business Rule Composer or use **Policy** or **PolicyTester** classes to execute from an application, command-line program, or orchestration.</span></span>  
  
6.  <span data-ttu-id="342b7-126">將原則版本發佈至規則存放區。</span><span class="sxs-lookup"><span data-stu-id="342b7-126">Publish the policy version to the rule store.</span></span>  
  
7.  <span data-ttu-id="342b7-127">部署原則版本。</span><span class="sxs-lookup"><span data-stu-id="342b7-127">Deploy the policy version.</span></span>  
  
8.  <span data-ttu-id="342b7-128">在裝載的應用程式中產生和建置短期事實清單。</span><span class="sxs-lookup"><span data-stu-id="342b7-128">Instantiate and build the short-term fact list in the hosting application.</span></span> <span data-ttu-id="342b7-129">使用**呼叫規則**執行商務原則，或以程式設計方式產生原則版本裝載的應用程式中使用協調流程。</span><span class="sxs-lookup"><span data-stu-id="342b7-129">Use the **Call Rules** shape in an orchestration to execute your business policy or programmatically instantiate a policy version in your hosting application.</span></span>  
  
9. <span data-ttu-id="342b7-130">視需要監控和追蹤規則執行。</span><span class="sxs-lookup"><span data-stu-id="342b7-130">Monitor and track rule execution as needed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="342b7-131">預設的追蹤攔截器可搭配協調流程使用。</span><span class="sxs-lookup"><span data-stu-id="342b7-131">The default tracking interceptor works with orchestrations.</span></span> <span data-ttu-id="342b7-132">若您裝載的應用程式並非協調流程，則必須撰寫自訂的追蹤攔截器來執行此項工作。</span><span class="sxs-lookup"><span data-stu-id="342b7-132">If your hosting application is not an orchestration, you must write your own tracking interceptor to do this.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="342b7-133">本節內容</span><span class="sxs-lookup"><span data-stu-id="342b7-133">In This Section</span></span>  
  
-   [<span data-ttu-id="342b7-134">規則</span><span class="sxs-lookup"><span data-stu-id="342b7-134">Rules</span></span>](../core/rules.md)  
  
-   [<span data-ttu-id="342b7-135">原則</span><span class="sxs-lookup"><span data-stu-id="342b7-135">Policies</span></span>](../core/policies.md)  
  
-   [<span data-ttu-id="342b7-136">詞彙</span><span class="sxs-lookup"><span data-stu-id="342b7-136">Vocabularies</span></span>](../core/vocabularies.md)  
  
-   [<span data-ttu-id="342b7-137">商務規則架構的架構</span><span class="sxs-lookup"><span data-stu-id="342b7-137">Business Rules Framework Architecture</span></span>](../core/business-rules-framework-architecture.md)  
  
-   [<span data-ttu-id="342b7-138">事實</span><span class="sxs-lookup"><span data-stu-id="342b7-138">Facts</span></span>](../core/facts.md)  
  
-   [<span data-ttu-id="342b7-139">規則引擎</span><span class="sxs-lookup"><span data-stu-id="342b7-139">Rule Engine</span></span>](../core/rule-engine.md)