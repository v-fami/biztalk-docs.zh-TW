---
title: 存取類別的巢狀的成員 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 358e1edf-ae0b-4916-b8db-7277f39e36f4
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 110244f9f007a417450b5bbfdce831d5f255cfe5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224518"
---
# <a name="accessing-nested-members-of-a-class"></a>存取類別的巢狀成員
規則引擎讓您能在規則中使用物件的巢狀屬性或方法。 例如，假設您有名為 AClass 的類別，該類別具有名為 B 的 BClass 型別屬性，該屬性則有名為 C 的欄位。規則引擎便讓您能夠建置使用 A.B.C 語法存取 C 欄位的規則。 然而，只有在使用程式設計方式 (而非使用 [商務規則編輯器] 工具) 建置規則時，才有可能使用此語法。 下列程式碼範例示範如何使用物件的屬性，該屬性是另一個物件的屬性：  
  
```  
// Create the condition list IF 1 == 1  
Equal eq = new Equal(new Constant(1), new Constant(1));  
  
// Create the action collection  
ActionCollection ac = new ActionCollection();  
  
// Create class binding and class member binding to cField  
// Set the value of cField to "Changed"  
Constant chg = new Constant("Changed");  
ArgumentCollection argCol = new ArgumentCollection();  
argCol.Add(chg);  
ClassBinding lstClass = new ClassBinding(typeof(AClass));  
ClassMemberBinding bBinding = new ClassMemberBinding("bObj", lstClass);  
ClassMemberBinding CBinding = new ClassMemberBinding("cField", bBinding,argCol);  
UserFunction uf_C = new UserFunction(CBinding);  
ac.Add(uf_C);  
  
// Create the rule  
Rule rl = new Rule("ChangeCField", eq, ac);  
  
// Create the policy  
RuleSet rs = new RuleSet("NestedNodeTest");  
rs.Rules.Add(rl);  
  
//Create the facts  
AClass aObj = new AClass();  
Console.WriteLine("The value of aObj.bObj.cField BEFORE executing the policy");  
Console.WriteLine(aObj.bObj.cField);  
  
//Execute the policy  
PolicyTester tester = new PolicyTester(rs);  
tester.Execute(aObj);  
  
Console.WriteLine("The value of aObj.bObj.cField AFTER executing the policy");  
Console.WriteLine(aObj.bObj.cField);  
```