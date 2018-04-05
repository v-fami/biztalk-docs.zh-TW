---
title: TrackedSchemas （ModuleRef 節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TrackedSchemas node [binding file]
ms.assetid: a2b99fbf-df6b-4a94-97b8-ac5eb819604f
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 303aeb1ed17b001583a596d5b550faf63ea1200b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="trackedschemas-moduleref-node"></a>TrackedSchemas (ModuleRef 節點)
繫結檔案之 TrackedSchemas 節點是所有 [結構描述] 節點的父節點，這些節點會描述繫結至隨同繫結檔案一起匯出之服務的結構描述。  
  
## <a name="nodes-in-the-trackedschemas-node"></a>TrackedSchemas 節點中的節點  
 下表列出可以為繫結檔案中的這個節點設定的屬性：  
  
|**名稱**|**節點類型**|**資料類型**|**說明**|**限制**|**註解**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[結構描述](../core/schema-trackedschemas-node.md)|記錄|ArrayOfSchema (ComplexType)|繫結至隨同繫結檔案一起匯出之服務的結構描述之容器節點。|不需要|預設值：無|