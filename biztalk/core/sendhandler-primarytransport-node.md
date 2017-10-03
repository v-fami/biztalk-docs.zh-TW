---
title: "SendHandler （PrimaryTransport 節點） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SendHandler node [binding file]
ms.assetid: c0b200ee-ecbc-4708-a2c8-c37cd6cd0060
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 029285e9b56aeb91bbca7a7c9eacf6abedc7ebbc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sendhandler-primarytransport-node"></a>SendHandler (PrimaryTransport 節點)
繫結檔案之 [PrimaryTransport] 節點的 [SendHandler] 節點中，包含與隨同繫結檔案一起匯出的傳輸關聯之傳送處理常式的特定資訊。  
  
## <a name="nodes-in-the-sendhandler-node"></a>SendHandler 節點中的節點  
 下表列出可以為繫結檔案中的這個節點設定的屬性：  
  
|**名稱**|**節點類型**|**資料類型**|**說明**|**限制**|**註解**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|名稱|Attribute|xs:string|指定與傳輸關聯之傳送處理常式的名稱。|不需要|預設值：空白|  
|HostTrusted|Attribute|xs:boolean|指定與傳送處理常式關聯的主控件是否受到信任。|Required|預設值：無<br /><br /> 設定為**true**主控件受到信任，否則設為**false**。|  
|[TransportType](../core/transporttype.md)|記錄|ProtocolType (ComplexType)|指定傳輸類型，這也是用於此傳送處理常式的配接器名稱。|Required|預設值：無|