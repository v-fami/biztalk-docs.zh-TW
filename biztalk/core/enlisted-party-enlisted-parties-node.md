---
title: 已登錄合作對象 （已登錄合作對象節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Enlisted Parties node [binding file]
ms.assetid: 2ff7b563-17c5-48e9-b33e-62c821188448
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 624f74d3b49b80e8000723c3f7451c52b37c8d3d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="enlisted-party-enlisted-parties-node"></a>已登錄的合作對象 (已登錄的合作對象節點)
繫結檔案的 [已登錄的合作對象] 節點包含與隨著繫結檔案匯出之角色關聯的已登錄之合作對象的特定資訊。  
  
## <a name="nodes-in-the-enlisted-party-node"></a>已登錄的合作對象節點中的節點  
 下表列出可以為繫結檔案中的這個節點設定的屬性：  
  
|**名稱**|**節點類型**|**資料類型**|**說明**|**限制**|**註解**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|名稱|Attribute|xs:string|指定已登錄的合作對象的名稱|不需要|預設值：空白|  
|[對應](../core/mappings-enlisted-party-node.md)|記錄|ArrayOfEnlistedPartyMapping (ComplexType)|合作對象連接埠與角色連接埠類型作業間之對應的容器節點。|不需要|預設值：無|