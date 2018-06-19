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
# <a name="how-to-analyze-multiple-objects-of-the-same-type-in-a-business-rule"></a><span data-ttu-id="47fdf-102">如何分析商務規則中相同類型的多個物件</span><span class="sxs-lookup"><span data-stu-id="47fdf-102">How to Analyze Multiple Objects of the Same Type in a Business Rule</span></span>
<span data-ttu-id="47fdf-103">在許多實例中，您將針對某一類型撰寫商務規則，預期判斷提示至引擎的該類型的每個執行個體可依照規則分別分析與作用。</span><span class="sxs-lookup"><span data-stu-id="47fdf-103">In many scenarios, you will write a business rule against a type and expect each instance of the type that is asserted into the engine to be separately analyzed and acted upon by the rule.</span></span> <span data-ttu-id="47fdf-104">不過，在某些實例中，您想要在規則中同時分析指定類型的多重執行個體。</span><span class="sxs-lookup"><span data-stu-id="47fdf-104">In some scenarios, however, you will want to analyze multiple instances of a given type simultaneously in a rule.</span></span>  
  
 <span data-ttu-id="47fdf-105">接受例如使用的執行個體的規則**FamilyMember**類別。</span><span class="sxs-lookup"><span data-stu-id="47fdf-105">Take for example a rule that uses instances of the **FamilyMember** class.</span></span>  
  
```  
IF FamilyMember.Role == Father  
AND FamilyMember.Role == Son  
AND FamilyMember.Surname == FamilyMember.Surname  
THEN FamilyMember.AddChild(FamilyMember)  
```  
  
 <span data-ttu-id="47fdf-106">此規則會識別**FamilyMember**這個執行個體是**父親**與另一個執行個體**Son**。</span><span class="sxs-lookup"><span data-stu-id="47fdf-106">The rule identifies a **FamilyMember** instance that is a **Father** and another instance that is a **Son**.</span></span> <span data-ttu-id="47fdf-107">如果執行個體以姓氏相關， **Son**執行個體加入 Father 執行個體的子系的集合。</span><span class="sxs-lookup"><span data-stu-id="47fdf-107">If the instances are related by surname, the **Son** instance is added to a collection of children on the Father instance.</span></span> <span data-ttu-id="47fdf-108">如果每個**FamilyMember**規則中分別分析執行個體，此規則會永遠不會引發，因為在此案例中， **FamilyMember**只有一個角色 —**父親**或**Son**。</span><span class="sxs-lookup"><span data-stu-id="47fdf-108">If each **FamilyMember** instance were analyzed separately in the rule, the rule would never fire, because in this scenario, the **FamilyMember** only has one role—**Father** or **Son**.</span></span>  
  
 <span data-ttu-id="47fdf-109">因此，您必須在規則中指示引擎應一起分析多個執行個體，且您需要一個區分規則中每個執行個體識別的方法。</span><span class="sxs-lookup"><span data-stu-id="47fdf-109">Therefore, you must indicate to the engine that multiple instances should be analyzed together in the rule, and you need a way to differentiate the identity of each instance in the rule.</span></span> <span data-ttu-id="47fdf-110">**執行個體識別碼**屬性用來提供這項功能。</span><span class="sxs-lookup"><span data-stu-id="47fdf-110">The **Instance ID** property is used to provide this functionality.</span></span> <span data-ttu-id="47fdf-111">當事實在 [事實總管] 中已選取時，可在 [屬性] 視窗中使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="47fdf-111">This field is available in the Properties window when a fact is selected in Facts Explorer.</span></span> <span data-ttu-id="47fdf-112">將事實或成員拖曳至規則中之前，應該先變更欄位的值。</span><span class="sxs-lookup"><span data-stu-id="47fdf-112">You should change the value of the field prior to dragging a fact or member into a rule.</span></span>  
  
 <span data-ttu-id="47fdf-113">使用**執行個體識別碼**屬性，可重建規則。</span><span class="sxs-lookup"><span data-stu-id="47fdf-113">Using the **Instance ID** property, the rule would be rebuilt.</span></span> <span data-ttu-id="47fdf-114">使用這些規則引數**Son**的執行個體**FamilyMember**、**執行個體識別碼**欄位從 0 到 1 的預設值變更。</span><span class="sxs-lookup"><span data-stu-id="47fdf-114">For those rule arguments that use the **Son** instance of **FamilyMember**, the **Instance ID** field is changed from the default of 0 to 1.</span></span> <span data-ttu-id="47fdf-115">當執行個體識別碼從 0 變更且事實或成員拖曳至規則編輯器時，執行個體識別碼的值會顯示在規則中的類別之後。</span><span class="sxs-lookup"><span data-stu-id="47fdf-115">When the Instance ID is changed from 0 and the fact or member is dragged into the rule editor, the value of Instance ID will show up in the rule after the class.</span></span>  
  
```  
IF FamilyMember.Role == Father  
AND FamilyMember(1).Role== Son  
AND FamilyMember.Surname == FamilyMember(1).Surname  
THEN FamilyMember.AddChild(FamilyMember(1))  
```  
  
 <span data-ttu-id="47fdf-116">現在，假設**父親**執行個體和**Son**執行個體判斷提示至引擎。</span><span class="sxs-lookup"><span data-stu-id="47fdf-116">Now, assume that a **Father** instance and a **Son** instance are asserted into the engine.</span></span> <span data-ttu-id="47fdf-117">此引擎將針對各種執行個體組合評估此規則。</span><span class="sxs-lookup"><span data-stu-id="47fdf-117">The engine will evaluate the rule against the various combinations of the instances.</span></span> <span data-ttu-id="47fdf-118">假設**父親**和**Son**執行個體具有相同姓氏， **Son**執行個體將會新增至**父親**做為執行個體目的。</span><span class="sxs-lookup"><span data-stu-id="47fdf-118">Assuming that the **Father** and **Son** instance have the same surname, the **Son** instance will be added to the **Father** instance as intended.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47fdf-119">**執行個體識別碼**只用在指定的規則評估的內容。</span><span class="sxs-lookup"><span data-stu-id="47fdf-119">The **Instance ID** is only used within the context of a given rule evaluation.</span></span> <span data-ttu-id="47fdf-120">它不會在執行原則時附加到物件執行個體，而且與判斷提示物件的順序無關。</span><span class="sxs-lookup"><span data-stu-id="47fdf-120">It is not affixed to an object instance across the policy execution and is not related to the order in which objects are asserted.</span></span> <span data-ttu-id="47fdf-121">每個物件執行個體都會在該類型的所有規則引數中評估。</span><span class="sxs-lookup"><span data-stu-id="47fdf-121">Each object instance will be evaluated in all rule arguments for that type.</span></span>