---
title: "SendHandler （SecondaryTransport 節點） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SendHandler node [binding file]
ms.assetid: 32eb3e87-25ac-461e-9c09-3d6d9bcba3b2
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f5ecdbb1860c9132133835b8928f85b1e0e1cfb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sendhandler-secondarytransport-node"></a>SendHandler (SecondaryTransport 節點)
繫結檔案之 [SecondaryTransport] 節點的 [SendHandler] 節點中，包含與隨同繫結檔案所匯出的傳輸關聯之傳送處理常式的特定資訊。  
  
## <a name="nodes-in-the-sendhandler-node"></a>SendHandler 節點中的節點  
 下表列出可以為繫結檔案中的這個節點設定的屬性：  
  
|**名稱**|**節點類型**|**資料類型**|**說明**|**限制**|**註解**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|名稱|Attribute|xs:string|指定與傳輸關聯之傳送處理常式的名稱。|不需要|預設值：空白|  
|HostTrusted|Attribute|xs:boolean|指定與傳送處理常式關聯的主控件是否受到信任。|Required|預設值：無<br /><br /> 設定為**true**主控件受到信任，否則設為**false**。|  
|[TransportType （SendHandler 節點）](../core/transporttype-sendhandler-node.md)|記錄|ProtocolType (ComplexType)|指定傳輸類型，這也是用於此傳送處理常式的配接器名稱。|Required|預設值：無|