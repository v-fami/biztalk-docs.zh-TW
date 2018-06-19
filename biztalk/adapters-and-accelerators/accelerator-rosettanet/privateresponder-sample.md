---
title: PrivateResponder 範例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3137fadd-9582-4cc6-acfb-c44aca636950
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3de3428aa9971ba62b682494cd94c6bb74bcab53
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206942"
---
# <a name="privateresponder-sample"></a><span data-ttu-id="71a98-102">PrivateResponder 範例</span><span class="sxs-lookup"><span data-stu-id="71a98-102">PrivateResponder Sample</span></span>
<span data-ttu-id="71a98-103">PrivateResponder.odx 範例包含 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 所安裝之回應者私用程序的程式碼。</span><span class="sxs-lookup"><span data-stu-id="71a98-103">The PrivateResponder.odx sample contains the code for the responder private process installed by [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].</span></span> <span data-ttu-id="71a98-104">這個一般私用程序會從預設 SQL 配接器架構的傳送埠和接收埠，傳送和接收 RNIF 服務內容訊息。</span><span class="sxs-lookup"><span data-stu-id="71a98-104">This generic private process sends and receives RNIF service-content messages from the default SQL adapter-based send and receive ports.</span></span>  
  
 <span data-ttu-id="71a98-105">根據預設，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]安裝程式安裝中的範例\<*磁碟機*>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本 > Accelerator for RosettaNet\SDK\PrivateResponder。</span><span class="sxs-lookup"><span data-stu-id="71a98-105">By default, the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Setup program installs the sample in \<*drive*>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version> Accelerator for RosettaNet\SDK\PrivateResponder.</span></span>  
  
## <a name="sample-contents"></a><span data-ttu-id="71a98-106">範例內容</span><span class="sxs-lookup"><span data-stu-id="71a98-106">Sample Contents</span></span>  
 <span data-ttu-id="71a98-107">回應者私用程序屬於回應者的內部商務程序。</span><span class="sxs-lookup"><span data-stu-id="71a98-107">The responder private process is the business process that is internal to the responder.</span></span> <span data-ttu-id="71a98-108">私用程序能讓回應者公開程序和後端商務營運系統程式進行後端整合。</span><span class="sxs-lookup"><span data-stu-id="71a98-108">The private process provides back-end integration between the responder public process and the back-end line-of-business program.</span></span> <span data-ttu-id="71a98-109">回應者私用程序會與公開程序進行通訊，以回應訊息。</span><span class="sxs-lookup"><span data-stu-id="71a98-109">The responder private process communicates with the public process to respond to messages.</span></span>  
  
 <span data-ttu-id="71a98-110">回應者私用程序對於每個實作而言都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="71a98-110">The responder private process is unique for each implementation.</span></span> <span data-ttu-id="71a98-111">您可以依照您的目的自訂 PrivateResponder.odx 範例。</span><span class="sxs-lookup"><span data-stu-id="71a98-111">You can customize the PrivateResponder.odx sample for your purposes.</span></span> <span data-ttu-id="71a98-112">但是您必須小心，不要對回應者公開程序的功能造成不良影響。</span><span class="sxs-lookup"><span data-stu-id="71a98-112">You must be careful that you do not adversely affect the functioning of the responder public process.</span></span>  
  
 <span data-ttu-id="71a98-113">如需詳細資訊，包括訊息流程的描述，請參閱[回應者私用程序](../../adapters-and-accelerators/accelerator-rosettanet/responder-private-process.md)。</span><span class="sxs-lookup"><span data-stu-id="71a98-113">For more information, including a description of the message flow, see [Responder Private Process](../../adapters-and-accelerators/accelerator-rosettanet/responder-private-process.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71a98-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71a98-114">See Also</span></span>  
 <span data-ttu-id="71a98-115">[協調流程範例](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md) </span><span class="sxs-lookup"><span data-stu-id="71a98-115">[Orchestration Samples](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md) </span></span>  
 [<span data-ttu-id="71a98-116">私用程序</span><span class="sxs-lookup"><span data-stu-id="71a98-116">Private Processes</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/private-processes.md)