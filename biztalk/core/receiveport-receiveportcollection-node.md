---
title: ReceivePort （ReceivePortCollection 節點） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30ae9cef-4e0f-42ca-ac45-fe1fabdfc7c5
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b8e30a789327f872e384152d64a2edbebb4b9dd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023156"
---
# <a name="receiveport-receiveportcollection-node"></a>ReceivePort (ReceivePortCollection 節點)
繫結檔案之 ReceivePortCollection 節點的 ReceivePort 節點，包含與該繫結檔案一起匯出之接收埠的相關特定資訊。  

## <a name="nodes-in-the-receiveport-node"></a>ReceivePort 節點中的節點  
 下表列出可以為繫結檔案中的這個節點設定的屬性：  


|                                      **名稱**                                       | **節點類型** |            **資料類型**             |                                               **說明**                                               | **限制** |                                                                                                 **註解**                                                                                                  |
|-------------------------------------------------------------------------------------|---------------|--------------------------------------|-------------------------------------------------------------------------------------------------------------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                        [屬性]                                         |   attribute   |              xs:string               |                                   指定接收埠的名稱。                                   |   不需要   |                                                                                             預設值：空白                                                                                              |
|                                      IsTwoWay                                       |   attribute   |              xs:boolean              |               指定接收埠為單向或要求-回應 (雙向)。               |     必要項     |      預設值：無<br /><br /> 可能的值位於**MSBTS_SendPort.IsTwoWay 屬性 (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]      |
|                                    BindingOption                                    |   attribute   |                xs:int                |                          指定協調流程連接埠的繫結類型。                          |     必要項     |                                             預設值：無<br /><br /> 可能的值位於**Microsoft.BizTalk.ExplorerOM.BindingType**列舉型別。                                              |
|                                     描述                                     |    元素    |              xs:string               |                                指定接收埠的描述。                                |     必要項     |                                                                                             預設值：空白                                                                                              |
|          [ReceiveLocations](../core/receivelocations-receiveport-node.md)           |    記錄     | ArrayOfReceiveLocation (ComplexType) |                 與此接收埠相關聯之接收位置的容器節點。                 |  非必要   |                                                                                              預設值：無                                                                                              |
| [TransmitPipeline (ReceivePort 節點)](../core/transmitpipeline-receiveport-node.md) |    記錄     |      PipelineRef (ComplexType)       | 指定當接收埠為雙向接收埠時，會與接收埠相關聯的傳送管線。 |   不需要   |                                                                                              預設值：無                                                                                              |
|                                  SendPipelineData                                   |    元素    |              xs:string               |         指定此管線用途之執行個體特定的自訂組態。          |   不需要   |                                                                                             預設值： 空白。                                                                                             |
|                                   驗證                                    |    元素    |                xs:int                |      指定列舉值，指示在此接收埠是否需要驗證。       |     必要項     |                                          預設值：無<br /><br /> 可能的值位於**Microsoft.BizTalk.ExplorerOM.AuthenticationType**列舉型別。                                          |
|                                      追蹤                                       |    元素    |                xs:int                |                        指定接收埠的文件追蹤層級                        |     必要項     |                                            預設值：無<br /><br /> 可能的值位於**Microsoft.BizTalk.ExplorerOM.TrackingTypes**列舉型別。                                             |
|       [Transforms (ReceivePort 節點)](../core/transforms-receiveport-node.md)       |    記錄     |    ArrayOfTransform (ComplexType)    |                  指定單向接收埠之輸入轉換的集合。                  |   不需要   |                                                                                              預設值：無                                                                                              |
|        [OutboundTransforms](../core/outboundtransforms-receiveport-node.md)         |    記錄     |    ArrayOfTransform (ComplexType)    |       指定套用至雙向接收埠上之文件的輸出轉換的集合。       |   不需要   |                                                                                              預設值：無                                                                                              |
|                                 RouteFailedMessage                                  |    元素    |              xs:boolean              |             指定失敗訊息是否會傳送至失敗的訊息訂閱者。              |     必要項     | 預設值：無<br /><br /> 可能的值位於**MSBTS_SendPort.RouteFailedMessage 屬性 (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] |
|                                   ApplicationName                                   |    元素    |              xs:string               |                   指定與接收埠相關聯之應用程式的名稱。                   |     必要項     |           預設值：空白<br /><br /> 可能的值位於**ISSOMapping 介面 (COM)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]           |

