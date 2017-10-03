---
title: "如何新增補償區塊 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- compensations, compensation blocks
- compensation blocks, adding
ms.assetid: 1bdeed92-3144-44ef-ad0d-1c6976f46a36
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2dec4f4dd01c2bbf522dfff44ec8aaf0c2f5e89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-compensation-block"></a>如何新增補償區塊
如果您不新增自己的補償，執行階段引擎便會執行預設的補償，叫用目前交易內任何巢狀交易的補償。 它首先會叫用最近完成之交易的補償，然後回溯處理直到補償了所有的巢狀交易為止。  
  
 如此即使當您進行補償 「 迴圈 」 圖形： 補償將會依照反向順序執行。 首先，會叫用迴圈最後一次反覆的補償，然後叫用前一次反覆的補償，依此類推。  
  
> [!CAUTION]
>  由於資料會保存到實體記憶體中供補償處理，因此在迴圈內使用補償會影響效能，而這在大量反覆運算的情況下，可能造成問題。  
  
 如果預設的處理順序不符需求，您可以自行撰寫補償處理常式，依您指定的順序明確呼叫巢狀範圍的補償處理常式。  
  
### <a name="to-add-a-compensation-block"></a>若要新增補償區塊  
  
1.  以滑鼠右鍵按一下**範圍**圖形，您要新增的交易**補償區塊**，然後按一下 **新補償區塊**。  
  
    > [!NOTE]
    >  若要加入**補償區塊**至**範圍**圖形，**交易類型**屬性**範圍**圖形必須設定為**不可部分完成**或**長時間執行的**。  
  
     A**補償區塊**緊接相關聯的協調流程加入**範圍**圖形。  
  
2.  內部**補償區塊**圖形中，新增圖形以建立恢復認可的交易的處理序。