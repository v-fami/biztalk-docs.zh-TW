---
title: "TransmitPipeline （ReceivePort 節點） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: TransmitPipeline node [binding file]
ms.assetid: 0f3b728f-1e4a-40e5-9ca9-f7dcdf995cbe
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf1b105f2e7cfc5601469ac55cac6af22aa21a16
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="transmitpipeline-receiveport-node"></a>TransmitPipeline (ReceivePort 節點)
繫結檔案的 [ReceivePort] 節點的 [TransmitPipeline] 節點，會針對繫結於隨同繫結檔案所匯出之雙向接收埠的傳送管線提供特定資訊。  
  
> [!NOTE]
>  因為傳送管線的雙向接收的繫結的接收位置層級[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]，此節點會提供回溯相容性與 BizTalk Server 2004。 傳送管線雙向接收的繫結在 BizTalk Server 2004 中接收埠層級。 針對從 BizTalk 2004 匯出之繫結檔案的這個節點所設定的屬性，將會在您匯入該繫結檔案至 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 時，套用至接收埠所參考的每一個雙向接收位置的 SendPipeline 節點。  
  
## <a name="nodes-in-the-transmitpipeline-node"></a>TransmitPipeline 節點中的節點  
 下表列出可以為繫結檔案中的這個節點設定的屬性：  
  
|**名稱**|**節點類型**|**資料類型**|**說明**|**限制**|**註解**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|名稱|Attribute|xs:string|指定傳送管線的名稱。|不需要|預設值：空白|  
|FullyQualifiedName|Attribute|xs:string|指定管線的完整格式名稱，此名稱包含管線被部署為其一部分之組件的名稱。|不需要|預設值：空白|  
|類型|Attribute|xs:int|指定管線的類型。|Required|預設值：無<br /><br /> 可能的值記載於<br /><br /> [Microsoft.BizTalk.ExplorerOM.PipelineType](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.pipelinetype.aspx)列舉型別。|  
|TrackingOption|Attribute|PipelineTrackingTypes (SimpleType)|指定管線的追蹤選項。|Required|預設值：無<br /><br /> 可能的值記載於 [Microsoft.BizTalk.ExplorerOM.PipelineTrackingTypes](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.pipelinetrackingtypes.aspx) 列舉中。|  
|說明|Attribute|xs:string|指定傳送管線的描述。|不需要|預設值：空白|  
  
## <a name="see-also"></a>另請參閱  
 [傳送管線](../core/sendpipeline-receivelocation-node.md)   
 [ReceiveLocation](../core/receivelocation-receivelocations-node.md)