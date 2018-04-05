---
title: 角色 （角色節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Role node [binding file]
ms.assetid: dfe2a579-7090-4d85-87e5-d627598c4ee8
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d70e99568db262ef5abd5b0885cb814c722347f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="role-roles-node"></a>角色 (角色節點)
繫結檔案之 [角色] 節點的 [角色] 節點，指定有關該繫結檔案所匯出服務繫結到之角色的資訊。  
  
## <a name="nodes-in-the-role-node"></a>角色節點中的節點  
 下表列出可以為繫結檔案中的這個節點設定的屬性：  
  
|**名稱**|**節點類型**|**資料類型**|**說明**|**限制**|**註解**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|名稱|Attribute|xs:string|指定角色的名稱。|不需要|預設值：空白|  
|RoleLinkTypeName|Attribute|xs:string|指定與角色關聯之角色連結類型的名稱。|不需要|預設值：空白|  
|RoleType|Attribute|RoleRefType (SimpleType)|指定與角色關聯之角色類型的名稱。|Required|預設值：無<br /><br /> 可能的值包括：<br /><br /> -不明<br />-實作<br />-使用|  
|[已登錄合作對象](../core/enlisted-parties-role-node.md)|記錄|ArrayOfEnlistedParty (ComplexType)|繫結到此角色之已登錄合作對象的容器節點|不需要|預設值：無|