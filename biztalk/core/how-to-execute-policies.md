---
title: 如何執行原則 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Business Rules Framework, policies
- Business Rules Framework, code samples
- Business Rules Framework, programming
ms.assetid: 90d28d9d-0204-47de-a927-26e284c886e4
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b0aa834150f0d5c84ebb4c757769a2be38f3942
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22253798"
---
# <a name="how-to-execute-policies"></a><span data-ttu-id="8f5f4-102">如何執行原則</span><span class="sxs-lookup"><span data-stu-id="8f5f4-102">How to Execute Policies</span></span>
<span data-ttu-id="8f5f4-103">下列範例程式碼示範如何叫用規則引擎來執行原則以程式設計方式使用**原則**類別**Microsoft.RuleEngine**組件。</span><span class="sxs-lookup"><span data-stu-id="8f5f4-103">The following sample code shows how to invoke the rule engine to execute a policy programmatically by using the **Policy** class in the **Microsoft.RuleEngine** assembly.</span></span>  
  
```  
xmlDocument = IncomingXMLMessage.XMLCase;  
typedXmlDocument = new Microsoft.RuleEngine.TypedXmlDocument("Microsoft.Samples.BizTalk.LoansProcessor.Case",xmlDocument);  
policy = new Microsoft.RuleEngine.Policy("LoanProcessing");  
policy.Execute(typedXmlDocument);  
OutgoingXMLMessage.XMLCase = xmlDocument;  
policy.Dispose();  
```  
  
## <a name="important-methods-of-the-policy-class"></a><span data-ttu-id="8f5f4-104">Policy 類別的重要方法</span><span class="sxs-lookup"><span data-stu-id="8f5f4-104">Important methods of the Policy class</span></span>  
 <span data-ttu-id="8f5f4-105">以下是 Policy 類別的重要方法以及其描述。</span><span class="sxs-lookup"><span data-stu-id="8f5f4-105">Here are the important methods of the Policy class and their descriptions.</span></span>  
  
|<span data-ttu-id="8f5f4-106">Policy 類別中的方法</span><span class="sxs-lookup"><span data-stu-id="8f5f4-106">Method in the Policy class</span></span>|<span data-ttu-id="8f5f4-107">Description</span><span class="sxs-lookup"><span data-stu-id="8f5f4-107">Description</span></span>|  
|--------------------------------|-----------------|  
|<span data-ttu-id="8f5f4-108">Execute</span><span class="sxs-lookup"><span data-stu-id="8f5f4-108">Execute</span></span>|<span data-ttu-id="8f5f4-109">將指定的短期事實新增至規則引擎的工作記憶體中，然後使用 Match-Conflict Resolution-Action 演算法來執行此原則。</span><span class="sxs-lookup"><span data-stu-id="8f5f4-109">Adds the specified short-term facts into the rule engine's working memory and executes the policy using Match-Conflict Resolution-Action algorithm.</span></span> <span data-ttu-id="8f5f4-110">如需 Match-conflict Resolution-action 演算法的詳細資訊，請參閱[條件評估與動作執行](../core/condition-evaluation-and-action-execution.md)。</span><span class="sxs-lookup"><span data-stu-id="8f5f4-110">For more information on Match-Conflict Resolution-Action algorithm, see [Condition Evaluation and Action Execution](../core/condition-evaluation-and-action-execution.md) .</span></span>|  
|<span data-ttu-id="8f5f4-111">處置</span><span class="sxs-lookup"><span data-stu-id="8f5f4-111">Dispose</span></span>|<span data-ttu-id="8f5f4-112">釋放規則引擎用來執行原則所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="8f5f4-112">Releases the resources used by the rule engine for executing the policy.</span></span>|  
|<span data-ttu-id="8f5f4-113">Clear</span><span class="sxs-lookup"><span data-stu-id="8f5f4-113">Clear</span></span>|<span data-ttu-id="8f5f4-114">清除或重設工作記憶體，以及為了執行原則所建立之規則引擎執行個體的議程。</span><span class="sxs-lookup"><span data-stu-id="8f5f4-114">Clears or resets the working memory and the agenda of the rule engine instance created for executing the policy.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8f5f4-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f5f4-115">See Also</span></span>  
 [<span data-ttu-id="8f5f4-116">Policy.Dispose 方法</span><span class="sxs-lookup"><span data-stu-id="8f5f4-116">Policy.Dispose Method</span></span>](../core/policy-dispose-method.md)