---
title: 訊息 TIBCO Rendezvous 中的對應 |Microsoft 文件
description: 訊息欄位和 XML 在 BizTalk Adapter for TIBCO Rendezvous 訊息對應
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62793bec-f076-425c-b25e-c4be5bd93cc8
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb80ea4f908aa50dc32755c333aa3ccf2ea4db91
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24014949"
---
# <a name="message-mapping-in-tibco-rendezvous"></a>TIBCO Rendezvous 中的訊息對應
TIBCO Rendezvous 訊息是由標頭資訊與一系列訊息欄位所組成。 標頭資訊直接對應訊息內容屬性。  
  
## <a name="message-field-elements"></a>訊息欄位元素  
 訊息欄位由下列元素所組成：  
  
|元素|Description|  
|-------------|-----------------|  
|**名稱**|字元字串。 在訊息中不需是唯一的。|  
|**識別碼**|短整數。 在訊息中是唯一的。 以隱含方式將訊息到 65535 之間的欄位數目的限制。 識別項的範圍是訊息 （或子訊息）。 相同的識別碼可用於兩個子訊息 (包含的訊息中它們各自的部分) 中。|  
|**值**|訊息欄位資料。|  
|**Count**|項目數 (在陣列的情況中)|  
|**型別**|訊息欄位的類型。|  
  
### <a name="mapping-process"></a>對應程序  
 TIBCO Rendezvous 結構化訊息會以下列方式對應至 XML 元素：  
  
-   **名稱**做為項目名稱。 TIBCO Rendezvous 欄位名稱可能會包含無法做為 XML 元素名稱的字元。 配接器會在 XML 與 TIBCO Rendezvous 結構化訊息之間產生有效的字元對應。  
  
-   **識別項**會放入 'id' 屬性。  
  
-   **值**包含項目主體的字串表示法。  
  
-   **計數**會被忽略。  
  
-   **型別**資訊放入產生的元素的 xsi: type 屬性。  
  
     如需詳細資訊，請參閱[Data Type Mapping for TIBCO Rendezvous 中的 接收處理常式](../core/data-type-mapping-for-receive-handlers-in-tibco-rendezvous.md)。  
  
## <a name="see-also"></a>另請參閱  
 [TIBCO Rendezvous 概念](../core/tibco-rendezvous-concepts.md)   
 [建立 TIBCO Rendezvous 接收處理常式](../core/creating-tibco-rendezvous-receive-handlers.md)