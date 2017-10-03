---
title: "規則動作的副作用 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Business Rules Engine, side effects
ms.assetid: 1ef65014-9c0a-40d3-b941-2a67c20b54d3
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2ed890ca8efca6fdd1403c4ec89f4c0c5d32eaa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="rule-action-side-effects"></a><span data-ttu-id="6cdac-102">規則動作的副作用</span><span class="sxs-lookup"><span data-stu-id="6cdac-102">Rule Action Side Effects</span></span>
<span data-ttu-id="6cdac-103">若執行動作會影響到物件的狀態或條件中使用的詞彙，那麼該動作即視為對物件有副作用。</span><span class="sxs-lookup"><span data-stu-id="6cdac-103">If the execution of an action affects the state of an object or a term used in conditions, that action is considered to have a side effect on the object.</span></span>  
  
 <span data-ttu-id="6cdac-104">假設我們有下列規則。</span><span class="sxs-lookup"><span data-stu-id="6cdac-104">Assume we have the following rules.</span></span>  
  
## <a name="rule-1"></a><span data-ttu-id="6cdac-105">規則 1</span><span class="sxs-lookup"><span data-stu-id="6cdac-105">Rule 1</span></span>  
  
```  
IF OrderForm.ItemCount > 100   
THEN OrderForm.Status = "important"  
```  
  
## <a name="rule-2"></a><span data-ttu-id="6cdac-106">規則 2</span><span class="sxs-lookup"><span data-stu-id="6cdac-106">Rule 2</span></span>  
  
```  
IF OrderList.IsFromMember = true   
THEN OrderForm.UpdateStatus("important")  
```  
  
 <span data-ttu-id="6cdac-107">在此情況下， **OrderForm.UpdateStatus**即所謂具有副作用**OrderForm.Status**。</span><span class="sxs-lookup"><span data-stu-id="6cdac-107">In this case, **OrderForm.UpdateStatus** is said to have a side effect on **OrderForm.Status**.</span></span> <span data-ttu-id="6cdac-108">這並不表示**OrderForm.UpdateStatus**有副作用; 相反地， **OrderForm.Status**可能會受到一或多個動作。</span><span class="sxs-lookup"><span data-stu-id="6cdac-108">This does not mean that **OrderForm.UpdateStatus** has side effects; instead, **OrderForm.Status** is potentially affected by one or more actions.</span></span>  
  
 <span data-ttu-id="6cdac-109">根據預設， **SideEffects** .NET 類別成員的屬性是**true**，它可防止規則引擎快取具有副作用的成員。</span><span class="sxs-lookup"><span data-stu-id="6cdac-109">By default, the **SideEffects** property for .NET class members is **true**, which prevents the rule engine from caching the member with side effects.</span></span> <span data-ttu-id="6cdac-110">在本例中，規則引擎並不會快取**OrderForm.Status**工作記憶體中改為取得最新值的**OrderForm.Status**每次評估規則 1。</span><span class="sxs-lookup"><span data-stu-id="6cdac-110">In our example, the rule engine does not cache **OrderForm.Status** in the working memory; instead it gets the most up-to-date value of **OrderForm.Status** every time Rule 1 is evaluated.</span></span> <span data-ttu-id="6cdac-111">如果**SideEffects**屬性設定為**false**，規則引擎快取的值評估的第一次**OrderForm.Status**，但 （在稍後的評估正向鏈結實例），它會使用快取的值。</span><span class="sxs-lookup"><span data-stu-id="6cdac-111">If the **SideEffects** property is set to **false**, the rule engine caches the value first time it evaluates **OrderForm.Status**, but for later evaluations (in forward-chaining scenarios), it uses the cached value.</span></span>  
  
 <span data-ttu-id="6cdac-112">目前商務規則編輯器 」 不提供方法，讓使用者修改**SideEffects**，不過，您只能設定**SideEffects**屬性以程式設計方式透過 「 商務規則架構.</span><span class="sxs-lookup"><span data-stu-id="6cdac-112">Currently the Business Rule Composer does not provide a way for users to modify **SideEffects**, however, you can only set the **SideEffects** property programmatically through the Business Rules Framework.</span></span> <span data-ttu-id="6cdac-113">您設定可以在繫結，請使用[ClassMemberBinding](https://msdn.microsoft.com/library/microsoft.ruleengine.classmemberbinding.aspx)類別，以指定物件的方法、 屬性和規則條件和動作中使用的欄位。</span><span class="sxs-lookup"><span data-stu-id="6cdac-113">You set do this at binding, using the [ClassMemberBinding](https://msdn.microsoft.com/library/microsoft.ruleengine.classmemberbinding.aspx) class to specify object methods, properties, and fields used in rule conditions and actions.</span></span> <span data-ttu-id="6cdac-114">**ClassMemberBinding**具有內容， [SideEffects](https://msdn.microsoft.com/library/microsoft.ruleengine.classmemberbinding.sideeffects.aspx#P:Microsoft.RuleEngine.ClassMemberBinding.SideEffects)，其中包含布林值，指出是否存取成員變更其值。</span><span class="sxs-lookup"><span data-stu-id="6cdac-114">**ClassMemberBinding** has a property, [SideEffects](https://msdn.microsoft.com/library/microsoft.ruleengine.classmemberbinding.sideeffects.aspx#P:Microsoft.RuleEngine.ClassMemberBinding.SideEffects), which contains a Boolean value indicating whether accessing the member changes its value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cdac-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6cdac-115">See Also</span></span>  
 [<span data-ttu-id="6cdac-116">規則引擎</span><span class="sxs-lookup"><span data-stu-id="6cdac-116">Rule Engine</span></span>](../core/rule-engine.md)