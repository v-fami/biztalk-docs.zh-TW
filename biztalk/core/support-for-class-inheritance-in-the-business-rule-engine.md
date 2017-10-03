---
title: "商務規則引擎中的類別繼承支援 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code samples, Business Rules Engine
- Business Rules Engine, inheritance
- Business Rules Engine, code samples
- Business Rules Engine, examples
- examples, Business Rules Engine
ms.assetid: 50871f34-ccbe-4f77-8feb-5694e1b14837
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 930fc5591ce55f1a2ec988b307203a4154e85c2b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="support-for-class-inheritance-in-the-business-rule-engine"></a><span data-ttu-id="4f7b6-102">支援商務規則引擎中的類別繼承</span><span class="sxs-lookup"><span data-stu-id="4f7b6-102">Support for Class Inheritance in the Business Rule Engine</span></span>
<span data-ttu-id="4f7b6-103">「物件導向程式設計」(OOP) 語言的其中一個主要功能為繼承。</span><span class="sxs-lookup"><span data-stu-id="4f7b6-103">One of the key features of Object Oriented Programming (OOP) languages is inheritance.</span></span> <span data-ttu-id="4f7b6-104">繼承是指可以使用現有類別的所有功能，並且不需重新撰寫原始類別即可擴充這些功能。</span><span class="sxs-lookup"><span data-stu-id="4f7b6-104">Inheritance is the ability to use all of the functionality of an existing class, and extend those capabilities without rewriting the original class.</span></span>  
  
 <span data-ttu-id="4f7b6-105">「商務規則架構」支援兩種類型的類別繼承：實作和介面。</span><span class="sxs-lookup"><span data-stu-id="4f7b6-105">The Business Rules Framework supports two types of class inheritance: implementation and interface.</span></span> <span data-ttu-id="4f7b6-106">實作繼承是指不需撰寫額外的程式碼，即可使用基底類別的屬性與方法。</span><span class="sxs-lookup"><span data-stu-id="4f7b6-106">Implementation inheritance refers to the ability to use a base class's properties and methods with no additional coding.</span></span> <span data-ttu-id="4f7b6-107">介面繼承是指只能使用屬性與方法的名稱，但是子類別必須提供實作。</span><span class="sxs-lookup"><span data-stu-id="4f7b6-107">Interface inheritance refers to the ability to use just the names of the properties and methods, but the child class must provide the implementation.</span></span>  
  
 <span data-ttu-id="4f7b6-108">這些規則可以根據一般基底類別來撰寫，但是引擎中已判斷提示的物件可以源自衍生類別。</span><span class="sxs-lookup"><span data-stu-id="4f7b6-108">The rules can be written in terms of a common base class, but the objects asserted into the engine can be from derived classes.</span></span> <span data-ttu-id="4f7b6-109">在下列範例中， **RegularEmployee**和**ContractEmployee**是基底類別的衍生的類別**員工**。</span><span class="sxs-lookup"><span data-stu-id="4f7b6-109">In the following example, **RegularEmployee** and **ContractEmployee** are derived classes of the base class **Employee**.</span></span>  
  
```  
class Employee  
   {  
      public string Status()  
      {   
         // member definition  
      }  
      public string TimeInMonths()        
      {   
         // member definition  
      }  
   }  
  
class ContractEmployee : Employee  
{  
   // class definition  
}  
class RegularEmployee : Employee  
{  
   // class definition  
}  
```  
  
 <span data-ttu-id="4f7b6-110">假設您有下列規則。</span><span class="sxs-lookup"><span data-stu-id="4f7b6-110">Assume you have the following rule.</span></span>  
  
## <a name="rule-1"></a><span data-ttu-id="4f7b6-111">規則 1</span><span class="sxs-lookup"><span data-stu-id="4f7b6-111">Rule 1</span></span>  
  
```  
IF Employee.TimeInMonths < 12  
THEN Employee.Status = "New"  
```  
  
 <span data-ttu-id="4f7b6-112">在執行階段，如果使用者判斷提示兩個物件，其中一個執行個體的**ContractEmployee**和其他執行個體的**RegularEmployee**，這兩個物件執行個體進行評估所述的規則稍早。</span><span class="sxs-lookup"><span data-stu-id="4f7b6-112">At run time, if the user asserts two objects, one an instance of **ContractEmployee** and the other an instance of **RegularEmployee**, both the object instances are evaluated against the rule described earlier.</span></span>  
  
 <span data-ttu-id="4f7b6-113">使用者也可以判斷在衍生的類別物件，在 [動作] 提示使用**Assert**。</span><span class="sxs-lookup"><span data-stu-id="4f7b6-113">The user can also assert derived class objects in actions by using an **Assert**.</span></span> <span data-ttu-id="4f7b6-114">這將導致重新評估在條件中包含衍生物件及其基底型別的規則，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4f7b6-114">This causes the rules that contain the derived object and its base type in their conditions to be re-evaluated, as shown in the following example.</span></span>  
  
## <a name="rule-2"></a><span data-ttu-id="4f7b6-115">規則 2</span><span class="sxs-lookup"><span data-stu-id="4f7b6-115">Rule 2</span></span>  
  
```  
IF Employee.Status = "Contract"   
THEN Employee.Bonus = false  
Assert(new ContractEmployee())  
```  
  
 <span data-ttu-id="4f7b6-116">包含的所有規則**員工**類型或**ContractEmployee**判斷提示後會重新評估其條件中的型別。</span><span class="sxs-lookup"><span data-stu-id="4f7b6-116">All rules containing the **Employee** type or the **ContractEmployee** type in their conditions get re-evaluated after the assertion.</span></span> <span data-ttu-id="4f7b6-117">此範例中的繼承類型為實作。</span><span class="sxs-lookup"><span data-stu-id="4f7b6-117">The type of inheritance in this example is implementation.</span></span> <span data-ttu-id="4f7b6-118">即使只判斷提示了衍生類別，若使用基底類別而不是衍生類別中的方法來撰寫規則，也會判斷提示基底類別。</span><span class="sxs-lookup"><span data-stu-id="4f7b6-118">Even though only the derived class is asserted, the base class also gets asserted if rules are written using methods in the base instead of the derived class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f7b6-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f7b6-119">See Also</span></span>  
 [<span data-ttu-id="4f7b6-120">規則引擎</span><span class="sxs-lookup"><span data-stu-id="4f7b6-120">Rule Engine</span></span>](../core/rule-engine.md)