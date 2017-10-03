---
title: "算術運算子 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d73e153c-aac1-4cea-92d8-af4a1bea6e6a
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b3d66a990437929176835228efa1a74a5fa8683
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="arithmetic-operators"></a>算術運算子
商務規則架構可支援使用加法、減法、乘法、除法和餘數運算子來建立商務規則。 下表描述可用的算數運算子。  
  
|算術運算子|Description|  
|-------------------------|-----------------|  
|**加入**|代表加法運算子 (arg1 加到 arg2)。|  
|**減去**|代表減法運算子 (arg2 減 arg1)。|  
|**相乘**|代表乘法運算子 (arg1 乘以 arg2)。|  
|**Divide**|代表除法運算子 (arg1 除以 arg2)。|  
|**餘數**|代表餘數運算子 (arg1 除以 arg2 的餘數)。|  
  
 當運算元的類型不同時，便會發生自動數值升級，將較小的運算元類型轉換成較大的運算元類型。 例如，如果**新增**運算子搭配的第一個運算元**int**類型和第二個運算元**長**類型，第一個運算元的類型會轉換成**長**執行之前**新增**作業。 如果兩個運算元都可以升級成一般類型，則規則引擎也可以支援雙重升級。 例如，如果**新增**運算子搭配的第一個運算元**int**類型和第二個運算元**uint**類型，這兩個運算元的類型會轉換成**長**執行之前**新增**作業。  
  
## <a name="to-use-a-logical-operator-in-a-business-rule"></a>在商務規則中使用邏輯運算子  
 使用下列程序可在商務規則中使用邏輯運算子。  
  
1.  在 事實總管 視窗中，按一下**詞彙** 索引標籤。  
  
2.  展開**詞彙**，依序展開**函式**，依序展開**1.0 版-已發佈**，然後將拖曳**新增/減/乘/除/餘數**到 條件窗格 / 執行 窗格。  
  
3.  指定左運算子和右運算子的值。  
  
## <a name="see-also"></a>另請參閱  
 [邏輯運算子](../core/logical-operators.md)