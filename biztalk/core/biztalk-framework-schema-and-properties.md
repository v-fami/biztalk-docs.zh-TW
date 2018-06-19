---
title: BizTalk Framework 結構描述和屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8986e4a7-0c0a-415f-8a74-4fca71d3f1b5
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 992f0fb9c66ee00cf425609db4231a57bf5782c4
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
ms.locfileid: "22232718"
---
# <a name="biztalk-framework-schema-and-properties"></a>BizTalk Framework 結構描述和屬性
**http://schemas.microsoft.com/BizTalk/2003/btf2-properties**命名空間包含可用來設定 BizTalk Framework 解譯器管線元件的訊息和部分內容屬性的屬性。 「BizTalk Framework 解譯器」管線元件使用這些屬性在建立的訊息中產生適當的標頭。 下表描述 BizTalk Framework 屬性。  

## <a name="properties-list"></a>屬性清單  
|名稱|型別|Description|  
|----------|----------|-----------------|  
|**IsReliable**|xs:boolean|指示 BizTalk Framework 訊息是否應重新傳送直到從目的接收到通知為止。 此屬性由 BizTalk Framework 元件在內部設定，並由引擎使用。 請勿從程式碼變更此屬性中的值。|  
|**PassAckThrough**|xs:boolean|指示通知訊息是否應通過「BizTalk Framework 解譯器」管線元件，而不是被取用。|  
|**eps_to_address**|xs:string|指定目的地址。|  
|**eps_to_address_type**|xs:string|指定目的地址類型。|  
|**eps_from_address**|xs:string|指定來源地址。|  
|**eps_from_address_type**|xs:string|指定來源地址類型。|  
|**prop_identity**|xs:string|以記錄、追蹤、錯誤處理或其他文件處理及相互關聯需求為目的而唯一識別 BizTalk Framework 文件的 URI 參考。|  
|**prop_sentAt**|xs:string|BizTalk Framework 文件的傳送時間戳記。|  
|**prop_topic**|xs:string|唯一識別 BizTalk Framework 文件的整體目的之 URI 參考。|  
|**svc_deliveryRctRqt_sendTo_address**|xs:string|指定 BizTalk Framework 文件送達回條的傳送地址。|  
|**svc_deliveryRctRqt_sendTo_address_type**|xs:string|指定 BizTalk Framework 文件送達回條的傳送地址類型。|  
|**svc_deliveryRctRqt_sendBy**|xs:dateTime|指定必須收到 BizTalk Framework 文件送達回條的時間 (以分鐘為單位)。|  
|**svc_commitmentRctRqt_sendTo_address**|xs:string|指定處理傳送者要求的收件者決策之通知的傳送地址。|  
|**svc_commitmentRctRqt_sendTo_address_type**|xs:string|指定處理傳送者要求的收件者決策之通知的傳送地址類型。|  
|**svc_commitmentRctRqt_sendBy**|xs:dateTime|指定傳送者必須收到 BizTalk Framework 文件保證回條的時間 (以分鐘為單位)。|  
|**prc_type**|xs:string|提供指定 BizTalk Framework 訊息處理所需的商務程序類型之 URI 參考。|  
|**prc_instance**|xs:string|提供唯一識別與 BizTalk Framework 文件相關聯的特定商務程序執行個體之 URI 參考。|  
|**deliveryRct_receivedAt**|xs:dateTime|指定此回條所通知的文件之接收時間戳記。 接收時間戳記可能反映收到第一份複本的時間或收到通知複本的時間。|  
|**deliveryRct_identity**|xs:string|指定送達回條所通知的 BizTalk Framework 文件識別。|  
|**commitmentRct_identity**|xs:string|指定保證回條所通知的 BizTalk Framework 文件識別。|  
|**commitmentRct_decidedAt**|xs:string|指定此回條所通知的文件之處理決策時間戳記。|  
|**commitmentRct_decision**|xs:string|指定實際決策，其可能值為正數或負數。|  
|**commitmentRct_commitmentCode**|xs:QName|指定完整格式名稱 (以 XSD 格式)，此名稱指定有關處理決策更加特定的狀態。|  
  
## <a name="see-also"></a>另請參閱  
-  **訊息內容屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]   
-  [設定原生管線元件](../core/configuring-native-pipeline-components.md)