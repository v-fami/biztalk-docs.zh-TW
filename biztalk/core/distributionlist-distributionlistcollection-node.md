---
title: DistributionList （DistributionListCollection 節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- DistributionList node [binding file]
ms.assetid: 51864a5c-1697-4804-ac18-8211494f3ff0
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 931443cdca27e5c06767f075298d50ff999545a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="distributionlist-distributionlistcollection-node"></a>DistributionList (DistributionListCollection 節點)
繫結檔案的 [DistributionList] 節點包含與該繫結檔案一起匯出之通訊群組清單的特定相關資訊。 通訊群組清單在 [BizTalk Server 系統管理員] 中稱為傳送埠群組。  
  
## <a name="nodes-in-the-distributionlist-node"></a>DistributionList 節點中的節點  
 下表列出可以為繫結檔案中的這個節點設定的屬性：  
  
|**名稱**|**節點類型**|**資料類型**|**說明**|**限制**|**註解**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|名稱|Attribute|xs:string|指定通訊群組清單的名稱。|不需要|預設值：空白|  
|[傳送埠](../core/sendports-distributionlist-node.md)|記錄|ArrayOfSendPortRef (ComplexType)|指定通訊群組清單所包含的一個或多個傳送埠。|不需要|預設值：無|  
|篩選|元素|xs:string|指定在此通訊群組清單使用之選擇性篩選條件運算式的名稱。|必要項|預設值：空白|  
|ApplicationName|元素|xs:string|指定通訊群組清單與其關聯之應用程式的名稱。|必要項|預設值：空白|  
|說明|元素|xs:string|指定通訊群組清單的描述。|必要項|預設值：空白|