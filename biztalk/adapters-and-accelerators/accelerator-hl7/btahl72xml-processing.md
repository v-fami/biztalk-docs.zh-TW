---
title: BTAHL72XML 處理 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 2.XML messages, processing
- acknowledgements, 2.XML messages
- 2.XML messages, message modes
- message modes, 2.XML message
- 2.XML messages
- validating, 2.XML messages
- 2.XML messages, acknowledgements
- 2.XML messages, validating
ms.assetid: 2f12cb44-816c-4773-9db0-9cbc3d1b1aee
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77bf987966e7f52b103c205298d8bf07c1fc1a5e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977287"
---
# <a name="btahl72xml-processing"></a><span data-ttu-id="72e8f-102">BTAHL72XML 處理</span><span class="sxs-lookup"><span data-stu-id="72e8f-102">BTAHL72XML Processing</span></span>
<span data-ttu-id="72e8f-103">在 Microsoft BizTalk Accelerator for HL7 的下列元件 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 處理 HL7 2.xml XML （XML 編碼） 訊息：</span><span class="sxs-lookup"><span data-stu-id="72e8f-103">The following components in Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) process HL7 2.XML (XML-encoded) messages:</span></span>  
  
- <span data-ttu-id="72e8f-104">管線和核心程式庫： [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。PipelineCommon.dll 和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。PipelineMessageCore.dll</span><span class="sxs-lookup"><span data-stu-id="72e8f-104">Pipelines and core libraries: [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].PipelineCommon.dll and [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].PipelineMessageCore.dll</span></span>  
  
- <span data-ttu-id="72e8f-105">組合器和解譯器程式庫： [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。HL72XmlAsm.dll 和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。HL72XmlDAsm.dll</span><span class="sxs-lookup"><span data-stu-id="72e8f-105">Assembler and disassembler libraries: [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].HL72XmlAsm.dll and [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].HL72XmlDAsm.dll</span></span>  
  
- <span data-ttu-id="72e8f-106">通知 (ACK) 的驗證程式庫用於雙向 MLLP 傳送配接器： [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]。HL7ACKHelper.dll</span><span class="sxs-lookup"><span data-stu-id="72e8f-106">The acknowledgment (ACK) validation library used for the two-way MLLP send adapter: [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].HL7ACKHelper.dll</span></span>  
  
## <a name="xml-message-modes"></a><span data-ttu-id="72e8f-107">XML 訊息模式</span><span class="sxs-lookup"><span data-stu-id="72e8f-107">XML Message Modes</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="72e8f-108"> 2.XML 訊息支援下列的訊息模式：</span><span class="sxs-lookup"><span data-stu-id="72e8f-108"> supports the following message modes for 2.XML messages:</span></span>  
  
- <span data-ttu-id="72e8f-109">發行者-訂閱 (pub sub) 模式</span><span class="sxs-lookup"><span data-stu-id="72e8f-109">Publisher-subscriber (pub-sub) mode</span></span>  
  
   <span data-ttu-id="72e8f-110">發行者會廣播至合作對象的 「 訂閱者 」 為宣告式或來路不明的更新。</span><span class="sxs-lookup"><span data-stu-id="72e8f-110">The publisher broadcasts to a party of subscribers, either as declarative or an unsolicited update.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="72e8f-111"> 和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]提供彈性，此模式中，因為您可以在設計階段之後管理訂用帳戶和合作對象。</span><span class="sxs-lookup"><span data-stu-id="72e8f-111"> and [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] provide flexibility to this mode, since you can manage subscriptions and parties after design time.</span></span>  
  
- <span data-ttu-id="72e8f-112">要求-回應模式</span><span class="sxs-lookup"><span data-stu-id="72e8f-112">Request-response mode</span></span>  
  
   <span data-ttu-id="72e8f-113">來自特定實體的特定要求回應訊息中產生 interrogative 或查詢訊息交換。</span><span class="sxs-lookup"><span data-stu-id="72e8f-113">An interrogative or query message exchange in which a specific request from a specific entity results in a responding message.</span></span>  
  
## <a name="xml-validation"></a><span data-ttu-id="72e8f-114">XML 驗證</span><span class="sxs-lookup"><span data-stu-id="72e8f-114">XML Validation</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="72e8f-115"> 提供下列的驗證 2.XML 訊息：</span><span class="sxs-lookup"><span data-stu-id="72e8f-115"> provides the following validation of 2.XML messages:</span></span>  
  
- <span data-ttu-id="72e8f-116">XML 讀取器</span><span class="sxs-lookup"><span data-stu-id="72e8f-116">XML reader</span></span>  
  
- <span data-ttu-id="72e8f-117">圖解</span><span class="sxs-lookup"><span data-stu-id="72e8f-117">Schematic</span></span>  
  
   <span data-ttu-id="72e8f-118">您可以啟用或停用圖解驗證合作對象。</span><span class="sxs-lookup"><span data-stu-id="72e8f-118">You enable or disable schematic validation by the party.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="72e8f-119"> 由 MSH9.3 訊息結構標頭欄位和 MSH12 版本識別碼欄位 （2.3.1、 2.4、 2.5） 會針對這項處理，直接使用 HL7 2.xml 結構描述。</span><span class="sxs-lookup"><span data-stu-id="72e8f-119"> uses the HL7 2.XML schemas directly for this processing, as determined by the MSH9.3 message-structure header field and the MSH12 Version ID field (2.3.1, 2.4, or 2.5).</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="72e8f-120"> 使用標準的 XML 處理功能，在[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="72e8f-120"> uses the standard XML processing capabilities in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
- <span data-ttu-id="72e8f-121">Z 區段</span><span class="sxs-lookup"><span data-stu-id="72e8f-121">Z segment</span></span>  
  
   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="72e8f-122"> 驗證未宣告的 Z 區段中，包含任何宣告的區段。</span><span class="sxs-lookup"><span data-stu-id="72e8f-122"> validates that no declared segments are included in an undeclared Z segment.</span></span>  
  
## <a name="ack-generation"></a><span data-ttu-id="72e8f-123">通知的產生</span><span class="sxs-lookup"><span data-stu-id="72e8f-123">ACK Generation</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="72e8f-124"> 2.XML 訊息支援下列類型的通知 (Ack)。</span><span class="sxs-lookup"><span data-stu-id="72e8f-124"> supports the following types of acknowledgments (ACKs) for 2.XML messages.</span></span> <span data-ttu-id="72e8f-125">HL7 錯誤類型和[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]（替代） 的錯誤類型使用：</span><span class="sxs-lookup"><span data-stu-id="72e8f-125">Both the HL7 error type and the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] (alternate) error type are used:</span></span>  
  
-   <span data-ttu-id="72e8f-126">HL7 原始通知</span><span class="sxs-lookup"><span data-stu-id="72e8f-126">HL7 original ACKs</span></span>  
  
-   <span data-ttu-id="72e8f-127">HL7 增強 Ack</span><span class="sxs-lookup"><span data-stu-id="72e8f-127">HL7 enhanced ACKs</span></span>  
  
     <span data-ttu-id="72e8f-128">認可接受並接受應用程式</span><span class="sxs-lookup"><span data-stu-id="72e8f-128">Commit Accept and Application Accept</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72e8f-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72e8f-129">See Also</span></span>  
 <span data-ttu-id="72e8f-130">[訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="72e8f-130">[Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span></span>  
 [<span data-ttu-id="72e8f-131">使用 HL7 2.XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="72e8f-131">Using HL7 2.XML Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)