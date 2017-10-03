---
title: "管理 BizTalk Server 效能設定 |Microsoft 文件"
description: "若要更新 BizTalk 群組、 主機和設定 BizTalk Server 中的主控件執行個體使用設定儀表板"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca56a981-a255-4c4d-82f8-a57d390e425e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0660fd4aa130049d80de4a0c2ee239ef5cae0068
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="manage-biztalk-server-performance-settings"></a><span data-ttu-id="684b8-103">管理 BizTalk Server 效能設定</span><span class="sxs-lookup"><span data-stu-id="684b8-103">Manage BizTalk Server Performance Settings</span></span>
  
 <span data-ttu-id="684b8-104">[!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] BizTalk Server 中自動分頁的效能設定，並提供了中央主控台，管理這些設定。</span><span class="sxs-lookup"><span data-stu-id="684b8-104">The [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] in BizTalk Server collates the performance settings, and provides a central console to manage these settings.</span></span> <span data-ttu-id="684b8-105">這有助於：</span><span class="sxs-lookup"><span data-stu-id="684b8-105">This helps to:</span></span>  
  
-   <span data-ttu-id="684b8-106">改善可設定之屬性的探索的能力</span><span class="sxs-lookup"><span data-stu-id="684b8-106">Improve the discoverability of the properties that can be set</span></span>
  
-   <span data-ttu-id="684b8-107">因為所有的設定現在都可存取在單一位置，而且可以匯出/匯入輕鬆地減少至方案的時間</span><span class="sxs-lookup"><span data-stu-id="684b8-107">Reduce the time-to-solution because all settings are now accessible in a single place and can be exported/imported easily</span></span>
  
-   <span data-ttu-id="684b8-108">提供的效能微調層級的整體檢視 BizTalk 部署上完成</span><span class="sxs-lookup"><span data-stu-id="684b8-108">Offers a holistic view of level of performance tuning done on a given BizTalk deployment</span></span>
  
## <a name="why-use-it"></a><span data-ttu-id="684b8-109">為何要使用它？</span><span class="sxs-lookup"><span data-stu-id="684b8-109">Why use it?</span></span>  
 <span data-ttu-id="684b8-110">[!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] 是針對需要廣泛調整 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 設定以達最佳化效能的 IT 系統管理員而設計的。</span><span class="sxs-lookup"><span data-stu-id="684b8-110">The [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] is targeted towards IT administrators who need to extensively tweak [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] settings for performance optimization.</span></span>  
  
 <span data-ttu-id="684b8-111">您可以使用 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] 來修改 BizTalk 群組的設定，以及該群組中所有 BizTalk 主控件和 BizTalk 主控件執行個體的設定。</span><span class="sxs-lookup"><span data-stu-id="684b8-111">You can use the [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] to modify settings for the BizTalk Group, and all the BizTalk Hosts and BizTalk Host Instances in that Group.</span></span>  
  
 <span data-ttu-id="684b8-112">若要深入了解群組、 主機和主機執行個體設定，請參閱[如何修改群組設定](../core/how-to-modify-group-settings.md)，[如何修改主控件設定](../core/how-to-modify-host-settings.md)，和[如何修改主控件執行個體設定](../core/how-to-modify-host-instance-settings.md).</span><span class="sxs-lookup"><span data-stu-id="684b8-112">To know more about the group, host, and host instance settings, see [How to Modify Group Settings](../core/how-to-modify-group-settings.md), [How to Modify Host Settings](../core/how-to-modify-host-settings.md), and [How to Modify Host Instance Settings](../core/how-to-modify-host-instance-settings.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="684b8-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="684b8-113">Prerequisites</span></span> 
 <span data-ttu-id="684b8-114">您可以從 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] 管理主控台啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="684b8-114">You can launch the [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] from the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="684b8-115">如需有關如何管理詳細[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]效能設定使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，請參閱[使用 BizTalk Server 管理主控台](../core/using-the-biztalk-server-administration-console.md)。</span><span class="sxs-lookup"><span data-stu-id="684b8-115">For information on how to manage [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performance settings using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, see [Using the BizTalk Server Administration Console](../core/using-the-biztalk-server-administration-console.md).</span></span>  
  
## <a name="where-do-i-start"></a><span data-ttu-id="684b8-116">要從何處著手？</span><span class="sxs-lookup"><span data-stu-id="684b8-116">Where Do I Start?</span></span>  
 <span data-ttu-id="684b8-117">您可以使用下列任一種方式存取 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)]：</span><span class="sxs-lookup"><span data-stu-id="684b8-117">You can access the [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] in any of the following ways:</span></span>  
  
-   <span data-ttu-id="684b8-118">啟動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**BizTalk 群組**在主控台樹狀目錄中，然後選取**設定**。</span><span class="sxs-lookup"><span data-stu-id="684b8-118">Start the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click **BizTalk Group** in the console tree, and then select **Settings**.</span></span>  
  
-   <span data-ttu-id="684b8-119">以滑鼠右鍵按一下底下的任何主機**平台設定**節點在 MMC 中的，按一下 中**設定**。</span><span class="sxs-lookup"><span data-stu-id="684b8-119">Right click any host under the **Platform Settings** node in MMC and click on **Settings**.</span></span> <span data-ttu-id="684b8-120">這會啟動 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)]，而您可以在其中修改該主控件的相關設定。</span><span class="sxs-lookup"><span data-stu-id="684b8-120">This launches [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] and you can modify the settings related to that host.</span></span>  
  
-   <span data-ttu-id="684b8-121">以滑鼠右鍵按一下任何主控件執行個體，底下**平台設定**節點在 MMC 中的，按一下 中**設定**。</span><span class="sxs-lookup"><span data-stu-id="684b8-121">Right click any host instance under the **Platform Settings** node in MMC and click on **Settings**.</span></span> <span data-ttu-id="684b8-122">這會啟動 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)]，而您可以在其中修改該主控件執行個體的相關設定。</span><span class="sxs-lookup"><span data-stu-id="684b8-122">This launches [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] and you can modify the settings related to that host instance.</span></span>  
  
## <a name="export-and-import-settings"></a><span data-ttu-id="684b8-123">匯出和匯入設定</span><span class="sxs-lookup"><span data-stu-id="684b8-123">Export and import settings</span></span>  
 <span data-ttu-id="684b8-124">[!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] 可讓您匯出 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的設定，再將該設定匯入到其他 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 環境，進而縮短完成解決方案所需的整體時間。</span><span class="sxs-lookup"><span data-stu-id="684b8-124">The [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] can be used to export settings from a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment and import it into another [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment, thereby reducing the overall time-to-solution.</span></span> <span data-ttu-id="684b8-125">當系統管理員會試著在測試環境中調整 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 效能，並會在達成想要的結果時將設定匯入實際執行環境的情況下，這種方式就特別有用。</span><span class="sxs-lookup"><span data-stu-id="684b8-125">This is especially useful in scenarios where the administrators try to tune [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performance in a test environment, and upon achieving the desired results, they can import the settings into a production environment.</span></span>  
  
 <span data-ttu-id="684b8-126">如需如何匯入/匯出使用[!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)]使用者介面，請參閱[匯入或匯出 BizTalk 設定使用設定儀表板](how-to-import-biztalk-settings-using-settings-dashboard.md)。</span><span class="sxs-lookup"><span data-stu-id="684b8-126">For information about how to import/export using the [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] user interface, see [Import or export BizTalk Settings Using Settings Dashboard](how-to-import-biztalk-settings-using-settings-dashboard.md).</span></span>
  
## <a name="scripting-support"></a><span data-ttu-id="684b8-127">指令碼支援</span><span class="sxs-lookup"><span data-stu-id="684b8-127">Scripting support</span></span>
 <span data-ttu-id="684b8-128">[!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] 不僅提供用以管理 BizTalk 設定的中央使用者介面，也可確保所有的設定與匯入/匯出工作皆可透過 API 與命令列選項來存取。</span><span class="sxs-lookup"><span data-stu-id="684b8-128">The [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] not only provides a central user interface to manage BizTalk settings but also ensures that all settings and the import/export tasks are accessible via APIs and command-line options.</span></span> <span data-ttu-id="684b8-129">這可以讓 BizTalk Server 系統管理員將 BizTalk Server 的相關設定工作自動化。</span><span class="sxs-lookup"><span data-stu-id="684b8-129">This enables BizTalk Server administrators to automate tasks related to BizTalk Server settings.</span></span> <span data-ttu-id="684b8-130">在這樣的指令碼支援當中：</span><span class="sxs-lookup"><span data-stu-id="684b8-130">As part of the scripting support:</span></span>  
  
-   <span data-ttu-id="684b8-131">可以存取及修改透過 WMI 類別的所有群組設定：`MSBTS_GroupSetting`</span><span class="sxs-lookup"><span data-stu-id="684b8-131">All group settings can be accessed and modified via the WMI Class: `MSBTS_GroupSetting`</span></span>  
  
-   <span data-ttu-id="684b8-132">所有的主控件設定可以存取及修改透過 WMI 類別：`MSBTS_HostSetting`</span><span class="sxs-lookup"><span data-stu-id="684b8-132">All host settings can be accessed and modified via the WMI Class: `MSBTS_HostSetting`</span></span>  
  
-   <span data-ttu-id="684b8-133">所有的主控件執行個體設定可以存取及修改透過 WMI 類別：`MSBTS_HostInstanceSetting`</span><span class="sxs-lookup"><span data-stu-id="684b8-133">All host instance settings can be accessed and modified via the WMI Class: `MSBTS_HostInstanceSetting`</span></span>  
  
-   <span data-ttu-id="684b8-134">匯入和匯出作業可以透過存取**BTSTask.exe**命令：`ExportSettings`和`ImportSettings`</span><span class="sxs-lookup"><span data-stu-id="684b8-134">Import and export operations can be accessed through **BTSTask.exe** commands: `ExportSettings` and `ImportSettings`</span></span>  
  
 <span data-ttu-id="684b8-135">如需有關如何使用 BTSTask.exe 命令列公用程式匯入/匯出的詳細資訊，請參閱[匯入或匯出 BizTalk 設定使用 BTSTask](how-to-import-biztalk-settings-using-btstask.md)。</span><span class="sxs-lookup"><span data-stu-id="684b8-135">For details about how to import/export using the BTSTask.exe command-line utility, see [Import or export BizTalk Settings Using BTSTask](how-to-import-biztalk-settings-using-btstask.md).</span></span>  
  
## <a name="next"></a><span data-ttu-id="684b8-136">下一個</span><span class="sxs-lookup"><span data-stu-id="684b8-136">Next</span></span>  
  
-   [<span data-ttu-id="684b8-137">使用設定儀表板，以便讓 BizTalk Server 效能調整</span><span class="sxs-lookup"><span data-stu-id="684b8-137">Use Settings Dashboard for BizTalk Server Performance Tuning</span></span>](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)  
  
-   [<span data-ttu-id="684b8-138">自動化 BizTalk Server 效能調整</span><span class="sxs-lookup"><span data-stu-id="684b8-138">Automate BizTalk Server Performance Tuning</span></span>](../core/automating-biztalk-server-performance-tuning.md)  
  
## <a name="see-also"></a><span data-ttu-id="684b8-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="684b8-139">See Also</span></span>  
 [<span data-ttu-id="684b8-140">管理 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="684b8-140">Manage BizTalk Server</span></span>](../core/use-groups-create-artifacts-optimize-performance-and-more-in-biztalk-server.md)