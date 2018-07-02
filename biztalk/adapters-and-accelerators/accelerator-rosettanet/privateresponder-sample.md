---
title: PrivateResponder 範例 |Microsoft Docs
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
ms.openlocfilehash: f2e44157c1b7a4e545bad23c5d9b6dcd9fa87cfe
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986863"
---
# <a name="privateresponder-sample"></a><span data-ttu-id="c70cf-102">PrivateResponder 範例</span><span class="sxs-lookup"><span data-stu-id="c70cf-102">PrivateResponder Sample</span></span>
<span data-ttu-id="c70cf-103">PrivateResponder.odx 範例包含安裝 Microsoft® 回應者私用程序的程式碼[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c70cf-103">The PrivateResponder.odx sample contains the code for the responder private process installed by Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].</span></span> <span data-ttu-id="c70cf-104">這個一般私用程序會從預設 SQL 配接器架構的傳送埠和接收埠，傳送和接收 RNIF 服務內容訊息。</span><span class="sxs-lookup"><span data-stu-id="c70cf-104">This generic private process sends and receives RNIF service-content messages from the default SQL adapter-based send and receive ports.</span></span>  
  
 <span data-ttu-id="c70cf-105">根據預設，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]安裝程式安裝中的範例\<*磁碟機*>: \Program Files\\Microsoft BizTalk\<版本 > Accelerator for RosettaNet\SDK\PrivateResponder。</span><span class="sxs-lookup"><span data-stu-id="c70cf-105">By default, the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Setup program installs the sample in \<*drive*>:\Program Files\\Microsoft  BizTalk \<version> Accelerator for RosettaNet\SDK\PrivateResponder.</span></span>  
  
## <a name="sample-contents"></a><span data-ttu-id="c70cf-106">範例內容</span><span class="sxs-lookup"><span data-stu-id="c70cf-106">Sample Contents</span></span>  
 <span data-ttu-id="c70cf-107">回應者私用程序屬於回應者的內部商務程序。</span><span class="sxs-lookup"><span data-stu-id="c70cf-107">The responder private process is the business process that is internal to the responder.</span></span> <span data-ttu-id="c70cf-108">私用程序能讓回應者公開程序和後端商務營運系統程式進行後端整合。</span><span class="sxs-lookup"><span data-stu-id="c70cf-108">The private process provides back-end integration between the responder public process and the back-end line-of-business program.</span></span> <span data-ttu-id="c70cf-109">回應者私用程序會與公開程序進行通訊，以回應訊息。</span><span class="sxs-lookup"><span data-stu-id="c70cf-109">The responder private process communicates with the public process to respond to messages.</span></span>  
  
 <span data-ttu-id="c70cf-110">回應者私用程序對於每個實作而言都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="c70cf-110">The responder private process is unique for each implementation.</span></span> <span data-ttu-id="c70cf-111">您可以依照您的目的自訂 PrivateResponder.odx 範例。</span><span class="sxs-lookup"><span data-stu-id="c70cf-111">You can customize the PrivateResponder.odx sample for your purposes.</span></span> <span data-ttu-id="c70cf-112">但是您必須小心，不要對回應者公開程序的功能造成不良影響。</span><span class="sxs-lookup"><span data-stu-id="c70cf-112">You must be careful that you do not adversely affect the functioning of the responder public process.</span></span>  
  
 <span data-ttu-id="c70cf-113">如需詳細資訊，包括訊息流程的描述，請參閱[回應者私用程序](../../adapters-and-accelerators/accelerator-rosettanet/responder-private-process.md)。</span><span class="sxs-lookup"><span data-stu-id="c70cf-113">For more information, including a description of the message flow, see [Responder Private Process](../../adapters-and-accelerators/accelerator-rosettanet/responder-private-process.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c70cf-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c70cf-114">See Also</span></span>  
 <span data-ttu-id="c70cf-115">[協調流程範例](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md) </span><span class="sxs-lookup"><span data-stu-id="c70cf-115">[Orchestration Samples](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md) </span></span>  
 [<span data-ttu-id="c70cf-116">私用程序</span><span class="sxs-lookup"><span data-stu-id="c70cf-116">Private Processes</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/private-processes.md)