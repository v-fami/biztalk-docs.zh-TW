---
title: "結構描述範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SDK samples, schemas
- examples, schemas
- schemas, examples
ms.assetid: 7d7e696d-935f-4582-b873-c5637673b651
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f346d2e7258c14e09dbcdc5f29ff0f7690cb4a4c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="schema-samples"></a><span data-ttu-id="1de39-102">結構描述範例</span><span class="sxs-lookup"><span data-stu-id="1de39-102">Schema Samples</span></span>
<span data-ttu-id="1de39-103">[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK 包含一系列 RNIF 和夥伴介面程序 (PIP) 處理的 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="1de39-103">The [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK includes a series of XSD schemas for RNIF and Partner Interface Process (PIP) processing.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="1de39-104">您可以使用這些結構描述處理訊息。</span><span class="sxs-lookup"><span data-stu-id="1de39-104"> uses these schemas to process messages.</span></span> <span data-ttu-id="1de39-105">您可以依照自己的目的修改這些結構描述，或是用來疑難排解失敗。</span><span class="sxs-lookup"><span data-stu-id="1de39-105">You can modify these schemas for your own purposes, or use these to troubleshoot failures.</span></span>  
  
 <span data-ttu-id="1de39-106">[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK 提供三組結構描述。</span><span class="sxs-lookup"><span data-stu-id="1de39-106">The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK provides three sets of schemas.</span></span> <span data-ttu-id="1de39-107">這些結構描述與 RosettaNet PIP、RosettaNet 下一代結構描述及 RNIF 結構描述關聯。</span><span class="sxs-lookup"><span data-stu-id="1de39-107">These schemas are XSD schemas associated with RosettaNet PIPs, RosettaNet next-generation schemas, and RNIF schemas.</span></span>  
  
## <a name="xsd-schemas-associated-with-rosettanet-pips"></a><span data-ttu-id="1de39-108">與 RosettaNet PIP 關聯的 XSD 結構描述</span><span class="sxs-lookup"><span data-stu-id="1de39-108">XSD Schemas associated with RosettaNet PIPs</span></span>  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="1de39-109"> 會使用這些結構描述，驗證訊息執行個體的服務內容。</span><span class="sxs-lookup"><span data-stu-id="1de39-109"> uses these schemas to validate the service content of message instances.</span></span> <span data-ttu-id="1de39-110">您可以修改這些結構描述，以變更訊息處理。</span><span class="sxs-lookup"><span data-stu-id="1de39-110">You can modify these schemas to change message processing.</span></span> <span data-ttu-id="1de39-111">在疑難排解處理服務內容中的錯誤時，您也可以使用結構描述驗證訊息執行個體。</span><span class="sxs-lookup"><span data-stu-id="1de39-111">You can also use the schemas to validate message instances when troubleshooting errors in processing service content.</span></span>  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="1de39-112"> 已經將這些結構描述編譯至 RNPIP 組件。</span><span class="sxs-lookup"><span data-stu-id="1de39-112"> has compiled these schemas into the RNPIPs assembly.</span></span> <span data-ttu-id="1de39-113">您可以解除部署 RNPIP 組件，再變更結構描述，然後重新部署 RNPIP，藉以修改任何其中一個結構描述。</span><span class="sxs-lookup"><span data-stu-id="1de39-113">You can modify any one of these schemas by undeploying the RNPIPs assembly, changing the schema, and then redeploying RNPIPs.</span></span> <span data-ttu-id="1de39-114">但是您必須小心，不要變更結構描述。</span><span class="sxs-lookup"><span data-stu-id="1de39-114">You must be careful that you do not change the schema.</span></span> <span data-ttu-id="1de39-115">如果變更結構描述，您所做的變更可能不符合對應的 RosettaNet PIP。</span><span class="sxs-lookup"><span data-stu-id="1de39-115">If you change the schema, your changes may not comply with the corresponding RosettaNet PIP.</span></span> <span data-ttu-id="1de39-116">您也可以在 RNPIP 中新增結構描述。</span><span class="sxs-lookup"><span data-stu-id="1de39-116">You can also add a schema to RNPIPs.</span></span> <span data-ttu-id="1de39-117">如需詳細資訊，請參閱[修改 Rnpip 中的現有 PIP](../../adapters-and-accelerators/accelerator-rosettanet/modifying-an-existing-pip-in-rnpips.md)。</span><span class="sxs-lookup"><span data-stu-id="1de39-117">For more information, see [Modifying an Existing PIP in RNPIPs](../../adapters-and-accelerators/accelerator-rosettanet/modifying-an-existing-pip-in-rnpips.md).</span></span>  
  
 <span data-ttu-id="1de39-118">[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]安裝程式會安裝在這些結構描述\<*磁碟機*>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本 > Accelerator for rosettanet\sdk\schemas。</span><span class="sxs-lookup"><span data-stu-id="1de39-118">The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Setup program installs these schemas in \<*drive*>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version> Accelerator for RosettaNet\SDK\Schemas.</span></span>  
  
## <a name="rnif-schemas"></a><span data-ttu-id="1de39-119">RNIF 結構描述</span><span class="sxs-lookup"><span data-stu-id="1de39-119">RNIF Schemas</span></span>  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="1de39-120"> 會使用這些結構描述驗證 RNIF 訊息部分，例如前序、服務標頭和傳遞標頭，</span><span class="sxs-lookup"><span data-stu-id="1de39-120"> uses these schemas to validate RNIF message parts, such as the preamble, service header, and delivery header.</span></span> <span data-ttu-id="1de39-121">其中也包括用於通知和例外狀況的結構描述。</span><span class="sxs-lookup"><span data-stu-id="1de39-121">These also include schemas for acknowledgments and exceptions.</span></span>  
  
 <span data-ttu-id="1de39-122">[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]安裝程式會安裝在這些結構描述\<*磁碟機*>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本 > Accelerator for RosettaNet\SDK\RNIFSchemas。</span><span class="sxs-lookup"><span data-stu-id="1de39-122">The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Setup program installs these schemas in \<*drive*>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version> Accelerator for RosettaNet\SDK\RNIFSchemas.</span></span>  
  
## <a name="rosettanet-next-generation-schemas"></a><span data-ttu-id="1de39-123">RosettaNet 下一代結構描述</span><span class="sxs-lookup"><span data-stu-id="1de39-123">RosettaNet Next-Generation Schemas</span></span>  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="1de39-124"> 會使用這些結構描述，驗證符合 RosettaNet 下一代結構描述的訊息。</span><span class="sxs-lookup"><span data-stu-id="1de39-124"> uses these schemas to validate messages conforming to next-generation schemas for RosettaNet.</span></span> <span data-ttu-id="1de39-125">這些結構描述本身支援 XSD，而非 DTD。</span><span class="sxs-lookup"><span data-stu-id="1de39-125">These schemas support XSD natively, instead of DTDs.</span></span> <span data-ttu-id="1de39-126">若要使用這些結構描述，將它們加入 Rnpip 組件中所述[修改 Rnpip 中的現有 PIP](../../adapters-and-accelerators/accelerator-rosettanet/modifying-an-existing-pip-in-rnpips.md)。</span><span class="sxs-lookup"><span data-stu-id="1de39-126">To use these schemas, add them to the RNPIPs assembly as described in [Modifying an Existing PIP in RNPIPs](../../adapters-and-accelerators/accelerator-rosettanet/modifying-an-existing-pip-in-rnpips.md).</span></span>  
  
 <span data-ttu-id="1de39-127">[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]安裝程式會安裝在這些結構描述\<*磁碟機*>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本 > Accelerator for RosettaNet\SDK\Schemas\網域、 \Interchange 和 \Universal 資料夾。</span><span class="sxs-lookup"><span data-stu-id="1de39-127">The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Setup program installs these schemas in the \<*drive*>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version> Accelerator for RosettaNet\SDK\Schemas\Domain, \Interchange, and \Universal folders.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1de39-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1de39-128">See Also</span></span>  
 <span data-ttu-id="1de39-129">[PIP 實作](../../adapters-and-accelerators/accelerator-rosettanet/pip-implementation.md) </span><span class="sxs-lookup"><span data-stu-id="1de39-129">[PIP Implementation](../../adapters-and-accelerators/accelerator-rosettanet/pip-implementation.md) </span></span>  
 <span data-ttu-id="1de39-130">[使用 Pip](../../adapters-and-accelerators/accelerator-rosettanet/working-with-pips.md) </span><span class="sxs-lookup"><span data-stu-id="1de39-130">[Working with PIPs](../../adapters-and-accelerators/accelerator-rosettanet/working-with-pips.md) </span></span>  
 [<span data-ttu-id="1de39-131">範例</span><span class="sxs-lookup"><span data-stu-id="1de39-131">Samples</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/samples3.md)