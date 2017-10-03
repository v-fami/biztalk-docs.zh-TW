---
title: "如何修改規則 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules, activating
- deactivating business rules
- business rules, priorities
- activating business rules
- business rules, deactivating
- modifying, business rules
- business rules, modifying
ms.assetid: 661b2637-b5d6-4bde-9c42-24cd9e9d241c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fce3fb78ce67b6c82f2301dfcb4cb2175aee0dde
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-modify-rules"></a>如何修改規則
變更規則的能力是商務規則範例的重要部分。 您可以使用兩種方式來修改原則中的規則：建立原則的新版本或是直接修改未發佈的原則版本。  
  
 您可以個別修改規則、新增規則或刪除現有的規則。 您可以從規則條件刪除述詞和邏輯運算子、刪除動作、在顯示中往上和往下移動動作，或是在條件中移動述詞和邏輯運算子。 不過，請記住述詞和邏輯運算子的顯示順序並不會決定評估的順序。  
  
 您可以將規則設定為非作用中，這樣在執行原則時就不會執行規則，或者您可以重新啟動已經停用的規則。  
  
 您可以在規則上設定優先順序，這樣就會在不同優先順序的任何規則的動作之前或之後執行其動作。  
  
> [!CAUTION]
>  若您需要停止 SQL Server 電腦，請務必儲存任何未儲存的詞彙版本或詞彙定義，並關閉「商務規則編輯器」，這樣就不會遺失任何變更。  
  
 本主題包含下列工作的程序：  
  
-   變更條件或動作中的引數  
  
-   移動條件中的述詞  
  
-   移動條件中的邏輯運算子  
  
-   變更規則中的動作順序  
  
-   刪除述詞、邏輯運算子或動作  
  
-   啟動或停用規則  
  
-   在規則上設定優先順序  
  
### <a name="to-change-an-argument-in-a-condition-or-action"></a>變更條件或動作中的引數  
  
1.  在 [事實和定義] 視窗中，按一下適當的索引標籤，巡覽至您要作為引數的詞彙。 該詞彙必須是述詞或函式所預期的類型。  
  
2.  按一下詞彙並將它拖曳至條件中的述詞引數或是動作中的函式引數。  
  
### <a name="to-move-a-predicate-within-a-condition"></a>移動條件中的述詞  
  
-   按一下述詞，並將它拖曳至另一個邏輯運算子。  
  
### <a name="to-move-a-logical-operator-within-a-condition"></a>移動條件中的邏輯運算子  
  
-   按一下邏輯運算子，並將它拖曳至另一個邏輯運算子或**條件**。  
  
### <a name="to-change-the-order-of-actions-within-a-rule"></a>變更規則中的動作順序  
  
-   按一下動作，然後按一下 **往上移動動作**或**往下移動動作**。  
  
    > [!NOTE]
    >  規則的動作將會依照引擎控制函式例外狀況所指定的順序執行，這些引擎控制函式將會在其他動作之後執行。  
  
### <a name="to-delete-a-predicate-logical-operator-or-action"></a>刪除述詞、邏輯運算子或動作  
  
-   按一下述詞、 邏輯運算子或動作，然後再按一下**刪除**。  
  
### <a name="to-activate-or-deactivate-a-rule"></a>啟動或停用規則  
  
-   按一下 [規則]，然後在 [屬性] 視窗中設定**Active**為**True**或**False**。  
  
### <a name="to-set-a-priority-on-a-rule"></a>在規則上設定優先順序  
  
-   按一下 [規則]，然後在 [屬性] 視窗中設定**優先順序**為整數值。  
  
    > [!NOTE]
    >  優先順序是相對的，而且某個指定優先順序的規則其所有動作都將在具有較低優先順序值的規則動作之前執行。 優先順序值預設為零，不過它可以是正數或負數。