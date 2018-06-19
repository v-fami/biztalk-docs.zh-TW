---
title: 執行 BizTalk Server 之電腦的災害復原 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10a2c26d-55d5-45d1-9fb1-e0664f005c21
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b0ca86ef9a412514fdf3f30f0a38cbac710e0f59
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26005223"
---
# <a name="disaster-recovery-for-computers-running-biztalk-server"></a><span data-ttu-id="e7427-102">執行 BizTalk Server 的電腦的嚴重損毀修復</span><span class="sxs-lookup"><span data-stu-id="e7427-102">Disaster Recovery for Computers Running BizTalk Server</span></span>
<span data-ttu-id="e7427-103">如果在您的組織中，執行 BizTalk Server 的電腦遇到無法復原的硬體失敗問題，您應該更換一台相同的電腦。</span><span class="sxs-lookup"><span data-stu-id="e7427-103">If the computer running BizTalk Server in your organization suffers an unrecoverable hardware failure, you should replace it with an identical computer.</span></span> <span data-ttu-id="e7427-104">這麼做是假設 BizTalk Server 資料庫仍然完整，而此次失敗是發生在其中一台執行 BizTalk Server 的電腦上。</span><span class="sxs-lookup"><span data-stu-id="e7427-104">This assumes that the BizTalk Server databases are intact, and that the failure is in any one of the computers running BizTalk Server.</span></span>  
  
 <span data-ttu-id="e7427-105">有一個可行方式，即是在安裝時維護每一台執行 BizTalk Server 的電腦的更新映像。</span><span class="sxs-lookup"><span data-stu-id="e7427-105">One possible approach is to maintain an updated image of every computer running BizTalk Server in your installation.</span></span> <span data-ttu-id="e7427-106">當電腦遇到硬體失敗的問題時，復原動作就像在新電腦上部署儲存的映像一樣簡單。</span><span class="sxs-lookup"><span data-stu-id="e7427-106">When a computer suffers a hardware failure, the recovery action is as simple as deploying the stored image on a new computer.</span></span> <span data-ttu-id="e7427-107">本損毀修復主題主要是針對無法儲存這類映像的狀況進行處理。</span><span class="sxs-lookup"><span data-stu-id="e7427-107">The disaster recovery topics address the case where storing such images is not feasible.</span></span>  
## <a name="recovering-different-editions-of-biztalk-server"></a><span data-ttu-id="e7427-108">復原不同版本的 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="e7427-108">Recovering Different Editions of BizTalk Server</span></span>  
 <span data-ttu-id="e7427-109">復原方式會因電腦執行的 BizTalk Server 版本不同而有所不同。</span><span class="sxs-lookup"><span data-stu-id="e7427-109">The recovery approach is different depending on the edition of BizTalk Server running on the computer.</span></span>  
  
 <span data-ttu-id="e7427-110">BizTalk Server Developer Edition 和 BizTalk Server Enterprise Edition、 多部電腦執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]允許。</span><span class="sxs-lookup"><span data-stu-id="e7427-110">For BizTalk Server Developer Edition and BizTalk Server Enterprise Edition, multiple computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] are permitted.</span></span> <span data-ttu-id="e7427-111">當其中一台執行 BizTalk Server 的電腦無法正常運作時，您可以準備替換的電腦，並將它加入現有的 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="e7427-111">When one of the computers running BizTalk Server fails, you can prepare a replacement computer and join it to the existing BizTalk group.</span></span> <span data-ttu-id="e7427-112">此時，您可以將相同名稱或不同名稱的電腦加入 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="e7427-112">In this case, you can join a computer with either the same name or a different name to the BizTalk group.</span></span>  
  
 <span data-ttu-id="e7427-113">為 BizTalk Server Standard Edition，您無法將電腦加入 BizTalk 群組中，因此上述的方法不適合。</span><span class="sxs-lookup"><span data-stu-id="e7427-113">For BizTalk Server Standard Edition, you cannot join the computer to a BizTalk group, so the above approach is not suitable.</span></span> <span data-ttu-id="e7427-114">相反地，我們概述設定新的電腦和還原所需的步驟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態設定，讓它可以做為替代函式。</span><span class="sxs-lookup"><span data-stu-id="e7427-114">Instead, we outline the steps needed to set up a new computer and restore the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration settings so that it can function as a replacement.</span></span> <span data-ttu-id="e7427-115">如需詳細資訊，請參閱[如何復原 BizTalk 群組](../core/how-to-recover-the-biztalk-group.md)。</span><span class="sxs-lookup"><span data-stu-id="e7427-115">For more information, see [How to Recover the BizTalk Group](../core/how-to-recover-the-biztalk-group.md).</span></span>  
  
## <a name="recovery-phases"></a><span data-ttu-id="e7427-116">復原階段</span><span class="sxs-lookup"><span data-stu-id="e7427-116">Recovery Phases</span></span>  
 <span data-ttu-id="e7427-117">對執行 BizTalk Server 的電腦進行復原，可以分為下列三個階段：</span><span class="sxs-lookup"><span data-stu-id="e7427-117">The recovery of a computer running BizTalk Server can be classified into the following three phases:</span></span>  
  
1.  <span data-ttu-id="e7427-118">**準備基底平台**</span><span class="sxs-lookup"><span data-stu-id="e7427-118">**Preparing the Base Platform**</span></span>  
  
     <span data-ttu-id="e7427-119">這個階段包括基底平台電腦的準備工作，準備的項目包括作業系統、軟體必要元件和適當的 BizTalk Server 元件。</span><span class="sxs-lookup"><span data-stu-id="e7427-119">This phase includes the preparation of a computer with the base platform including the operating system, software prerequisites and appropriate BizTalk Server components.</span></span> <span data-ttu-id="e7427-120">這份指南假設您在嘗試還原 BizTalk Server 組態之前，已經有一台安裝了基底平台、必要元件和 BizTalk Server 元件的電腦。</span><span class="sxs-lookup"><span data-stu-id="e7427-120">This guide assumes that before you attempt to restore the BizTalk Server configuration, you have a computer with the base platform, prerequisites, and BizTalk Server components installed.</span></span> <span data-ttu-id="e7427-121">本指南沒有說明如何還原基底平台。</span><span class="sxs-lookup"><span data-stu-id="e7427-121">This guide does not cover base platform restoration.</span></span>  
  
2.  <span data-ttu-id="e7427-122">**還原 BizTalk Server 組態**</span><span class="sxs-lookup"><span data-stu-id="e7427-122">**Restoring the BizTalk Server Configuration**</span></span>  
  
     <span data-ttu-id="e7427-123">這個階段假設您有失敗的電腦上所設定之功能的記錄，包括該電腦的 BizTalk Server 組態檔複本。</span><span class="sxs-lookup"><span data-stu-id="e7427-123">This phase assumes that you have a record of the features configured on the failed computer, including a copy of the BizTalk Server configuration file for that computer.</span></span> <span data-ttu-id="e7427-124">這份指南僅提供還原 BizTalk Server 組態的指導。</span><span class="sxs-lookup"><span data-stu-id="e7427-124">This guide provides guidance for restoring the BizTalk Server configuration.</span></span>  
  
3.  <span data-ttu-id="e7427-125">**還原 BizTalk 應用程式**</span><span class="sxs-lookup"><span data-stu-id="e7427-125">**Restoring BizTalk Applications**</span></span>  
  
     <span data-ttu-id="e7427-126">這個階段包括在替換的電腦上還原與 BizTalk Server 程序所裝載應用程式相連接的 .NET 組件。</span><span class="sxs-lookup"><span data-stu-id="e7427-126">This phase involves restoring the .NET assemblies connected with the applications that are hosted by the BizTalk Server processes on the replacement computer.</span></span> <span data-ttu-id="e7427-127">所需的任何成品 (例如 BizTalk 組件以外的使用者組件) 都應該各自安裝在電腦上的對應位置或全域組件快取 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="e7427-127">Any artifacts that are needed, such as user assemblies apart from BizTalk assemblies, should be installed in their respective locations or the global assembly cache (GAC) on the computer.</span></span> <span data-ttu-id="e7427-128">這份指南提供了一些在此階段的指導，</span><span class="sxs-lookup"><span data-stu-id="e7427-128">This guide provides some guidance on this phase.</span></span> <span data-ttu-id="e7427-129">不過並沒有另外提供用來還原 BizTalk 應用程式的指令碼或工具。</span><span class="sxs-lookup"><span data-stu-id="e7427-129">However, there are no separate scripts or tools for restoring BizTalk applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7427-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="e7427-130">See Also</span></span>  
 [<span data-ttu-id="e7427-131">備份和還原 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="e7427-131">Backing Up and Restoring BizTalk Server</span></span>](../core/backing-up-and-restoring-biztalk-server.md)