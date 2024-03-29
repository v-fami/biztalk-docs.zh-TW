---
title: ReceivePipeline （SendPort 節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ReceivePipeline node [binding file]
ms.assetid: 5305f255-e7a2-4052-bf50-4fb207cfae8d
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 210c54b18cc174f31ff795a657f7d23044cebc58
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268870"
---
# <a name="receivepipeline-sendport-node"></a>ReceivePipeline (SendPort 節點)
繫結檔案之 [SendPort] 節點的 [ReceivePipeline] 節點中，包含繫結至隨同繫結檔案匯出之雙向傳送埠的接收管線特定資訊。  
  
## <a name="nodes-in-the-receivepipeline-node"></a>ReceivePipeline 節點中的節點  
 下表列出可以為繫結檔案中的這個節點設定的屬性：  
  
|**名稱**|**節點類型**|**資料類型**|**說明**|**限制**|**註解**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|名稱|Attribute|xs:string|指定傳送管線的名稱。|不需要|預設值：空白|  
|FullyQualifiedName|Attribute|xs:string|指定管線的完整格式名稱，此名稱包含管線被部署為其一部分之組件的名稱。|不需要|預設值：空白|  
|類型|Attribute|xs:int|指定管線的類型。|Required|預設值：無<br /><br /> 可能的值記載於<br /><br /> [Microsoft.BizTalk.ExplorerOM.PipelineType](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.pipelinetype.aspx)列舉型別。|  
|TrackingOption|Attribute|PipelineTrackingTypes (SimpleType)|指定管線的追蹤選項。|Required|預設值：無<br /><br /> 可能的值記載於 [Microsoft.BizTalk.ExplorerOM.PipelineTrackingTypes](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.pipelinetrackingtypes.aspx) 列舉中。|  
|說明|Attribute|xs:string|指定傳送管線的描述。|不需要|預設值：空白|