---
title: ReceiveLocationTransportType （ReceiveLocation 節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ReceiveLocationTransportType node [binding file]
ms.assetid: 375076c3-d5e6-4c25-b054-b452e29717e0
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d0eae3e2c4fd9f5f668cb12ffd630640b1b63c74
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268718"
---
# <a name="receivelocationtransporttype-receivelocation-node"></a>ReceiveLocationTransportType (ReceiveLocation 節點)
繫結檔案的 [ReceiveLocation] 節點的 [ReceiveLocationTransportType] 節點中，包含與隨同繫結檔案所匯出的傳輸關聯之配接器的特定資訊。  
  
## <a name="nodes-in-the-receivelocationtransporttype-node"></a>ReceiveLocationTransportType 節點中的節點  
 下表列出可以為繫結檔案中的這個節點設定的屬性：  
  
|**名稱**|**節點類型**|**資料類型**|**說明**|**限制**|**註解**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|名稱|Attribute|xs:string|指定與傳輸關聯之配接器的名稱。|不需要|預設值：空白|  
|Capabilities|Attribute|xs:int|指定與傳輸關聯之配接器的功能。|Required|預設值：無<br /><br /> 可能的值包含 [Microsoft.BizTalk.ExplorerOM.Capabilities](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.capabilities.aspx) 列舉中可用的值。|  
|ConfigurationClsid|Attribute|xs:string|指定與傳輸關聯之配接器的組態 GUID。|不需要|預設值：空白|