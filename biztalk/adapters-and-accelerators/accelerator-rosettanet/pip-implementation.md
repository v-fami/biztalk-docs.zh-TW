---
title: "PIP 實作 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PIPs
- PIPs, element-level constraints
- Document Type Definitions (DTDs)
- PIPs, schemas
- examples, schemas
- schemas, examples
- PIPs, about PIPs
- element-level constraints
- PIPs, DTDs
- schemas, PIPs
- XML Schema Definition files (XSDs)
- Partner Interface Processes (PIPs)
- DTDs, XSDs
- schemas, XSDs
ms.assetid: 0d964223-e0b6-4377-b26a-5fdc89ec81f4
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70d845aa99910125a64e8a0744c4b3ef42d40f09
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="pip-implementation"></a><span data-ttu-id="b4b2e-102">PIP 實作</span><span class="sxs-lookup"><span data-stu-id="b4b2e-102">PIP Implementation</span></span>
<span data-ttu-id="b4b2e-103">RosettaNet 夥伴介面程序 (Pip) 會定義供應鏈中的交易夥伴之間的商務程序。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-103">RosettaNet Partner Interface Processes (PIPs) define business processes between trading partners in a supply chain.</span></span> [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="b4b2e-104">[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]提供一組 Pip 的方塊外，您可以建立其他的 Pip。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-104">[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] provides a set of PIPs out-of-the-box and you can create additional PIPs.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="b4b2e-105">支援 RosettaNet 組織所定義的所有 Pip。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-105"> supports all PIPs defined by the RosettaNet organization.</span></span>  
  
 <span data-ttu-id="b4b2e-106">如需詳細資訊，請參閱[RosettaNet Pip](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-pips.md)。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-106">For more information, see [RosettaNet PIPs](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-pips.md).</span></span>  
  
## <a name="schemas-in-btarn"></a><span data-ttu-id="b4b2e-107">BTARN 中的結構描述</span><span class="sxs-lookup"><span data-stu-id="b4b2e-107">Schemas in BTARN</span></span>  
 <span data-ttu-id="b4b2e-108">RosettaNet 以「文件類型定義」(DTD) 形式定義所有的 PIP 訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-108">RosettaNet specifies all PIP message schemas in the form of Document Type Definitions (DTDs).</span></span> <span data-ttu-id="b4b2e-109">在商務文件交換過程中參與的交易夥伴必須遵循這些 DTD。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-109">Trading partners who participate in the business-document exchange must comply with these DTDs.</span></span> <span data-ttu-id="b4b2e-110">不過，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]因為會將這些 Dtd 實作為 XML 結構描述定義檔案 (Xsd)，Microsoft[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]使用 Xsd 而非 Dtd 來呈現文件。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-110">However, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] implements these DTDs as XML Schema Definition files (XSDs), because Microsoft  [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] represents documents by using XSDs, not DTDs.</span></span> <span data-ttu-id="b4b2e-111">就功能而言，XSD 會取代 DTD，並且可以自然呈現訊息指導方針所提供的大部分資訊。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-111">XSDs supersede DTDs in terms of functionality, and can represent most of the information provided in the message guidelines natively.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="b4b2e-112"> 也支援 RosettaNet 組織最近所發佈，使用 XSD 規格的下一代 PIP。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-112"> also supports next-generation PIPs, recently published by the RosettaNet organization, that use XSD specifications.</span></span>  
  
 <span data-ttu-id="b4b2e-113">若要實作新的 PIP，您必須將 PIP 的 DTD 轉換為 XSD。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-113">To implement a new PIP, you must convert the PIP's DTD into an XSD.</span></span> <span data-ttu-id="b4b2e-114">下載從 RosettaNet 網站，網址 PIP 相關聯的 DTD [http://go.microsoft.com/fwlink/?linkid=33859](http://go.microsoft.com/fwlink/?linkid=33859)。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-114">You download the DTD associated with the PIP from the RosettaNet Web site at [http://go.microsoft.com/fwlink/?linkid=33859](http://go.microsoft.com/fwlink/?linkid=33859).</span></span> <span data-ttu-id="b4b2e-115">然後，您可以根據 PIP 建立 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 程序組態設定檔。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-115">You then create a [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] process configuration profile based on the PIP.</span></span> <span data-ttu-id="b4b2e-116">如需詳細資訊，請參閱[納入新的交易夥伴介面程序](../../adapters-and-accelerators/accelerator-rosettanet/incorporating-a-new-partner-interface-process.md)。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-116">For more information, see [Incorporating a New Partner Interface Process](../../adapters-and-accelerators/accelerator-rosettanet/incorporating-a-new-partner-interface-process.md).</span></span>  
  
 <span data-ttu-id="b4b2e-117">您可以根據現有的設定檔建立新的程序組態設定檔。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-117">You can create a new process configuration profile based on an existing profile.</span></span> <span data-ttu-id="b4b2e-118">如需詳細資訊，請參閱[如何建立或編輯程序組態](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-118">For more information, see [How to Create or Edit a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).</span></span> <span data-ttu-id="b4b2e-119">您可以在相同交易夥伴之間根據相同的程序組態設定檔建立多重協議。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-119">You can create multiple agreements based on the same process configuration profile between the same partners.</span></span> <span data-ttu-id="b4b2e-120">然而，您一次只能啟動其中一個協議。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-120">However, you can only activate one of them at a time.</span></span> <span data-ttu-id="b4b2e-121">若要建立和啟動協議，請參閱[建立或編輯協議](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-121">To create and activate an agreement, see [Creating or Editing an Agreement](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md).</span></span>  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="b4b2e-122"> 會使用下列 RosettaNet 標頭的 RosettaNet 訊息指導方針條件約束實作 XSD：</span><span class="sxs-lookup"><span data-stu-id="b4b2e-122"> implements XSDs with the RosettaNet message-guideline constraints for the following RosettaNet headers:</span></span>  
  
-   <span data-ttu-id="b4b2e-123">RNIF 1.1 及 RNIF 2.01 的前序</span><span class="sxs-lookup"><span data-stu-id="b4b2e-123">Preamble for RNIF 1.1 and RNIF 2.01</span></span>  
  
-   <span data-ttu-id="b4b2e-124">RNIF 1.1 及 RNIF 2.0 的服務標頭</span><span class="sxs-lookup"><span data-stu-id="b4b2e-124">Service header for RNIF 1.1 and RNIF 2.0</span></span>  
  
-   <span data-ttu-id="b4b2e-125">RNIF 2.0 的傳遞標頭</span><span class="sxs-lookup"><span data-stu-id="b4b2e-125">Delivery header for RNIF 2.0</span></span>  
  
-   <span data-ttu-id="b4b2e-126">RNIF 1.1 及 RNIF 2.01 所有信號訊息的服務內容。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-126">Service content for all signal messages of RNIF 1.1 and RNIF 2.01.</span></span>  
  
## <a name="sample-schemas"></a><span data-ttu-id="b4b2e-127">範例結構描述</span><span class="sxs-lookup"><span data-stu-id="b4b2e-127">Sample Schemas</span></span>  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="b4b2e-128">安裝程式會安裝一組 Pip 中\<*磁碟機*>: \Program Files\Microsoft BizTalk\<版本 > Accelerator for rosettanet\sdk\schemas。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-128"> setup installs a set of PIPs in \<*drive*>:\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK\Schemas.</span></span> <span data-ttu-id="b4b2e-129">這些僅當做範例使用。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-129">These are for sample purposes only.</span></span> <span data-ttu-id="b4b2e-130">實際運用在執行環境之前，我們強烈建議您將這些結構描述與最近發佈的 RosettaNet PIP 規格和訊息指導方針進行比較。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-130">Before using them in production, it is highly recommended that you compare these schemas against the latest published RosettaNet PIP specifications and message guidelines.</span></span> <span data-ttu-id="b4b2e-131">BTARN 支援所有 RosettaNet PIP 的實作。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-131">BTARN supports implementation of all RosettaNet PIPs.</span></span>  
  
## <a name="element-level-constraints-in-btarn"></a><span data-ttu-id="b4b2e-132">BTARN 中的元素階層條件約束</span><span class="sxs-lookup"><span data-stu-id="b4b2e-132">Element-Level Constraints in BTARN</span></span>  
 <span data-ttu-id="b4b2e-133">在 BTARN 中，您可以將 PIP 訊息指導方針文件中指定的元素階層條件約束實作為程序組態設定。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-133">In BTARN, you implement the element-level constraints specified in the PIP message-guideline documents as process configuration settings.</span></span> <span data-ttu-id="b4b2e-134">執行階段元件會使用程序組態決定處理特定 PIP 的方式。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-134">Runtime components use the process configuration to determine how to process a specific PIP.</span></span>  
  
 <span data-ttu-id="b4b2e-135">若要實作新的 PIP，您必須建立新的程序組態設定檔，以套用 PIP 的訊息指導方針條件約束。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-135">To implement a new PIP, you must apply the message guideline constraints for the PIP by creating a new process configuration profile.</span></span> <span data-ttu-id="b4b2e-136">您可以在 BTARN 管理主控台中執行這個動作。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-136">You do this in the BTARN Management Console.</span></span> <span data-ttu-id="b4b2e-137">如需詳細資訊，請參閱[如何建立或編輯程序組態](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-137">For more information, see [How to Create or Edit a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).</span></span>  
  
 <span data-ttu-id="b4b2e-138">程序組態設定檔對應至 RosettaNet PIP 規格中所示[使用 PIP 規格建立程序組態](../../adapters-and-accelerators/accelerator-rosettanet/using-the-pip-specification-to-create-a-process-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="b4b2e-138">The process configuration profile maps to the RosettaNet PIP specification as shown in [Using the PIP Specification to Create a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/using-the-pip-specification-to-create-a-process-configuration.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4b2e-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4b2e-139">See Also</span></span>  
 <span data-ttu-id="b4b2e-140">[BizTalk Accelerator for RosettaNet 新增至 BizTalk Server](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="b4b2e-140">[What BizTalk Accelerator for RosettaNet Adds to BizTalk Server](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md) </span></span>  
 <span data-ttu-id="b4b2e-141">[交易夥伴協議](../../adapters-and-accelerators/accelerator-rosettanet/trading-partner-agreements.md) </span><span class="sxs-lookup"><span data-stu-id="b4b2e-141">[Trading Partner Agreements](../../adapters-and-accelerators/accelerator-rosettanet/trading-partner-agreements.md) </span></span>  
 [<span data-ttu-id="b4b2e-142">RosettaNet Pip</span><span class="sxs-lookup"><span data-stu-id="b4b2e-142">RosettaNet PIPs</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/rosettanet-pips.md)