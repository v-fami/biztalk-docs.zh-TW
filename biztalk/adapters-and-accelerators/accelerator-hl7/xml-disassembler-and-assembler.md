---
title: "XML 解譯器和組合器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disassembler, XML
- assembler, XML
ms.assetid: 242a7a96-2342-4ab5-9d3f-1acbcc7ffd14
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4978484f888290377986ee4ae8bf049c14a1b31
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="xml-disassembler-and-assembler"></a><span data-ttu-id="28315-102">XML 解譯器和組合器</span><span class="sxs-lookup"><span data-stu-id="28315-102">XML Disassembler and Assembler</span></span>
<span data-ttu-id="28315-103">XML 解譯器和組合器確定[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 不只支援 HL7 編碼訊息，但是也支援傳入和/或傳出 XML 訊息。</span><span class="sxs-lookup"><span data-stu-id="28315-103">The XML disassembler and assembler ensure that [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) not only supports HL7-encoded messages, but also supports incoming and/or outgoing XML messages.</span></span>  
  
## <a name="xml-disassembler"></a><span data-ttu-id="28315-104">XML 解譯器</span><span class="sxs-lookup"><span data-stu-id="28315-104">XML Disassembler</span></span>  
 <span data-ttu-id="28315-105">XML 解譯器會將內送 XML 訊息剖析為 XML 區段進行處理。</span><span class="sxs-lookup"><span data-stu-id="28315-105">The XML disassembler parses incoming XML messages into XML segments for processing.</span></span> <span data-ttu-id="28315-106">因為它會剖析訊息，解譯器會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="28315-106">As it parses the messages, the disassembler performs the following tasks:</span></span>  
  
-   <span data-ttu-id="28315-107">控制代碼逸出序列</span><span class="sxs-lookup"><span data-stu-id="28315-107">Handles escape sequences</span></span>  
  
-   <span data-ttu-id="28315-108">處理必要/選用的屬性的檢查</span><span class="sxs-lookup"><span data-stu-id="28315-108">Handles checks of required/optional properties</span></span>  
  
-   <span data-ttu-id="28315-109">控制代碼宣告 Z 區段</span><span class="sxs-lookup"><span data-stu-id="28315-109">Handles declared Z segments</span></span>  
  
 <span data-ttu-id="28315-110">因為它會剖析訊息，解譯器會執行下列：</span><span class="sxs-lookup"><span data-stu-id="28315-110">As it parses the messages, the dissassembler performs the following:</span></span>  
  
-   <span data-ttu-id="28315-111">語法驗證</span><span class="sxs-lookup"><span data-stu-id="28315-111">Syntactic validation</span></span>  
  
-   <span data-ttu-id="28315-112">結構描述驗證 （如果啟用）</span><span class="sxs-lookup"><span data-stu-id="28315-112">Schema validation (if enabled)</span></span>  
  
## <a name="xml-assembler"></a><span data-ttu-id="28315-113">XML 組合器</span><span class="sxs-lookup"><span data-stu-id="28315-113">XML Assembler</span></span>  
 <span data-ttu-id="28315-114">XML 組合器序列化傳出 XML 訊息的 XML 區段。</span><span class="sxs-lookup"><span data-stu-id="28315-114">The XML assembler serializes XML segments into an outgoing XML message.</span></span> <span data-ttu-id="28315-115">「 XML 組合器 」 支援，並建立下列通知 (ACK) 訊息：</span><span class="sxs-lookup"><span data-stu-id="28315-115">The XML assembler supports and creates the following acknowledgment (ACK) messages:</span></span>  
  
-   <span data-ttu-id="28315-116">靜態</span><span class="sxs-lookup"><span data-stu-id="28315-116">Static</span></span>  
  
-   <span data-ttu-id="28315-117">原始模式</span><span class="sxs-lookup"><span data-stu-id="28315-117">Original mode</span></span>  
  
-   <span data-ttu-id="28315-118">增強的模式</span><span class="sxs-lookup"><span data-stu-id="28315-118">Enhanced mode</span></span>  
  
 <span data-ttu-id="28315-119">「 XML 組合器 」 也能夠將延後的 ACK 訊息路由傳送。</span><span class="sxs-lookup"><span data-stu-id="28315-119">The XML assembler also has the ability to route deferred ACK messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28315-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28315-120">See Also</span></span>  
 <span data-ttu-id="28315-121">[BTAHL72XML 處理](../../adapters-and-accelerators/accelerator-hl7/btahl72xml-processing.md) </span><span class="sxs-lookup"><span data-stu-id="28315-121">[BTAHL72XML Processing](../../adapters-and-accelerators/accelerator-hl7/btahl72xml-processing.md) </span></span>  
 [<span data-ttu-id="28315-122">BizTalk Accelerator for HL7 元件</span><span class="sxs-lookup"><span data-stu-id="28315-122">BizTalk Accelerator for HL7 Components</span></span>](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md)