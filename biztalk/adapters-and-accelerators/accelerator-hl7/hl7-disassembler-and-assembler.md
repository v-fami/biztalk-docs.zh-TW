---
title: "HL7 解譯器和組合器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assembler, HL7
- disassembler, HL7
ms.assetid: 54e83a04-86c8-482f-bea3-dbbdeb4584d6
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e81d621656fc678196f7f6fb709b29de87a3aaf9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="hl7-disassembler-and-assembler"></a><span data-ttu-id="8e71a-102">HL7 解譯器和組合器</span><span class="sxs-lookup"><span data-stu-id="8e71a-102">HL7 Disassembler and Assembler</span></span>
<span data-ttu-id="8e71a-103">HL7 解譯器和組合器支援 HL7 編碼訊息。</span><span class="sxs-lookup"><span data-stu-id="8e71a-103">The HL7 disassembler and assembler provide support for HL7-encoded messages.</span></span> <span data-ttu-id="8e71a-104">因為[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]處理 XML 格式中的原生訊息[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 使用 HL7 解譯器和組合器將[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]HL7 integration 引擎。</span><span class="sxs-lookup"><span data-stu-id="8e71a-104">Since [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] processes messages natively in XML format, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) uses the HL7 disassembler and assembler to make [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] an HL7 integration engine.</span></span>  
  
## <a name="hl7-disassembler"></a><span data-ttu-id="8e71a-105">HL7 反組譯工具</span><span class="sxs-lookup"><span data-stu-id="8e71a-105">HL7 Disassembler</span></span>  
 <span data-ttu-id="8e71a-106">HL7 解譯器會將傳入 HL7 編碼訊息剖析為處理的 XML 區段。</span><span class="sxs-lookup"><span data-stu-id="8e71a-106">The HL7 disassembler parses incoming HL7-encoded messages into XML segments for processing.</span></span> <span data-ttu-id="8e71a-107">它會執行驗證的訊息標頭和主體的基本驗證。</span><span class="sxs-lookup"><span data-stu-id="8e71a-107">It performs validation of the message header, and basic validation of the body.</span></span> <span data-ttu-id="8e71a-108">它會判斷它會使用來剖析 HL7 訊息結構描述 (請參閱[中 HL7 結構描述判斷 2.X 解譯器](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-disassembler.md))，判斷訊息的來源合作對象，並執行其他主體的驗證 (如果啟用合作對象）。</span><span class="sxs-lookup"><span data-stu-id="8e71a-108">It determines the schema that it uses to parse the HL7 message (see [Schema Determination in the HL7 2.X Disassembler](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-disassembler.md)), determines the source party for the message, and performs additional validation of the body (if enabled for the party).</span></span>  
  
## <a name="hl7-assembler"></a><span data-ttu-id="8e71a-109">HL7 組譯工具</span><span class="sxs-lookup"><span data-stu-id="8e71a-109">HL7 Assembler</span></span>  
 <span data-ttu-id="8e71a-110">HL7 組合器序列化傳出的 HL7 訊息的 XML 區段。</span><span class="sxs-lookup"><span data-stu-id="8e71a-110">The HL7 assembler serializes XML segments into an outgoing HL7 message.</span></span> <span data-ttu-id="8e71a-111">它會判斷它用來序列化 HL7 訊息結構描述 (請參閱[中 HL7 結構描述判斷 2.X 組譯工具](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-assembler.md))，判斷訊息的目的合作對象，並執行驗證的主體，（如果啟用合作對象）。</span><span class="sxs-lookup"><span data-stu-id="8e71a-111">It determines the schema that it uses to serialize the HL7 message (see [Schema Determination in the HL7 2.X Assembler](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-assembler.md)), determines the destination party for the message, and performs validation of the body (if enabled for the party).</span></span>  
  
 <span data-ttu-id="8e71a-112">組譯工具可以序列化下列通知 (ACK) 訊息：</span><span class="sxs-lookup"><span data-stu-id="8e71a-112">The assembler can serialize the following acknowledgment (ACK) messages:</span></span>  
  
-   <span data-ttu-id="8e71a-113">靜態</span><span class="sxs-lookup"><span data-stu-id="8e71a-113">Static</span></span>  
  
-   <span data-ttu-id="8e71a-114">原始模式</span><span class="sxs-lookup"><span data-stu-id="8e71a-114">Original mode</span></span>  
  
-   <span data-ttu-id="8e71a-115">增強的模式</span><span class="sxs-lookup"><span data-stu-id="8e71a-115">Enhanced mode</span></span>  
  
 <span data-ttu-id="8e71a-116">HL7 組譯工具也能夠將延後的 ACK 訊息路由傳送。</span><span class="sxs-lookup"><span data-stu-id="8e71a-116">The HL7 assembler also has the ability to route deferred ACK messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e71a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e71a-117">See Also</span></span>  
 <span data-ttu-id="8e71a-118">[BTAHL72X 一般檔案處理](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md) </span><span class="sxs-lookup"><span data-stu-id="8e71a-118">[BTAHL72X Flat File Processing](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md) </span></span>  
 [<span data-ttu-id="8e71a-119">BizTalk Accelerator for HL7 元件</span><span class="sxs-lookup"><span data-stu-id="8e71a-119">BizTalk Accelerator for HL7 Components</span></span>](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md)