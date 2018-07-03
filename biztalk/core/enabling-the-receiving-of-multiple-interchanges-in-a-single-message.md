---
title: 啟用多個接收單一訊息中的交換 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c98bcd2e-495a-49d8-a471-6e23b1e161f9
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77af57fb4a72e2e0c039b512d4e6f30659ccedd5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006847"
---
# <a name="enabling-the-receiving-of-multiple-interchanges-in-a-single-message"></a><span data-ttu-id="59c2e-102">啟用接收單一訊息中的多重交換</span><span class="sxs-lookup"><span data-stu-id="59c2e-102">Enabling the Receiving of Multiple Interchanges in a Single Message</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="59c2e-103"> 可以處理包含多個交換的訊息。</span><span class="sxs-lookup"><span data-stu-id="59c2e-103"> can process a message that contains multiple interchanges.</span></span> <span data-ttu-id="59c2e-104">對於 X12 訊息，這類訊息會包含多重 ISA 標頭和 IEA 結尾。</span><span class="sxs-lookup"><span data-stu-id="59c2e-104">For an X12 message, such a message would include multiple ISA headers and IEA trailers.</span></span> <span data-ttu-id="59c2e-105">對於 EDIFACT 訊息，這類訊息會包含多重 UNA/UNB 標頭和 UNZ 結尾。</span><span class="sxs-lookup"><span data-stu-id="59c2e-105">For an EDIFACT message, such a message would include multiple UNA/UNB headers and UNZ trailers.</span></span>  
  
 <span data-ttu-id="59c2e-106">若要讓 EDI 解譯器在 EdiReceive 或 AS2EdiReceive 管線，以剖析單一訊息中的多個交換，您必須設定**DetectMID**管線屬性 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="59c2e-106">To enable the EDI Disassembler in the EdiReceive or AS2EdiReceive pipeline to parse multiple interchanges in a single message, you must set the **DetectMID** pipeline property to **True**.</span></span> <span data-ttu-id="59c2e-107">(MID 表示多重交換解譯)。根據預設，此屬性是設定為 True。</span><span class="sxs-lookup"><span data-stu-id="59c2e-107">(MID stands for multiple interchange disassembling.) This property is set to True by default.</span></span>  
  
 <span data-ttu-id="59c2e-108">當包含 EDI 解譯器的接收管線收到具有多重交換的訊息時，解譯器會剖析交換標頭到交換結尾的每個交換。</span><span class="sxs-lookup"><span data-stu-id="59c2e-108">When the receive pipeline that includes the EDI Disassembler receives a message with multiple interchange, the Disassembler will parse each interchange from the interchange header to the interchange trailer.</span></span> <span data-ttu-id="59c2e-109">這項處理會根據下列規則執行：</span><span class="sxs-lookup"><span data-stu-id="59c2e-109">This processing is done according to the following rules:</span></span>  
  
- <span data-ttu-id="59c2e-110">相同訊息中的所有交換必須是相同的編碼類型 (X12 或 EDIFACT)。</span><span class="sxs-lookup"><span data-stu-id="59c2e-110">All interchanges in the same message must be of the same encoding type, either X12 or EDIFACT.</span></span> <span data-ttu-id="59c2e-111">如果訊息包含多個編碼類型的交換，EDI 解譯器會處理與訊息中第一個交換編碼類型相同的所有交換。</span><span class="sxs-lookup"><span data-stu-id="59c2e-111">If the message contains interchanges of more than one encoding type, the EDI Disassembler will process all interchanges that have the same encoding type as the first interchange in the message.</span></span> <span data-ttu-id="59c2e-112">解譯器會忽略與第一個交換的編碼類型不同的所有交換。</span><span class="sxs-lookup"><span data-stu-id="59c2e-112">The Disassembler will ignore all interchanges that are of a different encoding type from the first interchange.</span></span>  
  
- <span data-ttu-id="59c2e-113">EDI 解譯器會忽略某個交換的交換結尾與下一個交換的交換標頭之間的任何字元。</span><span class="sxs-lookup"><span data-stu-id="59c2e-113">The EDI Disassembler will ignore any character between the interchange trailer of one interchange and the interchange heading of the next interchange.</span></span>  
  
- <span data-ttu-id="59c2e-114">如果您啟用選取的驗證**驗證失敗時捨棄訊息**或**驗證失敗時保留訊息**屬性，接收埠，然後[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]將如果多個訊息的交換中的任何一個失敗時，請擱置整個訊息。</span><span class="sxs-lookup"><span data-stu-id="59c2e-114">If you enable authentication by selecting either the **Drop messages if authentication fails** or the **Keep messages if authentication fails** property for the receive port, then [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will suspend the entire message if any one of the multiple interchanges in the message fails.</span></span>  
  
- <span data-ttu-id="59c2e-115">如果啟用驗證，而且相同訊息中的任何一個交換未解析為協議，然後在訊息中的所有交換將遭都擱置，並沒有通知就會傳回，即使這些交換確實可解析為協議.</span><span class="sxs-lookup"><span data-stu-id="59c2e-115">If you enable authentication, and if any one interchange in the same message does not resolve to an agreement, then all interchanges in the message will be suspended, and no acknowledgments will be returned, even for those interchanges that did resolve to an agreement.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="59c2e-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="59c2e-116">Prerequisites</span></span>  
 <span data-ttu-id="59c2e-117">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="59c2e-117">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-enable-the-receiving-of-multiple-interchanges-in-a-message"></a><span data-ttu-id="59c2e-118">若要啟用接收單一訊息中的多重交換</span><span class="sxs-lookup"><span data-stu-id="59c2e-118">To enable the receiving of multiple interchanges in a message</span></span>  
  
1. <span data-ttu-id="59c2e-119">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下**接收位置**節點，以滑鼠右鍵按一下您要啟用成接收多個接收位置交換在單一訊息中，然後按一下  **屬性**。</span><span class="sxs-lookup"><span data-stu-id="59c2e-119">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click the **Receive Locations** node, right-click the receive location that you want to enable to receive multiple interchange in a single message, and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="59c2e-120">按一下接收管線 (必須是 EdiReceive 或 AS2EdiReceive) 旁的省略符號。</span><span class="sxs-lookup"><span data-stu-id="59c2e-120">Click the ellipses next to the receive pipeline (which must be either EdiReceive or AS2EdiReceive).</span></span>  
  
3. <span data-ttu-id="59c2e-121">在 [**設定管線**] 對話方塊中，將**DetectMID**管線屬性 **，則為 True**。</span><span class="sxs-lookup"><span data-stu-id="59c2e-121">In the **Configure Pipeline** dialog box, set the **DetectMID** pipeline property to **True**.</span></span>  
  
4. <span data-ttu-id="59c2e-122">按一下  **確定**，然後按一下**確定**一次。</span><span class="sxs-lookup"><span data-stu-id="59c2e-122">Click **OK**, then click **OK** again.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59c2e-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59c2e-123">See Also</span></span>  
 [<span data-ttu-id="59c2e-124">設定 EDI 解決方案的連接埠</span><span class="sxs-lookup"><span data-stu-id="59c2e-124">Configuring Ports for an EDI Solution</span></span>](../core/configuring-ports-for-an-edi-solution.md)