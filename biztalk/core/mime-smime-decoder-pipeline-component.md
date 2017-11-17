---
title: "MIME SMIME 解碼器管線元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components, MIME/SMIME Decoder
- MIME/SMIME Decoder [pipeline component]
ms.assetid: ff6c963c-1b5c-4be4-9eef-3ec9a018e7fd
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d85fe099cb876156410ba86c5f204a154dfbac36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="mime-smime-decoder-pipeline-component"></a><span data-ttu-id="7f7b9-102">MIME SMIME 解碼器管線元件</span><span class="sxs-lookup"><span data-stu-id="7f7b9-102">MIME-SMIME Decoder Pipeline Component</span></span>
<span data-ttu-id="7f7b9-103">MIME/SMIME 解碼器管線元件可為訊息提供 MIME 解碼功能。</span><span class="sxs-lookup"><span data-stu-id="7f7b9-103">The MIME/SMIME Decoder component provides MIME decoding functionality for messages.</span></span> <span data-ttu-id="7f7b9-104">此管線元件可放入接收管線的解碼階段，並支援 7 位元、8 位元、二進位、quoted-printable、UUEncode 以及 base64 解碼。</span><span class="sxs-lookup"><span data-stu-id="7f7b9-104">This pipeline component can be placed into the Decode stage of a receive pipeline, and it supports 7bit, 8bit, binary, quoted-printable, UUEncode, and base64 decoding.</span></span> <span data-ttu-id="7f7b9-105">當地語系化資料字元集變更不會影響解碼。</span><span class="sxs-lookup"><span data-stu-id="7f7b9-105">Localized data character set changes will not affect the decoding.</span></span>  
  
 <span data-ttu-id="7f7b9-106">MIME/SMIME 解碼器元件可以解密和簽章-驗證內送訊息。</span><span class="sxs-lookup"><span data-stu-id="7f7b9-106">The MIME/SMIME Decoder component can decrypt and sign-validate an incoming message.</span></span> <span data-ttu-id="7f7b9-107">從服務執行的目前使用者之個人憑證存放區使用解密憑證。</span><span class="sxs-lookup"><span data-stu-id="7f7b9-107">Decryption certificates are used from the personal certificate store of the current user under which the service is running.</span></span> <span data-ttu-id="7f7b9-108">從本機電腦的通訊錄存放區或訊息本身使用簽章-驗證憑證。</span><span class="sxs-lookup"><span data-stu-id="7f7b9-108">Sign-validation certificates are used from the Address Book store of the local computer or from the message itself.</span></span>  
  
 <span data-ttu-id="7f7b9-109">當訊息解密成功時，MIME/SMIME 解碼器管線元件會與用來將訊息解密為訊息述詞的解密憑證指紋相關聯。</span><span class="sxs-lookup"><span data-stu-id="7f7b9-109">On successful decryption of a message, the MIME/SMIME Decoder pipeline component associates the thumbprint of the decryption certificate used to decrypt the message as a predicate of the message.</span></span> <span data-ttu-id="7f7b9-110">這表示訂閱該訊息的任何服務 (協調流程或傳送埠) 都必須與擁有該金鑰的主控件相關聯。</span><span class="sxs-lookup"><span data-stu-id="7f7b9-110">This means that any service (orchestration or send port) that is subscribing to that message must be associated with a host that owns that key.</span></span> <span data-ttu-id="7f7b9-111">可以在 [BizTalk 管理] 主控台完成主控件與金鑰之間的關聯，作為主控件的屬性。</span><span class="sxs-lookup"><span data-stu-id="7f7b9-111">Associations between hosts and keys can be completed in the BizTalk Administration console as a property of the host.</span></span> <span data-ttu-id="7f7b9-112">如需在 BizTalk 管理主控台中設定主機的詳細資訊，請參閱[如何修改主機內容](../core/how-to-modify-host-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="7f7b9-112">For more information about configuring the host in the BizTalk Administration console, see [How to Modify Host Properties](../core/how-to-modify-host-properties.md).</span></span>  
  
 <span data-ttu-id="7f7b9-113">MIME/SMIME 解碼器管線元件是唯一現成的接收管線元件，可處理多部分訊息，包括多部分 MIME/SMIME 訊息。</span><span class="sxs-lookup"><span data-stu-id="7f7b9-113">The MIME/SMIME Decoder pipeline component is the only out-of-the-box receive pipeline component that handles multi-part messages, including multi-part MIME/SMIME messages.</span></span> <span data-ttu-id="7f7b9-114">管線元件會剖析訊息並建立對等的多部分 BizTalk 訊息。</span><span class="sxs-lookup"><span data-stu-id="7f7b9-114">The pipeline component parses the message and creates an equivalent multi-part BizTalk message.</span></span> <span data-ttu-id="7f7b9-115">多部分 BizTalk 訊息中有一個稱為內文部分的唯一部分。</span><span class="sxs-lookup"><span data-stu-id="7f7b9-115">A multi-part BizTalk message has one unique part named the body part.</span></span> <span data-ttu-id="7f7b9-116">所有其他管線元件 (例如 XML 解譯器管線元件) 只處理 BizTalk 訊息的內文部分。</span><span class="sxs-lookup"><span data-stu-id="7f7b9-116">All other pipeline components, such as the XML Disassembler pipeline component, only process the body part of the BizTalk Message.</span></span> <span data-ttu-id="7f7b9-117">還有對應到 BizTalk 內文部分的 MessageType，可用以路由訊息至訂閱者。</span><span class="sxs-lookup"><span data-stu-id="7f7b9-117">Also the MessageType corresponding to the BizTalk body part is used for routing the message to subscribers.</span></span>  
  
 <span data-ttu-id="7f7b9-118">下列條件由 MIME/SMIME 解碼器管線元件評估，以識別對應到多部分 MIME 訊息的 BizTalk BodyPart。</span><span class="sxs-lookup"><span data-stu-id="7f7b9-118">The following conditions are evaluated by the MIME/SMIME Decoder pipeline component to identify the BizTalk BodyPart corresponding to a multi-part MIME message.</span></span> <span data-ttu-id="7f7b9-119">條件評估的順序如下：</span><span class="sxs-lookup"><span data-stu-id="7f7b9-119">The order of the condition evaluation is as follows:</span></span>  
  
1.  <span data-ttu-id="7f7b9-120">具有設定為 "body" (區分大小寫) 的內容描述標頭的第一個 MIME/SMIME 部分。</span><span class="sxs-lookup"><span data-stu-id="7f7b9-120">The first MIME/SMIME part that has the Content-Description header set to "body" (case-insensitive).</span></span>  
  
2.  <span data-ttu-id="7f7b9-121">具有設定為 "text/xml" (區分大小寫) 的內容類型標頭的第一個 MIME/SMIME 部分。</span><span class="sxs-lookup"><span data-stu-id="7f7b9-121">The first MIME/SMIME part that has the Content-Type header set to "text/xml"(case-insensitive).</span></span>  
  
3.  <span data-ttu-id="7f7b9-122">具有設定為 "text/" (區分大小寫) 的內容類型標頭的第一個 MIME/SMIME 部分。</span><span class="sxs-lookup"><span data-stu-id="7f7b9-122">The first MIME/SMIME part that has the Content-Type header set to "text/" (case-insensitive).</span></span>  
  
4.  <span data-ttu-id="7f7b9-123">第一個 MIME/SMIME 部分。</span><span class="sxs-lookup"><span data-stu-id="7f7b9-123">The first MIME/SMIME part.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f7b9-124">輸出 BizTalk 訊息中的部分順序與 MIME/SMIME 訊息中 MIME/SMIME 的部分順序相同。</span><span class="sxs-lookup"><span data-stu-id="7f7b9-124">The order of the parts in the output BizTalk message is same as the order of MIME/SMIME parts in the MIME/SMIME message.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f7b9-125">若協調流程訂閱或取用多部分 BizTalk 訊息，則訊息中的部分數目必須符合啟動協調流程的訊息中的部分數目。</span><span class="sxs-lookup"><span data-stu-id="7f7b9-125">If the multi-part BizTalk message is being subscribed or consumed by an orchestration, the number of parts in the message has to match the number of parts in the message that activates the orchestration.</span></span>  
  
 <span data-ttu-id="7f7b9-126">如需設定 MIME/SMIME 解碼器管線元件的資訊，請參閱[如何設定 MIME SMIME 解碼器管線元件](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md)。</span><span class="sxs-lookup"><span data-stu-id="7f7b9-126">For information about configuring the MIME/SMIME Decoder pipeline component, see [How to Configure the MIME-SMIME Decoder Pipeline Component](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md).</span></span> <span data-ttu-id="7f7b9-127">如需 BizTalk Server 支援解密、 簽章驗證和憑證的使用方式的詳細資訊，請參閱[傳送和接收訊息的安全性](../core/security-for-sending-and-receiving-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="7f7b9-127">For more information about BizTalk Server support for decryption, sign-validation, and usage of certificates, see [Security for Sending and Receiving Messages](../core/security-for-sending-and-receiving-messages.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f7b9-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f7b9-128">See Also</span></span>  
 <span data-ttu-id="7f7b9-129">[管線元件](../core/pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="7f7b9-129">[Pipeline Components](../core/pipeline-components.md) </span></span>  
 <span data-ttu-id="7f7b9-130">[MIME SMIME 屬性結構描述和屬性](../core/mime-smime-property-schema-and-properties.md) </span><span class="sxs-lookup"><span data-stu-id="7f7b9-130">[MIME-SMIME Property Schema and Properties](../core/mime-smime-property-schema-and-properties.md) </span></span>  
 [<span data-ttu-id="7f7b9-131">MIME （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="7f7b9-131">MIME (BizTalk Server Sample)</span></span>](../core/mime-biztalk-server-sample.md)