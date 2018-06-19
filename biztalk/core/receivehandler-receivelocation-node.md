---
title: ReceiveHandler （ReceiveLocation 節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ReceiveHandler node [binding file]
ms.assetid: dd105052-ec71-4762-aa74-e8cdb806a6bf
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e865886624731414f979c77f3f2e898e417c8b11
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268534"
---
# <a name="receivehandler-receivelocation-node"></a>ReceiveHandler (接收位置節點)
繫結檔案的 [接收位置] 節點的 [ReceiveHandler] 節點中，包含與隨同繫結檔案所匯出的傳輸關聯之接收處理函式的特定資訊。  
  
## <a name="nodes-in-the-receivehandler-node"></a>ReceiveHandler 節點中的節點  
 下表列出可以為繫結檔案中的這個節點設定的屬性：  
  
|**名稱**|**節點類型**|**資料類型**|**說明**|**限制**|**註解**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|名稱|Attribute|xs:string|指定與傳輸關聯之接收處理常式的名稱。|不需要|預設值：空白|  
|HostTrusted|Attribute|xs:boolean|指定與接收處理常式關聯的主控件是否受到信任。|Required|預設值：無<br /><br /> 設定為**true**主控件受到信任，否則設為**false**。|  
|[TransportType （ReceiveHandler 節點）](../core/transporttype-receivehandler-node.md)|記錄|ProtocolType (ComplexType)|指定傳輸類型，這也是用於此接收處理常式的配接器名稱。|Required|預設值：無|