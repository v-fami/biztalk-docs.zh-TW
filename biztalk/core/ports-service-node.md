---
title: 連接埠 （服務節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Ports node [binding file]
ms.assetid: 498d4310-4e9e-4e74-bc3d-5cbf1319c4ff
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31e09470b9f3287cce5ce15c2941d2165157ec48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="ports-service-node"></a>連接埠 (服務節點)
繫結檔案的 [連接埠] 節點是所有 [連接埠] 節點的父節點，這些 [連接埠] 節點包含隨同繫結檔案一起匯出之繫結至服務的連接埠的特定相關資訊。  
  
## <a name="node-in-the-ports-node"></a>連接埠節點中的節點  
 下表列出可以為繫結檔案中的這個節點設定的屬性：  
  
|**名稱**|**節點類型**|**資料類型**|**說明**|**限制**|**註解**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[[通訊埠]](../core/port-ports-node.md)|記錄|ServicePortRef (ComplexType)|指定繫結至隨同繫結檔案匯出之服務的連接埠特定資訊。|不需要|預設值：無|