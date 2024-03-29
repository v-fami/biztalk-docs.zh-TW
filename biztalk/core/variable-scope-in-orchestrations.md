---
title: 協調流程中的變數範圍 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, variables
ms.assetid: 5856cdca-0ebd-4e16-8739-7bd50753b9f9
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82803cd7f2b0beb8349e978fdd7b9e453dca31ce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288118"
---
# <a name="variable-scope-in-orchestrations"></a>協調流程中的變數範圍
關於協調流程中各個部分的變數和協調流程參數之可見性和狀態 (包含例外狀況處理常式和補償區塊)，您必須瞭解一些重點。  
  
-   您可以在協調流程的整個內文及其補償區塊中看到協調流程參數。  
  
-   範圍層級的變數可以在範圍的內文及其所有例外狀況處理常式與補償區塊中看到。 在例外狀況處理常式內部，變數被視為未初始化，因為它無法確定引導至指定處理常式的例外狀況發生在內文中的任何初始作業之前或之後。 基於這個原因，若您在範圍中宣告變數並在內文中將它初始化，您就不能在例外狀況處理常式中讀取它，否則會發生編譯器錯誤。 該狀況的處理方式存在長時間執行交易的案例中。 下列範例顯示，成功的 () 運算子如何能用來確保適當的執行階段行為：  
  
    > [!NOTE]
    >  下面程式碼為描述邏輯程序的虛擬程式碼；此程式碼不能用在「協調流程運算式」圖形中。  
  
    ```  
    scope longrunning transaction L  
    {  
       System.Int32 i;  
       System.Int32 v;  
       body  
       {  
          i = 3;  
          scope longrunning transaction T  
          {  
             body  
             {  
                i = 5;  
             }  
          }  
       }  
       exceptions  
       {  
          catch  
          {  
             if(succeeded(T))  
             {  
                v = i;  // OK to read from it here — no compiler errors!  
             }  
          }  
       }  
    }  
    ```  
  
-   在補償區塊內部，所有變數會假設為認可範圍內文時所具有的值。 請注意，範圍的補償區塊絕不會在其內文完成之後立即執行；永遠會有中間程式碼。 若該中間程式碼更新部分範圍外部變數，然後執行補償區塊，則在補償區塊內部將看不到這些更新。 相反地，變數將暫時還原為值，其值為它們在擁有該補償的範圍已認可階段所具有的值。  
  
-   當迴圈中有巢狀交易時，該交易將被補償的次數與迴圈執行的次數相同。 在每個重複項目的補償區塊內部，範圍外部變數會假設為認可重複交易時所具有的值。  
  
-   對範圍外部變數或內部範圍的補償區塊中之協調流程參數所做的更新，在補償區塊完成後將看不到。 換句話說，補償區塊不能用來直接修改範圍外部變數的值。  
  
## <a name="see-also"></a>另請參閱  
 [XLANG 的資料型別](../core/xlang-s-data-types.md)