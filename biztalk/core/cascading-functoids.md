---
title: "串聯運算質 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functoid types, Cascading
- Cascading functoids
ms.assetid: 03c46e7b-be1c-475e-b68b-f9d1d7732fce
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d5e9cfcad2432eb83c8a251147bac76b20db0bc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="cascading-functoids"></a>串聯運算質
當一個運算質在連結到目的結構描述中的記錄或欄位之前，先連結到另一個運算質時，稱為串連運算質。 例如，您可以建立串連運算質，其中兩個串連的字串會產生要傳送至目的結構描述的欄位中的第三個字串。  
  
 當您串連運算質時，可以在格線頁中建立多個連續的轉換。 雖然在一頁中可串連的運算質數目沒有限制，但請謹慎使用。 複雜的串連會增加轉換輸入執行個體訊息為輸出執行個體訊息的時間，這會嚴重降低執行階段效能。  
  
## <a name="see-also"></a>另請參閱  
 [在對應中的運算質](../core/functoids-in-maps.md)   
 [使用運算質建立更複雜的對應](../core/using-functoids-to-create-more-complex-mappings.md)