---
title: "XML 訊息信封 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d01cd85d-7bf7-49fa-aa25-322213bce066
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3adb33866a3e6fdaee387934d2edededaab08aac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="xml-message-envelopes"></a><span data-ttu-id="54858-102">XML 訊息信封</span><span class="sxs-lookup"><span data-stu-id="54858-102">XML Message Envelopes</span></span>
<span data-ttu-id="54858-103">XML 信封在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所傳送和接收的 XML 執行個體訊息中有兩個目的：</span><span class="sxs-lookup"><span data-stu-id="54858-103">XML envelopes serve two purposes within XML instance messages sent and received by Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="54858-104">XML 信封可以包含補充 XML 文件內資料的資料。</span><span class="sxs-lookup"><span data-stu-id="54858-104">XML envelopes can contain data that supplements the data within the XML documents.</span></span> <span data-ttu-id="54858-105">XML 解譯器可將此資料升級至訊息內容，以提供更容易從各種 BizTalk Server 元件存取的能力。</span><span class="sxs-lookup"><span data-stu-id="54858-105">This data can be promoted into the message context by the XML disassembler to provide easier access from a variety of BizTalk Server components.</span></span> <span data-ttu-id="54858-106">就輸出 XML 執行個體訊息而言，XML 組合器可以將值從訊息內容降級至信封，以供其包含在執行個體訊息傳輸中。</span><span class="sxs-lookup"><span data-stu-id="54858-106">For outbound XML instance messages, the XML assembler can demote values from the message context into an envelope for inclusion in the instance message transmission.</span></span>  
  
-   <span data-ttu-id="54858-107">XML 信封可用來結合多個 XML 文件為單一、有效的 XML 執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="54858-107">XML envelopes can be used to combine multiple XML documents into a single, valid XML instance message.</span></span> <span data-ttu-id="54858-108">若沒有信封包裝單一根標記中的多個文件，則包含多個文件的 XML 執行個體訊息將不符合格式正確的 XML。</span><span class="sxs-lookup"><span data-stu-id="54858-108">Without an envelope to wrap multiple documents within a single root tag, an XML instance message containing multiple documents would not qualify as well-formed XML.</span></span>  
  
 <span data-ttu-id="54858-109">一般的 XML 信封 (以粗體顯示) 包含資料以及用來分隔一或多個它所包含的 XML 文件 (以一般字型顯示) 之標記。</span><span class="sxs-lookup"><span data-stu-id="54858-109">A typical XML envelope (shown in bold type) contains both data and a tag used to delimit the one or more XML documents (shown in regular font) that it contains.</span></span>  
  
```  
  
  <envelope fieldAttrib1="..." fieldAttrib2="..." ...>     <fieldElem1>...</fieldElem1>     <fieldElem2>...</fieldElem2>     ...     <body>  
    <document1>  
        ...  
    </document1>  
    <document2>  
        ...  
    </document2>  
    ...  
</body>    ...</envelope>  
```  
  
 <span data-ttu-id="54858-110">另一種較少見但仍為有效的 XML 信封 (以粗體顯示) 則不需包含任何資料或是用來分隔它所包含的 XML 文件 (以一般字型顯示) 之標記。</span><span class="sxs-lookup"><span data-stu-id="54858-110">Less common, but still valid, an XML envelope (shown in bold type) need not contain any data or a tag for delimiting the XML documents (shown in regular type) that it contains.</span></span>  
  
```  
  
      <envelope>  
    <document1>  
        ...  
    </document1>  
    <document2>  
        ...  
    </document2>  
    ...  
</envelope>  
```  
  
 <span data-ttu-id="54858-111">在此情況下，XML 信封僅包含開始和結束的信封標記。</span><span class="sxs-lookup"><span data-stu-id="54858-111">In such cases, the XML envelope consists of nothing other than the starting and ending envelope tags.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54858-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54858-112">See Also</span></span>  
 <span data-ttu-id="54858-113">[巢狀的 XML 訊息信封](../core/nested-xml-message-envelopes.md) </span><span class="sxs-lookup"><span data-stu-id="54858-113">[Nested XML Message Envelopes](../core/nested-xml-message-envelopes.md) </span></span>  
 <span data-ttu-id="54858-114">[XML 訊息的結構](../core/structure-of-an-xml-message.md) </span><span class="sxs-lookup"><span data-stu-id="54858-114">[Structure of an XML Message](../core/structure-of-an-xml-message.md) </span></span>  
 [<span data-ttu-id="54858-115">如何建立信封的結構描述</span><span class="sxs-lookup"><span data-stu-id="54858-115">How to Create Schemas for Envelopes</span></span>](../core/how-to-create-schemas-for-envelopes.md)