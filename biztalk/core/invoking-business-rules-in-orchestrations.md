---
title: 叫用協調流程中的商務規則 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Call Rules shape [Orchestration Designer], business rules
- business rules, orchestrations
- Call Rules shape [Orchestration Designer], policies
- policies, Call Rules shape [Orchestration Designer]
- orchestrations, business rules
ms.assetid: ac3a3277-e9ea-4f40-9326-c63076c6b90e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77ecbb9738089dfa2d885f9aa45ac12e92ed27aa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22261822"
---
# <a name="invoking-business-rules-in-orchestrations"></a><span data-ttu-id="d9ec9-102">叫用協調流程中的商務規則</span><span class="sxs-lookup"><span data-stu-id="d9ec9-102">Invoking Business Rules in Orchestrations</span></span>
<span data-ttu-id="d9ec9-103">您可以叫用原則 （或規則集） 從協調流程使用**呼叫規則**圖形。</span><span class="sxs-lookup"><span data-stu-id="d9ec9-103">You can invoke a policy (or rule set) from an orchestration by using the **Call Rules** shape.</span></span> <span data-ttu-id="d9ec9-104">此原則會叫用規則引擎；規則會根據原則中的規則來操作。</span><span class="sxs-lookup"><span data-stu-id="d9ec9-104">The policy invokes the rule engine, which operates on the rules in the policy.</span></span>  
  
 <span data-ttu-id="d9ec9-105">除了使用 呼叫規則，的規則引擎可以透過程式設計方式從運算式呼叫中的程式碼，例如**運算式**或**訊息指派**圖形。</span><span class="sxs-lookup"><span data-stu-id="d9ec9-105">In addition to using Call Rules, the rules engine can be programmatically called from expression code, for example, in an **Expression** or **Message Assignment** shape.</span></span> <span data-ttu-id="d9ec9-106">以程式設計方式執行原則的相關資訊，請參閱[如何執行原則來](../core/how-to-execute-policies.md)。</span><span class="sxs-lookup"><span data-stu-id="d9ec9-106">For information about programmatically executing policies, see [How to Execute Policies](../core/how-to-execute-policies.md).</span></span>  
  
 <span data-ttu-id="d9ec9-107">此部分會敘述組態資訊，以及在呼叫和執行 BizTalk 協調流程中的商務原則時所需要的程序。</span><span class="sxs-lookup"><span data-stu-id="d9ec9-107">This section describes configuration information and the procedures required to call and execute a business policy from a BizTalk orchestration.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d9ec9-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="d9ec9-108">In This Section</span></span>  
  
-   [<span data-ttu-id="d9ec9-109">組態資訊</span><span class="sxs-lookup"><span data-stu-id="d9ec9-109">Configuration Information</span></span>](../core/configuration-information.md)  
  
-   [<span data-ttu-id="d9ec9-110">如何使用 呼叫規則圖形</span><span class="sxs-lookup"><span data-stu-id="d9ec9-110">How to Use the Call Rules Shape</span></span>](../core/how-to-use-the-call-rules-shape.md)