---
title: "XML 組合器管線元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML Assembler [pipeline component]
- pipeline components, XML Assembler
ms.assetid: 3adfd603-0577-49c2-ae9d-445d62fed385
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 22348b61ca32567190fa99e103fe536f5199af58
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="xml-assembler-pipeline-component"></a><span data-ttu-id="54820-102">XML 組合器管線元件</span><span class="sxs-lookup"><span data-stu-id="54820-102">XML Assembler Pipeline Component</span></span>
<span data-ttu-id="54820-103">XML 組合器管線元件將 XML 序列化及組合的功能結合成一個元件。</span><span class="sxs-lookup"><span data-stu-id="54820-103">The XML Assembler pipeline component combines XML serializing and assembling in one component.</span></span> <span data-ttu-id="54820-104">其主要功能是將訊息內容的屬性傳回信封和文件。</span><span class="sxs-lookup"><span data-stu-id="54820-104">Its primary function is to transfer properties from the message context back into envelopes and documents.</span></span>  
  
 <span data-ttu-id="54820-105">接收一批訊息之後形成交換時，在 XML 組合器元件中會發生以下動作：</span><span class="sxs-lookup"><span data-stu-id="54820-105">The following actions occur in the XML Assembler component after receiving a batch of messages to form an interchange:</span></span>  
  
1.  <span data-ttu-id="54820-106">組合器使用指定的信封規格建立信封。</span><span class="sxs-lookup"><span data-stu-id="54820-106">The assembler creates the envelope by using the specified envelope specification.</span></span>  
  
2.  <span data-ttu-id="54820-107">元件藉由使用與訊息關聯的 XSD 結構描述中編碼為註解的預先定義 XPath，將內容屬性放置在訊息執行個體上。</span><span class="sxs-lookup"><span data-stu-id="54820-107">The component puts the content properties on the message instances by using the predefined XPaths coded as annotations in the XSD schemas associated with the message.</span></span>  
  
3.  <span data-ttu-id="54820-108">元件將訊息附加到信封。</span><span class="sxs-lookup"><span data-stu-id="54820-108">The component appends the message to the envelope.</span></span>  
  
4.  <span data-ttu-id="54820-109">元件使用與信封關聯的 XSD 結構描述中編碼為註解的預先定義 XPath，將內容屬性放置在信封上。</span><span class="sxs-lookup"><span data-stu-id="54820-109">The component puts the content properties on the envelope by using the predefined XPaths coded as annotations in the XSD schemas associated with envelopes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="54820-110">XML 組合器管線元件不會填入空缺的屬性欄位，不過，當欄位是選擇性但沒有預設或固定值時，則會填入空的項目欄位。</span><span class="sxs-lookup"><span data-stu-id="54820-110">The XML Assembler pipeline component does not populate missing attribute fields, but does populate empty element fields when the fields are optional but do not have default or fixed values.</span></span>  
  
 <span data-ttu-id="54820-111">如需設定 XML 組合器管線元件的資訊，請參閱[如何設定 XML 組合器管線元件](../core/how-to-configure-the-xml-assembler-pipeline-component.md)。</span><span class="sxs-lookup"><span data-stu-id="54820-111">For information about configuring the XML Assembler pipeline component, see [How to Configure the XML Assembler Pipeline Component](../core/how-to-configure-the-xml-assembler-pipeline-component.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="54820-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="54820-112">In This Section</span></span>  
  
-   [<span data-ttu-id="54820-113">XML 組合器管線元件中的字元編碼</span><span class="sxs-lookup"><span data-stu-id="54820-113">Character Encoding in the XML Assembler Pipeline Component</span></span>](../core/character-encoding-in-the-xml-assembler-pipeline-component.md)  
  
-   [<span data-ttu-id="54820-114">XML 組合器管線元件中的處理指示</span><span class="sxs-lookup"><span data-stu-id="54820-114">Processing Instructions in the XML Assembler Pipeline Component</span></span>](../core/processing-instructions-in-the-xml-assembler-pipeline-component.md)  
  
-   [<span data-ttu-id="54820-115">XML 組合器管線元件中無法辨識的訊息</span><span class="sxs-lookup"><span data-stu-id="54820-115">Unrecognized Messages in the XML Assembler Pipeline Component</span></span>](../core/unrecognized-messages-in-the-xml-assembler-pipeline-component.md)  
  
-   [<span data-ttu-id="54820-116">XML 組合器管線元件中的 XML 資訊集項目</span><span class="sxs-lookup"><span data-stu-id="54820-116">XML Information Set Elements in the XML Assembler Pipeline Component</span></span>](../core/xml-information-set-elements-in-the-xml-assembler-pipeline-component.md)  
  
-   [<span data-ttu-id="54820-117">XML 組合器管線元件中的文件結構強化</span><span class="sxs-lookup"><span data-stu-id="54820-117">Document Structure Enforcement in the XML Assembler Pipeline Component</span></span>](../core/document-structure-enforcement-in-the-xml-assembler-pipeline-component.md)