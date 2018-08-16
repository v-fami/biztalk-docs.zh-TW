---
title: 使用具有 SOAP 標頭的 Web 服務 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SOAP headers, consuming
- Web services, consuming
- Web services, SOAP headers
- SOAP headers, Web services
ms.assetid: c2dfe7d8-e2f0-4bc6-b79c-354d06a7ffd6
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45a3efa628e435092505fdc3884704baa15be34c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22237806"
---
# <a name="consuming-web-services-with-soap-headers"></a>使用具有 SOAP 標頭的 Web 服務
在您使用具有已定義之 SOAP 標頭的 Web 服務之後，這些標頭會變成協調流程和管線元件可以使用的內容屬性。 這些內容屬性包含 SOAP 標頭的字串表示法。 對於 Web 服務中每個已定義的 SOAP 標頭，您可以使用對應至 SOAP 標頭根項目的名稱，建立內容屬性。 所有已定義的 SOAP 標頭內容屬性位於**http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**命名空間。  
  
 下列範例示範如何建立 SOAP 標頭內容屬性**OrigDest**使用中的 SOAP 標頭範例[與取用 Web 服務的 SOAP 標頭](../core/soap-headers-with-consumed-web-services.md):  
  
```  
<?xml version="1.0" encoding="utf-16"?>  
<OrigDest xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns=" http://SOAPHeaderWS.ItemAvailability">  
   <Origination xmlns="">Home</Origination>  
      <Destination xmlns="">Work</Destination>  
</OrigDest>  
```  
  
 回應 SOAP 標頭也包含已定義之 SOAP 標頭的字串表示法。 其值與建立要求 SOAP 標頭類似。  
  
## <a name="see-also"></a>另請參閱  
 [SOAP 標頭與已使用的 Web 服務](../core/soap-headers-with-consumed-web-services.md)