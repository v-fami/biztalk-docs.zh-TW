---
title: ModuleRefCollection 節點 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ModuleRefCollection node [binding file]
ms.assetid: fa8593bf-6548-4615-9f98-1e0eadde9aa4
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 039cabd380195f840e9ffb99de5071026b3810c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="modulerefcollection-node"></a>ModuleRefCollection 節點
繫結檔案的 ModuleRefCollection 區段是所有 ModuleRef 節點的父節點，這些節點包含隨同繫結檔案一起匯出之 .NET 組件的特定相關資訊。  
  
## <a name="entries-in-the-modulerefcollection-section"></a>ModuleRefCollection 區段中的項目  
 下表列出可以為繫結檔案中這個區段的節點設定的屬性。  
  
|**名稱**|**節點類型**|**資料類型**|**說明**|**限制**|**註解**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[ModuleRef](../core/moduleref-modulerefcollection-node.md)|記錄|ModuleRef (ComplexType)|.NET 組件模組 (由繫結檔案所匯出) 的容器節點。|不需要|預設值：無|