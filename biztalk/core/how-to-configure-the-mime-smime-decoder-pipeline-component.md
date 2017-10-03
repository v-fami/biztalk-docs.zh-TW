---
title: "如何設定 MIME SMIME 解碼器管線元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, attachments
- pipeline components, MIME/SMIME Decoder
- MIME/SMIME Decoder [pipeline component], configuring
- messages, verifying
- messages, decoding
- messages, digital signatures
- messages, security
ms.assetid: bfd44893-f1c3-4524-abc6-f820b8c0ef07
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a32137528de5ea18ea5698ab823c2e703651b71b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-mime-smime-decoder-pipeline-component"></a><span data-ttu-id="e583c-102">如何設定 MIME SMIME 解碼器管線元件</span><span class="sxs-lookup"><span data-stu-id="e583c-102">How to Configure the MIME-SMIME Decoder Pipeline Component</span></span>
<span data-ttu-id="e583c-103">MIME/SMIME 解碼器管線元件可用來解碼和解密經過 MIME/SMIME 編碼的訊息，也可以用來驗證簽章訊息的數位簽章。</span><span class="sxs-lookup"><span data-stu-id="e583c-103">The MIME/SMIME Decoder pipeline component is used for decoding and decrypting MIME/SMIME encoded messages and for verifying digital signatures of signed messages.</span></span> <span data-ttu-id="e583c-104">當外部夥伴和 BizTalk Server 之間需要安全的文件交換時，這個元件會非常有用。</span><span class="sxs-lookup"><span data-stu-id="e583c-104">This component is useful when secured document interchange is needed between external partners and BizTalk Server.</span></span> <span data-ttu-id="e583c-105">在接收有附件的訊息時也可以使用這個元件。</span><span class="sxs-lookup"><span data-stu-id="e583c-105">This component can also be used for receiving messages with attachments.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e583c-106">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，MIME/SMIME 解碼器管線元件並沒有原生 64 位元支援。</span><span class="sxs-lookup"><span data-stu-id="e583c-106">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the MIME/SMIME decoder pipeline component does not have native 64-bit support.</span></span>  <span data-ttu-id="e583c-107">這表示，此元件必須在 32 位元模擬模式程序 (WOW64) 中執行。</span><span class="sxs-lookup"><span data-stu-id="e583c-107">This means that this component must be run in a 32-bit emulation mode process (WOW64).</span></span>  <span data-ttu-id="e583c-108">而這也暗示，此解碼器元件執行所在的主控件執行個體 (或此元件所在的接收管線)，必須以 32 位元模擬模式執行。</span><span class="sxs-lookup"><span data-stu-id="e583c-108">This implies that the host instance in which this decoder component (or the receive pipeline of which it is a part) runs must be running in 32-bit emulation mode.</span></span>  <span data-ttu-id="e583c-109">請注意，這項限制對於在此相同主控件執行個體中執行的其他 BizTalk 項目，也會有效能上 (或其他方面) 的暗示。</span><span class="sxs-lookup"><span data-stu-id="e583c-109">Be aware of the performance (and other) implications of this restriction for other elements of BizTalk running in this same host instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e583c-110">MIME/SMIME 解碼器元件也用於 POP3 配接器。</span><span class="sxs-lookup"><span data-stu-id="e583c-110">The MIME/SMIME decoder component is also used within the POP3 adapter.</span></span>  <span data-ttu-id="e583c-111">因此，相同的原生 64 位元支援限制也存在於 POP3 配接器執行所在的主控件執行個體中。</span><span class="sxs-lookup"><span data-stu-id="e583c-111">As a result, the same native 64-bit support restriction exists for the host instance in which the POP3 adapter runs.</span></span>  <span data-ttu-id="e583c-112">請參閱中的 POP3 配接器的相關的資訊[POP3 配接器](../core/pop3-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="e583c-112">See related information about the POP3 adapter in [POP3 Adapter](../core/pop3-adapter.md).</span></span>  
  
### <a name="to-configure-the-properties-for-the-mimesmime-decoder-pipeline-component"></a><span data-ttu-id="e583c-113">設定 MIME/SMIME 解碼器管線元件的屬性</span><span class="sxs-lookup"><span data-stu-id="e583c-113">To configure the properties for the MIME/SMIME Decoder pipeline component</span></span>  
  
1.  <span data-ttu-id="e583c-114">將 MIME/SMIME 解碼器管線元件拖曳至接收管線的「解碼」階段中。</span><span class="sxs-lookup"><span data-stu-id="e583c-114">Drag the MIME/SMIME Decoder pipeline component into the Decode stage of a receive pipeline.</span></span>  
  
2.  <span data-ttu-id="e583c-115">在 [屬性] 視窗中**管線元件屬性**區段中，執行下列動作。</span><span class="sxs-lookup"><span data-stu-id="e583c-115">In the Properties window, in the **Pipeline Component Properties** section, do the following.</span></span>  
  
    |<span data-ttu-id="e583c-116">使用</span><span class="sxs-lookup"><span data-stu-id="e583c-116">Use this</span></span>|<span data-ttu-id="e583c-117">動作</span><span class="sxs-lookup"><span data-stu-id="e583c-117">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="e583c-118">**允許非 MIME 訊息**</span><span class="sxs-lookup"><span data-stu-id="e583c-118">**Allow Non MIME Message**</span></span>|<span data-ttu-id="e583c-119">將此屬性設定為**True**如果您預期接收管線可能會收到不 MIME 編碼的訊息。</span><span class="sxs-lookup"><span data-stu-id="e583c-119">Set this property to **True** if you expect that the receive pipeline may get messages that are not MIME encoded.</span></span> <span data-ttu-id="e583c-120">當 MIME/SMIME 解碼器元件用於接收不同格式訊息 (例如，以 MIME 編碼或標準 XML) 時，此選項很實用。</span><span class="sxs-lookup"><span data-stu-id="e583c-120">This option is useful when the MIME/SMIME Decoder pipeline component is used in a pipeline that receives messages in different forms, for example, MIME encoded or plain XML.</span></span> <span data-ttu-id="e583c-121">根據預設，這個屬性設定為**False**，如果它接收到非 MIME 元件會產生錯誤的意義編碼的輸入訊息時。</span><span class="sxs-lookup"><span data-stu-id="e583c-121">By default, this property is set to **False**, meaning that the component generates an error if it receives a non-MIME encoded message on input.</span></span> <span data-ttu-id="e583c-122">**注意：** MIME 解碼器會掃描傳入訊息來搜尋 「 MIME 版本 」 標頭前 1024 個位元組。</span><span class="sxs-lookup"><span data-stu-id="e583c-122">**Note:**  The MIME decoder scans the first 1024 bytes of the incoming message to search for the "MIME-Version" header.</span></span> <span data-ttu-id="e583c-123">若沒找到此標頭，則此訊息將被視為非 MIME 訊息。</span><span class="sxs-lookup"><span data-stu-id="e583c-123">If this header is not found, the message is treated as a non-MIME message.</span></span> <br /><br /> <span data-ttu-id="e583c-124">預設值： **False**</span><span class="sxs-lookup"><span data-stu-id="e583c-124">Default value: **False**</span></span>|  
    |<span data-ttu-id="e583c-125">**內文部分內容類型**</span><span class="sxs-lookup"><span data-stu-id="e583c-125">**Body part content type**</span></span>|<span data-ttu-id="e583c-126">指示 MIME 部分的內容類型。</span><span class="sxs-lookup"><span data-stu-id="e583c-126">Indicates the content type of the MIME part.</span></span> <span data-ttu-id="e583c-127">具有此內容類型的 MIME 部分將會變成 BizTalk 訊息的內文部分。</span><span class="sxs-lookup"><span data-stu-id="e583c-127">The MIME part with this content type will become the body part of the BizTalk message.</span></span><br /><br /> <span data-ttu-id="e583c-128">預設值：無</span><span class="sxs-lookup"><span data-stu-id="e583c-128">Default value: None</span></span>|  
    |<span data-ttu-id="e583c-129">**內文部分索引**</span><span class="sxs-lookup"><span data-stu-id="e583c-129">**Body part index**</span></span>|<span data-ttu-id="e583c-130">指示一維索引成為 MIME 部分清單。</span><span class="sxs-lookup"><span data-stu-id="e583c-130">Indicates the 1-based index into the MIME part list.</span></span> <span data-ttu-id="e583c-131">在清單中此索引上的 MIME 部分將會變成 BizTalk 訊息的內文部分。</span><span class="sxs-lookup"><span data-stu-id="e583c-131">The MIME part at this index in the list will become the body part of the BizTalk message.</span></span> <span data-ttu-id="e583c-132">若要停用索引的內文部分選取項目，請使用值**0**。</span><span class="sxs-lookup"><span data-stu-id="e583c-132">To disable the selection of body part by index, use a value of **0**.</span></span><br /><br /> <span data-ttu-id="e583c-133">預設值： **0**</span><span class="sxs-lookup"><span data-stu-id="e583c-133">Default value: **0**</span></span>|  
    |<span data-ttu-id="e583c-134">**檢查撤銷清單**</span><span class="sxs-lookup"><span data-stu-id="e583c-134">**Check Revocation List**</span></span>|<span data-ttu-id="e583c-135">將此屬性設定為**True**如果您想要檢查憑證撤銷清單，傳送者用來簽署傳送至 BizTalk Server 訊息的憑證。</span><span class="sxs-lookup"><span data-stu-id="e583c-135">Set this property to **True** if you want to check the certificate revocation list for the certificates that senders use for signing messages that are being sent to BizTalk Server.</span></span> <span data-ttu-id="e583c-136">停用此選項會提高元件的效能。</span><span class="sxs-lookup"><span data-stu-id="e583c-136">Disabling this option increases the performance of the component.</span></span><br /><br /> <span data-ttu-id="e583c-137">與憑證相關聯的憑證撤銷清單可從遠端網站下載的 (例如，Verisign.com)。</span><span class="sxs-lookup"><span data-stu-id="e583c-137">The certificate revocation list associated with a certificate is downloaded from a remote Web site (for example, Verisign.com).</span></span> <span data-ttu-id="e583c-138">若 BizTalk Server 無法連結至遠端網站，則訊息將在管線中發生失敗。</span><span class="sxs-lookup"><span data-stu-id="e583c-138">If the BizTalk Server cannot connect to the remote Web site, the message fails in the pipeline.</span></span><br /><br /> <span data-ttu-id="e583c-139">預設值： **，則為 True**</span><span class="sxs-lookup"><span data-stu-id="e583c-139">Default value: **True**</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e583c-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e583c-140">See Also</span></span>  
 <span data-ttu-id="e583c-141">[MIME SMIME 解碼器管線元件](../core/mime-smime-decoder-pipeline-component.md) </span><span class="sxs-lookup"><span data-stu-id="e583c-141">[MIME-SMIME Decoder Pipeline Component](../core/mime-smime-decoder-pipeline-component.md) </span></span>  
 <span data-ttu-id="e583c-142">[設定原生管線元件](../core/configuring-native-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="e583c-142">[Configuring Native Pipeline Components](../core/configuring-native-pipeline-components.md) </span></span>  
 <span data-ttu-id="e583c-143">[MIME SMIME 屬性結構描述和屬性](../core/mime-smime-property-schema-and-properties.md) </span><span class="sxs-lookup"><span data-stu-id="e583c-143">[MIME-SMIME Property Schema and Properties](../core/mime-smime-property-schema-and-properties.md) </span></span>  
 [<span data-ttu-id="e583c-144">MIME （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="e583c-144">MIME (BizTalk Server Sample)</span></span>](../core/mime-biztalk-server-sample.md)