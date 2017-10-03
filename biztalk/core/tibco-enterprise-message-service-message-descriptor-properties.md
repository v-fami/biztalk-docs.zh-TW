---
title: "TIBCO 企業訊息服務訊息描述元屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message descriptor properties
ms.assetid: fc164c12-6dc3-4b74-9aa9-024e18faf80a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80c75875c44c4d082089fc9394fef390a0f91571
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tibco-enterprise-message-service-message-descriptor-properties"></a>TIBCO Enterprise Message Service 訊息描述元屬性
下表顯示所有可用的「訊息描述元」(TibcoEMSMD 結構)」屬性及其對應的類型與值。  
  
|名稱|型別|Value|注意|  
|----------|----------|-----------|-----------|  
|TibcoEMS .CorrelationID|string|||  
|TibcoEMS .DelieveryMode|string|PERSISENT 或 NON-PERSISTENT 之一||  
|TibcoEMS .Destination|string||唯讀|  
|TibcoEMS .Expiration|long|||  
|TibcoEMS .MessageID|string||唯讀|  
|TibcoEMS .Priority|integer|從 0 到 9||  
|TibcoEMS .Redelivered|boolean||唯讀|  
|TibcoEMS .ReplyTo|string|與 Destination 類似||  
|TibcoEMS .Timestamp|long||唯讀|  
  
 當訊息傳遞給 Microsoft BizTalk Adapter for TIBCO EMS 時，由 TIBCO Enterprise Message Service 所設定的屬性會是唯讀屬性。 雖然您可以在訊息指派圖形的運算式中變更值，但這麼做並不會影響訊息。  
  
 對於其他必須從 EMS 訊息移至 BizTalk Server 訊息的屬性，您必須建立屬性 DLL 並在專案中加以使用。  
  
 下列範例屬性結構描述可讓協調流程使用 `JMSXDeliveryCount` 訊息屬性。  
  
```  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:b="http://schemas.microsoft.com/BizTalk/2003" targetNamespace="http://schemas.microsoft.com/BizTalk/TibcoEMS-properties" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:annotation>  
        <xs:appinfo>  
            <b:schemaInfo schema_type="property" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" />  
        </xs:appinfo>  
    </xs:annotation>  
    <xs:element name="JMSXDeliveryCount" type="xs:long">  
        <xs:annotation>  
            <xs:appinfo>  
                <b:fieldInfo propertyGuid="f62f1a4b-a528-45fb-b1f8-bd880e9f46db" />  
            </xs:appinfo>  
        </xs:annotation>  
    </xs:element>  
</xs:schema>   
```  
  
 請確定已使用目標命名空間，只有使用此命名空間的屬性會複製到 BizTalk Server 訊息或 EMS 訊息。 如需 訊息內容屬性的詳細資訊，請參閱 BizTalk Server 文件。  
  
## <a name="see-also"></a>另請參閱  
 [訊息內容屬性](../core/message-context-properties2.md)