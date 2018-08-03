---
title: 與使用的 WCF 服務的 SOAP 標頭 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- consuming, WCF services
- SOAP headers, WCF services
- consuming, SOAP headers
- WCF services, SOAP headers
- SOAP headers, consuming [WCF services]
ms.assetid: 0582ee26-b549-4b50-b365-36824010dab0
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f60e0ae7f9cf2e6a224ce9d919c7c4d5e6f3119c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277486"
---
# <a name="soap-headers-with-consumed-wcf-services"></a>SOAP 標頭與使用 WCF 服務
若要傳送訊息至 WCF 服務使用自訂 SOAP 標頭，這些標頭必須設定 （在 「 運算式 」 圖形，例如） 的協調流程和管線元件 （在程式碼） 中為內容屬性**OutboundCustomHeaders**。 這個內容屬性位於目標命名空間**http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties**，並包含自訂 SOAP 標頭的字串表示法。  
  
 下列 XML 外寄訊息中的資料顯示的自訂 SOAP 標頭的字串表示法範例**OutboundCustomHeaders**屬性：  
  
```  
<headers>  
<Origination xmlns="http://SOAPHeaderSchemas.OrigDestSOAPHeader">Home</Origination>  
<Destination xmlns="http://SOAPHeaderSchemas.OrigDestSOAPHeader">Work</Destination>  
</headers>  
```  
  
 輸入的 SOAP 標頭也包含 SOAP 標頭的字串表示法。 其值與建立要求 SOAP 標頭類似。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [WCF 訊息與協調流程中使用 SOAP 標頭](../core/using-soap-headers-in-wcf-messages-with-orchestrations.md)  
  
-   [WCF 訊息的管線元件中使用 SOAP 標頭](../core/using-soap-headers-in-wcf-messages-with-pipeline-components.md)  
  
## <a name="see-also"></a>另請參閱  
 [WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md)   
 [SOAP 標頭與已發佈的 WCF 服務](../core/soap-headers-with-published-wcf-services.md)