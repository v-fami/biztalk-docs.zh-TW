---
title: "在協調流程中使用運算式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1947cd39-6ef2-4b2d-afeb-a0132b19db97
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 880e1ee08a232aca3a04763c5d5c1797fd238fbe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-expressions-in-orchestrations"></a><span data-ttu-id="bfbba-102">在協調流程中使用運算式</span><span class="sxs-lookup"><span data-stu-id="bfbba-102">Using Expressions in Orchestrations</span></span>
<span data-ttu-id="bfbba-103">您可以使用「BizTalk 運算式編輯器」輸入 XLANG/s 運算式，以新增邏輯來處理和測試協調流程變數和訊息的值。</span><span class="sxs-lookup"><span data-stu-id="bfbba-103">You can use BizTalk Expression Editor to enter XLANG/s expressions to add logic to manipulate and test the values of your orchestration variables and messages.</span></span> <span data-ttu-id="bfbba-104">但是，這種方式比較不適合用來執行高階協調流程邏輯，比較好的方式是透過協調流程繪圖本身來呈現高階協調流程邏輯。</span><span class="sxs-lookup"><span data-stu-id="bfbba-104">However, it is not a good practice to use it to perform high-level orchestration logic, which preferably would be visible in the orchestration drawing itself.</span></span> <span data-ttu-id="bfbba-105">為了使商務程序透明化且便於重新設定，建議您使用簡單且模組化的運算式。</span><span class="sxs-lookup"><span data-stu-id="bfbba-105">For business process transparency and easy of reconfiguration, we recommend that you use simple and modular expressions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bfbba-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="bfbba-106">In This Section</span></span>  
 [<span data-ttu-id="bfbba-107">運算式的需求與限制</span><span class="sxs-lookup"><span data-stu-id="bfbba-107">Requirements and Limitations for Expressions</span></span>](../core/requirements-and-limitations-for-expressions.md)  
  
 [<span data-ttu-id="bfbba-108">採用運算式的圖形</span><span class="sxs-lookup"><span data-stu-id="bfbba-108">Shapes that Take Expressions</span></span>](../core/shapes-that-take-expressions.md)  
  
 [<span data-ttu-id="bfbba-109">如何建立運算式</span><span class="sxs-lookup"><span data-stu-id="bfbba-109">How to Create Expressions</span></span>](../core/how-to-create-expressions.md)  
  
 [<span data-ttu-id="bfbba-110">在運算式中使用運算子</span><span class="sxs-lookup"><span data-stu-id="bfbba-110">Using Operators in Expressions</span></span>](../core/using-operators-in-expressions.md)  
  
 [<span data-ttu-id="bfbba-111">如何使用運算式執行訊息指派</span><span class="sxs-lookup"><span data-stu-id="bfbba-111">How to Use Expressions to Perform Message Assignments</span></span>](../core/how-to-use-expressions-to-perform-message-assignments.md)  
  
 [<span data-ttu-id="bfbba-112">如何使用運算式動態地轉換訊息</span><span class="sxs-lookup"><span data-stu-id="bfbba-112">How to Use Expressions to Dynamic Transform Messages</span></span>](../core/how-to-use-expressions-to-dynamic-transform-messages.md)  
  
 [<span data-ttu-id="bfbba-113">如何使用運算式執行管線</span><span class="sxs-lookup"><span data-stu-id="bfbba-113">How to Use Expressions to Execute Pipelines</span></span>](../core/how-to-use-expressions-to-execute-pipelines.md)  
  
 [<span data-ttu-id="bfbba-114">如何使用運算式來建立物件和呼叫物件方法</span><span class="sxs-lookup"><span data-stu-id="bfbba-114">How to Use Expressions to Create Objects and Call Object Methods</span></span>](../core/how-to-use-expressions-to-create-objects-and-call-object-methods.md)  
  
 [<span data-ttu-id="bfbba-115">如何使用運算式來將值指派給動態連接埠</span><span class="sxs-lookup"><span data-stu-id="bfbba-115">How to Use Expressions to Assign Values to Dynamic Ports</span></span>](../core/how-to-use-expressions-to-assign-values-to-dynamic-ports.md)  
  
## <a name="see-also"></a><span data-ttu-id="bfbba-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bfbba-116">See Also</span></span>  
 <span data-ttu-id="bfbba-117">[XLANG 的語言](../core/xlang-s-language.md) </span><span class="sxs-lookup"><span data-stu-id="bfbba-117">[XLANG-s Language](../core/xlang-s-language.md) </span></span>  
 <span data-ttu-id="bfbba-118">[協調流程中使用訊息](../core/using-messages-in-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="bfbba-118">[Using Messages in Orchestrations](../core/using-messages-in-orchestrations.md) </span></span>  
 [<span data-ttu-id="bfbba-119">在協調流程中使用變數</span><span class="sxs-lookup"><span data-stu-id="bfbba-119">Using Variables in Orchestrations</span></span>](../core/using-variables-in-orchestrations.md)