---
title: 實體圖 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying, network configuration
ms.assetid: 4291727b-8687-496a-8f03-0da4b3201967
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0fcd0558d8fe3d45063a53800b1f3c082a2ba056
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="physical-diagram"></a><span data-ttu-id="f7565-102">實體的圖表</span><span class="sxs-lookup"><span data-stu-id="f7565-102">Physical Diagram</span></span>
<span data-ttu-id="f7565-103">一般的部署已叢集化 BizTalk Server 電腦的訊息 （傳送和接收），來執行商務程序 （協調流程），以存取 InfoPath 範本 （MRSR 站台），BizTalk Server 電腦的 BizTalk Server 電腦和叢集的 SQL Server 電腦。</span><span class="sxs-lookup"><span data-stu-id="f7565-103">A typical deployment has clustered BizTalk Server computers for messaging (sending and receiving), BizTalk Server computers for executing the business process (orchestration), BizTalk Server computers for accessing the InfoPath templates (MRSR site), and clustered SQL Server computers.</span></span> <span data-ttu-id="f7565-104">下列部署可確保內部網路和網際網路使用者安全的環境。</span><span class="sxs-lookup"><span data-stu-id="f7565-104">The following deployment ensures a secure environment from both the intranet and Internet users.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7565-105">這個一般的部署是建議的設定。</span><span class="sxs-lookup"><span data-stu-id="f7565-105">This typical deployment is the recommended configuration.</span></span> <span data-ttu-id="f7565-106">您必須驗證您自己的商務需求和伺服器設定以確保您部署的正確運作。</span><span class="sxs-lookup"><span data-stu-id="f7565-106">You will need to verify your own business needs and server configurations to make certain your deployment works correctly.</span></span>  
  
 <span data-ttu-id="f7565-107">您可以調整此部署向上或向下或上一步，取決於使用設定檔和持續成長的商務需求。</span><span class="sxs-lookup"><span data-stu-id="f7565-107">You can scale this deployment up or down, out or back, depending on the usage profile and your growing business needs.</span></span> <span data-ttu-id="f7565-108">延展性的一般案例包括新增一或多個伺服器，每個叢集，以確保高可用性或更佳的輸送量。</span><span class="sxs-lookup"><span data-stu-id="f7565-108">Typical scalability scenarios include adding one or more servers in each cluster to ensure higher availability or better throughput.</span></span> <span data-ttu-id="f7565-109">較小的企業可能會想要調整回其部署至具有相同的伺服器執行多個功能，例如包含一個[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]電腦處理協調流程與傳訊。</span><span class="sxs-lookup"><span data-stu-id="f7565-109">Smaller enterprises might prefer scaling back their deployment to have the same servers perform multiple functions, such as having one [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] computer handle both orchestration and messaging.</span></span> [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="f7565-110">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]支援部署在單一伺服器上。</span><span class="sxs-lookup"><span data-stu-id="f7565-110">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] supports deployment on a single server.</span></span> <span data-ttu-id="f7565-111">下圖顯示完整的 A4SWIFT 部署的建議的分散式的部署環境的範例。</span><span class="sxs-lookup"><span data-stu-id="f7565-111">The following figure shows an example of the recommended distributed deployment environment for a full A4SWIFT deployment.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/fsa-deploy-full.gif "FSA_Deploy_Full")  
<span data-ttu-id="f7565-112">完整的 A4SWIFT 部署範例</span><span class="sxs-lookup"><span data-stu-id="f7565-112">Example of a full A4SWIFT deployment</span></span>