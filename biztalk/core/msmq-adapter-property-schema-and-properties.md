---
title: MSMQ 配接器屬性結構描述和屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- AcknowledgeType property [MSMQ adapters]
- MSMQ adapters, schemas
- AppSpecific property [MSMQ adapters]
- SegmentationSupport property [MSMQ adapters]
- SourceMachine property [MSMQ adapters]
- Label property, MSMQ adapters
- MSMQ adapters, properties
- TimeOut property [MSMQ adapters]
- BodyType property [MSMQ adapters]
- CorrelationId property [MSMQ adapters]
- Recoverable property [MSMQ adapters]
- Authenticated property [MSMQ adapters]
- EncryptionAlgorithm property [MSMQ adapters]
- ResponseQueue property [MSMQ adapters]
- configuring [MSMQ adapters], properties
- MaximumMessageSize property [MSMQ adapters]
- UseAuthentication property [MSMQ adapters]
- UseDeadLetterQueue property [MSMQ adapters]
- SentTime property [MSMQ adapters]
- schemas, MSMQ adapters
- TimeOutUnits property [MSMQ adapters]
- CertificateThumbPrint property [MSMQ adapters]
- Id property [MSMQ adapters]
- UseJournalQueue property [MSMQ adapters]
- MessageType property [MSMQ adapters]
- ArrivedTime property [MSMQ adapters]
- Transactional property [MSMQ adapters]
- configuring [MSMQ adapters], schemas
- Acknowledgement property [MSMQ adapters]
- Priority property [MSMQ adapters]
- AdministrationQueue property [MSMQ adapters]
ms.assetid: 9de29341-db8e-4d50-8f1d-3b7397afb58d
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 356aac0cbe7444c0b81955ae4982524606d11d54
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985383"
---
# <a name="msmq-adapter-property-schema-and-properties"></a>MSMQ 配接器屬性結構描述和屬性
MSMQ 配接器可指派值到您在應用程式中使用的內容屬性中。 取得一份傳送和接收 MSMQ 配接器中的屬性，請參閱[如何設定 MSMQ 接收位置](../core/how-to-configure-an-msmq-receive-location.md)並[如何設定 MSMQ 傳送埠](../core/how-to-configure-an-msmq-send-port.md)。  
  
## <a name="context-properties"></a>內容屬性  
 下表顯示 MSMQ 配接器指派值到其中的內容屬性。  
  
|**名稱**|**型別**|**說明**|**升級**|  
|--------------|--------------|---------------------|------------------|  
|**通知**|ssNoversion|指定的通知，此訊息表示使用中的值**System.Messaging.Acknowledgment**列舉型別。|否|  
|**AcknowledgeType**|ssNoversion|指定傳送應用程式要求的通知訊息類型。|否|  
|**AdministrationQueue**|string|指定接收通知訊息的佇列名稱之名稱。|否|  
|**AppSpecific**|ssNoversion|指定您可以用來組織不同訊息類型的應用程式特定資訊。|是|  
|**ArrivedTime**|dateTime|指定訊息到達目的地佇列的時間。|否|  
|**驗證**|boolean|指定訊息是否已驗證。|否|  
|**BodyType**|int|指定訊息內文包含的資料類型。|否|  
|**CertificateThumbPrint**|string|指定用於訊息驗證用途的用戶端憑證指紋。|是|  
|**相互關聯識別碼**|string|指定通知、報告以及回應訊息用來參考原始訊息的訊息識別項。|是|  
|**EncryptionAlgorithm**|ssNoversion|指定用來加密訊息內文的加密演算法。|否|  
|**Id**|string|指定訊息的識別項。|否|  
|**標籤**|string|指定描述訊息的應用程式定義 Unicode 字串。|是|  
|**MaximumMessageSize**|unsignedint|指定傳送到指定佇列的訊息之訊息大小上限 (以 KB 為單位)。|否|  
|**MessageType**|ssNoversion|指定訊息類型。 訊息佇列訊息可以是下列其中一種類型：<br /><br /> -Normal： 這是傳送至佇列，應用程式的一般訊息或回應訊息傳回給傳送應用程式。<br />-通知是每當傳送應用程式要求訊息佇列產生。 例如，訊息佇列可以產生正數或負數以指示原始訊息已送達或已讀取。 訊息佇列會將適當的通知訊息傳回由傳送應用程式指定的管理佇列。<br />-報表，每當報告佇列在來源佇列管理員定義訊息佇列產生。 啟用追蹤時，訊息佇列在每次原始訊息進入或離開訊息佇列伺服器時，會傳送報告訊息至訊息佇列報告。|否|  
|**優先權**|ssNoversion|指定使用中定義的值的訊息優先權**System.Messaging.MessagePriority**列舉型別。|是|  
|**可復原**|boolean|指定是否保證會在電腦當機或網路發生問題時傳遞訊息。|否|  
|**ResponseQueue**|string|指定接收應用程式產生之回應訊息的佇列。|否|  
|**SegmentationSupport**|boolean|指定是否支援大於 4 MB 的訊息區段。|否|  
|**SentTime**|dateTime|指定傳送電腦在來源佇列管理員傳送訊息時的日期與時間。|否|  
|**以 SourceMachine**|string|指定發出訊息的電腦。|否|  
|**TimeOut**|ssNoversion|指定在逾時發生之前訊息抵達目的地佇列的時間。|否|  
|**TimeOutUnits**|string|指定的單位**逾時**屬性。 您可以設定屬性為 [天]、[小時]、[分] 或 [秒]。|否|  
|**異動**|boolean|指定交易式與非交易式傳送埠及接收位置的行為。|否|  
|**UseAuthentication**|boolean|指定訊息在傳送之前是否 (或必須) 驗證。|否|  
|**UseDeadLetterQueue**|boolean|指定無法遞送的訊息複本是否應該傳送到寄不出的信件佇列。|否|  
|**UseJournalQueue**|boolean|指定訊息複本是否應該保留在來源電腦的電腦記錄檔中。|否|  
  
> [!NOTE]
>  **收條**， **AcknowledgeType**， **EncryptionAlgorithm**，以及**MessageType**屬性使用整數相等項中的列舉值**System.Messaging**命名空間。 如需這些值的詳細資訊，請參閱「.NET Framework 類別庫說明」中的＜System.Messaging 名稱空間＞。  
> 
> [!NOTE]
>  如果您要開發 BizTalk 專案，讓使用 MSMQ 配接器內容屬性，BizTalk 專案必須包含檔案的參考**Microsoft.BizTalk.Adapter.MSMQ.MsmqAdapterProperties.dll**位於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝目錄。  
  
## <a name="message-labels"></a>訊息標籤  
 您可以使用 Message Queuing**標籤**藉由將參考加入的篩選器中的屬性**Microsoft.BizTalk.Adapter.MSMQ.MsmqAdapterProperties.dll** ，然後選取中的屬性**篩選** 對話方塊。 您也可以使用其他內容中的屬性，因為 MSMQ 配接器會自動將它新增到訊息內容。  
  
## <a name="see-also"></a>另請參閱  
 [設定 MSMQ 配接器](../core/configuring-the-msmq-adapter.md)