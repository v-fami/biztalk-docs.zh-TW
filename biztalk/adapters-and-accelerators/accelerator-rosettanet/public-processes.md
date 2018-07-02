---
title: 公開程序 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- public processes, orchestrations
- business processes, public processes
- public processes, trading partners
- BTARN, public processes
- orchestrations, public-process orchestrations
- public processes
- trading partners, public processes
- public processes, about public processes
ms.assetid: 5ccc7449-5741-4d49-beb6-567bcd93f679
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f9d0288defa0705c7e12f102011edbf9ee7e90d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984719"
---
# <a name="public-processes"></a><span data-ttu-id="c964d-102">公開程序</span><span class="sxs-lookup"><span data-stu-id="c964d-102">Public Processes</span></span>
<span data-ttu-id="c964d-103">Microsoft[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]實作商務程序牽涉到與交易夥伴的公開程序整合。</span><span class="sxs-lookup"><span data-stu-id="c964d-103">Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] implements business processes that involve integration with trading partners as public processes.</span></span> <span data-ttu-id="c964d-104">並將組織內部的商務程序實作為私用程序。</span><span class="sxs-lookup"><span data-stu-id="c964d-104">It implements business processes that are internal to an organization as private processes.</span></span> <span data-ttu-id="c964d-105">使用公開程序和私用程序，會將 RosettaNet 實作架構 (RNIF) 處理 (在公開程序中) 從服務內容處理及後端整合 (在私用程序中) 隔離出來。</span><span class="sxs-lookup"><span data-stu-id="c964d-105">Using public and private processes isolates RosettaNet Implementation Framework (RNIF) handling (in the public process) from the service content processing and back-end integration (in the private process).</span></span>  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="c964d-106"> 會實作公開程序做為長期執行的 BizTalk 協調流程。</span><span class="sxs-lookup"><span data-stu-id="c964d-106"> implements public processes as long-running BizTalk orchestrations.</span></span> <span data-ttu-id="c964d-107">一個公開程序協調流程會在啟動者端執行，另一個則是在回應者端執行。</span><span class="sxs-lookup"><span data-stu-id="c964d-107">One public-process orchestration runs on the initiator side and one on the responder side.</span></span> <span data-ttu-id="c964d-108">[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 安裝程式為 RNIF 1.1 與 RNIF 2.01 都提供了啟動者及回應者公開程序協調流程版本。</span><span class="sxs-lookup"><span data-stu-id="c964d-108">The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Setup program provides versions of the initiator and responder public-process orchestrations for both RNIF 1.1 and RNIF 2.01.</span></span>  
  
 <span data-ttu-id="c964d-109">這些公開程序協調流程會實作所有的 RNIF 程序。</span><span class="sxs-lookup"><span data-stu-id="c964d-109">These public-process orchestrations implement all RNIF processes.</span></span> <span data-ttu-id="c964d-110">公開程序對其餘的元件隱藏了 RNIF 的複雜性。</span><span class="sxs-lookup"><span data-stu-id="c964d-110">Public processes hide the complexity of RNIF from the rest of the components.</span></span> <span data-ttu-id="c964d-111">公開程序除了強制執行 RNIF 相容的訊息流程之外，也會決定預設追蹤設定，並提供執行階段的程序狀態資訊，</span><span class="sxs-lookup"><span data-stu-id="c964d-111">Besides enforcing the RNIF-compliant message flow, the public process also determines default-tracking settings and provides process state information at run time.</span></span> <span data-ttu-id="c964d-112">但不會處理訊息的服務內容。</span><span class="sxs-lookup"><span data-stu-id="c964d-112">It does not process the service content of a message.</span></span> <span data-ttu-id="c964d-113">這種工作是由私用程序執行。</span><span class="sxs-lookup"><span data-stu-id="c964d-113">The private process does this.</span></span>  
  
 <span data-ttu-id="c964d-114">每個交易夥伴協議都會參考單一公開程序，以啟動或回應交易夥伴介面程序 (PIP) 動作。</span><span class="sxs-lookup"><span data-stu-id="c964d-114">Each trading partner agreement references a single public process to initiate or respond to Partner Interface Process (PIP) actions.</span></span> <span data-ttu-id="c964d-115">不過，公開程序無法確認 PIP 是否存在。</span><span class="sxs-lookup"><span data-stu-id="c964d-115">However, the public processes are PIP-agnostic.</span></span>  
  
 <span data-ttu-id="c964d-116">RosettaNet 規格規定了公開程序的設計。</span><span class="sxs-lookup"><span data-stu-id="c964d-116">The RosettaNet specifications dictate the design of the public process.</span></span> <span data-ttu-id="c964d-117">建議您不要修改公開程序。</span><span class="sxs-lookup"><span data-stu-id="c964d-117">It is recommended that you do not modify a public process.</span></span> <span data-ttu-id="c964d-118">公開程序協調流程已建立版本並經過簽署。</span><span class="sxs-lookup"><span data-stu-id="c964d-118">The public-process orchestration is versioned and signed.</span></span> <span data-ttu-id="c964d-119">如果修改公開程序，就不再與 RNIF 相容。</span><span class="sxs-lookup"><span data-stu-id="c964d-119">If you modify a public process, it will no longer be RNIF-compliant.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c964d-120">本節內容</span><span class="sxs-lookup"><span data-stu-id="c964d-120">In This Section</span></span>  
  
-   [<span data-ttu-id="c964d-121">啟動者公開程序</span><span class="sxs-lookup"><span data-stu-id="c964d-121">Initiator Public Process</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/initiator-public-process.md)  
  
-   [<span data-ttu-id="c964d-122">回應者公開程序</span><span class="sxs-lookup"><span data-stu-id="c964d-122">Responder Public Process</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/responder-public-process.md)