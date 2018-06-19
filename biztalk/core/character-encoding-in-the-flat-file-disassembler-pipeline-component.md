---
title: 一般檔案解譯器管線元件中的字元編碼 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IBaseMessagePart.Charset property
- XMLNorm.SourceCharset property
- pipeline components, Flat File Disassembler
- Flat File Disassembler [pipeline component], character encoding
ms.assetid: 0dbe24fb-c431-4edf-8aa9-4c040d6a7b32
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 839a3377f27417757e394c946fe96acc83752355
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231638"
---
# <a name="character-encoding-in-the-flat-file-disassembler-pipeline-component"></a><span data-ttu-id="90bbf-102">一般檔案解譯器管線元件中的字元編碼</span><span class="sxs-lookup"><span data-stu-id="90bbf-102">Character Encoding in the Flat File Disassembler Pipeline Component</span></span>
<span data-ttu-id="90bbf-103">一般檔案解譯器元件會使用下列演算法判斷處理內送訊息時要使用哪一種編碼：</span><span class="sxs-lookup"><span data-stu-id="90bbf-103">The following algorithm is used by the Flat File Disassembler component to determine which encoding to use for processing an incoming message:</span></span>  
  
1.  <span data-ttu-id="90bbf-104">若資料中有位元順序標記，則會依此標記判斷編碼資訊。</span><span class="sxs-lookup"><span data-stu-id="90bbf-104">If a byte order mark exists in the data, encoding information is determined from it.</span></span> <span data-ttu-id="90bbf-105">此編碼資訊不會保留反組譯工具 (亦即，不會儲存至**XMLNorm.SourceCharset**屬性)。</span><span class="sxs-lookup"><span data-stu-id="90bbf-105">This encoding information is not preserved by the disassembler (that is, it is not saved to the **XMLNorm.SourceCharset** property).</span></span>  
  
2.  <span data-ttu-id="90bbf-106">否則，如果**IBaseMessagePart.Charset**屬性設定，會那里指定的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="90bbf-106">Otherwise, if the **IBaseMessagePart.Charset** property is set, the encoding specified there is used.</span></span>  
  
3.  <span data-ttu-id="90bbf-107">或者，若標頭或文件結構描述包含字碼頁資訊，則會使用它。</span><span class="sxs-lookup"><span data-stu-id="90bbf-107">Otherwise, if the header or document schema contains codepage information, it is used.</span></span>  
  
4.  <span data-ttu-id="90bbf-108">或者，使用 UTF-8 編碼。</span><span class="sxs-lookup"><span data-stu-id="90bbf-108">Otherwise, UTF-8 encoding is used.</span></span>  
  
 <span data-ttu-id="90bbf-109">上述情況 2、 3 和 4，解譯器會將編碼資訊儲存在訊息內容中**XMLNorm.SourceCharset**屬性。</span><span class="sxs-lookup"><span data-stu-id="90bbf-109">For the preceding cases 2, 3, and 4, the disassembler saves the encoding information on the message context in the **XMLNorm.SourceCharset** property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90bbf-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90bbf-110">See Also</span></span>  
 <span data-ttu-id="90bbf-111">[一般檔案解譯器管線元件](../core/flat-file-disassembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="90bbf-111">[Flat File Disassembler Pipeline Component](../core/flat-file-disassembler-pipeline-component.md) </span></span>  
 <span data-ttu-id="90bbf-112">[如何設定一般檔案解譯器管線元件](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="90bbf-112">[How to Configure the Flat File Disassembler Pipeline Component](../core/how-to-configure-the-flat-file-disassembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="90bbf-113">管線 AssemblerDisassembler （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="90bbf-113">Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)</span></span>](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)