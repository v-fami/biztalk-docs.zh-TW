---
title: XML 組合器管線元件中的字元編碼 |Microsoft Docs
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
- pipeline components, XML Assembler
- XMLNorm.TargetCharset property
- Target Charset property
- XML Assembler [pipeline component], character encoding
ms.assetid: c031fbbf-f00f-41ba-8ac9-cec7d625cef6
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5d06842eab0def7846ab31419ce2feb0aeb2cd1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000871"
---
# <a name="character-encoding-in-the-xml-assembler-pipeline-component"></a><span data-ttu-id="23869-102">XML 組合器管線元件中的字元編碼</span><span class="sxs-lookup"><span data-stu-id="23869-102">Character Encoding in the XML Assembler Pipeline Component</span></span>
<span data-ttu-id="23869-103">XML 組合器管線元件可以根據使用者指定的字元編碼來產生訊息，下表顯示這兩種方式：</span><span class="sxs-lookup"><span data-stu-id="23869-103">The XML Assembler pipeline component can produce messages in user-specified character encoding in two ways, as shown in the following table.</span></span>  
  
|<span data-ttu-id="23869-104">編碼層級</span><span class="sxs-lookup"><span data-stu-id="23869-104">Encoding level</span></span>|<span data-ttu-id="23869-105">編碼方法</span><span class="sxs-lookup"><span data-stu-id="23869-105">Encoding method</span></span>|  
|--------------------|---------------------|  
|<span data-ttu-id="23869-106">元件</span><span class="sxs-lookup"><span data-stu-id="23869-106">Component</span></span>|<span data-ttu-id="23869-107">設定**目標字元集**管線設計師 」 中的元件屬性。</span><span class="sxs-lookup"><span data-stu-id="23869-107">Set the **Target charset** component property in Pipeline Designer.</span></span>|  
|<span data-ttu-id="23869-108">訊息</span><span class="sxs-lookup"><span data-stu-id="23869-108">Message</span></span>|<span data-ttu-id="23869-109">設定**XMLNorm.TargetCharset**訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="23869-109">Set the **XMLNorm.TargetCharset** property on the message context.</span></span> <span data-ttu-id="23869-110">**注意：** 的訊息內容屬性永遠會覆寫在管線設計師中設定任何內容屬性。</span><span class="sxs-lookup"><span data-stu-id="23869-110">**Note:**  A message context property always overrides any context property set in Pipeline Designer.</span></span>|  
  
 <span data-ttu-id="23869-111">XML 組合器會使用下列演算法來判斷輸出訊息的編碼：</span><span class="sxs-lookup"><span data-stu-id="23869-111">The XML Assembler uses the following algorithm to determine output message encoding:</span></span>  
  
1. <span data-ttu-id="23869-112">如果**XMLNorm.TargetCharset**內容屬性設定，則會使用該值。</span><span class="sxs-lookup"><span data-stu-id="23869-112">If the **XMLNorm.TargetCharset** context property is set, its value is used.</span></span>  
  
2. <span data-ttu-id="23869-113">否則，如果**目標字元集**屬性會指定在管線設計師中，則會使用該值。</span><span class="sxs-lookup"><span data-stu-id="23869-113">Otherwise, if the **Target charset** property is specified in Pipeline Designer, its value is used.</span></span>  
  
3. <span data-ttu-id="23869-114">否則，如果**XMLNorm.SourceCharset**屬性已指定，則會使用該值。</span><span class="sxs-lookup"><span data-stu-id="23869-114">Otherwise, if the **XMLNorm.SourceCharset** property is specified, its value is used.</span></span>  
  
4. <span data-ttu-id="23869-115">若未指定上述屬性，則會使用 UTF-8 編碼。</span><span class="sxs-lookup"><span data-stu-id="23869-115">If none of the preceding properties is set, UTF-8 encoding is used.</span></span>  
  
   <span data-ttu-id="23869-116">XML 組合器會將 BizTalk 訊息物件中編碼資訊儲存`IBaseMessagePart.Charset`屬性。</span><span class="sxs-lookup"><span data-stu-id="23869-116">The XML Assembler saves the encoding information of a BizTalk message object in the `IBaseMessagePart.Charset` property.</span></span> <span data-ttu-id="23869-117">當使用 Unicode 或 UTF-8 編碼時，XML 組合器永遠會將位元順序標記 (byte order mark, BOM) 新增到外寄訊息。</span><span class="sxs-lookup"><span data-stu-id="23869-117">When using Unicode or UTF-8 encoding, the XML Assembler always adds the byte order mark (BOM) to outgoing messages.</span></span>  
  
   <span data-ttu-id="23869-118">請注意，當使用的預設的 XML 傳送管線，其中包含 XML 組合器元件，產生的文件的編碼提交到伺服器，或它們可能已建立的文件使用 utf-8 編碼時，使用做為相同的字元集在伺服器和**XMLNorm.TargetCharset**未指定。</span><span class="sxs-lookup"><span data-stu-id="23869-118">Note that when using the default XML send pipeline, which contains the XML Assembler component, the produced documents may be encoded by using the same charset as when they were submitted into the server, or they may be encoded by using UTF-8 if documents were created within the server and **XMLNorm.TargetCharset** was not specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23869-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23869-119">See Also</span></span>  
 <span data-ttu-id="23869-120">[XML 組合器管線元件](../core/xml-assembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="23869-120">[XML Assembler Pipeline Component](../core/xml-assembler-pipeline-component.md) </span></span>  
 <span data-ttu-id="23869-121">[如何設定 XML 組合器管線元件](../core/how-to-configure-the-xml-assembler-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="23869-121">[How to Configure the XML Assembler Pipeline Component](../core/how-to-configure-the-xml-assembler-pipeline-component.md) </span></span>  
 [<span data-ttu-id="23869-122">Pipelines-AssemblerDisassembler (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="23869-122">Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)</span></span>](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)