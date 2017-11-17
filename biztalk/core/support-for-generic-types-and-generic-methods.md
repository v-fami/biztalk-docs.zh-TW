---
title: "泛型型別和泛型方法的支援 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc6b5b51-e084-4828-ad25-9209aa74dc6f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3601be46358a2f751bc44931043731d4e4b6351
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="support-for-generic-types-and-generic-methods"></a><span data-ttu-id="cf65e-102">對泛型型別和泛型方法的支援</span><span class="sxs-lookup"><span data-stu-id="cf65e-102">Support for Generic Types and Generic Methods</span></span>
<span data-ttu-id="cf65e-103">規則引擎支援在規則中使用特製化的泛型型別和泛型方法，</span><span class="sxs-lookup"><span data-stu-id="cf65e-103">The rule engine supports using specialized generic types and specialized generic methods in a rule.</span></span> <span data-ttu-id="cf65e-104">但是不支援在規則中使用泛型型別和泛型方法本身。</span><span class="sxs-lookup"><span data-stu-id="cf65e-104">It does not support using generic types and generic methods themselves in a rule.</span></span> <span data-ttu-id="cf65e-105">例如，商務規則中您可以使用**清單**\<*int*>，但不是**清單**\<T > (從**System.Collections.Generic** .NET 類別庫中的命名空間)。</span><span class="sxs-lookup"><span data-stu-id="cf65e-105">For example, in a business rule you can use **List**\<*int*>, but not **List**\<T> (from the **System.Collections.Generic** namespace in the .NET class library).</span></span> <span data-ttu-id="cf65e-106">目前，商務規則編輯器工具並不支援使用特製化泛型型別和泛型方法來建立規則。</span><span class="sxs-lookup"><span data-stu-id="cf65e-106">Currently, the Business Rule Composer tool does not support creating rules by using specialized generic types and specialized generic methods.</span></span> <span data-ttu-id="cf65e-107">您必須使用規則引擎物件模型，以程式設計的方式建立這些規則。</span><span class="sxs-lookup"><span data-stu-id="cf65e-107">You must create the rules programmatically by using the rule engine object model.</span></span> <span data-ttu-id="cf65e-108">下列程式碼範例示範如何使用**清單**商務規則中的泛型類別：</span><span class="sxs-lookup"><span data-stu-id="cf65e-108">The following sample code demonstrates how to use the **List** generic class in a business rule:</span></span>  
  
```  
  
// Create the condition list IF 1 == 1  
Equal eq = new Equal(new Constant(1), new Constant(1));  
  
// Create the action list List<int>.Add(3)  
ActionCollection ac = new ActionCollection();  
  
//Create class binding and class member bindings  
ClassBinding lstClass = new ClassBinding(typeof(System.Collections.Generic.List<int>));  
ArgumentCollection argc = new ArgumentCollection();  
argc.Add(new Constant(3));  
ClassMemberBinding add = new ClassMemberBinding("Add", lstClass, argc);  
  
// Wrapping the .NET binding as a user function  
UserFunction uf = new UserFunction(add);  
ac.Add(uf);  
  
// Create the rule  
Rule rl = new Rule("AddToList", eq, ac);  
  
// Create the policy  
RuleSet rs = new RuleSet("GenericTest");  
rs.Rules.Add(rl);  
  
// Create the .NET List object  
List<int> lst = new List<int>();  
lst.Add(1);  
lst.Add(2);  
  
// Print the list before executing the policy  
Console.WriteLine("Contents of the lists before executing the policy");  
foreach (int i in lst)  
    Console.WriteLine(i);  
  
PolicyTester pt = new PolicyTester(rs);  
pt.Execute(lst);  
  
// Print the list after executing the policy  
Console.WriteLine("Contents of the lists before executing the policy");  
foreach (int i in lst)  
    Console.WriteLine(i);  
```