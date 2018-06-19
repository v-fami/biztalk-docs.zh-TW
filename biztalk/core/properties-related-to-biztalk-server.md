---
title: BizTalk Server 相關屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring [MQSeries adapters], properties
- CompleteMessage property [MQSeries adapters]
- SSOAffiliateApplication property [MQSeries adapters]
- Ordered property [MQSeries adapters]
- TransactionSupported property [MQSeries adapters]
- BizTalk_CorrelationID property [MQSeries adapters]
- SegmentationAllowed property [MQSeries adapters]
- DynamicReceive property [MQSeries adapters]
- MQSeries adapters, properties
- DataConversion property [MQSeries adapters]
ms.assetid: c27d7f9c-8198-4624-9952-054ba8ea1c7c
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f729e4ab359471e002029efc04c0c8ad21e0d99b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269654"
---
# <a name="properties-related-to-biztalk-server"></a>與 BizTalk Server 相關的屬性
MQSeries 配接器會指派值到不是直接與 MQSeries 相關但仍在應用程式中有用的部分內容屬性。  
  
 所有屬性都會都接收值期間傳送和接收除了**BizTalk_CorrelationID**。 **BizTalk_CorrelationID**屬性只在接收期間有值。  
  
|名稱|型別|Description|  
|----------|----------|-----------------|  
|**BizTalk_CorrelationID**|string|使用這個屬性讓 MQSeries 伺服器產生相互關聯識別項以用於訊息。<br /><br /> 如需詳細資訊，請參閱[相互關聯訊息使用要求-回覆](../core/correlating-messages-using-request-reply.md)。|  
|**DataConversion**|string|將訊息轉換為 MQSeries Server for Windows 的 ANSI 字碼頁。 傳送時，若訊息格式不是 MQFMT_STRING，就不會轉換。<br /><br /> 選取**是**執行從 Unicode 轉換成 ANSI。<br /><br /> **預設值：** 否|  
|**排序**|string|設定 MQSeries 在接收到或傳送至 MQSeries 佇列的訊息時維護訊息順序。<br /><br /> 屬性對於傳送和接收有不同的值組。 如需有關值的詳細資訊，請參閱 [如何設定 MQSeries 配接器接收位置和傳送埠](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md)。<br /><br /> **預設值：** 否|  
|**SegmentationAllowed**|string|設定 MQSeries 以組合分割的訊息或就訊息原貌取得訊息。 屬性對於傳送和接收有不同的值組。<br /><br /> 在接收時，使用**No Action**從 MQSeries 佇列讀取訊息，而不啟用分割; 使用**完整訊息**讓 MQSeries 組合分割的訊息，再將其傳遞配接器。<br /><br /> **預設值：** 採取任何動作<br /><br /> 傳送時，選取**是**，讓 MQSeries 將分割的訊息放在佇列中。<br /><br /> **預設值：** 否|  
|**SSOAffiliateApplication**|string|設定單一登入 (SSO) 分支機構應用程式。 您使用的使用者識別碼和密碼 sso **MQMD_UserIdentifier**，而**MQIIH_Authenticator** (或**MQCIH_Authenticator**) 屬性分別。<br /><br /> 只有在傳送訊息時使用。<br /><br /> **預設值：** 空白|  
|**CompleteMessage**|string|指定從佇列擷取分割的訊息時是否擷取「完整訊息」。<br /><br /> 將此設**是**擷取 「 完整訊息 」 中分割的訊息佇列。<br /><br /> **預設值：** 否|  
|**DynamicReceive**|string|指定是否從佇列動態擷取訊息。<br /><br /> 將此設**是**動態地從佇列接收訊息時。 在搭配使用請求-回應傳送埠時會使用這個功能。<br /><br /> 若您指定符合選項 (MessageID、CorrelationID 或 GroupID)，那麼將只會擷取與符合準則相互關聯的訊息。|  
|**TransactionSupported**|string|配接器會開始 BizTalk Server 與 MQSeries Server 之間的 Microsoft Distributed Transaction Coordinator (DTC) 交易。 當設定為**否**，不保證訊息傳遞。<br /><br /> **預設值：** [是]|  
|**WaitInterval**|string|指定 MQ 系統等待適當訊息到達的大約時間 (以秒計)。 如果適當訊息未在此時間內到達，呼叫就會失敗。 **注意：** 這只能在協調流程內設定。 <br /><br /> **預設值：** 3|  
  
## <a name="see-also"></a>另請參閱  
 [MQSeries 配接器屬性](../core/mqseries-adapter-properties.md)   
 [屬性的資料類型轉換](../core/data-type-conversion-of-properties.md)   
 [MQSeries 內容屬性](../core/mqseries-context-properties.md)