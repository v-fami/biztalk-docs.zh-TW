---
title: 規則引擎 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- RuleEngine object
- Business Rules Engine, ruleset executor
- Business Rules Engine, ruleset translator
- Business Rules Engine, ruleset tracking interceptor
- Business Rules Engine, Business Rules Engine
ms.assetid: c4043a1f-357f-47bc-84e1-5e4bd9f8b5b8
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b0dc2d293697ccbb64851591037440d0371c1346
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268726"
---
# <a name="rule-engine"></a><span data-ttu-id="78411-102">規則引擎</span><span class="sxs-lookup"><span data-stu-id="78411-102">Rule Engine</span></span>
<span data-ttu-id="78411-103">本節會描述商務規則引擎的數個元件、功能及作業。</span><span class="sxs-lookup"><span data-stu-id="78411-103">This section describes several components, functionalities, and operations of the Business Rule engine.</span></span> <span data-ttu-id="78411-104">規則引擎會提供規則集的執行環境。</span><span class="sxs-lookup"><span data-stu-id="78411-104">The rule engine provides the execution context for a rule set.</span></span> <span data-ttu-id="78411-105">**RuleEngine**物件會使用下列外掛程式元件進行實作：</span><span class="sxs-lookup"><span data-stu-id="78411-105">The **RuleEngine** object uses the following plug–in components for implementation:</span></span>  
  
-   <span data-ttu-id="78411-106">**規則集執行子 （推斷引擎）**。</span><span class="sxs-lookup"><span data-stu-id="78411-106">**Ruleset executor (inference engine)**.</span></span> <span data-ttu-id="78411-107">實作負責規則條件評估及動作執行的演算法。</span><span class="sxs-lookup"><span data-stu-id="78411-107">Implements the algorithm responsible for rule condition evaluation and action execution.</span></span> <span data-ttu-id="78411-108">預設的規則集執行子是一個辨識網路型向前鏈結推斷引擎，其設計目的是最佳化記憶體中的作業。</span><span class="sxs-lookup"><span data-stu-id="78411-108">The default rule set executor is a discrimination network-based forward-chaining inference engine designed to optimize in-memory operation.</span></span>  
  
-   <span data-ttu-id="78411-109">**規則集轉譯程式**。</span><span class="sxs-lookup"><span data-stu-id="78411-109">**Ruleset translator**.</span></span> <span data-ttu-id="78411-110">輸入**RuleSet**物件，並會產生可執行檔規則集的表示。</span><span class="sxs-lookup"><span data-stu-id="78411-110">Takes as input a **RuleSet** object and produces an executable representation of the rule set.</span></span> <span data-ttu-id="78411-111">預設的記憶體中轉譯程式會從規則集定義中建立編譯的辨識網路。</span><span class="sxs-lookup"><span data-stu-id="78411-111">The default in-memory translator creates a compiled discrimination network from the rule set definition.</span></span>  
  
-   <span data-ttu-id="78411-112">**規則集追蹤攔截器**。</span><span class="sxs-lookup"><span data-stu-id="78411-112">**Rule set tracking interceptor**.</span></span> <span data-ttu-id="78411-113">接收來自規則集執行子 (推斷引擎) 的輸出，並將輸出轉送至規則集追蹤及監控工具。</span><span class="sxs-lookup"><span data-stu-id="78411-113">Receives output from the rule set executor (inference engine) and forwards it to rule set tracking and monitoring tools.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="78411-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="78411-114">In This Section</span></span>  
  
-   [<span data-ttu-id="78411-115">條件評估與動作執行</span><span class="sxs-lookup"><span data-stu-id="78411-115">Condition Evaluation and Action Execution</span></span>](../core/condition-evaluation-and-action-execution.md)  
  
-   [<span data-ttu-id="78411-116">議程與優先順序</span><span class="sxs-lookup"><span data-stu-id="78411-116">Agenda and Priority</span></span>](../core/agenda-and-priority.md)  
  
-   [<span data-ttu-id="78411-117">引擎控制函式</span><span class="sxs-lookup"><span data-stu-id="78411-117">Engine Control Functions</span></span>](../core/engine-control-functions.md)  
  
-   [<span data-ttu-id="78411-118">商務規則引擎中的資料存取</span><span class="sxs-lookup"><span data-stu-id="78411-118">Data Access in the Business Rule Engine</span></span>](../core/data-access-in-the-business-rule-engine.md)  
  
-   [<span data-ttu-id="78411-119">規則動作的副作用</span><span class="sxs-lookup"><span data-stu-id="78411-119">Rule Action Side Effects</span></span>](../core/rule-action-side-effects.md)  
  
-   [<span data-ttu-id="78411-120">商務規則引擎中的類別繼承支援</span><span class="sxs-lookup"><span data-stu-id="78411-120">Support for Class Inheritance in the Business Rule Engine</span></span>](../core/support-for-class-inheritance-in-the-business-rule-engine.md)  
  
-   [<span data-ttu-id="78411-121">規則引擎組態和調整參數</span><span class="sxs-lookup"><span data-stu-id="78411-121">Rule Engine Configuration and Tuning Parameters</span></span>](../core/rule-engine-configuration-and-tuning-parameters.md)  
  
-   [<span data-ttu-id="78411-122">使用規則引擎時的效能考量</span><span class="sxs-lookup"><span data-stu-id="78411-122">Performance Considerations When Using the Rule Engine</span></span>](../core/performance-considerations-when-using-the-rule-engine.md)  
  
## <a name="see-also"></a><span data-ttu-id="78411-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78411-123">See Also</span></span>  
 [<span data-ttu-id="78411-124">商務規則引擎</span><span class="sxs-lookup"><span data-stu-id="78411-124">Business Rules Engine</span></span>](../core/business-rules-engine.md)