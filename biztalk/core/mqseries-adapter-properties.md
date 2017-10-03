---
title: "MQSeries 配接器屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MQXQH_RemoteQName property [MQSeries adapters]
- MQMD_ReplyToQ property [MQSeries adapters]
- configuring [MQSeries adapters], properties
- MQXQH_MsgDesc_ReplyToQMgr property [MQSeries adapters]
- UserHttpHeaders property [MQSeries adapters]
- MQMD_CorrelId property [MQSeries adapters]
- MQXQH_MsgDesc_MsgId property [MQSeries adapters]
- MQXQH_MsgDesc_ReplyToQ property [MQSeries adapters]
- SubmissionHandle property [MQSeries adapters]
- BizTalk_CorrelationID property [MQSeries adapters]
- MQMD_ReplyToQMgr property [MQSeries adapters]
- EnableChunkedEncoding property [MQSeries adapters]
- MQSeries adapters, properties
- MQXQH_MsgDesc_CorrelId property [MQSeries adapters]
- MQXQH_RemoteQMgrName property [MQSeries adapters]
- MQMD_MsgId property [MQSeries adapters]
ms.assetid: c3cfbc8c-4c9b-431e-b0b6-4c065a69ce6b
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fae8cc1ed67f077b6ae12945da10c58cf0f147da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="mqseries-adapter-properties"></a>MQSeries 配接器屬性
若要從 BizTalk 協調流程存取 MQSeries 標頭屬性，您必須將 MQSeries.dll 組件的參考新增到您的專案。 這個組件位於您安裝 MQSeries 配接器的位置，例如 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]。  
  
 您參考 MQSeries 屬性結構描述之後，其他內容屬性可用於各種 BizTalk Server 開發工具 (例如，**訊息指派**圖形在協調流程設計師 」 中的)。  
  
> [!NOTE]
>  當您處理 MQSeries 標頭屬性時，請確定您遵照＜IBM WebSphere MQ＞文件中的指導方針。  
  
 配接器會自動升級部分 MQSeries 屬性。 您的應用程式和自訂元件必須避免降級這些屬性。 您可以使用自訂管線元件升級的其他屬性。 自動升級的屬性如下：  
  
-   **BizTalk_CorrelationID**  
  
-   **MQMD_CorrelId**  
  
-   **MQMD_MsgId**  
  
-   **MQMD_ReplyToQ**  
  
-   **MQMD_ReplyToQMgr**  
  
-   **MQXQH_RemoteQMgrName**  
  
-   **MQXQH_RemoteQName**  
  
-   **MQXQH_MsgDesc_CorrelId**  
  
-   **MQXQH_MsgDesc_MsgId**  
  
-   **MQXQH_MsgDesc_ReplyToQ**  
  
-   **MQXQH_MsgDesc_ReplyToQMgr**  
  
## <a name="in-this-section"></a>本節內容  
  
-   [屬性的資料類型轉換](../core/data-type-conversion-of-properties.md)  
  
-   [與 BizTalk Server 相關的屬性](../core/properties-related-to-biztalk-server.md)  
  
-   [MQSeries 內容屬性](../core/mqseries-context-properties.md)  
  
## <a name="see-also"></a>另請參閱  
 [設定 MQSeries 配接器](../core/configuring-the-mqseries-adapter.md)