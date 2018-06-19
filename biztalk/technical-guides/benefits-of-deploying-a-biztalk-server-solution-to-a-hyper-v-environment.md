---
title: 潛在優點，BizTalk Server 方案部署到使用 HYPER-V 的虛擬化環境 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 588c70f0-68f0-4e58-8f3d-aa6834397bd4
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9602a48b0deb4eeddc6f10b2d529d68d94cc781a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295926"
---
# <a name="potential-benefits-of-deploying-a-biztalk-server-solution-to-a-hyper-v-virtualized-environment"></a><span data-ttu-id="d7d2f-102">潛在優點，BizTalk Server 方案部署到使用 HYPER-V 的虛擬化環境</span><span class="sxs-lookup"><span data-stu-id="d7d2f-102">Potential Benefits of Deploying a BizTalk Server Solution to a Hyper-V Virtualized Environment</span></span>
<span data-ttu-id="d7d2f-103">本主題描述一些部署的優點您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]HYPER-V 虛擬化環境中的方案。</span><span class="sxs-lookup"><span data-stu-id="d7d2f-103">This topic describes some of the benefits of deploying your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution to a Hyper-V virtualized environment.</span></span>  
  
## <a name="benefits-of-running-a-biztalk-server-solution-on-a-hyper-v-virtualized-environment"></a><span data-ttu-id="d7d2f-104">HYPER-V 上執行 BizTalk Server 解決方案的優點虛擬化環境</span><span class="sxs-lookup"><span data-stu-id="d7d2f-104">Benefits of Running a BizTalk Server Solution on a Hyper-V Virtualized Environment</span></span>  
 <span data-ttu-id="d7d2f-105">部署在 HYPER-V 虛擬化環境上執行 BizTalk Server 解決方案提供彈性，下列功能：</span><span class="sxs-lookup"><span data-stu-id="d7d2f-105">Deploying your BizTalk Server solution to run on a Hyper-V virtualized environment provides the following flexibility and functionality:</span></span>  
  
-   <span data-ttu-id="d7d2f-106">**在單一的實體電腦-定義多個不同的邏輯安全性界限的能力**HYPER-V 可容納不同的邏輯安全性界限或單一實體硬體資源內的資料分割的建立。</span><span class="sxs-lookup"><span data-stu-id="d7d2f-106">**Ability to define multiple distinct logical security boundaries on a single physical computer -** Hyper-V accommodates the creation of distinct logical security boundaries or partitions within a single physical hardware resource.</span></span> <span data-ttu-id="d7d2f-107">資料分割是隔離的支援的 hypervisor，作業系統執行所在的單一邏輯單元。</span><span class="sxs-lookup"><span data-stu-id="d7d2f-107">A partition is a single logical unit of isolation, supported by the hypervisor, in which operating systems execute.</span></span> <span data-ttu-id="d7d2f-108">例如，您可以建立多個 BizTalk Server 群組，來執行單一的 HYPER-V 主機電腦上，而您會無法安裝時執行這項操作[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]單一主機電腦的主機作業系統上。</span><span class="sxs-lookup"><span data-stu-id="d7d2f-108">For example, you could create multiple BizTalk Server groups to run on a single Hyper-V host computer whereas you would not be able to do this when installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on the host operating system of a single host computer.</span></span>  
  
-   <span data-ttu-id="d7d2f-109">**簡化部署和管理 –** 的彙總[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]成較少的實體伺服器的電腦，可簡化部署。</span><span class="sxs-lookup"><span data-stu-id="d7d2f-109">**Ease of deployment and management –** Consolidation of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computers into fewer physical servers simplifies deployment.</span></span> [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]<span data-ttu-id="d7d2f-110">藉由使用.vhd 檔案，進行實體和虛擬電腦部署使用簡單的方法。</span><span class="sxs-lookup"><span data-stu-id="d7d2f-110"> uses a simplified method for physical and virtual computer deployments by using .vhd files.</span></span> <span data-ttu-id="d7d2f-111">此外，完整的 HYPER-V 管理解決方案是使用 System Center Virtual Machine Manager。</span><span class="sxs-lookup"><span data-stu-id="d7d2f-111">Furthermore, a comprehensive Hyper-V management solution is available with System Center Virtual Machine Manager.</span></span> <span data-ttu-id="d7d2f-112">如需 System Center Virtual Machine Manager 的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkID=111303](http://go.microsoft.com/fwlink/?LinkID=111303)。</span><span class="sxs-lookup"><span data-stu-id="d7d2f-112">For more information about System Center Virtual Machine Manager, see [http://go.microsoft.com/fwlink/?LinkID=111303](http://go.microsoft.com/fwlink/?LinkID=111303).</span></span>  
  
-   <span data-ttu-id="d7d2f-113">**錯誤容錯支援透過 HYPER-V 叢集-** 因為 HYPER-V 是感知叢集應用程式、 Windows Server 2008 提供原生的主機叢集為 HYPER-V 虛擬化環境中建立的虛擬機器的支援。</span><span class="sxs-lookup"><span data-stu-id="d7d2f-113">**Fault tolerance support through Hyper-V clustering -** Because Hyper-V is a cluster aware application, Windows Server 2008 provides native host clustering support for virtual machines created in a Hyper-V virtualized environment.</span></span>  
  
-   <span data-ttu-id="d7d2f-114">**向外延展-輕鬆**可以容納額外的處理電源、 網路頻寬和儲存容量的您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]方案快速且輕鬆地 apportioning 其他可用的資源從主機電腦客體虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="d7d2f-114">**Ease of scale-out -** Additional processing power, network bandwidth, and storage capacity can be accommodated for your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution quickly and easily by apportioning additional available resources from the host computer to the guest virtual machine(s).</span></span> <span data-ttu-id="d7d2f-115">這可能需要在主機電腦會在升級或客體虛擬機器會移至更適用的主機電腦。</span><span class="sxs-lookup"><span data-stu-id="d7d2f-115">This may require that the host computer is upgraded or that the guest virtual machines are moved to a more capable host computer.</span></span> <span data-ttu-id="d7d2f-116">即時移轉功能[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]可讓您移動執行中 Vm 的效能、 調整或最佳化彙總最佳的實體電腦而不會影響使用者。</span><span class="sxs-lookup"><span data-stu-id="d7d2f-116">The live migration feature of [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] allows you to move running VMs to the best physical computer for performance, scaling, or optimal consolidation without impacting users.</span></span>  
  
-   <span data-ttu-id="d7d2f-117">**硬體資源的彙總**多部實體伺服器可輕易地合併到相對較少的伺服器藉由實作與 HYPER-V 虛擬化。</span><span class="sxs-lookup"><span data-stu-id="d7d2f-117">**Consolidation of hardware resources -** Multiple physical servers can be easily consolidated into comparatively fewer servers by implementing virtualization with Hyper-V.</span></span> <span data-ttu-id="d7d2f-118">彙總可容納已部署的硬體資源的完整使用權。</span><span class="sxs-lookup"><span data-stu-id="d7d2f-118">Consolidation accommodates full use of deployed hardware resources.</span></span>  
  
 <span data-ttu-id="d7d2f-119">若要找出更多詳細資訊的功能和優點 HYPER-V 提供，請參閱[與 HYPER-V 虛擬化](http://go.microsoft.com/fwlink/?LinkID=202438)。</span><span class="sxs-lookup"><span data-stu-id="d7d2f-119">To find out more detailed information about the features and benefits Hyper-V provides, see [Virtualization with Hyper-V](http://go.microsoft.com/fwlink/?LinkID=202438).</span></span>