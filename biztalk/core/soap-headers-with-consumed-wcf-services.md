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
ms.sourcegitcommit: e172dedfd00d4de3a40c8289f3a97ef65cdadd3c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2018
ms.locfileid: "22277486"
---
# <a name="soap-headers-with-consumed-wcf-services"></a><span data-ttu-id="21f00-102">SOAP 標頭與使用 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="21f00-102">SOAP Headers with Consumed WCF Services</span></span>
<span data-ttu-id="21f00-103">若要傳送訊息至 WCF 服務使用自訂 SOAP 標頭，這些標頭必須設定 （在 「 運算式 」 圖形，例如） 的協調流程和管線元件 （在程式碼） 中為內容屬性**OutboundCustomHeaders**。</span><span class="sxs-lookup"><span data-stu-id="21f00-103">To send a message to a WCF service with the custom SOAP headers, these headers must be set in your orchestrations (in the Expression shape, for example) and pipeline components (in code) as the context property **OutboundCustomHeaders**.</span></span> <span data-ttu-id="21f00-104">此內容屬性位於目標命名空間**http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties**，並包含自訂 SOAP 標頭的字串表示法。</span><span class="sxs-lookup"><span data-stu-id="21f00-104">This context property is in the target namespace **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties**, and contains string representations of the custom SOAP headers.</span></span>  
  
 <span data-ttu-id="21f00-105">下列 XML 外寄訊息中的資料顯示的自訂 SOAP 標頭的字串表示法範例**OutboundCustomHeaders**屬性：</span><span class="sxs-lookup"><span data-stu-id="21f00-105">The data in the following XML outgoing message shows an example of the string representation of custom SOAP headers for the **OutboundCustomHeaders** property:</span></span>  
  
```  
<headers>  
<Origination xmlns="http://SOAPHeaderSchemas.OrigDestSOAPHeader">Home</Origination>  
<Destination xmlns="http://SOAPHeaderSchemas.OrigDestSOAPHeader">Work</Destination>  
</headers>  
```  
  
 <span data-ttu-id="21f00-106">輸入的 SOAP 標頭也包含 SOAP 標頭的字串表示法。</span><span class="sxs-lookup"><span data-stu-id="21f00-106">Inbound SOAP headers also contain string representations of the SOAP headers.</span></span> <span data-ttu-id="21f00-107">其值與建立要求 SOAP 標頭類似。</span><span class="sxs-lookup"><span data-stu-id="21f00-107">The values are similar to creating a request SOAP header.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="21f00-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="21f00-108">In This Section</span></span>  
  
-   [<span data-ttu-id="21f00-109">WCF 訊息與協調流程中使用 SOAP 標頭</span><span class="sxs-lookup"><span data-stu-id="21f00-109">Using SOAP Headers in WCF Messages with Orchestrations</span></span>](../core/using-soap-headers-in-wcf-messages-with-orchestrations.md)  
  
-   [<span data-ttu-id="21f00-110">WCF 訊息的管線元件中使用 SOAP 標頭</span><span class="sxs-lookup"><span data-stu-id="21f00-110">Using SOAP Headers in WCF Messages with Pipeline Components</span></span>](../core/using-soap-headers-in-wcf-messages-with-pipeline-components.md)  
  
## <a name="see-also"></a><span data-ttu-id="21f00-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21f00-111">See Also</span></span>  
 <span data-ttu-id="21f00-112">[WCF 配接器屬性結構描述和屬性](../core/wcf-adapters-property-schema-and-properties.md) </span><span class="sxs-lookup"><span data-stu-id="21f00-112">[WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md) </span></span>  
 [<span data-ttu-id="21f00-113">SOAP 標頭與已發佈的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="21f00-113">SOAP Headers with Published WCF Services</span></span>](../core/soap-headers-with-published-wcf-services.md)