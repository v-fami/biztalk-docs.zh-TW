---
title: 反向處理直接夥伴繫結 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- bindings, partners
- process management solution tutorial, partner binding
ms.assetid: 4cf8717a-2098-46f4-8f58-9d05fb562e2a
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6c9fe5e51f9f63ea098fa623dafbceeb670e75f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262390"
---
# <a name="inverse-direct-partner-binding"></a><span data-ttu-id="cb385-102">反向處理直接夥伴繫結</span><span class="sxs-lookup"><span data-stu-id="cb385-102">Inverse Direct Partner Binding</span></span>
<span data-ttu-id="cb385-103">商務程序管理解決方案的設計，可讓您變更訂單處理階段而不必停止應用程式。</span><span class="sxs-lookup"><span data-stu-id="cb385-103">The Business Process Management solution is designed so that you can change the order processing stages without stopping the application.</span></span> <span data-ttu-id="cb385-104">為了減少處理階段 (**CableOrder1**， **CableOrder2**) 從處理序管理員 (**OrderManager**)，解決方案會使用針對不同的技術繫結這些協調流程之間的連接埠。</span><span class="sxs-lookup"><span data-stu-id="cb385-104">In order to decouple the processing stages (**CableOrder1**, **CableOrder2**) from the process manager (**OrderManager**), the solution uses a different technique for binding ports among these orchestrations.</span></span>  
  
 <span data-ttu-id="cb385-105">繫結的一般形式，指示繫結， **OrderManager**協調流程會使用處理階段協調流程做為值夥伴協調流程連接埠屬性。</span><span class="sxs-lookup"><span data-stu-id="cb385-105">In the usual form of binding, direct binding, the **OrderManager** orchestration would use the process stage orchestration as the value for the Partner Orchestration Port property.</span></span> <span data-ttu-id="cb385-106">像這樣的直接繫結中**OrderManager**協調流程會視強式名稱 （包含版本） 的處理階段。</span><span class="sxs-lookup"><span data-stu-id="cb385-106">In direct binding like this the **OrderManager** orchestration depends on the strong names (which include the versions) of the process stages.</span></span> <span data-ttu-id="cb385-107">這使得無法改變處理階段，而不需重新部署**OrderManager**協調流程。</span><span class="sxs-lookup"><span data-stu-id="cb385-107">This makes it impossible to alter the process stages without re-deploying the **OrderManager** orchestration.</span></span> <span data-ttu-id="cb385-108">如需直接繫結的詳細資訊，請參閱[連接埠繫結](../core/port-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="cb385-108">For more information about direct binding, see [Port Bindings](../core/port-bindings.md).</span></span> <span data-ttu-id="cb385-109">直接繫結可用以下方式來說明：</span><span class="sxs-lookup"><span data-stu-id="cb385-109">Direct Binding might be illustrated this way:</span></span>  
  
 <span data-ttu-id="cb385-110">![反向處理直接夥伴繫結的圖表](../core/media/bpm-inverse-direct-binding.gif "BPM_Inverse_Direct_Binding")</span><span class="sxs-lookup"><span data-stu-id="cb385-110">![Diagram of Inverse Direct Partner Binding](../core/media/bpm-inverse-direct-binding.gif "BPM_Inverse_Direct_Binding")</span></span>  
  
 <span data-ttu-id="cb385-111">在反向處理直接夥伴繫結中，接收協調流程會指定繫結，而不是原始的協調流程。</span><span class="sxs-lookup"><span data-stu-id="cb385-111">In inverse direct partner binding, the receiving orchestration specifies the binding, rather than the originating orchestration.</span></span> <span data-ttu-id="cb385-112">上的連接埠**OrderManager**只會繫結至本身。</span><span class="sxs-lookup"><span data-stu-id="cb385-112">The port on the **OrderManager** is simply bound to itself.</span></span> <span data-ttu-id="cb385-113">也就是在連接埠**OrderManager**指定**PartnerOrchestrationPort**屬性。</span><span class="sxs-lookup"><span data-stu-id="cb385-113">That is, the port on the **OrderManager** is specified for the **PartnerOrchestrationPort** property.</span></span> <span data-ttu-id="cb385-114">不過，處理階段協調流程會使用適合**OrderManager**做為值的連接埠**PartnerOrchestrationPort**屬性。</span><span class="sxs-lookup"><span data-stu-id="cb385-114">However, the process stage orchestrations use the appropriate **OrderManager** port as the value for the **PartnerOrchestrationPort** property.</span></span> <span data-ttu-id="cb385-115">如此即可減少**OrderManager**來自處理階段協調流程的版本，並讓他們變更，而不重新部署**OrderManager**。</span><span class="sxs-lookup"><span data-stu-id="cb385-115">This decouples the **OrderManager** from the versions of the process stage orchestrations and allows them to be changed without redeploying the **OrderManager**.</span></span> <span data-ttu-id="cb385-116">直接繫結不允許此種減少方式。</span><span class="sxs-lookup"><span data-stu-id="cb385-116">Direct binding would not allow this decoupling.</span></span> <span data-ttu-id="cb385-117">反向處理直接夥伴繫結可以下列方式顯示：</span><span class="sxs-lookup"><span data-stu-id="cb385-117">Inverse direct partner binding might be shown this way:</span></span>  
  
 <span data-ttu-id="cb385-118">![直接繫結的圖表](../core/media/bpm-direct-binding.gif "BPM_Direct_Binding")</span><span class="sxs-lookup"><span data-stu-id="cb385-118">![Diagram of Direct Binding](../core/media/bpm-direct-binding.gif "BPM_Direct_Binding")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb385-119">反向處理直接繫結也允許以類似通訊群組清單的方式，與夥伴協調流程通訊。</span><span class="sxs-lookup"><span data-stu-id="cb385-119">Inverse direct binding also allows for communicating with partner orchestrations in a distribution-list like way.</span></span> <span data-ttu-id="cb385-120">**OrderManger**可以使用單一連接埠與所有階段通訊。</span><span class="sxs-lookup"><span data-stu-id="cb385-120">The **OrderManger** can use a single port to communicate with all stages.</span></span> <span data-ttu-id="cb385-121">這讓您可以新增和移除階段，而不必重新設計協調流程。</span><span class="sxs-lookup"><span data-stu-id="cb385-121">This enables you to add and remove stages without redesigning the orchestration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb385-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb385-122">See Also</span></span>  
 <span data-ttu-id="cb385-123">[商務程序管理解決方案的實作重點](../core/implementation-highlights-of-the-business-process-management-solution.md) </span><span class="sxs-lookup"><span data-stu-id="cb385-123">[Implementation Highlights of the Business Process Management Solution](../core/implementation-highlights-of-the-business-process-management-solution.md) </span></span>  
 [<span data-ttu-id="cb385-124">程序管理員邏輯</span><span class="sxs-lookup"><span data-stu-id="cb385-124">Process Manager Logic</span></span>](../core/process-manager-logic.md)