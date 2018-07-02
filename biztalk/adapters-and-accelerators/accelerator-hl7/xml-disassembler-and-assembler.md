---
title: XML 解譯器和組合器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- disassembler, XML
- assembler, XML
ms.assetid: 242a7a96-2342-4ab5-9d3f-1acbcc7ffd14
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3d8dfaf91d9b0d3d058c4d3e31cd67c652235eff
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983039"
---
# <a name="xml-disassembler-and-assembler"></a><span data-ttu-id="b841a-102">XML 解譯器和組合器</span><span class="sxs-lookup"><span data-stu-id="b841a-102">XML Disassembler and Assembler</span></span>
<span data-ttu-id="b841a-103">XML 解譯器和組合器確保 Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 不只支援 HL7 編碼訊息，但是也支援傳入和/或傳出 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="b841a-103">The XML disassembler and assembler ensure that Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) not only supports HL7-encoded messages, but also supports incoming and/or outgoing XML messages.</span></span>  
  
## <a name="xml-disassembler"></a><span data-ttu-id="b841a-104">XML 解譯器</span><span class="sxs-lookup"><span data-stu-id="b841a-104">XML Disassembler</span></span>  
 <span data-ttu-id="b841a-105">XML 解譯器會將內送 XML 訊息剖析為 XML 區段進行處理。</span><span class="sxs-lookup"><span data-stu-id="b841a-105">The XML disassembler parses incoming XML messages into XML segments for processing.</span></span> <span data-ttu-id="b841a-106">剖析訊息，解譯器會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="b841a-106">As it parses the messages, the disassembler performs the following tasks:</span></span>  
  
- <span data-ttu-id="b841a-107">控制代碼逸出序列</span><span class="sxs-lookup"><span data-stu-id="b841a-107">Handles escape sequences</span></span>  
  
- <span data-ttu-id="b841a-108">處理必要/選用屬性的檢查</span><span class="sxs-lookup"><span data-stu-id="b841a-108">Handles checks of required/optional properties</span></span>  
  
- <span data-ttu-id="b841a-109">宣告的 Z 區段的控制代碼</span><span class="sxs-lookup"><span data-stu-id="b841a-109">Handles declared Z segments</span></span>  
  
  <span data-ttu-id="b841a-110">剖析訊息，解譯器會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="b841a-110">As it parses the messages, the dissassembler performs the following:</span></span>  
  
- <span data-ttu-id="b841a-111">語法驗證</span><span class="sxs-lookup"><span data-stu-id="b841a-111">Syntactic validation</span></span>  
  
- <span data-ttu-id="b841a-112">結構描述驗證 （如果啟用）</span><span class="sxs-lookup"><span data-stu-id="b841a-112">Schema validation (if enabled)</span></span>  
  
## <a name="xml-assembler"></a><span data-ttu-id="b841a-113">XML 組合器</span><span class="sxs-lookup"><span data-stu-id="b841a-113">XML Assembler</span></span>  
 <span data-ttu-id="b841a-114">XML 組合器會序列化傳出 XML 訊息中的 XML 區段。</span><span class="sxs-lookup"><span data-stu-id="b841a-114">The XML assembler serializes XML segments into an outgoing XML message.</span></span> <span data-ttu-id="b841a-115">「 XML 組合器 」 支援，並建立下列認可 (ACK) 訊息：</span><span class="sxs-lookup"><span data-stu-id="b841a-115">The XML assembler supports and creates the following acknowledgment (ACK) messages:</span></span>  
  
- <span data-ttu-id="b841a-116">靜態</span><span class="sxs-lookup"><span data-stu-id="b841a-116">Static</span></span>  
  
- <span data-ttu-id="b841a-117">原始的模式</span><span class="sxs-lookup"><span data-stu-id="b841a-117">Original mode</span></span>  
  
- <span data-ttu-id="b841a-118">增強的模式</span><span class="sxs-lookup"><span data-stu-id="b841a-118">Enhanced mode</span></span>  
  
  <span data-ttu-id="b841a-119">「 XML 組合器 」 也可將延遲的 ACK 訊息路由傳送。</span><span class="sxs-lookup"><span data-stu-id="b841a-119">The XML assembler also has the ability to route deferred ACK messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b841a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b841a-120">See Also</span></span>  
 <span data-ttu-id="b841a-121">[BTAHL72XML 處理](../../adapters-and-accelerators/accelerator-hl7/btahl72xml-processing.md) </span><span class="sxs-lookup"><span data-stu-id="b841a-121">[BTAHL72XML Processing](../../adapters-and-accelerators/accelerator-hl7/btahl72xml-processing.md) </span></span>  
 [<span data-ttu-id="b841a-122">BizTalk Accelerator for HL7 元件</span><span class="sxs-lookup"><span data-stu-id="b841a-122">BizTalk Accelerator for HL7 Components</span></span>](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md)