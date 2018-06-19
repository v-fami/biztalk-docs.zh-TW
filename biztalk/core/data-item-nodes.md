---
title: 資料項目節點 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- definition files [BAM], data items
- Data Item nodes [Tracking Profile Editor]
- Tracking Profile Editor, node descriptions
- Tracking Profile Editor, definition files [BAM]
ms.assetid: 95856bfa-90e3-49d9-b55b-5f1b35a23f78
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a968bf7533697922938eeb8953f17813c77147c2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238022"
---
# <a name="data-item-nodes"></a>資料項目節點
資料項目節點存在於開發人員從商務分析師所建立觀察模型匯入的活動定義檔案中。 追蹤設定檔編輯器 (TPE) 將這些節點命名為節點所追蹤的資料項目，例如 Customer Name。 接著，您將「訊息結構描述檢視」(Message Schema View) 中的一或多個資料項目放到對應於 Customer Name 的節點。  
  
## <a name="working-with-data-item-nodes"></a>使用資料項目節點  
 對應資料項目節點時，若商務程序跨越多個追蹤設定檔，則每個商務程序只應該追蹤一次資料項目。 如果協調流程中含有條件路徑，您可以同時選取兩個路徑中的資料，因為將只有一個會執行。 不過，您不可以選擇迴圈內的圖形，除非資料項目的值會隨著每一次反覆運算而有所不同。  
  
## <a name="see-also"></a>另請參閱  
 [如何對應項目資料](../core/how-to-map-item-data.md)   
 [TPE 活動檢視節點](../core/tpe-activity-view-nodes.md)