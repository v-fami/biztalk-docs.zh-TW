---
title: 規則 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- business rules, actions
- Business Rules Engine, business rules
- business rules, about business rules
- business rules, conditions
- business rules, facts
- business rules
ms.assetid: b288dd07-33f1-42fe-bbfb-02674ef3b3ca
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 35f398cf98181d17833be79fbe9d282e8515e052
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268774"
---
# <a name="rules"></a><span data-ttu-id="61333-102">規則</span><span class="sxs-lookup"><span data-stu-id="61333-102">Rules</span></span>
<span data-ttu-id="61333-103">商務規則是控管商務程序進行的宣告陳述式。</span><span class="sxs-lookup"><span data-stu-id="61333-103">Business rules are declarative statements that govern the conduct of business processes.</span></span> <span data-ttu-id="61333-104">規則是由條件與動作組成。</span><span class="sxs-lookup"><span data-stu-id="61333-104">A rule consists of a condition and actions.</span></span> <span data-ttu-id="61333-105">評估條件時，如果其評估結果為**true**，規則引擎就會初始一或多個動作。</span><span class="sxs-lookup"><span data-stu-id="61333-105">The condition is evaluated, and if it evaluates to **true**, the rule engine initiates one or more actions.</span></span>  
  
 <span data-ttu-id="61333-106">商務規則架構中的規則會使用下列格式來定義：</span><span class="sxs-lookup"><span data-stu-id="61333-106">Rules in the Business Rules Framework are defined by using the following format:</span></span>  
  
 <span data-ttu-id="61333-107">如果`condition`然後`action`</span><span class="sxs-lookup"><span data-stu-id="61333-107">IF`condition` THEN`action`</span></span>  
  
 <span data-ttu-id="61333-108">請設想下列範例：</span><span class="sxs-lookup"><span data-stu-id="61333-108">Consider the following example:</span></span>  
  
 <span data-ttu-id="61333-109">IF amount is less than or equal to available funds</span><span class="sxs-lookup"><span data-stu-id="61333-109">IF amount is less than or equal to available funds</span></span>  
  
 <span data-ttu-id="61333-110">THEN conduct transaction and print receipt</span><span class="sxs-lookup"><span data-stu-id="61333-110">THEN conduct transaction and print receipt</span></span>  
  
 <span data-ttu-id="61333-111">這個規則會將商務邏輯 (以比較兩個貨幣值的形式) 套用到資料或事實 (以交易數量與可用資金的形式)，以判斷是否要進行交易。</span><span class="sxs-lookup"><span data-stu-id="61333-111">This rule determines whether a transaction will be conducted by applying business logic, in the form of a comparison of two monetary values, to data or facts, in the form of a transaction amount and available funds.</span></span>  
  
 <span data-ttu-id="61333-112">您可使用「商務規則編輯器」來建立、修改、訂定版本及部署商務規則。</span><span class="sxs-lookup"><span data-stu-id="61333-112">You can use the Business Rule Composer to create, modify, version, and deploy business rules.</span></span> <span data-ttu-id="61333-113">或者，您可以透過程式設計方式來執行前面的工作。</span><span class="sxs-lookup"><span data-stu-id="61333-113">Alternatively, you can perform the preceding tasks programmatically.</span></span>  
  
## <a name="conditions"></a><span data-ttu-id="61333-114">條件</span><span class="sxs-lookup"><span data-stu-id="61333-114">Conditions</span></span>  
 <span data-ttu-id="61333-115">條件就是一個 True/False (布林值) 運算式，其中包含一或多個套用到事實的述詞。</span><span class="sxs-lookup"><span data-stu-id="61333-115">A condition is a true/false (Boolean) expression that consists of one or more predicates that are applied to facts.</span></span>  
  
 <span data-ttu-id="61333-116">在本例中，則述詞**小於或等於**套用到事實**量**和**可用資金**。</span><span class="sxs-lookup"><span data-stu-id="61333-116">In our example, the predicate **less than or equal to** is applied to the facts **amount** and **available funds**.</span></span> <span data-ttu-id="61333-117">此條件將一律評估為**true**或**false**。</span><span class="sxs-lookup"><span data-stu-id="61333-117">This condition will always evaluate to either **true** or **false**.</span></span>  
  
 <span data-ttu-id="61333-118">述詞可以與邏輯運算子結合**AND**，**或者**，和**不**邏輯運算式可能很大，但將一律評估為表單任一**true**或**false**。</span><span class="sxs-lookup"><span data-stu-id="61333-118">Predicates can be combined with the logical operators **AND**, **OR**, and **NOT** to form a logical expression that is potentially quite large, but will always evaluate to either **true** or **false**.</span></span>  
  
## <a name="actions"></a><span data-ttu-id="61333-119">動作</span><span class="sxs-lookup"><span data-stu-id="61333-119">Actions</span></span>  
 <span data-ttu-id="61333-120">動作是條件評估的功能結果。</span><span class="sxs-lookup"><span data-stu-id="61333-120">Actions are the functional consequences of condition evaluation.</span></span> <span data-ttu-id="61333-121">若符合某規則條件，就會初始對應的一個或多個動作。</span><span class="sxs-lookup"><span data-stu-id="61333-121">If a rule condition is met, a corresponding action or actions are initiated.</span></span>  
  
 <span data-ttu-id="61333-122">在我們的範例中，"conduct transaction" 及 "print receipt" 就是在條件 (在此案例中就是 "IF amount is less than or equal to available funds") 為 True 時會執行的動作，而且也只有在此時才會執行。</span><span class="sxs-lookup"><span data-stu-id="61333-122">In our example, "conduct transaction" and "print receipt" are actions that are carried out when, and only when, the condition (in this case, "IF amount is less than or equal to available funds") is true.</span></span>  
  
 <span data-ttu-id="61333-123">而商務規則架構中的動作，是藉由呼叫方法或設定物件上的屬性，或是在 XML 文件或資料庫資料表上執行設定作業來表現。</span><span class="sxs-lookup"><span data-stu-id="61333-123">Actions are represented in the Business Rules Framework by invoking methods or setting properties on objects, or by performing set operations on XML documents or database tables.</span></span>  
  
## <a name="facts"></a><span data-ttu-id="61333-124">事實</span><span class="sxs-lookup"><span data-stu-id="61333-124">Facts</span></span>  
 <span data-ttu-id="61333-125">事實就是規則運作依據的資料。</span><span class="sxs-lookup"><span data-stu-id="61333-125">Facts are the data upon which rules operate.</span></span> <span data-ttu-id="61333-126">在我們的範例中 "amount" 及 "available funds" 就是事實。</span><span class="sxs-lookup"><span data-stu-id="61333-126">In our example, "amount" and "available funds" are facts.</span></span> <span data-ttu-id="61333-127">如需詳細資訊，請參閱[事實](../core/facts.md)。</span><span class="sxs-lookup"><span data-stu-id="61333-127">For more information, see [Facts](../core/facts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61333-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61333-128">See Also</span></span>  
 [<span data-ttu-id="61333-129">如何建立原則和規則</span><span class="sxs-lookup"><span data-stu-id="61333-129">How to Create Policies and Rules</span></span>](../core/how-to-create-policies-and-rules.md)