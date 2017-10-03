---
title: "XML 訊息的結構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a5bba81-2f2b-41f3-b8b2-c2fb9c15ea5a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f35e48e90ffb089342c268b7b6a45069e2f9869
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="structure-of-an-xml-message"></a><span data-ttu-id="3826b-102">XML 訊息的結構</span><span class="sxs-lookup"><span data-stu-id="3826b-102">Structure of an XML Message</span></span>
<span data-ttu-id="3826b-103">在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境中，XML 執行個體訊息是 XML 標記的有效階層，它們共同組成零或多個 XML 信封，以及一或多個 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="3826b-103">In the context of Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], an XML instance message is a valid hierarchy of XML tags that together constitute zero or more XML envelopes and one or more XML documents.</span></span> <span data-ttu-id="3826b-104">例如，下列 XML 執行個體訊息是由包含單一 XML 文件 (以粗體字顯示) 的單一 XML 信封 (一般字型) 組成。</span><span class="sxs-lookup"><span data-stu-id="3826b-104">For example, the following XML instance message consists of a single XML envelope (in regular font) that contains a single XML document (shown in bold type).</span></span>  
  
```  
<ns0:envelope xmlns:ns0="http://myEnvelopeNamespaceURI.org">  
    <header>  
        <firstName>John</firstName>  
        <lastName>Scott</lastName>  
    </header>  
    <body>  
        <ns1:document xmlns:ns1="http://myDocumentNamespaceURI.org">            <message>Hello</message>        </ns1:document>  
    </body>  
</ns0:envelope>  
```  
  
 <span data-ttu-id="3826b-105">它們包含的 XML 信封和 XML 文件可以使用數種不同方式結合成有效的 XML 執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="3826b-105">XML envelopes and the XML documents that they contain can be combined into valid XML instance messages in several different ways.</span></span> <span data-ttu-id="3826b-106">本節其餘部分敘述這些不同的組合。</span><span class="sxs-lookup"><span data-stu-id="3826b-106">The remainder of this section describes these different combinations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3826b-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="3826b-107">In This Section</span></span>  
  
-   [<span data-ttu-id="3826b-108">XML 訊息信封</span><span class="sxs-lookup"><span data-stu-id="3826b-108">XML Message Envelopes</span></span>](../core/xml-message-envelopes.md)  
  
-   [<span data-ttu-id="3826b-109">巢狀的 XML 訊息信封</span><span class="sxs-lookup"><span data-stu-id="3826b-109">Nested XML Message Envelopes</span></span>](../core/nested-xml-message-envelopes.md)