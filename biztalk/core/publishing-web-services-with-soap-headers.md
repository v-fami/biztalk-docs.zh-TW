---
title: 發佈具有 SOAP 標頭的 Web 服務 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SOAP headers, orchestrations
- SOAP headers, code samples
- SOAP headers, pipelines
- SOAP headers, BizTalk Web Services Publishing Wizard
- pipelines, SOAP headers
- orchestrations, SOAP headers
ms.assetid: c362caff-b75f-4c1b-9013-d2b9c74f5c65
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7baf6af0e4505e448a854fe6def372614bfdaa49
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269022"
---
# <a name="publishing-web-services-with-soap-headers"></a>發佈具有 SOAP 標頭的 Web 服務
當您執行「BizTalk Web 服務發佈精靈」時，可以將 SOAP 標頭加入至 Web 服務。 當您發佈可支援 SOAP 標頭的 Web 服務時，標頭會變成包含 SOAP 標頭字串表示的內容屬性，提供給協調流程和管線元件使用。  
  
## <a name="defined-soap-headers"></a>已定義的 SOAP 標頭  
 當您使用精靈加入已定義的 SOAP 標頭時，精靈會使用對應至 SOAP 標頭之根項目的名稱，建立內容屬性。 所有已定義的 SOAP 標頭內容屬性具有命名空間**http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**。 當 SOAP 配接器將 SOAP 要求轉換為 BizTalk 訊息時，它會建立一個 SOAP 標頭內容屬性。  
  
 下列範例示範簡單的 SOAP 要求：  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
       <soap:Header>  
             <OrigDest xmlns="http://SOAPHeaderWS.ItemAvailability">  
                    <Origination>Work</Origination>  
                    <Destination>Home</Destination>  
             </OrigDest>  
       </soap:Header>  
       <soap:Body>  
  
       </soap:Body>  
</soap:Envelope>  
```  
  
 對於簡單的 SOAP 要求，SOAP 配接器建立 BizTalk 訊息一個 SOAP 標頭內容屬性**OrigDest**和字串。  
  
 下列範例會顯示 SOAP 配接器建立的字串：  
  
```  
"<?xml version="1.0" encoding="utf-16"?><OrigDest xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://SOAPHeaderSchemas.OrigDestSOAPHeader"><Origination xmlns="">Home</Origination><Destination xmlns="">Work</Destination> </OrigDest>"  
```  
  
## <a name="unknown-soap-headers"></a>未知的 SOAP 標頭  
 如果您選擇支援未知的 SOAP 標頭，在精靈中，精靈會建立內容屬性名稱**UnknownHeaders**和命名空間**http://schemas.microsoft.com/BizTalk/2003/soap-properties**. **UnknownHeaders**內容屬性包含所有已接收的未知 SOAP 標頭。  
  
 例如，如果您收到未知的 SOAP 標頭的根元素名稱，與**CustomerGroup**、 **UnknownHeaders**內容屬性包含字串：  
  
```  
"<?xml version="1.0" encoding="utf-16"?><UnknownHeaders><CustomerGroup xmlns="http://SOAPHeaderWS/CustomerGroup"><Id xmlns="">My Customer</Id>  
</CustomerGroup></UnknownHeaders>"  
```  
  
 如需有關加入已定義 SOAP 標頭或支援未知的 SOAP 標頭，請參閱[協調流程發佈為 Web 服務](../core/publishing-an-orchestration-as-a-web-service.md)。 另請參閱[發佈為 Web 服務的結構描述](../core/publishing-schemas-as-a-web-service.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SOAP 標頭與已發佈的 Web 服務](../core/soap-headers-with-published-web-services.md)