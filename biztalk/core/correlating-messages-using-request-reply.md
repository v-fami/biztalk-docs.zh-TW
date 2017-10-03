---
title: "相互關聯使用要求-回覆訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, MQSeries adapters
- messages, correlating
- MQSeries adapters, correlating messages
ms.assetid: 4615b586-663b-41d8-949c-fefb6143c590
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f2f13d8dea9192e982f597311ca3ea13fa213ed0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="correlating-messages-using-request-reply"></a>使用要求-回應相互關聯訊息
有兩種方式可將 IBM WebSphere MQ 的 BizTalk 協調流程中的訊息，和 Windows 平台要求-回應實例的伺服器元件中的訊息相互關聯。 第一個方法是將 messageid 來提供相互關聯識別項 (**MQMD_MSGID**) 與 CorrelationID (**MQMD_CorrelId**) 為相同的值。 第二個是使用**BizTalk_CorrelationId**內容屬性。  
  
## <a name="setting-mqmdmsgid-and-mqmdcorrelid-to-the-same-value"></a>將 MQMD_MsgId 與 MQMD_CorrelId 設為相同值  
 將訊息傳送到 IBM WebSphere MQ Queue Manager 時，您可以設定訊息識別項 (**MQMD_MSGID**) 和相互關聯識別項 (**MQMD_CorrelId**) 為外寄訊息中相同的值. IBM WebSphere MQ Queue Manager 會在回覆訊息中複製 MessageID 到 CorrelationID。 下圖顯示此程序。  
  
 ![簡單相互關聯](../core/media/bts-dev-mqsimplecorrelation.gif "BTS_Dev_MQSimpleCorrelation")  
  
 您可以初始化的相互關聯集內送訊息使用的值與外寄訊息的相互關聯集**MQMD_CorrelId**。  
  
## <a name="using-the-mqseriesbiztalkcorrelationid-context-property"></a>使用 MQSeries.BizTalk_CorrelationId 內容屬性  
 而不是將 MessageID 與 CorrelationID 設外寄訊息中相同的值，您可以使用**BizTalk_CorrelationID**內容屬性與請求-回應傳送埠 MQSeries 配接器。 下圖顯示這個程序。  
  
 ![使用請求 &#45;若要產生的相互關聯識別碼的回應](../core/media/bts-dev-mqgeneratedcorrelation.gif "BTS_Dev_MQGeneratedCorrelation")  
  
 若要針對 BizTalk 協調流程中的相互關聯使用 IBM WebSphere MQ Server 提供的識別項，BizTalk Server 必須先取得識別項。 您的應用程式透過請求-回應要求執行此工作。 BizTalk Server 使用 MQSeries 配接器傳送請求-回應要求到 IBM WebSphere MQ Server。 會接收回應的訊息識別項 (**MQMD_MSGId**) 和相互關聯識別項 (**MQMD_CorrelId**)。  
  
 請求-回應傳送埠中的外寄訊息，配接器複製**MQMD_MSGID**到 IBM WebSphere MQ server 產生**MQSeries.BizTalk_CorrelationId**內容屬性。  
  
 配接器接收訊息時，會複製**MQMD_CorrelId**至**MQSeries.BizTalk_CorrelationId**。 在此情況下，使用相互關聯集，您可以初始化外寄訊息和相互關聯集內送訊息使用的相互關聯集**MQSeries.BizTalk_CorrelationId**。  
  
## <a name="see-also"></a>另請參閱  
 [MQSCorrelationSetOrchestrationWithSolicitResponse （BizTalk Server 範例）](../core/mqscorrelationsetorchestrationwithsolicitresponse-biztalk-server-sample.md)