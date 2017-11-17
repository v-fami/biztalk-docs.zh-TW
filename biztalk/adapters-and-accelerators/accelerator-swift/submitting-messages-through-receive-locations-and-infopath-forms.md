---
title: "提交訊息到接收位置和 InfoPath 表單 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, receive locations
- receive locations, messages
- messages, InfoPath forms
- InfoPath forms, messages
ms.assetid: e8676830-3fbc-423f-82f6-03e6a532075f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6cddeca2eb80fbeb7c9fb5742e2838a860079d6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="submitting-messages-through-receive-locations-and-infopath-forms"></a><span data-ttu-id="b5558-102">正在提交訊息到接收位置和 InfoPath 表單</span><span class="sxs-lookup"><span data-stu-id="b5558-102">Submitting Messages Through Receive Locations and InfoPath Forms</span></span>
<span data-ttu-id="b5558-103">接收位置接收訊息提交到[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="b5558-103">Receive locations receive messages for submission into [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] applications.</span></span> <span data-ttu-id="b5558-104">您可以定義為實體的端點來接收訊息，使用指定的傳輸通訊協定設定的接收位置。</span><span class="sxs-lookup"><span data-stu-id="b5558-104">You can define receive locations as physical endpoints configured to receive messages using a specified transport protocol.</span></span> <span data-ttu-id="b5558-105">例如，接收位置可能設定接收檔案放到 使用檔案傳輸特定的檔案系統資料夾。</span><span class="sxs-lookup"><span data-stu-id="b5558-105">For example, a receive location may be configured to receive files dropped to a particular file system folder using the FILE transport.</span></span>  
  
 <span data-ttu-id="b5558-106">您建立以邏輯方式分組和管理接收埠接收位置的接收位置。</span><span class="sxs-lookup"><span data-stu-id="b5558-106">You create receive locations for receive ports that logically group and manage receive locations.</span></span> <span data-ttu-id="b5558-107">針對每個接收位置，您會指定接收管線，並在該特定接收位置接收訊息的實際處理 （解碼、 解譯、 驗證，等等）。</span><span class="sxs-lookup"><span data-stu-id="b5558-107">For each receive location you specify a receive pipeline, which does the actual processing (decoding, disassembly, validation, and so on) of messages received at that particular receive location.</span></span> <span data-ttu-id="b5558-108">A4SWIFT 繫結接收位置接收連接埠，以邏輯方式分組和管理接收位置。</span><span class="sxs-lookup"><span data-stu-id="b5558-108">A4SWIFT binds receive locations to receive ports that logically group and manage receive locations.</span></span>  
  
 <span data-ttu-id="b5558-109">若要提交 SWIFT 訊息透過接收位置的 A4SWIFT 應用程式，必須是卸除設定的接收位置、 使用 SWIFT 解譯器的接收管線處理、 剖析和驗證訊息 SWIFT 的解譯器，並發佈至 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="b5558-109">To submit a SWIFT message into an A4SWIFT application through a receive location, the message must be dropped to a configured receive location, processed by a receive pipeline using the SWIFT disassembler, parsed and validated by the SWIFT disassembler, and published to the MessageBox database.</span></span> <span data-ttu-id="b5558-110">訊息發佈到 MessageBox 資料庫之後，A4SWIFT 應用程式中的其他元件就會擷取 （使用訂用帳戶） 訊息進行其他處理。</span><span class="sxs-lookup"><span data-stu-id="b5558-110">After messages are published to the MessageBox database, other components in your A4SWIFT application retrieve the messages (using subscriptions) for additional processing.</span></span> <span data-ttu-id="b5558-111">例如，您可以使用傳送埠的最後一個路由。</span><span class="sxs-lookup"><span data-stu-id="b5558-111">For example, you can use send ports for final routing.</span></span>  
  
 <span data-ttu-id="b5558-112">如需有關建立和設定接收埠和接收位置，請參閱[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="b5558-112">For more information about creating and configuring receive ports and receive locations, see [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
 <span data-ttu-id="b5558-113">您也可以提交新的訊息，透過[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]形成，請使用 Message Repair 和 New Submission 功能。</span><span class="sxs-lookup"><span data-stu-id="b5558-113">You can also submit a new message through an [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form, using the Message Repair and New Submission feature.</span></span> <span data-ttu-id="b5558-114">若要這樣做，請您開啟[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單從 MRSR 網站中的資料夾，該訊息。</span><span class="sxs-lookup"><span data-stu-id="b5558-114">To do so, you open the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form for that message from a folder in the MRSR site.</span></span> <span data-ttu-id="b5558-115">您在中的資料填入[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]形成、 您的憑證進行簽署，然後提交它。</span><span class="sxs-lookup"><span data-stu-id="b5558-115">You fill in the data in the [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] form, sign it using your certificate, and then submit it.</span></span> <span data-ttu-id="b5558-116">Message Repair 和 New Submission 協調流程處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="b5558-116">The Message Repair and New Submission orchestration processes the message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5558-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5558-117">See Also</span></span>  
 [<span data-ttu-id="b5558-118">BizTalk Accelerator for SWIFT 的執行階段</span><span class="sxs-lookup"><span data-stu-id="b5558-118">BizTalk Accelerator for SWIFT Runtime</span></span>](../../adapters-and-accelerators/accelerator-swift/biztalk-accelerator-for-swift-runtime.md)