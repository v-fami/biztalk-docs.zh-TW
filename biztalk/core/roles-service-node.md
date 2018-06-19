---
title: 角色 （服務節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Roles node [binding file]
ms.assetid: 847755c9-1697-41a0-b870-f9e795a1a2a6
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b47f5ae94326b0555c0c9cd84752cb9f1c409daa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268398"
---
# <a name="roles-service-node"></a>角色 (服務節點)
繫結檔案的 [角色] 節點是所有 [角色] 節點的父節點，這些節點提供與繫結檔案一起匯出之服務所繫結每個角色的特定資訊。  
  
## <a name="nodes-in-the-roles-node"></a>角色節點中的節點  
 下表列出可以為繫結檔案中的這個節點設定的屬性：  
  
|**名稱**|**節點類型**|**資料類型**|**說明**|**限制**|**註解**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[角色](../core/role-roles-node.md)|記錄|RoleRef (ComplexType)|指定與繫結檔案一起匯出之服務所繫結角色的相關資訊。|不需要|預設值：無|