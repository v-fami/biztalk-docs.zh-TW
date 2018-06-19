---
title: ModuleRef （ModuleRefCollection 節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ModuleRef node [binding file]
ms.assetid: 61787779-33bd-499a-a5c1-c1e0bd306b48
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ed580b022e9896ade824c8cf8eccc2458c7ddce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262902"
---
# <a name="moduleref-modulerefcollection-node"></a>ModuleRef (ModuleRefCollection 節點)
繫結檔案的 [ModuleRef] 節點包含與該繫結檔案一起匯出之 .NET 組件有關的特定資訊。 ModuleRef 節點包含 (但不限於) 有自訂程式碼、結構描述和協調流程之組件的說明。  
  
## <a name="nodes-in-the-moduleref-node"></a>ModuleRef 節點中的節點  
 下表列出可以為繫結檔案中的這個節點設定的屬性：  
  
|**名稱**|**節點類型**|**資料類型**|**說明**|**限制**|**註解**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[服務](../core/services-moduleref-node.md)|記錄|ArrayOfServiceRef (ComplexType)|與此 .NET 組件相關聯之服務的容器節點。|不需要|預設值：無|  
|[TrackedSchemas （ModuleRef 節點）](../core/trackedschemas-moduleref-node.md)|記錄|ArrayOfSchema (ComplexType)|與此 .NET 組件相關聯之結構描述的容器節點。|不需要|預設值：無|