---
title: "PrivateInitiator 範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f176566-2a71-487d-84c1-5e7767701e8b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 55d33b164033cdd3b966ed1f0e77dd551cd56076
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="privateinitiator-sample"></a><span data-ttu-id="a6e99-102">PrivateInitiator 範例</span><span class="sxs-lookup"><span data-stu-id="a6e99-102">PrivateInitiator Sample</span></span>
<span data-ttu-id="a6e99-103">PrivateInitiator.odx 範例包含 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] 所安裝之啟動者私用程序的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a6e99-103">The PrivateInitiator.odx sample contains the code for the initiator private process installed by [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].</span></span> <span data-ttu-id="a6e99-104">這是會從預設 SQL 配接器架構的傳送埠和接收埠，傳送和接收 RNIF 服務內容訊息的一般私用程序。</span><span class="sxs-lookup"><span data-stu-id="a6e99-104">This is a generic private process that sends and receives RNIF service-content messages from the default SQL adapter-based send and receive ports.</span></span>  
  
 <span data-ttu-id="a6e99-105">根據預設，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]安裝程式安裝中的範例\<*磁碟機*>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本 > Accelerator for RosettaNet\SDK\PrivateInitiator。</span><span class="sxs-lookup"><span data-stu-id="a6e99-105">By default, the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Setup program installs the sample in \<*drive*>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version> Accelerator for RosettaNet\SDK\PrivateInitiator.</span></span>  
  
## <a name="sample-contents"></a><span data-ttu-id="a6e99-106">範例內容</span><span class="sxs-lookup"><span data-stu-id="a6e99-106">Sample Contents</span></span>  
 <span data-ttu-id="a6e99-107">啟動者私用程序屬於啟動者的內部商務程序。</span><span class="sxs-lookup"><span data-stu-id="a6e99-107">The initiator private process is the business process that is internal to the initiator.</span></span> <span data-ttu-id="a6e99-108">私用程序能讓啟動者公開程序和後端商務營運系統程式進行後端整合。</span><span class="sxs-lookup"><span data-stu-id="a6e99-108">The private process provides back-end integration between the initiator public process and the back-end line-of-business program.</span></span> <span data-ttu-id="a6e99-109">啟動者私用程序會與公開程序進行通訊，以初始化訊息。</span><span class="sxs-lookup"><span data-stu-id="a6e99-109">The initiator private process communicates with the public process to initiate messages.</span></span>  
  
 <span data-ttu-id="a6e99-110">啟動者私用程序對於每個實作而言都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="a6e99-110">The initiator private process is unique for each implementation.</span></span> <span data-ttu-id="a6e99-111">您可以依照您的目的自訂 PrivateInitiator.odx 範例。</span><span class="sxs-lookup"><span data-stu-id="a6e99-111">You can customize the PrivateInitiator.odx sample for your purposes.</span></span> <span data-ttu-id="a6e99-112">但是您必須小心，不要對啟動者公開程序的功能造成不良影響。</span><span class="sxs-lookup"><span data-stu-id="a6e99-112">You must be careful that you do not adversely affect the functioning of the initiator public process.</span></span>  
  
 <span data-ttu-id="a6e99-113">如需詳細資訊，包括訊息流程的描述，請參閱[啟動者私用程序](../../adapters-and-accelerators/accelerator-rosettanet/initiator-private-process.md)。</span><span class="sxs-lookup"><span data-stu-id="a6e99-113">For more information, including a description of the message flow, see [Initiator Private Process](../../adapters-and-accelerators/accelerator-rosettanet/initiator-private-process.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6e99-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6e99-114">See Also</span></span>  
 <span data-ttu-id="a6e99-115">[協調流程範例](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md) </span><span class="sxs-lookup"><span data-stu-id="a6e99-115">[Orchestration Samples](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md) </span></span>  
 [<span data-ttu-id="a6e99-116">私用程序</span><span class="sxs-lookup"><span data-stu-id="a6e99-116">Private Processes</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/private-processes.md)