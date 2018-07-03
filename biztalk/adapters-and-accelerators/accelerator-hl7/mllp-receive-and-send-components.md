---
title: MLLP 接收和傳送元件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- send components
- Minimal Lower Layer Protocol (MLLP)
- MLLP adapters
- MLLP adapters, wrappers
- wrappers [MLLP adapters]
- receive components
ms.assetid: 2f1c4099-8f52-437a-bdc1-efe707fbf347
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0eebc51d23c66fb9dd7047f29982fbcc05a8215f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971799"
---
# <a name="mllp-receive-and-send-components"></a><span data-ttu-id="b99fe-102">MLLP 接收和傳送元件</span><span class="sxs-lookup"><span data-stu-id="b99fe-102">MLLP Receive and Send Components</span></span>
<span data-ttu-id="b99fe-103">Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 支援所有的 Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]原生配接器類型，包括檔案、 HTTP、 SQL 和 FTP。</span><span class="sxs-lookup"><span data-stu-id="b99fe-103">Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) supports all Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] native adapter types, including File, HTTP, SQL, and FTP.</span></span> <span data-ttu-id="b99fe-104">HL7 編碼的訊息接收和傳送，不過，您通常使用 MLLP 配接器。</span><span class="sxs-lookup"><span data-stu-id="b99fe-104">For HL7-encoded message receiving and sending, however, you typically use the MLLP adapter.</span></span> <span data-ttu-id="b99fe-105">此配接器是使用最低限度的較低層通訊協定 (MLLP) 的 TCP/IP 通訊端介面卡。</span><span class="sxs-lookup"><span data-stu-id="b99fe-105">This adapter is a TCP/IP socket adapter that uses the Minimal Lower Layer Protocol (MLLP).</span></span> <span data-ttu-id="b99fe-106">此通訊協定提供雙向訊息支援和端對端醫療保健應用程式整合。</span><span class="sxs-lookup"><span data-stu-id="b99fe-106">This protocol provides bi-directional message support and end-to-end health care application integration.</span></span>  
  
 <span data-ttu-id="b99fe-107">您可以設定 MLLP 接收配接器是雙向的介面卡或單向的配接器。</span><span class="sxs-lookup"><span data-stu-id="b99fe-107">You can configure the MLLP receive adapter as either a two-way adapter or a one-way adapter.</span></span> <span data-ttu-id="b99fe-108">您可以設定 MLLP 傳送配接器，如雙向請求-回應傳送配接器、 單向傳送配接器設定為相同的通訊端連線，接收通知 (Ack) 或單向傳送配接器不會傳回任何訊息。</span><span class="sxs-lookup"><span data-stu-id="b99fe-108">You can configure the MLLP send adapter as a two-way solicit-response send adapter, a one-way send adapter configured to receive acknowledgments (ACKs) on the same socket connection, or a one-way send adapter that does not return any messages.</span></span> <span data-ttu-id="b99fe-109">當您使用雙向請求-回應傳送 MLLP 配接器時，您可以設定要傳回 Ack 或回應訊息的接收埠。</span><span class="sxs-lookup"><span data-stu-id="b99fe-109">When you use the two-way solicit-response send MLLP adapter, you can configure the receive port to return either ACKs or response messages.</span></span> <span data-ttu-id="b99fe-110">範例為 MLLP 傳送與接收配接器，請參閱[詢問式教學課程](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="b99fe-110">For examples of MLLP send and receive adapters, see [Interrogative Tutorial](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md).</span></span>  
  
 <span data-ttu-id="b99fe-111">訊息[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]接收或傳送的 MLLP 配接器上需要下列的包裝函式：</span><span class="sxs-lookup"><span data-stu-id="b99fe-111">Messages that [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] receives or sends on an MLLP adapter require the following wrappers:</span></span>  
  
- <span data-ttu-id="b99fe-112">\<SB\>開始區塊的字元</span><span class="sxs-lookup"><span data-stu-id="b99fe-112">\<SB\> Start Block character</span></span>  
  
- <span data-ttu-id="b99fe-113">\<EB\> End 區塊的字元</span><span class="sxs-lookup"><span data-stu-id="b99fe-113">\<EB\> End Block character</span></span>  
  
- <span data-ttu-id="b99fe-114">\<CR\>歸位字元傳回的位元組 （選擇性）</span><span class="sxs-lookup"><span data-stu-id="b99fe-114">\<CR\> Carriage Return Byte (optional)</span></span>  
  
  <span data-ttu-id="b99fe-115">MLLP 配接器會提供錯誤處理遺漏\<SB\>或是\<EB\>包裝函式、 中斷的連線或逾時。</span><span class="sxs-lookup"><span data-stu-id="b99fe-115">MLLP adapters provide error handling for missing \<SB\> or \<EB\> wrappers, dropped connections, or timeouts.</span></span> <span data-ttu-id="b99fe-116">使用 MLLP 配接器，您可以設定限制連線數目。</span><span class="sxs-lookup"><span data-stu-id="b99fe-116">With an MLLP adapter, you can configure a limitation on the number of connections.</span></span> <span data-ttu-id="b99fe-117">您可以使用 MLLP 配接器的通知分類。</span><span class="sxs-lookup"><span data-stu-id="b99fe-117">You can use an assortment of acknowledgments with an MLLP adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b99fe-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b99fe-118">See Also</span></span>  
 <span data-ttu-id="b99fe-119">[處理 MLLP 編碼訊息](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md) </span><span class="sxs-lookup"><span data-stu-id="b99fe-119">[Processing MLLP-encoded Messages](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md) </span></span>  
 [<span data-ttu-id="b99fe-120">BizTalk Accelerator for HL7 元件</span><span class="sxs-lookup"><span data-stu-id="b99fe-120">BizTalk Accelerator for HL7 Components</span></span>](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md)