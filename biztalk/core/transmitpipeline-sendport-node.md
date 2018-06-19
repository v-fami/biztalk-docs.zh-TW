---
title: TransmitPipeline （SendPort 節點） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TransmitPipeline node [binding file]
ms.assetid: cee55451-6c3f-4e37-aef9-870d4b5d23aa
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4addad5ea98781865b44470f2d07b577afce6c0f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279270"
---
# <a name="transmitpipeline-sendport-node"></a>TransmitPipeline (SendPort 節點)
繫結檔案之 [SendPort ] 節點的 [TransmitPipeline] 節點，會針對繫結於隨同繫結檔案所匯出之傳送埠的傳送管線提供特定資訊。  
  
## <a name="nodes-in-the-transmitpipeline-node"></a>TransmitPipeline 節點中的節點  
 下表列出可以為繫結檔案中的這個節點設定的屬性：  
  
|**名稱**|**節點類型**|**資料類型**|**說明**|**限制**|**註解**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|名稱|Attribute|xs:string|指定傳送管線的名稱。|不需要|預設值：空白|  
|FullyQualifiedName|Attribute|xs:string|指定管線的完整名稱，此名稱包括管線被部署為其一部分之組件的名稱。|不需要|預設值：空白|  
|類型|Attribute|xs:int|指定管線的類型。|Required|預設值：無<br /><br /> 可能的值記載於 [Microsoft.BizTalk.ExplorerOM.PipelineType](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.pipelinetype.aspx) 列舉中。|  
|TrackingOption|Attribute|PipelineTrackingTypes (SimpleType)|指定管線的追蹤選項。|Required|預設值：無<br /><br /> 可能的值記載於 [Microsoft.BizTalk.ExplorerOM.PipelineTrackingTypes](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.pipelinetrackingtypes.aspx) 列舉中。|  
|說明|Attribute|xs:string|指定傳送管線的描述。|不需要|預設值：空白|