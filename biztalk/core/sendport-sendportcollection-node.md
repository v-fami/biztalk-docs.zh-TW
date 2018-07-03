---
title: SendPort （SendPortCollection 節點） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5cf7a6f9-9240-48b9-b196-8838afd4f41e
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c948ab5d288a714e790b22d7e79e5256094f08f9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008543"
---
# <a name="sendport-sendportcollection-node"></a>SendPort (SendPortCollection 節點)
繫結檔案的 SendPort 節點包含與該繫結檔案一起匯出之傳送埠有關的特定資訊。  

## <a name="nodes-in-the-sendport-node"></a>SendPort 節點中的節點  
 下表列出可以為繫結檔案中的這個節點設定的屬性：  


|                                   **名稱**                                    | **節點類型** |         **資料類型**          |                                       **說明**                                        | **限制** |                                                                                            **註解**                                                                                             |
|-------------------------------------------------------------------------------|---------------|--------------------------------|----------------------------------------------------------------------------------------------|------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                     [屬性]                                      |   attribute   |           xs:string            |                             指定傳送埠的名稱。                             |   不需要   |                                                                                        預設值：空白                                                                                         |
|                                   IsStatic                                    |   attribute   |           xs:boolean           |                    指定傳送埠是靜態或動態。                     |     必要項     |                                                                                         預設值：無                                                                                         |
|                                   IsTwoWay                                    |   attribute   |           xs:boolean           |         指定傳送埠是單向或是請求-回應 (雙向) 傳送埠。         |     必要項     |                                               預設值：無<br /><br /> 可能的值位於**MSBTS_SendPort.IsTwoWay 屬性 (WMI)**。                                                |
|                                 BindingOption                                 |   attribute   |             xs:int             |                  指定協調流程連接埠的繫結類型。                   |     必要項     |                                        預設值：無<br /><br /> 可能的值位於**Microsoft.BizTalk.ExplorerOM.BindingType**列舉型別。                                        |
|                                  描述                                  |    元素    |           xs:string            |                          指定傳送埠的說明。                          |     必要項     |                                                                                        預設值：空白                                                                                         |
| [TransmitPipeline (SendPort 節點)](../core/transmitpipeline-sendport-node.md) |    記錄     |   PipelineRef (ComplexType)    |                  指定與傳送埠關聯的傳送管線。                  |   不需要   |                                                                                         預設值：無                                                                                         |
|                               SendPipelineData                                |    元素    |           xs:string            |  指定此管線用途之執行個體特定的自訂組態。  |   不需要   |                                                                                        預設值： 空白。                                                                                        |
|         [PrimaryTransport](../core/primarytransport-sendport-node.md)         |    記錄     |  TransportInfo (ComplexType)   |  指定傳送埠已設定使用之主要傳輸的相關資訊。  |   不需要   |                                                                                         預設值：無                                                                                         |
|       [SecondaryTransport](../core/secondarytransport-sendport-node.md)       |    記錄     |  TransportInfo (ComplexType)   | 指定傳送埠已設定使用之次要傳輸的相關資訊。 |   不需要   |                                                                                         預設值：無                                                                                         |
|           [EncryptionCert](../core/encryptioncert-sendport-node.md)           |    記錄     | CertificateInfo (ComplexType)  |       指定與傳送埠搭配使用之加密憑證的相關資訊。        |   不需要   |                                                                                         預設值：無                                                                                         |
|          [ReceivePipeline](../core/receivepipeline-sendport-node.md)          |    記錄     |   PipelineRef (ComplexType)    |          指定與傳送埠搭配使用之任何接收管線的相關資訊。          |   不需要   |                                                                                         預設值：無                                                                                         |
|                              ReceivePipelineData                              |    元素    |           xs:string            |  指定此管線用途之執行個體特定的自訂組態。  |     必要項     |                                                                                        預設值：空白                                                                                         |
|                                   追蹤                                    |    元素    |             xs:int             |                  指定傳送埠的文件追蹤層級。                  |     必要項     |                                       預設值：無<br /><br /> 可能的值位於**Microsoft.BizTalk.ExplorerOM.TrackingTypes**列舉型別。                                       |
|                                    篩選                                     |    元素    |           xs:string            |         指定此傳送埠上使用的選擇性篩選條件運算式名稱。         |     必要項     |                                                預設值：空白<br /><br /> 可能的值位於**MSBTS_SendPort.Filter 屬性 (WMI)**                                                 |
|       [Transforms (SendPort 節點)](../core/transforms-sendport-node.md)       |    記錄     | ArrayOfTransform (ComplexType) |           指定單向傳送埠輸出轉換的集合。            |   不需要   |                                                                                         預設值：無                                                                                         |
|        [InboundTransforms](../core/inboundtransforms-sendport-node.md)        |    記錄     | ArrayOfTransform (ComplexType) |            指定雙向傳送埠輸入轉換的集合。            |   不需要   |                                                                                         預設值：無                                                                                         |
|                                OrderedDelivery                                |    元素    |           xs:boolean           |           指定傳送埠是否會排序訊息傳遞。            |     必要項     |                                            預設值：無<br /><br /> 可能的值位於**MSBTS_SendPort.OrderedDelivery 屬性 (WMI)**                                            |
|                                   優先權                                    |    元素    |             xs:int             |                           指定傳送埠的優先順序。                           |     必要項     |                                                 預設值： 5<br /><br /> 可能的值位於**MSBTS_SendPort.Priority 屬性 (WMI)**                                                  |
|                             StopSendingOnFailure                              |    元素    |           xs:boolean           |         指定傳送埠是否會在失敗時停止傳送訊息。          |     必要項     |                                          預設值：無<br /><br /> 可能的值位於**MSBTS_SendPort.StopSendingOnFailure 屬性 (WMI)**                                          |
|                              RouteFailedMessage                               |    元素    |           xs:boolean           |      指定失敗訊息是否會傳送至失敗的訊息訂閱者。      |     必要項     |                                           預設值：無<br /><br /> 可能的值位於**MSBTS_SendPort.RouteFailedMessage 屬性 (WMI)**                                           |
|                                ApplicationName                                |    元素    |           xs:string            |             指定與傳送埠關聯的應用程式名稱。             |     必要項     | 預設值：空白<br /><br /> 可能的值位於**ISSOMapping.ApplicationName 屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。 |

## <a name="see-also"></a>另請參閱
更多詳細資料，這些屬性[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。