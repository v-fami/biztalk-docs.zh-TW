---
title: 結構描述 （TrackedSchemas 節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Schema node
ms.assetid: a503aad6-07f8-4650-a214-4d2f6650cb80
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5376c505332ed05507169c1db2dc54ec4e7bdfe6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="schema-trackedschemas-node"></a>結構描述 (TrackedSchemas 節點)
繫結檔案之 TrackedSchemas 節點的 [結構描述] 節點會描述繫結到與繫結檔案一起匯出之服務的結構描述。  
  
## <a name="nodes-in-the-schema-node"></a>結構描述節點中的節點  
 下表列出可以為繫結檔案中的這個節點設定的屬性：  
  
|**名稱**|**節點類型**|**資料類型**|**說明**|**限制**|**註解**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|FullName|Attribute|xs:string|指定此結構描述的完整名稱。|不需要|預設值：空白|  
|AssemblyQualifiedName|Attribute|xs:string|指定包含此結構描述之組件的完整格式名稱。|不需要|預設值：空白|  
|AlwaysTrackAllProperties|Attribute|xs:boolean|指定是否要追蹤指定之組件的所有屬性。|Required|預設值：無<br /><br /> 設定為**true**追蹤所有屬性，否則設為**false**。|  
|Description|Attribute|xs:string|指定此結構描述的描述。|不需要|預設值：空白|  
|[TrackedPropertyNames （結構描述節點）](../core/trackedpropertynames-schema-node.md)|記錄|ArrayOfString (ComplexType)|指定要追蹤之屬性的項目容器。|不需要|預設值：無|