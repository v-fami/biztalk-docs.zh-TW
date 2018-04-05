---
title: TransportType |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TransportType node [binding file]
ms.assetid: 64eb00be-47c9-473f-aec6-03cb7f948e3b
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8d9636e7aa6dd8b09bb73678072242ed8b8725a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="transporttype"></a>TransportType
繫結檔案之 SendHandler 節點的 TransportType 節點，包含與該繫結檔案一起匯出之傳輸有關之配接器的特定資訊。  
  
## <a name="nodes-in-the-transporttype-node"></a>TransportType 節點中的節點  
 下表列出可以為繫結檔案中的這個節點設定的屬性：  
  
|**名稱**|**節點類型**|**資料類型**|**說明**|**限制**|**註解**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|名稱|Attribute|xs:string|指定與傳送處理常式關聯之配接器的名稱。|不需要|預設值：空白|  
|Capabilities|Attribute|xs:int|指定與傳送處理常式關聯之配接器的功能。|Required|預設值：無<br /><br /> 可能的值包含 [Microsoft.BizTalk.ExplorerOM.Capabilities](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.capabilities.aspx) 列舉中可用的值。|  
|ConfigurationClsid|Attribute|xs:string|指定與傳送處理常式關聯之配接器的組態 GUID。|不需要|預設值：空白|