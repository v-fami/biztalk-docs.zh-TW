---
title: 使用設定儀表板，以便讓 BizTalk Server 效能微調 |Microsoft Docs
description: 在 BizTalk Server 管理中使用設定儀表板，來更新群組、 主機和主機執行個體設定
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3bb1ddac-1e8f-4928-9c70-8326ae64a734
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b6ed0c44bea5abaaac7b2009e27819e66043957
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974855"
---
# <a name="use-settings-dashboard-for-biztalk-server-performance-tuning"></a><span data-ttu-id="36542-103">使用設定儀表板，以便讓 BizTalk Server 效能調整</span><span class="sxs-lookup"><span data-stu-id="36542-103">Use Settings Dashboard for BizTalk Server Performance Tuning</span></span>

## <a name="overview"></a><span data-ttu-id="36542-104">概觀</span><span class="sxs-lookup"><span data-stu-id="36542-104">Overview</span></span>
<span data-ttu-id="36542-105">使用此 [設定儀表板]，您可以彈性調整 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 設定以獲得最佳效能。</span><span class="sxs-lookup"><span data-stu-id="36542-105">Using the Settings Dashboard, you can extensively tweak [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] settings for performance optimization.</span></span> <span data-ttu-id="36542-106">您也可以修改 BizTalk 群組、BizTalk 主控件與 BizTalk 主控件執行個體的設定。</span><span class="sxs-lookup"><span data-stu-id="36542-106">You can also modify settings for the BizTalk Group, BizTalk Host, and BizTalk Host Instance.</span></span>  
  
- <span data-ttu-id="36542-107">**群組層級設定**： 在群組層級中，您可以使用[!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)]設定像是組態重新整理間隔、 訊息批次大小上限、 群組層級追蹤的屬性，等等。這些設定會套用至 BizTalk 群組中的所有機器。</span><span class="sxs-lookup"><span data-stu-id="36542-107">**Group-level settings**: At the group level, you can use the [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] to set properties like the configuration refresh interval, maximum message batch size, group level tracking, etc. These settings are applied to all machines in a BizTalk Group.</span></span>  
  
- <span data-ttu-id="36542-108">**主機層級設定**： 在主機層級中，您可以修改主控件追蹤、 與資源型節流相關的屬性、 訊息處理節流相關的屬性以及與協調流程節流相關的屬性等設定。</span><span class="sxs-lookup"><span data-stu-id="36542-108">**Host-level settings**: At the host level, you can modify settings like host tracking, properties related to resource based throttling, properties related to message process throttling, and properties related to orchestrations throttling.</span></span> <span data-ttu-id="36542-109">這些設定會套用至所選主控件的所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="36542-109">These settings are applied to all instances of the selected host.</span></span>  
  
- <span data-ttu-id="36542-110">**主控件執行個體層級設定**： 在主控件執行個體層級中，您可以修改.NET CLR 設定和與協調流程記憶體節流相關的屬性。</span><span class="sxs-lookup"><span data-stu-id="36542-110">**Host instance level settings**: At the host instance level, you can modify .NET CLR settings and properties related to orchestration memory throttling.</span></span> <span data-ttu-id="36542-111">這些設定只會套用至所選主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="36542-111">These settings are applied to only the selected host instance.</span></span>  
  
  <span data-ttu-id="36542-112">如需 BizTalk 群組、 BizTalk 主控件與 BizTalk 主控件執行個體設定的詳細資訊，請參閱[如何修改群組設定](../core/how-to-modify-group-settings.md)，[如何修改主控件設定](../core/how-to-modify-host-settings.md)，和[如何修改主機執行個體設定](../core/how-to-modify-host-instance-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="36542-112">For more information about BizTalk Group, BizTalk Host, and BizTalk Host Instance settings, see [How to Modify Group Settings](../core/how-to-modify-group-settings.md), [How to Modify Host Settings](../core/how-to-modify-host-settings.md), and [How to Modify Host Instance Settings](../core/how-to-modify-host-instance-settings.md).</span></span>  
  
  <span data-ttu-id="36542-113">[設定儀表板] 可讓您在不需一致的部署間匯入/匯出 BizTalk 設定。</span><span class="sxs-lookup"><span data-stu-id="36542-113">The Settings Dashboard enables you to import/export BizTalk settings across deployments that need not be identical.</span></span> <span data-ttu-id="36542-114">使用此使用者介面，您可以將目的地的主控件和主控件執行個體對應至來源部署。</span><span class="sxs-lookup"><span data-stu-id="36542-114">Using the user interface, you can map the hosts and host instances from destination to source deployments.</span></span> <span data-ttu-id="36542-115">這樣可讓您將設定套用至主控件與電腦名稱或它們的數目各不相同的的環境中。</span><span class="sxs-lookup"><span data-stu-id="36542-115">This helps you apply settings to an environment where host and machine names, or their respective counts, are different.</span></span> <span data-ttu-id="36542-116">如需匯入/匯出 BizTalk 設定的詳細資訊，請參閱 <<c0> [ 匯入或匯出 BizTalk 設定使用設定儀表板](how-to-import-biztalk-settings-using-settings-dashboard.md)。</span><span class="sxs-lookup"><span data-stu-id="36542-116">For more details about importing/exporting BizTalk settings, see [Import or export BizTalk Settings Using Settings Dashboard](how-to-import-biztalk-settings-using-settings-dashboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36542-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36542-117">See Also</span></span>  
 [<span data-ttu-id="36542-118">管理 BizTalk Server 效能設定</span><span class="sxs-lookup"><span data-stu-id="36542-118">Manage BizTalk Server Performance Settings</span></span>](../core/managing-biztalk-server-performance-settings.md)