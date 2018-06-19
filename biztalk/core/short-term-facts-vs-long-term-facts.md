---
title: 短期事實與長期事實 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- facts, short-term
- facts, long-term
- short-term facts
- business rules, facts
- long-term facts
ms.assetid: de020b20-1012-498a-969e-4adc4549918c
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3d5c37926fb1da5499f34e22c35f8a8f32d238bb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271038"
---
# <a name="short-term-facts-vs-long-term-facts"></a><span data-ttu-id="bc1b8-102">短期事實與長期事實</span><span class="sxs-lookup"><span data-stu-id="bc1b8-102">Short-Term Facts vs. Long-Term Facts</span></span>
<span data-ttu-id="bc1b8-103">有兩種事實會判斷提示到規則引擎的工作記憶體 – 一為短期事實，另一為長期事實。</span><span class="sxs-lookup"><span data-stu-id="bc1b8-103">Two types of facts are asserted into the working memory of the rule engine—short-term facts and long-term facts.</span></span>  
  
## <a name="short-term-facts"></a><span data-ttu-id="bc1b8-104">短期事實</span><span class="sxs-lookup"><span data-stu-id="bc1b8-104">Short-Term Facts</span></span>  
 <span data-ttu-id="bc1b8-105">短期事實是規則引擎的單一執行循環所特有的。</span><span class="sxs-lookup"><span data-stu-id="bc1b8-105">A short-term fact is specific to a single execution cycle of the rule engine.</span></span> <span data-ttu-id="bc1b8-106">短期事實會在原則執行之後自動從規則引擎的工作記憶體中撤回。</span><span class="sxs-lookup"><span data-stu-id="bc1b8-106">Short-term facts are retracted automatically from the working memory of the rule engine after the policy executes.</span></span> <span data-ttu-id="bc1b8-107">如果原則的資料在規則引擎的執行循環之間有所變更，則可以將該資料當做短期事實提交至規則引擎。</span><span class="sxs-lookup"><span data-stu-id="bc1b8-107">If your data changes between execution cycles of the rule engine for a policy, you submit the data as a short-term fact to the rule engine.</span></span>  
  
 <span data-ttu-id="bc1b8-108">短期事實的範例：</span><span class="sxs-lookup"><span data-stu-id="bc1b8-108">Examples of short-term facts are:</span></span>  
  
-   <span data-ttu-id="bc1b8-109">做為參數提交的事實**Policy.Execute**方法。</span><span class="sxs-lookup"><span data-stu-id="bc1b8-109">The facts you submit as parameters to the **Policy.Execute** method.</span></span>  
  
-   <span data-ttu-id="bc1b8-110">做為參數提交的事實**呼叫規則**圖形。</span><span class="sxs-lookup"><span data-stu-id="bc1b8-110">The facts you submit as parameters to the **Call Rules** shape.</span></span>  
  
-   <span data-ttu-id="bc1b8-111">從使用規則動作提交的事實**Assert**函式。</span><span class="sxs-lookup"><span data-stu-id="bc1b8-111">The facts you submit from an action of a rule using the **Assert** function.</span></span>  
  
## <a name="long-term-facts"></a><span data-ttu-id="bc1b8-112">長期事實</span><span class="sxs-lookup"><span data-stu-id="bc1b8-112">Long-Term Facts</span></span>  
 <span data-ttu-id="bc1b8-113">長期事實會載入至規則引擎的工作記憶體中，供任意數目的執行循環使用。</span><span class="sxs-lookup"><span data-stu-id="bc1b8-113">A long-term fact is loaded into the working memory of the rule engine for use over an arbitrary number of execution cycles.</span></span> <span data-ttu-id="bc1b8-114">一般而言，長期事實是變更緩慢的事實，一般不會在原則的執行作業之間變更。</span><span class="sxs-lookup"><span data-stu-id="bc1b8-114">Typically, long-term facts are slowly changing facts that do not typically change between executions of a policy.</span></span> <span data-ttu-id="bc1b8-115">例如，您可能只想建立一次資料庫連線，然後使用同一個資料庫連線來執行原則數次。</span><span class="sxs-lookup"><span data-stu-id="bc1b8-115">For example, you may want to create a database connection only once, and execute the policy several times by using the same database connection.</span></span> <span data-ttu-id="bc1b8-116">短期事實和長期事實唯一真正的差異在於實作。</span><span class="sxs-lookup"><span data-stu-id="bc1b8-116">The only real distinction between short-term facts and long-term facts is in implementation.</span></span>  
  
 <span data-ttu-id="bc1b8-117">若要將事實當做長期事實提交，需要執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="bc1b8-117">To submit a fact as a long-term fact, you need to perform the following steps:</span></span>  
  
1.  <span data-ttu-id="bc1b8-118">建立實作事實擷取器元件**IFactRetriever**介面。</span><span class="sxs-lookup"><span data-stu-id="bc1b8-118">Create a fact retriever component that implements the **IFactRetriever** interface.</span></span> <span data-ttu-id="bc1b8-119">建立和判斷提示至規則的工作記憶體的事實引擎**UpdateFacts**會叫用方法的第一個時間和更新事實時必要的後續引動過程上**UpdateFacts**方法。</span><span class="sxs-lookup"><span data-stu-id="bc1b8-119">Create and assert the fact into the working memory of the rule engine when the **UpdateFacts** method is invoked for the first time, and update the fact when necessary on subsequent invocations of the **UpdateFacts** method.</span></span>  
  
2.  <span data-ttu-id="bc1b8-120">使用商務規則編輯器將原則設定為使用事實擷取器。</span><span class="sxs-lookup"><span data-stu-id="bc1b8-120">Configure the policy to use the fact retriever component by using the Business Rule Composer.</span></span>  
  
 <span data-ttu-id="bc1b8-121">如需建立事實擷取器並使用它在原則中的詳細資訊，請參閱[如何建立事實擷取器](../core/how-to-create-a-fact-retriever.md)。</span><span class="sxs-lookup"><span data-stu-id="bc1b8-121">For more information about creating a fact retriever and using it in a policy, see [How to Create a Fact Retriever](../core/how-to-create-a-fact-retriever.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc1b8-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc1b8-122">See Also</span></span>  
 [<span data-ttu-id="bc1b8-123">事實</span><span class="sxs-lookup"><span data-stu-id="bc1b8-123">Facts</span></span>](../core/facts.md)