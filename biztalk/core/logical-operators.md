---
title: 邏輯運算子 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8aaceb64-a5a0-462a-a0eb-8352bed999e5
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e3b3c187e353babafd86590fdeacdc19fc115b6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262070"
---
# <a name="logical-operators"></a>邏輯運算子
「商務規則架構」可支援使用邏輯 AND、邏輯 OR 和邏輯 NOT 運算子來建立商務規則。 下表描述可用的邏輯運算子。  
  
|邏輯運算子|Description|  
|----------------------|-----------------|  
|**AND**|傳回**true**如果這兩個運算元都評估為**true**; 否則會傳回**false**。|  
|**OR**|傳回**true**如果其中一個運算元判斷值為**true**，否則會傳回**false**。|  
|**NOT**|傳回**true**如果運算元等於**false**，否則會傳回**false**。|  
  
 當運算元的類型不同時，規則引擎在評估運算式之前，會轉換其中一個參數的類型，使其符合另一個參數的類型，或是同時將兩個參數的類型轉換為共同的類型。  
  
## <a name="to-use-a-logical-operator-in-a-business-rule"></a>在商務規則中使用邏輯運算子  
 使用下列程序可在商務規則中使用邏輯運算子。  
  
1.  在**如果**的商務規則編輯器 窗格以滑鼠右鍵按一下**條件**節點，然後再選取您想要加入邏輯運算式的邏輯運算子。  
  
2.  以滑鼠右鍵按一下此邏輯運算子，然後加入述詞或是您想要加入的巢狀邏輯運算子。  
  
## <a name="see-also"></a>另請參閱  
 [算術運算子](../core/arithmetic-operators.md)