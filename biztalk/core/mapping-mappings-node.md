---
title: 對應 （對應節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Mapping node [binding file]
ms.assetid: bc54c476-505c-4020-b7df-1d19f86329aa
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2c62d46e4d5c2b73eee5094ecda0e20c039798a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="mapping-mappings-node"></a>對應 (對應節點)
繫結檔案的 [對應] 節點描述已登錄合作對象之合作對象連接埠和角色連接埠類型作業之間的對應。  
  
## <a name="nodes-in-the-mapping-node"></a>對應節點中的節點  
 下表列出可以為繫結檔案中的這個節點設定的屬性：  
  
|**名稱**|**節點類型**|**資料類型**|**說明**|**限制**|**註解**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|PortTypeName|Attribute|xs:string|指定連接埠類型的名稱。|不需要|預設值：空白|  
|OperationName|Attribute|xs:string|指定屬於此連接埠類型的作業。|不需要|預設值：空白|  
|[SendPortRef](../core/sendportref-mapping-node.md)|記錄|SendPortRef (ComplexType)|與對應有關之傳送埠清單的容器節點。|不需要|預設值：無|