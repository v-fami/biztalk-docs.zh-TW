---
title: "如何設定例外狀況圖形 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Throw Exception shape [Orchestration Designer]
- orchestrations, errors
- Orchestration Designer, errors
ms.assetid: d3190f1b-db5e-4988-bff6-f7a276760ece
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07d156572484ba4fbe71533252ce4fe956136699
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-throw-exception-shape"></a>如何設定例外狀況圖形
您可以明確擲回例外狀況的協調流程中使用**擲回的例外狀況**圖形。 執行擲回動作時，執行階段引擎會搜尋最接近且可以處理擲回之例外狀況類型的例外處理常式。  
  
 首先，執行階段引擎會先在目前的協調流程中搜尋封閉式範圍，再循序考慮此範圍中相關的例外處理常式，以針對擲回的例外狀況類型，找出適當的處理常式。  
  
 如果找不到適當的例外處理常式，便會在呼叫目前協調流程的協調流程中，搜尋含括目前協調流程之呼叫點的範圍。 這項搜尋作業會繼續進行，直到找到可以處理目前例外狀況的例外處理常式為止。  
  
 與例外狀況完全相符的例外狀況類別，屬於與擲回之例外狀況執行階段型別相同的類別，或是其基底類別。  
  
 找到相符的例外處理常式之後，控制權便會轉移到例外處理常式的第一個陳述式。  
  
 若相符例外處理常式的搜尋失敗，協調流程便會中止。 交易可以幫助您降低這種狀況的影響。  
  
## <a name="procedure"></a>程序  
  
#### <a name="to-configure-a-throw-exception-shape"></a>若要設定例外狀況圖形  
  
-   在 屬性 視窗中，選取 可用的物件類型，以從擲回**例外狀況物件**下拉式清單。  
  
    > [!NOTE]
    >  選取 一般例外狀況中**擲回的例外狀況**圖形才**擲回的例外狀況**圖形位於例外狀況處理常式，而且您想要重新擲回目前例外狀況處理常式中攔截到例外狀況。 如果您使用的一般例外狀況，您會在編譯期間收到錯誤**擲回的例外狀況**圖形中其他任何內容。  
  
## <a name="see-also"></a>另請參閱  
 [例外狀況](../core/exceptions.md)