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
# <a name="support-for-class-inheritance-in-the-business-rule-engine"></a>支援商務規則引擎中的類別繼承
「物件導向程式設計」(OOP) 語言的其中一個主要功能為繼承。 繼承是指可以使用現有類別的所有功能，並且不需重新撰寫原始類別即可擴充這些功能。  
  
 「商務規則架構」支援兩種類型的類別繼承：實作和介面。 實作繼承是指不需撰寫額外的程式碼，即可使用基底類別的屬性與方法。 介面繼承是指只能使用屬性與方法的名稱，但是子類別必須提供實作。  
  
 這些規則可以根據一般基底類別來撰寫，但是引擎中已判斷提示的物件可以源自衍生類別。 在下列範例中， **RegularEmployee**和**ContractEmployee**是基底類別的衍生的類別**員工**。  
  
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
  
 假設您有下列規則。  
  
## <a name="rule-1"></a>規則 1  
  
```  
IF Employee.TimeInMonths < 12  
THEN Employee.Status = "New"  
```  
  
 在執行階段，如果使用者判斷提示兩個物件，其中一個執行個體的**ContractEmployee**和其他執行個體的**RegularEmployee**，這兩個物件執行個體進行評估所述的規則稍早。  
  
 使用者也可以判斷在衍生的類別物件，在 [動作] 提示使用**Assert**。 這將導致重新評估在條件中包含衍生物件及其基底型別的規則，如下列範例所示。  
  
## <a name="rule-2"></a>規則 2  
  
```  
IF Employee.Status = "Contract"   
THEN Employee.Bonus = false  
Assert(new ContractEmployee())  
```  
  
 包含的所有規則**員工**類型或**ContractEmployee**判斷提示後會重新評估其條件中的型別。 此範例中的繼承類型為實作。 即使只判斷提示了衍生類別，若使用基底類別而不是衍生類別中的方法來撰寫規則，也會判斷提示基底類別。  
  
## <a name="see-also"></a>另請參閱  
 [規則引擎](../core/rule-engine.md)