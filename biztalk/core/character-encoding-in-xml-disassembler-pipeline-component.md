---
title: XML 解譯器管線元件中的字元編碼 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IBaseMessagePart.Charset property
- pipeline components, XML Disassembler
- XML Disassembler [pipeline component], character encoding
- XMLNorm.SourceCharset property
ms.assetid: 37962bdc-cbcb-4559-9ae8-6c4be49b4822
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b0e307f2f608cde266e7a566fb3005bde048c31
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231662"
---
# <a name="character-encoding-in-xml-disassembler-pipeline-component"></a><span data-ttu-id="5532e-102">XML 解譯器管線元件中的字元編碼</span><span class="sxs-lookup"><span data-stu-id="5532e-102">Character Encoding in XML Disassembler Pipeline Component</span></span>
<span data-ttu-id="5532e-103">XML 解譯器使用以下演算法以判斷使用哪種編碼處理內送訊息：</span><span class="sxs-lookup"><span data-stu-id="5532e-103">The XML Disassembler uses the following algorithm to determine which encoding to use for processing incoming messages:</span></span>  
  
1.  <span data-ttu-id="5532e-104">若資料中有位元順序標記，則會依此標記判斷編碼資訊。</span><span class="sxs-lookup"><span data-stu-id="5532e-104">If a byte order mark exists in the data, encoding information is determined from it.</span></span>  
  
2.  <span data-ttu-id="5532e-105">否則，如果**IBaseMessagePart.Charset**屬性設定，會那里指定的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="5532e-105">Otherwise, if the **IBaseMessagePart.Charset** property is set, the encoding specified there is used.</span></span>  
  
3.  <span data-ttu-id="5532e-106">或者，若 XML 文件中具有 XML 宣告，且 XML 宣告為 ANSI，則會使用其中指定的編碼。</span><span class="sxs-lookup"><span data-stu-id="5532e-106">Otherwise if the XML declaration is present in the XML document, the encoding specified there is used, provided the XML declaration is ANSI.</span></span>  
  
4.  <span data-ttu-id="5532e-107">或者，使用 UTF-8 編碼。</span><span class="sxs-lookup"><span data-stu-id="5532e-107">Otherwise, UTF-8 encoding is used.</span></span>  
  
 <span data-ttu-id="5532e-108">上述情況 2、 3 和 4，XML 解譯器判定編碼之後，它將它儲存在訊息內容中**XMLNorm.SourceCharset**屬性。</span><span class="sxs-lookup"><span data-stu-id="5532e-108">For the preceding cases 2, 3, and 4, after the XML Disassembler determines the encoding, it saves it on the message context in **XMLNorm.SourceCharset** property.</span></span> <span data-ttu-id="5532e-109">XML 解譯器管線元件所產生的訊息永遠使用 UTF-8 編碼。</span><span class="sxs-lookup"><span data-stu-id="5532e-109">Messages produced by the XML Disassembler pipeline component always use UTF-8 encoding.</span></span> <span data-ttu-id="5532e-110">對於情況 1，依位元順序標記判斷的編碼不會保留。</span><span class="sxs-lookup"><span data-stu-id="5532e-110">For case 1, encoding determined from the byte order mark is not preserved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5532e-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5532e-111">See Also</span></span>  
 <span data-ttu-id="5532e-112">[XML 解譯器管線元件](../core/xml-disassembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="5532e-112">[XML Disassembler Pipeline Component](../core/xml-disassembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="5532e-113">如何設定 XML 解譯器管線元件</span><span class="sxs-lookup"><span data-stu-id="5532e-113">How to Configure the XML Disassembler Pipeline Component</span></span>](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)