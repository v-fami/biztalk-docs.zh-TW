---
title: 實體圖表 |Microsoft Docs
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
ms.openlocfilehash: 695c8ca0fd03fd8324f5b0ab86d72c1c0b6daf9f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978631"
---
# <a name="physical-diagram"></a><span data-ttu-id="b8738-102">實體圖表</span><span class="sxs-lookup"><span data-stu-id="b8738-102">Physical Diagram</span></span>
<span data-ttu-id="b8738-103">典型的部署有叢集 BizTalk Server 電腦的訊息 （傳送和接收），來執行商務程序 （協調流程），以存取 InfoPath 範本 （MRSR 站台），BizTalk Server 電腦的 BizTalk Server 電腦和叢集的 SQL Server 電腦。</span><span class="sxs-lookup"><span data-stu-id="b8738-103">A typical deployment has clustered BizTalk Server computers for messaging (sending and receiving), BizTalk Server computers for executing the business process (orchestration), BizTalk Server computers for accessing the InfoPath templates (MRSR site), and clustered SQL Server computers.</span></span> <span data-ttu-id="b8738-104">下列的部署可確保安全的環境，從內部網路和網際網路使用者。</span><span class="sxs-lookup"><span data-stu-id="b8738-104">The following deployment ensures a secure environment from both the intranet and Internet users.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8738-105">這個典型的部署是建議的設定。</span><span class="sxs-lookup"><span data-stu-id="b8738-105">This typical deployment is the recommended configuration.</span></span> <span data-ttu-id="b8738-106">您必須確認您自己的商務需求和伺服器設定，確定您的部署正常運作。</span><span class="sxs-lookup"><span data-stu-id="b8738-106">You will need to verify your own business needs and server configurations to make certain your deployment works correctly.</span></span>  
  
 <span data-ttu-id="b8738-107">您可以調整此部署增加或減少、 放大或，根據使用方式設定檔，並不斷成長的業務需求。</span><span class="sxs-lookup"><span data-stu-id="b8738-107">You can scale this deployment up or down, out or back, depending on the usage profile and your growing business needs.</span></span> <span data-ttu-id="b8738-108">典型的擴充性案例包括新增一或多個伺服器中每個叢集，以確保更高的可用性或更高的輸送量。</span><span class="sxs-lookup"><span data-stu-id="b8738-108">Typical scalability scenarios include adding one or more servers in each cluster to ensure higher availability or better throughput.</span></span> <span data-ttu-id="b8738-109">較小的企業可能會偏好調整回其部署到具有相同的伺服器執行多個功能，例如有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]電腦處理協調流程和傳訊。</span><span class="sxs-lookup"><span data-stu-id="b8738-109">Smaller enterprises might prefer scaling back their deployment to have the same servers perform multiple functions, such as having one [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] computer handle both orchestration and messaging.</span></span> <span data-ttu-id="b8738-110">Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]支援部署在單一伺服器上。</span><span class="sxs-lookup"><span data-stu-id="b8738-110">Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] supports deployment on a single server.</span></span> <span data-ttu-id="b8738-111">下圖顯示完整的 A4SWIFT 部署的建議的分散式的部署環境的範例。</span><span class="sxs-lookup"><span data-stu-id="b8738-111">The following figure shows an example of the recommended distributed deployment environment for a full A4SWIFT deployment.</span></span>  
  
 <span data-ttu-id="b8738-112">![](../../adapters-and-accelerators/accelerator-swift/media/fsa-deploy-full.gif "FSA_Deploy_Full")</span><span class="sxs-lookup"><span data-stu-id="b8738-112">![](../../adapters-and-accelerators/accelerator-swift/media/fsa-deploy-full.gif "FSA_Deploy_Full")</span></span>  
<span data-ttu-id="b8738-113">完整的 A4SWIFT 部署範例</span><span class="sxs-lookup"><span data-stu-id="b8738-113">Example of a full A4SWIFT deployment</span></span>