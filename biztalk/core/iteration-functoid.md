---
title: "反覆項目運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Iteration functoids
- Greater Than or Equal To functoids
- And functoids
- Less Than or Equal To functoids
ms.assetid: 24d8911d-2282-4b07-910c-eb2e846dc1f9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a491b8829f23296e77ba5a89d12985e8ccd32783
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="iteration-functoid"></a>重複項目運算質
**反覆項目**運算質的輸出中迴圈的目前記錄的索引結構，在第一筆記錄，而第二個資料錄，2 的 1 開始等等。  
  
 下圖顯示**反覆項目**運算質結合**Greater Than 或 Equal To**運算質，**小於或等於**運算質和**和**建立的對等運算質**如**迴圈。  
  
 ![反覆項目運算質用法的對應](../core/media/iterationfunctoid.gif "iterationfunctoid")  
重複項目運算質對應  
  
 假設**Greater Than 或 Equal To**運算質會測試的值大於或等於 2，而**小於或等於**運算質會測試的值小於或等於 4。 在此情況下，**和**運算質會傳回**true**只針對記錄 2、 3 和 4。 因此，輸出執行個體將會包含兩個、 三和四個輸入執行個體訊息的記錄。  
  
## <a name="see-also"></a>另請參閱  
 [如何新增反覆項目運算質至對應](../core/how-to-add-iteration-functoids-to-a-map.md)   
 [進階運算質](../core/advanced-functoids.md)   
 [索引運算質](../core/index-functoid.md)   
 [迴圈運算質](../core/looping-functoid.md)   
 [記錄計數運算質](../core/record-count-functoid.md)