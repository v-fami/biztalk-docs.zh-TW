---
title: 商務規則架構的架構 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Business Rules Framework, caching
- Business Rules Framework, Rule Engine Update service
- rule store [Business Rules Framework]
- Policy class [Business Rules Engine]
- Business Rules Framework, architecture
- Business Rules Framework, RuleEngine class
- Business Rules Framework, Policy class
- Business Rules Framework, authoring tools
- RuleEngine class [Business Rules Engine]
- caching, Business Rules Framework
- Business Rules Framework, fact retrievers
- architecture, Business Rules Framework
- Business Rules Framework, rule store
ms.assetid: f5570cca-7664-4180-af9c-64ef90a0022b
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4b23723d01a29606637689966cc07246cdfbc1d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233870"
---
# <a name="business-rules-framework-architecture"></a><span data-ttu-id="59d42-102">商務規則架構的架構</span><span class="sxs-lookup"><span data-stu-id="59d42-102">Business Rules Framework Architecture</span></span>
<span data-ttu-id="59d42-103">下圖顯示「商務規則架構」的元件架構。</span><span class="sxs-lookup"><span data-stu-id="59d42-103">The following figure shows the component architecture of the Business Rules Framework.</span></span>  
  
 <span data-ttu-id="59d42-104">![商務規則架構的元件架構](../core/media/ebiz-rulesarch-new.gif "ebiz_rulesarch_new")</span><span class="sxs-lookup"><span data-stu-id="59d42-104">![Business Rules Framework component architecture](../core/media/ebiz-rulesarch-new.gif "ebiz_rulesarch_new")</span></span>  
<span data-ttu-id="59d42-105">「Microsoft 商務規則架構」的架構</span><span class="sxs-lookup"><span data-stu-id="59d42-105">Microsoft Business Rules Framework Architecture</span></span>  
  
 <span data-ttu-id="59d42-106">架構的部分元件會在下列段落中描述。</span><span class="sxs-lookup"><span data-stu-id="59d42-106">Some of the components of the framework are described in the following paragraphs.</span></span>  
  
## <a name="policy-class"></a><span data-ttu-id="59d42-107">原則類別</span><span class="sxs-lookup"><span data-stu-id="59d42-107">Policy Class</span></span>  
 <span data-ttu-id="59d42-108">A**原則**物件是為商務原則的單一執行個體，並提供以規則為基礎的應用程式所使用的介面。</span><span class="sxs-lookup"><span data-stu-id="59d42-108">A **Policy** object is a single instance of a business policy, and provides the interface that is used by rule-based applications.</span></span> <span data-ttu-id="59d42-109">它提供的抽象概念可以讓應用程式開發人員無需顧慮以下事項：規則存放區位置、從規則存放區擷取規則集、產生基礎規則引擎的執行個體，並確保長期事實會判斷提示至引擎。</span><span class="sxs-lookup"><span data-stu-id="59d42-109">It provides an abstraction that frees the application developer from concern about the location of the rule store, extracting rule sets from the rule store, instantiating instances of the underlying rule engine, and ensuring that long-term facts are asserted into the engine.</span></span> <span data-ttu-id="59d42-110">在許多案例中，以規則為基礎的應用程式會使用並行的執行個體的**原則**物件。</span><span class="sxs-lookup"><span data-stu-id="59d42-110">In many scenarios, a rule-based application uses concurrent instances of the **Policy** object.</span></span> <span data-ttu-id="59d42-111">這些並行執行個體可以代表相同原則、不同版本的相同原則，或是不同版本的不同原則。</span><span class="sxs-lookup"><span data-stu-id="59d42-111">These concurrent instances can represent the same policy, different versions of the same policy, or different versions of different policies.</span></span>  
  
## <a name="ruleengine-class"></a><span data-ttu-id="59d42-112">RuleEngine 類別</span><span class="sxs-lookup"><span data-stu-id="59d42-112">RuleEngine Class</span></span>  
 <span data-ttu-id="59d42-113">**RuleEngine**物件做為商務原則的執行引擎。</span><span class="sxs-lookup"><span data-stu-id="59d42-113">The **RuleEngine** object serves as the execution engine for business policies.</span></span> <span data-ttu-id="59d42-114">它會使用三個外掛程式元件 (轉譯程式、介面引擎和追蹤攔截器) 以進行實作。</span><span class="sxs-lookup"><span data-stu-id="59d42-114">It uses three plug-in components (translator, inference engine, and tracking interceptor) for implementation.</span></span> <span data-ttu-id="59d42-115">A **RuleEngine**物件會使用**RuleSet**物件代表商務原則做為輸入，並使用轉譯程式、 介面引擎和設定規則集來實作的追蹤攔截器規則集所定義的商務原則。</span><span class="sxs-lookup"><span data-stu-id="59d42-115">A **RuleEngine** object takes a **RuleSet** object representing a business policy as input and uses the translator, inference engine, and tracking interceptor configured for the rule set to implement the business policy defined by the rule set.</span></span>  
  
## <a name="fact-retriever"></a><span data-ttu-id="59d42-116">事實擷取器</span><span class="sxs-lookup"><span data-stu-id="59d42-116">Fact Retriever</span></span>  
 <span data-ttu-id="59d42-117">事實擷取器是一個選擇性、使用者定義的外掛程式元件，負責收集長期事實以供商務原則使用。</span><span class="sxs-lookup"><span data-stu-id="59d42-117">A fact retriever is an optional, user-defined, plug-in component that is responsible for gathering long-term facts for use by business policies.</span></span> <span data-ttu-id="59d42-118">如需詳細資訊，請參閱[如何建立事實擷取器](../core/how-to-create-a-fact-retriever.md)。</span><span class="sxs-lookup"><span data-stu-id="59d42-118">For more information, see [How to Create a Fact Retriever](../core/how-to-create-a-fact-retriever.md).</span></span>  
  
 <span data-ttu-id="59d42-119">在執行之前，**原則**物件執行個體會提供其**RuleEngine**事實擷取器，並賦予它機會來更新的規則引擎中的事實集的執行個體的工作記憶體。</span><span class="sxs-lookup"><span data-stu-id="59d42-119">Before execution, a **Policy** object instance provides its **RuleEngine** instance to the fact retriever, giving it the opportunity to update the set of facts in the rule engine's working memory.</span></span> <span data-ttu-id="59d42-120">如需詳細資訊，請參閱[短期事實與。長期事實](../core/short-term-facts-vs-long-term-facts.md)。</span><span class="sxs-lookup"><span data-stu-id="59d42-120">For more information, see [Short-Term Facts vs. Long-Term Facts](../core/short-term-facts-vs-long-term-facts.md).</span></span>  
  
## <a name="rule-engine-update-service"></a><span data-ttu-id="59d42-121">規則引擎更新服務</span><span class="sxs-lookup"><span data-stu-id="59d42-121">Rule Engine Update Service</span></span>  
 <span data-ttu-id="59d42-122">「規則引擎更新」服務會在分散式環境中提供動態商務原則更新。</span><span class="sxs-lookup"><span data-stu-id="59d42-122">The Rule Engine Update service provides dynamic business policy updates in a distributed environment.</span></span> <span data-ttu-id="59d42-123">自動啟動的 Microsoft Windows NT 服務應用程式會負責訂閱原則部署和解除部署變更商務原則時，會發生的事件。</span><span class="sxs-lookup"><span data-stu-id="59d42-123">An autostart Microsoft Windows NT service application is responsible for subscribing to policy deployment and undeployment events that occur when business policies are changed.</span></span>  
  
 <span data-ttu-id="59d42-124">在一般的企業實例中，商務原則會在更新、測試和版本建立之後，進行部署。</span><span class="sxs-lookup"><span data-stu-id="59d42-124">In a typical enterprise scenario, business policies are deployed after being updated, tested, and versioned.</span></span> <span data-ttu-id="59d42-125">部署包含將已更新的原則新增到安全且持續性的規則存放區，以及選擇性地在存放區上執行邏輯，以便將已更新原則的相關資訊發佈給所有感興趣的合作對象 (請注意，是發佈原則的相關資訊而非原則本身)。</span><span class="sxs-lookup"><span data-stu-id="59d42-125">Deployment consists of adding the updated policy to a secure, persistent rule store and optionally executing logic on the store to publish information about the updated policy to all interested parties (note that information about the policy is published and not the policy itself).</span></span>  
  
 <span data-ttu-id="59d42-126">在裝載以規則為基礎之應用程式的伺服器上執行的「規則引擎更新」服務，會接收原則更新通知，並快取資訊以供後續使用。</span><span class="sxs-lookup"><span data-stu-id="59d42-126">The Rule Engine Update service, running on a server hosting rule-based applications, receives the policy update notification and caches the information for subsequent use.</span></span> <span data-ttu-id="59d42-127">使用 pub/sub 模型以進行原則更新，可以讓您以近乎即時的方式變更商務原則，而不需將服務停機或中斷。</span><span class="sxs-lookup"><span data-stu-id="59d42-127">The use of a pub/sub model for policy updates enables you to change business policies in near real time without service downtime or interruption.</span></span>  
  
## <a name="policyvocabulary-authoring-tools"></a><span data-ttu-id="59d42-128">原則/詞彙撰寫工具</span><span class="sxs-lookup"><span data-stu-id="59d42-128">Policy/Vocabulary Authoring Tools</span></span>  
 <span data-ttu-id="59d42-129">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的「商務規則編輯器」，會提供原則與詞彙撰寫功能給一般使用者與開發人員。</span><span class="sxs-lookup"><span data-stu-id="59d42-129">The Business Rule Composer in Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides policy and vocabulary authoring capabilities to both end users and developers.</span></span>  
  
## <a name="rule-store"></a><span data-ttu-id="59d42-130">規則存放區</span><span class="sxs-lookup"><span data-stu-id="59d42-130">Rule Store</span></span>  
 <span data-ttu-id="59d42-131">A*規則存放區*是商務原則與詞彙的儲存機制。</span><span class="sxs-lookup"><span data-stu-id="59d42-131">A *rule store* is a repository for business policies and vocabularies.</span></span> <span data-ttu-id="59d42-132">儲存機制可以是簡單的檔案或安全、 可擴充、 持續性，且可靠的資料庫，例如 Microsoft SQL Server。</span><span class="sxs-lookup"><span data-stu-id="59d42-132">The repository can be a simple file or a secure, scalable, persistent, and reliable database such as Microsoft SQL Server.</span></span> <span data-ttu-id="59d42-133">(SQL Server 可做為架構的預設規則存放區)。</span><span class="sxs-lookup"><span data-stu-id="59d42-133">(SQL Server is used as the default rule store for the framework).</span></span>  
  
## <a name="caching"></a><span data-ttu-id="59d42-134">快取</span><span class="sxs-lookup"><span data-stu-id="59d42-134">Caching</span></span>  
 <span data-ttu-id="59d42-135">商務規則引擎架構提供的快取機制**RuleEngine**執行個體。</span><span class="sxs-lookup"><span data-stu-id="59d42-135">The Business Rules Engine Framework provides a caching mechanism for **RuleEngine** instances.</span></span> <span data-ttu-id="59d42-136">每個**RuleEngine**執行個體包含特定的原則版本的記憶體中表示。</span><span class="sxs-lookup"><span data-stu-id="59d42-136">Each **RuleEngine** instance contains an in-memory representation of a specific policy version.</span></span>  
  
 <span data-ttu-id="59d42-137">下列步驟說明在新的程序**原則**具現化執行個體 (不是執行的應用程式開發介面上呼叫**呼叫規則**圖形):</span><span class="sxs-lookup"><span data-stu-id="59d42-137">The following steps describe the process when a new **Policy** instance is instantiated (either with a call on the API or execution of the **Call Rules** shape):</span></span>  
  
1.  <span data-ttu-id="59d42-138">**原則**物件要求**RuleEngine**從規則引擎快取的執行個體。</span><span class="sxs-lookup"><span data-stu-id="59d42-138">The **Policy** object requests a **RuleEngine** instance from the rule engine cache.</span></span>  
  
2.  <span data-ttu-id="59d42-139">如果**RuleEngine**原則版本存在於快取中，執行個體**RuleEngine**來傳回執行個體**原則**物件。</span><span class="sxs-lookup"><span data-stu-id="59d42-139">If a **RuleEngine** instance for the policy version exists in the cache, the **RuleEngine** instance is returned to the **Policy** object.</span></span> <span data-ttu-id="59d42-140">如果**RuleEngine**執行個體無法使用，快取建立的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="59d42-140">If a **RuleEngine** instance is not available, the cache creates a new instance.</span></span> <span data-ttu-id="59d42-141">當**RuleEngine**具現化執行個體，並不會接著，建立新的事實擷取器執行個體，如果已設定的原則版本。</span><span class="sxs-lookup"><span data-stu-id="59d42-141">When a **RuleEngine** instance is instantiated, it does, in turn, create a new fact retriever instance if one is configured for the policy version.</span></span>  
  
 <span data-ttu-id="59d42-142">當**Execute**上呼叫方法**原則**物件時，會發生下列步驟：</span><span class="sxs-lookup"><span data-stu-id="59d42-142">When the **Execute** method is called on the **Policy** object, the following steps occur:</span></span>  
  
1.  <span data-ttu-id="59d42-143">原則物件呼叫**UpdateFacts**事實擷取器是否有事實擷取器執行個體上的方法。</span><span class="sxs-lookup"><span data-stu-id="59d42-143">The Policy object calls the **UpdateFacts**method on the fact retriever instance if a fact retriever exists.</span></span> <span data-ttu-id="59d42-144">事實擷取器實作的方法可能會長期事實判斷提示至工作記憶體**RuleEngine**。</span><span class="sxs-lookup"><span data-stu-id="59d42-144">The fact retriever's implementation of the method may assert long term facts into the working memory of the **RuleEngine**.</span></span>  
  
2.  <span data-ttu-id="59d42-145">**原則**物件會判斷提示中所包含的短期事實**陣列**傳入**Execute**呼叫。</span><span class="sxs-lookup"><span data-stu-id="59d42-145">The **Policy** object asserts the short term facts contained in the **Array** that was passed in the **Execute** call.</span></span>  
  
3.  <span data-ttu-id="59d42-146">**原則**物件會呼叫**Execute**上**RuleEngine**。</span><span class="sxs-lookup"><span data-stu-id="59d42-146">The **Policy** object calls **Execute** on the **RuleEngine**.</span></span>  
  
4.  <span data-ttu-id="59d42-147">**RuleEngine**完成執行，並會將控制傳回**原則**物件。</span><span class="sxs-lookup"><span data-stu-id="59d42-147">The **RuleEngine** completes execution and returns control to the **Policy**object.</span></span>  
  
5.  <span data-ttu-id="59d42-148">**原則**物件會撤回短期事實從**RuleEngine**。</span><span class="sxs-lookup"><span data-stu-id="59d42-148">The**Policy**object retracts the short term facts from the **RuleEngine**.</span></span> <span data-ttu-id="59d42-149">由事實擷取器所判斷提示的長期事實將保留於規則引擎的工作記憶體中。</span><span class="sxs-lookup"><span data-stu-id="59d42-149">The long term facts asserted by the fact retriever will remain in the working memory of the rule engine.</span></span>  
  
 <span data-ttu-id="59d42-150">之後**處置**上呼叫方法**原則**物件**RuleEngine**執行個體釋回規則引擎快取。</span><span class="sxs-lookup"><span data-stu-id="59d42-150">After the **Dispose** method is called on the **Policy** object, the **RuleEngine** instance is released back to the rule engine cache.</span></span>  
  
 <span data-ttu-id="59d42-151">規則引擎快取將會有多個指定原則版本的規則引擎執行個體 (若負載需要它)，而每個規則引擎執行個體都有自己的事實擷取器執行個體。</span><span class="sxs-lookup"><span data-stu-id="59d42-151">The rule engine cache will have multiple rule engine instances for a given policy version if the load requires it, and each rule engine instance has its own fact retriever instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59d42-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59d42-152">See Also</span></span>  
 [<span data-ttu-id="59d42-153">商務規則引擎</span><span class="sxs-lookup"><span data-stu-id="59d42-153">Business Rules Engine</span></span>](../core/business-rules-engine.md)