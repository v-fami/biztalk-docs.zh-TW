---
title: MLLP 接收和傳送元件 |Microsoft 文件
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
ms.openlocfilehash: e135b98c04531aa6200f3b79c5b6d5153bf299a7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25961077"
---
# <a name="mllp-receive-and-send-components"></a><span data-ttu-id="ddd2e-102">MLLP 接收和傳送元件</span><span class="sxs-lookup"><span data-stu-id="ddd2e-102">MLLP Receive and Send Components</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="ddd2e-103">BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 支援所有[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]原生配接器類型，包括 File、 HTTP、 SQL、 與 FTP。</span><span class="sxs-lookup"><span data-stu-id="ddd2e-103"> BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) supports all [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] native adapter types, including File, HTTP, SQL, and FTP.</span></span> <span data-ttu-id="ddd2e-104">HL7 編碼的訊息接收和傳送，不過，您通常使用 MLLP 配接器。</span><span class="sxs-lookup"><span data-stu-id="ddd2e-104">For HL7-encoded message receiving and sending, however, you typically use the MLLP adapter.</span></span> <span data-ttu-id="ddd2e-105">此配接器是使用最低限度的較低層通訊協定 (MLLP) 的 TCP/IP 通訊端介面卡。</span><span class="sxs-lookup"><span data-stu-id="ddd2e-105">This adapter is a TCP/IP socket adapter that uses the Minimal Lower Layer Protocol (MLLP).</span></span> <span data-ttu-id="ddd2e-106">此通訊協定提供雙向的訊息支援與端對端醫療保健應用程式整合。</span><span class="sxs-lookup"><span data-stu-id="ddd2e-106">This protocol provides bi-directional message support and end-to-end health care application integration.</span></span>  
  
 <span data-ttu-id="ddd2e-107">您可以設定 MLLP 為雙向配接器或單向配接器接收配接器。</span><span class="sxs-lookup"><span data-stu-id="ddd2e-107">You can configure the MLLP receive adapter as either a two-way adapter or a one-way adapter.</span></span> <span data-ttu-id="ddd2e-108">您可以設定 MLLP 傳送配接器，為雙向請求-回應傳送配接器、 單向傳送配接器設定為接收通知 (Ack) 上相同的通訊端連線，或單向傳送配接器不會傳回任何訊息。</span><span class="sxs-lookup"><span data-stu-id="ddd2e-108">You can configure the MLLP send adapter as a two-way solicit-response send adapter, a one-way send adapter configured to receive acknowledgments (ACKs) on the same socket connection, or a one-way send adapter that does not return any messages.</span></span> <span data-ttu-id="ddd2e-109">當您使用雙向請求-回應傳送 MLLP 配接器時，您可以設定要傳回 Ack 或回應訊息的接收埠。</span><span class="sxs-lookup"><span data-stu-id="ddd2e-109">When you use the two-way solicit-response send MLLP adapter, you can configure the receive port to return either ACKs or response messages.</span></span> <span data-ttu-id="ddd2e-110">如需為 MLLP 的範例傳送和接收配接器，請參閱[Interrogative 教學課程](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="ddd2e-110">For examples of MLLP send and receive adapters, see [Interrogative Tutorial](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md).</span></span>  
  
 <span data-ttu-id="ddd2e-111">訊息[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]接收或傳送的 MLLP 配接器上需要下列的包裝函式：</span><span class="sxs-lookup"><span data-stu-id="ddd2e-111">Messages that [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] receives or sends on an MLLP adapter require the following wrappers:</span></span>  
  
-   <span data-ttu-id="ddd2e-112">\<SB\>啟動區塊字元</span><span class="sxs-lookup"><span data-stu-id="ddd2e-112">\<SB\> Start Block character</span></span>  
  
-   <span data-ttu-id="ddd2e-113">\<EB\> End 區塊的字元</span><span class="sxs-lookup"><span data-stu-id="ddd2e-113">\<EB\> End Block character</span></span>  
  
-   <span data-ttu-id="ddd2e-114">\<CR\> （選擇性） 歸位字元傳回位元組</span><span class="sxs-lookup"><span data-stu-id="ddd2e-114">\<CR\> Carriage Return Byte (optional)</span></span>  
  
 <span data-ttu-id="ddd2e-115">MLLP 配接器會提供錯誤處理遺漏\<SB\>或\<EB\>包裝函式、 卸除的連接或逾時。</span><span class="sxs-lookup"><span data-stu-id="ddd2e-115">MLLP adapters provide error handling for missing \<SB\> or \<EB\> wrappers, dropped connections, or timeouts.</span></span> <span data-ttu-id="ddd2e-116">與 MLLP 配接器，您可以設定限制的連線數目。</span><span class="sxs-lookup"><span data-stu-id="ddd2e-116">With an MLLP adapter, you can configure a limitation on the number of connections.</span></span> <span data-ttu-id="ddd2e-117">您可以使用 MLLP 配接器的通知分類。</span><span class="sxs-lookup"><span data-stu-id="ddd2e-117">You can use an assortment of acknowledgments with an MLLP adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddd2e-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="ddd2e-118">See Also</span></span>  
 <span data-ttu-id="ddd2e-119">[處理 MLLP 編碼訊息](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md) </span><span class="sxs-lookup"><span data-stu-id="ddd2e-119">[Processing MLLP-encoded Messages](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md) </span></span>  
 [<span data-ttu-id="ddd2e-120">BizTalk Accelerator for HL7 元件</span><span class="sxs-lookup"><span data-stu-id="ddd2e-120">BizTalk Accelerator for HL7 Components</span></span>](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md)