---
title: AS2 內容屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4d63104-f31e-4ed2-b294-ba3ea8a39ae6
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9fffef06db874c63ddabaace9094baa006af67ce
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37020301"
---
# <a name="as2-context-properties"></a>AS2 內容屬性
五種類型的內容屬性適用於 BizTalk Server 中的 AS2 訊息：  

-   EdiIntProperties.xsd 結構描述中的內容屬性  

-   BizTalk Server 內部的內容屬性  

-   BizTalk MIME 內部的內容屬性  

-   AS2 內部的內容屬性  

-   AS2 狀態報告內部的內容屬性  

## <a name="context-properties-in-the-ediintpropertiesxsd-schema"></a>EdiIntProperties.xsd 結構描述中的內容屬性  
 EDI/INT 全域屬性結構描述中的訊息內容屬性都是公開屬性，因此您可以在例如訊息路由等作業中使用這些內容屬性。 這些內容屬性都是定義在 `Microsoft.BizTalk.Edi.BaseArtifacts` 組件的 EdiIntProperties.xsd 結構描述中。 屬性的命名空間是 `http://schemas.microsoft.com/BizTalk/2006/as2-properties`。 如果升級，這些訊息內容屬性可作為`EdiIntAS.<Property Name>`中**篩選**頁面**傳送埠屬性** 對話方塊。  

|[屬性]|類型|描述|  
|----------|----------|-----------------|  
|AS2From|string|包含代表傳送者名稱的 AS2-From AS2 標頭值。|  
|AS2PayloadContentType|string|包含內容 (Payload) 訊息的內容 (Content) 類型。|  
|AS2To|string|包含代表接收者名稱的 AS2-To AS2 標頭值。|  
|DispositionMode|string|包含 MDN 配置模式值。<br /><br /> 這個內容屬性和 DispositionType 內容屬性都必須升級，才能產生 MDN。|  
|DispositionType|string|包含 MDN 配置類型值。<br /><br /> 這個內容屬性和 DispositionMode 內容屬性都必須升級，才能產生 MDN。|  
|IsAS2AsynchronousMdn|boolean|表示訊息是非同步 MDN。|  
|IsAS2FailedMessage|boolean|表示內送 AS2 訊息的 AS2 處理失敗，導致內容訊息遭擱置。|  
|IsAS2Http200OKResponse|boolean|對將產生做為 HTTP 200 OK 回應訊息的訊息進行設定。 不會針對 AS2 訊息產生 MDN 或以非同步方式傳送 MDN 時，便會使用此內容屬性。|  
|IsAS2MdnResponseMessage|boolean|表示此訊息是 MDN 回應訊息。|  
|IsAS2MessageDuplicate|boolean|表示先前已收到內送 AS2 訊息。|  
|IsAS2MessageCompressed|boolean|表示內送 AS2 訊息已壓縮。|  
|IsAS2MessageEncrypted|boolean|表示內送 AS2 訊息已加密。|  
|IsAS2MessageSigned|boolean|表示內送 AS2 訊息已簽署。|  
|IsAS2PayloadMessage|boolean|表示這個訊息包含已解碼的 AS2 訊息內容，而且必須做為內容來處理。|  
|MDNAsyncURI|string|包含**回條傳遞選項**用於傳送非同步 MDN 回應訊息的值。|  
|MessageId|string|包含 AS2 訊息標頭中加入的「AS2 訊息識別碼」。|  
|OriginalMessageId|string|包含原始「AS2 訊息」的「訊息識別碼」。 這個內容屬性是 MDN 訊息的一部分，用來產生 AS2 訊息與其 MDN 回應的相互關聯。|  
|PreservedFileName|string|包含訊息的原始檔案名稱。 只有在內送訊息的 Content-Disposition MIME 標頭包含檔案名稱資訊時，才會填入此內容屬性。|  
|SendMDN|boolean|如果應該產生 MDN 訊息，則設定為 true。|  

## <a name="context-properties-internal-to-biztalk-server"></a>BizTalk Server 內部的內容屬性  
 下列訊息內容屬性都是不公開的，因此您無法在例如訊息路由等作業中使用這些內容屬性。 不過，您可以在擱置和追蹤的訊息中檢視它們。 這些內容屬性的命名空間是 `http://schemas.microsoft.com/BizTalk/2006/system-properties`。  


|                  [屬性]                  |  類型   |                                                                                            描述                                                                                             |
|----------------------------------------|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| IgnoreSslCertificateNameMismatchErrors | boolean |                  指示 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP 處理在處理時應忽略 SSL 名稱不符錯誤。                  |
|               KeepAlive                | 布林 |                                                                    控制 HTTP 保持運作功能的行為。                                                                     |
|        TreatEPMSuspendAsSuccess        | boolean | 指示 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在雙向 HTTP 輸入連線上處理時，將擱置的訊息視為成功訊息來處理。 |
|           IsSolicitResponse            | boolean |                      由 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 設定，表示此訊息為請求-回應訊息。                       |

## <a name="context-properties-internal-to-biztalk-mime"></a>BizTalk MIME 內部的內容屬性  
 下列訊息內容屬性都是不公開的，因此您無法在例如訊息路由等作業中使用這些內容屬性。 不過，您可以在擱置和追蹤的訊息中檢視它們。 這些內容屬性的命名空間是 `http://schemas.microsoft.com/BizTalk/2006/system-properties`。  


|                  [屬性]                   |  類型   |                                                                                     描述                                                                                     |
|-----------------------------------------|---------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            IsMultipartReport            | boolean |                 讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MIME 編碼器產生 multipart/report 訊息。                  |
| SuppressMimeVersionFromMultiPartMessage | boolean | 讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MIME 編碼器隱藏 Multipart 訊息中每個部分的「MIME 版本」標頭。 |

## <a name="context-properties-internal-to-as2"></a>AS2 內部的內容屬性  
 下列訊息內容屬性都是不公開的，因此您無法在例如訊息路由等作業中使用這些內容屬性。 不過，您可以在擱置和追蹤的訊息中檢視它們。 這些內容屬性的命名空間是 `http://schemas.microsoft.com/BizTalk/2006/as2-properties`。  

|[屬性]|類型|描述|  
|----------|----------|-----------------|  
|MicHashAlgorithm|string|包含用來計算 MIC 雜湊值的雜湊演算法。|  
|ReceivedContentMic|string|包含已經過計算的 MIC 雜湊值。|  

## <a name="context-properties-internal-to-as2-status-reporting"></a>AS2 狀態報告內部的內容屬性  
 下列訊息內容屬性都是不公開的，因此您無法在例如訊息路由等作業中使用這些內容屬性。 不過，您可以在擱置和追蹤的訊息中檢視它們。 這些內容屬性的命名空間是 `http://schemas.microsoft.com/BizTalk/2006/edi-properties`。  

|[屬性]|類型|描述|  
|----------|----------|-----------------|  
|InterchangeControlNo|string|來自 EDI 交換的交換控制編號。 這個屬性是在 AS2 編碼期間從訊息中讀取，用來報告 AS2 的「交換活動」。|  
|InterchangeDate|string|來自 EDI 交換的交換日期。 這個屬性是在 AS2 編碼期間從訊息中讀取，用來報告 AS2 的「交換活動」。|  
|InterchangeTime|string|來自 EDI 交換的交換時間。 這個訊息內容屬性是在 AS2 編碼期間從訊息中讀取，用來報告 AS2 的「交換活動」。|  
|ReceiverID|string|來自 EDI 交換的交換接收者識別碼。 這個屬性是在 AS2 編碼期間從訊息中讀取，用來報告 AS2 的「交換活動」。|  
|ReceiverQualifier|string|來自 EDI 交換的交換接收者辨識符號。 這個屬性是在 AS2 編碼期間從訊息中讀取，用來報告 AS2 的「交換活動」。|  
|SenderID|string|來自 EDI 交換的交換傳送者識別碼。 這個屬性是在 AS2 編碼期間從訊息中讀取，用來報告 AS2 的「交換活動」。|  
|SenderQualifier|string|來自 EDI 交換的交換傳送者辨識符號。 這個屬性是在 AS2 編碼期間從訊息中讀取，用來報告 AS2 的「交換活動」。|  

## <a name="see-also"></a>另請參閱  
 [開發和設定 BizTalk Server AS2 解決方案](../core/developing-and-configuring-biztalk-server-as2-solutions.md)