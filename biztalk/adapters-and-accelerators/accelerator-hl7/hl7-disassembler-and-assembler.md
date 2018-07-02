---
title: HL7 反組譯工具和組譯工具 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- assembler, HL7
- disassembler, HL7
ms.assetid: 54e83a04-86c8-482f-bea3-dbbdeb4584d6
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d603e74defeac983b1287f16c7f562b706b8c54d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994991"
---
# <a name="hl7-disassembler-and-assembler"></a><span data-ttu-id="581a9-102">HL7 反組譯工具和組譯工具</span><span class="sxs-lookup"><span data-stu-id="581a9-102">HL7 Disassembler and Assembler</span></span>
<span data-ttu-id="581a9-103">HL7 反組譯工具和組譯工具提供支援 HL7 編碼訊息。</span><span class="sxs-lookup"><span data-stu-id="581a9-103">The HL7 disassembler and assembler provide support for HL7-encoded messages.</span></span> <span data-ttu-id="581a9-104">由於 Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]處理原生 XML 格式，Microsoft BizTalk Accelerator for HL7 的訊息 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 使用 HL7 解譯器和組合器將[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]HL7 整合引擎。</span><span class="sxs-lookup"><span data-stu-id="581a9-104">Since Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] processes messages natively in XML format, Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) uses the HL7 disassembler and assembler to make [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] an HL7 integration engine.</span></span>  
  
## <a name="hl7-disassembler"></a><span data-ttu-id="581a9-105">HL7 反組譯工具</span><span class="sxs-lookup"><span data-stu-id="581a9-105">HL7 Disassembler</span></span>  
 <span data-ttu-id="581a9-106">HL7 反組譯工具將剖析內送 HL7 編碼的訊息處理的 XML 區段。</span><span class="sxs-lookup"><span data-stu-id="581a9-106">The HL7 disassembler parses incoming HL7-encoded messages into XML segments for processing.</span></span> <span data-ttu-id="581a9-107">它會執行驗證的訊息標頭和主體的基本驗證。</span><span class="sxs-lookup"><span data-stu-id="581a9-107">It performs validation of the message header, and basic validation of the body.</span></span> <span data-ttu-id="581a9-108">它會判斷用來剖析 HL7 訊息結構描述 (請參閱[HL7 中的結構描述判斷 2.X 反組譯工具](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-disassembler.md))，判斷訊息的來源合作對象，並會執行額外的驗證主體的 (如果啟用合作對象）。</span><span class="sxs-lookup"><span data-stu-id="581a9-108">It determines the schema that it uses to parse the HL7 message (see [Schema Determination in the HL7 2.X Disassembler](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-disassembler.md)), determines the source party for the message, and performs additional validation of the body (if enabled for the party).</span></span>  
  
## <a name="hl7-assembler"></a><span data-ttu-id="581a9-109">HL7 組譯工具</span><span class="sxs-lookup"><span data-stu-id="581a9-109">HL7 Assembler</span></span>  
 <span data-ttu-id="581a9-110">HL7 組合器會序列化傳出的 HL7 訊息中的 XML 區段。</span><span class="sxs-lookup"><span data-stu-id="581a9-110">The HL7 assembler serializes XML segments into an outgoing HL7 message.</span></span> <span data-ttu-id="581a9-111">它會判斷用來序列化 HL7 訊息結構描述 (請參閱[HL7 中的結構描述判斷 2.X 組譯工具](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-assembler.md))，判斷訊息的目的合作對象，並執行驗證的主體 （如果啟用合作對象）。</span><span class="sxs-lookup"><span data-stu-id="581a9-111">It determines the schema that it uses to serialize the HL7 message (see [Schema Determination in the HL7 2.X Assembler](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-assembler.md)), determines the destination party for the message, and performs validation of the body (if enabled for the party).</span></span>  
  
 <span data-ttu-id="581a9-112">「 組合器 」 可以序列化下列通知 (ACK) 訊息：</span><span class="sxs-lookup"><span data-stu-id="581a9-112">The assembler can serialize the following acknowledgment (ACK) messages:</span></span>  
  
- <span data-ttu-id="581a9-113">靜態</span><span class="sxs-lookup"><span data-stu-id="581a9-113">Static</span></span>  
  
- <span data-ttu-id="581a9-114">原始的模式</span><span class="sxs-lookup"><span data-stu-id="581a9-114">Original mode</span></span>  
  
- <span data-ttu-id="581a9-115">增強的模式</span><span class="sxs-lookup"><span data-stu-id="581a9-115">Enhanced mode</span></span>  
  
  <span data-ttu-id="581a9-116">HL7 組譯工具也能夠將延後的 ACK 訊息路由傳送。</span><span class="sxs-lookup"><span data-stu-id="581a9-116">The HL7 assembler also has the ability to route deferred ACK messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="581a9-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="581a9-117">See Also</span></span>  
 <span data-ttu-id="581a9-118">[BTAHL72X 一般檔案處理](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md) </span><span class="sxs-lookup"><span data-stu-id="581a9-118">[BTAHL72X Flat File Processing](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md) </span></span>  
 [<span data-ttu-id="581a9-119">BizTalk Accelerator for HL7 元件</span><span class="sxs-lookup"><span data-stu-id="581a9-119">BizTalk Accelerator for HL7 Components</span></span>](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md)