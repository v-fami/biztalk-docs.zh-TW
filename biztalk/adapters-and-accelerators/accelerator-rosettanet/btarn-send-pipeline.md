---
title: BTARN 傳送管線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XML Assembler
- send pipelines, message flow
- DOCTYPE headers
- MIME/SMIME Encoder
- send pipelines, BTARN
- BTARN, send pipelines
- XML Preprocessor
- messages, message flow
ms.assetid: 88562132-0ea4-4b5a-9445-b69f6c84e5ea
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0791ab4714e1e8a9de847a60d17d14e38f095ecf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011631"
---
# <a name="btarn-send-pipeline"></a><span data-ttu-id="e5c6b-102">BTARN 傳送管線</span><span class="sxs-lookup"><span data-stu-id="e5c6b-102">BTARN Send Pipeline</span></span>
<span data-ttu-id="e5c6b-103">Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] RNIFSend 管線 (RNIFSend.btp) 中的傳輸會準備 RosettaNet 實作架構 (RNIF) 訊息。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-103">Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] prepares a RosettaNet Implementation Framework (RNIF) message for transmission in the RNIFSend pipeline (RNIFSend.btp).</span></span> <span data-ttu-id="e5c6b-104">傳送管線包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="e5c6b-104">The send pipeline includes the following:</span></span>  
  
-   <span data-ttu-id="e5c6b-105">XML 前置處理器</span><span class="sxs-lookup"><span data-stu-id="e5c6b-105">XML preprocessor</span></span>  
  
-   <span data-ttu-id="e5c6b-106">XML 組合器</span><span class="sxs-lookup"><span data-stu-id="e5c6b-106">XML assembler</span></span>  
  
-   <span data-ttu-id="e5c6b-107">多用途網際網路郵件延伸標準/安全多用途網際網路郵件延伸 (MIME/SMIME) 編碼器</span><span class="sxs-lookup"><span data-stu-id="e5c6b-107">Multipurpose Internet Mail Extensions/Secure Multipurpose Internet Mail Extensions (MIME/SMIME) encoder</span></span>  
  
## <a name="xml-preprocessor"></a><span data-ttu-id="e5c6b-108">XML 前置處理器</span><span class="sxs-lookup"><span data-stu-id="e5c6b-108">XML Preprocessor</span></span>  
 <span data-ttu-id="e5c6b-109">XML 前置處理器會將訊息中的 DOCTYPE 標頭。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-109">The XML preprocessor adds a DOCTYPE header to the message.</span></span> <span data-ttu-id="e5c6b-110">標頭會識別與訊息相關聯的文件類型定義 (DTD) 結構描述。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-110">The header identifies the document type definition (DTD) schema associated with the message.</span></span> <span data-ttu-id="e5c6b-111">RNIF 規格要求必須有 DOCTYPE 標頭才能進行 RNIF 傳輸。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-111">The RNIF specification requires the presence of a DOCTYPE header for RNIF transmission.</span></span>  
  
## <a name="xml-assembler"></a><span data-ttu-id="e5c6b-112">XML 組合器</span><span class="sxs-lookup"><span data-stu-id="e5c6b-112">XML Assembler</span></span>  
 <span data-ttu-id="e5c6b-113">「 XML 組合器 」 根據 「 BizTalk Server XML 組合器 」。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-113">The XML assembler is based on the BizTalk Server XML assembler.</span></span> <span data-ttu-id="e5c6b-114">它會將訊息內容的屬性傳送到信封和文件中，</span><span class="sxs-lookup"><span data-stu-id="e5c6b-114">It transfers properties from the message context back into envelopes and documents.</span></span> <span data-ttu-id="e5c6b-115">並從訊息的 XML 部分和附件組合訊息。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-115">It assembles the message from its XML parts and attachments.</span></span> <span data-ttu-id="e5c6b-116">它並不會執行訊息驗證。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-116">It does not perform message validation.</span></span>  
  
 <span data-ttu-id="e5c6b-117">如需有關原生[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]XML 組合器，請參閱 「 XML 組合器管線元件 」 在 BizTalk Server 說明中。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-117">For more information about the native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] XML assembler, see "XML Assembler Pipeline Component" in BizTalk Server Help.</span></span>  
  
## <a name="mimesmime-encoder"></a><span data-ttu-id="e5c6b-118">MIME/SMIME 編碼器</span><span class="sxs-lookup"><span data-stu-id="e5c6b-118">MIME/SMIME Encoder</span></span>  
 <span data-ttu-id="e5c6b-119">MIME/SMIME 編碼器是以 BizTalk Server MIME/SMIME 編碼器為基礎。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-119">The MIME/SMIME encoder is based on the BizTalk Server MIME/SMIME Encoder.</span></span> <span data-ttu-id="e5c6b-120">根據交易夥伴協議和 BizTalk Server MIME/SMIME 編碼器的設定中的通訊協定設定[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]編碼器會執行下列：</span><span class="sxs-lookup"><span data-stu-id="e5c6b-120">Depending on the protocol settings in the trading partner agreement, and the settings of the BizTalk Server MIME/SMIME Encoder, the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] encoder performs the following:</span></span>  
  
- <span data-ttu-id="e5c6b-121">新增 8 位元組二進位標頭到訊息，這是 RNIF 1.1 訊息的要求。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-121">Adds an 8-byte binary header to the message, as required for RNIF 1.1 messages.</span></span>  
  
- <span data-ttu-id="e5c6b-122">編碼訊息部分，並計算摘要。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-122">Encodes the message parts, and calculates the digest.</span></span>  
  
- <span data-ttu-id="e5c6b-123">加密內容 (服務內容加上附件) 或內容容器 (服務內容加上服務標頭及附件)。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-123">Encrypts the payload (service content plus attachments), or the payload container (service content plus service header plus attachments).</span></span> <span data-ttu-id="e5c6b-124">如果您已將**編碼所有的連接埠**上設定**通訊協定**至交易夥伴協議索引標籤`False`，編碼器將加密只裝載。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-124">If you have set the **Encode all ports** setting on the **Protocol** tab of the trading partner agreement to `False`, the encoder will encrypt only the payload.</span></span> <span data-ttu-id="e5c6b-125">如果您已將**編碼所有的連接埠**設為  `True`，編碼器將加密內容容器。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-125">If you have set the **Encode all ports** setting to `True`, the encoder will encrypt the payload container.</span></span>  
  
  <span data-ttu-id="e5c6b-126">如需有關原生[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]MIME/SMIME 編碼器，請參閱 「 MIME/SMIME 編碼器管線元件 」 在 BizTalk Server 說明中。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-126">For more information about the native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] MIME/SMIME Encoder, see "MIME/SMIME Encoder Pipeline Component" in BizTalk Server Help.</span></span>  
  
## <a name="message-flow"></a><span data-ttu-id="e5c6b-127">訊息流程</span><span class="sxs-lookup"><span data-stu-id="e5c6b-127">Message Flow</span></span>  
 <span data-ttu-id="e5c6b-128">透過 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 傳送管線的訊息流程如下：</span><span class="sxs-lookup"><span data-stu-id="e5c6b-128">The message flow through the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] send pipeline is as follows:</span></span>  
  
1.  <span data-ttu-id="e5c6b-129">如果您已將**編碼所有部分**交易夥伴協議，以設定`True`，MIME/SMIME 編碼器會都編碼所有的訊息部分。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-129">If you have set the **Encode all parts** setting of the trading partner agreement to `True`, the MIME/SMIME encoder will encode all message parts.</span></span> <span data-ttu-id="e5c6b-130">MIME/SMIME 編碼器將會使用協議的 `Encoding` 屬性中設定的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-130">It will use the encoding method set in the `Encoding` property of the agreement.</span></span>  
  
2.  <span data-ttu-id="e5c6b-131">對於 RNIF 2.01，如果訊息是動作訊息且有附件，編碼器將對每個附件執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e5c6b-131">For RNIF 2.01, if the message is an action message and there is an attachment, the encoder will do the following for each attachment:</span></span>  
  
    1.  <span data-ttu-id="e5c6b-132">如果附件是二進位，編碼器將編碼該附件。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-132">If the attachment is binary, the encoder will encode it.</span></span>  
  
    2.  <span data-ttu-id="e5c6b-133">編碼器將產生附件的內容識別碼。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-133">The encoder will generate a content ID for the attachment.</span></span>  
  
    3.  <span data-ttu-id="e5c6b-134">編碼器將建立附件的 MIME 部分。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-134">The encoder will create a MIME part for the attachment.</span></span>  
  
3.  <span data-ttu-id="e5c6b-135">對於 RNIF 2.01，管線會將加密訊息部分，然後建立 RNIF 訊息，視設定而定**需要持續的機密性**（在程序組態設定）：</span><span class="sxs-lookup"><span data-stu-id="e5c6b-135">For RNIF 2.01, the pipeline will encrypt message parts and build the RNIF message depending on the setting of **Is Persistent Confidentiality Required** (as set in the process configuration settings):</span></span>  
  
    1.  <span data-ttu-id="e5c6b-136">如果您已將**需要持續的機密性**要**承載**，編碼器將加密服務內容和附件。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-136">If you have set **Is Persistent Confidentiality Required** to **Payload**, the encoder will encrypt the service content and the attachments.</span></span> <span data-ttu-id="e5c6b-137">接著，組合器會新增服務標頭、傳遞標頭和前序，以建構最後的 RNIF 訊息。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-137">The assembler will then add the service header, delivery header, and preamble to construct the final RNIF message.</span></span>  
  
    2.  <span data-ttu-id="e5c6b-138">如果您已將**需要持續的機密性**要**承載容器**，編碼器將加密服務標頭、 服務內容以及附件。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-138">If you have set **Is Persistent Confidentiality Required** to **Payload Container**, the encoder will encrypt the service header, service content, and the attachments.</span></span> <span data-ttu-id="e5c6b-139">接著，組合器會新增傳遞標頭和前序，以建構最後的 RNIF 訊息。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-139">The assembler will then add the delivery header and preamble to construct the final RNIF message.</span></span>  
  
    3.  <span data-ttu-id="e5c6b-140">如果您已將**需要持續的機密性**要**無**，組合器會新增服務標頭、 傳遞標頭和前序編碼的服務內容和附件 （不含「 加密 」） 以建構最後的 RNIF 訊息。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-140">If you have set **Is Persistent Confidentiality Required** to **None**, the assembler will add the service header, delivery header, and preamble to the service content and the attachments (without encryption) to construct the final RNIF message.</span></span>  
  
4.  <span data-ttu-id="e5c6b-141">對於 RNIF 1.1，組合器將建構未加密的最後 RNIF 訊息。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-141">For RNIF 1.1, the assembler will construct the final RNIF message without encryption.</span></span>  
  
5.  <span data-ttu-id="e5c6b-142">在以下情況中，編碼器將簽署訊息：</span><span class="sxs-lookup"><span data-stu-id="e5c6b-142">The encoder will sign the message in the following case:</span></span>  
  
    1.  <span data-ttu-id="e5c6b-143">訊息是信號訊息，而**不可否認性所需**屬性 （在程序組態設定中） 是`True`。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-143">The message is a signal message, and the **Non-Repudiation Required** property (in the process configuration settings) is `True`.</span></span>  
  
    2.  <span data-ttu-id="e5c6b-144">訊息是動作訊息，而**來源與內容的不可否認**屬性 （在程序組態設定中） 是`True`。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-144">The message is an action message, and the **Non-Repudiation of Origin and Content** property (in the process configuration settings) is `True`.</span></span>  
  
6.  <span data-ttu-id="e5c6b-145">對於 RNIF 2.01，編碼器將計算 MIME 訊息第一個內文部分的摘要，並保留摘要。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-145">For RNIF 2.01, the encoder will calculate the digest on the first body part of the MIME message, and persist the digest.</span></span> <span data-ttu-id="e5c6b-146">它將使用交易夥伴協議 (SHA-1 或 MD5) 中 `Digest` 方法屬性所設定的方法來計算摘要。</span><span class="sxs-lookup"><span data-stu-id="e5c6b-146">It will calculate the digest using the method set in the `Digest` method property in the trading partner agreement (SHA-1 or MD5).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5c6b-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5c6b-147">See Also</span></span>  
 [<span data-ttu-id="e5c6b-148">BTARN 中的訊息處理</span><span class="sxs-lookup"><span data-stu-id="e5c6b-148">Message Processing in BTARN</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md)