---
title: "巢狀位置記錄 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e205e9d-f740-4177-b45a-5e1baadae99a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c278d3ac794c560d8cd886605c1d04c097793564
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="nested-positional-records"></a>巢狀序數記錄
如果允許巢狀序數記錄**Max Occurs**子記錄的屬性設定為正整數。 欄位自動計算應該能夠處理新的深度。 不過，此行為的方式有些修改。 特別是因為可能有空值分隔符號，所以只會在符合下列其中一個條件時，欄位位置的自動計算才會運作：  
  
-   選取的節點有中置分隔的父系。  
  
-   選取的節點有指定的開始位置。  
  
 請注意，巢狀序數記錄和父系為分隔的容器 (分隔符號為空值) 之序數記錄有所不同。 對於真正巢狀位置的結構而言，在決定深度時不能有任何模稜兩可之處。 例如，分隔的迴圈節點可以包含一個重複的序數記錄，出現 0 至 N 次。 不過，因為該迴圈節點本身由位置決定，而且也可能包含對等於重複序數記錄的欄位，所以必須確定重複序數記錄的出現次數 (正整數)。  
  
## <a name="see-also"></a>另請參閱  
 [位置記錄的考量](../core/positional-record-considerations.md)