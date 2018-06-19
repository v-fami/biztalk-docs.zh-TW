---
title: 如何分析商務規則中相同類型的多個物件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- business rules, multiple types
- Business Rules Framework, programming
ms.assetid: ff9790c1-13b0-4eee-8cac-d4f25ef5f0b7
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a1e4d2fb01513b1d4d314264ab74b84d3a0223a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248430"
---
# <a name="how-to-analyze-multiple-objects-of-the-same-type-in-a-business-rule"></a>如何分析商務規則中相同類型的多個物件
在許多實例中，您將針對某一類型撰寫商務規則，預期判斷提示至引擎的該類型的每個執行個體可依照規則分別分析與作用。 不過，在某些實例中，您想要在規則中同時分析指定類型的多重執行個體。  
  
 接受例如使用的執行個體的規則**FamilyMember**類別。  
  
```  
IF FamilyMember.Role == Father  
AND FamilyMember.Role == Son  
AND FamilyMember.Surname == FamilyMember.Surname  
THEN FamilyMember.AddChild(FamilyMember)  
```  
  
 此規則會識別**FamilyMember**這個執行個體是**父親**與另一個執行個體**Son**。 如果執行個體以姓氏相關， **Son**執行個體加入 Father 執行個體的子系的集合。 如果每個**FamilyMember**規則中分別分析執行個體，此規則會永遠不會引發，因為在此案例中， **FamilyMember**只有一個角色 —**父親**或**Son**。  
  
 因此，您必須在規則中指示引擎應一起分析多個執行個體，且您需要一個區分規則中每個執行個體識別的方法。 **執行個體識別碼**屬性用來提供這項功能。 當事實在 [事實總管] 中已選取時，可在 [屬性] 視窗中使用此欄位。 將事實或成員拖曳至規則中之前，應該先變更欄位的值。  
  
 使用**執行個體識別碼**屬性，可重建規則。 使用這些規則引數**Son**的執行個體**FamilyMember**、**執行個體識別碼**欄位從 0 到 1 的預設值變更。 當執行個體識別碼從 0 變更且事實或成員拖曳至規則編輯器時，執行個體識別碼的值會顯示在規則中的類別之後。  
  
```  
IF FamilyMember.Role == Father  
AND FamilyMember(1).Role== Son  
AND FamilyMember.Surname == FamilyMember(1).Surname  
THEN FamilyMember.AddChild(FamilyMember(1))  
```  
  
 現在，假設**父親**執行個體和**Son**執行個體判斷提示至引擎。 此引擎將針對各種執行個體組合評估此規則。 假設**父親**和**Son**執行個體具有相同姓氏， **Son**執行個體將會新增至**父親**做為執行個體目的。  
  
> [!NOTE]
>  **執行個體識別碼**只用在指定的規則評估的內容。 它不會在執行原則時附加到物件執行個體，而且與判斷提示物件的順序無關。 每個物件執行個體都會在該類型的所有規則引數中評估。